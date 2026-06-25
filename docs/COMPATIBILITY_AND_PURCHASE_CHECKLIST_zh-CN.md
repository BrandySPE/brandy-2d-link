# Brandy 2D Link 1.6.3——兼容性与购买检查清单

购买或安装前请先阅读。本插件是聚焦 Photoshop–Blender 工作流的工具，不是泛用型 2D 管线套件。

## 最低环境要求

正式支持边界要求：

- Windows x64。
- 本地安装、能够运行 JSX 脚本的 Adobe Photoshop 桌面版。
- 系统允许运行 Blender 扩展和 Photoshop JSX 脚本。
- 使用 Windows 自动模式时，系统允许 Windows Script Host（`cscript.exe`）、WMI 进程查询和 Photoshop COM 自动化。
- 项目文件位于普通本地文件系统。
- 项目关联后，源贴图像素宽高保持不变。

本插件不包含 Adobe Photoshop，需要用户自行具备有效的本地安装。

Windows 自动模式会使用 `cscript.exe`、WMI、Photoshop COM 自动化和本地 JSX 执行。在企业管理、权限受限或经过安全加固的系统中，这些组件可能被系统策略或安全软件禁用。自动模式不可用时，仍可使用 **Manual Script / 手动执行** 模式。

## 已完整测试并正式支持

以下声明适用于 Windows x64 正式发行包。Blender 按完整版本号核对；Photoshop 按年份与用户可见应用版本核对。Adobe 内部构建号不作为购买或技术支持门槛。

**Blender：**

- Blender 4.2.21 LTS
- Blender 4.3.2
- Blender 4.4.3
- Blender 4.5.10
- Blender 5.0.1
- Blender 5.1.2

**Adobe Photoshop 桌面版：**

- Adobe Photoshop CC 2017.1.6
- Adobe Photoshop 2020，版本 21.2.1
- Adobe Photoshop 2022，版本 23.5.0
- Adobe Photoshop 2025，版本 26.10.0
- Adobe Photoshop 2026，版本 27.7.0

当 Blender 精确版本与 Photoshop 公开版本均列在上方，项目遵守文档工作流限制，并且**检测 PS**确认实际响应 Photoshop 的路径和应用报告版本时，属于正式支持矩阵。多版本 Photoshop 共存时，不能仅凭已安装名称或快捷方式判断连接版本。**检测 PS**不读取 Adobe 内部构建号。

扩展清单将兼容范围限制在 Blender 5.2 系列之前，预期安装范围为 Blender 4.2.0 至 Blender 5.1.x。范围内其他稳定 Blender 版本，以及 CC 2017 至 2026 世代中的其他稳定 Photoshop 公开版本，属于兼容候选。允许安装、能够启动或显示界面，不等同于完成完整核心工作流测试，但未列入矩阵的稳定版本仍可联系技术支持沟通。

## 购买前检查

- [ ] 我使用 Windows x64。
- [ ] 我拥有本地安装的 Adobe Photoshop 桌面版。
- [ ] 我的 Blender 完整版本号，以及 Photoshop 年份与用户可见应用版本，均出现在实测列表中；或者我接受当前环境仅属于兼容候选。
- [ ] 多版本 Photoshop 共存时，我会运行**检测 PS**并核对实际响应程序的路径和应用报告版本。
- [ ] 使用自动模式时，我的系统允许 Windows Script Host、WMI、Photoshop COM 自动化和本地 JSX 执行。
- [ ] 我的项目文件会存放在普通本地硬盘目录中。
- [ ] 我理解不同 Blender 补丁版本或 Photoshop 公开版本属于矩阵外环境；Photoshop 内部构建号不作为支持门槛。
- [ ] 我理解未来 Blender 版本或 Photoshop 公开版本需要完成测试并公开列出后才进入支持范围。
- [ ] 我理解关联工作流中源贴图尺寸必须保持不变。
- [ ] 我理解插件不替代备份、版本管理、可靠存储或专业数据恢复。
- [ ] 我理解插件不提供 Photoshop 内部面板，也不使用 UXP。
- [ ] 我已经阅读功能边界，包括有限的 Spine2D 静态导入范围。
- [ ] 我理解 JSON 外部贴图目录需要按次明确授权，同名贴图存在多个候选时插件不会自动猜测。
- [ ] 我理解产品支持与更新服务以购买平台页面说明为准。

## 不在正式支持范围内

- macOS 和 Linux。
- Blender 4.2.0 之前、Blender 5.2.0 及之后的版本。
- 未列入实测列表的 Blender 版本或 Photoshop 公开版本，包括兼容候选。
- Photoshop CC 2017.1.6 之前或 Photoshop 2026 27.7.0 之后的版本。
- Photoshop 网页版或 iPad 版。
- 非 Adobe 图像编辑器。
- Blender 或 Photoshop 的 Beta、Alpha、Nightly、测试通道或其他预发布版本。
- 依赖网络共享、NAS、虚拟文件系统、符号链接、目录联接或延迟同步行为的项目目录。
- 直接引擎导出、完整 Spine 动画导入、Mesh Attachment、约束、双色 Tint 或动画播放。
- 将任意自定义 Shader Node Group 作为公开文档工作流中的贴图来源。

无论插件包内部实现细节如何，正式支持范围仅以本文列出的平台和宿主版本为准。

## 工作流限制

- 插件在项目贴图文件保存后重新载入它们，不是逐笔刷实时串流。
- Blender 重新载入的是活动项目 `textures` 目录中的文件。只保存关联 PSD/PSB 不会更新 Blender。
- 关联文档中的保留分组不能重命名、复制、替换、移动或重新组织。
- Merge Layers 写回使用 `Brandy | Merge Layers` 中可见、第一层级、名称匹配的图层。
- 项目关联后，源贴图尺寸不能改变。
- 需要反复无损绘制时，推荐 PNG 或 TGA。
- 自动刷新依赖稳定的本地文件时间戳。外部存储或同步工具导致检测延迟时，请使用**手动刷新 / Reload Textures**。
- 静态 JSON 工具属于次要工作流扩展，不改变核心 Photoshop 保存与 Blender 刷新流程。

## 许可证与商业购买

官方 Brandy 2D Link 插件包以 **GPL-3.0-or-later** 发布。官方包包含对应源码文件和许可证文本。

购买提供的是正式测试包，以及销售平台页面声明的支持或更新服务。GPL 权利以插件包随附许可证文本为准。

## 退款与平台政策

退款、支付问题、VAT/税务、收据和授权码交付由实际购买平台处理。

购买前请确认兼容性、版本、存储位置和工作流限制。退款决定仍以销售平台政策和适用法律为准。

## 独立产品声明

Brandy 2D Link 是独立产品，与 Blender Foundation、Adobe、Unity Technologies、Epic Games、Esoteric Software 或其产品不存在从属、认可、赞助或官方关联关系。

Blender 是 Blender Foundation 的商标。Adobe 和 Photoshop 是 Adobe 在美国和/或其他国家或地区的注册商标或商标。Unity 是 Unity Technologies 或其关联公司的商标或注册商标。Unreal Engine 是 Epic Games, Inc. 的商标或注册商标。Spine 是 Esoteric Software LLC 的商标。
