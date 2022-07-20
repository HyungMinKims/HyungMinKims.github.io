---
title: "[javaScript] 비동기 대해 알아보자"
categories:
  - javaScript
tag:
  - javaScript
toc: true
toc_sticky: true
toc_label: "비동기 대해 알아보자"
author_profile: true
sidebar:
  nav: "docs"
last_modified_at: 2022-07-20T12:20:00-05:00
sitemap :
  changefreq : daily
  priority : 1.0
---
<script type="text/javascript">
  let open = false;

  function openFile() {
    open = !open;
    if (open) {
      document.getElementById("callbackExample").style.display = 'block';
      document.getElementById("callbackExampleText").innerHTML = "🔺";
    } else {
      document.getElementById("callbackExample").style.display = 'none';
      document.getElementById("callbackExampleText").innerHTML = "🔻";
    } 
  }
</script>
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

# 💼 비동기이란 무엇인가요? 동기이란 무엇인가요?
## 🔎 비동기
<div class="rcorners">
● 비동기는 동시에 일어나지 않습니다. <span style="color: red">요청과 결과가 동시에 일어나지 않음</span>
<br>
<br>
● 요청한 그 자리에서 결과가 주어지지 않습니다.
<br>
<br>
● <span style="color: aquamarine">장점:</span> 결과가 주어지는데 시간이 걸리더라도 그 동안 다른 작업을 할 수 있어서 자원의 효율적으로 사용 가능합니다.
<br>
<br>
● <span style="color: aquamarine">단점:</span> 설계가 동기식보다 복잡합니다.
</div>
<br>

## 🔎 동기
<div class="rcorners">
● 동기는 <span style="color: red">요청을 보낸 후 응답을 받아야지만</span> 다음 동작이 이루어지는 방식입니다.
<br>
<br>
● 모든 일은 순차적으로 실행되며 어떤 작업이 수행중이라면 다음 작업은 대기하게 됩니다.
<br>
<br>
● <span style="color: aquamarine">장점:</span> 설계가 비동기에 비해 쉽습니다.
<br>
<br>
● <span style="color: aquamarine">단점:</span> 응답이 올 때 까지 대기를 해야하기 때문에 자원을 비 효율적으로 사용 합니다.
</div>
<br>

## 🔎 동기, 비동기 예시

