---
next: "[[CS2DSA - Lecture 3|Lecture 2]]"
previous: "[[CS2DSA - Lecture 1|Lecture 1]]"
aliases:
  - CS2DSAL2
  - L2
  - DSAL2
  - L2DSA
tags:
image: https://images.unsplash.com/photo-1485470733090-0aae1788d5af?ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxzZWFyY2h8M3x8d2FsbHBhcGVyJTIwNGt8ZW58MHx8MHx8fDA%3D&fm=jpg&q=60&w=3000
---

# Unit Objectives
- Introduce the concept of algorithm analysis
- Introduce Big-O notation and tilde notation
- Use appropriate Big-O notation to describe the time complexity of an algorithm

# Motivation
- Analysis of algorithms provides a basis to compare the efficiency of algorithms
	- Which sorting algorithm is efficient?
	- Which data structure requires less memory?
	- Which collection ensures efficient access to its data elements?

# How to approach analysing an algorithm? #Algorithm #BigO #growthFunctions #timeComplexity #spaceComplexity 
- The resources of the algorithm must be determined (number of instructions + amount of storage) which are necessary to execute it
	- Most algorithms are designed to work with a arbitrary number of inputs
- The efficiency or complexity of a algorithm is stated as a mathematical function which relates the size of input to either:
	1. time complexity (the number of steps, number of instructions)
	2. space complexity (the size of storage space, amount of storage)
- which is used to execute the algorithm
- Growth functions can be used to fulfil the purpose of describe the time or space complexity and Big-O is used describe the efficiency of an algorithm

# Growth Functions #growthFunctions
- Analysis can be defined in general terms:
	- the problem size (the number of items that need to be sorted)
	- a key operation (comparison of 2 values, comparison of 3 values)
		- Swapping 2 values compared to comparing 2 values is a more complex operation, if so to determine the efficiency of a algorithm it would be import to consider the time taken to swap 2 values
		- This is only true if swapping the values at each step, if the values are in order than no swapping needs to be done but comparison of values would always need to be done so it is the key operation
- The problem size is expressed in terms the amount of data to be processed
- A growth function provides the relationship between the size of problem (*n*) and the time T*n* or the storage size S(*n*) to solve the problem:
$$
	T(n) = n^2 + 3n + 100
$$
when *n* is substituted with a expected amount of data, the time required to complete this task can be estimated via the growth function above 

$$
"\enspace A \enspace growth \enspace function \enspace shows \enspace time\enspace or \enspace space \enspace utilisation \enspace relative \enspace to \enspace problem \enspace size\enspace "
$$
Dishwashing Example:
1. Inefficient human dishwasher, every time a dish is washed the previous washed dishes and dried dishes are wet again
2. A complete washing cycle for each dish would include the time for washing and drying the current dish along with the time for drying all the previous washed dishes
3. If *each* dish takes 40 seconds and drying it takes 30 seconds, how long would washing *n* dishes require?
---
T(*n*) denotes the time required for washing *n* dishes:
$$
	T(n) = n \times \text{washing time} \space + \sum_{i=1}^{n} (i\times \text{drying time}) 

$$

$$
	= 40n + \sum{i=1}^{n}(30i)
$$
$$
= 40n + 30n(n+1) \div 2
$$
$$
= 15n^2 + 55n
$$
This means the growth function for this dish-washing algorithm is:
$$
T(n) = 15n^2 + 55n
$$
---

The simplest way to break down this function is:
1. Each dish takes 40 seconds to clean and 30 seconds to dry, along with the previously washed dishes
2. Time to wash the dishes is 
   $$
40n
$$
3. Time to dry the dishes is more complex as it's not constant
$$
\sum \space \text{simply means a summation or add up a series of terms}
$$
$$
		\sum_{i=1}^{} = \space \textbf{The Lower Limit} \space \text{This is the starting value, which would be} \space i=1
$$
$$
	\sum_{}^{n} \space \textbf{The Upper Limit} \space \text{This is the ending value.} \space i \space \text{is stopped} \space  \text{when it reaches} \space \text{n}
$$
$$
(30i) = \textbf{The Expression}: \space \text{This is the formula that each value of} \space i \space \text{is calcuated from start to the end}
$$
$$
(30i) \space \text{would mean}:
$$
$$
i=1: 30\times 1 =30
$$
$$
i=2: 30\times 2 =60
$$
$$
i=3: 30\times 3 =90
$$
$$
i=4: 30\times 4 =120
$$
$$
\textbf{Last time:} \space i=n: 30\times n =30n
$$
4. Simplification of the formula, 
	- we'd factor out the constant (30) which would give us
