# 📝 Longest Unequal Adjacent Groups Subsequence I

🔗 **문제 링크**: [Longest Unequal Adjacent Groups Subsequence I](https://leetcode.com/problems/longest-unequal-adjacent-groups-subsequence-i/description/)

## 📌 문제 설명  

You are given a string array words and a binary array groups both of length n, where words[i] is associated with groups[i].

Your task is to select the longest alternating subsequence from words. A subsequence of words is alternating if for any two consecutive strings in the sequence, their corresponding elements in the binary array groups differ. Essentially, you are to choose strings such that adjacent elements have non-matching corresponding bits in the groups array.

Formally, you need to find the longest subsequence of an array of indices [0, 1, ..., n - 1] denoted as [i0, i1, ..., ik-1], such that groups[ij] != groups[ij+1] for each 0 <= j < k - 1 and then find the words corresponding to these indices.

Return the selected subsequence. If there are multiple answers, return any of them.

Note: The elements in words are distinct.

---

## 💡 풀이 코드 (Kotlin)
```kotlin
 class Solution {
    fun getLongestSubsequence(words: Array<String>, groups: IntArray): List<String> {
        if (words.size == 1) return listOf(words[0])
        if (words.size < 3) {
            return if (groups[0] == groups[1]) listOf(words[0])
            else listOf(words[0], words[1])
        }

        val firstOneIndex = groups.indexOfFirst { it == 1 }
        val firstZeroIndex = groups.indexOfFirst { it == 0 }

        val firstResult = arrayListOf<String>()
        val secondResult = arrayListOf<String>()

        var currentKey = 1

        if (firstOneIndex != -1) {
            for (index in firstOneIndex until groups.size) {
                if (groups[index] == currentKey) {
                    firstResult.add(words[index])
                    currentKey = if (currentKey == 1) 0 else 1
                }
            }
        }

        if (firstZeroIndex != -1) {
            currentKey = 0

            for (index in firstZeroIndex until groups.size) {
                if (groups[index] == currentKey) {
                    secondResult.add(words[index])
                    currentKey = if (currentKey == 1) 0 else 1
                }
            }
        }

        return if (firstResult.size >= secondResult.size) firstResult else secondResult
    }
}
```

## 개선 사항
- 그리디 방식으로 수정해보기
