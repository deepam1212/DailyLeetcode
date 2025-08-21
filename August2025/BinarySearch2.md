**Optimized Formula:**

l + ((h - l) / 2), as l + h / 2 will go out of bound in some of the cases

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

88Search an Element in Sorted & Rotated Array:**

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





