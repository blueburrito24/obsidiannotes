### Lecture 1
The UML class diagram describes the following:
The classes of a software system -> the attributes and operations of each class -> the static relationships among classes -> the constraints on the connections among objects.
There are also details about visibility/access of attributes, and underlining to indicate when an attribute or operation is class-wide/static.
![[{D19C9F34-2663-4013-AA47-2CC8C95E110F}.png]]
- + signifies an item is publicly visible.
- - signifies an item is privately visible.
- \# signifies an item is protected.
- ~ signifies an item is a package.
It's also important we note that the location of data defines its scope and level of access. Variables declared in a class are available to all methods in that class, but variables declared in a method are only available to that method.
Below is an example of a UML class diagram.
![[{3241E524-014B-4BE1-948C-86054202E3E7}.png]]
Sub-classes inherit from a super-class to retool existing methods and procedures to avoid doubling efforts.
![[{FE42B327-1DDD-4971-AE89-9466BBF3EBD0}.png]]
In the above example, we have the abstract class "Ownable" which is our super-class. Then outside the super-class, we have Car and Pet, which are sub-classes and inherit features of "Ownable" such as having an OwnerTel (owner's number) and other features declared in the Ownable super-class.
Below is a further-developed example.
![[{46DD11F9-ABCE-473E-A02B-2418F9041287}.png]]
In this example, there is an explicit "Person" class which holds all the information like the previously mentioned phone number and other data. This allows for us to create a relationship between the classes - a Person can own 0-2 Ownables, those being either a Car or a Pet which both inherit Ownable operations like getting the owner's number or changing the designated owner.
![[{25E13AE3-7BBF-4DCA-A1C3-7B28FAE4E75A}.png]]
This excerpt of code is how we would translate the UML class diagram to an actual software system. The Person's constructor shows that we can only hold up to 2 "possessions" which would refer to those Ownable items.

Most class diagrams will include an abstract/concrete class and an interface, which provides methods for other classes to implement.
When implementing an interface, you can take the interface's operations but not its explicit rules, whereas inheriting a super-class gets the super-class' attributes and operations which is useful when two classes are similar in nature (like a type of something).
There are also different types of relations involved with UML class diagrams:
- Association relation
![[{5A18FA46-823C-4EE0-AFDE-14E8FC4DFEE3}.png]]
- Aggregation relation (has a)
![[{EF2BF530-E701-499B-A1C3-77947B49237D}.png]]
Note the diamond-ended arrows for aggregation.
- Composition relation (owns a)
![[{CBE49B8B-38DE-451C-BB40-DFD206D93BE6}.png]]
- Dependency relation (uses)
![[{DF896862-6A1C-459C-B471-1FDD17F8A79F}.png]]
![[{DF5B727C-E308-4DD1-8F04-C9B5C7375DE0}.png]]
Note the dotted-arrow for dependency.
- Generalisation relation (is a) -> relates to extending another class
![[{01F68624-3C11-4415-8E2E-8005FA1C5FD5}.png]]
Note the white-tipped arrow for generalisation.
- Realisation relation -> implements an interface
![[{E83E3557-6AFD-42C0-A0F3-D49A382B098D}.png]]
Note the dotted, white-tipped arrow for realisation.

--------------------------------------
### "Object Orientation - a quick revision"
 An object is a data entity in a Java program, representing complex data concepts. An object is an instance of a class, like a use case.
Java programs manage primitive data like numbers and characters.
![[{0215660C-FBAD-43FE-B7E8-F4F8FFD90727}.png]]
When we want to create an object, such as SavingAccount, we have to initiate it and then instantiate it. The data and methods of a class are called its members.
```java
int x;
Integer y;

y = new Integer(74);
```
In the above excerpt of code, we've initiated an Integer variable, however no Integer object exists until we instantiate it explicitly (see the third line).
The variable, or reference, stores the address where the object is stored in the system's memory. Some objects are so frequently used however that explicit instantiation is not needed, such as Strings.
```java
String name = "James Gosling"
```

The features of an object is defined by the class it's an implementation of, such as the "SavingAccount" class mentioned above.
Each object is "encapsulated" so they can manage and oversee their own instances of details from the classes that define them e.g., a SavingAccount object can manage its own name, balance and accountNumber. This also means that other objects cannot access this object's variables directly.
![[{395F5660-EB9D-4970-BB76-23966BD48F2D}.png]]

Classes can be created by inheriting other classes, so you don't have to define new characteristics for it. Inheritance allows us to reuse program code and streamline class relationships. For example, if we update a super-class like the type of features an "Ownable" object can use, inherited classes like "Car" and "Pet" will automatically inherit the updated features of "Ownable".
Further classes can inherit the sub-classes, forming a hierarchy.
High-level classes define common features, derived classes define specific distinctions.
![[Pasted image 20260103141447.png]]

A Java interface is an abstraction of a class, omitting the nitty gritty details of the class and only presenting the basic attributes and operations - what they are but not how they work.
![[Pasted image 20260103135334.png]]
The above model and sketch of the Tesla are abstractions - they show us what the item of interest is but not how it works.
![[Pasted image 20260103135423.png]]
In this excerpt of code, the class is abstract in that it only shows what we need to know about a Car so we know it exists - its model, make, other basic features.
Java interfaces are abstractions of classes in that they share no detail on their implemented classes or methods.
Also note that in UML Class Diagrams, abstract classes are signified with *italicised class names*.

A class library is a set of classes that support program development. They're often included with the programming language. For example, the String class mentioned previously is not a part of the Java language, but the Java standard class library that is included with any Java environment.
These classes are grouped into packages, typically grouped by their relation and under one package name. For example, String, StringBuffer, System and the interface Iterable are part of the java.lang.package.
All user-defined classes are assumed to be in the default package, however you can place your class in a specific user-defined package.
```java
package dsaj;

import java.util.Stack;

public class PureStack {
		// implementation detail omitted
}
```
"import" is used to make classes from any packages outside of java.lang available for use in a program. We can import a single class from a package:
```java
import java.util.ArrayList;
```
or import an entire package and all its classes:
```java
import java.util.*;
```
All objects have a state and set of behaviours. An object's state refers to the values of its variables, its behaviours refer to the actions the object can take through method calls. Behaviours are consistent across all objects of a given class.

