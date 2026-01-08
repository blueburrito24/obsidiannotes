---
image: https://images.unsplash.com/photo-1485470733090-0aae1788d5af?ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxzZWFyY2h8M3x8d2FsbHBhcGVyJTIwNGt8ZW58MHx8MHx8fDA%3D&fm=jpg&q=60&w=3000
next: "[[CS2DSA - Lecture 5|Lecture 5]]"
previous: "[[CS2DSA - Lecture 3|Lecture 3]]"
aliases:
  - L4
tags:
  - CS2DSA
  - BigO
  - ADT
  - Array
  - Bounded
  - Unbounded
  - Stack
  - Queue
  - AbstractDataTypes
  - Set
---
# Objectives 
- Revise Array Concepts 
- Use an array to implement a bounded stack ADT
- Use an array to implement an unbounded stack ADT
- Use an array to implement a queue ADT
- Examine an array implementation of the bounded set ADT
- Examine the time implications of the above using Big-O notation 

# Working with Arrays
Arrays can be defined as such, regardless primitive and user-defined classes
```Java
intp[] a; // declares a that can hold type of int

a = new int[10]; // size of 10 is allocated, they can be accessed a[0], a[1]

double[] b = new double[20];

int[] c = {5, 2, 1, 4};
```

Arrays are initialised in a "zero bit pattern" #ZeroBitPattern 
- for `int` it's 0
- for reference type it's `null` 
- for `boolean` all elements are false 


Array aggregates can only be used when the array is being declared, it cannot be done after they have been created (re-initialise). This would be illegal and would fail to compile:
```Java
double d = new double[4] = {1.0, 2.0, 3.0, 4.0};
```


Elements in a array can be accessed using length of the array 
```Java
for (int i = 0; i < a.length; i++) {
	a[i] += 2; // add 2 to each element of the array
}
```

but it is better to used a enhanced for #enhancedFor 
```Java
for (double elem : b) {
	elem = -elem; // change the sign of each element
}
```

# Time Complexity of Array Operations
#timeComplexity #Array 
Accessing array elements are fast as it involves:
1. calculating the address of the array element which is done in constant time O(1)
2. then accessing the data at the address 

To process a 1-D array of size *n* will involve a loop being executed *n* times, if the time complexity of processing one element in O(1) then the whole process will have the time complexity of O(n)

This *for* statement goes through every element in the array *salaries* which stores the salaries for each employee. If the company decided to increase the salaries by 1%, each element in the array must be operated on to apply a 1% increase

```Java
for (int i = 0; i < salaries.length; i++) {
	salaries[i] += salaries[i] * 0.01;
}
```

The line `salaries[i] += salaries[i] * 0.0.1;` executes at constant time O(1) as it's not dependant on the size of the array but to apply this line to the whole loop (and every element in the array to increase the salary by 1%) it is dependant on the size of the array so this means the loop executes in linear time O(n) where *n* is the length of the array 

# Bounded Stack implementation
#Bounded 
![[CS2DSA_W4_BOUNDEDSTACK]]

An array-based implementation of BoundedStackADT, this is the simplest collection ADTs as its easy to implement. As this is bounded #Bounded it will have a fixed size for it's lifetime once storage has been allocated
- The stack grows upward from the start of the array due to the items that are pushed onto it and shrinks back down as items are popped off
- An `int` variable is required to keep track of the position 
- a method `clear()` is required to empty the stack

## Example implementation of a BoundedStackADT

