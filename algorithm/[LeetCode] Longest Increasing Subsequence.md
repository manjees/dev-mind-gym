# 📝 Word Break

🔗 **문제 링크**: [Longest Increasing Subsequence](https://leetcode.com/explore/learn/card/dynamic-programming/632/common-patterns-in-dp-problems/4114/)

## 📌 문제 설명  

Given an integer array nums, return the length of the longest strictly increasing subsequence.

---

## 💡 풀이 코드 (Kotlin)
```kotlin
class Solution {
    fun lengthOfLIS(nums: IntArray): Int {
        val n = nums.size
        val dp = IntArray(n) { 1 }
        
        for (i in 1 until n) {
            for (j in 0 until i) {
                if (nums[j] < nums[i]) {
                    dp[i] = maxOf(dp[i], dp[j] + 1)
                }
            }
        }

        return dp.maxOrNull() ?: 0
    }
}
```

## 개선 사항
- 이진 탐색으로 시간 복잡도 줄여보기

## 풀이법
- 해당 인덱스까지의 최대 값을 구해서 넣어줌
- 값이 제일 큰 곳이 제일 긴 부분