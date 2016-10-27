# Software Engineering Practices

Software development is a young industry. While there is no fixed date one can claim as the industry beginning, we can say that the beginnings were sometime during 1960s. That is not to say that software did not exist before that but that only around that time software engineering started becoming a profession.

In the early days, the field was so new that the idea of management by schedule was non-existent. Making predictions of a project's completion date was almost impossible. Computer hardware was application-specific. Scientific and business tasks needed different machines. Due to the need to frequently translate old software to meet the needs of new machines, high-order languages like FORTRAN, COBOL, and ALGOL were developed. Hardware vendors gave away systems software for free as hardware could not be sold without software. A few companies sold the service of building custom software but no software companies were selling packaged software.

The first attempts to produce software in an organized fashion adopted practices present in other industries. The waterfall model was born.

## The Waterfall Model

The waterfall model originated in manufacturing and construction where changes are costly and investment in design of the production line is often much less than potential loss if the actual production fails. It is based on the idea that planning and design costs are much lower than those used in the actual production.

### Software development life-cycle (SDLC)

The software waterfall model often uses some variation of following phases:

* **Requirements specification (requirements analysis)** resulting in the requirements document that provides detailed (often functional) specification of the software that should be developed.
* **Software design** resulting in software design (SD) document that provides detailed technical specification of the software that should be developed.
* **Implementation** resulting in the code developed according to the requirements and design specifications.
* **Integration** phase when newly developed software is integrated with the rest of the system (other software).
* **Testing (or validation)** when software is tested for its compliance with the requirements specification.
* **Deployment (or installation)** resulting in the software being installed to the production environment and available to its users.
* **Maintenance** phase when software is being monitored for problems and bugs.

This model expects that each phase is finished before the next one starts. Between each of those phases there are often "gates" that consist of reviews of produced material. To pass those "gates", review of produced material needs to confirm that the previous phase is indeed complete. It usually ends with some form of a sign off. For example, requirements specification can be reviewed by customers. They are expected to sign off the document thus confirming that the result of the requirements phase (for example requirements specification document) is satisfactory and the team can proceed to the design.

Waterfall model discourages revisiting and revising any completed phase. For that reason there are "gates" that are acting as barriers towards the next phase. Each needs to be "perfect" since there is no going back.

McConnell shows that a bug found in the early stages (such as requirements specification or design) is cheaper in money, effort, and time to fix than the same bug found later on in the process. Waterfall responds to this claiming that time spent early on, while making sure that requirements and design are correct, saves much time and effort later. Thus, the thinking of those who follow the waterfall process goes, make sure each phase is 100% complete and absolutely correct before proceeding to the next phase. Program requirements should be set in stone before design begins (otherwise work put into a design based on incorrect requirements is wasted). The same can be said for the rest of the phases. Implementation should not start until the design is 100% complete. Integration needs implementation, testing needs integration... Each phase should be "perfect" before people begin to implement the next one.

### Criticism

Waterfall model was a start in the software industry. There was no other model to compare it with. In the mean time, problems started to become evident.

In almost all but non-trivial projects it is impossible to finish a phase perfectly. Customers often cannot know all the details of the end product up front, design is prone not to be 100% accurate, testing will find defects that might require the team to change the design, and so on.

> "Many of the details only become known to us as we progress in the implementation. Some of the things that we learn invalidate our design and we must backtrack." - David Parnas

One of the side effects of the waterfall model is the creation of "silos". Bigger companies, while adopting the model and growing bigger tend to create departments for each of the phases. As a result, requirements specification phase is done by business analysts, design by architects, implementation by developers, etc. Each of those departments tends to work in partial (if not full) isolation from others. The end result of one phase is often "thrown over the wall" to the team in charge of the next phase. That same department often moves on to the next project and has limited availability to provide support to the team working on the next phase.

The "silos" effect often prevents the team to establish necessary cohesion required for employment of techniques like continuous integration (CI).

The common result of having phases and "silos" is increase in management and documentation effort. It is not uncommon that medium to big projects spend one third or even half of the budget in documentation and management. Since team communication is reduced as the result of phases and silos, it needs to be compensated with the increase in documentation.

Each phase, with its own team, suffers from different problems that are getting accumulated with time. Those listed below are not applicable to all companies practising waterfall model. However, due to the nature of the model, its fostering of silos, and types of organizations that still practice this type of delivery, they are more common than not.

#### Estimations

