---
layout: page
title: "Getting started"
description: ""
group: navigation
scrollspy: [Checking associations, Database, Permissions] 
---
{% include JB/setup %}

<p class="lead">Getting started with Alias couldn't be easier. Just download and drag it into your plugins folder and away you go. Still stuck? Read on.</p>

## Checking associations

Alias matches player names to IP addresses automatically when people join your server. You can check for these associations using the plugin commands. To check if two players are related type `/as check <name>` to see a report of all the names they have used. For example `/as check grandwazir` would check all the names that I had used to login.

If you want to remove an assoication for any reason you can type `/as delete <name> alias`. For example `/as delete grandwazir sergeant_subtle` would delete any link between those two players.

## Database

Alias uses the Bukkit persistance system. This means that you need to configure your bukkit.yml in your server directory with your database settings. Below are example bukkit.yml for MySQL and SQlite3.

### MySQL

This is an example configuration if you wanted to use MySQL. This assumes that it is hosted locally and you want your minecraft database to be minecraft_game. You will need to customise this for your own username and password.

    database:
        username: bukkit
        isolation: SERIALIZABLE
        driver: com.mysql.jdbc.Driver
        password: walrus
        url: jdbc:mysql://localhost:3306/minecraft_game

If you get errors when setting this up make sure that you have given your user enough permissions to administrate the database and the database itself does actually exist.

### SQlite3

This is the default setting when you setup bukkit for the first time. It creates a sqlite database for each plugin that needs in the plugins data folder. For BanHammer this would be at plugins/BanHammer/BanHammer.db. You can change those folders by changing the settings below.

    database:
        username: bukkit
        isolation: SERIALIZABLE
        driver: org.sqlite.JDBC
        password: walrus
        url: jdbc:sqlite:{DIR}{NAME}.db

## Permissions

Each command is assigned its own permission node and all follow the same style. The full list of available permissions, and their defaults, is below. Additionally there is the `hearthstone.teleport.cooldown` node. Players who have this permission will not be able to teleport home unless the cooldown time has expired.

<dl>
  <dt>alias</dt>
  <dd>Allows access to everything in the plugin (defaults op).</dd>
  <dt>alias.check</dt>
  <dd>Allow a player to check the names another player has used (defaults op).</dd>
  <dt>alias.delete</dt>
  <dd>Allow a player to delete associations between players (defaults op).</dd>
</dl>
