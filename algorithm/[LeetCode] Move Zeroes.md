# 📝 Move Zeroes

🔗 **문제 링크**: [Move Zeroes](https://leetcode.com/explore/learn/card/fun-with-arrays/511/in-place-operations/3157/)

## 📌 문제 설명  

Given an integer array nums, move all 0's to the end of it while maintaining the relative order of the non-zero elements.

> Note that you must do this in-place without making a copy of the array.
> 🗒️ 두 포인터(Two-Pointer) 기법

---

## 💡 풀이 코드 (Kotlin)
```kotlin
fun moveZeroes(nums: IntArray): Unit {
  var writeIndex = 0

  for (readIndex in nums.indices) {
    if (nums[readIndex] != 0) {
      nums[writeIndex] = nums[readIndex]
      writeIndex++
    }
  }

  for (i in writeIndex until nums.size) {
    nums[i] = 0
  }
}
```

## 개선 사항