One of arguments for the usage of the waterfall model is that it has more accurate estimations and budget and that pleases the customers. However, since it is based on the idea that it will start with the "perfect" plan, this often tends not to be true due to increases in costs produced by inevitable changes that are requested later. Even when estimations are accurate, they are done at the expense of a big increase in costs that extensive documentation and planning requires. Due to pressures to do the project within the budget, estimations tend to be inflated so that everyone is safe from possible repercussions.

#### Requirements Specification (Requirements Analysis)

Requirements specification is often done by business analysts (BAs). Their primary role is to establish communication with the client and produce a document that is signed off and will be used as a "bible" of what should be designed by architects and coded by developers. BAs often lack skills to make actual decision about the final solution and act as proxies between a client on one side and the rest of the team on the other. Due to the nature of phases, that communication is limited and tends to be based mostly on revision of already produced documents.

#### Software Design

Another common side effect of a specialization to work in one specific phase is conversion of best developers and testers into "MS Office users". Senior developer would be promoted to, for example, the architect role. Since implementation is the job of developers, architects dedicate a lot (if not all) of their time writing design documents that are passed to developers. "Star developer" gets converted into a person that is more and more disconnected from the code resulting in someone who knows how things were done before, but is not up to date with current tendencies nor actual implementation of previous projects.

#### Implementation

Division into silos can be even more fractured with developers belonging to product or component teams. They can be working for departments made around different products. It is hard to get a full picture of the solution that will be built when knowledge and skills are concentrated on one specific part of the system. Division is inevitable. However, while some other methods foster the idea of one team and shared knowledge with the acknowledgment that each member of the team has some specialization in which he is more productive than others (Java, C, front-end, back-end, DB, etc), the result of the waterfall model and silos tends to go to extremes where one developer belongs to a group that is highly specialized (for example, only JavaScript front-end) and has a limited (if any) knowledge regarding the rest of components.

Developers are supposed to "blindly" implement the requirements document, often without having the direct contact with the customers. They often don't know the motivations and the reasons that resulted in a request for a feature. Common phrase, when it is discovered that the solution is not what the customer wants, is "I did it as it is written in the requirements document". This problem is increased even more with further splitting development team into the above mentioned product or component teams. Not only that, in that case, the developers might not have enough information, but they sometimes receive only requirements for their product or component.

Developers tend to rely on the next phases to validate their work. Since the tasks in those next phases are often performed by other teams, developers often do not have incentives to produce high quality code.

#### Integration

If development team is fractured into product and component teams, integration of these products and components is often left for the phase after the implementation, resulting in the "integration hell". This is the phase when everyone crosses fingers that components and products that were developed individually and by separate teams are working well together. Continuous integration practice was designed to made to solve this problem by making sure that everything is integrated most of the time. However, teams working with waterfall model tend to not use the CI due to team separations and the tendency to do only their part. CI requires much more cohesive environment and tighter collaboration than what waterfall model provides. In an extreme (but not uncommon) case, the integration is done by a separate team that puts it all together, does smoke testing, and passes problems back to developers.

##### Testing (Or Validation)

Since testing is a separate phase that is performed after the integration, work is mostly based on quality checking (QC). It is too late to ensure that the implementation is done with quality built-in. The common effect is that testers are acting as "police" trying to prevent the developed code from passing their "gate" unless all checks passed successfully.

This phase suffers from the similar problem as development. Since there is often no direct contact with the customer and all the work in this phase is based on the requirements document, validation can check whether the software conforms to the document, not whether it fulfills customer expectations.

Since testing is left for late stages of the project, actual discovery of bugs is postponed. McConnell's claim that a bug found in the early stages is cheaper in money, effort, and time to fix than the same bug found later on in the process tends to work against the waterfall model even though that is the main argument used by those practicing it.

Test automation is often limited or non-existent since testers often don't have enough coding skills to build the automated solution. On the other hand, developers are working on implementation and are concerned mostly to do their phase and fulfill their schedules. Due to the lack of cooperation between teams, testers are left on their own and are often forced to do most of the work manually. As a result, testing phase can last as long as the implementation, if not longer.

#### Maintenance

In extreme but very common cases, maintenance is handled by a dedicated team. Those that did the implementation and testing phase often move to the next project leaving the maintenance team to fix bugs that will occur in production. In such a situation knowledge of what was done during the project is based on documents instead on actual experience and the team needs more time to debug and solve problems.

#### Change requests

