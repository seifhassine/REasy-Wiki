[⬅️ Back to Games](../README.md)

# Street Fighter 6 File Structure Reference

This page contains quick-reference information for **Street Fighter 6** modding, including character IDs, stage IDs, costume slots, common abbreviations and frequently used RE Engine file types.

The main Street Fighter 6 game data is generally found under:

```text
natives/stm/product/
```

Streaming assets are generally found under:

```text
natives/stm/streaming/product/
```

The information on this page is based on observed game data and practical modding use. Sections can be expanded over time as more of the game's file structure is documented.

---

# Character Codes

Street Fighter 6 uses `esf` identifiers throughout character-related paths and files.

| Code | Character |
|---|---|
| `esf001` | Ryu |
| `esf002` | Luke |
| `esf003` | Kimberly |
| `esf004` | Chun-Li |
| `esf005` | Manon |
| `esf006` | Zangief |
| `esf007` | JP |
| `esf008` | Dhalsim |
| `esf009` | Cammy |
| `esf010` | Ken |
| `esf011` | Dee Jay |
| `esf012` | Lily |
| `esf013` | A.K.I. |
| `esf014` | Rashid |
| `esf015` | Blanka |
| `esf016` | Juri |
| `esf017` | Marisa |
| `esf018` | Guile |
| `esf019` | Ed |
| `esf020` | E. Honda |
| `esf021` | Jamie |
| `esf022` | Akuma |
| `esf025` | Sagat |
| `esf026` | M. Bison |
| `esf027` | Terry |
| `esf028` | Mai |
| `esf029` | Elena |
| `esf030` | C. Viper |
| `esf031` | Alex |
| `esf032` | Ingrid |
| `esf033` | Yasmine |

## Special / SiRN Characters

| Code | Character |
|---|---|
| `esf101` | SiRN Akuma |
| `esf102` | SiRN M. Bison |
| `esf103` | Dark Ingrid |

> `esf023` and `esf024` currently appear to be unused character slots and are not present as normal character entries within the known PAK file structure.

---

# Stage Codes

Street Fighter 6 uses different identifiers for many **Fighting Ground** and **World Tour** versions of its stages and locations.

| Fighting Ground | World Tour | Stage |
|---|---|---|
| `ess0000` | — | Training Room |
| `ess0100` | `wtc0100` | Old Town Market |
| `ess0101` | `wtc0101` | Suval'hal Arena |
| `ess0200` | `wtc0200` | Genbu Temple |
| `ess0201` | `wtc0201` | Enma's Hollow |
| — | `wtc0202` | Aokigahara |
| `ess0300` | `wtc0300` | Tian Hong Yuan |
| `ess0400` | `wtc0400` | Metro City Downtown |
| `ess0401` | `wtc0401` | Carrier Byron Taylor |
| `ess0410` | `wtc0410` | Pao Pao Cafe 6 |
| `ess0500` | `wtc0500` | Barmaley Steelworks |
| `ess0600` | `wtc0600` | Fête Foraine |
| `ess0700` | `wtc0700` | Dhalsim Temple |
| `ess0800` | `wtc0800` | Ranger's Hut |
| `ess0900` | `wtc0900` | Bathers Beach |
| `ess1000` | `wtc1000` | King Street |
| `ess1100` | `wtc1100` | Thunderfoot Settlement |
| `ess1200` | `wtc1200` | Colosseo |
| `ess1300` | `wtc1300` | Ruined Lab |
| `ess1400` | `wtc1400` | Geniala Remains |
| `ess1500` | `wtc1500` | Proud Spire |
| `ess4000` | — | The Macho Ring |
| `hub0000` | — | Battle Hub |
| — | `wtc3000` | NULSPACE |

---

# Costume Codes / Slots

SF6 modders commonly refer to costume slots as **C1, C2, C3, C4 and C5**.

| Folder | Modding Name | In-Game Name |
|---|---|---|
| `001` | C1 | Outfit 1 |
| `002` | C2 | Outfit 2 |
| `003` | C3 | Outfit 3 |
| `004` | C4 | Outfit 4 |
| `005` | C5 | Outfit 5 |

The number of available outfit slots depends on the character and current game version.

---

# Common Abbreviations

| Abbreviation | Meaning |
|---|---|
| `FG` | Fighting Ground |
| `WT` | World Tour |
| `WTM` | World Tour Mode |
| `BH` | Battle Hub |
| `MG` | Mini Game |
| `CS` | Cutscene |
| `CFN` | Capcom Fighters Network |
| `CMN` | Common Menus / shared menu data |
| `GM` | General Menus / front-end menus |
| `AC` | Avatar Arcade |
| `KSW` | Nintendo Switch gimmick / mini-game data |
| `ES` | Esports / main in-match GUI and textures |
| `ess` | Stage / Esports Scene Stage |
| `esf` | Character-related data |
| `om` | Commonly associated with background NPCs, objects or motion data; exact meaning varies |

