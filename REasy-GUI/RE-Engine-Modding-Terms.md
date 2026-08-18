[⬅️ Back to REasy GUI Documentation](./README.md)

# Common RE Engine Modding Terms

This page explains common RE Engine modding terms and concepts used throughout REasy and the wider RE Engine modding community.

It is intended as a quick-reference guide for users who are unfamiliar with RE Engine terminology or general modding terms.

---

## What is a PAK File?

A PAK file is a packed, protected archive used by RE Engine games to store most of the game's assets.

These are normally some of the largest files inside the game folder.

Depending on the title, a game can use multiple PAK files for the base game, updates, DLC or other content.

The contents of a PAK are organised using game file paths. Because the archive entries are identified internally by hashes, a `.list` file is used to resolve those hashes back into readable paths so modders can browse and extract the assets.

Assets commonly found inside PAK files include:

- Textures
- Models
- Audio
- Animations
- Game data
- UI assets
- Other game resources

REasy can browse and extract supported PAK archives without requiring the entire archive to be unpacked first.

For more information, see:

- [PAK Browser](./PAK-Browser.md)

---

## What is a `.list` File?

RE Engine PAK archives identify files using hashes.

A `.list` file contains known game file paths which can be converted to the corresponding hashes and matched against entries stored inside the PAK archives.

This allows REasy to display readable paths such as:

```text
natives/stm/product/model/...
```

instead of leaving the entry unresolved.

REasy comes bundled with `.list` files for its supported games.

These can be found under:

```text
REasy\resources\data\lists
```

<p align="left">
  <img src="../media/REeasy_Tool_PAK_Browser_Select_list.jpg"><br>
  <em>Captured in REasy 0.7.6</em>
</p>

A `.list` file can also be opened with any text editor.

Each known file path is stored on its own line.

<details>
<summary><strong>Example `.list` entries</strong></summary>

<br>

```text
natives/stm/product/model/esf/esf029/004/esf029_004_shape.user.2
natives/stm/product/model/esf/esf029/004/pubbuttleset_esf029_004_01_drv_bs1.jcns.22
natives/stm/product/model/esf/esf029/004/pubbuttleset_esf029_004_01_drv_rpy.jcns.22
natives/stm/product/model/esf/esf029/004/pubbuttleset_esf029_004_01_drv_skin.jcns.22
natives/stm/product/model/esf/esf029/005/00/esf029_005_00.mesh.230110883
natives/stm/product/model/esf/esf029/005/00/esf029_005_00_v00.mdf2.31
natives/stm/product/model/esf/esf029/005/01/esf029_005_01.mesh.230110883
natives/stm/product/model/esf/esf029/005/01/esf029_005_01_clotha_1_cmask.tex.241101895
natives/stm/product/model/esf/esf029/005/01/esf029_005_01_clotha_albd.tex.241101895
natives/stm/product/model/esf/esf029/005/01/esf029_005_01_clotha_atos.tex.241101895
natives/stm/product/model/esf/esf029/005/01/esf029_005_01_clotha_blend_msk4.tex.241101895
natives/stm/product/model/esf/esf029/005/01/esf029_005_01_clotha_blenda_nrrc.tex.241101895
natives/stm/product/model/esf/esf029/005/01/esf029_005_01_clotha_blendc_nrrc.tex.241101895
natives/stm/product/model/esf/esf029/005/01/esf029_005_01_clotha_blendd_nrrc.tex.241101895
natives/stm/product/model/esf/esf029/005/01/esf029_005_01_clotha_cwmask.tex.241101895
natives/stm/product/model/esf/esf029/005/01/esf029_005_01_clotha_dmask.tex.241101895
natives/stm/product/model/esf/esf029/005/01/esf029_005_01_clotha_nrrc.tex.241101895
natives/stm/product/model/esf/esf029/005/01/esf029_005_01_clothb_1_cmask.tex.241101895
natives/stm/product/model/esf/esf029/005/01/esf029_005_01_clothb_albd.tex.241101895
natives/stm/product/model/esf/esf029/005/01/esf029_005_01_clothb_atos.tex.241101895
natives/stm/product/model/esf/esf029/005/01/esf029_005_01_clothb_blend_msk4.tex.241101895
natives/stm/product/model/esf/esf029/005/01/esf029_005_01_clothb_blenda_nrrc.tex.241101895
natives/stm/product/model/esf/esf029/005/01/esf029_005_01_clothb_nrrc.tex.241101895
natives/stm/product/model/esf/esf029/005/01/esf029_005_01_v00.mdf2.31
natives/stm/product/model/esf/esf029/005/esf029_005_01_aogeo.user.2
natives/stm/product/model/esf/esf029/005/esf029_005_01_chain.chain.52
natives/stm/product/model/esf/esf029/005/esf029_005_01_chain.user.2
natives/stm/product/model/esf/esf029/005/esf029_005_01_drv_aim.jcns.22
natives/stm/product/model/esf/esf029/005/esf029_005_01_drv_point.jcns.22
natives/stm/product/model/esf/esf029/005/esf029_005_01_drv_rpy.jcns.22
natives/stm/product/model/esf/esf029/005/esf029_005_01_jcs.user.2
natives/stm/product/model/esf/esf029/005/esf029_005_bsd.user.2
natives/stm/product/model/esf/esf029/005/esf029_005_ccvd.user.2
natives/stm/product/model/esf/esf029/005/esf029_005_cmd_000.user.2
natives/stm/product/model/esf/esf029/005/esf029_005_cmd_001.user.2
natives/stm/product/model/esf/esf029/005/esf029_005_cmd_002.user.2
natives/stm/product/model/esf/esf029/005/esf029_005_drv_bs1.jcns.22
natives/stm/product/model/esf/esf029/005/esf029_005_msl.user.2
natives/stm/product/model/esf/esf029/005/esf029_005_nsd.user.2
natives/stm/product/model/esf/esf029/005/esf029_005_shape.user.2
natives/stm/product/model/esf/esf029/005/pubbuttleset_esf029_005_01_drv_bs1.jcns.22
```

