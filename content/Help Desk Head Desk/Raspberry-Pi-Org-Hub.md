+++
title = "The Hub"
author = ["Josh Rollins"]
publishDate = 2018-11-22T00:00:00-05:00
lastmod = 2019-07-28T07:16:20-04:00
tags = ["network", "raspberry-pi"]
draft = false
+++

Having a consisted, stable server for my org files has been on my mind for a while. I bought a Raspberry PI (RP) to serve as a file server to be used as a "hub" that will always be on and host these files. This is a description of the setup of what I've done to make this work. I hope you'd find this useful! Feel free to contact me with any questions.

<!--more-->


## Buying the Raspberry Pi. {#buying-the-raspberry-pi-dot}

For the setup I describe here, you need the RP itself, a power source, an SD card, a USB case for 2.5 inch HDD, and the HDD itself. You'll also need an Ethernet cord for this setup. If you don't have one, go grab yourself a [CAT6 cord Amazon Basics](https://www.amazon.com/AmazonBasics-RJ45-Cat-6-Ethernet-Patch-Cable-5-Feet-1-5-Meters/dp/B00N2VILDM/ref=lp%5F9938478011%5F1%5F1?s=pc&ie=UTF8&qid=1542991619&sr=1-1) cable, it's always good to have one around.

For the RP, you better off getting a package similar to [this one](https://www.amazon.com/CanaKit-Raspberry-Complete-Starter-Kit/dp/B01C6Q2GSY/ref=sr%5F1%5Ffkmr0%5F2?s=electronics&ie=UTF8&qid=1541986065&sr=1-2-fkmr0&keywords=canakit+raspberry+pi+3+b%2B+sd+card). You could probably get something slightly cheaper by getting all the parts yourself, but not by much. Better to have everything you need at once without worrying about forgetting something. I didn't get the above package with the SD card, so I had to wait a couple of days for another order to come in.

The HDD I had laying around already, so I got [this case](https://www.amazon.com/gp/product/B01M08LCXW/ref=oh%5Faui%5Fdetailpage%5Fo00%5Fs00?ie=UTF8&psc=1) for it. 8 bucks.


## Setting up the RP {#setting-up-the-rp}

First, we're going to set up the SD card to run our RP.

Before we jump in, a note about my setup: I have Linux in a VM inside a Windows host. As it turns out, having Windows an alt-tab away (or in my case, ctrl+alt+left arrow away) can be very useful.

If switch between Windows programs and Linux commands without mentioning it, that's because this setup comes naturally to me at this point. I've been working this way (office and home) for almost four years, minusaa half a year of dual-booting with Linux-Mint as my daily OS. There's a whole story here about the switch to Linux and back, but that's for another time.

OK! Enough chatter. Let's get on with it.

1.  Download [Raspbian](https://www.raspberrypi.org/downloads/raspbian/) (zip file).
2.  Format the SD to FAT32
3.  Unzip, and write the image to the SD using [Win32 diskimager](https://sourceforge.net/projects/win32diskimager/) or Underbootin. For me, the first option is better when I deal with SD cards and my USB-SD adapter, YMMV.
4.  Create an empty file (no extension) on the SD root called SSH.

That last part is important. Creating the file (in windows, just create a new text file, rename to SSH and delete the extension) is what tells our RP to open port 22 for SSH.

Then you insert the SD card and power the RP up. Log into your router to find the RP's IP address.  This is why you need to Ethernet connection for. You won't be able to access the RP with WiFi for this.

Go ahead and SSH into the RP as pi: `ssh pi@[RP IP address here]`. your default password is raspberry.

Once in, you want to sudo into  RP config tool: `sudo raspi-config`. The setup tool is straightforward enough, but I found that remoting into the pi itself with VNC (coming up) is more convenient, so the only option we really care about now is to turn VNC on:
go to interface options (option 5 in my case, in the middle), and do that.

Save, get out, and then download [RealVNC](https://www.realvnc.com/en/connect/download/vnc/linux/). I downloaded it for Linux because that's what I use to SSH and setup my Pi. It's also where later I will setup Syncthing (coming up), so it made sense. RealVNC is the recommended option for RPs. it's easy to install and run, and supports VNCing with a password, which is what you need for the RP. As a bonus, it automatically creates nice thumbnails of the last logins (IP addresses) which can be useful.

With RealVNC, go ahead and connect to the RP using the same IP address and default password. The Raspbian will jump on you right away telling you need to change your default password and a bunch of other things. and that's all good. Follow these screens, and after updates are downloaded, _don't_ restart just yet.

You might have noticed you're working in a tiny little screen. Let's change that quickly by going to the preferences (click on the RP icon at the top left), then Raspberry Pi Configurations. Under resolution, choose something that works well for you. for my ultra wide screen, 1920x1080 was good enough to work in. Now you can restart. If you changed your password (you should have!) leave RealVNC on and it will inform you the password is wrong (because you changed it). All good, log in.


## A note about passwords and password generators {#a-note-about-passwords-and-password-generators}

If you use a password manager (my favorite on Linux now is xpass, LastPass is another), I strongly recommend to copy-paste your password in plaintext somewhere first, then copy it to the RP password-change field, and click the eye icon to reveal it. _Make sure what you pasted is the same thing you think you pasted_. In my case, I messed this up twice and had to image my SD card all over again. Yes, [there's a technique to reset up the password by booting into the root shell](https://howtoraspberrypi.com/recover-password-raspberry-pi/), but this didn't work for me. And besides, it's annoying and requires to physically connect a screen and keyboard to the RP.

Because my RP is set up for SSH with a password for now, I made a random 32 character password for it. copy-paste is not a choice.


## Encrypting the HDD {#encrypting-the-hdd}

I chose to use a separate HDD for a couple of reasons:

1.  I can take it with me if I need to and mount to another machine
2.  I have unused HDDs laying around from computer repairs. In my case, the HDD is 500GB, more than enough for text files and occasional pictures I use in Org-mode.
3.  If the HDD dies, I still have a functional RP with the OS on the SD card.

The encryption tool of choice for me ended up being LUKS, the same thing that encrypts Linux machines at startup. Actually, my first choice was [VeryCrypt](https://www.veracrypt.fr/en/Downloads.html). It comes with a convenient GUI and better options to handle containers. As it turns out, there's no updated version for ARM (which is what the RP is), and I'd have to compile from source. Possible, but not worth it for now.

VNC into your RP.

1.  First, Install cryptsetup on the RP (apt-get). This is the LUKS suite.
2.  Figure out the USB-connected drive: `sudo fdisk -l`. this will show you where's your hdd in /dev. In my case, it was in /dev/sda (not sda1, etc.)
3.  Format with LUKS:  `cryptsetup luksFormat /dev/[drive]` the default option was fine for me, but be aware that LUKS comes with many options if you so desire. When formatting, it should ask for a passphrase, so give it one. Then it should start doing its thing.
4.  When done, verify your drive is encrypted with  `cryptsetup luksDump /dev/[drive]`. You should see information about the encryption, along with the first key (LUKS can hold up to eight keys) and its hash. This means we're all good so far.
5.  Now, create a mount point for your drive. for me, out of habit of using Mint, that was /media/pimount. So: `sudo mkdir /media/pimount`.
6.  This is where things get a bit hazy since I'm writing this from memory. We need to open the encrypted drive with `cryptsetup luksOpen /dev/mapper/[drive name] [mounting point name]`. Notice we have **mapper** in the path after dev now. that's how LUKS work. The encryption is not being done on _dev_[drive] itself. I'm not sure why (I'm sure there's some Linux file system reason behind it), so feel free to educate me.
7.  Now, we need to format the drive with the file system of our choice. In my case, ext4. I believe this can also be done for FAT32 or even NTFS if you want to access your drive from Windows, but I haven't tested that. To format, you can download Gparted, which is good to have in general. However, this is easy to do with `mkfs.ext4 /dev/[name]`. In fact, that's exactly what Gparted would do for you anyway.
8.  Mount the freshly formatted drive: `mount /dev/mapper/[name] /media/[name]`  If we have "show mounted drives" option on the desktop in RP, it should show now. As a matter of fact, it's a good idea to enable this (right click on the RP desktop).

Before you start putting stuff on your HDD, it's a good idea to restart and practice mounting the drive again (step 6 and 8; you don't need to format again!). Then do it again. The unmount command is umount (no n), or you can simply restart the Pi.  There's a way to automate this using fstab, but messing your fstab could screw up your RP as it happened to me. I figured I never plan on really turning off the thing, so I will just keep doing it manually. Now, if someone happens to just grab your HDD and walk away, it will need to be mounter and decrypted.


## Syncthing setup {#syncthing-setup}

To me, [Syncthing](https://en.wikipedia.org/wiki/Syncthing) is the best solution for all my file-syncing needs. It works without a hitch until you need to change something tiny and meaningless. Then all hell breaks loose. I don't understand why that is, but I learned to accept it as a fact of life at this point.

During this RP weekend setup, I had to change my Syncthing setup so that the RP will become the central hub. What happened was a fruitless night of trying to figure out why Syncthing stopped syncing and  an messy Monday at work. It was such a bad setback, in fact, that I decided to create a process dubbed "downfall" for future cases just like this one when I can't use Org-mode at work. Yes, not having Syncthing basically means I can't use Org. But I digress... The important lesson here is this:

don't mess with Syncthing. Set it up, make sure it works, and _don't touch it_.

As intimidating as this sounds, Syncthing actually has a pretty simple setup process. Here's the plan:

{{< figure src="/hub.png" >}}

The different colors represent the different folders in syncthing. To me these are personal, work, utilities (this is the only folder that does not have org files), and archive.

I use four devices, three daily, one (laptop) once in a while. The home VM, which is my main productivity box, gets everything. So does the laptop, it's meant to be used as my home away from home. My work VM (OpenSuse Linux) only contains work org files and the archive. On the phone, I skip media-heavy folders like DnD and some classical music flac files to save space.

The setup process:

1.  Install Syncthing on RP (apt-get).
2.  Choose the first device to sync. Add the RP's ID to its Syncthing.
3.  _Wait_ for RP to acknowledge the device. Approve.
4.  From the connecting device, share the folders you want to sync with the RP.
5.  _Wait_ for RP to acknowledge folders. Approve each, choose path.
6.  Verify the sync work by altering the files a bit.
7.  Choose the second device to sync... repeat step 3-5.

Now, folders that common to a couple of devices should be added first from one device (as stated above) with the RP, and then add that folder to the _other_ device. Device\_A --> RP --> Device\_B. This ensures you're sharing the same folder (same folder ID) and not creating duplicates. The reason you're doing it this way and not just sharing from one device to another is because you don't want the other devices to see each other; they should only "see" the RP. The RP is the only device that needs to see all of them. Fewer complications means Syncthing works better and faster. Remember what I said earlier: don't play with it, keep it simple and it will work. Complicate it, and you'll spend hours trying to figure out what's wrong.

So for example, if I first sync my home VM and share the "work" folder to the RP, after I'm done and verify the sync work, I am connecting the work VM to the RP, wait until it's recognized, and then send the work folder (which is now synced between home VM and RP) _to_ the work VM.