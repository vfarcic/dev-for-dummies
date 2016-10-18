# Virtualization and Containers

Software we're building would be useless with a place to run. If we exclude desktop applications (those that run on your laptop), everything we create runs on servers. What are they? *A server is a computer or a device on a network that manages network resources.* That was one more of those definitions understood only by those who already know what a server is. If we translate it to "plan English", a server is a computer that runs our software. It is, in a way, not much conceptually different than the computer you're using. The only important difference is that servers are optimized to "serve" applications. The only notable difference is that servers often to not have a monitor since they are not used by us directly. They tend to be more potent than laptop but they still have the same components. There is memory, hard disk, CPU, and so on.

At the begging, we were deploying our applications to *bare metal* servers.

## Bare Metal

Running applications on bare metal servers means that there is nothing between your application and the server. A customer, department, or a team would get their own dedicated server. Such a combination is often called single tenant server. From performance perspective, this is the best choice. There are no intermediaries between your application and a server allowing you to get maximum performance since nothing is wasting resources.

Single tenancy allows you to avoid the *noisy neighbor* effect. If multiple applications are running on the same server, they are impacting each others performance and stability. Let's say that we deploy two applications to a single server. If one of them is heavily used, it might, for example, occupy all available memory. As a result, the other application would become slow and unresponsive. If we're hosting a single application on a single server, such a problem is avoided. No one can impact our performance but ourselves.

If your application is sensitive to performance, bare metal can be unbeatable. It is faster than any other option we might choose.

The potential of breaking regulatory compliance in a multitenant environment was the main reason why security-sensitive organizations might be reluctant to move to some other option for hosting their applications. With bare-metal servers, it is possible to implement physical segregation of resources.

However, not everything is on a bright side with bare metal. It has its own set of disadvantages as well.

For one, bare metal tends to be more expensive than other options. This might seem contradictory since other option add additional layers on top of bare metal server. Those additional layers introduce monetary costs when they are from enterprise vendors. Moreover, they also introduce costs on resource usage. After all, every layer we add requires some amount on CPU, memory, hard disk, and so on. So, how can bare metal be more expensive than options that create additional costs? The answer lies in unbalanced resource usage. When we run applications on dedicated hosts, our resources are not at full capacity. It would be impossible to have an application that utilizes 100% of all the memory, all the CPUs, and others. No option will make the utilization be 100%. However, other solutions might allow us to get closer to that figure. Take this observation with a grain of salt. There are many different use case and the cost statement is not true in all of them.

Another potential problem is that bare metal servers are not very agile and elastic. It is hard to adjust capacity since we are dealing directly with physical resources. We cannot easily scale (increase capacity) or de-scale (decrease capacity).

To summarize, some of the potential advantages of bare metal servers are as follows.

* Resources dedicated to a single application, team, or department.
* Greater processing power.
* More consistent disk and network I/O performance.
* Quality of Service that guarantees elimination of the noisy neighbor problem in a multitenant environment.
* Higher level of security than with other options.
* Might be cheaper than other options.

Some of the potential disadvantages are as follows.

* Might be more expensive than other options (it contradicts one of the advantages, doesn't it?).
* Not agile and elastic
* Too much capacity for most applications

The alternative to bare metal servers is virtualization.

## Virtualization

Server virtualization is a virtualization technique that involves partitioning a physical server into a number of small, virtual servers with the help of virtualization software. In server virtualization, each virtual server runs multiple operating system instances at the same time.

In other words, if we adopt virtualization, one physical (bare metal) server is split into multiple virtualized entities. Each would have allocated part of the CPU, memory, and other resources. It is, in a way, as if you split a server into multiple smaller servers.

Virtualization is based on operating systems (OS) called hypervisors. It is a layer between the physical hardware and multiple operating systems running on top of it. each of those operating systems is isolated from each others and each has part of hardware resources allocated. Hypervisor's role is to create virtual machines that will run on bare metal servers. Each of those virtual machines would have OS of its own (Linux distributions like RedHat and Ubuntu, Microsoft Windows, and so on). As for hypervisors, there are multiple choices available. Some of the more commonly used are VMWare, KVM, Citrix XeriServer, Microsoft Hyper-V, and so on. The technology exists for a long time and is so mature that all options are very similar.

While virtualization exists from 60s, it become truly popular only during 90s. Even back than, many organizations failed to adopt it until early 2000. Today, most (not all) companies run their applications in virtualized servers. Why did this change happen? After all, bare metal looks like it has more pros than cons.

One of the main advantages VMs offer, when compared to bare metal, are dynamic workloads. Virtual machines can be easily created and destroyed. Their allocated resources can be adjusted and isolated between different VMs.

One of the most common use cases for virtualization is horizontal scalability. When more servers are required, additional virtual servers can be created on existing hardware (assuming that there are unused resources).

The major problem with virtualization is that hypervisor itself requires certain amount of resources. Total amount of resources allocated to virtual machines is lower if bare metal would be used. As a result, overall performance is lower.

Finally, unlike bare metal, VMs have a potential of the noisy neighbor effect, inconsistent performance, and might have security concerns.

To summarize, some of the potential advantages of bare metal servers are as follows.

* Easy creation and destruction of virtualized servers
* Adjustment of allocated resources
* Horizontal scalability
* Resource isolation

Some of the potential disadvantages are as follows.

* Lower performance than bare metal
* Potential of the noisy neighbor effect
* Inconsistent performance
* Potential security concerns

And then containers become popular.

## Containers

TODO

## Difference between virt and cont

TODO

## Cloud

TODO

AWS claims their performance is very close to bare metal.
No worries about hypervisor
Choose any OS image