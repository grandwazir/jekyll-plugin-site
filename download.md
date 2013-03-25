---
layout: page
title: "Download"
description: "Download Hearthstone"
---
{% include JB/setup %}

BanHammer is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version.

BanHammer is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.

Before installing, you need to make sure you are running at least the latest [recommended build](http://dl.bukkit.org/latest-rb/craftbukkit.jar) for Bukkit. Support is only given for problems when using a recommended build. This does not mean that the plugin will not work on other versions of Bukkit, the likelihood is it will, but it is not supported.

<button class="btn-large btn-primary" type="button">Download latest version</button>
<button class="btn-large btn-info" type="button">Download older versions</button>

### Getting the latest version

The best way to install BanHammer is to use the [symbolic link](http://repository.james.richardson.name/symbolic/BanHammer.jar) to the latest version. This link always points to the latest version of BanHammer, so is safe to use in scripts or update plugins. A [feature changelog](https://github.com/grandwazir/BanHammer/wiki/changelog) is also available.

### Getting older versions

Alternatively [older versions](http://repository.james.richardson.name/releases/name/richardson/james/bukkit/ban-hammer/) are available as well, however they are not supported. If you are forced to use an older version for whatever reason, please let me know why by [opening a issue](https://github.com/grandwazir/BanHammer/issues/new) on GitHub.

### Building from source

You can also build BanHammer from the source if you would prefer to do so. This is useful for those who wish to modify BanHammer before using it. Note it is no longer necessary to do this to alter messages in the plugin. Instead you should read the documentation on how to localise the plugin instead. This assumes that you have Maven and git installed on your computer.

    git clone git://github.com/grandwazir/BanHammer.git
    cd BanHammer
    mvn install
