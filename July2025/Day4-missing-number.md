# 268. Missing Number

## Problem Statement

Given an array `nums` containing `n` distinct numbers in the range `[0, n]`, return the only number in the range that is missing from the array.

### Example 1:

Input: nums = [3,0,1]  
Output: 2  

### Example 2:

Input: nums = [0,1]  
Output: 2  

### Example 3:

Input: nums = [9,6,4,2,3,5,7,0,1]  
Output: 8  

### Constraints:

- `n == nums.length`
- `1 <= n <= 10⁴`
- `0 <= nums[i] <= n`
- All the numbers of `nums` are unique.

---

## 🔸 Naive Solution (Using Set)

Time Complexity: `O(n)`  
Space Complexity: `O(n)`

```swift
class Solution {
    func missingNumber(_ nums: [Int]) -> Int {
        let n = nums.count
        let set = Set(nums)
        for i in 0...n {
            if !set.contains(i) {
                return i
            }
        }
        return -1
    }
}
```

Optimized Solution (Math Formula)
Use the formula of sum of first n natural numbers:
Sum = n * (n + 1) / 2

Time Complexity: O(n)
Space Complexity: O(1)
```swift
class Solution {
    func missingNumber(_ nums: [Int]) -> Int {
        let n = nums.count
        let expectedSum = n * (n + 1) / 2
        let actualSum = nums.reduce(0, +)
        return expectedSum - actualSum
    }
}
```
