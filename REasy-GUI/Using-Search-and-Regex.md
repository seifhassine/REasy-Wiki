[⬅️ Back to REasy GUI Documentation](./README.md)

# Using Search and Regex

Several parts of REasy include search or filter fields.

These can be used with simple text searches, or with **regular expressions (regex)** for more advanced filtering.

You do **not** need to know regex to use REasy effectively. In many cases, entering part of a filename, folder name or known ID is enough.

---

## Simple Search

For a normal search, type part of the filename or path you are looking for.

For example:

```text
esf001
```

This will find entries containing `esf001`.

In Street Fighter 6, this is useful for locating files associated with Ryu.

Another example:

```text
gui
```

will return paths containing `gui`.

---

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

## Mesh and Texture Version Examples

Below are examples of how `.mesh` and `.tex` versions differ between RE Engine games.

| Game | Mesh | Texture |
|---|---|---|
| Resident Evil 2 | `.mesh.1808312334` | `.tex.10` |
| Devil May Cry 5 | `.mesh.1808282334` | `.tex.11` |
| Resident Evil 3 | `.mesh.1902042334` | `.tex.190820018` |
| Resident Evil Village | `.mesh.2101050001` | `.tex.30` |
| Monster Hunter Rise | `.mesh.2008058288` | `.tex.28` |
| Monster Hunter Rise: Sunbreak | `.mesh.2109148288` | `.tex.28` |
| Resident Evil 2 / 3 RT | `.mesh.2109108288` | `.tex.34` |
| Resident Evil 7 RT | `.mesh.220128762` | `.tex.35` |
| Resident Evil 4 | `.mesh.221108797` | `.tex.143221013` |
| Street Fighter 6 | `.mesh.230110883` | `.tex.241101895` |
| Dragon's Dogma 2 | `.mesh.240423143` | `.tex.760230703` |
| Monster Hunter Wilds | `.mesh.241111606` | `.tex.241106027` |
| Resident Evil Requiem | `.mesh.250925211` | `.tex.250813143` |
| Pragmata | `.mesh.250925211` | `.tex.250813143` |

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

This is a useful example of why you should not assume that even the same game will always use the same file-format version forever.

Tools such as the **File List Generator** can analyse the game executable and identify the versions currently used by that game.

---

# Searching by File Type

To search for texture files:

```regex
\.tex(\.|$)
```

To search for mesh files:

```regex
\.mesh(\.|$)
```

To search for material files:

```regex
\.mdf2(\.|$)
```

To search for User files:

```regex
\.user(\.|$)
```

To search for Prefab files:

```regex
\.pfb(\.|$)
```

---

## Search for Specific Versions

You can search for a specific full suffix.

For example, Resident Evil 2 textures:

```regex
\.tex\.10$
```

Devil May Cry 5 meshes:

```regex
\.mesh\.1808282334$
```

Street Fighter 6 textures:

```regex
\.tex\.241101895$
```

Dragon's Dogma 2 meshes:

```regex
\.mesh\.240423143$
```

Monster Hunter Wilds textures:

```regex
\.tex\.241106027$
```

Resident Evil Requiem textures:

```regex
\.tex\.250813143$
```

Common User files:

```regex
\.user\.2$
```

Common Prefab files:

```regex
\.pfb\.17$
```

---

## Search for Multiple File Types

Regex can search several file types at once.

For example:

```regex
\.(tex|mesh)(\.|$)
```

finds both:

- `.tex`
- `.mesh`

To include materials:

```regex
\.(tex|mesh|mdf2)(\.|$)
```

To search several commonly modded structured formats:

```regex
\.(user|pfb|scn)(\.|$)
```

---

## Search for Multiple Names or IDs

Use the `|` character to mean **OR**.

For example:

```regex
esf001|esf002
```

finds entries containing either:

- `esf001`
- `esf002`

You can add more:

```regex
esf001|esf002|esf004
```

---

## Search Within a Path

To search for anything beneath a particular path:

```regex
^natives/stm/product/gui/
```

The `^` means:

**Start of the path**

You can also use a normal text search:

```text
product/gui
```

if you do not need the stricter regex behaviour.

---

## Useful Regex Symbols

| Symbol | Meaning | Example |
|---|---|---|
| `\.` | Literal dot | `\.tex` |
| `|` | OR | `tex|mesh` |
| `^` | Start of text/path | `^natives/stm/` |
| `$` | End of text/path | `\.user\.2$` |
| `()` | Group expressions | `\.(tex|mesh)` |
| `.*` | Any number of characters | `esf001.*tex` |

