# 📝 longest-common-prefix

🔗 **문제 링크**: [longest-common-prefix](https://leetcode.com/problems/longest-common-prefix/description/)

## 📌 문제 설명  

Write a function to find the longest common prefix string amongst an array of strings.

If there is no common prefix, return an empty string "".

---

## 💡 풀이 코드 (Kotlin)
```kotlin
 class Solution {
    fun longestCommonPrefix(strs: Array<String>): String {
        if (strs.isEmpty()) return ""

        val first = strs.first()

        for (i in first.indices) {
            val char = first[i]

            for (j in 1 until strs.size) {
                if (i == strs[j].length || strs[j][i] != char) {
                    return first.substring(0, i)
                }
            }
        }

        return first
    }
}
```

## 접근 방법
- str 에 첫 아이템을 first로 설정
- first의 요소를 가지고 for문 실행
- strs의 다음 요소들이 fist의 값과 맞는지 체크
- 달라지는 곳 까지 substring

## 개선 사항
