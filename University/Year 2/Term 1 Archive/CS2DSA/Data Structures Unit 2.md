### Lecture 2
### "Motivation"
Software quality can include the efficient use of resources, like the CPU.
Algorithm analysis is a core computing topic which gives us a basis to compare the efficiency between algorithms. E.g.,
- Which sorting algorithm is more efficient?
- Which data structure requires less memory?
- Which type of collection ensures the most efficient access to its data elements?

During software development, knowing the characteristics of the available data structures and algorithms enables us to make a more informed choice concerning which data structure and algorithm to use and so improves the quality of the final software product.

### "How to approach analysing an algorithm?"
Analysing an algorithm is in other words determining the resources that are necessary to execute it, the number of instructions and storage needed etc.
The efficiency or complexity of an algorithm is treated as a mathematical function relating the size of input to:
- the number of steps (time complexity) or,
- the size of storage space (space complexity)

required to execute the algorithm.
A growth function can be used to describe the time or space complexity of an algorithm. This often involves using Big-O Notation to describe the efficiency of an algorithm.

### "Growth Functions"
Analysis is defined based on:
- the problem size
- a key operation

Comparisons are typically chosen as the key operation when analysing sorting algorithms. Swaps are more expensive, taking 3 operations compared to comparing only taking 1, so swapping costs more per operation. 
Comparisons also occur more often as every sorting algorithm has to compare values to determine order. So comparisons are better for analysis as they occur more and so are more reliable than swaps.
We can express problem size in terms of how much data needs to be processed. Growth functions show the relationship between the size of the problem (n) and the time T(n) or the storage space S(n) it takes to solve the problem, e.g.,;

$$ T(n) = n^2 + 3n + 100 $$
When substituting "n" with the expected amount of data, we can estimate the time needed to finish the task, following the above growth function.
E.g.,
- Consider an inefficient dishwasher, whom washes dishes carelessly. Every time a dish is washed, he somehow wets all the previously washed AND dried dishes again.
- So his dishwashing cycle involves the time for washing, drying AND re-drying previously washed dishes. This guy sucks.
- Let's say washing a single dish takes 40 seconds, and drying each dish takes 30 seconds. How long does washing n dishes take?
- T(n) denotes the time required for washing n dishes:
$$T(n) = \underset{n}{\times} \text{ washing time} + \sum_{i=1}^{n} (i \times \text{drying time})$$
$$= T(n) = 40n + \sum_{i=1}^{n} (30i)$$
$$ = 40n + 30n(n+1)/2 $$
$$ = 15n^2 + 55n $$
Note that the $\sum_{i=1}^{n}$ part means sum or add up all the terms. Here it says, sum from i=1 to n of (30i), 30 meaning drying time and n being the amount of dishes. Also note that you read from the bottom!
The final equation is T(n) = 15n$^2$ + 55n.
So, growth functions show us the time or space complexity of an algorithm for solving a problem!

### "Formulating a growth function from source code"
Like the previous example, we can also formulate a growth function to estimate the time taken for a piece of source code to execute entirely. Execution time can vary between computers, but if we simplify the task by assuming each step will take the same time to complete we can estimate the execution time of the program by its number of steps. 
Consider the following method, "lots" is a java.util.ArrayList\<Lot> object:
```java
public void showLots() {
	for(Lot lot : lots) {
		System.out.println(lot);
		}
	}
```
The print line will run based on how big "lots" is, e.g., if there's 5 objectsin the ArrayList object lots, 5 prints will be executed. No matter what, the for-loop runs, so this must be factored in, alongside it running more as the ArrayList object lots increases in size. We can estimate the growth function as:
$$ T(n) \approx 2n + 1 $$
n being the number of elements in lots!

### "Growth Functions & the Asymptotic Complexity of an Algorithm"
To determine if an algorithm is efficient or what would be more efficient, we don't need to know the exact growth function.
We should focus on the "asymptotic complexity" of the function, how it grows as the problem (n) increases.
This is determined by the "dominant term" in the growth function;
a dominant term is the term that is most important to the result of the growth function, as its value increases as quick as n increases, e.g.,
$$ T(n) = 15n^2 + 55n $$
The dominant term is 15n^2 because it value increases way quicker than 55n, as the problem size n increases.
Asymptotic complexity is referred to as the order of the algorithm.
We use Big-O Notation to specify that order, such as O(1), O(n), O$(n^2)$.
The complexity of an algorithm is O(1) when it runs in constant time - there are no changes in its speed. Another example is the dishwasher algorithm which is O$(n^2)$ where the time complexity increases quadratically (squaring) as n increases.
Another example! Binary search runs an amount of steps in logarithmic time, O(log n).
Question from the beyond:
"Does the constant (multiplier) in front of $n^2$ matter when determining which term dominates?"
No! Even if you have the tiniest of constants like:
$$ T(n) \frac{1}{100,000,000} n^2 + 45n $$
You would think that 1/100,000,000 is sooo small, But no, for example with a large n:
$$ \frac{1}{100,000,000} \times (10,000,000,000)^2 = a\ huge\ number $$
$$ 45 \times 10,000,000,000 = much\ smaller $$
Even with the tiny fraction, n^2 still becomes much larger than 45n when it gets big enough. Always bet on exponential growth.
Also, here's some examples of growth functions and their asymptotic complexity.
![[{14C78A5B-D555-4765-BDA3-9647493F4BD9}.png]]
We only need the dominant term to determine the order of growth!
$$ T(n) = n(2n + 3) $$
For example here we only need to calculate n x 2n to determine its order to be O$(n^2)$ instead of simplifying the entire growth function.

