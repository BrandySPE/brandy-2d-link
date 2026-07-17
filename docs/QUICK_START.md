# 2D Link 1.6.3 — Quick Start

[Product Home](../README.md) · [User Guide](USER_GUIDE.md) · [Compatibility](COMPATIBILITY_AND_PURCHASE_CHECKLIST.md) · [Support](SUPPORT.md) · [简体中文](QUICK_START_zh-CN.md)

This guide completes two first-use checks:

1. edit one project texture in Photoshop and reload it in Blender;
2. write one artwork layer from the linked PSD/PSB back to its matching project texture.

Use a copy of a small asset for the first test.

## 1. Before you begin

You need:

- Windows x64;
- Blender 4.2.0 through 5.1.x;
- Adobe Photoshop desktop for Windows;
- a saved `.blend` file;
- one Blender Collection containing image-textured 2D parts;
- local PNG, TGA, JPG, or JPEG textures on a standard local drive.

PNG or TGA is recommended for the first test.

Each intended part must have a rectangular outer boundary, a rectangular active UV layout, the same 2D plane orientation as the other parts, and a unique base name. Blender suffixes such as `.001` are ignored during matching, so the remaining names must still be unique.

Use a file-based Image Texture in the material's top-level node tree. A direct connection to Principled BSDF Base Color is the clearest setup.

## 2. Install the add-on

1. Keep the purchased product package as a complete ZIP file.
2. In Blender, open **Edit > Preferences > Get Extensions** or **Extensions**.
3. Open the upper-right menu and choose **Install from Disk**.
4. Select the complete 2D Link ZIP.
5. Enable **Brandy 2D Link**.
6. In a 3D View, press `N` and open the **Brandy** tab.

The panel title should show **Brandy 2D Link v1.6.3**. Do not install the repository ZIP or individual Python or JSX files.

## 3. Connect Photoshop

1. Expand **Photoshop Setup**.
2. Set **PS Executable** to the Photoshop application you intend to use.
3. Start that Photoshop version, or click **Open PS**.
4. Wait until Photoshop has finished starting and close any modal dialog.
5. Click **Test PS**.
6. Confirm that the panel reports a ready connection and the expected Photoshop path and version.

When several Photoshop versions are installed, close the other versions before running **Test PS**.

## 4. Create a project

1. Set **Project Collection** to the Collection containing the asset.
2. Enable **Include Child Collections** only when intended parts are inside nested Collections.
3. Under **Project Action**, choose **Create a New Project in This Folder**.
4. Set **Project Folder** to an empty local folder or a path that does not yet exist.
5. Leave **Canvas Padding** at its default unless you need extra transparent space around the assembled PSD/PSB.
6. Click **Create Project** and wait for Blender and Photoshop to finish.

2D Link copies eligible textures into the project, reconnects Blender to those copies, and creates the linked PSD/PSB. The texture files used before project creation remain unchanged.

After creation, do not rename or move individual files inside the project. Keep every project texture at its current pixel width and height.

## 5. Complete one single-texture roundtrip

1. In Blender, make one intended sprite mesh the active object.
2. Click **Edit Active Object's Texture in PS**.
3. In Photoshop, make a visible change to the opened project texture.
4. Save the file without changing its name, location, width, or height.
5. Return to Blender and click **Reload Textures**.
6. Confirm that the edited texture updates on the object.

This confirms the direct Blender–Photoshop roundtrip. **Auto Reload** can be enabled after the manual reload works. It refreshes a project texture after a completed save; it does not stream brush strokes while you paint.

## 6. Prepare one Merge Layers write-back

1. In Blender, click **Open Linked Document in Photoshop**.
2. In the PSD/PSB, find these reserved groups:
   - **Brandy | Linked Content**
   - **Brandy | Merge Layers**
   - **Brandy | Merged Layers**
3. In **Brandy | Linked Content**, choose one target part and copy its exact layer name.
4. Create a visible artwork layer directly inside **Brandy | Merge Layers**.
5. Give the artwork layer the exact copied target name. Names are case-sensitive.
6. Keep the artwork layer directly inside the group; do not place it in a subgroup.
7. Keep **Brandy | Merge Layers** at 100% opacity with Normal or Pass Through blend mode.
8. Save the PSD/PSB.

Do not rename the reserved groups or move, transform, relink, or reorganize the generated Smart Objects in **Brandy | Linked Content**.

If the target project texture is already open in Photoshop, save it first and make sure it contains one artwork layer and no layer groups. Keep its pixel dimensions unchanged.

## 7. Apply the artwork to the project texture

1. Return to Blender and confirm that the intended project is still active.
2. Click **Apply “Merge Layers” to Source Textures**.
3. Review any Photoshop color-mode or JPG/JPEG warning before continuing.
4. Wait until both Photoshop and Blender have finished.
5. Confirm that the target project texture has changed in Blender.

In this command, **Source Textures** means the texture files inside the active 2D Link project, not the files used before the project was created.

After a successful write-back, the processed artwork moves to **Brandy | Merged Layers**, the linked document is saved, and Blender attempts to reload the affected image automatically. Use **Reload Textures** only when the Operation Report says the image was not reloaded or the Blender view has not refreshed.

To test recovery, click **Undo Last Merge** immediately after the successful write-back. Undo is refused after the affected project files no longer match the recorded recovery state.

## 8. When an operation stops

Read the message dialog and the first blocked condition in **Open Operation Report**. Correct that condition and repeat the operation. Do not use recovery tools or clear a project lock unless the panel or report tells you to do so.

For a problem that remains unresolved, follow the [Support](SUPPORT.md) page and send a redacted report to **brandyspe2026@gmail.com**.
