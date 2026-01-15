### "What is meant by hashing?"
In previous collections discussed, we have either assumed two things regarding order - order is unimportant or order is determined by the way elements are added.
Order can also be determined by comparing the values of the elements.
Hashing is the idea that the order between elements within a collection is determined by some function of the element to be stored, specifically the location of the element.
Elements are then stored in a hash table, the location of each element in the table is determined with a hash function.

When adding an element to a hash table, the hash function is used to compute the location of the element.
When retrieving the element from the hash table, the hash function is used to once again work out the elements location but within the hash table.
This allows us to avoid searching for the element with an explicit search algorithm, which means element access doesn't involve the hash table's size, making the operation O(1).
Each location in the hash table is called a cell or bucket.

Hashing is the process of computing the location within the hash table where an element will be stored.
Given an element, a hash function computes a hash value for the element which is used to decide its storage location. The java method "hashCode()" returns the hash value of the object.

The below diagram shows a hash table involving an extraction method to perform hashing.
This hash table contains 26 cells, each of which are dedicated to storing first names in English with the same initial such as Anna being stored under the first cell and so on so forth.
![[{9EE3C3C7-1A90-4DDE-9DB7-080D14F9813F}.png]]

### "Hashing: an example"
We can create a simple hash function for storing an array of 26 names using their first letter. We extract the first letter of the string, compute its value relative to the letter A.
We can also associate each letter in the alphabet with its relative position within the alphabet, A = 0 etc.
Below is our example!
![[{9B2DB931-107E-4ABB-8ED7-80B11DD1A473}.png]]
The above example is known as extraction, using only part of an element's value (or key) to compute the location at which to store the element.
This method is also used in the previous diagram.

### "Hashing: another example"
Division is another hashing method, using the remainder of the key divided by a positive integer, p, as an element's hash value. e.g.,
$$ hashValue(key) = Math.abs(key)\%p$$
\- where p can be the size of the hash table.
The symbol % refers to the "modulo operator" which appears in typical programming languages like Java. Modulo operators denote the process of finding the remainder of a division. Such as, this Java statement prints 2 on the console as the remainder for 17/5 is 2.
```java
System.out.println(17 % 5);
```
Math.abs is a static method in class java.lang.Math which returns the absolute value of the parameter, meaning that it removes the - sign from a negative value.

In the case of a library application, where information about books are referenced using their ISBN, not all possible combinations of digits in an ISBN will be used for a book owned by the library. We can define a smaller hash table to store the book information.
The division method will enable book information to be randomly distributed within the hash table.
A good hash function should assign an element to a cell in a random manner. This will ensure an even distribution of elements in the available cells, regardless of element values or collection size.

### "The need for Hashing"
Hashing is useful for when we have a large amount of possible element values, but any collection will only contain a small fraction of the possible values.
In a library application example, ISBN numbers are 10 or 13 digits long, using an array to store the book records with the ISBN as index would enable books to be looked up in O(1) time alongside adding new books being O(1) time.
Even if we use the older style of ISBN which have 10 digits, there are up to 10,000,000,000 possible ISBNs which would be a wasteful size of an array. Not all of those spots would be used realistically, or even given a title.
Using a hash table of size 75,000 or even 100,000 and a good hash function for the ISBN would achieve O(1) for looking up or adding new books.

### "Hashing: some implementation issues"
Using a hashing approach results in the access time for an element being independent of the number of elements in the table. This means that all the operations on an element of a hash table should be O(1), but this efficiency will only be realised if each element has a unique position on the table.
If two or more elements are mapped to one location, a collision occurs.
Hash functions that map each element to a unique position are called perfect hash functions.
When a perfect hash function is achieved, a function that does a good job of dispersing the elements in a table will still result in O(1) operations.
Also, another issue of hashing - how large should a hash table be?

If we are assured of a dataset of size n and a perfect hash function, the table should be of size n.
If a perfect hash function is not achieved, but we know the size n, then we should make the table 150% of the dataset size. If we can't do this, i.e., we don't know the dataset size, we need to use dynamic resizing.
![[{AF9E7F93-3BAE-4A0B-B926-B48CEA136FCA}.png]]
### "Resizing a Hash Table dynamically"
This is like expanding the capacity of an array, we create a new and larger hash table and insert all the existing hash table's elements in that new one (meaning we have to rehash them).
We could resize when a hash table is full, however hash tables always begin to faulter as they become full.
We should use "load factors" which is a percentage occupancy of the table where the table will be resized i.e., at 75 or 75% full the table is resized.

### "Hash functions"
There are a wide variety of hash functions that distribute various types of data. We have looked at extraction and division, which (reminder) compute the location of an element through part of its value (or key) and use a modulo operation against the size of the hash table to decide its location respectively.

### "Resolving Collisions: Chaining"
Chaining involves treating the hash table conceptually as a table of collections rather than a table of individual events. So, each cell is a pointer towards the associated collection of that location in the table.
This internal collection is typically a list.
Chaining can be done with a linked structure or array-based structure with an "overflow area".
![[{D48EAE24-DA34-4483-BD03-5ECA8338DCEC}.png]]
The overflow area allows each cell in the hash table to keep the element stored in the cell with a reference to another cell, in which another element with the same hash value can be found.

### "Deleting Elements from a Hash Table"
If we need to remove an element in the table, but it has an index in the overflow area, we have to replace the element and the next index value of the array position pointed to by the element that is gonna be removed.
We also have to set the position in the overflow area to null and add it back to our list of free overflow cells.
If the element we want to remove is at the end of the list of elements stored at that location, we have to set its position in the table to null, the next pointer of the previous element to null and add that position to the list of free overflow cells.
If we need to remove an element in the middle of lists stored at that location, we need to set its position in the overflow area to null, set the next pointer of the previous element to point to the next element of the element being removed and add the position back to free overflow cells.
If the element to be removed isn't in the table, we must throw an exception.

