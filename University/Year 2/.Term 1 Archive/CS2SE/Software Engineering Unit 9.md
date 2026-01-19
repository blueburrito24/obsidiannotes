### Lecture 9
Classes defined in system analysis depict key business concept and operations, only presenting some of the required class model.
In detailed design, more details are included like attributes' data types, primary operations, operation's signatures and parameter types and the visibility of attributes and operations.
OMG (2015, p.52) specifies guidelines for class diagrams:
- Class name should be centred and presented in bold.
- The first letter of class names should be capitalised if the character set supports uppercase.
- Attributes and operation names should begin with lowercas letters.
- Each abstract class should have italic names.
- Full attributes and operations should only be perceivable when needed, supressed out of context or when classes are briefly mentioned.

![[{9A952060-CA60-455F-B0C1-A72F3EEB24AE}.png]]
This is a good example of the above rules.
The "balance" attribute in BankAccount can be declared with the initial value of zero as seen above.
Attributes that are not null, are specified with the property string "not null" as seen under accountName.
Arrays are specified by multiplicity, such "qualifications:String\[0..10]"
The derived attribute, availableBalance which is calculated from balance + overdraftLimit, is marked with a /.
![[Pasted image 20260107063034.png]]
An operation's signature is determined by the operation's name, number and type of parameters and possible return type.
Visibility is the visibility of the operations, i.e., + public - private \# protected \~ package.
BankAccount's credit() operation is shown in the previous diagram as "credit (amount: Money) : Boolean". Money is the parameterType, and Boolean is the returnType.
More examples of this can be - hide() or + insertionSort\<T -> Comparable>(data : T\[1..\*\*])
![[Pasted image 20260107063314.png]]
We should only show primary operations, such as constructors, destructors, getters and setters, when necessary. Constructors are only visible when they have special significance.
There are varying levels of detail at different stages in the development cycle.

Templates are model Elements that are parameterised by other model Elements. (OMG 2013, p.15).
Templates typically appear within the context of specifying a generic type.
![[Pasted image 20260107063540.png]]
There is also notation for class relations.
![[Pasted image 20260107063604.png]]
For example, the Class "Owner" can send messages to the Class "Car" but not vice versa. Each "Owner" object keeps a reference to the owning "Car" object.
![[{B1BEFDE7-8634-4714-BA77-584CD00EA392}.png]]

Collection classes are used to hold the object identifiers, such as object references, when message passing is required from one to many along an association.
OO languages typically provide support for working with collection classes.
![[{5C0ECFB9-E7C4-4A9A-8DA1-5E098ED7102A}.png]]
There can also be one-to-many association using a collection class:
![[{D1BB4F59-5696-43C7-BD76-D717F2D0DAC3}.png]]

There are also constraints on "integrity":
- Referential integrity: an object identifier/reference should refer to an object that exists, otherwise a null value.
E.g.: the Campaign object reference(s) which a CreativeStaff
object keeps must be either null (i.e. the staff is not working on any
campaign) or must reference existing Campaign object(s).
- Dependency constraints: ensuring consistency in a case where one attribute may be calculated from other attributes.
An attribute whose value is calculated from other attributes is
known as a derived attribute and is marked by / in UML.
- Domain integrity: attributes only hold permissible values.
E.g.: attributes from the Cost domain must be non-negative
recorded in 2 decimal places.

For example:
![[{852FA039-0347-427E-9525-362D971531E1}.png]]

There are also two notations for Interfaces in UML. A small circle icon showing no detail and a stereotyped class icon with the list of supported operations, only one of which typically appears on a UML diagram.
Realisation, a relationship represented by a dashed line and whited-out arrow, indicates that the client class supports at minimum the operations listed in the interface.
![[{E3DD6F9B-2B20-4CB4-B98D-01F072468CC8}.png]]
"Cohesion" and "Coupling":
- Cohesion is a measure of the degree which an element contributes to a single purpose.
- Coupling describes the degree of interconnectedness between design components. It is reflected by the number of links an object has and by the degree of interaction the object has among other objects.
Bennett, McRobb and Farmer (2010).
- Cohesion with a module is the degree to which the module's elements belong together... it is a measure of how focused a module is.
Braude and Bernstein (2011).

