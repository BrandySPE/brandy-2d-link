# 2D Link | Blender 与 Adobe Photoshop 多贴图往返工作流

[English](README.md) · [快速入门](docs/QUICK_START_zh-CN.md) · [用户指南](docs/USER_GUIDE_zh-CN.md) · [兼容性](docs/COMPATIBILITY_AND_PURCHASE_CHECKLIST_zh-CN.md) · [技术支持](docs/SUPPORT_zh-CN.md)

**在 Adobe Photoshop 中绘制完整资产，同时让 Blender 继续使用独立贴图。**

2D Link 是一款面向 Windows x64 的 Blender 插件，适用于剪纸角色、模块化精灵图、分层游戏美术和其他多部件 2D 资产。它提供两种明确的 Photoshop 工作方式：直接编辑一张项目贴图，或通过关联 PSD/PSB 查看并绘制完整资产，同时让 Blender 保持各部件贴图彼此独立。

插件在 Blender 中显示为 **Brandy 2D Link**，主要工具位于 3D 视图的 **Brandy** 侧栏标签中。

本仓库是公开的产品主页与文档中心，不是可安装的插件包。可安装版本通过下方销售页面提供，并包含对应的 GPL 授权源代码。

## 获取 2D Link

- [Superhive](https://superhivemarket.com/products/brandy-2d-link)
- [itch.io](https://brandyspe.itch.io/brandy-2d-link)

不要把 GitHub 的仓库 ZIP 安装到 Blender。请使用销售页面提供的完整产品 ZIP。

## 查看工作流

- [中文演示与教程](https://www.youtube.com/watch?v=-xTnPTlHHwc)
- [English demo and tutorial](https://www.youtube.com/watch?v=seKdFcPqHf4)

## 工作方式

### 单贴图快速编辑

在 Blender 中选择一个精灵面片，并用 Adobe Photoshop 打开它的项目贴图。绘制并保存后，通过 **手动刷新** 或保存触发的 **自动刷新** 更新 Blender 中的显示。

该方式适合清理、调色和其他只影响一张贴图的修改。

### 完整资产绘制

打开关联 PSD/PSB 查看组装后的 Blender 资产。每个部件都以关联智能对象显示，因此绘制时可以同时判断接缝、重叠、对齐和相邻贴图关系。

准备写回时，将可见且名称匹配的图层直接放入 **Brandy | Merge Layers**，保存 PSD/PSB，再从 Blender 执行 **将 PS 合并组应用到源贴图**。此命令中的“源贴图”指当前 2D Link 项目内部的贴图文件。

仅保存关联 PSD/PSB 不会自动更新全部贴图。多贴图写回是一个独立、明确的操作。

## 项目文件

创建项目时，2D Link 会把合格贴图复制到项目目录，并让 Blender 改用这些副本。创建项目前使用的文件保持不变。此后，单贴图编辑、自动刷新和 Merge Layers 写回都针对项目贴图进行。

执行多贴图写回前，2D Link 会检查关联文档和目标贴图，并为受影响的文件创建经过验证的备份。只要项目文件仍与记录的恢复状态一致，**撤销上一次合并** 就能恢复最近一次成功写回。

这些保护不能替代正常的生产备份或版本管理。

## 基本要求

- Windows x64
- Blender 4.2.0 至 5.1.x
- Windows 版 Adobe Photoshop 桌面应用；无需额外安装 Photoshop 面板或扩展
- 本地 PNG、TGA、JPG 或 JPEG 贴图文件
- 位于标准本地磁盘的项目目录
- 平面矩形图像面片、矩形活动 UV、一致的 2D 平面朝向，以及唯一的部件基础名称

该工作流以保存为触发条件，不会把 Photoshop 中的单次笔触实时传输到 Blender。

1.6.3 已在 30 组 Blender–Photoshop 版本组合中完成文档所述工作流测试。精确版本、工作流边界和购买前检查见[兼容性与购买检查清单](docs/COMPATIBILITY_AND_PURCHASE_CHECKLIST_zh-CN.md)。

## 文档

- [快速入门](docs/QUICK_START_zh-CN.md) — 完成一次单贴图往返和一次 Merge Layers 写回。
- [用户指南](docs/USER_GUIDE_zh-CN.md) — 插件全部功能的详细操作说明。
- [兼容性与购买检查清单](docs/COMPATIBILITY_AND_PURCHASE_CHECKLIST_zh-CN.md) — 实测版本、系统与资产要求、存储限制和可选 JSON 功能范围。
- [技术支持](docs/SUPPORT_zh-CN.md) — 如何检查失败操作并提交有效的私密报告。
- [Superhive FAQ](https://superhivemarket.com/products/brandy-2d-link/faq) — 常见购买前问题的简要说明。

第一次使用时，请从[快速入门](docs/QUICK_START_zh-CN.md)开始。

## 许可证与独立产品声明

插件包采用 GPL-3.0-or-later 许可证发布，并包含对应源代码。

2D Link 是独立产品，与 Adobe、Blender Foundation 及其相关组织不存在隶属或背书关系。商标信息见 [NOTICE.md](NOTICE.md)。
