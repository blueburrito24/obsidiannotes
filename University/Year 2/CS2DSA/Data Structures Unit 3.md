Note that [[Data Structures Unit 1]] was made purely from my own notes, whereas this [[Data Structures Unit 2]] and this Unit 3 has been made with assistance from claude.ai to summarise chapters.
## Abstract Data TYPES (adtS)
An #ADT is a mathematical specification of set of data and the operations that can be performed on that set of data. This data set is *abstract* in that the focus is the properties of the data and behaviour of the operations, the actual structure of the data(e.g., array, linked list) is not specified nor the implementations of the operations (e.g., iteration) acting on the set of data.
With an ADT we know the logical structure of the data type (linear, hierarchically, ordered or unordered etc) and what we can do with it.
An example of ADT can be a string, list, stack, queue, set, map, tree or even a rational number (like a fraction or something).
ADTs can be implemented in many ways such as a stack being implemented using an array or linked list.

A collection is an object that hosts a group of objects, usually a fixed type. These objects can be organised in different ways depending on the collection type.
Collections are categorized as:
- Unordered: No logical order between elements
- Linear: Elements arranged in a straight line (each followed by a unique next element)
- Nonlinear: Elements arranged hierarchically or in a network
![[{4409FA93-EED8-438F-9443-2CCA035D7134}.png | 600]]
These objects are usually ordered by the order they were added (like a queue) or by their relationships (like alphabetical order).
Internal storage structure doesn't have to match logical structure, a list can appear logically linear but be stored in a binary search tree for faster searching.

Collections can also be catorigsed as :
- #Bounded - there is a limit to the number of elements that the collection can contain (size/capacity) such as arrays.
- #Unbounded - there is no limit on the size of the collection beyond machine memory such as ArrayList
All collections should provide the methods ==isEmpty()== to check if its empty and ==size()== to check its element count.
Bounded collections specifically need ==isFull()== to check if the collection has reached the maximum capacity and ==capacity()== to check the maximum possible size.

A collection is an abstraction in the sense that it separates interface from implementation (what client classes can do, how it works internally). Java interfaces define these operations.
This makes the collection flexible - you can swap implementations without affecting the client code e.g., replacing ArrayList with a LinkedList without changing any code in the collection. We obtain this benefit because the Iterator interface handles all these operations itself whereas we don't have to indulge on how the Iterator works with an ArrayList vs. a LinkedList.
![[{0C948C64-E00D-451B-8FD7-2E75B0A53D41}.png | 600]]
Collections are useful in that any computer software will 