+++
title = "Agenda, and the Benfit of Having Multiple Files"
author = ["Josh Rollins"]
publishDate = 2018-08-02T00:00:00-04:00
lastmod = 2019-03-12T07:48:26-04:00
tags = ["orgmode"]
draft = false
+++

I used to write all my tasks, personal and work, into one tasks.org
file.

On Sunday night, this was good. I had 5 tasks on my list, and I was
ready to start my work week. But it didn't take long (two days
actually) for tasks.org to become monster.org. It didn't happen
because of the number of tasks, which I kept (more or less) under
control. It happened because of the size of the projects I was
working on. Setting up computers, encryption, and even elementary
personal stuff like paying my bills; each task naturally grew to
sub-tasks, and those in turn had their own notes and lists.

My initial solution to that was to create a "Details" heading for
the projects. It contained time rangers I worked on a project
(entered manually), and links to other sources I needed. This kept
extra information out of the way when I didn't need it. This caused
two issues. First, I now had "Details" showing on my agenda, since
my time-range was directly under that header. Second, things
quickly got out of control on my Android phone with Orgzly. That's
because Orgzly does not fold seondary headings. I had to deal with
walls of texts which I had to scroll through before I got to the most
recent ToDo items.

As I was scratching my head at this, work and life continued. My
tasks list grew each day - No, each couple of hours. Interruptions
kept coming in, obscure urgent new projects oppoped up while older
ones from previous weeks resurfaced. My list was quickly overtaken
by work stuff, while personal projects remained in the background,
often pushed down the list and out of view.

Realizing that I can't handle just viewing my tasks.org on my phone
anymore (toward the end of the week, I could barely do it even in
Emacs) I started using the tool I should have used more from the
beginning: The agenda.


## The Agenda {#the-agenda}

The agenda view changed everything. Opened from everywhere with a
quick key combo, it enabled me to see everything that I need to
do. This is thanks to one thing that survived through the mess was
my method of _scheduling_ assignments I intended to work on that
day or in the next couple of hours. I picked this habit from one of
the old Org tutorials floating around, which I cannot find right
now. Scheduling means I still had a wall of ToDo items in
tasks.org, but I only scheduled up to 5 things I intended to work
on. I am only human, after all. Scheduling showed me what I wanted
to do, and ToDo keywords showed me assignments that I haven't yet
scheduled, but need to at some point. I could view both
comfortably from the agenda view with `C-c a n`.

This proved to be effective not only in Emacs, but also in Orgzly,
on my phone. Thanks to the "Scheduled" search, I now also have a
widget on my homescreen, an affective todo list. There's even a
check button to check off Items on this widget, which marks them as
"done." Orgzly also does a good job at creating customized
searches, so that I can specifically see what is scheduled for
today vs what is scheduled for the next 3 days, or week. I can have
another filter showing me my unscheduled ToDos as well, in case I
want to start working on them. What a wonderful thing.

Working with the agenda, I realized I'm faster than before. At
work, the first thing I do after I launch Emacs is to get into
agenda view. From there, it is much faster to "tab in" to whatever
task I need. This replaced my need for `C-x C-r`, recentf,
since now I was not only in the file I need, but also in the
_section_ I need. Even better: `C-x n s` can be used then to "zoom
in" to the task at hand, blocking out the long list of other items.

