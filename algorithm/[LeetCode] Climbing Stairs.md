# 📝 Climbing Stairs

🔗 **문제 링크**: [Climbing Stairs](https://leetcode.com/problems/climbing-stairs/description/)

## 📌 문제 설명  

You are climbing a staircase. It takes n steps to reach the top.

Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?

---

## 💡 풀이 코드 (Kotlin)
```kotlin
private fun climbStairs(n: Int): Int {
    val dp = IntArray(n + 1)
    dp[0] = 1
    dp[1] = 1

    for (i in 2..n) {
        dp[i] = dp[i - 1] + dp[i - 2]
    }

    return dp[n]
}
```

## 개선 사항
