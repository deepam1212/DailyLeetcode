**2210. Count Hills and Valleys in an Array**


You are given a 0-indexed integer array nums. An index i is part of a hill in nums if the closest non-equal neighbors of i are smaller than nums[i]. Similarly, an index i is part of a valley in nums if the closest non-equal neighbors of i are larger than nums[i]. Adjacent indices i and j are part of the same hill or valley if nums[i] == nums[j].

Note that for an index to be part of a hill or valley, it must have a non-equal neighbor on both the left and right of the index.

Return the number of hills and valleys in nums.


```swift
class Solution {
    func countHillValley(_ nums: [Int]) -> Int {
        var count: Int = 0
        //
        var iIndex: Int = 1
        var jIndex: Int = 0
        var isHill: Bool = false
        var isValley: Bool = false
        //
        while(iIndex < nums.count) {
            if nums[iIndex] > nums[jIndex] {
                isHill = true
                iIndex += 1
                jIndex += 1
                if isValley {
                    count += 1
                    isValley = false
                }
                continue
            } else if nums[iIndex] < nums[jIndex] {
                if isHill {
                   count += 1
                   isHill = false 
                }
                //
                isValley = true
                //
                iIndex += 1
                jIndex += 1
            } else {
                iIndex += 1
                jIndex += 1
            }
        }
        //
        return count
    }
}
```
