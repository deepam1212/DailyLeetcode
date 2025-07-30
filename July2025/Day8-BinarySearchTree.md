**Find the Kth Smallest Ele,ent in BST:**
**Idea 1: Brute Force**

**Idea 2 : In Order of a BST is always Sorted as it follows Left Node Right**

```
        4
      /   \
     0     10 
    / \     / \
   -1  3   7   20
          / \   / \
         6   9  10 25
```
-1 0 3 4 6 7 9 10....
so 3rd smallest element is 3

**Idea 3:** Dont store all the elements in Array, take a variable count and increase it & once it reaches to k print it


```swift
class Node {
    var val: Int
    var left: Node?
    var right: Node?

    init(_ val: Int) {
        self.val = val
        self.left = nil
        self.right = nil
    }
}

func kthSmallest(root: Node?, k: Int) -> Int? {
    var count = 0
    var result: Int? = nil

    func inOrder(_ node: Node?) {
        guard let node = node, result == nil else { return }

        inOrder(node.left)

        count += 1
        if count == k {
            result = node.val
            return
        }

        inOrder(node.right)
    }

    inOrder(root)
    return result
}
```

**InOrder Traversal of Binary Tree:**

        1
       / \
      2   3
     / \   \
    4   5   6
 We can solve this using Morris InOrder Traversal as the Space C. is O(1)


