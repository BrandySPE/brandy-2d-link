# Brandy 2D Link 1.6.3 — 用户指南

[返回 README](../README_zh-CN.md) · [快速入门](QUICK_START_zh-CN.md) · [兼容性与购买检查](COMPATIBILITY_AND_PURCHASE_CHECKLIST_zh-CN.md) · [技术支持](SUPPORT_zh-CN.md)

## 文档用途

本指南说明 Brandy 2D Link 的正常工作流，以及日常使用中最重要的功能边界。

它面向希望将 Photoshop 与 Blender 结合起来进行精灵贴图迭代的画师、动画师和 2D 游戏开发者。

完整的兼容性、购买、许可证和支持条款，请同时阅读 README、兼容性与购买检查清单和技术支持政策。Brandy 2D Link 不包含 Adobe Photoshop。用户需要在本地安装有效的 Photoshop 桌面版。

## 1. Brandy 2D Link 能做什么

Brandy 2D Link 是一款 Blender 插件，聚焦 Blender 与 Adobe Photoshop 桌面版之间的 2D 游戏美术工作流。

它的基本思路很简单：在 Blender 中准备精灵对象，创建 Brandy 项目，在 Photoshop 中编辑项目贴图，保存图像，然后在 Blender 中手动刷新或使用 Auto Reload 刷新对应材质贴图。

插件围绕可预测的文件处理、本地项目文件夹、操作报告、可信备份和低后台开销设计。它不是版本控制、独立项目备份，也不是 Blender 或 Photoshop 基础教学的替代品。

核心流程是：

1. 在 Blender 中准备静态精灵对象和文件式贴图。
2. 创建或关联 Brandy 项目文件夹。
3. 让插件创建带链接智能对象的 PSD 或 PSB 文档。
4. 在 Photoshop 中编辑并保存项目贴图文件。
5. 在 Blender 中手动刷新，或使用 Auto Reload。
6. 需要时，使用 Merge Layers 在完整关联文档中绘制，并将可见、名称匹配的图层写回到源贴图。

只保存关联 PSD 或 PSB 不会更新 Blender。Blender 刷新的是项目 `textures` 文件夹中的独立贴图文件。

## 2. 官方支持环境

Brandy 2D Link 1.6.3 官方包支持 Windows x64 和以下已测试宿主版本。

**已测试 Blender 版本：**

- Blender 4.2.21 LTS
- Blender 4.3.2
- Blender 4.4.3
- Blender 4.5.10
- Blender 5.0.1
- Blender 5.1.2

**已测试 Adobe Photoshop 桌面版：**

- Adobe Photoshop CC 2017.1.6
- Adobe Photoshop 2020，version 21.2.1
- Adobe Photoshop 2022，version 23.5.0
- Adobe Photoshop 2025，version 26.10.0
- Adobe Photoshop 2026，version 27.7.0

正式支持矩阵要求两个应用都匹配测试清单。安装多个 Photoshop 版本时，**Test PS** 显示的路径和版本才是实际响应结果。安装文件夹名称或快捷方式名称本身不能证明当前连接的是哪个 Photoshop。

请使用支持 JSX 脚本的 Photoshop 桌面版。Photoshop Web、Photoshop iPad 版、macOS、Linux、Beta/Nightly 宿主构建和其他图像编辑器不在 1.6.3 版本正式支持范围内。

1.6.3 扩展清单将兼容范围限制在 Blender 5.2 系列之前。位于清单范围内但未列入精确测试清单的稳定版本，应视为兼容候选，而不是完整测试环境。

## 3. 安装插件

保持官方 Brandy 2D Link ZIP 包完整。不要手动解压，也不要安装单独的 Python 或 JSX 文件。

在 Blender 中：

1. 打开 **Edit > Preferences**。
2. 进入 **Extensions** 或 **Get Extensions** 区域，具体名称取决于 Blender 版本。
3. 使用右上角菜单，选择 **Install from Disk**。
4. 选择官方 Brandy 2D Link 1.6.3 ZIP 文件。
5. 启用 Brandy 2D Link。
6. 在 3D View 中按 `N`，打开 **Brandy** 标签。

面板标题应显示 **Brandy 2D Link v1.6.3**。