---

# Practical Examples

## Street Fighter 6 — Ryu Textures

Find all texture files related to Ryu:

```regex
esf001.*\.tex(\.|$)
```

Find all Ryu mesh or material files:

```regex
esf001.*\.(mesh|mdf2)(\.|$)
```

---

## Street Fighter 6 — Stage Search

Find either the Fighting Ground or World Tour version of King Street:

```regex
ess1000|wtc1000
```

This is useful when a location exists in more than one game mode.

---

## Resident Evil 4 — Crafting Data

To find the crafting settings file:

```text
ItemCraftSettingUserdata
```

or target the full User file:

```regex
ItemCraftSettingUserdata\.user\.2$
```

Known file:

```text
ItemCraftSettingUserdata.user.2
```

---

## Resident Evil 4 — Ada Character Model

Search for Ada's character ID:

```text
cha800
```

To narrow the results to her mesh and material files:

```regex
cha800_00.*\.(mesh|mdf2)(\.|$)
```

Known files include:

```text
cha800_00.mdf2.32
cha800_00.mesh.221108797
```

You can also search specifically for the mesh:

```regex
cha800_00\.mesh\.221108797$
```

---

## Monster Hunter Wilds — Gemma

Search for Gemma's character files using:

```text
ch04_004_0000
```

To find the main character resources together:

```regex
ch04_004_0000.*\.(chain2|mdf2|mesh)(\.|$)
```

Known files include:

```text
ch04_004_0000.chain2.13
ch04_004_0000.mdf2.45
ch04_004_0000.mesh.241111606
```

To search only for Gemma's mesh:

```regex
ch04_004_0000\.mesh\.241111606$
```

---

## Why Start With the Identifier?

When possible, start with the most distinctive part of the filename:

```text
esf001
cha800
ch04_004_0000
ItemCraftSettingUserdata
```

This usually gives a useful group of related files before you narrow the search further with an extension or version number.

For example:

```regex
ch04_004_0000.*\.mesh
```

is often more useful than searching every `.mesh` file in the game.

---

# Where Search is Used

Search and filtering are available throughout REasy.

Some editors have their own built-in search fields. For example:

- **Project Browser**
- **PAK Browser**
- **MSG Editor**
- **File List Generator**
- **RSZ-related tools**
- **Text Finder**

If the editor you are using does not have an obvious search field, you can use REasy's global **Find** tools.

Open:

**Find → Find**

or press:

```text
Ctrl+F
```

This opens the standard Find function for the currently active editor or file where supported.

REasy also provides several specialised directory searches from the **Find** menu:

| Function | Shortcut | Use |
|---|---|---|
| **Find** | `Ctrl+F` | Search within the active editor or file |
| **Search Directory for GUID** | `Ctrl+G` | Search files in a directory for a GUID |
| **Search Directory for Text** | `Ctrl+T` | Search files in a directory for text |
| **Search Directory for Number** | `Ctrl+N` | Search files in a directory for a numeric value |
| **Search Directory for Hex** | — | Search files in a directory for hexadecimal data |
| **Find/Replace RSZ Field Value** | — | Find and replace matching RSZ field values |

The exact search options available can depend on the type of file or editor currently open.

---

## Searching Inside MSG Files

The **MSG Editor** has its own search bar.

You can search message entries by:

- Name
- Message content
- UUID

This is particularly useful for dialogue, menu text, system messages and other localised text stored in `.msg` files.

For example, searching:

```text
WinCommentMessage
```

can quickly narrow a large MSG file down to matching entries.

You can also search for text contained inside the messages themselves.

---

## Which Search Should I Use?

As a general rule:

- Use the **Filter** field when browsing PAK or Project files.
- Use an editor's own search bar when one is available.
- Use **Ctrl+F** for searching within the currently open editor or file.
- Use **Search Directory for Text** when you do not know which file contains the value.
- Use **Search Directory for GUID** when tracing references between RSZ files.
- Use **Search Directory for Number** or **Hex** when looking for values that are not stored as readable text.

---

# Tips

- Start with a simple text search first.
- Use regex when you need to narrow a large result set.
- Escape literal dots using `\.`.
- Use `|` to search several names, IDs or file types.
- Use `^` when the beginning of the path matters.
- Use `$` when the end of the filename matters.
- Include the version number when you need to target one specific game or file revision.
- Keep the expression as simple as possible.

---

[⬅️ Back to REasy GUI Documentation](./README.md) | [⬆️ Top](#using-search-and-regex)
