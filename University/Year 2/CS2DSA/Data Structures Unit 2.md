### Growth functions
A #Growth-function mathematically describes how completion time or space grows with the size of the problem (n, think of like #Big-O-Notation).
$$T(n) = n^2 + 3n + 100$$
E.g.,
An inefficient dishwasher that gets all the dry dishes wet.
Let's say it takes 40 seconds to wash one dish,
		 it takes 30 seconds to dry one dish, but also has to dry all the previously washed dishes
the total time for (n) dishes is:
$$T(n) = 40n + 30(1 + 2 + 3... + n) = 15n^2 + 55n$$
With coding in mind, growth functions come from our operations. Operations vary by problem, such as comparisons in sorting being more proficient than swaps as comparisons happen regardless of the order of the data.
E.g.,
$$ T(n) = n^2 + 3n + 100$$
As n grows larger and larger, the only dominant term (AKA the part that grows fastest) matters. For example, in
$$ T(n) = 15n^2 + 55n$$
```java
public void showLots()
{
	for(Lot lot : lots)
	{
		System.out.println(lot);
	}	
}
```
The number of times ==System.out.println(lot)== is run is determined by the size of ==lots==. However the for-loop always runs irrespective of the size of ==lots==. As ==lots== grows in size, ==System.out.println(lot)== runs more. From this information we can form the following equation:
$$T(n) \approx 2n + 1$$
###### The squiggly equals sign is an approximate equals sign. "n" is the number of elements in ==lots==.

## Growth Functions & Asymptotic Complexity

We don't need exact growth functions to compare algorithms, only how it grows as n increases AKA the asymptotic complexity of the growth function.
The dominant term is the part that increases fastest, e.g., in T(n) = 15n^2 + 55n, the term 15n^2 is dominant because it grows much faster as n increases.
$$ T(n) = 15n^2 + 55n -> O(n2)$$
$$ T(n) = 200 + 3n -< O(n)$$
$$ T(n) = 37 -> O(1)$$
We can use #Big-O-Notation to capture the dominant term.
