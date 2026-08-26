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

A mod can be placed into one or more Fluffy Mod Manager categories.

For example:

```ini
category=BattleHUD
category=Character Select
```

Multiple `category=` entries can be used in the same `modinfo.ini`.

Categories are useful for organising larger mod collections.

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

For example:

```ini
MenuPriority=10
```

Higher values are displayed above lower values.

If it is not specified, the priority defaults to:

```text
0
```

This is useful when you want a preferred option, default version or commonly used addon to appear near the top of a submenu.

---

## `DummyMod=True`

A dummy mod is used only to organise a mod menu.

For example:

```ini
name=Comic Portraits
DummyMod=True
```

The dummy mod itself does not need to contain files that are installed into the game.

Other mods can then use:

```ini
AddonFor=Comic Portraits
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
category=BattleHUD
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
name=Marvel Character Names - Battle HUD
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
