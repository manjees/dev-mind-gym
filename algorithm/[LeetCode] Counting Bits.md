# 📝 Counting Bits

🔗 **문제 링크**: [Counting Bits](https://leetcode.com/problems/counting-bits/description/)

## 📌 문제 설명  

Given an integer n, return an array ans of length n + 1 such that for each i (0 <= i <= n), ans[i] is the number of 1's in the binary representation of i.

---

## 💡 풀이 코드 (Kotlin)
```kotlin
fun countBits(n: Int): IntArray {
    val dp = IntArray(n + 1)
    for (i in 0..n) {
        dp[i] = i.toString(2).map { it.digitToInt() }.count { it == 1 }
    }
    return dp
}
```

## 개선 사항
- bitCount 사용해보기