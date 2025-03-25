# 📝 Check if Grid can be Cut into Sections

🔗 **문제 링크**: [Check if Grid can be Cut into Sections](https://leetcode.com/problems/check-if-grid-can-be-cut-into-sections/description/?envType=daily-question&envId=2025-03-25)

## 📌 문제 설명  

YYou are given an integer n representing the dimensions of an n x n grid, with the origin at the bottom-left corner of the grid. You are also given a 2D array of coordinates rectangles, where rectangles[i] is in the form [startx, starty, endx, endy], representing a rectangle on the grid. Each rectangle is defined as follows:

(startx, starty): The bottom-left corner of the rectangle.
(endx, endy): The top-right corner of the rectangle.
Note that the rectangles do not overlap. Your task is to determine if it is possible to make either two horizontal or two vertical cuts on the grid such that:

Each of the three resulting sections formed by the cuts contains at least one rectangle.
Every rectangle belongs to exactly one section.
Return true if such cuts can be made; otherwise, return false.

---

## 💡 풀이 코드 (Kotlin)
```kotlin
fun checkValidCuts(n: Int, rectangles: Array<IntArray>): Boolean {
        val m = rectangles.size
        if (m < 3) return false  // 세 구역에 직사각형을 배분해야 하므로 최소 3개 필요

        // ---- 세로 절단 (vertical cuts) 검사 ----
        // 직사각형들을 x좌표(왼쪽 경계) 기준으로 정렬합니다.
        val rectsByX = rectangles.sortedWith(compareBy { it[0] })

        // prefixMaxX[i] : 인덱스 0부터 i까지 직사각형들의 endx(오른쪽 경계) 중 최대값
        val prefixMaxX = IntArray(m)
        prefixMaxX[0] = rectsByX[0][2]
        for (i in 1 until m) {
            prefixMaxX[i] = maxOf(prefixMaxX[i - 1], rectsByX[i][2])
        }

        // 그룹 분할: 그룹1: [0..i], 그룹2: [i+1..j], 그룹3: [j+1..m-1]
        for (i in 0 until m - 2) {
            // 그룹1과 그룹2의 경계 조건: 그룹1의 최대 endx <= 그룹2의 첫 직사각형의 startx
            if (prefixMaxX[i] > rectsByX[i + 1][0]) continue
            var group2Max = rectsByX[i + 1][2]  // 그룹2의 최대 endx (초기값)
            var valid = false
            for (j in i + 1 until m - 1) {
                group2Max = maxOf(group2Max, rectsByX[j][2])
                // 그룹2와 그룹3의 경계 조건: 그룹2의 최대 endx <= 그룹3의 첫 직사각형의 startx
                if (group2Max <= rectsByX[j + 1][0]) {
                    valid = true
                    break
                }
            }
            if (valid) return true
        }

        // ---- 가로 절단 (horizontal cuts) 검사 ----
        // 직사각형들을 y좌표(하단 경계) 기준으로 정렬합니다.
        val rectsByY = rectangles.sortedWith(compareBy { it[1] })

        // prefixMaxY[i] : 인덱스 0부터 i까지 직사각형들의 endy(상단 경계) 중 최대값
        val prefixMaxY = IntArray(m)
        prefixMaxY[0] = rectsByY[0][3]
        for (i in 1 until m) {
            prefixMaxY[i] = maxOf(prefixMaxY[i - 1], rectsByY[i][3])
        }

        for (i in 0 until m - 2) {
            if (prefixMaxY[i] > rectsByY[i + 1][1]) continue
            var group2MaxY = rectsByY[i + 1][3]
            var valid = false
            for (j in i + 1 until m - 1) {
                group2MaxY = maxOf(group2MaxY, rectsByY[j][3])
                if (group2MaxY <= rectsByY[j + 1][1]) {
                    valid = true
                    break
                }
            }
            if (valid) return true
        }

        return false
    }
```

## 개선 사항
- 아래 코드 분석해보기
```kotlin
class Solution {
      
fun checkValidCuts(n: Int, rectangles: Array<IntArray>): Boolean { 
    val x = mutableListOf<Pair<Int, Int>>()
    val y = mutableListOf<Pair<Int, Int>>()
    for ((x1, y1, x2, y2) in rectangles) {
        x.add(Pair(x1, x2))
        y.add(Pair(y1, y2))
    }
    
    return solve(x) || solve(y)
}

fun solve(pairs: List<Pair<Int, Int>>): Boolean {
    val sorted = pairs.sortedWith(object : Comparator<Pair<Int, Int>> {
        override fun compare(o1: Pair<Int, Int>, o2: Pair<Int, Int>): Int {
            return o1.first - o2.first
        }
    })

    var max = -1
    var c = 0
    for (p in sorted) {
        if (max != -1 && max <= p.first)
            c++
        max = Math.max(max, p.second)
    }

    return c >= 2
}
       
}
```
