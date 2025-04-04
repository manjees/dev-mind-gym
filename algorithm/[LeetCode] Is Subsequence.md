# 📝 Is Subsequence

🔗 **문제 링크**: [Is Subsequence](https://leetcode.com/problems/is-subsequence/description/)

## 📌 문제 설명  

Given two strings s and t, return true if s is a subsequence of t, or false otherwise.

A subsequence of a string is a new string that is formed from the original string by deleting some (can be none) of the characters without disturbing the relative positions of the remaining characters. (i.e., "ace" is a subsequence of "abcde" while "aec" is not).

---

## 💡 풀이 코드 (Kotlin)
```kotlin
class Solution {
    fun isSubsequence(s: String, t: String): Boolean {
        s.ifEmpty { return true }

        val sList = s.toMutableList()

        t.forEach {
            sList.ifEmpty { return true }
            if (it.equals(sList.first())) sList.removeFirst()
        }

        return sList.isEmpty()
    }
}
```

## 개선 사항
- 
