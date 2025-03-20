# 📝 Kth Largest Sum in a Binary Tree

🔗 **문제 링크**: [Kth Largest Sum in a Binary Tree](https://leetcode.com/explore/learn/card/dynamic-programming/631/strategy-for-solving-dp-problems/4045/)

## 📌 문제 설명  

You are given the root of a binary tree and a positive integer k.

The level sum in the tree is the sum of the values of the nodes that are on the same level.

Return the kth largest level sum in the tree (not necessarily distinct). If there are fewer than k levels in the tree, return -1.

Note that two nodes are on the same level if they have the same distance from the root.

---

## 💡 풀이 코드 (Kotlin)
```kotlin
fun kthLargestLevelSum(root: TreeNode?, k: Int): Long {
    if (root == null) return -1

    val queue: Queue<TreeNode> = LinkedList()
        queue.add(root)

    val levelSums = mutableListOf<Long>()

    while (queue.isNotEmpty()) {
        val levelSize = queue.size
        var levelSum: Long = 0

        for (i in 0 until levelSize) {
            val node = queue.poll()
            levelSum += node.`val`.toLong()

            if (node.left != null) queue.add(node.left)
            if (node.right != null) queue.add(node.right)
        }

            levelSums.add(levelSum)
    }

    levelSums.sortDescending()
    return if (k <= levelSums.size) levelSums[k - 1] else -1
}
```

## 개선 사항
