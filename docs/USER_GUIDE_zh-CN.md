# 2D Link 1.6.3 — 用户指南

[产品主页](../README_zh-CN.md) · [快速入门](QUICK_START_zh-CN.md) · [兼容性](COMPATIBILITY_AND_PURCHASE_CHECKLIST_zh-CN.md) · [技术支持](SUPPORT_zh-CN.md) · [发行说明](RELEASE_NOTES.md)

本指南说明 2D Link 1.6.3 的完整文档化工作流。第一次使用时，请先完成[快速入门](QUICK_START_zh-CN.md)。

插件在 Blender 内显示为 **Brandy 2D Link**。本文保留英文 UI 名称，便于直接对应界面、Operation Report 和技术支持信息。

## 1. 工作流概览

2D Link 用于连接 Blender 与 Adobe Photoshop，面向由多张独立文件贴图构成的多部件 2D 资产。

核心项目流程是：

1. 在 Blender 中准备一个由图像贴图精灵平面组成的集合。
2. 创建或关联本地 2D Link 项目。
3. 直接编辑一张项目贴图，或打开完整组装资产的关联 PSD/PSB。
4. 在 Photoshop 中保存相关文件。
5. 使用 **Reload Textures** 或 **Auto Reload** 刷新单张项目贴图。
6. 需要把完整资产中的作品分发到多张贴图时，使用 'Brandy | Merge Layers'，并从 Blender 显式执行写回。

该工作流由保存触发，不会传输单独的笔刷操作。

保存关联 PSD/PSB 与把作品写回项目贴图是两个独立动作。这样可以避免普通文档保存意外修改多张贴图。

## 2. 支持环境

正式发行包适用于 Windows x64。扩展清单安装范围为 Blender 4.2.0 至 5.1.x，并要求支持 JSX 脚本的 Adobe Photoshop 桌面版。

完整实测 Blender 与 Photoshop 版本维护在[兼容性与购买检查清单](COMPATIBILITY_AND_PURCHASE_CHECKLIST_zh-CN.md)中。处于整体范围内但不在精确矩阵中的版本属于兼容候选。

Photoshop 网页版、iPad 版、macOS、Linux、非 Adobe 图像编辑器，以及 Beta 或 Nightly 宿主版本，不属于 1.6.3 正式支持范围。

正常自动工作流依赖 Windows Script Host、WMI、Photoshop COM 自动化和本地 JSX 执行。受管或安全加固电脑可能限制这些组件；本地策略允许 Photoshop JSX 时，仍可使用 **Manual Script**。

活动项目应位于普通本地文件系统。网络共享、NAS、虚拟文件系统、符号链接、目录联接和延迟同步目录不属于正式支持的存储模型。

## 3. 安装插件

1. 保持官方 2D Link ZIP 完整。
2. 在 Blender 中打开 **Edit > Preferences > Get Extensions** 或 **Extensions**。
3. 打开右上角菜单，选择 **Install from Disk**。
4. 选择完整官方 ZIP。
5. 启用 **Brandy 2D Link**。
6. 在 3D View 中按 'N'，打开 **Brandy** 标签。

面板标题应显示 **Brandy 2D Link v1.6.3**。

不要安装单独的 Python 或 JSX 文件，也不要把 GitHub 仓库 ZIP 当作插件安装包。

界面语言可以设置为 Auto、English 或 Chinese。更改语言后，请重新加载插件或重启 Blender。

## 4. 准备 Blender 资产

一个 Blender 集合代表一个项目资产。将目标精灵对象放入该集合；资产使用嵌套集合时，启用 **Include Child Collections**。

每个目标部件应使用：

- 本地文件式 PNG、TGA、JPG 或 JPEG 贴图；
- 平面矩形网格；
- 有效的矩形活动 UV；
- 唯一基础名称；
- 一致的 2D 平面朝向。

只要外边界保持矩形，内部网格细分可以存在。可以使用深度偏移表现视觉层级。

材质顶层节点树中应使用普通 Image Texture。直接连接 Base Color 是最清晰的设置。隐藏在任意自定义 Shader Node Group 中的 Image Texture 不属于文档化来源。

项目匹配会忽略 '.001' 这类 Blender 数字后缀。处理后，每个目标项目身份仍需保持唯一。

创建项目前：

- 保存 '.blend' 文件；
- 将所有源贴图保存为稳定的本地文件；
- 完成任何需要的贴图画布尺寸调整；
- 移除目标流程中的打包图像或未保存图像状态；
- 为重要美术保留独立备份。

