---
aliases:
  - CS2DSAL1
  - DSAL1
  - L1
  - L1DSA
image: https://images.unsplash.com/photo-1485470733090-0aae1788d5af?ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxzZWFyY2h8M3x8d2FsbHBhcGVyJTIwNGt8ZW58MHx8MHx8fDA%3D&fm=jpg&q=60&w=3000
Next: "[[CS2DSA - Lecture 2]]"
Previous:
---
# Unit Objectives
- Consider basic UML notation for class diagrams
- consider some core concepts underlying object-oriented (OO) programming
- Consider how some core OO concepts can be realised in a Java program
- Use generic types to define collection classes

# The Unified Modelling Language #UML
UML is a standard notation for software design, dependant on the programming language and provides diagrams which use icons and notations, these include class diagrams, use-case diagrams, sequences diagrams.

## UML Class Diagram #UML #UMLClass #Class
UML class diagram describes the overall design of a software system, for possible situation (instead of modelling a particular situation). 
These describe the relationships between classes, relation between classes show the number of objects
	- Zero
	- One or Many
	- One to Many


UML class diagrams include:
1. The classes used in the system
2. The static relationship among classes
3. The attributes and operation of each class
4. The constraints on the connections among objects
5. The constraint, if any, on each element

- Attributes is class level data, this includes variables and constants
- Operation is a method in Java
- Visibility, data types, and constraints are included

UML class visibility
- + Public
- - Private
- "#" Protected
- ~ Package

Check Lecture 1 Canvas for more information:
[[Lecture 1.canvas|UML Figure 1]]

## UML Class Relationships
### Generalisation #Generalisation #IsA
 The relationship between a superclass (parent) and it's subclass (children), known as *"is...a"*
 An example would include:
- A car is a vehicle
- A lorry is a vehicle
- Pizza is food
- Burger is food

### Association #Association 
A general description of relationship between two or more classes
### Aggregation #Aggregation #HasA
A kind of association #Association typically known as a *"has...a"* relation
An example of this would be:
- Book has a chapter
- Car has a wheel
### Composition #Composition #OwnsA
A more specific kind of aggregation #Aggregation typically known as *"owns...a"*.
Classes that are bounded by composite aggregation #Aggregation #Composition are dependant on each other for their existence
An example of this would be:
- Picture of a tree can be compose of a green circle and a brown rectangle, both shapes need to exist for the tree to be complete. If 1 shape is removed, the other shape would also need to be removed (as they both need each other exist)
### Realisation #Realisation
A class implements an interface #Interface #Implements #Class 
`public class chicken implements food ` 
### Dependency #Dependency
One piece of code is relied upon other piece of code (being dependant) for the correct functionality

# Object Orientation #OO
- Objects are a fundamental data entity in a Java Program #Objects #Java 
- Java programs also manage primitive data such as numbers and characters
- Objects usually representant more complex concepts such as bank accounts
- Objects often contain primitive data types, these include integer, floats, Boolean, doubles, and char #Integer #Float #Double #Boolean #Char 
	- A bank account object would contain a numeric account balance (using a float), the account code (using a string or integer) and the name of the account (using a string)
- Objects are instances of a class
- Class contains the definitions of data values (name and type) and operations (method, header, and body) for the objects of that class
	- Class is stored in the file system of a computer, with the extension `.java`
	- After compilation, a file with the `.class` extension is produced, these can be executed
