# 📝 Divide Array Into Equal Pairs

🔗 **문제 링크**: [Divide Array Into Equal Pairs](https://leetcode.com/problems/divide-array-into-equal-pairs/description/?envType=daily-question&envId=2025-03-17)

## 📌 문제 설명  

You are given an integer array nums consisting of 2 * n integers.

You need to divide nums into n pairs such that:

Each element belongs to exactly one pair.
The elements present in a pair are equal.
Return true if nums can be divided into n pairs, otherwise return false.

---

## 💡 풀이 코드 (Kotlin)
```kotlin
private fun divideArray(nums: IntArray): Boolean {
    return nums.groupBy { it }.none { it.value.size % 2 != 0 }
}
```

## 개선 사항
- 시간 복잡도 줄여보기