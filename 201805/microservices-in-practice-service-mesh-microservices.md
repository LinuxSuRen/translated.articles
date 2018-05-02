[original](https://medium.com/microservices-in-practice/service-mesh-for-microservices-2953109a3c9a)

# Service Mesh for Microservices
# 微服务的服务网格

Microservices architecture has been evolving a lot during last couple years and there are quite a few new concepts and patterns are emerging. ‘Service Mesh’ concept is getting quite popular . In this post, I’m planning to cover the key concepts related to Service Mesh and how it is used in real world microservices implementations.
在过去几年内，微服务架构已经发展了很多，而且有很多新的概念和模式融合进来。"服务网格"的概念变得流行起来。在本文中，我计划介绍服务网格相关的概念，以及如何用在真实的微服务中。

# Why ‘Service Mesh’?
# 为什么要有“服务网格”？
As with many emerging technologies, there was a lot of hype around the Microservices Architecture. Most people think that microservices is the answer to all the problems they had with previous architecture such as SOA/ESB. However, when we observe the real world microservices implementations, we can see that most of the functionalities that a centralized bus (ESB) supports are now implemented at microservices level. So, we are more or less solving the same set of fundamental problems, but we are solving them at different dimensions with Microservices.
正如很多融合技术，微服务架构周围有很多是炒作。大多数人认为微服务是所有问题的答案，之前的架构包括：SOA/ESB。然而，当我们观察真实世界中的微服务实现，我们可以看到大多数功能的支持现在已经在微服务层面实现，例如：总线（ESB）。所以，我们或多或少都在解决同样的基础问题，但是，我们是在微服务的不同方面来解决的。

![](https://cdn-images-1.medium.com/max/2000/1*l6rRbQ6pmWFUBy1lr8UAUw.png)
Figure 1: From centralized integration/ESB to Microservices
图1：从集中集成/ESB到微服务

For example, let’s take a scenario where you need to call multiple downstream services in resilient manner and expose the functionality as a another (composite) service. As shown in figure 1, with the ESB architecture, you can easily leverage the inbuilt capabilities of ESB, for building virtual/composite services and functionalities such as circuit breakers, timeouts and service discovery etc., which are useful during inter-service communication.
例如：让我们来看一个场景，你需要以弹性的方式来调用多个下游服务，并作为一个组合服务把这个功能暴露。如图1所示,通过ESB架构，你可以轻松地发挥ESB内在的能力，对于构建虚拟、组合服务和功能，例如断路器、超时和服务发现等等，在内部服务通信中是很有用的。

When you implement the same scenario using Microservices, then you no longer have a centralized integration/ESB layer but a set of (composite and atomic) microservices. So, you have to implement the all these functionalities at the microservices level.
当你用微服务实现相同的场景时，你不再需要一个集中集成、ESB，而是一套组合、原子微服务。因此，你不得不在微服务层面实现所有的这些功能。

![](https://cdn-images-1.medium.com/max/1600/1*BJFhfCfraN25GEY02VPq4g.png)
Figure 2: Microservice components and service-to-service communication
图2：微服务组件和服务间通信

Therefore a given microservice which communicates with other services(figure 2), comprises of:
因此，一个给定的微服务与其他服务（图2），包括：  
* 业务逻辑 实现业务功能，计算和服务组合、集成逻辑。
Network Functions that take care of the inter-service communication mechanisms (basic service invocation through a given protocol, apply resiliency and stability patterns, service discovery etc.) These network functions are built on top of the underlying OS level network stack.  
* 网络功能 处理内部服务通信机制（通过给定的协议启用基本服务，实现弹性、稳定、服务发现等）。这些网络功能是基于操作系统层面的网络。  
Now think about the effort involve in implementing a such microservice. Implementing the functionalities related service-to-service communication from scratch is a nightmare. Rather focusing on the business logic, you will have to spend a lot of time on building service-to-service communication functionalities. And this is even worse if you use multiple technologies to build microservices (such as multiple programming languages as shown in figure 1), because you need to duplicate the same efforts across different languages (e.g. Circuit breaker has to be implemented on Java, Node, Python etc.).  
现在想一下要实现这样的一个微服务需要付出的工作。从头开始实现面向服务通信这样的功能简直就是个噩梦。你将会不得不话大量的时间来维护面向服务通信功能，而不是关注在业务逻辑上。而且，如果你使用了多种技术（例如图1中显示的多种语言）来构建微服务的话，甚至会更糟糕。因为，你需要在不同语言上付出相同的精力（例如：熔断器不得用Java、Node、Python等语言来实现）。

The most complex challenge in realizing microservice architecture is not building the services themselves, but the communication between services.
实现微服务架构过程中最复杂的挑战不是构建服务本身，而是服务之间的通信。

Since most of the inter-service communication requirements are quite generic across all microservices implementations, we can think about offloading all such tasks to a different layer, so that we can keep the service code independent. That’s where ‘service mesh’ comes into the picture.
由于大部分内部服务之间的通信需要是通用的，我们可以考虑把这种任务抽离到一个层上，我们就可以保证这个服务代码的独立性。这就是“服务网格”的邮来。

# What is a ‘Service Mesh’?
# 什么是“服务网格”？
In a nutshell, a Service Mesh is an inter-service communication infrastructure. With a service mesh,
简单来说，服务网格也就是内部服务通信框架。在服务网格中，

* A given Microservice won’t directly communicate with the other microservices.
* 在微服务中，不会直接和其他服务通信。

* Rather all service-to-service communications will take places on-top of a software component called service mesh (or side-car proxy).
* 所有服务间的通信将会取代软件组件之间的调用成为服务网格（或 side－car 代理）。

* Service Mesh provides the built-in support for some network functions such as resiliency, service discovery etc.
* 服务网格默认提供部分网络功能，例如：弹性、服务发现等。

* Therefore, service developers can focus more on the business logic while most of the work related to the network communication is offloaded to the service mesh.
* 因此，服务开发者可以更多地关注业务逻辑，而大部分网络通信相关的工作交给来服务网格。

* For instance, you don’t need to worry about circuit breaking when your microservice call another service anymore. That’s already comes as part of service mesh.
* 例如：当你的微服务调用其他的服务时，不用再担心断路器问题。那已经是服务网格的一部分了。

* Service-mesh is language agnostic: Since the microservice to service mesh proxy communication is always on top to standard protocols such as HTTP1.x/2.x, gRPC etc., you can write your microservice from any technology and they will still work with the service mesh.
* 服务网格是语言无关的：服务网格代理通信对微服务来说建立在标准的协议之上，例如：HTTP1.x/2.x, gRPC等,你可以用任何技术来写你的微服务，都是可以兼容服务网格。

![](https://cdn-images-1.medium.com/max/2000/1*DIV3ZADt68hff9_mDIKLug.png)
Figure 3: Service to service communication with Service Mesh
图3：通过服务网格实现服务间通信

Let’s try to further understand the service interactions and responsibilities which are shown in figure 3.
让我们进一步了解图3所展示的服务交互和责任。

# Business Logic
# 业务逻辑

The service implementation should contain the realization of the business functionalities of a given service. This includes, logic related to it’s business functions, computations, integration with other services/systems(including legacy, proprietary and SaaS) or service compositions, complex routing logics, mapping logic between different message types etc.
服务的实现应该包含业务功能。这包括：业务相关的逻辑，计算，和其他服务、系统或者服务的集成，复杂的路由逻辑，不同消息类型间的映射逻辑等。


# Primitive Network Functions
# 原始网络功能

Although we offload most of the network functions to service mesh, a given service must contain the basic high-level network interactions to connect with the service mesh/side-car proxy. Hence, a given service implementation will have to use a given network library(unlike the ESB world, where you just have to use a very simple abstraction)to initiate network calls (to service mesh only). In most cases, microservices development framework embed the required network libraries to be used for these functions.
尽管我们把大部分网络功能都交给了服务网格，但服务还是必须包含和服务网格或者 side-car 代理之间基本的高级网络交互。因此，服务的实现必须使用特定的网络库来初始化网络（只是对服务网格的）调用。大多数情况下，微服务开发框架都嵌入了必要的网络库。

# Application Network Functions
# 应用网络功能

There are application functionalities which tightly coupled to the network, such as circuit breaking, timeouts, service discovery etc. Those are explicitly separated from the service code/business logic, and service mesh facilitate those functionalities out of the box.
还有一些应用功能和网络紧耦合，例如：断路器、超时、服务发现等。那些已经明确地从服务代码、业务逻辑中分离，并且服务网格使得这些功能开箱即用。

Most of the initial microservices implementations simply ignore the gravity of the network functions offered from a central ESB layer, and they implemented all such functionalities from scratch at each microservice level. Now they have started realizing the importance of having a similar shared functionality as a distributed mesh.
大多数初期的微服务实现简单地忽略了从中央 ESB 层提供的网络功能，他们从服务层面粗糙地实现了这些功能。现在他们已经开始意识到有一个类似网格这种分享功能的重要性。

# Service Mesh Control Plane
# 服务网格控制层面

All service mesh proxies are centrally managed by a control pane. This is quite useful when supporting service mesh capabilities such as access control, observability, service discovery etc.
所有服务网格代理都是由控制面板集中管理。当需要支持访问控制、服务发现等能力时，这就是很有用的。

# Functionalities of a Service Mesh
# 服务网格的功能

As we have seen earlier, the service mesh offers a set of application network functions while some (primitive) network functions are still implemented the microservices level itself. There is no hard and fast rule on what functionalities should be offered from a service mesh. These are the most common features offered from a service mesh.
正如我们之前看到的，服务网格提供了一套应用网络功能，一些（原始的）网络功能依然是作为微服务本身实现的。没有固定和快速的规则来说明哪些功能应该由服务网格提供。大多数通用的特性是由服务网格提供的。

* Resiliency for inter-service communications: Circuit-breaking, retries and timeouts, fault injection, fault handling, load balancing and failover.

* Service Discovery: Discovery of service endpoints through a dedicated service registry.

* Routing: Primitive routing capabilities, but no routing logics related to the business functionality of the service.

* Observability: Metrics, monitoring, distributed logging, distributed tracing.

* Security: Transport level security (TLS) and key management.

* Access Control: Simple blacklist and whitelist based access control.

* Deployment: Native support for containers. Docker and Kubernetes.

* Interservice communication protocols: HTTP1.x, HTTP2, gRPC

# Service Mesh Implementations
# 服务网格实现
Linkerd and Istio are two popular open source service mesh implementations. They both follows a similar architecture, but different implementation mechanisms. You can find a very good comparison between these two service mesh implementations at [1].

# Service Mesh — Pros and Cons
Let’s have a quick look at the pros and cons of service meshes.

Pros

* Commodity features are implemented outside microservice code and they are reusable.

* Solves most of the problems in Microservices architecture which we used to have ad-hoc solutions: Distributed tracing, logging, security, access control etc.

* More freedom when it comes to selecting a microservices implementation language: You don’t need to worry about whether a given language supports or has libraries to build network application functions.
Cons

* Complexity: Having a service mesh drastically increase the number of runtime instances that you have in a given microservice implementation.

* Adding extra hops: Each service call has to go through an extra hop(through service mesh sidecar proxy).

* Service Meshes address a subset of problems: Service mesh only address a subset of inter-service communication problems, but there are a lot of complex problems such as complex routing, transformation/type mapping, integrating with other services and systems, to be solved at your microservice’s business logic.

* Immature: Service mesh technologies are relatively new to be declared as full production ready for a large scale deployments.

# Conclusion
# 总结

In summary, service mesh addresses some of the key challenges when it comes to the realization of microservice architecture. It gives you more freedom to select diverse set of microservices implementation technologies as well as to focus more on business logic rather investing more time on network functions between services. However, service mesh won’t solve any of the business logic related or service integration/composition related problems.

Update: “Service Mesh vs API Gateway”?

Please check the articles API Gateways vs Service Mesh for more further information on this.
