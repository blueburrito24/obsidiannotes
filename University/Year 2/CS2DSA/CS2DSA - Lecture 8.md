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
