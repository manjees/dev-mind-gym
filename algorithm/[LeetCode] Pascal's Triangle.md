# 📝 Pascal's Triangle

🔗 **문제 링크**: [Pascal's Triangle](https://leetcode.com/problems/pascals-triangle/description/)

## 📌 문제 설명  

Given an integer numRows, return the first numRows of Pascal's triangle.

In Pascal's triangle, each number is the sum of the two numbers directly above it as shown:

---

## 💡 풀이 코드 (Kotlin)
```kotlin
fun generate(numRows: Int): List<List<Int>> {
        val resultList = mutableListOf<List<Int>>()

        if (numRows >= 1) {
            resultList.add(listOf(1))
        }
        if (numRows >= 2) {
            resultList.add(listOf(1, 1))
        }

        if (numRows >= 3) {
            for (num in 3..numRows) {
                val list = mutableListOf<Int>()
                for (i in 0 until  num) {
                    if (i == 0 || i == num - 1) {
                        list.add(1)
                    } else {
                        val prevList = resultList[num - 2]
                        list.add(prevList[i - 1] + prevList[i])
                    }
                }
                resultList.add(list)
            }
        }

        return resultList
    }
```

## 개선 사항
- 로직 더 간단하게 만들어보기