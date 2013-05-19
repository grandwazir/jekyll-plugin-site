---
layout: page
title: "Features"
description: ""
group: navigation
scrollspy: [Banning, Recording, Tab completion, Alias integration]
---
{% include JB/setup %}

<p class="lead">{{ site.title }} allows administrators and other trusted users to ban and kick players. It is a lightweight solution for all servers. The plugin stores all bans in a database of your choice.</p>

## Banning

You can ban players permanently or for a period of time using BanHammer's flexible system. When a player is banned they are notified of the reason when they are kicked and optionally the action is broadcasted to everyone in the game.

#### Configurable ban limits

This allows you to permit players to ban only up to a specified amount of time. This is useful if you only want to give a certain type of player temporary ban power rather than allowing them to ban permenantly.

The limits provided by the plugin exist as an example for you to setup your own. View the getting started page for more details on how to set up this feature.

#### Immune players

You can also setup a list of players who cannot be banned by the plugin. These players can only be banned by players who are operators on your server.

### Notifications

When a player who is banned attempts to join the server they will recieve a different notification depending on what type of ban they received. The notification is the message displayed to the player when they attempt to login to the server.

#### Temporary bans

<p><img src="http://archive.armathia.net/assets/banhammer/temp-ban-example.png" class="img-polaroid" /></p>

#### Permanent bans

<p><img src="http://archive.armathia.net/assets/banhammer/permenant-ban-example.png" class="img-polaroid" /></p>

## Recording

All bans are stored in a database of your choice using the Bukkit persistence system. By default this means an SQLite3 database. It is not necessary to configure your own database unless you want to. 

For each ban the plugin records:

* The name of the player
* The name of the person who banned them
* The reason they gave for the ban
* The date it was made
* The date it will expire (if applicable)

BanHammer supports any of the databases that Bukkit currently supports, which at the time of writing, are SQLite3 and MySQL. You can easily access these bans to create a custom ban list for your website.

You can also audit the number of bans made by your players to check how they are using the plugin. 

### Ban management

You can view your own ban history, or that of any other player, quickly and easily within the game. You can also revoke previous bans, clear the history of a player altogether and export or import bans from the stock minecraft list.

There is also the ability to review recent bans; a useful feature if you want to see who has been banned while you are away.

## Tab completion

BanHammer now features tab completion for all commands where it is appropriate. This means it is never been easier to manage the bans on your server. Simply start typing a player's name and press tab and it will automatically match the name either from the people online or from the database.

The same feature has been extended to completing names of commands and the names of limits. Go and try it out; it is awesome!

## Alias integration

By default BanHammer is a name based banning system. This means that it has no concept of IP addresses and does not store them. You can however get this ability by downloading an additional plugin called Alias.

What this does every time a player logins it the plugin will check with Alias to see if IP address is shared with any other players. If the address is shared with a banned player, BanHammer will then ban the player logging in with the same ban.

For example I ban Tim from my server for property damage. He then returns with an alternative account. Alias and Banhammer know it is the same address and will ban his new account with the same reason I gave for banning Tim. If I banned him temporarily both bans will expire at the same time.

This is a very useful feature to help make bans stick and add more hassle to people who choose to use alternative accounts to grief servers.

