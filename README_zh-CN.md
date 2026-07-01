# Brandy 2D Link

[English](README.md) · [快速入门](docs/QUICK_START_zh-CN.md) · [用户指南](docs/USER_GUIDE_zh-CN.md) · [兼容性与购买检查](docs/COMPATIBILITY_AND_PURCHASE_CHECKLIST_zh-CN.md) · [技术支持](docs/SUPPORT_zh-CN.md) · [发行说明](docs/RELEASE_NOTES.md)

**面向 2D 游戏美术的 Photoshop 与 Blender 贴图迭代工具。**

Brandy 2D Link 是一款 Windows x64 Blender 插件，面向需要同时使用 Blender 和 Adobe Photoshop 桌面版的画师、动画师、技术美术和 2D 游戏开发者。

它的核心循环很直接：在 Blender 中准备精灵对象，创建 Brandy 项目，在 Photoshop 中编辑项目贴图，保存图像，然后在 Blender 中手动刷新或使用 Auto Reload 自动刷新对应材质贴图。

这是“保存触发”的工作流，不是逐笔刷实时串流。

- 中文教程: https://youtu.be/-xTnPTlHHwc
- 英文教程: https://youtu.be/seKdFcPqHf4

在 itch.io 进行购买 / 下载：
https://brandyspe.itch.io/brandy-2d-link
在 Superhive 进行购买 / 下载：
https://superhivemarket.com/products/brandy-2d-link

## 它解决什么问题

Blender 中的分层 2D 资产通常会使用多张独立贴图。手动编辑这些贴图时，经常需要反复寻找对应文件、打开、保存、回到 Blender、刷新，并同时记住完整资产的组合效果。

Brandy 2D Link 将这个过程整理为可预测的项目工作流：

1. 在 Blender 中准备或导入静态精灵布局。
2. 从一个 Blender 集合创建或关联 Brandy 项目。
3. 在 Photoshop 中打开项目贴图或关联 PSD/PSB。
4. 绘制并保存。
5. 在 Blender 中使用 **Reload Textures** 或 **Auto Reload**。
6. 需要整体参考绘制时，将 `Brandy | Merge Layers` 中可见且名称匹配的图层写回到对应项目贴图。

只保存关联 PSD/PSB 不会更新 Blender。Blender 刷新的是项目 `textures` 文件夹中的独立贴图文件。

## 主要功能

- 创建、关联、切换、验证和恢复独立 Brandy 项目文件夹。
- 直接在 Photoshop 中打开活动精灵贴图。
- 手动刷新项目贴图，或使用保存触发的 Auto Reload。
- 生成带有智能对象的关联 PSD/PSB，用于在完整布局中参考绘制。
- 将 `Brandy | Merge Layers` 中可见、顶层、名称匹配的图层写回到对应源贴图。
- 在支持的破坏性写入操作前创建可信备份。
- 在严格文件一致性检查通过时撤销最近一次成功合并。
- 保护源贴图尺寸、关联文档结构、项目锁、任务记录和恢复状态。
- 支持 PNG、TGA、JPG、JPEG 静态贴图工作流。
- 导入和导出受支持的 PhotoshopToSpine 静态 JSON 布局。
- 导入有限范围的 Spine2D 静态 Region Attachments。
- 提供贴图格式切换、导入材质恢复、着色器数值复制、生成材质合并和视口独显等便捷工具。
- 界面语言支持 **Auto / 中文 / English**。

## 适合谁使用

Brandy 2D Link 适合：

- 在 Photoshop 和 Blender 之间制作 2D 游戏美术的用户；
- 精灵、Billboard、切片角色、分层角色贴图的迭代；
- 希望一边查看完整组合资产、一边绘制局部内容的画师；
- 为更大游戏管线准备 Photoshop–Blender 资产的技术美术；
- 希望使用轻量、文件式、可预测流程的小团队。

## 它不是什么

Brandy 2D Link 不是：

- 逐笔刷实时串流系统；
- Photoshop 内部面板或 UXP 扩展；
- Unity、Unreal Engine 或其他引擎的直接导出器；
- 完整 Spine 绑定、Mesh Attachment、约束、双色 Tint 或动画导入器；
- 面向任意非矩形网格或不受限制 UV 布局的工具；
- 对 Photoshop Web、Photoshop iPad 版、非 Adobe 图像编辑器、macOS 或 Linux 的支持；
- 独立备份、版本控制、Blender 与 Photoshop 基础知识的替代品。

## 资产要求

每个项目精灵建议使用：

- 基于文件的 PNG、TGA、JPG 或 JPEG 贴图；
- 平面矩形网格；
- 有效的矩形活动 UV 区域；
- 唯一基础名称；
- 一致的 2D 平面朝向。

