[⬅️ Back to REasy GUI Documentation](./README.md)

# Fluffy Mod Manager Export

REasy can package a project directly into a ZIP suitable for use with **Fluffy Mod Manager**.

This guide covers the built-in REasy export options and the additional `modinfo.ini` settings supported by Fluffy Mod Manager.

---

## Exporting a Fluffy Mod Manager ZIP from REasy

In a REasy project, click:

```text
Export Fluffy ZIP
```

REasy will package the project into a ZIP that can be installed with Fluffy Mod Manager.

The export settings can be customised by clicking the **cog button** beside `Export Fluffy ZIP`.

Available options include:

- **Mod Name**
- **Description**
- **Author**
- **Version**
- **PAK File Name**
- **Screenshot**

Use the `...` button beside **Screenshot** to browse for an image.

`PAK File Name` is only used when the project is being packaged as a PAK rather than loose files.

---

## Build PAK Instead of Loose Folders

REasy also includes:

```text
Build PAK instead of loose folders in Fluffy ZIP
```

When enabled, the exported Fluffy ZIP contains a PAK-based mod instead of the normal loose `natives` folder structure.

When disabled, REasy exports the project using the normal loose-file mod structure.

---

## What Gets Included in the Export?

REasy packages the contents of the project folder.

For example:

```text
REasy-v0.X.X\projects\SF6\Ui2\
```

Everything inside that project can therefore be included in the exported mod.

This can include files that are not used by RE Engine, such as:

```text
.dds
.psd
.blend
```

These extra files will normally not stop the mod from working in Fluffy Mod Manager, but they unnecessarily increase the size of the mod archive.

Before publishing a mod, it is recommended to remove:

- Working files
- Source artwork
- PSD files
- Blender files
- DDS files that are not required by the game
- Backups
- Temporary files
- Other files not needed by the finished mod

---

# Advanced `modinfo.ini`

Fluffy Mod Manager can read additional information from a file named:

```text
modinfo.ini
```

The file should normally be placed in the root of the mod alongside the `natives` folder.

A typical example is:

```ini
name=Marvel Character Names
version=v1.0
description=Changes the character names to Marvel equivalents.\nIncludes Character Select and Battle HUD names.
author=YourName
homepage=https://www.nexusmods.com/
screenshot=preview.jpg
category=Character Select
category=BattleHUD
```

`modinfo.ini` is optional.

If `name=` is not supplied, Fluffy Mod Manager will normally use the archive or folder name as the mod name.

---

## Common `modinfo.ini` Entries

| Entry | Purpose |
|---|---|
| `name=` | Name shown in Fluffy Mod Manager |
| `version=` | Mod version displayed in the preview |
| `description=` | Description of the mod |
| `author=` | Mod author |
| `homepage=` | Adds a link to the mod's webpage |
| `screenshot=` | Preview image filename |
| `category=` | Places the mod into one or more categories |
| `AddonFor=` | Makes the mod an addon for another mod |
| `NameAsBundle=` | Groups several related mods under one menu |
| `MenuPriority=` | Controls ordering inside an addon submenu |
| `DummyMod=True` | Creates a menu-only parent mod |

---

## `description=`

The description shown by Fluffy Mod Manager can be added with:

```ini
description=Changes the Battle HUD portraits.
```

Use:

```text
\n
```

to create a new line.

For example:

```ini
description=Changes the Battle HUD portraits.\nIncludes Player 1 and Player 2 versions.
```

---

## `screenshot=`

The screenshot file should normally be stored beside `modinfo.ini`.

For example:

```text
modinfo.ini
preview.jpg
natives/
```

Then use:

```ini
screenshot=preview.jpg
```

If no `screenshot=` entry is supplied, Fluffy Mod Manager can also look for common screenshot filenames such as:

```text
screenshot.jpg
screenshot.png
```

A reasonably sized JPG is recommended so the preview image does not unnecessarily increase the size of the mod archive.

---

## `category=`

Fluffy Mod Manager has a built-in category system for supported games.

Each game can have its own preset categories. These can include character-specific categories and broader groups such as:

```text
Characters
Stages
Sound
Music
Models
Textures
Misc
```

The exact category list varies between games.

Fluffy Mod Manager will normally scan the files contained in a mod and try to determine the most suitable category automatically.

A mod author can override this by using:

```ini
category=
```

### Using a Preset Category

If the category matches one of Fluffy Mod Manager's recognised preset categories, the mod can be placed directly into that category tree.

For example:

```ini
category=!Characters > Ryu
```

places the mod under:

```text
Characters
└─ Ryu
```

Another example:

```ini
category=!Other > Textures
```

places the mod under:

```text
Other
└─ Textures
```

It is generally good practice to use the game's existing preset categories where possible. This keeps mods organised consistently for the end user.

---

### Custom Categories Become Tags

If the value used with `category=` does **not** match a recognised preset category, Fluffy Mod Manager does not create a new category.

Instead, that value is added to the mod as a **Tag**.

For example:

```ini
category=BattleHUD
category=Character Select
```

does not create new `BattleHUD` or `Character Select` folders in the main category list.

Instead, the mod receives the tags:

```text
BattleHUD
Character Select
```

These can be found in Fluffy Mod Manager under:

```text
Filter mods
    ↓
Tags
```

This can be useful for adding more specific labels that do not exist in the game's normal preset categories.

For example, Street Fighter 6 mods could use tags such as:

```ini
category=BattleHUD
category=BattleUI
category=Character Select
category=Quick Startup
category=VFX
```

Multiple `category=` entries can be added to the same mod, allowing a mod to appear under several Tags.

For example:

```ini
category=BattleHUD
category=Character Select
category=Characters
```

would give that mod all three Tags.

This gives mod authors two useful ways to organise mods:

```text
Preset category
    ↓
Places the mod into Fluffy's normal category tree

Custom category value
    ↓
Creates a Tag for use with Filter mods
```

---

### Resident Evil 2 Remake Categories

Fluffy Mod Manager currently defines the following preset categories for Resident Evil 2 Remake:

#### Characters

```ini
category=!Characters > Leon
category=!Characters > Claire
category=!Characters > Ada
category=!Characters > Sherry
category=!Characters > Hunk
category=!Characters > Tofu
category=!Characters > Kendo
category=!Characters > Irons
category=!Characters > Ben
category=!Characters > Annette
category=!Characters > Enemies
category=!Characters > Multiple
```

#### Other

```ini
category=!Other > RE Framework
category=!Other > Code Injectors
category=!Other > Music
category=!Other > Models
category=!Other > Textures
category=!Other > Animation
category=!Other > Text
category=!Other > Misc
```

These are the category names published by FluffyQuack for manually overriding RE2 Remake's automatic category selection.

---

## `homepage=`

A homepage can be added with:

```ini
homepage=https://www.nexusmods.com/
```

This can link to:

- Nexus Mods
- GitHub
- Documentation
- The author's website
- Another page containing information about the mod

---

## `AddonFor=`

Use:

```ini
AddonFor=Main Mod Name
```

when a mod is an optional addon for another mod.

The value should match the main mod's `name=` entry.

For example:

```ini
name=Marvel Character Names - Battle HUD
AddonFor=Marvel Character Names
```

Fluffy Mod Manager will then organise the addon underneath the main mod rather than displaying it as a completely separate top-level entry.

Addons can also contain their own addons, allowing nested mod menus.

---

## `NameAsBundle=`

`NameAsBundle=` can group several related mods under one menu button.

For example:

```ini
NameAsBundle=Comic Portrait Collection
```

If several mods use the same bundle name, Fluffy Mod Manager can organise them together.

This is useful for collections of related alternatives where there is no single main mod to use with `AddonFor=`.

---

## `MenuPriority=`

`MenuPriority=` controls where a mod appears inside an addon submenu.

If `MenuPriority=` is not used, Fluffy Mod Manager will normally sort the entries **alphanumerically**:

```text
0-9
A-Z
```

For example, a set of addon options named:

```text
Jill Main Files (Install First)
Improved Jiggle
Clean No Dirt
50% Dirt
Dirty
Sweaty
No Sweat
Bloody
No Blood
```

would normally be displayed as:

```text
50% Dirt
Bloody
Clean No Dirt
Dirty
Improved Jiggle
Jill Main Files (Install First)
No Blood
No Sweat
Sweaty
```

This is not always the order you want, especially when a mod has a main file that should be installed first, followed by grouped optional choices.

`MenuPriority=` allows you to manually control that order.

Higher values are displayed above lower values.

For example:

```ini
Jill Main Files (Install First)
MenuPriority=10
```

```ini
Clean No Dirt
MenuPriority=9
```

```ini
50% Dirt
MenuPriority=8
```

```ini
Dirty
MenuPriority=7
```

```ini
No Blood
MenuPriority=6
```

```ini
Bloody
MenuPriority=5
```

```ini
No Sweat
MenuPriority=4
```

```ini
Sweaty
MenuPriority=3
```

This would give you a much more deliberate menu order:

```text
Jill Main Files (Install First)
Clean No Dirt
50% Dirt
Dirty
No Blood
Bloody
No Sweat
Sweaty
```

If `MenuPriority=` is not specified, the priority defaults to:

```text
0
```

This is especially useful for keeping main files, recommended options and related variants in a logical order instead of relying on alphanumeric sorting.

---

## `DummyMod=True`

A dummy mod is used only to organise a mod menu.

For example:

```ini
name=Marvel Character Names
DummyMod=True
```

The dummy mod itself does not need to contain files that are installed into the game.

Other mods can then use:

```ini
AddonFor=Marvel Character Names
```

This is useful for creating a clean parent menu for several modular or alternative options.

---

## Example `modinfo.ini`

```ini
name=Marvel Character Names
version=v1.0
description=Changes the character names to Marvel equivalents.\nIncludes Character Select and Battle HUD names.
author=YourName
homepage=https://www.nexusmods.com/
screenshot=preview.jpg
category=Character Select
MenuPriority=10
```

For a menu-only parent:

```ini
name=Marvel Character Names
description=Choose which parts of the mod you want to install.
author=YourName
DummyMod=True
```

An addon could then use:

```ini
name=Marvel Character Names - DLC Characters
version=v1.0
AddonFor=Marvel Character Names
MenuPriority=10
```

---

## Recommended Publishing Workflow

Before publishing a mod exported from REasy:

1. Check the project folder for working or temporary files.
2. Remove files that are not required by the finished mod.
3. Configure the Fluffy export information.
4. Add or review `modinfo.ini` if advanced Fluffy options are required.
5. Add a suitable screenshot.
6. Export the Fluffy ZIP.
7. Install the exported ZIP in Fluffy Mod Manager.
8. Test the mod before publishing it.

---

[⬅️ Back to REasy GUI Documentation](./README.md) | [⬆️ Top](#fluffy-mod-manager-export)
