# 2D Link 1.6.3 — 兼容性与购买检查清单

[产品主页](../README_zh-CN.md) · [快速入门](QUICK_START_zh-CN.md) · [用户指南](USER_GUIDE_zh-CN.md) · [技术支持](SUPPORT_zh-CN.md)

购买或安装前请阅读本页。2D Link 是面向多部件 2D 资产的 Blender–Adobe Photoshop 专用工作流，不是泛用型 2D 或 3D 管线套件。

## 快速判断是否适合

满足以下全部条件时，2D Link 通常适合你的工作流：

- 使用 Windows x64；
- 本地安装了 Adobe Photoshop 桌面版；
- 资产由平面矩形图像网格和矩形活动 UV 构成；
- 使用本地文件式 PNG、TGA、JPG 或 JPEG 贴图；
- 活动项目能够保存在普通本地文件系统中；
- 项目关联后可以保持贴图像素尺寸不变；
- 需要直接单贴图编辑，或在完整资产上下文中绘制后分别写回贴图。

如果你需要 macOS 或 Linux、非 Adobe 编辑器、逐笔刷实时串流、任意 3D 投射绘制、直接引擎导出，或完整 Spine 骨骼与动画导入，那么它不适合该需求。

2D Link 需要 Adobe Photoshop，但不包含 Photoshop。

## 精确实测矩阵

1.6.3 Windows x64 正式包完整测试了以下版本。

**Blender**

- Blender 4.2.21 LTS
- Blender 4.3.2
- Blender 4.4.3
- Blender 4.5.10
- Blender 5.0.1
- Blender 5.1.2

**Adobe Photoshop 桌面版**

- Adobe Photoshop CC 2017.1.6
- Adobe Photoshop 2020，版本 21.2.1
- Adobe Photoshop 2022，版本 23.5.0
- Adobe Photoshop 2025，版本 26.10.0
- Adobe Photoshop 2026，版本 27.7.0

当 Blender 完整版本和 Photoshop 年份及用户可见应用版本均列在上方，项目遵守文档化工作流，并且 **Test PS** 确认实际响应 Photoshop 的路径和版本时，该环境属于正式支持矩阵。

Adobe 内部构建号不作为购买或支持门槛。多版本 Photoshop 共存时，安装目录或快捷方式不能证明当前连接版本，请以 **Test PS** 结果为准。

## 安装范围与兼容候选

扩展清单允许 Blender 4.2.0 至 Blender 5.1.x，并在 Blender 5.2 系列之前截止。

安装范围内但未列入精确清单的稳定 Blender 版本，或 CC 2017–2026 世代中其他稳定 Photoshop 公开版本，属于兼容候选，而不是完整实测环境。能够安装、启动或显示界面，不代表完整核心工作流已经测试。

未来 Blender 或 Photoshop 版本只有在文档化工作流完成测试并更新矩阵后，才进入公开支持范围。

## Windows 自动化与存储

正常 **Auto** 执行模式会使用本地 Windows 和 Photoshop 自动化组件，包括 Windows Script Host（cscript.exe）、WMI 进程查询、Photoshop COM 自动化和 JSX 执行。

受管电脑、安全加固环境或企业策略可能阻止其中一个或多个组件。自动执行不可用时可以使用 **Manual Script**，但用户仍需具备从 Photoshop 运行 JSX 脚本的权限。

正式工作流要求活动项目位于普通本地硬盘。网络共享、NAS、虚拟文件系统、符号链接、目录联接和延迟同步目录不在支持的存储模型内，因为文件锁、时间戳或写入完成状态可能不稳定。

## 资产要求

每个目标项目部件应使用：

- 本地文件式 PNG、TGA、JPG 或 JPEG 贴图；
- 平面矩形网格；
- 有效的矩形活动 UV；
- 唯一基础名称；
- 一致的 2D 平面朝向。

只要外边界保持矩形，内部网格细分可以存在。可以使用深度偏移表现视觉层级。

文档化材质来源是材质顶层节点树中的普通 Image Texture。隐藏在任意自定义 Shader Node Group 内的 Image Texture 不属于公开支持来源。

项目匹配会忽略 “.001” 这类 Blender 数字后缀。经过后缀处理后，各名称仍需能够形成清晰且唯一的项目身份。

请在创建 2D Link 项目前调整贴图画布。关联后必须保持像素宽高不变。

## 工作流边界

- 2D Link 在项目贴图保存后刷新文件，不是逐笔刷实时串流。
- 仅保存关联 PSD/PSB 只会保存工作文档，不会更新所有项目贴图。
- 多贴图写回使用 “Brandy | Merge Layers” 中可见、顶层、名称匹配的图层。
- 三个保留组和生成的智能对象变换必须保持不变。
- 需要反复编辑与保存时推荐 PNG 或 TGA。
- JPG 和 JPEG 受到支持，但重复保存可能因有损压缩降低质量。
- 静态 PhotoshopToSpine 和 Spine2D JSON 工具是可选工具，不是产品核心用途。
- Spine2D 支持仅限受支持的静态 Region Attachments，不导入完整骨骼、动画、Mesh Attachments、约束、序列或双色 Tint。
- JSON 外部图像目录需要明确授权，同名文件存在歧义时插件不会猜测。
- 插件不替代独立备份、版本管理、可靠存储或专业数据恢复。

## 购买前检查

- [ ] 我使用 Windows x64。
- [ ] 我已经本地安装 Adobe Photoshop 桌面版，并理解产品不包含 Photoshop。
- [ ] 我的 Blender 和 Photoshop 公开版本位于实测矩阵中，或者我接受兼容候选环境。
- [ ] 安装多个 Photoshop 版本时，我会使用 **Test PS** 确认实际响应的路径和版本。
- [ ] 我的系统允许所选执行模式需要的自动化功能。
- [ ] 活动 2D Link 项目会保存在普通本地文件系统中。
- [ ] 我的资产使用平面矩形图像网格和受支持的文件式贴图。
- [ ] 项目关联后，我会保持贴图尺寸不变。
- [ ] 我理解单贴图快速编辑、保存关联 PSD/PSB 和显式 Merge Layers 写回之间的区别。
- [ ] 我理解可选 JSON 工具只支持有限静态范围。
- [ ] 我会为生产文件保留独立备份。
- [ ] 我已经阅读购买平台的支持、更新、退款和账户条款。

## 正式发行包、许可证与平台政策

2D Link 正式插件包以 **GPL-3.0-or-later** 分发，并包含对应源码文件和许可证文本。

购买提供的是经过正式测试的发行包，以及销售平台说明的支持或更新服务。本仓库不承诺终身更新、终身支持或未来宿主版本兼容性。

支付、收据、税务或 VAT、下载权限、退款和平台账户问题由实际购买平台处理。退款决定仍以对应平台政策和适用法律为准。

## 独立产品声明

2D Link 是独立产品，与 Blender Foundation、Adobe、Unity Technologies、Epic Games、Esoteric Software 或其产品不存在从属、认可、赞助或官方关联关系。

Blender 是 Blender Foundation 的商标。Adobe 和 Photoshop 是 Adobe 在美国和/或其他国家或地区的注册商标或商标。Unity 是 Unity Technologies 或其关联公司的商标或注册商标。Unreal Engine 是 Epic Games, Inc. 的商标或注册商标。Spine 是 Esoteric Software LLC 的商标。
