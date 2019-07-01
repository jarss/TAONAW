+++
title = "Capture in Files"
author = ["Josh Rollins"]
publishDate = 2019-06-22T00:00:00-04:00
lastmod = 2019-06-24T09:05:26-04:00
draft = true
+++

<!--more-->

intro:

-   Files as templates

Why do I need a template based in a file? To understand that, I need to explained some of the work I do as a help desk person in a large organization.

Among other things, my work includes prepping desktop and laptop computers for clients. For the most part, this is done from a clone or an image, and all software is installed remotely. But there are still many cases where the automatic system fails and we have to do hands-on deployment. Some scenarios include:

-   BYOD device, which was not imaged with our image
-   Prepping Macs (part of my role is to automate these)
-   Replacement of old computer (which have data stored locally, and require a cumborsome DLP proccess)

And there are more, like Malware removal proccesses, adding a new printer to our server, etc. Because we're a big company, many times I find that the technical checklist is half of the proccess. Communication with the clients, managers, and the purchasing people (and getting the right information from everyone as well as documenting it) is a big part of the checklist.

I've had a long checklist handy in a "setups.org" file which I used to copy-paste into new projects. The idea of having a file as a template for capture occured to me in the past, but because I've never seen a real-world example and didn't see a clear reference to it in the manual made me dismiss this idea as figure of my imagination.

At one point I asked about this on Reddit but didn't get answers. The question was mostly left ananswered, I believe, because folks didn't understand what I'm asking exactly. That's because I didn't know what I was looking for. After all, if I had a more concrete idea, I'd probably find this in Org manual:

> template
>
> The template for creating the capture item. If you leave this empty, an appropriate default template will be used. Otherwise this is a string with escape codes, which will be replaced depending on time and context of the capture call. The string with escapes may be loaded from a template file, using the special syntax ‘(file "template filename")’. See below for more details.

This little paragraph of text can be found about half a page down [in the manual](https://orgmode.org/manual/Template-elements.html#Template-elements). I read the capture part of the manual probably 20 times or more at this point, and I still feel I wouldn't know I can use a _file_ as a template reading it.

There's no clear statement that says you can load a capture from a file; rather, it states that "_the string with escapes_ may be loaded from a file...". To me, this means that if I want to include my template's definition in a file I can do so instead of using my init. For example, here's a code from my template:

```nil
  ("j" "Journal" entry (file+datetree "~/Documents/Work/Setups.org")
"**** %<%H:%M> about %a \n%?" :tree-type week)
```

So if for some reason I wouldn't want the _above snippet_ in my init (or in my case, my org file), I could throw it into a different file. I didn't bother with it because I'm comfortable with having my capture template _"string with escapes"_ where it is. Further, the manual says "see below for more details," and indeed, there are details: of properties which are part of the "string with escapes." There's nothing that tells me I can have my whole template, huge checklists and all, in another file. And, as far as I know, there's no other reference to files as template anywhere in the manual. So I just figured I'm imagining things and moved on.

I would have kept going in circles and dismiss this idea as non-existant again, if it wasn't for a note somewhere in my journal that I've seen someone pulling a template from a file. I _knew_ it is possible, and because of this I went looking for a solution to a specific problem. I couldn't find that example in my journal then nor can I now (which is why I didn't post it), but I searched online more agressively this time, using different queries. I managed to find a couple of questions related to org-mode in emacs.stackexchange.com that were not directly related to my issue, but had the following lines in the code (I cut out the paths as the do not matter here)

```nil
("j" "Journal" entry (file+datetree "...")
(file "..."))
```

And then, I found [this talk](https://emacsnyc.org/assets/documents/how-i-use-org-capture-and-stuff.pdf) by [Jonathan E. Magen](https://twitter.com/yonkeltron). Of particular interest was slide 6. Right there, in front of me, the title was "Template stored in file," and below it, a very simple _example_ that tells org-mode to read the template's content from a file. So, it is true. Org-mode _can_ read templates from other org files, even though the manual (so far) has failed to tell me that 20 times or so.

I wrote the code as I understood it from the examples I found and added `(file "~/Documents/Personal/journal-tmpl.org")` instead of that "string with escapes", and got a an error: "org-capture: Capture template ‘j’: Template is not a valid Org entry or tree".

In the past when I saw this error at a certain point, it was another proof I can't use org files as templates. After all, journal-tmpl.org was a good org file that opens otherwise, just not through capture. The conclusion then was, capture can't do it. But now I was convinced the concept of a template-file exists, and I looked at the error differently: Org-mode (or emacs for that matter) should open _any_ file if I tell it to, even if it's mp4 or a doc. I would see gybrish on my screen, but it would open. It follow then that if I see this error it means it is meant to work, but not in this particular case. This error now became an encouragement that I am headed in the right direction.

The error was not the conspet, or even the syntax of my capture template. The problem was my org file. What I should have asked was "what's wrong with my org template file" and paste the code, but I didn't know to ask that. I didn't know this was possible to ask it. Now, that I finally knew what the real error was, I was in the right mindset to work it out. And work it out I did.

As it turns out (for reasons I'm still trying to understand), ny regular or file that starts with certain options like `#+TITLE:` and `#+TODO:` with several headers already nested inside of it fails to work. However, if I simplify the file down to the headers I want and the checklist itself, it did work. Right in front of me, I had a long checklist I always wanted inside org capture:

then:

-   Now I need 2 letter template?
-   Why manual no good again

now need:

-   properties includes
-   not bothering with manual