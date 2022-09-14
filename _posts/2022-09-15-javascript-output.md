---
layout: post
title: "[JavaScript] 3. 자바스크립트의 출력 함수"
subtitle: "alert(), document.write(), console.log() 출력 함수 알아보기"
author: SeHyeok Park
categories : JavaScript
tags: [JavaScript]
comments : True
---
<div id='preview' class='display-none'>
자바스크립트의 3가지 출력 함수 알아보기
</div>

## 1. alert() 함수
- 함수 안의 메시지를 알림창을 통해서 출력.

```html
<body>
  <h3>--- alert() 함수 ---</h3>
  <button onclick="alert('알림 버튼을 눌렀습니다.');">알림 버튼</button><br>
    <script>
      alert("출력 함수를 통해 내용을 출력합니다.");
    </script>
</body>
```

## 2. document.write() 함수
- 함수 안의 내용을 웹페이지로 출력.
- HTML & CSS 태그를 적으면, 태그를 적용하여 출력.

```html
<body>
  <h3>--- document.write() 함수 ---</h3>
    <script>
      document.write("출력함수를 통해 내용을 출력합니다.");
    </script>
</body>
```

## 3. console.log() 함수
- 함수 안의 결과를 콘솔창으로 출력. (크롬에서 F12번을 눌러 콘솔Tab에서 확인)
- 자바스크립트의 문법, 계산 등을 확인하는 용도로 사용.

```html
<body>
  <h3>--- console.log() 함수 ---</h3>
    <script>
      let a = 10, b = 20;
      let sum = a + b;

      console.log("합계: ", sum);
    </script>
</body>
```