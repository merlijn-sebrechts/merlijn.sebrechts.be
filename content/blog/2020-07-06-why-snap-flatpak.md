---
title: "Why Linux desktop apps need containers"
layout: post
date: 2020-07-06
featured: "/2020/snap-flatpak/packaging.jpg"
type: "post"
---

> Note: This article talks about Snaps and Flatpaks. This is the software behind two universal Linux app stores: the [Snap Store](https://snapcraft.io/store) and [Flathub](https://flathub.org). If you are not familiar with these, please first read [The future of Linux desktop application delivery is Flatpak and Snap](https://www.zdnet.com/article/the-future-of-linux-desktop-application-delivery-is-flatpak-and-snap/).

The [Snap Store](https://snapcraft.io/store) and [Flathub](https://flathub.org) are two universal app stores for Linux. They are very different from how traditional software distribution works. As is always the case with new software, the question "why do we need this?" often arises. "Including software in distribution repositories has worked for so long, so why do we need to change it?"

There are many reasons, but this post will discuss two:

* We need it for software that is not developed at the same speed as distributions.
* We need it for software that is too "messy" for distributions.

Let's look at some examples based on snap packages I'm maintaining.

## Apps which release too quickly

Distributions such as Ubuntu and Fedora release a regular version about twice a year. The software available to that version changes very little in between releases, so users often have to wait six months to get major updates to an app. To make matters worse, users of the Ubuntu LTS version have to wait *two years* for major updates.

In contrast, the Arduino IDE sometimes releases a new version after just one month. New versions of the Arduino IDE add support for new hardware and software, so it's important for users to get the latest version as soon as possible. The [Arduino IDE Snap](https://snapcraft.io/arduino) updates immediately when a new version is released because the app and its dependencies are completely isolated from the OS itself.

## Apps which release too slowly

"Scratch for Arduino (S4A)" gives kids an introduction into robotics by allowing them to program robots using scratch. Although this application is still used for a lot for STEM introductions, it uses very old libraries, making it very hard to install on a recent Linux distribution. The application is developed by a group of educators as a side project and they do not have the resources to update S4A every six months so it works with the newest Ubuntu libraries. The snap of [Scratch for Arduino](https://snapcraft.io/s4a) solves this issue by including set of older 32-bit libraries into the snap. These libraries still receive security fixes, but it is very hard to install them on newer Ubuntu releases. Thanks to the snap container, this piece of software can still be used on newer Ubuntu releases.

## Apps which are too messy

The [Bridge Designer](https://bridgedesigner.org/) is used in middle- and high-schools to give kids a realistic introduction to engineering. The kids get to build, design and test a bridge, similar to how actual engineers do it. The problem with this application is that it is actually a Windows application. Windows software has no place in the Debian repositories. It is however possible to run the software on Linux using a specially crafted Wine environment, which is exactly what the [Bridge Designer snap](https://snapcraft.io/bridge-designer) does. Thanks to this snap, users can now install Bridge Designer on Linux without having to mess with Wine.

## Myth: it's only for closed source software

All these applications are open source. It is a common myth that these kind of issues only happen in closed source software, but this is clearly not the case. Being open source does not mean a project has the resources to be ported to Linux and it does not mean the developers have enough time to update their software every six months.

## Extra 1: Arduino is also too messy

Next to the "speed" issue, the Arduino IDE has not been updated in Debian and Ubuntu since 2015 because of [licensing issues](https://github.com/arduino/Arduino/pull/2703). Arduino source code uses a number of different open source licenses and according to Debian rules, it is not clear enough which files use which license. Although I think this issue should be fixed, Ubuntu users still need the Arduino IDE in the meantime. Because the snap is completely self-contained and does not affect any other part of the OS, it does not need to follow the strict rules of Debian.

## Extra 2: Alternatives

Since these issues are universal, people have come up with other very smart solutions.

* [AppImage](https://appimage.org/) solves these issues by creating a "fat binary" for each application. Each binary contains all the dependencies an application needs. One advantage is that an AppImage runs by itself; you do not need an additional package manager to run an app.
* [Nix](https://nixos.org/) is a package manager which allows multiple installed apps to use different versions of the same libraries. One advantage over Snaps and Flatpaks is that applications generally use less space because shared libraries are not actually duplicated.
* "Rolling" distributions such as [Manjaro](https://manjaro.org/) do not release every X months, but continuously releases updates at the same pace of the actual developers of the software. This solves the "too fast" apps, but not the other issues. This is one of the reasons Manjaro also includes Snapd and Flatpak by default.
