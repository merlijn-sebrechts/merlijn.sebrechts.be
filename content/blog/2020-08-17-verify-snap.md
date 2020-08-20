---
title: "How to verify the source of a Snap package"
layout: post
type: "post"
date: 2020-08-16
categories:
  - 'Linux'
tags:
  - 'Snap'
---

Many [Snap packages](https://snapcraft.io/) contain two files which allow users to verify what sources were used to build the package.

* `snap/snapcraft.yaml` is the "source" of the package. This file was used by [`snapcraft`](https://snapcraft.io/docs/snapcraft-overview) to build the package.
* `snap/manifest.yaml` is a "recording" of the build of that package. It is similar to the first file, but it includes a lot more information to pinpoint what exact sources were being used. It records the exact package versions of dependencies, the git commit of all source repositories, checksums of any downloaded binary and more.

The manifest is used by the Snap Store to check if Snap packages contain libraries with security vulnerabilities. If this is the case, the publisher gets an email asking them to rebuild the package.

Both these files are added by the `snapcraft` build tool when the environment variable `SNAPCRAFT_BUILD_INFO` is set during the build. This is automatically enabled for all snaps built by snapcraft.io, Launchpad and on GitHub.

## What do the manifests contain?

Let's look at Canonical's Chromium snap as an example.

In `snap/snapcraft.yaml`, `source` explains what repository is used to build the package and `stage-packages` describe what dependencies are included in the snap.

```yaml
 desktop-gtk3:
    source: https://github.com/ubuntu/snapcraft-desktop-helpers.git
    source-subdir: gtk
    stage-packages:
      - libxkbcommon0
      - ttf-ubuntu-font-family
      - shared-mime-info
...
```

In `snap/manifest.yaml`, `source-commit` is added to narrow down what exact source was used for this package and `stage-packages` include the exact version of each dependency.

```yaml
 desktop-gtk3:
    source: https://github.com/ubuntu/snapcraft-desktop-helpers.git
    source-commit: 622e2aa7a840b3a7dbb6ea4d432d687d5cc2e8ef
    source-subdir: gtk
    stage-packages:
    - libxkbcommon0=0.8.2-1~ubuntu18.04.1
    - ttf-ubuntu-font-family=1:0.83-2
    - shared-mime-info=1.9-2
...
```

Finally, for snaps built on Launchpad and GitHub, `snap/manifest.yaml` also contains a URL to the build log.

```yaml
image-info:
  build-request-id: lp-58361925
  build-request-timestamp: '2020-08-05T11:55:18Z'
  build_url: https://launchpad.net/~osomon/+snap/chromium-snap-firstrun-notice/+build/1071421
```

## How do I access these files?

Currently, you need to download the snaps before you can access the manifest.

* If you don't have the Snap installed, run `snap download snap-name`, which will download the snap to the current directory. You can then open the snap with any archive manager to look at the files.
* If you have the snap installed, you can find them in `/snap/snap-name/current/snap/`.

## Can the manifests be doctored?

Yes; a malicious publisher can change the contents of these files. If the snap was built on Launchpad or GitHub, however, you can verify if the manifest was changed since the package was built. This is the process to verify a snap build from Launchpad:

1. Download the snap and look for the `build_url` in `snap/manifest.yaml`.
2. Surf to the URL and download the snap in "Built files".
3. Calculate the checksum of both snaps and see if they match.

If the checksums match, you know the manifest was not changed since the package was built. On Launchpad, you can also see which machine the package was built on, the entire build log and the source of that build.

> Note: This process requires you to trust the information in Launchpad is correct. This is the same infrastructure that builds the regular Ubuntu packages and hosts their source code, however, so Ubuntu and all of its derivatives already depend on this information being correct.

## Can I trust any package built on Launchpad?

No! It is still very important to trust the _publisher_ of a package themselves. Because the publisher controls the entire source code of the application, it is impossible to stop them from including malicious code. Even if that code is built on Launchpad.

> Note: for this reason, I'm not convinced that it's useful to force publishers to include manifests and/or use Launchpad. It would only give users a false sense of security.

Snap is specifically designed to let developers publish their apps directly to users without a middleman. This also means that users should only install software from developers they trust. The Snap sandbox helps to reduce the damage a malicious or broken snap can do, but it does not completely protect you from harm.

## What if the Snap was built on GitHub?

As James Henstridge pointed out in the comments, if the Snap was built on GitHub using the official actions, you can also verify the manifest. The process is a little bit more complicated, though.

1. Download the snap and look for the `build_url` in `snap/manifest.yaml`.
2. Surf to the URL go to the log of the "build" step and look at the `Run snapcore/action-publish@v1` part for the "revision" number.

   ```txt
   Revision 13 of 'asciidoc-link-check' created.
   Track    Arch    Channel    Version    Revision
   latest   amd64   stable     1.0.14     13
                    candidate  ↑          ↑
                    beta       ↑          ↑
                    edge       1.0.13     10
   ```

3. Check the following things:

   * The name of the snap you just downloaded is the same as in this log.
   * The revision of the snap you just downloaded is the same as in this log.
   * The workflow uses `snapcore/action-build` and `snapcore/action-publish` to build and publish the Snap.

   If these three are true, then the manifest was not changed since the build because publishers cannot modify the Snap of a revision after it was uploaded. Every change creates a new revision number.

> Note: This process requires you to trust that the information in the Snap Store and on GitHub is correct.

## Areas of improvement

If you're interested in transparency, trust and reproducibility of snaps, there are many areas you can work on to further improve this. From the top of my head, these are some of the things that can improve:

* To see the manifest, users need to download the snap and manually look through the files. It would be very useful if the [Snap Store web frontend](https://github.com/canonical-web-and-design/snapcraft.io) and the [`snap` CLI command](https://github.com/snapcore/snapd) could show you the manifest and the data in it.
* Although the manifest records everything used to build the package, you can't yet use this recording to reproduce the package. The [`snapcraft`](https://github.com/snapcore/snapcraft) build tool needs to be modified so it can rebuild a snap from the `manifest.yaml`. You won't be starting from scratch though, as `snapcraft` already supports many of the fields in the manifest.
* The manifest currently does not contain the source url of the repository which contains the `snapcraft.yaml` file itself. You can use Launchpad to find this repository, but it would be better to include this repository in the manifest itself.
* As far as I know, Launchpad and GitHub are currently the only build services for Snaps which include a link to the build log. It would be useful for others such as the [KDE Neon build service](https://build.neon.kde.org) to do the same thing.

> Note: I am a human being, and like most human beings, I make mistakes. Did you find an issue with this article? Let me know in the comments, and I'll be happy to correct it!
