---
title: What's up with CRI-O, Kata Containers and Podman?
layout: post
date: 2020-01-14
categories:
  - 'Ubuntu & Linux'
type: "post"
featured: "/2020/container-runtimes-banner.jpg"
#featured: "/2020/container-ship-banner.jpg"
---

The container ecosystem is moving rapidly. A lot happened in 2019! It seems the container ecosystem has arrived at [the "consolidation" stage of the hype cycle](https://www.gartner.com/en/documents/3887767/understanding-gartner-s-hype-cycles):

* Docker Inc. sold off its enterprise business and had a bunch of restructuring. They **shelved Docker Swarm** saying "The primary orchestrator going forward is Kubernetes."
* Twitter joined Spotify in [**moving away from Mesos**-based container orchestration to Kubernetes](https://www.alibabacloud.com/blog/twitter-announced-switch-from-mesos-to-kubernetes_595156). This was a huge blow to Mesos given Twitter was its original developer.
* The Cloud Native Compute Foundation [**archived rkt**](https://www.cncf.io/blog/2019/08/16/cncf-archives-the-rkt-project/).
* Canonical doubled down on Kubernetes with MicroKubernetes for local development and Charmed Kubernetes for production setups and [introduced **support for Kata Containers**](https://ubuntu.com/blog/what-is-kata-containers) to improve the security and isolation of containers.
* Red Hat released RHEL8 **without Docker support**, [pointing customers towards their own Podman and CRI-O project](https://www.linkedin.com/pulse/part-ii-why-docker-openshift-4-rhel-8-scott-mccarty).

Kubernetes is the clear winner here, but how do Podman, CRI-O and Kata Containers relate to this ecosystem? The diagram below gives a simplified overview.

![](/img/2020/container-runtimes.jpg)

More explanation below.

# Standards and organizations

* The **OCI** or *Open Containers Initiative* is an organization that creates container standards. The *OCI runtime spec* defines the API of a low-level container runtime and the *OCI image spec* defines what a "Docker image"  actually is.
* The **CNCF** is the *Cloud Native Compute Foundation*, an organization created by the Linux Foundation which hosts a big number of open source projects that all have to do with running "cloud native" applications. This is mostly about microservices and containers.
* The Kubernetes project has also defined a number of standards. Relevant for this article is the **CRI**: the *Container Runtime Interface*. This interface defines how Kubernetes talks with a high-level container runtime.

But what is a *high-level container runtime* exactly? First; we'll look at what a low-level container runtime does.

# High- vs Low-level container runtime

An OCI runtime is relatively simple. You give it the root filesystem of the container and a json file describing core properties of the container, and the runtime spins up the container and connects it to an existing network using a pre-start hook.

So what an OCI runtime does _not_ do is the following.

* Actually creating the network of a container.
* Managing container images.
* Preparing the environment of a container.
* Managing local/persistent storage.

All this is the job of a high-level container runtime. On top of this, the high-level container runtime implements the CRI so that Kubernetes has an easy way to drive the runtime.

At the moment, we have three main OCI runtimes or low-level container runtimes.

* `runc`, which is the default for most tools such as Docker and Podman. This is based on the code initially donated by Docker.
* `kata-run` from the "Kata Containers" project, which aims to provide much better security and isolation between containers by running each container in a lightweight VM. It's a merge of the `runv` and `Intel Clear Containers` projects.
* `gVisor` is created by Google. It provides better isolation by running each container in a tight security sandbox.

There are also three main high-level container runtimes.

* `containerd` is a CRI-compatible container runtime which was donated to the CNCF by Docker. It is currently the default in many Kubernetes distributions such ad Canonical's Charmed Kubernetes. It supports all OCI-compliant runtimes and has a special shim for `kata-run`.
* `CRI-O` is a bridge between Kubernetes and OCI-compliant runtimes created by Red Hat. It has the big advantage that it gets released in lock-step with Kubernetes itself. Each CRI-O version is compatible with the Kubernetes version that has the same version number. This runtime is the default in OpenShift.
* Docker itself can also be used as a CIR-compatible container runtime using the `docker-shim`. However, many Kubernetes distributors are moving away from this solution, due to the added unnecessary complexity of Docker.

# Podman, Buildah and crictl

Now, what was this about Red Hat moving from Docker to Podman in RHEL8? Scott McCarty wrote an excellent blog series excplaining [Why There Is No Docker in OpenShift 4 and RHEL 8](https://www.linkedin.com/pulse/part-ii-why-docker-openshift-4-rhel-8-scott-mccarty/). In short:

* Docker is a **big fat daemon** running almost always as root and which does a million things in the same binary. He argues it's better to split up functionality in a bunch of different projects so you can pick and choose which ones you actually need.
* **Development** of the Docker engine is **too slow** to keep up with Kubernetes.
* Docker's **community is on life support** because of how Docker handled the CE/EE split and the move/rename to the Moby project.
* Docker Inc.'s future is **uncertain**.

So, what should we use instead of Docker?

* Use [Podman](https://blog.openshift.com/crictl-vs-podman/) managing pods and containers. It's a CLI tool which is very similar to `docker`. It uses libpod which uses runc in backend and is fully compatible with "Docker Images".
* Use [Buildah](https://developers.redhat.com/blog/2019/02/21/podman-and-buildah-for-docker-users/) for building "Docker Images". It supports building containers from DockerFiles, but you can also build them with simple shell scripts!
* Use `CRI-O` for running containers with Kubernetes. If you want to debug pods and containers maintained by Kubernetes, you can use the [`crictl`](https://blog.openshift.com/crictl-vs-podman/) tool instead of the `docker` commands.

# Conclusion

Developers who use Docker and Kubernetes might have been surprised that Docker Inc. is in such bad shape. Further inspection, however, shows an entire ecosystem that is moving on. Docker clearly started this entire revolution, but it just didn't work out. The restructured Docker inc. will focus solely on developers. This might turn out to be an excellent move, since the docker client is still the prime way for developers to build run "Docker containers" on their development workstations. It will be interesting to watch this space in 2020 and see if Docker is able to implement this vision.

* *A special thanks to Kunal Kushwaha for his excellent presentation on Kubecon ["How Container Runtimes matter in Kubernetes?"](https://events19.linuxfoundation.org/wp-content/uploads/2017/11/How-Container-Runtime-Matters-in-Kubernetes_-OSS-Kunal-Kushwaha.pdf).*
* *Container ship image by [Sergii ILyushin](https://www.pexels.com/photo/aft-container-ship-containers-cranes-2181449/)*