Change requests are probably the most painful part of the process. Since the model assumes that each phase is complete before the next one starts and that it was executed "perfectly", any change to the scope tends to break the whole process. Even a simple change request might move the team back to the beginning resulting in potentially huge costs. For all but the most trivial projects, there is no perfect plan nor there is the perfect scope and design defined in advance.

### Summary

The waterfall model tries to plan everything in advance, execute that plan and observe the result at the end of the process.

Most commonly defined stages of an waterfall project are as follows.

* Requirements specification (requirements analysis)
* Software design
* Implementation
* Integration
* Testing (or validation)
* Deployment (or installation)
* Maintenance

Waterfall model can be useful for static projects where there will not be many changes. For most others it is outdated, too inflexible and too expensive. However, it is still used in enterprises.

Often overlooked aspect of the waterfall model is its indirect effect on the company structure and the organization of teams that tends to create silos of highly specialized people and the expense of decreased collaboration. There is an increase in management costs and creation of rigid environment with little space left for improvement.

And then came the iterative and incremental development model, better known as Agile.

## The Agile Model

In February 2001, 17 software developers met at the Snowbird resort in Utah to discuss lightweight development methods. They published the Manifesto for Agile Software Development. The manifesto, and the practices that followed it, we based on their individual experiences and best practices.

> We are uncovering better ways of developing software by doing it and helping others do it. Through this work we have come to value:
>
> Individuals and interactions over processes and tools
> Working software over comprehensive documentation
> Customer collaboration over contract negotiation
> Responding to change over following a plan
>
> That is, while there is value in the items on the right, we value the items on the left more.

The Agile Manifesto is based on twelve principles:

* Customer satisfaction by early and continuous delivery of valuable software
* Welcome changing requirements, even in late development
* Working software is delivered frequently (weeks rather than months)
* Close, daily cooperation between business people and developers
* Projects are built around motivated individuals, who should be trusted
* Face-to-face conversation is the best form of communication (co-location)
* Working software is the principal measure of progress
* Sustainable development, able to maintain a constant pace
* Continuous attention to technical excellence and good design
* Simplicity, the art of maximizing the amount of work not done, is essential
* Best architectures, requirements, and designs emerge from self-organizing teams
* Regularly, the team reflects on how to become more effective, and adjusts accordingly

**Agile software development is based on iterative and incremental development model.**

### Iterative and Incremental Development

To understand the change that was brought with agile practices, you need to have a picture of the software world before it. Most companies were using the waterfall methodology. A typical project would last for month, if not years. It consisted of phases like requirements gathering, development, and testing (just to name a few). Each of those phases lasted for weeks or months and were performed by separate teams. As a result, we got the "silos" effect. Each team had a very limited communication with the other and the knowledge of what should be done was mainly based on the artifacts (e.g. requirements document) produced by the team that finished the previous phase. As a result, teams were working on their tasks based on those artifacts.

Waterfall teams often did not understand the full picture of what should be done. The "silos" effect resulted in a very poor communication and very specialized set of skills. If you are, for example, a front-end developer, you would have a strong dependency on other teams to deliver parts of the project you depend on. As a result, waiting time was often considerable. If you would, for example, require a back-end service before proceeding with your front-end application, you would wait for the other team to deliver it. That wait time ultimately increased the costs of the projects and, more importantly, resulted in poorly designed applications. Even though specialization is a necessity (no one can be an equal expert in everything), lack of knowledge about the system as a whole prevented us from creating optimum solutions.

Another example of a problem produced by "silos" are automated tests. A project would have development and a testing teams that operated with different objectives and under different management. As a result, developers did not have an incentive to test the applications they were working on. After all, that's the job of a different team. On the other hand, testers did not have the knowldge of the internals of the application developers were producing. How could they know what's inside when they did not work with developers? Testers would receive a finished application that would be a black box for them. They would know what's outside but not what is below the surface. As a result, test coverage and quality was generally very low. On top of that, testers working in a separate department would not have coding skills so their testing would be, in many cases, fully manual and last for weeks, if not months. Without automated tests, even a simple change in the code would require a full regression testing since testers, due to their lack of knowledge about the internals, could not concentrate only on the parts that changed nor they could execute automated tests since they were very limited or non-existent. Testers would act as a police trying to find a fault in the system instead helping developers create applications with the quality baked in. Developers, on the other hand, had no incentive to test their own work since that was a job of testing teams.

