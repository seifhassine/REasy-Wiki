[⬅️ Back to REasy GUI Documentation](./README.md)

# Common RE Engine Modding Terms

This page explains common RE Engine modding terms and concepts used throughout REasy and the wider RE Engine modding community.

It is intended as a quick-reference page for users who are new to REasy or unfamiliar with RE Engine terminology.

---

## What is a PAK File?

A PAK file is an archive used by RE Engine games to store large numbers of game files.

Depending on the game, a PAK can contain:

- Textures
- Models
- Audio
- RSZ files
- UI data
- Animations
- Stage assets
- Configuration files
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
natives/stm/product/gui/...
```

instead of leaving the entry unresolved.

REasy comes bundled with `.list` files for its supported games.

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

REasy uses game-specific RSZ information to identify the classes, fields and data types stored inside these files.

For working with RSZ files, see:

- [RSZ Editor (PFB / SCN / User)](./RSZ/RSZ-Editor.md)

---

## What are RSZ Dumps?

REasy uses game-specific RSZ dumps to understand the available RSZ classes, fields, types and structures for each supported game.

These dumps are included with REasy and are normally updated alongside REasy releases or when supported games receive updates that change their RSZ structures.

They are stored under:

```text
resources/data/dumps/
```

The current dumps can also be viewed in the main REasy repository:

```text
https://github.com/seifhassine/REasy/tree/master/resources/data/dumps
```

For working with RSZ files, see:

- [RSZ Editor (PFB / SCN / User)](./RSZ/RSZ-Editor.md)

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

## What is a Resource Reference?

Many RE Engine files do not contain all of their data directly.

Instead, they reference external resources such as:

- Meshes
- Materials
- Textures
- Motion banks
- Audio
- Prefabs
- User files

For example, a character scene may reference:

```text
Product/Model/esf/esf001/001/01/esf001_001_01.mesh
```

rather than containing the mesh itself.

REasy can often display these references and open the linked resource directly.

---

## What is Streaming Data?

Some RE Engine games separate larger or higher-resolution assets into a streaming path.

A common structure is:

```text
natives/stm/product/
```

for normal game data, and:

```text
natives/stm/streaming/product/
```

for streaming assets.

Streaming data can include:

- Full-resolution textures
- Large audio files
- Other assets loaded or streamed when required

For some modding workflows, both the normal and streaming versions of an asset need to be replaced.

---

## What Does `natives/stm/` Mean?

`natives/stm/` is the common root path used by many PC RE Engine game resources.

For example:

```text
natives/stm/product/gui/
natives/stm/product/model/
natives/stm/product/sound/
```

The exact folder structure varies between games.

Some games and platforms can use different path layouts or suffixes.

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

## What is a ShortID?

ShortIDs are numeric identifiers commonly used by Wwise audio systems.

They can identify:

- Events
- Actions
- Audio objects
- Music objects
- Other Wwise resources

In audio modding, REasy can display and work with these IDs when editing supported sound banks.

A readable event name may be converted into a ShortID and stored numerically inside the bank.

---

## What is a Source ID?

A Source ID identifies an individual audio source inside a Wwise sound system.

It is commonly used to link:

```text
Sound Bank Logic
    ↓
Source ID
    ↓
Audio Media
```

REasy can display Source IDs when working with supported BNK/PCK or SBNK/SPCK audio workflows.

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

## What is a Mod Manager Path?

Most RE Engine mods recreate the same folder structure used by the game.

For example:

```text
natives/
└── stm/
    └── product/
        └── gui/
```

A mod manager such as Fluffy Mod Manager then places or redirects these replacement files when the mod is enabled.

Keeping the correct folder structure is essential because the game expects the replacement file to match the original resource path.

---

## What is a Streaming Variant?

A streaming variant is a second copy or counterpart of an asset stored in the streaming data.

For example, a texture may have:

```text
product/model/...
```

and:

```text
streaming/product/model/...
```

versions.

The streaming version is often the larger or full-resolution asset.

When replacing such an asset, both versions may need to be included in the mod.

---

## What is a Fluffy Mod Manager ZIP?

REasy projects can be exported as a ZIP structured for use with Fluffy Mod Manager.

This allows a project to be packaged with the correct folder structure so it can be installed and toggled through Fluffy.

REasy can also export supported projects as PAK files.

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

## Related Guides

- [Getting Started: Setup REasy](./Getting-Started.md)
- [Using Search and Regex](./Using-Search-and-Regex.md)
- [PAK Browser](./PAK-Browser.md)
- [File List Generator](./File-List-Generator.md)
- [RSZ Editor (PFB / SCN / User)](./RSZ/RSZ-Editor.md)

---

[⬅️ Back to REasy GUI Documentation](./README.md) | [⬆️ Top](#common-re-engine-modding-terms)
