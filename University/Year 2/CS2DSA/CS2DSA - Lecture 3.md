---
next: "[[CS2DSA - Lecture 4|Lecture 4]]"
previous: "[[CS2DSA - Lecture 2|Lecture 2]]"
tags:
  - "#AbstractDataTypes"
  - Stack
  - Queue
  - List
  - Set
  - Multi-Set
  - Map
  - ADT
aliases:
  - CS2DSAL3
  - L3
  - ADT
image: https://images.unsplash.com/photo-1485470733090-0aae1788d5af?ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxzZWFyY2h8M3x8d2FsbHBhcGVyJTIwNGt8ZW58MHx8MHx8fDA%3D&fm=jpg&q=60&w=3000
---

# Unit Objectives
- Define the concept of an Abstract Data Type
- Define the concepts and terminology related to collection ADTs
- Discuss the abstract design of selected collections: stack, queue, list, set, multi-set, and map
# Abstract Data Types 
#AbstractDataTypes #ADT 
This is a mathematical specification of a *set of data* and *set of operations* that can be performed on the data so this data type is *abstract* so the focus is on the behaviour and properties rather than implementation #Abstract 

The structure of the data isn't specified nor is the implementation (what is acting on the data). These details do not affect the use of the data type and the implementation details maybe changed without the client being affected or notified 

With ADTs we may know the structure of the data type (linear or hierarchy) and what can be done with the data, but not how the data type is implemented #dataType

Examples of ADTs are:
1. string #String
2. list #List 
3. stack #Stack
4. queue #Queue 
5. set #Set 
6. map #Map
7. tree #Tree
8. or a rational number (fractions) #Fractions

Same ADT's can be implemented in multiple ways, for example a stack can be implemented using a array or linear linked structure but the underlying implementation doesn't matter as long as the stack still acts as a LIFO collection #LIFO #LastInFirstOut

# Collections 
#Collection 
Collections are objects that contain groups of objects, the objects within a collection are typically of a fixed type and depending on the collection, the objects can be organised in different ways (ordered, unordered etc) and each object within the collection is called an *element* 

The fundamental collections in computer science are:
1. stack #Stack 
2. queue #Queue 
3. list #List 
4. tree #Tree 
5. graph #Graph

These collections can be categorised as being:
- unordered (no logical order)
- linear (arranged logically in a straight line) #Linear (line of people in a queue)
- nonlinear (arranged in a hierarchy) (family tree or a web of friends)

![[{A5786C0C-AABB-4299-ACAB-74DDAB031101}.png]] 
- Figure 1 shows a linear collection on the left with a nonlinear collection on the right
The order of elements within a collection are based on: 
1. The order in which they were added to the collection (Shopping List, Stack, Queue)
2. Inherent relationship within the elements themselves (Alphabetical or Numerical order)
*In a supermarket queue, people are kept int the order they joined the queue whereas for a telephone directory, they are kept in alphabetical order*

The collection that should be used is dependant on what is being accomplished and how the collection would be used

The internal structure doesn't need to match the logical structure, what this mean is that a list which is linear ordered (logically) can be stored using a binary search to have a fast searching of the list #List . A set of objects that has no logical ordering could be ordered internally (based on a defined order) to have a faster implementation of set union #SetUnion and intersection #Intersection

**A data structure may look simple on the outside but maybe more complex on the inside as to be more efficient**

Collections might allow for fast access to elements but maybe slow to update while the reverse can be true. Operations of one collection can be easier to implement compared to others and the reverse might be the case for different collections

## Bounded and Unbounded Collections
#Bounded #Unbounded 

Collections can be of 2 types:
1. Bounded - There is a limit to the number of elements that a collection can contain (*collection has a max capacity*)
2. Unbounded - There is no limit to the size of the collection (other than limits on resources like memory or CPU)

### Bounded
A bounded structure in Java is the `array` #Array . When the array is created, the length is specified in the constructor which is then fixed for it's lifetime. Any collection that's implementation is based on array will be bounded where as the Java `ArrayList` #ArrayList  is a unbounded collection where the size can increase without limits

Any collection ADT would provide operations:

- `isEmpty()` - to enable a client to know if the collection is empty
- `size()` - to return the current size (the number of elements) in the collection 

It shouldn't be possible to remove an element if the collection is empty so `remove()` should thrown an exception which can be done using try and catch or checking if the collection is empty before attempting a removal by calling `isEmpty()` 

A *bounded* collection ADT should provide operations:
- `isFull()` - lets the client know if the collection is full
- `capacity()` - return the maximum size of the collection 

This is unnecessary for unbounded collections.

For bounded collection, it shouldn't be possible to add an element to a collection that is full so the `add()` method should throw a exception or by checking if the collection is full using `isFull()` 

### Unbounded
- Grows dynamically (only limitation is available memory)
- `ArrayList` expands automatically
Unbounded has, just like, any collection ADT would have
- `isEmpty()`
- `size()`
however, it doesn't have `isFull()` nor `capacity()` as they don't fit for unbounded collections. Array List, unbounded collection, cannot get "full" nor get the "the maximum size" as the only constraint is memory of the device  
## Collections and Abstraction
#Collection #Abstraction 
Abstraction hides details of implement so it's easier to deal with the complexity of a larger system

This can be achieved within in Java, using interfaces #Interface 

This is allows programmers to focus on what *it* actually does rather than *how* it does it. 

*Simply, this means, a client knows how to use a iterator (to iterator through objects in a collection) but not how it actually it goes through the data*

This means:
1. Modular Design - Changes do not affect clients
2. Flexibility - Implementations can be replaced with another

Collections are abstractions. 
How we interact with the collection should be separate from how it should be implemented. *A user can access the service by not how the service is provided* 

![[Figure2W3]]

ADT - group of values and operations are defined on those values #ADT 
Data structure - programming constructs used to implement data type (array, linked list, linear linked structure) 

## Issues with Collections 
Computer software is bound to work with large number of objects, understanding the characteristics of each collection can provide a informed choice. 
1. How does the collection operate conceptually
2. How do define it's interface 
3. What problems does it help solve 
4. Ways that can be implemented
5. Benefits and cost of execution (cost meaning storage usage or execution time)

# Java Interfaces and Abstract Data Types 
#Interface #AbstractDataTypes #ADT 

- Interfaces provide a way to define the operations on a collection ADT. 
- Java interfaces provide abstract #Abstract  methods #Method that will be implemented by the class #Class 
	- Makes it ideal for defining ADTs 

Java interfaces don't contain data members, suitable for abstract view without any commitment to the way data is represented

A suitable class with data members is required as to store the elements and implement operations of the interface 

The nature of the objects doesn't matter when operations are acting upon a collection. Adding a book to a library is the same as adding teams to a league, it's the same.

This means that classes and interfaces used to develop collection data structure should be generic #Generic  as it would allow the same structure to hold any object type `<T>`

# Stacks 
#Stack 
- They are a linear collection 
- Elements can be added and removed from *only one end* 
- They are depicted vertically 
- They are LIFO #LIFO 
- Pringles are a example of a stack data structure

![[cs2dsa_W3_figure3]]
### Operations 
1. `push(element)` - add to the top 
2. `pop()` - remove and return top element 
3. `peek()` - return top element without removing it
4. `isEmpty()` - check if stack has no elements (if empty)
5. `size()` - the number of elements 

```Java
public interface StackADT<T> {
    void push(T element);
    T pop();
    T peek();
    boolean isEmpty();
    int size();
}

```

#### Bounded Stack ADT
- This adds `isFull()` - to check if the collection is full
- This adds `capacity()` - to check the maximum size of the collection 
A separate `Bounded` interface could also be created that contains this method as which allows multiple ADT's to share it

# Queues 
#Queue 
- Linear data structure
- opening on *each* end
- Elements are added on one end, removed from the other end
- Queue is processed in FIFO #FIFO First in First Out
- Elements are removed in the same order they were added 
- Any waiting line are a queue:
	- supermarket line
	- service queue in banks
	- cars at traffic light
	- assembly line in a factory 
![[cs2dsa_W3_figure5]]

Queues and stacks are similar, both are linear collections but operations are different. Stacks operated at one end while queues operated at both

## Queue Operations
#Enqueue #Dequeue

When a element is added to the queue's tail, it is called *Enqueue* 
When a element is being removed from queue's head, it is called *Dequeue* 

The benefit of using the `peek()` method is that the first element (the element at the head) can be inspected without it being removed (which is what `pop()` does)

Just like a stack, a "pure queue" does not allow the user to access the middle of the queue 

### Operations 
- *Enqueue* - Add element to the queue's tail
- *Dequeue* - Remove element from the queue's head and return it
- *First* - return the element at the head but don't remove it

As just like any collection ADT, it also as the operations of isEmpty and size 

 ```Java
 public interface QueueADT<T> {
    void enqueue(T element);
    T dequeue();
    T first();
    boolean isEmpty();
    int size();
}
 ```
 - For a bounded queue, the class would implement `Bounded` interface as well to use the methods 

# Lists
#List 
Lists are also linear collections, just like stacks or queues but are more flexible 
Lists allow for elements to be added in and removed from anywhere within a list, the add and remove operations aren't dependant on the place on either end. 
Depending on the list, adding elements may be possible within the list at a designated position 

![[CS2DSA_W3_FIGURE7]]
## List Operations 
List types all have several common operations 

| Operation   | Purpose                                  |
| ----------- | ---------------------------------------- |
| removeFirst | Removes the first element from the list  |
| removeLast  | Remove the last element from the list    |
| remove      | Remove a specified element from the list |
| first       | Returns the first element of the list    |
| last        | Returns the last element of the list     |
| contains    | Check if element is on the list          |
| isEmpty     | Check if list is empty                   |
| size        | Returns the number of elements in a list |

