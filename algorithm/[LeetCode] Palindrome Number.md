# 📝 Palindrome Number

🔗 **문제 링크**: [Palindrome Number](https://leetcode.com/problems/palindrome-number/description/)

## 📌 문제 설명  

Given an integer x, return true if x is a palindrome, and false otherwise.

---

## 💡 풀이 코드 (Kotlin)
```kotlin
class Solution {
    fun isPalindrome(x: Int): Boolean {
        if (x < 0) return false

        val str = x.toString()
        val centerIndex = str.length / 2
        
        for (i in 0 until centerIndex) {
            if (str[i] != str[str.length - 1 - i]) return false
        }

        return true
    }
}
```

## 개선 사항
- 실행 시간 줄여보기

## 풀이 방법
- x가 음수면 대칭일 수 없으니 return 시킴
- 주어진 숫자의 길이를 구함
- 길이의 반만큼 반복문을 돌며 앞 쪽 반 뒤 쪽 반 값을 비교함