</details>

### Unknown PAK Entries

If REasy detects an entry inside a PAK but the corresponding path is not known by the loaded `.list`, it can be displayed beneath:

```text
_Unknown
```

For example:

```text
_Unknown (423)
```

means that 423 PAK entries were found which could not currently be resolved to known paths.

A `.list` does not necessarily contain every path used by a game, so lists can continue to improve over time as new paths are discovered.

For more information, see:

- [PAK Browser](./PAK-Browser.md)
- [File List Generator](./File-List-Generator.md)

---

## What is RSZ?

RSZ is the structured object-data system used by RE Engine for many game files.

Common RSZ-based file types include:

```text
.user
.pfb
.scn
```

These files can contain structured objects, arrays, references, components and game-specific settings.

Examples include:

- Character configuration
- Stage setup
- GameObjects
- Prefabs
- UI configuration
- Camera data
- Gameplay settings

REasy uses a game-specific RSZ `.json` template to interpret the numeric type IDs and field layouts stored inside these files.

This allows REasy to display readable information such as:

- Class names
- Field names
- Data types
- Arrays
- Object references
- Values

instead of only showing raw numeric data.

---

## RSZ Templates / JSON Dumps

REasy comes bundled with RSZ `.json` files for its supported games.

These act as templates describing the classes, fields and data types available in that version of the game.

<details>
<summary><strong>Example RSZ JSON entry</strong></summary>

<br>

A small section of an RSZ JSON can look like:

```json
"1003863": {
    "crc": "bbee45b0",
    "fields": [
        {
            "align": 4,
            "array": false,
            "name": "PoolNameHash",
            "native": false,
            "original_type": "System.UInt32",
            "size": 4,
            "type": "U32"
        }
    ],
    "name": "app.AdaptiveRTTAllocator",
    "parent": "System.Object"
}
```

</details>

In this example, the template identifies:

```text
Type ID
Class Name
Parent Class
Field Name
Field Type
Field Size
Array / non-array state
```

REasy uses this information to build the editable RSZ structure shown in the editor.

The RSZ templates are updated alongside REasy releases and when supported games receive updates that change their RSZ structures.

---

## REasy RSZ Tools

REasy includes several tools for working with RSZ-based files.

### RSZ Editor

The main RSZ Editor is used for opening and editing:

```text
SCN
PFB
USER
```

files.

For more information, see:

- [RSZ Editor (PFB / SCN / User)](./RSZ/RSZ-Editor.md)

### RSZ File Diff Viewer

The RSZ File Diff Viewer can compare two RSZ files and highlight differences between their structures and values.

> As of REasy 0.7.6, this tool is still considered highly experimental.

### Outdated Files Detector

The Outdated Files Detector can help identify RSZ files that are incompatible with the currently selected RSZ template.

This is useful after a game update, where an older mod may still contain RSZ data based on a previous game structure.

When checking older mods, use the latest RSZ `.json` for the current game version.

### CSV Extractor (RSZ Data Matcher)

Introduced in REasy 0.7.6, the **CSV Extractor (RSZ Data Matcher)** can scan RSZ files and extract selected matching data into a CSV file.

It can work with:

```text
SCN
PFB
USER
```

files and can match fields between two sets of RSZ data using configurable rules.

This can be useful for analysing large groups of files and exporting selected values into a spreadsheet-friendly format.

---

## What is CSV?

CSV stands for **Comma-Separated Values**.

It is a simple text format used to store table-like data in rows and columns.

CSV files can be opened in applications such as:

- Microsoft Excel
- LibreOffice Calc
- Google Sheets
- Text editors

REasy uses CSV export in tools such as the RSZ Data Matcher so extracted game data can be reviewed or compared more easily.

---

## What is a Scene?

A scene is a collection of GameObjects, components and references used to build or configure part of the game.

