# 📝 Maximum Score from Performing Multiplication Operations

🔗 **문제 링크**: [Maximum Score from Performing Multiplication Operations](https://leetcode.com/explore/learn/card/dynamic-programming/631/strategy-for-solving-dp-problems/4146/)

## 📌 문제 설명  

You are given two 0-indexed integer arrays nums and multipliers of size n and m respectively, where n >= m.

You begin with a score of 0. You want to perform exactly m operations. On the ith operation (0-indexed) you will:

- Choose one integer x from either the start or the end of the array nums.
- Add multipliers[i] * x to your score.
>Note that multipliers[0] corresponds to the first operation, multipliers[1] to the second operation, and so on.
- Remove x from nums.

Return the maximum score after performing m operations.

---

## 💡 풀이 코드 (Kotlin)
```kotlin
fun maximumScore(nums: IntArray, multipliers: IntArray): Int {
    val n = nums.size
    val m = multipliers.size
    val dp = Array(m + 1) { IntArray(m + 1) }

    for (i in m - 1 downTo 0) {
        for (left in i downTo 0) {
            val right = n - 1 - (i - left)

            dp[i][left] = maxOf(
                multipliers[i] * nums[left] + dp[i + 1][left + 1],
                multipliers[i] * nums[right] + dp[i + 1][left]
            )
        }
    }
    return dp[0][0]
}
```

## 개선 사항
