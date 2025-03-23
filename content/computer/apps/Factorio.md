---
date: "2025-03-23T10:21:19.719+01:00"
title: "Factorio"
description: "A game about automation, logistics and network optimizations"
dg-folder: computer/apps
dg-publish: true
microsoft-id: 
winget-id: 
github-repo: 
github-release-filename: 
website: https://factorio.com/download
priority: 10
link-modportals:
  - "[Mod portal](https://mods.factorio.com/mod/~modportal0-id~)"
categories:
  - Gaming
backup-install-media: https://onedrive.live.com/download?cid=1D2B2E681295AC2B&resid=1D2B2E681295AC2B%21419737&authkey=AG1w_3MTEaosDeQ
synopsis: Factorio is a game in which you build and maintain factories.
steam-id: "427520"
cssclasses:
  - cards
dg-content-classes:
  - cards
thumbnail: https://styles.redditmedia.com/t5_2wabp/styles/communityIcon_lnp25hfmcbg01.png
---

![thumbnail](https://styles.redditmedia.com/t5_2wabp/styles/communityIcon_lnp25hfmcbg01.png) Factorio - A game about automation, logistics and network optimizations is a [gaming](install%20gaming%20apps.md.md) app. Factorio is a game in which you build and maintain factories.

- Download it from the [publisher's website](https://factorio.com/download)
- Open in [Steam](steam://store/427520)


# Tips to play the game

# Aspects of the game

- Building supplies - Bulk craft any item without a mall
- Train network
- Flying robots
- Logistics in Factorio
- Input controls
- Base layouts
- Circuit networks
- Main bus, Compact bus
- City block
- Modules
- Combat

# Discussions

- Should logistic bots supply only the character or the factory as well
- How far can you reach - How much can you do remotely
- Turret creep

# Playstyles

- [Biters pathing logic - Factorio Forums](https://forums.factorio.com/viewtopic.php?t=78808)
- Compact bus
- Main bus
- City block
- Don't produce main green chips, steel from main bus
- If your factory is bad, use your resources to build a better one
- Smelt ores directly at outpost using brought-in coal
- Produce power locally in outpost using brought-in coal
- Rail reach all mall chests
- Don't plan ahead
- Wrong ways to play Factorio
- Design factories in Factorio

Combat
- Use area of affect weapons like grenades, flamethrowers, poison capsules (worms)
- Don't turret creep, use combat robots
- [Ideas to Avoid Turret Creeping - Factorio Forums](https://forums.factorio.com/viewtopic.php?t=32867)
- [Friday Facts #166 - Combat Revisit | Factorio](https://www.factorio.com/blog/post/fff-166)

Mobility
- Move around using personal resupply trains or by hijacking regular trains
- Drive parallelly to the terrain [VehicleSnap](./VehicleSnap.md)
- Cruise drive on paved roads incentivizes you to build mobility infrastructure [Pavement Drive Assist](./Pavement-Drive-Assist.md)

Remote access, far reach
- How far can you reach - How much can you do remotely

# Possible phases of the game

- Jump start base
- Starter base phase

Early game
- Logistics: spaghetti 
- modular armor with loaded up shields
- build pollution stuff in chunks with many trees, trees damaging obsorbs 10 pollution 
- Build row of 8 assemblers
- change assembler recipes instead of belt automation
- build in surrounding chunks to prevent biter expansion 
- leave one wide gap between turrets
- mark wall for deconstruction to make them only-player-passable
- [Can you beat FACTORIO when the Biters start at 100% EVOLUTION - Full Movie (edited) - YouTube](https://youtu.be/KWBtboASrRM?si=StWIdFpGOzAWwaTs)

Don'ts
- Build spontaneously instead of planning ahead. The factory can easily be moved. Future requirements can usually be better implemented with a new factory section instead of upgrading existing ones.
- If you hand-craft something you should probably add it to your mall.
- If you are afk to wait for something to finish, a research or crafting
- If hand-crafting takes too long, use assembling machines with speed modules
- Don't play afk to wait for a research to finish, improve your production instead
- Don't use buffers. They make seeing your actual production harder.
- Don't drive trains manually. Temporary stops are much safe to travel with.
- Overproduce instead of balancing the output precisely

Defence, Outposts
- Don't attack from the north, less visibility 
- Biters attack polluting machines (boiler, drills, pumpjack, refinery) and military targets (radar, walls, turrets)
- Space out turrets at almost double shotting range to catch at incoming biters, temporarily space turret in the mittle to show ideal distance 
- Build outposts instead of walling in everything, which gets hard to expand
- Kill the nests in your pollution cloud
- Move half of the resource patch's ores in the opposite direction in order to increase mining on the richer center
- All outposts stations should be reachable independently from a bidirectional connection to the railroad
- Wall of turrets with a one wide gap to prevent biters from reaching over
- Leave 1 wide gap between turrets to prevent slash damage
- Place distanced flamethrower turrets
- Place repair roboports as far from wall as possible to let the flamethrower fire disappear before the bots reach the wall
- Round of wall edges
- Turret creep: Not have more entities in the blueprint than your personal roboports (10 robots each) can build at once to force the power to be built on the first flight, no corner turrets
- Power armor: charge batteries with solar panels, replace with shields
- Built roboport network in separate rectangles, so bots don't fly out of it

Trains
- Use double headed trains on bidirectional outposts and connect them with directional railroads
- Personal resupply train that can refill from the mall
- Refuel trains automatically [Automatic Train Fuel Stop](./Automatic-Train-Fuel-Stop.md)
- Place rails everywhere you want to visit like mall, defenses, miners
- Refuel stop that auto detect train length

Tweak game aspects - Does this mod go to far?

- [Discover and lookup recipes in Factorio](../../Discover-and-lookup-recipes-in-Factorio.md)

# External Sites

- [Seven Years of Factorio Friday Facts · William Spies](https://spieswl.github.io/blog/2020/seven-years-of-factorio-friday-facts)
- [FactorioLab Ratio Calculator](https://factoriolab.github.io/)
- [Factorio Cheat Sheet](https://factoriocheatsheet.com/)

# Extensions

- Picket Dollies: Move combinators
- Tree Xray: See below trees
- Temporary Stop Default: No 5s restart timer

```dynamic-embed
[[List extensions for this app]]
```


Replace local settings with synchronized cloud settings

```powershell
New-Item "$env:AppData\Factorio" -Target "D:\PlutosCloud\Gaming\Factorio Space Age" -ItemType SymbolicLink -Force
$filesToKeepAvailable = Get-ChildItem "D:\PlutosCloud\Gaming\Factorio Space Age" -Recurse
$filesToKeepAvailable += Get-Item "D:\PlutosCloud\Gaming\Factorio Space Age"
$filesToKeepAvailable | foreach {
    $_.Attributes = $_.Attributes -bor 0x080000 -band (-bnot 0x100000)
}
```

---
Sources:

Related:
```dynamic-embed
[[List related notes]]
```

Tags:
