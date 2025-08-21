**Optimized Formula:**
```swift
l + ((h - l) / 2), as l + h / 2 will go out of bound in some of the cases
```
Example:

```swift
let arr = Array(repeating: 0, count: Int(Int32.max)) // big array

var l = Int32.max - 10
var h = Int32.max - 1

// Unsafe calculation
let mid1 = (l + h) / 2
print("Unsafe mid:", mid1)

// Safe calculation
let mid2 = l + (h - l) / 2
print("Safe mid:", mid2)
```

**Search an Element in Sorted & Rotated Array:**

```swift
var arr: [Int] = [8, 10, 15, 2, 4]
var arr2: [Int] = [4, 5, 6, 8, 1, 2, 3]
```

Observation

* **Individually Both the parts the Sorted**
* **element in part 1 > element in part 2**


**Graph for Array 2 is:**

```swift
             8
            / \
           /   \
          6     \
         /       \
        /         \           3
       5           \         /
      /             \       /
     /               \     2
   4                  \   /
                       \ / 
                        1
```

```swift

var arr: [Int] = [24, 30, 35, 44, 2, 6, 7, 11, 13, 18, 21, 23]
         index =   0   1   2   3  4  5  6   7   8   9  10  11
k = 18  
if arr[mid] >= arr[0] => Part 1
else arr[mid] < arr[0] => Part 2
___________________________________________________________________________
|    l    |    r    |    mid index    |     mid area    |    target area  | 
|    0    |    11   |        5        |      Part 2     |     Part 2      | low = mid + 1 
|    6    |    11   |        8        |  Now the Second Half is sorted after the First check we can directly check                               
---------------------------------------------------------------------------------


func searchSortedRotatedArray() -> Int {
    var arr: [Int] = [24, 30, 35, 44, 2, 6, 7, 11, 13, 18, 21, 23]
    var start: Int = 0
    var end: Int = arr.count - 1
    var middle: Int = start + ((end - start) / 2)
    var k: Int = 6
    //
    while(start <= end) {
        if arr[middle] == k {// If we found the Element then return the index
            return middle
        }
        //
        if k > arr[middle] && k <= arr[end] {
            start = middle + 1
        } else {
            end = middle - 1
        }
        //
        middle = start + ((end - start) / 2)
    }
    //
    return -1
}
print("searchSortedRotatedArray", searchSortedRotatedArray())
```

**Question Find SquareRoot**

```swift
N = 10, answer = 3
N = 16, answer = 4
N = 29, answer = 5, since: 5 X % = 25

N = 29

    Low       High       Middle
    0          29          15           15 * 15 > 29
    0          14           7            7 * 7 > 29
    0          6            3            3 * 3 < 29, Store 3 in answer, because 3 can be a potential answer
    4          6            5            5 * 5 < 29, store 5
    6          6            6            

func findSquareRoot() -> Int {
    let n: Int = 29
    var start: Int = 1
    var end: Int = n
    var potentialAnswer: Int = -1
    var middle = start + ((end - start) / 2)
    //
    while(start <= end) {
        if middle * middle == n {
            return middle
        } else if middle * middle > n {
            end = middle - 1
        } else {
            potentialAnswer = middle
            start = middle + 1
        }
        //
        middle = start + ((end - start) / 2)
    }
    //
    return potentialAnswer
}
print("findSquareRoot", findSquareRoot())

As O(Log N) is less T.C. than O(SQRT(N)), So we solved this using Binary Search instead of Brute Force Approach
```

**Question: Median of 2 Sorted Array**

**Median is For Odd total count of array the Middle Element is the Median for any Array & for even count the mediam if arr[middle] + arr[middle + 1] / 2**

```swift
A: [Int] = [1,2,3]
B: [Int] = [4,5]

So the total array would be: [1,2,3,4,5] & the Mediam is the middle element of an array that is 3
```






