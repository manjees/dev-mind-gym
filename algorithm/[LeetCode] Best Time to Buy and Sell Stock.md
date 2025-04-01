# 📝 Best Time to Buy and Sell Stock

🔗 **문제 링크**: [Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/description/)

## 📌 문제 설명  

You are given an array prices where prices[i] is the price of a given stock on the ith day.

You want to maximize your profit by choosing a single day to buy one stock and choosing a different day in the future to sell that stock.

Return the maximum profit you can achieve from this transaction. If you cannot achieve any profit, return 0.

---

## 💡 풀이 코드 (Kotlin)
```kotlin
 fun maxProfit(prices: IntArray): Int {
        var minPrice = Int.MAX_VALUE
        var maxProfit = 0

        for (price in prices) {
            minPrice = minOf(minPrice, price)
            maxProfit = maxOf(maxProfit, price - minPrice)
        }

        return maxProfit
    }
```

## 개선 사항
