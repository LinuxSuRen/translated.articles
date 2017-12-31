# 15 Metrics for DevOps Success
# 影响DevOps成功实践的15个指标

Keeping an eye on metrics is key to measuring your success as a DevOps shop. In this article, we take a look at fifteen such metrics you really need to be watching.  
持续对特定指标的关注是衡量DevOps实践是否成功的关键。通过本文，我们看一下你确实需要关注的十五个指标。  

How is DevOps going within your organization? If you need some help measuring just how well it is going, we have prepared a list of some key DevOps metrics to track. These metrics can help you understand how your team is doing over time.  
你所在的组织里DevOps是如何践行的？如果你需要一些帮助来了解这个过程进行的怎么样，我们已经准备了一个关键的DevOps指标清单用来追踪。这些指标可以帮助你了解，在随着时间的推移你的团队是如何做的。

# Define What DevOps Means to Your Organization
# 定义Devops对你们组织的意义

The word DevOps means different things to different people. Some say it a culture and every vendor in the industry claims that their tools help with DevOps. Depending on how you define DevOps, some of these metrics may matter more or less to you and your team.  
DevOps这个词对于不同的人有不同的含义。有人认为它是一种文化，这个行业中的每个厂商都声称他们的工具是有益于DevOps的。依据你对DevOps的定义不同，这些指标可能对你的或者你的团队的意义或大或小。  

I define DevOps as everything that relates to deploying and monitoring your applications. In many ways, this bleeds over to site reliability engineering. At Stackify, we don’t even have an operations team to collaborate with. Our developers deploy directly to the cloud and we operate in more of a “NoOps” style. Check out my blog post to learn more about my views on what DevOps is.  
 Check out my blog post to learn more about my views on what DevOps is.
我认为DevOps包括了你的应用程序的在部署和监控中的所有过程。从很多方面来说，这都是现场可靠性工程的问题。
在Stackify，我们甚至都没有运维团队来操作。我们的开发人员会直接部署到云服务器，并且更像是“没有运维”的方式。
查看我的博客，可以找到更多我对于DevOps是什么的观点。

# Identify Your DevOps Challenges
# 识别DevOps实践中将会面临的挑战

Before you figure out what DevOps metrics to track, you need to identify what challenges your organization has and what problems you are trying to solve. At Stackify, our biggest issue has been not deploying often enough and lowering our defect escape rate. Our executive team is putting a big focus on those specific metrics for 2018.
在你弄明白有哪些DevOps指标需要追踪之前，你需要识别出来你所在的组织中有哪些挑战，有哪些问题是你们正在解决的。
在Stackify，我们最大的问题是部署频率低，并且降低了缺陷逃逸速度。我们的执行团队正在把重点放在2018年的具体指标上。

# Types of DevOps Metrics
# Devops的指标类型

DevOps is all about continuous delivery and shipping code as fast as possible. You want to move fast and not break things. By tracking these DevOps metrics, you can evaluate just how fast you can move before you start breaking things.
DevOps是为了尽可能快的持续交付并运输代码。你希望能尽快交付而不因此导致问题发生。
通过追踪这些DevOps指标，可以评估出你们持续交付的速度有多块，而不会导致有问题。

1. Deployment frequency
1. 开发频率
2. Change volume
2. 体积变化
3. Deployment time
3. 开发时间
4. Lead time
4. 投产周期
5. Customer tickets
5. 客户支持率
6. Automated test pass %
6. 自动化测试通过率
7. Defect escape rate
7. 缺陷逃逸率
8. Availability
8. 可用性
9. Service level agreements
9. 服务等级协议
10. Failed deployments
10. 部署失败
11. Error rates
11. 错误率
12. Application usage and traffic
12. 应用程序的使用和流量
13. Application performance
13. 应用程序性能
14. Mean time to detection (MTTD)
14. 平均检测时间（MTTD）
15. Mean time to recovery (MTTR)
15. 平均恢复时间（MTTR）

