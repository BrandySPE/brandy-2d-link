# 2D Link | Multi-Texture Roundtrip For Blender & Adobe Photoshop

[简体中文](README_zh-CN.md) · [Quick Start](docs/QUICK_START.md) · [User Guide](docs/USER_GUIDE.md) · [Compatibility](docs/COMPATIBILITY_AND_PURCHASE_CHECKLIST.md) · [Support](docs/SUPPORT.md) · [Release Notes](docs/RELEASE_NOTES.md)

**Paint the whole asset in Adobe Photoshop. Keep every texture separate in Blender.**

2D Link is a Windows x64 Blender add-on for artists working with cutout characters, modular sprites, layered game art, and other multi-part 2D assets. It lets you edit one project texture directly or paint with the complete assembled asset visible in a linked PSD/PSB.

Inside Blender, the add-on is displayed as **Brandy 2D Link**, and its tools are located in the **Brandy** sidebar tab.

This repository is the official public product and documentation hub, not the installable add-on package. The official storefront package includes the complete release and its corresponding GPL-licensed source files.

## Watch the Workflow

- [English Demo & Tutorial](https://www.youtube.com/watch?v=seKdFcPqHf4)
- [中文演示与教程](https://www.youtube.com/watch?v=-xTnPTlHHwc)

## Get 2D Link

- [Superhive](https://superhivemarket.com/products/brandy-2d-link)
- [itch.io](https://brandyspe.itch.io/brandy-2d-link)

Installable builds are distributed through the official storefronts above; GitHub Releases and Code → Download ZIP are not used for product installation.

## Two Ways to Work

### Quick Texture Edit

Select a sprite object in Blender and open its project texture in Adobe Photoshop. Paint, save, then update Blender with **Reload Textures** or save-triggered **Auto Reload**.

This is the fastest workflow for cleanup, color adjustments, and other edits that affect one texture.

### Full-Asset Painting

Open a linked PSD/PSB containing the assembled Blender asset. Its parts appear as linked Smart Objects, so you can judge seams, overlaps, alignment, and neighboring textures while painting in full context.

When the artwork is ready, place each visible artwork layer directly inside Brandy | Merge Layers and name it after its target part. Save the document, then run Apply "Merge Layers" to Source Textures in Blender.

Saving the linked PSD/PSB alone does not update every texture. The write-back action is intentionally separate from an ordinary document save.

## Why Artists Use It

- Edit and refresh one project texture without reconnecting or rebuilding its Blender material.
- Paint with the assembled asset visible, making seams, overlaps, and neighboring parts easier to judge.
- Write finished artwork back to multiple project textures with document validation, verified backups, and Undo Last Merge.

These safeguards complement normal production backups and version control; they do not replace them.

## Designed For

2D Link is intended for:

- cutout characters and layered animation assets;
- modular sprites and multi-part game art;
- billboard-style image planes and simple layered 2.5D assets;
- artists who need complete visual context while keeping production textures separate;
- small teams using a focused, file-based Photoshop–Blender workflow.

The main workflow expects flat rectangular image planes, rectangular active UVs, a consistent 2D plane orientation, unique part base names, and local file-based PNG, TGA, JPG, or JPEG textures.

2D Link focuses on file-based 2D texture roundtrips for multi-part assets. It does not provide general 3D projection painting, direct game-engine export, Photoshop panel integration, or full Spine rig and animation import.

## Requirements at a Glance

- Windows x64
- Blender 4.2.0 through 5.1.x install range
- Adobe Photoshop desktop with JSX scripting
- Local project storage on a normal filesystem
- File-based PNG, TGA, JPG, or JPEG textures

2D Link requires Adobe Photoshop desktop on Windows x64. Photoshop web, Photoshop for iPad, macOS, Linux, non-Adobe image editors, and beta or nightly host builds are outside the 1.6.3 support matrix.

The exact tested matrix and purchase checks are listed in the [Compatibility and Purchase Checklist](docs/COMPATIBILITY_AND_PURCHASE_CHECKLIST.md).

## Validation and Testing

TThe 1.6.3 Windows x64 release completed the same end-to-end test workflow across 30 Blender–Photoshop version combinations. Each run used a 39-part character asset and covered project creation, linked PSD setup, manual and automatic texture refresh, dimension-mismatch blocking, invalid-document rejection, named-layer write-back, Undo Last Merge, JSON roundtripping, and PNG, TGA, and JPG refresh behavior.

Four boundary version pairings also completed 20 consecutive save-and-manual-refresh cycles each. All 80 cycles completed without failure or detected changes to geometry or Blender data-blocks.

All automated matrix runs completed without a release-blocking failure or report-level warning. The results apply to the documented workflow, the listed host versions, Windows x64, and the tested local-storage environment. Custom studio pipelines, restricted systems, third-party add-ons, network storage, and unlisted host versions should be evaluated separately.

## Documentation

- [Quick Start](docs/QUICK_START.md) — installation and the shortest path to a successful first roundtrip.
- [User Guide](docs/USER_GUIDE.md) — complete daily workflow, project handling, optional tools, and recovery actions.
- [Compatibility and Purchase Checklist](docs/COMPATIBILITY_AND_PURCHASE_CHECKLIST.md) — exact tested versions, environment requirements, and purchase-fit checks.
- [Support Policy](docs/SUPPORT.md) — support scope, reporting requirements, privacy guidance, and response target.
- [Release Notes](docs/RELEASE_NOTES.md) — current package notes and unchanged workflow boundaries.
- [Superhive FAQ](https://superhivemarket.com/products/brandy-2d-link/faq) — concise answers to common pre-purchase questions.

New users should begin with the [Quick Start](docs/QUICK_START.md), complete one manual texture reload, and then enable Auto Reload or test multi-texture write-back.

## License and Independent Product Notice

Your purchase includes the current official release and product support for the documented version. Future updates and compatibility with new Blender or Photoshop versions are not guaranteed until they are published on this page.

The official add-on package is distributed under GPL-3.0-or-later and includes its corresponding source code. Purchases provide the official release package and the support terms stated by the selected storefront.

2D Link is an independent product and is not affiliated with or endorsed by Blender Foundation or Adobe. See NOTICE.md for additional trademark notices.
