**House Robbers:**


**Lets say that we want to rob any house, but i can not rob the Adjuscenr House:**

```swift

        H1          H2        H3        H4
      [ 1            2         3        1]

Answer = [1,3]

    [2  7  9  3  1]

answer = [2,7,1]  
```

**Approaches:**
  * Rob max money house❌
  * Sum of all odd and the sum of all even❌ // [100, 1, 1, 100], as taking odd index sum & even index sum gives 101, but the maximum money is 200
  * **BruteFoce Idea:** Try out all possibilities
```swift
        0   1  2   3
  A = [100  1  1  100]

          f(0)
    ROB   /  \ !ROB
         /    \
  100 + f(2)   f(1)
       / \ 
  ROB /   \!ROB
1 + f(4)  f(3)
```

**Question: in am n*m matrix how many ways we can react from 0,0 to n-1, m-1**