$$
T(n) = 40n + 30\left( \sum i=1ni \right)
$$
	- Using the summation shortcut which would be n(n+1) / 2, this would give us:
$$
\text{Shortcut:}i =1\sum ni=2n(n+1)
$$
$$
T(n) = 40n+30(2n(n+1))
$$
	- Algebra can be used to clean the expression
$$
T(n) = 40n + 15n(n+1)
$$
$$
T(n) = 40n + 15n^2 + 15n
$$
$$
\text{First}: (n + 1) \space \text{ should be distributed out,} \space \text{Second:} \space 15n \times n = 15^2, \text{Third: } \space 15 \times 1
$$
$$
15n^2 + 15n + 40n = 55n + 15n^2
$$


$$
T(n) = 15n^2 + 55n
$$
5. The most important part of this equation is:
$$
15n^2
$$
	- which means the equation has quadratic growth and as you double the dishes, the time quadruples, the Big-O notation for this would be
$$
\\\textbf{Big-O Notation: } = O(n^2)
$$
---
# Formulating a growth function from source code #growthFunctions 

- By using the dishwasher example, growth function can also be formulated for source code
- Execution time will vary between computers due to the range of CPUs and processing power available, however we can assume that each step within the program will take the same amount of time to complete
	- This means that execution time can be found by counting the steps it took to complete the tasks

```java
public void showLots() {
		for(Lot lot : lots) {
			System.out.println(lot);	
		}
}
```

- The line `System.out.println(lot);` will be ran depending on the size of `lots` 
- If there are 5 objects, it will run 5 times (to print out the 5 objects) whereas the line `for(Lot lot : lots)` will run regardless, even if `lots` is 0

---
- The growth function can be estimated as:
$$
T(n) \approx 2n + 1
$$
- This can be explained as such:
$$
2n = \text{Every time the for loop is ran},
$$
$$
\text{2 operations are done, accessing lot and printing},
$$
$$
n = \text{number of elements in lot}
$$
$$
\text{So it would be} \space 2 \times n = 2n
$$
$$
\text{As for the }1 \space \text{this is the intialisation of the for loop,}
$$
$$
\text{even if lots is empty, this is still ran to see the collection of lots}
$$
$$
\text{So the growth function is: } T(n) \approx 2n + 1
$$
---
# Growth Functions & the Asymptotic Complexity of an Algorithm #asymptoticComplexity #BigO #orderOfGrowth #dominantTerm #Logarithmic

- Knowing the exact growth function of a algorithm isn't necessary to see if its efficient, the key is the asymptotic complexity  or *how it grows as the problem size (n) increases*
	- This is found by the **dominant term** in the growth function
---
The dominant term would be the term that increase more quickly as *n* increases, for example in the growth function of:
$$
T(n) = 15n^2 + 55n
$$
The dominant term would be:
$$
15^2
$$
because the value increases faster than the other term 55*n* 

---
Asymptotic complexity is simply the order of the algorithm and this is specified using Big-O and the dish-washing example would have a complexity of:

$$
O(n^2)
$$
Binary Search runs in logarithmic [^1] time:
$$
O(\log n)
$$

---
One may ask:
*Whatever is multiplied by  n^2 is important when finding out the dominant term, especially if the constant is small such as:*
$$
\frac {1}{100000000}
$$
For small values such as this, *n* will be small and even when *n*^2 it is still the dominant term as *n* will grow which will eventually lead to *n* having the most influence in the algorithm's result

During the analysis of algorithm, problem size *n* must be accounted for as it could be a very large number or it could be infinite unless a limit is known 

To find the order of growth, the exact value computed from a growth function  doesn't need to be worked out. Just the dominant term, for example:

$$
T(n) = n(2n+3) 
$$
We only need to know that *n x 2n* to find the order of growth which will be:

