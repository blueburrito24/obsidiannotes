---
tags:
  - "#Stack"
  - "#LinkedStructures"
  - "#Array"
aliases:
  - L6
  - DSA6
image: https://images.unsplash.com/photo-1485470733090-0aae1788d5af?ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxzZWFyY2h8M3x8d2FsbHBhcGVyJTIwNGt8ZW58MHx8MHx8fDA%3D&fm=jpg&q=60&w=3000
description: CS2DSA
Previous: "[[CS2DSA - Lecture 5|Lecture 5]]"
Next: "[[CS2DSA - Lecture 7|Lecture 7]]"
---
# Objectives 
- Examine `stack` processing 
- Demonstrate how a stack can be used to solve practical problems 
- Examine various implementation of stack in Java

# Using Stacks
1. common use-case for stacks is a *undo* feature within applications #Use-Case #Undo
	1. The application keeps track of the recent operations (in reverse order)
	2. When a operation is performed, that operation is pushed onto a stack 
	3. When undo is invoked, the operation is popped off the stack for undoing
2. Another method is during run-time of programming languages 
	1. As methods are called, acitvation records are pushed onto the stack 
	2. As the methods complete it's call, the activation records are popped off
	3. Run-time can then roll back the chain of method calls as each methods finishes it's execution
![[CS2DSA_W6_FIGURE2]]

3. Alternative positions/paths within trial and error algorithm #Algorithm 
4. Postfix expressions can utilise stacks
	1. They can be processed from left to right

# Two-Dimensional Arrays
```Java
int[] [] b;
b = new int[3][4];

double [] [] d = new double[10][10];

int[][] c = {{5, 2, 1, 4},
			  {6, 0, 3, 2}};
```

 1. First a variable  `b` is declared to hold 2D Array of type `int` #Integer 
 2. Storage is then allocated for 2D array object
	 1. This creates storage for 12 values (3 x 4)
 3. Elements can be accessed via notation `b[i] [j]` where *i* is the row and *j* is the column
 4. Can be viewed as a block of memory
 ![[CS2DSA_W6_FIGURE3]]
 5. A 2D Array of `double` #Double which allocates storage for 100 elements (10 rows and 10 columns)
 6. Another 2D array is declared (2 rows and 4 columns), 2D aggregate is used to initialise the elements
	 1. Better than separate declarations
	 2. aggregates can only be used when 2D array variable is declared
---
- Rows can be accessed in Array B using `length` (`b.length`)
- 2D arrays are 1D arrays of 1D arrays, so `b.length` is the number of rows 
- `b.length` works by taking elements from the outer array which would be 2 ({5,2,1,4} and {6,0,3,2} is 2 elements) hence giving rows
---
- To find columns however you can access the first array `b[0].length` 
- What this does is access the first *row* ({5,2,1,4}) and then checks how many elements are in there which would be **4** 
- Hence it would print out 3x4

> [!question]+ Jagged vs Rectangular 2D arrays
> This assumes that your 2D array is *rectangular* (where all rows have the same length) and **not** jagged
> 
> For example (jagged):
> `{1, 2, 3, 4}` - **4 columns** 
> `{5, 6}` - **2 columns**
> `{7, 8, 9}` - **3 columns**
> 
> These have different columns for each array, so `B[0].length` will have a different result compared to `B[1].length`

To process 2D arrays, a nested for loop is required #For #nestedFor 
```Java
for (int i = 0; i < b.length; i++) {
	for (int j = 0; j < b[0].length; j++) {
		b[i][j] *= 2; // multiply by 2 	
	}
}
```

Enhanced `for` loop can be used aswell: #enhancedFor 
```Java
for (int[] row : b) {
	for (int elem: row) {
		elem++; // increment by 1	
	}
}
```

