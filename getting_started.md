---
layout: page
title: "Getting started"
description: ""
group: navigation
scrollspy: [Setting titles, Using scoreboards, Permissions] 
---
{% include JB/setup %}

<p class="lead">Getting started with jChat couldn't be easier. Just download and drag it into your plugins folder and away you go. Still stuck? Read on.</p>

<div class='alert alert-block'>
These documentation is for version 2.0.0 and beyond. If you are using an earlier version please read the documentation available on the jChat wiki.
</div>

## Setting titles

You can easily create titles by modifying `titles.yml` file in the jChat configuration directory. In the following example I am going to create a title for the moderators on my server. The title will give them a yellow name.

    moderators:
      prefix: '§e'
      suffix: ''
      weight: 0
      
The name of the title is designated by the name of the section which is in this case `moderators`. To give this title to someone I will need to grant them the `jchat.title.moderators` permission. 

jChat will add a reset colour code to the end of a players name. This means that regardless of your settings any text typed by the player will be in white.

### Configuring title weights

Additionally you can set weights to the titles you configure. Consider the following example:

    moderators:
      prefix: '§e'
      suffix: ''
      weight: 0
    resident:
      prefix: '§2'
      suffix: ''
      weight: 1

If a player has both `jchat.title.moderators` and `jchat.title.resident`, prehaps through inheriting permission groups, the plugin will first check if they have the moderator title before checking resident. Heavier titles 'sink' to the bottom of the list while lighter ones rise to the top. 

### Refreshing titles

Occassionally you might need to refresh the title you have given to a player, for example when their permissions are updated. jChat automatically updates display names when a player joins the server and when they change worlds. To force an update type `jchat refresh [name of player]`.

## Using scoreboards

You can use the new scoreboard support introduced in version 2.0.0 to make any changes to a player's display name visible above their head and on the player list (the list retrieved when pressing Tab in game). Enable scoreboard support in `config.yml` and then configure the titles in `titles.yml`

In the following example I am going to setup the plugin to give all residents a blue name and add the suffix `(guest)` to their name on the player list.

    default:
      prefix: '§3'
      suffix: ''
      weight: 0
      scoreboard:
        display-name: "guest"
        append-team-name: true
        friendly-fire: false
        see-invisibles: false

To turn this feature off set `append-team-name` to false.

## Permissions

<dl>
  <dt>jchat</dt>
  <dd>Allow access to everything in the plugin (defaults op)</dd>
  <dt>jchat.reload</dt>
  <dd>Allow a player to reload the plugin's configuration (defaults op)</dd>
  <dt>jchat.refresh</dt>
  <dd>Allow a player refresh the display name of any player (defaults op)</dd>
  <dt>jchat.refresh.self</dt>
  <dd>Allow a player to refresh their own display name (defaults true)</dd>
  <dt>jchat.refresh.others</dt>
  <dd>Allow a player to refresh the display name of others (defaults op)</dd>
</dl>
