# 📝 qr code

🔗 **문제 링크**: [qr code](https://school.programmers.co.kr/learn/courses/30/lessons/181903)

## 📌 문제 설명  
두 정수 q, r과 문자열 code가 주어질 때, code의 각 인덱스를 q로 나누었을 때 나머지가 r인 위치의 문자를 앞에서부터 순서대로 이어 붙인 문자열을 return 하는 solution 함수를 작성해 주세요.

---

## 💡 풀이 코드 (Kotlin)
```kotlin
fun solution(q: Int, r: Int, code: String): String {
  var answer: String = ""
  code.mapIndexed { index, c -> index % q == r }.forEachIndexed { index, b -> if(b) answer += code[index] }
  return answer
}
```

## 개선 사항
- filter / joinToString 사용해보기
