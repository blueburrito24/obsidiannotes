Note that [[Data Structures Unit 1]] was made purely from my own notes, whereas this [[Data Structures Unit 2]], [[Data Structures Unit 3]] and this Unit 4 has been made with assistance from claude.ai to summarise chapters.

## Working with Arrays
We can define arrays using primitive types like int or double, or user-authored classes, using the following form:
```java
int[] a;
a = new int[10];

double[] b = new double[20];

int[] c = {5, 2, 1, 4};
```
Line 1 declares a variable "a" that can hold a #Reference to an array object, type int.
Line 2 allocates storage for an array object size 10 (0-9) which can be accessed using the notation "a[1], ..., a[9]".
![[{D3091C7E-2AE5-4C35-B865-12C27409FD70}.png]]
Array elements are initialised to a zero-bit pattern, so an int array's elements are all initialised to 0 and arrays of reference types they are null. Boolean arrays initialise to false.
Line 4shows how we can declare an array variable and also allocate storage for it in a single declaration.

We can also allocate storage for an array object and initialise it using array aggregation. This can only be done when declaring new array variables however, not when re-initialising arrays that have already been created.
```java
double d = new double[4] = {1.0, 2.0, 3.0, 4.0};   // !!! ERROR
```
The number of elements in an array can be accessed through the final field "length" of the array. Typically this is used in a loop to process each array element.
```java
for (int i = 0; i < a.length; i++) {
	a[i] += 2; // add 2 to each element of array a
	}
```
Enhanced for loops are often more convenient.
```java
for (double elem : b) {
	elem  -elem; // change the sign of each element for array b
	}
```
## Time Complexity of Array Operations
Accessing array elements is fast, O(1), as it involves calculating the address of the array element and then accessing the data of that address. Processing a 1-D array of size n will involve a loop being executed n times. If one element is O(1), the entire process is O(n).
```java
// increase the salary of each grade point by 1%
for (int 1 = 0; i < salaries.length; i++) {
	salaries[i] += salaries [i] * 0.01;*
	}
```
If a company increases all salaries by 1% then each element of the array needs have that increase applied. The operation in line 4 does not depend on the size of the array, so it executes at O(1). Completing the salary increase process is dependent on the array "salaries" size, so the loop is O(n) where n is the length of the array.

## A Bounded Stack Implementation