- Multiple objects can be instantiated from that class ("There can be multiple bank accounts, where each bank account keeps track of it's own balance and information)
	- This is called Encapsulation #Encapsulation where it can protect and manage its own information

## Inheritance #Inheritance
- Classes can be created from other classes via inheritance
- This means that one classes definition can be based on another class that has been defined
- Inheritance can lead to reuse of existing code, promoting recycling 
- A class that inherits or derives from another class is the subclass (child) of that class, the class which the subclass is derived from is known as the superclass (or parent) #Subclass #Superclass
- A hierarchy is created from subclasses deriving from subclasses
- Super classes define the common characteristics
- Differences will be defined in derived subclasses
[[Lecture 1.canvas|Figure 9]]

## Abstraction #Abstraction
- Objects are abstractions which means the precise details are hidden from the user
	- A watch is a abstraction, we don't need to know how it work only that it tells the time
	- A phone is a abstraction, we don't need to know how it work only that it works 
- Abstraction confines them to the minimum scope, doesn't remove the details
- Objects are seen as abstractions by other objects because the details of it's implementation is ignored from other collaborating objects, the collaborating objects only know what objects can do and how it can be instructed, which means it can focus on the essential. Objects can change as long as it performs the same tasks for the collaborators
- a *interface* class is an abstraction, the methods are abstract and contain no implementation details
- Abstract classes cannot be instantiated

## Creating Objects #Objects
- Java variables can hold primitives or reference an object
```Java
int x; // x intialised as 0
Integer y; // intialised as null

y = new Integer(74); // using the "new" keyword, we can intialise the integer object
```

- Object reference variable, like *y*, stores the address where the objected is stored in computer memory 
- Certain objects don't require explicit instantiation, like strings because they're used frequently

## Class Libraries and Packages #Class #Libraries #Packages
- These are libraries that are set of classes that support the development of programs
- They are supplied by the language or third-party vendors
- `String` class is part of the Java standard class library, not part of the Java language
- the standard class library is made up of related classes, called Java APIs. Java Database API includes classes that support database applications. Java Collections Framework (JCF) has classes and interfaces for modelling collection types including: #LinkedList #ArrayList #TreeSet #HashMap #ArrayBlockingQueue #PriorityQueue 
- These are grouped into packages #Packages where related classes are grouped into one package name
- `java.lang` package contains `String, StringBuffer, System, Iterable` 

## The `import` Declaration #Import
- A import statement should be used if classes are to be used from other packages
```java
import java.util.ArrayList; // Import only ArrayList
import java.util.*; // Import everything
```

## State and Behaviour #State #Behaviour
- Objects have state and behaviours
- State refers to the value of a object's variable
- Behaviour is the actions that an object can take, this is done using method call 
- Behaviours, unlike state, are consistent through objects of a class

## Classes #Class 
- Classes are the blueprint which objects can be created
- Objects are defined by the class (what state and behaviour does a object have?)
- Class contains the data that will be stored in each object and the methods that can be invoked, these are called *members*
[[Lecture 1.canvas|FIgure 10]]
- Visibility modifiers (private, public, protected) are used when defining a member of a class
- To make encapsulation is enforced, fields and helper methods are defined as private (for protection)
- By default, all members have package access is no visibility modifiers are used
## Instance Data #Instance
- Where a variable is defined, defines the scope
- Variables declared inside the class but not the method can be used by any method, this is called **Instance Data**
## Encapsulation #Encapsulation 
- Objects can be thought of in 2 ways:
	1. As a developer of that particular object, we need to know the details of how that object works
	2. As a develop of other objects (in a larger context) we only need to know what services (functionality) that object provides
- Objects should only modify their own variables (via methods), it should be difficult for other objects to change the variable within that class, this is *Encapsulation* #Encapsulation 
- Objects attributes and the details are hidden from other objects
- Any code that uses an object, called a client, should not be allowed to access any variable directly
**"Don't access your object's data directly; use it's method"**
# Visibility Modifiers #Modifiers #Private #Public #Protected
- Modifiers are reserved words that is used for a particular characteristic 
	- the `final` modifier is used to declare a constant
- Access to the members of a class is controlled via modifiers
- `public` and `private` can be applied to variables or methods in a class 
	- `public` means it can be access outside of the class
	- `private` means it can only be access inside the class
- `protected` is only relevant when it comes to inheritance
[[Lecture 1.canvas|Figure 11]]

## Local Data
- Local data is declared inside of a method, only has the scope within the method that it is declared
- Parameter names within the header of a method are also local data
- Only exist until method is called, cease to exit when the method is exited
## Constructors #Constructor
- Constructors are used to establish the initial state of an object
- Constructors are different from methods:
	1. Constructor will always have the same name as the class
	2. Constructors cannot return a value, no return type in the header

## Method Overloading #MethodOverloading #Method

- The same method name can be used with different parameter lists for multiple methods, this is called *Method Overloading* 
- a method's signature is the name, number, type, and order of its parameters and as long as the method signature is unique, the compiler can tell which method is being referenced
- `System.out.println` is a overload method:
	- ```Java
	  println(String s);
	  println(int i);
	  println(double d);
	  println(char c);
	  println(boolean b);
	  ```
- Method overloading is used to define constructors of a class:
	- `ArrayList()` - Constructs an empty list with a capacity of ten
	- `ArrayList (int initialCapacity)` Constructs an empty list with specified initial capacity 
	- `ArrayList(Collection<? extends E> c)` - Constructs a list containing elements of the specified collection, in the order they are returned by the collection's iterator
# References #References
- If an object variable doesn't point to a object, it is a `null`reference 
- An object may also reference itself using `this`
```Java
public class SavingAccount
2 {
3 // instance variable declarations
4 private float balance;
5 private int accountNumber;
6 private String name;
7
8 /**
9 * Constructor for a SavingAccount object
10 */
11 public SavingAccount(int accountNumber, String owner)
12 {
13 this.balance = 0;
14 this.accountNumber = accountNumber;
15 this.name = owner;
16 }
17
18 }
```
	this keyword simply means that its referencing the current object in a method or constructor 

# Garbage Collection #Garbage
- Garbage is when all references to an object is discarded, access to that object is not allowed
- Java performs automatic garbage collection, it collects objects marked as garbage, returns their memory to the system
- Other languages require manually returning the memory

# Passing Objects as Parameters #Objects #Parameters
- Formal vs Actual Parameters
	- Formal parameters are listed in the header of a method
	- Actual parameters are listed in the call to a method
```Java
int sum(int a, int b) // Formal parameters, listed in the header of a method

sum(a = 5, b = 5) // Actual parameters, listen in the call of a method
```
- Parameters are passed by value in Java, the value of the actual parameters is copied into the formal parameters however for object reference variables, the formal parameter becomes a alias to the actual parameter
	- Since they are the same, changing anything would change the other

# The `static` Modifier #Static 
- The `static`variable means that there is only one copy of a static variable for all objects of a class (it belongs to the class, rather than a specific instance, even if no objects are created), it is a reserved word, used as modifier #Modifiers to declare a static variable #Variable
`private static int count = 0;`
- They are also known as class variables
- Used for memory management

# Static Methods #StaticMethods #Static
- Static methods are shared among all instances of a a class, just like a static variable, they are often used to together as there is only one copy of a static method for all objects of a class
- Static modifier is used to make a method static, also known as a class method
- They can be invoked via reference of the class name rather than being a instantiated object
```Java
System.out.println("Square root of 27: + Math.sqrt(27));
```
	The method of sqrt is used directly, no object is created

# Static Classes #Static #StaticClass
- Static can also be used with a class, classes include field and methods but they can belong to an object of the class, classes can include another class as it's member (called inner classes)
- To promote encapsulation, inner classes are defined as static
```Java
package dsaj;
2
3 import java.util.Iterator;
4 /**
5 * Class BinaryTree models some operations of a binary tree.
6 *
7 * @author A Barnes
8 *
9 * @param <T>
10 */
11 public class BinaryTree<T> implements Iterable<T>{
12
13 protected BinaryTreeNode<T> root;
14
15 // constructs an empty tree
16 public BinaryTree() {
17 root = null;
18 }
19
20 /**
21 * Constructs a tree with just a root node
22 * @param element
23 */
24 public BinaryTree(T element) {
25 root = new BinaryTreeNode<T>(element);
26 }
27
28 /**
29 * Reset the tree to empty state
30 */
31 public void clear() {
32 root = null;
33 }
34
35 // OTHER METHOD DETAIL OMITTED
36
37 /**
38 * Inner class for modelling a node on a binary tree.
39 * @author A Barnes
40 *
41 * @param <E>
42 */
43 protected static class BinaryTreeNode<E> {
44 public E element;
45 public BinaryTreeNode<E> left;
46 public BinaryTreeNode<E> right;
/**
49 * Constructor for creating a leaf node
50 * @param element
51 */
52 public BinaryTreeNode(E element) {
53 this.element = element;
54 left = null;
55 right = null; // no children
56 }
57
58 /**
59 * Returns true if this binary tree node is a leaf node,
60 * i.e. a tree node with no children.
61 * @return Returns true if this is a leaf node;
62 * returns false otherwise.
63 */
64 public boolean isLeaf() {
65 return (left == null && right == null);
66 }
67 }// end of inner class
```
# Wrapper Classes #Wrapper
- To use primitive data types to be used in a object content,  they need to be classes. This is provided by Java as wrapper classes
	- int - Integer
	- short - Short
	- long - Long
	- float - Float
	- double - Double
	- char - Character
	- boolean - Boolean
- Wrapper classes provide useful methods such a `MIN_VALUE` and `MAX_VALUE`to represent the smallest and largest `int` values
- Custom wrapper classes may also be defined
```Java
package dsaj;
2 import java.util.Stack;
3 /** Class PureStack is a wrapper class which uses a java.util.Stack object
4 * to model the contents and the operations of a pure stack.
5 * @author S H S Wong
6 */
7 public class PureStack<I> {
8
9 private Stack<I> contents;
10
11 /**
12 * Constructor: creates a new java.util.Stack object to model
13 * the contents and the operations of a pure stack.
14 */
15 public PureStack() {
16 contents = new Stack<I>();
17 }
18
19 /**
20 * Adds one element to the top of the stack.
21 * @param the element to be added to the stack
22 */
23 public void push(I item) {
24 contents.push(item);
25 }
26
27 /**
28 * Removes and returns the top element from the stack.
29 * @return the element at the top of the stack
30 */
31 public I pop() {
32 return contents.pop();
33 }
34
35 /**
36 * Returns the top element of the stack without removing it.
37 * @return the element at the top of the stack
38 */
39 public I peek() {
40 return contents.peek();
41 }
42
43 /**
44 * Returns the number of elements in the stack.
45 * @return the number of elements in the stack
46 */
47 public int size() {
48 return contents.size();
49 }
50
51 /**
52 * Returns true if the stack contains no elements and false otherwise.
53 * @return true if the stack contains no elements
54 */
55 public boolean isEmpty() {
56 return contents.isEmpty();
57 }
58
```
# Interfaces #Interface #Abstraction
- Interface can be used to define abstraction
	- Bank provide a lot of accounts (current, saving, mortgage) these share some common operations
		- This can be defined in Java as a interface to capture the common features
- Java interface are abstract and constant methods, java interfaces are public and they don't have any implementation
```Java
/**
* A java interface to model the complexity of a task
*
*
*/

interface Complexity
{
	void setComplexity(int complexity);
	int getComplexity();
}
```

- Method implementations are provided for each abstract method, all methods in a abstract class are accessible by other classes, so they are `public abstract`
- `implements` is the reserved word that is used for implementation

```Java
public class Questions implements Complexity
{
	int difficulty
	
	public void setComplexity (int complexity)
	{
		difficulty = complexlity;
	}
	
	public int getComplexity()
	{
		return difficulty;
	}
}
```

- A class that has implementation for all abstract methods in a interface by doesn't explicitly use `implements`is considered to *not* be a implementation of a interface
- A single class may implement multiple interfaces, multiple classes may implement the same interface
### Interfaces - `Comparable` #Interface #Comparable
The `comparable` interface contains one method, `compareTo`
-  `compareTo` which takes an object (as a parameter) and returns a integer 
	- `int result = obj1.compareTo(obj2);`
- `compareTo` compared the current object (obj1) with the specified object (obj2) to determine their order, this is import when sorting objects
- `compareTo` should return:
	- negative if obj < obj2
	- 0 if obj1 and obj2 are equal
	- positive if obj1 >obj2
- `Comparable` provides a mechanism to compare objects of same type according to some order, classes that can be naturally ordered should implement `Comparables`
### Interfaces - Iterator #Interface #Iterator
- This is a interface used by classes (that represents a collection of objects) to provide a means to move through the collection one object at a time
- `Iterator` has `hasNext()` (which returns a Boolean) and `next`(which returns a object)
- It also has `remove()` which is to remove the object returned by the recent call of the next method
### Interfaces - Iterable #Interface #Iterable
- `Iterable` has a method called  `iterator()` (no parameters) and returns an `Iterator` over the given collection
- Collection classes that implement `Iterable` interface allow it's objects to use and be a target for a enhanced for statement 
	- Elements within such a collection object can be iterated through one by one using a enhanced for statement (for each) 
## More on Inheritance #Inheritance #Subclass #Superclass
- To derive a class from the definition of another class is called Inheritance, this is the heart of software reuse and new classes via inheritance are cheaper, easier, and faster 
- Classes group objects with similar characteristics
- A `Mammal` class would describe the state and behaviour of the mammals using variables and methods
	- From this a `Horse` class can be derived, it would inherit all variables and methods from the `Mammal` (super)class while the `Horse` class can have it's own variables and methods
- The original class is called a superclass or parent
- Derivation is a *"Is...A"* relationship between the 2 classes #IsA 

### Inheritance - the `protected` Modifier 
- The `protected` modifier can only apply to Inheritance
- A subclass does not have access to the variables and methods that are declared private within in the superclass and only those that are public (within the superclass)
	- All variables and methods declared public breaks encapsulation #Encapsulation
- The `protected` modifier provides the child class variables and methods but maintains encapsulation
	- Variables or Methods that are declared using the `protected` modifier can be access by any class in the same package
### Inheritance - the `super` Reference #super
- `super` is used by a subclass to refer to it's superclass 
- `super` is a general references to the members of it's superclass while `this.` is only within a specific instance (scope)
- It it used to call the constructor of the superclass
```Java
public class Horse extends Mammal {
	public Horse() {
		super();	
	}
}
```
	The super() invokes the constructor Mammal() as it extends (inherits) from it 

### Inheritance - Overriding Methods #Override
- a child class may have it's own methods, with the same name as it's parent (superclass) with different implementation (and a child class inherits all variables and methods of it's superclass) this may cause issues, this is where overriding is used
- An example of this would be to redefine the `toString()` in `java.lang.Object` to suit their own needs
	- If a method is defined with a `final` modifier, it cannot be overriden

### Inheritance - Class Hierarchy #Class #Hirearchy
- A superclass that has a subclass, can be a parent of it's own class and one single superclass can have multiple subclasses

### Inheritance - the `Object`class #Object
- Classes are derived from the `Object` class
- `Object` has it's own `toString()` method, often overridden by the `String` class (as it has it's own implementation of `toString()`)
- `Object` has it's own `equals()` method which is used to test if 2 objects are aliases and is also overridden
	- It is overridden by `String` class which has it's own implementation
- `Object` provides a `hashCode` which returns a hash code value (as a #Integer) which is used by a hashtable #Hashtable which is used to implement a collection #Collection
- If the `equals()` method is redefined, `hashCode()` must also be redefined
	- if two objects are equal to each other, they have the same hash code

### Inheritance - Abstract Classes #Abstract 
- Abstract classes may include abstract methods or fully implemented methods
- Abstract classes cannot be instantiated and it is declared abstract by having the `abstract` modifier in the class header
- Classes that are conceptually abstract would have use for abstract classe
	- Like vehicles
- Abstract classes are useful for the implementation of collection types, a class called `AbstractSet` can be used to model other set operations like `addAll()`, `isSubset()`, `equals()`
	- the methods can be modelled in a superclass
```java
package dsaj;

import java.util.Iterator;

public abstract class AbstractSet<T> implements setADT<T> {
	// details ommited
}
```

### Interface Hierarchies #Hirearchy 
- Just like classes, a hierarchy of interfaces can also be applied in the same respect
- A child interface inherits the abstract methods and constants of the parent interface 

# Polymorphism #Polymorphism
- Polymorphism or "having many forms", a polymorphic references simply means that a reference variable can refer to different types of objects at different points in time
- Whatever referenced method by a polymorphic references can change, from one mention to the next
- Dynamic binding is needed for polymorphic references as normal bindings call at compile time, dynamic bindings must call at run time

``` Java
Mammal pet; // variable pet can be ANY Mammal (Horse, Dog, Cat, Lion etc), value of null


/*
Create a new Horse object (Horse is a subclass of the Mammal superclass)
Call it ManhattanCafe
Intialise it as a new Horse object
*/
Horse ManhattanCafe = new Horse();

// Assign previous variable pet (Mammal) to reference ManhattanCafe (Horse
// This is allowed because Horse is a Mammal
pet = ManhattanCafe;

/* 
While pet may reference ManhattanCafe (Horse object) it can only use 
The fields and methods of it's superclass (Mammal) and must be casted
into a Horse to use the Horse specific methods and fields 
```

- This can be easily thought of as variable pet wears Mammal shaped glasses (can only see what is within the Mammal class) whereas ManhattanCafe wears Horse shaped glasses (can see what everything a horse can do)
- Pet behaves as a Mammal object while it's real object (Horse) behaves as a Horse object
	- Polymorphism as a result of Inheritance #Inheritance 
- Interfaces can also be effected by Polymorphism
- An analogy for this would be a "*One to many*" relationship. If there is 1 job, many people can have that job but each person would do it in their own way, hence being polymorphic (having many forms or in this case many ways to do a job) 

- An interface called Speaker can be the one job or tasks
```Java
public interface Speaker
{
	void speak();
	void annouce(String announcement);

}
```


- Then we hold a seminar (where the task can be performed) and we have the current speaker of the seminar
- Depending on what is inputted (if it's 'd' or nothing) then:
	- then the reference variable of current would be initialised as Dog, the dog could perform it's job by saying "Woof"
	- if it's nothing then the variable current would be initialised as Philosopher, the philosopher can perform it's job by saying "Don't depend too much on anyone in this world because even your own shadow leaves you when you are in darkness"	
```Java
public class Seminar
{
	private Speaker current;
	
	public Seminar(char type) {
		switch (type)
		{
			case 'd': this.current = new Dog();
				break;
			default: this.current = new Philospher();
				break;
		}	
	}
}
```

- **Polymorphism, at it's core, is just one to many relationships**

# Generic Types #Generic #typeVariable
- A generic type is a type that is not specified until the class is instantiated, this is done by using *Type Variable*

- If we need a class called Box which manages and stores objects (like a box), this is how it would be done
```Java
public class Box<T> {
	private ArrayList<T> contents;
	
	// Omitted
}
```

```Java
Box<Widget> box1 = new Box<>(); // Box is instantiated to hold objects of the Widget class 

// Box is instantiated to hold objects of the gadget class
Box<Gadget> box2 = new Box<>();
```

- During run time, *T* (for example in `public class Box<T>`) is replaced via with whatever is used in the declaration of the class, this is called as type variable

```Java

public class Raffle {
	// Box object is holding Ticket AND Prizes, which replacing *T*
	private Box<Ticket> ticket;
	private Box<Prize> prizes;
	
	
	// Constructor
	public Raffle {
		ticket = new Box<>();
		prizes = new Box<>();	
	}
	
}
```

- Since Java 7, the value of a type can be inferred which means it doesn't have to be explicitly declared. In the above code block, as the type can be inferred from `Box<Ticket> or Box<Prize>` the constructor can leave the type parameter blank
## Generic vs Type Casting #Generic #typeCasting
- In previous Java versions it was necessary to type cast all objects that are stored in collections, this must be casted explicitly otherwise it would lead to run-time error
- Collection object is designed to hold any type of object references, it doesn't have to be the same type and this is done by assuming the elements are instances of class `Object` 
	- So to interact with the object (the real object) it must be type-casted explicitly otherwise it would a `Object` object
- Generics was introduced in Java 5, this provided a better approach to work with collection without having to explicitly type cast

# Standard `for` vs Enhanced `for` #For #enhancedFor #Iterable #Iterator 
- Enhanced `for` loop allows easier formulation for a `for` loop

Standard `for` loop
```Java
public void showLots()
{
	    // Intialise step, test step, no update step
	for(Iterator<Lot> it = lots.iterator(); it.hastNext()) {
		System.out.println(it.next());	
	}
}
```

Enhanced `for` loop
```Java
public void showLots() {
	for(Lot lot : lots) {
		System.out.println(lot);	
	}
}
```

This can be read as:
- For each `Lot` object in the collection *lots*, output each object to standard output stream 

- The right hand side of the colon must reference a collection objects like *lots* or a static array
- The left hand side of the colon is an element within the collection or static array (`Lot` object)

- Enhanced for loops may provide a simpler syntax but require the use of `java.util.Iterator` to go through a collection and if a collection can't provide the `Iterator` than the enhanced `for` will fail to work 
- All collection objects that wish to use enhanced `for` loops must implement the interface `Iterable` as it contains the `iterator()` method 

No `Iterator` object, failed due to syntax error
```Java

public class Raffle {
	// Box object is holding Ticket AND Prizes, which replacing *T*
	private Box<Ticket> ticket;
	private Box<Prize> prizes;
	
	
	// Constructor
	public Raffle {
		ticket = new Box<>();
		prizes = new Box<>();	
	}
	
	// List prizes 
	pulbic void showPrizes() {
		for(Prize p : prizes)
		{
			System.out.println(p);	
		}	
	}
	
}
```

To fix this, we implement `Iterable` 
```Java
import java.util.Iterator;
import java.util.ArrayList;

public class Box<T> implements Iterable<T>
{
	private ArrayList<T> contents;
	
	public Box() {
		contents = new ArrayList<>();	
	}
	
	/**
	A method to return a Iterator object 
	as ArrayList 	
	
	
	*/
	public Iterator<T> iterator() {
		return contents.iterator();	
	}
}
```
- By implementing `Iterable<T>` and importing `Iterator` this basically says that we make our program loop able with the help of `Iterator` by calling it via the `iterator()` method

# Exceptions #Exceptions #Try #Catch #Finally
- Exceptions are thrown when problems arise in Java programs such as `NullPointerException` which is thrown because *application attempted to use null in case where an object is required*
- Instead of returning null values, exceptions can be thrown

```Java
import java.util.ArrayList;
import java.util.Iterator;
import java.util.Random;

public class Box<T> implements Iterable<T> {
	private ArrayList<T> contents;
	
	// Pick item from box
	public T draw() {
		if(contents.isEmpty())
			throw new IllegalStateException("Empty box.");
			
		
		Random randomizer = new Random();
		int which = randomizer.nextInt(contents.size()):
		 return contents.remove(which);	 }
}
```

- Exceptions are objects that is used to define a usual or erroneous situation
- Once a exception is thrown, the program is halted which would mean there is no need for a `if` or `else` statement as the rest of the statements won't be executed

- Errors represent a unrecoverable situation even if it's similar to a exception

- There are 3 ways that exception can be handled:
	1. Not handle it 
		1. If exception isn't handled, it was produce `Exception in three "main" java.lang.ArithmeticException: / by zero at Zero.main (Zero.java:17)`
	2. Only when it occurs
		- To handle it when it is thrown, this is done via a `try` statement with `catch` clauses
	3. Handle it at another point in the program
		- If exception isn't handled where it occurs, control is returned to the method, if that method doesn't handle the exception (using `try` and a `catch` clause) then control is returned back to the method that called it, this is called propagating the exception
		- This continues until it is caught and handled and if it's propagated out of the `main` method then the program is terminated

- Handling exception when it is thrown:
```Java
try {
	// what to try
}
catch (IOException exception) {
	// statments that handle the IO problem
}
```
- If a exception is thrown, control is passed to the first catch clause which the exception corresponds to the class of the exception that was thrown
- In general it is a bad programming practice to catch an exception using the `catch` clause but there is no way to handle the exception:
```Java
import java.io.File;
import java.util.Scanner;

public class BadPractice {
	
	public BadPractice {
		
		try {
			Scanner in - new Scanner(new File("My Expenditure.txt"));
			while (in.hastNextLine()) {
				String record = in.NextLine();	
			}
			catch (FileNotFoundException exception) {
			  // do literally nothing	
			}	
		}	
	}	
}
```
- However if it's intended that nothing should be done, exception should be propagated to the calling method which can decide what to do

- `try` and `catch` can also have a `finally` clause:
- `finally` will only execute after `try` AND `catch` have been executed, even if  `try` has ended `finally` will still be executed
- This can be useful during File I/O operations where files may not be found, this may result into an IOException being thrown but the `BufferedReader` object would stay open (bad practice). This can be solved using the `finally` clause to close a resource regardless of `try` 
```Java
public static String readFirstLineFromFileWithFinallyBlock(String path)
throws IOException

{
BufferedReader br = new BufferedReader(new FileReader(path));
try {
return br.readLine();
} finally {
// Ensure that the BufferedReader is closed at the end
if (br != null) br.close();
}
}
```
- With Java 7 however, `finally` doesn't always have to be used and instead a `try-with-resources` can be used instead:
```Java
public static String readFirstLineFromFile(String path) throws IOException {
	try (BufferedReader br = new BufferedReader(new FileReader(path))) {
		return br.readLine();	
	}
}
```
- `BufferedReader` will close regardless

[[Lecture 1.canvas|Figure 22 showing the Error and Exception class hierarchy]]
