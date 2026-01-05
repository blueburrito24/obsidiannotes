### Lecture 5
"Systems Analysis" is an operation that takes place when we need to define solutions for our requirements. We can't implement anything yet, but are close to doing so. Systems Analysis can overlap with Domain Analysis, seen in [[Software Engineering Unit 2]], but is more technical and a synthesis activity rather than an analysis activity.

Domain Analysis is how we get the information necessary for Systems Analysis, which delivers a more in-depth, technical solution for the system requirements, such as detailed system models and models of internal mechanisms.
![[{350FD180-8389-453A-B98B-9C87E5E45280}.png]]
The role of a Systems Analyst is to research problems and determine requirements and plan technical solutions for modified/new systems (derive object designs from requirements, include all use cases in actor-object/object-object interactions, and assign specific implementable actions to objects) to create a comprehensive model of the system's objects, behaviours and interfaces.

Software-based object-oriented modelling was introduced  to simulate real-world entities in the 60s (Also known as Simula).
This involves software objects representing entities such as students or products, their attributes such as student names and behaviours (autonomous and interactions).
Objects interact by signalling to each other.

UML Sequence Diagrams give us a way to depict objects and their interactions in a sequence.
![[Pasted image 20260105211049.png]]
^ The actor does an action, which affects the Webform object and then other objects are affected in tandem with it.
The circle with a T represents a boundary, circles with underlining represent entities and a circle with an arrow is a control object.
Boundary Objects facilitate interactions between an actor and a system, which can be a UI and API for example. They only wrap data and are always present in sequence diagrams.
Entity Objects model stored/persistent data in a system.
Control Objects involve use cases and complex behaviours, interacting with the Boundary Object to facilitate interactions with actors.
![[{EA338D5E-ADDA-410F-98F7-ACD14F9AFBE2}.png]]
Similar to forks and joins seen in [[Data Structures Unit 1]], "activation bars" indicate when an object is active. They are not crucial to a sequence diagram.
![[Pasted image 20260105213158.png]]
Two different types of signals can be shown between objects, a regular tipped arrow for synchronous messages (sender waits until receiver finishes action and returns, represented by a dotted arrow) and asynchronous messages (one-way signals).
![[{BFD36E00-B550-444F-941B-FBA001C173F1}.png]]