$$
O(n^2)
$$
---
## Exercises on Identifying order of growth
$$
T(n) = n + 1 + n + 2
$$
$$
\text{Order of Growth} = O(n)
$$
$$
T(n) = 5(3n + 2)
$$
$$
\text{Order of Growth} = O(n)
$$
$$
T(n) = \frac{1}{2}n(4n + 2)
$$
$$
\text{Order of Growth} = O(n^2)
$$
$$
T(n) = 4 + 5 + 2
$$
$$
\text{Order of Growth} = O(1)
$$
$$
T(n) = \frac{(n+1)(n+2)}{2}
$$
$$
\text{Order of Growth} = O(n^2)
$$
$$
T(n) = n(n + 1)(2n + 1)
$$
$$
\text{Order of Growth} = O(n^3)
$$
$$
T(n) = n^2(n+3) + 4n + 15
$$
$$
\text{Order of Growth} = O(n^3)
$$

## Examples of common orders of functions
This is the relative order for Big-O functions, listed as from fastest to slowest (with O(1) being the most efficient):

$$
O(1) \prec O(\log n) \prec O(n) \prec O(n \log n) \prec O(n^2) \prec O(n^3) \prec O(2^n)
$$

| Notation          | Name        | Example                                                                   |
| ----------------- | ----------- | ------------------------------------------------------------------------- |
| $$ O(1) $$        | constant    | Determining if a number is even or odd                                    |
| $$ O(\log n) $$   | Logarithmic | Finding an item in a sorted list using binary search                      |
| $$ O(n) $$        | Linear      | Finding an item in a unsorted list                                        |
| $$ O(n \log n) $$ | Log-Linear  | Sort a list with quick sort                                               |
| $$ O(n^2) $$      | Quadratic   | Sorting a list with insertion sort                                        |
| $$ O(n^3) $$      | Cubic       | Finding the best sum of a sequence of numbers using brute force algorithm |
| $$ O(2^n) $$      | Exponential | Finding the exact solution to the travelling salesperson problem          |
# Asymptotic Analysis #asymptoticAnalysis
Asymptotic analysis is used to classify limiting behaviours within a algorithm by looking at trends, key point here is that asymptotic analysis is focused on purely the growth rate of the algorithm and **not** the speed (which is dependant on the machine resources).

Asymptotic analysis provides a way to test the scalability of a algorithm by focusing on the input size (*n*) and it's behaviour when it becomes increasingly large or even near infinite.

----
If we take a phone vs a supercomputer, and we run a algorithm on both of these devices and let us assume that the supercomputer is 1000x faster than the phone. This is a constant 1000x increase of performance regardless of what the size of *n*. This ratio is fixed.

The phone doesn't become 2000 times slower or the supercomputer doesn't become 2000x fastest depending on the size of *n* 

Asymptotic analysis provides a way which gives a universal standard on how an algorithm can be measured, not dependant on any platform by comparing how algorithms behave when the size of input *n* becomes large 

---
## Examples regarding 2 algorithms
$$
\mathbf{Algorithm \space 1:} \space T(n) = 100n + 500
$$
$$
\mathbf{Algorithm \space 2: } \space T(n) = n^2 + 1
$$
If we was to input a small number such as *10* we should see that *B* is faster (1500 vs 101 steps)
$$
\mathbf{A: \space} 100(10) + 500 = 1500 \mathbf{\space steps}
$$

$$
\mathbf{B: \space} 10^2 + 1 = 101 \space \text{steps}
$$
If we was to input a larger number such as *1,000,000* instead we would see that A if faster (100 million vs 1 trillion steps)
$$
\mathbf{A: } \space 100,000,000 + 500 \approx 100 \space \text{million steps}
$$
$$
\mathbf{B:} \space (1,000,000)^2 + 1 \approx 1,000,000,000,000 \space \text{steps
}
$$
So this means that algorithm A will always beat algorithm B for a large input

---
## Hidden Constant #hiddenConstant
The hidden constant is a static modifier which can be things such as:
1. The efficiency of the programming language
2. The quality of the compiler
3. CPU 
This is ignored by asymptotic analysis because it doesn't affect the order of growth #orderOfGrowth and it's more concerned with the growth rate rather than the constant (speed) 

The constant becomes *important* when you're comparing 2 algorithms with the same Big-O notation such as O(n^2) such as bubble sort and insertion sort #bubbleSort #insertionSort we must then look at their constant to see which one is faster is most scenarios

## Twiddle ~ #Twiddle #Tilde
Comparison of 2 algorithms with the same Big-O notation would use the tilde notation as to be more precise

