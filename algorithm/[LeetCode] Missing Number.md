# 📝 Missing Number

🔗 **문제 링크**: [Missing Number](https://leetcode.com/problems/missing-number/description/)

## 📌 문제 설명  

Given an array nums containing n distinct numbers in the range [0, n], return the only number in the range that is missing from the array.

---

## 💡 풀이 코드 (Kotlin)
```kotlin
 class Solution {
    fun missingNumber(nums: IntArray): Int {
        val max = nums.max()
        var result = -1

        for (i in 0 .. max) {
             if (!nums.contains(i)) {
                 result = i
                 break
             }
        }

        return if (result == -1) max + 1 else result
    }
}
```

## 접근 방법
- 주어진 nums에서 최대 값을 찾음
- 0 부터 max 까지 접근하여 nums에 해당 값이 있나 찾아봄
- 리스트를 끝까지 돌았는데 result -1이라면 모든 값이 있다는거라 최대 값에 1 더해줌
- 시간 복잡도를 좀 더 고려해야했음..

## 개선 사항
- 등차수열의 합 공식 사용해보기