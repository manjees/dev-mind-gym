# 📝 Multiples of 3 or 5

🔗 **문제 링크**: [Multiples of 3 or 5](https://www.codewars.com/kata/514b92a657cdc65150000006)

## 📌 문제 설명  
If we list all the natural numbers below 10 that are multiples of 3 or 5, we get 3, 5, 6 and 9. The sum of these multiples is 23.

Finish the solution so that it returns the sum of all the multiples of 3 or 5 below the number passed in.

Additionally, if the number is negative, return 0.

Note: If the number is a multiple of both 3 and 5, only count it once.


---

## 💡 풀이 코드 (Kotlin)
```kotlin
fun solution21(number: Int): Int {
    val list = arrayListOf<Int>()

    for (i in 1 until number) {
        if (i % 3 == 0 || i % 5 == 0) {
            list.add(i)
        }
    }
    return list.toSet().sum()
}
```

## 개선 사항
- filter 사용해보기
