+++
title = "My Org Capture Templates - Part 3"
author = ["Josh Rollins"]
publishDate = 2019-02-09T00:00:00-05:00
lastmod = 2019-02-09T07:56:50-05:00
tags = ["orgmode", "emacs"]
draft = false
+++

I took a long unplanned break from writing about my Templates because of the [CSS changes](https://joshrollinswrites.com/blogging/css-updates-1/) I worked on and the complications with Magit. I'm happy to say these are now behind me, and that I gained another grain of confidence using Magit and knowing git, but this is a post for yet another time.

Since the last two templates are rather short, I'm putting them both here together. Here we go:

<!--more-->


## Part 3 - The Tasks Template {#part-3-the-tasks-template}

```emacs-lisp
("t" "ToDo" entry
  (file+headline "~/Documents/Archive/OhSnap!.org" "Tasks")

    "** TODO %? \n SCHEDULED: %^T \n"
)
```

1.  For key-press "t" initiate "ToDo" template, which is  as follows:
2.  Go to `~/Documents/Archive/OhSnap!.org` and create a headline "tasks" there.
3.  Create a second level header, space, add a TODO keyword, space, Place cursor here. New line.
4.  Add the text "`SCHEDULED:`", space, and ask for a complete timestamp (date and time).
5.  New line
6.  Finish

To create a regular "todo" item, I want to have it scheduled right away so it's on my agenda. The word `SCHEDULED:` is what initiates the scheduling in Org-mode. On my agenda, I clearly see scheduled tasks, and I try to schedule everything I want to do. Scheduling a task then is my actual "To Do" trigger, not the TODO keyword.

Of course, things often get shifted around. I constantly reschedule things at work. The benefit of scheduling tasks this way is that tasks I haven't done are highlighted for the next day, so I know to revisit it.  That's all there is to this template, it's rather simple.


## Part 4 - The Event Template {#part-4-the-event-template}

The Event template is probably the first one I created. It changed around quite a bit. This is my go-to personal stuff template which works hand in hand with my journal. Here it is:

```emacs-lisp
("e" "Event" entry
  (file+headline "~/Documents/Archive/OhSnap!.org" "Event")
       "** %? \n %^T \n"
)
```

1.  For key-press "e" initiate "event" template as follows:
2.  Create a headline "Event" in file `"~/Documents/Archive/OhSnap!.org"`...
3.  ...As a second level header. Place cursor here. New line.
4.  Prompt for a complete active timestamp. New line.
5.  Finish

Even simpler than the previous template, this one asks for a complete timestamp (date and time) without a keyword. The active timestamp alone means that this event will show on my agenda, but without the scheduling, it's not highlighted as a task (in my theme, tasks are in green and events are in gray). I use these "concrete" events for meeting with other people, or something that is happening with other people that are important to me.
Events usually have an ending time, even if it's speculative. I go back in later to adjust the timeframe.

I usually follow the event title with a @ sign and link to the location on Google maps if I can. This creates a nice way for me to reflect back later in my journal, which links to these events. For example, an event could be "`<2019-01-13 Sun 19:00-21:00> dinner with Marcy @ The Green Inn`" and The Green Inn would be a link to the location. A quick `C-c o` and the browser opens to the right location, and I can look up directions. The location links also work from Orgzly on my phone, though I'm looking into integrating this whole thing with Google Calendar, which should work better.

After an event took place, I place the cursor on it in my agenda and initiate the journal capture template, as I explained above. Something I started doing lately is to store the link of the journal entry while there `(C-c C-l)`, and then enter a [J] at the end of the title of the event on the agenda, linking to the journal entry. If this works well, I will look into creating a macro or a function to create this journal link automatically. Shouldn't be too hard.