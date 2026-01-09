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
