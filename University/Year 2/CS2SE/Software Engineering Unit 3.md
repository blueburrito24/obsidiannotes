### Lecture 3
Requirements Engineering is how we determine the requirements of a system - what it does, the services it provides and the problems that can be encountered.
"Functional requirements":
- Statements of a system's provided services
- How the system should react to a particular input
- How the system should behave in given situations
- What the system should NOT do in given situations
- Need to be complete and consistent!

"Non-Functional requirements":
- Constraints on services/functions of the system.
- Timing constraints on development due to standards etc.

Non-functional requirements can be more critical than functional requirements. They can be ethical, external, legislative, accounting-related, operational, performance-related, space-related, etc.
The main factor of a non-functional requirement is that it is quantifiable and can be tested.
![[{6B7963B6-97C5-480D-A758-55111F65030E}.png]]
There are certain metrics for specifying non-functional requirements:
- Speed (response time)
- Size (number of)
- Ease of use (training or help needed)
- Reliability (mean time to failure, unavailability, rate of failure occurrence)
- Robustness (time to restart after failure, percentage of events causing failure)
- Portability (percentage of target dependent statements, number of target systems)

There should be an official statement of what software developers need to implement, it covers both user and system requirements alongside functional and non-functional requirements.
![[Pasted image 20260102203316.png]]
The "Feasibility Study" is a short evaluation deciding if the system is useful for the business. It should tell us if the system contributes to the organisation, if it can be implemented into the business' schedule and budget and if it can be integrated alongside other systems in the business.
E.g.,
Probe the feasibility of the following project:
Develop a system that allows real-time editing of a slide by all
students at once when doing a lecture exercise.

This system is not highly useful. Lecture slides are used to teach content, so students don't need to make changes to the content provided by the university. For it to be implemented into the university, there needs to be components for students to interact with the slides through, which may involve altering how the university uses blackboard.
**Note that you should consider what happens if we don't implement a system. The rest above is good.**

Software engineers need to work with stakeholders to evaluate and decide upon requirements. The following stages are used for this process:
- Discovery (finding out about the domain, users and system requirements)
- Classification and Organisation (categorising requirements, forming clusters of those requirements and assigning sub-systems)
- Prioritisation and Negotiation (deciding on definite requirements and resolving conflicts)
- Specification (validating and formally documenting requirements)

Discovery has some challenges, e.g., stakeholders don't fully grasp the priority of what their business wants/needs, requirements are expressed from a personal perspective, different stakeholders will conflict on what requirements they want, etc.
So, we have to brainstorm, discuss and interview the stakeholders, run surveys, etc to come up with definite requirements.
![[Pasted image 20260102204627.png]]
Scenarios can involve multiple workflows, i.e., the sequence of events/actions is influenced and initiated by an actor. There is a primary and assumed path, alternative paths and exception (missed) paths.
We can acknowledge this concept with the 80/20 rule - "You will spend 80% of your time dealing with what will happen 20% of the time".
![[Pasted image 20260102204828.png]]
An exception path to making tea, e.g., with a faulty kettle, would be that the kettle explodes upon activating and you have to stop a fire. So to include this exception path forms a scenario with multiple workflows, instead of a single/primary workflow, similar to the above where two workflows are present.

A use case is an example of functionality in a given scenario, performed by the system with an identifying title. Each use case is associated with the initiating actor and a description for the use case. Its title should fit its function.
Use cases are depicted with UML use case diagrams.