界面语言可以设置为 Auto、English 或 Chinese。切换界面语言后，请重新加载插件或重启 Blender。

## 4. 准备 Blender 资产

Brandy 2D Link 使用一个 Blender 集合作为项目资产。请将需要关联的精灵对象放入该集合。如果精灵位于嵌套集合中，启用 **Include Child Collections**。

每个精灵应使用普通文件式图像贴图，并表现为平面矩形 2D 部件。合适的源精灵通常具有：

- 文件式 PNG、TGA、JPG 或 JPEG 贴图；
- 平面矩形网格；
- 有效的矩形活动 UV 区域；
- 唯一基础名称；
- 一致的 2D 平面朝向。

只要外边界保持矩形，内部网格细分可以存在。可以使用深度偏移表现视觉层级。

材质方面，请在材质节点树的顶层使用普通 Image Texture 节点。直接连接到 Base Color 是最清晰的设置。隐藏在自定义 Shader Node Group 内部的 Image Texture 节点不属于文档化贴图来源。

创建 Brandy 项目前，请先调整需要改变尺寸的源贴图画布。项目关联后，贴图尺寸必须保持不变。尺寸变化会被阻止，而不是被静默接受并改变布局。

请避免以下情况：

- 打包图像；
- 未保存的 Blender 图像编辑；
- 位于不稳定或延迟云同步路径中的源文件；
- 位于网络共享、NAS、符号链接、目录联接或虚拟文件系统上的项目文件夹；
- `face` 和 `face.001` 这类不代表清晰唯一项目身份的命名。

创建生产项目前，尽可能先保存 `.blend` 文件，并为重要美术保留独立备份。

## 5. 配置 Photoshop

打开 **Photoshop Setup** 面板。将 **PS Executable** 设置为你要使用的 Photoshop 应用程序。正常 Windows 工作流下，**PS Execution Mode** 保持 **Auto**。

推荐步骤：

1. 如果安装了多个 Photoshop 版本，先关闭其他正在运行的版本。
2. 点击 **Open PS**。
3. 等待 Photoshop 完全启动。
4. 关闭欢迎页、保存对话框或其他模态窗口。
5. 回到 Blender，点击 **Test PS**。

Test PS 成功后，Blender 会显示实际响应的 Photoshop 版本。这个结果比快捷方式名称或安装文件夹标签更重要。

面板会分开显示 Photoshop 连接状态和兼容性状态。Ready 连接表示 Blender 能与实际响应的 Photoshop 通信。Tested combination 表示当前精确 Blender 版本和 Photoshop 公开版本已进入发布测试矩阵。Candidate 不是连接失败，而是表示该精确组合尚未加入测试矩阵。

Windows 自动模式依赖本地 Photoshop 自动化和 Photoshop 脚本功能。受管电脑、强化安全设置或企业策略可能阻止部分流程。无法使用自动通信时，可以使用 Manual Script 模式。

## 6. 创建新的 Brandy 项目

在 **Project Action** 中选择 **Create a New Project in This Folder**。将 **Project Folder** 设置为空的本地文件夹，或尚不存在的路径。只有在完整关联文档周围需要额外透明工作区时，才设置 **Canvas Padding**。Canvas Padding 不会改变贴图尺寸。

点击 **Create Project**，任务完成前保持 Blender 和 Photoshop 打开。项目任务执行时不要关闭任一应用。

项目创建期间，插件会验证集合、精灵布局、图像文件和 Photoshop 项目结构。如果验证发现不匹配，操作会停止并写入 Operation Report。请修正报告中的问题后重新创建项目。

创建成功后：

- **Current Project** 显示新项目名；
- **Linked Document** 显示生成的 PSD 或 PSB；
- 项目文件夹包含关联文档、项目元数据、任务或布局数据，以及 `textures` 文件夹；
- Blender 会引用项目贴图副本。

创建项目不会修改原始项目创建前贴图。之后的 Photoshop 编辑和 Merge Layers 写回会影响项目贴图副本。

## 7. 编辑单张贴图并刷新

单贴图工作流是 Brandy 2D Link 最直接的使用方式。

