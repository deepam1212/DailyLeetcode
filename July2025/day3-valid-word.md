# 3136. Valid Word

> [Leetcode Link](https://leetcode.com/problems/valid-word/)  
> Difficulty: Easy  
> Tags: String, Validation, Swift

---

### 🧩 Problem Statement

A word is **valid** if:

1. It contains **only alphanumeric characters**.
2. It contains **at least one vowel** (`a, e, i, o, u`) and **at least one consonant**.
3. Its length is **at least 3**.

Return `true` if the word is valid; otherwise, return `false`.

---

### ✅ My Swift Solutions

```swift
// ❌ Unoptimized Version (Initially Accepted)
class Solution {
    func isValid(_ word: String) -> Bool {
        if word.count < 3 {
            return false
        }
        //
        var isValid: Bool = true
        var dictVowel: [String: Bool] = ["a": true, "e": true, "i": true, "o": true, "u": true]
        var dictConsonent: [String: Bool] = ["b": true, "c": true, "d": true, "f": true, "g": true, "h": true, "j": true, "k": true, "l": true, "m": true, "n": true, "p": true, "q": true, "r": true, "s": true, "t": true, "v": true, "w": true, "x": true, "y": true, "z": true]
        var dictNumber: [Int: Bool] = [0: true, 1: true, 2: true, 3: true, 4: true, 5: true, 6: true, 7: true, 8: true, 9: true]
        //
        var isVowelFound: Bool = false
        var isConsonentFound: Bool = false
        //
        for char in word {
            if let _ = dictVowel[char.lowercased()] {
                isVowelFound = true
            } else if let _ = dictConsonent[char.lowercased()] {
                isConsonentFound = true
            } else if let value = Float("\(char)"), let _ = dictNumber[Int(value)] {
                // valid digit
            } else {
                return false
            }
        }
        return isVowelFound && isConsonentFound
    }
}

// ✅ Optimized Version (Cleaner & Efficient)
class Solution {
    func isValid(_ word: String) -> Bool {
        if word.count < 3 {
            return false
        }

        var hasVowel = false
        var hasConsonant = false

        for char in word.lowercased() {
            if !char.isLetter && !char.isNumber {
                return false
            }

            if char.isLetter {
                if "aeiou".contains(char) {
                    hasVowel = true
                } else {
                    hasConsonant = true
                }
            }
        }

        return hasVowel && hasConsonant
    }
}
```
