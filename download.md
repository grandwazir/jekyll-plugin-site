---
layout: page
title: "Download"
description: "Download Hearthstone"
version: 1.3.2
group: navigation
---
{% include JB/setup %}

<p class="lead">The latest stable version is <strong>{{page.version}}</strong> and available to download. Before installing make sure to check the change log for any relevant changes.</p>

<ul class="inline">
    <li><a href="http://repository.james.richardson.name/releases/name/richardson/james/bukkit/hearthstone/{{ page.version }}/hearthstone-{{ page.version }}.jar"><button class="btn btn-large btn-primary" type="button">Download</button></a></li>
    <li><a href="/versions/{{page.version}}.html"><button class="btn btn-large btn-info" type="button">What's new</button></a></li>
    <li><a href="https://github.com/grandwazir/Hearthstone/tree/v{{ page.version }}"><button class="btn btn-large btn" type="button">Source</button></a></li>
</ul>

### Getting other versions

<p><strong>Older versions are available to download but are no longer supported.</strong></p>

{% assign pages_list = site.pages %}
{% assign group = 'changelog' %}
<p>
<ul>
{% include JB/pages_list %}
</ul>
</p>
### Building from source

You can also build BanHammer from the source if you would prefer to do so. This is useful for those who wish to modify BanHammer before using it or want to contribute new features. 

Note it is no longer necessary to do this to alter messages in the plugin. Instead you should read the documentation on how to localise the plugin instead. This assumes that you have Maven and git installed on your computer.

    git clone git://github.com/grandwazir/BanHammer.git
    cd BanHammer
    mvn install
