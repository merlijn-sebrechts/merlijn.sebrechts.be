---
title: "Open Google Drive and Google Calendar as a specific user"
layout: post
type: "post"
date: 2022-09-10
categories:
  - 'PhD'
tags:
  - 'Google Drive'
  - 'Google Calendar
  - 'Gmail'
---

Quick tip: did you know you can open Google Drive, Google Calendar and more as a specific user?

Just add `?authuser=` and your URL encoded email address behind the address. For example,

* `https://drive.google.com/?authuser=merlijn.sebrechts%40gmail.com` opens Google Drive as user `merlijn.sebrechts@gmail.com`.
* `https://calendar.google.com/?authuser=merlijn.sebrechts%40ugent.be` opens Google Calendar as user `merlijn.sebrechts@ugent.be`.

This works with almost every google website, including gmail.

> Note: you can use [an online tool to URL encode](https://www.urlencoder.org/) your email address.
