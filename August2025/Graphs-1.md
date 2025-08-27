**Graphs - Collection of Nodes & Edges**


**All Internet is a Graph**
**Example: Social Media, Google Maps**

**Properties/ Types of Graphs**
* Directed (Direction) (If i follow a celebrity does not mean the same person follows me too)
      example: Instagram
```swift
        ....                    ....
      (    ) ---------------> (      ) (Node) (Undirected example as facebook)
        ....                    ....
               Edge
       
```     
* UnDirected (No Direction)
  ```swift
        ....                    ....
      (    ) --------------- (      ) (Node) (Undirected example as facebook)
        ....                    ....
                  Edge
  ```
* For undirected graph cycle length must be atlest 3
       
* Connected graph 
* Disconnected Graphs
* Cyclic Graph (Graph which has a cyclic)
* acyclic Graph (Graph which does not have cycle)
* Degree: Number of nodes connected to `x` (applies to undirected graph)
  ```swift
          18            1
            \          /
              \      /
                  X degree(X) = 5
               /  |  \
              /   |   \ 
            11    12   14
  ```
* In-degree & out-degree (Number of incoming edges & number of outgoing edges & it applies to directed graph)
  ```swift
          18            1
            \          /
             >       <
                 X degree(X) = 5
               ^  ^  ^
              /   |   \ 
            11    12   14
  ```

**We can create either Array of Array of Int, as it shows Nodes & the nodes it connected with the weight of the edges, or we can also use Dictionary also**
```swift
class Pair {
//
weight
node
}
```













          
