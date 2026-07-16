# 2D Link 1.6.3 — 快速入门

[产品主页](../README_zh-CN.md) · [用户指南](USER_GUIDE_zh-CN.md) · [兼容性](COMPATIBILITY_AND_PURCHASE_CHECKLIST_zh-CN.md) · [技术支持](SUPPORT_zh-CN.md)

本指南提供 Blender 与 Adobe Photoshop 完成第一次成功往返的最短路径。首次测试请使用资产副本，不要直接使用唯一一份生产文件。

## 1. 开始前确认

你需要：

- Windows x64；
- Blender 4.2.0 至 5.1.x；
- 支持 JSX 脚本的 Adobe Photoshop 桌面版；
- 位于本地的 PNG、TGA、JPG 或 JPEG 贴图文件；
- 由图像贴图平面组成的多部件 2D 资产。

2D Link 需要 Adobe Photoshop，但不包含 Photoshop。精确实测版本和完整支持边界见[兼容性与购买检查清单](COMPATIBILITY_AND_PURCHASE_CHECKLIST_zh-CN.md)。

最简单的首次测试，是在一个 Blender 集合中放入少量平面矩形部件，并让每个目标部件都有一张明确的本地 Image Texture。需要反复保存时，推荐使用 PNG 或 TGA。

## 2. 安装插件

1. 从实际购买 2D Link 的销售平台下载官方 ZIP。
2. 保持安装包为 ZIP，不要解压。
3. 在 Blender 中打开 **Edit > Preferences > Get Extensions** 或 **Extensions**，具体名称取决于 Blender 版本。
4. 打开右上角菜单，选择 **Install from Disk**。
5. 选择完整官方 ZIP，并启用 **Brandy 2D Link**。
6. 在 3D View 中按 'N'，打开 **Brandy** 标签。

面板标题应显示 **Brandy 2D Link v1.6.3**。不要单独安装 Python 或 JSX 文件。

## 3. 连接 Adobe Photoshop

1. 在 **Brandy** 标签中展开 **Photoshop Setup**。
2. 将 **PS Executable** 设置为需要使用的 Photoshop 应用程序。
3. 正常 Windows 工作流下，将 **PS Execution Mode** 保持为 **Auto**。
4. 启动已配置的 Photoshop，或点击 **Open PS**。
5. 等待 Photoshop 完全启动，并关闭欢迎页或其他模态对话框。
6. 回到 Blender，点击 **Test PS**。
7. 确认面板显示 **PS connection: Ready** 和预期的 Photoshop 版本。

2D Link 不会自动搜索已安装的 Photoshop。安装多个版本时，测试前请关闭其他正在运行的版本。**Test PS** 返回的路径和版本，代表实际响应的 Photoshop 实例。

如果本机安全策略阻止自动脚本，请展开 **Photoshop Settings**，把 **PS Execution Mode** 设为 **Manual Script**，重新执行操作，并按照屏幕提示在 Photoshop 中通过 **File > Scripts > Browse** 运行生成的 JSX 文件。

## 4. 准备 Blender 资产

将同一资产的部件放入一个清晰的 Blender 集合。使用嵌套集合时，启用 **Include Child Collections**。

创建项目前请确认：

- 每张目标贴图已经保存为本地 PNG、TGA、JPG 或 JPEG；
- 部件使用平面矩形网格、矩形活动 UV 和一致的 2D 朝向；
- 每个目标部件都有唯一的基础名称；
- 材质顶层节点树中存在文件式 Image Texture；
- '.blend' 文件已经保存；
- 所有需要改变的贴图画布尺寸已在创建项目前调整完成。

项目部件匹配会忽略 '.001' 这类 Blender 数字后缀。只要外边界保持矩形，内部网格细分可以存在。

项目创建后，请保持每张项目贴图的像素宽高不变。

## 5. 创建项目

1. 将 **Project Collection** 设置为包含资产的集合。
2. 在 **Project Action** 中选择 **Create a New Project in This Folder**。
3. 将 **Project Folder** 设置为空的本地文件夹，或尚不存在的路径。
4. 只有完整关联文档需要额外透明工作区时才设置 **Canvas Padding**。Padding 不会改变单张贴图尺寸。
5. 点击 **Create Project**。
6. 任务完成前保持 Blender 和 Photoshop 打开。
7. 创建失败时查看 **Open Operation Report**。

项目创建期间，2D Link 会把合格贴图复制到新项目，重新连接 Blender 到这些项目副本，记录资产与贴图的关系，并创建关联 PSD 或 PSB。

**Create Project 不会覆盖原始贴图文件。** 项目创建后，该 2D Link 项目内部的贴图文件将用于后续 Blender–Photoshop 往返。

不要手动重命名或移动生成项目结构中的单个文件。

## 6. 完成一次单贴图快速编辑

当一张贴图需要直接修改时，使用这个工作流。

1. 在 Blender 中将目标精灵网格设为活动对象。
2. 点击 **Edit Active Object's Texture in PS**。
3. 在 Photoshop 中绘制并保存，不要改变像素尺寸。
4. 回到 Blender。
5. 点击 **Reload Textures**。

