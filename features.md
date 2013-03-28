---
layout: page
title: "Features"
description: ""
group: navigation
scrollspy: [Message lists, Location specific, Permission support]
---
{% include JB/setup %}

<p class="lead">Create messages which occur periodically at a time of your choosing. Timing can be specified a mixture of days, hours, minutes or seconds. This allows you to create messages which are only broadcast when you want them to.</p>

## Message lists

Each message has a list attached of possible phrases it could broadcast to players when asked. This allows you to have one message broadcasting many different phrases. Each message can have two modes, rotation or random which specifies how you want the message to behave.

#### Rotating messages

Rotating messages work through the list in order. The first time the timer expires it will broadcast the message at the top of the list, the next the second one and so on. When it reaches the end it starts at the top again.

#### Random messages

When a random message is asked to broadcast it chooses one of the messages from the list at random.

## Location specific

TimedMessages supports specifying your messages so that only players in a certain location will hear them. This is currently supported on two levels.

#### World specific messages

You can choose your messages to only be heard by players in certain worlds or across all your worlds. This can be useful for things like world rules or general server rules.

#### Region specific messages

You can also choose for messages to only be given to people in a certain WorldGuard region. This allows you to provide context sensitive messages for particular regions in your world. We use them on our server to create atmosphere messages for our adventure dungeons.

## Permission support

Additionally you can configure your messages so only players which certain permissions will receive them. This is very useful for targeting your messages at groups of players, such as guests, to give them additional help.

