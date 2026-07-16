# 2D Link 1.6.3 — Release Notes / 发行说明

[Product Home / 产品主页](../README.md) · [English](#english) · [简体中文](#简体中文)

## English

This repository documents the official 2D Link 1.6.3 Windows x64 package. Installable release packages are distributed through the official storefronts.

### User-facing notes

- The published support matrix includes six tested Blender versions and five tested Adobe Photoshop desktop versions, forming 30 tested combinations.
- English UI terminology is standardized around **Reload Textures**, **Linked Document**, **Switch Texture Format**, and **PS Response Wait Limit (s)**.
- Auto Reload remains a save-triggered refresh loop with low background overhead; it is not brush-by-brush live streaming.
- Full-asset write-back continues to use `Brandy | Linked Content`, `Brandy | Merge Layers`, and `Brandy | Merged Layers`.
- Write-back validates the linked document and target files and creates verified backups for the textures involved.
- Static JSON import and export remain optional utilities. Spine2D support remains limited to supported static Region Attachments.
- The extension manifest is capped before the Blender 5.2 series.

### Unchanged boundaries

- Adobe Photoshop desktop with JSX scripting is required and is not included with 2D Link.
- Project texture pixel dimensions must remain unchanged after linking.
- Active projects should remain on a normal local filesystem rather than a network share, NAS, delayed-sync folder, symbolic link, directory junction, or virtual filesystem.
- Saving only the linked PSD/PSB does not update every project texture.
- Independent backups and version control remain the user's responsibility.

## 简体中文

本仓库用于展示和说明 2D Link 1.6.3 Windows x64 正式发行包。可安装发行包通过官方销售渠道分发。

### 面向用户的说明

- 公开支持矩阵包含 6 个实测 Blender 版本和 5 个实测 Adobe Photoshop 桌面版，共 30 组组合。
- 英文界面术语围绕 **Reload Textures**、**Linked Document**、**Switch Texture Format** 和 **PS Response Wait Limit (s)** 统一。
- Auto Reload 继续采用低后台开销的保存触发刷新，不是逐笔刷实时串流。
- 完整资产写回继续使用 `Brandy | Linked Content`、`Brandy | Merge Layers` 和 `Brandy | Merged Layers`。
- 写回前会验证关联文档与目标文件，并为涉及的贴图建立经过验证的备份。
- 静态 JSON 导入与导出仍是可选工具。Spine2D 支持仍限于受支持的静态 Region Attachments。
- 扩展清单将范围限制在 Blender 5.2 系列之前。

### 保持不变的边界

- 需要支持 JSX 脚本的 Adobe Photoshop 桌面版，2D Link 不包含 Photoshop。
- 项目关联后，项目贴图像素尺寸必须保持不变。
- 活动项目应位于普通本地文件系统，而不是网络共享、NAS、延迟同步目录、符号链接、目录联接或虚拟文件系统。
- 仅保存关联 PSD/PSB 不会更新所有项目贴图。
- 独立备份和版本管理仍由用户负责。
