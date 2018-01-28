10 Ways You're Doing DevOps Wrong  
DevOps实践的10个误区

The term DevOps is getting a lot of attention these days, and for good reason: adopting DevOps practices helps teams work more efficiently, ship better code and make customers happier. But along with the term’s increasing popularity, we’ve also seen some common pitfalls teams attempting to “do DevOps” fall into.  
DevOps的理念由于它的优势，在近期受到很多关注，它可以使得团队更加高效，交付高质量的代码，并让客户更加满意。但是，随着这个理念的流行，在尝试“DevOps”时
走进了一些常见的误区。  

(This list is based on the webinar ‘DevOps: You’re Doing It Wrong’ that we hosted in November featuring our CTO Rob Zuber and Andrew Homeyer, founder of Waffle.io.)  
（下面的列表是基于我们的CTO Rob Zuber和Andrew Homeyer在Waffle.io上十一月的研讨会“DevOps：实践误区”总结出来的）

# 1.You have a “DevOps” team
# 1.你有一个“DevOps”团队

The concept of DevOps was coined to counteract the “wall mentality” that often exists between development and operations teams, as a way to imagine those teams working more closely together and to see them embracing some of each other’s practices. So when done right, DevOps is a cultural shift adopted by your entire engineering organization—not one team brought on to “do DevOps.” The real challenge of DevOps is getting your developers to think like operators and vice versa.  
DevOps旨在打破经常存在与研发和运维之间的“沟通障碍”，想象下这些团队之间紧密合作，并互相学习各自的实践经验。所以，如果正确地实践了的话，DevOps会被
当作一种文化在整个团队中被接受，而不是某个团队在“承担DevOps任务”。DevOps真正的挑战是，如何让你的研发团队像运维一样思考问题，反之亦然。

# 2.You’ve stopped trying to tighten your release cycles
# 2.不再尝试缩短你的发版周期

If DevOps means shipping fast and often, how fast is fast enough? It really depends. Moving to DevOps is about gradually getting closer to a fully continuous deployment model. If you’re in an enterprise and shipping every six months, eight weeks probably feels really fast. But if you’re a startup, eight weeks is a sign that you’re probably delivering a ton of work at once. Instead of measuring how often you release, start measuring how painful each release is. When something is finished, can you deploy it? If the answer is no, what can you do to remove blocks? Can you chunk code into smaller pieces? What about adding feature flags or toggles? Eventually, deploying code should be a non-event. While eight weeks may be the goal for larger organizations, we tend to see a series of thresholds: once a team is deploying weekly, it’s easier to move to a nightly deploy. After that, we start to see deploys quickly ramp to 20 to 30 times a day. This is when things really start to get continuous.  
如果DevOps意味着快速、频繁迭代，那么多块才够呢？这确实要依据情况而定向DevOps靠拢就是在逐渐地接近全面的持续研发模式。如果你所在的企业内容，迭代周期是
六个月，那么可能感觉八周就真的很快了。但如果你处在创业阶段，八周意味着你每次交付需要做的工作太多。开始回顾一下每次发版时有多痛苦，而不是多久才能发
一次版。当某件事情完成后，你会部署吗？如果答案是否定的，那么怎么做才能移除这个障碍呢？你可以把大型的工程代码分成一些较小的吗？增加一些特性标签呢？
最终，部署将不再是什么大事。可能对于大型组织而言，八周可能就是他们的目标。让我们来看一些指标：当一个团队是每周发版一次时，他们更容易做到每晚发一次。
之后，开始看到部署可以做到每天20到30次。当到了这种程序，就开始做到真正的持续迭代了。

# 3.You treat your development team as a cost center
# 3.你把研发当作了成本中心

Staffing is expensive, and developers can be some of the most expensive staff a company employs. Many organizations view this expense as something to be contained, but this isn’t the right way to think about it. Instead of thinking solely about cost, companies should be focusing on maximizing developer productivity. The best way to do that is to ensure developers are doing work they’re excited about. Here’s the thing: engineers joined your organization because they wanted to solve interesting problems, namely: the problem of your business. So the best thing you can do is remove everything that stops them from working on that problem. The biggest offender? Ineffective tooling. When developers ship in fast cycles and see their work’s impact on customers, they take more ownership of their code, and are more motivated to put out the best quality work they can. By providing them with frictionless tooling and a feedback-rich work environment, you are maximizing your return on your developer investment.
人员的成本很大，而研发人员的成本则是最大的。很多组织认为这是一种可控的成本，但这不是正确的思路。公司应该关注如何最大化研发的产出，而不是成本。
最好的办法就是，就是让研发去做他们感兴趣的事情。事实上，工程师加入你们的组织的原因，就是想要解决感兴趣的问题，也就是你们的业务问题。因此，你最应该
做的事情，就是排除一切会阻碍他们解决这些问题的事情。最大的罪恶？就是低效率的工具。当研发人员进行快速迭代时，如果能看到他们的成果对客户的影响。那么，
他们就会对自己的代码更加有主人翁意识，并尽力提高质量。给他们提供好用的工具，以及有很对反馈的环境，就可以最大化你在研发人员上的投资。

