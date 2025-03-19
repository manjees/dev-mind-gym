# 📝 Longest Common Subsequence

🔗 **문제 링크**: [Longest Common Subsequence](https://leetcode.com/explore/learn/card/dynamic-programming/631/strategy-for-solving-dp-problems/4045/)

## 📌 문제 설명  

Given two strings text1 and text2, return the length of their longest common subsequence. If there is no common subsequence, return 0.

A subsequence of a string is a new string generated from the original string with some characters (can be none) deleted without changing the relative order of the remaining characters.

- For example, "ace" is a subsequence of "abcde".

A common subsequence of two strings is a subsequence that is common to both strings.

---

## 💡 풀이 코드 (Kotlin)
```kotlin
fun longestCommonSubsequence(text1: String, text2: String): Int {
    val text1Length = text1.length
    val text2Length = text2.length

    val dp = Array(text1Length + 1) { IntArray(text2Length + 1) }

    for (i in 1..text1Length) {
        for (j in 1..text2Length) {
            dp[i][j] = if (text1[i-1] == text2[j-1]) {
                dp[i - 1][j - 1] + 1
            } else {
                maxOf(dp[i - 1][j], dp[i][j - 1])
            }
        }
    }

    return dp[text1Length][text2Length]
}
```

## 개선 사항
