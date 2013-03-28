---
layout: page
title: "Getting started"
description: ""
group: navigation
scrollspy: [Creating the kit, Giving the kit, Permissions] 
---
{% include JB/setup %}

<p class="lead">Getting started with StarterKit couldn't be easier. Just download and drag it into your plugins folder and away you go. Still stuck? Read on.</p>

## Creating the kit

Creating a kit has never been easier. Simply arrange your own inventory and include any items that you want new players to have. Once you are finished save the kit by typing `/sk save`.

When a player logs in they will get an exact copy of the inventory you just saved, including any armour you were wearing and the item you were holding.

#### Checking what is in the kit

You can check what is in the kit at any time by typing `/sk list`.

Alternatively you can replace your current inventory with the saved StarterKit. This is useful if you just need to change a couple of items in your current kit. You do this by typing `/sk load`.

## Giving the kit

By default StarterKit gives every new player a copy of the kit when they first login to your server. You do not need to configure anything for this to happen.

#### Grant a kit on death

Alternatively you can configure the plugin so it grants the kit every time someone dies. You do this by setting the following in your config.yml.

    provide-kit-on-death: true

## Permissions

<dl>
  <dt>starterkit</dt>
  <dd>Allows access to everything in the plugin (defaults op).</dd>
  <dt>starterkit.list</dt>
  <dd>Allow a player to see what is in the kit (defaults op)</dd>
  <dt>starterkit.load</dt>
  <dd>Allow a player to give themselves the kit (defaults op).</dd>
  <dt>timedmessages.save</dt>
  <dd>Allow a player save a copy of their inventory as the kit (defaults op).</dd>
</dl>