### "Examples of common orders of functions"
The table further below shows common orders of functions, listed in their relative order of time efficiency in Big-O notation! i.e.,
$$ O(1) ≺ O(log n) ≺ O(n) ≺ O(n log n) ≺ O(n2) ≺ O(n3) ≺ O(2n) $$
The Big-O expressions above are listed left-to-right in order of time efficiency, the ones that less take time to run on the left and vice versa. 
O(1) for example, is the most efficient while O$(n^2)$ is the least efficient.
![[{E05279F4-7FEB-406E-8AFF-E99C64F1959B}.png]]

### "Asymptotic Analysis"
Asymptotic Analysis is a method of classifying limiting behaviour, concentrating on some sort of trend/pattern.
Asymptotic estimates are used because different or "reasonable" implementations of the same algorithm can differ in efficiency. That difference is regarded as unimportant in the analysis of algorithms, as the efficiency of two implementations are related by a more constant multiplicative factor known as the "hidden constant".
For example, consider linear and binary search. They find a target amongst a group of items to determine if it's there or not.
Linear examines each item one by one. O(n).
Binary search begins the comparison with the middle item in the group and then compares either the elements on the right or left side in the same fashion. O(log n).
A careless implementation of a binary search could take twice as long as an efficient one, so the hidden constant is 2. But, both binary search implementations have the order O$(\log_{2} n)$ whereas any implementation of a linear search, no matter how efficiently coded, will have order O(n).
For large n, the binary search algorithms will always out-perform the linear search.
We can be more precise and distinguish between the efficiency of two algorithms with the same asymptotic complexity (or same Big-O behaviour), the $\sim$ "tilde" sign (albeit the single variant) is used (meaning similarly equal to) and we keep the constant multiplier in the dominant term. 
If we relate to the dishwashing example:
$$ T(n)  \sim 15n^2 $$
But if we found a dishwasher who would dry dishes in 20 seconds, the time complexity would be:
$$ T(n) \sim 10n^2 $$
as shown in the below elaborated example:
$$ T(n) = n \times washing\ time\ + \sum_{i=1}^{n}  (i\ \times drying\ time) $$
$$ = 40n+ \sum_{i=1}^{n}  (i\ \times drying\ time)  $$
$$ = 40n\ +\ 20n(n+1)/2 $$
$$ = 40n\ +\ 10n(n+1) $$
$$ = 40n\ +\ 10n^2\ + 10n$$
$$ = 50n\ +\ 10n^2 $$
As another example, we have two simple sorting algorithms! 
Straight insertion sort and bubble sort. 
Both sorts have a Big-O behaviour of O\(n^2), however a straight insertion sort has the comparative values $C(n) \sim \frac{1}{2} n^2$ and $A(n) \sim \frac{1}{2} n^2$ while a bubble sort would have the corresponding (or equivalent) values $C(n) \sim \frac{1}{2} n^2$ and $A(n) \sim \frac{3}{2} n^2$. Both sorts are inferior however, to advanced sorts like heap sorts or quick sorts which have a complexity of lower order, O$(n \log_{2} n)$.

### "Analysing the time complexity of an algorithm"
Given source code, method or even a procedure, we can determine the order of the underlying algorithm by analysing the time complexity (Big O) of its operations and identify which operations increase the required processing time substantially when the size of the problem (or data to be processed) grows.
Each type of statement can be classified by a typical order of growth, e.g.,
O(1) corresponds to:
- an assignment statement such as,
```java
double vat = 0.2;
```
- a return statement such as, 
  ```java
return (this.age >= 18);
```
- a conditional statement such as,
```java
if (this.age < 18) {
	return "You are too young to buy alcohol.";
	}
```

O(n) typically corresponds to a simple loop.
O$(n^2)$ typically corresponds to a nested loop (loop within a loop).
O$(n^3)$ typically corresponds to a triple nested loop (loop, within a loop within a loop).

