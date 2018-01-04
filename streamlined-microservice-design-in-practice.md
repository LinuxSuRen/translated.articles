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
The microservices movement has been driven by developers, is closely aligned with the rise of Agile methods and DevOps, and has been motivated by a desire for faster software delivery. Consequently, developers often start coding quickly and rely on emergent design to guide their work, which can result in sub-optimal service disposition over the long haul. On the other hand, an overly-involved service design process can bog down development efforts and undermine the intended benefits of microservice architecture. How can appropriate design thinking be injected into the process in a streamlined way?  ```
微服务活动被研发人员驱动着，几乎接近敏捷方法、DevOps的潮流。更快的软件交付需求也带动着微服务。随之而来的，研发人员会快速地编码，基于紧急的设计来指导他们的工作，这就导致会出现低效的服务。另外过度的服务设计也会降低开发效率，破坏微服务架构的优势。如何进行适当的设计是需要考虑的?

With a hat tip to Simon Brown’s “just enough up front design” concept, the Microservice Design Canvas intends to capture the essential service attributes that can help guide development of the service itself as well as its consuming applications.  
根据西蒙·布朗的“尽量前置设计”理念，微服务设计画板是为了抓住重要服务的特性，以便指导服务的开发以及消费。  

![Image title](https://dzone.com/storage/temp/7525113-screen-shot-2017-12-13-at-95434-am.png)

Figure 1 - The Microservice Design Canvas.
图 1 - 微服务设计画板。

In addition to the name and description of the service, the canvas includes the following sections:  
除了服务的名称和描述外，画板上还包括下面的内容：

![Image title](https://dzone.com/storage/temp/7525148-screen-shot-2017-12-13-at-100052-am.png)

Ideally, a service designer can complete sections in the table's order and capture the essence of the service using the canvas. Here is an example of a completed canvas fora Transaction Search Service:  
理论上，一个服务的设计者应该能完成上面表格列出的内容，并依据画板抓住服务的重点。这里给出一个交易搜索服务的例子：  

![Image title](https://dzone.com/storage/temp/7525149-screen-shot-2017-12-13-at-100121-am.png)

Figure 2 - a sample microservice design canvas for "Transaction Search."
图 2 - “交易搜索”的微服务设计画板

# Microservices at Capital One
# 第一资本投资集团的微服务
Capital One has been an early adopter of microservice architecture, with several hundred now running in production across the company. Capital One’s technology is large and heterogeneous, not all of which is built using microservices. The initial rise of microservices adoption happened organically, by different teams experimenting with and adopting its concepts as they saw fit in their daily work.In 2017, the Capital One executive team declared maturation of microservices capabilities an important priority, and a team was put together to provide a microservices adoption strategy, implementation guidelines, and training workshops for development teams.  
第一资本在早期已经引入了微服务架构，并在全公司的线上产品中有几百个在运行着。他的技术体系是复杂而且庞大的，并不是所有的都以微服务的形式构建的。微服务正在蓬勃地发展中，很多不同的团队在日常工作中根据自己的实际情况在尝试。在2017年，第一资本的管理团队申明他们的微服务运用能力已经成熟，并将为开发团队提供微服务采用策略、实现指导以及培训。  

To align their microservices efforts across the organization, Capital One first needed to identify a common goal. When analyzing the success of the organic microservices efforts, the Capital One microservices team recognized that the power of the new architecture was that it allowed developers to move fast without compromising the safety and quality of their solutions. Irakli Nadareishvili, one of the leaders of the team, explains:  
为了能够让微服务在整个组织内推广，第一资本首先需要确定一个共同的目标。当在分析微服务效果时，第一资本的团队认为新架构的能力是允许研发人员可以快速迭代而不用在质量和安全问题上作出妥协。这个领导团队中的Irakli Nadareishvili解释到：  

For the longest time, there has been a belief in software engineering that you have to compromise between speed and safety: either you go fast or you build with high quality. Such a compromise makes intuitive sense. Complex systems are built by many teams, working on different parts of an application. Every now and then those teams need to coordinate their work with others, and at that point you have one of two choices: you either ignore coordination need and keep going fast, which may break some things along the way, or you acknowledge the need to coordinate and slow down. But what if we had a system architected in a way that minimized the need for coordination? Then we wouldn’t need to choose between speed and safety as often. It turns out you can have such a design if you have autonomous teams working on small batches of isolated work. For us, that is the essence of microservice architecture.  
长期以来，软件工程师认为必须在速度和安全的问题上作出妥协：快速构建或者高质量的构建。这样的妥协给人直观的感觉。这样的妥协给人一种很直观的感觉。复杂的系统是由很多团队开发出来的，他们分布在一个应用的不同部分上。这些团队之间时不时地需要进行协调，这时候你有两个选择：忽视协作的需要而保持高效，这样会导致有一些破坏；或者你认为需要协作而降低效率。但是，如果我们有一套系统可以最小化这些协作的需求呢？那么，就不需要经常在效率和安全之间做选择了。如果团队能够独立工作，并且是基于小批量的，就可以采用这样的设计。对我们来说，这就是微服务架构的要点。  

# Designing Microservices at Capital One
# 第一资本的微服务设计
Many organizations get stuck when trying to find the size for the microservices. In Capital One’s analysis of microservice design, they found that the optimal microservice size varies over time, as illustrated by microservice pioneers like Netflix:  
很多组织在寻找微服务的大小把握上遇到了问题。根据第一资本的微服务设计分析，优化微服务的大小是在随着时间在继续，例如微服务的先驱Netflix：  

![Image title](https://dzone.com/storage/temp/7525255-screen-shot-2017-12-13-at-100812-am.png)

At Capital One, development teams start with coarse-grained design and split microservices when they find need to eliminate emerging instances of coordination.Teams are not expected to get service boundaries “right” out of the gate. Instead, boundaries evolve over time to allow autonomous, high-performance teams to develop systems quickly and safely.  
在第一资本，他们不期待找到服务边界。反而这些边界会随着时间的推移而有变化，高效的团队会高效、安全地进行研发。  

When examining how to design greenfield or brownfield system of microservices, the Capital One microservices team used Domain Driven Design (DDD) as a starting point. They found the concept of bounded contexts to be extremely useful for representing autonomous capabilities in a complex system. Overall, however, they felt that applying DDD in depth across the organization would require expertise and experience that most software teams were not equipped with, and trying to make it work would be costly and difficult to implement consistently.  
在研究如何设计微服务时，第一资本的团队采用领域驱动设计（DDD）作为突破点。他们发现边界上下文的概念对于复杂的系统是极其有用的。然而，他们认为，在组织中应用DDD的深度需要专业知识和经验，大多数软件团队是不具备的，尝试的话可能会有代价并难以持续。  

Capital One found a viable shortcut to DDD in AlbertoBrandolini’s Event Storming methodology. This new approach that is rapidly gaining popularity in the software industry allows teams to explore a complex domain—including the identification of bounded contexts—in just a handful of 4-hour sessions. In addition to its work products, Capital One has found Event Storming to be a collaborative and inclusive exercise that helps quickly develop a shared understanding of a product between engineering, product teams, design teams, as well as other key stakeholders.  
第一资本在AlbertoBrandolini的事件风暴方法论中找到了DDD可行的捷径。这种在软件行业中迅速流行的新方法允许团队探索一个复杂的领域——包括识别边际上下文——在短短4个会话中。除了工作以外的产品，第一资本发现事件风暴是一个协作包容的活动，他有助于快速地开发可以在工程师、产品、设计以及其他的相关团队之间互相认同的产品。  

# The Microservice Design Canvas at Capital One
# 第一资本的微服务设计画板
One issue the Capital One team encountered withEvent Storming is that, while the process is very useful, its final artifact—a wall full of sticky notes—is difficult to digitize or document. Since they wanted something more than just a list of bounded contexts and hotspots as a takeaway, they decided to codify the resulting microservice designs using a variant of the Microservices Design Canvas. Team member James Higginbotham reordered the boxes on the canvas to align more closely with the Business Model Canvas, resulting in the following:  
第一资本发现事件风暴虽然非常有用，但还是有个问题，就是无法数字化和文档化。因此，他们不仅仅想要的是列出上下文边界和热点，于是决定把微服务设计的结果使用微服务设计画板保存下来。Higginbotham团队成员James重新排列了画布，更像下面的商业式画布：  

![Image title](https://dzone.com/storage/temp/7525273-screen-shot-2017-12-13-at-100922-am.png)

Figure 3 - A sample microservice design canvas for "Payments Management Service" using the Capital One variant (information purely for demonstration purposes).
图 3 - “支付管理服务”的微服务设计画板（仅供演示）

So far, the Capital One team has found the canvas to be a useful way of documenting the design of their microservices. Importantly, they are able to use the canvas in a non-intrusive way that helps them reduce coordination between teams in order to improve their overall delivery speed without compromising the safety and stability of their systems.  
到目前为止，第一资本的团队发现画板是一个描述微服务设计的一个好办法。重要地，他们有能力使用画板作为一个非侵入式的方法来帮助他们减少团队之间的协作，这样可以提高交付效率而不用在安全性和稳定性问题上作出妥协。  

# Design Thinking in Microservice Architecture
# 微服务架构设计的思考
Just as Capital One recognized that microservice boundaries evolve over time, the structure of the Microservice Design Canvas will also change as it is applied and adapted by individuals and organizations. Its value should be measured by how effectively it meets its goal: to provide a simple tool for capturing just enough design thinking at the right time in order to help deal with the complexity of distributed software ecosystems.Experimentation and iteration are hallmarks of the microservices way, so please let the authors know about your own experiences working with the canvas and the other tools discussed in this article.  
正如第一资本承认的那样，微服务边界会随着时间的推移而改变，微服务设计画板的结构也会随着个人和组织的应用而变化。它的价值应该依据它是如何有效地满足目标来衡量：为了帮助处理复杂的分布式软件系统，提供一个简单的工具，用来在合适的时间捕捉足够的设计思想。
