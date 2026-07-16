# 2D Link — Support Policy

[Product Home](../README.md) · [Quick Start](QUICK_START.md) · [User Guide](USER_GUIDE.md) · [Compatibility](COMPATIBILITY_AND_PURCHASE_CHECKLIST.md)

This policy applies to the official 2D Link 1.6.3 Windows x64 package.

Product support is handled through the storefront where the product was purchased. Superhive customers should use Superhive messaging. Customers from another official storefront should use the support contact or channel provided there.

## First-Response Target

The first-response target is **3 calendar days** for reasonable product assistance inside the documented support boundary.

Response time may be affected by weekends, holidays, storefront-message delivery, report complexity, and missing reproduction information. Data-safety problems and reproducible failures in the core Blender–Photoshop workflow receive the highest priority.

## What Support Covers

Support covers:

- installation of the official unmodified ZIP;
- initial Photoshop path configuration and **Test PS** interpretation;
- documented project creation, linking, switching, and validation;
- Quick Texture Edit, Reload Textures, and Auto Reload;
- linked PSD/PSB handling and Merge Layers write-back;
- Undo Last Merge and documented recovery actions;
- supported static JSON and utility workflows;
- Operation Report interpretation;
- reproducible failures in the documented core workflow.

The exact tested host versions and compatibility-candidate rules are defined in the [Compatibility and Purchase Checklist](COMPATIBILITY_AND_PURCHASE_CHECKLIST.md).

An unlisted stable version may still receive an initial support review. Comparison with a listed version may be requested when it is useful for isolating a version-specific difference.

## What Support Does Not Include

Support does not include:

- general Blender or Photoshop training;
- custom project repair or private asset debugging as an ongoing service;
- custom pipeline development or feature implementation;
- third-party add-on conflicts outside the documented workflow;
- modified packages, incomplete ZIP installations, or files assembled from separate package components;
- official support for macOS, Linux, beta or nightly hosts, non-Adobe editors, network shares, NAS devices, virtual filesystems, symbolic links, directory junctions, or delayed-sync project folders;
- data recovery beyond the documented built-in recovery tools;
- guaranteed compatibility with future Blender, Photoshop, Windows, hardware, or security-policy changes before they enter the published matrix;
- legal, tax, payment, refund, receipt, download-access, or marketplace-account assistance.

## Before Sending a Report

Please complete these checks first:

1. Confirm that the official unmodified ZIP is installed.
2. Confirm that the active project is on a normal local drive.
3. Restart Blender and Photoshop when no write operation is active.
4. Run **Test PS** again if the Photoshop path, execution mode, or version changed.
5. Try **Reload Textures** once if Auto Reload did not update the view.
6. Click **Open Operation Report** and read the first blocked condition and recommended action.
7. Do not force-clear a task state or project lock while Photoshop may still be writing files.
8. Reproduce the problem in a copy of the project when possible.
9. Reduce the report to the smallest asset and sequence that still shows the problem.

## What to Include

Send one issue per message and include:

- 2D Link version;
- complete Blender version;
- Photoshop year and user-visible application version;
- Windows version;
- whether several Photoshop versions are installed or running;
- the Photoshop path and reported version shown by **Test PS**;
- the project's storage type: local drive, network drive, NAS, cloud-sync folder, symbolic link, or directory junction;
- exact reproduction steps;
- expected result;
- actual result and complete visible error text;
- a reviewed and redacted copy of 'BRANDY_2D_LINK_Last_Report', when available;
- for JSON issues, the import mode, original 'skeleton.images' value, JSON folder layout, and whether external-folder access was authorized.

Screenshots are useful only when they clarify a UI state or visible error. Do not substitute screenshots for exact reproduction steps and text errors.

## Privacy and Shared Files

Do not send a full production project unless it is specifically requested. Use a minimal reproduction project whenever possible.

Operation Reports and task logs may contain local paths, account names, project names, customer names, or unpublished artwork references. Review and redact every file before sharing it.

Never include credentials, payment data, private license information, confidential client assets, or unrelated production files.

## Recovery and Data Safety

Use **Open Operation Report** before using any recovery tool. Preserve the project folder, task folder, project lock, backup records, and recovery markers until the state is understood.

Do not manually delete locks or replace project files while Photoshop may still be writing. Recovery or undo can be refused when current files no longer match the recorded state; this behavior is intentional and prevents an outdated recovery action from overwriting newer changes.

Built-in backups and undo support the documented workflow but do not replace independent backups, version control, or professional data recovery.

## Storefront, Updates, and Future Versions

Payment, receipts, tax or VAT handling, download access, refund requests, and marketplace-account issues are handled by the storefront where the purchase was made.

Each storefront defines the purchase, download, refund, and support terms for orders placed there. A purchase includes the current official release and support for the documented version. Future updates and compatibility with new Blender, Photoshop, or Windows versions are not guaranteed until they are tested and published.

New Blender and Photoshop public versions enter the support matrix after the documented workflow is tested and the published compatibility page is updated.

## License Boundary

The official 2D Link add-on package is distributed under **GPL-3.0-or-later**. The package includes the corresponding source files and license text. Support and update access are storefront services and do not change the GPL rights described in the included license.

## Independent Product Notice

2D Link is an independent product and is not affiliated with or endorsed by Blender Foundation, Adobe, or Esoteric Software. Blender, Adobe Photoshop, and Spine are trademarks of their respective owners.

Blender is a trademark of Blender Foundation. Adobe and Photoshop are either registered trademarks or trademarks of Adobe in the United States and/or other countries. Unity is a trademark or registered trademark of Unity Technologies or its affiliates.
