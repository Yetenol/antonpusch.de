---
title: "Microsoft Edge"
date: "2025-01-03T00:00:00.000+01:00"
dg-publish: true
microsoft-id: XPFFTQ037JWMHS
winget-id: Microsoft.Edge
github-repo: SimonBrazell/privacy-redirect
github-release-filename: 
website: 
priority: 1
link-modportals:
  - "[Edge Add-ons](https://microsoftedge.microsoft.com/addons/detail/~modportal0-id~)"
  - "[Chrome Web Store](https://chrome.google.com/webstore/detail/~modportal1-id~)"
modportal0-id: 
thumbnail: 
categories:
  - Office
synopsis: Microsoft Edge is the best performing browser on Windows 10.  Let Microsoft Edge help you stay in the flow, save big while shopping, and stay safer online with built-in tools that simply make browsing better.
not-in-use: true
cssclasses:
  - cards
dg-content-classes:
  - cards
---
Microsoft Edge is a **discarded** [essential](install%20essential%20apps.md.md), [office](install%20office%20apps.md.md) app. Microsoft Edge is the best performing browser on Windows 10.  Let Microsoft Edge help you stay in the flow, save big while shopping, and stay safer online with built-in tools that simply make browsing better.

- Open in [Microsoft Store](ms-windows-store://pdp/?ProductId=XPFFTQ037JWMHS&mode=mini) or invoke:
  ```
  winget install -e XPFFTQ037JWMHS --accept-package-agreements
  ```
- Invoke the installer listed on Windows Package Manager:
  ```powershell
  winget install -e Microsoft.Edge
  ```
- Download the [latest release](https://github.com/SimonBrazell/privacy-redirect/releases/latest) of its source code [repository](https://github.com/SimonBrazell/privacy-redirect) on GitHub


# Add custom search engines

```
about:settings/searchEngines
```

- `Google` ← Search engine used in the address bar

| Search engine             | Keyword                 | URL with %s in place of query                                                                    |
| ------------------------- | ----------------------- | ------------------------------------------------------------------------------------------------ |
| DeepL                     | deepl.com               | `https://www.deepl.com/translator#../../%s`                                                      |
| Duden                     | duden.de                | `https://www.duden.de/suchen/dudenonline/%s`                                                     |
| LaTeX Documentation       | texdoc.org              | `http://texdoc.org/serve/%s/0`                                                                   |
| LaTeX Documentation       | ctan.org                | `https://ctan.org/pkg/%s`                                                                        |
| Wolfram Alpha             | wolframalpha.com        | `https://www.wolframalpha.com/input?i=%s`                                                        |
| IMDb                      | imdb.com                | `https://www.imdb.com/find/?ref_=opensearch&q=%s`                                                |
| JustWatch                 | justwatch.com           | `https://www.justwatch.com/de/Suche?q=%s`                                                        |
| Unicode Character Table   | unicode-table.com       | `https://symbl.cc/en/search/?q=%s`                                                               |
| MOSES Modul Kurzübersicht | moseskonto.tu-berlin.de | `https://moseskonto.tu-berlin.de/moses/modultransfersystem/bolognamodule/ansehen.html?number=%s` |
| Google Maps               | maps.google.com         | `https://www.google.com/maps/search/%s`                                                          |

# Toggle experimental features

| Status   | Flag                                             | Description                       |
| -------- | ------------------------------------------------ | --------------------------------- |
| Disabled | `about:flags/#overscroll-history-navigation`     | Two-finger overscroll navigations |
| Disabled | `about:flags/#edge-show-feature-recommendations` | Recommends Bing as search engine  |

# Extensions

| Name                                               | Thumbnail                                                                                                                                                                                             | Modportal links                                                                                                                                                                                    | Categories | Description                                                                       |
| -------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- | --------------------------------------------------------------------------------- |
| **[Privacy Redirect](./privacy-redirect.md)** | ![](https://lh3.googleusercontent.com/pC5a_u12RlaLQhJ-5Jz87rtju2s0tCksUfZHvr3JYzAaiYZJfJapmuftodT7wuAedFOHtgxR2BGh_GmKijgiK5bJyA=w128-h128-e365-rj-sc0x00ffffff)                                      | [Edge Add-ons](https://microsoftedge.microsoft.com/addons/detail/elnabkhcgpajchapppkhiaifkgikgihj), [Chrome Web Store](https://chrome.google.com/webstore/detail/pmcmeagblkinmogikoikkdjiligflglb) | \-         | Redirects Twitter, YouTube, Instagram and more to privacy friendly alternatives.  |
| **[uBlock Origin](./ublock-origin.md)**       | ![](https://store-images.s-microsoft.com/image/apps.13212.a2659c2b-e8a2-4d0e-8b43-757be3f59cb5.2d0e9ee2-fee9-493a-9feb-124e50294b05.78dc92a0-64c2-47e3-a16b-6ef3f3025a18?mode=scale&h=100&q=90&w=100) | [Edge Add-ons](https://microsoftedge.microsoft.com/addons/detail/odfafepnkmbhccpbejgmiehpchacaeak), [Chrome Web Store](https://chrome.google.com/webstore/detail/cjpalhdlnbpafiamejdnhcphjbkeiagm) | \-         | Finally, an efficient blocker. Easy on CPU and memory.                            |


- Hide extensions from toolbar
    - Click on `Extensions button` in the toolbar
    - Disable `Show in toolbar` (eye icon) for all extensions

## Add keyboard shortcuts

```
about:extensions/shortcuts
```

- `Alt + Shift + D` ← Toggle current site _# Dark Reader_
- `Ctrl + Shift + 2` ← Choose another field in KeeWeb _# KeeWeb Connect_
- `Ctrl + Shift + 1` ← One-time codes _# KeeWeb Connect_
- `Ctrl + Shift + V` ← Submit the form automatically _# KeeWeb Connect_

# Modify settings manually

## Hide Bing Discover button

```
edge:settings/sidebar/appSettings?hubApp=2354565a-f412-4654-b89c-f92eaa9dbd20
```

- [ ] Show Discover

## Sync 

```
about:settings/profiles/sync
```

- Sign in to turn on sync
- [x] Favorites
- [x] Settings
- [ ] Basis info
- [ ] Passwords
- [ ] History
- [ ] Open tabs
- [x] Extensions
- [x] Collections
- [ ] Payments using Microsoft account

## Appearance

```
about:settings/appearance
```

- `System default` ← Overall appearance
- Scroll to `Customize toolbar`
- [x] Show tab actions menu
- [x] Hide title bar while in vertical tabs
- `Turn on` ← Show vertical tabs for all current browser windows
- `Only on new tabs` ← Show favorites bar
- Scroll to `Select which buttons to show on the toolbar:`
- [ ] Home button `[Alt+Home]`
- `Show automatically` ← Extensions button 
- [x] Favorites buttons `[Ctrl+Shift+O]`
- [ ] Collections button `[Ctrl+Shift+Y]`
- [ ] History button `[Ctrl+H]`
- [ ] Downloads button
- [ ] Web capture button `[Ctrl+Shift+S]`
- [ ] Share button
- [ ] Feedback button

## When Edge starts

```
about:settings/onStartup
```

- `Open the new tab page` ← When Edge starts

## Setup content handling

Block the following permission requests
```
about:settings/content/location
```
```
about:settings/content/notifications
```