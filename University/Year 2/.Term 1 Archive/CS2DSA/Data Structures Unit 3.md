### Lecture 3
### "Abstract Data Types (ADTs)"
An abstract data type is a high-level description of data and operations that focuses on what you can do with the data rather than how it's explicitly implemented.
It's abstract in the sense that we only code or see the logical structure or collection of the data (sort of like a LIFO collection) without knowing the inner workings.
Implementation details are omitted and can be changed without affecting the implementation of the ADT.
We know what operations are available and how they behave, not their specific algorithms or data structures.

### "Collections"
A collection hosts a group of objects, they are typically of the same fixed type.
Depending on the type of collection, the elements can be sorted in different ways.
There are lots of types of collections like stack, queue, list, tree, graph etc.
They can be categorised as either unordered, linear (line of elements) or non-linear (arranged hierarchically or in a network).
![[Pasted image 20260108141217.png]]
The sorting of elements in a collection is based on the order they were added or a relationship between the elements. E.g., at a till checkout, people will be in the order of when they joined the queue, telephone directories are often ordered alphabetically.
The internal structure of a collection and the logical structure of a collection are not mutually exclusive. E.g., a linear ordered list can be stored in a binary search tree, similar to the collection on the right of the above diagram, to facilitate O(n log n) searching of the list.
A set of objects with no logical ordering can also be ordered internally based on some defined order to facilitate implementation of set union and intersection operations.
Some collections allow fast access to elements, but are slow to update elements, whereas for others the reverse can be the case. The same goes for implementing operations of a collection.
### "Bounded & Unbounded Collections"
Collections can be bounded - limiting the number of elements that can be added - and unbounded - not limiting the size of the collection,
Arrays are an example of a bounded collection, when creating an array we specify the length and capacity for the array's entire lifetime.

Collection ADTs typically provide access-based operations, like isEmpty() and size() which returns the current size of the collection.
Bounded collection ADTs also provide isFull() and capacity() which returns the max size of the collection.

### "Collections and Abstraction"
Abstracting a collection makes it easier to deal with a large, complex system.
Java interfaces provide programmers to use abstraction. It allows them to focus on what an object should do and not how it does.
Let's look at the source code below for java.util.Iterator.
Iterators can carry out explicitly abstract methods from an interface, such as hasNext() and next(). With the purpose of abstraction in practice, we know that programmers can replace ArrayIterators with a LinkedIterator.