---
title: "What is the Apache 2.0 LLVM Exception?"
layout: post
type: "post"
date: 2024-03-04
categories:
  - 'Linux'
tags:
  - 'Copyright'  
featured: "/2024/asf-logo.png"
---

Some open source projects use the Apache 2.0 license ["with LLVM Exception"](https://spdx.org/licenses/LLVM-exception.html) `SPDX: "Apache-2.0 WITH LLVM-exception"`). So what is the "LLVM exception" exactly, and why do some projects add it to their license?

Heather Meeker, a notable open source attorney, created this when she was hired by the LLVM foundation to solve two issues with the Apache 2.0 license.

## It solves the compiler runtime problem

The first issue with the Apache 2.0 license is specific to compilers. When you compile your application, the compiler will inject part of their own code into the resulting binary. The problem is that, if your application uses Apache 2.0-licensed code, you need to let your users know about that. For LLVM, this would mean that every program compiled by Clang would have to say this to their users.

As a result, the LLVM Exception adds a clause that says you don't have to notify your users if your application ends up containing some of the compiler's code.

```txt
As an exception, if, as a result of your compiling your source code, portions
of this Software are embedded into an Object form of such source code, you
may redistribute such embedded portions in such Object form without complying
with the conditions of Sections 4(a), 4(b) and 4(d) of the License.
```

## It solves GPLv2 incompatibility

The **Apache 2.0 license is not compatible with GPLv2 because it has an additional restriction**. The Apache 2.0 license says you are not allowed to start a patent lawsuit about the code. Otherwise, you will loose the patent grant the Apache 2.0 license provides you. This is incompatible with the GPLv2, because it explicitly forbids imposing additional restrictions. Even if that restriction is intended to protect users.

This incompatibility is accidental, though. The GNU project has made it clear they agree with the patent restriction, which is why they explicitly fixed the incompatibility in the later version of their GPL license. However, a lot of code still uses the older GPLv2 license and will not be relicensed any time soon.

So the second reason for the LLVM Exception is to solve this incompatibility. It explicitly makes Apache 2.0 compatible with the GPLv2.

```txt
In addition, if you combine or link compiled forms of this Software with
software that is licensed under the GPLv2 ("Combined Software") and if a
court of competent jurisdiction determines that the patent provision (Section
3), the indemnity provision (Section 9) or other Section of the License
conflicts with the conditions of the GPLv2, you may retroactively and
prospectively choose to deem waived or otherwise exclude such Section(s) of
the License, but only in their entirety and only with respect to the Combined
Software.
```

## Sources

* [LLVM Relicensing Effort](https://foundation.llvm.org/docs/relicensing/)
* [LLVM contemplates relicensing](https://lwn.net/Articles/701155/)
* [GPLv2 Combination Exception for the Apache 2 License](https://blog.gerv.net/2016/09/gplv2-combination-exception-for-the-apache-2-license/)
* [GNU comments about Apache 2.0 license](https://www.gnu.org/licenses/license-list.html#apache2)
