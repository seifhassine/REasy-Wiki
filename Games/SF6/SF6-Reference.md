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

---

# Common Modding Areas

<details>
<summary><strong>Character Models and Costumes</strong></summary>

<br>

Character and costume modding is one of the most common types of Street Fighter 6 modding.

The main folders used are:

```text
product/model/esf/
product/charparam/
streaming/model/esf/
```

More detail will be added here as the reference is expanded.

</details>

---

[⬅️ Back to Games](../README.md) | [⬆️ Top](#street-fighter-6-file-structure-reference)
