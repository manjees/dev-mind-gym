# 📝 Convert A Hex String To RGB

🔗 **문제 링크**: [Convert A Hex String To RGB](https://www.codewars.com/kata/5282b48bb70058e4c4000fa7/solutions/kotlin)

## 📌 문제 설명

When working with color values it can sometimes be useful to extract the individual red, green, and blue (RGB) component values for a color. Implement a function that meets these requirements:

Accepts a case-insensitive hexadecimal color string as its parameter (ex. "#FF9933" or "#ff9933")
Returns a Map<String, int> with the structure {r: 255, g: 153, b: 51} where r, g, and b range from 0 through 255
Note: your implementation does not need to support the shorthand form of hexadecimal notation (ie "#FFF")
---

## 💡 풀이 코드 (Kotlin)
```kotlinfun
// data class RGB(val r: Int, val g: Int, val b: Int)
fun hexStringToRGB(hexString: String): RGB {
    val hex = hexString.removePrefix("#")
    
    val r = hex.substring(0, 2).toInt(16)
    val g = hex.substring(2, 4).toInt(16)
    val b = hex.substring(4, 6).toInt(16)
    
    return RGB(r, g, b)
}
```

## 개선 사항