> [!tip] Time Complexity
> Accessing arrays is fast at O(1) as it only requires calculating the address and then accessing the data at that address 
> 
> For 2D arrays however, it can still be done in constant time but requires more effort 
> A whole 2D array with rows and columns requires:
> - A nested loop, executed n times inside a loop which executes m times, the body will be *mn* times 
> 	- m is rows, n is columns 
> - If one element is O(1), the time complexity will be O(*mn*) and if the rows and columns are equal or roughly equal to *n* then the time complexity is **O(n^2)**


# Traversing a Maze using a Stack
#Maze #Stack 
Mazes can be represented as a 2D array using Binary #Binary
This can be done by:
1. 0 representing a block/wall
2. 1 representing a path
This means that a grid can be represented as:
```Java
public class Maze {
    
    // Predefined maze as a 2D array
    // 0 = path, 1 = wall
    int[][] grid = {
        { 1, 1, 1, 0, 1, 1, 0, 0, 0, 1, 1, 1, 1 },
        { 1, 0, 0, 1, 1, 0, 1, 1, 1, 1, 0, 0, 1 },
        { 1, 1, 1, 1, 1, 0, 1, 0, 1, 0, 1, 0, 0 },
        { 0, 0, 0, 0, 1, 1, 1, 0, 1, 0, 1, 1, 1 },
        { 1, 1, 1, 0, 1, 1, 1, 0, 1, 0, 1, 1, 1 },
        { 1, 0, 1, 0, 0, 0, 0, 1, 1, 1, 0, 0, 1 },
        { 1, 0, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1 },
        { 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 },
        { 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1 }
    };
}
```

>[!success]
>Successful traverse would mean a continuous path of 1 is found from start to finished
> - Top left corner to bottom right corner 

To traverse a maze using a trial and error approach/brute force where having a stack allows us to track our moves 
- By remembering the position we prevent taking used paths, this can be done by changing the 1 to a 3 to mark it as *visited*
- There may be more *3s* as paths might have dead ends and would require backtracking to find a visited path

These are the potential moves where not all moves need to be valid

> [!info]  Figure 6
> ![[CS2DSA_W6_FIGURE6]]
> # Figure 6
> Possible scenarios for the neighbouring cells: (i) on the edge, (ii) at the start corner,
> (iii) with neighbouring wall(s), or (iv) neighbouring to previously visited positions, i.e. positions
> marked as ’3’.

For valid moves, they are pushed onto the stack, for example:
- From position (0,0) there are 2 moves:
	1. position (1,0)
	2. position (0,1)
		- These position are pushed onto the stack
- The algorithm works regardless of the order 
- When a move is made, the position is popped from the stack, and is actually moved to this new position
- As we move, more valid moves are found and pushed onto the stack where each position will be marked as visited (by changing 1 to 3)
- The maze continues till the target location is reached (or no valid moves remain)
	- infinite loops are not possible as visited cells aren't revisited 

> [!tip] 
> Maze search enables the target location to be found but the path isn't recorded by the algorithm

Here is the UML class diagram:
>[!info] Figure 7
># Figure 7
> ![[CS2DSA_W6_FIGURE7]]

