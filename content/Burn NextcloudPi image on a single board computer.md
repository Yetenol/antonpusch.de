---
publish: true
priority: 1
---

# Install Operating System

Download **NextCloudPi OS Image** for RaspberryPi from [nextcloud's Github](https://github.com/nextcloud/nextcloudpi/releases)

Burn image onto an SD card using [Raspberry Pi Imager](https://www.raspberrypi.com/software/)
- *downloaded image* =: Operating System
- Click the gear to open settings
- `to always use` =: Image customization options
- [x] `plutoscloud` =: Set hostname
- [x] `Use password authentication` =: Enable SSH
- [x] `anton`, *password* =: Set username and password
- [x] Set locale settings
    - `Europe/Berlin` =: Time zone
    - `de` =: Keyboard layout
- Save and write to SD card

Put SD card into PI and boot it up

Assign the PI a fixed IP address via the router or a static IP

# Enable NextcloudPi Web Interface

Login to the PI via SSH

```shell
ssh-keygen -R plutoscloud
ssh plutoscloud
```

- The Nextcloudpi logo should appear

Enable local network HTTP connection to NextcloudPi Configuration Web Panel
- Run `sudo ncp-config`
- Open `CONFIG > nc-webui`
- Replace `no` with `yes`
- Restart webserver `sudo systemctl reload apache2`

# Access remotely

- Open `ssh anton@plutoscloud.local` on your computer and login using your Raspberry Pi credential to access NextcloudPi Shell 
- Open https://10.0.0.2:4333 in your computers web browser to access NextcloudPi Configuration Web Panel
    - Initial username: `ncp`
    - Initial password: `ownyourbits`
- Save the newly generated Nextcloud and NextcloudPi credentials

---

Sources:
- [Build Your Own Raspberry Pi Cloud Server With Nextcloud](https://www.makeuseof.com/raspberry-pi-nextcloud/)
- [Tutorial: How to migrate mass data to a new NextCloud server - 📑 How to - Nextcloud community](https://help.nextcloud.com/t/tutorial-how-to-migrate-mass-data-to-a-new-nextcloud-server/9418)
- [☁ Nextcloud Server Anleitung: Eigene (Raspberry Pi) Cloud einrichten](https://tutorials-raspberrypi.de/raspberry-pi-nextcloud-owncloud-einrichten-und-konfigurieren/)

Related:

Tags:
[Setup my PlutosCloud](./Setup%20my%20PlutosCloud.md)
