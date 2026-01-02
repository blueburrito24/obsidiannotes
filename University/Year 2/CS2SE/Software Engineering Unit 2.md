### Lecture 2
Software Development Lifecycle, or SDLC as we will call it moving forward, is a sequence of stages we follow to create a software application.
There are many models/frameworks for this process.
SDLC should involve a logical progression of activities, not based on time.
![[{0A63554B-1016-40D8-84C1-2B3639BB3B4F}.png]]
![[Pasted image 20260102183001.png]]
These are the phases of SDLC:
- Domain analysis
-Understand what exists and what problem we are solving.
- Specification
-Produce clear, agreed requirements for the system.
- Design
-Plan the structure and behaviour of the software.
- Implementation
-Turn these designs into a working system.
- Validation
-Confirm the system meets requirements.
- Deployment
-Make the system usable and maintainable in a practical setting.

Alternative to SDLC, there is also the Waterfall Process. It is rarely used currently.
Each phase of the Waterfall Process must be fully completed before the next one starts, which means each stage involves lots of documents and models. 

There are also two approaches to improvement within a software project- incremental (doing it stage by stage) and iterative (improving upon the entire project at each stage).
![[{3E02E905-81A3-42B4-A7E7-F74BF617C530}.png]]
The Unified Process is an example of an iterative improvement process:
- Inception
-Deciding what we want to create, what goals we will achieve with it and how we will make it.
- Elaboration
-Identifying what problems we will face while producing, refining requirements and plan, identifying actors.
- Construction
-Producing a beta version, meeting needs and testing for deployment.
- Transition
-Deployment and maintenance, alongside taking feedback from users.
![[Pasted image 20260102184404.png]]
This is how SDLC would play a part in the Unified Process.
Notice how it isn't a linear process, but many phases can be active at the same time.

Another approach to software development is Agile. Agile prioritises human interaction in project development e.g., face-to-face communication amongst team members and customers, customers getting representation that they need, software is developed in iterations and tested quickly, code is well-documented, long-term is only considered for goals and visions.
"Scrum" is a framework for Agile that provides roles for project members to fit into and an approach to development.
- Transparency, inspection and adaptation are key pillars of Scrum.
- Product Owner handles product requirements.
- Development Team brings the product to life.
- Scrum Master ensures that the Scrum framework is understood and followed accordingly, alongside facilitating "Scrum Events".
Scrum Events involve the following:
- "Sprint" - a fixed time period to produce working software (in the iterative sense).
- "Sprint Planning" - deciding what will be produced in the Sprint and how we will produce it, alongside a backlog.
- "Daily Scrum" - short daily meeting to make sure everyone is in sync and knows what they're doing and any problems they may encounter.
- "Sprint Review" - Demonstrating the completed work and getting feedback from stakeholders.
- "Sprint Retrospective" - Team reflects on their performance and what to do next.

UML Activity Diagrams show how important business processes occur in our system.
![[{492AD636-BF5F-45F0-8565-2A647FC4237D}.png]]
Actions in these activity diagrams start when they receive a control token (i.e., the black circle above).
Diamonds are used to depict decision/merge nodes.
An "edge" is a representation of data flow and decision path.
![[Pasted image 20260102190133.png]]
Multiple actions that run in parallel are depicted using forks and joins, the flow is broken up into two or more simultaneous flows which must finish before the flow continues past the join node.
![[Pasted image 20260102190358.png]]
We can't finish a flow until all actions are done, so we can't do a latter action before we finish all the previous ones related to that action.
When an activity has time relevance, we use time events to model a waiting period.
![[{E97A6723-B210-41C4-966F-F3452E21B2D0}.png]]
When an activity involves external actors/processes, it has to send signals to the actor/process. A receive signal wakes up an action, while a send signal is a message to the external participant.
![[{D9D23DFC-9B02-4010-95FB-D9962F1FA42B}.png]]
Interruptions are receive signals that change the flow of an activity, signified with a lightning bolt symbol. The region in which the interruption can take place is often outlined with a dotted box, referred to as the Interruptible Region.
![[{96A3B6C4-A422-4800-9E90-8089870928FD}.png]]
