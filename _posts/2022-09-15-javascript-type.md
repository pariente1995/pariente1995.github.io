---
layout: post
title: "[JavaScript] 4. 자바스크립트의 변수 특징 및 자료형"
subtitle: "자바스크립트의 변수 규칙, 선언, 데이터 타입(자료형), 변환 함수 알아보기"
author: SeHyeok Park
categories : JavaScript
tags: [JavaScript]
comments : True
---
<div id='preview' class='display-none'>
자바스크립트의 변수 및 여러 가지의 데이터 타입(자료형) 특징 알아보기
</div>

## 1. 자바스크립트의 변수의 특징
- 데이터 타입이 정해져 있지 않음.
- 값을 입력하면, 입력하는 값에 따라 타입이 결정됨.
<br><br>

## 2. 변수를 만드는 규칙
- 영문자, 숫자, 특수문자(_, $) 사용.
  - <span style="color:red">But) $는 사용하지 않을 것을 권장.</span>
- 영어 대소문자는 구분해서 사용.
- 첫 글자로는 숫자 사용 불가.
- 공백은 사용 불가.
- 자바스크립트의 예약어는 사용 불가.
- ***<mark>변수명은 의미를 파악할 수 있도록 만들 것을 권장 !</mark>***
<br><br>

## 3. 자바스크립트의 변수 선언
- **var**
  - 변수의 중복 선언이 가능하고, 많은 문제점을 야기.
  - 권장하지 않는 방법.

  ```html
  <body>
    <script>
      // 1. var

      var a = 10;
      console.log("a = " + a); // a = 10
      var a = 20; // 변수의 중복 선언 가능 -> 문제점을 야기함.
      console.log("a = " + a); // a = 20
    </script>
  </body>
  ```

- **let**
  - ES6버전부터 사용 가능.
  - 변수의 중복 선언이 불가, 값의 변경은 가능.
  - 권장하는 방법.

  ```html
  <body>
    <script>
      // 2. let

      let b = 20;
      console.log("b = " + b); // b = 20
      //let b = 30; -> 에러, 변수의 중복 선언 불가.
      b = 30; // 값의 변경 가능.
      console.log("b = " + b); // b = 30
    </script>
  </body>
  ```

- **const**
  - constant -> 상수
  - 변수의 중복 선언 불가, 값의 변경 불가.
  - 변수를 선언하면서 값을 초기화하면, 이후 값의 변경이 불가.

  ```html
  <body>
    <script>
      // 3. const
      
      const c = 30;
      console.log("c = " + c); // c = 30
      //const c = 30; -> 에러, 변수의 중복 선언 불가.
      //c = 40; -> 에러, 값의 변경 불가.

      //const d; -> 에러, const 상수는 선언하면서 초기화하여 사용해야 함.
      const d = 40;
      console.log("d = " + d); // d = 40
    </script>
  </body>
  ```
<br>

## 4. 변수의 데이터 타입(자료형)
- **number :** 숫자형, 정수와 실수를 모두 포함.
- **string :** 문자열형, 문자와 문자열의 구분없이 사용 가능, \' \'(홑따옴표), \" \"(쌍따옴표) 모두 사용 가능.
- **boolean :** 논리형, 비교 연산, 논리 연산의 결과를 true, false 로 판별함.
- **undefined :** 변수의 어떠한 값도 저장되지 않은 상태.

<hr>

- ***<mark>null 값(object 타입)</mark> :*** null이라는 값이 저장된 상태, 초기화하는 용도로 사용, 객체 타입.
- ***<mark>NaN 값(number 타입)</mark> :*** Not a Number, 숫자로 계산할 수 없는 값, number 타입.

```html
<body>
  <script>
    // 변수의 타입 확인

    let s1 = "javascript", n1 = 20, n2 = 20.0, b1 = true;
    let x;
    let y = null;
    let s2 = "10",  s3 = "ten";

    console.log(s1 + ", " + typeof(s1));   // javascript, string 타입
    console.log(n1 + ", " + typeof(n1));   // 20, number 타입
    console.log(n2 + ", " + typeof(n2));   // 20, number 타입
    console.log(b1 + ", " + typeof(b1));   // true, boolean 타입
    console.log(x  + ", " + typeof(x));    // undefined, undefined 타입 -> 변수의 어떠한 값도 저장되지 않은 상태
    console.log(y  + ", " + typeof(y));    // null, object 타입 -> null이라는 값이 저장된 상태
    console.log(s2 + ", " + typeof(s2));   // 10, string 타입
    console.log(++s2 + ", " + typeof(s2)); // 11, number 타입 -> string에서 number로 타입 변경
    console.log(++s3); // NaN(Not a Number)
    console.log(typeof(NaN)); // number 타입
  </script>
</body>
```
<br>

