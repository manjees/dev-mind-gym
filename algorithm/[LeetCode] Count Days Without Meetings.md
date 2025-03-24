# 📝 Count Days Without Meetings

🔗 **문제 링크**: [Count Days Without Meetings](https://leetcode.com/problems/count-days-without-meetings/description/?envType=daily-question&envId=2025-03-24)

## 📌 문제 설명  

You are given a positive integer days representing the total number of days an employee is available for work (starting from day 1). You are also given a 2D array meetings of size n where, meetings[i] = [start_i, end_i] represents the starting and ending days of meeting i (inclusive).

Return the count of days when the employee is available for work but no meetings are scheduled.

Note: The meetings may overlap.

---

## 💡 풀이 코드 (Kotlin)
```kotlin
fun countDays(days: Int, meetings: Array<IntArray>): Int {
    val intervals = meetings.mapNotNull { meeting ->
        val s = meeting[0]
        val e = meeting[1]
        if (e < 1 || s > days) null
        else intArrayOf(maxOf(s, 1), minOf(e, days))
    }

    if (intervals.isEmpty()) return days

    val sortedIntervals = intervals.sortedBy { it[0] }

    var mergedMeetingDays = 0
    var currentStart = sortedIntervals[0][0]
    var currentEnd = sortedIntervals[0][1]
    for (i in 1 until sortedIntervals.size) {
        val s = sortedIntervals[i][0]
        val e = sortedIntervals[i][1]

        if (s <= currentEnd + 1) {
            currentEnd = maxOf(currentEnd, e)
        } else {
            mergedMeetingDays += (currentEnd - currentStart + 1)
            currentStart = s
            currentEnd = e
        }
    }
    mergedMeetingDays += (currentEnd - currentStart + 1)

    return days - mergedMeetingDays
}
```

## 개선 사항
