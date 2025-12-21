---
date: "2025-07-17T08:14:04.547+02:00"
title: "ms-settings"
description: "Open Windows settings pages like display"
dg-publish: true
dg-folder: windows
---

`ms-setting` URIs used to open various pages of the Settings app

# Settings home page

| Page               | URI            |
| ------------------ | -------------- |
| Settings home page | `ms-settings:` |

# System

| Page                                                     | URI                                                          |
| -------------------------------------------------------- | ------------------------------------------------------------ |
| Display                                                  | `ms-settings:display`                                        |
| Night light settings                                     | `ms-settings:nightlight`                                     |
| Advanced scaling settings                                | `ms-settings:display-advanced`                               |
| Connect to a wireless display                            | `ms-settings-connectabledevices:devicediscovery`             |
| Graphics settings                                        | `ms-settings:display-advancedgraphics`                       |
| Display orientation                                      | `ms-settings:screenrotation`                                 |
| Sound                                                    | `ms-settings:sound`                                          |
| Manage sound devices                                     | `ms-settings:sound-devices`                                  |
| App volume and device preferences                        | `ms-settings:apps-volume`                                    |
| Notifications & actions                                  | `ms-settings:notifications`                                  |
| Focus assist                                             | `ms-settings:quiethours` <br> `ms-settings:quietmomentshome` |
| During these hours                                       | `ms-settings:quietmomentsscheduled`                          |
| Duplicating my display (When I'm duplicating my display) | `ms-settings:quietmomentspresentation`                       |
| Playing a game full screen (When I'm playing a game)     | `ms-settings:quietmomentsgame`                               |
| Power & sleep                                            | `ms-settings:powersleep`                                     |
| Battery                                                  | `ms-settings:batterysaver`                                   |
| See which apps are affecting your battery life           | `ms-settings:batterysaver-usagedetails`                      |
| Battery Saver settings                                   | `ms-settings:batterysaver-settings`                          |
| Storage                                                  | `ms-settings:storagesense`                                   |
| Configure Storage Sense or run it now                    | `ms-settings:storagepolicies`                                |
| Change where new content is saved                        | `ms-settings:savelocations`                                  |
| Tablet mode                                              | `ms-settings:tabletmode`                                     |
| Multitasking                                             | `ms-settings:multitasking`                                   |
| Projecting to this PC                                    | `ms-settings:project`                                        |
| Shared experiences                                       | `ms-settings:crossdevice`                                    |
| Clipboard                                                | `ms-settings:clipboard`                                      |
| Remote Desktop                                           | `ms-settings:remotedesktop`                                  |
| Device Encryption (where available)                      | `ms-settings:deviceencryption`                               |
| About                                                    | `ms-settings:about`                                          |

# Devices

| Page                                            | URI                                                         |
| ----------------------------------------------- | ----------------------------------------------------------- |
| Bluetooth & other devices                       | `ms-settings:bluetooth` <br> `ms-settings:connecteddevices` |
| **CONNECT** to wireless display or audio device | `ms-settings-connectabledevices:devicediscovery`            |
| Printers & scanners                             | `ms-settings:printers`                                      |
| Mouse                                           | `ms-settings:mousetouchpad`                                 |
| Touchpad                                        | `ms-settings:devices-touchpad`                              |
| Typing                                          | `ms-settings:typing`                                        |
| Hardware keyboard - Text suggestions            | `ms-settings:devicestyping-hwkbtextsuggestions`             |
| Wheel (where available)                         | `ms-settings:wheel`                                         |
| Pen & Windows Ink                               | `ms-settings:pen`                                           |
| AutoPlay                                        | `ms-settings:autoplay`                                      |
| USB                                             | `ms-settings:usb`                                           |

# Phone

| Page                   | URI                                          |
| ---------------------- | -------------------------------------------- |
| Phone                  | `ms-settings:mobile-devices`                 |
| Add a phone            | `ms-settings:mobile-devices-addphone`        |
| Your Phone (opens app) | `ms-settings:mobile-devices-addphone-direct` |

# Network & Internet

| Page                           | URI                                                             |
| ------------------------------ | --------------------------------------------------------------- |
| Network & Internet             | `ms-settings:network`                                           |
| Status                         | `ms-settings:network-status`                                    |
| Show available networks        | `ms-availablenetworks:`                                         |
| Cellular & SIM                 | `ms-settings:network-cellular`                                  |
| Wi-Fi                          | `ms-settings:network-wifi`                                      |
| Show available networks        | `ms-availablenetworks:`                                         |
| Manage known networks          | `ms-settings:network-wifisettings`                              |
| Wi-Fi Calling                  | `ms-settings:network-wificalling`                               |
| Ethernet                       | `ms-settings:network-ethernet`                                  |
| Dial-up                        | `ms-settings:network-dialup`                                    |
| DirectAccess (where available) | `ms-settings:network-directaccess`                              |
| VPN                            | `ms-settings:network-vpn`                                       |
| Airplane mode                  | `ms-settings:network-airplanemode` <br> `ms-settings:proximity` |
| Mobile hotspot                 | `ms-settings:network-mobilehotspot`                             |
| NFC                            | `ms-settings:nfctransactions`                                   |
| Data usage                     | `ms-settings:datausage`                                         |
| Proxy                          | `ms-settings:network-proxy`                                     |

# Personalization

| Page                                 | URI                                                            |
| ------------------------------------ | -------------------------------------------------------------- |
| Personalization                      | `ms-settings:personalization`                                  |
| Background                           | `ms-settings:personalization-background`                       |
| Colors                               | `ms-settings:personalization-colors` <br> `ms-settings:colors` |
| Lock screen                          | `ms-settings:lockscreen`                                       |
| Themes                               | `ms-settings:themes`                                           |
| Fonts (build 17083+)                 | `ms-settings:fonts`                                            |
| Start                                | `ms-settings:personalization-start`                            |
| Choose which folders appear on Start | `ms-settings:personalization-start-places`                     |
| Taskbar                              | `ms-settings:taskbar`                                          |

# Apps

| Page                     | URI                                                            |
| ------------------------ | -------------------------------------------------------------- |
| Apps & features          | `ms-settings:appsfeatures` <br> `ms-settings:appsfeatures-app` |
| Manage optional features | `ms-settings:optionalfeatures`                                 |
| Default apps             | `ms-settings:defaultapps`                                      |
| Offline maps             | `ms-settings:maps`                                             |
| Download maps            | `ms-settings:maps-downloadmaps`                                |
| Apps for websites        | `ms-settings:appsforwebsites`                                  |
| Video playback           | `ms-settings:videoplayback`                                    |
| Startup                  | `ms-settings:startupapps`                                      |

# Accounts

| Page                            | URI                                                     |
| ------------------------------- | ------------------------------------------------------- |
| Your info                       | `ms-settings:yourinfo`                                  |
| Email & accounts                | `ms-settings:emailandaccounts`                          |
| Sign-in options                 | `ms-settings:signinoptions`                             |
| Windows Hello face setup        | `ms-settings:signinoptions-launchfaceenrollment`        |
| Windows Hello fingerprint setup | `ms-settings:signinoptions-launchfingerprintenrollment` |
| Security Key setup              | `ms-settings:signinoptions-launchsecuritykeyenrollment` |
| Dynamic Lock                    | `ms-settings:signinoptions-dynamiclock`                 |
| Access work or school           | `ms-settings:workplace`                                 |
| Family & other people           | `ms-settings:otherusers`                                |
| Set up a kiosk                  | `ms-settings:assignedaccess`                            |
| Sync your settings              | `ms-settings:sync`                                      |

# Time & language

| Page                                  | URI                                                                            |
| ------------------------------------- | ------------------------------------------------------------------------------ |
| Date & time                           | `ms-settings:dateandtime`                                                      |
| Region                                | `ms-settings:regionformatting`                                                 |
| Japan IME settings (where available)  | `ms-settings:regionlanguage-jpnime`                                            |
| Pinyin IME settings (where available) | `ms-settings:regionlanguage-chsime-pinyin`                                     |
| Wubi IME settings (where available)   | `ms-settings:regionlanguage-chsime-wubi`                                       |
| Korea IME settings (where available)  | `ms-settings:regionlanguage-korime`                                            |
| Language                              | `ms-settings:regionlanguage` <br> `ms-settings:regionlanguage-languageoptions` |
| Windows Display language              | `ms-settings:regionlanguage-setdisplaylanguage`                                |
| Add Display language                  | `ms-settings:regionlanguage-adddisplaylanguage`                                |
| Keyboard (removed in build 17083+)    | `ms-settings:keyboard`                                                         |
| Speech                                | `ms-settings:speech`                                                           |

# Gaming

| Page                                | URI                                 |
| ----------------------------------- | ----------------------------------- |
| Game bar                            | `ms-settings:gaming-gamebar`        |
| Captures                            | `ms-settings:gaming-gamedvr`        |
| Broadcasting                        | `ms-settings:gaming-broadcasting`   |
| Game Mode                           | `ms-settings:gaming-gamemode`       |
| TruePlay (removed in version 1809+) | `ms-settings:gaming-trueplay`       |
| Xbox Networking                     | `ms-settings:gaming-xboxnetworking` |

# Extras

| Page                                                           | URI                  |
| -------------------------------------------------------------- | -------------------- |
| Extras (available only when Settings app extensions installed) | `ms-settings:extras` |

# Ease of Access

| Page                                     | URI                                                      |
| ---------------------------------------- | -------------------------------------------------------- |
| Display                                  | `ms-settings:easeofaccess-display`                       |
| Mouse Pointer                            | `ms-settings:easeofaccess-cursorandpointersize`          |
| Text Cursor                              | `ms-settings:easeofaccess-cursor`                        |
| Magnifier                                | `ms-settings:easeofaccess-magnifier`                     |
| Color Filters                            | `ms-settings:easeofaccess-colorfilter`                   |
| Adaptive Color Filters Link              | `ms-settings:easeofaccess-colorfilter-adaptivecolorlink` |
| Night Light Link                         | `ms-settings:easeofaccess-colorfilter-bluelightlink`     |
| High Contrast                            | `ms-settings:easeofaccess-highcontrast`                  |
| Narrator                                 | `ms-settings:easeofaccess-narrator`                      |
| Start Narratorafter sign-in for me       | `ms-settings:easeofaccess-narrator-isautostartenabled`   |
| Audio                                    | `ms-settings:easeofaccess-audio`                         |
| Closed captions                          | `ms-settings:easeofaccess-closedcaptioning`              |
| Speech                                   | `ms-settings:easeofaccess-speechrecognition`             |
| Keyboard                                 | `ms-settings:easeofaccess-keyboard`                      |
| Mouse                                    | `ms-settings:easeofaccess-mouse`                         |
| Eye Control                              | `ms-settings:easeofaccess-eyecontrol`                    |
| Other options (removed in version 1809+) | `ms-settings:easeofaccess-otheroptions`                  |

# Search (version 1903+)

| Page                  | URI                                 |
| --------------------- | ----------------------------------- |
| Permissions & history | `ms-settings:search-permissions`    |
| Searching Windows     | `ms-settings:cortana-windowssearch` |
| More details          | `ms-settings:search-moredetails`    |

# Cortana

| Page            | URI                                 |
| --------------- | ----------------------------------- |
| Cortana         | `ms-settings:cortana`               |
| Talk to Cortana | `ms-settings:cortana-talktocortana` |
| Permissions     | `ms-settings:cortana-permissions`   |
| More details    | `ms-settings:cortana-moredetails`   |

# Privacy

| Page                                       | URI                                                 |
| ------------------------------------------ | --------------------------------------------------- |
| General                                    | `ms-settings:privacy`                               |
| Speech                                     | `ms-settings:privacy-speech`                        |
| Inking & typing personalization            | `ms-settings:privacy-speechtyping`                  |
| Diagnostics & feedback                     | `ms-settings:privacy-feedback`                      |
| View Diagnostic Data                       | `ms-settings:privacy-feedback-telemetryviewergroup` |
| Activity history (build 17040+)            | `ms-settings:privacy-activityhistory`               |
| Location                                   | `ms-settings:privacy-location`                      |
| Camera                                     | `ms-settings:privacy-webcam`                        |
| Microphone                                 | `ms-settings:privacy-microphone`                    |
| Voice activation                           | `ms-settings:privacy-voiceactivation`               |
| Notifications                              | `ms-settings:privacy-notifications`                 |
| Account info                               | `ms-settings:privacy-accountinfo`                   |
| Contacts                                   | `ms-settings:privacy-contacts`                      |
| Calendar                                   | `ms-settings:privacy-calendar`                      |
| Phone calls (removed in version 1809+)     | `ms-settings:privacy-phonecalls`                    |
| Call history                               | `ms-settings:privacy-callhistory`                   |
| Email                                      | `ms-settings:privacy-email`                         |
| Eye tracker (requires eyetracker hardware) | `ms-settings:privacy-eyetracker`                    |
| Tasks                                      | `ms-settings:privacy-tasks`                         |
| Messaging                                  | `ms-settings:privacy-messaging`                     |
| Radios                                     | `ms-settings:privacy-radios`                        |
| Other devices                              | `ms-settings:privacy-customdevices`                 |
| Background apps                            | `ms-settings:privacy-backgroundapps`                |
| App diagnostics                            | `ms-settings:privacy-appdiagnostics`                |
| Automatic file downloads                   | `ms-settings:privacy-automaticfiledownloads`        |
| Documents                                  | `ms-settings:privacy-documents`                     |
| Pictures                                   | `ms-settings:privacy-pictures`                      |
| Videos                                     | `ms-settings:privacy-documents`                     |
| File system                                | `ms-settings:privacy-broadfilesystemaccess`         |

# Update & security

| Page                                | URI                                                                                        |
| ----------------------------------- | ------------------------------------------------------------------------------------------ |
| Windows Update                      | `ms-settings:windowsupdate`                                                                |
| Check for updates                   | `ms-settings:windowsupdate-action`                                                         |
| View update history                 | `ms-settings:windowsupdate-history`                                                        |
| Restart options                     | `ms-settings:windowsupdate-restartoptions`                                                 |
| Advanced options                    | `ms-settings:windowsupdate-options`                                                        |
| Change active hours                 | `ms-settings:windowsupdate-activehours`                                                    |
| Optional updates                    | `ms-settings:windowsupdate-optionalupdates`<br> `ms-settings:windowsupdate-seekerondemand` |
| Delivery Optimization               | `ms-settings:delivery-optimization`                                                        |
| Windows Security / Windows Defender | `ms-settings:windowsdefender`                                                              |
| Open Windows Security               | `windowsdefender:`                                                                         |
| Backup                              | `ms-settings:backup`                                                                       |
| Troubleshoot                        | `ms-settings:troubleshoot`                                                                 |
| Recovery                            | `ms-settings:recovery`                                                                     |
| Activation                          | `ms-settings:activation`                                                                   |
| Find My Device                      | `ms-settings:findmydevice`                                                                 |
| For developers                      | `ms-settings:developers`                                                                   |
| Windows Insider Program             | `ms-settings:windowsinsider` <br> `ms-settings:windowsinsider-optin`                       |

# Mixed reality

| Page             | URI                                           |
| ---------------- | --------------------------------------------- |
| Mixed reality    | `ms-settings:holographic`                     |
| Audio and speech | `ms-settings:holographic-audio`               |
| Environment      | `ms-settings:privacy-holographic-environment` |
| Headset display  | `ms-settings:holographic-headset`             |
| Uninstall        | `ms-settings:holographic-management`          |

# Surface Hub

| Page                   | URI                                       |
| ---------------------- | ----------------------------------------- |
| Accounts               | `ms-settings:surfacehub-accounts`         |
| Team Conferencing      | `ms-settings:surfacehub-calling`          |
| Team device management | `ms-settings:surfacehub-devicemanagenent` |
| Session cleanup        | `ms-settings:surfacehub-sessioncleanup`   |
| Welcome screen         | `ms-settings:surfacehub-welcome`          |


---
Sources:
- 2021-08-13: [List of ms-settings URI commands to open specific settings in Windows 10 – 4sysops](https://4sysops.com/wiki/list-of-ms-settings-uri-commands-to-open-specific-settings-in-windows-10/history/?revision=1555539)
- 2021-11-19: [ms-settings: URI scheme reference](https://docs.microsoft.com/en-us/windows/uwp/launch-resume/launch-settings-app#ms-settings-uri-scheme-reference)

Related:

Tags:
