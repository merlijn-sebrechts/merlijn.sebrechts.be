---
title: "Lightweight Kubernetes Controllers with WebAssembly"
layout: post
type: "post"
date: 2022-09-05
categories:
  - 'Linux'
tags:
  - 'Kubernetes'
  - 'WebAssembly
  - 'Edge'
featured: "/2022/address-book-example.png"
---





Kubernetes uses a lot of RAM. This is an issue on edge devices, which typically don't have a lot of it. Kubernetes controllers and operators are a big contributor to this. Running controllers on-demand as WebAssembly modules might help solve this issue.

## Kubernetes Controllers and Operators

More and more applications on Kubernetes are managed using operators and Custom Resources. These add additional functionality to the Kubernetes API. For example, the ArgoCD operators provide additional resources to create CI/CD pipelines and Rook allows you to manage storage clusters such as Ceph.

The issue with operators is that they keep running even when there is nothing to do. Simply adding the ArgoCD functionality to a Kubernetes cluster will eat up RAM, even when you're not actively using it.

## WebAssembly



## 



This paper presents a WebAssembly-based framework for running lightweight controllers on-demand, only when they are needed. This framework extends the WebAssembly System Interface (WASI), in order to run Kubernetes controllers as lightweight Wasm modules. The framework runs these Wasm controllers in a modified version of Wasmtime, the reference WebAssembly (Wasm) runtime, that swaps idle controllers to disk and activates them when needed. A thorough evaluation shows this framework achieves a 64% memory reduction compared to traditional container-based controller frameworks. 

