---
layout: post
title: "[JavaScript] 11. 자바스크립트의 중첩 반복문"
subtitle: "자바스크립트의 중첩 반복문 - 구구단 출력"
author: SeHyeok Park
categories : JavaScript
tags: [JavaScript]
comments : True
---
<div id='preview' class='display-none'>
자바스크립트의 중첩 반복문 - 구구단 출력 예제로 알아보기
</div>

## 1. 중첩 반복문 활용 예제 - 구구단 출력
- **<mark>for문</mark>**
  ```javascript
  for(let i=2; i<=9; i++) {
    for(let j=1; j<=9; j++) {
      console.log(`${i} * ${j} = ${i*j}`);
    }
  } 
  ```
  ***<a href="https://jsfiddle.net/" target="_blank"><span style="color:#707070"><u>> 예문 실행해보기</u></span></a>***
  <br><br>

- **<mark>while문</mark>**
  ```javascript
  let i=2;

  while(i<=9) {
    let j=1;

    while(j<=9) {
      console.log(`${i} * ${j} = ${i*j}`);
      j++;
    }
    i++;
  }
  ```
  ***<a href="https://jsfiddle.net/" target="_blank"><span style="color:#707070"><u>> 예문 실행해보기</u></span></a>***
  <br><br>

- **<mark>do~while문</mark>**
  ```javascript
  let i=2;

  do {
    let j=1;

    do {
      console.log(`${i} * ${j} = ${i*j}`);
      j++;
    } while(j<=9);
    i++;
  } while(i<=9);
  ```
  ***<a href="https://jsfiddle.net/" target="_blank"><span style="color:#707070"><u>> 예문 실행해보기</u></span></a>***
  <br><br>