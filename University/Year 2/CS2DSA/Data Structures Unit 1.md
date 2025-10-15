## #CS2DSA_Concepts

#Big-O-Notation:

-a way of recording the time spent to do an action.

O(1)
	constant time, consistently fast no matter what size of input
O(n) 
	linear time, time increases with the size of input
O(n^2) 
	every item in a data-set interacts with every other item, e.g., 10 students handshaking amongst each other = 100 handshakes. Very slow!
O(log n) 
	faster than O(n) but slower than O(1). Like perusing a dictionary, this algorithm speed goes to the middle of a data set then jumps back or forth to find the inquired data. This halves and halves the operation over and over.

Accessing data via a data-set, like an array, would be an example of O(1). Making a new array in order to add new data, or deleting data (besides data at the very end) which shifts the whole array, would be O(n).

#LinkedLists are lists where the individual data items are separated as nodes. Example below from W3S.
```java
// Import the LinkedList class
import java.util.LinkedList;

public class Main {
  public static void main(String[] args) {
    LinkedList<String> cars = new LinkedList<String>();
    cars.add("Volvo");
    cars.add("BMW");
    cars.add("Ford");
    cars.add("Mazda");
    System.out.println(cars);
  }
}
```
Linked lists can have their items easily removed or added compared to arrays, however perusing the data set is slower overall.
==Accessing items== is O(n) because there's no indexing.
==Inserting items== is O(1) if you reference what nodes you're inserting between, otherwise it's O(n).
Similarly, ==deleting items== has the same caveats. Specifically if you don't use pointers you have to go through the list to delete an item, which is O(n). #Pointers are memory addresses.

#Stacks are Last-in, First-out groups of data, like Pringles. Each element is stored in an ordered manner and to access or alter elements you have to go through each item, there's no indexing. ==Accessing items== in the stack is an O(n) operation.
==Inserting== is O(1) since you just place it on top, and ==deleting== is O(1) too.

#Queues are First-in, First-out groups of data. It's alike a conveyer belt, elements can only be removed from the front and added at the back.
==Accessing== items is O(n) as you have to search through the set.
==Inserting/Deleting== is O(1) as you add and delete from the front and back. 

#Heaps or Priority-Queues are sets where a root data value is always needed, the latter data values are children of the higher data value.
Heaps come in two variations:

![[Min Heap.png | 200]] ![[Max Heap.png | 220]]

==Accessing== is not a typical operation for heaps, but it would be O(1) for the root/first data value and O(n) for following children values.
==Inserting== is O(log n) because of how inserting works. You add the value into the heap, then the value has to bubble up to its right position based on its size.
==Deleting== acts the same, O(log n), as when you delete a root value the smallest or biggest value must shift to the root position.

#Hashmaps store data through key-value pairs. Keys are associated with data within the storage via a Hash-function. A Hash-function could be the length of a String, such as John being in position 4. This makes ==accessing== data from a Hash-map typically O(1), however if there is too much data in one Hash e.g., two names, John and Andy, being in position 4, values will have to be adjusted into a Linked-List and the accessing speed can slow down to O(n).
==Inserting== is a similar scenario, where inserting data is typically O(1) but if there's too many values associated with a single position then it slows to O(n).
==Deleting== is O(1) as you can just delete by key, but again with a Linked-List situation it would become O(n).
Note that Hashmaps are called Dictionaries in Python.

#Binary-Search-Trees store data in nodes that follow an order. Left children have to contain smaller values than the parent, and right children contain higher values than the parent.
==Accessing== and ==Deleting== become an O(log n) operation.
==Inserting== becomes an O(log n) operation, as you can just look through each value and halve your time. If the tree is unbalanced alike a Linked-List, all three operations become O(n).

#Sets include unique values and don't use any specific order.
==Inserting/Deleting== shares its benefits and drawbacks with HashMaps, at best being O(1) and at worst being O(n).
Set Operations and using Sets to remove duplicates from Linked-Lists are common operations. **Definitely need to research.**

## #CS2DSA_UML

