# 2D Link 1.6.3 — User Guide

[Product Home](../README.md) · [Quick Start](QUICK_START.md) · [Compatibility](COMPATIBILITY_AND_PURCHASE_CHECKLIST.md) · [Support](SUPPORT.md) · [简体中文](USER_GUIDE_zh-CN.md)

This guide explains how to use every documented feature in 2D Link 1.6.3. Complete the [Quick Start](QUICK_START.md) first if you have not yet tested one manual texture reload and one Merge Layers write-back.

The instructions use the English interface labels. In Blender, the add-on appears as **Brandy 2D Link** in the **Brandy** tab of the 3D View sidebar.

## 1. Understand the project workflow

A 2D Link project connects one Blender Collection, a set of separate texture files, and one linked PSD/PSB.

When you create a project, 2D Link:

1. checks the eligible sprite objects and their textures;
2. copies the eligible texture files into the new project folder;
3. reconnects Blender to the copied project textures;
4. creates the linked PSD/PSB containing the assembled asset.

The files used before project creation are the **original textures**. They remain unchanged during project creation. The copies inside the project are the **project textures**. Direct editing, Reload Textures, Auto Reload, and Merge Layers write-back operate on the project textures.

The interface button **Apply “Merge Layers” to Source Textures** also refers to these project textures. It does not write back to the original pre-project files.

There are two normal editing routes:

- **Quick Texture Edit** opens one project texture for a direct correction.
- **Full-Asset Painting** opens the linked PSD/PSB so you can paint while seeing the assembled asset, then explicitly distribute finished layers to one or more project textures.

Both routes are save-triggered. 2D Link does not transmit individual brush strokes while you paint.

## 2. Install and open the add-on

1. Keep the purchased product ZIP intact.
2. In Blender, open **Edit > Preferences > Get Extensions** or **Extensions**.
3. Open the upper-right menu and choose **Install from Disk**.
4. Select the complete product ZIP.
5. Enable **Brandy 2D Link**.
6. Open a 3D View, press `N`, and choose the **Brandy** tab.

The panel title should show **Brandy 2D Link v1.6.3**.

Do not install individual Python or JSX files. Do not use GitHub's repository ZIP as the add-on package.

The interface language can be changed under **Photoshop Settings**. Choose Auto, English, or Chinese, then reload the add-on or restart Blender when the panel asks you to do so.

## 3. Prepare a Blender asset

### Collection scope

Set **Project Collection** to the Collection that represents one asset. Enable **Include Child Collections** when intended parts are stored in nested Collections.

Keep unrelated objects outside the selected scope. A small, clearly organized Collection makes validation and project switching easier to understand.

### Part structure

Each intended sprite part should use:

- a flat mesh with one rectangular outer boundary;
- a rectangular active UV layout;
- the same 2D plane orientation as the other project parts;
- a unique base name;
- a local file-based PNG, TGA, JPG, or JPEG texture.

Internal subdivisions are allowed when the outer boundary remains rectangular. The complete UV rectangle may be rotated or mirrored, but local stretching, seams, separate islands, or rearranged UV sections are not supported by the main project workflow.

Depth offsets can be used to stack parts. Animation, drivers, constraints, and modifiers are not transferred into the linked document; the project uses the asset's current base layout.

### Names

Part names are used during project matching and Merge Layers write-back. Blender's standard three-digit duplicate suffixes, such as `.001`, are ignored. After that suffix is removed, every intended part name must still be unique.

Choose stable names before creating the project. Do not rename generated project files to compensate for a naming problem; correct the Blender object names and create a new project when necessary.

### Materials and textures

Use a file-based Image Texture in the material's top-level node tree. A direct connection from the Image Texture to Principled BSDF Base Color is the clearest setup.

When a material contains several Image Texture nodes, the add-on must be able to identify one primary project texture. A supported import record or a clear direct Base Color connection can provide that identification. Arbitrary image sources hidden inside custom node groups are not part of the main workflow.

Before project creation:

1. save the `.blend` file;
2. save every intended texture as a local file;
3. complete any required canvas resizing;
4. unpack images that are stored inside the `.blend`;
5. keep a separate backup of important production artwork.

After project creation, do not change the pixel width or height of a project texture. A dimension change is blocked because it would invalidate the recorded layout.

## 4. Configure and test Photoshop

