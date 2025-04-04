# 📝 Divisor Game

🔗 **문제 링크**: [Divisor Game](https://leetcode.com/problems/divisor-game/description/)

## 📌 문제 설명  

Alice and Bob take turns playing a game, with Alice starting first.

Initially, there is a number n on the chalkboard. On each player's turn, that player makes a move consisting of:

Choosing any x with 0 < x < n and n % x == 0.
Replacing the number n on the chalkboard with n - x.
Also, if a player cannot make a move, they lose the game.

Return true if and only if Alice wins the game, assuming both players play optimally.

---

## 💡 풀이 코드 (Kotlin)
```kotlin
class Solution {
    fun divisorGame(n: Int): Boolean {
        return n % 2 == 0
    }
}
```

## 개선 사항
- 점화식부터 생각하기
