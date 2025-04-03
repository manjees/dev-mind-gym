# 📝 Maximum Repeating Substring

🔗 **문제 링크**: [Maximum Repeating Substring](https://leetcode.com/problems/maximum-repeating-substring/description/)

## 📌 문제 설명  

For a string sequence, a string word is k-repeating if word concatenated k times is a substring of sequence. The word's maximum k-repeating value is the highest value k where word is k-repeating in sequence. If word is not a substring of sequence, word's maximum k-repeating value is 0.

Given strings sequence and word, return the maximum k-repeating value of word in sequence.

---

## 💡 풀이 코드 (Kotlin)
```kotlin
class Solution {
    fun maxRepeating(sequence: String, word: String): Int {
        var k = 0
        var repeated = word

        while (sequence.contains(repeated)) {
            k++
            repeated += word
        }

        return k
    }
}
```

## 개선 사항
- 
