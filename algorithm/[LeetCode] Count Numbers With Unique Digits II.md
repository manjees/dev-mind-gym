# 📝 Count Numbers With Unique Digits II

🔗 **문제 링크**: [Count Numbers With Unique Digits II](https://leetcode.com/problems/count-numbers-with-unique-digits-ii/description/)

## 📌 문제 설명  

Given two positive integers a and b, return the count of numbers having unique digits in the range [a, b] (inclusive).

Input: a = 80, b = 120
Output: 27
Explanation: There are 41 numbers in the range [80, 120], 27 of which have unique digits.

---

## 💡 풀이 코드 (Kotlin)
```kotlin
fun numberCount(a: Int, b: Int): Int {
    fun hasUnique(num: Int): Boolean {
        val s = num.toString()
        return s.length == s.toSet().size
    }
    return (a..b).count { hasUnique(it) }
}
```

## 개선 사항
