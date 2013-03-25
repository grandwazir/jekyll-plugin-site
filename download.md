---
layout: page
title: "Download"
description: "Download Hearthstone"
group: navigation
---
{% include JB/setup %}

Before installing, you need to make sure you are running at least the latest [recommended build](http://dl.bukkit.org/latest-rb/craftbukkit.jar) for Bukkit. Support is only given for problems when using a recommended build. This does not mean that the plugin will not work on other versions of Bukkit, the likelihood is it will, but it is not supported.

### Getting the latest version

The best way to install BanHammer is to use the [symbolic link](http://repository.james.richardson.name/symbolic/BanHammer.jar) to the latest version. This link always points to the latest version of BanHammer, so is safe to use in scripts or update plugins. A [feature changelog](https://github.com/grandwazir/BanHammer/wiki/changelog) is also available.

### Getting older versions
* ewr
{% assign pages_list = site.pages %}
{% assign group = 'changelog' %}
<p>
<ul>
{% include JB/pages_list %}
</ul>
</p>
### Building from source

You can also build BanHammer from the source if you would prefer to do so. This is useful for those who wish to modify BanHammer before using it. Note it is no longer necessary to do this to alter messages in the plugin. Instead you should read the documentation on how to localise the plugin instead. This assumes that you have Maven and git installed on your computer.

    git clone git://github.com/grandwazir/BanHammer.git
    cd BanHammer
    mvn install
