# Brandy 2D Link 1.6.3 — User Guide

[Back to README](../README.md) · [Quick Start](QUICK_START.md) · [Compatibility Checklist](COMPATIBILITY_AND_PURCHASE_CHECKLIST.md) · [Support](SUPPORT.md)

## Document Purpose
This guide explains the normal Brandy 2D Link workflow and the most important boundaries for daily use.
It is written for artists, animators, and 2D game developers who want to use Photoshop and Blender together for sprite texture iteration.

For complete compatibility, purchase, license, and support terms, also read the README, Compatibility and Purchase Checklist, and Support Policy.
Adobe Photoshop is not included with Brandy 2D Link. A valid local desktop installation of Photoshop is required.

## 1. What Brandy 2D Link Does

Brandy 2D Link is a Blender add-on for a focused 2D game-art workflow between Blender and the Adobe Photoshop desktop application.

The main idea is simple: prepare sprite objects in Blender, create a Brandy project, edit the project textures in Photoshop, save the images, and reload the matching material textures in Blender.

The add-on is designed around predictable file handling, local project folders, operation reports, trusted backups, and low background overhead.
It is not a replacement for version control, independent project backups, or general Blender and Photoshop training.

The core workflow is:

1. Prepare static sprite objects and file-based textures in Blender.
2. Create or link a Brandy project folder.
3. Let the add-on create a linked PSD or PSB document with linked Smart Objects.
4. Edit and save the project texture files in Photoshop.
5. Reload textures in Blender manually or with Auto Reload.
6. When needed, use Merge Layers to paint in the full linked document and apply visible, name-matched artwork back to the source textures.

Saving only the linked PSD or PSB does not update Blender.
Blender reloads the individual texture files stored in the project `textures` folder.

## 2. Officially Supported Environment

The official Brandy 2D Link 1.6.3 package is supported for Windows x64 and the tested host versions listed below.

Tested Blender versions:

- Blender 4.2.21 LTS
- Blender 4.3.2
- Blender 4.4.3
- Blender 4.5.10
- Blender 5.0.1
- Blender 5.1.2

Tested Adobe Photoshop desktop versions:

- Adobe Photoshop CC 2017.1.6
- Adobe Photoshop 2020, version 21.2.1
- Adobe Photoshop 2022, version 23.5.0
- Adobe Photoshop 2025, version 26.10.0
- Adobe Photoshop 2026, version 27.7.0

Both applications should match the tested list for the official support matrix.
The Photoshop path and version shown by Test PS are the authoritative result when several Photoshop versions are installed.
An installed folder name or shortcut name alone does not prove which Photoshop instance is responding.

Use the desktop version of Photoshop with JSX scripting.
Photoshop web, Photoshop for iPad, macOS, Linux, beta or nightly host builds, and other image editors are not officially supported by this release.

The 1.6.3 extension manifest is capped before the Blender 5.2 series.
Stable versions inside the manifest range but outside the tested list should be treated as compatibility candidates, not as fully tested environments.

## 3. Install the Add-on

Keep the official Brandy 2D Link ZIP package intact.
Do not unzip it manually and do not install individual Python or JSX files.

In Blender:

1. Open **Edit > Preferences**.
2. Open the **Extensions** or **Get Extensions** area, depending on your Blender version.
3. Use the upper-right menu and choose **Install from Disk**.
4. Select the official Brandy 2D Link 1.6.3 ZIP file.
5. Enable Brandy 2D Link.
6. In a 3D View, press `N` and open the **Brandy** tab.

The panel title should show **Brandy 2D Link v1.6.3**.

The interface language can be set to Auto, English, or Chinese.
After changing the interface language, reload the add-on or restart Blender.

## 4. Prepare the Blender Asset

Brandy 2D Link works with one Blender collection as the project asset.
Put the sprite objects you want to link into that collection.
If the sprites are inside nested collections, enable **Include Child Collections**.

Each sprite should use a normal file-based image texture and behave like a flat rectangular 2D piece.
A good source sprite usually has:

- a file-based PNG, TGA, JPG, or JPEG texture;
- a flat rectangular mesh;
- a valid rectangular active UV area;
- a unique base name;
- a consistent 2D plane orientation.

Internal mesh subdivisions are allowed when the outer boundary remains rectangular.
Depth offsets may be used for visual stacking.

For the material, use a normal **Image Texture** node in the top level of the material node tree.
A direct **Base Color** connection is the clearest setup.
Image Texture nodes hidden inside custom Shader Node Groups are not the documented texture source.

Before creating a Brandy project, resize any source texture canvases that need a different pixel size.
After the project is linked, texture dimensions must stay the same.
Dimension changes are blocked instead of silently changing the layout.

Avoid these conditions:

