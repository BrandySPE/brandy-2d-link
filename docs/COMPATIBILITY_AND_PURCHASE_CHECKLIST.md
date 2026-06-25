# Compatibility and Purchase Checklist — Brandy 2D Link 1.6.3

Read this before purchase or installation. Brandy 2D Link is a focused Photoshop–Blender workflow tool, not a general-purpose 2D pipeline suite.

## Minimum Environment

The official support boundary requires:

- Windows x64.
- A locally installed Adobe Photoshop desktop application that can run JSX scripts.
- Permission to run Blender extensions and Photoshop JSX scripts.
- For Windows automatic mode: Windows Script Host (`cscript.exe`), WMI process queries, and Photoshop COM automation must be available.
- Project files stored on a normal local filesystem.
- Source texture pixel dimensions kept unchanged after the project is linked.

Adobe Photoshop is not included with this add-on. A valid local installation is required.

Windows automatic mode uses `cscript.exe`, WMI, Photoshop COM automation, and local JSX execution. These components may be disabled by enterprise policy or security software on managed or hardened systems. **Manual Script** mode remains available when automatic mode cannot be used.

## Fully Tested and Officially Supported

The following declaration applies to the official Windows x64 package. Match the complete Blender version and the Photoshop year plus user-visible application version. Adobe internal build numbers are intentionally not used as a purchase or support gate.

**Blender:**

- Blender 4.2.21 LTS
- Blender 4.3.2
- Blender 4.4.3
- Blender 4.5.10
- Blender 5.0.1
- Blender 5.1.2

**Adobe Photoshop desktop:**

- Adobe Photoshop CC 2017.1.6
- Adobe Photoshop 2020, version 21.2.1
- Adobe Photoshop 2022, version 23.5.0
- Adobe Photoshop 2025, version 26.10.0
- Adobe Photoshop 2026, version 27.7.0

The environment is inside the official support matrix when the exact Blender version and Photoshop public version are listed above, the project follows the documented workflow limits, and **Test PS** confirms the path and reported application version of the Photoshop instance that actually responds. When several Photoshop versions coexist, an installed name or shortcut alone does not identify the connected version. **Test PS** does not inspect Adobe internal build numbers.

The extension manifest is capped before the Blender 5.2 series. The intended install range is Blender 4.2.0 through Blender 5.1.x. Other stable Blender releases in that range, and other stable Photoshop public versions in the CC 2017 through 2026 generations, are compatibility candidates. Installation, launch, or a visible interface does not prove that the complete core workflow has been tested, but an unlisted stable version can still be discussed with support.

## Purchase Checklist

- [ ] I use Windows x64.
- [ ] I have a locally installed Adobe Photoshop desktop application.
- [ ] My complete Blender version and my Photoshop year plus user-visible application version appear in the tested list, or I accept that my environment is only a compatibility candidate.
- [ ] When several Photoshop versions coexist, I will run **Test PS** and verify the path and reported application version of the responding application.
- [ ] For automatic mode, Windows Script Host, WMI, Photoshop COM automation, and local JSX execution are permitted on my computer.
- [ ] My project files will be stored on a normal local drive.
- [ ] I understand that a different Blender patch version or Photoshop public version is outside the tested matrix; Photoshop internal build numbers are not used as a support gate.
- [ ] I understand that future Blender versions or Photoshop public versions enter support only after testing and publication.
- [ ] I understand that source texture dimensions must remain unchanged during the linked workflow.
- [ ] I understand that the add-on does not replace backups, version control, reliable storage, or professional data recovery.
- [ ] I understand that the add-on does not provide a Photoshop panel and does not use UXP.
- [ ] I have reviewed the feature limits, including the limited static Spine2D import scope.
- [ ] I understand that external JSON image folders require explicit per-operation authorization and that ambiguous same-name image matches are not guessed.
- [ ] I understand that product support and update access are defined by the storefront where I purchase the product.

## Not Officially Supported

- macOS and Linux.
- Blender releases earlier than 4.2.0 or Blender 5.2.0 and later.
- Any Blender version or Photoshop public version not included in the tested list, including compatibility candidates.
- Photoshop releases earlier than CC 2017.1.6 or later than Photoshop 2026, version 27.7.0.
- Photoshop on the web or Photoshop for iPad.
- Non-Adobe image editors.
- Blender or Photoshop beta, alpha, nightly, test-channel, or other pre-release builds.
- Project folders that depend on network shares, NAS devices, virtual filesystems, symbolic links, directory junctions, or delayed synchronization behavior.
- Direct engine export, full Spine animation import, Mesh Attachments, constraints, two-color Tint, or animation playback.
- Arbitrary custom shader node groups as the documented texture source.

Only the platforms and host versions listed in this document are officially supported, regardless of implementation details in the package.

## Workflow Limits

- The add-on reloads project texture files after they are saved. It is not live brush-by-brush streaming.
- Blender reloads files in the active project's `textures` folder. Saving only the linked PSD/PSB does not update Blender.
- The linked document's reserved groups must not be renamed, duplicated, replaced, moved, or reorganized.
- Merge Layers write-back uses visible, top-level, name-matched layers inside `Brandy | Merge Layers`.
- Source texture dimensions must not change after the project is linked.
- PNG or TGA is recommended for repeated lossless painting.
- Auto Reload depends on stable local file timestamps. Use **Reload Textures** when external storage or synchronization delays change detection.
- Static JSON tools are secondary workflow extensions. They do not change the core Photoshop save-and-reload workflow.

## License and Commercial Purchase

The official Brandy 2D Link add-on package is distributed under **GPL-3.0-or-later**. The official package includes corresponding source files and the license text.

A purchase provides the official tested package and the support or update service stated on the storefront. GPL rights remain as described in the license included with the package.

## Refund and Store Policy

Refunds, payment issues, VAT/tax handling, receipts, and license-key delivery are handled by the storefront where the purchase is made.

Review the compatibility, version, storage-location, and workflow limits before purchase. Refund decisions remain subject to the store policy and applicable law.

## Independent Product Notice

Brandy 2D Link is an independent product. It is not affiliated with, endorsed by, sponsored by, or officially connected to Blender Foundation, Adobe, Unity Technologies, Epic Games, Esoteric Software, or their products.

Blender is a trademark of Blender Foundation. Adobe and Photoshop are either registered trademarks or trademarks of Adobe in the United States and/or other countries. Unity is a trademark or registered trademark of Unity Technologies or its affiliates. Unreal Engine is a trademark or registered trademark of Epic Games, Inc. Spine is a trademark of Esoteric Software LLC.
