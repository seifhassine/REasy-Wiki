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

## What is a Scene?

A Scene is a structured collection of GameObjects, components and references used by RE Engine to build or configure part of the game.

RE Engine Scene files commonly use:

```text
.scn
```

A `.scn` file can contain many different types of data depending on its purpose.

Some scenes contain or reference visible 3D geometry, while others act mainly as containers for systems such as:

- 3D scene/ Environment objects
- Cameras
- Lighting
- Visual effects
- Sound
- Collision-related data
- NPCs
- Spawn points
- Gameplay logic
- Prefabs
- Other child scenes

REasy includes a built-in **Scene Editor** for supported `.scn` file

- Moving objects with Transform values
- Rotating and scaling objects
- Adding new GameObjects
- Removing GameObjects
- Enabling or disabling objects and components
- Editing component values
- Editing linked resource paths
- Working with child scenes
- Loading multiple scenes together

---

<details>
<summary><strong>More Details on scenes</strong></summary>
  
### Scene Hierarchies

A single area can be built from many separate `.scn` files rather than one large scene.

A useful example is the World Tour area `wtc0202` in Street Fighter 6.

The main environment scene is:

```text
product/environment/stage/scene/wtc/wtc0202/wtc0202_env.scn.20
```

This acts as a master environment scene and references the child scenes used to build the area.

Under:

```text
product/environment/stage/scene/wtc/wtc0202/area/
```

the area is divided into three main scenes:

```text
wtc0202_00.scn.20
wtc0202_01.scn.20
wtc0202_02.scn.20
```

In this example:

- `wtc0202_00` is an exterior area.
- `wtc0202_01` is another exterior area connected seamlessly to `00`.
- `wtc0202_02` is the interior cave area.

Each of these can then reference additional child scenes.

For example, `wtc0202_00` uses scene groups such as:

```text
wtc0202_00_props_dynamic.scn.20
wtc0202_00_props_manual_high.scn.20
wtc0202_00_props_manual_low.scn.20
wtc0202_00_props_static_large.scn.20
wtc0202_00_props_static_small.scn.20
```

These divide the environment into different types of objects.

For example:

```text
props_static_large
```

can contain larger static objects such as rocks or major environment props, while:

```text
props_static_small
```

contains smaller detail objects.

This allows large environments to be split into manageable groups rather than storing everything inside one Scene file.

---

### Scenes Can Contain 3D Geometry

A Scene can reference Mesh and MDF resources directly through its GameObjects and components.

For example, a `via.render.Mesh` component can reference:

```text
Product/Environment/Stage/Resource/ess/ess0000_00/ess0000_00.mesh
Product/Environment/Stage/Resource/ess/ess0000_00/ess0000_00.mdf2
```

REasy can load supported scene resources into its Scene Editor, allowing the scene to be viewed and edited in 3D.

Depending on the scene and game, this can allow modders to work with:

- 3D geometry placement
- Object transforms
- Props
- Scene hierarchy
- Child scenes
- Lighting
- VFX emitters
- NPC and dynamic-object placement
- Child scene layout
- GameObject and component settings
- Other scene-linked resources

---

### Camera Scenes

Scenes are not limited to environment geometry.

For the same `wtc0202` example, camera data is stored under:

```text
product/camera/scene/wtc/
```

with a scene such as:

```text
wtc0202_camera.scn.20
```

Camera scenes can contain detailed rendering and camera configuration.

Depending on the game, this can include:

- Field of View
- Render output
- Camera behaviour
- Tone mapping
- HDR values
- Sharpness
- Contrast
- Film grain
- Screen Space Reflections
- Fog
- Bloom
- Motion blur
- Other post-processing and rendering controls

These values are stored as components attached to GameObjects inside the Scene.

---

### Level and Control Scenes

Other Scene files can control gameplay rather than visible geometry.

For example:

```text
product/level/scene/wtc/wtc0202/control/
```

contains Scene files used for level and control data.

These can determine which NPCs, objects or other game elements are active depending on factors such as:

- Player location
- Mission state
- Current area
- Graphics settings
- Other gameplay conditions

For example, higher graphics settings can allow scenes to use more NPCs or more detailed objects than lower settings.

---

### Spawn and Position Data

Scene files can also define important gameplay positions.

For example:

```text
product/level/scene/wtc/wtc0202/level/point_base.scn.20
```

can contain components defining locations used by the game, such as where the player loads or spawns.

---

### Lighting Scenes

Lighting data for an area can be stored in separate Scene files.

For example:

```text
product/light/scene/wtc/wtc0202/
```

These scenes can contain the lights used by the environment.

When loaded together with the environment scenes, they help build the complete visual appearance of the area.

---

### Sound Scenes

Sound-related Scene files can also exist separately.

For example:

```text
product/sound/sound_scene/wtc/wtc0202/
```

These contain scene-based sound setup and references used by the area.

---

### VFX Scenes

Visual effects can also be stored in separate Scene files.

For example:

```text
product/vfx/environment/wtm/wtc/wtc0202/
```

These can contain VFX-related GameObjects and components for effects such as:

- Waterfalls
- Environmental particles
- Atmospheric effects
- Dynamic effects
- Other scene-based VFX

The Scene can contain the position and configuration of the effect while the actual VFX resources are referenced separately.

---

### Building a Complete Scene in REasy

A complete environment may therefore be spread across many Scene files:

```text
Environment
Camera
Level
Control
Lighting
Sound
VFX
Props
```

REasy can add multiple supported Scene files into the Scene Viewer.

This allows related scenes to be viewed together and can make it possible to inspect or edit things such as:

- 3D geometry placement
- Props
- Lighting positions
- VFX emitter positions
- NPC and dynamic-object placement
- Child scene layout
- Other scene-linked resources

For example, a World Tour environment can be assembled from its environment, prop, lighting, sound and VFX scenes to give a much more complete representation of the area.

---

> The `wtc0202` example above demonstrates one way Street Fighter 6 structures a World Tour environment. Other RE Engine games, and even other systems within the same game, can use `.scn` files in very different ways.

</details>

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

## What Does RT / non-RT Mean?

Resident Evil 2, Resident Evil 3 and Resident Evil 7 originally released on PC without Ray Tracing.

In June 2022, Capcom released updated versions of all three games with Ray Tracing, enhanced 3D audio and other engine changes. These updates also changed some RE Engine file formats and version numbers.

Because many existing mods were created for the original versions, the modding community generally refers to the two builds as:

```text
RE2      = non-RT
RE2RT    = Ray Tracing version
RE3      = non-RT
RE3RT    = Ray Tracing version
RE7      = non-RT
RE7RT    = Ray Tracing version
```

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
