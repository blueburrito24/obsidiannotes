### LECTURE 1
Software Engineering refers to the methods for analysing, designing, implementing, testing and maintaining software.
The term was coined by Margaret Hamilton under NASA in the 60s, as a title for NATO's conference to discuss software issues, guidelines, practices etc. SE aims to solve failures due to increasing demands and low expectations for software.
SE sets a standard for the programs we produce.

Systems thinking is a holistic (or interconnected) approach to solving problems related to a system's interconnected components change over time, with the goal of the system in mind.

A bicycle is an example of a system because all the parts work together for the goal of movement. The gears, wheels, etc all work together to keep the bicycle driver in motion.
A pile of paper, although a collection of items, is not a system as these items do not work together for any sort of goal.
A tree is a collection of interconnected items, the branches, leaves, roots, they all work together for survival but this might not fit into the definition of a system.

Systems are defined by the following:
- Central Objective
- Integration
- Interaction
- Interdependence
- Organisation/Hierarchy

There are also components we should expect in a system:
- Input, processes, output
- Internal and external environment
- Boundaries of the system
- Interface of the system
- Feedback and control
![[Pasted image 20260102162530.png]]
Control manages the behaviour of the system to achieve its goal.

Complex systems are comprised of various sub-systems. These sub-systems are arranged in hierarchies and integrated (work together) to achieve the goal of the overall system.
When integrated, a system will develop new properties which we can call "emergent properties". These properties can either be functional (emerging the entire system is working to achieve a goal) or non-functional (how the entire system behaves while its operational).

A motorbike weighing 180kg is not an emergent property, the weight of all these parts isn't a new property caused by the system's operation.
A motorbike can be ridden due to its system's operation, so that is an emergent property.
A motorbike's lights can turn on, this is a functional emergent property as the system can do this to make movement easier.
ATMs provide a secure service, this is a non-functional emergent property as the ATM's system goal is just to carry out transactions.

In order to understand and criticise a system, we have to model it AKA create a vision of it.
We have to define the most crucial features of the system; its components, how the components relate to one another, how they interrelate as a system to perform a function, how the system interacts with its environment.

Models allow us to focus on the most important features of a system (abstraction), present our ideas on the system concretely (representation), share our ideas easily (communicate) and check if we meet the requirements for the system (early evaluation).
![[Pasted image 20260102163731.png]]
Models are always abstract - they focus on specific details of a system, software does too - details like code organisation, runtime entities, data flow, etc.
UML is a great way for us to produce models.

Component diagrams help us map out the complex elements of a system to decide how the system should be structured and how the components should interact and interdepend on one another.
![[{08D3817E-B62C-4B7B-9179-D92494D707B7}.png]]
There are two common ways to draw how components work together.
You can either use an arrow for how a component depends on another, or a ball-socket connection.
![[{969F41AB-EBEA-4A25-9F28-E1E4BA79A54E}.png]]
Ports are used to show how a component interacts with the outside environment.
![[{38CD08F7-F6B4-4000-85DB-598505D963D2}.png]]
A good example of these features is this circuit diagram:
![[Pasted image 20260102172111.png]]
The engine powers the battery, so it plugs into the socket of the battery. The lights require power from the battery, so it has a socket for the battery to plug into.

### Tutorial 1