# Goals of DevOps: Velocity, Quality, Performance
# DevOps的目标：快速、质量、性能
The main goals of DevOps are velocity, quality and application performance.  
DevOps的主要目标是快速，质量和性能。  

You want to ship code as fast and often as possible. How fast you can do this will vary wildly based on your type of product, team, and risk tolerance.
你希望尽可能经常、快速地交付代码。可以做到多块，很大程度上取决于你的产品类型、团队以及风险承受能力。

Even if you don’t track any DevOps metrics around your velocity, you should at least measure how you are doing on quality. Perhaps you try to ship when you can, and you don’t really care how fast exactly. However, you always care about quality. The last thing you want is to be chasing production fires all the time.
你可以不跟踪DevOps中速度的指标，但至少应该关于质量问题。你可能已经试着根据自己的能力来做这些，但并没有真正地关心到底能有多块。
然而，你总是在关注质量。你最不希望的就是总是在救产品的“火“。

The third piece of the equation is performance. You could argue that it is also at odds with your goals of high velocity and quality. Performance is also related to quality, but perhaps a little different.
第三部分是性能。你可能对速度和质量的权衡有质疑。性能也和质量有关，只是有点区别。

# Deployment Size
# 部署规模
Tracking how many stories, feature requests, and bug fixes are being deployed is another good DevOps metric. Depending on how large your individual work items are, their counts could vary wildly. You could also track how many story points or days’ worth of development work are being deployed.
跟踪有多少故事、特性需求以及修复的bug正在被部署是DevOps的另外一个好的指标。你的项目的大小会影响部署规模的。你还可以追踪有多少故事点或者开发任务量。

# Deployment Frequency
# 部署频率
Tracking how often you do deployments is a good DevOps metric. Ultimately, the goal is to do more smaller deployments as often as possible. Reducing the size of deployments makes it easier to test and release.
跟踪部署频率是另外一个不错的DevOps指标。最终的目标是，降低部署规模并加快部署频率。降低部署规模使得更加容易测试和发布。

I would suggest counting both production and non-production deployments separately. How often you deploy to QA or pre-production environments is also important. You need to deploy early and often in QA to ensure time for testing. Finding bugs in QA is important to keep your defect escape rate down.
我建议单独统计生产和非生产的部署频率。你多久部署一次QA或者预生产环境同样是重要的。为了确保测试的时间，你需要尽早尽快地部署到QA环境中。
在QA环境中查找bug，可以有效地保持较低的缺陷逃逸率。

# Deployment Time
# 部署时间
This might seem like a weird one, but tracking how long it takes to do an actual deployment is another good metric. One of our applications at Stackify is deployed with Azure worker roles and it takes about an hour to deploy. It is a nightmare. Tracking such things could help identify potential problems. It is much easier to deploy more often when the task of actually doing it is quick.
这一点看起来有些奇怪，但跟踪部署一次所需要花的时间同样是一个好的指标。如果在Stackify中，你的一个程序需要花费一个小时才能部署到Azure上时。这将会是个噩梦。
跟踪这些事情可以帮助你识别潜在的问题。如果部署的很快，也更加容易增加部署频率。

# Lead Time
# 投产周期
If the goal is shipping code quickly, this is a really key DevOps metric. I would define lead time as the amount of time that occurs between starting on a work item until it is deployed. This helps you know that if you started on a new work item today, how long would it take on average until it gets to production. This is also a good metric to help with BizDevOps.
如果目标是快速交付代码的话，这也确实是一个关键的DevOps指标。我对投产周期的定义是，从开始工作到部署之间所需要的时间。
这可以帮你了解，如果今天开始一项新的工作时，多久将能够投产。这也是有助于BizDevOps的一个好的指标。

# Customer Tickets
# 客户支持率
The best and worst indicator of application problems is customer support tickets and feedback. The last thing you want is for your users to find bugs or have problems with your software. Because of this, they also make a good indicator of application quality and performance problems.
应用程序问题的最好和最坏的表现是客户支持和反馈。你最不希望看到的就是你的用户发现bug或者软件的问题。因此，这也就成为了程序质量和性能问题的指示器。

