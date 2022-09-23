---
layout: post
title: "[JavaScript] 8. 자바스크립트의 반복문 - while문"
subtitle: "자바스크립트의 while문 형식 및 예제 알아보기"
author: SeHyeok Park
categories : JavaScript
tags: [JavaScript]
comments : True
---
<div id='preview' class='display-none'>
자바스크립트의 반복문 중, while문 알아보기
</div>

## 1. 자바스크립트 반복문의 종류
- **while, do-while문, for문**
<br><br>

## 2. while문 형식

```javascript
초기값;

while(조건) {
  실행문;
  증감값;
}
```
<br><br>

## 3. while문의 간단한 활용 예제
- **<mark>예제1</mark>**
  - **Q:** 1부터 10까지 1씩 증가하는 정수를 출력하시오.

  ```javascript
  let i = 1;

  while(i<=10) {
    console.log(i);
    i++;
  }
  ```
  ***<a href="https://jsfiddle.net/" target="_blank"><span style="color:#707070"><u>> 예문 실행해보기</u></span></a>***
  <br><br>

- **<mark>예제2</mark>**
  - **Q:** 10부터 1까지 1씩 감소하는 정수를 출력하시오.

  ```javascript
  let i = 10;

  while(i>=1) {
    console.log(i);
    i--;
  }
  ```
  ***<a href="https://jsfiddle.net/" target="_blank"><span style="color:#707070"><u>> 예문 실행해보기</u></span></a>***
  <br><br>

- **<mark>예제3</mark>**
  - **Q:** 1부터 100까지 3씩 증가하는 정수를 출력하시오.

  ```javascript
  let i = 1;

  while(i<=100) {
    console.log(i);
    i += 3;
  }
  ```
  ***<a href="https://jsfiddle.net/" target="_blank"><span style="color:#707070"><u>> 예문 실행해보기</u></span></a>***
  <br><br>

- **<mark>예제4</mark>**
  - **Q:** 1부터 100까지 정수 중에서 짝수를 출력하고, 합과 개수를 출력하시오.

  ```javascript
  let i = 1;
  let sum = 0, cnt = 0;

  while(i<=100) {
    if(i % 2 == 0) {
      console.log(i);
      sum += i;
      ++cnt;
    }
    i++;
  }
  // 최종 결과 출력
  console.log(`합: ${sum}\n개수: ${cnt}`);
  ```
  ***<a href="https://jsfiddle.net/" target="_blank"><span style="color:#707070"><u>> 예문 실행해보기</u></span></a>***
  <br><br>

- **<mark>예제5</mark>**
  - **Q:** 1부터 100까지 정수 중에서 3의 배수이면서 4의 배수인 수를 출력하고, 합과 개수를 출력하시오.

  ```javascript
  let i = 1;
  let sum = 0, cnt = 0;

  while(i<=100) {
    if(i % 12 == 0) {
      console.log(i);
      sum += i;
      ++cnt;
    }
    i++;
  }
  // 최종 결과 출력
  console.log(`합: ${sum}\n개수: ${cnt}`);
  ```
  ***<a href="https://jsfiddle.net/" target="_blank"><span style="color:#707070"><u>> 예문 실행해보기</u></span></a>***
  <br><br>