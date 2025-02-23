# 📝 Rectangle into Squares

🔗 **문제 링크**: [Rectangle into Squares](https://www.codewars.com/kata/55466989aeecab5aac00003e/kotlin)

## 📌 문제 설명  
The drawing below gives an idea of how to cut a given "true" rectangle into squares ("true" rectangle meaning that the two dimensions are different).

Can you translate this drawing into an algorithm?

You will be given two dimensions

a positive integer length
a positive integer width
You will return a collection or a string (depending on the language; Shell bash, PowerShell, Pascal and Fortran return a string) with the size of each of the squares.

sqInRect(5, 3) should return [3, 2, 1, 1]
sqInRect(3, 5) should return [3, 2, 1, 1]
---

## 💡 풀이 코드 (Kotlin)
```kotlin
package squares

fun sqInRect(lng:Int, wdth:Int):List<Int>? {
    if (lng == wdth) return null

    val result = mutableListOf<Int>()
    var a = lng
    var b = wdth
    
    while (true) {
        if (a == b) {
            result.add(a)
            break
        }
        if (a > b) {
            result.add(b)
            a -= b
        } else {
            result.add(a)
            b -= a
        }
    }
    return result
}
```

## 개선 사항
