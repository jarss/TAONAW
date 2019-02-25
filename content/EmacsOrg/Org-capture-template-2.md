+++
title = "My Org Capture Templates - Part 2"
author = ["Josh Rollins"]
publishDate = 2019-01-21T00:00:00-05:00
lastmod = 2019-02-23T23:29:26-05:00
tags = ["orgmode", "emacs"]
draft = false
+++

I was happy to see part one of this series generated interest on [Reddit](https://www.reddit.com/r/orgmode/comments/agxe8n/my%5Forgmode%5Ftemplates%5Fpart%5Fone%5Fany%5Finterest%5Fin%5Fmore/). One of the things I love about Org-mode (and Emacs) is this passion among its user and the thirst to learn more from each other. I believe one of the major reasons for that is Org-mode's complexity: there are so many options, it _has_ to be personalized by its users' needs. Org-mode is esaily the most personal tool I've used in a while. Every time I read something Org-mode related somewhere else it's as if I'm invited over for a discussion over a cup of coffee.

<!--more-->

Speaking of personal, today I'm going to discuss my Journal capture template. I hope you enjoy, and as always, comments are welcome on Reddit (follow me using the links above) at least until I integrate a commenting system on this site.


## Part 2 - The Journal template {#part-2-the-journal-template}

First, here's the code:

```emacs-lisp
("j" "Journal" entry
  (file+datetree "~/Documents/Personal/journal.org")

  "**** %U%?%a \n" :tree-type week)
```

1.  For key-press "j" initiate "Journal" template, which as follows:
2.  Go to `~/Documents/Personal/journal.org` and create a [dateree](https://orgmode.org/manual/Template-elements.html#DOCF82) entry there
3.  Create a sub header (level 4) under the day header, under the week header, under the year header (a function of datetree, see link above).
4.  Enter an inactive timestamp, place cursor right after it, place a link to file you were just in.
5.  New line
6.  Make this a _weekly_ datetree (the default is a monthly datetree)
7.  Finish

I prefer a weekly format in my journal over a monthly format. In fact, the week is a "productivity unit" which always made sense to me, and this mindset integrates beautifully into Org-mode. In my archive folder, which you saw in part 1, each week has its own `.org` file (from 1 to 50 something). I don't really need this to make Org-mode work, but there's something assuring in viewing the folder and seeing all the week files.

The reason the timestamp and the link are condensed together (no space) is because I delete most of the timestamp and just leave the hour. This way the cursor is where I need to start erasing the timestamp from. I haven't found a way yet to create an hourly timestamp only and I don't want to forget to put in the hour, so this is the best solution for now. Why is the hour important? First, personal preference from the past, where I would write the time and the location for each entry. Second, this helps me see a couple of entries in the journal that are about the same event (the title is just the name of the event on my agenda) so that if a certain event is developing and I've journaled about it a couple of times, I can easily see the hour of each entry as a separator.

Finally, I use a link to connect me back to `w[##].org` file (week number of the year, as I mentioned above) from which I created the journal entry. In my weekly org files, the incidents or events themselves contain very little details, usually only what is my next action (next thing to do) and a logbook drawer containing the times I worked on a task if I keep track. If I want to discuss something, I create a journal entry for it. I always prefer to leave my thoughts and conclusions in a personal space, separate from the more generic org file which also contains work-related material. The link takes me back to that event or incident, and because the name is the same as the event, I know exactly what I'm referring to.

{{< figure src="/Org-capture-template-2.1.png" >}}

My journal is another feature of Org-mode that fits my workflow effortlessly. The notion that I keep entries around events rather than just a daily or a semi-daily habit works well and behooves me to write my thoughts down often. At the same time, the journal file is kept in a personal folder that is not synced to my work VM. I use TRAMP inside my work VM's capture template, so when I want to capture something in my journal from work, I'm prompted to log into my file server with a password, without saving anything at work.

This privacy barrier may sound cumbersome, but once working, I almost never have to tweak with it. This kind of privacy and separation of my personal files from the cloud help me sleep better at night.