**Binary Search**

* Searching
* Binary Search
* Problems on Binary Search

**Binary Search is keep discarding one half of your search space:**

**Question: given a sorted Array, Search an element K, if present return index else -1**

**We have to run the condition untill; low is always less than the height i.e. low <= high, Ehenever the high is less than low it means that element is not in the array and we stop searhing and end the loop
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





