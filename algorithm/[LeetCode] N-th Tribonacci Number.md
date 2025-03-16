# 📝 N-th Tribonacci Number

🔗 **문제 링크**: [N-th Tribonacci Number](https://leetcode.com/explore/learn/card/dynamic-programming/631/strategy-for-solving-dp-problems/4041/)

## 📌 문제 설명  

The Tribonacci sequence Tn is defined as follows: 

T0 = 0, T1 = 1, T2 = 1, and Tn+3 = Tn + Tn+1 + Tn+2 for n >= 0.

Given n, return the value of Tn.

---

## 💡 풀이 코드 (Kotlin)
```kotlin
private fun tribonacci(n: Int): Int {
    val resultArray = IntArray(n + 1).apply {
        if (n >= 0) this[0] = 0
        if (n >= 1) this[1] = 1
        if (n >= 2) this[2] = 1
    }

    if (n < 3) return resultArray[n]

    for (i in 3..n) {
        resultArray[i] = resultArray[i - 3] + resultArray[i - 2] + resultArray[i - 1]
    }

    return resultArray[n]
}
```

## 개선 사항
- 메모리 최적화
```kotlin
private fun tribonacci(n: Int): Int {
    if (n == 0) return 0
    if (n == 1 || n == 2) return 1

    var t0 = 0
    var t1 = 1
    var t2 = 1
    var t3 = 0

    for (i in 3..n) {
        t3 = t0 + t1 + t2
        t0 = t1
        t1 = t2
        t2 = t3
    }

    return t3
}
```