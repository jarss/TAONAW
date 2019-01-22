+++
title = "My Org Capture Templates - Part 2"
author = ["Josh Rollins"]
publishDate = 2019-01-21T00:00:00-05:00
lastmod = 2019-01-21T19:27:54-05:00
draft = false
+++

Looks like the previous post generated interest after I posted it on [Reddit](https://www.reddit.com/r/orgmode/comments/agxe8n/my%5Forgmode%5Ftemplates%5Fpart%5Fone%5Fany%5Finterest%5Fin%5Fmore/). One of the things I love about Org-mode (and Emacs) is this passion amongst its user and the thirst to learn more from each other. I think that one of the major reasons for that is because Org-mode is so complex, it _has_ to be personalized by  its users needs. It's probably nearly impossible know every single thing about Org-mode (and even if you do somehow, it's definitely impossible to follow up on the vast number of packages available) so each person uses what makes sense to them. Org-mode is the most personal tool I've used in a while, and everytime I read something somewhere else, it's as if I'm invited over for a discussion over a cup of coffee.

<!--more-->

Speaking of personal, today I'm going to discuss my Journal capture template. I hope you enjoy, and as always, comments are welcome on Reddit (follow me using the links above) at least until I integrate a commenting system on this site.


## Part 2 - The Journal template {#part-2-the-journal-template}

First, here's the code:

```emacs-lisp
("j" "Journal" entry
  (file+datetree "~/Documents/Personal/journal.org")

  "**** %U%?%a \n" :tree-type week)
```

1.  For key-press "j" initiate "Journal" template, which as as follows:
2.  Go to `~/Documents/Personal/journal.org` and create a [dateree](https://orgmode.org/manual/Template-elements.html#DOCF82) entry there
3.  Create a subtheader (level 4) under the day header, under the week header, under the year header (function of datetree, see link above).
4.  Enter an inactive timestamp,place cursor right after it, place a link to file you were just in.
5.  New line
6.  Make this a _weekly_ datetree (the default is a monthly datetree)
7.  Finish

I prefer a weekly format in my journal over a monthly format. In fact, the week is a "productivity unit" which always made sense to me, and this mindset integrates beatifully into Org-mode. In my archive folder, which you saw in part 1, each week has its own `.org` file (from 1 to 50 something). I don't really need this to make Org-mode work, but there's something mentally very assuring in viewing this folder and seeing a week file associated with the week I'm in.

The reason the timestamp and the link are condenced together (no space) is because I delete most of the timestamp, and just leave the hour. This way the cursor is where I need to start erasing the timestamp from. I haven't found a way yet to create an hourly timestamp only, and I don't want to forget to put in the hour, so this is the best solution for now. Why is the hour important? First, personal prefrence from the past, where I would write the time and the location. Second, this helps me see a couple of entires in the journal that are about the same thing (remember, the title is the link of the event) so that if a certain even is developing and I've journaled about it a couple of times, I can easily see the hour of each entry as a seperator.

Finally, I use a link to connect me back to `w[##].org` file (week number of the year, as I mentioned above) from which I created the journal entry. In my weekly org files, the incidents or events themselves contain very little dtails, usually only what is my next action (next thing to do) and a logbook drawer containing the times I worked on a task if I keep track. If I want to discuss something, I create a journal entry for it. I always prefer to leave my thoughts and conclusions in a personal space seperate from a more generic org file which also contain work related material. The link takes me back to that event or incident, and because the name is the same as the event, I know exactly what I'm referring to.

{{< figure src="/Org-capture-template-2.1.png" >}}