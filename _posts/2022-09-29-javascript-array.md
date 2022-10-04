---
layout: post
title: "[JavaScript] 13. 자바스크립트의 배열"
subtitle: "자바스크립트의 배열(Array) 알아보기"
author: SeHyeok Park
categories : JavaScript
tags: [JavaScript]
comments : True
---
<div id='preview' class='display-none'>
자바스크립트의 배열(Array) 사용법 알아보기
</div>

## 1. 배열 (Array)
- (여러 가지 타입의) 변수의 집합.
<br><br>

## 2. 배열의 선언 및 생성
- **[ ] 배열 기호를 사용**
  ```javascript
  let a1 = []; // 빈 배열
  let a2 = [10, 20, 30, 40, 50]; // 정수 5개를 갖는 배열
  let a3 = ["자료구조", 84, "웹프로그래밍", 92, "알고리즘", 76] // 문자열과 정수를 모두 저장한 배열

  console.log(a1);
  console.log(typeof a1); // object
  console.log(a2);
  console.log(typeof a2); // object
  console.log(a3);
  console.log(typeof a3); // object
  ```
  ***<a href="https://jsfiddle.net/" target="_blank"><span style="color:#707070"><u>> 예문 실행해보기</u></span></a>***
  <br><br>

- **Array() 생성자 함수를 사용**
  ```javascript
  let b1 = new Array(); // 빈 배열
  let b2 = new Array(10, 20, 30, 40, 50); // 정수 5개를 갖는 배열
  let b3 = new Array("자료구조", 84, "웹프로그래밍", 92, "알고리즘", 76); // 문자열과 정수를 모두 저장한 배열

  console.log(b1);
  console.log(typeof b1); // object
  console.log(b2);
  console.log(typeof b2); // object
  console.log(b3);
  console.log(typeof b3); // object
  ```
  ***<a href="https://jsfiddle.net/" target="_blank"><span style="color:#707070"><u>> 예문 실행해보기</u></span></a>***
  <br><br>

## 3. 배열 관련 정보 확인
- **배열의 모든 정보 확인 - 콘솔**
  ```javascript
  let months = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12];
  let weeks = ["Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat"];
  let seasons = ["Spring", "Summer", "Autumn", "Winter"];

  console.log(months);
  console.log(weeks);
  console.log(seasons);
  ```
  ***<a href="https://jsfiddle.net/" target="_blank"><span style="color:#707070"><u>> 예문 실행해보기</u></span></a>***
  <br><br>

- **배열의 모든 정보 확인 - 웹**
  ```javascript
  let months = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12];
  let weeks = ["Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat"];
  let seasons = ["Spring", "Summer", "Autumn", "Winter"];

  document.write(months + "<br>");
  document.write(weeks + "<br>");
  document.write(seasons + "<br>");
  ```
  ***<a href="https://jsfiddle.net/" target="_blank"><span style="color:#707070"><u>> 예문 실행해보기</u></span></a>***
  <br><br>

- **배열의 길이 확인**
  ```javascript
  let seasons = ["Spring", "Summer", "Autumn", "Winter"];

  console.log("길이: " + seasons.length); // 길이: 4
  ```
  ***<a href="https://jsfiddle.net/" target="_blank"><span style="color:#707070"><u>> 예문 실행해보기</u></span></a>***
  <br><br>

- **배열의 각 요소 확인**
  ```javascript
  let seasons = ["Spring", "Summer", "Autumn", "Winter"];

  console.log(seasons[0]); // Spring
  console.log(seasons[1]); // Summer
  console.log(seasons[2]); // Autumn
  console.log(seasons[3]); // Winter
  console.log(seasons[4]); // undefined
  console.log(typeof seasons[4]) // undefined
  ```
  ***<a href="https://jsfiddle.net/" target="_blank"><span style="color:#707070"><u>> 예문 실행해보기</u></span></a>***
  <br><br>

- **반복문을 통한 배열 요소 확인**
  ```javascript
  let seasons = ["Spring", "Summer", "Autumn", "Winter"];
  
  for(let i=0; i<seasons.length; i++) {
    console.log(`${i}번 요소: ${seasons[i]}`);
  }
  ```
  ***<a href="https://jsfiddle.net/" target="_blank"><span style="color:#707070"><u>> 예문 실행해보기</u></span></a>***
  <br><br>