1. 在 Blender 中选择一个精灵对象。
2. 点击 **Edit Active Object's Texture in PS**。
3. Photoshop 会打开活动精灵使用的项目贴图。
4. 绘制或编辑图像。
5. 保存图像，不要改变像素宽度或高度。
6. 回到 Blender。
7. 点击 **Reload Textures**。

Blender 会重新载入项目图像文件，并更新材质的图像贴图。材质节点设置不会被重建，只有图像数据会重新载入。

如果操作被阻止，打开 Operation Report，并按照第一条安全处理建议执行。

## 8. 使用 Auto Reload

Auto Reload 会监视项目贴图文件，并在保存后的文件写入稳定后重新载入图像。它不是实时笔刷预览，而是在 Photoshop 保存文件且 Blender 能安全读取后更新。

需要更顺畅的保存—刷新循环时使用 Auto Reload。当出现卡顿、不需要自动更新，或希望手动控制时，请关闭它。**Reload Textures** 仍可用于立即手动刷新。

如果 Auto Reload 没有按预期更新，请检查：

- 编辑的文件是否位于活动项目的 `textures` 文件夹；
- 图像尺寸是否没有改变；
- 项目是否位于普通本地文件系统；
- Photoshop 是否已经完成保存；
- Photoshop 是否被模态窗口阻塞；
- Operation Report 是否显示了不安全图像状态。

Auto Reload 面向时间戳稳定的本地文件设计。它不会在后台持续计算贴图文件哈希。同步盘、网络共享、NAS，以及会延迟或保留时间戳的工具，可能导致变更检测延迟。

## 9. 理解关联文档

点击 **Open Linked Document in Photoshop**，打开 Brandy 项目创建的组装 PSD 或 PSB。

新项目的关联文档包含三个保留根组：

- `Brandy | Linked Content`
- `Brandy | Merge Layers`
- `Brandy | Merged Layers`

`Brandy | Linked Content` 包含插件管理的链接智能对象。`Brandy | Merge Layers` 是等待写回源贴图的可见绘画工作区。`Brandy | Merged Layers` 存放成功应用后的绘画内容。

不要重命名、删除、移动、复制或替换这些保留根组。不要手动修改链接智能对象的变换。检查绘画内容时保持 Merge Layers 组可见。不要在 `Brandy | Merge Layers` 内创建子组来承载写回图层。

只保存关联 PSD 或 PSB 不会更新 Blender。Blender 刷新的是项目 `textures` 文件夹中的独立贴图文件。

## 10. 使用 Merge Layers 在整体布局中绘制

当你需要把完整组装布局作为绘制参考时，使用 Merge Layers。它适合大范围重绘、跨多个精灵部件的图案设计，或在查看完整姿势时重绘角色局部。

基本步骤：

1. 在 Photoshop 中打开关联文档。
2. 在 `Brandy | Merge Layers` 中直接创建新的可见图层。
3. 在关联文档中绘制修改。
4. 将图层重命名为目标精灵的精确名称。
5. 注意名称匹配区分大小写。
6. 保存关联文档。
7. 回到 Blender。
8. 点击 **Apply “Merge Layers” to Source Textures**。

插件会验证关联文档，然后把每个可见、顶层、名称匹配的图层映射到对应源贴图。超出该贴图画布的像素会被裁切。

成功应用后，已处理的绘画内容会从 `Brandy | Merge Layers` 移到 `Brandy | Merged Layers`。源贴图会被保存，链接智能对象会更新，Blender 会重新载入受影响图像。

如果一笔绘画需要影响多个精灵，请复制绘画图层。每个副本命名为一个目标精灵的精确名称。所有副本都应直接放在 `Brandy | Merge Layers` 中，保存关联文档，然后在 Blender 中应用合并。

对于严格像素级工作，尤其是跨重叠精灵的柔和透明边缘，直接编辑单张源贴图仍然是最可控的方法。Merge Layers 是整体参考绘制工具，不是精细逐贴图像素编辑的替代品。

## 11. 撤销最近一次合并

成功应用后，**Undo Last Merge** 可能变为可用。这是针对最近一次成功合并的单次项目级撤销。

如果合并结果不符合预期，请立即使用。使用前不要继续编辑或保存新变化。

点击 **Undo Last Merge** 后，插件会根据合并记录检查当前文件。如果文件不再匹配记录状态，命令会被拒绝。这种严格行为是有意设计，用于避免覆盖已经改变的项目状态。

