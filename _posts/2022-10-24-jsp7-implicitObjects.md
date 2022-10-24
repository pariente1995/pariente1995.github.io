---
layout: post
title: "[JSP] 7. JSP 내장 객체(Implicit Objects) 및 영역 객체"
subtitle: "JSP 내장 객체(Implicit Objects) 및 영역 객체 알아보기"
author: SeHyeok Park
categories : JSP
tags: [JSP]
comments : True
---
<div id='preview' class='display-none'>
JSP 내장 객체(Implicit Objects) 및 영역 객체 알아보기
</div>

## 1. 내장 객체 (Implicit Objects)
- 객체의 생성없이 바로 사용할 수 있도록 JSP에서 미리 만들어 놓은 객체.
- 출력, 요청, 응답, 예외처리 등등...
<br><br>

## 2. 9개의 내장 객체
##### &emsp; 1. request 객체: 웹 브라우저의 요청을 처리하는 객체
##### &emsp; 2. response 객체: 웹 브라우저의 요청에 대한 응답을 처리하는 객체
##### &emsp; 3. session 객체: 웹 브라우저의 세션에 관한 처리를 하는 객체
##### &emsp; 4. application 객체: 웹 애플리케이션의 Context 정보를 저장하는 객체
##### &emsp; 5. pageContext 객체: JSP 페이지에 대한 정보를 저장하는 객체
##### &emsp; 6. out 객체: JSP 페이지의 출력을 담당하는 객체
##### &emsp; 7. page 객체: JSP 페이지를 구현하는 자바 클래스의 객체, 사용하지 않음.
##### &emsp; 8. config 객체: JSP 페이지의 설정 정보를 저장하는 객체, 거의 사용하지 않음
##### &emsp; 9. exception 객체: JSP 페이지의 예외처리를 담당하는 객체
&emsp;&emsp; - directive의 errorPage, isErrorPage 설정과 함께 사용하는 객체.<br>
&emsp;&emsp; - 위의 2가지 기능을 사용하지 않으므로, exception 객체도 사용하지 않음.
<br>

**<mark><span style="color:red">※ 자주 사용하는 객체:</span></mark>** request, out, response, session<br>
**<mark>※ 가끔 사용하는 객체:</mark>** application, pageContext
<br><br>

## 3. 영역 객체
##### - 웹 브라우저의 요청에 대한 처리 영역과 관련된 4가지 내장 객체.
##### - pageContext, request, session, application
- **pageContext:** 해당 페이지에서 처리되는 영역.
- **request:** 요청에 대한 처리 영역.
- **session:** 세션에 대한 처리 영역.
- **application:** 애플리케이션에 대한 처리 영역.
- **영역의 크기:** pageContext < request < session < application