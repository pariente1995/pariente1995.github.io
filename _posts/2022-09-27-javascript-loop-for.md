---
layout: post
title: "[JavaScript] 10. 자바스크립트의 반복문 - for문"
subtitle: "자바스크립트의 for문 형식 및 예제 알아보기"
author: SeHyeok Park
categories : JavaScript
tags: [JavaScript]
comments : True
---
<div id='preview' class='display-none'>
자바스크립트의 반복문 중, for문 알아보기
</div>

## 1. for문 형식

```javascript
for(초기값; 조건; 증감값) {
  실행문;
}
```
<br>

## 2. for문의 간단한 활용 예제
- **<mark>예제1</mark>**
  - **Q:** 1부터 10까지 1씩 증가하는 정수를 출력하시오.

  ```javascript
  for(let i=1; i<=10; i++) {
    console.log(i);
  }
  ```
  ***<a href="https://jsfiddle.net/" target="_blank"><span style="color:#707070"><u>> 예문 실행해보기</u></span></a>***
  <br><br>

- **<mark>예제2</mark>**
  - **Q:** 10부터 1까지 1씩 감소하는 정수를 출력하시오.

  ```javascript
  for(let i=10; i>=1; i--) {
    console.log(i);
  }
  ```
  ***<a href="https://jsfiddle.net/" target="_blank"><span style="color:#707070"><u>> 예문 실행해보기</u></span></a>***
  <br><br>

- **<mark>예제3</mark>**
  - **Q:** 1부터 100까지 3씩 증가하는 정수를 출력하시오.

  ```javascript
  for(let i=1; i<=100; i+=3) {
    console.log(i);
  }
  ```
  ***<a href="https://jsfiddle.net/" target="_blank"><span style="color:#707070"><u>> 예문 실행해보기</u></span></a>***
  <br><br>

- **<mark>예제4</mark>**
  - **Q:** 1부터 100까지 정수 중에서 짝수를 출력하고, 합과 개수를 출력하시오.

  ```javascript
  let sum = 0, cnt = 0;

  for(let i=1; i<=100; i++) {
    if(i % 2 == 0){
      console.log(i);
      sum += i;
      ++cnt;
    }
  }

  console.log(`합: ${sum}\n개수: ${cnt}`);
  ```
  ***<a href="https://jsfiddle.net/" target="_blank"><span style="color:#707070"><u>> 예문 실행해보기</u></span></a>***
  <br><br>

- **<mark>예제5</mark>**
  - **Q:** 1부터 100까지 정수 중에서 3의 배수이면서 4의 배수인 수를 출력하고, 합과 개수를 출력하시오.

  ```javascript
  let sum = 0, cnt = 0;

  for(let i=1; i<=100; i++) {
    if(i % 12 == 0){
      console.log(i);
      sum += i;
      ++cnt;
    }
  }

  console.log(`합: ${sum}\n개수: ${cnt}`);
  ```
  ***<a href="https://jsfiddle.net/" target="_blank"><span style="color:#707070"><u>> 예문 실행해보기</u></span></a>***
  <br><br>