## 12. 关联或切换已有项目

只要项目文件夹来自同一兼容资产布局，一个 Blender 集合可以拥有多个 Brandy 项目文件夹。这适合备用服装、配色或贴图变体。

切换步骤：

1. 将 **Project Folder** 设置为想使用的已有 Brandy 项目文件夹。
2. 在 **Project Action** 中选择 **Link or Switch to an Existing Project**。
3. 检查 **Pending Project Switch** 行。
4. 确认其中显示的当前项目文件夹和目标项目文件夹正确。
5. 点击 **Link or Switch Project**。

切换前，插件会验证精灵身份、顺序、布局和贴图尺寸。如果所选项目与当前 Blender 集合不匹配，切换会停止，当前项目保持活动状态。

## 13. Photoshop 设置与报告

日常使用中，大多数 Photoshop Settings 可以保持默认值。

正常 Windows 工作流下，**PS Execution Mode** 通常保持 **Auto**。无法使用自动通信时，可以使用 **Manual Script**。该模式会创建任务脚本，可在 Photoshop 中通过 **File > Scripts > Browse** 运行。

**PS Response Wait Limit** 控制 Blender 连续等待 Photoshop 任务的时间。任务超过此限制时，Blender 会切换为周期性检查。这不会取消 Photoshop，只是改变 Blender 等待任务结果的方式。

操作失败时，优先查看 **Open Operation Report**。它会给出可读的问题摘要和下一步安全操作。

**Open Task Log Folder** 主要用于深入诊断或技术支持。任务日志可能包含本地路径、账户名、项目名或其他私人信息，分享前请检查。没有任务日志时，该按钮可能不可用。

## 14. 可选导入与导出工具

JSON 工具是可选静态精灵扩展，不改变主 Photoshop 保存—刷新工作流。

**PhotoshopToSpine Import** 读取受支持的静态 PhotoshopToSpine JSON 布局，并在 Blender 中创建带贴图的精灵平面。请选择与源图像匹配的 JSON 文件、贴图格式和 alpha 设置。**Import Scale** 将像素坐标转换为 Blender 单位。**Sprite Z Spacing** 根据顺序分离导入精灵，方便检查分层布局。

**PhotoshopToSpine Export** 将符合条件的当前 Blender 布局写出为兼容 JSON 文件。它导出当前 Blender 组合，不修改活动 Photoshop 项目。

**Spine2D Static Import** 是有限兼容工具。它从受支持的 Region Attachments 创建静态 setup-pose 精灵布局。它不是 Spine 动画导入器，不导入 Mesh Attachments、约束、完整骨骼动画、序列或 two-color Tint。

JSON 工作流中，尽量让图像路径清晰并靠近 JSON 文件夹。只有在信任 JSON 且明确知道图像有意位于 JSON 文件夹外部时，才授权外部图像文件夹。在 Spine2D Static Import 中，默认保持 **Allow External Image Folder** 关闭，除非满足上述条件。

如果图像路径缺失、含糊、位于允许搜索根目录之外，或搜索范围过大而无法安全处理，请修正 JSON 路径，或使用更小的专用文件夹。导入验证会在创建 Blender 精灵数据前停止。插件不会在多个同名图像之间猜测。

## 15. 便捷工具

**Switch Texture Format**：先设置 **Reload Format**，然后点击 **Switch Texture Format**，将所选精灵重定向到同基础名称、指定扩展名的现有图像文件。例如，当前使用 PNG 的精灵旁边已经存在同名 TGA 文件，就可以切换到 TGA。该功能不转换图像数据，目标文件必须已经存在。缺失的匹配文件会被跳过或报告，而不会被猜测。

**Copy Shader Settings to Selected Objects**：将活动精灵上兼容且未连接的着色器输入值复制到其他已选精灵。贴图链接会保留。先选择目标精灵，最后选择源精灵，使其成为活动对象。该工具最适合插件导入的干净精灵，因为这些材质节点结构一致。

**Merge Duplicate Materials**：在可以安全共享时，合并插件生成的匹配且未修改材质。它不用于合并任意自定义材质。

**Restore Imported Material**：根据导入期间记录的 JSON 和贴图记录，重建导入精灵的第一个材质槽。当导入精灵材质需要恢复到记录的导入设置时使用。

