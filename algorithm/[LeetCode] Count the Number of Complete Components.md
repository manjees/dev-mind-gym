# 📝 Count the Number of Complete Components

🔗 **문제 링크**: [Count the Number of Complete Components](https://leetcode.com/problems/count-the-number-of-complete-components/description/?envType=daily-question&envId=2025-03-22)

## 📌 문제 설명  

You are given an integer n. There is an undirected graph with n vertices, numbered from 0 to n - 1. You are given a 2D integer array edges where edges[i] = [ai, bi] denotes that there exists an undirected edge connecting vertices ai and bi.

Return the number of complete connected components of the graph.

A connected component is a subgraph of a graph in which there exists a path between any two vertices, and no vertex of the subgraph shares an edge with a vertex outside of the subgraph.

A connected component is said to be complete if there exists an edge between every pair of its vertices.

---

## 💡 풀이 코드 (Kotlin)
```kotlin
fun countCompleteComponents(n: Int, edges: Array<IntArray>): Int {
    val graph = Array(n) { mutableListOf<Int>() }
    for (edge in edges) {
        val u = edge[0]
        val v = edge[1]
        graph[u].add(v)
        graph[v].add(u)
    }

    val visited = BooleanArray(n)
    var completeComponents = 0

    fun dfs(start: Int): List<Int> {
        val stack = ArrayDeque<Int>()
        val component = mutableListOf<Int>()
        stack.add(start)
        visited[start] = true

        while (stack.isNotEmpty()) {
            val node = stack.removeLast()
            component.add(node)
            for (neighbor in graph[node]) {
                if (!visited[neighbor]) {
                    visited[neighbor] = true
                    stack.add(neighbor)
                }
            }
        }
        return component
    }

    for (i in 0 until n) {
        if (!visited[i]) {
            val component = dfs(i)
            val size = component.size
            if (size == 1) {
                completeComponents++
            } else {
                val compSet = component.toSet()
                var isComplete = true
                for (node in component) {
                    val neighborCount = graph[node].count { it in compSet }
                    if (neighborCount != size - 1) {
                        isComplete = false
                        break
                    }
                }
                if (isComplete) {
                    completeComponents++
                }
            }
        }
    }

    return completeComponents
} 
```

## 개선 사항
