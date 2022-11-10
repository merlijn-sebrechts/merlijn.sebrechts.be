---
title: "You can now completely disable automatic snap updates!"
layout: post
type: "post"
date: 2022-11-10
categories:
  - 'Linux'
tags:
  - 'Snap'
---

During the Ubuntu Summit, a long-awaited feature was quietly released for preview: [You can now completely turn off automatic updates of snaps](https://snapcraft.io/docs/keeping-snaps-up-to-date#heading--hold).

> "The `snap refresh --hold` command holds, or postpones, snap updates for individual snaps, or for all snaps on the system, either indefinitely or for a specified period of time."
>
> _(currently only available in `edge` channel of `snapd`)_

This might sound like an obvious feature to many people, but it's a continental shift in philosophy for the Snap developers.

Snaps allow users to easily install Linux applications. By default, snaps automatically update to the newest version. Snapd, the service that manages snaps, checks for updates four times in a day. Although there are many ways to control when and how often updates are installed, it was **not possible to completely turn off automatic updates.**

This was a conscious choice by the developers. Outdated and insecure Linux system are a massive problem because they are weaponised into botnets that [attack services](https://krebsonsecurity.com/2021/09/krebsonsecurity-hit-by-huge-new-iot-botnet-meris/) and [spread malware](https://en.wikipedia.org/wiki/Mirai_(malware)). In an attempt to help solve this issue, the Snap developers decided to simply make it impossible to turn off automatic updates. When Snap was initially released in 2014, automatic updates were so new to the Linux ecosystem that the developers feared every list of "10 things to do after installing `<distro>`" would include "turn off automatic updates", making the issue of insecure Linux devices even larger.

Nowadays, however, automatic updates have become commonplace. Even Ubuntu server has been automatically installing security updates since late 2016! Over the years, the snap update mechanism has been continiously refined to ensure updates don't break things and to allow updates to happen at a convenient time. As a result, adding the functionality to disable updates will probably not result in a new wave of insecure devices. Moreover, as Snap matures and enters large enterprises with IT teams dedicated to manually updating software, adding this feature is a logical next step to give IT teams the control and predictability they have come to expect from Linux systems.
