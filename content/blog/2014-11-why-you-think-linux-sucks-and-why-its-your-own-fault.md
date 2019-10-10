---
title: Windows power users are not Linux power users!
layout: post
date: 2014-11-08
sharing_disabled:
  - 1
categories:
  - 'Ubuntu & Linux'
type: "post"
featured: "/old/dilbert-unix.png"
---
Let's rid the world of one of the most prominent Linux myths: _&#8220;Desktop Linux sucks. It's just not there yet&#8221;._

When Windows power users try out Linux two things always happen:

  1. They get frustrated because they can't find how to do something in Linux.
  2. They brick their system, or make it extremely buggy.

I've been that person, I've bricked my system (a lot!), and the fact is, it was entirely my own fault. Linux didn't suck, I made it suck! This post is a summary of every mistake I made the last 4 years, in an attempt to prevent other people from making the same ones.

{{< fancybox path="/img/old/" file="dilbert-unix.png" caption="Let's rid the world of a few Linux misconceptions" >}}

## Linux is different

_Let's start with an example: Bill is trying out Ubuntu and wants to change his screen resolution. Bill knows that on Windows, you can right-click the desktop background and click &#8220;change screen resolution&#8221;. Bill tries this, but cannot find the &#8220;change screen resolution&#8221; option. Bill can now do two things:_

  1. _[the bad way] Assume you can only change this using the commandline. Go online and rant about how Ubuntu is impossibly hard to use._
  2. _[the good way] Open the dash and search for &#8220;Resolution&#8221; or &#8220;screen&#8221; or &#8220;display&#8221; or &#8220;monitor&#8221; or &#8220;projector&#8221; or whatever. He will find the &#8220;Displays&#8221; application. If he isn't entirely sure if that is the right application, he can right-click the icon and he will see a description of what the application does._

Linux is not Windows. You are used to doing things a certain way on Windows. Some things will work differently on Linux. You will have to get used to it. This does not mean Linux is hard, only that it is different. Mac has this exact same problem. Windows power users complaining that ctrl-c ctrl-v does not work on a mac, even though the command button makes a lot of sense.

{{< fancybox path="/img/old/" file="change-screen-resolution.png" caption="And yes, you can change the resolution in a GUI" >}}

## Windows power user != Linux power user

_Another example: Jessica knows a thing or two about Windows, she can even re-install Windows, if she finds that dvd she once burned. Jessica want to try out Ubuntu. She takes an old computer lying around and starts up the Ubuntu installer. She knows it's better to have different partitions, so she chooses to partition the disks manually. She tries to configure the partitions, but she keeps getting errors she does not understand. She gets frustrated and rants on G+ about how in Linux, everything is complicated._

I see this mentality a lot: &#8220;I know how to do advanced tasks on Windows. I don't know how to do advanced tasks on Linux, so Linux must be hard.&#8221;

You can do advanced tasks on Windows, because you learned how to do them on Windows. You will have to learn how to do some of them for Linux. This is the same for every platform. You can be a complete Linux Guru, being able to install Linux From Scratch. But you will still have to relearn how to flash your android phone.

Give it time, after a while you will come to have the same skill level on Linux as you have on Windows. Just don't expect to get there on the first day.

## You are a danger to your Linux

_Exhibit A: Alice her Windows machine is becoming really slow and she wonders what she could do to speed it up a little. Alice googles &#8220;how to speed up Windows&#8221;. One of the first results is a blog explaining how to use cCleaner to disable processes. Alice, being a Windows power user, knows this can break her system really bad, so she is very careful and googles each process before disabling it. Alice is happy, her Windows is faster again._

_Exhibit B: Bob is running the latest Ubuntu on a 10-year old laptop and notices it is a bit slow. Bob is a Windows power user, he figures he knows enough about computers to do something about it. He googles &#8220;how to make Ubuntu faster&#8221;. He finds a blog telling him to run different commands. The blogpost is a year old and has a lot of &#8220;thanks!&#8221; comments, so Bob thinks he can trust the author. Bob runs the commands. When a command fails, he figures it is a permission problem, so he runs the command again with &#8220;sudo&#8221;. The following week, Bob experiences weird glitches and crashes, and his computer cannot connect to his printer anymore. Bob is unhappy and goes on twitter to rage about how buggy Linux is._