# Automated Tests Pass %
# 自动化测试通过率
To increase velocity, it is highly recommended that your team makes extensive usage of unit and functional testing. Since DevOps relies heavily on automation, tracking how well your automated tests work is a good DevOps metrics. It is good to know how often code changes are causing your tests to break.
为了加快速度，强烈建议你的团队广泛使用单元测试和功能测试。由于DevOps严重依赖自动化，跟踪你的自动化测试工作质量是一个好的DevOps指标。
知道代码的变更多久会导致你的测试会失败是件好事情。

# Defect Escape Rate
# 缺陷逃逸率
Do you know how many software defects are being found in production versus QA? If you want to ship code fast, you need to have confidence that you can find software defects before they get to production. Your defect escape rate is a great DevOps metric to track how often those defects make it to production.
你知道有多少软件的缺陷在声称和QA中被发现？如果想要快速交付代码，你需要有信心能上在生产之前发现软件的缺陷。
你的缺陷逃逸率是非常大的一个指标，用来跟踪这些缺陷在生产中经常发生的情况。

# Availability
# 可用性
The last thing you ever want is for your application to be down. Depending on your type of application and how you deploy it, you may have a little downtime as part of scheduled maintenance. I would suggest tracking that and all unplanned outages.
你最不想要的就是程序停止。根据你的程序类型以及部署方式，可能会需要在维护计划中让程序下线。我建议跟踪这一点，以及所有计划外的停机。

# Service Level Agreements
# 服务等级协议
Most companies have some service level agreement (SLA) that they operate with. It is also important that you track your compliance with your SLAs. Even if there are no formal SLA, there probably are application requirements or expectations to be achieved.
大多数有一些服务等级协议（SLA）。跟踪你的SLA是否合规同样重要。即使没有正式的SLA，也可能需要有对程序的期望。

# Failed Deployments
# 部署失败
We all hope this never happens, but how often do your deployments cause an outage or major issues for your users? Reversing a failed deployment is something we never want to do, but it is something you should always plan for. If you have issues with failed deployments, be sure to track this metric over time. This could also be seen as tracking mean time to failure (MTTF).  
我们都不希望发生，但是对于你们的用户部署过程多久会发生一次中断或者较大的问题？挽救一次失败的部署是我们都不想要做的事情，但总是应该对此有应对措施。如果你们的部署过程有缺陷，一定要对这个指标做追踪。这也应当在平均错误时间（MTTF）中被看到。

# Error Rates
# 错误率
Tracking error rates within your application is super important. Not only are they an indicator of quality problems, but also ongoing performance and uptime related issues. Good exception handling best practices are critical for good software.
跟踪程序的错误率是特别重要的。它不仅仅是质量问题的指示器，也与持续的性能和时间相关的问题有关联。对于好的软件来说良好的异常处理机制是很重要的。

* Bugs – Identify new exceptions being thrown in your code after a deployment.
* Bugs – 识别代码部署后产生的新异常。
* Production issues – Capture issues with database connections, query timeouts, and other related issues.
* 线上问题 – 捕获数据库连接问题，查询超时，以及其他相关问题。

Errors are a fact of life for most applications. At Stackify, we process millions of messages an hour across a couple hundred servers and over a thousand SQL databases. A few errors here and there are just part of the noise of a busy system. It is important that you keep a pulse on your error rates and look for spikes.  
对于大多数程序来说，错误总是存在的。在Stackify，我们在几百台服务器和上千个SQL数据库中处理百万条消息。这里有些错误只是繁忙系统的意外。
重要的是你要把错误率保持在一个频率并且查找一个峰值。

