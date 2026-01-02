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
Objects can be depicted with object nodes/pins. Input pins represent input objects, i.e., an action cannot run without an object parameter. Output pins specify that an object is an output from an action.
![[{7E1E6137-8772-4996-BEDE-EA8F6B03E4DE}.png]]
"Swimlanes" or partitions are used to depict which component/participant is responsible for which actions.
![[{31C19137-FB57-42B3-B8C1-DE955F13D92B}.png]]

### Tutorial 2 - "Activity Diagrams"
#### Reading and Modifying an Activity Diagram
Consider the following activity diagram that attempts to show some aspects of a single Unified Process iteration:
![[{395CF92C-1B35-4279-9A04-573F68E486AB}.png]]
This diagram has logical mistakes i.e., it shows a model that is not consistent with reality.

What sequences of activities does the diagram allow? Consider all possible
sequences of activities that this model permits (i.e., legal paths through the diagram, from start to end). Write down each sequence using the activity numbers provided. For example, 1,2,3,4,5,6,7 is one of the paths to consider.

1,2,3,4,5,6 (Completed phase and planning for next phase)
1,2,3,4,5,6,7 (Completed phase, planned next phase and review goals for next iteration)
1,2,3,4,5,6 (Completed phase and next phase is the last phase)

One of the permitted sequences of activities does not make sense and should be forbidden. Fix the diagram and then check that the meaningless sequence is no longer legal and all the other sequences remain legal.
![[Pasted image 20260102191851.png]]
Now you cannot do 1,2,3,4,5,7 as that is not logical.

#### Unified Process phases and iterations
Consider the following preliminary system specification:
Develop an intruder alarm system controlled by one computer with a control panel, connected to a number of sensors, an alarm bell and a telephone line. The system is activated and deactivated by entering a four digit code. The activation code can be changed using the panel when the system is inactive. After activation, the system monitors the sensors. At first it does not react to any sensor signals but when the signals stop occurring and have been absent for 1 minute, the system will react to any
further signal by setting off the bell and making a phone call to a designated number. The designated number and the phone message can be changed using the panel when the system is inactive.

Identify FIVE-SIX major communication and technical risks of developing the
software component of the system and prioritise these risks. Focus on what
could be difficult or go wrong during development, not after development when the system is in operation.

1. If someone compromises the household without alerting the system, they can easily change the number and message targets for the system, alongside the four-digit activation code. There should be another layer of failsafe to keep these methods intact.
2. If someone compromises the household, regardless of the system being activated they can break the alarm bell and even disconnect the telephone line to prevent the communications being performed. These two lines of communication should be protected and not easily accessed.
3. If the number and message cannot be changed, when someone gets a new phone or their current phone breaks, they cannot be reached in an emergency. The number and message should be readily changed if the last set number is unavailable or the message is not preferred for that chosen number. 
4. If the panel is easily accessible e.g., available in the living room, anyone can go and modify the information for the alarm system. The panel should be in a secluded area so that there is another layer of failsafe to its performance.
5. If someone compromises the household, they can do what they please in that 1 minute period and then leave without the alarm bell or communications being set off. This needs to be reliably tested with live testers.

Outline a plausible potential list of iterations for developing the specified system using Unified Process. Cover all four phases indicating which iterations belong to which of the four phases. The plan is expected to have 10–15 iterations. For each iteration, very briefly specify its objectives and deliverables.

- Inception
-During first iteration we need to decide what features are core and need to be prioritised. Let's say we need an activator, sensors and a bell.
-Second Iteration, we need to build upon this system's features. We need to involve three more sensors.
-Third Iteration, we need to add an activation code to activate the entire system.
-Fourth Iteration, we need to be able to change the code.
- Elaboration
-During first iteration we need to figure out how to achieve those features and what components are needed. We need a button to activate the system and that button needs to connect to the sensors, which connect to the bell.
-During second iteration we need to make sure all the sensors can interact with the activator and bell.
-Third iteration requires a panel for interacting with the system activation, also deciding where the panel will be placed.
-Fourth Iteration requires we have an interface where the testers can modify the code for the system activation.
- Conception
-First iteration of the system with these components and features. Producing the above system.
-Second iteration involves producing the above system.
-Third iteration involves producing the above system.
-Fourth iteration involves producing the above system.
- Transition
-First iteration of live testing.
-Second iteration of live testing, making sure all sensors are individually performing.
-Third iteration of live testing, making sure the system cannot be activated without the code and sensors only function when the code is entered.
-Fourth iteration involves live testing the system to see if it still works as normal, then seeing if changing the code affects any performance.