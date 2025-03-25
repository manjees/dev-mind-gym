# 📝 Minimum Difficulty of a Job Schedule

🔗 **문제 링크**: [Minimum Difficulty of a Job Schedule](https://leetcode.com/explore/learn/card/dynamic-programming/632/common-patterns-in-dp-problems/4110/)

## 📌 문제 설명  

You want to schedule a list of jobs in d days. Jobs are dependent (i.e To work on the ith job, you have to finish all the jobs j where 0 <= j < i).

You have to finish at least one task every day. The difficulty of a job schedule is the sum of difficulties of each day of the d days. The difficulty of a day is the maximum difficulty of a job done on that day.

You are given an integer array jobDifficulty and an integer d. The difficulty of the ith job is jobDifficulty[i].

Return the minimum difficulty of a job schedule. If you cannot find a schedule for the jobs return -1.

---

## 💡 풀이 코드 (Kotlin)
```kotlin
 fun minDifficulty(jobDifficulty: IntArray, d: Int): Int {
        val n = jobDifficulty.size
        if (d > n) return -1
        // INF: 매우 큰 값 (여기서는 Int.MAX_VALUE 사용)
        val INF = Int.MAX_VALUE

        // dp[day][i]는 day일 동안, i번째 작업부터 시작하여
        // 모든 작업을 마치는 스케줄의 최소 난이도 합을 의미합니다.
        // day는 1부터 d까지, i는 0부터 n까지 (n은 작업이 없는 경우를 위해 사용)
        val dp = Array(d + 1) { IntArray(n + 1) { INF } }

        // [Base Case] 마지막 날(d일)
        // 마지막 날에는 남은 모든 작업(i번째부터 n-1번째까지)을 한 번에 수행해야 하므로,
        // dp[d][i] = max(jobDifficulty[i..n-1])
        for (i in n - 1 downTo 0) {
            var maxVal = 0
            for (j in i until n) {
                maxVal = maxOf(maxVal, jobDifficulty[j])
            }
            dp[d][i] = maxVal
        }
        // dp[d][n]은 작업이 없는 경우로, 0으로 설정되어 있어도 무방합니다.
        dp[d][n] = 0

        // [Transition] 마지막 날 전의 날들 (day = d-1, d-2, ..., 1)
        // 여기서 dp[day][i]를 구하기 위해, 현재 day일에 i번째 작업부터 시작해서
        // j번째 작업까지 오늘 처리하고, (i <= j < n - (d - day))
        // 내일(day+1)부터는 j+1번째 작업부터 시작하도록 합니다.
        //
        // - 주의: 남은 날들마다 최소 1개의 작업은 남겨두어야 하므로,
        //         j의 상한은 n - (d - day) (즉, j가 n - (d - day) - 1 까지 가능)
        for (day in d - 1 downTo 1) {
            // i는 현재 day일에 시작할 작업 인덱스.
            // i의 최대값은 남은 날들에 필요한 작업 수를 고려하여 n - (d - day) - 0 까지 입니다.
            for (i in 0 until n - (d - day)) {
                var maxVal = 0
                // 오늘(day일)에 처리할 작업 구간: i부터 j까지.
                // j는 i부터 n - (d - day) - 1 까지 가능합니다.
                for (j in i until n - (d - day)) {
                    // i부터 j까지 작업 중 최대 난이도 (오늘의 난이도)
                    maxVal = maxOf(maxVal, jobDifficulty[j])
                    // dp[day+1][j+1]는 내일부터 j+1번째 작업부터 진행했을 때의 최소 난이도 합
                    // 오늘의 난이도(maxVal)와 내일 이후의 난이도 합을 더한 값 중 최솟값을 선택
                    if (dp[day + 1][j + 1] != INF) {
                        dp[day][i] = minOf(dp[day][i], maxVal + dp[day + 1][j + 1])
                    }
                }
            }
        }

        // 최종적으로 1일차, 0번째 작업부터 시작한 경우가 전체 문제의 정답입니다.
        return dp[1][0]
    }
```

## 개선 사항
