---
layout: post
title: "[JavaScript] 1. 자바스크립트의 간략한 정보 및 작성 방법"
subtitle: "자바스크립트에 대한 대략적인 정보와 자바스크립트의 다양한 작성 방법 알아보기"
author: SeHyeok Park
categories : JavaScript
tags: [JavaScript]
comments : True
---
<div id='preview' class='display-none'>
자바스크립트의 역사 및 응용 API, 작성 방법 알아보기
</div>

## 1. 자바스크립트의 역사
- 1990년대 생성, 2000년 중반 급부상.
- 넷스케이프 회사에서 개발, 개발명(mocha) -> 라이브 스크립트(live script).
- 썬마이크로시스템사와 함께 개발 -> 자바스크립트(Javascript).
- 자바스크립트를 ECMA스크립트라고도 부른다.

**[ ECMA(European Computer Manufacturers Association) ]**
- 유럽 컴퓨터 제조업자 협회.
- ECMAScript1~5, ECMAScript6(2015), ECMAScript2020, ECMAScript2022 등의 버전이 있다.
- ECMAScript를 줄여서 약자로 ES라고 사용.
<br><br>

## 2. 자바스크립트 응용 API
- 프론트엔드 영역에서 프레임워크로 사용하는 API.
- angular.js(구글), react.js, vue.js
  - 이 중에서 react.js가 가장 많이 사용됨.
- node.js - 서버와도 연결이 가능.
- jQuery - 자바스크립트 핵심 기능을 좀 더 쉽게 구현할 수 있도록 하는 API.

**[ 바닐라 스크립트(Vanilla Script) ]**
- 순수한 자바스크립트만을 개발해 보자는 취지의 자바스크립트.
<br><br>

## 3. 자바스크립트 작성 방법
#### 1. 내부 자바스크립트 작성 방법
- 1-1. body 영역 안에서 자바스크립트 작성
  - 장점: 필요한 내용을 바로 적용하여 결과를 파악할 수 있음.
  - 단점: 관리가 어려움.

```html
<body>
  <script>
     document.write("Welcome to Javascript!!!");
  </script>
</body>
```

<br>

- 1-2. head 영역 안에 자바스크립트 작성
  - 전체 html 문서에 자바스크립트를 적용하고자 하는 경우

```html
<head>
  <meta charset="UTF-8">
    <script>
    let text = "자바스크립트의 세상에 오신 것을 환영합니다!!!";

    function welcome (target) {
      document.write(target);
    }
  </script>
</head>
<body>
  <script>
    welcome(text);
  </script>
</body>
```
<br><br>

#### 2. 외부 자바스크립트 작성 방법
***<mark>실무적으로는 자바스크립트 파일을 따로 나누어 관리하는 것이 원칙!</mark>***
- 장점: html 문서 간결, 자바스크립트 파일의 관리가 용이.
- 단점: 코드를 바로 확인하기 불편함(자바스크립트 파일을 찾아야 한다).

`js_basic01.js 파일`

```javascript
let text = "자바스크립트의 세상에 오신 것을 환영합니다!!!";

function welcome() {
  document.write(text);
}

welcome();
```

<br>

```html
<body>
  <script src="js_basic01.js"></script>
</body>
```
<br><br>

#### 3. 인라인 자바스크립트 작성 방법
***최근에는 지양하는 방법이지만, 오랫동안 많이 써왔던 방법이기에 알아두어야 한다!***
```html
<body>
  <button onclick="alert('Welcome to Javascript!!!');">Javascript</button>
</body>
```
<br><br>

#### 4. 내부&인라인 자바스크립트 작성 방법
```html
<body>
  <button onclick="welcome(text);">Javascript</button>
</body>
```


