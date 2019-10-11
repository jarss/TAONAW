+++
title = "Blog Updates: 2019-10"
author = ["Josh Rollins"]
publishDate = 2019-10-07T00:00:00-04:00
lastmod = 2019-10-08T06:42:30-04:00
tags = ["blogging", "hugo"]
draft = false
+++

I've been working on A few additional subtle CSS updates to this website.

<!--more-->


## Tags to Topics {#tags-to-topics}

The "tags" title changed to "Popular Topics". This list now displays any topics that have been featured at least 3 times on TAONAW from the highest to lowest. A new "All Topics" link at the bottom leads to the tag page (which I need to change to "topics" now) to view all the other topics, sorted by latest addition. I am planning to add a short summary to this page later on, something that was inspired a bit by [Karl Voit](https://karl-voit.at/).

The "Sections" portion of the sidebar will be eliminated. More personal posts are now tagged as "[life](https://joshrollinswrites.com/tags/life/)" ([HelpDesk/HeadDesk](https://joshrollinswrites.com/help-desk-head-desk/) is the main section of the blog, the one you're viewing now).

As a preparation to go sections-less, the tags were cleaned and condensed to reflect broader topics. Popular topics that emerge will receive their own  tags as they become more popular.


## Cosmetics {#cosmetics}

The sidebar [is now 14rem wide](https://github.com/jarss/TAONAW/blob/master/static/css/hyde.css) to contain the "Popular Topics" heading without a break. This caused the words "Art Of" at red title at the sidebar to come together, something I intend to change.

Post titles have a new font, [Montserrat](https://fonts.google.com/specimen/Montserrat). If you don't see this font, please let me know.

Colors for the tags under the titles and the "Read More" links on the main page were changed to the same red as the Title's red. Other links in the posts and remain the same[^fn:1].


## Fixing the Homepage {#fixing-the-homepage}

My homepage, which displays a list of summaries of posts, broke after a recent Hugo update. That was because of a [specific Hugo change in version .58](https://gohugo.io/news/0.58.0-relnotes/).  This was fixed after a day of diving into Hugo, something I should probably do more often.


## Footnotes {#footnotes}

[^fn:1]: This was harder than it should have been... these links are nested inside a class which is also nested inside a class. The right syntax in CSS is `[parent-class] [child-class] [html-tag]` with spacing being important: three spaces, no more. However, because my CSS was messy, the rules I've added were re-defined again later in the CSS file; I wasn't aware I called the same elements in two different places. As it turns out, cleaning your code (CSS, bash, or whatever) is important - and so as adding comments.