+++
title = "CSS Updates"
author = ["Josh Rollins"]
publishDate = 2019-02-02T00:00:00-05:00
lastmod = 2019-02-06T19:48:28-05:00
tags = ["blogging", "git"]
draft = false
+++

About some CSS Updates... and why I haven't posted in the last two weeks or so. (Changes are now complete!)

<!--more-->

Last week I started making some changes for my current Hugo theme, [Hyde](https://themes.gohugo.io/hyde/). This was after I tried out the [Hermit](https://themes.gohugo.io/hermit/) theme and found out the hard way that my site is already "committed" to Hyde. Some of my customizations did not work well in Hermit and required more tweaking, while other parts of the theme didn't look as good to me as they did on first impression.

So instead of changing a theme I started tweaking my current one and got myself lost between the branches of Git. Going in, I knew the changes I'm working on need more time than I could commit to in one sitting. Creating another branch seemed to be the way to go. Things got out of hand when I realized I never started a new branch. I was working on my master branch, which was now out of sync with the one on GitHub.

If you find the above confusing -- that's fine. The problem was that I was in the same boat as you are now, scratching my head and going "huh?" And the more I struggled, the bigger mess I've made.

Thankfully, folks like [Kaushalmodi](https://github.com/kaushalmodi) exist. I don't know where I would be without his help. Not on a Hugo site using Git, that's for sure. I've learned a couple of things from him and the experience this time:

[Magit](https://magit.vc/) can be very helpful to get back on track. That's because it gives you sort of a road map to your project. You cay see the branches and then _go up and down the list using the arrow keys to choose the right location_. For the first time, I saw the benefit of doing that because of the mess I was in.

a whole menu of options is a question mark away, and everything has a hotkey. Magit was something I stayed away from in the past because I'm still scared of Git. After my last experience tough, I should keep using Magit for my work on this site. Magit is more effective and visual, and to me, the later is crucial.

I will babble some more about my tweaks and CSS as I work on things. I will keep updates in this category ([Blogging](https://joshrollinswrites.com/blogging/)) so you can follow up, or ignore them.


## Changes now merged (2019-02-06) {#changes-now-merged--2019-02-06}

I completed some initial changes to the CSS and merged with back with my main site version.

Those of you who understand git won't think much of it: all I did was marge a branch. Those of you who don't understand git won't think of it at all.

To me however, this is quite a big deal. I have successfully finished my first merge, in Magit none-the-less, after implementing changes on another branch.


## Changes implemented {#changes-implemented}

Most of the complaints I got about my current layout is the width of the sidebar to the left. It takes a lot of space, and for people who like to work with small screens, this was very annoying. The other issues I found was that this theme has three layout versions (we can call them extra wide, wide, and narrow). They were also indicated in ems and rems in the CSS, which I didn't like.

When it comes to screen width, I prefer to use pixels. So the site now has two versions: more than 800px and less than 800px. I will tweak with these some more (I think 600 as a max is better). The sidebar was tweaked to be narrower, as well as the site's title font.

Next, I think I will turn my attention to the navigation links themselves (under Topics) and make them more obvious with pure CSS; I have no intention of uploading fancy images. I also want to break the empty white at the right of the content in a way that doesn't make it all look so empty. We will see what happens there.

If anything looks off to you, please let me know in the comments! Thank you.