# 4.You’re doing undifferentiated heavy lifting by building everything yourself
# 4.任何繁重的事情都亲自做而不作区分

Undifferentiated heavy lifting refers to any hard work that takes up your time but isn’t core to your business. As an extreme example, you wouldn’t build a new email program because you want to send emails to your coworkers; you would sign up for Gmail. Likewise, you wouldn’t harvest your own coffee beans because you need caffeine to work. When you’re in the build vs. buy debate, ask yourself, “does doing this work in-house deliver immediate value to our customers? Is this the secret sauce of our business that we cannot possibly outsource?” If the answer to one or both of those questions is no, then think about bringing in a tool. Other people have made your undifferentiated heavy lifting into their business. So stand on the shoulders of those who have already done the work and focus on the core of your business.  
对任何繁重的事情都亲自来做，而不进行区分，这样会占用你的很多时间，但这不一定是你的核心业务。举一个极端的例子，当你想要给同事发送邮件时，可以选择
开发出一个新的邮件程序，也可以注册Gmail。同样地，你并不会由于工作时需要就自己去种植咖啡豆。当你在犹豫自建还是购买时，请思考“自己做这件事情对我们的客户
产生直接的价值吗？由于是我们的商业机密而不能购买吗？如果其中任何一个答案是否定的，就可以考虑利用一个工具来做。这些复杂的事情已经有人在他们的业务中
完成了。所以，你应该站在巨人的肩膀上，关注自己的核心业务。

# 5.You don’t have any tests
# 5.不做任何测试

The business imperative behind DevOps is that teams working together can move faster. One way to speed up delivery cadence is by reducing the paranoia factor when deploying new code via automated tests. Shifting the burden of validation away from manual testing into automated tests is a time investment, but it’s one that lets you deploy code exponentially faster. Automated testing buys you assurance that you’re checking exactly what you checked last time, and keeps you feeling secure even when others have made changes in the codebase.  
DevOps产生的背景是：团队合作更高效。加快交付节奏的一种方法是，部署通过了自动化测试的新代码，会减少一些奇葩的因素。当把手工测试中的部分验证工作转移
为自动化测试时，需要一定的时间投入。当它会使得你在部署前的测试速度程指数加快。自动化测试能保证上次检查过的部分亦然是正确的，并既是码线已经发生变化
亦然会令你感到安全。

# 6.You have too many tests
# 6.做过多的测试

Are more tests always better? Maybe. On one of Andrew [Homeyer, of Wafflie.io]’s previous teams, a suite of Selenium webdriver tests took 8 hours to run. And that suite included several non-deterministic tests that would sometimes fail for random reasons. Are tests like that improving your ability to confidently deploy? Probably not. A better question than “How many tests do you have?” would be “Do you feel comfortable walking away from your computer after you merge to master?” Having a lean suite of fast, non-flaky tests focused on your core business value will give you the confidence to deploy without fear.  
测试越多越好吗？可能吧，在Andrew的一个团队中，一套基于Selenium的自动化测试需要运行8个小时。这些测试包含一些不确定性，可能随机地发生失败。像这样的
测试能让你对部署很自信吗？可能不会吧。思考”到底需要多少测试“，不如想一下”代码后并到master后怎么做才能让你感到放心“。有一套轻量级的测试，并关注在
核心业务价值上，会让你很放心地做部署。

# 7.Everything is urgent. You get interrupted all the time.
# 7.事情没有轻重缓急，你总是被打断

Being continuous is great. Continuous resolution of non-urgent problems? Not so great. The increased reliance on real-time chat comes with the implicit expectation is that you’re responding to every message that comes in. If you have operational issues you need to deal with, it’s good to have access to everyone on the team. But it’s also important to decide how best to invest your time, then block out your day accordingly. After all, the object of the continuous model is to free developers from constant fire-fighting.
紧急的事情处理最好能做到持续性。非紧急问题的持续性怎么办呢？不太好说。对实时沟通依赖的增加，会导致你需要回应每个消息。如果你有业务问题需要处理，最好能
让团队中的每个人都了解。合理安排时间很重要，根据情况来利用整块的时间。毕竟，持续模型的目标就是解救研发人员于水火之中。

# 8.You spend time merging
# 8.合并代码占用了你的时间

