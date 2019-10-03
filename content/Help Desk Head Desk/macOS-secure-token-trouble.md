+++
title = "AFPS Secure Token Active Directory Problems"
author = ["Josh Rollins"]
publishDate = 2018-11-26T00:00:00-05:00
lastmod = 2019-10-03T07:02:56-04:00
tags = ["apple"]
draft = false
+++

Most chances are, you won't even hear about Secure Token unless you happen to manage Macs for your company. Secure Token seems to be only an issue with Active Directory.

<!--more-->

Because Apple doesn't talk much about Secure Token, I suggest you read about it on [Der Flounder](https://derflounder.wordpress.com/2018/01/20/secure-token-and-filevault-on-apple-file-system/). There's a pretty good explanation of what it does and why.

My story begins with the delivery of an iMac. It usually takes me 1.5 hours to prep a Mac from start to finish since we don't have a working image yet; that's a whole issue in itself. The prepped iMac gets to the user bound to the domain so all they have to do is log in. I then connect them to their user's share drive (as a startup item so they always have it) and see if they need access to any printers that we don't have on the server, There is usually at least one.

I have to log in first (as the iMac's admin) to unlock FileVault. So far, so good. Then, using the fast switching menu, I get back to the login screen and ask the user to log in using their domain credentials. On AFPS, like the one here, I get the Security Token window. Mo problem. I put in the admin credentials, the user is approved, and after adding said printers and share drive, we restart to make sure everything is in working order.

Last week though, it didn't.

The user that I just authenticated was not on the login screen. My admin account was there, my test account was there, his account... nope. This was odd since I knew we just went through authenticated with the secure token. I logged into my admin account and check the security settings since I know it will tell me if anyone is not allowed to log in because of FileVault... but nothing. I ran `fdesetup list`, which shows the list of approved FileVault users, and sure enough, he was there.

In the next couple of days, I've had a couple of users log into this iMac to test. I also had the user log into a different iMac, one that I set up a week previously using the exact same procedure. Everyone could sign in and _stay_ approved (they'd show up after approved with the secure token and restart) on the iMac besides this one person. On the other iMac, we ran into the same issue with this user. The problem then was with the account.

Because I saw the user log in and out so many times and checked the users list, I noticed something odd: the user's name was omitted. There was nothing at the top right corner (fast switching) and in the list of users, the icon for a user showed up without a name. I've never seen anything like that before on a mac.

Back at my desk I looked into the account and couldn't find anything odd at first. I even copied the account to create another test user... and then I saw it: the Display Name field for that user was blank for some reason. The Display Name field in AD is populated automatically when a new user is created, but not here.

Today I managed to do final testing. I repeated the same test: signed in with admin, gave my test user with the blank Display Name field access with secure token, and restarted. Sure enough, the test user could not be seen on the login screen. Only after my admin account was signed in the test user was able to sign in as well.

As soon as I populated the Display Name field and logged in again, everything worked. The name showed up, and the secure token remained.

The conclusion: macOS pulls the user's name field from "Display Name" in AD. And it _needs_ this name for the secure token. Without it, it doesn't work. the secure token is tied to the display name of the user, not the user account itself... or at least, not completely.