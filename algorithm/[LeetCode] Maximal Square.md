# 📝 Maximal Square

🔗 **문제 링크**: [Maximal Square](https://leetcode.com/explore/learn/card/dynamic-programming/631/strategy-for-solving-dp-problems/4046/)

## 📌 문제 설명  

Given an m x n binary matrix filled with 0's and 1's, find the largest square containing only 1's and return its area.

---

## 💡 풀이 코드 (Kotlin)
```kotlin
fun maximalSquare(matrix: Array<CharArray>): Int {
    if (matrix.isEmpty() || matrix[0].isEmpty()) return 0

    val height = matrix.size
    val width = matrix[0].size

    val dp = Array(height) { IntArray(width) }

    var max = 0

    for (i in 0 until height) {
        dp[i][0] = if (matrix[i][0] == '1') 1 else 0
        max = maxOf(max, dp[i][0])
    }

    for (i in 0 until width) {
        dp[0][i] = if (matrix[0][i] == '1') 1 else 0
        max = maxOf(max, dp[0][i])
    }

    for (i in 1 until height) {
        for (j in 1 until width) {
            if (matrix[i][j] == '1') {
                dp[i][j] = minOf(dp[i - 1][j], dp[i][j - 1], dp[i - 1][j - 1]) + 1
                max = maxOf(max, dp[i][j])
            } else {
                dp[i][j] = 0
            }
        }
    }

    return max * max 
}
```

## 개선 사항