$$
\tilde{}
$$
Such as the dishwashing algorithm:
$$
T(n) \space \textasciitilde 15n^2
$$
This can only be done with the algorithms that have the same Big-O complexity

# Analysing the time complexity of an algorithm #timeComplexity #Algorithm 
The order of the underlying algorithm can be determined by analysing the time complexity of each operation and identify which operation will have a larger increase in processing time when more data needs to be processed

Each statement can be classified as a order of growth
- O(1) would refer to a assignment statement
```java
double vat = 0.2;
```
- a return statement
```Java
return (this.age >= 10);
```
- a conditional statement
```Java
if (this.age < 10) {
	return "You are too young"
}
```

- O(n) would responds to a *simple loop*
- O(n^2) would responds to a *nested loop*
- O(n^3) would respond to a *tripled nested loop*

## Analysing Loop Execution #Loop 
A loop executes a certain number of times (n) and the complexity of the loop would be *n* times the body of said loop. If loops are nested than the outer loop is also included into the inner loop

### Analysing the execution of a simple for-loop #For 

```java
int x = 0;
for(int i = 0; i < n; i++) {
	x += i;
}
```
- The `for` loop would be O(n) as the loop executes n times while the body of the loop is O(1) as it's a constant increase 

### Analysing the execution of a simple `while` loop #While
```java
long power = 1;
while( power < n) {
	power *= 2
}
```
- The `while` loop is O(Log n) because the loop executes log2(n) times while the body is O(1) as it's a constant increase 
- This is O(Log n) because the power increase by 2 every iteration compared to O(1) which would be a constant increase
		- 1 x 2 = 2
		- 2 x 2 = 4
		- 4 x 2 = 8
		- 8 x 2 = 16 
	- quickly reaching the *n* and will only stop when power no longer less than *n* 
### Analysing the execution of a simple nested `for` loop #nestedFor #For 
```java
int x = 0;
int y = 0;

for (int i=0; i<n; i++) {
	x = x + 1;
	for (int j=0; j<n; j++) {
		y = y + 1;	
	}
}
```

- This nested`for` loop would be O(n^2) because the loop executed *n* times meaning that it would loop once and then loop again hence being squared, while the body for both are linear O(n) as they grow because of the size of *n*
- If *n* is high than both *x* and *y* variables won't stop until they become bigger than *n* hence being a linear notation
---
Loop executions, like the one above, are only true if there is no fixed value and is dependant on the size of the problem. If it is fixed then it would be O(1) as it would be constant (no changes, if it's 10 it would be done 10 times) whereas it would be O(n) if it was dependant on *n*

```java
for (int i = 0; i < n; i++) { // would be O(n)
	x = x + 1;
	for (int j = 0; j < 10; j++) { // would be O(1)
		y = y - 1	
	}
}
```


---

# Comparing Growth Functions #growthFunctions 
The processing time of algorithms also depend on the processor of the computer, having a faster computer doesn't mean that we shouldn't worry about time efficiency as it's been shown that using a efficient algorithm is better than having a faster computer.

![[Pasted image 20251017104413.png]]

This figure here shows the difference of having a efficient vs non-efficient processor and how a processor may affect that

Algorithm A1 has a low time complexity (only using O(n)) with the data of S1 however when a faster processor is used, A1 can process 10 times more

Algorithm A5 which has the high time complexity (using O(2^n)) speeding up the processor only provides a increase of 3.3, a small constant value.

![[{0193B4D4-774A-4A56-BC96-54EA0BB3E749}.png | Figures ]]
 - This figure shows how algorithms scale when the input *n* increases, it is important to use a efficient algorithm when working with large amounts of data
- This is relevant when working with storing large amounts of data into the computer's memory as Inefficient algorithms can lead to memory overflow and not fix the problem 
- The order of algorithm using Big-O notations is used to see how efficient an algorithm is in general terms however if the algorithm will only be used a few times and will never be too large, implementing the simplest algorithm regardless of the efficiency would be desired due to the processing time

# Average Case and Worst Case analysis
 Average case and worst case analysis must be done to algorithm because if an algorithm performs well on average but there are few worst cases where it performs badly, this may need to be addressed.

If the worst cases are rare, this can be tolerated but if worst cases occur regularly within practical situations, such things need to be distinguished between average and worst-case complexity


[^1]: A logarithm is a function that simply states *what exponent is required to raise a base to get a certain number*