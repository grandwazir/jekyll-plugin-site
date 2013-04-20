---
layout: page
title: "Getting started"
description: ""
group: navigation
scrollspy: [Creating a world, Managing worlds, Teleporting to worlds] 
---
{% include JB/setup %}

<p class="lead">Getting started with DimensionDoor couldn't be easier. Just download and drag it into your plugins folder and away you go. Still stuck? Read on.</p>

## Creating a world

You can create extra worlds easily with DimensionDoor. Each world needs to have an Environment. There is a list of Environment types available in the [Bukkit documentation](http://jd.bukkit.org/apidocs/org/bukkit/World.Environment.html). For our example we will create a new nether world, and import an existing normal world called mining.

* `/dd create nether e:NETHER` creates a nether world.
* `/dd create mining e:NORMAL` creates a normal world.
* `/dd teleport nether` teleports you to the nether world you just made.

### Create a world using a seed

We can also create worlds using seeds. Seeds can either be words or numbers depending on what you want to use. DimensionDoor will do the conversion for you. We do the same technique that Notch uses so words you use to generate worlds in singleplayer will generating the same worlds on your server. To specify a seed we need to prefix it with `s:`; for example `/dd create myWorld e:NORMAL s:sausages`

### Create a world using a custom chunk generator

Instead of creating a world based on the 3 built in environments you can now use custom chunk generators. These allow developers to change everything about how a world is created, from creating ocean worlds to flat land; nearly anything is possible.

DimensionDoor does not have any custom chunk generators of it's own. You will need to [download some](http://plugins.bukkit.org/#ti=&ta=WGEN&au=&subm=false&pno=0) before you will be able to take advantage of this feature. The rest of these examples assume the plugins are already downloaded and enabled.

For our first example we are going to create a completely empty world, using the plugin [NullTerrain](http://forums.bukkit.org/threads/wgen-nullterrain-v0-4-1-generate-empty-worlds-1000.27362/). To specify a custom chunk generator we need to prefix our argument with g: and the plugin name. So in this case we need to type `/dd create emptyWorld e:NORMAL g:NullTerrain`.

Some chunk generators also accept additional arguments. This could be anything from what material you want the world to be made out of, to how many caves you want per chunk depending on the plugin. DimensionDoor supports this also. 

For this example we are going to create a world using the [CleanroomGenerator](http://forums.bukkit.org/threads/wgen-cleanroomgenerator-v0-0-4-clean-room-flat-world-multilayer-chunk-generator-1000.24791/). This is like the first plugin but instead of creating an empty world we can create a world made out of completely one type of block. 

In the following example I am going to create a world where the base height is 64 and made completely of stone. We specific these extra arguments by adding another : after we have provided the plugin name. `/dd create emptyWorld e:NORMAL g:CleanroomGenerator:64,stone` would create a world with those settings.

Different generators work in different ways so make sure to check the documentation for which ever one you are going to use. Regardless of what plugin and arguments you use DimensionDoor will remember your settings so your worlds always load the same way, automatically when the server starts.

#### Beware when importing existing worlds

If you make a mistake and choose the wrong Environment when importing your world it will be deleted and replaced with a new world. There is no way for the plugin to detect the Environment of an unloaded world until it is fully loaded. This in the only scenario when you can lose your world data using DimensionDoor.

## Managing worlds

DimensionDoor includes several commands to help you manage your worlds.

### Deleting a world

If you get bored with a world you can delete it. For the example I am going to remove the world Trev: `/dd remove Trev`

The world will be unloaded from memory and players will no longer be able to use it. DimensionDoor will also forget all about it and not automatically load it next time your server starts. If you wanted to create a new world with the same name, make sure to delete the world data first from your server directory.

### Loading and unloading worlds

You can also load and unload worlds to your heart's content. DimensionDoor will only load worlds it already knows about. If you want to import an existing world use the create command instead. In the following example I am going to load the world fantastic and unload dreary.

* `/dd load fantastic`
* `/dd unload dreary`

The difference between unloading a world and removing it that unloading a world keeps the world specific settings intact. The plugin will still automatically load the world next time the server starts.

### Listing managed worlds

A managed world is a world that DimensionDoor knows about and has configuration saved for. It may not be the same as the number of worlds you have in your server directory (but usually is once you have imported them all). You can list all the worlds that DimensionDoor knows about by typing `/dd list`

Worlds in green are currently loaded, while worlds in red are not.

## Changing world settings

DimensionDoor allows you to set a number of world specific settings. With the exception of one setting, these all mirror normal world properties. For my example below I am going to turn pvp on for my main world, while stopping anything spawning in my creative world.

* `/dd modify world pvp true`
* `/dd modify creative spawnMonsters false`
* `/dd modify creative spawnAnimals false`

You can also set the difficulty of a world, together with your desired game mode. This can be useful if you want to create creative worlds for example. Game mode changes will apply to **all** players in the specified world.

* `/dd modify creative gamemode creative`
* `/dd modify creative difficulty peaceful`

We can check the results by inspecting the configuration for our creative world by typing `/dd info creative`.

### Full list of available attributes

<dl>
<dt>difficulty</dt>
<dd>Change the difficulty of the world.</dd>
<dt>enabled</dt>
<dd>If a world should be loaded when the server starts.</dd>
<dt>game_mode</dt>
<dd>Change the default game mode of the world.</dd>
<dt>spawn_monsters</dt>
<dd>Change if monsters will spawn in the world.</dd>
<dt>spawn_animals</dt>
<dd>Change if a animals will spawn in the world.</dd>
<dt>pvp</dt>
<dd>Set if players are able to hurt each other in the world.</dd>
<dt>keep_spawn_in_memory</dt>
<dd>Set if the spawn of the world should be kept loaded.</dd>
<dt>isolated_chat</dt>
<dd>Set if chat in this world should be private to this world.</dd>
<dt>texture_pack</dt>
<dd>Set a URL to a custom texture pack for this world.</dd>
<dt>respawn</dt>
<dd>Set if a player should respawn in this world when they die.</dd>
</dl>

### World specific chat

An additional feature offered by the plugin is the ability to turn on world specific chat. This allows you to segregated your chat and keep it within individual worlds. For example let us say we have three worlds on our server; armathia, elysium and lethe.

In this scenario I want players in armathia and elysium to be able to talk to each other but keep the chat in lethe separate because it is a roleplay world. We can do this by issuing the following command `/dd modify lethe isolatedChat true`

The easy way to remember how this works if isolatedChat is true players in that world can only chat with players in the same world. If it is off they can chat with players in any world where isolatedChat is false.

Chat messages are preserved exactly as they are sent when isolatedChat is on. You might find it helpful to get another plugin to add a world prefix if you have lots of worlds.

Regardless of the setting chatting through commands, for example /whisper in commandbook, will always work.

### World specific texture packs

New in version 2.2.0 is the ability to set world specific texture packs. These works exactly the same as if you had specified it in your server.properties. To do this you first need a publicly accessible location to download your texture pack from. Once you have done that you apply it to a world using the following command: `/dd modify world TEXTURE_PACK http://example.com/texture.pack`

### Additional settings for creative worlds

In version 1.8 of DimensionDoor there are now extra settings for managing how your players use creative worlds. These settings apply to all creative worlds and are set by editing the configuration file at: plugins/DimensionDoor/inventory_protection_configuration.yml.

#### Preventing items from spawning in creative worlds

This setting prevents any items from spawning in creative worlds. This includes, but is not limited to, drops from when blocks are broken, items when dropped on the floor and items fired from dispensers.

    world-settings:
        preventItemsSpawning: true

If this is not enabled players will be able to drop items on the floor and then pick them up into their inventory and use them on their return.

#### Preventing people bringing items back from creative worlds

There are two new settings to help you manage what people bring back from creative worlds. If enabled they will check every time a player returns a creative world to a survival world. 

The first clears whatever is in a player's hand. The second clears all items from a player's action bar. The third stops players placing items into a chest and then placing those items into their inventory. If you absolutely do not want players to bring anything back through you will need to all three of these plus the option above.

    inventory-settings:
        deleteActionBar: true
        deleteItemInHand: true
    world-settings:
        preventContainerBlocks: true

### Setting new spawn locations

DimensionDoor manages the respawning of players so by default they will always respawn in the world they died in; either to their bed or back to the initial spawn location. You can change the spawn location a world by walking to where you want it to be and typing `/dd spawn`.

You can disable this functionality completely on a world basis by using the following command. In this situation DimensionDoor does not interfere with respawning at all. To do this type `/dd modify world respawn false`.

## Teleporting to worlds

As a convenience feature for setting up new worlds you can teleport to any loaded world by using the teleport command. I am going to teleport to fantastic by typing `/dd teleport fantastic`. You will always be teleported to that world's initial spawn location. 

It is tempting to give players this command but I would recommend you instead look into creating portals to each world using another plugin such as Stargate. This has the added bonus of you being able to control which worlds players can access.

## Permissions

<dl>
<dt>dimensiondoor.*</dt>
<dd>Allows access to everything in the plugin (defaults op).</dd>
<dt>dimensiondoor.access.*</dt>
<dd>Allow a player to access every world in the server (defaults op).</dd>
<dt>dimensiondoor.access.[world]</dt>
<dd>Allow a player to access a specified world (defaults op).</dd>
<dt>dimensiondoor.clear</dt>
<dd>Allow a player to clear a world of monsters and animals (defaults op).</dd>
<dt>dimensiondoor.info</dt>
<dd>Allow a player to read information of a world (defaults op).</dd>
<dt>dimensiondoor.list</dt>
<dd>Allow a player to list all the worlds on the server (defaults op).</dd>
<dt>dimensiondoor.load</dt>
<dd>Allow a player to load an unloaded world (defaults op).</dd>
<dt>dimensiondoor.modify.*</dt>
<dd>Allow a player to modify all world attributes (defaults op).</dd>
<dt>dimensiondoor.modify.[attribute]</dt>
<dd>Allow a player modify a specific attribute for a world (defaults op).</dd>
<dt>dimensiondoor.remove</dt>
<dd>Allow a player to remove a world from the server (defaults op).</dd>
<dt>dimensiondoor.spawn</dt>
<dd>Allow a player to set the spawn of the world (defaults op).</dd>
<dt>dimensiondoor.teleport</dt>
<dd>Allow a player to teleport to other worlds (defaults op).</dd>
<dt>dimensiondoor.unload</dt>
<dd>Allow a player to unload a world (defaults op).</dd>
</dl>