RE Engine scene files commonly use:

```text
.scn
```

A scene can contain things such as:

- Stage objects
- Character setup
- Cameras
- Lighting
- Effects
- Collision-related references
- Prefabs
- Gameplay systems

REasy can expose these structures through the RSZ Editor.

---

## What is a Prefab?

A prefab is a reusable object or group of objects referenced by other game data.

RE Engine prefab files commonly use:

```text
.pfb
```

A prefab can contain:

- GameObjects
- Components
- Resource references
- UI elements
- Character-related setup
- Reusable gameplay objects

Prefabs are often referenced by scenes and other RSZ files.

---

## What is a GameObject?

A GameObject is a basic object used inside RE Engine scenes and prefabs.

A GameObject can contain:

- A name
- A GUID
- Transform data
- Components
- Child objects
- References to resources or other systems

Examples include:

- Cameras
- Lights
- Stage props
- Character objects
- UI objects
- Trigger objects

REasy displays GameObjects and their components in supported RSZ files.

---

## What is a Component?

Components are the individual systems attached to a GameObject.

Examples include:

```text
via.Transform
via.Camera
via.render.Fog
via.render.MotionBlur
```

A component can contain its own fields, values and references.

The exact components available depend on the game and the type of object being edited.

---

## What is Regex?

Regex, short for **regular expression**, is a pattern-based search system.

REasy uses regex-capable search fields in several tools.

For example:

```text
\.tex(\.|$)
```

can be used to search for texture files.

Regex is not required for normal searching, but it becomes useful when searching for:

- Multiple file types
- Specific filename patterns
- Character IDs
- Versioned extensions
- Groups of related paths

For practical examples, see:

- [Using Search and Regex](./Using-Search-and-Regex.md)

---

## What is a File Version Suffix?

RE Engine files commonly include a numeric version after the extension.

For example:

```text
example.tex.241101895
example.mesh.230110883
example.mdf2.31
example.scn.20
example.pfb.17
example.user.2
```

These numbers identify the version of that RE Engine file format used by the game.

The same basic file type can use different version numbers between games or engine revisions.

Because of this, a file from one RE Engine game is not automatically compatible with another game just because the extension is the same.

For examples of common versions, see:

- [Using Search and Regex](./Using-Search-and-Regex.md)

---

## What is a Fluffy Mod Manager ZIP?

REasy projects can be exported as a ZIP structured for use with Fluffy Mod Manager.

This allows a project to be packaged with the correct folder structure so it can be installed and toggled through Fluffy.

REasy can also export supported projects as PAK files.

---

## What Does RT / non-RT Mean?

Some Resident Evil titles have both older non-Ray-Tracing builds and newer Ray-Tracing updated builds.

In REasy documentation these may be identified as:

```text
RE2
RE2RT

RE3
RE3RT

RE7
RE7RT
```

The RT and non-RT versions can use different RE Engine file versions and internal structures.

Mods made for one version may therefore require conversion before they work with the other.

---

## What is a Memory Dump?

A memory dump is a snapshot of a running program's memory.

For REasy file-list work, a memory dump can be useful because the running game may contain readable resource paths that are not easy to find elsewhere.

On Windows, a dump can be created using Task Manager:

1. Open Task Manager.
2. Find the running game process.
3. Right-click the process.
4. Choose **Create memory dump file**.
5. Note the location where Windows saves the dump.

REasy's File List Generator can analyse the dump and extract candidate resource paths.

See:

- [File List Generator](./File-List-Generator.md)

---

## What is a GUID?

A GUID is a globally unique identifier used by many RE Engine objects and references.

It commonly appears in:

- GameObjects
- Components
- Scene data
- Prefabs
- Resource references

A GUID usually looks similar to:

```text
976544d6-c971-4e08-afff-6fd4492dba13
```

REasy can display and, where appropriate, generate or edit GUID values.

---

## What is a Hash?

RE Engine uses hashes in several systems instead of storing or looking up everything by readable text.

Hashes are commonly encountered in:

- PAK file paths
- Audio events
- Trigger IDs
- Resource lookups
- Internal object identifiers

A hash converts text or other data into a numeric value.

This is why a `.list` file is useful: REasy can hash a known path and compare it with the hashed entries stored in a PAK archive.

REasy also includes a Hash Calculator under:

```text
Tools → Hash Calculator
```

for supported hash types.

---

## Related Guides

- [Getting Started: Setup REasy](./Getting-Started.md)
- [Using Search and Regex](./Using-Search-and-Regex.md)
- [PAK Browser](./PAK-Browser.md)
- [File List Generator](./File-List-Generator.md)
- [RSZ Editor (PFB / SCN / User)](./RSZ/RSZ-Editor.md)

---

[⬅️ Back to REasy GUI Documentation](./README.md) | [⬆️ Top](#common-re-engine-modding-terms)
[⬅️ Back to REasy GUI Documentation](./README.md) | [⬆️ Top](#common-re-engine-modding-terms)
