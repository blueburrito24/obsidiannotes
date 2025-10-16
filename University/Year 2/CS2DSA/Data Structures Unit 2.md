### Growth functions
A #Growth-function mathematically describes how completion time or space grows with the size of the problem (n, think of like #Big-O-Notation).

T (n) = n^2 + 3n + 100

E.g.,
An inefficient dishwasher that gets all the dry dishes wet.
Let's say it takes 40 seconds to wash one dish,
		 it takes 30 seconds to dry one dish, but also has to dry all the previously washed dishes
the total time for (n) dishes is:
- T(n) = 40n + 30(1 + 2 + 3... + n) = 15n^2 + 55n
With coding in mind, growth functions come from our operations. Operations vary by problem, such as comparisons in sorting being more proficient than swaps as comparisons happen regardless of the order of the data.
E.g.,