## Class `Maze`
```Java
package maze;

import dsaj.*;

/**
 * Maze.java
 *
 * Represents a maze of characters. The goal is to get from the
 * top left corner to the bottom right, following a path of 1's.
 *
 * @author Lewis/Chase
 * @author S H S Wong
 * @author A Barnes
 * @version 10-2018
 */
public class Maze {
    // For Marking a location within the maze that has been visited.
    private final int TRIED = 3;
    private Position start = new Position(0, 0);
    private Position finish = new Position(8, 12);

    // The maze as represented by a 2D grid.
    private int[][] grid = {
        { 1, 1, 1, 0, 1, 1, 0, 0, 0, 1, 1, 1, 1 },
        { 1, 0, 0, 1, 1, 0, 1, 1, 1, 1, 0, 0, 1 },
        { 1, 1, 1, 1, 1, 0, 1, 0, 1, 0, 1, 0, 0 },
        { 0, 0, 0, 0, 1, 1, 1, 0, 1, 0, 1, 1, 1 },
        { 1, 1, 1, 0, 1, 1, 1, 0, 1, 0, 1, 1, 1 },
        { 1, 0, 1, 0, 0, 0, 0, 1, 1, 1, 0, 0, 1 },
        { 1, 0, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1 },
        { 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 },
        { 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1 }
    };

    StackADT<Position> stack = new ArrayStack<>(200);

    /**
     * A method for pushing a new position onto the stack. A new position (x, y) 
     * is pushed onto the stack ONLY IF it is a valid position that is it
     * is inside the grid, is not a wall and has not been visited already.
     */
    private void push_new_pos(int x, int y) {
        if (valid(x, y)) {
            stack.push(new Position(x, y));
        }
    }

    /**
     * Attempts to iteratively traverse the maze. It inserts special
     * characters indicating locations that have been tried and that
     * eventually become part of the solution. This method uses a
     * stack to keep track of the possible moves that could be made.
     */
    public boolean traverse() {
        boolean done = false; // set true when the finish position is reached
        Position pos;
        stack.push(start);

        while (!done) {
            pos = stack.pop();
            grid[pos.getX()][pos.getY()] = TRIED; // this cell has been tried
            
            if (pos.getX() == finish.getX() && pos.getY() == finish.getY()) {
                done = true; // the maze is solved
            } else {
                /*
                 * Get the four positions that are adjacent to the current
                 * position, i.e. the positions on the left, on the right,
                 * above and below the current position. These correspond
                 * to the potential moves. Each of such position is analysed
                 * to see if it is a valid move. Only valid moves will be
                 * pushed onto the stack.
                 */
                push_new_pos(pos.getX(), pos.getY() - 1);
                push_new_pos(pos.getX(), pos.getY() + 1);
                push_new_pos(pos.getX() - 1, pos.getY());
                push_new_pos(pos.getX() + 1, pos.getY());
            }
        }
        return done;
    }

    /**
     * Determines if a specific location is valid.
     */
    private boolean valid(int row, int column) {
        boolean result = false;

        /* Check if cell is in the bounds of the maze */
        if (row >= 0 && row < grid.length && column >= 0 && column < grid[row].length) {
            /* Check if cell is not blocked and not previously tried */
            if (grid[row][column] == 1) {
                result = true;
            }
        }

        return result;
    }

    /**
     * Returns the maze as a string.
     */
    public String toString() {
        String result = "\n";

        // Print the grid line by line
        for (int row = 0; row < grid.length; row++) {
            // Print each element in a line
            for (int column = 0; column < grid[row].length; column++) {
                result += grid[row][column] + "";
            }
            result += "\n";
        }
        return result;
    }
}
```

## Class `Position`
```Java
package maze;

/**
 * Position.java
 * Represents a single position in a rectangular grid
 *
 * @author Lewis/Chase
 * @author A Barnes
 * @author S H S Wong
 * @version 24-10-2010
 */
public class Position {
    private int x;
    private int y;

    /**
     * Constructs a position and sets the x and y coordinates
     * @param x X coordinate of a position
     * @param y Y coordinate of the position
     */
    Position(int x, int y) {
        this.x = x;
        this.y = y;
    }

    /**
     * Returns the x-coordinate value of the current position.
     * @return the X coordinate of the current position
     */
    public int getX() {
        return x;
    }

    /**
     * Returns the y-coordinate value of the current position.
     * @return the Y coordinate of the current position
     */
    public int getY() {
        return y;
    }
}
```

