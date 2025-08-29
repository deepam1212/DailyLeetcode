**Count Sort & Merge Sort**


**Question find the smallest number that can be formed by rearranging the digits of the given number in an array. return the smallest number in the form of an Array**

```swift
var arr: [Int] = [6, 3, 4, 2, 7, 2, 1]// sort it in assending order, so the answer will be 1223467
var arr2: [Int] = [4, 2, 7, 3, 9, 0]// Smallest Number which can be formed  from this Array
```

**Count sort is storing the frequency of an input array in an array & then rearranging the output array as the frequency, as indexes are the elements and the element at that index is the frequency of that element**
```swift
var arr: [Int] = [1, 2, 3, 4, 5, 6, 7, 8, 9, 100, 11, 31, 33]
count[0]  = 0
count[1]  = 1   (since 1 appears once)
count[2]  = 1
count[3]  = 1
...
count[9]  = 1
count[10] = 0
count[11] = 1
...
count[31] = 1
count[33] = 1
...
count[100] = 1
```

```swift
// How count sort works
func countSort() -> [Int] {
    var arr: [Int] = [2, 1, 2, 3, 4, 100, 5, 6, 7, 8, 9, 100, 11, 31, 33]
    //
    var maxElement: Int = Int.min
    for item in arr {
        if item > maxElement {
            maxElement = item
        }
    }
    //
    var frequencyArray: [Int] = Array(repeating: 0, count: maxElement + 1)
    //
    for item in arr {
        frequencyArray[item] = frequencyArray[item] + 1
    }
    //
    var outputArray: [Int] = []
    //
    for (index, item) in frequencyArray.enumerated() where item > 0 {
        var number: Int = 0
        while(number < item) {
            outputArray.append(index)
            number += 1
        }
    }
    //
    return outputArray
}
print("Count Sort", countSort())
```

```swift
T.C. of Count Sort is O(n log n) & S.C. is O(N), where N is the output array space in the space complexity
```


**For handling the negative integers**



```swift
func countSort() -> [Int] {
    var arr: [Int] = [2, -5, 1, 2, 3, -1, 4, 100, 5, 6, -3, 7, 8, 9, 100, 11, 31, 33]

    // 1. Find min & max
    var minElement = Int.max
    var maxElement = Int.min
    for item in arr {
        minElement = min(minElement, item)// finding the smallest number in an Array
        maxElement = max(maxElement, item)// finding the largest number in Array
    }

    // 2. Create frequency array (shifted by minElement) (Formula is b - a + 1)
    let range = maxElement - minElement + 1
    var frequencyArray = Array(repeating: 0, count: range)
    // inx = A[i] - min, so A[i] = inx = min
    for item in arr {
        frequencyArray[item - minElement] += 1// If we subtrack the negative numbers, then i can get the 0 position
    }

    // 3. Build output array
    var outputArray: [Int] = []
    for (index, count) in frequencyArray.enumerated() where count > 0 {
        for _ in 0..<count {
            outputArray.append(index + minElement)  // shift back
        }
    }

    return outputArray
}

print("Count Sort:", countSort())
```

**Count sort works well when the range of the array is small. as it wont work for 10 ^ 9, because then we have to create the frequency array with 10 ^ 9 + 1, it will only work for 10 ^ 5 to 10 ^ 6**

**To calculate Range we have b - a + 1, Which we use in Count Sort to hande the negative numbers**


**Merge Sort**

**Merge Two sorted Arrays**
```swift
// Brute Force
func mergeTwoSortedArray() {
    var a: [Int] = [2, 4, 7, 8, 12]
    var b: [Int] = [3, 5, 6, 7]
    var aIndex: Int = 0
    var bIndex: Int = 0
    var outputArray: [Int] = []
    //
    while(aIndex < a.count && bIndex < b.count) {
        //
        if a[aIndex] < b[bIndex] {
            if aIndex < a.count {
                outputArray.append(a[aIndex])
                aIndex += 1
            }
        } else {
            if bIndex < b.count {
                outputArray.append(b[bIndex])
                bIndex += 1
            }
        }
    }
    //
    while(aIndex < a.count) {// if any element in a is left
        outputArray.append(a[aIndex])
        aIndex += 1
    }
    //
    while(bIndex < b.count) {// If any element in b is left
        outputArray.append(b[bIndex])
        bIndex += 1
    }
    //
    print("OutputArray: \(outputArray)")
}
mergeTwoSortedArray()
//OutputArray: [2, 3, 4, 5, 6, 7, 7, 8, 12]
T.C. O(a.count + b.count), S.C. O(a.count + b.count)
```

**Merge sort is a Recursive Algorithm**


**Recursion is nothing but Divide & Conquer**
```swift

                [3, 10, 6, 8, 15, 2, 12, 18, 17]
                          /        \      
                        /            \
                      /                \
                    /                    \
            [3, 10, 6, 8, 15]       [2, 12, 18, 17]
                /     \                   /  \
              /        \                 /     \
        [3, 10, 6]     [8, 15]        [2, 12]   [18, 17]
            /  \   
     [3, 10]   [6]
        / \
      [3] [10]// Base Case

To Find the middle element we have a formula (low + (high - low / 2)) or ((low + high) / 2)
```

**Merge Sort**

```swift
func mergeSort(arr: [Int], low: Int, high: Int) -> [Int] {
    if low == high {// Base Case, return a single size Array
        return [arr[low]]
    }
    var middle: Int = low + ((high - low) / 2)
    let left = mergeSort(arr: arr, low: low, high: middle)
    let right = mergeSort(arr: arr, low: middle + 1, high: high)
    func merge(leftArr: [Int], rightArr: [Int]) -> [Int] {
        var lIndex: Int = 0
        var rIndex: Int = 0
        //
        var outputArr: [Int] = []
        //
        while(lIndex < leftArr.count && rIndex < rightArr.count) {
            if leftArr[lIndex] < rightArr[rIndex] {
                outputArr.append(leftArr[lIndex])
                lIndex += 1
            } else {
                outputArr.append(rightArr[rIndex])
                rIndex += 1
            }
        }
        //
        while(lIndex < leftArr.count) {
            outputArr.append(leftArr[lIndex])
            lIndex += 1
        }
        //
        while(rIndex < rightArr.count) {
            outputArr.append(rightArr[rIndex])
            rIndex += 1
        }
        //
        return outputArr
    }
    var outputArr: [Int] = merge(leftArr: left, rightArr: right)
    return outputArr
}
let arr: [Int] = [3, 10, 3, 6, 8, 15, 2, 12, 18, 17]
print("Merge Sort", mergeSort(arr: arr, low: 0, high: arr.count - 1))
// Merge Sort [2, 3, 3, 6, 8, 10, 12, 15, 17, 18]
T.C. O(N Log N), S.C. O(N), as the height of the recursion is Log N, so it must be Log N, but we are also merging so N + Log N, => O(N)
T.C. O(Number of Functyions calls * time taken by each level)
       We divide array in to 2    * We are merging them, N Times => O(N * Log N), & arr.sort() has O(N * Log N) & .sort() uses Merge Sort Algorithm
            N / 2, N / 2          * N / 2 * N / 2  
            N / 4, N / 4
        we do this for Log N times
```




