**Isolate Selection**：切换当前 3D View 中所选对象的 Blender 局部视图。点击一次独显所选精灵，再点击一次返回之前视图。它适合在不改变全局可见性的情况下移动或检查少量精灵。

## 16. 恢复工具

恢复工具不是日常工作流按钮。请优先查看 Operation Report，并遵循其中建议的安全操作。

在状态确认前，请保留项目文件夹、任务文件夹、可信备份、不完整项目标记和项目锁。Photoshop 仍可能写入文件时，不要手动删除锁、任务状态、备份记录或恢复标记。

**Recover Incomplete Project**：只会在项目创建中断并留下可恢复标记后出现。面板或 Operation Report 提示可以恢复不完整项目时使用。

**Restore Source Textures from Backup**：用于中断的写回操作。使用前请完全关闭 Photoshop。请使用内置恢复动作，而不是手动替换项目文件。

**Repair Part IDs**：这是定向修复工具。仅在 Operation Report 明确说明项目元数据只有 Part IDs 不一致时使用。

这些恢复工具设计上避免不安全猜测。如果当前文件不再匹配记录状态，恢复或撤销命令可能会被拒绝。

## 17. 常见错误

不要解压插件并安装单独文件。请直接安装官方 ZIP 包。

不要在网络共享、NAS、延迟云同步目录、符号链接、目录联接或虚拟文件系统上创建 Brandy 项目。请使用普通本地文件夹。

项目关联后不要改变贴图像素尺寸。需要调整画布时，请在创建 Brandy 项目前完成。

不要重命名或重新组织关联文档中的三个保留根组。它们是项目协议的一部分。

不要期待只保存关联 PSD 或 PSB 就能更新 Blender。Blender 刷新的是项目 `textures` 文件夹中的独立贴图文件。

不要把 Merge Layers 当作跨重叠透明边缘的严格像素级工具。最可控的像素编辑方式仍然是直接编辑单张源贴图。

不要在项目状态或 Operation Report 未要求时使用 Repair Part IDs、Restore Source Textures from Backup 或 Recover Incomplete Project。

分享原始日志前请先检查。报告和任务日志可能包含私人路径、账户名、项目名或未公开美术引用。

## 18. 请求支持前

发送支持请求前，请确认：

- 安装的是未修改的官方包；
- 两个宿主应用匹配精确测试矩阵，或者你理解当前环境只是兼容候选；
- Test PS 显示的是预期 Photoshop 路径和版本；
- 项目位于本地文件系统；
- 贴图尺寸没有改变；
- 问题可以在项目副本中复现。

每次只提交一个问题，并包含：

- Brandy 2D Link 版本；
- 完整 Blender 版本；
- Photoshop 年份与用户可见应用版本；
- Windows 版本；
- Test PS 显示的 Photoshop 路径和版本；
- 精确复现步骤；
- 预期结果；
- 实际结果和完整可见错误；
- 可以提供时，经过检查的 `BRANDY_2D_LINK_Last_Report`。

发送文件前，请移除私人路径、账户名、客户名、未公开美术、凭据和支付信息。

首次回复目标为 3 个自然日。复杂报告可能需要复现信息、补充说明或在多个应用版本上确认。

## 19. 推荐学习顺序

如果你第一次使用 Brandy 2D Link，建议按以下顺序学习：

1. 安装插件。
2. 准备一个只包含少量精灵平面的干净 Blender 集合。
3. 设置 Photoshop 路径并执行 Test PS。
4. 创建新的本地 Brandy 项目。
5. 在 Photoshop 中编辑一张贴图，并在 Blender 中刷新。
6. 手动刷新正常后，再启用 Auto Reload。
7. 打开关联文档，理解三个保留组。
8. 尝试一次简单的 Merge Layers 操作。
9. 在这次合并后立即测试 Undo Last Merge。
10. 用复制的测试项目学习项目切换。
11. 只有在管线确实需要时，再使用 JSON 导入/导出和便捷工具。
12. 只有在 Operation Report 或项目状态要求时，才使用恢复工具。

这个顺序能让第一次测试保持小而可控。基础保存—刷新循环正常后，其余工作流会更容易理解。
