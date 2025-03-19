# 📝 3191. Minimum Operations to Make Binary Array Elements Equal to One I

🔗 **문제 링크**: [3191. Minimum Operations to Make Binary Array Elements Equal to One I](https://leetcode.com/problems/minimum-operations-to-make-binary-array-elements-equal-to-one-i/description/?envType=daily-question&envId=2025-03-19)

## 📌 문제 설명  

You are given a binary array nums.

You can do the following operation on the array any number of times (possibly zero):
- Choose any 3 consecutive elements from the array and flip all of them.

**Flipping** an element means changing its value from 0 to 1, and from 1 to 0.

Return the minimum number of operations required to make all elements in nums equal to 1. If it is impossible, return -1.

---

## 💡 풀이 코드 (Kotlin)
```kotlin
fun minOperations(nums: IntArray): Int {
    var count = 0

    fun flip(num: Int): Int {
        return if (num == 0) 1 else 0
    }

    for (i in 0 until nums.size - 2) {
        if (nums[i] == 0 && i < nums.size - 2) {
            nums[i] = flip(nums[i])
            nums[i + 1] = flip(nums[i + 1])
            nums[i + 2] = flip(nums[i + 2])
            count ++
        }
    }

    return if (nums.any { it != 1 }) -1 else count
}
```

## 개선 사항
