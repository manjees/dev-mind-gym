# 📝 Minimum Time to Repair Cars

🔗 **문제 링크**: [Minimum Time to Repair Cars](https://leetcode.com/problems/minimum-time-to-repair-cars/description/?envType=daily-question&envId=2025-03-16)

## 📌 문제 설명  

You are given an integer array ranks representing the ranks of some mechanics. ranksi is the rank of the ith mechanic. A mechanic with a rank r can repair n cars in r * n2 minutes.

You are also given an integer cars representing the total number of cars waiting in the garage to be repaired.

Return the minimum time taken to repair all the cars.

Note: All the mechanics can repair the cars simultaneously.

---

## 💡 풀이 코드 (Kotlin)
```kotlin
fun repairCars(ranks: IntArray, cars: Int): Long {
    var left = 0L
    var right = ranks.min() * (cars.toLong() * cars.toLong())

    fun canRepairTime(time: Long): Boolean {
        var repaired = 0L

        for (rank in ranks) {
            repaired += floor(Math.sqrt(time / rank.toDouble())).toLong()
            if (repaired >= cars) return true
        }
        return repaired >= cars
    }

    while (left < right) {
        val mid = (left + right) / 2
        if (canRepairTime(mid)) {
            right = mid
        } else {
            left = mid + 1
        }
    }

    return left
}
```

## 개선 사항
