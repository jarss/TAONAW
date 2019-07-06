+++
title = "Org-capture in Files"
author = ["Josh Rollins"]
publishDate = 2019-07-06T00:00:00-04:00
lastmod = 2019-07-06T10:03:58-04:00
tags = ["orgmode"]
draft = false
+++

I've been pretty busy org-mode-ly speaking. There is a lot to say, and as I was writing my post, more ideas occurred to me that behooved me to stop writing and experiment more, which lead to more interesting results, which meant I ran out of time to write about the results. When I finally returned to my post this morning, I realized there's so much to explain, I can't include it all in one go. Here you go, part one of my latest adventure in org mode: org-capture from org files.

<!--more-->


## Why a File as a Capture Template? {#why-a-file-as-a-capture-template}

Why do I need a template based in a file? To understand that, I need to explained some of the work I do as a help desk person in a large organization.

Among other things, my work includes prepping desktop and laptop computers. For the most part, this is done from an image, and all software that is not included is installed remotely from our SMA. However, there are still many cases where the automation fails or does not apply and hands-on deployment is needed. Some scenarios include:

-   BYOD devices, which need to be evaluated and prepared for our environment.
-   Macbooks, which we can't automate yet for political-human reasons.
-   Replacements of old computers, which come in different models and different usage (and abuse) scenarios.

These scenarios are complex but similar: a natural perfect place to use checklists. We're a big company, and many times I find that checklists is half of the job. Communication with clients, managers, purchasing staff, as well as getting the right information from everyone and documenting it, is also a big part of the checklist. The difference between a job that was done with a checklist and one that was done without is so obvious that my checklists have been adopted throughout the team and I was asked several time to guide others (especially new comers) because of "my" organization. I find this humorous, because if you know me, you'd know I've  always been _far_ from organized. It's all org-mode, to which I'm very thankful.

In the past, I've had a long checklist "template" in a header in "setups.org" file which I used to copy-paste into new projects. The idea of having a file as a template for capture occurred to me in the past, but because I've never seen a real-world example and didn't see a clear reference to it in the manual, I dismissed the idea as wishful thinking.


## Why Finding the Answer Took so Long? {#why-finding-the-answer-took-so-long}

I asked about using other org files as templates on Reddit in the past too, but didn't get answers. That's because, I believe, folks didn't understand what I'm asking exactly. And that, in turn, was because I didn't know what I was looking for exactly. After all, if I had a more concrete idea, I'd probably read this in Org manual for what it was:

> template
>
> The template for creating the capture item. If you leave this empty, an appropriate default template will be used. Otherwise this is a string with escape codes, which will be replaced depending on time and context of the capture call. **The string with escapes may be loaded from a template file, using the special syntax ‘(file "template filename")’.** See below for more details.

