# Brandy 2D Link 1.6.3 — 快速入门

本指南覆盖安装和第一次正常贴图编辑循环。完整工作流、功能边界、恢复工具和常见错误，请阅读[用户指南](USER_GUIDE_zh-CN.md)。

## 1. 确认环境

1.6.3 版本的正式支持范围限于 Windows x64 和以下已测试版本。

**Blender**

- 4.2.21 LTS
- 4.3.2
- 4.4.3
- 4.5.10
- 5.0.1
- 5.1.2

**Adobe Photoshop 桌面版**

- CC 2017.1.6
- 2020，version 21.2.1
- 2022，version 23.5.0
- 2025，version 26.10.0
- 2026，version 27.7.0

正式支持矩阵要求两个应用都匹配清单。1.6.3 扩展清单将兼容范围限制在 Blender 5.2 系列之前。

请使用支持 JSX 脚本的 Photoshop 桌面版。Photoshop Web、Photoshop iPad 版、macOS、Linux、Beta/Nightly 宿主程序和其他图像编辑器不在正式支持范围内。

## 2. 安装插件

1. 保持官方 Brandy 2D Link ZIP 包完整。
2. 在 Blender 中打开 **Edit > Preferences > Extensions**。
3. 打开右上角菜单，选择 **Install from Disk**。
4. 选择官方 ZIP。
5. 启用 **Brandy 2D Link**。
6. 在 3D View 中按 `N`，打开 **Brandy** 标签。

面板标题应显示 **Brandy 2D Link v1.6.3**。

不要解压 ZIP 后安装单独的 Python 或 JSX 文件。

## 3. 准备 Blender 资产

1. 将一个资产的精灵对象放入同一个 Blender 集合。
2. 在 **Project Collection** 中选择该集合。
3. 如果资产使用嵌套集合，启用 **Include Child Collections**。
4. 保存 `.blend` 文件。
5. 为重要美术文件保留独立备份。

每个精灵建议使用文件式 PNG、TGA、JPG 或 JPEG 贴图，平面矩形网格，有效矩形活动 UV 区域，唯一基础名称，以及一致的 2D 平面朝向。

生产项目不要使用打包图像、未保存的 Blender 图像编辑、不稳定云同步路径、网络共享、NAS、符号链接、目录联接或虚拟文件系统。

需要调整贴图画布尺寸时，请在创建 Brandy 项目前完成。项目关联后，贴图像素尺寸必须保持不变。

## 4. 配置并检测 Photoshop

1. 打开 **Photoshop Setup**。
2. 在 **PS Executable** 中设置 Photoshop 应用路径。
3. 正常 Windows 工作流下，**PS Execution Mode** 保持 **Auto**。
4. 点击 **Open PS**。
5. 等待 Photoshop 完全启动。
6. 关闭欢迎页、保存对话框或其他模态窗口。
7. 回到 Blender，点击 **Test PS**。

安装多个 Photoshop 版本时，请先关闭其他正在运行的版本。**Test PS** 显示的路径和版本才是判断实际响应实例的依据。快捷方式名称或安装文件夹名称本身不能证明当前连接的是哪个 Photoshop。

## 5. 创建 Brandy 项目

1. 在 **Project Action** 中选择 **Create a New Project in This Folder**。
2. 将 **Project Folder** 设置为空的本地文件夹，或尚不存在的文件夹路径。
3. 只有在完整关联文档周围需要额外透明空间时，才设置 **Canvas Padding**。
4. 点击 **Create Project**。
5. 任务完成前保持 Blender 和 Photoshop 打开。

创建成功后，**Current Project** 显示新项目名，**Linked Document** 显示生成的 PSD 或 PSB，项目文件夹内包含项目元数据和 `textures` 文件夹。

创建项目不会修改原始贴图文件。后续 Photoshop 编辑和 Merge Layers 写回影响的是项目贴图副本。

## 6. 编辑单张贴图并刷新

1. 在 Blender 中选择一个精灵对象。
2. 点击 **Edit Active Object's Texture in PS**。
3. 在 Photoshop 中编辑图像。
4. 保存时不要改变像素宽高。
5. 回到 Blender。
6. 点击 **Reload Textures**。

Blender 会重新载入项目图像文件并更新材质中的图像贴图，不会重建材质节点结构。

如果操作被阻止，打开 **Open Operation Report**，按第一条安全处理建议修正。

## 7. 使用 Auto Reload

启用 **Auto Reload**，然后在 Photoshop 中编辑并保存项目贴图。文件写入稳定后，Blender 会刷新保存后的图像。

