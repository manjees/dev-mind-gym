# 📝 Word Break

🔗 **문제 링크**: [Word Break](https://leetcode.com/explore/learn/card/dynamic-programming/632/common-patterns-in-dp-problems/4113/)

## 📌 문제 설명  

Given a string s and a dictionary of strings wordDict, return true if s can be segmented into a space-separated sequence of one or more dictionary words.

Note that the same word in the dictionary may be reused multiple times in the segmentation.

---

## 💡 풀이 코드 (Kotlin)
```kotlin
class Solution {
    fun wordBreak(s: String, wordDict: List<String>): Boolean {
        val dp = BooleanArray(s.length + 1)
        dp[0] = true

        for (i in 1..s.length) {
            for (word in wordDict) {
                val len = word.length
                if (i - len >= 0 && dp[i - len] && s.substring(i - len, i) == word) {
                    dp[i] = true
                    break
                }
            }
        }

        return dp[s.length]
    }
}
```

## 개선 사항
- 

## 풀이법
- 목표 문자열 길이 + 1 만큼 배열 생성
- 빈 문자열은 항상 분할 가능하므로 dp[0] = true
- 주어진 문자열 길이만큼 하나씩 탐색
- wordDict 내의 모든 값 검사
- word와 주어진 문자열을 자른 문자가 같다면 dp[i] = true