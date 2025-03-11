# 📝 Valid Mountain Array

🔗 **문제 링크**: [Valid Mountain Array](https://leetcode.com/explore/learn/card/fun-with-arrays/527/searching-for-items-in-an-array/3251/)

## 📌 문제 설명  
Given an array of integers arr, return true if and only if it is a valid mountain array.

Recall that arr is a mountain array if and only if:

arr.length >= 3
There exists some i with 0 < i < arr.length - 1 such that:
arr[0] < arr[1] < ... < arr[i - 1] < arr[i]
arr[i] > arr[i + 1] > ... > arr[arr.length - 1]
---

## 💡 풀이 코드 (Kotlin)
```kotlin
fun validMountainArray(arr: IntArray): Boolean {
    val maxNum = arr.max()
    var beforeIndex = arr.first()
    var isTop = false
    var isResult = true
        
    if (arr.size == 1 || arr.last() == maxNum) return false

    for (i in 1 until arr.size) {
        if (isTop) {
            if (beforeIndex <= arr[i]) isResult = false
        } else {
            if (beforeIndex >= arr[i]) isResult = false
        }

        if (arr[i] == maxNum) isTop = true
            beforeIndex = arr[i]
        }
        return isResult
}
```

## 개선 사항
- 불 필요한 변수 제거 및 로직 개선