---

# Common File Types

These are some of the file types most commonly encountered when modding Street Fighter 6.

| File Type | Typical Use |
|---|---|
| `.mesh` | 3D model geometry |
| `.tex` | Textures, masks and UI images |
| `.mdf2` | Material definitions, texture assignments, shader flags and parameters |
| `.user.2` | Structured game data; used by many systems including costume colour data |
| `.chain` | Character body, hair, clothing and accessory physics |
| `.scn` | Scene data and resource references |
| `.pfb` | Prefab data and resource holders |
| `.uvs` | UI animation / UV layout data |
| `.msg` | Text, localisation and message data |
| `.motbank` | Motion / animation banks |
| `.motlist` | Motion lists |
| `.sbnk` | Wwise sound-bank logic and event data |
| `.spck` | Wwise audio media / sound packs |
| `.oft` | Font data |
| `.rtex` | Render-texture resources |

File versions are appended after the extension, for example:

```text
.mesh.230110883
.tex.241101895
.mdf2.31
.user.2
.chain.52
.scn.20
.pfb.17
```

# Understanding RE Engine File Names

RE Engine files commonly use a structure such as:

```text
filename.extension.version
```

For example:

```text
20101.mov.1
```

This can be broken down as:

| Part | Example | Meaning |
|---|---|---|
| Filename | `20101` | The name or identifier of the file |
| Extension | `.mov` | The file type |
| Version | `.1` | The version of that file format used by the game |

A texture may look like:

```text
example.tex.241101895
```

where:

- `example` is the filename.
- `.tex` is the file type.
- `.241101895` is the file-format version used by that game.

The same applies to other common RE Engine formats.

Examples include:

```text
example.user.2
example.pfb.17
example.mesh.230110883
example.tex.241101895
```

Files such as `.user.2` and `.pfb.17` are especially common when working with RE Engine game data.

The version suffix is important because different RE Engine games — and sometimes different revisions of the same game — can use different versions of the same file format.

---

### Street Fighter 6 Texture Version Change

Street Fighter 6 previously used:

```text
.tex.143230113
```

before the later engine changes associated with the Switch 2-era update.

Current versions use:

```text
.tex.241101895
```

# Common Modding Areas

<details>
<summary><strong>Character Models and Costumes</strong></summary>

<br>

Character and costume modding is one of the most common types of Street Fighter 6 modding.

Common character mods include:

- Costume colour edits
- Texture replacements
- Hair swaps
- Mesh swaps
- Removing costume parts
- Swapping parts between outfits
- Full costume replacements
- Physics edits
- Material edits

The three most important locations are:

```text
product/model/esf/
product/charparam/
streaming/product/model/esf/
```

- `product/model/esf/` — Character meshes, MDF materials, CMD colour data, chain physics and lower-resolution texture assets.
- `product/charparam/` — Character setup and references linking body, head, hair, materials, physics and other character resources.
- `streaming/product/model/esf/` — Full-resolution streaming character textures and related assets.

---

## Character and Costume Folder Structure

Character model data is organised using the character's `esf` ID.

For example:

```text
product/model/esf/esf009/
```

is **Cammy**.

Each outfit then uses its numbered costume slot:

```text
001 = C1
002 = C2
003 = C3
004 = C4
005 = C5
```

Not every character currently has every outfit slot.

**Yasmine currently has C1, C2 and C5**, making her the only current character without C3.

### Characters Currently With C4

- Luke
- Jamie
- Chun-Li
- Kimberly
- Juri
- Dee Jay
- Manon
- Zangief
- Cammy
- A.K.I.
- Elena

Available costume slots may expand as additional outfits are added to the game.

---

## Character Model Parts

Within each costume folder, numbered folders commonly separate the fighter into different model parts.

| Folder | Typical Part |
|---|---|
| `00` | Head |
| `01` | Body / Costume |
| `02` | Hair |
| `10` | Bone / shared skeletal-related model |

For example:

```text
product/model/esf/esf009/001/01/
```

contains the main body resources for **Cammy C1**.

The exact structure can differ depending on the fighter and outfit.

---

## Typical Character Mod Files

A character mod may contain files such as:

```text
esf009_001_01.mesh.230110883
esf009_001_01_v00.mdf2.31
esf009_001_01_chain.chain.52

esf009_001_cmd_001.user.2
esf009_001_cmd_002.user.2
esf009_001_cmd_003.user.2
...
esf009_001_cmd_010.user.2

esf009_001_01_clothb_albd.tex.241101895
esf009_001_01_clothb_nrrc.tex.241101895
```

A mod does not necessarily need all of these files.

A simple colour mod may only replace textures or CMD files, while a full costume replacement can include meshes, MDFs, textures, physics and character scene edits.

---

## Important Character File Types

| File Type | Purpose |
|---|---|
| `.mesh.230110883` | Character model geometry |
| `.tex.241101895` | Character textures and masks |
| `.mdf2.31` | Materials, texture assignments, shader flags and parameters |
| `.user.2` | Structured data, including CMD costume colour data |
| `.chain.52` | Character body, hair, clothing and accessory physics |
| `.scn.20` | Character scene/configuration container and resource references |

REasy supports these major character-modding formats with dedicated viewers or editors where applicable.

---

## Character Textures

Character texture filenames usually identify:

```text
Character → Outfit → Part → Material → Texture Type
```

Examples from Cammy include:

```text
esf009_001_01_clothb_albd.tex.241101895
esf009_001_01_clothb_nrrc.tex.241101895
esf009_001_01_clothb_1_cmask.tex.241101895
esf009_001_01_clothb_2_cmask.tex.241101895

esf009_001_01_clothc_albd.tex.241101895
esf009_001_01_clothc_nrrc.tex.241101895
esf009_001_01_clothc_1_cmask.tex.241101895
esf009_001_01_clothc_2_cmask.tex.241101895

esf009_001_01_costume_cwmask.tex.241101895
```

These are examples of the normal naming structure used by the game.

More experienced modders can use completely custom texture names, but the corresponding MDF texture paths must also be changed to reference them.

---

### `ALBD` — Base Colour

Example:

```text
esf009_001_01_clothb_albd.tex.241101895
```

The MDF normally identifies this texture as:

```text
BaseDielectricMap
```

`ALBD` contains the main visible colour information for the material.

---

### `NRRC` — Normal / Roughness / Cavity

Example:

```text
esf009_001_01_clothb_nrrc.tex.241101895
```

The MDF normally identifies this as:

```text
NormalRoughnessCavityMap
```

This packed texture controls surface detail and how the material reacts to lighting.

It contains information associated with:

- Normal detail
- Roughness
- Cavity / surface detail

It has a major effect on how skin, cloth and other materials respond to lighting.

---

### `CMASK` — Costume Colour Mask

Examples:

```text
esf009_001_01_clothb_1_cmask.tex.241101895
esf009_001_01_clothb_2_cmask.tex.241101895
```

The MDF identifies these as custom colour masks.

`CMASK` defines which areas of the material can be recoloured through Street Fighter 6's costume colour system.

Multiple CMASK textures can be used by the same costume.

They work together with the character's **CMD / CostumeMaterialData** files.

In simple terms:

```text
CMASK
   ↓
Defines which parts can change colour
   ↓
CMD
   ↓
Defines the colours used for each colour slot
```

Costume recolouring is one of the easiest and most common forms of SF6 character modding.

---

### `DMASK` / `DMGMASK` — Battle Damage Mask

Damage masks are used by Street Fighter 6's battle-damage system.

They control where progressive battle effects can appear on the character during a match.

These can include:

- Dirt
- Bruising
- Damage colouring
- Progressive battle wear

The MDF normally exposes these through a:

```text
DamageMask
```

texture binding.

---

### `ATOS`

The MDF identifies ATOS textures through bindings such as:

```text
AlphaTranslucentOcclusionSSSMap
```

ATOS is a packed material texture used for several surface properties including:

- Alpha
- Translucency
- Occlusion
- Subsurface / SSS information

Because material setups can vary, checking the original texture channels together with the MDF is recommended before modifying one.

---

### `CWMASK`

Example:

```text
esf009_001_01_costume_cwmask.tex.241101895
```

`CWMASK` is another costume-related mask used by the material system.

Its exact use can depend on the costume and shader setup, so the corresponding MDF should be checked when working with it.

---

## MDF — Material Definition

Character MDF files commonly use:

```text
.mdf2.31
```

For example:

```text
esf009_001_01_v00.mdf2.31
```

The MDF is one of the most important files for advanced character modding.

It connects the mesh to:

- Material parts
- Texture paths
- Shader types
- Shader flags
- Material parameters

A costume body can contain many separate materials for different parts of the outfit.

Examples may include:

```text
esf_Body00
esf_Cloth_Leotard
esf_Cloth_Beret
esf_Cloth_Boots
esf_Cloth_Emblem
esf_Cloth_Gauntlet
esf_Cloth_Pouch
```

### When Do You Need to Edit the MDF?

For a simple texture replacement using the **same filename and path**, the MDF normally does not need to be changed.

MDF editing becomes important when you want to:

- Rename a texture
- Redirect a material to a different texture
- Use textures not originally assigned to that material
- Use a different material or shader setup
- Change material flags
- Change material parameters
- Change transparency behaviour
- Change two-sided rendering
- Add or change emissive behaviour
- Change how costume colours are handled
- Redirect materials for custom meshes or UV layouts

Increasing the resolution of an existing texture does **not by itself** require an MDF edit if the original texture path and material binding remain unchanged.

### MDF Texture Bindings

The **Textures** section in REasy shows which texture is assigned to each material function.

Examples include:

