+++
title = "Basic SSH Security"
author = ["Josh Rollins"]
publishDate = 2019-07-28T00:00:00-04:00
lastmod = 2019-08-14T08:32:35-04:00
tags = ["security", "emacs", "tramp", "ssh"]
draft = false
+++

They say a picture is worth a thousand words:

{{< figure src="/basic-ssh-security.png" >}}

This is my SSH server's log, and this looks like a good time to talk about basic ssh server security.

<!--more-->

Let's back up just a bit for the whys and hows.

To access my personal org files from work (my journal for example), I use [TRAMP](https://www.emacswiki.org/emacs/TrampMode) with SSH. Why SSH? It's rudimentary, supported out of the box, and relatively private. My work and personal tasks meet in my agenda, but I like to keep my personal resources away from work computers just as I prefer to keep work material away from my personal machine. So, I need to have an SSH server up and running. My setup includes a Raspberry Pi (cheap, reliable, good single-function device) as an [SSH server and Syncthing hub](https://joshrollinswrites.com/help-desk-head-desk/raspberry-pi-org-hub/) and a router that has port-forwarding to allow incoming SSH connections.

Even though I used a different port than the default 22, it was easy enough for the script kiddie in the picture above to find and identify. This is not hard to do; all you need is nmap. In this case, it seems some of the IPs belong to an Amazon server in the Philippines, so it looks like this particular individual uses an automated environment to find and exploit unprotected users. So far, this sounds like a classic scenario.

I set down and decided to implement some basic security configurations I've should have had in place since day one. None of these are ground-breaking security, and I'm not an expert myself, but these are probably a good start.


## My Setup {#my-setup}

These configurations are available inside `/etc/ssh/sshd_config`. I'm using OpenSSH server. If you're using my configurations, remember to delete the "#" at the start of these lines, as they are marked as comments by default.

1.  `Port ####`: Specify a port number. Never leave as 22. Go high up, I would personally start at the 8000s. These ports are less likely to be used and script kiddies are less likely to sniff these with their tools. Not exactly ironclad facts, but we need to start somewhere.

2.  `ListenAddress`: The idea is to restrict the IP addresses the server will listen to, _but this is not where we actually do it (it failed for me)_. Rather, I use it here as a reminder for later. Figure out where you're connecting from and stick to it. You probably don't need to SSH from across the world; for this, there's [Syncthing](https://syncthing.net/) and a laptop. Read more details about my approach here further down.

3.  `LoginGraceTime 20s`: In seconds (as in, 20s) this is how long the server will wait before it closes the connection. Leave low since you're going to copy-paste a long, 30-character password you will never remember from password manager anyway (because you're not going to use an 8-character password, right?? if you do, please stop reading right now and stop using SSH, you'll be better off) and 20 seconds is plenty to do that. You could use a key, however, I chose not to use it for my setup because I keep using different machines (I should probably stop) and I figure I can change my password every other month or so. This is easy enough to do with a password manager.

4.  `PermitRootLogin no`: Never a good idea to log into your ssh as Root, you can always escalate once logged in as a user. Don't let hackers login as root either. I can't think of a good reason to allow root logins.

5.  `MaxAuthTries 2`: Yes, you get two tries to try the password before it locks out. Not clear yet if this lasts until you reset the server or if it's a timeout-based. Either way, since we copy-paste a password, this is good security measure if someone's trying to brute-force their way in from a specific IP address, like in my case.

6.  `ClientAliveCountMax 0` and `ClientAliveInterval 600`: these work together, as per [this article](https://www.thegeekstuff.com/2011/05/openssh-options/). The idea is to kill SSH when ideal. Here's how it works: Interval is how long before the server sends a "hey, are you there?" question. CountMax is how many of these answered questions the server will accept. So, in the above, we are waiting 600 seconds which are 10 minutes, and then the server will send... nothing, so it will disconnect. It means we'll get kicked off after 10 minutes of inactivity.


## Restricting to certain IPs only {#restricting-to-certain-ips-only}

In additions to these, I also restricted the allowed IP range as mentioned above. To do that we're using two files, `/etc/hosts.deny` and `/etc/hosts.allow`. This is discussed [here](https://unix.stackexchange.com/questions/406245/limit-ssh-access-to-specific-clients-by-ip-address), in option 2 (TCP wrappers). The system described here did not work for me as explained, and after reading into the instructions in the files themselves, I got it to work as follows:

In the deny file, we add the line `sshd: ALL EXCEPT xxx.xxx.`
where the xxx is the first and second octet of the IP address we want to allow. This is usually good enough to include all IPs from a certain place, but YMMV. In my case, this range specifies a specific office floor in my work site (which is fairly large), which restricts access only to my office floor area. When I tested the connection from my Android, I could not connect using my carrier but I _could_ connect from work since that's the IP address I specified. This is an awesome technique.

Again, this works for me but may not work for you. For one, you might be using a laptop for work and have a wider range of IPs as you move around. For this, I would consider using the laptop itself to store the files and sync with Syncthing. You may also decide to use one machine, in which case you might want to allow all IPs, but use a PGP key, which is much longer to guess than a password and will automatically reject connections trying to guess a password. This is a preferred method to what I use, try to implement it first if you can.