## 5. 데이터 타입(자료형) 예제
- **number(숫자형)**
  - 정수는 15자리까지, 실수는 소수점 이하 15자리까지 정확하게 표현함.
  - 정수와 실수를 구분하지 않음.

  ```html
  <body>
    <script>
      // number(숫자형)

      let n1 = 9999999999 // 99억
      let n2 = 99999999999 // 999억
      let n3 = 999999999999 // 9999억
      let n4 = 9999999999999 // 9조 9999억
      let n5 = 99999999999999 // 99조 9999억
      let n6 = 999999999999999 // 999조 9999억, 15개
      let n7 = 9999999999999999 // 9999조 9999억, 16개
      console.log(n1); // 9999999999
      console.log(n2); // 99999999999
      console.log(n3); // 999999999999
      console.log(n4); // 9999999999999
      console.log(n5); // 99999999999999
      console.log(n6); // 999999999999999 -> 15개, 정확하게 표현
      console.log(n7); // 10000000000000000 -> 16개, 정확하게 표현하지 않음
      console.log(10 / 3); // 3.3333333333333335, 소수점 15자리까지 정확도를 보장

      // 지수승 표현
      let x1 = 3.14;
      let x2 = 314e-2; // 314 * 10의 -2승
      let y1 = 123450000000000
      let y2 = 12345e10; // 12345 * 10의 10승
      
      console.log(x1); // 3.14
      console.log(x2); // 3.14
      console.log(y1); // 123450000000000
      console.log(y2); // 123450000000000
    </script>
  </body>
  ```

- **string(문자열)**
  - \' \', \" \" 모두 사용 가능.
  - 문자와 문자열의 구분이 없음.

  ```html
  <body>
    <script>
      // string(문자열)
      let s1 = "Javascript";
      let s2 = "Web Programming";
      let s3 = "한국대학교 '컴퓨터공학' 전공";
      let s4 = '한국대학교 "컴퓨터공학" 전공';

      console.log(s1 + ", " + typeof(s1)); // Javascript, string
      console.log(s2 + ", " + typeof(s2)); // Web Programming, string
      console.log(s3); // 한국대학교 '컴퓨터공학' 전공
      console.log(s4); // 한국대학교 "컴퓨터공학" 전공
      console.log("문자열의 길이: " + s1.length); // 문자열의 길이: 10
      console.log("문자열의 길이: " + s4.length); // 문자열의 길이: 16
      console.log("s2의 첫글자: " + s2[0]); // s2의 첫글자: W -> 자바와는 달리 문자열을 배열처럼 사용할 수 있다.
      console.log("s2의 끝글자: " + s2[s2.length-1]); // s2의 끝글자: g
    </script>
  </body>
  ```

- **boolean(논리형)**
  - 비교, 논리 연산에 대해 결과를 true, false로 나누어 판별함.
  - 자바스크립트에서는 모든 데이터를 boolean값으로 판별할 수 있음.

  ***[ 모든 데이터를 논리값으로 판별하는 방법 ]***
  - Boolean() 함수: 모든 데이터를 논리값으로 판별할 수 있도록 하는 함수
  - 숫자: 0은 false, 0 이외의 모든 숫자: true
  - 문자열: 빈 문자열은 false, 이외의 모든 문자열은 true
  - undefined, null, NaN은 false
  - object 타입은 true
  - 배열은 object 타입, true
  - 함수는 function 타입, true

  ```html
  <body>
    <script>
      // boolean(불린형, 논리형)

      let n1 = 0, n2 = 23, n3 = -55, n4 = 3.14;
      let s1 = "Javascript", s2 = "", s3 = " ";
      let obj1, obj2 = null, obj3 = new Object();
      let s4 = "ten" * 10;

      console.log(n1 + ", " + typeof(n1)); // 0, number
      console.log(n2 + ", " + typeof(n2)); // 23, number
      console.log(n3 + ", " + typeof(n3)); // -55, number
      console.log(n4 + ", " + typeof(n4)); // 3.14, number
      console.log(n1 + ", " + Boolean(n1)); // 0, false
      console.log(n2 + ", " + Boolean(n2)); // 23, true
      console.log(n3 + ", " + Boolean(n3)); // -55, true
      console.log(n4 + ", " + Boolean(n4)); // 3.14, true
      console.log("----------");
      console.log(s1 + ", " + typeof(s1)); // Javascript, string
      console.log(s2 + ", " + typeof(s2)); // , string
      console.log(s3 + ", " + typeof(s3)); //  , string
      console.log(s1 + ", " + Boolean(s1)); // Javascript, true
      console.log(s2 + ", " + Boolean(s2)); // 빈 문자열, false
      console.log(s3 + ", " + Boolean(s3)); // 공백 한 칸, true
      console.log("----------");
      console.log(obj1 + ", " + typeof(obj1));  // undefined, undefined
      console.log(obj2 + ", " + typeof(obj2));  // null, object
      console.log(obj3 + ", " + typeof(obj3));  // [object Object], object
      console.log(s4 + ", " + typeof(s));       // NaN, undefined
      console.log(obj1 + ", " + Boolean(obj1)); // undefined, false
      console.log(obj2 + ", " + Boolean(obj2)); // null, false
      console.log(obj3 + ", " + Boolean(obj3)); // [object Object], true
      console.log(s4 + ", " + Boolean(s4))      // NaN, false
      console.log("----------");
      console.log(typeof([1, 2, 3, 4, 5]));  // object, 배열도 객체형
      console.log(typeof(function(){}));     // function, 함수는 함수형
      console.log(Boolean([1, 2, 3, 4, 5])); // true
      console.log(Boolean(function(){}));    // true
    </script>
  </body>
  ```