```text
BaseDielectricMap
NormalRoughnessCavityMap
AlphaTranslucentOcclusionSSSMap
CustomizeColor_Mask
DamageMask
BodyMuscle_Mask
```

This makes the MDF one of the best places to check when you are unsure what a particular texture does.

It is also how experienced modders can use completely custom texture filenames: the MDF is changed to reference the new texture path.

### MDF Material Flags

The MDF also contains flags affecting how materials are rendered.

Examples include:

```text
AlphaUsed
AlphaMaskUsed
AlphaTestEnable
TwoSideEnable
ForcedTwoSideEnable
EmissiveUsed
ShadowCastDisable
SSSProfileUsed
NoRayTracing
ForwardPrepassEnabled
```

These can be important when creating or modifying:

- Transparent materials
- Cut-out materials
- Double-sided cloth
- Emissive parts
- Skin
- Hair
- Special costume effects

### MDF Parameters

The **Parameters** section contains shader and material values.

Examples include:

```text
BaseColor

CustomizeColor_0
CustomizeColor_1
CustomizeColor_2
CustomizeColor_3

DamageColor_0
DamageColor_1
DamageColor_2

Character_LightParam

AfterImage_BaseColor
AfterImage_EmissiveColor

Emit_BaseColor
Emit_Color
```

These can affect:

- Base material colour
- Costume colours
- Battle damage
- Character lighting
- Emissive effects
- Afterimages
- Other shader behaviour

---

## CMD — Costume Material Data

CMD files are `.user.2` files containing costume colour configuration.

For example:

```text
esf009_001_cmd_001.user.2
esf009_001_cmd_002.user.2
esf009_001_cmd_003.user.2
...
esf009_001_cmd_010.user.2
```

Each file represents one costume colour slot.

For example:

```text
esf009_001_cmd_005.user.2
```

can be read as:

```text
esf009 = Cammy
001    = C1
005    = Colour 05
```

REasy exposes the `CostumeMaterialData` structure, allowing costume colours and related material settings to be edited.

---

## Chain — Character Physics

Chain files commonly use:

```text
.chain.52
```

For example:

```text
esf009_001_01_chain.chain.52
```

Chain data controls much of the character's **secondary motion and physics**.

This can include:

- Hair movement
- Clothing movement
- Belts and straps
- Accessories
- Loose costume pieces
- Body secondary motion
- Breast physics
- Butt / body jiggle
- Other physics-driven character parts

A costume may use separate chain data for the body, hair or individual costume components.

When swapping or replacing character parts, the corresponding chain data may also need to be changed so the new model uses the correct physics.

---

## `product/charparam/`

Character scene files beneath:

```text
product/charparam/
```

connect many of the fighter's assets together.

An important example is:

```text
esf001v00.scn.20
```

For visual character modding, one of the most useful areas inside the scene is the **FighterVisualHolder**.

### Body, Head and Hair References

The FighterVisualHolder identifies resources used for model parts such as:

```text
Body
Head
Hair
Bone
```

Each part can reference its own:

```text
Mesh
MDF
Joint Constraints
Chain / Physics
AO Geometry
Havok Cloth
```

For example:

```text
Body
Product/Model/esf/esf001/001/01/esf001_001_01.mesh
Product/Model/esf/esf001/001/01/esf001_001_01_v00.mdf2

Head
Product/Model/esf/esf001/001/00/esf001_001_00.mesh
Product/Model/esf/esf001/001/00/esf001_001_00_v00.mdf2

Hair
Product/Model/esf/esf001/001/02/esf001_001_02.mesh
Product/Model/esf/esf001/001/02/esf001_001_02_v00.mdf2
```

This is particularly useful for:

- Swapping hairstyles between outfits
- Replacing a head
- Redirecting a body to another mesh
- Removing a costume part
- Mixing model parts from different outfits
- Redirecting MDF files
- Redirecting physics data

Rather than replacing the original asset itself, the character scene can sometimes be edited to point the model part to a different resource.

### Footwear / Footstep Type

The character visual configuration also contains:

```text
soundEquipFootType
```

Observed values include:

```text
None
Boots
Shoes
Geta
Sandal
```

This is useful when a costume mod changes the fighter's footwear.

For example, changing boots to sandals or bare feet can also be accompanied by changing the footstep type rather than retaining the original footwear sound.

---

## Streaming Character Assets

Streaming character assets are found under:

```text
streaming/product/model/esf/
```

These files are extremely important for character and costume texture modding.

For many character textures, the files under the **streaming** path contain the **full-resolution texture** used by the game.

Typical streaming textures include high-resolution:

- Body textures
- Clothing textures
- Hair textures
- Costume masks
- Normal and material maps

For texture replacement work, the normal workflow is to edit the **full-resolution streaming texture first**.

For example:

```text
streaming/product/model/esf/esf009/001/...
```

Once the high-resolution texture is complete, a reduced-resolution version can then be created for the corresponding asset under:

```text
product/model/esf/
```

So for character texture mods, both locations are important:

