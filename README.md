# 2D Link | Multi-Texture Roundtrip For Blender & Adobe Photoshop

[简体中文](README_zh-CN.md) · [Quick Start](docs/QUICK_START.md) · [User Guide](docs/USER_GUIDE.md) · [Compatibility](docs/COMPATIBILITY_AND_PURCHASE_CHECKLIST.md) · [Support](docs/SUPPORT.md) · [Release Notes](docs/RELEASE_NOTES.md)

**Paint the whole asset in Adobe Photoshop. Keep every texture separate in Blender.**

2D Link is a Windows x64 Blender add-on for artists working with cutout characters, modular sprites, layered game art, and other multi-part 2D assets. It lets you edit one project texture directly or paint with the complete assembled asset visible in a linked PSD/PSB.

Inside Blender, the add-on is displayed as **Brandy 2D Link**, and its tools are located in the **Brandy** sidebar tab.

This repository is the official public product and documentation hub, not the installable add-on package. The official storefront package includes the complete release and its corresponding GPL-licensed source files.

## Get 2D Link

- [Superhive](https://superhivemarket.com/products/brandy-2d-link) — product page, purchase, FAQ, first-roundtrip documentation, and marketplace support.
- [itch.io](https://brandyspe.itch.io/brandy-2d-link) — official storefront for the same 1.6.3 release package.

Install the complete ZIP supplied by the storefront. Do not use GitHub's **Code > Download ZIP** as the Blender add-on package.

## Two Ways to Work

### Quick Texture Edit

Select a sprite object in Blender and open its project texture in Adobe Photoshop. Paint, save, then update Blender with **Reload Textures** or save-triggered **Auto Reload**.

This is the fastest workflow for cleanup, color adjustments, and other edits that affect one texture.

### Full-Asset Painting

Open a linked PSD/PSB containing the assembled Blender asset. Its parts appear as linked Smart Objects, so you can judge seams, overlaps, alignment, and neighboring textures while painting in full context.

When the artwork is ready, place visible, name-matched layers in `Brandy | Merge Layers`, save the document, and run **Apply “Merge Layers” to Source Textures** from Blender.

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

It is not a general 3D texture-painting or projection system, a Photoshop panel, a direct game-engine exporter, or a complete Spine rig and animation importer.

## Requirements at a Glance

- Windows x64
- Blender 4.2.0 through 5.1.x install range
- Adobe Photoshop desktop with JSX scripting
- Local project storage on a normal filesystem
- File-based PNG, TGA, JPG, or JPEG textures

Adobe Photoshop is required and is not included with 2D Link. Photoshop web, Photoshop for iPad, macOS, Linux, non-Adobe image editors, and beta or nightly host builds are not part of the official 1.6.3 support matrix.

The exact tested matrix and purchase checks are listed in the [Compatibility and Purchase Checklist](docs/COMPATIBILITY_AND_PURCHASE_CHECKLIST.md).

## Validation and Testing

The official 1.6.3 Windows x64 package was matrix-tested across 30 combinations formed by six Blender versions and five Adobe Photoshop desktop versions.

Additional supervised testing covered a 39-part production-style character asset and 40 repeated save–refresh cycles on representative legacy, mid-range, and current configurations. Testing covers the documented workflow on the listed host versions; third-party add-ons, custom studio pipelines, managed security policies, storage systems, and future host versions require separate evaluation.

## Documentation

- [Quick Start](docs/QUICK_START.md) — installation and the shortest path to a successful first roundtrip.
- [User Guide](docs/USER_GUIDE.md) — complete daily workflow, project handling, optional tools, and recovery actions.
- [Compatibility and Purchase Checklist](docs/COMPATIBILITY_AND_PURCHASE_CHECKLIST.md) — exact tested versions, environment requirements, and purchase-fit checks.
- [Support Policy](docs/SUPPORT.md) — support scope, reporting requirements, privacy guidance, and response target.
- [Release Notes](docs/RELEASE_NOTES.md) — current package notes and unchanged workflow boundaries.
- [Superhive FAQ](https://superhivemarket.com/products/brandy-2d-link/faq) — concise answers to common pre-purchase questions.

New users should begin with the [Quick Start](docs/QUICK_START.md), complete one manual texture reload, and only then enable Auto Reload or test multi-texture write-back.

## Distribution and Support

Purchase from an official storefront to receive the verified release package and the support or update service described on that storefront.

Product support is handled through the storefront where the product was purchased. Payment, receipts, tax or VAT handling, download access, refunds, and marketplace-account issues are also handled by that storefront.

Before sharing an Operation Report or task log, remove private paths, account names, customer names, unpublished artwork references, credentials, payment information, and confidential production data.

## License and Independent Product Notice

The official 2D Link add-on package is distributed under **GPL-3.0-or-later** and includes the corresponding source files and license text. A purchase provides the official release package and the support or update service stated on the sales page; GPL rights remain as described in the included license.

2D Link is an independent product. It is not affiliated with, endorsed by, sponsored by, or officially connected to Blender Foundation, Adobe, Unity Technologies, Epic Games, Esoteric Software, or their products.

Blender is a trademark of Blender Foundation. Adobe and Photoshop are either registered trademarks or trademarks of Adobe in the United States and/or other countries. Unity is a trademark or registered trademark of Unity Technologies or its affiliates. Unreal Engine is a trademark or registered trademark of Epic Games, Inc. Spine is a trademark of Esoteric Software LLC.
