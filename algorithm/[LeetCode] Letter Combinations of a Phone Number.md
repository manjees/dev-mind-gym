# 📝 Letter Combinations of a Phone Number

🔗 **문제 링크**: [Letter Combinations of a Phone Number](https://leetcode.com/problems/letter-combinations-of-a-phone-number/description/)

## 📌 문제 설명  

Given a string containing digits from 2-9 inclusive, return all possible letter combinations that the number could represent. Return the answer in any order.

A mapping of digits to letters (just like on the telephone buttons) is given below. Note that 1 does not map to any letters.

---

## 💡 풀이 코드 (Kotlin)
```kotlin
class Solution {
    fun letterCombinations(digits: String): List<String> {
        if (digits.isEmpty()) return emptyList()

    val phoneMap = mapOf(
        '2' to "abc", '3' to "def", '4' to "ghi", '5' to "jkl",
        '6' to "mno", '7' to "pqrs", '8' to "tuv", '9' to "wxyz"
    )

    val result = mutableListOf<String>()

    fun backtrack(index: Int, path: StringBuilder) {
            if (index == digits.length) {
                result.add(path.toString())
                return
            }

            val letters = phoneMap[digits[index]] ?: return
            for (ch in letters) {
                path.append(ch)
                backtrack(index + 1, path)
                path.deleteCharAt(path.length - 1) // backtrack
            }
        }

        backtrack(0, StringBuilder())
        return result
    }
}
```

## 개선 사항
