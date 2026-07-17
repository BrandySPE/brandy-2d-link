# 2D Link 1.6.3 — Compatibility and Purchase Checklist

[Product Home](../README.md) · [Quick Start](QUICK_START.md) · [User Guide](USER_GUIDE.md) · [Support](SUPPORT.md) · [简体中文](COMPATIBILITY_AND_PURCHASE_CHECKLIST_zh-CN.md)

Use this page to decide whether 2D Link fits your current computer, host versions, asset structure, and storage setup.

## Quick fit check

2D Link 1.6.3 is a suitable match when all of the following are true:

- You work on **Windows x64**.
- You use **Blender 4.2.0 through 5.1.x**.
- Adobe Photoshop desktop for Windows is installed on the same computer.
- Your asset is built from separate, file-textured 2D planes.
- The project can be stored on a standard local drive.
- You are comfortable with save-triggered refresh rather than live brush streaming.

Adobe Photoshop is required and is not included. No separate Photoshop panel or extension is required.

## Tested host versions

The 1.6.3 package completed the documented workflow in all 30 combinations formed by these versions:

**Blender**

- 4.2.21 LTS
- 4.3.2
- 4.4.3
- 4.5.10
- 5.0.1
- 5.1.2

**Adobe Photoshop desktop for Windows**

- CC 2017.1.6; some Photoshop interfaces may report this build as 18.1.6
- Photoshop 2020 21.2.1
- Photoshop 2022 23.5.0
- Photoshop 2025 26.10.0
- Photoshop 2026 27.7.0

Four boundary pairings also completed 20 consecutive Photoshop save-and-manual-refresh cycles each, for 80 successful cycles in total, without detected changes to scene geometry or unrelated Blender data-blocks.

Other stable Blender versions inside the 4.2.0–5.1.x install range, or other public Photoshop versions between the listed releases, may work but have not completed the full matrix. The add-on may describe such a combination as **Compatibility Candidate** after **Test PS**.

Beta, nightly, preview, or modified host builds are outside the tested matrix.

## Operating system and Photoshop connection

The packaged workflow is for Windows x64. macOS and Linux are not supported by the 1.6.3 automated Photoshop connection.

2D Link uses Photoshop desktop scripting. Managed or hardened Windows environments may restrict automatic script launching. When Photoshop can still run local JSX scripts, **Manual Script** mode can be used instead of the normal **Auto** execution mode.

When several Photoshop versions are installed, configure the intended **PS Executable**, close other running Photoshop versions, start the configured version, and run **Test PS**. The path and version reported by the test identify the Photoshop instance that responded.

Photoshop web, Photoshop for iPad, and non-Adobe image editors are not supported by the documented workflow.

## Storage requirements

Keep active projects on a standard local drive.

Network shares, NAS devices, virtual filesystems, symbolic links, directory junctions, and folders with delayed or staged synchronization can interfere with save detection, file locking, project validation, or recovery. A synchronized folder may appear local but still delay a completed Photoshop save.

Moving the complete project folder is supported when its internal structure remains unchanged. Moving or renaming individual generated files is not supported.

## Asset requirements

The main project workflow expects:

- one asset organized in a clear Blender Collection;
- flat image-plane meshes with a rectangular outer boundary;
- a rectangular active UV layout without local distortion, seams, or rearranged islands;
- a consistent 2D plane orientation across the asset;
- a unique base name for every intended part;
- a detectable file-based Image Texture in the material's top-level node tree;
- local PNG, TGA, JPG, or JPEG files.

Internal subdivisions are acceptable when the outer boundary remains rectangular. Rotating or mirroring the complete rectangular UV layout is acceptable; changing its local shape is not.

Blender's standard three-digit duplicate suffixes, such as `.001`, are ignored during part matching. Names must still be unique after that suffix is removed.

A direct Image Texture connection to Principled BSDF Base Color is the clearest material setup. Images packed into the `.blend`, generated images, unsaved images, and arbitrary texture sources hidden inside custom node groups are not part of the main workflow.

After project creation, keep every project texture at its recorded pixel width and height. Resize the source files before creating the project, not during an active roundtrip.

## Project and texture behavior

Creating a project copies eligible textures into the project folder and reconnects Blender to those copies. It does not overwrite the files used before project creation.

Afterward, **Edit Active Object's Texture in PS**, **Reload Textures**, **Auto Reload**, and **Apply “Merge Layers” to Source Textures** operate on the project textures. In that button label, **Source Textures** means the files inside the active 2D Link project.

The workflow supports PNG, TGA, JPG, and JPEG. PNG or TGA is recommended for artwork that will be saved repeatedly. JPG and JPEG use lossy compression and require an additional confirmation during write-back.

## Merge Layers requirements

For multi-texture write-back:

- keep the generated groups **Brandy | Linked Content**, **Brandy | Merge Layers**, and **Brandy | Merged Layers** unchanged;
- do not transform, relink, or reorganize the generated Smart Objects;
- place visible artwork layers directly inside **Brandy | Merge Layers** without subgroups;
- match each layer name exactly and case-sensitively to its target in **Brandy | Linked Content**;
- keep the Merge Layers group at 100% opacity with Normal or Pass Through blend mode;
- save the linked PSD/PSB before applying the write-back;
- keep each affected project texture saved, at its original dimensions, and as a one-layer Photoshop document with no groups.

RGB 8-bit target documents can be used directly. Photoshop may offer to convert supported 8-bit or 16-bit RGB, Grayscale, CMYK, or Lab documents to RGB 8-bit; conversion can change color or precision. Unsupported color modes or bit depths must be converted manually first. Missing or non-sRGB color profiles produce a warning because Blender normally interprets these project textures as sRGB inputs.

For strict pixel-level corrections, especially soft transparent artwork across overlapping parts, direct single-texture editing is the more controlled workflow.

## Optional JSON tools

The JSON tools are secondary static-sprite utilities.

- **PhotoshopToSpine Import** accepts the defined static PhotoshopToSpine structure used by the add-on.
- **PhotoshopToSpine Export** writes a compatible static layout from eligible Blender sprite planes.
- **Spine2D Static Import** supports a limited setup-pose subset using static Region Attachments.

These tools do not import a complete Spine rig or animation. Mesh Attachments, animation timelines, Region Sequences, unsupported constraints, and other data outside the documented static subset are rejected rather than approximated.

External image folders are disabled by default. Enable **Allow External Image Folder** only for JSON files you trust and only when their declared image folder is intentionally outside the JSON directory.

## Before purchasing

Confirm the following:

- [ ] Windows x64 is available.
- [ ] Your Blender version is inside 4.2.0–5.1.x.
- [ ] Adobe Photoshop desktop for Windows is installed locally.
- [ ] Your assets use separate local image files on rectangular sprite planes.
- [ ] Part names remain unique after `.001`-style suffixes are removed.
- [ ] The project can remain on a standard local drive.
- [ ] Texture dimensions can stay fixed after project creation.
- [ ] Save-triggered refresh meets your workflow needs.
- [ ] You do not require general 3D projection painting or complete Spine rig and animation import.

For an unusual host version, managed workstation, custom storage system, or studio pipeline, contact **brandyspe2026@gmail.com** before purchasing and describe the environment clearly.
