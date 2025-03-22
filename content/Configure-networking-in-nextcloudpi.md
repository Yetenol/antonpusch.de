---
date: "2025-03-22T07:21:26.068+01:00"
title: "Configure networking in nextcloudpi"
description: "-"
dg-publish: true
priority: 2
---

# Router setup

**On your router**, setup port forwarding to allow you to access PlutosCloud from the internet.

- Forward ports 80 and 443 to your pi
- Setup DynDNS with duckdns.org [Duck DNS - install](https://www.duckdns.org/install.jsp)

# Configure domain access with HTTPS

Automatic setup via NextcloudPi wizard
- [Menubar > wizard](https://10.0.0.2:4443/wizard)
- Skip to *External access*
- Follow wizard's instructions
- Connect with NO-IP account
- Create a *Let's Encrypt* certificate with a random email address

Ensure everything is setup correctly or do manual setup

- `SECURITY > fail2ban` Brute force protection for SSH and NextCloud
- `CONFIG > nc-httpsonly` Force HTTPS
- `CONFIG > nc-prettyURL` Set pretty URLs (no index.php in URL)


DNS server with cache
- `NETWORKING > dnsmasq`
- [x] Active
- `yetenol.de` =: Domain
- `8.8.8.8` =: DNS server
- `150` =: Cache size

Automatic signed SSL certificates. Let’s Encrypt is a free, automated, and open Certificate Authority.
- `NETWORKING > letsencrypt`
- [x] Active
- `yetenol.de` =: Domain
- `mycloud@ownyourbits.com` =: Email

# Test domain access from your computer

- open [PlutosCloud](https://yetenol.de/)

Test domain connection

```powershell
while ($True) {
    Test-Connection yetenol.de |
        select Address, IPV4Address, IPV6Address, ResponseTime
    Start-Sleep 1
}
```

Test HTTP port connection

```powershell
while ($True) {
    Test-NetConnection yetenol.de -Port 80 | 
        select ComputerName, RemoteAddress, RemotePort, TcpTestSucceeded
    Start-Sleep 1
}
```

Test HTTPS port connection

```powershell
while ($True) {
    Test-NetConnection yetenol.de -Port 443 | 
        select ComputerName, RemoteAddress, RemotePort, TcpTestSucceeded
    Start-Sleep 1
}
```

# Troubleshoot domain acc

View Letsencrypt log

```shell
sudo cat /var/log/letsencrypt/letsencrypt.log
```

---
Sources:
- [Raspberry Pi SSL Zertifikat kostenlos mit Let's Encrypt erstellen](https://tutorials-raspberrypi.de/raspberry-pi-ssl-zertifikat-kostenlos-mit-lets-encrypt-erstellen/)

Related:

Tags:
[Setup my PlutosCloud](./Setup-my-PlutosCloud.md)
