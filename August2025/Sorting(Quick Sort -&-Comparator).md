**Pivot Partition**


**Question: Given an Int Array, consider first element as pivot, rearrange the elements such that for all i :**
* **if A[i] <= p then it should be on the left side.**
* **if A[i] > p then it should be on the right side**
```swift
var arr: [Int] = [54, 26, 93, 17, 77, 31, 44, 55, 20], Pivot is the First Element 
```

**In this we have to select an pivot element then check if all the elements before pivot is smaller & all the elements after pivot is greater than pivot**
```swift
func quickSort() {
    var arr: [Int] = [54, 26, 93, 17, 77, 31, 44, 55, 20]
    let pivot: Int = 77
    var i: Int = 0
    var j: Int = 1
    while(j < arr.count - 1) {
        if arr[j] < pivot {
            let temp = arr[j]
            arr[j] = arr[i]
            arr[i] = temp
            i += 1
        }
        j += 1
    }
    //
    let temp = arr[j]
    arr[j] = arr[i]
    arr[i] = temp
    //
    print("Quick Sort", arr)
}

quickSort(), T.C. O(N), S.C. O(1), so if we do this by sorting it work with O(n log n), we have done it in O(n) which is definately better
```

**Quick Sort: Sorting based on the Pivot Element(It is also an example of Divide & conquer approach)**


















