- packed images;
- unsaved Blender image edits;
- source files with unstable or delayed cloud synchronization;
- project folders on network shares, NAS devices, symbolic links, directory junctions, or virtual filesystems;
- names such as face and face.001 when they do not represent clear unique project identities.

Save the .blend file before creating a production project when possible.
Keep an independent backup of important artwork.

## 5. Configure Photoshop

Open the **Photoshop Setup** panel.
Set **PS Executable** to the Photoshop application you want to use.
For the normal Windows workflow, leave **PS Execution Mode** on **Auto**.

Recommended setup steps:

1. Close other running Photoshop versions if several versions are installed.
2. Click **Open PS**.
3. Wait until Photoshop has fully started.
4. Close welcome screens, save dialogs, or other modal dialogs.
5. Return to Blender and click **Test PS**.

When **Test PS** succeeds, Blender shows the Photoshop version that responded.
This result matters more than the shortcut name or the installed folder label.

The panel separates the Photoshop connection status from the compatibility status.
A ready connection means Blender can communicate with the responding Photoshop instance.
A tested combination means the exact Blender version and Photoshop public version are in the published tested matrix.
A candidate notice is not a connection failure; it means that exact combination has not been added to the tested matrix.

On Windows, automatic mode depends on local Photoshop automation and Photoshop scripting being available on the system.
Managed computers, hardened security settings, or enterprise policies may block part of that workflow.
Manual Script mode remains available when automatic communication cannot be used.

## 6. Create a New Brandy Project

Under **Project Action**, choose **Create a New Project in This Folder**.
Set **Project Folder** to an empty local folder, or to a folder path that does not exist yet.
Set **Canvas Padding** only when you need extra transparent workspace around the complete linked document.
**Canvas Padding** does not change the texture size.

Click **Create Project** and keep Blender and Photoshop open until the task finishes.
Do not close either application while a project task is running.

During project creation, the add-on validates the collection, sprite layout, image files, and Photoshop project structure.
If validation finds a mismatch, the operation stops and writes an Operation Report.
Fix the reported issue and run project creation again.

After project creation succeeds:

- **Current Project** shows the new project name.
- **Linked Document** shows the generated PSD or PSB.
- The project folder contains a linked document, project metadata, task or layout data, and a `textures` folder.
- Blender references the project texture copies.

The original pre-project texture files are not modified by project creation.
Later Photoshop editing and Merge Layers write-back affect the project texture copies.

## 7. Edit One Texture and Reload It

The single-texture workflow is the most direct way to use Brandy 2D Link.

1. Select one sprite object in Blender.
2. Click **Edit Active Object's Texture in PS**.
3. Photoshop opens the project texture used by the active sprite.
4. Paint or edit the image.
5. Save the image without changing its pixel width or height.
6. Return to Blender.
7. Click **Reload Textures**.

Blender reloads the project image file and updates the material's image texture.
The material node setup is not rebuilt.
Only the image data is reloaded.

If the operation is blocked, open the Operation Report and follow the first safe action shown there.

## 8. Use Auto Reload

Auto Reload watches the project texture files and reloads a saved image after the file write becomes stable.
It is not a real-time brush preview.
It updates after Photoshop saves the file and Blender can safely read it.

Use Auto Reload when you want a smoother save-and-refresh loop.
Turn it off when you notice stutter, when you do not need automatic updates, or when you prefer manual control.
Reload Textures remains available for immediate manual reloads.

If Auto Reload does not update as expected, check these points:

- The edited file is inside the active project's `textures` folder.
- The image size did not change.
- The project is on a normal local filesystem.
- Photoshop finished saving the file.
- No modal dialog is blocking Photoshop.
- The Operation Report does not show an unsafe image state.

Auto Reload is designed for local files with stable timestamps.
It does not continuously calculate texture-file hashes in the background.
Sync drives, network shares, NAS devices, and tools that delay or preserve timestamps may delay change detection.

## 9. Understand the Linked Document

Click **Open Linked Document in Photoshop** to open the assembled PSD or PSB created by the Brandy project.

Inside the linked document, new projects use three reserved root groups:

- `Brandy | Linked Content`
- `Brandy | Merge Layers`
- `Brandy | Merged Layers`

`Brandy | Linked Content` contains linked Smart Objects managed by the add-on.
`Brandy | Merge Layers` is the workspace for visible artwork that you want to apply back to source textures.
`Brandy | Merged Layers` stores artwork after a successful apply operation.

Do not rename, delete, move, duplicate, or replace these reserved root groups.
Do not manually alter the linked Smart Object transforms.
Keep the Merge Layers group visible while checking artwork.
Do not create subgroups inside `Brandy | Merge Layers` for write-back artwork.

Saving only the linked PSD or PSB does not update Blender.
Blender reloads the individual texture files from the project's `textures` folder.

## 10. Paint in Context with Merge Layers

