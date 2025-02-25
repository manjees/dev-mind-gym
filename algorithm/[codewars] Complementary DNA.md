# 📝 Complementary DNA

🔗 **문제 링크**: [Complementary DNA](https://www.codewars.com/kata/554e4a2f232cdd87d9000038/kotlin)

## 📌 문제 설명  Deoxyribonucleic acid (DNA) is a chemical found in the nucleus of cells and carries the "instructions" for the development and functioning of living organisms.

If you want to know more: http://en.wikipedia.org/wiki/DNA

In DNA strings, symbols "A" and "T" are complements of each other, as "C" and "G". Your function receives one side of the DNA (string, except for Haskell); you need to return the other complementary side. DNA strand is never empty or there is no DNA at all (again, except for Haskell).

More similar exercise are found here: http://rosalind.info/problems/list-view/ (source)

"ATTGC" --> "TAACG"
"GTAT" --> "CATA"
---

## 💡 풀이 코드 (Kotlin)
```kotlinfun
makeComplement(dna : String) : String {
  var result = ""
  dna.forEach {
    if (it =='A') result += 'T'
    if (it =='T') result += 'A'
    if (it == 'G') result  += 'C'
    if (it == 'C') result  += 'G'
  }

  return  result
}
```

## 개선 사항
- map / joingString 으로 해보기
