# 📝 Find All Possible Recipes from Given Supplies

🔗 **문제 링크**: [Find All Possible Recipes from Given Supplies](https://leetcode.com/problems/find-all-possible-recipes-from-given-supplies/description/?envType=daily-question&envId=2025-03-21)

## 📌 문제 설명  

You have information about n different recipes. You are given a string array recipes and a 2D string array ingredients. The ith recipe has the name recipes[i], and you can create it if you have all the needed ingredients from ingredients[i]. A recipe can also be an ingredient for other recipes, i.e., ingredients[i] may contain a string that is in recipes.

You are also given a string array supplies containing all the ingredients that you initially have, and you have an infinite supply of all of them.

Return a list of all the recipes that you can create. You may return the answer in any order.

Note that two recipes may contain each other in their ingredients.

---

## 💡 풀이 코드 (Kotlin)
```kotlin
fun findAllRecipes(recipes: Array<String>, ingredients: List<List<String>>, supplies: Array<String>): List<String> {
        val supplySet = supplies.toHashSet()
        val recipeSet = recipes.toHashSet()

        val indegree = mutableMapOf<String, Int>()
        val graph = mutableMapOf<String, MutableList<String>>()

        for (recipe in recipes) {
            indegree[recipe] = 0
        }

        for (i in recipes.indices) {
            for (ing in ingredients[i]) {
                if (ing in supplySet) continue

                if (ing in recipeSet) {
                    graph.getOrPut(ing) { mutableListOf() }.add(recipes[i])
                    indegree[recipes[i]] = indegree.getOrDefault(recipes[i], 0) + 1
                } else {
                    indegree[recipes[i]] = indegree.getOrDefault(recipes[i], 0) + 1
                }
            }
        }

        val queue: java.util.Queue<String> = java.util.LinkedList()
        for (recipe in recipes) {
            if (indegree[recipe] == 0) {
                queue.offer(recipe)
            }
        }

        val result = mutableListOf<String>()
        while (queue.isNotEmpty()) {
            val curr = queue.poll()
            result.add(curr)

            if (graph.containsKey(curr)) {
                for (next in graph[curr]!!) {
                    indegree[next] = indegree[next]!! - 1
                    if (indegree[next] == 0) {
                        queue.offer(next)
                    }
                }
            }
        }

        return result
    }

```

## 개선 사항
