---
layout: page
title: "Getting started"
description: ""
group: navigation
scrollspy: [Creating messages, Specifing locations, Permissions] 
---
{% include JB/setup %}

<p class="lead">Getting started with TimedMessages couldn't be easier. Just download and drag it into your plugins folder, write your messages into messages.yml and away you go. Still stuck? Read on.</p>

## Creating messages

For our example I am going to create a basic message which provides hints to players every 5 minutes. I want all players to receive the messages and I want to go through the message list in order to make sure people get to read each one. My messages.yml is going to end up looking something like this:

    messages:
      general-hints:
        mode: rotation
        delay: 5m
        messages:
        - Type /help for details on all our commands.
        - Type /home set to set your home.
        - You may not build near spawn.

You can specify times using either seconds, minutes, hours or days. For example if I wanted to do a message every 1 hour, 12 minutes and 30 seconds I would use:

    delay: 1h12m30s

Next I am going to create another message but this time make it random, get broadcasted every every 7 minutes and 47 seconds (specific I know). I still want to keep my general hints so I will add our new message to our existing configuration like so:

    messages:
      general-hints:
        mode: rotation
        delay: 5m
        messages:
        - Type /help for details on all our commands.
        - Type /home set to set your home.
        - You may not build near spawn.
      portal-quotes:
        mode: random
        delay: 7m47s
        messages:
        - What's your favorite thing about space? Mine is space.
        - SPAAACCCCCE!
        - Space space wanna go to space yes please space. Space space. Go to space.

Both will now run at the same time. You may want to vary your delay times slightly to ensure that you do not have lots of messages being broadcast at the same time.

#### Breaking long messages across separate lines

You can also separate long messages across separate lines by using `\n` where you want your message to be split. 

This effectively broadcasts splits your message into two and broadcasts each part to the players. Because of this you need to take this into account when using colour codes.

    messages:
    - "&LIGHT_PURPLEType /help for details on all our commands.\n&LIGHT_PURPLEType /home to go home."

#### Using colours

You can use colours in your message list to make them more varied and interesting to read. You can either use the classic minecraft colours or use a more readable syntax. 

In the following example I am going to change my general hints so they are displayed in light purple.

    messages:
    - "&LIGHT_PURPLEType /help for details on all our commands."
    - "&LIGHT_PURPLEType /home set to set your home."
    - "&LIGHT_PURPLEYou may not build near spawn."

You can mix and match as well and have as many colours as you like in a message. For example I am now going to colour my message so the commands are highlighted in red:

    messages:
    - "&LIGHT_PURPLEType &RED/help&LIGHT_PURPLE for details on all our commands."
    - "&LIGHT_PURPLEType &RED/home&LIGHT_PURPLE set to set your home."
    - "&LIGHT_PURPLEYou may not build near spawn."

## Specifying locations

#### Messages to only people in a certain world

You can also create messages which are only broadcast to players that are in a specific world. This is useful for example if you have world specific rules that you want your players to know about.

In the following example the messages will only be sent to players who are in the world 'nether' with the permission 'group.explorer'

    guest-hints:
      mode: rotation
      delay: 5m
      worlds:
      - nether
      permission: group.default

#### Messages to only people in a certain WorldGuard region

You can also create messages which are only broadcast to players who are in a specified WorldGuard region. This is useful if you want to provide specific rules for a region or if you want to create some atmosphere in different parts of an adventure map.

In the following example the messages will only be sent to players who are in the world 'erabus' and in the 'spawn' or 'starting_area' region.

    guest-hints:
      mode: rotation
      delay: 5m
      worlds:
      - world
      regions:
      - spawn
      - starting_area

*You must specify the world that contains the region otherwise your message will be ignored by the plugin*

## Permissions

<dl>
  <dt>timedmessages</dt>
  <dd>Allows access to everything in the plugin (defaults op).</dd>
  <dt>timedmessages.reload</dt>
  <dd>Allow a player to reload messages.yml from disk (defaults op).</dd>
  <dt>timedmessages.start</dt>
  <dd>Allow a player to start all timed messages (defaults op)</dd>
  <dt>timedmessages.status</dt>
  <dd>Allow a player to check how many timed messages are running (defaults op).</dd>
  <dt>timedmessages.stop</dt>
  <dd>Allow a player to stop all timed messages (defaults op).</dd>
</dl>

#### Using permissions in messages

You can also create messages which are only broadcast to players that have a specific permission. This is useful if you want to create rank specific hints for the players on your server for example. 

In the following example the messages will only be sent to players with the permission 'group.default'

    guest-hints:
      mode: rotation
      delay: 5m
      permission: group.explorer



