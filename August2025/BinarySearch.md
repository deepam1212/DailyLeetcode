**Binary Search**

* Searching
* Binary Search
* Problems on Binary Search

**Binary Search is keep discarding one half of your search space:**

**Question: given a sorted Array, Search an element K, if present return index else -1**

**We have to run the condition untill; low is always less than the height i.e. low <= high, Whenever the high is less than low it means that element is not in the array and we stop searhing and end the loop
```swift
func findElement() -> Int {
    //
    let arr: [Int] = [3,6,10,15,20,23,33,47,50,58]
    let k: Int = 20
    var low: Int = 0
    var high: Int = arr.count - 1
    var middle = (low + high) / 2
    //
    while(low <= high) {
        if arr[middle] < k {
            low = middle + 1
            middle = (low + high) / 2
        } else if arr[middle] > k {
            high = middle - 1
            middle = (low + high) / 2
        } else {
            return middle
        }
    }
    return -1
}
print(findElement())
```
**Find the First & Last Occurance of k & find th Frequency of K:**

```swift
func frequencyofK() -> Int {
    let arr: [Int] = [-5,-5, -3, 0, 0, 1, 5, 5, 5, 5, 5, 5, 8, 10, 10,  15]
    var k: Int = 5
    var start: Int = 0
    var end: Int = arr.count - 1
    var firstOccurance: Int = 0
    var lastOccurance: Int = 0
    var middle: Int = (start + end) / 2
    //
    while(start <= end) {
        if arr[middle] < k {
            start = middle + 1
        } else if arr[middle] > k {
            end = middle - 1
        } else {//Arr[middle] == k
            firstOccurance = middle
            end = middle - 1
        }
        //
        middle = (start + end) / 2
    }
    //
    start = 0
    end = arr.count - 1
    middle = (start + end) / 2
    //
    while(start <= end) {
        if arr[middle] < k {
            start = middle + 1
        } else if arr[middle] > k {
            end = middle - 1
        } else {//arr[middle] == k
            lastOccurance = middle
            start = middle + 1
        }
        //
        middle = (start + end) / 2
    }
    //
    return lastOccurance > 0 ? lastOccurance - firstOccurance + 1 : 0
}
print("Frequency of K is:", frequencyofK())
```
The time complexity for Finding frequency in a sorted Array is O(Log(N)) & if we do the it using Dictionary then T.C. is O(N)

**Google Question: Every Element occurs twice except for 1. Fidn the Unique Element. Note: Duplicates are adjacent to each other & array isn't necessarily sorted.**

```swift
var arr: [Int] = [8, 8, 5, 5, 9, 9, 6, 2, 2, 4, 4]
    index : =>    0  1  2  3  4  5  6  7  8  9  10
                 |________________|   |___________|
                   the first occu.      odd index  
                 comes at the even
                      index     
```

Brute force idea is Using Dictonary or XOR Operator, But hte T.C. is O(N), Better Brute Force is XOR, Binary Search can do this in O(Log N)
**For Binary Search we need that we are able to discard the Array in half, not necessarily be sorted:**
**Before the unique element: the first occurance before the unique element is even index & similarly on the right sode the first ocurance of k is odd Index:**
So if we find the first occurance on the even index then it means before that index the unique element was not present because if it present then the first occurance must be at the odd index, so we can discard the completely left part of the array & similarly if the first occurance is at the odd index then it means on the right it is not be possible to find the unique element so we can discard the right side of that array from that element:

```swift
func singleNonDuplicate(_ nums: [Int]) -> Int {
    //
    if nums.count == 1 {// Edge Case
        return nums[0]
    }
    //
    var start: Int = 0
    var end: Int = nums.count - 1
    var middle: Int = (start + end) / 2
    //
    while(start <= end) {
        //
        if nums[0] != nums[1] {// If the First Element is Unique
            return nums[0]
        } else if nums[nums.count - 1] != nums[nums.count - 2] {// Last Element is unique
            return nums[nums.count - 1]
        }
        //
        if nums[middle] == nums[middle + 1] || nums[middle] == nums[middle - 1] {
            if nums[middle] == nums[middle - 1] {// Second Occurance
                if middle % 2 == 0 {
                    end = middle - 2
                } else {
                    start = middle + 1
                }
            } else if nums[middle] == nums[middle + 1] {// First Occurance
                if middle % 2 == 0 {
                    start = middle + 2
                } else {
                    end = middle - 1
                }
            }
        } else {
            return nums[middle]
        }
        //
        middle = (start + end) / 2
        //
    }
    //
    if start == nums.count - 1 && nums[start] != nums[start - 1] {
        return nums[start]
    }
    //
    return -1
}
```

**Given array need to find the one local minima**

**Local Minima: An Element which is less than or equals to it's adjacent elements & Given array is unsorted:**
```swift
let arr: [Int] = [9, 8, 7, 3, 6, 4, 1, 3, 2]
                           _        _     _
                           Local Minima's

               9
                 \ 
                   8
                    \
                      7      
                         \
                           \              6   
                             \          /    \
                               \      /       4
                                 3              \    3
                                 L               \  /\
                                                  \/  2
                                                  1   L
                                                  L 


`L` Denotes the Local Minima

```





















