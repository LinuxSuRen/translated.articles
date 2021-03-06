Selecting a Cloud Provider
云服务商选择

Etsy.com and most of our related services have been hosted in self-managed data centers since the first Etsy site was 
launched in 2005. Earlier this year, we decided to evaluate migrating everything to a cloud hosting solution. 
The decision to run our own hardware in data centers was the right decision at the time, but infrastructure as a service
 (IaaS) and platform as a service (PaaS) offerings have changed dramatically in the intervening years. It was time to 
 reevaluate our decisions. We recently announced that we have selected Google Cloud Platform (GCP) as our cloud provider 
 and are incredibly excited about this decision. This marks a shift for Etsy from infrastructure self-reliance to a 
 best-in-class service provider. This shift allows us to spend less time maintaining our own infrastructure and more 
 time on strategic features and services that make the Etsy marketplace great.
自从2005年Etsy网站开始运营，Etsy.com和大多数相关的服务就被部署在自托管的数据中心。今年早些时候，我们决定评估是否要把所有服务部署到云上。
当时，在我们自己的硬件上运营数据中心是一个正确的决定，基础设施即服务（IaaS）和平台即服务（PaaS）在这些年里已经发生了戏剧性的变化。是时候
重新评估我们的决定了。我们最近宣布选择谷歌云平台（GCP）作为我们的云提供商，而且这是个明智的决定。这标志着Etsy从自托管转为选择了一流的提供商。
这使得我们在维护基础设施上节省了时间，而可以在战略特性和服务上投入更多的精力，从而巩固了Etsy市场。

Although we use the term ‘vendor’ when referring to a cloud provider, we viewed this as much more than a simple vendor 
selection process. We are entering into a partnership and a long-term relationship. The provider that we have chosen is 
going to be a major part of our successful initial migration, as well as a partner in the long-term scalability and 
availability of our site and services. This was not a decision that we wanted to enter into without careful consideration 
and deliberate analysis. This article will walk you through the process by which we vetted and ultimately selected a 
partner. We are not going to cover why we chose to migrate to a cloud hosting provider nor are we going to cover the 
business goals that we have established to measure the success of this project.
尽管我们在提到云提供商时用到了“厂商”的概念，但这不像一个简单的厂商选择的过程。我们会进入一个长期合作伙伴的关系。他们是我们在迁移前期得以成功的
重要部分，也是网站和服务可以长期保持可伸缩性和可用性的合作伙伴。这是我们认真考虑和分析后的决定。本文将会带你一起看我们审查并最终选择合作伙伴的
过程。但不会包括我们为什么要迁移到云上以及商业目标，主要是如何衡量这个项目的成功。

From One, Many
从少到多
While the migration to a cloud hosting provider can be thought of as a single project, it really is one very large 
project made up of many smaller projects. In order to properly evaluate each cloud provider accurately, we needed to 
identify all of the sub-projects, determine the specific requirements of each sub-project, and then use these 
requirements to evaluate the various providers. Also, to scope the entire project, we needed to determine the sequence, 
effort, dependencies, priority, and timing of each sub-project.
而迁移到云托管提供商可以被认为是单一项目，但它确实是由很多较小的项目组成的非常大的项目。为了能够正确、合理地评估每个提供商，我们需要识别出每个
子项目，了解它们的特殊需求，并以此作为评估的依据。而且，为了确定整个项目的范围，我们需要确定顺序、工作量、依赖和每个子项目的时机。

We started by identifying eight major projects, including the production render path for the site, the site’s search 
services, the production support systems such as logging, and the Tier 1 business systems like Jira. We then divided 
these projects further into their component projects—MySQL and Memcached as part of the production render path, for 
example. By the end of this exercise, we had identified over 30 sub-projects. To determine the requirements for each of 
these sub-projects, we needed to gather expertise from around the organization. No one person or project team could 
accurately, or in a timely enough manner, gather all of these requirements. For example, we not only needed to know the 
latency tolerance of our MySQL databases but also our data warehousing requirement for an API to create and delete data. 
To help gather all of these requirements, we used a RACI model to identify subproject ownership.
我们确定了八个主要的项目，包括网站的生产路径，搜索服务，日志等生产支持系统，像Jira这样的一级业务系统。然后，我们把这些工程更进一步拆分成组件，
例如：MySQL和Memcached作为生产路径。通过这样的实践，我们最终确定了30个子项目。为了确定每个子项目的需求，我们需要向各个组织收集专业知识。
没人或者项目团队可以准确及时地收集所有需求。例如：我们不仅仅需要知道MySQL数据库的延时容忍度还包括新增和删除数据API对数据仓库的需求。为了
方便收集所有的需求，我们使用RACI模型来确定子项目的关系。

