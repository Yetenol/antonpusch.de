---
date: "2025-03-22T07:21:26.089+01:00"
title: "Configure settings in nextcloudpi"
description: "-"
dg-publish: true
priority: 4
---
# CONFIG category

Set pretty URLs (no index.php in URL)
-  `CONFIG > nc-prettyURL`
- [x] Active

# UPDATES category

Periodically update all installed Nextcloud Apps
- `UPDATES > nc-update-nc-apps-auto`
- [x] Active

Automatically apply Nextcloud updates
- `UPDATES > nc-autoupdate-nc` 
- [x] Active

# BACKUPS category

Set periodic backups
- `BACKUPS > nc-backup-auto`
- [x] Include data
- [x] Active
- Destination Directory: another external harddrive like `media/myCloudDrive/ncp-backups`

Scheduled datadir BTRFS snapshots
- `BACKUPS > nc-snapshot-auto`
- [x] Active

---
Sources:

Related:

Tags:
[Setup my PlutosCloud](./Setup-my-PlutosCloud.md)