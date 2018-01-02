Streamlined Microservice Design in Practice  
流线型微服务器设计实践  

Learn about the concept of the Microservice Design Canvas and how it is used to design microservice architecture at Capital One.  
学习微服务设计画板，以及微服务架构是如何在“美国第一资本投资集团”中是如何应用的。  

This article is featured in the new DZone Guide to Microservices. Get your free copy for more insightful articles, industry statistics, and more!  
本文介绍了DZone新的微服务指导。可以获得更多有见地的文章、行业数据等等。  

As more organizations implement microservices, the practices of microservice architecture become more mature. Whereas much of the early microservices literature focused on companies decomposing a monolithic web application into microservices, larger and more diverse organizations are now tackling how to migrate their existing software ecosystems into domains of services in order to improve their software delivery speed and scalability. This problem space is significantly more complex than breaking down the single monolith, and comes with higher-order challenges.  
随着更多的组织在实践微服务，微服务架构变得更加成熟。然而，早期的微服务活动关注在如何把单个Web程序解偶成多个服务，更大更多的组织为了提高他们的软件交付速度和可伸缩性，也正在把已有的软件生态迁移成服务。这个问题显然要比拆分大的系统要更复杂，更具有挑战性。  

Modularization is fundamental to dealing with the complexity of distributed software systems. This is both the reason microservice architecture is gaining popularity, and an important reminder of how to approach it. Finding the right boundaries between services is understandably one of the main focus areas for organizations adoptingmicroservices in order to reduce coordination between teams, and there is a growing body of information on techniques to draw those boundaries. This technology-agnostic design work deals with the essential complexity of the software system, helping to improve its evolvability and sustainability over time. Once the boundaries are drawn, there is still design work that needs to be done.  
模块化主要是为了解决分布式系统的复杂性。这既是微服务架构流行起来的原因，也是指导如何着手的一个重要提示。找到服务之间正确的边界自然是很重要的，组织采用微服务减少团队直接的协调。这项与技术无关的设计工作处理必要的软件复杂性问题，用于不断地改进软件的演进和持续。即使边界划分好以后，设计工作还是不可或缺的。  

# The Microservice Design Canvas
# 微服务设计面板
The microservices movement has been driven by developers, is closely aligned with the rise of Agile methods and DevOps, and has been motivated by a desire for faster software delivery. Consequently, developers often start coding quickly and rely on emergent design to guide their work, which can result in sub-optimal service disposition over the long haul. On the other hand, an overly-involved service design process can bog down development efforts and undermine the intended benefits of microservice architecture. How can appropriate design thinking be injected into the process in a streamlined way?  
更快的软件交付需求

With a hat tip to Simon Brown’s “just enough up front design” concept, the Microservice Design Canvas intends to capture the essential service attributes that can help guide development of the service itself as well as its consuming applications.  


Image title

Figure 1 - The Microservice Design Canvas.

In addition to the name and description of the service, the canvas includes the following sections:

Image title

Ideally, a service designer can complete sections in the table's order and capture the essence of the service using the canvas. Here is an example of a completed canvas fora Transaction Search Service:

Image title

Figure 2 - a sample microservice design canvas for "Transaction Search."

# Microservices at Capital One
# 第一资本投资集团的微服务
Capital One has been an early adopter of microservice architecture, with several hundred now running in production across the company. Capital One’s technology is large and heterogeneous, not all of which is built using microservices. The initial rise of microservices adoption happened organically, by different teams experimenting with and adopting its concepts as they saw fit in their daily work.In 2017, the Capital One executive team declared maturation of microservices capabilities an important priority, and a team was put together to provide a microservices adoption strategy, implementation guidelines, and training workshops for development teams.  
他的技术体系是复杂而且庞大的，并不是所有的都以微服务的形式构建的。

