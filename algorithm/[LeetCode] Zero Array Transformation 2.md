# 📝 Zero Array Transformation 2

🔗 **문제 링크**: [Zero Array Transformation 2](https://leetcode.com/problems/zero-array-transformation-ii/description/?envType=daily-question&envId=2025-03-13)

## 📌 문제 설명  

You are given an integer array nums of length n and a 2D array queries where queries[i] = [li, ri, vali].

Each queries[i] represents the following action on nums:

Decrement the value at each index in the range [li, ri] in nums by at most vali.
The amount by which each value is decremented can be chosen independently for each index.
A Zero Array is an array with all its elements equal to 0.

Return the minimum possible non-negative value of k, such that after processing the first k queries in sequence, nums becomes a Zero Array. If no such k exists, return -1.

---

## 💡 풀이 코드 (Kotlin)
```kotlin
fun rob(nums: IntArray): Int {
    fun minZeroArray(nums: IntArray, queries: Array<IntArray>): Int {
    if (nums.all { it == 0 }) return 0

    val n = nums.size
    val totalQueries = queries.size

    fun feasible(k: Int): Boolean {
        val diff = IntArray(n + 1)  
        for (i in 0 until k) {
            val (l, r, v) = queries[i]
            diff[l] += v
            if (r + 1 < diff.size) {
                diff[r + 1] -= v
            }
        }
        var current = 0
        for (i in 0 until n) {
            current += diff[i]
            if (current < nums[i]) return false
        }
        return true
    }

    var low = 1
    var high = totalQueries
    var ans = -1
    while (low <= high) {
        val mid = (low + high) / 2
        if (feasible(mid)) {
            ans = mid
            high = mid - 1
        } else {
            low = mid + 1
        }
    }
    return ans
    }
}
```

## 개선 사항
