**Very fameous Interview Questions on Binary Search**


```swift
Space Complexity in Binary Search is O(Log N), Because the maximum space of maximum elemtn which we can have in a call stack are Log N
```
**Question: Painters Partition:**


Input:

* A board cn only be painted by 1 Painter
* A Painter can only paint boards placed next to each other(i.e. contineous segment)

* Find minimum time to paint all boads if `P` painters are available

```swift
              ____________________        _____________            _____________________________        _____      ______________________________________
N = 5        |                    |      |             |          |                             |      |     |    |                                      |
              --------------------        -------------            -----------------------------        -----      -------------------------------------- 
                      5                          3                               6                        1                           9

Time taken to paint the Board = [5, 3, 6, 1, 9]
```


```swift
func minTimeToPaint(arr: [Int], painters: Int) -> Int {
    var minTime: Int = 0
    var maxTime: Int = 0
    //
    for item in arr {
        maxTime += item // As if there is only one painter is there
        minTime = max(minTime, item)// it is only finding the max element in an array, we can say like if arr[i] > minTime, then minTime = arr[i]
    }
    //
    var middle: Int = (minTime + ((maxTime - minTime) / 2))
    var answer: Int = 0
    //
    while(minTime <= maxTime) {
        if checkTime(time: middle, totalPainters: painters, arr: arr) {// If all Assigned painters can paint the board in given time, then we have to check if lower time is possible or not
            maxTime = middle - 1
            answer = middle
        } else {
            minTime = middle + 1
        }
        //
        middle = (minTime + ((maxTime - minTime) / 2))
    }
    //
    return answer
}

func checkTime(time: Int, totalPainters: Int, arr: [Int]) -> Bool {
    //
    var painters: Int = 1
    var myTime: Int = 0
    //
    for item in arr {
        myTime += item
        //
        if myTime > time {
            painters += 1
            myTime = item
        }
    }
    //
    return painters <= totalPainters
}

print("Total Time required by painters to Paint is: ", minTimeToPaint(arr: [5, 3, 6, 1, 9], painters: 2))
```

```swift
T.C. is O(N * log(maxTime - minTime))
```


















