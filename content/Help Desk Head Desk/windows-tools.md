+++
title = "Tools in Windows"
author = ["Josh Rollins"]
publishDate = 2019-09-28T00:00:00-04:00
lastmod = 2019-10-03T06:57:48-04:00
tags = ["tools"]
draft = false
+++

My [first public video](https://open.tube/videos/watch/697084c3-6e9b-435c-b5e2-7647a9d9c30f) introduced me to new challanges I didn't face until now. Case in point: displaying milliseconds in VLC. I looked online in various places for a solution with my tools of choice, VLC player and ffmpeg. Workarounds do exist, but not nearly as simple as what exists for me in Windows. This happened to me before. As I was starting to get stuck, I realized that sometimes it's ok not to wrack my head over every single hurdle. This is a reminder for myself, and hopefully save you some time to.

<!--more-->


## Millseconds? Why? {#millseconds-why}

While going over my video and deciding on parts to cut out (you guys don't need to see me reading from my notes and going "uhhh, that doesn't make any sense...") it became clear that the cuts are sharp and unpolished. I start to say something, and then the video cuts to me looking at a different direction starting a new sentence. It's jarring and makes me cringe.

FFMPEG allows sepcifying which sagments you want to isolate down to the millisecond to prevent this from happening. Figuring out the point of cutting percisely on that level though proved to be too hard in VLC. I'm sure I can tune VLC to move frame by frame and somehow display the exact timestamp I'm on, but after a day and a half of looking into different solutions and two extensions, I gave up.


## Windows and MPC-HC {#windows-and-mpc-hc}

[Media Player Classic: Home Cinema](https://mpc-hc.org/) is exactly what I needed. I remembered it from my pre-linux days, when I used it to watch different exotic video codecs that would not play on any other player.

It's a lightweight tool that doesn't do much else (as far as I know) besides playing videos and, if you right-click on the timestamp and choose "high precision". Bang. A day and a half of looking into complicated solutions resolved in a single rightclick. The fact that I sometimes record and always edit my videos on my Windows desktop (which is my much stronger gaming-oriented machine) helps.

Unfortuantely, WPC-HC is [discontinued](https://mpc-hc.org/2017/07/16/1.7.13-released-and-farewell/). After all, who needs such a niche product when you have something as rubust and full-featured like VLC...? So while it runs great for now, I probably need to keep my eyes open for a replacement (any recommendtations are warmly welcome).


## But for Everything Else, Linux is Awesome... Right? {#but-for-everything-else-linux-is-awesome-dot-dot-dot-right}

For the most part, yes. But there are a few exceptions.

Another good tool without a Linux alternative that jumps to mind is [Greenshot](https://getgreenshot.org/). Yes, I blogged about [Flameshot](https://joshrollinswrites.com/help-desk-head-desk/best-tools-flameshot/) before, but I since stopped using it due to an [annoying locale issue](https://github.com/lupoDharkael/flameshot/issues/563#issuecomment-526918408) deep in my Manajro's configuration. It's replacement, [Ksnip](https://store.kde.org/p/1156408/)[^fn:1], is not as good. While I can forgive flameshot's lack of features in favor of lightness and elegance, ksnip is way "bulkier" but lacks many good features compared to greenshot and a good amount of polish.

While I'm at the graphics department: another great tool in Windows is [paint.net](https://www.getpaint.net/index.html). It's a light photo-editing tool which walks the thin line of "photoshop light" like no other app I've used. There's GIMP of course, but I never use it. It comes with its own learning curve and plethora of features I almost never need beyond my Android's [Snapspeed](https://play.google.com/store/apps/details?id=com.niksoftware.snapseed&hl=en) (here are two [recent](https://pixelfed.social/p/JR121/74693748268863488) [examples](https://pixelfed.social/p/JR121/82812393729691648)).

I'll skip the loaded issue of gaming on Linux, since the fact that I have a Windows desktop built mostly for that speaks for itself, and continue into other forms of entertainment: hosting my movies, music, and Ebooks. Linux does have the top hand when it comes to running a good server, but installing PLEX and managing file permissions for a NTFS hard drive shared with Windows is an experience I'm willing to pass on. When I eventually graduate to a NAS, it will probably be Linux based.

So this mostly leaves us with Windows for entertainment and video editing, Linux for productivity and work[^fn:2]. Sounds about right to me.

What about you? Do you use different systems side by side like this, or are you the laptop warrior kind? Maybe a Windows guru? A mac-all-the-way person?


## Footnotes {#footnotes}

[^fn:1]: Seems like this [project has been killed](https://community.kde.org/Incubator/Projects/Ksnip#Status) in favor of [KimageAnnonator](https://github.com/DamirPorobic/KImageAnnotator), which looks exactly the same to me.
[^fn:2]: Actually, since I use Backblaze to backup my files, my Windows machine is also my dedicated "backup server-client" as well. However it's my Raspberry Pi that does the automation and uploads a compressed backup file every night without fail. You can't beat Linux when it comes to automations of "set up and forget" like these.