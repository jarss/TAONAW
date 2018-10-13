+++
title = "Org Update"
author = ["Josh Rollins"]
lastmod = 2018-10-13T08:49:10-04:00
draft = false
+++

It’s been a while since I blogged about my Org activities. Overall, not a lot has changed from my latest setup. Setting up a new site on GitHub with Hugo kept me fairly busy, away from hacking away at Emacs.

<!--more-->

{{< figure src="/OrgUpdate_1.png" >}}


# Lighter Agenda: No Sub-Tasks {#lighter-agenda-no-sub-tasks}

So, looking at my agenda sometimes less is more. I don’t rush to include every single detail in my agenda anymore, especially at work, becuase it’s redundant. We have a ticketing system that we _have_ to use, and the details are constantly updated by different team members. Because of that, updating technical details for myself again under each heading is not that appealing.

But I do still include notes. Just differently. I start notes with an inactive timestamp and describe where I left off. In other words, exactly what the subtask used to do. So I don’t bother with many sub-tasks anymore. The benefit of one heading is better visual organization. I get a nice Logbook which includes all the time I spent on the project, my notes are more streamlined and easy to find. It also clears the agenda from the clutter of subtasks that sometimes don’t make sense to me anymore because I forgot the big picture already. I also grew more comfortable with changing the header wordings of the task to better reflect what is the big picture I just mentioned. Since I keep short notes of where I left off with the most recent one at the top, it’s easy to see what’s going on.

{{< figure src="/OrgUpdate_2.png" >}}

Sometimes I would even copy-paste from the ticket straight into Org just to remind myself what was done; other times I include references to other people and cases; yet other times, if I have to vent about something, there’s a link to my journal (more on that later).

A fun sidenote: Orgzly, my companion Andoird App, [now has the ability](http://www.orgzly.com/changelog) to start with Org headings collapsed. This means that when I’m on the go, I can open specifically the task on hand and view my notes which I often update just before I get up to do something.


# Keeping Track Of Time Without Going Nuts {#keeping-track-of-time-without-going-nuts}

The Logbook contains estimated times. I almost never get to close a clock on a task once I started, because I almost never get the chance to keep working on one thing before I am called away, or have to do a prerequisite. Other times, I simply forget to start the clock. I estimate how much time I worked on something when I’m back at my desk. Now, since I don’t bother with sub-tasks and separate clocking times for these, it means I need to expend my agenda to view my logs (l in agenda view). This allows me to see the time I spent working on a certain task, even though it is marked as done later, sometimes even days (or weeks) later. This way I know when the whole task was finished, and I can see when (and for how long) I was working on it.

All of that said, most of my tasks don't get logged with a clock. That’s because many of them are simple tasks or just interruptions when I am asked a question or something similar. I should overall though get in the habit of logging tasks in retro-respect to see where my time went.

Another area I stopped worrying as much about are which org files in my archive my headers go to when I refile. This was a mouthful so let me explain.

My system is based on a weekly review. Every week has its own .org file. In the past, filenames used to specify a date range like `08102018_15102018.org`, for example. This caused me complications because I seldom had the chance to summarize and finish my week Sunday and start a clean slate Monday. Many times I wanted to conclude an .org file on a Friday after work or didn’t get the chance to do so until Monday or even Tuesday. Besides, this whole week range thing is redundant because you can always list files by dates anyway (to see when it was last modified).

On the other hand, since I started using my journal again, which is based on weeks rather than months, it made more sense to name the files after the number of the weeks. For instance, this week is w41.org, last week was w40.org, etc. My journal tells me what week I’m on if I ever need to reflect, the file name is very clear and obvious and there’s no room for confusion. My weekly summaries will always be based on their respective `<number>.org`, even if I summarize a month later.

In the past, I refiled events and tasks depending on what week they were to take place. If I was planning a vacation four weeks in advance, for example, I would open a new file for that week and place the event there. This lead to all kinds of problems when I worked on projects that stretched over more than just a weekly period. Let’s say I take a vacation from Friday to Monday of next week. Now what, which file do I choose? At the time, I opted for the completion date. But, this too wasn’t simple. Because certain projects (especially at work) could last even months, or re-surface from the past. That would mean I would have to move them to the appropriate week and think about what “done” really means. One day thinking about it out loud, I just started laughing at myself: “dude,” I said, as I like to refer anyone for some reason, “what are you doing? Org takes care of all of that for you automatically! That’s what’s the Agenda is for!” Who cares if I placed a project in week 20 or week 30, I don’t ever search it that way or know where it comes from anyway, I just see it on the agenda or search for it with the agenda anyway `(C-a s)`. That’s what it’s for. So I stopped caring about that, and events now naturally fall into the week I created them.


# The Journal Revisited {#the-journal-revisited}

I don’t use the journal as much as I used to when I had it earlier this year. I find that I use it capture experiences and emotions more than technical notes. For the later, I now have an org file called “wiki” which I keep organized as it grows further. The journal is good to keep moods and mental “patterns” I can look into on my weekly review. For this, I also use tags. This is a good exercise that allows me to recognize mental “traps” I get into more often than not.

The journal works nicely with my weekly reviews, which are essentially weekly videos I make reading back from my agenda and journal. With time, these became more of a personal “summary of summaries” where I highlight my week tasks and review, usually for a 10-minute segment or so. I keep these in a well-compressed mp4 format on an SD card ([FFMPEG](https://ffmpeg.org/) is awesome for that) and I can easily use one SSD for an entire year and still have additional room. I am now starting to name the videos based on the same weekly theme that I use for my weekly agenda files and journal.