You're a Windows power user. You can mess with Windows, because you know what is dangerous, you know what warnings you can safely ignore. You are not a Linux power user. You do not know how to make that distinction on Linux, so be very careful!

{{< fancybox path="/img/old" file="make-ubuntu-faster-e1415460263146.png" caption="Do not blindly trust commands from the web" >}}

I cannot stress this enough. I've seen this happen so many times, with myself, and with other people.  A friend of mine wanted to make a lightweight Ubuntu install for a media center. He was using a heavily outdated guide to do so. The guide instructed him to remove a lot of programs, including compiz. Little did he know that newer versions of Ubuntu(Unity) require compiz to function properly. The result: he bricked his system, and blamed Ubuntu in the process.

## **A Desktop environment is not a theme**

A desktop environment(DE) is a collection of software that does a lot more than just &#8220;look good&#8221;. A DE handles a lot of the &#8220;usability&#8221; features of the desktop, like automounting USB-sticks, CD's, DVD's and memory cards. It also helps you set up your network, it configures DHCP, detects wireless networks and gives you a nice user interface to enter the WIFI password. A DE also handles the function keys (brightness, sound, &#8230;) on your keyboard, and it can even connect to your smartphone to show you if you have new messages.

When you choose a DE, you basically choose how you will interact with your computer. If you choose a lightweight DE like lxde, you will lose a lot of the out-of-the-box experience a Windows/Mac user might expect. You will have to pop open a terminal, even to do basic stuff, like change your timezone. Unity on the other hand has those features, but demands more from your hardware.

{{< fancybox path="/img/old/" file="xubuntu-trusty_desktop-600x450.png" caption="Xubuntu might be fast and stable, but it comes with a price" >}}

A lot of the DE's share the same libraries and software. Installing multiple DE's at the same time can cause problems. If you want to try out different DE's, I recommend doing a clean install with one of [the official Ubuntu flavours][1], or another distro.

## Choose wisely, and stick to that choice

Linux gives you a lot of choice. This is a great strength, but also a weakness. People have a tendency of making bad decisions when presented with so much choice.

Everyone who tried Linux for the first time has had the same question: &#8220;what distro should I use?&#8221;. This seems like a very hard question, and [the internet gives you a lot of conflicting answers to it][2]. However, for 99% of the people, the answer is really simple.

If you're looking for a Window/Mac replacement for your primary machine, and you are new to Linux,  you should use default Ubuntu. Ubuntu offers the complete out-of-the-box experience you are used to on Windows/Mac. It is the best supported desktop, and It also has a good community that is very newbie-friendly. Every problem you will have, someone has had already. Askubuntu is full of questions Windows and Mac users might have when switching to Ubuntu.


{{< fancybox path="/img/old/" file="askubuntu-1024x644.png" caption="Askubuntu, helping Windows users change to Linux since 2010" >}}

You will surely find a DE that is easier to use than Unity. You will also find one that is more stable and one that is more beautiful. However, Unity offers the complete package with very few rough edges.

It's also easy to find a Distro that is more up-to-date than Ubuntu. Finding one that is more stable and one that is faster is easy too. But again, Ubuntu offers the complete package, with very few rough edges. It makes the transition very easy and it is a care-free Windows/Mac replacement.


{{< fancybox path="/img/old/" file="unity-is-beautiful-1024x576.png" caption="With a Numix theme, Unity looks pretty good!" >}}

## Conclusion

Are you thinking of joining the cool kids and trying out Linux? Then start with an easy distro like Ubuntu and be careful with what you do in the commandline. Most important of all, remember that Linux is different, and that's a good thing.

Enjoy your Linux, and let me know your experiences in the comments down below.

 [1]: http://www.ubuntu.com/about/about-ubuntu/flavours
 [2]: https://www.google.com/search?safe=off&q=Linux%20best%20beginner%20disto&rct=j
