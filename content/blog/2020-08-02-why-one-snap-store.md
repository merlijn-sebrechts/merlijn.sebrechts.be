---
title: "Why is there only one Snap Store?"
layout: post
date: 2020-08-02
featured: "/2020/snap-flatpak/snap-store.png"
type: "post"
---

Snap and Flatpak are the basis of two universal app stores for Linux: the [Snap Store](https://snapcraft.io/store) and [Flathub](https://flathub.org/home). Interestingly, Flatpak has multiple repositories: Flathub is the main one but both Fedora and Elementary OS also host their own store. In contrast; there is only one Snap store. Why is that?

> Note: for an introduction into Flatpak and Snap, please read [The future of Linux desktop application delivery is Flatpak and Snap](https://www.zdnet.com/article/the-future-of-linux-desktop-application-delivery-is-flatpak-and-snap/).

Snap is designed so each device only connects to a single store for three reasons:

* users can easily discover new applications,
* developers can easily publish their apps,
* and developing Snap itself is easier.

Canonical, the company behind Snap and Ubuntu, already tried the distributed approach and discovered its downsides. Before Snap, "Personal Package Archives" (PPAs) were the recommended way to get third-party software to Ubuntu users. The idea of these is that each developer creates a tiny repository which includes their app. Users get new software by adding the PPA and installing the software using their package manager. This is very similar to how Flatpak supports multiple "stores".

On Android and iOS, users often find new software by opening the app store and searching for what they need. This is not possible with PPAs because the software in a PPA only shows up in the Ubuntu app store _after_ a user adds it. Snap solves this by having a single repository with all available apps. Users discover new software straight from the app store instead of having to search the internet.

Many developers also find creating and maintaining a repository too cumbersome. Canonical tried to make this as easy as possible for PPAs with Launchpad taking care of building and hosting the apps. Nevertheless, the process is inherently more complicated than uploading your app to a store. Although PPAs are still used by many developers, even more software is only available to download from a website.

These issues are not unknown to the Flatpak project, which is [why Flathub was created](https://www.youtube.com/watch?v=Hga20qlyknw): having a single store which contains all apps benefits everyone.

Given the downsides of the distributed approach, Canonical decided to invest engineering resources in other parts of Snap instead. Creating a distributed system is a multiplier to complexity; each feature becomes harder to implement. That said, the Snap developers made it clear in the past that if anyone is interested in implementing this feature in Snap, they can definitely do so.

## Will there ever be an alternative Snap store?

Let's hope so! Although Snap is designed so that each _device_ only connects to a single store, multiple stores can still exist! A distribution like Manjaro could very well point Snap at their own store. Manjaro chose to use the Snap store hosted by Canonical because they like the advantages that gives them. In the future, however, Manjaro could switch to their own Snap store if that makes sense to them.

This is exactly what the [Ubuntu Touch](https://ubuntu-touch.io/) project did. Ubuntu Touch is a smartphone OS which uses "click", the precursor to Snap. They initially used the click store hosted by Canonical but they created their [their own store](https://open-store.io/) and switched to it completely when Canonical gave up on their attempt to break the smartphone duopoly.

## Is the Snap Store open source?

Sadly, part of the Snap store is still closed source. Snap itself is [completely open source](https://github.com/snapcore/snapd) and many parts of the Snap store are open source like the [web-store front-end](https://github.com/canonical-web-and-design/snapcraft.io), [the automatic review tools](https://launchpad.net/review-tools), [the build service](https://launchpad.net/), the [desktop store app](https://launchpad.net/snap-store-desktop), and [many more](https://github.com/snapcore). The back-end hosting the snaps, however, is still proprietary.

Open sourcing the Snap store back-end would require significant changes to it, [according to Martin Wimpress of Canonical](https://www.techrepublic.com/article/why-canonical-views-the-snap-ecosystem-as-a-compelling-distribution-agnostic-solution/):

> *[because of its history,]* the Snap store now integrates with other areas of the Canonical infrastructure. So the Snap store isn't a single thing. It's not like this one piece of software that you can easily decouple from the rest of the machinery that powers the infrastructure at Canonical. So we can't just pull it apart and separate it and say, "Here you go, here's the open source Snap store.

Canonical is doubtful that this investment would be worth it because of what happened with Launchpad. Although they invested significant resources in open sourcing Launchpad, there is still only one instance of Launchpad running and they have not received any significant contributions from non-Canonical employees.

Interestingly, Canonical actually [released an open-source prototype Snap store backend](https://ubuntu.com/blog/howto-host-your-own-snap-store) a few years ago, but there was very little interest from the community in in actually maintaining and running a second Snap store, so the project bit-rotted and became incompatible with the current Snap protocol.

## Can other distros curate packages?

Linux Mint recently made headlines by blocking users from installing Snap on Linux Mint. One of the reasons they gave for this decision is that the centralization of Snap means Linux Mint cannot provide different versions of certain snaps for their users. [They explain](https://linuxmint-user-guide.readthedocs.io/en/latest/snap.html) that this is possible with APT:

> Thanks to the way APT works, if a bug isn’t fixed upstream, Debian can fix it with a patch. If Debian doesn’t, Ubuntu can. If Ubuntu doesn’t Linux Mint can. If Linux Mint doesn’t, anyone can, and not only can they fix it, they can distribute it with a PPA.

It's understandable that a distribution wants some level of control over what packages their users get but this is already possible with the Snap store!

["Brand stores"](https://core.docs.ubuntu.com/en/build-store/) are special copies of the Snap store where admins select which packages from the main store are available and which additional or modified packages are included. The European Space Agency, for example, has [a brand store specific to satcom research](https://sdrsatcom.snapcraft.io/). The downside of Brand stores is that you're still using the infrastructure of Canonical, but Linux Mint is no stranger to this. Like most Ubuntu derivatives, they heavily relied on Canonical infrastructure when they first started out, even using the regular Ubuntu repositories and mirrors.

Another option would be to create their own Snap store with similar functionality and [Canonical's previous behavior](https://ubuntu.com/blog/howto-host-your-own-snap-store) suggests they would be open to helping that effort.

## My thoughts about this

Having a single Snap store which has closed source parts is very controversial in some parts of the Linux community. The decision to have only a single store per device seems reasonable to me: it has clear advantages both to users and developers. Still, I am happy Flatpak exists as a competing project with a decentralized design and Elementary OS's [hybrid approach](https://blog.elementary.io/elementary-appcenter-flatpak/) does a great job of taking advantage of it. I hope that someday the community creates an alternative Snap store similar to what F-Droid is doing.

I do not like the fact that the Snap store backend is proprietary because it is becoming such a core part of Ubuntu. I don't think there is anything wrong with Canonical producing closed-source add-ons on top of Ubuntu in an "Open Core" fashion. GitLab does this really well and we have an amazing open source GitHub alternative because of it. There is nothing wrong with Canonical trying to make money; Ubuntu would not be here without them. Linux is great because of all the companies surrounding it.

What I do take issue with is that you currently cannot use Snap for its intended purpose without this proprietary back-end. Ironically, Ubuntu's former community member, Jono Bacon, made it very clear [in a recent video](https://www.youtube.com/watch?v=o-OOxOS8oDs) that the proprietary parts of an Open Core project need to be _optional_. Having paid enterprise features such as the [Snap Store Proxy](https://docs.ubuntu.com/snap-store-proxy/en/) is fine, for example, because Snap is still completely functional without it.

That said, I'm pragmatic about the proprietary back-end. DockerHub and GitHub are insanely popular and they are _completely_ proprietary. Moreover, Canonical is much more receptive to community pressure than Docker inc or GitHub so we are in a much better position to steer them towards doing "the right thing". There are [many reasons](./2020-07-03-snap-vs-flatpak.md) to like Snap, and if things really don't work out with Canonical, we can always build our own back-end.

> Note: I am a human being, and like most human beings, I make mistakes. Did you find an issue with this article? Let me know in the comments, and I'll be happy to correct it!
