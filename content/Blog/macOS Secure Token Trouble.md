+++
title = "AFPS Secure Token Active Directory Problems"
author = ["Josh Rollins"]
publishDate = 2018-11-26T00:00:00-05:00
lastmod = 2018-11-26T21:15:55-05:00
draft = true
+++

Most chances are, you won't even hear about Secure Token unless you happen to manage Macs for your company. Even then, Secure Token seems to be only an issue with Active Directory (I might be wrong), so depending on how you manage these macs also.

Because Apple doesn't talk much about Secure Token, I suggest your read about  it on [Der Flounder](https://derflounder.wordpress.com/2018/01/20/secure-token-and-filevault-on-apple-file-system/). There's a pretty good explination of what it does and why.

My story begins with a delivery of an iMac. It usually takes me 1.5 hours to prep a Mac from start to finish since we don't have a working image yet; that's a whole issue in itself. The prepped iMac gets to the user bound to the domain so all they have to do is log in. I then connect them to their user's share drive (as a startup item so they always have it) and see if they need access to any printers that we don't have on the server, and there is always at least one.

I have to log in first (as the iMac's admin) to unlock FileVault. So far, so good. Then, using the fast switching menu, I get back to the login screen and ask the user to log in using their domain credentials. On AFPS, like the one here, I get the Security Token window. Fine no problem. I put in the admin credentials, the user is approved, and after adding said printers and share drive, we restart to make sure everything is in working order.

But it wasn't.

The user that I just authenticated is not on the login screen. My admin account is there, my test account is there, his account... nope. This is odd, since I know we just went through authenticated with the secure token. I log into my admin account and check the security settings, since I it will tell me if anyone is not allowed to log in because of FileVault... but nothing. I run `fdesetup list`, which shows the list of approved FileVault users, and sure enough, it's there.

In the next couple of days, I've had a couple of people log into this iMac to test. I also had the user log into a different iMac, one that I setup a week previsouly, with the exact same setup. Everyone could sign in and _stay_ approved (they'd show up after approved with the secure token and restart) on the iMac besides this one person. On the other iMac, we ran into the same issue with this user. I realized that the problem must be with the account.

Because I saw the user log in and out so many times and checked the users list, I noticed something odd: the user's name was omitted. There was nothing at the top right corner (fast switching) and in the list of users, the icon for a user showed up without a name. I've never seen anything like that.

Back at my desk I looked into the account and couldn't find anything odd at first. I even copied the account to create another test user... and then I saw it: the Display Name field for this user was blank for some reason. The Display Name field in AD is populated automatically when we create a new user, but not here.

Today I managed to do some finaly testings, and sure enough, the user name in macOS (at least for 10.13 AFPS) is pulled form this Display Name field. I repeated the same test - signed in with admin, gave my test user with the blank Display Name field access with secure token, and restarted. Sure enough, the test user could not be seen on the login screen. Only after my admin account was signed in, that test user was able to sign in as well.

As soon as I populated the Display Name field and logged in again, everything worked. Name showed up, and the secure token remained.

The conclusion here is interesting: macOS pulls the user's name field from "Display Name" in AD. And it _needs_ this name for the secure token; somehow, without it, it doesn't work. the secure token is tied to the name of the user, not the user account itself... or at least, not completely. Interesting.