# 📝 Pascal's Triangle II

🔗 **문제 링크**: [Pascal's Triangle II](https://leetcode.com/problems/pascals-triangle-ii/description/)

## 📌 문제 설명  

Given an integer rowIndex, return the rowIndexth (0-indexed) row of the Pascal's triangle.

---

## 💡 풀이 코드 (Kotlin)
```kotlin
 fun getRow(rowIndex: Int): List<Int> {
    val resultList = mutableListOf(listOf(1), listOf(1,1))

    for (row in 2..rowIndex) {
        val rowList = mutableListOf<Int>()
        for (i in 0 .. row) {
            if (i == 0 || i == row) {
                rowList.add(1)
            } else {
                rowList.add(resultList[row - 1][i] + resultList[row - 1][i - 1])
            }
        }
        resultList.add(rowList)
    }

    return resultList[rowIndex]
}
```

## 개선 사항
