---
layout: post
title: "[JSP] 9. JSP Response"
subtitle: "JSP Response 알아보기"
author: SeHyeok Park
categories : JSP
tags: [JSP]
comments : True
---
<div id='preview' class='display-none'>
JSP Response 알아보기
</div>

## 1. Response 내장 객체
- 웹 브라우저로 응답할 정보를 가지고 있는 내장 객체.
<br><br>

## 2. Response 내장 객체의 메소드
##### &emsp; 1. setHeader(name, value): 헤더 정보의 값을 수정하는 메소드, 헤더 정보를 새로 설정할 때 사용.
##### &emsp; 2. setContentType(type): 페이지의 contentType을 설정하는 메소드
##### &emsp; 3. sendRedirect(url): 지정한 url로 이동하는 메소드, 많이 사용하는 메소드
<br>

##### &emsp; * 페이지의 이동 방법
##### &emsp;&emsp; - redirect 방법: 리다이렉팅, 리다이렉트한 페이지로 제어가 이동함. url도 변경됨.
##### &emsp;&emsp; - forward 방법: 포워딩, 포워딩한 페이지로 제어가 이동함. url은 변경되지 않음. -> 액션 태그 부분에서 다시 설명!
<br>

##### &emsp; 4. addCookie(): 쿠키를 설정하는 메소드
&emsp;&emsp; - cookie와 session 부분에서 자세히 설명할 것!
<br><br>

### <span style="color:cornflowerblue">예제</span>
`responseTest01.jsp 파일`

```
<body>
	<h2>response 내장 객체 - 1번 페이지</h2>
	
	현재 페이지는 <b>responseTest01.jsp</b> 페이지입니다.
	
	<%
	response.sendRedirect("responseTest02.jsp");
	%>
</body>
```
<br>

`responseTest02.jsp 파일`

```
<body>
	<h2>response 내장 객체 - 2번 페이지 </h2>
	지금 보고 있는 페이지는 <b>responseTest02.jsp</b> 페이지입니다.
</body>
```

#### <span style="color:cornflowerblue">실행 결과</span>
![실행 결과]({{ site.baseurl }}/assets/img/jsp-result9.png){: width="60%"}