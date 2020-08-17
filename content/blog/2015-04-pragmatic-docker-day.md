---
title: Pragmatic Docker Day 2015
layout: post
type: "post"
date: 2015-04-25
categories:
  - 'Linux'
featured: "/old/container-2934279_1280.jpg"
---
I got a ticket to the Pragmatic Docker Day meetup in Ghent in exchange for writing a blogpost about it. Free food, drinks & awesome talks for a whole day, who would want to miss that? _Not me!_

So here are my unstructured thoughts I gathered from the meetup:

## Docker is awesome!

What is docker? Docker encapsulates apps in their own little sandbox. Every app runs in its own container. An environment made especially so the app can run well and can't mess to much with other apps running on the same server. It's basically a VM without the overhead.

> Docker is an open platform for developers and sysadmins to build, ship, and run distributed applications

Developers write their apps and put them in a docker container. They give this container to sysadmins and they are sure everything will work once deployed on the server because the app and all its dependencies are bundled in the docker container.

## Docker is fancy!

This isn't new at all. Containers have existed on Linux for a very long time. What docker does is provide a very fancy interface and API to work with and distribute those containers. This opens container technologies to a much broader public.

Docker is becoming so popular that even Microsoft wants in on the party. Docker announced a partnership with Microsoft to bring Docker to Windows.

## Docker is production-ready*

Tomas Doran talked about how Yelp is using Docker in their Continues Integration & Continues Deployment workflow. From what I gathered, almost every service at Yelp is running in docker containers. This allows for very dynamic scaling, and makes the development &#8211; testing &#8211; production chain a lot shorter without compromising on the stability.

*Docker is still a very young and fast-moving platform. Using this in production requires a lot of knowledge and requires some caution. For a small infrastructure the benefits you get from docker might not outweigh the disadvantages from working with such early technology. However, even when you don't use Docker in production, you can still benefit from it during development and testing!

## Docker containers are not cross-platform&#8230;

The docker container still uses the host's kernel. This means that a docker container will only work on a machine that supports the same kernel functionality. If you make a docker container on Linux, and you run it on a distro with a different version of the Linux kernel, most of the time you'll be allright. However, running Linux docker containers native on a Mac or Windows won't work.

## You can still run containers on Windows?!

It's still possible to run Linux docker containers on Mac and Windows using boot2docker. This is basically a lightweight Linux VM. Docker containers run in this VM. This is great for development, but there might be an overhead because of the virtualization.

*[Image by distel2610](https://pixabay.com/photos/container-port-loading-stacked-2934279/)*
