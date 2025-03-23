# 📝 Number of Ways to Arrive at Destination

🔗 **문제 링크**: [Number of Ways to Arrive at Destination](https://leetcode.com/problems/number-of-ways-to-arrive-at-destination/description/?envType=daily-question&envId=2025-03-23)

## 📌 문제 설명  

You are in a city that consists of n intersections numbered from 0 to n - 1 with bi-directional roads between some intersections. The inputs are generated such that you can reach any intersection from any other intersection and that there is at most one road between any two intersections.

You are given an integer n and a 2D integer array roads where roads[i] = [ui, vi, timei] means that there is a road between intersections ui and vi that takes timei minutes to travel. You want to know in how many ways you can travel from intersection 0 to intersection n - 1 in the shortest amount of time.

Return the number of ways you can arrive at your destination in the shortest amount of time. Since the answer may be large, return it modulo 109 + 7.

---

## 💡 풀이 코드 (Kotlin)
```kotlin
fun countPaths(n: Int, roads: Array<IntArray>): Int {
        val mod = 1_000_000_007
        val graph = Array(n) { mutableListOf<Pair<Int, Int>>() }
        for (road in roads) {
            val u = road[0]
            val v = road[1]
            val time = road[2]
            graph[u].add(Pair(v, time))
            graph[v].add(Pair(u, time))
        }

        val dist = LongArray(n) { Long.MAX_VALUE }
        val ways = LongArray(n) { 0L }
        dist[0] = 0
        ways[0] = 1

        val pq = PriorityQueue<Pair<Long, Int>>(compareBy { it.first })
        pq.add(Pair(0L, 0))

        while (pq.isNotEmpty()) {
            val (currentDistance, node) = pq.poll()
            if (currentDistance > dist[node]) continue
            for ((neighbor, time) in graph[node]) {
                val newDist = currentDistance + time
                if (newDist < dist[neighbor]) {
                    dist[neighbor] = newDist
                    ways[neighbor] = ways[node]
                    pq.add(Pair(newDist, neighbor))
                }
                else if (newDist == dist[neighbor]) {
                    ways[neighbor] = (ways[neighbor] + ways[node]) % mod
                }
            }
        }

        return ways[n - 1].toInt()
    }
```

## 개선 사항
