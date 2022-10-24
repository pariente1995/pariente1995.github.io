---
layout: post
title: "[JSP] 8. JSP Request"
subtitle: "JSP Request 알아보기"
author: SeHyeok Park
categories : JSP
tags: [JSP]
comments : True
---
<div id='preview' class='display-none'>
JSP Request 알아보기
</div>

## 1. Request 내장 객체의 주요 메소드
##### &emsp; 1. setCharacterEncoding(): 인코딩을 변경하는 메소드
##### &emsp; 2. getParameter(): 파라미터로 넘어오는 값 1개를 얻는 메소드
&emsp;&emsp; - input, select(단수) 사용 시
##### &emsp; 3. getParameterValues(): 파라미터로 넘어오는 여러 개의 값을 얻는 메소드
&emsp;&emsp; - 문자열 배열 사용
&emsp;&emsp; - input 중에서 checkbox, select(복수) 사용 시
##### &emsp; 4. getProtocol(): 사용중인 프로토콜을 알려주는 메소드 
##### &emsp; 5. getSeverName(): 서버의 도메인 이름을 알려주는 메소드
##### &emsp; 6. getMethod(): 요청 방식을 알려주는 메소드(get, post...)
##### &emsp; 7. getRequestURI(): 요청에 사용된 URI를 리턴하는 메소드
##### &emsp; 8. getRequestURL(): 요청에 사용된 URL을 리턴하는 메소드
##### &emsp; 9. getContextPath(): 요청에 사용된 컨텍스트 경로를 리턴하는 메소드
##### &emsp; 10. getRemoteHost(): 웹 브라우저의 호스트 이름을 알려주는 메소드
##### &emsp; 11. getRemoteAddr(): 웹 브라우저의 IP 주소를 알려주는 메소드 
##### &emsp; 12. getServerPort(): 서버의 포트번호를 알려주는 메소드 
##### &emsp; 13. getHeader(): 헤더의 속성값을 알려주는 메소드
##### &emsp; 14. getHeaderNames(): 헤더에 있는 모든 헤더 이름을 리턴하는 메소드
<br><br>

## 2. 접근 경로 4가지
##### &emsp; 1. URL(Uniform Resource Locator)
&emsp;&emsp; - 페이지의 전체 경로.<br>
&emsp;&emsp; - 서버부터 페이지명까지 모두 포함한 경로.<br>
##### &emsp; 2. URI(Uniform Resource Identifier)
&emsp;&emsp; - 프로젝트명부터 페이지명까지를 포함한 경로, 서버는 제외.
##### &emsp; 3. Context Path
&emsp;&emsp; - 컨텍스트 경로, 해당 프로젝트명.
##### &emsp; 4. 접근 경로
&emsp;&emsp; - 프로젝트명을 제외한 폴더명과 페이지명을 포함한 경로.
<br><br>

### <span style="color:cornflowerblue">예제1</span>
`requestTest01Form.jsp 파일`

```
<body>
	<h2>학생정보를 입력하는 폼페이지</h2>
	<form action="requestTest01Pro.jsp" method="post">
		학번: <input type="text" name="no"><br>
		이름: <input type="text" name="name"><br>
		학년: 
		<input type="radio" name="grade" value="1학년">1학년&ensp;
		<input type="radio" name="grade" value="2학년">2학년&ensp;
		<input type="radio" name="grade" value="3학년">3학년&ensp;
		<input type="radio" name="grade" value="4학년">4학년<br>
		선택과목:<br>
		<select name="subject" multiple>
			<option value="자료구조">자료구조</option>
			<option value="알고리즘">알고리즘</option>
			<option value="데이터베이스">데이터베이스</option>
			<option value="빅데이터">빅데이터</option>
			<option value="컴퓨터구조">컴퓨터구조</option>
			<option value="운영체제">운영체제</option>
		</select><br>
		<input type="submit" value="입력완료">
	</form>
</body>
```
<br>

