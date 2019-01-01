+++
title = "Hugo - what takes so long?"
author = ["Josh Rollins"]
publishDate = 2018-10-04T00:00:00-04:00
lastmod = 2019-01-01T13:25:01-05:00
draft = false
+++

If you've bseen following me online for the last month or so (especially on reddit) you'd know I've been engaged in shifting away from WordPress and into the world [Hugo](https://gohugo.io/).

<!--more-->

I'd imagine the people of in [r/emacs](https://www.reddit.com/r/emacs/) would raise an eyebrow at the term "world of Hugo." After all, Hugo is a relatively simple program, not a deep rabbit-hole like Emacs. Yet, it's Hugo that got me overwhelemed, not so much Emacs. What? Really?

You see, it has to do with background and expectations. As a non-programmer (as in, someone who never wrote anything a bit more complicated then a few lines of shell script) Emacs was a mountain. Standing at the bottom, I gazed at the cloud shrowing its peek and told myself "well, you gotta take a first step somewhere..." so I did. For me, that was Org-mode. As a matter of fact, at the time, I didn't even know much about Emacs and how deep it can get. All I knew was that Org was cool, and I'm interested in learning more.

After a couple of months, I got a bit more comfortable with Emacs and my level of doing things with it. I am still miles away from the top, and I'm fine with that. I got Emacs to do most of what I want it to do for me at this point, which is writing these posts, my journal entries, and of course my agenda and tasks both at work and at home.

Hugo, on the other hand, was meant to replace WordPress. As a person who used WordPress on and off a couple of years, I expected more or less the same thing. You know, going to my webiste online somewhere, log in with a username and password, navigate the GUI and post stuff, add plugins... As such, I didn't care for a change that much. WordPress was working more or less OK, so why change to something similar and learn things all over again?

I get frequent alerts that my website is down from my webhost, but I got used to shrug these off. I got it as a cheap deal, and for about $6 a month or so hosting, what do you expect? People in the Emacs reddit mentioned they see more spam from my site's URL instead of my posts, but again, with 1 person complaining out of 10 or so, it wasn't a big deal. After all, SSL and https is for professional website that can afford it, and I am just an amatuer-ish blogger. Perhaps the biggest hurdle was Github: I knew people who use Hugo usually use Github to publish their blog, but they were all programmers. Me, I didn't know anything about Github or git. That was for coders, people who write scripts for a living. This is not me. I am not a porgrammer.

To be honest, I'm not sure what changed that perspective. Perhaps it was a random tutorial I saw about Git which made me realize it's not _that_ crazy complicated. Perhaps it was the fact that someone advised me not to link to my website again if I don't have https. Maybe it was just my inner geek, itching for a change, and WordPress was getting too familiar and too boring. Whatever it was, I took the bait, and I started doing all of it at once.

First I watched some Lynda videos about git and read a few posts. Then, I learned more about Hugo. After that, it was [ox-hugo](https://ox-hugo.scripter.co/)'s turn (because I gotta write my posts from inside Emacs), and then it was [Magit](https://magit.vc/) (because I gotta use git from inside Emacs). I think I went through everything in a matter of about a month. I learned too much too fast. But that's how I roll. I don't know why I do that to myself, and I'm not sure how it makes sense to go from "git is for coders" to "ALL THE THINGS," but I do anyway.

Obviously, this attitude has terrible consequences. You learn everything on a very shallow level, which means the first tiny bump in the road sends you launching out of control. You get frustrated and you try again, just to hit another bump. Turns out, if I _learn everything_ I also expect to _know everything_ out of myself, which is of course nonsense. But not everything is futile. Knowing the big picture in advance is not a bad idea. Learning a couple of things at once make you realize how they work together, and helps you develop a mindset that is more skilled at solving specific problems. Later, when you go look at the official documents, certain things already make sense to you even though you haven't seen them before.

Be it as it may, it's not easy. I wouldn't recommend this method to anyone. it's doing damage control instead of learning. However, manuals never made sese to me. In the rare occessions where I do have the patience to read through the introduction, I'd forget what I wanted to do (or how to do it) by the time I get the real stuff. Besides, manuals are usually written by the people who made the program; as such, they are written from the inside, for insiders. Certain terms and syntax make aboslutely no sense to newcomers, who find that they struggle with basic terms that the veterans spit out as if they were born into it. Indeed, if there's one thing that I kept running into when learning Emacs is _not_ to bother with its documentation. As helpful as it is, and as much as everyone loves to say all the help you ever want is C-h v (or a or whatever) away, it was not true for me. It is much, much easier to Google something up and find a blog post (or a YouTube video) that explains it to you in plain English.

Now I'm much further ahead than where I was when I started my Hugo ordeal. I have sucessfully launched a couple of testing websites on and off Github. I have whined, complained, and whined again to anyone who would listen.

So, here we are with Hugo. I use git, and well, the site is on Github. This post was written with ox-hugo. I used Magit, but because there are so many issues I'm running into, I decided to make a decision not to use it for at least another month. It's very hard to hold myself back, for sure. On one hand, since I've done WordPress for so long, I'm aching to go back to my old website where I don't have problems learning how to create a new static page (that doesn't show on the front page of this blog), or how exactly images work with these posts, or how can I automate the long process of saving a post and updating my Hugo website compared to the simple "click to publish"  in WordPress. I'm sure some of you are aching to tell me just how to do some of these things. Don't worry, I'll get back to you.

Oh, and speaking of helpful people: a big thank you to [Kaushal Modi](https://github.com/kaushalmodi), who kept answering my endless questions, who was there through my frustration, anywhere I went. This guy is passionate and compassionate about what he does.