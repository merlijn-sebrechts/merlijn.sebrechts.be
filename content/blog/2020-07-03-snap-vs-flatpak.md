---
title: "A fundamental difference between Snap and Flatpak"
layout: post
date: 2020-07-03
featured: "/2020/snap-flatpak/snap-flatpak-banner.png"
type: "post"
---

Snaps and Flatpaks are often compared to each other because they both make it super easy for Linux users to *get the latest versions of desktop applications*. If a Linux user wants to install the latest version of apps like Slack, Krita or Blender, either tool will work just fine. There is one fundamental difference between Snaps and Flatpaks, however. While both are systems for distributing Linux apps, snap is also a tool *to build Linux Distributions*.

> Note: This article talks about Snaps and Flatpaks. This is the software behind two universal Linux app stores: the [Snap Store](https://snapcraft.io/store) and [Flathub](https://flathub.org). If you are not familiar with these, please first read [The future of Linux desktop application delivery is Flatpak and Snap](https://www.zdnet.com/article/the-future-of-linux-desktop-application-delivery-is-flatpak-and-snap/).

Flatpak is designed to install and update "apps"; user-facing software such as video editors, chat programs and more. Your operating system, however, contains a lot more software than apps. It contains a kernel, printer drivers, audio subsystems and more. While Flatpak assumes this software is installed using a traditional package manager, snaps can install anything. These are some examples.

* There is current work ongoing to put *the entire Linux printing stack* inside of a snap. This has the advantage that printer drivers can be updated independently from the operating system. Once this work is complete, every single Ubuntu version will be able to use the latest printer drivers. Trying to use new printers on old Linux distributions can be very frustrating, and installing newer printer drivers can be risky. Having the printing stack in a snap will solve this issue.
* A few years ago, Ubuntu drastically changed the system theme. When this initiative started, we wanted an easy way to make the latest updates of the theme available to users immediately. Normally, a system theme is shipped together with the distro, so users do not get get theme updates after the distro releases. For "CommuniTheme", however, we fixed this by putting the _system_ theme inside of a snap. Because of this, users got updates to their theme every day, instead of every 6 months. This is again not something Flatpak was built for. Flatpak applications can update their own theme, but it is not possible to ship the system theme as a Flatpak. This is because Flatpak was designed for distributing apps, not building an entire Linux distribution.
* Even the Linux kernel, the most fundamental part of a Linux distribution, can be put in a snap. This is used a lot for IoT devices such as routers and satellites. The impact of a broken kernel update is catastrophic if you require a rocket in order to plug a USB stick into the device. Snaps allow these devices to safely update their kernel and automatically roll back if something goes wrong during the process.

As a result, it's possible to build an entire operating system using only snaps, which is exactly what [Ubuntu Core](https://ubuntu.com/core) is.

Just to be clear, this is *not* meant to be criticism of Flatpak. Flatpak was designed to give developers an easy way to bring their apps directly to users, and it does that job *very well*. The focussed approach of Flatpak even has a big advantage: it's a lot easier for a distribution to integrate with Flatpak because it does a lot less. The tradeoff is that it only provides app distribution; it doesn't solve the issues of distributing entire operating systems. [Fedora Silverblue](https://silverblue.fedoraproject.org/), for example, creates an immutable desktop operating system by using Flatpak for app distribution and [OSTree](https://ostree.readthedocs.io/en/latest/) for distributing the OS itself.

> Note: I am a human being, and like most human beings, I make mistakes. Did you find an issue with this article? Let me know in the comments, and I'll be happy to correct it!
