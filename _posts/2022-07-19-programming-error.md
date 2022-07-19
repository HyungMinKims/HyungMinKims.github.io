---
title: "[concepts] Error 종류"
categories:
  - concepts
tag: 
  - concepts
toc: true
toc_sticky: true
toc_label: "Error 종류"
author_profile: true
sidebar:
nav: "docs"
last_modified_at: 2022-07-19T16:38:43-05:00
sitemap :
  changefreq : daily
  priority : 1.0
---
<style>
.rcorners {
  border-radius: 5px;
  border: 2px solid lightslategrey;
  padding: 20px 20px;
  margin-left: 0.5rem;
  width: auto; /* Making auto-sizable width */
  height: auto;
}
</style>
<br>
# 🔎 프로그래밍 에러?

![images](/assets/post/2022-07-19-programming-error/DEFINICIONES.-ERROR-404.jpg){: .align-center}
<br>
<br>
코딩을 하면서 여러가지 에러를 만나 본 경험이 있을 겁니다. 근데 대 다수 프로그래머들은 에러만 고쳐봤지 어떤 에러가 왜 어떤 식으로 발생하여 이 오류는 어떤 에러에 종류이다. 라는 생각까지는 해본 적이 없을
것이라고 생각합니다. 저도 마찬가지로 에러만 고치기 바쁘지 어떤 에러에 종류인지 궁금해 하지 않았습니다. 하지만 에러 종류를 공부하면서 에러 발견 시 어떻게 대처 해야 할지 신속하게 생각 할 수 있었습니다. 본론으로
에러의 종류가 무엇이 있는지 또 어떻게 처리하는 것이 가장 **BEST**인지 알아보도록 하겠습니다.

## 1️⃣ Syntax Error(구문적 오류)

<div class="rcorners">

● 프로그래밍 언어의 <span style="color: red">문법적인 에러</span>를 말합니다.
<br>
● 컴파일 과정에서 나오는 것들이며 <span style="color: red">구문 오류, 컴파일 에러</span>라고도 합니다.
<br>
● 예를 들어 세미콜론 제외, 키워드를 잘못 작성, 괄호를 연 후 닫지 않은 경우가 있습니다.
<br>
● 문법 오류는 컴파일러가 <span style="color: red">어떤 줄에서 발생했는지 알려주기 때문에</span> 비교적 해결이 쉬운 편입니다.
</div>
<br>

● 예시 코드 (javascript)
``` javascript
  cons name = "123"; // cons -> const 에러
```
<br>

● 예시 코드 (java)
``` java
 int a = 10 // 세미콜론이 없음
```
<br>

● 예시 코드 (kotlin)
``` kotlin
 var a = 10
 a.apply{
 this = 20  // 괄호 에러
```
<br>

## 2️⃣ Runtime Error (실행 오류)

<div class="rcorners">

● 프로그램 <span style="color: red">실행 중 발생하여 프로그램이 비정상적으로 종료되게 하는 오류</span>를 말합니다.
<br>
● 프로그램이 실행되는 중 실행할 수 없는 연산을 만나면 발생하는 오류 입니다.
<br>
● <span style="color: red">잘못된 입력이 있는 경우 발생하는 입력오류</span>입니다.
</div>

<br>

● 예시 코드 (java)

``` java
 Scanner sc = new Scanner(System.in);
 int a;
 a = sc.nextInt(); // 입력 : b 입력 시 런타입 에러
```
<br>

## 3️⃣ Semantic Error(의미적 오류)

<div class="rcorners">

● 프로그램 <span style="color: red">문법은 정상적이지만 실행의 결과가 원하는 대로 나오지 않는 오류</span>를 말합니다.
<br>
● 컴파일러가 오류를 잡아주지 않아 사람이 검출해야 해서 다른 오류보다 수정이 어렵습니다.
</div>
<br>

### 🔎 Semantic Error(의미적 오류)와 Logical Error(논리 오류) 차이점
의미적 오류와 논리 오류는 컴파일러는 되는 대신 <span style="color: red">원하는 결과값이 나오지 않는다 </span> 라는 공통점이 있습니다.
<br>
두개의 차이점은 무엇인지 알아보겠습니다. 
<br>
의미적 오류는 예를 들어 계산기 생각 해 보십다. 
<br>__더하기를 할 때 사용하는 변수를 모르고__ 뺏셈 할 때 사용하는 변수를 사용하여 뻇셈을 하는 경우 <span style="color: red">Semantic Error 라고 합니다.</span>
<br>__문제를 잘못 이해하여 더하기를 해야하는 곳에서 뺏기를 하는 경우__ <span style="color: red">Logical Error 라고 합니다.</span>