## Class `MazeSearch`
```Java
package maze;

/**
 * MazeSearch.java
 * Top-level class for the maze-search application.
 * This application simulates the process of finding a path of 1's in a
 * maze of characters (represented by 1's and 0's).
 *
 * @author Lewis/Chase
 * @author S H S Wong
 * @version 24-10-2010
 */
public class MazeSearch {
    /**
     * Creates a new maze, prints its original form, attempts to solve it,
     * and prints out its final form.
     */
    public static void main(String[] args) {
        // Create the maze.
        Maze labyrinth = new Maze();

        /*
         * Print the maze. At the beginning, the maze contains 0's (i.e.
         * blockage) & 1's (i.e. path) only.
         */
        System.out.println(labyrinth);

        /*
         * labyrinth.traverse() is for traversing the maze. When a path is
         * found at the end of the maze traversal, the value true is returned.
         * Otherwise, false is returned.
         */
        if (labyrinth.traverse()) {
            System.out.println("The maze was successfully traversed!");
        } else {
            System.out.println("There is no possible path.");
        }

        /*
         * Print the maze after the traversal has taken place. As during the
         * traversal, each visited position is marked with 3, the maze should
         * now contain 0's, 1's & 3's.
         */
        System.out.println(labyrinth);
    }
}
```

# Evaluating Postfix Expressions using a Stack
#Postfix #Stack 
In postfix, the operator comes after the 2 operands and parentheses aren't required which compared to infix where parentheses are used for precedence

Postfix:
$$
3 \space 4 + \space 2 \times
$$
Infix:
$$
(3+4) \times 2
$$

This means that postfix expressions can be used with a stack for storing the operands and then the results of the computation, this is done by:
1. Scan left to right to check if input is operator or operand
2. If operand, push it on the stack 
3. if operator, pop stack *twice* to get 2 operands, do operation and then push result back into stack

## Class `Postfix` 
This class utilises a array-based stack to find postfix expressions
The operands are integers so the class will only work with Integer objects only #Integer 

```Java
package postfix;

import java.util.Scanner;

public class Postfix {
	public static void main (Stringp[] args) {
		String expression, again;
		int result;
		
		try {
			Scanner in = new Scanner(System.in);	
			
			do {
				PostfixEvaluator evaluator = new Postfix Evaluator();
				System.out.println("Enter a valid postfix expression: ");
				expression = in.nextLine();
				
				result = evaluator.evaluate(expression);
				System.out.println();
				System.out.println("That expression equals " + result);
				
				System.out.print ("Evaluate another expression [y/n]? ");
				again = in.nextLine();
				System.out.println();	
			}
		}
		while (again.equalsIgnoreCase("y"));
	}
	catch (Exception IOException) {
		System.out.println("Input exception reported");	
	}
}
```

- This Postfix implementation uses a `LinkedStack` object to model the stack, any implementation of the stack will suffice 
- `PostfixEvaluator` uses a `LinkedStack` object which is used to evaluate of the expressions, where this class is used by `Postfix
- `Postfix` then defines how a postfix expressions is obtained by the user via the input stream using scanner 

```Java
package postfix;

import dsaj.*;
import java.util.StringTokenizer;

public class PostfixEvaluator {
	private final char ADD = '+';
	private final char SUBTRACT = '-';
	private final char MULTIPLY = '*';
	private final char DIVIDE = '/';
	private final char REMAINDER = '%';
	private StackADT<Integer> stack;
	
	// Create new stack
	publc PostfixEvaluator() {
		stack = new LinkedStack<>();	
	}
	
	public int evaluate(String expr) {
		int op1, op2, result = 0;
		String token;
		// Break input into tokens
		StringTokenizer tokenizer = new StringTokenizer (expr);
		
		white (tokenizer.hasMoreTokens()) {
			token = tokenizer.nextToken();	
			// if token is a operator then pop 2 integers, push result back
			if (isOperator(token)) {
				op2 = stack.pop();
				op1 = stack.pop();
				result = evalSingleOp (token.charAt(0), op1, op2);
				stack.push (result);	
			}
			else 
				// if not, token is a integer 
				// convert to type int and push to stack
				stack.push (Integer.parseInt(token));
		}
		return result;
	}
	
	// check if token is a operator
	private boolean isOperator (String token) {
		return ( token.equals("+") || token.equals("-")) 
			|| token.equals("*") || token.equals("/") || token.equals("%");	
	}
	
