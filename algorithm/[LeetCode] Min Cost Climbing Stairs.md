# 📝 Min Cost Climbing Stairs

🔗 **문제 링크**: [Min Cost Climbing Stairs](https://leetcode.com/explore/learn/card/dynamic-programming/631/strategy-for-solving-dp-problems/4040/)

## 📌 문제 설명  

You are given an integer array cost where cost[i] is the cost of ith step on a staircase. Once you pay the cost, you can either climb one or two steps.

You can either start from the step with index 0, or the step with index 1.

Return the minimum cost to reach the top of the floor.

---

## 💡 풀이 코드 (Kotlin)
```kotlin
fun minCostClimbingStairs(cost: IntArray): Int {
            val n = cost.size
            if (n == 2) return min(cost[0], cost[1])
    
            val dp = IntArray(n + 1) { 0 }
    
            for (i in 2..n) {
                dp[i] = min(dp[i - 1] + cost[i - 1], dp[i - 2] + cost[i - 2])
            }
    
            return dp[n]
    }
```

## 개선 사항
