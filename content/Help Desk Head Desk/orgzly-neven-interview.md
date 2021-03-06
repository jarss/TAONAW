+++
title = "Orgzly: An Interview"
author = ["Josh Rollins"]
publishDate = 2019-06-07T00:00:00-04:00
lastmod = 2019-10-03T06:58:17-04:00
tags = ["orgmode", "tools"]
draft = false
+++

I've talked about [Orgzly](http://www.orgzly.com/) several times on this blog, but I haven't dedicated a full post to it yet until now. Instead of describing my workflow again or just praising Orgzly's usefulness in a repeated manner, I thought it would be interesting to reach out to its creator and ask a couple of questions instead. To my delight, he was happy to reply! I'm happy to present my first interview on this blog.

<!--more-->

First, for those of you who are not familiar with Orgzly, a quick intro. Those of you who are, just skip the next paragraph.

Org-mode, as awesome as it is, has one glaring problem which keeps many users from using it all day: it's inability to be mobile. Org-mode is built into Emacs, which in turn is built into Linux (or, with some alternations, into macOS). This means you can't take Org-mode with you on the go. For Android, Org-mode's official tool was [MobileOrg](https://github.com/matburt/mobileorg-android), which is no longer active. While workarounds exist, it's probably safe to say the only Android tool worth your time out there is Orgzly. As I mentioned several times before, it was actually Orgzly that got me into Org-mode and then into Emacs. I use Orgzly every day, all day. It is easily the main reason why Org-mode is even an option for me at work: it is what allows me to access my agenda and todo's with all their details on my running-around routine.

With this out of the way, let's turn to the creator of Orgzly: Neven.

Neven prefers not to talk too much about himself but agreed to tell us he's a software engineer working for a company in the US. His experience comes mostly from working with Java. Below, my questions in italic, his answers in the texts under.

_Orgzly seem to answer a very specific niche: Android Org-mode users on the go. Are these the people you're trying to reach?_

The project was born from the need to have org files on my Android phone. MobileOrg was the only app available I could find, but I had a hard time setting it up and getting used to it. Initially, I started writing a web app, in Rails. But too many little things bothered me, it felt hackish and clunky. So eventually, I started playing with Android. I never wrote anything for it before, but since I use it, it seemed like the best alternative. Orgzly literally grew from the "hello, world" app, while I was learning to program for Android. So my first goal was to have an easy-to-use Android app for org files, yet powerful enough to be able to do the majority of work in it.

Having Org-mode users as the app's early adopters was very useful, as they know what they want and how they want it. It was also a motivator for me. But I had non-Org-mode users in mind right from the start. Even with huge competition in the field of task apps, I thought it would be useful for the quality of Orgzly to make it tempting for those users as well and see what suggestions they'd have on improving it. It's easy to get stuck writing for the very specific type of mostly tech-savvy users and end up with a hard-to-use app. Orgzly was made to support more formats to store the notebooks in - not just org files - from day one.

_As an Org-mode user, how does Orgzly help you with your personal workflow?_

When I got a job years ago, I needed a way to track all the projects and the little tasks I was working on. I never had a real need for that before, so I started using a simple spreadsheet (I used OpenOffice, which was popular at the time).  Occasionally I gave random software or productivity apps a go, looking to improve my system. Eventually I tried Org-mode (after about a year or so) and never looked back. At the time I was a Vim user, but because Org-mode became such an important part of my workflow, I eventually switched to Emacs. It was way more convenient for me, as I became a heavy Org-mode user.

Nowadays I use Org-mode for pretty much everything: Orgzly-related work, day job-related projects, and personal tasks. Anything from new Orgzly repository type support to buying fruits at the store, really.

_Can we expand on that? We Org-mode folk love hearing about other people's methods and hacks..._

I don't do anything too crazy. I used to store the majority of my tasks in three big org files (Orgzly.org, work.org, and personal.org) with different states, tags and properties. Search speed became an issue for me in Org-mode, mainly when filtering by planning times and properties, so now I have two files per area: one for active tasks and one for some day/maybe (a la GTD) stuff. I also have a separate Inbox.org file (again taken from GTD, the method I'm trying to follow as much as I can in Org-mode). This seems to be working particularly well with a mobile app such as Orgzly, since you don't want to spend too much time thinking where and how to store some idea or a task when you're on the go.