	private int evalSingleOp (char operation, int op1, op2) {
		int result = 0;
		
		switch (operation) {
		case ADD:
			result = op1 + op2;
			break;
		case SUBTRACT:
			result = op1 - op2;
			break;
		case MULTIPLY:
			result = op1 * op2;
			break;
		case DIVIDE:
			result = op1 / op2;
			break;
		case REMAINER:
			result = op1 % op2;
		}	
		return result;
	}
}
```

# Class `java.util.Stack`
- `java.util.Stack` has been part of JDK since version 1
From the Java documentation, it states: 
>[!important] 
>The Stack class represents a last-in-first-out (LIFO) stack of objects. It extends class Vector with
five operations that allow a vector to be treated as a stack. The usual push and pop operations are
provided, as well as a method to peek at the top item on the stack, a method to test for whether the
stack is empty, and a method to search the stack for an item and discover how far it is from the top.
When a stack is first created, it contains no items.

- Class `Stack` has operations such as `pop`, `push`, `peek`, and `empty` (to check if empty)
- `java.util.Stack` extends `java.util.Vector` 
	- This means that it has characterisitcs that aren't natural for a pure stack
		- `add`
		- `addAll`
		- `addElement`
		- `capacity`
		- `contains`
		- `elementAt`
		- `indexOf`
		- `insertElementAt`
		- `remove`
		- `removeAll`
		- `subList`
		- `trimToSize`
	- These methods violate what a pure stack should do such as `insertElementAt` which provides a method to insert a element at a specific index where stacks only have access to the top 
	- The method `search` searches through the stack and returns if element exists within stack
		- Stacks only have openings at one end, elements shouldn't be inspected unless at the top 
---
- Classes like `java.util.Stack` and `java.util.Vector` have been around since Java 1
- `java.util.Stack` is ***NOT*** part of the JCF #JavaCollectionFramework Java Collection Framework 
- `java.util.Vector` however has been configured to implement `java.util.List` hence making it ***PART*** of the Java Collection Framework (JCF) #JavaCollectionFramework 
 >[!tip] `java.util.Stack` documentation 
 > <iframe src="https://docs.oracle.com/javase/8/docs/api/java/util/Stack.html" title="Java Docs regarding Stacks" width="600" height="600"></iframe>

- As we know that `java.util.Stack` doesn't have the true attributes of a pure stack, to fix this a wrapper class can be used:
	1. A wrapper class called `PureStack` can be made
	2. This wrapper class contains `contents` where type is of `java.util.Stack` 
	3. Class `PureStack` can be then define methods that only belong to a pure stack 
		1. `pop`
		2. `push`
		3. `peek`
		4. `isEmpty`
	4. These methods simply call the same method within `java.util.Stack` 

```java
package dsaj;
import java.util.Stack;

public class PureStack<T> {
	private Stack<T> contents;
	
	public PureStack() {
		contents = new Stack<>();	
	}
	
	// add element to top of stack	
	public void push(T item) {
		contents.push(item)	
	}
	
	// remove and return element from top of stack
	public void pop() {
		return contents.pop();	
	}
	
	// return top element without removing it 
	public void peek() {
		return contents.peek();	
	}
	
	// size of stack 
	public int size() {
		return contents.size();
	}
	
