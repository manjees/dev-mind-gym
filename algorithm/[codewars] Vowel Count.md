# 📝 Bouncing Balls

🔗 **문제 링크**: [Vowel Count](https://www.codewars.com/kata/54ff3102c1bad923760001f3/kotlin)

## 📌 문제 설명  
Return the number (count) of vowels in the given string.

We will consider a, e, i, o, u as vowels for this Kata (but not y).

The input string will only consist of lower case letters and/or spaces.

---

## 💡 풀이 코드 (Kotlin)
```kotlin
fun getCount(str : String) : Int {
    var count = 0;
    str.forEach {
        if (it == 'a' || it == 'e' || it == 'i' || it == 'o' || it == 'u') {
            count++
        }
    }
    return count
}
```

## 개선 사항
- count 사용해 코드 간소화
