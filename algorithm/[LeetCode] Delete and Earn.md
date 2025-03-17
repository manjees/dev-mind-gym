# 📝 Delete and Earn

🔗 **문제 링크**: [Delete and Earn](https://leetcode.com/explore/learn/card/dynamic-programming/631/strategy-for-solving-dp-problems/4147/)

## 📌 문제 설명  

You are given an integer array nums. You want to maximize the number of points you get by performing the following operation any number of times:

Pick any nums[i] and delete it to earn nums[i] points. Afterwards, you must delete every element equal to nums[i] - 1 and every element equal to nums[i] + 1.
Return the maximum number of points you can earn by applying the above operation some number of times.

---

## 💡 풀이 코드 (Kotlin)
```kotlin
fun deleteAndEarn(nums: IntArray): Int {
    if (nums.isEmpty()) return 0

    val maxNum = nums.max()
    val points = IntArray(maxNum + 1)

    for (num in nums) {
        points[num] += num
    }

    var prev = 0
    var curr = 0

    for (i in points.indices) {
        val newCurr = max(curr, prev + points[i])
        prev = curr
        curr = newCurr
    }

    return curr
}
```

## 개선 사항