Blender 会重新载入项目图像文件，不会重建材质节点结构。

手动刷新正常后，可以在保存前启用 **Auto Reload**。Auto Reload 会在受支持的项目贴图写入稳定后刷新；它不会传输单独的笔刷操作。

## 7. 打开完整资产 PSD/PSB

需要在完整组装资产的上下文中绘制时，使用这个工作流。

1. 确认当前活动的是正确 2D Link 项目。
2. 点击 **Open Linked Document in Photoshop**。
3. 在完整资产可见的情况下绘制。
4. 工作过程中正常保存 PSD/PSB。

关联文档包含三个保留根组：

- 'Brandy | Linked Content' — 表示项目贴图的关联智能对象；
- 'Brandy | Merge Layers' — 准备写回的可见作品；
- 'Brandy | Merged Layers' — 成功写回后存放已处理作品。

不要重命名、移动、复制、替换或重新组织这些保留组。不要移动、旋转、翻转、扭曲或重新链接生成的智能对象。

普通绘画图层、参考和备注可以放在保留组之外。保存 PSD/PSB 只会保存工作文档，不会自动更新所有项目贴图。

## 8. 将作品写回贴图

1. 在 'Brandy | Merge Layers' 中直接创建或粘贴作品图层。
2. 保持每个作品图层可见。
3. 将每个图层命名为 'Brandy | Linked Content' 中对应目标的精确名称。
4. 图层必须直接位于该组内，不要使用子组。
5. 保持 'Brandy | Merge Layers' 为 100% 不透明度。
6. 组混合模式使用 **Normal** 或 **Pass Through**。
7. 保存 PSD/PSB。
8. 回到 Blender，确认活动项目正确。
9. 点击 **Apply “Merge Layers” to Source Textures**。
10. 出现警告时先阅读，再等待 Photoshop 和 Blender 完成任务。

名称匹配区分大小写。最安全的方法是直接从 'Brandy | Linked Content' 复制目标名称。

作品跨越多个部件时，为每个目标复制一份相关作品，并分别使用对应目标名称。写回期间，每个匹配图层会映射到目标贴图，超出目标画布的像素会被裁切。

修改文件前，2D Link 会验证关联文档和目标贴图，并为本次操作涉及的文件建立备份。成功写回后，匹配的项目贴图会更新，已处理作品会移到 'Brandy | Merged Layers'，关联文档会保存，Blender 会尝试刷新受影响图像。

对于严格像素级工作，尤其是重叠部件之间的柔和透明边缘，直接编辑单张贴图仍然最可控。

## 9. 撤销最近一次写回

点击 **Undo Last Merge** 可以恢复最近一次成功的 Merge Layers 操作。

请在继续编辑或保存新变化前使用。只有当前项目文件仍符合 2D Link 记录的恢复状态时，撤销才可用。目标文件再次改变或必要备份缺失时，操作可能被拒绝。

内置备份和撤销属于额外保护，生产文件仍应保留正常备份。

## 10. 常见首次运行问题

### Test PS 失败

- 检查 **PS Executable**。
- 启动已配置的 Photoshop 版本。
- 关闭其他正在运行的 Photoshop 版本。
- 关闭模态对话框，再次执行 **Test PS**。
- 自动脚本被阻止时使用 **Manual Script**。

### Edit Active Object's Texture in PS 没有打开贴图

- 确认当前项目正确。
- 将目标网格设为活动对象。
- 确认项目贴图文件仍然存在。
- 材质包含多张图像时，确保可以通过直接 Base Color 连接或受支持的导入元数据识别一张主要贴图。

### 保存贴图后 Blender 没有更新

- 确认编辑的是活动项目 'textures' 目录中的贴图。
- 在保存前启用 Auto Reload，或点击 **Reload Textures**。
- 确认 Photoshop 没有把文件另存到新名称或新位置。
- 确认像素尺寸没有改变。
- 注意保存关联 PSD/PSB 与保存单张贴图是两个不同动作。

### Merge Layers 没有应用

- 先保存 PSD/PSB。
- 将可见作品图层直接放在 'Brandy | Merge Layers' 中。
- 移除子组。
- 从 'Brandy | Linked Content' 复制精确目标名称。
- 保持目标贴图尺寸不变。
- 保持 Merge Layers 组为 100% 不透明度，并使用 Normal 或 Pass Through 混合模式。

## 11. 报告、恢复与下一步

操作失败时，展开 **Photoshop Settings**，点击 **Open Operation Report**。最近一次完整报告也会保存到 Blender Text 数据块 'BRANDY_2D_LINK_Last_Report'。

Photoshop 仍可能写入文件时，不要手动删除项目锁、任务状态、备份记录或恢复标记。只有 Operation Report 建议时才使用恢复工具。

项目切换、恢复工具、可选 JSON 工作流、便捷工具和完整支持准备见[用户指南](USER_GUIDE_zh-CN.md)。

分享报告前，请移除私人路径、账户名、项目名、客户名、未公开美术引用、凭据和机密生产信息。
