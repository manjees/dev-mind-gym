# 📝 House Robber IV

🔗 **문제 링크**: [House Robber IV](https://leetcode.com/problems/house-robber-iv/submissions/1574444412/?envType=daily-question&envId=2025-03-15)

## 📌 문제 설명  

There are several consecutive houses along a street, each of which has some money inside. There is also a robber, who wants to steal money from the homes, but he refuses to steal from adjacent homes.

The capability of the robber is the maximum amount of money he steals from one house of all the houses he robbed.

You are given an integer array nums representing how much money is stashed in each house. More formally, the ith house from the left has nums[i] dollars.

You are also given an integer k, representing the minimum number of houses the robber will steal from. It is always possible to steal at least k houses.

Return the minimum capability of the robber out of all the possible ways to steal at least k houses.

---

## 💡 풀이 코드 (Kotlin)
```kotlin
fun minCapability(nums: IntArray, k: Int): Int {
        var left = nums.min()
        var right = nums.max()

        fun canRob(capability: Int): Boolean {
            var count = 0
            var i = 0
            while (i < nums.size) {
                if (nums[i] <= capability) {
                    count++
                    i++
                }
                i++
            }
            return count >= k
        }

        while (left < right) {
            val mid = (left + right) / 2
            if (canRob(mid)) right = mid
            else left = mid + 1
        }

        return left
    }
```

## 개선 사항
