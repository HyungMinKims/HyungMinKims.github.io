---
title: "[concepts] Error μ’λ₯"
categories:
  - concepts
tag: 
  - concepts
toc: true
toc_sticky: true
toc_label: "Error μ’λ₯"
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
# π νλ‘κ·Έλλ° μλ¬?

![images](/assets/post/2022-07-19-programming-error/DEFINICIONES.-ERROR-404.jpg){: .align-center}
<br>
<br>
μ½λ©μ νλ©΄μ μ¬λ¬κ°μ§ μλ¬λ₯Ό λ§λ λ³Έ κ²½νμ΄ μμ κ²λλ€. κ·Όλ° λ λ€μ νλ‘κ·Έλλ¨Έλ€μ μλ¬λ§ κ³ μ³λ΄€μ§ μ΄λ€ μλ¬κ° μ μ΄λ€ μμΌλ‘ λ°μνμ¬ μ΄ μ€λ₯λ μ΄λ€ μλ¬μ μ’λ₯μ΄λ€. λΌλ μκ°κΉμ§λ ν΄λ³Έ μ μ΄ μμ
κ²μ΄λΌκ³  μκ°ν©λλ€. μ λ λ§μ°¬κ°μ§λ‘ μλ¬λ§ κ³ μΉκΈ° λ°μμ§ μ΄λ€ μλ¬μ μ’λ₯μΈμ§ κΆκΈν΄ νμ§ μμμ΅λλ€. νμ§λ§ μλ¬ μ’λ₯λ₯Ό κ³΅λΆνλ©΄μ μλ¬ λ°κ²¬ μ μ΄λ»κ² λμ² ν΄μΌ ν μ§ μ μνκ² μκ° ν  μ μμμ΅λλ€. λ³Έλ‘ μΌλ‘
μλ¬μ μ’λ₯κ° λ¬΄μμ΄ μλμ§ λ μ΄λ»κ² μ²λ¦¬νλ κ²μ΄ κ°μ₯ **BEST**μΈμ§ μμλ³΄λλ‘ νκ² μ΅λλ€.

## 1οΈβ£ Syntax Error(κ΅¬λ¬Έμ  μ€λ₯)

<div class="rcorners">

β νλ‘κ·Έλλ° μΈμ΄μ <span style="color: red">λ¬Έλ²μ μΈ μλ¬</span>λ₯Ό λ§ν©λλ€.
<br>
β μ»΄νμΌ κ³Όμ μμ λμ€λ κ²λ€μ΄λ©° <span style="color: red">κ΅¬λ¬Έ μ€λ₯, μ»΄νμΌ μλ¬</span>λΌκ³ λ ν©λλ€.
<br>
β μλ₯Ό λ€μ΄ μΈλ―Έμ½λ‘  μ μΈ, ν€μλλ₯Ό μλͺ» μμ±, κ΄νΈλ₯Ό μ° ν λ«μ§ μμ κ²½μ°κ° μμ΅λλ€.
<br>
β λ¬Έλ² μ€λ₯λ μ»΄νμΌλ¬κ° <span style="color: red">μ΄λ€ μ€μμ λ°μνλμ§ μλ €μ£ΌκΈ° λλ¬Έμ</span> λΉκ΅μ  ν΄κ²°μ΄ μ¬μ΄ νΈμλλ€.
</div>
<br>

β μμ μ½λ (javascript)
``` javascript
  cons name = "123"; // cons -> const μλ¬
```
<br>

β μμ μ½λ (java)
``` java
 int a = 10 // μΈλ―Έμ½λ‘ μ΄ μμ
```
<br>

β μμ μ½λ (kotlin)
``` kotlin
 var a = 10
 a.apply{
 this = 20  // κ΄νΈ μλ¬
```
<br>

## 2οΈβ£ Runtime Error (μ€ν μ€λ₯)

<div class="rcorners">

β νλ‘κ·Έλ¨ <span style="color: red">μ€ν μ€ λ°μνμ¬ νλ‘κ·Έλ¨μ΄ λΉμ μμ μΌλ‘ μ’λ£λκ² νλ μ€λ₯</span>λ₯Ό λ§ν©λλ€.
<br>
β νλ‘κ·Έλ¨μ΄ μ€νλλ μ€ μ€νν  μ μλ μ°μ°μ λ§λλ©΄ λ°μνλ μ€λ₯ μλλ€.
<br>
β <span style="color: red">μλͺ»λ μλ ₯μ΄ μλ κ²½μ° λ°μνλ μλ ₯μ€λ₯</span>μλλ€.
</div>

<br>

β μμ μ½λ (java)

``` java
 Scanner sc = new Scanner(System.in);
 int a;
 a = sc.nextInt(); // μλ ₯ : b μλ ₯ μ λ°νμ μλ¬
```
<br>

## 3οΈβ£ Semantic Error(μλ―Έμ  μ€λ₯)

<div class="rcorners">

β νλ‘κ·Έλ¨ <span style="color: red">λ¬Έλ²μ μ μμ μ΄μ§λ§ μ€νμ κ²°κ³Όκ° μνλ λλ‘ λμ€μ§ μλ μ€λ₯</span>λ₯Ό λ§ν©λλ€.
<br>
β μ»΄νμΌλ¬κ° μ€λ₯λ₯Ό μ‘μμ£Όμ§ μμ μ¬λμ΄ κ²μΆν΄μΌ ν΄μ λ€λ₯Έ μ€λ₯λ³΄λ€ μμ μ΄ μ΄λ ΅μ΅λλ€.
</div>
<br>

### π Semantic Error(μλ―Έμ  μ€λ₯)μ Logical Error(λΌλ¦¬ μ€λ₯) μ°¨μ΄μ 
μλ―Έμ  μ€λ₯μ λΌλ¦¬ μ€λ₯λ μ»΄νμΌλ¬λ λλ λμ  <span style="color: red">μνλ κ²°κ³Όκ°μ΄ λμ€μ§ μλλ€ </span> λΌλ κ³΅ν΅μ μ΄ μμ΅λλ€.
<br>
λκ°μ μ°¨μ΄μ μ λ¬΄μμΈμ§ μμλ³΄κ² μ΅λλ€. 
<br>
μλ―Έμ  μ€λ₯λ μλ₯Ό λ€μ΄ κ³μ°κΈ° μκ° ν΄ λ³΄μ­λ€. 
<br>__λνκΈ°λ₯Ό ν  λ μ¬μ©νλ λ³μλ₯Ό λͺ¨λ₯΄κ³ __ λΊμ ν  λ μ¬μ©νλ λ³μλ₯Ό μ¬μ©νμ¬ λ»μμ νλ κ²½μ° <span style="color: red">Semantic Error λΌκ³  ν©λλ€.</span>
<br>__λ¬Έμ λ₯Ό μλͺ» μ΄ν΄νμ¬ λνκΈ°λ₯Ό ν΄μΌνλ κ³³μμ λΊκΈ°λ₯Ό νλ κ²½μ°__ <span style="color: red">Logical Error λΌκ³  ν©λλ€.</span>