This little paragraph of text can be found about half a page down [in the manual](https://orgmode.org/manual/Template-elements.html#Template-elements). I read the capture part of the manual probably 20 times or more at this point, and I still feel I wouldn't know I can use a _file_ as a template just from reading it. But why?

There's no clear statement that says you can load a capture from a file; rather, it states that "_the string with escapes_ may be loaded from a file...". To me, this means that I can include my template's definition in a separate file instead of specifying it in my init file. For example, here's a code from my template:

```nil
  ("j" "Journal" entry (file+datetree "~/Documents/Work/Setups.org")
"**** %<%H:%M> about %a \n%?" :tree-type week)
```

So, if for some reason I wouldn't want the _above snippet_ in my init file, I could throw it into a different dedicated file. I didn't bother with it because I'm comfortable with having my capture template _"string with escapes"_ where it is. Further, the manual says "see below for more details," and there aren't any. Not of usage in a file, that is, but what is referred as "string with escapes." There's nothing that tells me I can have my _whole_ template, huge checklist and all, in another file. And, as far as I know, there's no other reference to files as template anywhere in the manual. So I just figured this cannot be done, unless I want to specify a whole checklist in the string above, such as `[ ] checklist item one /n [ ] checklist item two /n` and so forth. I also didn't know how to tell org-capture to reserve the indent for the sub-lists I needed for some of the items on my complex checklists. This looked very cumbersome to do inside the code itself when I already had an org file with the checklist to copy-paste from.

But there was a note somewhere in my journal that said I've seen someone pulling a template from a file. I wrote down that I _know_ it is possible. So two weeks ago I went looking around for this elusive option again, with a somewhat different attitude - I figured that if I find nothing, at least I'll learn other people's work around and could find a way to get what I want.


## How I Finally Found the Solution {#how-i-finally-found-the-solution}

I searched online more aggressively this time, using different queries. I managed to find a couple of questions related to org-mode in emacs.stackexchange.com that were not directly related to my issue, but had the following lines in the code (I cut out the paths as they do not matter here)

```nil
("j" "Journal" entry (file+datetree "...")
(file "..."))
```

And then, I found [this talk](https://emacsnyc.org/assets/documents/how-i-use-org-capture-and-stuff.pdf) by [Jonathan E. Magen](https://twitter.com/yonkeltron). Of particular interest was slide 6. Right there, in front of me, the title was "Template stored in file," and below it, a very simple _example_ that tells org-mode to read the template's content from a file. It was as it is in the manual, but this time, the slide was very specific, tell me: "this is how you tell org to read from a file." It was that simple. So simple that it was right under my nose the whole time, but I kept missing it because there was no clear example or scenario; it was another option that was mentioned briefly as a head nod, and here, someone finally pointed a finger it at for me. So, this was true. Org-mode _can_ read templates from other org files.

I wrote the code as I understood it from the examples I found and added `(file "~/Documents/Personal/journal-tmpl.org")` to the code above instead of that "string with escapes", and got a an error: `org-capture: Capture template ‘j’: Template is not a valid Org entry or tree`.

I saw this in the past, I remembered. Somehow I did got this far before. However, when I saw this error then, it was yet another proof I couldn't use org files as templates. After all, journal-tmpl.org was a good org file that opens otherwise, just not through capture. The conclusion _then_ was, wrongly, that capture can't do it.

Now, through the eyes of someone who's looking at work-arounds, my attitude was different. Org-mode, I knew, (or Emacs for that matter) should open _any_ file if I tell it to, even if an mp4 or a JPEG file. I would see gibberish on my screen, yes, but it would open. It follow then that if I see this error, it means that capture _should_ work, and what I wrote _does_ tell it to open the template from a file, but something in this file specifically is wrong. Suddenly, this error became an encouragement that I am headed in the right direction. The error was telling me, "hey, I want to do this for you, but your file is messed up, sorry." What I should have asked folks should have been "what's wrong with my org template file" and paste the code in Reddit, but I didn't know to ask that. Now, that I finally knew what the real problem was, I was in the right mindset to work it out. And work it out I did.

As it turns out (for reasons ~~I'm still trying to~~ I do understand now), my regular org file started with certain options like `#+TITLE:` and `#+TODO:` with several headers already nested inside of it failed to work. However, if I simplify the file down to the headers I want and the checklist itself, it did work. The reason for that, I know now, is exactly what the manual said all along: "**this is a string with escape codes**, which will be replaced depending on time and context of the capture call..." Org-capture needs specifically org-capture syntax to work with, and the org-mode options at the top of the file specified above are not org-_capture_ syntax; they are _org-mode_ syntax. I need to get them out of the way and feed org-capture org-capture syntax, just like I did in my init. As a matter of fact, as I now know, I can specify the entire syntax (or "strings with escapes") under my first header and it will work just fine. I don't even need to specify it in my init. Yes, this is what the manual said. But no, this is not what it said to _me_. I just couldn't see it.


## What Does it Look Like? {#what-does-it-look-like}

Here's an example of one of my org files templates. Notice how the very first thing is the header itself. Turns out it _must_ be the first thing in org-capture syntax. Then the second line specifies what the template does just like it did in my init. Finally, the checklist itself:

\#+BEGIN\_SRC