项目关联后，贴图像素尺寸必须保持不变。尺寸不匹配会被拒绝，而不是静默接受并改变布局。

## 5. 配置 Photoshop

打开 **Photoshop Setup**，将 **PS Executable** 设置为需要使用的 Photoshop 应用程序。

推荐顺序：

1. 安装多个 Photoshop 版本时，关闭其他正在运行的版本。
2. 正常 Windows 工作流下，将 **PS Execution Mode** 保持为 **Auto**。
3. 点击 **Open PS**，或手动启动已配置的 Photoshop。
4. 等待 Photoshop 完全启动。
5. 关闭欢迎页、保存对话框或其他模态窗口。
6. 回到 Blender，点击 **Test PS**。

Ready 连接表示 Blender 能够与实际响应的 Photoshop 通信。**Test PS** 返回的路径和用户可见应用版本代表该实例。多版本共存时，快捷方式名称或安装目录标签不足以确认连接版本。

连接状态和兼容状态是两个不同概念。连接可以为 Ready，但精确宿主组合仍可能只是兼容候选。

### Manual Script 模式

自动通信被阻止时，展开 **Photoshop Settings**，把 **PS Execution Mode** 设置为 **Manual Script**。

再次执行所需操作，并按照屏幕提示找到生成的 JSX 文件。在 Photoshop 中选择 **File > Scripts > Browse** 并运行该文件。Photoshop 完成后回到 Blender。

Manual Script 只改变任务启动方式，不会取消文档、项目或文件验证要求。

## 6. 创建新项目

1. 将 **Project Collection** 设置为包含资产的集合。
2. 在 **Project Action** 中选择 **Create a New Project in This Folder**。
3. 将 **Project Folder** 设置为空的本地文件夹，或尚不存在的路径。
4. 只有完整组装文档需要额外透明工作区时才设置 **Canvas Padding**。
5. 点击 **Create Project**。
6. 任务完成前保持 Blender 和 Photoshop 打开。

Canvas Padding 只影响组装工作文档，不会调整单张项目贴图尺寸。

创建期间，2D Link 会验证集合、精灵布局、图像文件和 Photoshop 项目结构；把合格贴图复制到项目；重新连接 Blender 到项目副本；记录项目元数据；并创建关联 PSD 或 PSB。

Create Project 不会覆盖创建项目前的原始贴图文件。创建后，直接编辑、Auto Reload 和 Merge Layers 写回都会操作 2D Link 项目内的贴图文件。

成功后，**Current Project** 和 **Linked Document** 会显示对应值。不要手动重命名、移动或替换生成项目结构中的单个文件。

创建中止时，打开 **Open Operation Report**，修正第一条被阻止的条件后重新执行。在报告状态未确认前，保留不完整项目标记和任务状态。

## 7. 单贴图快速编辑

当修改只属于一张贴图时，使用单贴图快速编辑。

1. 在 Blender 中将目标精灵网格设为活动对象。
2. 点击 **Edit Active Object's Texture in PS**。
3. 在 Photoshop 中编辑打开的项目贴图。
4. 保存时不要改变像素宽高。
5. 回到 Blender。
6. 点击 **Reload Textures**。

Blender 会重新载入材质使用的图像数据，不会重建材质节点。

材质包含多张 Image Texture 时，插件需要通过受支持的直接连接或导入记录识别主要项目贴图。打开了错误贴图或没有打开贴图时，应检查材质和 Operation Report，不要手动重命名项目文件。

## 8. Auto Reload

Auto Reload 会监视活动项目中受支持的贴图文件，并在保存完成、文件写入稳定后刷新图像。

它用于更顺畅的绘制—保存—检查循环，不是实时笔刷预览，也不会在后台持续计算所有项目文件哈希。

Auto Reload 没有更新时：

- 确认编辑的文件位于活动项目 'textures' 目录；
- 确认文件名称和位置没有改变；
- 确认像素尺寸没有改变；
- 等待 Photoshop 完成保存；
- 关闭模态对话框；
- 查看 Operation Report；
- 使用 **Reload Textures** 立即手动刷新。

延迟时间戳、保持文件句柄或分阶段写入的存储与同步系统可能延迟或阻止检测。文档化工作流应使用普通本地存储。

## 9. 关联 PSD/PSB

点击 **Open Linked Document in Photoshop**，打开组装项目文档。

文档包含三个保留根组：

- 'Brandy | Linked Content' 包含由插件管理、表示项目贴图的关联智能对象。
- 'Brandy | Merge Layers' 包含准备显式写回的可见作品。
- 'Brandy | Merged Layers' 存放成功写回后的已处理作品。

