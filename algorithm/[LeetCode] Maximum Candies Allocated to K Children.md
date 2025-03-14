# 📝 Maximum Candies Allocated to K Children

🔗 **문제 링크**: [Maximum Candies Allocated to K Children](https://leetcode.com/problems/maximum-candies-allocated-to-k-children/description/?envType=daily-question&envId=2025-03-14)

## 📌 문제 설명  

You are given a 0-indexed integer array candies. Each element in the array denotes a pile of candies of size candies[i]. You can divide each pile into any number of sub piles, but you cannot merge two piles together.

You are also given an integer k. You should allocate piles of candies to k children such that each child gets the same number of candies. Each child can be allocated candies from only one pile of candies and some piles of candies may go unused.

Return the maximum number of candies each child can get.

---

## 💡 풀이 코드 (Kotlin)
```kotlin
private fun maximumCandies(candies: IntArray, k: Long): Int {
        val totalCandies = candies.fold(0L) { acc, num -> acc + num }
        if (totalCandies < k) return 0

        var left = 1
        var right = candies.maxOrNull() ?: 0
        var result = 0

        while (left <= right) {
            val mid = left + (right - left) / 2

            var count = 0L
            for (candy in candies) {
                count += candy / mid
                if (count >= k) break
            }

            if (count >= k) {
                result = mid
                left = mid + 1
            } else {
                right = mid - 1
            }
        }

        return result
    }
```

## 개선 사항
- 이진 탐색 로직 간소화