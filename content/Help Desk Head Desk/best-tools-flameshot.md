+++
title = "Best Tools for the job: Flameshot"
author = ["Josh Rollins"]
publishDate = 2019-05-25T00:00:00-04:00
lastmod = 2019-07-28T07:21:04-04:00
tags = ["flameshot", "tools"]
draft = false
+++

Every now and then I discover (or re-discover) a tool in Linux that does exactly what I need it to do. Some examples include ffmpeg, to shrink down my self-recorded webcam journal session while increasing the volume; abcde, to rip a classical music CD to flac and find its exact title and name; youtube-dl, which downloads any video online I need along with aria to speed these downloads, and more.

Today I want to praise a new excellent tool, this time for screenshots: [Flameshot](https://flameshot.js.org/#/).

<!--more-->

{{< figure src="/2019-05-25.jpg" >}}

Flameshot is walking the thin line between being a heavy future-rich screen capture tool with all kinds of features (think  and the minimal screen-capture one that usually comes bundled with your distro. I think it manages to be "just enough" to do exactly what it needs to do. Nothing more, nothing less.

It was easy enough to tie Flameshot to my print-screen button. When summoned, the entire screen becomes dark, and a little message asks me to drag my selection with the mouse. The resulting window, which you can see in the picture above, is a frame that can be adjusted by dragging its sides to crop exactly what you need.

As you stretch the frame, the different tools buttons re-arrange themselves depending on the frame's size. It's a really nice feature which makes the whole application feel smooth and responsive. The wider the frame is, the more tools on the bottom. If the frame is really small, the tools will wrap all around the frame, creating a second row, as needed.

Flameshot comes with all the basic tools you need from an annotation application: arrows, lines, and now (finally) a text tool, which needs to first be activated from the tools configuration menu: (`$ flameshot config`). There's also a text-blur and upload to Imgur tool. Flameshot is minimal: there's no eraser button, for example, because it's not needed. You can only undo and re-do. The color palette is basic, without a large color wheel. You can't rotate and flip images; it trusts you to use a more "heavy guns" editing tool for that, reminding you it's there only for a screenshot.

It's an elegant tool, with an intuitive UI: right-click to choose a color; scroll to make the lines wider or thinner. When you choose the upload to Imgur button, for example, it automatically does that in the background and opens a window for you to either save, copy the freshly-created link to the clipboard or delete the image from the site, which opens another tab in your browser for that. This is the kind of application that makes you feel proud using it.