只要外轮廓保持矩形，内部网格细分可以存在。可以使用深度偏移来表现视觉层级。

项目关联后，源贴图像素尺寸必须保持不变。需要调整画布尺寸时，请在创建 Brandy 项目前完成。反复绘制建议优先使用 PNG 或 TGA。

Brandy 2D Link 基于标准文件式 Image Texture 使用方式。隐藏在自定义 Shader Node Group 内部的 Image Texture 节点不属于文档化贴图来源。

## 兼容性摘要

Brandy 2D Link 1.6.3 官方包支持 Windows x64，并针对以下宿主版本完成测试。

**Blender**

- Blender 4.2.21 LTS
- Blender 4.3.2
- Blender 4.4.3
- Blender 4.5.10
- Blender 5.0.1
- Blender 5.1.2

**Adobe Photoshop 桌面版**

- Adobe Photoshop CC 2017.1.6
- Adobe Photoshop 2020，version 21.2.1
- Adobe Photoshop 2022，version 23.5.0
- Adobe Photoshop 2025，version 26.10.0
- Adobe Photoshop 2026，version 27.7.0

正式支持矩阵以完整 Blender 版本，以及 Photoshop 年份加用户可见应用版本为准。Adobe 内部构建号不作为购买或支持门槛。

扩展清单将兼容范围限制在 Blender 5.2 系列之前，预期安装范围为 Blender 4.2.0 至 Blender 5.1.x。位于该范围内但未列入精确测试清单的稳定 Blender 版本，只能视为兼容候选。

安装多个 Photoshop 版本时，**Test PS** 显示的路径和应用版本才代表实际连接的 Photoshop 实例。

购买前请阅读完整的[兼容性与购买检查清单](docs/COMPATIBILITY_AND_PURCHASE_CHECKLIST_zh-CN.md)。

## 测试摘要

1.6.3 Windows x64 包已完成由以上六个 Blender 版本和五个 Photoshop 版本组成的 **30 组 Blender–Photoshop 组合**矩阵测试。

监督型生产测试使用了真实 JSON 布局和一个 **39 部件角色资产**，覆盖静态 JSON 导入、项目创建、Photoshop 启动与连接检测、关联文档验证、手动和自动贴图刷新、尺寸变更拒绝、命名图层写回、最近一次合并撤销、JSON 导出与重新导入，以及 PNG/TGA/JPG 保存刷新检查。

额外监督型长时段测试覆盖了代表性旧版、中间版本和当前版本配置下的 **40 次保存—刷新循环**。

测试覆盖的是列出宿主版本下的 Brandy 2D Link 文档化工作流。第三方插件、自定义工作室管线、受管安全策略、存储环境和未来宿主版本，建议在用户自己的环境中另行确认。

## 文档

- [快速入门](docs/QUICK_START_zh-CN.md)：安装和第一次贴图刷新的最快路径。
- [用户指南](docs/USER_GUIDE_zh-CN.md)：完整日常工作流、功能边界、恢复工具和常见错误。
- [兼容性与购买检查清单](docs/COMPATIBILITY_AND_PURCHASE_CHECKLIST_zh-CN.md)：购买前检查环境、工作流、许可证与支持边界。
- [技术支持政策](docs/SUPPORT_zh-CN.md)：支持范围、报告应包含的信息，以及不属于支持范围的内容。
- [发行说明](docs/RELEASE_NOTES.md)：当前版本说明。

## 购买与官方包

本仓库是公开产品与文档页面。正式发布包通过官方销售平台分发。

如果你需要经过验证的官方发布包、文档化支持入口和销售平台管理的更新，请通过官方销售页购买。

## 技术支持

技术支持通过购买所在平台处理。直接销售用户请使用官方包或销售页中提供的支持联系方式。

发送报告前，请阅读[技术支持政策](docs/SUPPORT_zh-CN.md)，并从共享文件中移除私人路径、账户名、客户名、未公开美术、凭据、支付信息和机密生产资料。

## 许可证与独立产品声明

官方 Brandy 2D Link 插件包以 **GPL-3.0-or-later** 发布。购买提供的是官方发布包，以及销售页面中说明的支持或更新服务。

Brandy 2D Link 是独立产品，与 Blender Foundation、Adobe、Unity Technologies、Epic Games、Esoteric Software 或其产品不存在从属、认可、赞助或官方关联关系。

Blender 是 Blender Foundation 的商标。Adobe 和 Photoshop 是 Adobe 在美国和/或其他国家或地区的注册商标或商标。Unity 是 Unity Technologies 或其关联公司的商标或注册商标。Unreal Engine 是 Epic Games, Inc. 的商标或注册商标。Spine 是 Esoteric Software LLC 的商标。
