# 📝 Kth Largest Element in an Array

🔗 **문제 링크**: [Kth Largest Element in an Array](https://leetcode.com/explore/learn/card/heap/646/practices/4014/)

## 📌 문제 설명  

Given an integer array nums and an integer k, return the kth largest element in the array.

Note that it is the kth largest element in the sorted order, not the kth distinct element.

Can you solve it without sorting?

---

## 💡 풀이 코드 (Kotlin)
```kotlin
 class Solution {
    fun findKthLargest(nums: IntArray, k: Int): Int {
        val priorityQueue = PriorityQueue<Int>()
        for (num in nums) {
            priorityQueue.add(num)
            if (priorityQueue.size > k) {
                priorityQueue.poll()
            }
        }
        return priorityQueue.peek()
    }
}
```

## 접근 방법
- 우선 순위 큐를 만들어서 사용
- 주어진 배열을 하나씩 큐에 추가
- k 번째보다 큐가 커진경우 제일 작은 숫자를 지워준다 (poll)
- 반복문이 완료된 후 제일 앞에있는게 k 번째로 큰 수 임

## 개선 사항
