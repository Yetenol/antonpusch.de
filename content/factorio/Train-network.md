---
date: "2025-03-29T14:51:40.898+01:00"
title: "Train network"
description: "-"
dg-folder: factorio
dg-publish: true
---
Trains
- **Single resource**: Only one item, or fluid per train, Massively **simplifies schedules**
- **Refuel**: Interrupt refueling station, Can force upgrade the fuel type
- **Generic** schedules: Use train groups, Use generic schedules using interrupts dependent on picked up cargo
- **Train limit 1**: Replaces train stackers, **Prevent** train **queues** on the main track, 
- **Bidirectional** trains: Locomotives on both ends of the train, Allow more **compact** stations using terminus[^1] aka. terminal station

Pickup stations
- Generic item, or fluid pickup
- Buffer one train load (40 slots) per wagon, usually 4 chests limited to 10 slots each

Dropoff stations
- Specific to one item, or fluid
- Generic pickup stations
- Train must always unload completely
    - enable stop $\iff$ entire buffer runs low (<1000 items)
    - multiple buffer chests per wagon
    - balance consumption between wagons

Rail tracks
- Separate tracks per direction: Prevents deadlocks
- Leave sufficient space for signals between lanes (6 tiles in 1.1)
- Don't align to grid: Grids are inflexible, Adapt to terrain
- Build power lines, signals separately: 
- **Rail planner**: Don't use blueprint aligned to a grid, Adapt your tracks to the terrain instead of landfilling and flattening it to fit your blueprint
- Redundant routes: Bypass high traffic, if you temporary stop on main track
- No main base: Distributed production if more expandable and spreads out traffic

Junctions

Deprecated 

- 4 directional lanes
- left-hand traffic
- path block are straight, t-junctions, curves, or stations
- provider stations enable when a train could be fully loaded
    - minimun of stations to deposit all trains is always ensured
- requester stations enable when a train could be fully unloaded
    - if demand surpases production, only 1 or 2 of the 3 stations enable, cycle through all requester stations and only assign one train the iteration
- no roundabouts
- no 4-way intersection
- Build a rail network out of t-junctions instead of roundabouts


---
Sources:
[^1]: [Train station - Wikipedia](https://en.wikipedia.org/wiki/Train_station#Terminus)

Related:

Tags:
