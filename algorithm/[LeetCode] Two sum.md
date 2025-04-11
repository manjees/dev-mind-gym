# 📝 Word Break

🔗 **문제 링크**: [Two Sum](https://leetcode.com/problems/two-sum/)

## 📌 문제 설명  

Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

You can return the answer in any order.

---

## 💡 풀이 코드 (Kotlin)
```kotlin
class Solution {
    fun twoSum(nums: IntArray, target: Int): IntArray {
        val resultArray = IntArray(2)

        for (i in 0 until nums.size) {
            for (j in i + 1 until nums.size) {
                if (nums[i] + nums[j] == target) {
                    resultArray[0] = i
                    resultArray[1] = j
                    break
                }
            }
        }
        return resultArray
    }
}
```

## 개선 사항
- 해시 + 포인터 기법으로 풀어보기 (실행 속도 개건)

## 풀이법
- 각 인덱스마다 처음투버 탐색하여 합이 Target과 같아지는게 있는지 찾음