![](https://stackify.com/wp-content/uploads/2017/12/word-image-2.png)

# Application Usage & Traffic
# 应用程序的使用和流量
After a deployment, you want to see if the amount of transactions or users accessing your system looks normal. If you suddenly have no traffic or a giant spike in traffic, something could be wrong.
部署之后，你想要看到会话的数量或者用户访问系统是否正常。如果突然没有了流量或者出现峰值，就可能是出问题了。

The last thing you ever want to see is no traffic at all. You could also see a spike in traffic if you are using microservices and one of your applications is causing a lot more traffic all of a sudden.
你最不希望看到的就是没有任何流量。当你采用服务时，也可能看到有流量的峰值，而一个程序突然有了大量的流量。

# Application Performance
# 应用程序性能
Before you even do a deployment, you should use a tool like Retrace to look for performance problems, hidden errors, and other issues. During and after the deployment, you should also look for any changes in overall application performance.
在你部署之前，应该使用类似Retrace这样的工具查找性能问题、隐藏的问题或者其他问题。在部署期间和之后，你也应该查找是否有性能上的变化。

It might be common after a deployment to see major changes in the usage of specific SQL queries, web service calls, and other application dependencies. Tools like Retrace can provide valuable visualizations like this one below that helps make it easy to spot problems.
在部署之后，可以看到特定的SQL查询、web服务调用和其他程序依赖的主要变化。像Retrace这样的工具可以提供下面可视化的价值评估，以帮助你发现问题。

![](https://stackify.com/wp-content/uploads/2017/12/word-image-3.png)

# Mean Time to Detection (MTTD)
# 平均检测时间（MTTD）
When problems do happen, it is important that you identify them quickly. The last thing you want is to have a major partial or broad system outage and not know about it. Having robust application monitoring and good coverage in place will help you detect issues quickly. Once you detect them, you also have to fix them quickly!
当问题发生后，重要的是能够快速识别出来。你最不想看到是主要功能或者大部分系统宕机并不知道原因。健壮的应用程序监控并且能覆盖到位将有助于你快速定位问题。一旦你定位了问题，就必须快速地修复！

# Mean Time to Recovery (MTTR)
# 平均恢复时间（MTTR）
This metric helps you track how long it takes to recover from failures. A key metric for the business is keeping failures to a minimum and being able to recover from them quickly. It is typically measured in hours and may refer to business hours, not clock hours.
这个指标帮你记录从失败到恢复需要花费多长时间。一个关键的商业指标就是保持错误最小化并能够快速地恢复。通常按小时来计算，但对应的是商业上的小时而不是时钟小时数。

Having good application monitoring tools in place to quickly identify issues and quickly deploy the fix is important to reducing your MTTR.
拥有一个健壮的应用程序监控工具从而快速识别问题并修复和部署对于减少你的平均恢复时间（MTTR）是很重要的。

# Application Metrics
# 应用程序指标
Beyond the DevOps metrics listed above, there are dozens of other metrics you can track that are specific to your applications. Most of them are not necessarily relevant to DevOps in regards to deploying your application. However, they are very critical for monitoring the usage and performance of your applications in production.
除了上面列出来的DevOps指标外，你还可以记录很多其他指标，这些指标都是针对特定程序的。它们中的大多数都在DevOps部署你的应用程序时不是必需的。然而，它们对于应用程序在生产中的使用和性能的监控是非常重要的。

For example, at Stackify, we use custom metrics to track how many log messages are received via our API per minute. This is a critical metric that helps us understand the volume of data flowing through our system. Depending on your application, you may have similar custom metrics that are critical to your application.
例如，在Stackify中，我们利用自定义指标来跟踪每分钟通过API收到的日志消息数量。这是一个重要的指标，它可以帮助我们了解通过我们系统的数据量。根据你的应用程序实际情况，你可以定义类似对于你们来说非常重要的指标。

After a deployment, you will want to keep an eye on all of your critical application metrics to ensure that everything still looks normal.
当部署以后，你就想要关注所有重要的程序指标，以确保是没问题的。

# Summary
# 总结
If you want to take DevOps to the next level, I’m sure that our list of DevOps metrics will help give you some ideas of what to track and improve. The goal of DevOps is collaboration and getting developers more involved in the deployment process and application monitoring.
如果你想要把DevOps实践到更高层次，我相信上面列出的DevOps指标将会有助于你追踪和改进。DevOps的目标是共同协作并让更多的开发者参与到部署和应用程序监控中来。