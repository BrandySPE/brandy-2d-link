# 2D Link 1.6.3 — Quick Start

[Product Home](../README.md) · [User Guide](USER_GUIDE.md) · [Compatibility](COMPATIBILITY_AND_PURCHASE_CHECKLIST.md) · [Support](SUPPORT.md)

This guide covers the shortest path to a successful first roundtrip between Blender and Adobe Photoshop. Use a copied test asset rather than the only copy of production artwork.

## 1. Before You Begin

You need:

- Windows x64;
- Blender 4.2.0 through 5.1.x;
- Adobe Photoshop desktop with JSX scripting;
- local PNG, TGA, JPG, or JPEG texture files;
- a multi-part 2D asset built from image-textured planes.

Adobe Photoshop is required and is not included with 2D Link. See the [Compatibility and Purchase Checklist](COMPATIBILITY_AND_PURCHASE_CHECKLIST.md) for the exact tested versions and full support boundary.

For the easiest first test, use one Blender collection containing a few flat rectangular parts, with one clear local Image Texture for each intended part. PNG or TGA is recommended for artwork that will be saved repeatedly.

## 2. Install the Add-on

1. Download the official ZIP from the storefront where you purchased 2D Link.
2. Keep the package as a ZIP file.
3. In Blender, open **Edit > Preferences > Get Extensions** or **Extensions**, depending on the Blender version.
4. Open the upper-right menu and choose **Install from Disk**.
5. Select the complete official ZIP and enable **Brandy 2D Link**.
6. In a 3D View, press 'N' and open the **Brandy** tab.

The panel title should show **Brandy 2D Link v1.6.3**. Do not install individual Python or JSX files separately.

## 3. Connect Adobe Photoshop

1. In the **Brandy** tab, expand **Photoshop Setup**.
2. Set **PS Executable** to the Photoshop application you want to use.
3. Leave **PS Execution Mode** on **Auto** for the normal Windows workflow.
4. Start the configured Photoshop version, or click **Open PS**.
5. Wait until Photoshop has fully started and close any welcome screen or modal dialog.
6. Return to Blender and click **Test PS**.
7. Confirm that the panel shows **PS connection: Ready** and the expected Photoshop version.

2D Link does not automatically search for installed Photoshop versions. When several versions are installed, close the other running versions before testing. The path and version reported by **Test PS** identify the Photoshop instance that actually responds.

If automatic scripting is blocked by local security policy, expand **Photoshop Settings**, set **PS Execution Mode** to **Manual Script**, run the operation again, and follow the on-screen instruction to execute the generated JSX file through **File > Scripts > Browse** in Photoshop.

## 4. Prepare the Blender Asset

Place the parts belonging to one asset in a clear Blender collection. Enable **Include Child Collections** when the asset uses nested collections.

Before creating the project:

- save each intended texture as a local PNG, TGA, JPG, or JPEG file;
- use flat rectangular planes with rectangular active UVs and a consistent 2D orientation;
- give every intended part a unique base name;
- use a file-based Image Texture in the material's top-level node tree;
- save the '.blend' file;
- resize any texture canvas that needs to change before the project is created.

Blender numeric suffixes such as '.001' are ignored for project part matching. Internal mesh subdivisions are supported when the outer boundary remains rectangular.

After the project is created, keep each project texture's pixel width and height unchanged.

## 5. Create the Project

1. Set **Project Collection** to the collection containing the asset.
2. Under **Project Action**, choose **Create a New Project in This Folder**.
3. Set **Project Folder** to an empty local folder or a path that does not yet exist.
4. Set **Canvas Padding** only when the complete linked document needs extra transparent workspace. Padding does not resize the individual textures.
5. Click **Create Project**.
6. Keep Blender and Photoshop open until the task finishes.
7. Review **Open Operation Report** if creation does not succeed.

During project creation, 2D Link copies eligible textures into the new project, reconnects Blender to those project copies, records the asset-to-texture relationship, and creates the linked PSD or PSB.

**Create Project does not overwrite the original texture files.** After creation, the texture files inside the 2D Link project are the files used by this Blender–Photoshop roundtrip.

Do not manually rename or move individual files inside the generated project structure.

## 6. Complete a Quick Texture Edit

Use this workflow when one texture needs a direct correction.

1. Make the intended sprite mesh the active object in Blender.
2. Click **Edit Active Object's Texture in PS**.
3. Paint and save the texture in Photoshop without changing its pixel dimensions.
4. Return to Blender.
5. Click **Reload Textures**.

Blender reloads the project image file without rebuilding the material node setup.

