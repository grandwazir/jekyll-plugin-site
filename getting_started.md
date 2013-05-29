---
layout: page
title: "Getting started"
description: ""
group: navigation
scrollspy: [Scheduling tasks, Configuring tasks, Permissions] 
---
{% include JB/setup %}

<p class="lead">Getting started with TimedRestore couldn't be easier. Just download and drag it into your plugins folder and away you go. Still stuck? Read on.</p>

## Scheduling tasks

<div class="alert alert-block">
  Restoring regions is a time consuming operation and <strong>will lock</strong> your server while they are ongoing. You may want to consider this in your scheduling when restoring multiple large regions.
</div>

Scheduling tasks in TimedRestore is very flexible and best explained through examples. Internally TimedRestore uses the [cron4j](http://www.sauronsoftware.it/projects/cron4j) library to simulate a unix cron like syntax for scheduling tasks. It is broken into 5 values and seperated by spaces:

<dl>
  <dt>Minutes sub-pattern</dt>
  <dd>During which minutes of the hour should the task been launched? The values range is from 0 to 59.</dd>
  <dt>Hours sub-pattern</dt>
  <dd>During which hours of the day should the task been launched? The values range is from 0 to 23.</dd>
  <dt>Days of month sub-pattern. </dt>
  <dd>During which days of the month should the task been launched? The values range is from 1 to 31. The special value "L" can be used to recognize the last day of month.</dd>
  <dt>Months sub-pattern.</dt>
  <dd>During which months of the year should the task been launched? The values range is from 1 (January) to 12 (December), otherwise this sub-pattern allows the aliases "jan", "feb", "mar", "apr", "may", "jun", "jul", "aug", "sep", "oct", "nov" and "dec".</dd>
  <dt>Days of week sub-pattern</dt>
  <dd>During which days of the week should the task been launched? The values range is from 0 (Sunday) to 6 (Saturday), otherwise this sub-pattern allows the aliases "sun", "mon", "tue", "wed", "thu", "fri" and "sat".</dd>
</dl>

Full documentation is available in the [cron4j manual](http://www.sauronsoftware.it/projects/cron4j/manual.php).

### Example schedules

<dl>
  <dt>0 */1 * * *</dt>
  <dd>To be scheduled once every hour, at the start of the hour.</dd>
  <dt>* * * * *</dt>
  <dd>To be scheduled every minute.</dd>
  <dt>*/5 * * * *</dt>
  <dd>To be scheduled every 5 minutes</dd>
  <dt>0 0 */7 * *</dt>
  <dd>To be scheduled once a week on the first day at midnight.</dd>
  <dt>0 7 L * *</dt>
  <dd>To be scheduled on the last day of each month at 7AM.</dd>
</dl>

## Configuring tasks

For this example I am going to simple create a task which is going to restore a single region. I've already [taken a snapshot](http://wiki.sk89q.com/wiki/WorldEdit/Snapshots) of the world called `original` which I am going to use to restore the region. The region I am going to restore is called `spawn` and I want to do it once every day. My tasks.yml is going to end up looking like this:

    tutorial:
      schedule: "0 0 */1 * *"
      world: world
      snapshot: "original"
      regions:
        - spawn

You can configure as many regions as you like to restore within one task. TimedRestore will restore the regions in the order that you specify. They will all be restored using the same snapshot.

## Permissions

<dl>
  <dt>timedrestore</dt>
  <dd>Allow access to everything in the plugin (defaults op)</dd>
  <dt>timedrestore.reload</dt>
  <dd>Allow a player to reload the plugin's configuration (defaults op) </dd>
  <dt>timedrestore.scheduler</dt>
  <dd>Allow a player to enable or disable scheduled tasks (defaults op)</dd>
  <dt>timedrestore.status</dt>
  <dd>Allow a player to check the status of the scheduler (defaults op)</dd>
</dl>
