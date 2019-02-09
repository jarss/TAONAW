+++
title = "My Org Capture Templates - Part 1"
author = ["Josh Rollins"]
publishDate = 2019-01-17T00:00:00-05:00
lastmod = 2019-02-09T07:52:02-05:00
draft = false
+++

[emsenn](https://mastodon.social/@emsenn) [asked](https://mastodon.social/@emsenn/101387457090836368) Org-mode users for their day-to-day capture templates in the [technology Mastodon](https://mastodon.technology) (which you should join and follow if you haven't yet). I was happy to reply and figured it would be intesting to dig into my capture templates. I started writing this post explaining all of my templates, but then realized I'm starting to edit out details because the post is getting too long. So instead, I'm going to explain each template at a time. Hopefully you find this interesting!

<!--more-->

First, Here's the code for the capture templates I'm going to cover:

```emacs-lisp
("i" "INC" entry (file+headline "~/Documents/Archive/OhSnap!.org" "Incidents")
"** TODO %? \n  %^{Ticket}p %^{PIN}p %^{Computer}p %^{Location}p \n")
("j" "Journal" entry (file+datetree "~/Documents/Personal/journal.org")
"**** %U%?%a \n" :tree-type week)
("t" "ToDo" entry (file+headline "~/Documents/Archive/OhSnap!.org" "Tasks")
"** TODO %? \n SCHEDULED: %^T \n")
("e" "Event" entry (file+headline "~/Documents/Archive/OhSnap!.org" "Event")
"** %? \n %^T \n")
```

Going into details below, I broke the code down so it makes sense to people starting out with Org-mode in hope this would help new-commers like I was not too long ago. If these steps do not sound right (especially for those of you who know Emacs lisp better than me, which is probably 99% of you...) please let me know so I can correct and learn. Thanks!

Ok, here we go.


## Part 1 - The INC Template {#part-1-the-inc-template}

```emacs-lisp
("i" "INC" entry
  (file+headline "~/Documents/Archive/OhSnap!.org" "Incidents")

"** TODO %? \n
  %^{Ticket}p %^{PIN}p %^{Computer}p %^{Location}p \n
")
```

1.  For key-press "i" initiate "INC" template as follows:
2.  Create a headline "Incidents" in file  `~/Documents/Archive/#OhSnap!.org`...
3.  ...As a second level header. Create a TODO keyword, space, place cursor here, new line.
4.  Create Property "Ticket" and ask for input.
5.  Create Property "PIN" and ask for input
6.  Create Property "Computer" and ask for input
7.  Create Property "Location" and ask for input
8.  Space, New line
9.  Finish

I use the above template for ticket creation at work. The file "OhSnap.org" is my "dumping grounds" for everything before I sort it out- usually in front of a desktop. This is useful to me because many times I'm running around using my phone with [Orgzly](http://www.orgzly.com), a very minimal version of Org-mode. I click the add note widget, speak or write out my note in a few words, and save. Later I add details. (By the way, going on a tangent here: you can use Google Assistant on your phone with Orgzly like any other note taking app: "OK Google, make note: buy eggs today" - and bam, you have a quick header in your org file.)

The properties help me keep my work-related issues organized. I have the ticket number for the issue, which is also the fastest way to find it in our ticketing system. Then I have the person's ID, to quickly identify the person's name and email from the directory if I need to. The computer property is the hostname, so I can remote in or know where it is. Location is helpful because we span over different buildings and even parts of the city. In turn, this also makes Column view beneficial if I want to quickly see all the tickets formatted in a nice table. I don't use it often, but it's there.

I don't always have all the properties filled in (though I do try to at least have a ticket and a person's name entered), but I do use this template for anything work related. This is because I have a "work" category property inside the Incident tree, which quickly shows me my work related things on my agenda. This means I can also quickly filter into just work-related stuff if I need to, say, when I show something to my co-workers.

Let me expand on that last at the risk of going into a somewhat unrelated tangent: one of the huge things about Org-mode efficiency in my case is the ability to mix work and personal items in the same place. I have different apps, difference accounts, and different devices, and Org-mode is the first place where I'm comfortable mixing all of them into one agenda because I still have individual org files. This _very_ helpful to keep me organized.

This concludes part 1. As you can see I went into other areas that are not directly related to the template itself. Let me know what you think, and if you want me to expand further! Thanks for reading.