不要重命名、移动、复制、替换或重新组织这些组。不要移动、旋转、翻转、扭曲或重新链接生成的智能对象。

普通绘画图层、参考、备注和临时内容可以留在保留组之外。保持保留结构清晰，验证才能区分插件管理内容与普通作品。

保存 PSD/PSB 只会保存工作文档。Blender 仍然刷新项目 'textures' 目录中的独立文件。

## 10. 完整资产绘制与写回

需要在绘制时查看接缝、重叠、对齐或相邻部件时，使用关联文档。

按以下方式准备作品：

1. 在 'Brandy | Merge Layers' 中直接创建或粘贴每个作品图层。
2. 保持所有目标图层可见。
3. 将每个图层命名为 'Brandy | Linked Content' 中目标的精确名称。
4. 不要在 'Brandy | Merge Layers' 中使用子组。
5. 保持该组为 100% 不透明度。
6. 组混合模式使用 Normal 或 Pass Through。
7. 保存 PSD/PSB。

名称匹配区分大小写。直接复制生成的目标名称比重新输入更安全。

一份作品跨越多个部件时，为每个目标复制一次作品，并分别使用对应目标名称。写回时，每个匹配图层会映射到目标，并裁切到该贴图画布。

然后回到 Blender：

1. 确认活动项目正确。
2. 点击 **Apply “Merge Layers” to Source Textures**。
3. 继续前阅读所有警告。
4. 等待 Photoshop 和 Blender 完成。
5. 图层被跳过或图像没有刷新时查看 Operation Report。

修改目标前，2D Link 会验证项目、关联文档、保留结构、目标映射、贴图尺寸、文件状态和操作状态，并为本次操作涉及的贴图建立经过验证的备份。

成功后，匹配的项目贴图会更新，已处理作品会移到 'Brandy | Merged Layers'，关联文档会保存，Blender 会尝试刷新受影响图像。

对于严格像素级工作，尤其是重叠部件之间的柔和透明边缘，直接编辑单张贴图仍然最可控。Merge Layers 是整体上下文绘制和分发工作流，不替代细致的逐贴图像素编辑。

## 11. Undo Last Merge

**Undo Last Merge** 是针对最近一次成功 Merge Layers 写回的单次项目级撤销。

结果错误时应立即使用，不要先继续编辑或保存目标文件。

命令会把当前项目文件与记录的恢复状态进行比对。文件再次改变或必要备份缺失时，撤销会被拒绝，以避免旧记录覆盖更新后的作品。

## 12. 关联、切换或移动项目

一个 Blender 集合可以使用多个基于同一资产结构创建的兼容 2D Link 项目，例如皮肤、配色、本地化变体或损伤状态。

关联或切换步骤：

1. 将 **Project Collection** 设置为目标集合。
2. 在 **Project Action** 中选择 **Link or Switch to an Existing Project**。
3. 将 **Project Folder** 设置为已有 2D Link 项目文件夹。
4. 检查 **Pending Project Switch**。
5. 点击 **Link or Switch Project**。

切换前，插件会验证部件身份、顺序、布局和贴图尺寸。验证失败时，当前项目保持活动状态。

整个项目文件夹移动后，请保持内部结构不变，在新位置选择该文件夹，并使用 **Link or Switch Project**。不要移动或重命名单个生成贴图后期待插件搜索整台电脑。

## 13. Photoshop Settings 与任务处理

日常使用中，大多数 **Photoshop Settings** 可以保持默认值。

**PS Execution Mode** 控制自动或手动启动任务。

**PS Response Wait Limit (s)** 控制 Blender 连续等待 Photoshop 任务结果的时长。达到限制不会取消 Photoshop，只会改变 Blender 的等待方式，转为周期性检查结果。

**Open Operation Report** 显示最近一次可读结果和安全的下一步。任务失败时应首先查看这里。

**Open Task Log Folder** 用于深入诊断和技术支持。没有任务日志时可能不可用。日志可能包含本地路径、账户名、项目名或未公开美术引用，分享前必须检查。

项目创建或写回期间不要关闭 Blender 或 Photoshop。Photoshop 仍可能写入文件时，不要强制清除任务状态或锁。

## 14. 报告与恢复工具

最近一次完整 Operation Report 也会保存到 Blender Text 数据块 'BRANDY_2D_LINK_Last_Report'。

恢复工具不是日常按钮。只有面板或 Operation Report 指明对应状态时才使用。

### Recover Incomplete Project

