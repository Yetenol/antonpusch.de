---
dg-publish: true
---
To format a new drive as Btrfs (B-tree file system) and mount it in Linux, you can follow these steps:

# Identify all attached drives

```shell
lsblk --output NAME,FSTYPE,LABEL,MODEL,UUID,FSAVAIL,FSUSE%,MOUNTPOINT
```

```
df -Th
```

# Wipe drive

Unmount an already mounted drive, to able to modify its filesystem

```bash
sudo umount /dev/sdX1
```

Wipe the filesystem from a partition

```shell
sudo wipefs -a /dev/sdX1
```

If necessary, merge multiple partitions on the disk

```shell
sudo fdisk /dev/sdX
```

- delete second partition: `d` `2`
- delete first partition: `d` `1`
- create new partition over entire disk: `n` `1` *default* *default*
- write changes to disk: `w`

Format partition with filesystem

```shell
sudo mkfs.btrfs /dev/sdX1
```

Mount drive automatically at boot

```shell
sudo nano /etc/fstab
```

- Add text line and save

```
UUID=38ffd02c-c135-4aa6-8a41-494b8112a011  /media/redCloudDrive  btrfs  defaults,nofail  0  0
UUID=e7ec61d1-e369-4d81-b10f-dfa53f1f86c3  /media/blackBackupDrive  btrfs  defaults,nofail  0  0
```

Reboot to apply changes

```shell
sudo reboot now
```

# Temporary mount drive

```
sudo mkdir /media/redCloudDrive
sudo mount /dev/sdX1 /media/redCloudDrive
```

# List BTRFS subvolumes

```shell
sudo btrfs subvolume list /media/redCloudDrive
```


---
Sources:
- [How To Partition and Format Storage Devices in Linux | DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-partition-and-format-storage-devices-in-linux)

Related:
- [AI response - Format and mount new disks](AI%20response%20-%20Format%20and%20mount%20new%20disks.md)

```dynamic-embed
[[List related notes]]
```

Tags:
[Setup my PlutosCloud](./plutoscloud.md)
