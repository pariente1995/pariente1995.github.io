---
layout: post
title: "[JSP] 3. JSP Directive(디렉티브)"
subtitle: "JSP Directive(디렉티브) 알아보기"
author: SeHyeok Park
categories : JSP
tags: [JSP]
comments : True
---
<div id='preview' class='display-none'>
JSP Directive(디렉티브) 알아보기
</div>

## 1. 디렉티브(directive)
- 지시어, 지시문
- 형식: <%@ %>
- 역할: JSP 페이지의 기본적인 환경 설정

## 2. 디렉티브의 종류
### - page, include, taglib
<br>

#### (1) page directive
- info: 페이지의 설명 -> getServletInfo() 메소드로 정보를 리턴
- language: JSP 페이지에서 사용하는 언어, 기본값: java
- contentType: 문서의 타입, 기본값: "text/html; charset=UTF-8"
- pageEncoding: 해당 페이지의 문자 인코딩, 기본값: "UTF-8"
- extends: 상속받을 클래스를 지정할 때 사용
- <mark>★import★</mark>: 다른 패키지에 있는 클래스를 사용하고자 할 때 -> 자주사용
- session: 세션의 사용 여부를 지정, 기본값: true
- buffer: 버퍼의 크기를 지정, 기본값: 8KB
- autoFlush: 출력버퍼가 다 찼을 때 버퍼의 내용을 처리하는 속성, 기본값: true
- isThreadSafe: 다중 쓰레드를 허용할지의 여부, 기본값: true
- errorPage: 현재 페이지에서 에러가 발생했을 때, 에러를 처리할 페이지를 지정하는 속성, 사용불가
- isErrorPage: 현재 페이지를 에러 페이지로 지정하는 속성, 기본값: false, 사용불가<br><br>

- <span style="color:red">errorPage, isErrorPage는 JSP 2.0부터 사용되지 않음, Tomcat 5.5.9 버전 이상에서는 사용불가</span>
<br><br>

#### (2) include directive
- 여러 페이지에 공통적인 내용이 있을 때, 그 페이지를 따로 저장해 두고 필요할 때마다 삽입하여 사용하는 기능
- 정적인 페이지 작성 방법 -> 사용되지 않는 방법
- 동적인 페이지 작성 방법 -> include Action Tag(액션 태그) -> 많이 사용하는 방법
<br><br>

#### (3) taglib directive
- EL, JSTL, Custom Tag를 활용할 때 사용
<br><br>

### <span style="color:cornflowerblue">예제1</span>
```
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<%@ page info="디렉티브의 기능을 설명하는 페이지"%>
<%@ page import="java.sql.Timestamp"%>
<!DOCTYPE html>

...(중략)

<body>
	<h1>디렉티브 연습 1(page)</h1>
	<%
	Timestamp now = new Timestamp(System.currentTimeMillis());
	%>
	현재 날짜와 시간은 <%=now %>입니다.<br>
	이 페이지는 <b><%=getServletInfo() %></b>입니다.<br>
</body>
```

#### <span style="color:cornflowerblue">실행 결과</span>
![디렉티브 실행 결과 1]({{ site.baseurl }}/assets/img/jsp-post1-1.png){: width="60%"}
<br>

### <span style="color:cornflowerblue">예제2</span>
`directive02_top.jsp 파일`

```
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<%@ page import="java.sql.Timestamp"%>
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>directive_top</title>
</head>
<body>
	<h3>Top Page</h3>
	<%
	Timestamp now = new Timestamp(System.currentTimeMillis());
	%>
	<%=now %>
</body>
</html>
```
<br>

`directive02_bottom.jsp 파일`
```
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>directive_bottom</title>
</head>
<body>
	<h3>Bottom Page</h3>
	<%-- 같은 페이지에 있어 실행은 되지만, 에러 표시로는 나타남. --%>
	<%//=name %>
</body>
</html>
```
<br>

`directive02.jsp 파일`
```
...(중략)

<body>
	<h1>디렉티브 연습 2 (include)</h1>
	<br>
	
	<%
	String name = "우영우";
	%>
	
	<%@ include file="directive02_top.jsp" %>
	<hr>
	<h2>Main Page</h2>
	<p>메인 페이지입니다.</p>
	<hr>
	<%@ include file="directive02_bottom.jsp" %>
</body>
```

#### <span style="color:cornflowerblue">실행 결과</span>
![디렉티브 실행 결과 2]({{ site.baseurl }}/assets/img/jsp-post1-2.png){: width="60%"}