After manual reload works, you can enable **Auto Reload** before saving. Auto Reload refreshes a supported project texture after the file write becomes stable; it does not transmit individual brush strokes.

## 7. Open the Full-Asset PSD/PSB

Use this workflow when you need the complete assembled asset as painting context.

1. Confirm that the correct 2D Link project is active.
2. Click **Open Linked Document in Photoshop**.
3. Paint with the assembled asset visible.
4. Save the PSD/PSB normally while you work.

The linked document contains three reserved root groups:

- 'Brandy | Linked Content' — linked Smart Objects representing the project textures;
- 'Brandy | Merge Layers' — visible artwork prepared for write-back;
- 'Brandy | Merged Layers' — processed artwork stored after a successful write-back.

Do not rename, move, duplicate, replace, or reorganize the reserved groups. Do not move, rotate, flip, distort, or relink the generated Smart Objects.

Ordinary painting layers, references, and notes can remain outside the reserved groups. Saving the PSD/PSB saves the working document but does not automatically update every project texture.

## 8. Write Artwork Back to the Textures

1. Create or paste artwork layers directly inside 'Brandy | Merge Layers'.
2. Keep each artwork layer visible.
3. Give each layer exactly the same name as its target in 'Brandy | Linked Content'.
4. Keep the artwork layers directly inside the group; do not use subgroups.
5. Keep 'Brandy | Merge Layers' at 100% opacity.
6. Use **Normal** or **Pass Through** as the group blend mode.
7. Save the PSD/PSB.
8. Return to Blender and confirm that the correct project is active.
9. Click **Apply “Merge Layers” to Source Textures**.
10. Review any warning before continuing, then wait for Photoshop and Blender to finish.

Names are case-sensitive. Copying target names from 'Brandy | Linked Content' is the safest method.

When artwork crosses several parts, duplicate the relevant artwork once for each target and name each copy after that target. During write-back, each matched layer is mapped to its target and clipped to that texture's canvas.

Before changing files, 2D Link validates the linked document and target textures and creates backups for the files involved. After a successful write-back, matching project textures are updated, processed artwork moves to 'Brandy | Merged Layers', the linked document is saved, and Blender attempts to refresh the affected images.

For strict pixel-level work, especially around soft transparent edges across overlapping parts, direct single-texture editing remains the most controlled method.

## 9. Undo the Latest Write-Back

Click **Undo Last Merge** to restore the most recent successful Merge Layers operation.

Use it before continuing to edit or save new changes. Undo is available only while the current project files still match the recovery state recorded by 2D Link. It may be refused after a target file has changed again or when a required backup is missing.

The built-in backup and undo features are additional safeguards. Continue to keep normal production backups.

## 10. Common First-Run Problems

### Test PS fails

- Check **PS Executable**.
- Start the configured Photoshop version.
- Close other running Photoshop versions.
- Close modal dialogs and run **Test PS** again.
- Use **Manual Script** mode when automatic scripting is blocked.

### Edit Active Object's Texture in PS opens no texture

- Confirm that the correct project is active.
- Make the intended mesh the active object.
- Confirm that the project texture file still exists.
- If the material contains several image textures, make sure one primary texture can be identified through a direct Base Color connection or supported import metadata.

### A saved texture does not update

- Confirm that you edited the texture inside the active project's 'textures' folder.
- Enable Auto Reload before saving, or click **Reload Textures**.
- Confirm that Photoshop did not save the file under a new name or location.
- Confirm that the pixel dimensions did not change.
- Remember that saving the linked PSD/PSB is different from saving an individual texture.

### Merge Layers are not applied

- Save the PSD/PSB first.
- Put visible artwork layers directly inside 'Brandy | Merge Layers'.
- Remove subgroups.
- Copy the exact target names from 'Brandy | Linked Content'.
- Keep target texture dimensions unchanged.
- Keep the Merge Layers group at 100% opacity with Normal or Pass Through blend mode.

## 11. Reports, Recovery, and Next Steps

When an operation fails, expand **Photoshop Settings** and click **Open Operation Report**. The latest complete report is also stored in the Blender Text data-block 'BRANDY_2D_LINK_Last_Report'.

Do not manually delete project locks, task state, backup records, or recovery markers while Photoshop may still be writing files. Use recovery tools only when the Operation Report recommends them.

Continue with the [User Guide](USER_GUIDE.md) for project switching, recovery tools, optional JSON workflows, utility tools, and detailed support preparation.

Before sharing a report, remove private paths, account names, project names, customer names, unpublished artwork references, credentials, and confidential production information.
