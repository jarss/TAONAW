+++
title = "Scripting in Bash 102"
author = ["Josh Rollins"]
publishDate = 2019-09-03T00:00:00-04:00
lastmod = 2019-09-08T17:00:47-04:00
draft = false
+++

This is my first attempt at explaining a full (though simple) script I wrote. This is also the longest post I've ever written.

I always say I'm no programmer (or scripter). Despite that, I somehow ended up creating a couple of useful scripts on my Linux machine.

My elementray scripts are a dynamic work in progress. I keep tweaking them as I learn and create new ones. I'd love to hear from experienced scripters just as I'd love to hear from those of you who never opened Nano before. Feedback is always welcome.

<!--more-->


## Newcomers: Few Basic Requirements {#newcomers-few-basic-requirements}

Before we dive in, a few scripting points to cover:

1.  A script is nothing more than a text file containing a list of commands in Bash (Linux's default shell). You can use any text editor you'd like to create the file, it doesn't matter. I use [Emacs](https://www.gnu.org/software/emacs/), of course.

2.  Speaking of a text editor: if you're on Linux, you probably have Nano built-in. Just type "nano" in terminal to bring it up. It has a slight learning curve with its weird key bindings, so [Here's a quick guide](https://www.lifewire.com/beginners-guide-to-nano-editor-3859002) to get you started.

3.  In Linux, it doesn't matter what extension your file has. That world belongs to Windows and MacOs. You can save your script as  "myfirstscript" and it will run just fine without an extension.[^fn:1]

4.  What _is_ important though is permissions in Linux, which is a whole topic in itself. In order to allow a text file to run as an executable chain of commands, you need to permit to do so. To do this, type in your terminal "chmod +x [your script path and name here]"[^fn:2] to tell Linux this is an executable file.

5.  You can't just run your script by typing it in your terminal and hit Enter. That's because it's not part of your system's path configuration, which tells Linux where are the scripts and programs you can run are.[^fn:3] You have to be specific and write out the entire path "[path/to/your/script/script here]" or be in the same directory as the script and execute it with `./[script here]`.

Hopefully the above makes sense. If not, don't worry about it for now, just try to follow the instructions.


## The Script {#the-script}

OK then, here it is:

```nil
#!/bin/bash

filename=w`date +%V_%y`
init_mon=`date +%Y-%m-%d`

cp /media/pispace/Documents/Archive/weekly-template.org /media/pispace/Documents/Archive/$filename.org

#+TITLE: Week Starting Monday 2019-02-11
sed -i "1s/^/#+TITLE: Week Starting Monday $init_mon\n/" /media/pispace/Documents/Archive/$filename.org
```

I'll go line by line to explain what it does and hopefully how it works.

So What does it do?

A practical little thing, this script creates a new .org file for me every week[^fn:4] from a template and changes its title to "Week Starting Monday [date]" where the date updated based on that week's date.

So for example, on 02-09-2019 (at 3:00 AM specifically), my Raspberry Pi created a new org file. The first line in that file, which is the title, reads "Week Starting Monday 2019-09-02" (I like my dates backward).

How does it do it?

Ah. Well, this is what this post is about. Let's dive in:


## The Shebang {#the-shebang}

The very first line, #!/bin/bash, is called shebang (or hashbang, but shebang seems to be more popular). Every script in Linux should (though there are ways around it, it's just good practice) start with a shebang. But what does this cryptic line do? We're just on the first line and it already seems like we need to learn another language!

No worries. Everything looks big and scary at first, that's why you break it down to parts you understand.

The "#" sign is usually used to enter a comment into your script. This means this line is not meant to be run as a command and should be skipped. When combined with a "!" it creates a special combo[^fn:5] called the [interpreter directive](https://en.wikipedia.org/wiki/Interpreter%5Fdirective), which tells Linux how to interpret the script we're about to write - or more precisely, where is the interpreter so the computer can find it and use it to interpret the command.

Since we're about to write a script in Bash, we need to tell our computer: "OK, this file is written in Bash, here's where you find bash" which is exactly what the next part is: `/bin/bash`.  this is where bash is, in your `/etc/bash` folder. If it was in a folder named giraffe, for example, it would be `#!/giraffe/bash`.


## Variables {#variables}

This is probably one of the most popular phrases used when you hear someone talking about a script. A variable (or var for short) is a container for a piece of data, usually called a string (string is one type of data, but for our purposes here let's keep it simple)

Our script contains two variables: filename and init-mon. It makes sense if you look at how it's written: `filename=[something...]` and `init_mon=[something...]`, like saying `my_name=Josh-Rollins`, for example.

In Bash, as soon as we place a "=" after a name like that, Bash knows this is a variable. Simple. OK, so what exactly goes into these containers?  This seems complicated... Again, it's all about breaking things down.

By the way, you can define variables anywhere in the script (as long as it's before you use them, of course), but it's considered good practice to write them first thing.


## The Date Command, and Reading the Manual {#the-date-command-and-reading-the-manual}

This is our first command. If you copy `date +%V_%y` and run it in your terminal, you'd get a number, an underscore, and another number. If I type this today (which happens to be September 3, 2019), I'd get "36\_19". By the way, notice the plus sign before the options (these are the letters with the percent sign)? it's important: in the manual, it says to use a plus sign when specifying a specific format to display.

We know a command named "date" is probably giving us date related output, and I just gave you today's date... can you guess what this command does? What are these numbers?

To be sure, let's run the _manual_ command on date. Type `man date` in your terminal. This is the manual for the date command (and yes, mostly every command in Linux has a manual page, isn't this awesome?)

The most important bits of info to get from the manual are the name the synopsis. The name tells us what the command does right there: "print or set the system date and time", and then the description which is the same thing. Go ahead and run "date" without any format options (that is, without the `%[something]`) part and see what it prints out by default; you'd notice it's the same as specified under the "Synopsis" part of the manual.

In our case, we use the date command with specific formatting options. In the manual for the command, scroll down to "Format" to see these. Do you see how many options the date command has? You can print out the current century or even the number of seconds since the beginning of 1970[^fn:6]. The options used in the script, %V and %y, give out the week number in the year and the year's last two digits. The underscore in between is nothing but a separator that will later show in the file name, to get the following format: [week number]\_[year's two digits], which gets us something like "12\_19.org".

The other variable, init\_mon, is another "twist" on the date command. Go ahead and try to figure out the options used on your own this time. Why do I need this second date? We will find out shortly.


## The Copy Command and Using Variables {#the-copy-command-and-using-variables}

the next line starts with "cp". This is simply us writing out a command, nothing fancy. cp stands for copy in Linux, a command that copies files and directories. Don't take my word for it, check the manual!

The command then says to copy my weekly org template (I talked about org files as templates [previously](https://joshrollinswrites.com/help-desk-head-desk/org-capture-in-files/)) from the origin directory to the destination directory (this format, of writing the origin location first, space, target location, is also noted in the manual. You have to follow this order), as a file named... "filename".org. And filename is the name of our variable, from earlier. We tell Bash we want to use the data in a variable (remember, it's just a container) by writing a dollar sign in front of the name of the variable we want to use. I added ".org[^fn:7]" at the end because - you got it - this is going to be a .org file.


## The sed Command {#the-sed-command}

The sed command stands for "stream editor". This is one powerful command, which I'm only scratching the surface of here. It allows you to manipulate text in all kinds of ways, but probably one of it's most popular usages (as in this script) is to substitute one line of text with another.

We call the command, sed, with option -i which tells it not to produce output. Basically "just do it, don't show me." This is because we don't want to see the replacement on the screen, we just want to manipulate the text.

The rest looks a bit crazy, but hang on, it makes sense:


### Using Quotation Marks {#using-quotation-marks}

We're going to use the quotation marks to include our entire stream _and option_ (you can see it ends at the very end of the line). It's our way of telling sed to take "this" where "this" is everything included in quotation lines[^fn:8]. We need to use it here because our substation includes spaces, and that usually interprets as a workflow instruction for the command: remember the cp command, and how it uses space to differentiate between the origin and the target? Well, something similar happens in sed, so if we just include spaces without the quotation marks, sed will do something else.


### Selecting the Right Text {#selecting-the-right-text}

Next, we have `1s/`. this is actually two in one combo: 1, for first line, and s, which tells sed we want a substitution. Then we have a forward slash (remember, forward slash "/" because it leans forward; backward slash "\\" because it leans backward) which is how we tell sed this is the expression we want to replace. In other words, we are selecting the text from here going forward, until the next forward slash.

Now wait a second, we already used the quotation marks for that, didn't we? Well yes. Kind of. The quotation marks acted as a wrapper for the whole expression, the text we want to replace (which is missing in this script, I will talk about this in a second), the text we want to replace with, variables... the whole shebang (sorry, couldn't resist). Quotation marks work in Bash in general as "wrappers" like this. The forward slash, on the other hand, is specific for the expressions _inside_ the command here, sed.

Think about it like a sandwich: you order a sandwich, you get it in a wrapping paper and a plastic bag. You don't eat those, that's just how you carry it home. Once you take it out, you still have a sandwich, and this sandwich includes the good stuff inside. The quotation marks are the plastic bag and the wrapping paper, the slashes represent the slices of the bread. you eat those, they are part of the food command, the bag and paper are not. Both act as wrappers, but for different purposes.

The last part of selecting the text is the caret (`^`) sign. This is a regex expression (short for ["regular expression"](https://en.wikipedia.org/wiki/Regular%5Fexpression)) which says "this is the very first part of the line". Regex expressions are a whole world of their own, a powerful way to explain text strings to the computer. I explored [a bit of regex](https://joshrollinswrites.com/help-desk-head-desk/finding-non-macos14-compatible-macs/) on my own earlier, if you're interested. It's a good example to show when this comes in handy. Combined with the `1s` from earlier, it tells sed to select the first line, at the beginning. But if we're replacing a whole line, why do we can to tell sed to go to the very beginning? Ah ha! And you'd be right. The reason for that has to do with how this particular script is written.


### Replacing Text and placing in File {#replacing-text-and-placing-in-file}

Above, we went over how to direct sed to the right text we want it to replace, but we didn't tell it what to replace, and what to replace with. This is what's coming up next.

Remember how forward slashes represent the pieces of the sandwich for the sed command? These are called [delimiters](https://en.wikipedia.org/wiki/Delimiter). Sed substitution defines our sandwich like so: "replace `/this/` with `/this/`." The syntax looks like "`/this/this/`". The first part tells sed what's getting replaced, the second part what it's replaced with.

In our script above, we told sed to replace the... nothing in the beginning of the line (there's nothing there after the `^` sign) with "`#+TITLE: Week Starting Monday $init_mon\n/`". Because we specified nothing as what we want to replace, sed will simply replace the whole line. It won't search for anything specific. And to make sure it starts right at the beginning of that line, we specified the carot from before.

If you use org-mode like me, you'd recognize this bit of text: it's org-mode's syntax of specifying a title for an org file. So, our sed goes to the very beginning of the very first line and replaces the entire line there with the "#TITLE..." line.

You'd recall from before, where I discussed variables, what the dollar sign is: we're calling our `init-mon` variable here, which contains the full date every Monday: The title is "Week Starting Monday " and then the date as I explained above.

Finally, we have a special bit of regex again after we finished the replacing job (the forward slash after the variable): "`\n`". This means, "start a new line please" - just like pressing enter on your keyboard. And... done, we just finished our sandwich, wrappers and all.

Then, we have space (it's a new line) which specifies the _target_ of the whole sed command. This is where I specify the file where this line of text should be added. In our case, the file we copied from our template above. So the sed command takes a generic line in the template that is served as a title holder (I simply typed in "#+TITLE: Week Starting Monday ----" but it could have said "pink rabbit" or simply nothing, doesn't matter, since this entire line is replaced) and replaces it with what we've done here.


### More about sed command {#more-about-sed-command}

I've used different sources when I wrote this post, and I'd just like to mention a few in case you're curious and want to go down the many holes of this awesome and complex command.

First, there's the [GNU manual for this command](https://www.gnu.org/software/sed/manual/sed.pdf) which goes beyond the man page. Just so you get an idea, it's .5MB of a PDF file with almost 40 pages. Yep, don't say I didn't warn you.

Then there's [this excellent tutorial](https://www.grymoire.com/Unix/Sed.html#TOC) that came up first in a search. It's long and thorough, with a touch of sense of humor. A bit more advanced.

If you want to read up more about regex, [I found this as a helpful reminder](https://www.rexegg.com/regex-quickstart.html).

And then you can always use stackoverflow for specific questions such as "[What does sed -i option do?](https://stackoverflow.com/questions/18527365/what-does-sed-i-option-do)"


## Conclusion {#conclusion}

That's it. If you followed along, you probably wondered where's the part that automates the whole thing, so I get it every Monday. The way it is now, I have to remember to run the script every week. What's the point in that? I mentioned in the footnotes, the automotive part is cron, and it will be discussed next time.

You may have more questions now than you had before reading the post. That's a good thing - you now have specific questions which are more likely to give you specific answers. I hope to get many of these questions myself so I can update and modify the post to help more folks. Linux and Bash is a wonderful thing. You get all this power to automate and create things completely for free. I spent over a week writing this post, and one of the reasons is that I kept getting distracted by "why is that?" and then looking for answers. The research is one part of the fun, sharing it is another.

Thank you for reading!


## Footnotes {#footnotes}

[^fn:1]: If you ever write scripts to execute in Mac or Windows (say, in another program) you'll notice these files has a ".sh" extension. But again, in Linux, this doesn't matter. You'd notice below that I create a .org file though, with an extension. What's that about? It has to do with the way Emacs is built. It can open _any_ file, but org-mode files (this is the "program" that opens org files) are identified by .org extension for sake of convenience. You can include a special line in any file that would tell Emacs this is an org-mode file as well, but using .org is just more natural.
[^fn:2]: **chmod** (change file mode) is a powerful and important command in Linux, outside of the scope of this post. You should check the manual for it (you should know how if you read through this post). This will take you down a rabbit hole regarding Linux file permissions, and you can [read more about it](https://devconnected.com/linux-file-permissions-complete-guide/) here (one of many links available). Wikipedia [also has a good section](https://en.wikipedia.org/wiki/File%5Fsystem%5Fpermissions#Traditional%5FUnix%5Fpermissions) to get you started.
[^fn:3]: The path in Linux is a variable (you'll learn about those in a bit) which contains all the directories where your Linux knows to find scripts and commands. OK, but what does that mean? I can't get into it here (because I'll never get to publish this post) but enough to say that the script you're writing is not a part of the "Linux default" commands which came with your Linux distro, so Linux doesn't know it's a command. Imagine telling a person who never shook hands before to just "shake hands." You'd have to explain it, and then that person could remember how to shake hands. Linux's way of remembering "shaking hands" and similar tricks it to add those to the list of directories that include such constrictions - the path.
[^fn:4]: Automating tasks in Linux are done by a different component, called cron. It takes a specific set of instructions written out in a string and translates it to a specific time loop (for me when using this script, on Monday, 3AM, every week). Cron is something I hope to expand on in a future post.
[^fn:5]: This special combo is called a "magic number", a unique value in ASCII that the computer understands as a direct command. I am not sure how many magic numbers like these exist. Sounds like something interesting to find out.
[^fn:6]: Turns out that this date (1/1/1970) is known as "The Unix [Epoch](https://en.wikipedia.org/wiki/Epoch%5F(computing))." A quick search led me to this [this discussion](https://stackoverflow.com/questions/2533563/why-are-dates-calculated-from-january-1st-1970). Turns out such dates are common in the computing world... read and learn!
[^fn:7]: When scripting, certain special characters (like our $ above) are reserved. This means that if we wanted to call our variable "$usd" for example, we couldn't. There are certain ways to tell Bash we want to use the character as a character, not as a "special signal." As a matter of fact, the period in my .org is a bit dangerous because the period also has a special meaning. I should have typed out something more specific telling Bash the period here is meant as just a period, not a signal -- but at this point I'm not sure how the syntax would look like. I'm learning these things myself, after all.
[^fn:8]: Those of you who look carefully might find yourself asking, "OK, but the quotation marks _include_ the command syntax, not just the text we want to use, what's up with that? Why isn't it `1s/^/"#+TITLE: Week Starting...`"? And I have a good answer: I don't know. It doesn't make sense to me either at the moment, but in all documentation I find, this is how the syntax works.