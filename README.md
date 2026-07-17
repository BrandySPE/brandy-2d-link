# 2D Link | Multi-Texture Roundtrip for Blender & Adobe Photoshop

[简体中文](README_zh-CN.md) · [Quick Start](docs/QUICK_START.md) · [User Guide](docs/USER_GUIDE.md) · [Compatibility](docs/COMPATIBILITY_AND_PURCHASE_CHECKLIST.md) · [Support](docs/SUPPORT.md)

**Paint the whole asset in Adobe Photoshop. Keep every texture separate in Blender.**

2D Link is a Windows x64 Blender add-on for cutout characters, modular sprites, layered game art, and other multi-part 2D assets. It supports two focused Photoshop workflows: direct editing of one project texture, and full-asset painting through a linked PSD/PSB while Blender continues to use separate texture files.

Inside Blender, the add-on appears as **Brandy 2D Link** in the **Brandy** sidebar tab.

This repository is the public product and documentation hub. It is not the installable add-on package. Installable builds are distributed through the storefronts below and include the corresponding GPL-licensed source code.

## Get 2D Link

- [Superhive](https://superhivemarket.com/products/brandy-2d-link)
- [itch.io](https://brandyspe.itch.io/brandy-2d-link)

Do not install GitHub's repository ZIP through Blender. Use the complete product ZIP supplied by one of the storefronts.

## Watch the workflow

- [English demo and tutorial](https://www.youtube.com/watch?v=seKdFcPqHf4)
- [中文演示与教程](https://www.youtube.com/watch?v=-xTnPTlHHwc)

## How it works

### Quick Texture Edit

Select a sprite object in Blender and open its project texture in Adobe Photoshop. Paint, save, then update Blender with **Reload Textures** or save-triggered **Auto Reload**.

This is the direct route for cleanup, color changes, and other edits that affect one texture.

### Full-Asset Painting

Open the linked PSD/PSB to view the assembled Blender asset. Each part appears as a linked Smart Object, so seams, overlaps, alignment, and neighboring textures remain visible while you paint.

To write finished artwork back, place visible, name-matched layers directly inside **Brandy | Merge Layers**, save the PSD/PSB, and run **Apply “Merge Layers” to Source Textures** in Blender. In this command, **Source Textures** means the texture files inside the active 2D Link project.

Saving the linked PSD/PSB does not update every texture by itself. Multi-texture write-back is a separate, explicit action.

## Project files

When you create a project, 2D Link copies eligible textures into the project folder and reconnects Blender to those copies. The files used before project creation remain unchanged. From that point onward, direct texture editing, Auto Reload, and Merge Layers write-back use the project textures.

Before a multi-texture write-back, 2D Link checks the linked document and target textures and creates verified backups of the affected files. **Undo Last Merge** can restore the latest successful write-back while the project files still match its recorded recovery state.

These safeguards do not replace normal production backups or version control.

## Requirements

- Windows x64
- Blender 4.2.0 through 5.1.x
- Adobe Photoshop desktop for Windows; no separate Photoshop panel or extension is required
- Local PNG, TGA, JPG, or JPEG texture files
- A project folder on a standard local drive
- Flat rectangular image planes with rectangular active UVs, a consistent 2D plane orientation, and unique part base names

The workflow is save-triggered. It does not stream individual brush strokes from Photoshop to Blender.

Version 1.6.3 completed the documented workflow across 30 tested Blender–Photoshop combinations. Exact versions, workflow limits, and purchase checks are listed in the [Compatibility and Purchase Checklist](docs/COMPATIBILITY_AND_PURCHASE_CHECKLIST.md).

## Documentation

- [Quick Start](docs/QUICK_START.md) — complete one single-texture roundtrip and one Merge Layers write-back.
- [User Guide](docs/USER_GUIDE.md) — detailed operating instructions for the complete feature set.
- [Compatibility and Purchase Checklist](docs/COMPATIBILITY_AND_PURCHASE_CHECKLIST.md) — tested versions, system and asset requirements, storage limits, and optional JSON scope.
- [Support](docs/SUPPORT.md) — how to check a failed operation and send a useful private report.
- [Superhive FAQ](https://superhivemarket.com/products/brandy-2d-link/faq) — concise answers to common pre-purchase questions.

New users should begin with the [Quick Start](docs/QUICK_START.md).

## License and independent product notice

The add-on package is distributed under GPL-3.0-or-later and includes its corresponding source code.

2D Link is an independent product and is not affiliated with or endorsed by Adobe, the Blender Foundation, or their related organizations. See [NOTICE.md](NOTICE.md) for trademark information.
