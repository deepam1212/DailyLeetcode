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


The actual benifit of using DAT is lets say the elements are 11, 100, 21, 45, then we get the modules of each item and add them in that index on that array and if the 2 elements got the same modules then it becomes collision

as the searching, inserting, deleting has T.C. O(1)

Dictionary is stored in Array of Array List

🔬 Step-by-step:
1. Hash Function 🔑
Swift uses a hash function to convert "deepam" to a large integer (the hash value).

Example: "deepam".hashValue → some integer like -8733642192857291125

2. Modulo Operation 🧮
The hash is mapped into the internal table using modulo:

swift
Copy
Edit
index = abs(hashValue) % capacity
If the table size is 16, then:
index = abs(-8733642192857291125) % 16 = 5

3. Store in Bucket 🪣
Now value 99 is stored at buckets[5].

Each bucket is often a linked list or an array (in Swift, often open addressing is used instead).

4. On Retrieval:
swift
Copy
Edit
dict["deepam"]
Same steps:

Compute hash of "deepam" → -8733642192857291125

Do modulo → 5

Check buckets[5] for "deepam" key (collision resolution may apply)


