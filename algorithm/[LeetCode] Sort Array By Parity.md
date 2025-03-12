# 📝 Sort Array By Parity

🔗 **문제 링크**: [Sort Array By Parity](https://leetcode.com/explore/learn/card/fun-with-arrays/511/in-place-operations/3260/)

## 📌 문제 설명  

Given an integer array nums, move all the even integers at the beginning of the array followed by all the odd integers.

Return any array that satisfies this condition.

---

## 💡 풀이 코드 (Kotlin)
```kotlin
fun sortArrayByParity(nums: IntArray): IntArray {
  if (nums.size == 1) return nums

  val oddArrayList = arrayListOf<Int>()
  var writeIndex = 0

  for (index in nums.indices) {
    if (nums[index] % 2 == 0) {
      nums[writeIndex] = nums[index]
      writeIndex++
    } else {
      oddArrayList.add(nums[index])
    }
  }

  oddArrayList.forEach {
    nums[writeIndex] = it
    writeIndex++
  }

  return nums
}
```

## 개선 사항
- Two-Pointer 방식으로 O(1)로 줄여보기