According to the Standish Group, 29% of waterfall projects done since the year 2000 failed while 57% were challenged. The processes we have today are more mature and we could expect even worst results before 2000. Yet, many companies even today having trouble moving away from waterfall.

And then came iterative development better known as agile.

Iterative development was created as a response to inefficiencies and problems found in the waterfall model. Most, if not all, agile models are based on iterations.

**The general idea is to develop a system through iterations (repeated cycles) and incrementally (in small portions of time). Through them, team members or stakeholders can learn from their mistakes and apply that knowledge in the next iteration.**

Working through iterations means that the development of an application is split into smaller chunks. In each iteration features are defined, designed, developed and tested. Iteration cycles are repeated until fully functional software is ready to be delivered to production. The process does not try to start with the full set of requirements and design. Instead, the team tries to prepare just what is needed for the successful delivery of the next iteration.

Some models have different names for an iteration, like sprint, or time-boxed. Iterations can be limited in time; they end after the agreed period independently of the size of the scope that was done. Alternative way of doing iterations is to limit them in scope. They last until the agreed scope is fully finished (developed and tested).

It is a common practice that each iteration is finished with a demo to stakeholders. That demo is used as the learning process with the objective to correct the way the next iteration is done or modify the scope. Since a working model is available much earlier, it is much easier to spot problems before it is too late or too expensive to take corrective actions.

This way of developing is in stark contrast with the waterfall model where each phase of the software development life-cycle (SDLC) needs to be fully completed until the next one starts.

**One of the main advantages of iterative development is that it allows more flexibility to adapt to changes.** Unlike the waterfall model where unforeseen problems often surface late in the project and are very costly to fix, the iterative approach, on the other hand, goes through short cycles that allow the team to learn, adapt and change the direction in the next iteration.

Looking at the same report from the Standish Group, failed agile projects are measured in 9%, even though the amount of those that are challenged is still, more or less, the same (49%).

### Why Doesn't Everyone Use Some Form Of Iterative Development?

The short answer to this question is that not everyone can use it effectively. Iterative development is much harder than the waterfall model. It requires higher level of technical excellence, more discipline and buyout from the whole team. It often requires that the team members are capable of performing more than one type of tasks (for example develop and test or work on both front-end and back-end).

Changes need to be done across all roles when they come from the waterfall process. Two of those roles that are often most affected are integration engineers and testers.

#### Integration Engineers

