**Given a and n, find a^n using recursion (N >= 0)**


```swift
func power(n: Int) -> Int {
    var a: Int = 2
    //
    if n == 0 {
        return 1
    }
    //
    return a * power(n: n-1)
}
print(power(n: 4))
```
T.C. = O(N)
S.C. = O(N) // **Space complexity is calculated by maximum height of the Call Stack**
**How to reduce complexity for this:**

```swift
func myPower(n: Int) -> Int {
    var a: Int = 2
    //
    if n == 0 {
        return 1
    }
    //
    if n % 2 == 0 {
        return myPower(n: n / 2) * myPower(n: n / 2)
    } else {
        return a * myPower(n: n / 2) * myPower(n: n / 2)
    }
}
print(myPower(n: 5))
```
T.C. is 2^log(n) with the base 2 with that G.P. Formula so T.C> for this is O(N) & S.C. is also O(log N)

Printing Array from 0 -> N Index
```swift
func printArray(arr: [Int], n: Int) {
    if n > 0 {
        printArray(arr: arr, n: n-1)
        print(arr[n-1])
    }
    
}
printArray(arr: [1,2,3,4,5], n: 5)
```

**Find the max Number in an Array:**

```swift
func maxOfAnArray(arr: [Int], index: Int) -> Int {
    var maxNumber: Int = arr[index]
    
    if index < arr.count - 1 {
        maxNumber = max(maxNumber, maxOfAnArray(arr: arr, index: index + 1))
    }
    //
    return maxNumber
}
print(maxOfAnArray(arr: [5,100,2,3,4,5,6], index: 0))
```

**Find the Sum of Array:**

```swift
func findSum(arr: [Int], index: Int) -> Int {
    var sum: Int = arr[index]
    //
    if index < arr.count - 1 {
        sum += findSum(arr: arr, index: index + 1)
    }
    return sum
}

print(findSum(arr: [1,2,3,4,5,100], index: 0))
```

**Find Element in an Array:**

```swift
func findElement(arr: [Int], index: Int, target: Int) -> [Int] {
    var output: [Int] = []
    //
    func find(index: Int) {
        if index == arr.count {
            return
        }
        if arr[index] == target {
            output.append(index)
        }
        //
        find(index: index + 1)
    }
    
    find(index: index)
    return output
}

print(findElement(arr: [1, 2, 3, 4, 1], index: 0, target: 1)) // Output: [0, 4]
```

**Check Palidrome:**

```swift
func checkPalindrome(str: String, start: String.Index, end: String.Index) -> Bool {
    if start < end {
        if str[start] != str[end] {
            return false
        }
        checkPalindrome(str: str, start: str.index(after: start), end: str.index(before: end))
    }
    return true
}
let str = "RADAAR"
checkPalindrome(str: str, start: str.startIndex, end: str.index(str.startIndex, offsetBy: str.count - 1))
```
