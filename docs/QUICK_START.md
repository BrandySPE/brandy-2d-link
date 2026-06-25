# Brandy 2D Link 1.6.3 — Quick Start

This guide covers installation and the first normal texture-editing loop. For the complete workflow, feature boundaries, recovery tools, and common mistakes, read the [User Guide](USER_GUIDE.md).

## 1. Confirm the Environment

Official support for version 1.6.3 is limited to Windows x64 and the tested versions below.

**Blender**

- 4.2.21 LTS
- 4.3.2
- 4.4.3
- 4.5.10
- 5.0.1
- 5.1.2

**Adobe Photoshop desktop**

- CC 2017.1.6
- 2020, version 21.2.1
- 2022, version 23.5.0
- 2025, version 26.10.0
- 2026, version 27.7.0

Both applications should match the list for the official support matrix. The 1.6.3 extension manifest is capped before the Blender 5.2 series.

Use the desktop version of Photoshop with JSX scripting. Photoshop web, Photoshop for iPad, macOS, Linux, beta/nightly host builds, and other image editors are not officially supported.

## 2. Install the Add-on

1. Keep the official Brandy 2D Link ZIP intact.
2. In Blender, open **Edit > Preferences > Extensions**.
3. Open the upper-right menu and choose **Install from Disk**.
4. Select the official ZIP.
5. Enable **Brandy 2D Link**.
6. In a 3D View, press `N` and open the **Brandy** tab.

The panel title should show **Brandy 2D Link v1.6.3**.

Do not unzip the package and install individual Python or JSX files.

## 3. Prepare the Blender Asset

1. Put the sprites for one asset in one Blender collection.
2. Set that collection under **Project Collection**.
3. Enable **Include Child Collections** if the asset uses nested collections.
4. Save the `.blend` file.
5. Keep an independent backup of important artwork.

Each sprite should use a file-based PNG, TGA, JPG, or JPEG texture, a flat rectangular mesh, a valid rectangular active UV area, a unique base name, and a consistent 2D plane orientation.

Do not use packed images, unsaved Blender image edits, unstable cloud-sync paths, network shares, NAS devices, symbolic links, directory junctions, or virtual filesystems for production projects.

Resize texture canvases before creating a Brandy project. After the project is linked, texture pixel dimensions must stay the same.

## 4. Configure and Test Photoshop

1. Open **Photoshop Setup**.
2. Set the Photoshop application path under **PS Executable**.
3. Leave **PS Execution Mode** on **Auto** for the normal Windows workflow.
4. Click **Open PS**.
5. Wait until Photoshop has fully started.
6. Close welcome screens, save dialogs, or other modal dialogs.
7. Return to Blender and click **Test PS**.

When several Photoshop versions are installed, close other running versions first. The path and version shown by **Test PS** are authoritative. A shortcut name or installed folder alone does not prove which Photoshop instance is responding.

## 5. Create a Brandy Project

1. Under **Project Action**, choose **Create a New Project in This Folder**.
2. Set **Project Folder** to an empty local folder, or to a folder path that does not exist yet.
3. Set **Canvas Padding** only when extra transparent workspace is needed around the complete linked document.
4. Click **Create Project**.
5. Keep Blender and Photoshop open until the task finishes.

After creation succeeds, **Current Project** shows the new project name, **Linked Document** shows the generated PSD or PSB, and the project folder contains project metadata plus a `textures` folder.

The original pre-project texture files are not modified by project creation. Later Photoshop editing and Merge Layers write-back affect the project texture copies.

## 6. Edit One Texture and Reload It

1. Select one sprite object in Blender.
2. Click **Edit Active Object's Texture in PS**.
3. Edit the image in Photoshop.
4. Save without changing the pixel width or height.
5. Return to Blender.
6. Click **Reload Textures**.

Blender reloads the project image file and updates the material's image texture. The material node setup is not rebuilt.

If the operation is blocked, open **Open Operation Report** and follow the first safe action shown there.

## 7. Use Auto Reload

Enable **Auto Reload**, then edit and save a project texture in Photoshop. Blender refreshes the saved image after the file write becomes stable.

Auto Reload is useful for a smoother save-and-check loop. It is not a real-time brush preview.

