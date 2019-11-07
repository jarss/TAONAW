+++
title = "Emacs & Org From the Beginning: Part 1"
author = ["Josh Rollins"]
publishDate = 2019-10-18T00:00:00-04:00
lastmod = 2019-10-20T07:53:39-04:00
draft = false
+++

intro here

<!--more-->


## How to Read the Keys {#how-to-read-the-keys}

One of the early realizations that I'm looking into something "weird" happened when I started looking into Emacs key "shortcuts[^fn:1]". I came across things like saving (`C-x C-s`) and aborting (`C-g`) and suspected "C" was for control, but got thrown off by execute command (`M-x`). Only after reading more "normal folks" explinations like [Mastering Emacs](https://masteringemacs.org/book) I understood this crazines.

Capital C is indeed the Control key, but capital M turns out to be the [Meta key](https://en.wikipedia.org/wiki/Meta%5Fkey), which is mostly replaced by the Alt key on a regular PC keyboard of the Command key on a Mac. This means that the above command, `C-x C-s`, means "press Control-X and then press S while still pressing the Control key." That last bit is important, because it's different from `C-x s`, for example, which means "press Control-X, let go, and press s", which will invoke a different command altogether.

In the beginning, Emacs weird key combinations was the hardest part to get over. It does take time, but after I've dopted these combos and started using them, they started to make more and more sense. Still there are exceptions. For example, I still don't use Emacs's built in move up (`C-p`) or down (`C-n`) and prefer the arrows instead except special cases[^fn:2].


## Overrated: Emacs Built-in Help System {#overrated-emacs-built-in-help-system}

I'm probably going to get a good amount of pushback for this, but I'm just being honest when I say the built-in help system was little to no use to me back when I started using Emacs.

The Emacs built-in tutorial (`C-h t`) is very through and teaches you the basics one step at a time, but I was never the kind of person who would open a thick textbook and start reading cover to cover[^fn:3]. Emacs also comes with an extensive help system, and these are some of the pupular combos for it:

`C-h a`: apropos-command: "is there such a thing as [search term] and what does it do?"
`C-h k`: describe-key: "what does this key do?"
`C-h f`: describe-function: "what does this function or command do?"
`C-h v`: describe-veriable: "what does this variable does?"

But as you can see, you need to at least have a generic idea of what you're looking for in order to get the help you need.

For instance, if you want to quit a command or escape something, usually by  pressing the "Esc" key anywhere else, you'd be clueless to know it's the `C-g` key combo. You won't know to search for this key combo (`C-h k`) because this is exactly what you're looking for. You won't know what the function is that would cancel a command (is it cancel? escape? quit? and then there are variants of those, like quit-proccess, quit-window...) called, because you have no idea what it is in "Emacs speak". It's not a variable (that much I knew when I started) so `C-h v` is usless here, and even the friendlier "search all" `C-h a` seems to fall short here since you'll be presented with a large list of anything that contains the word "quit" (if that's what you're looking for) in differnent functions and packages, if you have any installed. In short, you'd be lost.

Having to look up new key-combos like that when I started every single time I wanted to finish a paragraph was terrible, and I believe it's the wrong (and terribly boring) way to learn Emacs.

So, even with all its good intentions, I didn't use Emacs help system as much as many folks told me I should. Instead I turned to Google and many different forums where folks as confused as me posted these questions. The book I mentioned above also helped a great deal, since Mickey Petersen explains things to you as another _normal_ computer user. I will get back to this point again and again.


## This is Where you Should Start {#this-is-where-you-should-start}

OK, so I explained how to read Emacs' weird key systems and then encouraged you _not_ to  use the built-in help system. Great. Now what?

Since Emacs' biggest issue when you start are the keys, we want to do something about making the environment more familiar. Again, many veteran Emacsers would yell at me here, and I myself cringe at the thought of using CUA mode these days, but you got to start somewhere familar, and this is a good place.

CUA mode, AKA Common User Access mode, is what you're probably familiar with in most Word proccessing programs. Control+C to copy, Control+X to cut, Control+v to paste, etc. To turn this on, Click the "Options" menu at the top of the Emacs window (yes, with your mouse...) and check the box next to "Use CUA Keys". Then from the same menu all the way at the botton, click "Save Options" if you want this to be turned on every time you start Emacs. Congradualtions, you've just saved yourself the mental pain of looking for "paste" in Emacs for 20 minutes and then realizing it doesn't exist (in Emacs speak, paste is "yank").

Now that you've made Emacs a bit "stupider" to fit your needs (as you become better at Emacs, you'll learn quickly why CUA mode is not that good later on), it's time to tweak yourself a bit for Emacs.

Look down at your keyboard, at that Caps key. See it? Do you remember when's the last time you've used it? Did you ever wonder why such a useless key is so big and pronouced? Well then, congradulations. Time to kiss it goodbye. From now on, your Caps key will function is a secondary control key.

Emacs uses the control key a lot. And I mean, a _lot_. Today's modern keyboards are simply not meant for frequent control presses (remember, Emacs was invented back when a Meta key was a thing and "paste" did not exist in the computer user's lexicon). Emacs users developed a terrible condition called "Emacs Pinky." And yes, I can tell you from personal experience (I have smaller hands), it's a real thing. Many Emacs guros wrote pages on avoiding the Emacs pinky ([here's a good one](http://ergoemacs.org/emacs/emacs%5Fpinky.html)), but using your Caps key as control is probably one of the eaisest.

This is easy to do in Linux and Macs, but somewhat tricker in Windows. The best tool I found for that is [Ctrl2Cap](https://docs.microsoft.com/en-us/sysinternals/downloads/ctrl2cap). Take care of this now. Don't be that person who knows better. Don't be me. Just do it. Emacs has very smart ways of turning any words or letter to upper-cases in ways that will blow your socks off later.


## Footnotes {#footnotes}

[^fn:1]: Back then, pressing keys instead of using the mouse was refered to as "shortcuts." I knew Emacs works directly from the keyboard, but I didn't know how to refer to this odd practice which is second nature now.
[^fn:2]: Sometimes pressing the up arrow key is taken by another, more familiar function. When I ran shell inside emacs (I don't do that much anymore), pressing `C-p` became important because it would take the cursor and move it inside the text window, _not_ repeat the last command, which is what the up arrow key meant.
[^fn:3]: This was never the way for me to learn anything, particularly computer stuff. As a matter of fact, this is one of a few big reasons I did not do well in college in computer programming calsses and decided to put computers behind me for later in life. :EXPORT\_HUGO\_SECTION: Help Desk Head Desk :EXPORT\_FILE\_NAME: you-are-on-sale :EXPORT\_HUGO\_PUBLISHDATE: 2019-10-18: The fan noise that came from my Windows machine finally got on my nerves, so I turned off my PC. I turned it on the next day, not thinking much about anything, my coffee at hand. As soon as I logged in I was greated with all kinds of windows opening on me, intruding on my space, notifying me on updates, of new games sales, of emails... "click me! No! Click me!!" I heard them yell in the back of my head. I put my coffee down and shut my Windows PC off again, shaking my head.