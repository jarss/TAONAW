+++
title = "From LastPass to KeePass"
author = ["Josh Rollins"]
publishDate = 2019-02-11T00:00:00-05:00
lastmod = 2019-02-13T07:06:13-05:00
draft = false
+++

I've been using LastPass for the last 5 years and been happy with it. I recommended it to friends, family, and co-workers. I tried to sell it through its convenience: once set up, LastPass auto-fills user and password fields, and can even log you into a website directly. LastPass also creates complicated passwords automatically and is available on every major browser, iPhones and Android.

But it seems like even LastPass's time has come.

<!--more-->

As we know, Convenience usually comes at the price of security. LastPass auto-fill is quick and effective but also makes it very easy for someone else to grab your laptop, find your bank website in your history, and log int with your saved credentials.  To resolve this issue, LastPass has a couple of built-in options such as logging you out after a certain amount of time or logging off when the browser is closed. There features need to be activated on each new installation of LastPass.

So LastPass was an obvious choice for my mom's new chromebook. I thought I'd set her up with a new account and share passwords with her directly. I wanted her to learn to trust the app and starts creating new secure passwords instead of using the same two or three she's been using for years. But instead, I discovered a problem.  there were problems.

The option to log off automatically if chrome is closed was ignored. I've checked and [asked other users on Reddit](https://www.reddit.com/r/Lastpass/comments/aozro2/lastpass%5Fauto%5Flogout%5Fdoesnt%5Fwork%5Fout%5Fon/), but all I got is the [generic troubleshooting advice](https://lastpass.com/support.php?cmd=showfaq&id=3846) to make sure Chrome completely exists for the auto logoff to work. Exiting Chrome is possible on Windows, Mac, and Linux (for which this guide was written) but, as it turned out, is _not_ possible on a Chromebook. I [summoned the ChromeOS task manager](https://support.google.com/chromebook/answer/6309225?hl=en) with `shift+esc` or more recently `search+esc` (this is different than the Chrome browser's task manager, which is accessible from inside Chrome) and saw that Chrome was still running even after I exited the app. I couldn't force chrome to quit either: The button to do so was grayed out when I had Chrome highlighted on the list.

That meant that the only thing protecting someone from accessing all your passwords is your Google Password with lockscreen enabled. Perhaps i'm paranoid, but for me, that's not nearly enough. I disabled the extension and asked myself these two questions:

1.  Is it worth using LastPass over Chrome's built in password manger?
2.  Is LastPass really a good option to securely save passwords?

The the first answer is "not really." If you're a LastPass power user, who have the application on your phone and use a family plan (which allows you to share passwords), then yes, LastPass gives you more features. However, Chrome's Password Manager now allows you to create secure passwords and sync them with your Google Profile, which means you will have access to those anywhere you log in including your Phone. Since on a Chromebook your security is already handled by Google, there's not much sense to start a new account with LastPass, which basically does the same thing.

The second question is harder to answer. LastPass is a company that makes its business to secure passwords all day every day, and they have a great product. They are, overall, pretty transparent with their security breaches when they happen and apply patches and fixes very fast.

However, LastPass' browser extension is also its weakest point. To be fair, the same can be said for _any_ password manager that has an extension built into the browser. Various vulnerabilities have been listed before and [some were listed by LastPass](https://lastpass.com/support.php?cmd=showfaq&id=11012) themselves. If you're really concerned about the security of your passwords, you should not use a browser extension. However,if I am hard-pressed between choosing Chrome's built in password solution and a third party's solution that is built into Chrome, I will go with Chrome's built-in solution because it's native to the application and hence (hopefully) more secure.

But. The real answer here is that you shouldn't use a browser extension _at all_. And that's what I do these days.

My favorite solution is to use good ol' [KeyPass](https://en.wikipedia.org/wiki/KeePass), which has been around for about 15 years. I like KeyPass for a couple of reasons:

1.  It's a standalone program with  a simple GUI and flexibility. It works and looks better than LastPass's more complicated controls and does not relay on cookies.
2.  The only person with my passwords is me, which makes me sleep better at night. This has been my general trend since I started using Linux. It's not about privacy and less about security, a proud feeling of owning my on data, something I feel we don't do enough these days.
3.  KeyPass is old, open sourced, free, and probably not going anywhere. I'd like to say the same thing about LastPass, but companies such as these are constantly get eaten by greedy corporation that inject them with crap like social network integration and ads.
4.  With it's combination of using key files and different ciphers (at least via plugins), it feels solid and secure. Not that LastPass security is not good enough. It should also be mentioned that LastPass has two-factor authentication.

Because KeyPass doesn't have a browser extension (at least not out of the box), I use [xdotool](https://www.semicomplete.com/projects/xdotool/) to auto-type passwords into websites' text fields. The workflow: I click the user field on a website, Alt+Tab back to KeyPass, hit the auto-type shortcut, and watch KeyPass putting in my credentials as if I'm typing them from memory. Because I can customize the auto-input macro (KeyPass2 and up), eventually this makes it even more reliable than LastPass' auto-fill feature, which sometimes doesn't work well with fancy animated menus.

LastPass is another tool I didn't think about replacing when I transitioned into Linux, and for a long time, I kept using it in Linux as well. When I switched away from Chrome and stopped being logged into Google all the time, Chrome's extensions stayed behind. Like many other products (Gmail, Google Docs, Dropbox...) I'm slowly but surely finding good open source options which are often better.