RACI
The RACI model is used to identify the responsible, accountable, consulted, and informed people for each sub-project. 
We used the following definitions:
RACI模型用来确定责任、义务、咨询和通知每个子项目的人员。我们采用如下的定义：

Responsible – This is the person ultimately responsible for completing the project or initiative.
责任 - 对项目的完成或者发起最终负责的人。
Accountable – This is the person to whom the R is accountable, and who must approve the work before it is okay to complete.
义务 - 也就是R的负责人，他批准后才算完成。
Consulted – These people might have data that is useful in completing the project.
咨询 - 这些人可能会对项目的完成有有用的数据。
Informed – These are people that should be kept informed or notified about the progress of the project but who do not need to approve of any step or artifact.
通知 - 应该通知这些人项目的进度，而不需要他们的批准。
Each Responsible person owned the gathering of requirements and the mapping of dependencies for their sub-project. The 
accountable person ensured the responsible person had the time, resources, and information they needed to complete the 
project and ultimately signed off that it was done.
每个负责人都拥有对他们项目需求的收集和依赖关系的责任。义务人要确保责任人有时间、资源和完成项目所需要的信息，并最终确认完成。
![](https://codeascraft.com/wp-content/uploads/2018/01/RACI.png)

Architectural Review
架构审查
Etsy has long used an architectural review process, whereby any significant change in our environment, whether a 
technology, architecture, or design, undergoes a peer review. As these require a significant contribution of time from 
senior engineers, the preparation for these is not taken lightly. Experts across the organization collaborated to solicit 
diverse viewpoints and frequently produced 30+ page documents for architectural review.
Etsy长期以来都有架构审查的过程，重要的环境改变——不管是技术、架构还是设计，都需要经过同级审查。由于这需要高级工程师贡献大量的时间，因此准备工作
不能掉以轻心。组织之间的专家合作下，不同的观点在架构审核中通常会产生30多页内容。

We determined that properly evaluating various cloud providers required an understanding of the desired end state of 
various parts of our system. For example, our current provisioning is done in our colocation centers using a custom 
toolset as automation to build bare-metal servers and virtual machines (VMs). We also use Chef roles and recipes applied 
on top of provisioned bare-metal servers and VMs. We identified a few key goals for choosing a tool for infrastructure 
creation in the cloud including: greater flexibility, accountability, security, and centralized access control. Our 
provisioning team evaluated several tools against these goals, discussed them, and then proposed new workflows in an 
architecture review. The team concluded by proposing we use Terraform in combination with Packer to build the base OS 
images.
我们发现想要合理地评估很多云服务商，需要明白我们的系统最终要达到的状态。例如：在我们的服务器托管中心，已经通过一套工具实现了自动化构建裸服务器和虚拟机。
我们还使用Chef管理和配置裸服务器和虚拟机。我们定义了一些关键指标用于选择在云环境中创建基础设施的工具，包括：高灵活性、可靠性、安全性和集中访
问控制。我们的预备团队借助这些指标评估了几个工具，在架构审查中讨论并提出了新的流程。根据提议，我们决定使用Terraform中的Packer来做基础操作系统
镜像的编排构建。

Ultimately, we held 25 architectural reviews for major components of our system and environments. We also held eight 
additional workshops for certain components we felt required more in-depth review. In particular, we reviewed the 
backend systems involved in generating pages of etsy.com (a.k.a. the production render path) with a greater focus on 
latency constraints and failure modes. These architectural reviews and workshops resulted in a set of requirements 
that we could use to evaluate the different cloud providers.
最终，对我们系统和环境的主要组件做了25次架构审查。而且对认为需要深入审查的八个组件做了研讨。特别地，我们审查了etsy.com生成页面的后端系统
，主要关注的是延时约束和故障模式。这些审查和研讨会得出了一套用于评估不同云服务商的需求。

How it Fits Together
如何做整合
Once we had a firm-ish set of requirements for the major components of the system, we began outlining the order of 
migration. In order to do this we needed to determine how the components were all interrelated. This required us to 
graph dependencies, which involved teams of engineers huddled around whiteboards discussing how systems and subsystems 
interact.
一旦我们有了系统主要组件的需求，就开始规划迁移的顺序。为了做到这一点，需要确定这些组件之间是如何关联的。这需要我们相关的工程师一起讨论系统
和子系统之间的交互并在白板上画出依赖关系。
![](https://codeascraft.com/wp-content/uploads/2018/01/dependency_map.jpg)

The dependency graphing exercises helped us identify and document all of the supporting parts of each major component, 
such as the scheduling and monitoring tools, caching pools, and streaming services. These sessions ultimately resulting 
in high-level estimates of project effort and timing, mapped in Gantt-style project plans.
画依赖的过程有助于我们识别并记录每个主要组件的支撑部分，例如：调度和监控工具、缓存池和流式服务。这些会议最终得出了项目工作和时间的高层预估，
并印射到了甘特式的项目计划中。
![](https://codeascraft.com/wp-content/uploads/2018/01/project_plan.png)

Experimentation
实验
Earlier in the year, we ran some of our Hadoop jobs on one of the cloud providers’ services, which gave us a very good 
understanding of the effort required to migrate and the challenges that we would face in doing so at scale. For this 
initial experiment, however, we did not use GCP, so we didn’t have the same level of understanding of the cloud 
provider we ultimately chose.
在今年早些时候，我们在云服务商提供的服务上运行了一些Hadoop任务，这有助于我们理解迁移的需求以及在伸缩时面临的挑战。然而，在这次实验中，我们没有
使用GCP，因此没有对云服务商最终选择上得出一致的理解。

We therefore undertook an experiment to enable batch jobs to run on GCP utilizing Dataproc and Dataflow. We learned a 
number of lessons from this exercise including that some of the GCP services were still in alpha release and not 
suitable for the workloads and SLAs that we required. This was the first of many similar decisions we’ll need to 
make: use a cloud service or build our own tool. In this case, we opted to implement Airflow on GCP VMs. To help us 
make these decisions we evaluated the priority of various criteria, such as vendor support of the service, vendor 
independence, and impact of this decision on other teams.
因此，我们做了一项实验，基于GCP利用Dataproc和Dataflow运行批量任务。通过这次实验，我们了解到一些GCP服务仍然在测试阶段，并不适合我们要求的
工作负载和SLAs。这是我们将会做出的很多相似决定的第一个：使用云服务还是构建自己的工具。在这个情况下，我们选择在GCP虚拟机上实现Airflow。为了
帮助我们做出这些决定，我们评估了各种标准的优先级，例如：厂商支持的服务，厂商的自主性，以及这些决定对其他团队的影响。

There is no right answer to these questions. We believe that these questions and criteria need to be identified for each 
team to consider them and make the best decision possible. We are also not averse to revisiting these decisions in the 
future when we have more information or alpha and beta projects roll out into general availability (GA).
这些问题没有标准答案。我们相信这些问题和标准，需要每个团队根据各自的情况考虑，并尽可能作出最好的选择。我们不希望当得到更多信息或者测试版本的项目
转到GA版本后再次做这些决定。

Meetings
会议
Over the course of five months, we met with the Google team multiple times. Each of these meetings had clearly defined 
goals, ranging from short general introductions of team members to full day deep dives on various topics such as using 
container services in the cloud. In addition to providing key information, these meetings also reinforced a shared 
engineering culture between Etsy and Google.
在过去五个月的时间里，我们和谷歌的团队进行了多次会议。每次会议都有明确的目标，从简单的团队成员介绍到整天多个话题的讨论，例如在云上使用容器服务。
除了提供关键信息外，这些会议还加强了Etsy和谷歌工程师文化交流。

We also met with reference customers to discuss what they learned migrating to the cloud and what to look out for on our 
journey. The time spent with these companies was unbelievably worthwhile and demonstrated the amazing open culture that 
is pervasive among technology companies in NY.
我们还和相关客户讨论了他们在向云迁移时学习到的经验，并探索自己的方向。和这些公司在一起的时间是非常值得的，并且在纽约的科技公司里这种开放的文化
是非常普遍的。

We also met with key stakeholders within Etsy to keep them informed of our progress and to invite their input on key 
directional decisions such as how to balance the mitigation of financial risk with the time-discounted value of cost 
commitments. Doing so provided decision makers with a shared familiarity and comfort with the process and eliminated 
the possibility of surprise at the final decision point.
我们还和Etsy内部的相关利益人交流，使他们了解我们的进展情况，并邀请他们在关键问题上发表意见，例如如何平衡缓解财务风险与成本的时间贴现。

The Decision
决定
By this point we had thousands of data points from stakeholders, vendors, and engineering teams. We leveraged a tool 
called a decision matrix that is used to evaluate multiple-criteria decision problems. This tool helped organize and 
prioritize this data into something that could be used to impartially evaluate each vendor’s offering and proposal. 
Our decision matrix contained over 200 factors prioritized by 1,400 weights and evaluated more than 400 scores.
基于我们已经从相关利益人、厂商和工程师团队获得了成千上万的点子。我们使用决策矩阵的方法来评估有多个判断条件的问题。这个工具帮助组织和优化每个厂商
的提议，并作出公平的评估。我们的决策矩阵包括200多个因子，优先级为1400个权重，并评估了超过400的分数。

This process began with identifying the overarching functional requirements. We identified relationship, cost, ease of 
use, value-added services, security, locations, and connectivity as the seven top-level functional requirement areas. We 
then listed every one of the 200+ customer requirements (customers referring to engineering teams and stakeholders) and 
weighted them by how well each supported the overall functional requirements. We used a 0, 1, 3, 9 scale to indicate
这个过程是从识别重要的功能性需求开始的。我们确定了关系、成本、易用性、服务增值、安全、位置以及连接七个顶层功能的需求。我们列出了200多个客户的每个
需求（客户指的是工程师团队和相关利益人），并通过如何很好地支持全部的功能性需求作为权重。我们用0、1、3、9来标识
![](https://codeascraft.com/wp-content/uploads/2018/01/example_scale-768x201.png) 
the level of support. For example, the customer requirement of “autoscaling support” was weighted as a 9 for 
cost (as it would help reduce cost by dynamically scaling our compute clusters up and down), a 9 for ease of 
use (as it would keep us from having to manually spin up and down VMs), a 3 for value-added services (as it is an 
additional service offered beyond just basic compute and storage but it isn’t terribly sophisticated), and a 0 for 
supporting other functional requirements. Multiple engineering teams performed an in-depth evaluation and weighting 
of these factors. Clear priorities began to emerge as a result of the nonlinear weighting scale, which forces overly 
conservative scorers to make tough decisions on what really matters.
支持的级别。例如：“自动伸缩”需求的权重是9（通过自动伸缩我们的集群启动和关闭有助于降低成本），易用性也是9（这可以让我们手动启动和关闭虚拟机），
服务增值是3（作为增值服务只是提供基本的计算和存储，并不是特别复杂），其他功能性需求则是0。多个工程师团队对这些因素做了深入的评估和权衡。明确
优先的事项并不是以线性增长的，这使得在决定哪些事情是真正重要的时显得比较困难。
![](https://codeascraft.com/wp-content/uploads/2018/01/qfd.png)  

We then used these weighted requirements to rank each vendor’s offering. We again used a 0, 1, 3, 9 scale for how well 
each cloud vendor met the requirement. Continuing with our “autoscaling support” example, we scored each cloud vendor a 
9 for meeting this requirement completely in that all the vendors we evaluated provided support for autoscaling compute 
resources as native functionality. The total scores for each vendor reached over 50,000 points with GCP exceeding the 
others by more than 10%.
然后，我们利用这些加权对每个厂商的产品进行排名。我们还是利用0、1、3、9来对每个云厂商在需求的实现上做评分。继续以我们的“自动伸缩”为例，我们给
每个完整地实现了自动伸缩计算资源的厂商打9分。每个厂商的总分分数都超过了50,000点，并且GCP超过了其他的10%。
![](https://codeascraft.com/wp-content/uploads/2018/01/decision_matrix.png)

As is likely obvious from the context, it should be noted that Etsy’s decision matrix (filled with Etsy’s requirements, 
ranked with Etsy’s weights by Etsy’s engineers) is applicable only to Etsy. We are not endorsing this decision as right 
for you or your organization, but rather we are attempting to provide you with insight into how we approach decisions 
such as these that are strategic and important to us.
很明显，根据上文Etsy的决策矩阵应该只适用于Etsy（根据Etsy的需求填写，由Etsy的工程师做权重排名）。我们不认为这个决定对于你或者你们组织是正确的，
但是我们尝试给你提供我们的决策过程，这些对我们来说是战略而且重要。

Just the beginning
只是开始
Now, the fun and work begin. This process took us the better part of five months with a full-time technical project 
manager, dozens of engineers and engineering managers, as well as several lawyers, finance personnel, and sourcing 
experts working on this part or in some cases full time. Needless to say, this was not an insignificant effort but 
really just the beginning of a multi-year project to migrate to GCP. We have an aggressive timeline to achieve our 
migration in about two years. We will do this while continuing to focus on innovative product features and minimizing 
risk during the transition period. We look forward to the opportunities that moving to GCP provides us and are 
particularly excited about this transformational change allowing us to focus more on core, strategic services for the 
Etsy marketplace by partnering with a best-in-class service provider.
现在，乐趣和工作开始了。这个过程我们花费了五个月，是一个全职的技术项目。数十名工程师和项目管理人员，还有几个律师、财务人员在一些情况下会全职
做这些工作。不必说，这不是无关紧要的工作，而是一个转移到GCP的多年项目的开始。我们有一个积极的时间表，要在两年内实现我们的目标。我们会继续关注
创新的产品特色上这么做，并在过度期间最小化风险。我们期待迁移到GCP后带来的机遇，尤其兴奋的是，在转型过程中允许我们更多地关注核心，通过和一流的
服务提供商在Etsy市场上的战略服务。

https://codeascraft.com/2018/01/04/selecting-a-cloud-provider/