# 📝 List Filtering

🔗 **문제 링크**: [List Filtering](https://www.codewars.com/kata/53dbd5315a3c69eed20002dd)

## 📌 문제 설명  
In this kata you will create a function that takes a list of non-negative integers and strings and returns a new list with the strings filtered out.


---

## 💡 풀이 코드 (Kotlin)
```kotlin
fun solution22(l: List<Any>): List<Int> {
  return l.filterIsInstance<Int>().filter { it > 0 }
}
```

## 개선 사항
