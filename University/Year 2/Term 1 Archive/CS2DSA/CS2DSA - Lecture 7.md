---
tags:
  - "#LinkedStructures"
  - "#LinkedList"
  - "#Queue"
  - "#FIFO"
  - "#BigO"
  - "#JavaCollectionFramework"
aliases:
  - L7
  - DSA7
image: https://images.unsplash.com/photo-1485470733090-0aae1788d5af?ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxzZWFyY2h8M3x8d2FsbHBhcGVyJTIwNGt8ZW58MHx8MHx8fDA%3D&fm=jpg&q=60&w=3000
description: CS2DSA
Previous: "[[CS2DSA - Lecture 6|Lecture 6]]"
Next: "[[CS2DSA - Lecture 8|Lecture 8]]"
---
# Objectives
- Examine an efficient array-based implementation of QueueADT
- Consider Priority Queues#
- Examine a linked-list implementation of a priority queue
- Examine a implementation of a priority queue based on a array of FIFO queues

# Alternative Array Implementation of `QueueADT` to `CircularArrayQueue`
In previous iterations of queue ADT, regardless of array-based or linked structure, they all suffered from having the time complexity of dequeue of being O(n)
- All elements needed to shifted one place down to fill the gap left by removing element from the front while other operations were constant time 
This can be possible by removing the need of shifting elements after dequeue operations 

- A circular queue is a implementation of a queue which uses a array that wraps around itself
	- The last index is followed by index 0
![[CS2DSA_W7_FIGURE1]]

- A circular array is a ring but it's a normal linear array, the difference is how the array is processed 
- Arrays are linear sequence of cells where Index 0 is the first cell and n - 1 is the last sell where n is the length of the array however for a circular index, they still exist but it's not viewed as 0 nor n -1 (as being the first and last cells)
- All array cells are *pretended* to be arranged in a circle which is why there is no *last* or *first* cell 

---
*Figure 3* shows a circular queue which has been implemented as a array. The front of the queue is at index 0 while the rear is at index 8

![[CS2DSA_W7_FIGURE3|700x300]]

*Figure 4* is after 4 dequeue operations where the elements A,B,C,D are removed from the queue
![[CS2DSA_W7_FIGURE4|700x300]]
To add more elements to this queue, these elements will be stored in the array cells from index 8 but this array only has 10 cells which means that after 2 elements the linear array is full. However for a circular array, after index 9 what logically follows is index 0, this means that the remaining 2 elements can be stored at indices at 0 and 1 (which aren't occupied)
So when a element in enqueued, the value of rear is increased but it must loop back to 0 when the linear array has been filled, so this statement:
```Java
rear = (rear+1) % queue.length;
```
Utilises the *modulo* operator to find the remainder of the expression #Modulo 

*Figure 5* shows the final positions of the elements where the elements have been loop
![[CS2DSA_W7_FIGURE5|700x300]]

If the new rear position is the same as the length of the array, return 0
```Java
public void enqueue (T element) {
	if (count == queue.length)
		expandCapacity();
	queue[rear] = element;
	
	rear = (rear+1) % queue.length;
	
	count++;
}
```

- The reason why `expandCapacity` is required is the array (due to being bounded) can become full and requires enlarging
```Java
private void expandCapacity() {
	T[] larger = (T[]) (new Object[queue.length *2]);
	
	for (int scan = 0; scan < count; scan++) {
		larger[scan] = queue[front];
		front = (front+1) % queue.length; // required for loop back	
	}
	front = 0;
	rear = count;
	queue = larger
}
```

- When elements are copied to a bigger array, they are set to the front of the queue (where front is now index 0 again)
- Dequeuing a element means to go to the `front` or whose index is the value of `front`, assign that to `null` and then increment `front` while decrementing `count` will complete the dequeue operations.
	-  `null` is not required but its better for the garbage collector #Null 
```java
public T dequeue() {
	if (isEmpty()) {
		throew new IllegalStateException("Queue empty in dequeue");	
	}
	
	T result = queue[front]; //saves current element at front to result
	queue[front] = null; // deletes element at front (but saved in result)
	front = (front+1) % queue.length; // wraps around 
	count--; // decrease items in queue
	return result; // give back the saved result
}
```

# Time Complexity of the Circular Array Queue Implementation 
#timeComplexity #CircularArrayQueue #Array #Queue 
The time complexity for all operations for a circular array is constant O(1), `enqueue` is O(1) but worst case maybe O(n) when the array needs to be expanded (and copied). 
For a bounded implemented of a circular array, all operations are O(1) whereas linear array-based implementation of dequeue is O(n) and other operations are constant time. Enqueue fails when the array is full #BigO #Linear #Array #Bounded 

# Some Uses of Queues 
#Multi-Threading #Queue 
1. Queues are used in multi-threaded, data for processing produced by producer threads and then using a queue it's deposited where they are retrieved later by consumer threads and processed. This means that producers and consumer threads are separate, this means:
	1. If producers are producing data faster than it can be consumed, the producers don't have to wait they can just add the data to the queue 
	2. Consumers may consume data faster than it can be produced but there is no delays as they can retrieve data from backlog in the queue
2. Queues are used to simulate model real-life queueing situations such as queues at a ticket booth.
	1. Another example might a traffic simulation, where vehicles at a traffic stop can be modelled by a queue data structure 
		1. A pure queue might be insufficient as vehicles leave the queue by joining traffic at opposite directions 

## Ticket Counter Simulation 
- A queue can be used to simulate a waiting line for a ticket booth
---
Here is the scenario:
1. The manager wants to find out how many cashiers are needed to maintain a level of service, they want to employ as little cashiers as possible but want a good service 
2. The simulation will be used to determine how many cashiers are needed to keep the time below 7 minutes 
- We assume that :
	- Customer arrives at every 15 seconds 
	- 2 minutes is taken to process a request 
3. As to be realistic, the simulation should factor in that a cashier might not have anybody to serve as customer is waiting in the queue 
4. The simulation can be done in a brute force/trial-and-error manner. The simulation can be ran using 1 cashier, then 2, then 3, then 4, until perhaps 10. The result from each simulation can be compared and then a result can be determined 

2 classes are used to model this simulation, `Customer`and `TicketCounter` along with a `LinkedQueue` to model the state of the customer queue, here is the UML Class: a

![[CS2DSA_W7_FIGURE7|800x200]]

### Class `Customer`
This is a class that simulates the customer behaviour, it keeps track of arrival time and departure time 
```Java
package ticketCounter;

public class Customer {
	private int arrivalTime; // when the customer comes at the counter
	
	private int departureTime; // when the customer leaves
	
	public Customer (int arrives) {
		arrivalTime = arrives;
		departuretime = 0; // We don't know when they're going to leave	
	}
	
	// return the arrival time of customer
	public int getArrivalTime() {
		return arrivalTime;	
	}
	// Set the departure time 
	public void setDepartureTime (int departs) {
		departureTime = departs;	
	}
	// return the departure time 
	public int getDepartureTime() {
		return departureTime;	
	}
	// compute the total time for this customer
	public int totalTime() {
		return departureTime - arrivalTime;	
	}
}
```

### Class `TicketCounter`
The actual simulation is modelled using `TicketCounter` class 