Expand **Photoshop Setup**.

1. Set **PS Executable** to the Photoshop application you want 2D Link to use.
2. Start the configured Photoshop version, or click **Open PS**.
3. Wait until Photoshop has fully started.
4. Close welcome screens, save dialogs, and other modal windows.
5. Click **Test PS**.

A successful test shows a ready connection and the responding Photoshop version. When several Photoshop versions are installed, close the other running versions before testing. The configured path and the version reported by **Test PS** are more reliable than a shortcut name or installation-folder label.

**PS Execution Mode** is under **Photoshop Settings**. Leave it on **Auto** for the normal Windows workflow.

Run **Test PS** again after changing the Photoshop executable, changing the execution mode, restarting Photoshop under a different version, or when the panel says the previous test is no longer current.

### Manual Script mode

Use **Manual Script** only when automatic Photoshop scripting is blocked but Photoshop can still execute local JSX files.

1. Expand **Photoshop Settings**.
2. Set **PS Execution Mode** to **Manual Script**.
3. Start the desired operation again.
4. Follow the path shown in Blender to the generated JSX file.
5. In Photoshop, choose **File > Scripts > Browse** and run that file.
6. Return to Blender after Photoshop finishes.

Manual Script changes only how the task is launched. All project, document, naming, and file-state requirements remain the same.

## 5. Create a new project

1. Set **Project Collection** and **Include Child Collections** as needed.
2. Under **Project Action**, choose **Create a New Project in This Folder**.
3. Set **Project Folder** to an empty local folder or a path that does not yet exist.
4. Set **Canvas Padding** if you need additional transparent workspace around the assembled asset.
5. Confirm that **Test PS** is ready.
6. Click **Create Project**.
7. Keep Blender and Photoshop open until the task finishes.

**Canvas Padding** adds transparent space around the complete linked document. It does not resize the individual textures or change the relative placement of parts.

During creation, the add-on validates the Collection, parts, UVs, image files, names, and layout. If creation succeeds, the **Photoshop Setup** and **Photoshop Project** sections show the current project and linked document.

Do not manually rename, replace, or move individual generated files. Keep the entire project folder together.

If creation stops, open **Operation Report**, correct the first blocked condition, and run creation again. Keep any incomplete project folder until the report identifies whether it should be recovered or discarded.

## 6. Work with the current project

The **Photoshop Project** section becomes available after a project is linked. It shows the current project and linked document and contains the daily workflow controls. **Source Texture Status** shows whether the active project can currently be watched and reloaded; follow the message below it when the watcher is paused or blocked.

### Open the linked document

Click **Open Linked Document in Photoshop** to open the assembled PSD/PSB.

### Open one texture

Make a project sprite the active object and click **Edit Active Object's Texture in PS**. The add-on opens the primary project texture assigned to that part.

### Reload project textures

Click **Reload Textures** to reload supported images from the active project. Use this after a Photoshop save when Auto Reload is disabled or when you want an immediate manual check.

Reloading is refused when an affected Blender Image has unsaved pixel changes, is packed into the `.blend`, is no longer file-based, or would be unsafe to update. Read the message and Operation Report rather than forcing a reload.

### Auto Reload

Enable **Auto Reload** after manual reload has worked once. The add-on watches supported texture files in the active project and reloads an image after a completed save becomes stable.

Auto Reload watches the current project only. It can pause when the project is incomplete, a project switch is being validated, a Photoshop write-back is running, or a file no longer matches the project's recorded state.

When a saved texture does not update:

1. confirm that you edited the file inside the active project's `textures` folder;
2. confirm that Photoshop did not save under a different name or path;
3. confirm that width and height are unchanged;
4. wait for Photoshop to finish writing the file;
5. use **Reload Textures**;
6. read **Operation Report** if the reload is blocked.

## 7. Direct single-texture editing

Use direct editing when a change affects one texture or requires exact pixel control.

1. Make the intended sprite mesh the active Blender object.
2. Click **Edit Active Object's Texture in PS**.
3. Paint in Photoshop.
4. Save the same file in place.
5. Return to Blender and use **Reload Textures**, or let Auto Reload detect the completed save.

Do not change the file name, folder, format, width, or height during this roundtrip. To use a different existing file format, use **Switch Texture Format** as described later instead of Save As.

