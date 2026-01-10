### Lecture 5
"Systems Analysis" is an operation that takes place when we need to define solutions for our requirements. We can't implement anything yet, but are close to doing so. Systems Analysis can overlap with Domain Analysis, seen in [[Remote-Folder/University/Year 2/CS2SE/Software Engineering Unit 2]], but is more technical and a synthesis activity rather than an analysis activity.

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
Below is an example of an object and its sequence of actions.
![[Pasted image 20260105214054.png]]
![[{D7114BBF-AE7C-4D64-AF4C-716EBBB1D0F8}.png]]
"Alternative fragments" are alternate paths for a workflow to take. A "guard" is used to decide what path to take, a guard is similar to an if statement choosing one of the available options. So neither action has a return signal, as the object either does one or the other.
"Alt" in the top left corner signifies that this decision has multiple paths.
![[Pasted image 20260105214839.png]]
Optional fragments only take place when the condition is true.
If the object is reachable, then the left arm reaches forward and after reaching forward (returning the signal of the action) grasps the object (which is an asynchronous action as nothing occurs after).
"Opt" in the top left corner signifies that this decision is optional.
![[{6EC3CC06-0432-495D-AA19-7414ED656F37}.png]]
Loop fragments depict repetitive sequences.
It shows the sequence of actions within a loop class, featuring the trigger for the loop. As you can see here, fragments can be combined to communicate a model.
![[{7526BF27-9274-410B-BF83-8E210D8220A9}.png]]
Reflexive calls allow an object to send messages to itself. This represents an object's active processing.
![[{AAFD4C55-F815-4D8D-8307-5B85A2B44678}.png]]

"Deriving Objects from Use Cases"
For each use case, we need to:
- pick a few representative scenarios, such as primary/alternative/exceptions
- express each scenario as a sequence diagram with their involved objects and interactions
- adapt the sequence diagrams into communication diagrams
- combine the communication diagrams to form an overview class diagram

![[{E853B2CE-6B8D-4251-8562-5AA440F15B4A}.png]]
![[Pasted image 20260105221338.png]]
![[Pasted image 20260105221348.png]]
![[Pasted image 20260105221407.png]]
UML communication diagrams are a similar method to convey objects and their interactions, except that it gives a concise, numbered line of action for the objects that makes it easier to communicate the process and derive the classes involved.
![[Pasted image 20260105221647.png]]
When we identify the objects we can form a UML class diagram and add more details like attributes, associations and amounts.
![[{53F586D3-0E64-496D-8FFD-AB97F4A2B47F}.png]]
This entire process of creating use cases, use case descriptions, sequence diagrams, communication diagrams and class diagrams is an iterative process. All the models produced are aggregated to produce an outline class model of the system we want to create.