# Support Policy — Brandy 2D Link

This policy applies to the official Brandy 2D Link 1.6.3 Windows x64 package.

Support is handled through the storefront where the product was purchased. For direct-sale customers, use the support contact included with the official package or sales page.

## First-Response Target

The first-response target is **3 calendar days** for reasonable product assistance within the documented support boundary.

Complex reports may require reproduction details or follow-up checks. Response time may be affected by weekends, holidays, platform-message delivery, report complexity, and the amount of information included.

Data-safety problems and reproducible failures in the core Blender–Photoshop workflow receive the highest priority.

## What Support Covers

Support covers:

- installation of the official unmodified package;
- initial Photoshop path configuration;
- the documented Project Link, texture reload, Auto Reload, Merge Layers, undo, recovery, static JSON, and utility workflows;
- Operation Report interpretation;
- reproducible failures in the core Blender–Photoshop workflow;
- the fully tested Blender and Photoshop versions listed in `README.md`.

## Fully Tested Versions

In this policy, “fully tested versions” means the exact Windows x64 Blender releases and the listed Photoshop public versions below:

- Blender 4.2.21 LTS, 4.3.2, 4.4.3, 4.5.10, 5.0.1, and 5.1.2;
- Adobe Photoshop CC 2017.1.6; Photoshop 2020, version 21.2.1; Photoshop 2022, version 23.5.0; Photoshop 2025, version 26.10.0; and Photoshop 2026, version 27.7.0.

Blender is matched by its complete version. Photoshop is matched by its year and user-visible application version; Adobe internal build numbers are not used as a support gate. When several Photoshop versions coexist, the path and reported application version confirmed by **Test PS** identify the responding application. An unlisted stable version may still receive support review; a comparison on a listed version is requested only when it is useful for isolating a version-specific difference.

## What Support Does Not Include

Support does not include:

- general Blender or Photoshop training;
- custom project repair or private asset debugging as a service;
- custom pipeline development;
- third-party add-on conflicts outside the documented workflow;
- support for modified packages or incomplete ZIP installations;
- support for macOS, Linux, beta/nightly host applications, network shares, NAS, virtual filesystems, symbolic links, directory junctions, or delayed cloud-sync project folders;
- data recovery beyond the plugin's documented recovery tools;
- compatibility review for future Blender, Photoshop, Windows, hardware, or security-policy changes before they enter the published support matrix;
- legal, tax, payment, or marketplace-account support.

## Future Versions

The sales page and order terms define the support and update period included with a purchase. This repository does not promise lifetime support or lifetime compatibility.

New Blender releases or Photoshop public versions enter the published support matrix after the documented workflow is tested and the matrix is updated. Photoshop internal build numbers are not used as a separate support boundary.

## Before Sending a Report

Please do the following first:

1. Confirm that the official unmodified ZIP is installed.
2. Confirm that the project is on a normal local drive.
3. Restart Blender and Photoshop if no write operation is active.
4. Run **Test PS** again if the Photoshop path, execution mode, or version changed.
5. Try **Reload Textures** once if Auto Reload did not update the view.
6. Open **Open Operation Report** and read the first blocked condition.
7. Do not force-clear a task state or project lock while Photoshop may still be writing files.
8. Reproduce the issue in a copy of the project when possible.

## What to Include

Send one issue per message and include:

- Brandy 2D Link version;
- complete Blender version;
- Photoshop year and user-visible application version;
- Windows version;
- whether several Photoshop versions are installed or running;
- the actual Photoshop path and reported application version shown by **Test PS**;
- whether the project is on a local drive, network drive, NAS, cloud-sync folder, symbolic link, or directory junction;
- exact reproduction steps;
- expected result;
- actual result and complete visible error text;
- screenshots only when they clarify the issue;
- a reviewed and redacted copy of `BRANDY_2D_LINK_Last_Report`, when available;
- for JSON import/export problems, the import mode, the original `skeleton.images` value, the JSON folder layout, and whether external-folder access was authorized.

Remove private paths, account names, customer names, unpublished artwork, credentials, payment data, and any confidential production information before sharing files or reports.

## Privacy and Files

Do not send full production projects unless specifically requested. Use a minimal reproduction project whenever possible.

Operation Reports may still contain local diagnostic data even after some known paths are replaced. Review and redact reports before sharing them.

## Storefront and Refund Issues

Payment, receipts, tax/VAT handling, download access, refund requests, and marketplace-account issues are handled by the storefront where the purchase was made. Follow that storefront's policy and support channel.

For compatibility-candidate environments, first compare against the published support matrix and documented workflow limits.

## License Boundary

The official Brandy 2D Link add-on package is distributed under **GPL-3.0-or-later**. Support and update access are services defined by the storefront. GPL rights remain as described in the license included with the package.

## Independent Product Notice

Brandy 2D Link is an independent product. It is not affiliated with, endorsed by, sponsored by, or officially connected to Blender Foundation, Adobe, Unity Technologies, Epic Games, Esoteric Software, or their products.

Blender is a trademark of Blender Foundation. Adobe and Photoshop are either registered trademarks or trademarks of Adobe in the United States and/or other countries. Unity is a trademark or registered trademark of Unity Technologies or its affiliates. Unreal Engine is a trademark or registered trademark of Epic Games, Inc. Spine is a trademark of Esoteric Software LLC.
