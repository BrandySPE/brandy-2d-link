# 2D Link 1.6.3 — Compatibility and Purchase Checklist

[Product Home](../README.md) · [Quick Start](QUICK_START.md) · [User Guide](USER_GUIDE.md) · [Support](SUPPORT.md)

Read this page before purchase or installation. 2D Link is a focused Blender–Adobe Photoshop workflow for multi-part 2D assets, not a general-purpose 2D or 3D pipeline suite.

## Quick Fit Check

2D Link is a suitable purchase when all of the following are true:

- you use Windows x64;
- you have Adobe Photoshop desktop installed locally;
- your asset is built from flat rectangular image planes with rectangular active UVs;
- the asset uses local file-based PNG, TGA, JPG, or JPEG textures;
- you can keep the active project on a normal local filesystem;
- you can keep project texture pixel dimensions unchanged after linking;
- you want either direct single-texture editing or full-asset painting with separate texture write-back.

It is not the right tool when you require macOS or Linux support, a non-Adobe editor, real-time brush streaming, arbitrary 3D projection painting, direct game-engine export, or complete Spine rig and animation import.

Adobe Photoshop is required and is not included with 2D Link.

## Exact Tested Matrix

The official 1.6.3 Windows x64 package was fully tested with the versions below.

**Blender**

- Blender 4.2.21 LTS
- Blender 4.3.2
- Blender 4.4.3
- Blender 4.5.10
- Blender 5.0.1
- Blender 5.1.2

**Adobe Photoshop desktop**

- Adobe Photoshop CC 2017.1.6
- Adobe Photoshop 2020, version 21.2.1
- Adobe Photoshop 2022, version 23.5.0
- Adobe Photoshop 2025, version 26.10.0
- Adobe Photoshop 2026, version 27.7.0

The environment is inside the official support matrix when the complete Blender version and the Photoshop year plus user-visible application version are listed above, the project follows the documented workflow, and **Test PS** confirms the path and version of the Photoshop instance that actually responds.

Adobe internal build numbers are not used as a purchase or support gate. When several Photoshop versions coexist, an installed folder name or shortcut does not identify the connected version; use **Test PS**.

## Install Range and Compatibility Candidates

The extension manifest allows Blender 4.2.0 through Blender 5.1.x and is capped before the Blender 5.2 series.

A stable Blender version inside that install range but outside the exact list, or another stable Photoshop public version in the covered CC 2017–2026 generations, is a compatibility candidate rather than a fully tested environment. Successful installation, launch, or visible UI does not prove that the complete core workflow has been tested.

Future Blender or Photoshop versions enter the published support matrix only after the documented workflow is tested and the matrix is updated.

## Windows Automation and Storage

The normal **Auto** execution mode uses local Windows and Photoshop automation components, including Windows Script Host (cscript.exe), WMI process queries, Photoshop COM automation, and JSX execution.

Managed computers, hardened security configurations, or enterprise policies may block one or more of these components. **Manual Script** mode is available when automatic execution cannot be used, but the user must still be permitted to run JSX scripts from Photoshop.

For the official workflow, keep active projects on a normal local drive. Network shares, NAS devices, virtual filesystems, symbolic links, directory junctions, and delayed-sync folders are outside the supported storage model because file locks, timestamps, or write completion may not behave predictably.

## Asset Requirements

Each intended project part should use:

- a local file-based PNG, TGA, JPG, or JPEG texture;
- a flat rectangular mesh;
- a valid rectangular active UV area;
- a unique base name;
- a consistent 2D plane orientation.

Internal mesh subdivisions are supported when the outer boundary remains rectangular. Depth offsets may be used for visual stacking.

The documented material source is a normal Image Texture in the material's top-level node tree. Image Texture nodes hidden inside arbitrary custom Shader Node Groups are not a documented source.

Blender’s standard three-digit duplicate suffixes, such as ".001", are removed when matching part names. Suffixes with a different format are not automatically removed. After suffix handling, every project part must still resolve to a unique name.

Resize texture canvases before creating the 2D Link project. Pixel width and height must remain unchanged after linking.

## Workflow Boundaries

- 2D Link refreshes project texture files after they are saved; it is not brush-by-brush live streaming.
- Saving only the linked PSD/PSB saves the working document and does not update every project texture.
- Multi-texture write-back uses visible, top-level, name-matched layers inside 'Brandy | Merge Layers'.
- The three reserved linked-document groups and generated Smart Object transforms must remain unchanged.
- PNG or TGA is recommended for artwork that will be edited and saved repeatedly.
- JPG and JPEG are supported, but repeated saves may reduce quality because they use lossy compression.
- Static PhotoshopToSpine and Spine2D JSON tools are optional utilities, not the core purpose of the product.
- Spine2D support is limited to supported static Region Attachments; it does not import complete rigs, animation, Mesh Attachments, constraints, sequences, or two-color Tint.
- External JSON image folders require explicit authorization, and ambiguous same-name files are not guessed.
- The add-on does not replace independent backups, version control, reliable storage, or professional data recovery.

## Purchase Checklist

- [ ] I use Windows x64.
- [ ] I have Adobe Photoshop desktop installed locally and understand that it is not included.
- [ ] My exact Blender and Photoshop public versions are in the tested matrix, or I accept a compatibility-candidate environment.
- [ ] When several Photoshop versions are installed, I will use **Test PS** to confirm the responding path and version.
- [ ] My system permits the automation required by my chosen execution mode.
- [ ] My active 2D Link project will remain on a normal local filesystem.
- [ ] My asset uses flat rectangular image planes and supported file-based textures.
- [ ] I will keep project texture dimensions unchanged after linking.
- [ ] I understand the difference between Quick Texture Edit, saving the linked PSD/PSB, and explicit Merge Layers write-back.
- [ ] I understand the limited static scope of the optional JSON tools.
- [ ] I will keep independent backups of production work.
- [ ] I have reviewed the storefront's support, update, refund, and account terms.

## Official Package, License, and Store Policy

The official 2D Link add-on package is distributed under **GPL-3.0-or-later** and includes the corresponding source files and license text.

A purchase provides the official tested package and the support or update service described by the storefront. This repository does not promise lifetime updates, lifetime support, or compatibility with future host versions.

Payments, receipts, tax or VAT handling, download access, refunds, and marketplace-account issues are handled by the storefront where the purchase was made. Refund decisions remain subject to that storefront's policy and applicable law.

## Independent Product Notice

2D Link is an independent product. It is not affiliated with, endorsed by, sponsored by, or officially connected to Blender Foundation, Adobe, Unity Technologies, Epic Games, Esoteric Software, or their products.

Blender is a trademark of Blender Foundation. Adobe and Photoshop are either registered trademarks or trademarks of Adobe in the United States and/or other countries. Unity is a trademark or registered trademark of Unity Technologies or its affiliates. Unreal Engine is a trademark or registered trademark of Epic Games, Inc. Spine is a trademark of Esoteric Software LLC.
