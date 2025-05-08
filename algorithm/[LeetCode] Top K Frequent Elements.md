# 📝 Top K Frequent Elements

🔗 **문제 링크**: [Top K Frequent Elements](https://leetcode.com/explore/learn/card/heap/646/practices/4015/)

## 📌 문제 설명  

Given an integer array nums and an integer k, return the k most frequent elements. You may return the answer in any order.

---

## 💡 풀이 코드 (Kotlin)
```kotlin
 class Solution {
    fun topKFrequent(nums: IntArray, k: Int): IntArray {
        val frequncyMap = mutableMapOf<Int, Int>()
        nums.forEach {
            frequncyMap[it] = frequncyMap.getOrDefault(it, 0) + 1
        }

        val priorityQueue = PriorityQueue<Pair<Int, Int>>(compareBy { it.second })
        for ((num, freq) in frequncyMap) {
            priorityQueue.add(Pair(num, freq))
            if (priorityQueue.size > k) priorityQueue.poll()
        }

        val result = mutableListOf<Int>()
        while (priorityQueue.isNotEmpty()) {
            result.add(priorityQueue.poll().first)
        }

        return result.toIntArray()
    }
}
```

## 접근 방법
- 주어진 배열을 숫자, 횟수로 hashmap으로 만든다
- 횟수를 기준으로 우선순위 큐를 만들고 하나씩 추가해줌
- k보다 큰 경우 큐 제일 앞에 아이템을 지워준다
- 큐를 높은 순서로 소팅해 배열에 넣어주면 끝

## 개선 사항