"Analysing Loop Execution"
- Simple for-loop
The following for-loop is O(n) because the loop executes n times, while the body of the loop is O(1).
```java
int x = 0;
for (int i=0; i<n; i++) {
	x += i;
	}
```
- Simple while-loop
The following while-loop is O(log n) because the loop executes $log_2$(n) times, where n is the size of the computing problem, the body of the loop is O(1).
```java
long power = 1;
while (power < n) {
	power *= 2
	}
```
The number of times (x) that the while-loop executes depends on how quickly the value of power reaches/exceeds the value of n.
In each iteration, the power increases by a factor of 2.
The loop terminates at the first value of x for which:
$$ 2^x  \geq n $$
The loop executes x times, where x is the first integer $\geq$ $log_2(n)$.
This means the time complexity of the above loop is O$(log_2n)$.
- Simple nested for-loop
The following nested for-loop is O$(n^2)$ because the loop executes n times while the body of the loop, including the nested loop, is O(n).
```java
int x = 0;
int y = 0;

for (int i=0; i<n; i++) {
	x = x + 1;
	for (int j=0; j<n; j++) {
		y = y - 1;
		}
	}
```
The below definition of "maxSubsequenceSum" executes over a given int[].
The method body contains a nested for-loop which executes in cubic time, i.e., O$(n^3)$. 
This is because the loop executes n times and the body of the loop contains another nested for-loop. 
With each loop executing up to n times, the time complexity is n x n x n, i.e., $n^3$.
```java
public static int maxSubsequenceSum(int[] a) {
	int maxSum = 0;
	int seqStart = 0;
	int seqEnd = 0;
	
	for (int 1 = 0; i < a.length; i++) {
		for(int j = i; j <= i; j++) {
			int thisSum = 0;
			for(int k = i; k <= j; k++) {
				thisSum += a[k];
			}
			if (thisSum > maxSum) {
				maxSum = thisSum;
				seqStart = i;
				seqEnd = j;
				}
		}
	}
}
```
Also note that the above for-loop executions if the number of execution of each loop depends on the size of the problem! If a loop executes a fixed number of times, the time complexity is O(1).

### "Comparing Growth Functions"
The processing time of an algorithm also depends on the speed of the computer processor used, which is a detail we pushed off in previous topics. If we're using a faster computer processor, it actually doesn't really matter - efficient algorithms can be far better than a fast computer processor.
In the below table, "maximum problem size" refers to the amount of data an algorithm can process. Algorithm A$_1$ for example can cope with a problem of size S$_1$ with a standard processor, but it can process 10x more data under a faster processor.
![[{9F013D90-3839-4C6D-AF95-F6E50F8D497C}.png]]
An algorithm with high time complexity such as Algorithm A$_5$ does not improve substantially under a faster processor, such as 3.3.
Whereas, a low time complexity algorithm like the aforementioned Algorithm A$_1$ gains 10x speed under a faster processor.
So, we see how a better algorithm is the key to victory!

The below graph shows typical growth functions and their increases in processing time (mapped onto the Y-axis) as n (the size of the problem) increases.
When dealing with a large volume of data, such as in most commercial situations, it is particularly crucial we use an efficient algorithm.
When dealing with lots of complex inputs, using an inefficient algorithm can lead to memory overflow and so failure to solve the problem.
This is relevant especially when your computing problem requires the storing of large working data in the computer's main memory.
The order of an algorithm, regardless of what order, indicates its efficiency in general terms. 
But, in some cases, for example if we know the problem size will never be large or if the program will only be ran a few times on moderately sized problems, using a less efficient algorithm intentionally can be simpler to implement while achieving the same solution.
Not all efficient algorithms can be justified with time constraints and the level of effort needed.
![[Pasted image 20260107235757.png]]

### "Average Case and Worst Case Analysis"
Sometimes an algorithm can perform well on average, but for a few special input data sets, or worst cases, of the same size it performs substantially worse.
If worst case data arises rarely in practice, we might be able to tolerate that. However, if worst cases, rare in random data, occur frequently in practical situations then we have encountered a problem!
In this scenario, we need to distinguish between average case and worst case time complexity.
For example! The original quick sort algorithm has an average time complexity of O(n log n), but has a worst case time complexity of O$(n^2)$.
The worst cases occur when the data is already sorted or or even sorted in reverse order. 
Algorithms can also perform badly if only a few data items are out of order. The chances that a random data set is already or almost sorted is very small, but in practice the chances of it occurring are quite high. 
A typical application might sort a large data set, then sort them in reverse order. Or! After initial sorting, it could add or modify a few data items and re-sort the set. In both cases, the algorithm behaviour is O$(n^2)$ rather than O(n log n).

### "Software Engineering and Data Structures"
As software grows more complex, we need efficient algorithms to meet user needs.
Knowing the characteristics of each data structure, we can make appropriate engineering choices when developing such software.