Use Merge Layers when you need the full assembled layout as painting context.
This is useful for broad repainting, pattern design across several sprite pieces, or redrawing part of a character while seeing the complete pose.

Basic steps:

1. Open the linked document in Photoshop.
2. Create a new visible layer directly inside `Brandy | Merge Layers`.
3. Paint the change in the linked document.
4. Rename the layer so it exactly matches the target sprite name.
5. Remember that name matching is case-sensitive.
6. Save the linked document.
7. Return to Blender.
8. Click **Apply "Merge Layers" to Source Textures**.

The add-on validates the linked document, then maps each visible, top-level, name-matched layer into the matching source texture.
Pixels outside that texture canvas are clipped.

After a successful apply operation, the processed artwork is moved from `Brandy | Merge Layers` to `Brandy | Merged Layers`.
The source texture is saved, the linked Smart Object is updated, and Blender reloads the affected image.

If one brush stroke needs to affect several sprites, duplicate the artwork layer.
Give each copy the exact name of one target sprite.
Place all copies directly inside `Brandy | Merge Layers`, save the linked document, and apply the merge from Blender.

For strict pixel-level work, especially with soft transparent edges across overlapping sprites, direct single-texture editing is still the most controlled method.
Merge Layers is a context-painting tool, not a replacement for careful per-texture pixel editing.

## 11. Undo the Latest Merge

After a successful apply operation, **Undo Last Merge** may become available.
This is a single project-level undo for the latest successful merge.

Use it immediately if the merge result is not what you expected.
Do not continue editing or saving new changes before using it.

When you click **Undo Last Merge**, the add-on checks the current files against the merge record.
If the files no longer match the recorded state, the command is refused.
This strict behavior is intentional because the tool should not overwrite a project state that has already changed.

## 12. Link or Switch to an Existing Project

One Blender collection can have more than one Brandy project folder, as long as the folders were created from the same compatible asset layout.
This is useful for alternate costumes, color sets, or texture variants.

To switch:

1. Set **Project Folder** to the existing Brandy project folder you want to use.
2. Under **Project Action**, choose **Link or Switch to an Existing Project**.
3. Check the **Pending Project Switch** line.
4. Confirm that it shows the current project folder and the target project folder you intend to use.
5. Click **Link or Switch Project**.

Before switching, the add-on validates sprite identity, order, layout, and texture dimensions.
If the selected project does not match the current Blender collection, the switch is stopped and the current project remains active.

## 13. Photoshop Settings and Reports

For normal daily work, most Photoshop Settings can stay at their default values.

**PS Execution Mode** normally stays on **Auto** for the Windows workflow.
Manual Script is available when automatic communication cannot be used.
It creates a task script that can be run in Photoshop through **File > Scripts > Browse**.

**PS Response Wait Limit** controls how long Blender waits continuously for a Photoshop task.
If a task takes longer than this limit, Blender switches to periodic checks.
This does not cancel Photoshop; it only changes how Blender waits for the task result.

When an operation fails, **Open Operation Report** is the first place to check.
It gives a readable summary of the problem and the next safe step.

**Open Task Log Folder** is mainly for deeper diagnostics or support.
Task logs may contain local paths, account names, project names, or other private information.
Review them before sharing.
This button may be unavailable when no task log exists.

## 14. Optional Import and Export Tools

The JSON tools are optional static-sprite extensions.
They do not change the main Photoshop save-and-refresh workflow.

**PhotoshopToSpine Import** reads a supported static PhotoshopToSpine JSON layout and builds textured sprite planes in Blender.
Choose the JSON file, texture format, and alpha settings that match your source images.
**Import Scale** converts pixel coordinates into Blender units.
**Sprite Z Spacing** separates imported sprites by order, making the layered layout easier to inspect.

**PhotoshopToSpine Export** writes the eligible current Blender layout to a compatible JSON file.
It exports the current Blender composition and does not modify the active Photoshop project.

**Spine2D Static Import** is a limited compatibility tool.
It builds a static setup-pose sprite layout from supported Region Attachments.
It is not a Spine animation importer.
It does not import Mesh Attachments, constraints, full skeleton animation, sequences, or two-color Tint.

For JSON workflows, keep image paths clear and close to the JSON folder when possible.
Only authorize an external image folder when you trust the JSON and know that its images are intentionally outside the JSON folder.
In Spine2D Static Import, leave **Allow External Image Folder** off by default unless that condition is true.

If image paths are missing, ambiguous, outside the allowed search root, or too broad to search safely, fix the JSON paths or use a smaller dedicated folder.
Import validation is designed to stop before creating Blender sprite data when required files cannot be resolved safely.
The add-on does not guess between multiple same-name image files.

## 15. Utility Tools

