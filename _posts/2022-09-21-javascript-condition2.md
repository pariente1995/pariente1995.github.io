---
layout: post
title: "[JavaScript] 6. 자바스크립트의 조건문 - switch ~ case문"
subtitle: "자바스크립트의 switch ~ case문 형식 및 예제 알아보기"
author: SeHyeok Park
categories : JavaScript
tags: [JavaScript]
comments : True
---
<div id='preview' class='display-none'>
자바스크립트의 조건문 중, switch ~ case문 알아보기
</div>

## 1. switch ~ case문 형식

```javascript
switch(조건) {
  case 값:
    실행문;
    break;
  case 값: 
    실행문;
    break;
  ...
  default:
    실행문;
    break;
}
```
<br><br>

## 2. switch ~ case문의 간단한 활용 예제
- **<mark>예제1</mark>**
  - **Q:** 월을 입력하여 월에 대한 계절을 콘솔로 출력하시오.

  ```javascript
  let month = Number(prompt("월을 입력하시오."));
  let season;

  switch(month) {
    case 3: case 4: case 5:
      season = "봄";
      break;
    case 6: case 7: case 8:
      season = "여름";
      break;
    case 9: case 10: case 11:
      season = "가을";
      break;
    case 12: case 1: case 2:
      season = "겨울";
      break;
    default:
      season = "잘못된 월";
  }

  // 최종 결과 출력
  console.log(`${month}월은 ${season}입니다.`);
  ```
  ***<a href="https://jsfiddle.net/" target="_blank"><span style="color:#707070"><u>> 예문 실행해보기</u></span></a>***
  <br><br>

- **<mark>예제2</mark>**
  - **Q:** 현재 시간에 맞는 문자를 알림창으로 출력하시오.<br>(9 - 아침 운동하세요, 14 - 점심을 드세요, 18 - 업무를 정리하고 퇴근하세요)

  ```javascript
  let hour = Number(prompt("현재 시간을 입력하시오."));
  let result;

  switch(hour) {
    case 9: 
    result = "아침 운동하세요.";
      break;
    case 14:
    result = "점심을 드세요.";
      break;
    case 18:
    result = "업무를 정리하고 퇴근하세요.";
      break;
    default:
    result = "할 일이 없습니다.";
      break;
  }

  // 최종 결과 출력
  alert(`${hour}시 입니다. ${result}`);
  ```
  ***<a href="https://jsfiddle.net/" target="_blank"><span style="color:#707070"><u>> 예문 실행해보기</u></span></a>***
  <br><br>

- **<mark>예제3</mark>**
  - **Q:** 국어, 영어, 수학 점수를 입력하여 총점, 평균, 학점을 콘솔로 출력하시오.<br>(학점은 평균이 90점 이상일 때는 A, 80점 이상일 때는 B, 70점 이상일 때는 C, 60점 이상일 때는 D, 60점 미만일 때는 F를 출력하시오.)

  ```javascript
  let kor = Number(prompt("국어 점수를 입력하시오."));
  let eng = Number(prompt("영어 점수를 입력하시오."));
  let mat = Number(prompt("수학 점수를 입력하시오."));

  let tot = Number(kor) + Number(eng) + Number(mat);
  let ave = tot / 3;
  let grade;

  switch (parseInt(ave / 10)) {
    case 10: case 9:
      grade = "A";
      break;
    case 8:
      grade = "B";
      break;
    case 7:
      grade = "C";
      break;
    case 6:
      grade = "D";
      break;
    default:
      grade = "F";
      break;
  }

  // 최종 결과 출력
  console.log("총점: " + tot);
  console.log("평균: " + ave.toFixed(2)); // 소수점 두번째자리까지 표현(반올림)
  console.log("학점: " + grade);
  ```
  ***<a href="https://jsfiddle.net/" target="_blank"><span style="color:#707070"><u>> 예문 실행해보기</u></span></a>***
  <br><br>