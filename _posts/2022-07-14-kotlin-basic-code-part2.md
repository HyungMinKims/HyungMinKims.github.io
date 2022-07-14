---
title: "[android] kotlin 기본 문법 (2)"
categories:
  - android
tag:
  - android
  - kotlin
toc: true
toc_sticky: true
toc_label: "코틀린 기본 문법 (2)"
author_profile: true
sidebar:
  nav: "docs"
date: 2022-07-13 12:00:00
lastmod : 2022-07-13 12:01:00
sitemap :
changefreq : daily
priority : 1.0
---

# 1️⃣ 범위 지정 함수
<br>
범위 지정 함수는 <span style="color: #6eb958">__특정 객체에 대한 작업을 블록 안에 넣어 실행할 수 있도록 하는 함수__</span>입니다. <span style="color: #6eb958">__블록은 특정 객체에 대해 할 작업의 범위가 됨으로__</span>
라고 **범위 지정 함수** 부릅니다. 특정 객체에 대한 작업을 블록안에 넣게 되면 __가독성이 증가하여 유지보수가 편하게 됩니다.__ 코틀린에서 범위 지정 함수는 **let, run, apply, also, with**
총 5가지 기본적인 범위 지정함수를 지원합니다.

```
💼 코틀린의 범위 지정 함수 💼

✔ apply

✔ run

✔ with

✔ let

✔ also
```

***
## 🚩 범위 지정함수와 수신객체 지정 람다(함수)

범위 지정함수는 <span style="color: #6eb958">__수신 객체 지정 람다(함수)__</span>라고 부릅니다. 수신객체를 명시 하지 않거나 it을 호출하는 것만으로 람다 안에서 수신객체의 메서드를 호출이 가능하도록 합니다.
가능 한 이유는 <span style="color: #6eb958">__블록(block) 람다식에서 수신객체를 람다의 입력 파라미터 혹은 수신객체로 사용하였기__</span>에 가능합니다.

also에서 block은 람다식의 입력 파라미터로 also의 수신객체(T)를 지정합니다.

```kotlin
// T.also -> also의 수신 객체
// block: (T) -> Unit -> 람다의 파라미터  
public inline fun <T> T.also(block: (T) -> Unit) 
```

apply에서 block은 람다식의 수신객체로 apply의 수신객체(T)를 지정합니다.

```kotlin
// T.apply -> apply의 수신 객체
// block: T.() -> Unit -> 람다의 파라미터  
public inline fun <T> T.apply(block: T.() -> Unit): T 
```
위 두 가지를 활용하면 람다 블록에서 수신객체 지정함수의 수신객체를 명시하지 않고 접근 가능하거나 it으로 접근 할 수 있게 됩니다. 
<br><br>

|              -               | [블록에서 수신객체 접근] <br/><span style="color: #6eb958">명시하지 않거나 this로 접근가능</span><br/><span style="font-size: 12px">* 수신객체를 람다의 수신객체로 전달하기 때문</span> | [블록에서 수신객체 접근] <br/><span style="color: #6eb958">it으로 접근 가능</span><br/><span style="font-size: 12px">* 수신객체를 람다의 파라메타로 전달하기 때문</span> |
|:----------------------------:|:----------------------------------------------------------------------------------------------------------------------------------------------:|:-------------------------------------------------------------------------------------------------------------------------------------:|
 |   [return 값]<br/> 수신객체 자체    |                                                                     apply                                                                      |                                                                 also                                                                  |
 | [return 값]<br/> Block의 마지막 줄 |                                                                   run, with                                                                    |                                                                  let                                                                  |

<br><br>
밑에 코드를 이용하여 어떻게 적용을 할 수 있는지 확인 해보겠습니다.

<script src="https://gist.github.com/HyungMinKims/f7b99f514c2eb7cd078ca0979c2bbb3c.js"></script>