### "Hash Functions in the Java Language"
In Java, an object's hash code is used to determine where to put the object in a hash table. Java requires that identical objects must have the same hash code value, to ensure appropriate storage.
The java.lang.Object class defines a method called "hashCode" that returns the hash code of the object as an integer. The integer is based on the memory location where the object was initially placed, so no two objects can be truly identical as each memory location only stores one object.
This hash value isn't useful if we need a different definition of object identity, for example two String objects are considered identical if they contain the same sequence of characters.
Reminder! We can define object identity using different criteria.
We might want to define that two BankAccount objects can be considered to be identical if they both have the same account code, doing so by overriding the "equals" method inherited from the super class Object when inheriting the class BankAccount.
```java
public class BankAccount {
	private String accountCode;
	private String name;
	private int balance;
	
	public boolean equals(Object obj) {
		boolean result = false;
		
		if (obj instanceof BankAccount) {
			BankAccount another = (BankAccount) obj;
			if (this.accountCode.equals(another.accountCode)) {
				result = true;
				}
			}
			return result;
		}
	}
```
In order for several utilities involved with hashing in the standard Java libraries to work correctly, the equals and hashCode must be compatible.
Invoking the hashCode methods of two objects that are considered equal should produce the same hash value, so whenever equals is overridden within a class, method hashCode must be overridden in a way which is compatible.

Classes derived from Object often override the definition inherited for hashCode to provide their own version. For example, String and integer classes define their own hashCode methods.
![[{418CD7B1-76D6-4495-9E61-32A3893A764F}.png]]
These more specific hashCode functions are more effective.

### "Redefining the method hashCode: an Example"
In Java, the primitive type int is a 32-bit numeric value, so it ranges between -2,147,483,648 and 2,147,483,648.
We can redefine the hashCode method for class "Student" using the student identification number of a Student object. In Aston University, a student ID number is a string made up of 9 digits.
To give it a hashCode, using the student ID we can perform conversion from String to int using the static method parseInt in the wrapper class Integer.
```java
public class Student {
	private String id;
	private String surname;
	private String firstname;
	
	public int hashCode() {
		try {
			return Integer.parseInt(id);
			}
			catch (NumberFormatException e) {
				System.out.println("The student ID " + id + " is not parsable.");
				}
		}
	}
```
But, this approach could lead to an exception being thrown!
Another way to implement this is to return the hash code of the String object sun.
```java
public class Student {
	private String id;
	private String surname;
	private String firstname;
	
	public int hashCode() {
		return id.hashCode();
	}
}
```
It's hard to construct a good hash function from scratch, we as laymen should use hashCode methods from the standard Java types like above.

### "Use of Hashing in the JCF"
The Java Collections Framework has seven classes which use hashing in their implementation.
- Hashtable<K, V>
Stores key-value pairs as non-null objects, using hashCode() and equals().
It needs an initial capacity and a load factor. It handles collisions by just storing those keys in the same cell, searches are done one by one.
We shouldn't use Hashtable.
- HashMap<K, V>
Stores key-value pairs using a hash table, allowing for null keys and values.
It's not synchronised and has no guaranteed order.
It's very fast for get() and put() operations being O(1).
Iteration speed depends on capacity and size.
- ConcurrentHashMap<K, V>
Thread-safe/synchronised so multiple threads can use it at the same time!
Fast for reading and writing, does not allow null keys or values.
Better than Hashtable for multi-threaded programs.
- IdentityHashMap<K, V>
Special-purpose, compares keys using == instead of equals.
Two keys are equal only if they're the exact same object in memory.
Only use when you need to check if keys are the same object!
- HashSet\<V>
Implements the Set interface, uses a hash table internally for fast operations.
Constant-time performance for add(), remove(), contains() and size().
Works best when elements are evenly distributed across cells.
No guaranteed order of elements.
- LinkedHashSet\<V>
Like HashSet, but remembers insertion order. Uses both a hash table and doubly-linked list (where each element has two pointers to the next and previous element). Elements are linked in the order they are added.
Slightly slower than HashSet but maintains predictable order.
- LinkedHashMap<K, V>
Like HashMap, but remembers insertion order.
Uses both hash table and doubly-linked list. When iterated, entries come out in the order they were added.
Slightly slower than HashSet but maintains predictable order.
![[{4DD1F4F1-203F-4866-BDE5-0E33AFA7B658}.png]]
LinkedHashMap<K,V> maintains predictable insertion order (unlike HashMap's chaotic ordering) and is cheaper than TreeMap, making it ideal for copying maps while preserving order or returning results in the same order they were input. 
It has the same constant-time speed as HashMap for basic operations but is slightly slower due to maintaining a linked list, however iteration is actually faster because it only depends on the number of entries, not capacity (unlike HashMap which depends on both). 
Setting capacity too high is less harmful than with HashMap since iteration speed isn't affected by capacity. 
The diagram shows LinkedHashSet uses both a doubly-linked list to maintain insertion order and a hash table for fast lookups - each element exists in both structures simultaneously.
- WeakHashMap<K, V>
Hash table-based map with weak keys. Entries are automatically removed when their keys are no longer used elsewhere in the program.
Garbage collector can delete keys at any time.
Primarily for keys compared using \==.
Because the garbage collector can remove entries unpredictably, the map acts as if an invisible thread is deleting things silently i.e., size() decreasing over time, isEmpty() returning false and then true later, containsKey() might return true then false for the same key, get() could return a value and then null for the same key, put() could return null for a key previously in the map, remove() might return false for a key that seemed to exist, also iterating through the map multiple times causing fewer elements to yield each time.