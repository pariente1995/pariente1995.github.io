---
layout: post
title: "[JavaScript] 5. 자바스크립트의 조건문 - if문"
subtitle: "자바스크립트의 if문 형식 및 예제 알아보기"
author: SeHyeok Park
categories : JavaScript
tags: [JavaScript]
comments : True
---
<div id='preview' class='display-none'>
자바스크립트의 조건문 중, if문 알아보기
</div>

## 1. 자바스크립트의 조건문
- **if문**
- **switch ~ case문** 
- *자바의 문법과 거의 동일*
<br><br>

## 2. if문 형식
- **조건이 1개인 경우**

  ```javascript
  if(조건) {
    조건이 참일 때 실행문;
  }
  ```

- **조건이 2개인 경우**

  ```javascript
  if(조건) {
    조건이 참일 때의 실행문;
  } else {
    조건이 거짓일 때의 실행문;
  }
  ```

- **조건이 3개인 경우**

  ```javascript
  if(조건1) {
    조건1이 참일 때의 실행문;
  } else if(조건2) {
    조건2가 참일 때의 실행문;
  } else {
    조건1과 조건2가 모두 거짓일 때의 실행문;
  }
  ```

- **조건이 4개 이상인 경우**

  ```javascript
  if(조건1) {
    조건1이 참일 때의 실행문;
  } else if(조건2) {
    조건2가 참일 때의 실행문;
  } else if(조건3) {
    조건3이 참일 때의 실행문;
  } else {
    조건1, 조건2, 조건3이 모두 거짓일 때의 실행문;
  }
  ```
<br><br>

## 3. if문의 간단한 활용 예제
- **<mark>예제1 - 조건이 1개인 경우</mark>**
  - **Q:** 점수가 80점 이상일 때, \"시험을 통과하였습니다.\" 라는 메시지를 출력하도록 하시오.

  ```javascript
  let scores = 85;

  if(scores >= 80) {
    console.log("시험을 통과하였습니다.");
  }
  ```
  ***<a href="https://jsfiddle.net/" target="_blank"><span style="color:#707070"><u>> 예문 실행해보기</u></span></a>***
  <br><br>

- **<mark>예제2 - 조건이 2개인 경우</mark>**
  - **Q:** 점수가 80점 이상일 때 \"합격입니다.\"라는 메시지를 출력하고, 80점 미만일 때 \"불합격입니다.\"라는 메시지를 출력하도록 하시오.

  ```javascript
  let score = 75;

  if(score > 80) {
    console.log("합격입니다.");
  } else {
    console.log("불합격입니다.");
  }
  ```
  ***<a href="https://jsfiddle.net/" target="_blank"><span style="color:#707070"><u>> 예문 실행해보기</u></span></a>***
  <br><br>

- **<mark>예제3 - 조건이 3개인 경우</mark>**
  - **Q:** 점수가 90점이상일 때는 \"최우수\", 80점 이상일 때는 \"우수\", 80점미만일 때는 \"보통\"이라는 메시지를 출력하시오.

  ```javascript
  let score = 90;

  if(score >= 90) {
    console.log("최우수");
  } else if(score >= 80) {
    console.log("우수");
  } else {
    console.log("보통");
  }
  ```
  ***<a href="https://jsfiddle.net/" target="_blank"><span style="color:#707070"><u>> 예문 실행해보기</u></span></a>***
  <br><br>

- **<mark>예제4 - 조건이 4개 이상인 경우</mark>**
  - **Q:** 점수가 90점이상일 때 \"A학점\", 80점이상일 때 \"B학점\", 70점이상일 때 \"C학점\", 60점이상일 때, \"D학점\", 60점 미만일 때 \"F학점\"을 출력하시오.

  ```javascript
  let score = 55;

  if(score >= 90) {
    console.log("A학점");
  } else if(score >= 80) {
    console.log("B학점");
  } else if(score >= 70) {
    console.log("C학점");
  } else if(score >= 60) {
    console.log("D학점");
  } else {
    console.log("F학점");
  }
  ```
  ***<a href="https://jsfiddle.net/" target="_blank"><span style="color:#707070"><u>> 예문 실행해보기</u></span></a>***
  <br><br>