<br>

## 6. 데이터 타입(자료형) 변환 함수
- **1. 논리형 변환 함수**
  - Boolean() - 모든 데이터를 논리값으로 판별하는 함수.<br><br>

- **2. 숫자형 변환 함수**
  - Number() - 데이터를 숫자형으로 변환하는 함수.
  - parseInt() - 데이터를 정수로 변환하는 함수.
  - parseFloat() - 데이터를 실수로 변환하는 함수.<br><br>
  
- **3. 문자형 변환 함수**
  - 모든 데이터를 문자열로 변환하는 함수.
  - 값.toString()

```html
<body>
  <script>
    // 자동 형변환

    console.log(7+", " + typeof(7));                   // 7, number
    console.log(7+null + ", " + typeof(7+null));       // 7, number
    console.log("7"+null + ", " + typeof("7"+null));   // 7null, string
    console.log("7"+2 + ", " + typeof("7"+2));         // 72, string
    console.log(7+"2" + ", " + typeof(7+"2"));         // 72, string
    console.log(7+"hello" + ", " + typeof(7+"hello")); // 7hello, string
    console.log("----------");

    console.log(7 - 2 + ", " + typeof(7-2));           // 5, number
    console.log("7"-2 + ", " + typeof("7"-2));         // 5, number
    console.log(7-"2" + ", " + typeof(7-"2"));         // 5, number
    console.log("7"-"2" + ", " + typeof("7"-"2"));     // 5, number
    console.log("----------");

    console.log("7"*2 + ", " + typeof("7"*2));         // 14, number
    console.log(7*"2" + ", " + typeof(7*"2"));         // 14, number
    console.log("7"*"2" + ", " + typeof("7"*"2"));     // 14, number
    console.log("sever"*2 + ", " + typeof("sever"*2)); // NaN, number
    console.log("----------");

    console.log("7"/2 + ", " + typeof("7"/2));         // 3.5, number
    console.log(7/"2" + ", " + typeof(7/"2"));         // 3.5, number
    console.log("7"/"2" + ", " + typeof("7"/"2"));     // 3.5, number
    console.log("sever"/2 + ", " + typeof("sever"/2)); // NaN, number

    // 형변환 함수

    let n1 = 3.14, n2 = 20, n3 = -100, n4 = 0;
    let s1 = "58", s2 = "3.456", s3 = "hello";
    let b1 = true, b2 = false;
    let s4 = ""; // 빈 문자열
    let s5 = null; // null, 객체형
    let s6 = new Object(); // 객체형

    console.log(s1 + n1);             // 583.14, 문자열 연결
    console.log(s1 - n1);             // 54.86, 자동 형 변환
    console.log(Number(s1) + n1);     // 61.14, 형 변환
    console.log(parseInt(s1) + n1);   // 61.14
    console.log(parseFloat(s1) + n1); // 61.14
    console.log("----------");

    console.log(s2 + n2);             // 3.45620, 문자열 연결
    console.log(s2 - n2);             // -16.544, 자동 형 변환
    console.log(Number(s2) + n2);     // 23.456, 형 변환
    console.log(parseInt(s2) + n2);   // 3 + 20 -> 23, 소수점 이하를 캐스팅
    console.log(parseFloat(s2) + n2); // 23.456
    console.log(Number(s3) + n2);     // NaN
    console.log("----------");

    console.log(n1 + ", " + typeof(n1)); // 3.14, number
    console.log(Boolean(n1)); // true
    console.log(Boolean(n2)); // true
    console.log(Boolean(n3)); // true
    console.log(Boolean(n4)); // false
    console.log("----------");

    console.log(n1.toString() + ", " + typeof(n1.toString())); // 3.14, string
    console.log(b1 + ", " + typeof(b1));                       // true, boolean
    console.log(b1.toString() + ", " + typeof(b1.toString())); // true, string
    console.log("----------");

    console.log(s4 + ", " + typeof(s4), ", " + Boolean(s4)); // , string, false
    console.log(s5 + ", " + typeof(s5), ", " + Boolean(s5)); // null, object , false
    console.log(s6 + ", " + typeof(s6), ", " + Boolean(s6)); // [object Object], object , true
  </script>
</body>
```