Direct editing is recommended for fine cleanup and for soft transparent edges that cross overlapping parts, because you are working on the exact target texture without an additional distribution step.

## 8. Use the linked PSD/PSB

The linked document contains three reserved root groups.

### Brandy | Linked Content

This group contains the generated linked Smart Objects for the separate project textures. Their names identify the valid Merge Layers targets.

Do not rename, move, duplicate, transform, flip, distort, relink, replace, or reorganize these Smart Objects. Do not rename or move the reserved group.

### Brandy | Merge Layers

Place finished artwork here when it should be written to project textures. Only visible artwork layers directly inside this group are considered. Subgroups are not used as write-back targets.

Keep the group at 100% opacity. Use Normal or Pass Through as its blend mode.

### Brandy | Merged Layers

After a successful write-back, processed artwork is moved here. This keeps the active Merge Layers group clear and preserves the artwork in the linked document.

You may keep references, notes, sketches, and ordinary working layers outside the reserved groups. Saving the PSD/PSB saves the working document only; it does not update every project texture.

## 9. Apply Merge Layers to project textures

Use Merge Layers when you need to paint with the complete asset visible and then distribute finished artwork to one or more textures.

### Prepare target layers

For each target texture:

1. create or paste one visible artwork layer directly inside **Brandy | Merge Layers**;
2. copy the exact target name from **Brandy | Linked Content**;
3. apply that exact, case-sensitive name to the artwork layer;
4. keep the layer outside subgroups.

When one artwork element crosses several parts, duplicate it once for each target and give each copy the corresponding target name. During write-back, pixels outside each target texture's canvas are clipped.

Before applying:

- save the linked PSD/PSB;
- keep the three reserved groups and generated Smart Objects unchanged;
- keep each affected project texture at its recorded dimensions;
- if an affected project texture is already open in Photoshop, save it and leave one artwork layer with no layer groups.

### Color mode and file-format checks

A target already in RGB 8-bit can be used directly.

For supported RGB, Grayscale, CMYK, or Lab documents in 8-bit or 16-bit, Photoshop may ask for permission to convert the target to RGB 8-bit. Review the prompt before continuing because conversion can change color or precision.

Unsupported modes or bit depths must be converted manually before the write-back. A missing or non-sRGB color profile produces a warning because Blender normally reads these textures as sRGB inputs.

JPG and JPEG targets require an additional confirmation because saving is lossy. Use PNG or TGA for files that will be edited repeatedly when possible.

### Run the write-back

1. Return to Blender.
2. Confirm the intended current project.
3. Click **Apply “Merge Layers” to Source Textures**.
4. Review any warning.
5. Wait for Photoshop and Blender to finish.
6. Read the Operation Report if a layer is skipped or an image does not refresh.

Before changing files, 2D Link checks the project, linked document, reserved group structure, target names, target dimensions, and current file state. It creates verified backups for the affected project textures.

After a successful operation:

- the matching project textures are updated;
- processed layers move to **Brandy | Merged Layers**;
- the linked document is saved;
- Blender attempts to reload the affected images.

Click **Reload Textures** only when the report says a Blender image was not reloaded or the visible result remains stale.

## 10. Undo the latest Merge Layers write-back

**Undo Last Merge** restores the project textures changed by the most recent successful Merge Layers operation.

Use it immediately after discovering an incorrect result. Do not edit or save the affected textures first.

Undo verifies that the files still match the recorded post-write state. If a target file has changed again, the linked recovery record is missing, or the project no longer matches, the command is refused to protect newer work.

Undo Last Merge is one project-level undo, not a history browser. Keep normal backups and version control for production work.

## 11. Link or switch to an existing project

Use this workflow to reopen a project, reconnect after moving the complete project folder, or switch a compatible asset Collection between project variants.

1. Set **Project Collection** to the Blender Collection that should use the project.
2. Under **Project Action**, choose **Link or Switch to an Existing Project**.
3. Set **Project Folder** to the existing folder that contains the 2D Link project data.
4. Review **Pending Project Switch** when it appears.
5. Confirm that **Test PS** is ready.
6. Click **Link or Switch Project**.
7. Wait for validation to finish.

The current project remains active until the candidate project passes validation. Part identities, layout, and texture dimensions must match the selected Blender Collection.

