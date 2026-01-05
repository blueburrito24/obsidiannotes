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
