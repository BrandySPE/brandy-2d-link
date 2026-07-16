# 2D Link 1.6.3 — User Guide

[Product Home](../README.md) · [Quick Start](QUICK_START.md) · [Compatibility](COMPATIBILITY_AND_PURCHASE_CHECKLIST.md) · [Support](SUPPORT.md) · [Release Notes](RELEASE_NOTES.md)

This guide explains the complete documented workflow for 2D Link 1.6.3. New users should complete the [Quick Start](QUICK_START.md) first.

2D Link is displayed as **Brandy 2D Link** inside Blender. This guide uses the English UI labels so they can be matched directly with the interface, Operation Reports, and support messages.

## 1. Workflow Overview

2D Link connects Blender and Adobe Photoshop for multi-part 2D assets that use separate file-based textures.

The core project model is:

1. Prepare a collection of image-textured sprite planes in Blender.
2. Create or link a local 2D Link project.
3. Edit one project texture directly, or open the assembled linked PSD/PSB.
4. Save the relevant file in Photoshop.
5. Refresh individual textures with **Reload Textures** or **Auto Reload**.
6. When full-asset artwork must be distributed across textures, use 'Brandy | Merge Layers' and run the explicit write-back action from Blender.

The workflow is save-triggered. It does not stream individual brush strokes.

Saving the linked PSD/PSB and writing artwork back to the project textures are separate actions. This separation prevents an ordinary document save from unexpectedly changing several texture files.

## 2. Supported Environment

The official package is for Windows x64. The manifest install range is Blender 4.2.0 through 5.1.x, and Adobe Photoshop desktop with JSX scripting is required.

The exact fully tested Blender and Photoshop versions are maintained in the [Compatibility and Purchase Checklist](COMPATIBILITY_AND_PURCHASE_CHECKLIST.md). Versions inside the general range but outside the exact matrix are compatibility candidates.

Photoshop web, Photoshop for iPad, macOS, Linux, non-Adobe image editors, and beta or nightly host builds are not officially supported for version 1.6.3.

The normal automated workflow depends on Windows Script Host, WMI, Photoshop COM automation, and local JSX execution. Managed or hardened computers may restrict these components; **Manual Script** mode remains available when local policy permits Photoshop JSX scripts.

Active projects should remain on a normal local filesystem. Network shares, NAS devices, virtual filesystems, symbolic links, directory junctions, and delayed-sync folders are outside the supported storage model.

## 3. Install the Add-on

1. Keep the official 2D Link ZIP intact.
2. In Blender, open **Edit > Preferences > Get Extensions** or **Extensions**.
3. Open the upper-right menu and choose **Install from Disk**.
4. Select the complete official ZIP.
5. Enable **Brandy 2D Link**.
6. In a 3D View, press 'N' and open the **Brandy** tab.

The panel title should show **Brandy 2D Link v1.6.3**.

Do not install individual Python or JSX files. Do not use GitHub's repository ZIP as the add-on package.

The UI language can be set to Auto, English, or Chinese. Reload the add-on or restart Blender after changing the interface language.

## 4. Prepare the Blender Asset

One Blender collection represents one project asset. Put the intended sprite objects in that collection and enable **Include Child Collections** when nested collections are part of the asset.

Each intended part should use:

- a local file-based PNG, TGA, JPG, or JPEG texture;
- a flat rectangular mesh;
- a valid rectangular active UV area;
- a unique base name;
- a consistent 2D plane orientation.

Internal subdivisions are supported when the outer boundary remains rectangular. Depth offsets may be used for visual stacking.

Use a normal Image Texture in the material's top-level node tree. A direct Base Color connection is the clearest setup. Image Texture nodes hidden inside arbitrary custom Shader Node Groups are not a documented source.

Blender numeric suffixes such as '.001' are ignored for part matching. After suffix handling, each intended project identity must still be unique.

Before creating the project:

- save the '.blend' file;
- save all source textures to stable local files;
- apply any required texture-canvas resizing;
- remove packed or unsaved image states from the intended workflow;
- keep an independent backup of important artwork.

After linking, texture pixel dimensions must remain unchanged. A dimension mismatch is rejected instead of being silently accepted and shifting the layout.

