---
publish: true
priority: 3
---

- [Format and mount new drives in linux](./Format%20and%20mount%20new%20drives%20in%20linux.md)

# Store Nextcloud's data like files and calendar on an external drive

- use a SSD or a RAID setup
- use the BTRFS filesystem for easy snapshots

Change your data dir to a new location, like a USB or SATA drive
- Open `CONFIG > nc-datadir`
- `/media/redCloudDrive/ncdata` =: Data directory

Scheduled datadir BTRFS snapshots
- Open `BACKUPS > nc-snapshot-auto`
- [x] Active

# Store Nextcloud's system and data backups on another external drive

- use a HDD

Set periodic backups
- Open `BACKUP > nc-backup-auto`
- [x] Active
- `/media/blackBackupDrive/ncp-backups` =: Destination Directory
- [x] Include data

# View path to different drives

List connected block devices (SSD's, HDD's) and their mount points

- connect to NextcloudPi Shell

```shell
lsblk --output NAME,FSTYPE,LABEL,MODEL,UUID,FSAVAIL,FSUSE%,MOUNTPOINT
```

- `lsblk` abbreviates **L**i**S**t **BL**oc**K** devices
- the `SIZE` column helps you identify your physical drive
- the `NAME` identifies the (sub)volume thoughout linux
- the `MOUNTPOINT` column tells you the **path** where the (sub)volume is mounted

---
Sources:
- 2023-07-01: [NextCloudPi moving data directory - ℹ️ Support / 📦 Appliances (Docker, Snappy, VM, NCP, AIO) - Nextcloud community](https://help.nextcloud.com/t/nextcloudpi-moving-data-directory/22464/3)
- [Tutorial: How to migrate mass data to a new NextCloud server - 📑 How to - Nextcloud community](https://help.nextcloud.com/t/tutorial-how-to-migrate-mass-data-to-a-new-nextcloud-server/9418)

Related:

Tags:
[Setup my PlutosCloud](./Setup%20my%20PlutosCloud.md)
