---
layout: page
title: "Getting started"
description: ""
group: navigation
scrollspy: [Setting homes, Going home, Permissions] 
---
{% include JB/setup %}

<p class="lead">Getting started with Hearthstone couldn't be easier. Just download and drag it into your plugins folder and away you go. Still stuck? Read on.</p>

## Setting homes

Players can set a home anywhere in the game world with two exceptions. Firstly players may not set homes in areas where they are unable to build. Secondly they can not use an obstructed location. Hearthstone considers any area which is not made out of air and does not have enough space for the player to teleport to as obstructed.

You can set your own home by typing either `/home set` or `/hs set`; both do exactly the same thing. There is no cooldown when setting a new home and you can do it as often as you like.

Players are allowed to set one home per world. If they set another one when they already have an existing home, it will forget about the other one.

### Setting other players homes

You can also set a home for someone else using the same command. This works exactly the same way but you need to supply the name of the player whos home you want to set. For example `/hs set grandwazir` would set my home to your current location.

### Restricting home locations

You can also prevent players from setting a world in a location where they are unable to build. This is helpful for example in adventure maps where teleportation could cause you problems.

All you need to do is download WorldGuard and region the areas of your world. Hearthstone will check with WorldGuard to see if a player is allowed to build in an area. It is that simple!
## Going home

You can teleport home at any time by typing `/home` providing it is not cooling down. This will instantly teleport to your home in your current world. Unless I have permission I would not be able to teleport again until my cooldown has expired.

You can also teleport to homes located in other worlds by typing `/hs teleport grandwazir world_nether`. This would teleport me to my secret nether fortress.

### Teleporting to other players homes

Additionally you can teleport to a home belonging to any player in any world. This command still enforces a cooldown, so it you may want to make sure your moderators are except from the cooldown when you give them permission to use this command. For example I am going to teleport to Fuzic's house in the current world by typing `/hs teleport fuzic`.

### Cooldown between teleports

It is possible for administrators to force players to obey a cooldown between teleports. This is useful to prevent players repeatedly setting and teleporting home as a travel, safety or griefing exploit. You set the amount of time you wish players to wait by changing the value of cooldown in the config.yml. By default it looks like this:

    cooldown: 15m

## Permissions

Each command is assigned its own permission node and all follow the same style. The full list of available permissions, and their defaults, is below. Additionally there is the `hearthstone.teleport.cooldown` node. Players who have this permission will not be able to teleport home unless the cooldown time has expired.

    hearthstone.set (op)
    hearthstone.set.own (true)
    hearthstone.set.others (op)
    hearthstone.teleport (op)
    hearthstone.teleport.own (true)
    hearthstone.teleport.others (op)
    hearthstone.teleport.cooldown (!op)
