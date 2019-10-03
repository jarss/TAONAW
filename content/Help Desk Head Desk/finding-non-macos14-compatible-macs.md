+++
title = "Using Regex for Old macOS Models"
author = ["Josh Rollins"]
publishDate = 2019-02-17T00:00:00-05:00
lastmod = 2019-10-03T07:04:46-04:00
tags = ["automation"]
draft = false
+++

At work, we are a small team serving a very large gorup of clients. Because of that, automation is very importnat. It is impossible to get to each client directly, and we constantly have our plates full with other projects, walk-ins and general maintanance.

One project that was recently brought up was detecting and replacing old company-owned Macs that are out of warranty and cannot be upgraded to Apple's newest macOS, which at the time of this writing is [macOS Mojavi (10.14)](https://itunes.apple.com/us/app/macos-mojave/id1398502828). the idea is to locate these machines and retire them. To do such projects, we use system managment tool, KACE. KACE used to belong to Dell, and is still mostly used for Windows machines (it is most usefuls on Dells, obviously) but in this line of work it's many times using the tools you already have.

<!--more-->


## Identifying macOS 10.14 minimum requirements {#identifying-macos-10-dot-14-minimum-requirements}

Here's Apple's official [compatible model list](https://support.apple.com/en-us/HT201475), which contains models by their release date in a buyer-friendly format, such as "MacBook Air introduced in mid 2012 or later." The problem is that this imibgious description doesn't work with  systme management tools, which use the specific  model identifiers (as it should). Given the popularity of Macs, however, it's not hard to find a list of the model identifiers matched with Apple's official list. Here's EveryMac.com's [compatible model identifer list](https://everymac.com/mac-answers/macos-mojave-faq/macos-mojave-1014-compatible-macs-system-requirements.html).

Using the above list, we can use this [full list](https://everymac.com/systems/by%5Fcapability/mac-specs-by-machine-model-machine-id.html) from the same site to fine the first model identifier that will _not_ work for macOS10.14. This model would be the newest model on our "non-compatible list". We need to find each model of the different major Mac families.


## Loading it into KACE: {#loading-it-into-kace}

KACE lists model identifiers under "System Model". It the case here, we are looking at a MacBook Pro 14,2 (which is mid 2017, according to the list above). This is the key we will use to create our filter:

{{< figure src="/mnt/hgfs/Space/hallway/finding-non-macos14-compatible-macs2.png" >}}

One of KACE's killer features is its smart lables, which allows us to build very detailed filters to profile hardware. Smart labels comb through the entire inventory and capture devices that fit our desired filter. There is a basic wizard built into KACE which allows us to create basic labels, but if we need to dive in deeper we need to use Regex or straight up SQL.

To create the smart label, I used [this helpful article](https://www.itninja.com/blog/view/using-regex-in-smart-labels-to-find-lower-versioned-software-w-java-example). I suspect KACE's Regex is nothing special, but this was my first time trying to get my hands dirty with it. It was fun! Here's what it looks like:

{{< figure src="/mnt/hgfs/Space/hallway/finding-non-macos14-compatible-macs1.png" >}}

As we can see, the filter uses conditions for eahc one of the six family models. Let's take a look at `^(MacBookAir[1-4],)` as an example, keep in mind how the System Model (above) looks like.

1.  Our complete Regex statement needs to be included inside a parenthesis
2.  Going back, we use `^` as a starting point. It declares that this is the start of the string, and nothing should come before it.
3.  We spell out `MacBookAir` because that's just the text string of the model.
4.  Next, square brackets call a range of numbers; in this case, 1 through 4. This goes back to the minimum requirement mentioned previously. Using our lists above, we know that the lowest compatible MacBook Air model for 10.14 is MacBook Air 5,1. This means MacBook Air 4,2 is the first _non-compatible_ Mac we need to capture. This is why any Model Identifiers that include 4,2 and below (4,1 3,2 3,1 etc.)
5.  the comman after the number range is just a text string, as we have it in the System Model field in KACE.


## Creating the report {#creating-the-report}

KACE has the ability to create an automatic report for machiens that answer specific creteria. The reports also come with a built in filter and a wizard, even though not as customizable as the one in smart labels.

It's generally a good idea to create a report that is based on a smart label because the smart label can be applied to other actions in KACE. For example, if we'd like to later send an alert to the users of these old Macs, telling them to come to IT with their Macs for inspection. Smart Labels also work immidetly with KACE's databse, where reports are built only from new results, meaning we need to wait for Macs to connect and update on KACE before we see results. If someone has a work Mac they generally keep at home and don't connect to our network, we will wait a long time before we know about it.

in KACE reporting tools, there's an option to base the report directly on a Smart Label, which is what we'll do here. I won't cover the report in this post, but it's important to mention that while the smart label is good to _capture_ the information, the report is much better at _presenting_ it. Use the report to specifiy things like the user's full name, last login to KACE, IP address, etc. The report can also be created as a CSV or HTML file among others, and can be emailed.