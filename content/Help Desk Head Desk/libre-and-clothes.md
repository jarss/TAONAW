+++
title = "Libre and Clothes"
author = ["Josh Rollins"]
publishDate = 2018-08-01T00:00:00-04:00
lastmod = 2019-09-30T20:55:17-04:00
tags = ["orgmode", "emacs"]
draft = false
+++

When I write, I live in Emacs (with the awesome [Solorized](https://github.com/altercation/solarized) theme)
inside Org-Mode.

With time, I found that Org has already made me more effienet writer
and note taker. I write notes in every meeting now, rather it's my
"turn" or not. I write notes as I work, about every solution and every
problem I'm facing. I write first thing in the morning, usually about
org-related thoughts I had as I wake up, over a cup of Sumatra cofee
(little almond milk, one pack of sugar). Quite honestly, Org makes me
_feel_ good, because it's transparent. It's an extensions of my
thoughts, continuing on one long line, uninterrupted, before I stop to
think a second and relfect one what I was thinking (`X-q`).

There's no pretending in Org. No fancy text, fonts, or even
images. Style is only applied to function. It's a delicate balance
which, with the Solirized theme, work extremly well (by the way, the
[story of the man who created Solorized](http://observer.com/2015/02/meet-the-man-behind-solarized-the-most-important-color-scheme-in-computer-history/) is quite interesting and worth
reading). There's also an inviting segue here about Linux, which is
the Org-writing mindset extended into an operating system. But I'm
joyfully digress.

Alright then. But every now on then you need to present stuff, and
this means you need to "dress up" so other people can talk to you and
relate. The "Normals," so to speak, do not understand my Org
dedication and often give me concerned looks when I type away, a
single long line into a blank screen. The purity is empty, the lack of
buttons and distracting elements feels threatening withough GUI
guidance. Fine then, I can do fancy schmancy.

Most Org-folk I've read and listened to talk about LaTex. In my case,
that meant a full installation, which is huge. Over 2GB huge. Not
worth it for concessional usage, especially since I work in Microsoft
environment at work, and most people I'll share with will need .docx
or .ppt format anyway. So for me, [.odt](https://en.wikipedia.org/wiki/OpenDocument) seems like a better answer.

Two things are needed on my Emacs (version 25.2.1) for that:

1.  **Download and install Libre Office**. It comes built in with many
    personal desktop-geared Ubuntu distros, but in my version (Mint) I
    chose to opt out at start. OK, not biggie, full Libre office suite
    is only 100MB, and I can do that. I see myself edit the
    concessional Word file or producing a PDF.

2.  **Add the following** to .emacs to turn on .odt option in the export
    dispatcher:

    `` `(eval-after-load "org"
          '(require 'ox-odt nil t))` ``

Now I can create the .dot file, which I can open in Libre Writer I
just downloaded. Ooof. Hello GUI word proccessing, with weird paper
screen restrictions look. And the white, the white! It burnsss
usss.... But anyway. Overall things look excellent, but if I want to
change fonts, move around images etc, now I can in a more eyecandy
format without leaving Linux. Then again, if I really need to produce
a document, I might as well save my .odt in Writer to a .docx and
remote remote into my work computer, where Mirosoft reigns
supreme. Options. We like having them, yes?

Even another option I was considering is to use [Typora](https://typora.io/), which is a
pretty markdown writer. It comes with [Pandoc](https://en.wikipedia.org/wiki/Pandoc), and can handle Word and
PDF files. Typora does not exactly feel "Linux free" to me and seems
heavily inspired by different "minimalist" Mac word processing apps,
if that's your thing. It probably won't show in your distro's and
require installation from a ppa. I used Typora for a while for
markdown, but we've parted ways now.

I'm curious how this will stand out when I present my notes (since
I've became the unofficial note taker at work, for reasons mentioned
above). But for now, I'm more than happy to take off the fancy clothes
and slide back to my comfortable t-shirt and shorts and write in Org.