If nothing updates, confirm that the edited file is inside the active project's `textures` folder, the image size did not change, the project is on a normal local filesystem, Photoshop finished saving the file, and no modal dialog is blocking Photoshop. Use **Reload Textures** for an immediate manual reload.

## 8. Understand the Linked Document

Open it with **Open Linked Document in Photoshop**.

The linked PSD/PSB contains three reserved root groups:

- `Brandy | Linked Content`
- `Brandy | Merge Layers`
- `Brandy | Merged Layers`

Do not rename, duplicate, replace, move, or reorganize these groups. Do not manually alter the linked Smart Object transforms.

Saving only the linked PSD/PSB does not update Blender. Blender reloads the individual files in the project `textures` folder.

## 9. Paint in Context with Merge Layers

1. Open the linked document in Photoshop.
2. Create a visible artwork layer directly at the top level of `Brandy | Merge Layers`.
3. Do not place it inside a subgroup.
4. Name the layer exactly like the target sprite, including case.
5. Paint the required change.
6. Save the linked document.
7. Return to Blender.
8. Click **Apply “Merge Layers” to Source Textures**.

The add-on maps each visible, top-level, name-matched layer into the matching source texture. Pixels outside that texture canvas are clipped.

For artwork crossing several sprites, duplicate the artwork layer once per target and name each copy after its target.

For strict pixel-level work, especially around soft transparent edges across overlapping sprites, direct single-texture editing remains the most controlled method.

## 10. Undo the Latest Merge

After a successful apply operation, **Undo Last Merge** may become available.

Use it immediately if the merge result is wrong. Do not continue editing or saving new changes before using it.

The command is intentionally refused when the current files no longer match the recorded pre-merge state.

## 11. Link or Switch to an Existing Project

Use **Link or Switch to an Existing Project** only for compatible texture sets built from the same asset structure, such as skins, palettes, localization variants, or damage states.

Before switching, the add-on validates sprite identity, order, layout, and texture dimensions. If validation fails, the current project remains connected.

## 12. Reports and Recovery

Start with **Open Operation Report** whenever an operation fails.

Preserve the project folder, task folder, backups, incomplete-project marker, and project lock until the state is understood.

- **Recover Incomplete Project** appears only after interrupted project creation leaves a recoverable marker.
- **Restore Source Textures from Backup** is for an interrupted write-back operation. Close Photoshop completely before using it.
- **Repair Part IDs** should be used only when the Operation Report specifically says that the project metadata differs only in Part IDs.
- **Open Task Log Folder** is mainly for deeper diagnostics and may be unavailable when no task log exists.

Do not manually delete locks, task state, backup records, or recovery markers while Photoshop may still be writing files.

## 13. Optional JSON and Utility Tools

The JSON tools are optional static-sprite extensions. They do not change the main Photoshop save-and-refresh workflow.

- **PhotoshopToSpine Import** imports a supported static JSON layout.
- **PhotoshopToSpine Export** exports the eligible current Blender layout without modifying the active Photoshop project.
- **Spine2D Static Import** is limited to supported static Region Attachments.
- **Switch Texture Format** redirects selected sprites to existing matching files in another supported format. It does not convert image data.
- **Copy Shader Settings to Selected Objects** copies compatible unlinked shader values from the active object.
- **Merge Duplicate Materials** consolidates matching generated materials when safe.
- **Restore Imported Material** rebuilds the first imported material slot from stored import metadata.
- **Isolate Selection** toggles Blender local view for the current viewport.

For JSON workflows, keep image paths clear and close to the JSON folder when possible.

## 14. Before Requesting Support

Confirm that the official unmodified package is installed, the project is on a local filesystem, Test PS shows the intended Photoshop path and version, texture dimensions were not changed, and the issue can be reproduced in a copy of the project.

Send one issue per message and include the Brandy version, full Blender version, Photoshop year and application version, Windows version, Test PS result, reproduction steps, expected result, actual result, visible error text, and a reviewed copy of `BRANDY_2D_LINK_Last_Report` when available.

Remove private paths, account names, customer names, unpublished artwork, credentials, payment information, and confidential production data before sharing files or reports.