```text
streaming/product/model/esf/
    ↓
Full-resolution texture

product/model/esf/
    ↓
Reduced-resolution / non-streaming texture
```

A typical texture workflow is therefore:

1. Extract and edit the full-resolution texture from `streaming/product/model/esf/`.
2. Save the finished high-resolution replacement.
3. Downsize the finished texture as required.
4. Replace the matching lower-resolution texture under `product/model/esf/`.

Editing only the `product` version can leave the game using the unchanged high-resolution streaming texture.

Always check whether a matching texture exists under:

```text
streaming/product/model/esf/
```

before considering a character texture replacement complete.

</details>

<details>
<summary><strong>Audio Modding</strong></summary>

<br>

Audio modding is another major area of Street Fighter 6 modding.

The most important locations are:

```text
product/sound/resource/
product/sound/wwise/
streaming/product/sound/wwise/
product/message/sound/
product/gui/data/musicplayer_logo/
```

These folders contain the sound-bank logic, audio media, music metadata and artwork used by the game's audio systems.

---

## Important Audio File Types

| File Type | Purpose |
|---|---|
| `.sbnk.1.x64` | Wwise sound-bank logic, events, actions and playback structure |
| `.spck.1.x64` | Wwise sound packs containing audio media |
| `.msg.21` | Text and localisation, including music titles, artists and album / series names |

REasy 0.7.6 includes dedicated sound-modding tools for supported Street Fighter 6 audio files.

---

## Sound Banks and Sound Packs

The two most important file types for normal audio replacement are:

```text
.sbnk.1.x64
.spck.1.x64
```

A simple way to think of them is:

```text
SBNK
    = Logic

SPCK
    = Audio
```

The `.sbnk` describes how the game uses the sound.

This can include:

- Events
- Actions
- Music Switches
- Music Segments
- Music Tracks
- Audio Sources
- Source IDs
- Playback routing
- Loop behaviour
- Transitions
- Dynamic music states

The `.spck` contains the actual audio media referenced by those Source IDs.

The relationship is generally:

```text
Event
   ↓
Action
   ↓
Music / Sound Object
   ↓
Source ID
   ↓
SPCK
   ↓
Audio
```

REasy can follow these relationships and, where supported, open the matching sound bank or sound pack directly.

---

## Source IDs

Audio stored inside a sound pack is referenced using a **Source ID**.

When a `.spck` is opened in REasy, the Sound Modding editor can show:

- Source ID
- Duration
- Audio format
- Which bank / event uses the source
- Preview
- Replace Audio
- Export WEM
- Export WAV
- Loop / Marker information

For example, a sound pack may contain several audio sources while the corresponding `.sbnk` defines where and how each source is played.

This means that when researching an unknown sound, the **Source ID is often the link between the bank logic and the actual audio**.

---

## `product/sound/wwise/`

Many Street Fighter 6 Wwise banks and sound packs are stored under:

```text
product/sound/wwise/
```

This includes music used by systems such as:

- Battle BGM
- Jukebox
- Music Player
- Preview tracks
- Other game audio

Both `.sbnk` and `.spck` files can be present in this folder.

---

# Example: Cap-Jams Album

A useful example is the **Cap-Jams** album.

The battle replacement tracks use filenames such as:

```text
bgm_battle_replase_070017001.sbnk.1.x64
bgm_battle_replase_070017002.sbnk.1.x64
bgm_battle_replase_070017003.sbnk.1.x64
...
bgm_battle_replase_070017011.sbnk.1.x64
```

There are **11 tracks** in this set.

Matching sound packs use the same base name:

```text
bgm_battle_replase_070017001.spck.1.x64
bgm_battle_replase_070017002.spck.1.x64
...
bgm_battle_replase_070017011.spck.1.x64
```

So a typical pair is:

```text
bgm_battle_replase_070017001.sbnk.1.x64
bgm_battle_replase_070017001.spck.1.x64
```

The bank contains the playback logic while the sound pack contains the audio media.

---

## Jukebox Tracks

The same album also has Jukebox entries.

For example:

```text
bgm_jukebox_0017_001.sbnk.1.x64
bgm_jukebox_0017_001.spck.1.x64
```

The numbering continues through the tracks in the album:

```text
bgm_jukebox_0017_001
bgm_jukebox_0017_002
bgm_jukebox_0017_003
...
bgm_jukebox_0017_011
```

---

## Jukebox Preview Tracks

Jukebox music can also have separate preview audio.

For example:

```text
bgm_jukebox_0017_001_preview.sbnk.1.x64
bgm_jukebox_0017_001_preview.spck.1.x64

bgm_jukebox_0017_001.sbnk.1.x64
bgm_jukebox_0017_001.spck.1.x64
```

This means one Jukebox track may have both:

```text
Preview
    ↓
bgm_jukebox_0017_001_preview

Full Track
    ↓
bgm_jukebox_0017_001
```

When replacing a Jukebox track, check whether a matching `_preview` version also exists.