## 5. Configure Photoshop

Open **Photoshop Setup** and set **PS Executable** to the Photoshop application you want to use.

Recommended sequence:

1. Close other running Photoshop versions when several versions are installed.
2. Keep **PS Execution Mode** on **Auto** for the normal Windows workflow.
3. Click **Open PS** or start the configured Photoshop manually.
4. Wait until Photoshop has fully started.
5. Close welcome screens, save dialogs, or other modal dialogs.
6. Return to Blender and click **Test PS**.

A Ready connection means Blender can communicate with the responding Photoshop instance. The path and user-visible application version reported by **Test PS** identify that instance. A shortcut name or installation-folder label is not sufficient when several versions coexist.

Compatibility status and connection status are separate. A connection can be Ready while the exact host combination remains a compatibility candidate.

### Manual Script mode

When automatic communication is blocked, expand **Photoshop Settings** and set **PS Execution Mode** to **Manual Script**.

Run the required operation again, then follow the on-screen path to the generated JSX file. In Photoshop, choose **File > Scripts > Browse** and execute that file. Return to Blender after Photoshop finishes.

Manual Script mode changes how the task is launched; it does not remove the document, project, or file-validation requirements.

## 6. Create a New Project

1. Set **Project Collection** to the collection containing the asset.
2. Under **Project Action**, choose **Create a New Project in This Folder**.
3. Set **Project Folder** to an empty local folder or a path that does not yet exist.
4. Set **Canvas Padding** only when extra transparent workspace is needed around the assembled linked document.
5. Click **Create Project**.
6. Keep Blender and Photoshop open until the task finishes.

Canvas Padding affects the assembled working document and does not resize the individual project textures.

During creation, 2D Link validates the collection, sprite layout, image files, and Photoshop project structure. It copies eligible textures into the project, reconnects Blender to the project copies, records project metadata, and creates the linked PSD or PSB.

Create Project does not overwrite the original pre-project texture files. After creation, direct editing, Auto Reload, and Merge Layers write-back operate on the texture files inside the 2D Link project.

A successful project shows values under **Current Project** and **Linked Document**. Do not manually rename, move, or replace individual files inside the generated project structure.

If creation stops, open **Open Operation Report**, correct the first blocked condition, and run the operation again. Preserve any incomplete-project marker or task state until the report is understood.

## 7. Quick Texture Edit

Use Quick Texture Edit for a correction that belongs to one texture.

1. Make the intended sprite mesh the active Blender object.
2. Click **Edit Active Object's Texture in PS**.
3. Edit the opened project texture in Photoshop.
4. Save it without changing pixel width or height.
5. Return to Blender.
6. Click **Reload Textures**.

Blender reloads the image data used by the material. It does not rebuild the material node setup.

When a material contains several Image Textures, the add-on must be able to identify a primary project texture through a supported direct connection or import record. If the wrong texture is selected or no texture opens, review the material and Operation Report rather than renaming project files manually.

## 8. Auto Reload

Auto Reload watches the active project's supported texture files and refreshes an image after a save has finished and the file write becomes stable.

It is intended for a smoother paint–save–check loop. It is not a real-time brush preview and does not continuously hash every project file in the background.

If Auto Reload does not update:

- confirm that the edited file is inside the active project's 'textures' folder;
- confirm that the file name and location did not change;
- confirm that the pixel dimensions are unchanged;
- wait until Photoshop finishes saving;
- close modal dialogs;
- check the Operation Report;
- use **Reload Textures** for an immediate manual refresh.

Storage or synchronization systems that delay timestamps, retain file handles, or stage writes can delay or prevent detection. Use normal local storage for the documented workflow.

## 9. The Linked PSD/PSB

Click **Open Linked Document in Photoshop** to open the assembled project document.

The document contains three reserved root groups:

- 'Brandy | Linked Content' contains plugin-managed linked Smart Objects for the project textures.
- 'Brandy | Merge Layers' contains visible artwork prepared for explicit write-back.
- 'Brandy | Merged Layers' stores processed artwork after a successful write-back.

Do not rename, move, duplicate, replace, or reorganize these groups. Do not move, rotate, flip, distort, or relink the generated Smart Objects.

