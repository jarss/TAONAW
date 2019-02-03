+++
title = "CSS Updates"
author = ["Josh Rollins"]
publishDate = 2019-02-02T00:00:00-05:00
lastmod = 2019-02-03T11:02:47-05:00
tags = ["blogging", "git"]
draft = false
+++

About some CSS Updates... and why I haven't posted in the last two weeks or so.

<!--more-->

Last week I started making some changes for my current Hugo theme, [Hyde](https://themes.gohugo.io/hyde/). This was after I tried out the [Hermit](https://themes.gohugo.io/hermit/) theme and found out the hard way that my site is already "committed" to Hyde. Some of my customizations did not work well in Hermit and required more tweaking, while other parts of the theme didn't look as good to me as they did on first impression.

So instead of changing a theme I started tweaking my current one and got myself lost between the branches of Git. Going in, I knew the changes I'm working on need more time than I could commit to in one sitting. Creating another branch seemed to be the way to go. Things got out of hand when I realized I never started a new branch. I was working on my master branch, which was now out of sync with the one on GitHub.

If you find the above confusing -- that's fine. The problem was that I was in the same boat as you are now, scratching my head and going "huh?" And the more I struggled, the bigger mess I've made.

Thankfully, folks like [Kaushalmodi](https://github.com/kaushalmodi) exist. I don't know where I would be without his help. Not on a Hugo site using Git, that's for sure. I've learned a couple of things from him and the experience this time:

[Magit](https://magit.vc/) can be very helpful to get back on track. That's because it gives you sort of a road map to your project. You cay see the branches and then _go up and down the list using the arrow keys to choose the right location_. For the first time, I saw the benefit of doing that because of the mess I was in.

a whole menu of options is a question mark away, and everything has a hotkey. Magit was something I stayed away from in the past because I'm still scared of Git. After my last experience tough, I should keep using Magit for my work on this site. Magit is more effective and visual, and to me, the later is crucial.

I will babble some more about my tweaks and CSS as I work on things. I will keep updates in this category ([Blogging](https://joshrollinswrites.com/blogging/)) so you can follow up, or ignore them.