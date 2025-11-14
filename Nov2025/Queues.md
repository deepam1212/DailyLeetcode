**Queue:** FIFO or LILO (First In First Out/ Last In Last Out)

**Queue is not a class, instead it is a protocol, while stack is a class**

functions which queue has in java

```swift
add(), insert at the end which is append() in swift
remove() in java removefirst() in swift
peek() in java is similar to first in swift
Similar to stack overflow we also have queue overflow

Queue = means add
dequeue = means remove

initialize with two pointers, front & read, add in the rear and remove from front, when the first element is added make front = 0 & rear = 0, initally both the values stand at -1, and once remove, front += 1, if front > rear it means array is empty, then make both the variables, front and rear as -1
```

To implement in LinkedList

```swift
in LinkedList

insert in tail & remove from tail
```

```swift
Enqueue Function will be refereed to add & dequeue function will be referred to remove
```

```swift
Implement Queue using Stack

As Stack follows FILO || LIFO, But queue uses FIFO || LILO

If we try to implement Queue using Stack, then Addition is fine as we use .append, but removing would take O(N) T.C.,  so we use 2 Stacks foer this

here is the Solution

import Foundation
import Glibc

class UserQueue {
    private var queue: [Int] = []
    private var stack1: [Int] = []
    private var stack2: [Int] = []

    /** Initialize your data structure here. */
    init() {
        
    }
    
    /** Push element X to the back of the queue. */
    func push(_ X: Int) {
        self.stack1.append(X)
    }
    
    /** Removes the element from in front of the queue and returns that element. */
    func pop() -> Int {
        if stack2.isEmpty {
            while(!stack1.isEmpty) {
                stack2.append(stack1.last ?? 0)
                stack1.removeLast()
            }
        } 
        let number: Int = stack2.last ?? 0
        stack2.removeLast()
        return number
    }
    
    /** Get the front element of the queue. */
    func peek() -> Int {
        if stack2.isEmpty {
            while(!stack1.isEmpty) {
                stack2.append(stack1.last ?? 0)
                stack1.removeLast()
            }
        } 
        let number: Int = stack2.last ?? 0
        return number
    }
    
    /** Returns whether the queue is empty. */
    func empty() -> Bool {
        return stack1.isEmpty && stack2.isEmpty
    }
}

/**
 * Your UserQueue object will be instantiated and called as such:
 * let obj = UserQueue()
 * obj.push(X)
 * let param2 = obj.pop()
 * let param3 = obj.peek()
 * let param4 = obj.empty()
 */
```


**Deque: Double Ended Queue is like Insertion & Deletion can happen from both ends, but in case of Normal Queue we can add at last & remove at first**














