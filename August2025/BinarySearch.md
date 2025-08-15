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




