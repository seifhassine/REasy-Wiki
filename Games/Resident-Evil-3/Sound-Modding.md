[⬅️ Back to Resident Evil 3](./README.md)

# Sound and Music Modding (non-RT)

Notes for Resident Evil 3 (2020), the standard build without the ray-tracing
update. Every ID below was read from the game files in that build. The RT
build may differ.

The full map of how the game picks music (every switch, every cue, every
object ID) is in [the music system reference](./Music-Graph.md). This page is the steps.

## The hotspots (main files for music)

```
system.bnk        → natives/stm/escape/sound/wwise/system.bnk.2.stm
music_resident.bnk → natives/stm/escape/sound/wwise/music_resident.bnk.2.stm
music_resident.pck → natives/stm/streaming/escape/sound/wwise/music_resident.pck.3.stm
master_system.wel → natives/stm/escape/sound/resource/snd_event/event_master/master_system.wel.11
music.wel         → natives/stm/escape/sound/resource/snd_event/event_music/music.wel.11
```

REasy shows the stems (`bnk`/`pck`/`wel`). The `.2`/`.3`/`.11` are RE Engine
suffixes.

Other files you might frequently edit:

```
music_title.bnk   → natives/stm/escape/sound/wwise/music_title.bnk.2.stm
event_system.bnk  → natives/stm/escape/sound/wwise/event_system.bnk.2.stm
music_title.wel   → natives/stm/escape/sound/resource/snd_event/event_music/music_title.wel.11
event_system.wel  → natives/stm/escape/sound/resource/snd_event/event_event/event_system.wel.11
state files (.wss / .wgs) → natives/stm/escape/sound/resource/snd_state/state_music/
```

`music_title` is the title-screen song. `event_system` is system one-shots.

## The one rule

`system.bnk` holds the logic. `music_resident.bnk` only holds audio.

- Replace a song's sound → `music_resident.pck` + `music_resident.bnk` (Replace only in one. REasy will automatically modify the other).
- Change what plays, when, or how it loops → `system.bnk` only. The HIRC copy
  inside `music_resident.bnk` is stale and the game ignores it.

## 1. Replace a song's audio

1. Replace the `.wem` inside `music_resident.pck.3.stm`. If the cue is a
   prefetch, REasy will automatically replace the embedded chunk in `music_resident.bnk.2.stm`.
2. REasy swaps the audio bytes only — it does not recompute duration or loop
   points. If the new clip is a different length or loops differently, fix
   them in `system.bnk` (the Music Segment / Music Track), not in
   `music_resident.bnk`.

## 2. Point an existing cue at your song

The game already sets a cue at the right moment. You re-point that cue.

Worked example, `chp1_town1` (the town theme at the start of chapter 1):

1. Put your audio in as a source (Recipe 1) or reuse an existing source.
2. Open `system.bnk` in REasy, **All Objects** tab:
   - **Duplicate…** an existing Music Track (type `0x0B`, 11) and give it a name;
     REasy turns the name into its ShortID. Then **Properties…** and set the
     track's **Source ID** to your audio.
   - **Duplicate…** an existing Music Segment (type `0x0A`, 10) and give it a name.
     Select it and **Connect Child…** → pick your track. Write down the
     segment's ShortID.
3. Still in **All Objects**, search `0x214A8DC5 (558534085)` (the chapter 1 switch).
4. **Properties…** → **Value mappings**: find the `chp1_town1` row and change
   its **Child ShortIDs** from `0x33134FD9 (856903641)` to your segment's ID.
5. Save. No `.wel` change, no new state.

Trace the chain before you edit it, so you know what you're re-pointing:

```
chp1_town1 → Random 0x33134FD9 (856903641) → Segment 0x0933E796 (154396566) (45.7 s) → Track 0x23F48427 (603227175) → source 0x13A3E92A (329509162) (streamed .wem)
```

You're changing the first hop in that chain.

Switch object ID per chapter:

| Chapter | Switch object ID (in `system.bnk`) |
|---|---|
| chp0 | `0x3E64B0EE (1046786286)` |
| chp1 | `0x214A8DC5 (558534085)` |
| chp2 | `0x207E79C0 (545159616)` |
| chp3 | `0x3970DFAC (963698604)` |
| chp3_2 | `0x029A2387 (43656071)` |
| chp4 | `0x3F76BB24 (1064745764)` |
| chp5 | `0x1167467F (291980927)` |

Each cue's current target ID is listed in [the music system reference](./Music-Graph.md).

## 3. Start or stop a song from your own trigger

Use this when you control the trigger (a collider, door, or script) and want a
specific song.

1. In `system.bnk` add an Event whose action is Play → your Music Segment (or
   a Random/Sequence of several segments).
2. Note the event's ShortID. When you add the event, REasy asks for "Event name
   or numeric ShortID" — type a name and it computes the FNV-1a ID for you
   (case-insensitive).
3. Add a row to `master_system.wel.11`:
   - `TriggerID = Murmur3(trigger name)` — case-sensitive
   - `EventID  = the event ID from step 2
4. Fire that trigger from your collider or script.

Trigger ID tool: REasy's **Tools → Hash Calculator** computes Murmur3 (use the
hex result). It does not compute FNV-1a, so the event ID comes from the bank
editor in step 2, not from the calculator.

To stop it, add a second event with a Stop action and a second trigger row.

Which `.wel` to use:

- events in `system.bnk` → `master_system.wel`
- events in `music_resident.bnk` → `music.wel`
- title music → `music_title.wel` (bank `music_title.bnk`)
- system one-shots → `event_system.wel`

The `.wel` header names its bank, so put the row in the file whose bank holds
your event.

Hash reference. FNV-1a lowercases before hashing: `on` = `0x6277173E (1651971902)`,
`off` = `0x37798A64 (930712164)`, `in` = `0x687720AC (1752637612)`, `out` = `0x26796F4B (645492555)`. Murmur3 does
not lowercase, so `Foo` and `foo` are different IDs.

Gotcha: hash the state value, not the `.wss` file name. The file
`chp2_em30_2ormore.wss` holds the value `chp2_em30_2`. The file
`bgm_difficulty_other.wss` holds the value `other`.

## 4. Adding a new state (rarely worth it)

Cue names (`chp1_town1`, `chp0_chase_3rd`, …) are set by game code. To add a
new one you need a `.wss` pair, a `.wgs` entry, a switch mapping, and game code
that actually sets the state. Recipe 2 or
3 is almost always easier.

---

[⬅️ Back to Resident Evil 3](./README.md) | [⬆️ Top](#sound-and-music-modding-non-rt)