> 출처: [https://simju9397.tistory.com/45](https://simju9397.tistory.com/45)

![image](/assets/post/2022-07-20-javascript-asynchronous/asynchronous_example.jpg){: .align-center}

<br>

윗 사진 예시를 보고 동기와 비동기를 알아보도록 하겠습니다.

<font style="font-size: 20px">💻 동기 </font>
<div class="rcorners">
  ● 첫 번째 손님이 커피를 시켰습니다. 첫 번째 손님의 커피가 나올때 까지 기다립니다.
  <br>
  <br>
  ● 두 번째 손님은 첫 번째 손님이 커피를 받을 때 까지 <b style="color:red">무한정 대기를</b> 해야 합니다.
  <br>
  <br>
  ● 세 번째 손님은 첫 번쨰, 두 번쨰 손님 커피를 받을 떄 까지 <b style="color:red">무한정 대기를</b> 해야 합니다.
</div>

<br>

<font style="font-size: 20px">💻 비동기 </font>
<div class="rcorners">
  ● 첫 번째 손님이 커피를 시켰습니다. 첫 번째 손님이 진동벨을 들고 갑니다.
  <br>
  <br>
  ● <b style="color:red">첫 번째 손님 커피가 나오지 않았지만</b> 카운터에서 두 번쨰 손님의 주문을 받습니다.
  <br>
  <br>
  ● 진동벨이 울리면, 카운터에 가서 커피를 받아옵니다.
</div>

## 🔎 비동기가 필요한 이유

> 굳이 편하게 동기로 만들면 되는데 비동기로 만드는 이유는 무엇일까? 라고 생각을 종종 하는 경우가 있을 겁니다.
> <br> 하지만 여러분들이 서버(server)로 부터 데이터(data)를 받아오는 앱(App)을 만든다고 과정을 해보십다.
> <br> <b style="color:red">동기</b> 로 만든 경우 <b style="color:red">서버에서 데이터를 받아 올때 까지</b> 무한정으로 대기를 해야합니다. 물론 데이터가 적으면 금방 동작합니다.
> <br> 하지만 <b style="color:red">데이터가 많은 경우</b> 앱의 실행속도는 기하급수적으로 느려집니다. 
> <br> <b style="color:red">비동기</b> 로 처리 할 경우 대기 하지않고 다른 일을 할 수 있기 때문에 실행속도는 크게 떨어지지 않습니다.


``` javascript
  console.log(1);
  console.log(2);
  console.log(3);
  
  // 1 2 3
```

``` javascript
  console.log(1);
  setTimeout(() => {
   console.log("[3초 후] 2 출력");
  }, 3000)
  console.log(3);
  
  // 1 3 [3초 후] 2 출력
```
---
# 💼  비동기 종류
## 🔎 Callback
<div class="rcorners">
  ● 이름 그대로 나중에 호출되는 함수입니다.
  <br>

  ● 콜백 함수는 코드를 통해 명시적으로 호출하는 함수가 아니라, <b style="color:red">개발자는 단지 함수를 등록 하기만 하고, 어떤 이벤트가 발생했거나 특정 시점에 도달했을 때 시스템에서 호출하는 함수</b>를 말합니다.
</div>
<br>

<div style="font-size: 20px" onclick="openFile()">콜백에 좀 더 쉽게 이해 해보기 <span id="callbackExampleText">🔻</span>(Click)</div>
<div style="display: none" id="callbackExample">
  <div class="rcorners">
    콜백 함수의 동작 방식은 일종의 식당 자리 예약과 같습니다. 일반적으로 맛집을 가면 사람이 많아 자리가 없습니다. 그래서 대기자 명단에 이름을 쓴 다음에 자리가 날 때까지 주변 식당을 돌아다니죠. 만약 식당에서 자리가 생기면 전화로 자리가 났다고 연락이 옵니다. 그 전화를 받는 시점이 여기서의 콜백 함수가 호출되는 시점과 같습니다. 손님 입장에서는 자리가 날 때까지 식당에서 기다리지 않고 근처 가게에서 잠깐 쇼핑을 할 수도 있고 아니면 다른 식당 자리를 알아볼 수도 있습니다.
    <br>
    <a href="https://joshua1988.github.io/web-development/javascript/javascript-asynchronous-operation/#%EB%A7%88%EB%AC%B4%EB%A6%AC">출저: <span style="color: lightgreen">캡팁판교 비동기/동기</span></a>  
  </div>
</div>

---
### 1️⃣ 콜백 동기, 비동기
콜백 함수에는 synchronous callback (콜백 동기)와 asynchronous callback(비동기 콜백) 두 종류가 있습니다.

<font style="font-size: 20px">💻 Synchronous callback</font>
```javascript
  console.log(1) 
  function printImmediately(print) {
    print();
  }
  printImmediately(() => console.log(2));  
  console.log(3);
```

> 결과 값 : 1 2 3

<br>

<font style="font-size: 20px">💻 asynchronous callback</font>
```javascript
  function printWithDelay(print, timeout) {
    setTimeout(print, timeout);
  }

  printWithDelay(() => console.log(1), 1000); 
  printWithDelay(() => console.log(2), 2000); 
  console.log(3); 
```

> 결과 값 : 3 1 2

### 2️⃣ 콜백 지옥(Callback Hell)
콜백 지옥은 JavaScript를 이용한 비동기 프로그래밍시 발생하는 문제로서, 함수의 매개 변수로 넘겨지는 콜백 함수가 반복되어 코드의 들여쓰기 수준이 감당하기 힘들 정도로 깊어지는 현상을 말합니다.
```javascript
 step1(function (value1) {
    step2(function (value2) {
        step3(function (value3) {
            step4(function (value4) {
                step5(function (value5) {
                    step6(function (value6) {
                        // Do something with value6
                    });
                });
            });
        });
    });
});
```

<div class="rcorners">
  ● 가독성이 떨어짐
  <br>

  ● 비즈니스 로직을 한 눈에 보기 어려움
  <br>

  ● 에러가 발생했을때, 문제를 찾기 어려움
  <br>

  ● 유지보수가 어렵다
  <br>
</div>

---
## 🔎 Promise
<div class="rcorners">
  ● 자바스크립트 비동기 처리에 사용되는 객체입니다.
  <br>

  ● 비동기 처리를 제어하는, 혹은 기존 비동기 처리 코드들을 <b style="color:red">동일한 (표준) API 형태로 사용할 수 있게 해주는 기능</b>입니다.
</div>
<br>

### 1️⃣ 사용 법
```javascript
// resolve:성공, reject:실패
const promise = new Promise((resolve, reject) => {
  // 비동기 작업을 수행한다.

  if (/* 비동기 작업 수행 성공 */) {
    resolve('result');
  }
  else { /* 비동기 작업 수행 실패 */
    reject('failure reason');
  }
});

promise.then(console.log);
```
<br>

<font style="font-size: 20px">💻 producer & consumer</font>
```javascript
//producer 
const promise = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve("hello world!!!!");
    //  reject(new Error('no network'))
  }, 2000);
});

//consumer : then, catch, finally  
promise
  .then((value) => {
    console.log(value);
  })
  .catch((error) => {
    console.log(error);
  })
  .finally(() => {
    console.log("finally");
  });
```
<br>
|상태|의미|구현|
|---|---|---|
|pending |비동기 처리가 아직 수행되지 않은 상태 | resolve 또는 reject 함수가 아직 호출되지 않은 상태|
|fulfilled | 비동기 처리가 수행된 상태 (성공)| resolve 함수가 호출된 상태|
|rejected |비동기 처리가 수행된 상태 (실패) |reject 함수가 호출된 상태 |
|settled | 비동기 처리가 수행된 상태 (성공 또는 실패)| 	resolve 또는 reject 함수가 호출된 상태|

<font style="font-size: 20px">💻 then</font>
<div class="rcorners">
  then 메소드는 두 개의 콜백 함수를 인자로 전달 받습니다. 
  <br>
    <b style="color:#96cbfe">첫 번째 콜백 함수는 성공(fulfilled, resolve 함수가 호출된 상태) 시 호출</b>되고 
  <br>
    <b style="color:#96cbfe">두 번째 함수는 실패(rejected, reject 함수가 호출된 상태) 시 호출</b>됩니다.
</div>
<br>

<font style="font-size: 20px">💻 catch</font>
<div class="rcorners">
  <b style="color:#96cbfe">예외(비동기 처리에서 발생한 에러와 then 메소드에서 발생한 에러)가 발생하면 호출</b> 됩니다.
  <br>
    catch 메소드는 <b style="color:#96cbfe">Promise를 반환합니다.</b>
</div>
<br>

<font style="font-size: 20px">💻 Promise flow chart</font>
![image](/assets/post/2022-07-20-javascript-asynchronous/promise.svg){: .align-center}
> 출처 : MDN
<br>

<font style="font-size: 20px">💻 Promise Chaining</font>
```javascript
const fetchNumber = new Promise((resolve, reject) => {
  setTimeout(() => resolve(1), 1000);
});

fetchNumber
  .then((num) => num * 2) //2
  .then((num) => num * 3) //6
  .then((num) => {
    return new Promise((resolve, reject) => {
      setTimeout(() => resolve(num - 1), 1000); //5 
    });
  })
  .then((num) => console.log(num)); //5

//5 
```
<br>

<font style="font-size: 20px">⛔ Error Handling</font>
```javascript
const getHen = () =>
  new Promise((resolve, reject) => {
    setTimeout(() => resolve("🐓"), 1000);
  });

const getEgg = (hen) =>
  new Promise((resolve, reject) => {
    // setTimeout(() => resolve(`${hen} => 🥚`), 1000);
    setTimeout(() => reject(new Error(`${hen} => 🥚`) ), 1000);
  });

const cook = (egg) =>
  new Promise((resolve, reject) => {
    setTimeout(() => resolve(`${egg} => 🍳`));
  });

getHen() //
  .then(getEgg)
  .catch(error => {
      return '🥖'
  })
  .then(cook)
  .then(console.log)
  .catch(console.log);//🥖 => 🍳
```

## 🔎 async & await
<div class="rcorners">
  ● async와 await는 자바스크립트의 비동기 처리 패턴 중 가장 최근에 나온 문법입니다.
  <br>

  ● 콜백 함수와 프로미스의 단점을 보완하고 <b style="color:red">개발자가 읽기 좋은 코드를 작성할 수 있게</b>도와줍니다.
</div>
<br>

### 1️⃣ 사용 법
<font style="font-size: 20px">💻 async</font>
```javascript
async function f() {
  return Promise.resolve(1);
}

f().then(alert); 
```

<br>

<font style="font-size: 20px">💻 await</font>
```javascript
async function f() {

  let promise = new Promise((resolve, reject) => {
    setTimeout(() => resolve("완료!"), 1000)
  });

  let result = await promise; // 프라미스가 이행될 때까지 기다림 (*)

  alert(result); // "완료!"
}

f();
```

<br>

<font style="font-size: 20px">⚠️일반 함수엔 await을 사용할 수 없습니다.</font>
```javascript
function f() {
  let promise = Promise.resolve(1);
  let result = await promise; // Syntax error
}
```

<br>

<font style="font-size: 20px">⛔ Error Handling</font>
```javascript
async function f() {
  let response = await fetch('http://유효하지-않은-주소');
}

// f()는 거부 상태의 프라미스가 됩니다.
f().catch(alert); // TypeError: failed to fetch // (*)
```