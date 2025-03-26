# 📝 Minimum Operations to Make a Uni-Value Grid

🔗 **문제 링크**: [Minimum Operations to Make a Uni-Value Grid](https://leetcode.com/problems/minimum-operations-to-make-a-uni-value-grid/description/?envType=daily-question&envId=2025-03-26)

## 📌 문제 설명  

You are given a 2D integer grid of size m x n and an integer x. In one operation, you can add x to or subtract x from any element in the grid.

A uni-value grid is a grid where all the elements of it are equal.

Return the minimum number of operations to make the grid uni-value. If it is not possible, return -1.

---

## 💡 풀이 코드 (Kotlin)
```kotlin
private fun minOperations(grid: Array<IntArray>, x: Int): Int {
        val array = grid.map { it.toList() }.flatten()

        val mod = array[0] % x
        if (array.any { it % x != mod }) return -1

        val sorted = array.sorted()

        val centerValue = sorted[sorted.size / 2]

        var result = 0

        for (num in sorted) {
            result += abs(num - centerValue) / x
        }

        return result
    }
```

## 개선 사항