```Java
// implementation of a BoundedStackADT

public class ArrayStack<T> implements BoundedStackADT<T> {
	private static final int DEFAULT_CAPACITY = 100;
	
	private T[] elems; // array to hold the stack elements 
	private final int maxSize; // maximum capacity of the stack
	private int currentSize; // current size 
	
	// Construct a new empty stack with specified capacity	
	@SuppressWarnings("unchecked")
	public ArrayStack (int maxSize) {
		elems = (T[]) (new Object[maxSize]);
		currentSize = 0;
		this.maxSize = maxSize;	
	}
	
	// Construct a new empty stack with default capacity
	public ArrayStack() {
		this(DEFAULT_CAPACITY); // calls the one argument constructor above	
	}
	
	@Override
	public int size() {
		return currentSize;	
	}
	
	@Override
	public boolean isEmpty() {
		return (currentSize == 0);	
	}
	
	@Override
	public boolean isFull() {
		return (currentSize == maxSize);	
	}
	
	@Override
	public void push(T element) {
		// check if the stack is full
		if (currentSize == maxSize) {
			throw new IllegalStateException("Stack full in method push");	
		}
		// add the element at the top of the stack
		elems[currentSize] = element;
		
		// increase the size by 1
		currentSize++;

	}
	
	@Override
	public T pop() {
		// check if stack is empty
		if (currentSize == 0) {
			throw new IllegalStateException("Stack empty in method pop");	
		}	
		
		// decrease the size of the stack by 1
		currentSize--;
		
		// return the element on the top of the stack	
		return elems[currentSize];
	}
	
	@Override
	public T peek() {
		// check if stack is empty 
		if (currentSize == 0) {
			throw new IllegalStateException("Stack empty in method peek");
				
		}
		// return the element at the top of the stack
		// the index of the top element in one less than currentSize 
		return elems[currentSize - 1];
	}
	
	public void clear() {
		currentSize = 0;	
	}
}
```

- Two constructors are provided
	- First constructor allocated a stack that can specific a capacity using `maxSize` 
	- Second constructor allocates a empty stack with default capacity (100 in this case) 
- Java doesn't allow creation of arrays using a generic type #Generic which is why a array of `Object` type must be created and then casted to a type. This refers to the lines:
```Java
	private T[] elems; // array to hold the stack elements 
	private final int maxSize; // maximum capacity of the stack
	private int currentSize; // current size 
	
	// Construct a new empty stack with specified capacity	
	@SuppressWarnings("unchecked")
	public ArrayStack (int maxSize) {
		elems = (T[]) (new Object[maxSize]);
		currentSize = 0;
		this.maxSize = maxSize;	
	}
```
- Here is what's happening:
	- `new Object[maxSize]` - This creates the array, as it's "Object" type #Object it will hold Objects. `maxSize` is "100" so it will create `Object[100]` 
	- `(T[])` - This is the type-cast #typeCasting. It tells the complier something like this:
		- I made a `Object[]` but I will only ever put `T` items in it so treat it as if it were `T[]` 
	- `elems = ....` - This assigns the new array which is a `Object[]` pretending to be `T[]`
- So in the end, `Object[]` is being casted to `T[]` and not the other way around 
- Why is it done this way?
	- The "ideal" code in Java #Java  is illegal, where writing something like this `elems = new T[maxSize]` isn't possible due of something called *Type Erasure* #TypeErasure
	- #### Type Erasure
		- In compile time - Java is aware of what `T` is where `ArrayStack<String>` it will know `T` is `String` #String 
		- Run Time - Java erases `T` and is left with `Object` The JVM doesn't know what `T` is #JavaVirtualMachine
		- As Java doesn't know what `T` is at runtime, it won't create a new array of type `T` and doesn't know what to make and this is why `Object[]` is used as it's "safe" during both compile and run-time #Compile #Run-Time and it can hold anything 
		- Mismatch - then happens as `elems` is `T[]` but the array is `Object[]` 
		- Ugly Cast - You force assignment using `(T[])` which is ugly and generates a unchecked warning which is why `@SuppressWarnings("unchecked")` is added to tell the complier it's fine. #UglyCast #typeCasting 

There is another more reliable way to do this by using the `static` method of `newInstance` #Static #newInstance which can be found in `java.lang.reflect.Array` 

