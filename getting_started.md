---
layout: page
title: "Getting started"
description: ""
group: navigation
scrollspy: [Kicking, Banning, Management, Permissions]
---
{% include JB/setup %}

<p class="lead">Getting started with {{ site.title }} couldn't be easier. Just download and drag it into your plugins folder and away you go. Still stuck? Read on.</p>

## Kicking

You can kick players easily using BanHammer. This does exactly the same as the vanilla command except it uses the same notification system for players as if you banned them. For example I am going to kick peppe70 for using a hacked client by typing `/kick peppe70 Using a hacked client`. 

Kick actions are not recorded in the database but are logged to the server log.

## Banning

All bans are recorded in the BanHammer database until you pardon a player or purge their ban history. Times are stored in milliseconds so you may need to do some conversion if you are doing a simple ban list for your website for example.

### Permanently

You can ban players in a variety of interesting ways. Permenant bans are easist to do. In this example I am going to ban tom by typing `/ban tom Being silly`. Anything after their name is included in the ban reason.

### Temporarily

You can also ban players for a specific period of time. This is quite useful if it is someone's first offence or if you use short temporary bans as a warning system. 

In this example I am going to ban alice for 1 day, 16 hours and 30 minutes: `/ban alice t:1d16h30m Being silly`.

Valid time units are: seconds (s), minutes (m), hours (h), days (d) and weeks (w).

### Setting a maximum length for temporary bans

You can now set configurable ban limits to prevent moderators from issuing excessive bans. You give moderators the ability to ban up to a limit by giving them the relevant permission node. For example in the configuration below I have three ban limits:

    ban-limits:
        short: 1d
        medium: 3d
        long: 7d

If I wanted my moderators to only be able to ban for up to 3 days I would give them the following permission node:

    banhammer.ban.medium

You can also use these as a short cut for specifying time when you ban a player. This becomes really useful when you define your limits as sanctions for specific offences and helps to ensure that your players are consistent with the bans they hand out. 

In this example I am going to ban a player for 3 days by using the limit name: `/ban Yul t:medium`.

## Unbanning

To understand this section properly you will need to know the difference between active and inactive bans. Active bans are bans that stop a player from logging into the server. Examples would include temporary bans which have not expired and permanent bans.

Inactive bans are any bans which have expired so they would be past temporary bans.

### Pardoning

Pardoning a player will remove from the database any active bans and allow them to rejoin the server. I felt I was a bit mean to tom so I am going to pardon him now by typing `/pardon tom`.

If you only want your moderators to be able to pardon their own bans, for example to undo mistakes they make when issuing them, you can give them the permission node `banhammer.pardon.own`.

### Purging ban history

Purging a player's ban history will remove all bans from the database (including expired ones) and leave them with a clean record. For example `/bh purge franlink123`.

Because this clears all evidence you should restrict access to this command to your most trusted moderators.

## Management

Banhammer also comes with various extra commands which help in running your server.

### Checking if a player is banned

You can easily check if a player is banned using the `/bh check` command. Depending on the type of ban you will get different information from the command. This is due to the way that bans are cached into memory. For the full details of a ban look through a player's ban history instead. 

### Viewing recent bans

You can also get a list of recent bans made by players on your server - useful for when you want to see what has been going on. This example gets me the last 5 bans made on the server: `/bh recent 5`

### Reviewing a player's ban history

You can get a report of all the bans associated with a particular player easily. The report includes who the date they were banned, who banned them, the reason given and how long for.

To view the ban history of someone else type `/bh history <name>`.

To view your own type `/bh history`.

### Importing and exporting bans

You can now transfer the bans from BanHammer into banned-players.txt for when you want to convert to another plugin or if you find yourself in a situation where you need to go without Bukkit for a while.

#### Importing bans

BanHammer will add all the banned names in banned-players.txt to the database using the default reason specified for your language. By default this is "Imported from banned-players.txt". 

All bans will be imported as permanent bans and as the names are imported they *will be removed* from basic list. This is to stop basic bans interfering with BanHammer. You import the bans by using the following command: `/bh import`.

On occasion some bans may not be imported. The only foreseeable reason for this is that a ban for that player already exists in the database. It will not be replaced however the basic ban will be removed like all the others.

#### Exporting bans

BanHammer can export the names of all the players who have bans to the basic ban list. You can do this by using the following command: `/bh export`.

*All active bans will be converted into permenant bans when exported.*