_What do you hope Org-mode users get out of Orgzly? What about the non-Org users you mentioned?_

For Org-mode users, my goal is that they feel as comfortable and efficient in Orgzly as much as they do in Org-mode. This is obviously a huge goal and the app has still a long way to go for that to happen, but I think it's a useful goal to have since it helps to improve the quality of the app.

As for Non-Org-mode users, they should be able to use the app easily, without the underlying format of notebooks or any Org-mode-specific features getting in their way. They shouldn't need to know what Org-mode even is, but if they learn about it through Orgzly, great.

_What makes Orgzly different than the other task and productivity apps out there then?_

Considering the number of apps out there, it's pretty hard to stand out. Having notebooks in plain text and being able to sync them anywhere would be the main advantage I guess. Syncing is currently done through Orgzly's Directory repository, and Dropbox is still the only way to do that directly.

_Do you get any help developing the app? How much work and time do you put into it? Orgzly doesn't have any ads or any other form of contribution, is that something you are looking into?_

I try to work on Orgzly as much as I can, but I don't do it nearly as much as I'd like to. It's not always easy to find the time between my day job and personal projects. There are periods when I have a lot of free time to work on Orgzly, and there are times when I can barely get on top of my emails. Contribution on GitHub is great, especially small and tested pull requests which I can just merge immediately. There have been some larger projects done too. For example, there is a Git repository support currently in progress which I'm barely involved in, which is great. As for Orgzly monetization, my plan is to implement in-app purchases for the version in Google Play. (_note: Orgzly is available in Google Play store and in the free [F-Droid store](https://www.f-droid.org/) - J.R._) I never considered adding ads (I do not like seeing them in apps). I considered accepting donations, but I prefer trying to have a long-term steady income instead, eventually.

_Neven, thank you so much for agreeing to do this FAQ. Please keep up the excellent work!!_

Thank you!
-Neven


## A Couple of Concluding Remarks {#a-couple-of-concluding-remarks}

I have a few additional thoughts to share after heading from Neven:

First, It was intriguing to hear the Neven's opinion about non-tech and non-Org users. In a way, he looks up to them as inspiration: the more they can use the app, the better the app is. This makes me think about the Org-mode and Emacs manual. It is very detailed, very informative, yet in the beginning it served me as a last resort only. That's because it feels the Emacs was written from the "inside" by people who understand programming and Linux. Because of that I often couldn't find what I was looking for and ended up Googling basic questions. I didn't know what to ask. Today, when I have a better understanding of what I need, I can use the manual more often. But Orgzly was not created this way. I started using Orgzly before I started using Emacs, and one of the reasons for that was because it made sense from the start. The manual was intuitive, made sense, and _small_. I think Neven is on to something very important here.

Second, I find that a couple of hacks really help me work around Orgzly's limitation. It is, after all, just an "Org-mode" light. It might be useful to highlight some of these here again:

Neven said that in a mobile app, you don't want to think much about what information you capture and where to put it. This is something I very much agree with. I have Orgzly's agenda widget on my screen for my tasks for the day, which a quick tap away from projects I'm working on at any given moment (since I go back to my office to refile and organized between tasks). The widget has a plus sign at the corner which quickly launches a new note in my default "inbox" org file. When I create a note, I often don't type. Instead, I tap the microphone on my Android's keyboard and dictate what I need. Even if the translation is 100%, it's close enough that I know what I wanted to say when I'm in front of a computer. This is so quick it's often _better_ than using org-capture. When the note saves, it is automatically scheduled as a todo item on my agenda to the same day (an option in Orgzly) so that it's in front of my face on the agenda and I can refile and schedule it as needed and don't forget about it.

The second thing is [Syncthing](https://syncthing.net/). Neven mentioned Dropbox, which works fine, but for the more privacy and space-aware folks out there, Syncthing is a godsend. I [wrote about it in length before](https://joshrollinswrites.com/help-desk-head-desk/raspberry%5Fpi%5Forg%5Fhub/), so I won't get into my system here. If Orgzly is what allows me to work with Org-mode everywhere, Syncthing is the glue that makes it possible. An update on my phone from the field will show up in a second on my VM at work and my Linux box at home, and vice versa.