***
# 2️⃣ apply
<br>
<span style="color: #6eb958">__apply는 수신객체 내부 프로퍼티를 변경한 다음 수신객체 자체를 반환하기 위해 사용되는 함수입니다.__</span> 
<br>
따라서 __객체 생성 시에 다양한 프로퍼티를 설정해야 하는 경우 사용됩니다.__

<script src="https://gist.github.com/HyungMinKims/f8897c1d0ea94b168fa5364b5f501ea2.js"></script>

***
# 3️⃣ run
<br>
<span style="color: #6eb958">__run는 apply와 똑같이 동작하지만 수신 객체를 return 하지 않고, run 블록의 마지막 라인을 return 하는 범위 지정 함수입니다.__</span>
<br>
따라서 __수신 객체에 대해 특정한 동작을 수행한 후 결과값을 리턴 받아야 할 경우 사용합니다.__

<script src="https://gist.github.com/HyungMinKims/3a37d605265c3b0395e660ccd314d2ec.js"></script>

suvCarSpeed 변수 결과 값은 **30**이 나옵니다.

***
# 4️⃣ with
<br>
<span style="color: #6eb958">__with는 run과 완전히 똑같이 동작을 하지만 run은 확장 함수로 사용되고 with은 수신객체를 매개변수로 받아 사용한다는 점입니다.__</span>
<br>
with는 람다 결과를 제공하지 않고 컨텍스트 개체에서 함수를 호출하는 것이 좋습니다.

<script src="https://gist.github.com/HyungMinKims/4c3df45ec9b7afa2161a34d892d19b08.js"></script>

***
# 5️⃣ let
<br>
<span style="color: #6eb958">__let는 호출 결과에 대해 하나 이상의 함수를 호출하는데 사용 할 수 있습니다.__</span>
<br>
여러 가지 자동차 중 speed가 40이상 인 자동차만 도출 할 경우 밑에 코드 처럼 사용이 가능합니다.

<script src="https://gist.github.com/HyungMinKims/4c942e0f9a49fe03b864c9b594460efb.js"></script>
<br>
또한 블록에 인수로 포함된 단일 함수가 포함된 경우 람다 대신 it을 참조하여 ::를 사용 할 수 있습니다.
<script src="https://gist.github.com/HyungMinKims/c3745ebc78a34b1e5b7bd9f28c102fd2.js"></script>
<br>
let은 null이 아닌 값으로만 코드 블록을 실행하는 데 자주 사용됩니다. null이 아닌 개체에 대해 작업을 수행하는 경우 ? 사용하여 호출 해야합니다.
<script src="https://gist.github.com/HyungMinKims/39b72a1930e27713df54d635dff4fb2a.js"></script>

결과 값은 null을 제외한 자동차 정보가 나옵니다.


***
# 6️⃣ also
<br>
<span style="color: #6eb958">__also는 컨텍스트 개체를 인수로 사용하는 일부 작업을 수행하는데 좋습니다.__<span>
<br>
properties 및 function 아닌 개체에 대한 참조가 필요한 작업 또는 외부 범위에서 also를 숨기고 싶지 않은 경우에 사용 합니다.

<script src="https://gist.github.com/HyungMinKims/346ba36b7effeac69fb1f70307b0f50b.js"></script>

결과 값은 **color 전은 RED color 후은 BLUE**로 변경되었습니다.


***
# 7️⃣ takeif와 takeUnless
<br>
범위 함수 외에도 표준 라이브러리에는 함수 takeIf및 takeUnless. 이러한 함수를 사용하면 호출 체인에 개체 상태 검사를 포함할 수 있습니다.
<br>
<span style="color: #6eb958">__takeIf는 조건이 일치하는 경우 개체를 반환하고 그렇지 않으면 null을 반환합니다.__</span>
<br>
<span style="color: #6eb958">__takeUnless는 조건이 일치하지 않은 경우 개체를 반환하고 일치하면 null을 반환합니다.__</span>
<br>
마지막으로 null이 들어 올 수도 있기 때문에 ? 처리는 필수입니다.

<script src="https://gist.github.com/HyungMinKims/7df40fcc46f551499984d1c40466aa16.js"></script>
***