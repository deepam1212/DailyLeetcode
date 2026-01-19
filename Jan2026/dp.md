**Fibonacci Number**


```swift
The Fibonacci numbers, commonly denoted F(n) form a sequence, called the Fibonacci sequence, such that each number is the sum of the two preceding ones, starting from 0 and 1. That is,

F(0) = 0, F(1) = 1
F(n) = F(n - 1) + F(n - 2), for n > 1.
Given n, calculate F(n).

 

Example 1:

Input: n = 2
Output: 1
Explanation: F(2) = F(1) + F(0) = 1 + 0 = 1.
Example 2:

Input: n = 3
Output: 2
Explanation: F(3) = F(2) + F(1) = 1 + 1 = 2.
Example 3:

Input: n = 4
Output: 3
Explanation: F(4) = F(3) + F(2) = 2 + 1 = 3.
 

Constraints:

0 <= n <= 30
```

```swift
Memoization or top down approach

class Solution {
    func fib(_ n: Int) -> Int {
        //
        var dp: [Int] = Array(repeating: -1, count: n + 1)
        return fibonacci(n, &dp)
    }

    func fibonacci(_ n: Int,_ dp: inout [Int]) -> Int {
        //
        if n <= 1 {
            dp[n] = n
            return n
        }
        if dp[n] != -1 {
            return dp[n]
        }
        var answer = fibonacci(n - 1, &dp) + fibonacci(n - 2, &dp)
        dp[n] = answer
        return dp[n]
    }
}
```

```swift
tabulation or bottom up approach

class Solution {
    func fib(_ n: Int) -> Int {
        //
        if n <= 1 {return n}
        var dp: [Int] = Array(repeating: -1, count: n + 1)
        dp[0] = 0
        dp[1] = 1
        for index in 2...n {
            dp[index] = dp[index - 1] + dp[index - 2]
        }
        return dp[n]
    }
}
```

**Stairs**


**Problem Description**
```swift
You are climbing a staircase and it takes A steps to reach the top.

Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?

Return the number of distinct ways modulo 1000000007
```

**Problem Constraints**

```swift
1 <= A <= 105
```

**Input Format**

```swift
The first and the only argument contains an integer A, the number of steps.
```

**Output Format**

```swift
Return an integer, representing the number of ways to reach the top.
```

**Example Input**

```swift
Input 1:

 A = 2
Input 2:

 A = 3
```

**Example Output**

```swift
Output 1:

 2
Output 2:

 3
```

**Example Explanation**
```swift
Explanation 1:

 Distinct ways to reach top: [1, 1], [2].
Explanation 2:

 Distinct ways to reach top: [1 1 1], [1 2], [2 1].
```

```swift
import Foundation

class Solution {
	func climbStairs(_ A: inout Int) -> Int {
        //
        if A <= 1 {return A}
        var dp: [Int] = Array(repeating: -1, count: A + 1)
        //
        dp[0] = 1
        dp[1] = 1
        for i in 2...A {
            dp[i] = (dp[i - 1] + dp[i - 2]) % 1000000007
        }
        //
        return dp[A]
	}
}
```