Ordinary painting layers, references, notes, and temporary work may remain outside the reserved groups. Keep the reserved structure clean so validation can distinguish managed content from normal artwork.

Saving the PSD/PSB saves the working document. Blender still reloads the individual files inside the project's 'textures' folder.

## 10. Full-Asset Painting and Write-Back

Use the linked document when seams, overlaps, alignment, or neighboring parts need to remain visible while painting.

Prepare the artwork as follows:

1. Create or paste each artwork layer directly inside 'Brandy | Merge Layers'.
2. Keep each intended layer visible.
3. Give each layer exactly the same name as its target in 'Brandy | Linked Content'.
4. Do not use subgroups inside 'Brandy | Merge Layers'.
5. Keep the group at 100% opacity.
6. Use Normal or Pass Through as the group blend mode.
7. Save the PSD/PSB.

Names are case-sensitive. Copying the generated target name is safer than typing it again.

When one piece of artwork crosses several parts, duplicate the artwork once for each target and name each copy after that target. Each matched layer is mapped to its target and clipped to that texture's canvas during write-back.

Then return to Blender:

1. Confirm that the correct project is active.
2. Click **Apply “Merge Layers” to Source Textures**.
3. Review any warning before continuing.
4. Wait for Photoshop and Blender to finish.
5. Read the Operation Report if a layer is skipped or an image does not refresh.

Before changing a target, 2D Link validates the project, linked document, reserved structure, target mapping, texture dimensions, file state, and operation state. It creates verified backups for the texture files involved.

After a successful operation, the matching project textures are updated, processed artwork moves to 'Brandy | Merged Layers', the linked document is saved, and Blender attempts to refresh the affected images.

For strict pixel-level work, especially with soft transparent edges across overlapping parts, direct single-texture editing remains the most controlled method. Merge Layers is a context-painting and distribution workflow, not a replacement for careful per-texture pixel editing.

## 11. Undo Last Merge

**Undo Last Merge** is a single project-level undo for the latest successful Merge Layers write-back.

Use it immediately when the result is wrong. Do not continue editing or saving target files first.

The command checks the current project files against the recorded recovery state. If the files changed again or a required backup is missing, undo is refused to avoid overwriting newer work with an outdated record.

## 12. Link, Switch, or Move a Project

A Blender collection can use more than one compatible 2D Link project built from the same asset structure. This can support skins, palettes, localization variants, or damage states.

To link or switch:

1. Set **Project Collection** to the intended collection.
2. Under **Project Action**, choose **Link or Switch to an Existing Project**.
3. Set **Project Folder** to the existing 2D Link project folder.
4. Review **Pending Project Switch**.
5. Click **Link or Switch Project**.

The add-on validates part identity, order, layout, and texture dimensions before switching. If validation fails, the current project remains active.

If the entire project folder has been moved, preserve its internal structure, select the folder at the new location, and use **Link or Switch Project**. Do not move or rename individual generated texture files and expect the add-on to search the computer for them.

## 13. Photoshop Settings and Task Handling

Most values under **Photoshop Settings** can remain at their defaults.

**PS Execution Mode** controls automatic or manual task launching.

**PS Response Wait Limit (s)** controls how long Blender waits continuously for a Photoshop task before changing to periodic result checks. Reaching the limit does not cancel Photoshop; it changes Blender's waiting behavior.

**Open Operation Report** shows the latest readable result and safe next action. Start there whenever a task fails.

**Open Task Log Folder** is intended for deeper diagnostics and support. It may be unavailable when no task log exists. Logs can contain local paths, account names, project names, or unpublished artwork references and must be reviewed before sharing.

Do not close Blender or Photoshop during a project creation or write-back task. Do not force-clear task state or locks while Photoshop may still be writing files.

## 14. Reports and Recovery Tools

The latest complete Operation Report is also stored in the Blender Text data-block 'BRANDY_2D_LINK_Last_Report'.

Recovery tools are not normal daily workflow buttons. Use them only when the panel or Operation Report identifies the relevant state.

### Recover Incomplete Project

This appears after interrupted project creation leaves a recoverable marker. Preserve the project folder and marker, close unrelated tasks, and use the built-in recovery action when instructed.