If merging always takes a ton of time and lots of collaboration, you’re doing DevOps wrong. It used to require a lot of work to get a merge together: things are constantly diverging, there’s entropy in software, and you want to control that. Therefore, the more easily you can see how your code interacts with others’, the more quickly you can respond if something goes awry. When you do everything in smaller increments, it’s simply easier to manage and recover from any issues. Many developers have had the experience of being “all hands on deck” in a Slack channel when merging. Slack is great for emergencies. If your emergency is ‘merging’, Slack should not be the answer. Take a different approach: continuous integration, or trunk-based development, for example. Find ways of minimizing the increments that you’re merging with other people’s code.  
如果代码合并总是需要占用很多时间，并需要很多人员协调，那么你实践DevOps的方法是有问题的。过去，由于软件的混乱总是有不一致的地方，所以合并需要大量的工作。
这是需要你控制的。因此，你的代码和其他模块之间的关系越简单，出问题后就越容易定位。当你的增量越小，就更容易做合并或者从错误中恢复。很多研发人员有过
这样的经历，当做合并时所有的人都在Stack频道上。Stack在紧急情况下很有帮助。如果你的紧急情况只是”合并“的话，Stack不是最佳选择。例如：比较一下基于主干（trunk）
的或者持续集成方式的研发，找到一种当你和别人合作时最小化增量的方式。

# 9.Deploys scare you
# 9.部署吓跑了你

Deployment should be a non-issue. As you’re adopting continuous delivery practices, how do you make it safer to deploy code? By implementing tests, yes, but also by thinking about what happens when something does go wrong. Teams should spend time practicing fast rollbacks. Can you ship a fix in 30 seconds? Awesome. By practicing these solutions, you’ll know how to snap into action when an emergency happens.  
部署不应该是个难题。根据你的持续部署实践经验，如何保障部署是安全的？是的，可以借助测试，但也应该思考当发生故障时该怎么办。团队应该做到快速回滚。
你能做到在30秒内打一个补丁吗？对极了。通过演练这些方案，你可以在遇到紧急情况时提前采取行动。

# 10.Your developers don’t care about what happens in production
# 10.研发人员不关心生产上的事情

DevOps is about closing the gap — not only between developers and operations, but also between your team and customers. How do you get developers to care more about what happens in production? By removing any handoff of responsibility between their code and what customers see. In other words, have developers do their own QA. This is another way that shortening the feedback loop leads to all-around better code. When developers are the last stop before code reaches customers, they see the effects of failures firsthand, and those failures feel personal. In order to be fully confident their code will work, they’ll want to be doing more than giving their code a cursory glance before deploying. Writing better tests becomes a way to show pride in their work and ensures it works as intended. And the effect of getting developers closer to end-users and letting them see firsthand the value they’ve built: well, it’s infectious. The excitement of building something in the morning and seeing it production in the afternoon is the reason developers got into the industry to begin with, so clearing way for that cycle to proliferate is the key to keeping developers happy and productive.  
DevOps不仅时要缩短研发与运维之间的距离，还包括团队与客户之间的。如何才能让研发更加关心生产活动？通过消除任何阻断在他们的代码与客户所见之间的责任。
换句话说，研发应该是自己的QA。这是另一种缩短反馈回路而提高代码质量的方法。当研发就是代码到达客户之前的最后一道关卡时，他们能亲身感受到错误带来的
影响，并感觉是自己的错误。他们为了对自己的代码更加放心不出问题，就会在部署之前做更多的工作，而不只是草草了事。写更好的测试代码成为了一种保障不出错
的方法。让研发接近最终用户，并让他们亲身体验构建出来的价值，这样很有效。上午构建后下午就能在生产中看到效果的这种激动，也正是他们进入这个行业的初衷，
这种简单的方法是使得研发人员能愉快并高产的关键。  

No matter how long you’ve been practicing DevOps methodology, there is always room to improve, and good reason to do so. Integrating more DevOps practices benefits the entire organization, not just the engineering team. Yes, DevOps is about enabling developers to move faster, see the results of their work, and make quick improvements or fixes as necessary. But by empowering developers to own their work more fully, you create not only a happy engineering team, but an engineering team who can focus solely on creating happier customers, and that is a win for the entire organization.
无论你实践了多久的DevOps方法论，总会有值得改进的地方。更多的DevOps实践不仅有益于研发团队，而且对所有的组织都是哦有益的。是的，DevOps就是为了让研发
看到他们自己工作的结果，并快速改进或者修复，从而实现快速迭代。通过对研发工作的充分授权，不仅会创建一个愉快的研发团队，而且这样的团队也可以专注地
带来一批满意的客户。这对于所有的组织来说都是一种成功。