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
        minElement = min(minElement, item)
        maxElement = max(maxElement, item)
    }

    // 2. Create frequency array (shifted by minElement)
    let range = maxElement - minElement + 1
    var frequencyArray = Array(repeating: 0, count: range)

    for item in arr {
        frequencyArray[item - minElement] += 1
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



























