---
title: What does “perf interrupt took too long” mean?
author: galgalesh
layout: post
date: 2015-09-13
categories:
  - 'Ubuntu & Linux'
type: "post"
---

## Wifi problems

So, I&#8217;m having a problem with my laptop. When I&#8217;m using the &#8220;TelenetWiFree&#8221; connection, I get disconnected after a certain amount of time, and for some reason I cannot reconnect until I restart my computer. Toggling the hardware Wifi kill-switch, which lets you disable and enable the power to the wifi hardware, does not resolve the problem. After re-enabling the hardware, the wifi doesn&#8217;t seem to come back again. Only a reboot makes the Wifi work again&#8230;

The &#8220;TelenetWiFree&#8221; Wifi doesn&#8217;t play well with all the computers we have, three Ubuntu laptops and one Chromebook, but it seems particularly wonky with my computer.  I had some free time, so I started digging into the problem.

## Who watches the watchmen? It seems the kernel does&#8230;

In the _dmesg_ output, I found the following line:

> _perf interrupt took too long (2528 > 2500), lowering kernel.perf\_event\_max\_sample\_rate to 50000_

This doesn&#8217;t seem right, maybe this is the source of the problem! Let&#8217;s do some digging:

  * **Perf** is a [Linux Kernel performance monitor][1].
  * Perf uses **[Non-Maskable Interrupts][2]**. This basically means Perf can tell the cpu &#8220;Pauze whatever you&#8217;re doing now and let me do something&#8221;. This allows perf to have a &#8220;watchdog&#8221; functionality where it can monitor even the most critical processes and interrupts.

With great power comes great responsibility. Perf can hang your computer by constantly pauzing everything. To make sure this won&#8217;t happen, the kernel itself monitors perf.  When it decides perf is pauzing too long, [it tells perf to do a little bit less][3]. That&#8217;s basically what that _dmesg_ line means. The kernel told perf to do a little bit less. **Does it have anything to do with the Wifi problem? Probably not&#8230;** But at least I learned something: The kernel watches the watchmen&#8230;

Additional sources:

  * <https://superuser.com/questions/757444/perf-samples-too-long-lowering-kernel-perf-event-max-sample-rate-to>
  * <https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1246216>
  * <https://bbs.archlinux.org/viewtopic.php?id=170471>
  * <http://ubuntuforums.org/showthread.php?t=2253552>

 [1]: https://en.wikipedia.org/wiki/Perf_(Linux)
 [2]: http://x86vmm.blogspot.nl/2005/10/linux-nmis-on-intel-64-bit-hardware.html
 [3]: https://lkml.org/lkml/2013/5/29/640