UML Diagrams consist of the classes, attributes (fields) and operations (methods) of a class. They include the relationships between classes and the constraints (features) of connections between objects.
![[{EB546BF4-1E45-487B-9EB2-FCAB63ACF59C}.png | 300]]
This UML diagram depicts an abstract class with private fields and public methods, each showing their parameter type and structure.
![[{75AE6DB5-93B9-465A-82DF-47E2799B9522}.png | 600]]
This UML diagram shows multiple classes, some of which denoting how much of an object they can input or output. e.g., 1 person can have 0 or 1 pet and 1 person can have 1 car, the Car and Pet classes inherit the Ownable class which holds their logic to interact with the Person class.
Inheritance involves superclasses and subclasses, which allows for logic reuse and streamlining activities.
This UML diagram is a more streamlined rendition which allows for more Ownables of each type being allocated to a single Person.
![[{01BBEE7C-D9B0-42B7-A65E-396D12E90425}.png | 600]]
Typical components of a UML class diagram:
- class (abstract/concrete)
- interface
- relation:
  -association "owns a" or "borrows" etc
  ![[{322AF244-0107-438F-8822-9102386C9FC2}.png | 500]]
  -aggregation "has a" or "has"
  ![[{C5F50ECA-5F32-4D38-9FA5-463CAB8F8F86}.png | 500]]
  -composition "is part of a" or "makes up"
  ![[{799F71D4-0F63-4A89-9A6D-EBEF4F6E8435}.png | 500]]
  -dependency "uses"
  ![[{5C48227D-8094-4FE1-B08E-AE3A947C6679}.png | 500]]
  -generalisation "is a" or extends
  ![[{CDA17F12-435F-40B6-A2F4-77E5247D6FDB}.png | 500]]
  -realisation or implements (interface has method names, implementing class uses that method name with its own code)
  ![[{36F93393-22F1-4900-8893-A4EED23818ED}.png | 500]]

  ![[{70DF2244-ACD2-4E38-AA7C-686FEEBDCBEA}.png | 600]]

## #CS2DSA_OOP
### A catch-up on first year CS's OOP module/Object Orientation as a whole.
(Page 5 onwards of the PDF)

Something huge is our definition of an "object". An object in java, unlike the typical vague noun, is not a tangible thing. An object can be a bank account's value or a list of items in a shopping cart. 
==**Objects represent values!**==
#Objects can contain "primitive" data types, numbers, floats, doubles (can store more data than float). They can also represent multiple pieces of data, e.g., a bank account balance (integer), account code (integer or string) and the account name (string).

*An object is an instance of a class.*
==The class would hold the values and logic for the balance, code and name. An object would be the occurrence of those values.
Another example, we have a class "Dog" which holds data for the name and dialogue of a dog object. Then we call a dog object, dog1, which has the name Lucy and "Woof!". That dog1 is an instance of the Dog class.==
```java
Dog dog1 = new Dog("Lucy", "Woof!");
```
Concrete classes can be templates for objects. Abstract classes can be templates for other classes' objects e.g., A car can have general vehicle elements, but has its own features. A truck can be another "subclass" that inherits the abstract "superclass."

Quick side-track, #inheritance is a subclass that "is a" type of the superclass, while implementation is a subclass that "can do" what the superclass says it can. E.g., A Dog subclass could inherit the "legs" "height" "speak" methods from a mammal superclass, but it has to provide the body of logic within the method e.g., the Dog class can implement "speak" with its own specific way of speaking while a Person class could implement "speak" in another way. 
You can't instantiate something that has no body of logic.