**Switch Texture Format**
Set **Reload Format** first, then click **Switch Texture Format** to redirect selected sprites to image files with the same base name and the selected supported extension.
For example, if a sprite currently uses a PNG file and a matching TGA file already exists beside it, you can switch the selected sprite to TGA.
This does not convert image data. The target file must already exist.
If a matching file is missing, the item is skipped or reported instead of being guessed.

**Copy Shader Settings to Selected Objects**
This copies compatible, unconnected shader input values from the active sprite to the other selected sprites.
Texture links are preserved.
Select the target sprites first, then select the source sprite last, so it becomes the active object.
This is most useful for clean sprites imported by the add-on, where the material node setup is consistent.

**Merge Duplicate Materials**
This consolidates matching unmodified materials created by the add-on, but only when they can be shared safely.
It is not intended to merge arbitrary custom materials.

**Restore Imported Material**
This rebuilds the first material slot of an imported sprite using the JSON and texture records stored during import.
Use it when an imported sprite material needs to be restored to its recorded imported setup.

**Isolate Selection**
This toggles Blender local view for selected objects in the current 3D View.
Click it once to isolate selected sprites.
Click it again to return to the previous view.
It is useful when you want to move or inspect a few sprites without changing global visibility in the scene.

## 16. Recovery Tools

Recovery tools are not normal daily workflow buttons.
Use **Open Operation Report** first and follow the specific safe action it recommends.

Preserve the project folder, task folder, trusted backups, incomplete-project marker, and project lock until the state is understood.
Do not manually delete locks, task state, backup records, or recovery markers while Photoshop may still be writing files.

**Recover Incomplete Project**
This appears only after interrupted project creation leaves a recoverable marker.
Use it when the panel or Operation Report indicates that an incomplete project can be recovered.

**Restore Source Textures from Backup**
This is for an interrupted write-back operation.
Close Photoshop completely before using it.
Use the built-in recovery action instead of replacing project files manually.

**Repair Part IDs**
This is a targeted repair tool.
Use it only when the Operation Report specifically says that the project metadata differs only in Part IDs.

These recovery tools are designed to avoid unsafe guessing.
If the current files no longer match the recorded state, a recovery or undo command may be refused.

## 17. Common Mistakes to Avoid

Do not unzip the add-on and install individual files.
Install the official ZIP package directly.

Do not create a Brandy project on a network share, NAS, delayed cloud-sync folder, symbolic link, directory junction, or virtual filesystem.
Use a normal local folder.

Do not change texture pixel dimensions after the project is linked.
Resize texture canvases before creating the Brandy project.

Do not rename or reorganize the three reserved root groups in the linked document.
They are part of the project protocol.

Do not expect saving only the linked PSD or PSB to update Blender.
Blender reloads the individual texture files in the project `textures` folder.

Do not use Merge Layers as a replacement for strict pixel-level work across overlapping transparent edges.
For the most controlled pixel work, edit the individual source texture directly.

Do not use **Repair Part IDs**, **Restore Source Textures from Backup**, or **Recover Incomplete Project** unless the project state or Operation Report calls for them.

Do not share raw logs before checking them.
Reports and task logs may contain private paths, account names, project names, or unpublished artwork references.

## 18. Before Requesting Support

Before sending a support request, confirm that:

- the official unmodified package is installed;
- both host applications match the exact tested matrix, or you understand that the environment is a compatibility candidate;
- Test PS shows the intended Photoshop path and version;
- the project is on a local filesystem;
- texture dimensions were not changed;
- the issue can be reproduced in a copy of the project.

Send one issue per message and include:

- Brandy 2D Link version;
- full Blender version;
- Photoshop year and user-visible application version;
- Windows version;
- Photoshop path and version shown by Test PS;
- exact reproduction steps;
- expected result;
- actual result and complete visible error;
- a reviewed copy of BRANDY_2D_LINK_Last_Report, when available.

Remove private paths, account names, customer names, unpublished artwork, credentials, and payment information before sending files.

The first-response target is 3 calendar days.
Complex reports may require reproduction details or follow-up checks.
Complex issues may require reproduction, additional information, or confirmation on more than one application version.

## 19. Recommended Learning Order

If you are new to Brandy 2D Link, learn it in this order:

1. Install the add-on.
2. Prepare one clean Blender collection with a few sprite planes.
3. Set Photoshop path and run Test PS.
4. Create a new local Brandy project.
5. Edit one texture in Photoshop and reload it in Blender.
6. Enable Auto Reload only after manual reload works.
7. Open the linked document and understand the three reserved groups.
8. Try one simple Merge Layers operation.
9. Test Undo Last Merge immediately after that merge.
10. Learn project switching with a copied test project.
11. Use JSON import/export and utility tools only when your pipeline needs them.
12. Use recovery tools only when the Operation Report or project state calls for them.

This order keeps the first test small and predictable.
Once the basic save-and-refresh loop is working, the rest of the workflow is easier to understand.
