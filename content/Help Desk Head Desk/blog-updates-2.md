+++
title = "Blog Updates: 2019-10"
author = ["Josh Rollins"]
publishDate = 2019-10-12T00:00:00-04:00
lastmod = 2019-10-14T08:28:47-04:00
tags = ["blogging", "hugo"]
draft = false
+++

I've been fairly active with the website this month, but most of the changes are behind the scenes.

<!--more-->


## Tags to Topics {#tags-to-topics}

The "tags" title changed to "Popular Topics". This list now displays any topics that have been featured at least 3 times on TAONAW from the highest to lowest. A new "All Topics" link at the bottom leads to the tag page (which I need to change to "topics" now - work in progress) to view all the other topics, sorted by latest addition. I am planning to add an introduction the page later on, inspired a bit by [Karl Voit](https://karl-voit.at/).

The "Sections" portion of the sidebar ~~will be~~  was eliminated. More personal posts are now tagged as "[life](https://joshrollinswrites.com/tags/life/)". As a preparation to go sections-less, the tags were cleaned and condensed to reflect broader topics. Popular topics that emerge will receive their own  tags as they become more popular.


## Cosmetics {#cosmetics}

The sidebar [is now 14rem wide](https://github.com/jarss/TAONAW/blob/master/static/css/hyde.css) to contain the "Popular Topics" heading without a break. This caused the words "Art Of" in the red title at the sidebar to come together, something I ~~intend to~~ changed. I learned that it's probably smarted to increase the spaces between words in the title using the [word-spacing](https://www.w3schools.com/cssref/pr%5Ftext%5Fword-spacing.asp) CSS property instead of changing the width of the sidebar.

Post titles have a new font, [Montserrat](https://fonts.google.com/specimen/Montserrat). If you don't see this font, please let me know. This change was implemented previously, but later deleted by mistake in the CSS file. This is a Google Font that is enabled for free using the head\_fonts.html in Hugo.

Colors for the tags under the titles and the "Read More" links on the main page were changed to the same red as the Title's red. Other links in the posts and remain the same[^fn:1].


## Fixing the Homepage {#fixing-the-homepage}

My homepage, which displays a list of summaries of posts, broke after a recent Hugo update. That was because of a [specific Hugo change in version .58](https://gohugo.io/news/0.58.0-relnotes/).  This was fixed after a day of diving into Hugo, something I should probably do more often.


## Trimming Down the fat {#trimming-down-the-fat}

As it turns out, there are a lot of unused files inside the builds of this website. For example, when I changed my tagging and got rid of the old tags, it turned out the old tags still have HTML files inside the site. The original theme I used to build this site is still stored intact inside the theme folders, ~~and I don't really need it~~[^fn:2]. There are other examples, probably one of the known side effects of having a static website that builds HTML webpages for everything.

Clearing the old files is tricky, and I ended up deleting files I didn't know I need until I tried to publish the site again. Not a big problem since everything is backed up many times over, but something I can live without.


## Netifly - Coming Soon {#netifly-coming-soon}

As Kaushal Modi, my Hugo mentor [pointed out](https://mastodon.technology/@kaushalmodi/102949264377765642), the answer to all these annoyances is Netifly. I knew about this service previously, but this time because of a specific issue[^fn:3] I had with git, I learned that Netifly bypasses the entire build Hugo creates. That is, it reads the md files directly.

Because the md files are created on the fly for me thanks to ox-hugo, it's almost as if I have a dynamic website. I would still need to push the changes to github, but Netifly would take care of everything from there. No more old dead HTML files or forgetting to build my website before pushing to github - something I do more often than I'd like to, for sure.

Getting a website to build on Netifly is pretty easy, but I'll need to change the DNS records to point to Netifly's servers instead of github. That's not a hard thing to do, but there's a chance something would break and my website will be down, and I'm running out of time as I'm writing this. I will wait on Netifly a bit longer, but this is a change that is pretty sure to happen.


## About Section {#about-section}

I've added an [about section](http://joshrollinswrites.com/about/) to the blog. Creating a section that uses the posts' template was a learning experience since Hugo's default is to treat all sections' main pages (index.html pages) as a "list" template. To resolve this, I needed to use `layout: "single"` in the [front-matter](https://gohugo.io/content-management/front-matter/) for the index page. In ox-hugo, this is done by adding a ~ `:EXPORT_HUGO_LAYOUT: single` property under the header.

I'm still not sure how to fit the link to the about section in the sidebar. For now, it's just a linked from my name in the site's description.


## Footnotes {#footnotes}

[^fn:1]: This was harder than it should have been... these links are nested inside a class which is also nested inside a class. The right syntax in CSS is `[parent-class] [child-class] [html-tag]` with spacing being important: three spaces, no more. However, because my CSS was messy, the rules I've added were re-defined again later in the CSS file; I wasn't aware I called the same elements in two different places. As it turns out, cleaning your code (CSS, bash, or whatever) is important - and so as adding comments.
[^fn:2]: When I tried to publish the site to Netifly (see below) it turned out I _do_ need the original theme of the site. I am unsure why at this point, since all the essential files I use are stored outside of the theme's folder. I believe this has to do with the site's theme setting which specifies the theme's name, which probably points to that folder.
[^fn:3]: I included the word "hugo" in my git ignore file. This was because I used to store a hugo binary in the site's root folder, because a newer version was not available on Linux Mint, at the time.