Otherwise the Jukebox preview may continue playing the original music even though the full track has been replaced.

---

## Replacing Audio in REasy

REasy's Sound Modding editor can display the audio sources contained in a sound pack.

For a supported source, REasy provides options including:

```text
Preview
Replace Audio
Loop / Markers
Export WEM
Export WAV
Bulk Replace
Export All
```

When replacing audio, REasy can resolve the corresponding Source ID and associated bank / pack relationships.

For straightforward music replacements, keeping the existing:

- Event IDs
- Source IDs
- Bank structure
- Music structure

is usually easier than rebuilding the logic from scratch.

More advanced editing can modify the `.sbnk` itself.

---

## Dynamic Music and Bank Logic

Street Fighter 6 music can use dynamic Wwise structures rather than simply playing one flat audio file.

A sound bank can contain objects such as:

```text
Event
Action
Music Switch
Music Segment
Music Track
Audio Source
```

This allows music to respond to gameplay conditions and switch between different parts of a track.

For example, a battle BGM may contain several:

```text
Music Segments
Music Tracks
Audio Sources
```

connected through one event.

Editing this structure can change:

- Which audio source is used
- Track duration
- Segment duration
- Loop points
- Transitions
- Dynamic playback behaviour
- How different parts of a track connect

For a simple audio replacement, it is normally best to retain the existing bank structure and replace the referenced audio source.

More advanced sound-bank editing will be covered separately.

---

## `streaming/product/sound/wwise/`

Additional Street Fighter 6 audio is stored under:

```text
streaming/product/sound/wwise/
```

Streaming sound packs are used for audio that the game loads or streams as required.

This can include larger audio assets such as:

- Music
- Character voice
- Stage audio
- Announcer audio
- Longer sound effects
- Other streamed media

When locating audio, check both:

```text
product/sound/wwise/
```

and:

```text
streaming/product/sound/wwise/
```

because the bank logic and actual media may not always be located in the same part of the file structure.

---

# Music Titles, Artists and Album Names

Changing the audio itself does not automatically change the text displayed in Street Fighter 6's music menus.

Music metadata is stored under:

```text
product/message/sound/
```

Important files include:

```text
bgmartistmessage.msg.21
bgmseriesmessage.msg.21
bgmtitlemessage.msg.21
```

These control information such as:

| File | Typical Use |
|---|---|
| `bgmartistmessage.msg.21` | Artist names |
| `bgmseriesmessage.msg.21` | Album / series names |
| `bgmtitlemessage.msg.21` | Track titles |

REasy's MSG editor can be used to search and edit these entries.

So a complete custom music replacement may involve:

```text
Audio
    ↓
product/sound/wwise/
or
streaming/product/sound/wwise/

Track / Artist / Album Text
    ↓
product/message/sound/
```

---

# Music Player Album Artwork

Music Player artwork is stored separately under the GUI data.

Large artwork is found under:

```text
product/gui/data/musicplayer_logo/texture_l/
```

For the Cap-Jams album:

```text
tex_bgmsr017_iam.tex.241101895
```

Smaller artwork is stored under:

```text
product/gui/data/musicplayer_logo/texture_s/
```

For example:

```text
tex_bgmsr017_s_iam.tex.241101895
```

So the same music release can involve several different parts of the game:

```text
Sound Bank / Logic
    ↓
product/sound/wwise/

Audio
    ↓
product/sound/wwise/
or
streaming/product/sound/wwise/

Track / Artist / Album Text
    ↓
product/message/sound/

Large Album Artwork
    ↓
product/gui/data/musicplayer_logo/texture_l/

Small Album Artwork
    ↓
product/gui/data/musicplayer_logo/texture_s/
```

---

## Example: Replacing a Cap-Jams Track

For example, replacing:

```text
bgm_jukebox_0017_001
```

may involve the following files.

### Main Track

```text
product/sound/wwise/
bgm_jukebox_0017_001.sbnk.1.x64
bgm_jukebox_0017_001.spck.1.x64
```

### Preview

```text
product/sound/wwise/
bgm_jukebox_0017_001_preview.sbnk.1.x64
bgm_jukebox_0017_001_preview.spck.1.x64
```

### Music Metadata

```text
product/message/sound/
bgmartistmessage.msg.21
bgmseriesmessage.msg.21
bgmtitlemessage.msg.21
```

### Album Artwork

```text
product/gui/data/musicplayer_logo/texture_l/
tex_bgmsr017_iam.tex.241101895
```

and:

```text
product/gui/data/musicplayer_logo/texture_s/
tex_bgmsr017_s_iam.tex.241101895
```

This allows a mod to replace not just the audio, but also its:

- Preview
- Track title
- Artist
- Album / series name
- Large album artwork
- Small album artwork

---

## Typical Music Replacement Workflow

A complete music replacement can therefore follow this general workflow:

1. Locate the relevant `.sbnk.1.x64`.
2. Open it in REasy and identify the event / Source ID used by the track.
3. Open the matching `.spck.1.x64`.
4. Preview the existing audio to confirm the correct source.
5. Replace the audio.
6. Check whether a separate `_preview` bank and sound pack also need replacing.
7. If required, edit the track title in `bgmtitlemessage.msg.21`.
8. If required, edit the artist in `bgmartistmessage.msg.21`.
9. If required, edit the album / series in `bgmseriesmessage.msg.21`.
10. Replace the large and small Music Player artwork if creating a complete custom album replacement.
11. Test both the full track and preview in game.

For a simple replacement, keeping the original bank structure and Source IDs is usually the safest approach.

</details>

<details>
<summary><strong>UI/HUD Modding</strong></summary>

<br>

UI modding is another major area of Street Fighter 6 modding.

Most commonly edited UI assets are found beneath:

```text
product/gui/
```

One of the most important locations is:

```text
product/gui/data/
```

This folder contains a large amount of the artwork and interface data used throughout:

- Fighting Ground
- Character Select
- Battle HUD
- Battle Hub
- CFN
- World Tour
- Avatar Arcade
- Training
- Tutorials
- Music Player
- Rankings
- Menus
- Online modes
- In-match HUD elements

---

## Important UI File Types

| File Type | Purpose |
|---|---|
| `.tex.241101895` | UI artwork, portraits, icons, logos, masks and other interface textures |
| `.pfb.17` | UI Prefabs; often contain or reference textures and other interface resources |
| `.uvs.7` | UI animation / UV layout data; can control how regions of a texture are displayed or animated |
| `.user.2` | Structured UI and menu configuration data |
| `.gui` | GUI layout and behaviour data |

REasy can open and edit many of the file types used by the Street Fighter 6 interface.

A dedicated guide for `.uvs.7` files and their practical uses can be added separately.

---

# `product/gui/data/`

This is one of the most useful folders when searching for UI artwork.

It contains many clearly named subfolders including:

```text
area_image
avatarcreate_thumbnail
battlehub_image
battlehub_movie
battlehub_screen
battlehub_walltexture
battletour_banner
brand_logo
cfn
character_image
commentary_image
controller
dialog
emote_image
endcard_other
endcard_past
equip_thumbnail
fgcharacterguide
fgtraining
fgtutorial
historymovie_logo
item_thumbnail
musicplayer_logo
nationalflag
newchallenger
npc_face_thumbnail
photomode
rank
shop_banner
stamp
theme
ticker
tips
title
tournamentlogo
```

Not every folder is equally important for normal UI modding, but the folder names often give a good indication of where a particular interface asset is used.

---

## `area_image` — Stage Artwork

Stage-related UI images are stored under:

```text
product/gui/data/area_image/
```

These include artwork and thumbnails representing stages and locations in various menus.

The Stage Codes table at the top of this reference can help when identifying stage-specific assets.

---

## `avatarcreate_thumbnail`

Avatar creation thumbnails are stored beneath:

```text
product/gui/data/avatarcreate_thumbnail/
```

These are mainly images used by the Avatar Creation interface.

This folder is less commonly modified than the main character, Battle HUD or match UI folders.

---

# `character_image` — Character UI Artwork

One of the most important UI folders is:

```text
product/gui/data/character_image/
```

Character folders use a three-digit version of the normal `esf` character ID.

For example:

```text
product/gui/data/character_image/001/
```

contains UI artwork for:

```text
esf001 = Ryu
```

The same numbering continues for the other fighters.

The Character Codes table at the top of this reference can therefore also be used when navigating this folder.

---

## Avatar Arcade / `avatarvs`

Within a character folder, the `avatarvs` section contains the image used when an avatar is fighting with that character's style in **Avatar Arcade**.

For Ryu:

```text
product/gui/data/character_image/001/avatarvs/
```

An example texture is:

```text
tex_avatarvs_esf001_alba.tex.241101895
```

This artwork is shown for an avatar using Ryu's fighting style rather than displaying Ryu's normal character portrait.

---

## `battlehud` — In-Match Character Portraits

Battle HUD character portraits are stored beneath:

```text
product/gui/data/character_image/001/battlehud/
```

for Ryu, with the equivalent numbered folder used for other characters.

Typical files include:

```text
tex_001_1p_iam.tex.241101895
tex_001_2p_iam.tex.241101895

tex_battlehud_001_1p_iam.tex.241101895
tex_battlehud_001_2p_iam.tex.241101895
```

These provide the **Player 1 and Player 2 portraits** used during a match.

The separate P1 / P2 artwork allows the game to use different orientation or colour treatment depending on which side the character occupies.

---

# Character Select Portraits

Character Select artwork is stored inside each character's `character_image` folder.

There is an important naming quirk in the game files.

For character IDs up to `029`, Capcom used the misspelled folder name:

```text
caracterselect
```

For later characters `030` to `033`, the folder name is correctly spelled:

