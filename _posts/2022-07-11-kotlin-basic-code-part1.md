---
title: kotlin 기본 문법 (1)
categories:
- android
tag:
- android
- kotlin
toc: true
toc_sticky: true
toc_label: "코틀린 기본 문법 (1)"
author_profile: true
sidebar: 
  nav: "docs"
---

# 코틀린 기본 문법 - 변수 처리
코틀린은 다른 언어와 다르게 세미콜론(;)가 필요하지 않습니다.
<br>
또한 변수 타입을 지정하지 않을 수도 있습니다.

`JAVA Code`
<script src="https://gist.github.com/HyungMinKims/5be152c2f68cec1cf4a3d0c4e5ea535a.js"></script>

`Kotlin Code`
<script src="https://gist.github.com/HyungMinKims/e08cc86304aff90830dc44d5503aff01.js"></script>

<br>
# 코클린 기본 문법 - var, val
코틀린에는 2가지 변수 선언 타입이 있습니다.
- val : 변할 수 없는 상수 
- var : 일반적인 변수에 해당

`JAVA Code`
<script src="https://gist.github.com/HyungMinKims/689bcf217622f292b6d1429244452f41.js"></script>

`Kotlin Code`
<script src="https://gist.github.com/HyungMinKims/6bd872478c502a6e573273c546033f52.js"></script>

여기서 그럼 var만 쓰면 좋지 않냐고 물어보시는 경우가 있는데 **상수는 의도치 않은 값의 변경을 사전에 예방해주는 역할을 하기 때문에 명확하게 사용
하시면 편하게 사용 할 수 있습니다.** ex) 반지름 : 3.14

<br>
# 코틀린 기본 문법 - 함수 처리
코틀린은 일반적으로 함수 처리를 fun (parameter: 타입 형): 반환 타입 형식으로 사용 합니다. 

`JAVA Code`
<script src="https://gist.github.com/HyungMinKims/f18026dab11b18a708631648d24de62d.js"></script>

`Kotlin Code`
<script src="https://gist.github.com/HyungMinKims/59810ea225b364e783b97ac4448f6095.js"></script>

코틀린은 함수를 간단하게 사용 가능 합니다.
```Kotlin
fun max(a: Int, b: Int) = if (a > b) a else b
```

<br>
# 코틀린 기본 문법 - null
코틀린의 기본 변수는 null을 가질 수 없습니다. 하