You may move the entire project folder to another local location when its internal structure remains unchanged. Select the folder at its new location and use **Link or Switch Project**. Do not move individual generated textures, metadata files, or the linked PSD/PSB separately.

After a successful switch, Auto Reload remains off. Run **Reload Textures** once, confirm the result, then enable Auto Reload if needed.

## 12. Photoshop task controls

Most Photoshop tasks should be allowed to finish normally. Do not close Blender or Photoshop while project creation, project switching, Merge Layers, or Undo Last Merge is running.

### PS Response Wait Limit (s)

This setting controls how long Blender waits continuously before changing to periodic result checks. Reaching the limit does not stop Photoshop and does not mean the operation failed.

### Stop After Current Step

Use **Stop After Current Step** when you want the active task to stop at a safe point. Cancellation is cooperative; Photoshop may need time to finish its current step and restore files.

### Switch to Periodic Checks

Use **Switch to Periodic Checks** to stop Blender's foreground wait when Photoshop is still running or its final state cannot yet be read. This does not cancel Photoshop. Keep both applications and the project files unchanged until the operation's final state is known.

### Clear Unknown Task State

This appears when Blender cannot determine whether a task is still running. Use it only after confirming that Photoshop has finished and no related file write is continuing. The command clears the unknown task state; it does not complete or reverse unfinished Photoshop work.

## 13. Operation Reports, logs, and recovery

### Operation Report

Expand **Photoshop Settings** and click **Open Operation Report** whenever a task stops or a result is incomplete. The latest complete report is also stored in the Blender Text data-block:

`BRANDY_2D_LINK_Last_Report`

Start with the first blocked condition. Correct it before retrying. Later messages often describe consequences of the same initial problem.

### Open Task Log Folder

Use **Open Task Log Folder** only when deeper diagnostics are needed or support asks for it. Logs may contain local paths, account names, project names, and artwork references. Review and redact them before sharing.

### Recover Incomplete Project

This button appears when interrupted project creation leaves a recoverable project marker.

1. Keep the incomplete project folder unchanged.
2. Confirm that the configured Photoshop version is ready.
3. Close unrelated Photoshop documents or dialogs.
4. Click **Recover Incomplete Project** only when the panel or report directs you to it.

If recovery is refused, follow the new report rather than editing the generated files manually.

### Restore Source Textures from Backup

Use this only for an interrupted Merge Layers write-back when the panel or report identifies a restorable backup state.

1. Completely exit Photoshop so it cannot continue saving the target files.
2. Keep the project folder unchanged.
3. Click **Restore Source Textures from Backup**.
4. Run **Reload Textures** after restoration and verify the result.

Task backups are not automatically deleted. Keep them until the project has been checked.

### Repair Part IDs

Use **Repair Part IDs** only when project linking reports that the project metadata differs only in Part IDs. The action creates a backup and repairs that specific mismatch. It is not a general repair for renamed parts, changed layouts, or moved files.

### Clear Stale Project Lock

A project lock can remain after an abnormal exit. Clear it only after confirming that every Blender and Photoshop operation using that project has ended and no process is writing project files.

If the panel says another Blender instance owns the lock, return to that instance or wait for its task to finish. Do not force-clear an active lock.

## 14. PhotoshopToSpine Import

This tool imports the supported static PhotoshopToSpine JSON structure and creates textured sprite planes in Blender. It does not import animation.

1. Expand **PhotoshopToSpine Import**.
2. Set **JSON File** to the source JSON.
3. Set **Texture Format** to the extension used by the source images: PNG, JPG, or TGA.
4. Enable **Use Alpha** when the textures contain transparency.
5. Enable **Premultiplied Alpha** only when the source images were prepared that way.
6. Enable **Flip Horizontally** when the complete imported composition should be mirrored.
7. Set **Import Scale** to convert source pixel coordinates to Blender units. The default is `0.001`.
8. Set **Sprite Z Spacing** to control depth separation between imported parts. The default is `0.001`.
9. Click **Import PhotoshopToSpine JSON**.

The importer expects a complete static structure and matching image files. If validation fails, it stops before leaving a partial imported asset. Correct the first error in the Operation Report and import again.

The created Collection and root controller preserve the imported composition. Keep the original JSON and image folder if you may need **Restore Imported Material** later.

## 15. PhotoshopToSpine Export