### Restore Source Textures from Backup

This is for an interrupted write-back operation. Close Photoshop completely before using it. Use the built-in action rather than manually replacing project files.

### Repair Part IDs

This is a targeted metadata repair. Use it only when the Operation Report states that the project differs only in Part IDs.

Recovery tools intentionally avoid guessing. A recovery action can be refused when current files no longer match the recorded state.

## 15. Optional JSON Workflows

JSON tools are secondary static-sprite utilities. They do not change the core Photoshop save-and-refresh workflow.

### PhotoshopToSpine Import

Imports supported static PhotoshopToSpine JSON layout data and creates textured sprite planes in Blender. Select the matching JSON, texture format, alpha behavior, import scale, and Z spacing for the source layout.

### PhotoshopToSpine Export

Exports the eligible current Blender layout to a compatible JSON file. It does not modify the active Photoshop project.

### Spine2D Static Import

Creates a static setup-pose layout from supported Region Attachments. It is not a Spine animation importer and does not import Mesh Attachments, constraints, complete bone animation, sequences, or two-color Tint.

Keep image paths clear and close to the JSON folder when possible. Authorize an external image folder only when the JSON is trusted and the images are intentionally outside the JSON folder. Leave **Allow External Image Folder** off by default.

When image paths are missing, ambiguous, outside the allowed search root, or too broad to resolve safely, correct the JSON or use a smaller dedicated folder. The add-on stops before creating sprite data and does not guess between multiple same-name image files.

## 16. Utility Tools

### Switch Texture Format

Set **Reload Format**, then click **Switch Texture Format** to redirect selected sprites to existing files with the same base name and selected supported extension.

The tool does not convert image data. A matching target file must already exist; missing targets are skipped or reported.

### Copy Shader Settings to Selected Objects

Copies compatible unconnected shader input values from the active sprite to the other selected sprites while preserving texture links. Select target sprites first and the source sprite last so it becomes active.

This is most predictable on clean materials created by the add-on or built with matching node structures.

### Merge Duplicate Materials

Consolidates matching unmodified materials created by the add-on when they can be shared safely. It is not intended to merge arbitrary custom materials.

### Restore Imported Material

Rebuilds the first material slot of an imported sprite from the JSON and texture records stored during import.

### Isolate Selection

Toggles Blender local view for the selected objects in the current 3D View. Use it to inspect or move a small set of sprites without changing global scene visibility.

## 17. Common Mistakes

- Installing separate files instead of the complete official ZIP.
- Using GitHub's repository ZIP as the add-on package.
- Creating an active project on a network share, NAS, delayed-sync folder, symbolic link, directory junction, or virtual filesystem.
- Changing texture pixel dimensions after the project is linked.
- Renaming or reorganizing reserved groups or generated project files.
- Expecting a linked PSD/PSB save to update every texture automatically.
- Placing Merge Layers artwork inside subgroups or using incorrect target names.
- Using Merge Layers as a substitute for strict per-texture pixel work across overlapping transparent edges.
- Using recovery tools without an Operation Report or matching project state.
- Sharing raw reports or logs without checking for private information.

## 18. Support Preparation and Learning Order

Before requesting support, confirm that the official unmodified package is installed, **Test PS** shows the intended Photoshop path and version, the project is on a local filesystem, texture dimensions are unchanged, and the issue can be reproduced in a project copy.

Follow the [Support Policy](SUPPORT.md) for the required report contents and privacy guidance.

Recommended learning order:

1. Install the add-on.
2. Prepare a small copied asset in one clean collection.
3. Configure Photoshop and run **Test PS**.
4. Create a local project.
5. Complete one Quick Texture Edit and manual reload.
6. Enable Auto Reload only after manual reload works.
7. Open the linked document and identify the three reserved groups.
8. Complete one simple Merge Layers write-back.
9. Test **Undo Last Merge** immediately after that write-back.
10. Learn project switching with a copied project.
11. Use JSON and utility tools only when the pipeline requires them.
12. Use recovery tools only when the Operation Report identifies the matching state.

Keeping the first test small makes project structure, save behavior, and error reporting easier to understand before production artwork is involved.
