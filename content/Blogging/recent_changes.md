+++
title = "Some Recent Changes"
author = ["Josh Rollins"]
publishDate = 2018-12-09T00:00:00-05:00
lastmod = 2018-12-10T07:42:53-05:00
draft = true
+++

After I [moved joshrollinswrites.com from my (now dead) WordPress site over to my Hugo-created Github-hosted site](http://localhost:1313/TAONAW/blogging/switching%5F2%5Fhugo%5Fft/), I decided to work on some of the issues over the weekend.


## Navigational Changes {#navigational-changes}

As a personal blog, TAONAW does not only include tech bits but also personal thoughts. This was the most obvious seperation between topics. Personal stories are now stored in [The JR Life](https://joshrollinswrites.com/jrl/). In ox-hugo, creating this section means just another header in the site's org file.

Technology-related posts started to be disorganized. I write about different projects, and I decided to start splitting them up to topics they generally fall under. For example, I've been blogging about emacs and org for quite some time, so these will be included in [Emacs & Org](http://localhost:1313/TAONAW/emacsorg/) section. I also need to see about collecting the old posts from my WordPress website and my wiki and throw them in this section. Other tech posts which do not have categories yet (this basically means that there's only one or two posts about these) will fall under the [TechDen](http://localhost:1313/TAONAW/techden/), a generic tech "stuff" bracket, at least for now. I hope that the rule of two-or-more-posts-means-new-section would prevent this from becoming just a new messy section. Finally under tech related stuff, [Blogging](http://localhost:1313/TAONAW/blogging/) is now its own section, since this very blog is a tech project of its own.

There are a few more sections that are not visable yet on the published site. These sections already containted drafts of posts I'm working on. In ox-hugo, all I need to do is to switch the keyword from "ToDo" to "ACTIVE" to allow these changes to take place on the site. This makes the whole blogging experience feel the same like the Org flow I use on a daily basis. It is a synergy that I've never epxerienced before when writing, and it definitely changes my writing frequency to the better.


## Design changes {#design-changes}

Besides just creating sections and categorizing my posts, I've also added a section descriptor to the main blog homepage. This allows readers quickly know what the new posts fall under. If you were to visit  my site after this post is published, you will see the summary of this post along with the date and the category this is under (Blogging) so you know the latest post is about Blogging, not some tech project or my personal life.

Speaking of dates, I also changed the date format to be the same throughout the website: yyyy-mm-dd. I never fully agreed with the American way of describing dates (mm-dd-yyyy) and stuck the the rest-of-the-modern-world way (dd-mm-yyyy) which just makes more sense. When you start working with computers often, you learn to appriciate the yyyy-mm-dd format because that's how comptuers organize files automatically.


## Cosmetic changes {#cosmetic-changes}

Additional changes include removing the little wrench picture (a tattoo pic of Zen and The Art of Motorcycle Maintainance, a book that influenced TAONAW). The picture pushed the title out of the sreen, and just didn't fit that well. It might be restored later with some CSS magic.

A "navagation" title was added above the sidebar links with a decoration that is nothing more than fancy html symbols (I enjoy using those instead of pictures).


## Next: Section Descriptions {#next-section-descriptions}

When you click on a section, you can see a list of posts specific to that section. These list (of posts) pages are created by Hugo automatically, depending on my theme. It is possible to include a short description (along with whatever else you want) to these pages, so each section is described. However, I could not figure this out yet from reading the official documentation. This change will come as soon as I figure this next part out.