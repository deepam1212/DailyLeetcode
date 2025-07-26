**Why Recursion:** 
* Pre-requisite of backtracking, Trees, D.p. Graphs, LinkedList

**Sorting Algo:**
Merge Sort, Quick Sort

**What is Recursion:** 
Function calling itself, breaking a problem in to subproblem/ smaller parts then that is called recursion

**Sum of First N Natural Numners:**

1+2+3+4+5....N
```swift
func sumOfNNatural(n: Int) -> Int {
    if n <= 0 {
        return 0
    }
    return n + sumOfNNatural(n: n - 1)
}
sumOfNNatural(n: 5)
```

First it will run for 5, then for 4, 3, 2, 1 and for 0 it is returning 0 directly so no recursive call for n = 0 and thus it stops at 0

**Factorial of a Number N**

```swift
func factorial(n: Int) -> Int {
    if n > 1 {
        return n * factorial(n: n - 1)
    } else {
        return 1
    }
}
print("factorial: \(factorial(n: 5))")
```

So for 5 it works as return 5 * factorial(5-1), then it runs for 4,3,2 respectively, and for 1 it does not run the recursive call, so it stops at here

Recursion works using a stack—specifically, the call stack of the system.

Here's how it works:
When a function calls itself recursively:

The current function call is pushed onto the call stack.

Each recursive call keeps adding a new frame to the stack.

Once the base condition is met, the calls start returning one by one.

As each call returns, its frame is popped off the stack.

**Print Increasing order of N Natural:**
```swift
func printIncreasing(n: Int) {
    if n == 0 { return }
    printIncreasing(n: n - 1)
    print(n)
}
```
**Time Complexity: O(Number of function calls * Time taken by each function calls)**

Multiplying like operations would take O(1)
**Space Complexity in Recursion is Maximum Depth of Recursion** O(N) for Factorial

|           |
|           | So this is stack each & every number is added to the Call Stack
|           |
|           | 
|___________|

**Ohhhh kkkkkkk it means for n = 5**

* It will add 5 in a call stack, then add 4 on the top of it then 3 on it then 2 then 1 and for n = 0 the base condition hits
* Then as stack removes from the top it will print 1,2,3,4,5
  
**Nth Fibonacci**

**F.B. = [0,1,1,2,3,5,8,13,21,34,55]**

```swift
func generateFibonacci(n: Int) -> Int {
    if n == 0 {
        return 0
    }
    if n == 1 {
        return 1
    }
    return generateFibonacci(n: n - 1) + generateFibonacci(n: n - 2)
}
generateFibonacci(n: 11)
```

Every Function is calling 2 other functions
n-1 + n-2

and for every n-1 it cals 2 other functions
n-1 & n-2

                        F.B.(N)            Level 0
                        /      \
                       /        \
                     N-1        N-2        Level 1
                    /  \
                   /    \
                  N-1   N-2                Level 2
                                                             n
So this is a G.P. Sum of (N+1) terms in G.P.           a * (r)            N+1
                                                   --------------- => 1 (2      -      1) / 2-1 =? 2^N
                                                        r - 1

T.C. = O(2^N)
S.C. = N
**To Print all the Fibonacci Numbers up to N, Use this:**

```swift
func printAllFibonacciNumbers(n: Int) {
    var i: Int = 0
    var firstNumber: Int = 0
    var secondNumber: Int = 1
    //
    while(i <= n) {
        if i == 0 {
            print(i)
        } else if i == 1 {
            print(i)
        } else {
            print(firstNumber + secondNumber)
            let temp = secondNumber
            secondNumber = firstNumber + secondNumber
            firstNumber = temp
        }
        //
        i += 1
    }
}

printAllFibonacciNumbers(n: 11)
```
