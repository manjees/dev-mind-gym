# 📝 과자 나눠주기

🔗 **문제 링크**: [과자 나눠주기](https://www.acmicpc.net/problem/16401)

## 📌 문제 설명  

명절이 되면, 홍익이 집에는 조카들이 놀러 온다. 떼를 쓰는 조카들을 달래기 위해 홍익이는 막대 과자를 하나씩 나눠준다.

조카들이 과자를 먹는 동안은 떼를 쓰지 않기 때문에, 홍익이는 조카들에게 최대한 긴 과자를 나눠주려고 한다.

그런데 나눠준 과자의 길이가 하나라도 다르면 조카끼리 싸움이 일어난다. 따라서 반드시 모든 조카에게 같은 길이의 막대 과자를 나눠주어야 한다.

M명의 조카가 있고 N개의 과자가 있을 때, 조카 1명에게 줄 수 있는 막대 과자의 최대 길이를 구하라.

단, 막대 과자는 길이와 상관없이 여러 조각으로 나눠질 수 있지만, 과자를 하나로 합칠 수는 없다. 단, 막대 과자의 길이는 양의 정수여야 한다.

---

## 💡 풀이 코드 (Kotlin)
```kotlin
fun main() {
    val br = System.`in`.bufferedReader()
    val bw = System.out.bufferedWriter()

    val (m, n) = br.readLine().split(" ").map { it.toInt() }
    val snacks = br.readLine().split(" ").map { it.toLong() }

    var left = 1L
    var right = snacks.maxOrNull() ?: 0L
    var answer = 0L

    while (left <= right) {
        val mid = (left + right) / 2
        val count = snacks.sumOf { it / mid }

        if (count >= m) {
            answer = mid
            left = mid + 1
        } else {
            right = mid - 1
        }
    }

    bw.write("$answer\n")
    bw.flush()
    bw.close()
}
```

## 개선 사항

## 풀이 방법
- 과자 길이의 최댓값을 high로 두고, low = 1부터 이진 탐색
- 각 mid 값으로 과자를 나눴을 때, 몇 명의 조카에게 줄 수 있는지 계산
- 그 수가 M 이상이면 → 가능한 길이 → 더 길게 도전 (left = mid + 1)
- 그 수가 M 미만이면 → 너무 길다 → 줄이자 (right = mid - 1)