In agenda, I was also able to quickly see tags and categories, edit
properties, and most importantly, quickly schedule ToDos. As the
agenda became my bread and butter, another small issue surfaced:
the category property. Since I still used one file, I used the category
property to differentiate between personal and work tasks. On the
agenda, each schedule task was placed in a "Tasks" category by
default, since that was the file I was using. Even when I did
assigned a category from the agenda, I still had to do so for a child
header (I thought these are supposed to be inharied, but this
didn't seem to work). This may sound like aesthetics, but being
able to filter out all personal/work tasks can be very handy.

I was also thinking of my issue of having multiple values for one
property. This was a problem I was trying to solve for the last
several weeks. As an example, consider a task of setting up several
computers, where extra information such as serial numbers and
models is needed. Up to that point, I had a header nested inside my
task.org file, like "set up 4 computers." I used the custom
property `:Serials:` followed by the serial numbers for set-up
tasks: `:Serials: 1111 2222 3333 4444` etc. This didnt' work well,
since Org considered the _whole_ thing, including spaces, as the
value of the property "Serials." I could still search, using Swiper
(Ivy is one of the first things I install), for the serial as text,
but anything that has to do with properties as functions did not
work. I asked about this in reddit and in IRC several times, but
could not find a satisfactory solution to breaking down properties
that way. Someone, at one point, offered a rather complicated
function -- but I kept feeling this was a too common of an issue to
be overlooked like that. Something more fundemental was off in the
way I was working with Org, but I didn't know what it was. So I
decided to "go back" and reflect again on how Org was meant to work
originally.

After re-reading some sections of the manual and watching [Carsten
Dominik's](https://www.youtube.com/watch?v%3DoJTwQvgfgMM#t%3D1m20s) presentation back from 2008, I was reminded of Org-modes
original built-in tools. In the lecture, Carsten emphasized [Column
View](https://orgmode.org/manual/Column-view.html) in Org. It is something I saw in passing previously, but now
that I was having a mess on my hands with properties, Column View
glowed in a welcoming aura. A quick and efficient way to have a
table of the computers' serial numbers (or users, or model...)
right next to the header, in a comfortable layout? I needed this. I
could set columns per header, if I wanted to, which meant more
fiddling around with the specific laptop-setup task in my old
method. Or... I could just have a set-up dedicated org file which will
already have the column view for laptop-set up built in with the
properties... Wait a minute.


## Using Multiple Org Files {#using-multiple-org-files}

That was it. Everything I learned to this point came together in a
torrent of thoughts. The solution to the properties problem was to
have dedicated org files for each big project. After all, that's
_exactly_ what the agenda was made for: to be used as the "glue"
between them. This was why I was supposed to use agenda in the
first place! As long as I had a task scheduled, it didn't matter
what file it was in. All I need to do is to tab in, just like I did
with tasks.org. The idea of having a list of tasks in one file was
so ingrained in my head from all the apps I used in the past, I was
blind to see what was under my nose.

With the realization of needing to break tasks back to different
files came the realization that I am probably squeezing too much
data into one org file. After all, setting up laptops as a task is
a _project_ in itself. It should include a heading for _each_
laptop, along with a checklist of steps I do for each, with a log
describing different issues I am having in the process. From the
agenda, this looks just like another project I do during the week.
it fits inside the tasks list and on my phone just the
same.

I was in for another pleasent surprise: In my agenda, since now I
seperated the setups to a different file, my category problem
suddenly disappeared as well. All my laptop setups were shown as
"setups" as a category, because this is the file they are
in. Wow. So this is what happens when you stop fighting something and
start using it the way it was meant to be used.


## Next Steps {#next-steps}

I've been using the system above for almost a week now (this post has
been a week in the making). Here are some ideas about what's next.

1.  ~~adoptive capture template for tickets~~ this was done this morning!  I
    now have a capture template that automatically prompts me for the
    properties needed for each ticket I need to work on. It is then filed
    as a ToDo task in my weekly "tasks.org"
2.  Should Figure out what to use tags for: work in progress. While categories
    have their place, tags are more fluid. For now, it seems like I'm
    gravitating toward creating "mind keywords" of certain topics or
    terms that I'm familiar with. These, in turn, should be good for
    searches since I think in these terms when I'm looking for
    something. For example, a task flagged with my boss's name tells me
    this is a task he's viewing actively, or a "wiki" tag tells me
    there's some good info stored in the notes of the tasks that I
    should probably store for later.
3.  Learn to trust the system. It's _hard_ to let myself create tasks
    in different files. I still need my weekly "mind-dump" of a place
    where I throw in quick captures and tasks that are not big enough
    for their own file, but I should stop thinking of it as my weekly
    list of things I'm doing, since it's misleading. The agenda is what
    reflects that now.