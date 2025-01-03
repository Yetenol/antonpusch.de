---
title: "Configure settings in nextcloudpi"
date: "2024-07-24T00:00:00.000+02:00"
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
[Setup my PlutosCloud](./plutoscloud.md)