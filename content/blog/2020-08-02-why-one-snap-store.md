---
title: "Why is there only one Snap Store?"
layout: post
date: 2020-08-02
featured: "/2020/snap-flatpak/snap-store.png"
type: "post"
---

Snap and Flatpak are the basis of two universal app stores for Linux: the [Snap store](https://snapcraft.io/store) and [Flathub](https://flathub.org/home). One question that often comes up is why there is only one Snap store. In contrast; Flatpak has a great number of repositories next to Flathub. Both Fedora and Elementary OS, for example have their own Flatpak store hosting additional apps and some app developers even host stores specific to their software.

There are two reasons why Snap was designed so each device only connects to a single store. The reason is that Canonical, the company behind Snap and Ubuntu, already tried creating a distributed store and discovered that it has significant downsides for users and app developers. Before Snap, the "official" way to get third-party software into Ubuntu were PPA's. With PPA's, each developer creates an additional repository which contains their apps. Users add the PPA's of the software they want and then install the software using the package manager. This is very similar to how Flatpak works today.

This led to a poor user experience because users have to add an additional repository before they can even _search_ software from a different vendor. Developers also found ppa's too cumbersome and wanted a better way for users to discover their software. The failure of ppa's were not from a lack of trying: Canonical designed Launchpad to make it as easy as possible for a developer to build their software and create a ppa. Although ppa's are still used by many developers, many more software is only available to download from a website.

Having a single Snap store solves this issue: users have a single place to discover new Linux applications and software developers can easily publish their software. The Flatpak project created Flathub for the same reason: having a single store which contains all apps benefits everyone.

The second advantage of designing snap for a single store is that it makes makes everything in easier to develop. Creating a distributed system is a multiplier to complexity: each feature becomes more difficult to implement. Given the downsides of distributed stores, the Snap developers decided to focus on other features instead.

## Will there ever be an alternative snap store?

Let's hope so! Although Snap is designed so that each _device_ only connects to a single store, multiple stores can still to exist! A distribution like Manjaro could very well point Snap at their own store. Manjaro chose to use the snap store hosted by Canonical because they like the advantages that gives them. In the future, however, Manjaro could switch to their own snap store if that makes sense to them.

This is exactly what the Ubuntu Touch project did; Ubuntu Touch uses "click", the precursor to Snap. They initially used the click store hosted by Canonical but they created their [their own store](https://open-store.io/) and switched to it completely when Canonical decided to give up on their attempt at breaking the smartphone duopoly.

## Is the Snap store open source?

Sadly, part of the Snap store is still closed source. Snap itself is [completely open source](https://github.com/snapcore/snapd) and many parts of the Snap store are open source like the [web-store front-end](https://github.com/canonical-web-and-design/snapcraft.io), [the automatic review tools](https://launchpad.net/review-tools), [the build service](https://launchpad.net/), the [desktop store app](https://launchpad.net/snap-store-desktop), and [many more](https://github.com/snapcore). The back-end hosting the snaps, however, is still proprietary. A few years ago Canonical created [a prototype open source snap-store backend](https://ubuntu.com/blog/howto-host-your-own-snap-store) but there wasn't much community interest in actually maintaining and running one, so the project bit-rotted and became incompatible with the current protocol used by snapd.

Open sourcing the snap store back-end would require significant changes to it, [according to Martin Wimpress of Canonical](https://www.techrepublic.com/article/why-canonical-views-the-snap-ecosystem-as-a-compelling-distribution-agnostic-solution/):

> *[because of its history,]* the Snap store now integrates with other areas of the Canonical infrastructure. So the Snap store isn't a single thing. It's not like this one piece of software that you can easily decouple from the rest of the machinery that powers the infrastructure at Canonical. So we can't just pull it apart and separate it and say, "Here you go, here's the open source Snap store.

Canonical is doubtful that this investment would be worth it because of what happened with Launchpad. Although they invested significant resources in open sourcing Launchpad, there is still only one instance of Launchpad running and they have not received any significant contributions from non-Canonical employees.

Interestingly, Canonical actually [released an open-source prototype snap-store backend](https://ubuntu.com/blog/howto-host-your-own-snap-store) a few years ago, but there was very little interest from the community in in actually maintaining and running a second Snap store, so the project bit-rotted and became incompatible with the current Snap protocol.

## Can other distro's curate packages?

Linux Mint recently made headlines by blocking users from installing snap on Linux Mint. One of the reasons they gave for this decision is that the centralization of Snap means Linux Mint cannot provide different versions of certain snaps for their users. [They explain](https://linuxmint-user-guide.readthedocs.io/en/latest/snap.html) that this is possible with APT:

> Thanks to the way APT works, if a bug isn’t fixed upstream, Debian can fix it with a patch. If Debian doesn’t, Ubuntu can. If Ubuntu doesn’t Linux Mint can. If Linux Mint doesn’t, anyone can, and not only can they fix it, they can distribute it with a PPA.

It's understandable that a distribution wants some level of control over what packages their users get and this should definitely be possible with Snap by using ["Brand stores"](https://core.docs.ubuntu.com/en/build-store/). These are special copies of the store where you can select exactly what packages are available and provide your own modified packages. The European Space Agency, for example, has [a brand store specific to satcom research](https://sdrsatcom.snapcraft.io/). These brand stores can be used by other distributions to have more control over what snaps their users can install. The downside of Brand stores is that you're still using the infrastructure of Canonical.

It's understandable that some distributions might shy away from using Canonical infrastructure but Linux Mint is no stranger to this; they heavily relied on Canonical infrastructure when they first started out, only using their own repositories for the packages that they patched. This is very common for Ubuntu derivatives. Another option would be to create their own Snap store with similar functionality and [Canonical's previous behavior](https://ubuntu.com/blog/howto-host-your-own-snap-store) suggests they would be open to helping that effort.

## My thoughts about this

Having a single snap store which has closed source parts is very controversial in some parts of the Linux community. The decision to have only a single store per device seems reasonable to me: it has clear advantages both to users and developers. That said, I am happy that there is competition and I think the [hybrid model](https://blog.elementary.io/elementary-appcenter-flatpak/) that Elementary OS is doing is really interesting. I also hope that someday the community creates an alternative snap store similar to what F-Droid is doing.

I do not like the fact that the snap store backend is proprietary because it is becoming such a core part of Ubuntu. I don't think there is anything wrong with Canonical producing closed-source add-ons on top of Ubuntu in an "Open Core" fashion. GitLab does this really well and we have an amazing open source GitHub alternative because of it. There is nothing wrong with Canonical trying to make money; Ubuntu would not be here without them. Linux is great because of all the companies surrounding it.

What I do take issue with is that you currently cannot use Snap for its intended purpose without this proprietary back-end. Ironically, Ubuntu's former community member, Jono Bacon made it very clear [in a recent video](https://www.youtube.com/watch?v=o-OOxOS8oDs) that the proprietary parts of an Open Core project need to be _optional_. Having proprietary enterprise features such as the [Snap Store Proxy](https://docs.ubuntu.com/snap-store-proxy/en/) is fine, but the core should remain open source.

That said, I'm pragmatic about this. DockerHub and GitHub are insanely popular and their back-end is _completely_ proprietary. Moreover, Canonical is much more receptive to community pressure than Docker inc or GitHub so we are in a much better position to steer them towards doing "the right thing". Finally, if things don't work out in the end, we can always build our own back-end.

> Note: I am a human being, and like most human beings, I make mistakes. Did you find an issue with this article? Let me know in the comments, and I'll be happy to correct it!