Integration phase in iterative development is very short or, when done right, continuous. While in the waterfall model this phase can take even several weeks for bigger projects, iterations require it to be very short and done often. If, for example, testers need to test some functionality as soon as the code is done, integration and deployment needs to be almost instantaneous. There are many tools currently in use that facilitate the integration and deployment. Some of them are [Puppet](http://puppetlabs.com/) and [Chef](http://www.getchef.com/) for configuration management and [Jenkins](http://jenkins-ci.org/), [Bamboo](https://www.atlassian.com/software/bamboo) and [Travis](https://travis-ci.org/) for Continuous Integration, Delivery and Deployment. Everything, or almost everything, should be scripted and run on certain events (commit to the repository or click of a button).

#### Testers

Testers (especially when used to perform only manual testing) are among those who have most difficulties adapting to the iterative process when they're coming from the waterfall model, especially if they are used to test the application after it is done. Switch to iterations forces them to act in a different way and think in terms of specific functionalities that should be verified instead of a fully developed system.

Testers need to work in parallel with developers in order to meet iteration deadlines.

Often there is no time to perform manual testing after the code of some specific functionality is finished. High level of automation is required. While developers are writing the code, testers need to write scripts that will verify functionalities created by developers. Automation requires certain coding skills that testers might not posses. As a result, test automation might be left to developers while testers continue being focused on manual testing (both are required to certain extent). However, in those cases testers might feel that part of their work, and the security it brings, is taken away from them.

### Advantages

End products are often more aligned to client needs due to abilities to demo functionalities done in each iteration and adjust depending on the feedback. Higher level of automation required for successful iterations allows faster detection of problems and creation of reliable and repeatable processes. Automation, after initial investment, leads to reduction in costs and time to market. Interdependency among team members increases the shared knowledge within the team leading to a better understanding.

Some of those changes can be applied to the waterfall model but, in many cases, they are not. The incentives for doing them are not big since they might not be perceived as necessities. For example, continuous integration has big potential savings in non-waterfall projects due to the need to perform installations, deployments, testing and other tasks often and fast. In the waterfall model intention is to do the integration once (after the development phase is finished) so the investment for scripts and jobs that will perform repeatable and scheduled processes does not look like it provides enough return.

**In many cases, the iterative and incremental process contains the complexity and mitigates risks within a defined time box. This allows the team to continually review and adapt the solution according to the realities of the ever-changing situation.

### The Most Common Agile Flavours

Since the emergence of the Agile Manifesto, quite a few Agile methodologies appeared, with **eXtreme Programming and Scrum being among the most commonly practiced.**

### eXtreme Programming

Extreme programming (XP) is a software development methodology which is intended to improve software quality and responsiveness to changing customer requirements. As a type of agile software development,it advocates frequent "releases" in short development cycles, which is intended to improve productivity and introduce checkpoints at which new customer requirements can be adopted.

Other elements of extreme programming include: programming in pairs or doing extensive code review, unit testing of all code, avoiding programming of features until they are actually needed, a flat management structure, simplicity and clarity in code, expecting changes in the customer's requirements as time passes and the problem is better understood, and frequent communication with the customer and among programmers. The methodology takes its name from the idea that the beneficial elements of traditional software engineering practices are taken to "extreme" levels. As an example, code reviews are considered a beneficial practice; taken to the extreme, code can be reviewed continuously, i.e. the practice of pair programming.

In a certain way, **XP is mostly focused on technical aspects of the software development life-cycle.**

### Scrum

Scrum is an iterative and incremental agile software development framework for managing product development. It defines "a flexible, holistic product development strategy where a development team works as a unit to reach a common goal", challenges assumptions of the "traditional, sequential approach" to product development, and enables teams to self-organize by encouraging physical co-location or close online collaboration of all team members, as well as daily face-to-face communication among all team members and disciplines involved.

A key principle of Scrum is its recognition that during product development, the customers can change their minds about what they want and need (often called requirements volatility), and that unpredicted challenges cannot be easily addressed in a traditional predictive or planned manner. As such, Scrum adopts an evidence-based empirical approach-accepting that the problem cannot be fully understood or defined, focusing instead on maximizing the team's ability to deliver quickly, to respond to emerging requirements and to adapt to evolving technologies and changes in market conditions.

Unlike XP, **Scrum is mostly focused on human and management aspects of the software development life-cycle.**

### Summary

The Agile movement started with the manifesto.

> Individuals and interactions over processes and tools
> Working software over comprehensive documentation
> Customer collaboration over contract negotiation
> Responding to change over following a plan

Agile software development is based on iterative and incremental development model.

The general idea is to develop a system through iterations (repeated cycles) and incrementally (in small portions of time). Through them, team members or stakeholders can learn from their mistakes and apply that knowledge in the next iteration. One of the main advantages of iterative development is that it allows more flexibility to adapt to changes.

The most commonly practiced Agile flavours are eXtreme Programming (XP) and Scrum. XP is mostly focused on technical aspects of the software development life-cycle while Scrum puts more attention to human and management aspects of the software development life-cycle.

With time, the industry realized that Agile is not enough and the DevOps movement was born.

## The DevOps Model

Software industry is changing rapidly. The challenges from a few years, or even months ago might not be the same as those we are facing today. When Agile appeared, it tried to solve the problems related to some of the development practices and issues created by the waterfall management style. Among other things, Agile tried to create self-sufficient teams capable of rapid development of high quality products. It removed some of the silos that were preventing engineers from delivering results in an effective way. At that time, being self-sufficient meant that the team is capable of gathering requirements, developing the code, and testing it. With time, we realized that is not enough. **Agile, in a way, excluded professionals in charge of software deployments and monitoring. DevOps was created as a way to remedy that.**

Why didn't we have DevOps before? The short answer is that the needs changed. While in the past we could be well off with only a few servers, today we are dealing with huge clusters. Cloud approach to infrastructure is becoming prevalent. Fault tolerance and high availability are much more important today then they were before. A single minute of a downtime might cause our business to come to ruin.

How did the world look like before we adopted DevOps practices? To understand the current situation, you'd need to understand the pitfalls of agile development.

Agile teams were supposed to be self-sufficient and flexible. Those qualities would allow them to avoid wait time produced by waiting for other teams to finish working on tasks they depend on. The teams would manage to finish the whole project much faster than when they worked inside waterfall processes. One of the reasons for such an increase in speed were iterations or sprints. A sprint would last for a few weeks and, at the end of it, the team would have a set of features fully developed. Those features would be presented to stakeholders. Through evaluation of the results of a sprint, many of the problems could be avoided and mitigated in those that follow. Sprins allow teams to increase the speed and overall quality by continuously evaluating the result of their work and adapting to change.

The problem with agile is that the teams were, in most cases, not truly self-sufficient. A team would consists of expert capable of defining the requirements (user stories), developing, and testing the features. However, agile failed to include operators into the mix. As a result, agile succeeded (up to a point) to greatly improve the development but failed to deliver the result. It was not successful at doing the last steps of the life-cycle and create processes that would deliver their results to production in a quick and continuous manner. It did not remove all the silos by excluding experts that know how to operate and monitor production systems. Those experts continued being in their own silo with often opposing objectives than those of agile teams.

The main objective of a development or an agile team is to finish new features as soon as possible while maintaining certain level of quality. The soon those features are available, the sooner business will get value from them thus increasing the return of investment (ROI). However, experts in charge of maintaining the production clusters have a different objectives. Their main interest is stability. The more stable the system is, the better they fulfill their goals. The less changes are introduced to the system, the more stable it is. If taken to an extreme, development teams would prefer deploying new features to production continuosly, while operators would rather choose to never deploy anything new.

That changed with the introduction of continuous delivery (CD) and deployment (CDP) processes. In a nutshell, the idea is to have an automated pipeline that would allow teams to deploy a feature every time the code is committed to the repository. For such a system to work, the pipeline had to be fully automated. The code has to be built and tested with such a great coverage that we have almost absolute certainty that it is safe to deploy to production without any human intervention. For such processes to work, operations had to be automated as well and people responsible for maintaining the live systems had to be included in the teams. They had to gain coding skills without which automation is not possible. On the other hand, developers had to gain a better understanding of the deployment processes and system monitoring so that they can design their applications around those proccesses.

Hence DevOps was born and CD and CDP pipelines became part of the automated processes we employ on a continuous bases.

With time, we developed sophisticated processes and tools that help us provision servers, and deploy and monitor our code. We are on a quest of running software that is always working (zero-downtime) and highly responsive no matter whether we have hundreds, thousands, or millions users using our service at the same time (high availability). On top of all that, new releases are being continuously deployed to our servers (continuous deployment) introducing new problems that might put the system at risk. The way we are trying to overcome all those, and quite a few other challenges is DevOps.

One of the major problems organizations were (and still are) facing is that developers have quite different objectives from professionals in charge of maintaining servers and applications running inside them (we'll call them operations). Developer's interest is to release new features as fast as possible. The sooner a feature is available to our users, the sooner we rip benefits. Operations, on the other hand, are in charge of stability. Their objective is to have high up-time. The easiest way to accomplish that is by not introducing changes that might potentially reduce the availability. If we take those objectives to the extreme, developers would make changes to production all the time and operations would reject any change. As you can imagine, such opposing objectives might lead to very low cooperation between the teams.

**DevOps is a culture, a movement, or a practice that emphasizes the collaboration and communication of both software developers and other information-technology professionals while automating the process of software delivery and infrastructure changes.** It aims at establishing a culture and environment where building, testing, and releasing software can happen rapidly, frequently, and more reliably. It enables teams to be in full control of the whole process, from gathering requirements, all the way until software is running in production. It tries to bring together all types of professionals into one team with the objective to develop and release software fast without sacrificing quality and availability.

**DevOps integrates developers and operations teams in order to improve collaboration and productivity by automating infrastructure, automating workflows, and continuously measuring application performance.** In a nutshell, DevOps teams try to automate all the repetitive tasks. While Agile (especially XP) put a lot of emphasis on tests automation, DevOps extends that with automated workflows, infrastructure setup, deployment, and monitoring. It aims at creating automated processes that result in self-healing systems.

While Agile aimed at releasing software at the end of iterations that typically last for a couple of weeks, DevOps tries to shorten that period to hours, sometimes even minutes. In larger organizations, successful DevOps implementations can result in hundreds or even thousands deployments to production every single day.

### Summary

Agile, in a way, excluded professionals in charge of software deployments and monitoring. DevOps was created as a way to remedy that.

DevOps is a culture, a movement, or a practice that emphasizes the collaboration and communication of both software developers and other information-technology professionals while automating the process of software delivery and infrastructure changes. It integrates developers and operations teams in order to improve collaboration and productivity by automating infrastructure, automating workflows, and continuously measuring application performance.