	// check if stack empty
	public boolean isEmpty() {
		return contents.isEmpty();	
	}
}
```

> [!danger] information regarding `java.util.Stack`
> Class `java.util.Stack` is a legacy class, it shouldn't be used
> The Java API specification states:
> -  A more complete and consistent set of LIFO stack operations is provided by the Deque interface
>and its implementations, which should be used in preference to this class. For example:
> 	- `Dequeue<Integer> stack = new ArrayDeqeue<>();`

# Interface `java.util.Dequeue`
> [!info] Java Platform API Specification
> A linear collection that supports element insertion and removal at both ends. The name deque
is short for ”double ended queue” and is usually pronounced ”deck”. Most Deque implementa-
tions place no fixed limits on the number of elements they may contain, but this interface supports
capacity-restricted deques as well as those with no fixed size limit.
This interface defines methods to access the elements at both ends of the deque. Methods are
provided to insert, remove, and examine the element. Each of these methods exists in two forms:
one throws an exception if the operation fails, the other returns a special value (either null or false,
depending on the operation). The latter form of the insert operation is designed specifically for use
with capacity-restricted Deque implementations; in most implementations, insert operations cannot fail 
Deques can be used as LIFO (Last-In-First-Out) stacks. This interface should be used in prefer-
ence to the legacy Stack class. When a deque is used as a stack, elements are pushed and popped
from the beginning of the deque. Stack methods are precisely equivalent to Deque methods as indi-
cated in the table below: ![[CS2DSA_W6_DEQUEUE]]

>[!tip] Java Collection Framework
>`java.util.dequeue` has been introduced into Java Collection Framework since *Java 1.6*

>[!tip] Usage of `java.util.Dequeue`
>It is a multi-purpose collection designed to be used as either **stack** or **queue**

# Class `java.util.ArrayDequeue`
>[!info] Java Documentation regarding `ArrayDequeue` 
>Resizable-array implementation of the Deque interface. Array deques have no capacity restric-
tions; they grow as necessary to support usage. . . . Null elements are prohibited. This class is likely
to be faster than Stack when used as a stack, and faster than LinkedList when used as a queue.
Most ArrayDeque operations run in amortized constant time. Exceptions include remove,
removeFirstOccurrence, removeLastOccurrence, contains, iterator.remove(),
and the bulk operations, all of which run in linear time. 

>[!hint]  Java Collection Framwork
>Class `java.util.ArrayDequeue` has been in JCF since **Java 1.6**

`ArrayDequeue` implements `java.util.Dequeue` which means it can be used as a **stack**, however anyone who uses it must stick to the *stack-only* methods such as `addFirst` `removeFirst` and `peekFirst`

# Class `java.util.concurrent.LinkedBlockingDeque` 
>[!info] Java Documentation
>An optionally-bounded blocking deque based on linked nodes.
The optional capacity bound constructor argument serves as a way to prevent excessive expan-
sion. The capacity, if unspecified, is equal to Integer.MAX VALUE. Linked nodes are dynamically
created upon each insertion unless this would bring the deque above capacity.
Most operations run in constant time (ignoring time spent blocking). Exceptions include re-
move, removeFirstOccurrence, removeLastOccurrence, contains, iterator.remove(), and the bulk op-
erations, all of which run in linear time.

- Just like `ArrayDequeue` it also implements `java.util.Deque` which means it can be used as **stack** 
	- The programmer must stick to stack-only methods just like `java.util.ArrayDequeue`

>[!tip] Java Collection Framework
>`java.util.concurrent.LinkedBlockingDeque` has been in JCF since *Java 1.6*

# Class `java.util.LinkedList`
>[!info] Java Documentation
>Doubly-linked list implementation of the List and Deque interface. Implements all optional
list operations, and permits all elements (including null).
All of the operations perform as could be expected for a doubly-linked list. Operations that index
into the list will traverse the list from the beginning or the end, whichever is closer to the specified
index.
The iterators returned by this class’s iterator and listIterator methods are fail-fast: if
the list is structurally modified at any time after the iterator is created, in any way except through the
Iterator’s own remove or add methods, the iterator will throw a ConcurrentModificationException.
Thus, in the face of concurrent modification, the iterator fails quickly and cleanly, rather than risking
arbitrary, non-deterministic behaviour at an undetermined time in the future.
This class is a member of the Java Collections Framework.

- `java.util.LinkedList` also implements `java.util.Deque` which means it can also be used as a stack but must stick to stack-only methods 

>[!tip] Java Collection Framework
>`java.util.LinkedList` has been in JCF since **Java 1.2**, retrofitted in **Java 1.6** to implement `Deque` interface 



