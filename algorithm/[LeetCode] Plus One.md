# 📝 Plus One

🔗 **문제 링크**: [Plus One](https://leetcode.com/problems/plus-one/description/)

## 📌 문제 설명  

You are given a large integer represented as an integer array digits, where each digits[i] is the ith digit of the integer. The digits are ordered from most significant to least significant in left-to-right order. The large integer does not contain any leading 0's.

Increment the large integer by one and return the resulting array of digits.

---

## 💡 풀이 코드 (Kotlin)
```kotlin
 class Solution {
    fun plusOne(digits: IntArray): IntArray {
        val t = digits.toMutableList()
        for (i in digits.size - 1 downTo 0) {
            if (i == digits.size - 1) {
                t[i]++
            }
            if (t[i] >= 10) {
                t[i] -= 10
                if (i - 1 >= 0) {
                    t[i-1]++
                } else {
                    t.add(0, 1)
                }
            } else {
                break
            }
        }

        return t.toIntArray()
    }
}
```

## 접근 방법
- digits의 맨 뒤에서부터 Loop 시작
- 마지막 숫자에 1을 더해서 10이 되면 10을 뺴고 앞에 숫자를 1 더 해줌
- 그 앞의 숫자 위의 로직처럼 체크

## 개선 사항
- 원시 배열 조작으로 풀어보기