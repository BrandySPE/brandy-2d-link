# 2D Link | Multi-Texture Roundtrip For Blender & Adobe Photoshop

[English](README.md) · [快速入门](docs/QUICK_START_zh-CN.md) · [用户指南](docs/USER_GUIDE_zh-CN.md) · [兼容性](docs/COMPATIBILITY_AND_PURCHASE_CHECKLIST_zh-CN.md) · [技术支持](docs/SUPPORT_zh-CN.md) · [发行说明](docs/RELEASE_NOTES.md)

**在 Adobe Photoshop 中查看并绘制完整资产，同时让 Blender 继续使用独立贴图。**

2D Link 是一款 Windows x64 Blender 插件，适用于剪纸角色、模块化精灵、分层游戏美术和其他多部件 2D 资产。它既能直接编辑单张项目贴图，也能通过关联 PSD/PSB 在完整组装资产的上下文中绘制。

插件在 Blender 内显示为 **Brandy 2D Link**，主要工具位于 3D View 的 **Brandy** 侧栏标签中。

本仓库是官方公开产品主页和文档中心，不包含可安装的正式发行包。请通过下方官方销售渠道获取完整 ZIP 包。

## 插件工作流展示

- [中文演示与教程](https://www.youtube.com/watch?v=-xTnPTlHHwc)
- [English Demo & Tutorial](https://www.youtube.com/watch?v=seKdFcPqHf4)

## 获取 2D Link

- [Superhive](https://superhivemarket.com/products/brandy-2d-link) — 产品页面、购买、FAQ、首次往返文档和平台内支持。

## 两种工作方式

### 单贴图快速编辑

在 Blender 中选择一个精灵对象，直接用 Adobe Photoshop 打开它的项目贴图。绘制并保存后，通过 **Reload Textures** 或保存触发的 **Auto Reload** 更新 Blender。

这适合清理、调色和其他只影响一张贴图的修改。

### 完整资产绘制

打开包含完整 Blender 资产的关联 PSD/PSB。各部件以关联智能对象显示，绘制时可以同时判断接缝、重叠、对齐和相邻贴图关系。

作品准备好后，将可见且名称匹配的图层放入 `Brandy | Merge Layers`，保存文档，再从 Blender 执行 **Apply “Merge Layers” to Source Textures**。

仅保存关联 PSD/PSB 不会自动更新所有贴图。普通文档保存与多贴图写回被有意设计为两个独立动作。

## 它能提供的帮助

- 无需重新连接或重建 Blender 材质就能编辑和刷新项目贴图。
- 便于在可见的完整资产上进行绘画，更容易对贴图接缝、重叠和相邻部分进行修改。
- 可一次性修改多个项目贴图，同时支持文档验证、已验证的备份以及撤销上次合并。

这些保护用于补充正常的生产流程，不替代备份等安全操作。

## 适用范围

2D Link 主要面向：

- 剪纸角色和分层动画资产；
- 模块化精灵和多部件游戏美术；
- Billboard 图像平面和简单的分层 2.5D 资产；
- 需要在完整视觉上下文中绘制、同时保持生产贴图独立的画师；
- 使用明确文件式 Photoshop–Blender 工作流的小型团队。

主工作流要求平面矩形图像网格、矩形活动 UV、一致的 2D 平面朝向、唯一的部件基础名称，以及位于本地文件系统中的 PNG、TGA、JPG 或 JPEG 贴图。

本插件目前注于基于文件的多部件资产 2D 纹理往返操作，不支持通用的 3D 投影绘画、导出到游戏引擎、Photoshop 面板集成，也不支持完整的 Spine 骨架和动画导入。

## 基本要求

- Windows x64
- Blender 4.2.0 至 5.1.x 安装范围
- 支持 JSX 脚本的 Adobe Photoshop 桌面版
- 位于普通本地文件系统中的项目目录
- 文件式 PNG、TGA、JPG 或 JPEG 贴图

本插件需要在 Windows x64 上使用 Adobe Photoshop 桌面版。Photoshop 网页版、iPad 版、macOS、Linux、非 Adobe 图像编辑器，以及 Beta 或 Nightly 宿主版本都不在 1.6.3 的公开支持范围内。

精确实测版本和购买前检查见[兼容性与购买检查清单](docs/COMPATIBILITY_AND_PURCHASE_CHECKLIST_zh-CN.md)。

## 验证与测试

1.6.3 Windows x64 正式版使用同一套自动化端到端 QA 流程，在 6 个 Blender 版本与 5 个 Adobe Photoshop 桌面版组成的 30 个版本组合中完成了实机测试。

每次完整测试均使用一个包含 39 个部件的生产型资产，测试内容包括正式构建校验、资产导入、项目创建、关联 PSD 结构、自动与手动贴图刷新、尺寸不匹配保护、异常状态下的安全写回拒绝、按名称匹配的图层写回、字节级精确恢复的 Undo Last Merge、JSON 导出与导入往返，以及 PNG、TGA 和 JPG 的保存与刷新流程。

此外，测试还选取了 4 组边界版本组合，即最早与最新的 Photoshop 测试版本分别搭配最早与最新的 Blender 测试版本。每个组合执行了 20 次连续的 Photoshop 保存—手动刷新循环，共计 80 次。所有循环均未出现失败，也未检测到几何数据或 Blender 数据块发生漂移。

全部自动化矩阵测试均未发现阻断发布的问题，也未产生报告级警告。测试结果适用于文档所述工作流程、列出的宿主软件版本、Windows x64 平台和本地存储环境。自定义工作室管线、受限制的系统环境、第三方插件、网络存储以及未列出的宿主软件版本，仍应根据实际使用环境单独评估。

## 文档入口

- [快速入门](docs/QUICK_START_zh-CN.md) — 安装和完成第一次成功往返的最短路径。
- [用户指南](docs/USER_GUIDE_zh-CN.md) — 完整日常工作流、项目管理、可选工具和恢复操作。
- [兼容性与购买检查清单](docs/COMPATIBILITY_AND_PURCHASE_CHECKLIST_zh-CN.md) — 精确实测版本、环境要求和购买适配检查。
- [技术支持政策](docs/SUPPORT_zh-CN.md) — 支持范围、问题报告要求、隐私提醒和回复目标。
- [发行说明](docs/RELEASE_NOTES.md) — 当前发行包说明和保持不变的工作流边界。
- [Superhive FAQ](https://superhivemarket.com/products/brandy-2d-link/faq) — 常见购买前问题的简要说明。

第一次使用时，建议先按照[快速入门](docs/QUICK_START_zh-CN.md)完成一次手动贴图刷新，再启用 Auto Reload 或测试多贴图写回。

## 许可证与独立产品声明

2D Link 正式插件包以 **GPL-3.0-or-later** 分发，并包含对应源码文件和许可证文本。购买提供的是正式发行包，以及销售页面说明的支持或更新服务；GPL 权利以包内许可证为准。

2D Link 是独立产品，与 Blender Foundation 或 Adobe 无关联，更多商标信息请查看 NOTICE.md。
