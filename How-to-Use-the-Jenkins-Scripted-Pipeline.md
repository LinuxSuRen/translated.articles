How to Use the Jenkins Scripted Pipeline
如何使用Jenkins的脚本化流水线（Pipeline）

In this simple tutorial, you'll learn about Jenkins pipeline as code and see some guidelines on how to develop your pipeline scripts.  
在这篇简单的教程中，你将会学习到Jenkins的流水线即代码，以及如何开发流水线脚本的指导。  

Jenkins is an open source continuous integration server that provides the ability to continuously perform automated builds and tests. Several tasks can be controlled and monitored by Jenkins, including pulling code from a repository, performing static code analysis, building your project, executing unit tests, automated tests and/or performance tests, and finally, deploying your application. These tasks typically conform a continuous delivery pipeline.  
Jenkins是一个开源持续集成服务器，它可以提供持续执行自动化构建和测试的能力。Jenkins可以控制和监控多种任务，包括：拉取代码、静态代码分析、构建工程、执行单元测试、自动化或者性能测试，最后部署应用。这些任务通常是一个持续部署流水线。  

Pipelines are a suite of Jenkins plugins. Pipelines can be seen as a sequence of stages to perform the tasks just detailed, among others, thus providing continuous releases of your application. The concept "continuous" is relative to your application and/or environment: In some cases, releases can be performed on a daily basis while for others could be weekly, depending on your business needs. In some situations - a critical fix, for example - it would be desirable to have your environment ready to release your application as soon as possible. Pipelines provide a way to do this through an automated process.  
流水线（Pipeline）是Jenkins的一套插件。流水线可以认为是执行任务的一系列阶段，它可以持续地发布你的应用。“持续”的概念是相对于你的应用环境来说的：在某些情况下，持续发布可以是每天也可以是每周，这取决于你的业务需要。在特定场景中，例如严重bug的修复，就需要在环境准备好后尽快地发布程序。流水线提供了自动化这些过程的方法。

In Jenkins, Pipelines are specified by using a specific DSL following almost the same structure as Groovy to specify its statements and expressions. This makes pipelines easy to use for Groovy savants.  
在Jenkins中，流水线使用DSL来定义语句和表达式，和Groovy的语法结构相同。这使得流水线对于了解Groovy的人来说很简单。

Starting with Jenkins 2.0, the pipeline functionality comes right out of the box, meaning that no configuration needs to be made to be able to create them. Another improvement is that pipelines can be specified as code, enabling you to develop a pipeline script and add it to your code repository so you can version it.  
从Jenkins的2.0版本开始，流水线功能变得开箱即用，不需要特殊的配置。另外一个改进的地方是，流水线可以被当作代码，使你开发出来的脚本可以利用版本管理工具控制它。

By using script, releases of code can be pushed to the repository along
 with pipeline scripts in order to test specific functionalities just developed. This is done to ensure no bugs were introduced and that the application can perform with at least the same response times as the previous code. So, you can develop your pipeline script to execute automated tests only for specific flows and run performance tests by invoking Apache JMeter™ only for the desired test cases.  
利用流水线脚本，可以把刚开发出来的特定功能代码发布后测试。这是为了不引入新的bug，保证程序可以像之前一样正确执行。因此，你可以开发流水线脚本来执行指定流程的自动化测试，对特定场景利用Apache JMeter™ 执行性能测试。

In this post, we will discuss the Scripted Pipeline (Pipeline as Code) in detail, while explaining its structure and providing examples of how to use it. More information on using Jenkins Pipelines with JMeter can be found in the blog post Continuous Integration 101: How to Run JMeter With Jenkins. Also, the post How to Run a JMeter Test with Jenkins 2.0 Pipelines and GitHub provides an example of how to run JMeter tests by using a Pipeline script.
本文，我们会讨论脚本化流水线（流水线即代码）的细节，并解释它的结构，提供一些使用示例。更多有关在Jenkins中使用JMeter的信息，可以在持续集成入门的博文中找到：如何在Jenkin中运行JMeter。同时，文章还介绍了如何利用Jenkins2.0的流水线来运行JMeter测试，并在Github中提供了例子。

With the introduction of the Pipeline, Jenkins added an embedded Groovy engine, making Groovy the scripting language in the Pipeline's DSL.
随着流水线的引入，Jenkins提供了一个嵌入式的Groovy引擎，使得Groovy成为了流水线的DSL脚本语言。

Here are the steps you need to take to set up a Jenkins Pipeline.
这里是设置Jenkins流水线的步骤。

