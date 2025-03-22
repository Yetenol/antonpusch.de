---
date: "2025-03-22T23:45:55.004+01:00"
title: "Microsoft Edge"
description: "-"
dg-folder: computer/apps
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
```dynamic-embed
[[Describe this app and list installation sources]]
```

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

```dynamic-embed
[[List extensions for this app]]
```

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