This tool exports the eligible current Blender sprite arrangement as PhotoshopToSpine-compatible static JSON. It does not create, link, or modify a Photoshop project.

1. Set **Project Collection** to the Collection you want to export.
2. Enable **Include Child Collections** if needed.
3. Expand **PhotoshopToSpine Export**.
4. Set **Output Path** to a JSON file or output folder.
5. Click **Export JSON from Collection**.

The exporter checks sprite names, image paths, rectangular structure, UVs, layout, and consistent display scale. It does not write an incomplete JSON when required parts fail validation. Read the Operation Report, correct the asset, and export again.

## 16. Spine2D Static Import

This tool imports a limited static Setup Pose from supported Spine Region Attachments. It is not a full Spine importer.

1. Expand **Spine2D Static Import**.
2. Set **JSON File**.
3. Choose **Texture Format**.
4. Set **Use Alpha**, **Premultiplied Alpha**, and **Flip Horizontally** as required by the source images.
5. Leave **Allow External Image Folder** off unless the trusted JSON deliberately points to an image directory outside the JSON folder.
6. Set **Missing Size Fallback (px)** only when a supported Region Attachment omits width or height. The default is 100 px.
7. Set **Import Scale** and **Sprite Z Spacing**.
8. Click **Import Spine2D JSON**.

Only supported static Region Attachments are imported. Complete rigs, animation timelines, Mesh Attachments, Region Sequences, unsupported constraints, two-color Tint, and unsupported blend or transform behavior are rejected.

Image paths must resolve unambiguously within the permitted folder. If several files share a possible name or a path crosses the allowed boundary, the importer stops instead of guessing. Enable external image access only for JSON files you trust.

## 17. Utility tools

### Switch Texture Format

Use this to point selected sprites to existing files with the same base name and a different supported extension.

1. Prepare the replacement files in advance, using the same base names and the intended PNG, TGA, or JPG extension.
2. Select the sprite objects to update.
3. Under **Utilities**, set **Reload Format**.
4. Click **Switch Texture Format**.
5. Review the Operation Report for skipped objects.

The tool does not convert image data or create replacement files. It only switches to an existing same-name file. Packed, unsaved, shared, or otherwise unsafe images can be skipped.

### Copy Shader Settings to Selected Objects

Use this to copy compatible unlinked Principled BSDF input values from one sprite material to other selected sprites while preserving their texture links.

1. Select the target objects first.
2. Select the source object last so it becomes active.
3. Click **Copy Shader Settings to Selected Objects**.
4. Review the result if the operation reports partial completion.

Only same-name Principled BSDF inputs with a compatible linked-input structure are copied. Connected inputs remain connected. The tool does not rebuild unrelated custom node systems.

### Merge Duplicate Materials

Select the intended sprite objects and click **Merge Duplicate Materials**.

The tool consolidates matching, unmodified materials created by the add-on when they can be shared safely. It recognizes standard `.001`-style duplicates. Custom or modified materials are skipped rather than merged by name alone.

### Restore Imported Material

Use this for a sprite created by one of the JSON import tools when its first material slot was removed or changed.

1. Select the imported sprite or sprites.
2. Click **Restore Imported Material**.
3. Review any prompt about shared mesh data or an external image folder.
4. Confirm only when the source JSON and image location are trusted.

The tool rebuilds the first material slot from the import information stored on the sprite. If the original JSON moved, the currently selected JSON path may be used as a fallback when it matches the imported asset.

### Isolate Selection

Select the objects you want to inspect and click **Isolate Selection** in the 3D View. Click the same button again to leave local view and restore the previous selection state.

Run the command from the 3D View. If another local-view state is already active, leave it before using the add-on's isolation toggle.

## 18. A practical checking order

When a normal operation does not complete:

1. read the visible message;
2. open **Operation Report**;
3. correct the first blocked condition;
4. confirm the intended **Project Collection**, current project, and project folder;
5. run **Test PS** again if Photoshop path, version, or execution mode changed;
6. confirm that project files remain on a local drive and texture dimensions are unchanged;
7. repeat the operation on a copy of the project when the problem may be asset-specific.

Use recovery buttons only when the report names the matching recovery state. For an unresolved problem, follow [Support](SUPPORT.md) and send a redacted report to **brandyspe2026@gmail.com**.