The biggest difference between list types is the way elements are added into the list, even though all lists support a add operation, the definition of the operation however is dependant on the specific type of list

Without knowing how a operation like add is supposed to work, it's not possible to define a abstract method for modelling. 
When defining Java interface for a list ADT, the method add isn't included. 

All methods when it comes to interfaces must be abstract and public, there is no need to define the methods as public or abstract 

# Set Collections 
#Set 
Within computer science, a set is a collection of distinct objects of a particular type while in mathematics  a set is written with the elements enclosed in curly braces 
$$
\text{Vowels} \space = {e,u,i,o,a} = {u,a,o,e,i} 
$$
Elements can only appear once within a set, so if a set contains the letter "a"  that already has the letter "a"  then the set is unchanged and would still count as being 1 element rather than 2
There is no sense of order within elements in a set, so it is a unordered collection but internally it can be implemented as a linear data structure for efficiency

## Set Operations 
Just like other collections, set has operations that can be used to interact with, these are:
- determine if set is empty
- determine number of elements in a set
- add one of more specified elements to the set
- remove one or more specified elements from the set
- remove every element from a set except specified elements 
For sets, they have will their own type-specific operations, like any other collection 

# Multi-Set Collections 
#Multi-Set 
A multi-set collection is a like a bag where same elements may appear more than once, just like a bag can have more than one same item 

The multi-set of {a, a ,e ,i} would have 4 elements compared to the set of {a, a, e, i} which would have 3 elements
Just like sets, the order of a multi-set is irrelevant 

## Multi-Set Operations
Operations for multi-set are similar to those of a set where the only difference between a multi-set and a set are the methods that take proper account for duplicate elements 

```Java
//********************************************************************
// MultisetADT.java Author: Alan Barnes
//
// Defines the interface to a multi-set collection.
//********************************************************************

package dsaj;

/* We make MultisetADT<T> extend the interface Iterable<T> so as to make
 * it possible for us to use enhanced for loops with multi-sets */
public interface MultisetADT<T> extends Iterable<T>
{
    /** Adds the element to the multi-set and returns true */
    public boolean add(T element);

    /** Adds all elements of multi-set A to this multi-set
    Returns true if the multi-set is modified, otherwise false */
    public boolean addAll(MultisetADT<T> A);

    /** Removes the element from the multi-set if it is present and returns true
    If the element is not present, the multi-set is not modified
    and false is returned. */
    public boolean remove(T element);

    /** Removes all elements of A from this multi-set
    Returns true if the multi-set is modified, otherwise false */
    public boolean removeAll(MultisetADT<T> A);

    /** Removes all elements from this multi-set
    except those that are in A.
    Returns true if the multi-set is modified, otherwise false */
    public boolean retainAll(MultisetADT<T> A);

    /** Returns a new multi-set which is the union of this multi-set and A */
    public MultisetADT<T> union(MultisetADT<T> A);

    /** Returns a new multi-set which is the sum of this multi-set and A */
    public MultisetADT<T> sum(MultisetADT<T> A);

    /** Returns a new multi-set which is the intersection
    of this multi-set and A */
    public MultisetADT<T> intersection(MultisetADT<T> A);

    /** Returns a new multi-set which is the difference
    of this multi-set and A */
    public MultisetADT<T> difference(MultisetADT<T> A);

    /** Returns true if this multi-set and A contain
    exactly the same elements */
    public boolean equals(SetADT<T> A);

    /** Returns true if this multi-set contains the element */
    public boolean contains(T element);

    /** Returns true if this multi-set is a sub-bag of A */
    public boolean isSubbag(MultisetADT<T> A);

    /** Returns the number of times element appears in this multi-set */
    public int count(T element);

    /** Returns true if this multi-set contains no elements */
    public boolean isEmpty();

    /** Returns the number of elements in this multi-set */
    public int size();
}

```

# Maps 
#Map 
Maps is abstract data type (ADT) that maps set of keys to a set of values 

![[CS2DSA_L3_Figure11]]
Keys in a map *should* be unique but the same value can be associated with different keys 

## Maps Operations 
- Add: Associate a new value with a new key in a map
- Reassign: Associate an existing key in the map with new value
- Remove: Remove a key with its associated value from the set of key-value pairs in the map
- Lookup: Find the value (if any) in the map that is associated with the given key

Maps can also be known as a dictionary, associative array, and lookup table #Dictionary #AssociativeArray #LookupTable

##  Uses of Maps
1. Modelling the records in a telephone/address book (telephone number to an address)
2. Modelling the entries within word dictionary (mapping a word to its meaning)
3. Modelling the records in database table (mapping attributes to it's primary key)
4. Modelling any lookup table 


