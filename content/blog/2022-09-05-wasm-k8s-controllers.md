---
title: "Lightweight Kubernetes Operators with WebAssembly"
layout: post
type: "post"
date: 2022-09-28
categories:
  - 'Linux'
tags:
  - 'Kubernetes'
  - 'WebAssembly'
  - 'Edge'
---


We created [a prototype that runs Kubernetes operators in WebAssembly (wasm)](https://github.com/IBCNServices/wasm-operator) and suspends them to disk when they are not used.

## Why

Developers want to use Kubernetes in the edge, but it uses too much memory for most devices. Running k8s operators in wasm greatly reduces their memory overhead and allows us to start and stop them dynamically. This way, they only run when there is actually something to do.

## Kubernetes Operators

Operators are an important part of the Kubernetes control plane. They add additional functionality to Kubernetes using Custom Resources. The ArgoCD operators, for example, provide additional resources to create CI/CD pipelines, and Rook allows you to manage storage clusters such as Ceph.

The issue with operators is that they keep running even when there is nothing to do. Simply adding the ArgoCD functionality to a Kubernetes cluster will eat up RAM, even when you're not actively using it.

## WebAssembly + WASI

WebAssembly (wasm) is a binary format to run applications in lightweight virtual machines. Many compilers support `wasm` as a target next to `arm` and `x86_64`. The WebAssembly System Interface (WASI) is a standardized API for wasm apps to talk to the outside world. They're the "System Calls" of the WebAssembly world.

Combining these two gives you a very lightweight but very secure way to isolate applications. Each wasm app runs in their own sandbox and the runtime decides what external resources it can access. Moreover, wasm apps start up lightning fast!

## Kubernetes Operators in WebAssembly

In 2020, Markus Thömmes and Francesco Guardiani introduced the idea of running Kubernetes controllers in WebAssembly:

> *Today I’m going to introduce you an idea Markus Thömmes and I had to package, deploy and operate Kubernetes controllers in a modern and efficient way that may have a fundamental impact on the Kubernetes ecosystem.* - [Kubernetes Controllers - A new hope](https://slinkydeveloper.com/Kubernetes-controllers-A-New-Hope/)

Their prototype didn't support unloading idle controllers, however, and hasn't seen any activity in over 2 years. So, to continue this dream, we ported their prototype to [wasmtime](https://wasmtime.dev/), and added the functionality to suspend idle operators to disk.

## Performance

We did a bunch of extensive performance tests to see whether this actually reduces the memory footprint of controllers. The results are published in [our paper at IEEE CloudNet 2022](https://arxiv.org/abs/2209.01077). Two findings from the paper:

* 100 Rust operators running in our wasm runtime use **68% less memory** than if they run in containerd.

  <img src="/img/2022/wasi-operators-perf-containment.png" alt="wasi-operators-perf-containment" width="500"/>


* Moreover, they use an additional **50% less memory** when swapped to disk during idling.

  <img src="/img/2022/wasi-operators-perf-unloading.png" alt="wasi-operators-perf-unloading" width="500"/>

## Next steps

Right now, [this](https://github.com/IBCNServices/wasm-operator) is a very rough prototype which shows the potential of the approach. It's definitely not ready for any serious usage, though, so our first step is to get it into a more usable state. There are also a couple of new features planned:

* Predictive unloading/swapping to disk. Right now, a controller gets swapped to disk immediately after finishing a control loop. This creates a lot of overhead, however, for controllers which have more changes to process. We want to be smarter about when to unload controllers.
* Go support. Right now, we only support controllers written in Rust. Go is the default language for controllers, however, so we want to take a look at adding support for those controllers in the framework.
* Better integration in lightweight Kubernetes distributions. This framework would be a great addition to tiny k8s distributions such as the [FLEDGE project](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&ved=2ahUKEwjtjKX46bf6AhWlgf0HHa1VDk0QFnoECCEQAQ&url=https%3A%2F%2Fbiblio.ugent.be%2Fpublication%2F8635821%2Ffile%2F8635824.pdf&usg=AOvVaw3k5JONOhwhwNssosrX4Tpr), created by a colleague of mine.

## More information

* [The runtime](https://github.com/IBCNServices/wasm-operator) and [the modifications to kube-rs](https://github.com/IBCNServices/kube-rs) are available on Github.
* We published [a preprint of the paper introducing this prototype at IEEE CloudNet 2022](https://arxiv.org/abs/2209.01077).
* For even more information, read [Tim Ramlot's master's thesis about this framework](https://lib.ugent.be/fulltxt/RUG01/003/063/694/RUG01-003063694_2022_0001_AC.pdf).

## Acknowledgements

A great amount of thanks goes to Tim Ramlot, who developed the software as part of his master's thesis, and Markus Thömmes and Francesco Guardiani for the initial idea and original Proof of Concept.
