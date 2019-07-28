+++
title = "Why Gcal Failed"
author = ["Josh Rollins"]
publishDate = 2019-04-12T00:00:00-04:00
lastmod = 2019-07-28T07:20:46-04:00
tags = ["orgmode"]
draft = false
+++

I recently tried [Org-Gcal](https://github.com/myuhe/org-gcal.el) a second time just to turn it off again. I was following the (now slightly outdated) [instructions](https://cestlaz.github.io/posts/using-emacs-26-gcal/) on [Mike Zamansky's](https://cestlaz.github.io/) blog and managed to get it working this time, but I found the end result messy and cumbersome. This is mostly because of how I use org and my agenda to quickly get a view of what I need, not really a reflection on the tool itself. It made me understand how different the methodology of Google calendar and Org-mode are.

<!--more-->

First, what exactly is Org-Gcal?
It's an Emacs package that allows Org-mode to sync with Google calendar. Unlike other solutions, Org-Gcal works both ways, so you can create an event on Google calendar and have it show on your Org agenda, and vice versa.

As much as I enjoy Org-mode, it's hard to eliminate Google calendar usage completely for a few reasons. First, Google calendar is a smart and mature product that is integrated into Android. Your Google Assistant, if you use it, can quickly create an event for you complete with location and invitations sent to contacts with a simple voice request. If you let it, the assistant can read what's on your screen and suggest an event, build routines for you, and quickly save important dates and reminders. Further, as an owner of a Google Home, it's nice to ask about your agenda for the day and be reminded of your meetings and tasks. Google Calendar is also a tool that quickly works with others, whether they use an Android device or an iPhone. an invitation via email is usually a seamless affair.

When I attempted Org-Gcal for the first time, I got stuck with my Google account authorization token. I use two different Google accounts on a regular basis, and I ended up requesting access on the wrong account. When I discovered that issue I retraced my steps but got stuck somewhere in the middle. I wasn't able to get to the point of asking for another token from the other account, so I didn't manage to authorize the right account, and I gave up for a bit.

The second time, something similar happened and I got stuck with a specific HTML error that ended up leading to that wrong token. This time, after digging around a bit, I found where Org-Gcal stores that token (in `~/.emacs.d/org-gcal/.org-gcal-token`) and deleted it. This caused Org-Gcal to ask for a new token, which I was now able to provide it with. Since I was following the instructions mentioned above, the setup came with two hooks to cause automatic sync with Google calendar whenever I saved my agenda or org file. I soon started seeing my events live, and then I've experienced a couple of issues.

First, each event started repeating multiple times on the org file dedicated to syncing. This was because, I think, Org-Gcal works both ways and it pasted to events from Emacs to Google Calendar and then again from Google Calendar to Emacs. I noticed some events started repeating even more than twice.

Second, and this is a harder issue to fix, is the lack of details I got from events posted from Org-mode. On my agenda, my events have a title completed with a location and a link to that location completed with a tag for the person I'm with. For example, "Breakfast at Tiffany @ [Tiffany](https://www.nytimes.com/2017/11/11/travel/tiffany-and-co-jewelry-breakfast-audrey-hepburn.html)      ::Tiffany::" conveniently shows me what I'm doing, where, and with who in online line on my agenda. It's crystal clear, and with quick `C-c C-o` I can check the location, get direction, and later even have a journal link connected to it. When converting to Google calendar event, this would result in a long title with the link's syntax square brackets, the location of the event left blank, and useless timestamp information in the details section. Of course, this is how it's intended to works. While I didn't expect miracles, this did make me realize that "translating org" to Google is not just a technical manner. it's a different _style_ entirely. It is just so much easier to squeeze my Pixel2 (which activates the Assistant if I don't feel saying "hey Google") and say "Create a calendar invite, Dinner at Tiffany at Tiffany Diner with Tiffany today at 8 PM". Google Assistant will usually nail this on the first attempt. This is the _Google style_ and this is what it's really good at doing. If I need minor adjustments, like inviting Tiffany or correct the address, that's pretty easy too with the Android's contextual AI and suggestions. In short, things are more inviting this way than the straight sync the package offers.

<br>
![](/why-gcal-failed.png)
<br>
This style difference is a pretty big gap to cross. Org-mode is private, quiet, at-my-computer (usually) planning, where Google assistant is not private (Google can say whatever they want). The Calendar, in a weird way, is also not really personal: it's usually intended to share with a different person. What I have on Org-mode is an event. An event can be personal, often enough summed up in my journal with my impressions. The difference is big enough philosophically speaking that I can create the same occurrence twice: once on my Google Calendar, and once in Org. Sure, this is mostly a waste of time. The difference is not always so black-and-white, but it's there. For now, I am creating my Google events manually after creating the Org-mode events.