The concepts of coupling and cohesion interact with one another. 
Maximising cohesion of modules of code so all contribute to the achievement of a single function.
Minimising coupling means unnecessary linking between modules, that makes them difficult to maintain or use in isolation.

There are various types of coupling and cohesion relevant to an object-oriented approach:
- Interaction coupling
This is a measure of the number of message types sent between objects, with a number of parameters passed with these message types. Message connections involving 3 or more parameters should be considered if they can be simplified. Similarly, interaction coupling in a detailed design should be kept to a minimum to reduce the possibility of changes rippling through the system, and making reuse easier.
- Inheritance coupling
This is the degree to which a sub-class actually needs the features it inherits from its base class. Class inheritance should not be used carelessly as it can weaken the degree of information hiding in the classes concerned.
![[Pasted image 20260107065002.png]]
![[Pasted image 20260107065022.png]]
![[Pasted image 20260107065040.png]]
- Operation cohesion
This measures the degree to which an operation focuses on a single functional requirement. A good example of operation cohesion:
![[{8A553647-AEFD-4B0E-A36F-039153E6908B}.png]]
calculateRoomSpace() computes the total area of the room.
- Class cohesion
This measures the number of things a class represents. Each class should represent a single entity (or requirement), like a lecturer or programme.
An example of good class cohesion:
![[{F0379CAC-811C-4079-A7D5-BB06DB0711A8}.png]]
Note how it doesn't have any unnecessarily inherited methods or operations, like if it had calculateRoomSpace().
- Specialisation cohesion
This refers to the semantic cohesion of inheritance hierarchies - the semantic-relatedness between inherited attributes and operations of a class. Are they related through an "is_a" or "is_a_kind_of" relation? Or is the generalisation/specialisation relation defined out of convenience?
Class A should extend and inherit attributes and operations from class B, only when A is a specialised version of B, not because it needs to use its attributes and operations.
![[{C960797F-58FE-41A4-818D-8760F57AFCE7}.png]]
- Temporal cohesion
Module elements linked only by the time at which they need to be done. (Temporal -> related to time)
e.g.: an initialisation module
“Temporal cohesion is present when a subprogram performs a set of functions that are related in time, such as ’initialisation’, ’house-keeping’, and ’wrap-up’. . . . The only connection between these operations is that they are performed within the same limited time-span.” - p.91 Information Systems Engineering: An Introduction, By
Arne Soelvberg, David C. Kung

“Low cohesion classes often represent a very ‘large grain’ of abstraction or have taken on responsibilities that should have been delegated to other objects. . . . As a rule of thumb, a class with high cohesion has a relatively small number of methods, with highly related functionality, and does not do too much work. It collaborates with other objects to share the effort if the task is large.” Larman (2005, pp.314–317)

. . . no coupling between classes . . . offends against a central metaphor of object technology. . . Low coupling taken to excess yields a poor design. . . It is not high coupling per se that is the problem; it is high coupling to elements that are unstable in some dimension, such as their interface,
implementation, or mere presence.” Larman (2005, pp.299–302)

### Liskov Substituion Principle
“What is wanted here is something like the following substitution property: If for each object o1 of type S there is an object o2 of type T such that for all programs P defined in terms of T , the behavior of P is unchanged when o1 is substituted for o2 then S is a subtype of T.” Liskov (1988, p.7)
![[{7A41FE27-D669-4972-830E-6F210605FE11}.png]]
“Functions that use pointers or references to base classes must be able to use objects of derived classes without knowing it.” Martin (1996)
Essentially, this principle states that in object interactions, it should be possible to treat a "derived object" i.e., an instance of a sub-class, as if it were the base object i.e., the instance of a super-class, without integrity problems.

Here is an example of a Liskov-compliant class hierarchy:
![[{A971ED60-229B-4A94-A682-7E6F2EE1CA36}.png]]
Liskov's principle helps ensure that an OO class design is maintainable and reusable. 
Sub-classes typically inherit attributes and operations from their super-class.
If an attribute or operation isn't suitable for the semantic of a sub-class, it's possible for the sub-class to "disinherit" it by declaring it - private (however this goes against Liskov's principle).
Example below:
![[{893877A9-4D70-4945-A0A3-27F5C5F6C42E}.png]]

Reminder!!
![[Pasted image 20260107070823.png]]
