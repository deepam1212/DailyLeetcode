**A Direct Access Table is a simple and efficient data structure that allows constant time access (O(1)) to elements using keys as indexes — typically integers from a known and small range. It’s like an array where each index directly corresponds to a key, making operations like insert, delete, and search very fast.**


🧠 Why it's called a "Direct Access Table" and not just an "Array"
Conceptual Purpose:

An array can store anything, anywhere.

A Direct Access Table (DAT) is used with the assumption that the key itself is an integer index from a known universe (say 0...n).

The key maps directly to an index, without any hashing or searching.

Analogy:

Think of it like a hash table with a perfect hash function: index = key, which means:

No collisions.

No need for probing or chaining.

Access is truly O(1).

Terminology Origin (from Algorithms textbooks like CLRS):

"Direct Access Table" is a term used in algorithm theory to describe how you store and retrieve values without computation or lookup — purely by index.

Data Structure vs Implementation:

Array = Implementation (low-level tool).

Direct Access Table = Abstract Data Type (conceptual model).

Just like a stack can be implemented using an array or linked list — it's the behavior that defines it.



