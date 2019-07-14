+++
title = "Submenus in org-mode Capture"
author = ["Josh Rollins"]
publishDate = 2019-07-14T00:00:00-04:00
lastmod = 2019-07-14T13:21:59-04:00
tags = ["orgmode"]
draft = false
+++

[In my last post](https://joshrollinswrites.com/help-desk-head-desk/org-capture-in-files/), I discussed how I (finally) found out that I can use entire org files as capture templates. This is a basic feature that works out of the box, but the org-mode manual doesn't give it enough exposure in my opinion. Turns out it [wasn't just me](https://irreal.org/blog/?p=8161) either.

As I was expanding my checklists and learning more "trivial" org-capture features, I discovered more useful things, but ran out of time to write about them. It's now time to get back to more "basics" of org-capture again for some helpful tips.

<!--more-->

When you build your org-mode templates, it's possible to create sub-menus for better organization. Another way to explain it is to think of "categories" in your capture.

Says [the manual](https://orgmode.org/manual/Template-elements.html#Template-elements):

> Keys
>
> The keys that selects the template, as a string, characters only, for example ‘"a"’, for a template to be selected with a single key, or **‘"bt"’ for selection with two keys. When using several keys, keys using the same prefix key must be sequential in the list and preceded by a 2-element entry explaining the prefix key**, for example.

The bold part was another part that I had to read several times to understand. I knew there's something different because two letters are used, but my capture template failed to work the first couple of times. I figured it out, and here it is:

```nil
 (setq org-capture-templates
  (quote (
	  ("s" "Manual Laptop Setups")
	  ("sd" "Staff Dell Laptops" entry
	  (file+headline "/mnt/veracrypt1/Archive/OhSnap!.org" "Staff Dells")
	  (file "/mnt/veracrypt1/Work/setup-dells.org"))
	  ("sa" "Staff Apple Laptops" entry
	  (file+headline "/mnt/veracrypt1/Archive/OhSnap!.org" "Staff MacBooks")
	  (file "/mnt/veracrypt1/Work/setup-macs.org"))
	  ("sm" "SLS-Mac" entry
	  (file+headline "/mnt/veracrypt1/Archive/OhSnap!.org" "SLS-Mac")
	  (file "/mnt/veracrypt1/Work/setup-SLS-Mac.org"))
	  ("sw" "SLS-Windows" entry
	  (file+headline "/mnt/veracrypt1/Archive/OhSnap!.org" "SLS-Windows")
	  (file "/mnt/veracrypt1/Work/setup-SLS-Mac.org"))
...
```

Let's take it piece by piece from the top. Keep in mind this is not the entire template, just the relevant part. If you just copy-paste it, it will fail (it's incomplete).

First, as soon as I start the capture templates, it seems as if I am starting to create another one _inside_ the first one. That's what the manual means. In my opinion, it stumbles on its own words. Another case where an example (like the above) would go a long way. What I did is basically created a _sub-menu_ for "Manual Laptop Setups."

The result is that when I call org-capture, I get the following:

```nil
Select a capture template
===========================

[s]... Manual Laptop Setups...
[i] INC (my incident template)
[e] Event (my event and journal template)
```

I have more templates going down, but I want you to look at the very first one. That `[s]` with the three dots after it indicates pressing `s` will take me to a sub-menu of the capture template, which looks like this:

```nil
Select a capture template
===========================

s [d] Staff Dell Laptops
s [a] Staff Apple Laptops
s [m] SLS-Mac
s [w] SLS-Windows
```

You can see form how the menu looks like that all of these items start with an `s` but this time without the brackets. The brackets indicate what you can press _now_ after you've already pressed s to get into the sub-menu you're currently in. That is, d for Dell checklist, a for Apple checklist, and so on.

Each one of these sub-templates is a checklist based in an org file like I explained in the previous post. The templates are all org files (like `setup-SLS-Mac.org` for example, the third template) which are nothing but checklists like I pointed out in the previous post.

This way I can have an entire "category" of capture templates, with S for setup, without having a long list with letters that won't seem related.