# 📝 House Robber

🔗 **문제 링크**: [House Robber](https://leetcode.com/explore/learn/card/dynamic-programming/631/strategy-for-solving-dp-problems/4148/)

## 📌 문제 설명  

You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed, the only constraint stopping you from robbing each of them is that adjacent houses have security systems connected and it will automatically contact the police if two adjacent houses were broken into on the same night.

Given an integer array nums representing the amount of money of each house, return the maximum amount of money you can rob tonight without alerting the police.

---

## 💡 풀이 코드 (Kotlin)
```kotlin
fun rob(nums: IntArray): Int {
    if (nums.size == 1) return nums.first()
    if (nums.size == 2) return nums.max()

    val dp = IntArray(nums.size)
    dp[0] = nums.first()
    dp[1] = max(nums.first(), nums[1])

    for (index in 2 until nums.size) {
        dp[index] = max(dp[index - 1], nums[index] + dp[index - 2])
    }

    return dp.max()
}
}
```

## 개선 사항
