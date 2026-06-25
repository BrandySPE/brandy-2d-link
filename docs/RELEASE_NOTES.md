# Brandy 2D Link 1.6.3 — Release Notes / 发行说明

[English](#english) · [简体中文](#简体中文)

## English

This repository documents Brandy 2D Link 1.6.3 for Windows x64. Official release packages are distributed through official storefronts.

### User-facing notes

- Official support matrix updated to six tested Blender versions and five tested Photoshop desktop versions, for 30 Blender–Photoshop combinations.
- English UI terminology is standardized around **Reload Textures**, **Linked Document**, **Switch Texture Format**, and **PS Response Wait Limit (s)**.
- Auto Reload is designed as a save-triggered refresh loop with low background overhead. It is not brush-by-brush live streaming.
- Merge Layers write-back continues to use the reserved groups `Brandy | Linked Content`, `Brandy | Merge Layers`, and `Brandy | Merged Layers`.
- Static JSON import/export remains an optional extension for supported static sprite layouts. Spine2D support remains limited to supported static Region Attachments.
- The 1.6.3 extension manifest is capped before the Blender 5.2 series.

### Unchanged boundaries

- Texture pixel dimensions must remain unchanged after a project is linked.
- The documented workflow assumes local project folders, not network shares, NAS devices, delayed cloud-sync folders, symbolic links, directory junctions, or virtual filesystems.
- Photoshop desktop with JSX scripting is required. Photoshop web, Photoshop for iPad, macOS, Linux, beta/nightly host applications, and non-Adobe image editors are not officially supported.
- Independent backups and version control remain the user's responsibility.

## 简体中文

本仓库用于展示和说明 Windows x64 版 Brandy 2D Link 1.6.3。正式发布包通过官方销售平台分发。

### 面向用户的说明

- 官方支持矩阵更新为 6 个已测试 Blender 版本和 5 个已测试 Photoshop 桌面版，共 30 组 Blender–Photoshop 组合。
- 英文界面术语围绕 **Reload Textures**、**Linked Document**、**Switch Texture Format** 和 **PS Response Wait Limit (s)** 统一。
- Auto Reload 是保存触发的低后台开销刷新循环，不是逐笔刷实时串流。
- Merge Layers 写回继续使用 `Brandy | Linked Content`、`Brandy | Merge Layers` 和 `Brandy | Merged Layers` 三个保留组。
- 静态 JSON 导入/导出仍是可选静态精灵扩展。Spine2D 支持仍限于受支持的静态 Region Attachments。
- 1.6.3 扩展清单将兼容范围限制在 Blender 5.2 系列之前。

### 保持不变的边界

- 项目关联后，贴图像素尺寸必须保持不变。
- 文档化工作流假设项目位于本地文件夹，不建议使用网络共享、NAS、延迟云同步目录、符号链接、目录联接或虚拟文件系统。
- 需要支持 JSX 脚本的 Photoshop 桌面版。Photoshop Web、Photoshop iPad 版、macOS、Linux、Beta/Nightly 宿主程序和非 Adobe 图像编辑器不在正式支持范围内。
- 独立备份和版本控制仍由用户自行负责。
