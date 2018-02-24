---
layout: post
title: "Docker, Kubernetes 和 Weaveworks都是什么鬼？"
author: "学习的Yang"
categories: techynotes
tags: [concept, product]
image: docker1.jpg
techy: true
---

接触这几个词是因为组里的一些D和MD们互相撕逼抢钱，然后撕赢的说要推动整个组的技术变革，不知道从那些组那里听来了这些个词汇，然后组里没几个人知道是什么东西。然后这个阿叉D就叫我给他讲讲。

我笑笑地说，好呀让我回去做一下功课。心里其实想的是，这样的陈年狗屎系统你以为加一些花里胡哨的技术就能为你往上跪舔挣来更多关爱么，科科真是搞SIAO。

安尼喂，我就趁机多学点东西了。

**1. Docker**

这是个Container。什么鬼是Container？

> Containers include the application and all of its dependencies -- but share the kernel with other containers, running as isolated processes in user space on the host operating system. Docker containers are not tied to any specific infrastructure: they run on any computer, on any infrastructure, and in any cloud. 

如其名，就是把application和所有的dependencies都包在一起，这样在同一个核上可以像运行一个各自独立的进程一样运行你的application。于是乎提供了更多的兼容性可移植性，就是可以把一个container里的东西丢到不同的环境中运行，所以在用云端的时候也会更方便。

很多人拿这个跟虚拟机做比较，其实它们之间的共同点还是很多的，都是为了更好地兼容不同的系统。主要的区别在于：同一个操作系统OS上面，可以跑多个Container，而VM本身是创造OS的，一个VM对应一个OS。

![](/assets/img/docker2.jpg?raw=true)

好的说回Docker，定义是这样的：

> Docker containers wrap a piece of software in a complete file system that contains everything needed to run: code, runtime, system tools, system libraries – anything that can be installed on a server. This guarantees that the software will always run the same, regardless of its environment.

就是Container的定义啦。于是，还衍生出了一个CaaS - Container as a Service，因为Docker可以on-prem（就是On-premisessoftware，跟remote相对的一个概念），可以在云端，还可以在虚拟机上运行，兼容Linux和Windows系统，用户就再也不用担心因为运行环境的不同而产生的麻烦了。所以用户可以直接使用整个container，像是用已经设定调试好的一个产品。（才怪=.=）

![](/assets/img/docker3.jpg?raw=true)

在Docker里，image是一个专有名词，指的是一个运行时需要的文件系统Filesystem和参数的总和，image本身并没有任何状态也不会改变，一个container是一个image的instance。

关于Docker主要的应用，除了之前的CaaS之外，还因为Docker本身跟Jenkins和GitHub这类工具可以协同，可以直接应用在Continous Integration/Development (CI/CD)以及优化大系统本身的结构（就是把不同的东西装到container里，然后挪来挪去）。

**2. Kubernetes**

好了，当你有了Docker以后，你要怎样来大范围地实现Container应用呢，它们在各自的Docker Hosts上，你需要怎样管理呢？

这时候出现了Kubernetes：

> Kubernetes is an open-source platform for automating deployment, scaling, and operations of application containers across clusters of hosts, providing container-centric infrastructure. (Orchestration System)

感觉就是一个用来定义和管理各个container pool的一个工具, 然后这个工具在好多个Nodes上面运行。一个Kubernetes pod可以是由一个或一群container组成的，是Kubernetes的基本单位，一个Pod通常对应一个application。

因为Pod的生命周期很短暂，IP地址是不稳定的，所以在与外界交流的时候会有问题，引入servie这个概念：就是在一堆Pod之上弄一个proxy，给一个虚拟的IP地址，以方便与外界的其它service交流。

![](/assets/img/docker4.jpg?raw=true)

一个Kubernetes cluster的具体组成结构是：

- A **master** (with several independent sub-components) that coordinates the work.这就是一个controlling service，可以安装在一台或者多台分布的机器上，功能就是实现Nodes与外界的交流，里面有API，可以接收REST的指令。
- A distributed key-value store, currently **etcd** (developed by the CoreOS team), for maintaining the resource state in a persistent and reliable manner, throughout the cluster.一个用来存储可以被全部Nodes使用的设定参数的数据库。
- A number of **nodes** that carry out the work.
- A command line tool called **kubectl** allowing to query and manipulate the cluster state; this is a fancy way of saying: running containers, creating services and administrating the cluster (logging, monitoring, debugging).

差不多就是这样，Kubernetes对网络设置的主要要求是：每一个Pod都要有其自己的IP地址，并且conatiner host和pod之间要可以通信。

**3. Weaveworks**

这是另外一个因为container而产生的产品，我的理解就是这是用来为container构架虚拟网络的一套工具。

> Weave creates a virtual, software-defined network, or SDN, across every Docker host in your infrastructure. Each container gets its own IP, allowing you to design your application topology without changing your application’s behaviour.

就是用来建一个自定义的虚拟网络，然后给每个container不同的IP地址，主要有这么几个产品：

1. Weave Scope allows you see and interact with your distributed application and its containers in real time. Weave Scope automatically detects and monitors every host, Docker container and process in your infrastructure, builds a map showing their inter-communications and then presents an up-to-date view of your infrastructure in a web interface.
2. Weave Net creates a virtual network that connects Docker containers across multiple hosts and enables their automatic discovery. With Weave Net, portable microservices-based applications consisting of multiple containers can run anywhere: on one host, multiple hosts or even across cloud providers and data centers. Applications use the network just as if the containers were all plugged into the same network switch, without having to configure port mappings, ambassadors or links.
3. Weave Flux is a tool for deploying container images to Kubernetes clusters.

还可以设置Weave Cloud：

![](/assets/img/docker1.jpg?raw=true)

    1. Setup: Troubleshooting Dashboard
    2. Deploy: Continuous Delivery
    3. Monitor: Prometheus Monitoring
    4. Secure: Container Firewalls

好吧，差不多就这样。觉得就算打算要用了，直到具体实现还隔着好几年的距离，呵呵。

*Reference：*

*[Docker](https://www.docker.com/)*

*[Kubernetes](https://kubernetes.io/)*

*[Weaveworks: Container & Microservices Networking](https://www.weave.works/)*