To align their microservices efforts across the organization, Capital One first needed to identify a common goal. When analyzing the success of the organic microservices efforts, the Capital One microservices team recognized that the power of the new architecture was that it allowed developers to move fast without compromising the safety and quality of their solutions. Irakli Nadareishvili, one of the leaders of the team, explains:  

For the longest time, there has been a belief in software engineering that you have to compromise between speed and safety: either you go fast or you build with high quality. Such a compromise makes intuitive sense. Complex systems are built by many teams, working on different parts of an application. Every now and then those teams need to coordinate their work with others, and at that point you have one of two choices: you either ignore coordination need and keep going fast, which may break some things along the way, or you acknowledge the need to coordinate and slow down. But what if we had a system architected in a way that minimized the need for coordination? Then we wouldn’t need to choose between speed and safety as often. It turns out you can have such a design if you have autonomous teams working on small batches of isolated work. For us, that is the essence of microservice architecture.  
长期以来，软件工程师认为必须在速度和安全的问题上作出妥协：快速构建或者高质量的构建。这样的妥协给人直观的感觉。

# Designing Microservices at Capital One
Many organizations get stuck when trying to find the size for the microservices. In Capital One’s analysis of microservice design, they found that the optimal microservice size varies over time, as illustrated by microservice pioneers like Netflix:  
很多组织在寻找微服务的大小尺度上遇到了问题。

Image title

At Capital One, development teams start with coarse-grained design and split microservices when they find need to eliminate emerging instances of coordination.Teams are not expected to get service boundaries “right” out of the gate. Instead, boundaries evolve over time to allow autonomous, high-performance teams to develop systems quickly and safely.  
在第一资本，他们不期待找到服务边界。

When examining how to design greenfield or brownfield system of microservices, the Capital One microservices team used Domain Driven Design (DDD) as a starting point. They found the concept of bounded contexts to be extremely useful for representing autonomous capabilities in a complex system. Overall, however, they felt that applying DDD in depth across the organization would require expertise and experience that most software teams were not equipped with, and trying to make it work would be costly and difficult to implement consistently.  
第一资本采用领域驱动设计（DDD）作为突破点。

Capital One found a viable shortcut to DDD in AlbertoBrandolini’s Event Storming methodology. This new approach that is rapidly gaining popularity in the software industry allows teams to explore a complex domain—including the identification of bounded contexts—in just a handful of 4-hour sessions. In addition to its work products, Capital One has found Event Storming to be a collaborative and inclusive exercise that helps quickly develop a shared understanding of a product between engineering, product teams, design teams, as well as other key stakeholders.

# The Microservice Design Canvas at Capital One
One issue the Capital One team encountered withEvent Storming is that, while the process is very useful, its final artifact—a wall full of sticky notes—is difficult to digitize or document. Since they wanted something more than just a list of bounded contexts and hotspots as a takeaway, they decided to codify the resulting microservice designs using a variant of the Microservices Design Canvas. Team member James Higginbotham reordered the boxes on the canvas to align more closely with the Business Model Canvas, resulting in the following:

Image title

Figure 3 - A sample microservice design canvas for "Payments Management Service" using the Capital One variant (information purely for demonstration purposes).

So far, the Capital One team has found the canvas to be a useful way of documenting the design of their microservices. Importantly, they are able to use the canvas in a non-intrusive way that helps them reduce coordination between teams in order to improve their overall delivery speed without compromising the safety and stability of their systems.

# Design Thinking in Microservice Architecture
Just as Capital One recognized that microservice boundaries evolve over time, the structure of the Microservice Design Canvas will also change as it is applied and adapted by individuals and organizations. Its value should be measured by how effectively it meets its goal: to provide a simple tool for capturing just enough design thinking at the right time in order to help deal with the complexity of distributed software ecosystems.Experimentation and iteration are hallmarks of the microservices way, so please let the authors know about your own experiences working with the canvas and the other tools discussed in this article.

This article is featured in the new DZone Guide to Microservices. Get your free copy for more insightful articles, industry statistics, and more! 
