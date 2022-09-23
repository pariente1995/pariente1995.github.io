---
layout: post
title: "[JavaScript] 2. 자바스크립트의 연산자 종류 및 활용 방법"
subtitle: "산술, 증감, 비교, 논리, 조건 선택, 대입/복합 대입 연산자 알아보기"
author: SeHyeok Park
categories : JavaScript
tags: [JavaScript]
comments : True
---
<div id='preview' class='display-none'>
자바스크립트의 연산자 활용 방법 알아보기
</div>

## 1. 산술 연산자
- +, -, *, / (나누기), % (나머지)
- / (나누기) 연산자: 나눈 결과 전체를 출력(소수점까지 출력)
- **<mark>자바와 자바스크립트의 차이점</mark>**
  - ex) 자바: 10 / 3 = 3, 몫
  - ex) 자바스크립트:  10 / 3 = 3.333333...

```html
<body>
  <script>
    let n1 = 10, n2 = 3;

    console.log("--- 1. 산술 연산자 ---");
    console.log(n1 + n2); // 13
    console.log(n1 - n2); // 7
    console.log(n1 * n2); // 30
    console.log(n1 / n2); // 3.3333333333333335
    console.log(n1 % n2); // 1
  </script>
</body>
```

* **<mark>+ 연산자의 활용</mark>**
  * 덧셈
  * console.log() 함수에서 문자열의 연결을 위해 사용

```html
<body>
  <script>
    let num1 = 15, num2 = 4;
    let str1 = "Javascript", str2 = "Programming";

    console.log(num1 + num2); // 19, 숫자 + 숫자 -> 덧셈
    console.log(str1 + str2); // JavascriptProgramming, 문자열 + 문자열 -> 문자열의 연결
    console.log(str1 + num1); // Javascript15, 문자열 + 숫자(문자열화) -> 문자열로 연결
    console.log(num2 + str2); // 4Programming, 숫자(문자열화) + 문자열 -> 문자열로 연결
    
    console.log(num1 - num2); // 11, 숫자 - 숫자 -> 뺄셈
    console.log(str1 - str2); // 문자열 - 문자열 -> NaN, Not a Number, 숫자로 처리가 불가
  </script>
</body>
```
<br>

## 2. 증감 연산자
- ++, \--
- 자신의 값을 1증가 또는 1감소하는 연산자
- 전위: 먼저 값을 1증가 또는 1감소하고, 참조함. ex) ++n, \--n
- 후위: 먼저 참조하고 난 후, 1증가 또는 1감소함. ex) n++, n\--

```html
<body>
  <script>
    let n1 = 10, n2 = 3;

    console.log("--- 2. 증감 연산자 ---");
    console.log(n1++ + 30); // 10 + 30 = 40
    console.log(n1);        // 11
    console.log(++n1 + 30); // 12 + 30 = 42
  </script>
</body>
```
<br>

## 3. 비교 연산자
- \>, >=, <, <=, ==, !=
- 비교 연산은 참(true) 또는 거짓(false)으로 결과가 나타남.
- ==, != : 값만 비교하여 결과를 판별함.
- ===, !\== : 값과 타입을 모두 비교하여 결과를 판별함.
- **typeof 연산자**: 변수의 타입을 확인하는 연산자

```html
<body>
  <script>
    let num1 = 15, num2 = 3; // 정수
    let num3 = 15.0;         // 실수
    let str1 = "15", str2 = "javascript";

    console.log("--- 3. 비교 연산자 ---");
    console.log(num1 > num2);   // true
    console.log(num1 < num2);   // false
    console.log(num1 == num2);  // false
    console.log(num1 != num2);  // true
 
    console.log(num3 == num1);  // true, 실수 == 정수
    console.log(str2 == num2);  // false
    console.log(str1 == num1);  // true, 문자열 == 정수, 문자열이 숫자로 변환될 수 있다면, 숫자로 비교함, 값만 비교
    console.log(str1 === num1); // false, 값과 타입을 모두 비교


    console.log(typeof num1); // number 타입
    console.log(typeof str1); // string 타입
  </script>
</body>
```
<br>

## 4. 논리 연산자: &&(논리 AND), ||(논리 OR), !(논리 NOT) 
- 논리 AND : 양쪽의 항이 모두 참일 때 참으로 판별함.
- 논리 OR : 양쪽의 항 중 하나만 참이여도 참으로 판별함.
- 논리 NOT : 참은 거짓으로, 거짓은 참으로 바꾸어줌.

```html
<body>
  <script>
    let num1 = 15, num2 = 3; // 정수
    let num3 = 15.0;         // 실수
    let str1 = "15", str2 = "javascript";

    console.log("--- 4. 논리연산자 ---");
    console.log(num1>num2 && num3>num2); // true && true -> true
    console.log(num1>num2 && num3<num2); // true && false -> false
    console.log(num1<num2 && num3<num2); // false && false -> false

    console.log(num1>num2 || num3>num2); // true || true -> true
    console.log(num1>num2 || num3<num2); // true || false -> true
    console.log(num1<num2 || num3<num2); // false || false -> false

    console.log(num1>num2);    // true
    console.log(!(num1>num2)); // false
  </script>
</body>
```
<br>

## 5. 조건 선택 연산자
- (조건 ? 참 : 거짓)
- 조건의 참과 거짓을 판별하는 연산자

```html
<body>
  <script>
    let num1 = 15, num2 = 3; // 정수

    console.log("--- 5. 조건 선택 연산자 ---");
    let result = num1>num2 ? num1 : num2;
    console.log("result = " + result); // result = 15
  </script>
</body>
```
<br>

## 6. 대입 연산자, 복합 대입 연산자
- = : 대입 연산자
- +=, -=, *=, /=, %= : 복합 대입 연산자

```html
<body>
  <script>
    let a = 10, b = 5;

    console.log("--- 6. 복합 대입 연산자 ---");
    a += b; // a = a + b;
    console.log("a = " + a); // a = 15
  </script>
</body>
```