Note that this is type of relation visible in UML Class Diagrams. A Car will have its own original methods for registration and getRegistration, but will also extend and therefore inherit the getOwnerTel and changeOwner methods from the Ownable class. (Example of abstract class inheritance, abstract isn't just different ways of using a method but also each instance of a method being different i.e., different cars having different Owners and Telephone Numbers).

![[{E9AADDD0-247F-4539-9FC4-8E2B3FBF9921}.png | 500]]

#Abstraction is an important term, Abstraction is when the precise details of an object is out of focus. A watch is an abstraction, we as consumers don't know how a watch works but we know its output (time). Abstraction confines details to the littlest amount that we need.
A java interface is an example of a class being abstracted.

## Creating objects

#Variables in Java can either hold a primitive value or a reference to an object, e.g.,
```java
int x; /* creates a variable x to hold a primitive integer */
Integer y; /* creates a variable y to hold a reference to
an object of the Integer class */
Integer y = new Integer(74); /* creates a new Integer object with value 74 and
sets the object reference variable y
to point to the new object */
```
Note that the "74" is the parameter for the object being fulfilled.

#Class-Libraries are sets of classes either included in a language or provided by a third party. Groups of related classes can be called API (Application Package Interface). E.g., the Java Database API is a set of classes that supports database applications such as a Microsoft Access, Java Collections Framework is a set of classes and interfaces for making collection types like LinkedList, ArrayList, HashMap, etc.
Stuff like String and System are in the java.lang package (core classes for Java programming).

You can even make packages within your program, e.g.,
```java
package dsaj;

import java.util.Stack;

public class PureStack {
	// implementation detail omitted
}
```
#Behaviours are the actions an object can take whereas #States are a field of a class (e.g., On, Off, could be a variable).
Variables can be objects (like the aforementioned reference Object variable) so a field can be many things.

#Classes define objects, like design blueprints for a house or patterns for a seamstress' new dress. A class declares the data that each object would store, like a cookie cutter defines what shape a cookie would hold. These declarations are the members of the class.
Visibility modifiers like public, private and protected allow other classes to mingle with the members of a class. Most fields and helper methods should be private as a general rule of thumb. Any members that have no visibility modifiers are treated as "package access" aka can be accessible by any class in the same package.

#Instance-Data is when a variable is declared in a class but not inside any method, i.e., right at the top of the class. This data can be referenced in any method of that class, because the location of a variable determines its scope/reach.

When creating and managing objects, we have two perspectives to consider:
- Designing/developing an object and considering the details of how it works
- Designing/developing other objects that can interact with that object, during which we only take interest in the services (outputs) of those objects.
Objects should be "self-governing" meaning that only the object itself can modify the variables it contains, e.g., an object from a Dog class can only control what it outputs as "speech". No other object should be able to modify the variables of the "Dog" object. This attribute is called #Encapsulation.
Each object in a program only interact amongst each other through their methods, their attributes and inner details are hidden from other objects.
==The methods of a class define the interface between objects of that class and the overarching program.==
Code that uses an object, i.e., a client, should not access the variables of the object.
==Use methods, not direct data!==

#Visibility-Modifiers control access to the members (variables and methods) of a class.
Some examples include:
- final, which makes constant/unmodifiable variables
- public, which makes variables usable from anywhere outside of the class
- private, which makes variables only usable from within the class
- protected, which makes variables only usable by a class and any classes that inherit it.
![[{5632EAB2-53A6-45A8-A63D-D39CB50AE525}.png| 500]]

Instance data is declared at the class level, whereas #Local-Data is declared at the method level. Local data can only be used within that method. 
This can include the parameter names in a method header and variables within the method. Local data ceases when its method is not in use.

#Constructors are alike methods that are called when a object is instantiated. Constructors are how we determine the initial state of an object,
Constructors unlike methods hold the same name as their parent class and do not return values (aka a void method).
If a class has no given constructor it has a default one.

#Method-Overloading is when multiple methods share the same name but still function as they have different parameters. A method's name and its number, type and order of its parameters are what make up its "signature".
If each method's signature is unique then the computer will know what method is being referenced.
```java
System.out.println(String s) // This method is a good example of overloading. Each reference has a different parameter so it still works.
...println(int i)
...println(double d)
...println(char c)
...println(boolean b)
```
Method overloading is used for class constructors and providing a client-class different ways to initialise the fields of its parent-class.
![[{D2AC6C6C-0C2A-4886-88C3-DB4AEA666012}.png | 500]]

An object can refer to itself using the keyword "this".
```java
public class SavingAccount {
	private float balance;
	private int accountNumber;
	private String name;
	
	public SavingAccount(int accountNumber, String owner) {
		this.balance = 0;
		this.accountNumber = accountNumber;
		this.name = owner;
		}
	}
```
If an object reference variable doesn't point to an object, it is null. e.g.,
```java
Integer y // no object pointed to, becomes null
y = new Integer(74) // points to an object, has a value
```
Two or more variables can also point to the same object.
![[{41556997-D5FA-452D-978E-4D181E3AF78E}.png | 500]]
Both x and y here reference SavingAccount, so if you change the balance value then both x and y's balance values are altered.

If an object is not referenced at all, it is referred to as "garbage". Java automatically "collects" this garbage, in that the Java runtime environment collects these unreferenced objects and returns their memory allocation to the system for future use. In other languages you would have to explicitly return that memory space.

### Passing Objects as Parameters
Formal parameters is what we call the parameters in the header of a method, whereas actual parameters is what we call those listed in a method call.
```java
// formal parameters
public class SavingAccount(int accountNumber, String owner)
// actual parameters
SavingAccount jamesSaving = new SavingAccount(24009, James)
```
In Java, all parameters are #passed-by-value meaning that when the method is called, the value of the actual parameter is copied into the formal parameter.
However, if an object is used as a parameter then the address of the object is passed and the formal parameter is an alias for the actual parameter.
```java
public class newAccount {
// instance data omitted
	public class newAccount {
	// body of logic omitted
	}
	
	public class isAccountValid(Person person) {
		return person.getName()
		return person.getAddress()
		return person.getPhone()
		}
}
// In this example, isAccountValid uses Person as a parameter to access the data addressed through Person e.g., name, home address, phone number
```
If you modify the object being referenced, i.e., its state, you modify the state of the object referenced by the actual parameter.
However if you modify the formal parameter, such as assigning it to a different object (i.e., y = new Person) then the actual parameters being used are not impacted.

There is another kind of variable, called a #static-variable, which is declared with the keyword static e.g., private static int count = 0;
Static variables are shared amongst all instances of a class, so there is only one version of that variable for all objects of a class. This means that all the objects instantiated through this class share this one variable, regardless of their own additional services. This can be used to keep track of how many objects have been instantiated from a single class.

Static variables are shared among all instances of a class, as well as #Static-methods. As the static variable is declared, a static method will have static in its declaration. Static variables and methods are both referred to as class variables and class methods.
A great practical example of a static method in a class is java.lang.Math:
```java
System.out.println("Square root of 27:" + Math.sqrt(27));
System.out.println("The larger number is:" + Math.max(5, 8));
// Notice how we call the Math class but don't need an object to make use of the methods sqrt or max?
```
java.lang.Math is an API, so we can even call the methods from it without referencing an instance of the class Math, so long as we have the API imported of course.

The keyword static can also be used as a class modifier. A class typically involves fields and methods, can be a class from an object of a class or a class itself (while not being in any instance of that class), a class can also have a class as one of its members. This is called an "inner class".
For the purpose of encapsulation, an inner class can be defined as static. E.g., here we have a static inner class called BinaryTreeNode. The fields in BinaryTreeNode are public so we don't have to get or set them, but we still have a good level of encapsulation.
```java
package dsaj;

import java.util.Iterator;
/**
  * Class BinaryTree models some operations of a binary tree.
  *
  * @author A Barnes
  *
  * @param <T>
  */
public class BinaryTree<T> implements Iterable<T>{

	protected BinaryTreeNode<T> root; // <T> is like a placeholder that keeps this memory address intact for the later created object being referenced.
		// Note that the <T> placeholder is a use of Java Generics.
	// constructs an empty tree
	public BinaryTree() {
	root = null;
	}

	/**
	  * Constructs a tree with just a root node
	  * @param element
	  */
	public BinaryTree(T element) {
	root = new BinaryTreeNode<T>(element);
	}
	
	/**
	  * Reset the tree to empty state
	  */
	public void clear() {
	root = null;
	}
	
	// OTHER METHOD DETAIL OMITTED
	
	/**
	  * Inner class for modelling a node on a binary tree.
	  * @author A Barnes
	  *
	  * @param <E>
	  */
	protected static class BinaryTreeNode<E> {
		public E element;
		public BinaryTreeNode<E> left;
		public BinaryTreeNode<E> right;
		/**
		  * Constructor for creating a leaf node
		  * @param element
		  */
		public BinaryTreeNode(E element) {
		this.element = element;
		left = null;
		right = null; // no children
		}
		
		/**
		  * Returns true if this binary tree node is a leaf node,
		  * i.e. a tree node with no children.
		  * @return Returns true if this is a leaf node;
		  * returns false otherwise.
		  */
		public boolean isLeaf() {
			return (left == null && right == null);
		}
	}// end of inner class
}
```