1. First, log on to your Jenkins server and select "New Item" from the left panel:
1. 首先，登陆到你的Jenkins服务器，并从左侧面板选择“New Item”：
![](https://cdn2.hubspot.net/hubfs/208250/Blog_Images/pipe1.png)

2. Next, enter a name for your pipeline and select "Pipeline" from the options. Click "Ok" to proceed to the next step:
2. 下一步，输入名称并选择“Pipelie“类型。点击”OK“后进入下一步：
![](https://cdn2.hubspot.net/hubfs/208250/Blog_Images/pipe2.png)

3. You can now start working your Pipeline script:
3. 你可以开始写流水线脚本了：
![](https://cdn2.hubspot.net/hubfs/208250/Blog_Images/pipe3.png)

The red box in the middle is where you can start writing your script, which will be explained now.
你可以在中间红色框里写脚本，这也是下面要解释的。

Pipelines have specific sentences or elements to define script sections, which follow the Groovy syntax.
流水线用特殊的语句或者元素定义章节，这遵循Groovy语法。

Node Blocks
节点块
The first block to be defined is the "node:"
首先定义的块是“node：”

A "node" is part of the Jenkins distributed mode architecture, where the workload can be delegated to multiple "agent" nodes. A "master" node handles all the tasks in your environment. Jenkins agent nodes offloads builds from the master node, thus performing all the pipeline work specified in the node block. Detailed information on this can be found at Jenkins Distributed builds.
“node”是Jenkins分布式架构的一部分，它可以把负载分布到多个“agent”节点。“maerer”节点处理所有的环境。Jenkins代理节点从master节点上取得构建任务，然后根据node块指定的节点上执行所有任务。更多信息可以在Jenkins分布式构建中找到。

This block is not mandatory but it is desired and can be considered as a good practice, since with the code included in this block, Jenkins will schedule and run all the steps once any node is available and creates a specific workspace directory.


Stage Blocks
The next required section is the "stage:"

Your pipeline will consist of several steps that can be grouped in stages. Among these stages you might have:

Pull code from the repository
Build your project
Deploy your application
Perform functional tests
Perform performance tests
Each of the these can include more than one action. For example, a stage to deploy your application can consist of copying the files to a specific environment for functional tests and to a dedicated server for performance tests; and once files are copied successfully, proceed to deploy it.

Each stage block specifies the tasks to be performed. For example, a full scripted pipeline might be:

This script has the following stages:

Build stage:
Selenium tests stage:
dir(automation_path): Changes the current directory to the value set on the automation_path variable.
bat "mvn clean test ... ": Invokes maven to perform tests specified in the suite "SMOKE_TEST" and using the values defined on "QA". Also, the "clean" flag will clean the build.
Stage blocks are also optional, but they are recommended because they provide an organized way of specifying tasks to be executed in the script.

Jenkins provides an interface that generates pipeline sentences for predefined actions that can be added to any of the script stages. On your pipeline script page, click on "Pipeline Syntax" to access the following page:
![](https://cdn2.hubspot.net/hubfs/208250/Blog_Images/pipe4.png)

For example, to create a script command to execute a windows batch file, select the following:
![](https://cdn2.hubspot.net/hubfs/208250/Blog_Images/pipe5.png)

Clicking on "Generate Pipeline Script" will create the desired sentence that can be added to your script right away.

Pipeline as code is based on the idea of being able to add the pipeline script to a code repository for source control and versioning. The text file containing the code of your pipeline is also known as a Jenkinsfile.

Writing your pipeline into a Jenkins file and make it part of your application repository for source control has several advantages: it can be reviewed/edited by other team members and the file can be versioned and included with your application builds.

Your Jenkinsfile can be edited through the Jenkins web interface or with a text editor, and you can also edit it with your prefered IDE, thus making it part of your project. Then, you can configure Jenkins to automatically poll your repo, while triggering new builds when updates to it are detected. This can be done through the following screen on your Project configuration under "Build triggers" section:
![](https://cdn2.hubspot.net/hubfs/208250/Blog_Images/pipe6.png)

Enabling "Poll SCM", allows you to enter a cron-like expression in the Schedule text box. Configuring Jenkins to poll your repo is not a clean and efficient way to retrieve updates. Instead, Git Hooks is a neat way of doing it. The document at Customizing Git - Git Hooks provides information on how to configure it.

Jenkins limits the execution of any Groovy script by providing a sandbox. The option "Use Groovy Sandbox", shown below, is available in the Pipeline tab, and it allows the scripts to be run by any user without requiring administrator privileges. In this case, the script is run only by using the internal accessible APIs (that allow you to develop your script by using Groovy).
![](https://cdn2.hubspot.net/hubfs/208250/Blog_Images/pipe7.png)

When unchecked, if the script has operations that require approval, an administrator will have to provide them. This method is known as "Script approval". By default, all Jenkins pipelines run in a Groovy sandbox. If the option is checked and unauthorized operations are used, the script will fail when run. Both the whitelist and the blacklist of functions can be checked at Script Security's built-in list. Please refer to In-process Script Approval for more information on this topic.

One of the latest Pipeline improvements is the Jenkins Declarative Pipeline, which is a bit different than the Scripted Pipeline that we have been discussing. Both are implementations of the pipeline as code, but the Declarative way is designed to make it easier to develop and maintain your code by providing a more meaningful syntax. These two enhancements are achieved by adding syntax elements allowing you to define a different pipeline skeleton.

Basically, a scripted pipeline has the following skeleton:

On the other hand, a declarative pipeline can be written by using more elements, as shown next:

The script has the elements "pipeline", "agent" and "steps" which are specific to Declarative Pipeline syntax; "stage" is common to both Declarative and Scripted; and finally, node" is specific for the Scripted one.

"Pipeline" defines the block that will contain all the script content.
"Agent" defines where the pipeline will be run, similar to the "node" for the scripted one.
"Stages" contains all of the stages.
In this blog, we have reviewed Jenkins pipeline as code. We also provided guidelines on how to develop your pipeline scripts along with its advantages. For full documentation please refer to Jenkins pipeline.

Learn how to use Jenkins for all of your testing needs for free from our Continuous Testing Academy.

You can also integrate BlazeMeter into your Jenkins Pipeline. Try out running your performance tests in BlazeMeter by requesting a demo or putting your URL in the box below, and your test will start in minutes.