`requestTest01Pro.jsp 파일`

```
<style>
	table {width: 500px; border: 1px solid black; border-collapse: collapse;}
	tr { height: 30px;}
	th { background-color: lightgray;}
	th, td { border: 1px solid black; text-align: center;}
</style>

...

<body>
	<h2>학생정보를 처리하는 페이지</h2>
	<%
	request.setCharacterEncoding("UTF-8");
	String no = request.getParameter("no");
	String name = request.getParameter("name");
	String grade = request.getParameter("grade");
	String[] subjects = request.getParameterValues("subject");
	
	String s_subjects ="";
	for(String s : subjects) {
		s_subjects += s + " ";
	}
	%>
	
	<table>
	<tr>
		<th width="20%">학번</th>
		<td width="80%"><%=no %></td>
	</tr>
	<tr>
		<th>이름</th>
		<td><%=name %></td>
	</tr>
	<tr>
		<th>학년</th>
		<td><%=grade %></td>
	</tr>
	<tr>
		<th>선택과목</th>
		<td><%=s_subjects %></td>
	</tr>
	</table>
</body>
```

#### <span style="color:cornflowerblue">실행 결과</span>
![실행 결과 1]({{ site.baseurl }}/assets/img/jsp-result8-1.png){: width="60%"}

![실행 결과 2]({{ site.baseurl }}/assets/img/jsp-result8-2.png){: width="60%"}

### <span style="color:cornflowerblue">예제2</span>
`requestTest02.jsp 파일`

```
<style>
	#t1 { width: 700px; border: 1px solid black; border-collapse: collapse;}
	#t1 tr { height: 30px;}
	#t1 th, #t1 td { border: 1px solid black;}
	#t1 th { width: 25%;}
	#t1 td { width: 75%;}
	
	#t2 { width: 1200px; border: 1px solid black; border-collapse: collapse;}
	#t2 tr { height: 30px;}
	#t2 th, #t2 td { border: 1px solid black;}
	#t2 th { width: 25%;}
	#t2 td { width: 75%;}
</style>

...

<body>
	<h2>request 내장 객체의 메소드</h2>
	<%
	String[] names = {"프로토콜 이름", "서버 이름", "호스트 이름", "IP 주소", "포트 번호", "메소드 방식", "URL", "URI", "컨텍스트 경로"};
	String[] values = {request.getProtocol(), request.getServerName(), request.getRemoteHost(), request.getRemoteAddr(), request.getServerPort() +"", 
			request.getMethod(), request.getRequestURL().toString(), request.getRequestURI(), request.getContextPath()}; 
	%>
	
	<h3>웹서버의 정보 확인</h3>
	<table id="t1">
	<%
	for(int i=0; i<names.length; i++) {
		out.print("<tr><th>" + names[i] + "</th>" + "<td>" + values[i] + "</td></tr>");
	}
	// 접근 경로 생성 -> uri에서 프로젝트명을 제외한다!.
	String uri = request.getRequestURI(); // 프로젝트명부터 폴더, 페이지명까지
	String context = request.getContextPath(); // 프로젝트명
	String path = uri.substring(context.length()); // 접근 경로
	out.print("<tr><th>" + "접근 경로" + "</th><td>" + path + "</td></tr>"); 
	%>
	</table>
	
	<h2>헤더 정보</h2>
	<table id="t2">
	<%
	Enumeration<String> e = request.getHeaderNames();
	String headerName = "";
	String headerValue = "";
	
	while(e.hasMoreElements()) {
		headerName = e.nextElement();
		headerValue = request.getHeader(headerName);
		out.print("<tr><th>" + headerName + "</th><td>" + headerValue + "</td></tr>");
	} 
	%>
	</table>
</body>
```

#### <span style="color:cornflowerblue">실행 결과</span>
![실행 결과 3]({{ site.baseurl }}/assets/img/jsp-result8-3.png){: width="100%"}