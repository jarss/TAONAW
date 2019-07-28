+++
title = "Emacs Windows"
author = ["Josh Rollins"]
publishDate = 2018-10-13T00:00:00-04:00
lastmod = 2019-07-28T07:18:21-04:00
tags = ["emacs"]
draft = false
+++

In his 5th Emacs podcast, [Rakhim](https://emacscast.org/episode%5F5/) discusses the difficulties of windows management in Emacs. I agree with him. Emacs' Windows are a pain. It was probably one of the longest pet peeves I had with the program, and it wasn't until this podcast that I realized that I'm much better off than I used to be.

<!--more-->

I don't use any extension that manages windows (unless you consider Ivy's switch buffer, which he uses too. [Ivy](https://oremacs.com/swiper/) is awesome). My method is based on bits and pieces I picked up. Here are a couple of lines from my settings.org, which I use to make Emacs' windows work better for me.

First, for my ultra-wide screen at home, it helps to enlarge the default frame size. After a few tests, I found this size satisfying:

```emacs-lisp
(setq default-frame-alist '((width . 90) (height . 50) (menu-bar-lines . 6)))
```

Then, we need to turn on the mouse vertical mouse divider. This will allow us to use the mouse to drag and adjust windows in our frame vertically as well. I actually don't use this as much anymore (the reason is coming up) but this is a basic feature that should be on by default, in my opinion:

```emacs-lisp
(window-divider-mode +1)
```

Another basic feature, which I now use everywhere, is the [visual line mode](https://www.gnu.org/software/emacs/manual/html%5Fnode/emacs/Visual-Line-Mode.html). If you write more than you code on Emacs (which is true in my case) this mode just makes sense.

```emacs-lisp
(global-visual-line-mode +1)
```

Those are all good and nice, but here's the biggest tip which I stumbled upon a few months back, from [Ergoemacs](http://ergoemacs.org/emacs/emacs%5Feffective%5Fwindows%5Fmanagement.html): just don't use windows. Use frames. Seriously, it's that simple. There are probably many Emacs experts out there with their windows functions and extensions and what not, but let's not reinvent the wheel here. If there's one thing a GUI is good for is to manage windows (or frames in Emacs). They are very easy to move with the mouse, they snap to each other, easy to resize. Besides, Emacs itself splits the frames to Windows often enough. I find that I use C-0 and C-1 very often to get rid of windows I don't need, and I can have them back quickly by switching back to the buffer with Ivy.

One of the things that used to drive my bananas when I started using Org was how the agenda and its habit to kill my windows setup. One of the most helpful lines in my settings.org is the following:

```emacs-lisp
(setq org-agenda-window-setup (quote other-frame))
```

This saved me from going insane. Since I start up my agenda every time I start up my Emacs, this shortcut also effectively creates the other frame for me to work with until I exit Emacs. From there, I can just use the Agenda frame itself to switch to another buffer if I want to. Agenda is also the only place where I do use windows often - when I tab into one of my headers there. I tab into a task, view it, make changes if I want, save, and C-0 to return to full agenda view. It's so fast it's just my muscle memory now.