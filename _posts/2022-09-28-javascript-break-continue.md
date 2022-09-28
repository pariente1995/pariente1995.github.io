---
layout: post
title: "[JavaScript] 12. 자바스크립트의 break문과 continue문"
subtitle: "자바스크립트의 break문 & continue문"
author: SeHyeok Park
categories : JavaScript
tags: [JavaScript]
comments : True
---
<div id='preview' class='display-none'>
자바스크립트의 break문과 continue문 알아보기
</div>

## 1. break문
- 반복문을 강제로 탈출하도록 하는 명령문.

## 1-1. break문 예제
- **<mark>예제</mark>**
  - **Q:** i가 5가 되면, 반복문을 종료하도록 하시오.

  ```javascript
  for(let i=1; i<=10; i++) {
    if(i == 5) break;
    console.log(i);
  }
  ```
  ***<a href="https://jsfiddle.net/" target="_blank"><span style="color:#707070"><u>> 예문 실행해보기</u></span></a>***
  <br><br>

## 2. continue문
- 반복문의 끝으로 이동하여 continue문과 반복문 끝 사이의 구문들을 실행하지 않음.

## 2-1. continue문 예제
- **<mark>예제</mark>**
  - **Q:** i가 3의 배수이면, console 창에 출력되지 않도록 하시오.

  ```javascript
  for(let i=1; i<=100; i++) {
    if(i % 3 == 0) continue;
      console.log(i);
  }
  ```
  ***<a href="https://jsfiddle.net/" target="_blank"><span style="color:#707070"><u>> 예문 실행해보기</u></span></a>***
  <br><br>