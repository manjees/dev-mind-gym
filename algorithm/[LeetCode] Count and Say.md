# 📝 Count and Say

🔗 **문제 링크**: [Count and Say](https://leetcode.com/problems/count-and-say/description/)

## 📌 문제 설명  

The count-and-say sequence is a sequence of digit strings defined by the recursive formula:

countAndSay(1) = "1"
countAndSay(n) is the run-length encoding of countAndSay(n - 1).
Run-length encoding (RLE) is a string compression method that works by replacing consecutive identical characters (repeated 2 or more times) with the concatenation of the character and the number marking the count of the characters (length of the run). For example, to compress the string "3322251" we replace "33" with "23", replace "222" with "32", replace "5" with "15" and replace "1" with "11". Thus the compressed string becomes "23321511".

Given a positive integer n, return the nth element of the count-and-say sequence.

---

## 💡 풀이 코드 (Kotlin)
```kotlin
class Solution {
    fun countAndSay(n: Int): String {
        if (n == 1) return "1"
        if (n == 2) return "11"
        var result = "11"

        for (i in 3..n) {
            var newResult = ""
            var currentValue = result.first()
            var currentCount = 1

            for (j in 1 until result.length) {
                if (result[j] == currentValue) {
                    currentCount++
                } else {
                    newResult += "$currentCount$currentValue"
                    currentValue = result[j]
                    currentCount = 1
                }
            }

            newResult += "$currentCount$currentValue"
            result = newResult
        }

        return result
    }
}
```

## 개선 사항
- StringBuilder로 성능 높여보기

## 풀이 방법
- 기본적인 예외 값 미리 리턴해줌
- n이 3이상일 경우부터 RLE 찾는 로직 추가해줌
- 현재 숫자와 같은 값의 갯수를 세고 값이 다르면 result에 값 추가해줌