Auto Reload 适合更顺畅的保存—检查循环。它不是实时笔刷预览。

如果没有更新，请确认编辑的文件位于活动项目的 `textures` 文件夹中，图像尺寸没有变化，项目位于普通本地文件系统，Photoshop 已完成保存，并且没有模态窗口阻塞 Photoshop。需要立即刷新时，使用 **Reload Textures**。

## 8. 理解关联文档

使用 **Open Linked Document in Photoshop** 打开关联 PSD/PSB。

关联文档包含三个保留根组：

- `Brandy | Linked Content`
- `Brandy | Merge Layers`
- `Brandy | Merged Layers`

不要重命名、复制、替换、移动或重新组织这些分组。不要手动修改链接智能对象的变换。

只保存关联 PSD/PSB 不会更新 Blender。Blender 刷新的是项目 `textures` 文件夹中的独立文件。

## 9. 使用 Merge Layers 进行整体参考绘制

1. 在 Photoshop 中打开关联文档。
2. 在 `Brandy | Merge Layers` 顶层直接创建可见绘画图层。
3. 不要把图层放进子组。
4. 将图层命名为目标精灵的精确名称，包括大小写。
5. 绘制需要的内容。
6. 保存关联文档。
7. 回到 Blender。
8. 点击 **Apply “Merge Layers” to Source Textures**。

插件会把每个可见、顶层、名称匹配的图层映射到对应源贴图。超出该贴图画布的像素会被裁切。

如果绘画内容跨越多个精灵，请为每个目标复制一份绘画图层，并分别命名为对应目标。

对于严格像素级工作，尤其是重叠精灵的柔和透明边缘，直接编辑单张贴图仍然是最可控的方法。

## 10. 撤销最近一次合并

成功应用后，**Undo Last Merge** 可能变为可用。

如果合并结果不正确，请立即使用。使用前不要继续编辑或保存新变化。

当当前文件与合并前记录状态不一致时，该命令会拒绝执行，这是有意的安全设计。

## 11. 关联或切换已有项目

**Link or Switch to an Existing Project** 只适合基于同一资产结构制作的兼容贴图套装，例如皮肤、配色、本地化贴图或损坏状态。

切换前，插件会验证精灵身份、顺序、布局和贴图尺寸。如果验证失败，当前项目会保持连接。

## 12. 报告与恢复

任何操作失败时，优先打开 **Open Operation Report**。

在状态确认前，请保留项目文件夹、任务文件夹、备份、不完整项目标记和项目锁。

- **Recover Incomplete Project** 只会在项目创建中断且留下可恢复标记后出现。
- **Restore Source Textures from Backup** 用于中断的写回操作。使用前请完全关闭 Photoshop。
- **Repair Part IDs** 只应在执行报告明确说明项目元数据仅 Part IDs 不一致时使用。
- **Open Task Log Folder** 主要用于深入诊断；没有任务日志时可能不可用。

Photoshop 仍可能写入文件时，不要手动删除锁、任务状态、备份记录或恢复标记。

## 13. 可选 JSON 与便捷工具

JSON 工具是可选静态精灵扩展，不改变 Photoshop 保存与 Blender 刷新的主工作流。

- **PhotoshopToSpine Import** 导入受支持的静态 JSON 布局。
- **PhotoshopToSpine Export** 导出符合条件的当前 Blender 布局，不修改活动 Photoshop 项目。
- **Spine2D Static Import** 仅限受支持的静态 Region Attachments。
- **Switch Texture Format** 将所选精灵重定向到另一种受支持格式的现有同名文件，不转换图像数据。
- **Copy Shader Settings to Selected Objects** 从活动对象复制兼容且未连接的着色器数值。
- **Merge Duplicate Materials** 在安全时合并匹配的生成材质。
- **Restore Imported Material** 根据存储的导入元数据重建第一个导入材质槽。
- **Isolate Selection** 切换当前视口的局部视图。

JSON 工作流中，尽量让图像路径清晰并靠近 JSON 文件夹。

## 14. 请求支持前

请确认安装的是未修改官方包，项目位于本地文件系统，Test PS 显示的是预期 Photoshop 路径和版本，贴图尺寸没有改变，并且问题可以在项目副本中复现。

每次只提交一个问题，并包含 Brandy 版本、完整 Blender 版本、Photoshop 年份和应用版本、Windows 版本、Test PS 结果、复现步骤、预期结果、实际结果、可见错误文字，以及可以提供时经过检查的 `BRANDY_2D_LINK_Last_Report`。

分享文件或报告前，请移除私人路径、账户名、客户名、未公开美术、凭据、支付信息和机密生产资料。
