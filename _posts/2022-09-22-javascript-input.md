---
layout: post
title: "[JavaScript] 7. 자바스크립트의 입력 함수"
subtitle: "prompt(), confirm() 입력 함수 알아보기"
author: SeHyeok Park
categories : JavaScript
tags: [JavaScript]
comments : True
---
<div id='preview' class='display-none'>
자바스크립트의 2가지 입력 함수 알아보기
</div>

## 1. prompt() 함수
- 대화상자를 통해서 사용자가 원하는 값을 입력하는 함수.

  ```javascript
  let age = Number(prompt("당신의 나이를 입력하시오."));

  if(age >= 19) {
    console.log("당신은 투표권이 있는 나이입니다.");
  } else {
    console.log("당신은 투표권이 없는 나이입니다.");
  }
  ```
  ***<a href="https://jsfiddle.net/" target="_blank"><span style="color:#707070"><u>> 예문 실행해보기</u></span></a>***
  <br><br>

## 2. confirm() 함수
- 대화상자를 통해서 확인일 때는 true, 취소일 때는 false의 결과를 입력하는 함수.

  ```javascript
  let answer = confirm("당신은 나이는 19세이상인가요?");

  if(answer) {
    console.log("당신은 투표권이 있는 나이입니다.");
  } else {
    console.log("당신은 투표권이 없는 나이입니다.");
  }
  ```
  ***<a href="https://jsfiddle.net/" target="_blank"><span style="color:#707070"><u>> 예문 실행해보기</u></span></a>***
  <br><br>