```text
characterselect
```

This is important when searching paths because both spellings are present in the game.

For example, Ryu uses:

```text
product/gui/data/character_image/001/caracterselect/
```

while later characters use:

```text
product/gui/data/character_image/030/characterselect/
```

---

## Character Select Texture Variants

Each character normally has six Character Select portrait textures.

For Ryu:

```text
tex_esf001_face_l_l_iam.tex.241101895
tex_esf001_face_l_m_iam.tex.241101895
tex_esf001_face_l_s_iam.tex.241101895

tex_esf001_face_r_l_iam.tex.241101895
tex_esf001_face_r_m_iam.tex.241101895
tex_esf001_face_r_s_iam.tex.241101895
```

The filename identifies both the **side** and **size**.

### Side

```text
l = Left
r = Right
```

### Size

```text
l = Large
m = Medium
s = Small
```

So:

```text
tex_esf001_face_l_l_iam.tex
```

can be read as:

```text
esf001 = Ryu
face   = Character portrait
l      = Left side
l      = Large
```

while:

```text
tex_esf001_face_r_s_iam.tex
```

is:

```text
Ryu
Right side
Small portrait
```

These variants allow different parts of the interface to use the correct orientation and resolution.

---

# `newchallenger` — Here Comes a New Challenger

Another popular character UI folder is:

```text
product/gui/data/character_image/001/new_challenger/
```

or the equivalent numbered character folder.

This contains artwork used for the **Here Comes a New Challenger** sequence.

Examples for Ryu include:

```text
tex_nextchallenger_esf001_00_00_iam.tex.241101895
tex_nextchallenger_esf001_00_01_iam.tex.241101895
tex_nextchallenger_esf001_00_02_iam.tex.241101895

tex_nextchallenger_esf001_01_iam.tex.241101895
tex_nextchallenger_esf001_02_iam.tex.241101895
tex_nextchallenger_esf001_03_iam.tex.241101895
...
```

A character can have many individual textures used by the full New Challenger presentation.

---

# Other Character UI Data

The `character_image` folder contains many other character-specific interface resources.

Depending on the character, these can include areas such as:

```text
avatarvs
battlehud
caracterselect / characterselect
comicdemo
command_resource
endcard
levelup
new_challenger
online_shop
pub
```

These folders cover artwork used across different game modes rather than one single character portrait system.

---

# `product/gui/es/` — In-Match HUD

Outside of `character_image`, another extremely important location is:

```text
product/gui/es/
```

`ES` is used for much of the **in-match interface**.

This contains UI assets used during actual battles, including elements such as:

- Vital / Health Gauge
- Drive Gauge
- Super Art / Critical Art gauges
- Hit counters
- Combo information
- Round information
- Win indicators
- Player information
- Match status elements
- Other Battle HUD graphics

For modders changing the appearance of the Fighting Ground match interface, `product/gui/es/` is one of the first places to investigate.

---

# UI Textures and Prefabs

Although `.tex` files contain most of the visible artwork, some UI systems use Prefabs to reference those textures.

A UI Prefab may contain:

```text
.pfb.17
```

and can act as a holder for one or more interface resources.

This can be useful when you want to change **which texture the interface uses** rather than simply replacing the original texture file.

In simple terms:

```text
PFB
   ↓
References UI resources
   ↓
TEX
   ↓
Visible artwork
```

This makes Prefab editing useful for more advanced UI swaps and redirects.

---

# UVS — UI Animation and Texture Layout

Street Fighter 6 also uses:

```text
.uvs.7
```

files throughout its interface.

These can be used for UI animation and for defining how different regions of a texture are displayed.

A single texture may contain several interface elements, while the UVS data determines which section is shown or animated.

Because UVS editing is more specialised, practical `.uvs.7` workflows will be covered in a separate guide.

---

## Useful Starting Points for UI Modding

For most UI mods, these are good places to begin:

```text
Character portraits / artwork
    ↓
product/gui/data/character_image/

Stage artwork
    ↓
product/gui/data/area_image/

In-match Battle HUD
    ↓
product/gui/es/

Music Player artwork
    ↓
product/gui/data/musicplayer_logo/

General menu and mode artwork
    ↓
product/gui/data/
```

The best approach is usually to identify **where the artwork appears in the game first**, then search the corresponding GUI folder for the relevant texture, Prefab or UVS file.

</details>

---

## New to REasy?

If you're new to REasy, these guides cover the basic setup and search tools used throughout this reference.

- [Getting Started: Setup REasy](../../REasy-GUI/Getting-Started.md)  
  Download or build REasy, configure the game version and basic settings, and learn the main starting workflow.

- [Using Search and Regex](../../REasy-GUI/Using-Search-and-Regex.md)  
  Learn how to find files, character IDs, paths and file types using REasy's search fields and regular expressions.


[⬅️ Back to Games](../README.md) | [⬆️ Top](#street-fighter-6-file-structure-reference)