项目创建中断并留下可恢复标记后出现。保留项目文件夹和标记，关闭无关任务，并在收到提示时使用内置恢复动作。

### Restore Source Textures from Backup

用于中断的写回操作。使用前完全关闭 Photoshop。请使用内置动作，不要手动替换项目文件。

### Repair Part IDs

这是定向元数据修复。只有 Operation Report 明确说明项目仅在 Part IDs 上存在差异时使用。

恢复工具会有意避免猜测。当前文件不再匹配记录状态时，恢复操作可能被拒绝。

## 15. 可选 JSON 工作流

JSON 工具是次要的静态精灵工具，不改变核心 Photoshop 保存—刷新工作流。

### PhotoshopToSpine Import

导入受支持的静态 PhotoshopToSpine JSON 布局数据，并在 Blender 中创建带贴图的精灵平面。请根据源布局设置匹配的 JSON、贴图格式、Alpha 行为、导入比例和 Z 间距。

### PhotoshopToSpine Export

将符合条件的当前 Blender 布局导出为兼容 JSON，不修改活动 Photoshop 项目。

### Spine2D Static Import

从受支持的 Region Attachments 创建静态 setup-pose 布局。它不是 Spine 动画导入器，不导入 Mesh Attachments、约束、完整骨骼动画、序列或双色 Tint。

尽量让图像路径清晰并靠近 JSON 文件夹。只有 JSON 可信且图像有意位于外部时，才授权外部图像目录。默认关闭 **Allow External Image Folder**。

图像路径缺失、含糊、超出允许搜索根目录或搜索范围过大时，请修正 JSON 或使用更小的专用文件夹。插件会在创建精灵数据前停止，不会在多个同名图像之间猜测。

## 16. 便捷工具

### Switch Texture Format

先设置 **Reload Format**，再点击 **Switch Texture Format**，把所选精灵重定向到同基础名称、指定受支持扩展名的现有文件。

该工具不转换图像数据。匹配目标必须已经存在；缺失目标会被跳过或报告。

### Copy Shader Settings to Selected Objects

将活动精灵上兼容且未连接的着色器输入值复制到其他已选精灵，同时保留贴图链接。先选择目标精灵，最后选择源精灵，使其成为活动对象。

在插件创建的干净材质或节点结构一致的材质上，该工具最可预测。

### Merge Duplicate Materials

在能够安全共享时，合并插件创建的匹配且未修改材质。它不用于合并任意自定义材质。

### Restore Imported Material

根据导入期间保存的 JSON 与贴图记录，重建导入精灵的第一个材质槽。

### Isolate Selection

切换当前 3D View 中所选对象的 Blender 局部视图，适合在不改变全局可见性的情况下检查或移动少量精灵。

## 17. 常见错误

- 安装单独文件，而不是完整官方 ZIP。
- 把 GitHub 仓库 ZIP 当作插件安装包。
- 在网络共享、NAS、延迟同步目录、符号链接、目录联接或虚拟文件系统中创建活动项目。
- 项目关联后改变贴图像素尺寸。
- 重命名或重新组织保留组或生成项目文件。
- 期待保存关联 PSD/PSB 自动更新所有贴图。
- 把 Merge Layers 作品放进子组，或使用错误目标名称。
- 把 Merge Layers 当作处理重叠透明边缘的严格逐贴图像素工具。
- 没有 Operation Report 或匹配项目状态时使用恢复工具。
- 未检查私人信息就分享原始报告或日志。

## 18. 支持准备与学习顺序

请求支持前，请确认安装的是未修改的官方包，**Test PS** 显示预期 Photoshop 路径和版本，项目位于本地文件系统，贴图尺寸没有改变，并且问题可以在项目副本中复现。

报告内容和隐私要求见[技术支持政策](SUPPORT_zh-CN.md)。

推荐学习顺序：

1. 安装插件。
2. 在一个干净集合中准备小型资产副本。
3. 配置 Photoshop 并执行 **Test PS**。
4. 创建本地项目。
5. 完成一次单贴图快速编辑和手动刷新。
6. 手动刷新正常后再启用 Auto Reload。
7. 打开关联文档，识别三个保留组。
8. 完成一次简单的 Merge Layers 写回。
9. 写回后立即测试 **Undo Last Merge**。
10. 使用复制项目学习项目切换。
11. 只有管线需要时才使用 JSON 和便捷工具。
12. 只有 Operation Report 指明匹配状态时才使用恢复工具。

让首次测试保持小而明确，可以在涉及生产美术前更容易理解项目结构、保存行为和错误报告。
