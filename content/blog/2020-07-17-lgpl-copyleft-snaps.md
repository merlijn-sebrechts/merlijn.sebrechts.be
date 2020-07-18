---
title: "Copyleft and LGPL in Snaps and Flatpaks"
layout: post
date: 2020-07-17
featured: "/2020/snap-flatpak/snap-flatpak-gpl.png"
type: "post"
---

The question often comes up of how [Snaps](https://snapcraft.io/) and [Flatpaks](https://flatpak.github.io/) influence copyleft, GPL and LGPL licenses. It is a common misconception that these new packaging formats significantly influence license compliance.

*Disclaimer: I am not a lawyer, this is not legal advice.*

**Distributing your software in a Snap has no effect on GPL copyleft and LGPL compliance.**

* It has no effect on copyleft because [containers do not trigger copyleft](https://www.gnu.org/licenses/gpl-faq.html#AggregateContainers) according to the GNU GPL FAQ *[see note]*.
* It has not effect on LGPL compliance because the user can modify the LGPL library and relink the application using `LD_LIBRARY_PATH` or by unsquashing the snap.

If your software is compliant when running outside of a snap, it will still be compliant when running inside of a snap.

## Longer explanation

Two questions arise about GPL licensing and snaps.

### When my snap includes GPL software, should everything in the snap be released as open source?

No.

When you add copyleft code to your application, you need to open source your entire application. The GPL is the most widely-used copyleft license and it uses the term *combined work* to describe an application which includes GPL code. The entire *combined work* needs to be open source, even if only a small part is GPL.

The GPL clearly makes the distinction between a "combined work" and an “aggregate”:

* If GPL code is part of a combined work, all parts of that combined work need to be open sourced.
* If GPL code is "aggregated" together with other software, the other software does not need to be open sourced.

So the question becomes "is a snap a combined work or a mere aggregation?". The [GPL FAQ](https://www.gnu.org/licenses/gpl-faq.html#AggregateContainers) is quite clear that containers, such as Snaps or Flatpaks, do not create combined works *[see note]*:

> Q: When it comes to determining whether two pieces of software form a single work, does the fact that the code is in one or more containers have any effect?
>
>A: No, the analysis of whether they are a [single work or an aggregate](https://www.gnu.org/licenses/gpl-faq.html#MereAggregation) is unchanged by the involvement of containers.

This works in both ways: if your application is a combined work outside of a container, it will be a combined work inside of a container. If your application is an aggregate outside of a container, it will be so inside of a container. See [What is the difference between an “aggregate” and other kinds of “modified versions”?](https://www.gnu.org/licenses/gpl-faq.html#MereAggregation) for more information.

### When my snapped application uses an LGPL library, should the application be released as open source?

No.

Closed source application are allowed to link to LGPL libraries as long as [a number of requirements are met](https://opensource.org/licenses/LGPL-3.0#section4). The [GNU GPL FAQ](https://www.gnu.org/licenses/gpl-faq.html#LGPLStaticVsDynamic) explains the one most relevant to snaps  *[see note]*:

> For the purpose of complying with the LGPL (any extant version: v2, v2.1 or v3):
>
>   (1) If you statically link against an LGPLed library, **you must also provide your application in an object (not necessarily source) format, so that a user has the opportunity to modify the library and relink the application.**
>
>   (2) If you dynamically link against an LGPLed library already present on the user's computer, you need not convey the library's source. On the other hand, if you yourself convey the executable LGPLed library along with your application, whether linked with statically or dynamically, you must also convey the library's sources, in one of the ways for which the LGPL provides.

When you put an application which uses dynamically linked libraries in a snap, the dynamic libraries are distributed in the same snap, but they are not linked yet. When your application starts, the libraries are dynamically linked to your application, just as they would outside of a snap.

Some might argue that a snap is statically linked because every library is in the same file. However, even in that case, your application is still compliant because the snap *provides the application in an object format so that a user has the opportunity to modify the library and relink the application*: the individual binaries and libraries of the snap are available in the filesystem at `/snap/<snap-name>/<revision/` or by unsquashing the snap manually, and users can relink applications using `LD_LIBRARY_PATH`.

## *Note*

I use the FAQ as an authoritative source because it hold legal value and the language is a lot clearer than the licenses themselves.

In license infringement cases, the *spirit of the license* holds value. This means what the creators of a license wanted to achieve with it, is important. The GNU GPL FAQ is written by the creators of the GPL license and explains what their intention was. Because of this, the FAQ can be used in court to explain what the license means.

> Note: I am a human being, and like most human beings, I make mistakes. Did you find an issue with this article? Let me know in the comments, and I'll be happy to correct it!
