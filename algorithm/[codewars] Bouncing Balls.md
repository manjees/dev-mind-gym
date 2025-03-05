# 📝 Bouncing Balls

🔗 **문제 링크**: [Bouncing Balls](https://www.codewars.com/kata/5544c7a5cb454edb3c000047/kotlin)

## 📌 문제 설명  
A child is playing with a ball on the nth floor of a tall building. The height of this floor above ground level, h, is known.

He drops the ball out of the window. The ball bounces (for example), to two-thirds of its height (a bounce of 0.66).

His mother looks out of a window 1.5 meters from the ground.

How many times will the mother see the ball pass in front of her window (including when it's falling and bouncing)?

Three conditions must be met for a valid experiment:
Float parameter "h" in meters must be greater than 0
Float parameter "bounce" must be greater than 0 and less than 1
Float parameter "window" must be less than h.
If all three conditions above are fulfilled, return a positive integer, otherwise return -1.

- h = 3, bounce = 0.66, window = 1.5, result is 3
---

## 💡 풀이 코드 (Kotlin)
```kotlin
fun bouncingBall(h:Double, bounce:Double, window:Double):Int {
    if (h <= 0 || bounce <= 0 || bounce >= 1 || window >= h) return -1

    var currentHeight = h * bounce
    var lookCount = 1
    while (currentHeight > window) {
        lookCount += 2
        currentHeight *= bounce
    }
        
    return lookCount
}
```

## 개선 사항
