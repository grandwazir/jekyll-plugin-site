---
layout: page
title: "Features"
description: ""
group: navigation
---
{% include JB/setup %}

<p class="lead">{{ site.title }} allows administrators and other trusted users to check if a player has used any other account on your server. It is a lightweight solution for all servers. The plugin stores all bans in a database of your choice.</p>

## Tracking 

Alias automatically tracks the IP address of every player who joins your server and then associates it with a player. If multiple players have the same address they will share the same address in the database. This is helpful when attempting to determine if two players are the same person.

## Stable API

Alias has a stable API for other plugins to use. This means that if an administrator has Alias installed you do not need to worry about matching and storing addresses yourself. A list of some plugins that currently use Alias includes:

* BanHammer
* CanTheSpam
