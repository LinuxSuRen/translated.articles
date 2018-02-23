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
自从2005年Etsy网站开始运营，Etsy.com和大多数相关的服务就被部署在自我管理的数据中心。今年早些时候，我们决定评估是否要把所有服务部署到云上。
那时候，在我们自己的硬件上运营数据中心是一个正确的决定，基础设施即服务（IaaS）和平台即服务（PaaS）在这些年里已经发生了戏剧性的变化。是时候
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
而迁移到云托管提供商可以被认为是单一项目，它确实是由很多较小的项目组成的非常大的项目。为了能够正确、合理地评估每个提供商，我们需要识别出每个
子项目，了解它们的特殊需求，并以此作为评估的依据。而且，为了确定整个项目的范围，我们需要确定顺序、效果、依赖和每个子项目的时机。

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
没有人或者项目团队可以准确及时地收集所有需求。例如：我们不仅仅需要知道MySQL数据库的延时容忍度还包括新增和删除数据API对数据仓库的需求。为了
帮助收集所有的需求，我们使用RACI模型来确定子项目的关系。

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

Architectural Review
架构审查
Etsy has long used an architectural review process, whereby any significant change in our environment, whether a 
technology, architecture, or design, undergoes a peer review. As these require a significant contribution of time from 
senior engineers, the preparation for these is not taken lightly. Experts across the organization collaborated to solicit 
diverse viewpoints and frequently produced 30+ page documents for architectural review.
Etsy长期依赖都有架构审查的过程，重要的环境改变——不管是技术、架构还是设计，都需要经过同级审查。由于这需要高级工程师贡献大量的时间，因此准备工作
不能掉以轻心。组织之间的专家合作下，不同的观点在架构审核中通常会产生30多页内容。

We determined that properly evaluating various cloud providers required an understanding of the desired end state of 
various parts of our system. For example, our current provisioning is done in our colocation centers using a custom 
toolset as automation to build bare-metal servers and virtual machines (VMs). We also use Chef roles and recipes applied 
on top of provisioned bare-metal servers and VMs. We identified a few key goals for choosing a tool for infrastructure 
creation in the cloud including: greater flexibility, accountability, security, and centralized access control. Our 
provisioning team evaluated several tools against these goals, discussed them, and then proposed new workflows in an 
architecture review. The team concluded by proposing we use Terraform in combination with Packer to build the base OS 
images.

Ultimately, we held 25 architectural reviews for major components of our system and environments. We also held eight 
additional workshops for certain components we felt required more in-depth review. In particular, we reviewed the 
backend systems involved in generating pages of etsy.com (a.k.a. the production render path) with a greater focus on 
latency constraints and failure modes. These architectural reviews and workshops resulted in a set of requirements 
that we could use to evaluate the different cloud providers.

How it Fits Together
Once we had a firm-ish set of requirements for the major components of the system, we began outlining the order of 
migration. In order to do this we needed to determine how the components were all interrelated. This required us to 
graph dependencies, which involved teams of engineers huddled around whiteboards discussing how systems and subsystems 
interact.

The dependency graphing exercises helped us identify and document all of the supporting parts of each major component, 
such as the scheduling and monitoring tools, caching pools, and streaming services. These sessions ultimately resulting 
This was not a decisionin high-level estimates of project effort and timing, mapped in Gantt-style project plans.

Experimentation
实验
Earlier in the year, we ran some of our Hadoop jobs on one of the cloud providers’ services, which gave us a very good 
understanding of the effort required to migrate and the challenges that we would face in doing so at scale. For this 
initial experiment, however, we did not use GCP, so we didn’t have the same level of understanding of the cloud 
provider we ultimately chose.

We therefore undertook an experiment to enable batch jobs to run on GCP utilizing Dataproc and Dataflow. We learned a 
number of lessons from this exercise including that some of the GCP services were still in alpha release and not 
suitable for the workloads and SLAs that we required. This was the first of many similar decisions we’ll need to 
make: use a cloud service or build our own tool. In this case, we opted to implement Airflow on GCP VMs. To help us 
make these decisions we evaluated the priority of various criteria, such as vendor support of the service, vendor 
independence, and impact of this decision on other teams.

There is no right answer to these questions. We believe that these questions and criteria need to be identified for each 
team to consider them and make the best decision possible. We are also not averse to revisiting these decisions in the 
future when we have more information or alpha and beta projects roll out into general availability (GA).

Meetings
会议
Over the course of five months, we met with the Google team multiple times. Each of these meetings had clearly defined 
goals, ranging from short general introductions of team members to full day deep dives on various topics such as using 
container services in the cloud. In addition to providing key information, these meetings also reinforced a shared 
engineering culture between Etsy and Google.

We also met with reference customers to discuss what they learned migrating to the cloud and what to look out for on our 
journey. The time spent with these companies was unbelievably worthwhile and demonstrated the amazing open culture that 
is pervasive among technology companies in NY.

We also met with key stakeholders within Etsy to keep them informed of our progress and to invite their input on key 
directional decisions such as how to balance the mitigation of financial risk with the time-discounted value of cost 
commitments. Doing so provided decision makers with a shared familiarity and comfort with the process and eliminated 
the possibility of surprise at the final decision point.

The Decision
决定
By this point we had thousands of data points from stakeholders, vendors, and engineering teams. We leveraged a tool 
called a decision matrix that is used to evaluate multiple-criteria decision problems. This tool helped organize and 
prioritize this data into something that could be used to impartially evaluate each vendor’s offering and proposal. 
Our decision matrix contained over 200 factors prioritized by 1,400 weights and evaluated more than 400 scores.

This process began with identifying the overarching functional requirements. We identified relationship, cost, ease of 
use, value-added services, security, locations, and connectivity as the seven top-level functional requirement areas. We 
then listed every one of the 200+ customer requirements (customers referring to engineering teams and stakeholders) and 
weighted them by how well each supported the overall functional requirements. We used a 0, 1, 3, 9 scale to indicate 
the level of support. For example, the customer requirement of “autoscaling support” was weighted as a 9 for 
cost (as it would help reduce cost by dynamically scaling our compute clusters up and down), a 9 for ease of 
use (as it would keep us from having to manually spin up and down VMs), a 3 for value-added services (as it is an 
additional service offered beyond just basic compute and storage but it isn’t terribly sophisticated), and a 0 for 
supporting other functional requirements. Multiple engineering teams performed an in-depth evaluation and weighting 
of these factors. Clear priorities began to emerge as a result of the nonlinear weighting scale, which forces overly 
conservative scorers to make tough decisions on what really matters.  

We then used these weighted requirements to rank each vendor’s offering. We again used a 0, 1, 3, 9 scale for how well 
each cloud vendor met the requirement. Continuing with our “autoscaling support” example, we scored each cloud vendor a 
9 for meeting this requirement completely in that all the vendors we evaluated provided support for autoscaling compute 
resources as native functionality. The total scores for each vendor reached over 50,000 points with GCP exceeding the 
others by more than 10%.

As is likely obvious from the context, it should be noted that Etsy’s decision matrix (filled with Etsy’s requirements, 
ranked with Etsy’s weights by Etsy’s engineers) is applicable only to Etsy. We are not endorsing this decision as right 
for you or your organization, but rather we are attempting to provide you with insight into how we approach decisions 
such as these that are strategic and important to us.

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

https://codeascraft.com/2018/01/04/selecting-a-cloud-provider/