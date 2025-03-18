# 📝 Longest Nice Subarray

🔗 **문제 링크**: [Longest Nice Subarray](https://leetcode.com/problems/longest-nice-subarray/description/?envType=daily-question&envId=2025-03-18)

## 📌 문제 설명  

You are given an array nums consisting of positive integers.

We call a subarray of nums nice if the bitwise AND of every pair of elements that are in different positions in the subarray is equal to 0.

Return the length of the longest nice subarray.

A subarray is a contiguous part of an array.

Note that subarrays of length 1 are always considered nice.

---

## 💡 풀이 코드 (Kotlin)
```kotlin
fun longestNiceSubarray(nums: IntArray): Int {
    var left = 0
    var orSum = 0
    var maxLen = 0

    for (right in nums.indices) {
        while ((orSum and nums[right]) != 0) {
            orSum = orSum xor nums[left]
            left++
        }
        orSum = orSum or nums[right]
        maxLen = maxOf(maxLen, right - left + 1)
    }

    return maxLen
}
```

## 개선 사항