The code is as follows:
```Java
import java.lang.reflect.Array;

// Construct empty stack with specified capacity
@SuppressWarnings("unchecked")
public ArrayStack (int maxSize) {
	// another way to create generic array rather than type casting object
	elems = (T[]) Array.newInstance(Object.class, maxSize);
	currentSize = 0;
	this.maxSize = maxSize;
}
```

The line `elems = (T[]) Array.newInstance(Object.class, maxSize);` is identical to `elems = (T[]) (new Object[maxSize]);`

`ArrayStack` inherits `BoundedStackADT` which is a sub-interface of `Bounded` and `QueueADT` and it has 7 methods that are inherited. Each of those 7 methods have been overridden using Override and it should not be treated as new methods #Override 

- `push()` method - check if stack is full (throw exception if so) or store element at the top of stack, increase size of stack by one 
- `pop()` method - check if stack is empty (throw exception if so) or decrease the size of stack by one, return items at the top of the stack (old top before `pop`) 
- `peek()`  method - check if stack is empty (throw exception if so) or return the item at the top of stack (don't remove it)
- `clear()` method - `currentSize()` is set to 0

Looking at every method in `ArrayStack` it is evident that none of them contain a looping method and such will execute in Constant Time of O(1) 


# Implementing an Unbounded Stack using Array
#Array #Unbounded #Stack 
Arrays are static which means they're not a good choice for making unbounded collections however it is still possible to store the content in a array, this can be done by increasing the underlying array capacity as the stack grows in size hence automatically expanding the storage capacity 

*expand the storage capacity* - this simply means creating a larger array and then copying existing elements to the new array, here's the code:

```Java
private void expandCapacity() {
	T[] larger = (T[]) (new Object[contents.length*2]);
	
	// copy the elements from the old array to new one, one by one 
	for (int index=0; index < contents.length; index++) {
		larger[index] = contents[index];	
	}
	
	contents = larger;
}
```

at each `push` operation, before an element in added to the stack, the capacity is checked and if it's full, then a method called `expandCapacity()` is called before that element is pushed into the stack. There is no need to throw a IllegalStateException during the push operation 
```Java
public void push(T element) {
	if (size() == contents.length) {
		expandCapacity();	
	}
	
	contents[currentSize = element];
	
	currentSize++;
}
```

When the element is added to the stack, it may need to trigger the expansion of the capacity which means the time complexity is O(n) but it may not be used frequently such as if the underlying array has been selected not to expand in capacity during it's lifetime, it instead be O(1) constant

# Bounded Queue Implementation
#Bounded #Queue 
For the contents of a queue, it can be managed using an array where index at 0 represents one end.
A `int` variable `rear` can be defined to represents the next available slot in the array (where a cell is not used for object reference) and the number of elements in the queue #Integer 
```Java
public class ArrayQueue<T> implements QueueADT<T> {
	private static final int DEFAULT_CAPACITY = 100;
	private int rear;
	private T[] queue;
}
```

- An empty queue means that no element is in the array, rear is 0. An array of certain size needs to be created for enqueue and dequeue #Array #Enqueue #Dequeue 
```Java
public ArrayQueue (int initialCapacity) {
	rear = 0;
	queue = (T[]) (new Object[initialCapacity])
}  
  ```

- The size of the queue is kept in the variable `rear` so the time complexity for `size` is O(1) constant. The queue is empty if the size if 0 so `isEmpty` is also O(1) #timeComplexity 
- To enqueue a element to the rear of a queue, the value of rear needs to be updated 
```Java
public void enqueue (T element) {
	if (size() == queue.length)
		throw new IllegalStateException("Queue full in Enqueue");
	
	queue[rear] = element;
	
	rear++;
}
```
due to no loop being used, the time complexity is O(1)

- To dequeue is to remove the cell at index 0 but `null` cannot be assigned as this is the one end of the queue and no gaps are allowed so all other elements need to be shifted. #Null
```Java
public T dequeue() {
	if (isEmpty())
		throw new IllegalStateException("Queue empty in dequeue");
		
	T result = queue[0];
	rear--
	// Shift elements
	for (int scan = 0; scan < rear; scan++) {
		queue[scan] = queue[scan+1];	
	}
	
	queue[rear] = null;
	return result;
}
```

 - Every dequeue operation requires shifting the elements in the queue, this would mean the time complexity is O(n)
 - Queues operate on both ends, so the elements must be shifted to keep one end at index 0 this means the implementation is Inefficient where O(1) would be considered efficient 

# Implementing an Unbounded Queue using Array
This is done just like `ArrayStack` where instead of throwing a IllegalStateException when the array is full, invoked expandCapacity instead 

# An Abstract Set Class
#Abstract #Set #Class 
A abstract set class will be used to simply the implementation of ArraySet #ArraySet #SetADT 

- `setADT` extends `Iterable` #Iterable which means that AbstractSet will have the method `Iterator` #Iterator and because it's *abstract* it doesn't have to have a implementation for the method of Iterator as the sub-classes will be responsible for that #Subclass 

- `addAll` - add to the elements of set A one by one as it's iterated over 
- `removeAll` - similar way `remove` can be implemented 
- `contains` - iterate over current set to see if every element of this set is a member of set A this means `isSubset` can be implemented. 
	- Just like addAll and removeAll, contains is independen of the details of how it's implemented 
- `equal` - implemented via `isSubset`. This is done by using the result that two sets A and B are equal if: 
$$
A \subseteq B \space\text{and} \space B \subseteq A
$$

- This technique of using abstract classes to simply ADT interfaces is used a lot in the Java Collection Framework (JCF) #JavaCollectionFramework

![[CS2DSA_W4_FIGURE4]]

```Java
public abstract class AbstractSet<T> implements SetADT<T> {
	public boolean addAll (SetADT<T> A) {
		boolean hasBeenModified = false;
		// Apply add to the elements of set A
		for (T element : A) {
			if(this.add(elementll)) {
				hasBeenModified = true;	
			}	
		}	
		return hasBeenModified;	
	}
	
	public boolean removeAll(SetADT<T> A) {
		boolean hasBeenModified = false;
		// remove the elements of set A one by one 
		Iterator<T> iter = A.iterator();
		while (iter.hasNext()) {
			if(this.remove(iter.next())) {
				hasBeenModified = true;	
			}	
		}
		return hasBeenModified	
	}

	public boolean retainAll(SetADT<T> A) {
		boolean hasBeenModified = false;
		Iterator<T> iter = this.iterator();
		while (iter.hasNext()) {
			T elem = iter.next();
			if (!A.contains(elem)) {
				// current element doesn't appear in set A
				hasBeenModified = this.remove(elem);	
			}	
		}
		return hasBeenModified;	
	}
	
	public boolean isSubset(SetADT<T> A) {
		if(this.size() > A.size()) {
			// as it has more elements than A, it can't be subset
			return false;	
		}
		
		// check through each element to see if elements are NOT a member of set A 	
		for(T element : this) {
			if(!A.contains(element)) {
				return false // member in this set thats not in set A	
			}	
		}
		
		return true;
			
	}
	
	public boolean equals(SetADT<T> A) {
		if(this.size() != A.size) {
			return false;	
		}
		
		return isSubset(A) && A.isSubset(this);	
	}
}
```

- `addAll` - enhanced for loop is used to iterate through elements and add them one by one to the current set #enhancedFor #For 
	- If only only 1 element of A was added to this set then it must affect `hasBeenModified` and then return the final value of this boolean variable #Boolean 
- `retainAll` - Check if each element of current set (this) is in set A. if not we remove it from this set and set boolean variable to true 
- `isSubset` - `this` current set is iterated over and not set A using a enhanced for, if any element of `this` is *not* in set A, false is return immediately and would be Inefficient to continue looping (as it would not be a subset)
	- size will execute in constant time so we can check if `this` set is larger than the size of *A*. If it is then `this` set cannot a subset of A
- `equals`  - check if both sets are equals, if both sets have different sizes they are *not* equal
# Bounded Set Implementation
#Bounded #Set
- Just like with BoundedStackADT, it will have 4 methods (`isEmpty, isFull, size, capacity`) and 2 constructors 
- When implementing methods such as union, intersection, difference, these methods should be written via public methods defined in SetADT and it's forbidden to peek inside parameter *A* and should be treated as a ArraySet 
	- This is so that the union, intersection, difference methods (or any method in general) is flexible and not limited to the implementation of a specific type of set is passed as A (could be ArraySet or LinkedSet #LinkedSet, makes no difference)

- There are ways to implement a more efficient set operations such as `union` or `isSubset`  by assuming that both sets are the same concrete class (XSet, where *X* is array, linear linked, tree, hash etc). This would allow for method overloading #MethodOverloading 
- `XSet<T> union(XSet<T> A)` - This requires  the argument set *A* to be the same concrete class as the calling set (*XSet* in this case) 
	- This means that return type will that specific concrete class, this means the caller will know what object they get back 
	- As the programmers knowns that both are of the same concrete class, this can lead to development of a highly efficient algorithm
	- This allows the compiler select the most type-specific method at compile time #Compile 

## Class `ArraySet` 
```Java
import java.util.Iterator;

public class ArraySet<T> extends AbstractSet<T> implements Bounded {
	private static final int DEFAULT_CAPACITY = 100;
	
	private T[] contents;
	private final int maxSize;
	private int currentSize;
	
	public ArraySet (int maxSize) {
		contents = (T[]) (new Object[maxSize]);
		currentSize = 0;
		this.maxSize = maxSize;	
	}
	
	public ArraySet() {
		this(DEFAULT_CAPACITY);
	}
	
	public int size() {
		return currentSize;	
	}
	
	public boolean isEmpty() {
		return (currentSize == 0);	
	}
	
	public int capacity() {
		return maxSize;	
	}
	
	public boolean isFull() {
		return (currentSize == maxSize);	
	}
	
	public boolean contains(T element) {
		for (int i = 0; i < currentSize; i++) {
			if (element.equals(contents[i]))
				return true;	
		}
		return false;
	}
	
	public boolean add(T element) {
		if (!contains(element)) {
			if (!isFull()) {
				contents[currentSize] = element;	
				currentSize++;
				return true;
			} else {
				throw new IllegalStateException("Set full in method add");
			}
		} else {
			return false;	
		}
	}
	
	public boolean remove(T element) {
		for (int i = 0; i < currentSize; i++) {
			if (element.equals(contents[i])) {
				currentSize--;
				contents[i] = contents[currentSize];
				return true;	
			}	
		}
		return false;	
	}
	
	// other set operations (union)
	
	public Iterator<T> iterator() {
		return new ArrayIterator<T>(contents, currentSize);	
	}
}
```

- `contains` - Searches the array to see if the element is present in the set, if so returns true as soon as the element is found and if it fails, it returns false
	- enhanced for loop is not used as it would search the whole array whereas we want to search only a portion of the array up to index `currentSize` 
	- Iterators also require `Iterator` object which would slow down the operation
	- Elements can be access directly using array indexes. #Array 
- `add` - first check to see if the element is already present in the set using `contains` if it is then return false (leave the set unmodified) 
	- If it's not present, add the element to the end of the array (same as `push` from BoundedStackADT) 
	- returns true if indicate modification
- `remove` - first check the array to see if element is present
	- if it's not then leave the set unmodified, return false
	- if it finds the element at index *i*, decrease the size of the set by one, overwrite element at index *i* with the last element at index *currentSize*
		- This removes the element without leaving a "gap" in the array.
		- This works because elements in a set #Set  are unordered #Unordered so there is no need to shift elements unlike a queue #Queue 
- `intersection` - This creates a new empty set so that it can hold the result set. 
	- It goes through the set checking every element is a member of set *A*
		- If so, adds it to the result set #Intersection 
- Using `add` to add the result set would make a unnecessary call to `contains` 
	- Instead the element is *NOT* in the result set and can be added to the end 
# Array Iterator 
#Array #Iterator #Iterable 
To complete the `ArraySet` a `iterator()` method is required as it implements `java.util.Iterable` 
- An iterator is a object that use each element of a collection in turn, going through them one by one 
- Implementation is determined by the order of the elements 
- Sets have no logical order, hence iterator can return elements randomly 
	- However for efficiency, iterator will deliver the elements in the order they are stored in the underlying array
- `Iterable` interface is found in `java.lang` #Iterable 
- `Iterator` interface is found in `java.util`
- `iterator()` method returns a Iterator object

Since Java 8, `Iterator` has the methods:
1. `hasNext` - returns true if there are elements in the iteration
2. `next` - returns the next element in the iteration
3. `default remove` - remove the current element of the collection, `default` throws an exception (UnsupportedOperationException)
4. `default forEachRemaining` - Performs a action for each remaining element until all elements have been processed or exception has been thrown

This implementation of `iterator` is a new class called `ArrayIterator` so that it can be used for other array-based collections 
```Java
import java.util.Iterator;

public class ArrayIterator<T> implements Iterator<T> {
	private T[] contents;
	private int cursor;
	private int limit;
	
	public ArrayIterator(T[] array, int size) {
		contents = array;
		limit = size;
		cursor = 0;	
	}
	
	public boolean hasNext() {
		return cursor < limit;	
	}
	
	public T next() {
		if (!hasNext()) {
			throw new IllegalStateException("ArrayIterator: no next element");	
		} else {
			return contents[cursor++];	
		}	
	}
	
	public void remove() {
		throw new UnsupportedOperationException("ArrayIterator: remove");	
	}
}
```

- Constructor takes 2 parameters #Parameters 
	- The array to be iterated over 
	- An `int` parameter `size` to indicate the portion of the array to iterate over
- `int` field `cursor` keeps track of the next element (return by `next`) 
- Method `next` returns the element at the current value of cursor, increments `cursor` by one (for next element)
	- `return contents[cursor++]` - returns the value of where  `cursor` is in `contents` array and then increments `cursor` by one (move to the next position)
- `remove` - Not implemented, throws exception 
	- Since Java 8, `Iterator` has a default implementation of `remove` which also throws UnsupportedOperationException so it's not necessary to for `ArrayIterator`
- It's safe to *not* support `remove` within `ArrayIterator` as it's a public class and has no access to the collection, by allowing `ArrayIterator` to remove a element it would result into `size` being incorrect (different value to actual number of elements)

This now provides context for this line in `ArraySet`
```Java
public Iterator<T> iterator() {
	return new ArrayIterator<T>(elems, currentSize);
}
```

# Time Complexity of `ArraySet` Operations
#timeComplexity #ArraySet 
From the previous `ArraySet` Implementation we can find out the time complexity
- `contains` - Contains a *loop* #Loop if the size of the set is *n*, it's executed *n* times
	- Time complexity = O(*n*)
- `add` - It calls `contains` and then does a comparison to check for full `isFull` 
	- Time complexity = O(*n*)
- `remove` - Contains a loop, loop is executed *n* times 
	- Time complexity = O(*n*)
- `intersection` - When applied to another instance of `ArraySet` it's O(*n*^2) 
	- It contains a loop, executed *n* times where *n* is the size of current set
	- It then calls `contains` which also has a loop where the time complexity for that is O(n)
	- Time complexity = O(*n*^2) 


