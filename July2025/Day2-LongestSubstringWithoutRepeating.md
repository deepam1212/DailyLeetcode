# 🚀 Day 2 - Longest Substring Without Repeating Characters

## 🧩 Problem Statement

Given a string `s`, find the length of the longest substring without repeating characters.

---

## 🔢 Examples

| Input       | Output | Explanation                  |
|-------------|--------|------------------------------|
| `"abcabcbb"`| 3      | Longest: `"abc"`             |
| `"AaaA"`    | 2      | Longest: `"Aa"` or `"aA"`    |
| `"bbbb"`    | 1      | Longest: `"b"`               |
| `"pwwkew"`  | 3      | Longest: `"wke"`             |

---

## 💡 Approach

We use a **sliding window + Set** to track characters and ensure no duplicates in the current window.

- If a character is **not in the set**, expand the window (move `end`).
- If a character **already exists**, shrink from the `start` until it’s removed.
- Track and update the `maxLength`.

---

## 🧠 Swift Solution

```swift
func lengthOfSubString(str: String) {
    var start = str.startIndex
    var end = start
    var seen: Set<Character> = []
    var maxLength: Int = 0

    while end < str.endIndex {
        let char = str[end]

        if !seen.contains(char) {
            seen.insert(char)
            let size = str.distance(from: start, to: end) + 1
            print("size", size)
            maxLength = max(maxLength, size)
            end = str.index(after: end)
        } else {
            seen.remove(str[start])
            start = str.index(after: start)
        }
    }

    print("MaxLength is : \(maxLength)")
}
```
