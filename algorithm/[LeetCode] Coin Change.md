# 📝 Coin Change

🔗 **문제 링크**: [Coin Change](https://leetcode.com/explore/learn/card/dynamic-programming/632/common-patterns-in-dp-problems/4111/)

## 📌 문제 설명  

You are given an integer array coins representing coins of different denominations and an integer amount representing a total amount of money.

Return the fewest number of coins that you need to make up that amount. If that amount of money cannot be made up by any combination of the coins, return -1.

You may assume that you have an infinite number of each kind of coin.

---

## 💡 풀이 코드 (Kotlin)
```kotlin
class Solution {
    fun coinChange(coins: IntArray, amount: Int): Int {
        if (amount == 0) return 0

        val dp = IntArray(amount + 1) { amount + 1 }
        dp[0] = 0

        for (i in 1..amount) {
            for (coin in coins) {
                if (i - coin >= 0) {
                    dp[i] = minOf(dp[i], dp[i - coin] + 1)
                }
            }
        }

        return if (dp[amount] > amount) -1 else dp[amount]
    }
}
```

## 개선 사항
- 

## 풀이법
- dp[i]가 금액 i를 만들기 위해 필요한 최소 동전 개수라고 정의
- dp[0] = 0 (금액 0은 동전 사용 필요 없음)
- 나머지 dp[i] (i > 0) 값은 초기에는 무한대(또는 amount+1과 같은 매우 큰 값)로 초기화
- 각 금액 i (1 ≤ i ≤ amount)에 대해, 모든 동전 coin에 대해 i - coin이 음수가 아니라면 dp[i] = min(dp[i], dp[i - coin] + 1)
- 이는 "동전 coin 하나를 추가하면 금액 i를 만들기 위해 dp[i - coin]에 1을 더한 값과 비교해서, 더 작은 값을 선택"하는 것
- dp[amount]의 값이 초기 설정한 무한대(혹은 amount+1)와 같다면, 금액을 만들 수 없는 경우이므로 -1을 반환하고 아니면 dp[amount]가 최소값