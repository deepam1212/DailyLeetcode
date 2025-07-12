# Day 1 - Two Sum

## Problem
Given an array of integers `nums` and an integer `target`, return indices of the two numbers such that they add up to `target`.

## Code
```swift
func twoSum(_ nums: [Int], _ target: Int) -> [Int] {
    var map = [Int: Int]()
    for (i, num) in nums.enumerated() {
        if let index = map[target - num] {
            return [index, i]
        }
        map[num] = i
    }
    return []
}
```
Complexity
Time: O(n)
Space: O(n)

Notes
Used a hashmap to store visited values
