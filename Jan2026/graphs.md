**Cycle in Directed Graph**

**Problem Description**

```swift
Given an directed graph having A nodes. A matrix B of size M x 2 is given which represents the M edges such that there is a edge directed from node B[i][0] to node B[i][1].
```
```swift
Find whether the graph contains a cycle or not, return 1 if cycle is present else return 0.
```

```swift
NOTE:
```
* The cycle must contain atleast two nodes.
* There are no self-loops in the graph.
* There are no multiple edges between two nodes.
* The graph may or may not be connected.
* Nodes are numbered from 1 to A.
* Your solution will run on multiple test cases. If you are using global variables make sure to clear them.


**Problem Constraints**
```swift
2 <= A <= 105

1 <= M <= min(200000,A*(A-1))

1 <= B[i][0], B[i][1] <= A
```


**Input Format**

```swift
The first argument given is an integer A representing the number of nodes in the graph.

The second argument given a matrix B of size M x 2 which represents the M edges such that there is a edge directed from node B[i][0] to node B[i][1].
```

**Output Format**
```swift
Return 1 if cycle is present else return 0.
```

**Example Input**

```swift
Input 1:

 A = 5
 B = [  [1, 2] 
        [4, 1] 
        [2, 4] 
        [3, 4] 
        [5, 2] 
        [1, 3] ]
Input 2:

 A = 5
 B = [  [1, 2]
        [2, 3] 
        [3, 4] 
        [4, 5] ]
```

**Example Output**
```swift
Output 1:

 1
Output 2:

 0
```

**Example Explanation**

```swift
Explanation 1:

 The given graph contain cycle 1 -> 3 -> 4 -> 1 or the cycle 1 -> 2 -> 4 -> 1
Explanation 2:

 The given graph doesn't contain any cycle.
```

**Solution**
```swift
import Foundation

class Solution {
	func solve(_ A: inout Int, _ B: inout [[Int]]) -> Int {
        var graph: [[Int]] = Array(repeating: [Int](), count: A + 1)
        for edge in B {
            graph[edge[0]].append(edge[1])
        }
        //
        var visited: [Bool] = Array(repeating: false, count: A + 1)
        var path: [Bool] = Array(repeating: false, count: A + 1)
        //
        for node in 1...A {
            if !visited[node] {
                //
                if dfs(graph: graph, index: node, visited: &visited, path: &path) {
                    return 1
                }
            }
        }
        //
        return 0
    }

    func dfs(graph: [[Int]], index: Int, visited: inout [Bool], path: inout [Bool]) -> Bool {
        visited[index] = true
        path[index] = true
        //
        for nbr in graph[index] {
            if path[nbr] {
                return true
            }
            if !visited[nbr] {
                if dfs(graph: graph, index: nbr, visited: &visited, path: &path) {
                    return true
                }
            }
        }
        //
        path[index] = false
        return false
    }
}
```

**Path in Directed Graph**


**Problem Description**

```swift
Given an directed graph having A nodes labelled from 1 to A containing M edges given by matrix B of size M x 2such that there is a edge directed from node

B[i][0] to node B[i][1].

Find whether a path exists from node 1 to node A.

Return 1 if path exists else return 0.
```
**NOTE:**

* There are no self-loops in the graph.
* There are no multiple edges between two nodes.
* The graph may or may not be connected.
* Nodes are numbered from 1 to A.
8 Your solution will run on multiple test cases. If you are using global variables make sure to clear them.

**Problem Constraints**
```swift
2 <= A <= 105

1 <= M <= min(200000,A*(A-1))

1 <= B[i][0], B[i][1] <= A
```

**Input Format**
```swift
The first argument given is an integer A representing the number of nodes in the graph.

The second argument given a matrix B of size M x 2 which represents the M edges such that there is a edge directed from node B[i][0] to node B[i][1].
```

**Output Format**
```swift
Return 1 if path exists between node 1 to node A else return 0.
```

**Example Input**

```swift
Input 1:

 A = 5
 B = [  [1, 2] 
        [4, 1] 
        [2, 4] 
        [3, 4] 
        [5, 2] 
        [1, 3] ]
Input 2:

 A = 5
 B = [  [1, 2]
        [2, 3] 
        [3, 4] 
        [4, 5] ]
```

**Example Output**

```swift
Output 1:

 0
Output 2:

 1
```

**Example Explanation**

```swift
Explanation 1:

 The given doens't contain any path from node 1 to node 5 so we will return 0.
Explanation 2:

 Path from node1 to node 5 is ( 1 -> 2 -> 3 -> 4 -> 5 ) so we will return 1.
```

**Solution**

```swift
import Foundation

class Solution {
	func solve(_ A: inout Int, _ B: inout [[Int]]) -> Int {
        var graph: [[Int]] = Array(repeating: [Int](), count: A + 1)
        for edge in B {
            graph[edge[0]].append(edge[1])
        }
        //
        var visited: [Bool] = Array(repeating: false, count: A + 1)

        func dfs(node: Int) -> Bool {
            if node == A {
                return true
            }
            visited[node] = true
            for nbr in graph[node] {
                if !visited[nbr] {
                    if dfs(node: nbr) {
                        return true
                    }
                }
            }
            //
            return false
        }
        //
        return dfs(node: 1) ? 1 : 0
	}
}
```


