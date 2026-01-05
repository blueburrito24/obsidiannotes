### Lecture 4
"Analysis" is an inspection on the smaller pieces of an entire item of interest, it involves abstraction.
"Synthesis" is creating something real out of abstract models.
![[{5DFCAC48-4467-4458-BCD0-1E0D36E6BB28}.png]]
In the context of a business or domain, we analyse existing structures and processes. In requirements analysis, we define the goals of our new or modified system. In systems analysis, we develop requirements into a spoken, formal specification - this is more like synthesis than analysis.
If we create an activity diagram while designing a system, it's akin to synthesis activity. We have no real system yet, but we've made something concrete out of our analysis.

Business analysis is the actions we take alongside stakeholders to understand the business' structure, policies and operations.
A business analyst's role involves:
- Identifying problems and opportunities in a business.
- Draw out needs and constraints from stakeholders.
- Analyses the needs and defines requirements.
- Assesses and validates potential and actual solutions to those problems.
- Focuses on business goals and designs.

There are fairly equal ratios of Business Analysts and Developers involved in a business.

There are four important components of a business that business analysts focus on:
- Information about the business, referred to as data.
- Manual and automated activities the business partakes in.
- People and systems, inside and outside the business.
- Guidelines, constraints and policies of the business.

Business analysts have to break down requirements and identify what changes or improvements need to be made.
In the previous units, we looked at business scenarios, workflows/use cases and process models/activity diagrams. Now we will focus on business process maps, class/object diagrams and state machines.
![[{BA17C719-3EDC-4E2D-8A68-828B441E138F}.png]]
This workflow is how we adapt the business from a high-level, abstract description into a detailed, practical model.

Business processes are timelines of the most crucial events taking place in a business. Business process maps collect the named processes in a business, grouped in a hierarchy of up to 3 levels. The first level is very abstract - it doesn't have much detail - and only includes up to 10 processes.
![[{E56858AB-AC54-42FB-AC18-DCAD13D22F1A}.png]]
Of course, as the levels go further then the detail increases.
![[{DA3A3868-B0AF-4F4D-8286-4DAF83CAA267}.png]]
This business process map uses more than three levels, which defeats the purpose of the map which is to abstract the business' processes.
Business process maps focus on the scope and top-level view of the business, making it easy to understand for everyone. It DOESN'T show business structure, information flow, time events or how the processes interact.

Making a business process map is usually done with a daytime workshop involving business managers and experts - they all contribute while reaching an agreement on the process map. Often a facilitator oversees the discussion and enforces rules, making sure a high-level view is achieved while not taking too long to do so.

"Noun-verb analysis" is how we break down large problems into class diagram structures. Nouns can represent Classes, specialisations (classes that extend Abstract classes), attributes and data. Verbs represent services provided by a Class or services used by Classes.

For example, if we look at this kettle workflow from the previous unit, we can identify the classes involved by identifying the nouns of the workflow.
![[{72FD0F98-4A87-4BC7-9607-1417FE6BADFC}.png]]

UML Object Diagrams help us discuss object information, like relationships. They depict instances of classes, sharing a lot of features with UML Class Diagrams (discussed in [[Data Structures Unit 1]]).
Object Diagrams can contain object attribute values. Object Diagrams are also usually less detailed than Class Diagrams.
Also note, "myCup: Cup" depicts myCup being an instance of the class Cup.
![[{081551D1-D9A1-406F-A42A-E97086C99F2D}.png]]
Object Diagrams also use the same notation for relationships as Class Diagrams.
![[{C2176596-47F0-4FE1-A379-155BAD6221DA}.png]]
Even more so, when relationships involve multiple of something we indicate so with the information next to the class.
![[{E4371286-A169-49DE-AD87-1BCC848F5308}.png]]

Below is a good example of an object diagram.
![[Pasted image 20260105195016.png]]
You can see here how a shirt's buttons are part of the whole shirt, a shirt's seams cannot exist without the shirt, and the buttons and seams of a shirt are often adjacent or *associated*.
Class Diagrams, as seen in [[Data Structures Unit 1]] can be very detailed. 
Same notation, same structure. Note that "realisation" and "specialisation" can be treated as idioms for interfaces and abstract classes.
![[{F2D0AD82-C0FE-4F10-86E7-331EDB1FA3BD}.png]]

UML Object diagrams are for showing the static view/structure of an interaction without workflows, the object relationships of a system.
UML Class diagrams are used to better understand the overview of a system, showing us what the system contains but not its nitty gritty details like its code. This is useful for planning and analysis.

State Machine Diagrams are used to show the state of an object across its lifetime, which involves its attribute values. To draw a state machine diagram, we have to abstract the involved object more.
![[{379917BA-325D-4574-8240-EF83D53CC8AF}.png]]
Object states can be a passive quality (on or off) or an active quality.
![[{21411894-81D1-4A75-9DC5-5B374038FD6F}.png]]
Objects transition from "source" states to "target" states.
![[{C2310DB1-77FE-4D61-970E-829F217A1B4C}.png]]
The above syntax follows the format:
trigger [guard]/behaviour
There can also be multiple reasons for a "transition" (action taking place).
![[{EE8712F5-84EE-464A-9DB9-D8FE68812802}.png]]

UML can show multiple states at the same time with the "composite" states notation.
![[{5DE30A48-7285-4FA4-9D59-E56DE73F7688}.png]]
Even if the substate completes early, the entire composite state only completes if all substates have completed i.e., searching can finish, but pacing will still be active so the NPC is still "neutral" until both states are finished.

"History states" are used to remember the state of an object before an interruption takes place.
![[{486B5561-C781-4323-A125-F989B5478479}.png]]
The "H" indicates that the object will go back to whatever state it was in before the powercut (which is the interruption).

Just like in [[Data Structures Unit 1]], UML diagrams can involve choices, forks and joins.
![[{49F04C14-F666-4B92-A290-DEEDBF1B8C23}.png]]
UML State Machines show event-driven objects in a reactive system, and describe how the object evolves and changes during its lifetime.

### Tutorial 4 - "Object relationships and state machines"
Consider the following process map of a certain kitchen:
![[{A8A4FB7D-9930-46B0-8D02-A46136A16AEA}.png]]
(Note that it contains 2 levels).
Pick one of the processes shown in the process map of this certain kitchen and identify 4–5 classes of objects that play an important part in this process and have sufficiently many associations among themselves for the second task.

"store food" -> "organise" -> box, label, cupboard, shelf, food item

Identify among these objects at least:
– ONE composition,
– ONE aggregation that is not composition,
– TWO associations that are not aggregations.
Draw ONE object diagram showing all these relationships.
Draw ONE class diagram showing these relationships with correct multiplicities.

**This is a model answer**
![[{36DEFC0F-16CD-46E5-BF83-78988BD7823C}.png]]
