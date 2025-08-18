**Fibonacci Serioes:**


```swift
// This is with the Recursion
func fibonacci(n: Int) -> Int {
  if n <= 1 {
    return n
  }
  //
  return fibonacci(n: n - 1) + fibonacci(n: n - 2)
}
```
**T.C. of Fibonacci Series is 2^N for Recursion, because for one call we are creating 2 functions**

```swift
                     f(5)
                   /     \ 
                  /        \
                f(3)       f(4)
                / \         /  \
               /   \       /     \
             f(2)  f(1)  f(2)    f(3)

S.C. is O(N), because if we look closely in a Fibonacci tree, it is as close to N
```

**Property to Apply D.P.**

* Any of the Problem can be formed using sub-problem
    * Like in Fibonacci Series, we can find the answer of f(4), using f(4) & f(3), so f(5) is nothing but the answer of f(4) + f(3).
    * Overlapping Subproblems, There are repeated sub-problems, like in fibonacci series, we have f(3) with finding fum for 5 & f(3) is also there when finding sum of f(4),


**Note: So for a question to be solved via D.P. 1 & 2 must be true**












