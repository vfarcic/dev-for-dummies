# Software Development Life-Cycle (SDLC)

Software Development Life-Cycle (SDLC) is a process used by software industry to design, develop, test, and deploy software. It is a series of steps, or phases, that provide a model for the development and lifecycle management of an application or piece of software.

In most cases, the phases used in SDLC are as follows:

* Analysis (requirements and planning)
* Design
* Development
* Testing
* Deployment And Maintenance

The major difference between different organizations is how long each of those phases lasts. In the waterfall model, one project would have only one SDLC cycle. If a project is a year long, months (or at least weeks) would be spent in each of those phases.

Agile models splits a project into multiple iterations (sprints). A single sprint contains all the SDLC phases. Durations of those iterations vary from organization to organization and can be anything from a week to four weeks. During that time, a team passes through all the phases in a rapid pace. Each iteration repeats the whole SDLC cycle.

Organizations that adopt DevOps and continuous delivery or deployment, often shorten the cycle to a few days, hours, or even minutes.

It is important to understand that, in some cases, the phases of the cycle might overlap. It is not uncommon to have a longer planning session at the beginning of a sprint and than repeat it every day (15 minutes stand-up). For example, some teams apply emergent design effectively merging this phase with development. Another example would be deployment. Even though it is listed as the last phase, it is often required before the testing phase. After all, most applications cannot be fully tested without being deployed to a testing environment.

The order of some phases might be reverted. For example, when test-driven development is used, automated tests are written before development (coding) and the time between testing and coding phases is much shorter (often measured in minutes). Those two phases are repeated until a feature is finished and the deployment phase can commence.

No matter the duration and the order of SDLC phases, all are present in a formal or informal way.

## Analysis (Requirements And Planning)

The goal of this phase is to get an *understanding of the different aspects of the system and the features* that will be developed. Naturally, it consists of gathering information and specification of the desired software. The source of that information can be a client, a user, or even another team.

In the waterfall model, the phases that follow cannot commence before all the requirements are defined. Only after every single feature and technical aspect of the system is known, a planning phase can begin. The reason for such a strict division lies in theory that correcting mistakes produced by faulty or incomplete requirements are too expensive.

Once requirements are finalized, a plan is created based on their complexity and the estimated effort required to design, develop, test, and deploy software that fulfils them.

*In the waterfall model, the analysis phase can last for weeks, or even months. It prevents the work on subsequent phases.*

In the agile model, the requirements phase is often much lighter and divided into two phases. High level requirements are defined (often without much detail). Those requirements are called epics. More detailed requirements are called user stories and are often defined when they are needed. An epic gets split into user stories when a team decided to include it in the next sprint. In many cases, a user story (in a way equivalent to a requirement) is less detailed than a requirement. The team would refine it as it progresses through development and testing phases.

Similarly as with the requirements (user stories), planning in the agile model is often done on a high level with details refined for each sprint. Agile teams acknowledge that it is impossible to know everything in advance. Instead, they tend to divide planning into smaller chunks, often related only to the next sprint.

*In the agile model, the analysis phase is often much shorter, even though the discussion about features and planning is spread throughout the whole SDLC.*

## Design

During the design phase, the team that will develop the application or, in many cases, someone with a systems or application architect role, would generate the design document. Its purpose is to *specify all the technical details of the application that will be developed*. It is, in a way, a translation of the functional requirements generated in the previous phase into their technical specification. This document should be a guide for the development phase.

The document would specify which database should be used, which programming language the code must be written in, the patterns that should be followed, the frameworks that should be used, and so on. It defines the architecture of the application as well as low level technical details that must be followed.

*In the waterfall model, the design phase produces a document that contains detailed technical specification of the application that is to be developed. It prevents the work on subsequent phases.*

In the agile model, many teams practice emerging design. The team defines in advance only high level design. All the details related to the design are emerging as the development progresses. As with requirements, agile teams acknowledge that not all technical decisions can be made in advance.

*In the agile model, the design phase is limited to high level decisions, leaving the details to emerge during the development.*

## Development

Once the requirements are specified and the design document is written, the team that start developing the application. The development phase mostly consists of *writing the code of the application and performing a limited number of locally executed tests*.

Due to the separation of phases, developers do not have a direct contact with the person or the organization that made requests for the new features. Instead, the are developing the code to fulfil the requirements and design specifications generated in the previous phases of the SDLC.

*In the waterfall model, the development phase produces a full finished application that fulfils all the requirements and design specifications.*

In the agile model, development is done in short iterations (usually between one and three weeks long). The goal is to produce a fully functioning set of selected features, not to develop the complete application. After each iteration, a demo is presented to the stakeholders allowing the experience from the current sprint to influence the planning and the features that will be developed in the next.

*In the agile model, the development phase is short (between one and three weeks) and produces a selected set of fully finished features.*

## Testing

Only after the application is fully developed, the testing phase can commence. The application is usually delivered to a separate testing team that has the task of *validating whether it fulfils all the requirements*. When a problem is found, a new issue is created in one of the tools used for managing tickets (e.g. Jira). The issue usually contains the test case that reproduces the problem together with testers observations. Once the ticket is opened, its own lifecycle starts. The ticket is assigned to a developer who needs to correct the application. At the end of a round of testing, a new software release is deployed to testing servers, test cases are executed again, and new issues are opened. This validate-correct-release cycle is repeated until all the tests pass successfully and the application is fully validated.

*In the waterfall model, the testing phase is executed in validate-correct-release cycles until all tests pass successfully.*

In the agile model, since the goal is to produce a fully functioning set of features at the end of each sprint, testing is done in parallel with the development phase. Developers and testers are usually members of the same team (no hand overs) or the developers act as testers as well. Due to the need to produce fully functioning features in a short time, the level of test automation is usually higher and often powered by continuous integration (CI), delivery (CD) or deployment (CDP) processes and tools. If test-driven development (TDD) is practiced, tests are usually written by developers before writing the code that implements a feature, making the testing phase shifted.

*In the agile model, the testing phase is mixed with the development aiming at producing fully tested features at the end of a sprint.*

## Deployment And Maintenance

After all the other phases are finished, the application can be deployed to production. Normally, integration engineers or operators are in charge of this phase. They would practice the process in an production-like environment and once they are comfortable with the result, proceed to *deploy it to production servers*.

No SDLC is ever executed without a flow and it is to be expected that some problems will occur after the application is deployed to production. For that reason, often separate, maintenance team is assigned to *monitor the behaviour of the application and fix all the problems that might occur*. When an issue is found, a similar process to SDLC's testing phase. The cause of the problem is documented in form of an issue, a fix is developed, it is tested, and, if tests passed, deployed as a hot-fix to production. Alternative is to postpone the deployment if the issue is not critical and perform it at some later date together with other fixes. Even though the problem is usually found by operators, fixing and testing the solution is often delegated to other teams.

*In the waterfall model, the deployment and maintenance tasks are delegated to separate teams.*

In the agile model, teams are often self-sufficient and capable of defining requirements, designing, developing, and testing the application. While there is no fixed rule, deployment and monitoring usually also falls into the responsibility of the same team.

*In the agile model, the deployment and maintenance is often responsibility of the team that developed the application.*