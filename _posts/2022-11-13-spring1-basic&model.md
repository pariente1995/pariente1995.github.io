---
layout: post
title: "[Spring] 1. 웹 개발의 역사, Model, MVC"
subtitle: "웹 개발의 역사, Model, MVC 알아보기"
author: SeHyeok Park
categories : Spring, Model, MVC
tags: [Spring, Model, MVC]
comments : True
---
<div id='preview' class='display-none'>
웹 개발의 역사, Model, MVC 알아보기
</div>

## 1. 웹 개발의 역사
#### 1. Servlet 등장 전
- 초창기 Web은 HTML, CSS등의 파일(정적 파일)만 넘겨주는 Web Server의 기능만 존재.
- DB에서 가져온 동적 데이터를 표출할 수 없는 문제 발생.<br><br>
`초창기 Web`<br>
![초창기 Web]({{ site.baseurl }}/assets/img/초창기web.PNG){: width="80%"}

- 그래서 등장한 개념이 <b>CGI(Common Gateway Interface: 동적 데이터 처리에 대한 공통규약)</b>이다.
- CGI 클라이언트에서 request가 오면 WebServer에서 CGI프로그램을 호출하게 되고 CGI프로그램은 요청 하나당 프로세스 하나씩을 생성하여 동적 데이터를 처리하게 됨.
- CGI프로그램은 처음에 문제가 없어보였지만, 야후같은 대형사이트(사용자가 다수인)가 등장하면서 문제가 발생하게 된다.
- 프로세스는 사용자의 요청이 많아지면 메모리가 계속해서 증가하고 먼저 생성된 프로세스가 처리되기 전까지는 다음 프로세스가 진행되지 않는 문제점이 있었다.<br><br>
`CGI Web`<br>
![CGI Web]({{ site.baseurl }}/assets/img/CGIweb.PNG){: width="80%"}<br>
`CGI Web 문제점`<br>
![CGI Web 문제점]({{ site.baseurl }}/assets/img/CGIweb문제점.PNG){: width="80%"}
<br><br>

#### 2. Servlet
- 위에 서술한 문제점들을 보완하기 위해 고안된 방식이 Servlet. 
- Servlet은 요청 하나당 프로세스를 생성하지 않고 쓰레드를 하나씩 생성. 
- 쓰레드를 통한 병렬 분산처리로 다중 요청에 대한 처리 속도를 끌어올렸다. 
- 그리고 Java 소스에서 HTML 웹 문서를 만들 수 있도록 구현되어 있어 Web Server 성능을 향상시킴.
- 하지만 Servlet에서 HTML 웹 문서를 만드는 작업이 매우 복잡하고 귀찮은 작업이었다.<br><br>
`Servlet`<br>
![Servlet]({{ site.baseurl }}/assets/img/Servlet.PNG){: width="80%"}<br>
`Servlet의 쓰레드`<br>
![Servlet의 쓰레드]({{ site.baseurl }}/assets/img/Servlet의쓰레드.PNG){: width="80%"}
<br><br>

#### 3. JSP(Java Server Page)
- Servlet의 소스 코드가 너무 복잡하여 HTML에서 java소스를 사용할 수 있도록 고안된 방식.
- 소스 코드를 구현하기 쉽고 개발 기간 단축, 화면단과 비즈니스 로직을 모두 가지고 있다. <b>(Model 1 방식의 개발)</b>
- 비즈니스 로직과 화면단 소스 코드가 한 파일에 존재하여 코드가 어지럽고 더러워지는 단점이 존재한다.<br><br>
`JSP - Model 1`<br>
![JSP(Model1)]({{ site.baseurl }}/assets/img/JSP(Model1).PNG){: width="80%"}
<br><br>

#### 4. Model 2(JSP + Servlet)
- 현재 제일 많이 사용되는 MVC(Model View Controller)의 시초.
- JSP는 화면단만 담당, PageController(Servlet)는 화면단과 모델을 연결, Model(비즈니스 로직, Java).<br><br>
`Model 2 MVC`<br>
![Model2MVC]({{ site.baseurl }}/assets/img/Model2MVC.PNG){: width="80%"}
<br><br>

#### 5. MVC 패턴
- Model 2 방식에서 좀 더 진화된 형태의 패턴.
- PageController 하나만 존재하던 Model 2방식과 다르게 기능별 Controller로 세분화(Http 프로토콜(규약)을 따르는 HttpServlet을 상속받아 구현).
- Model 부분도 비즈니스 로직을 담당하는 Service, ServiceImpl과 데이터를 담당하는 DAO로 세분화.<br><br>
`MVC`<br>
![MVC]({{ site.baseurl }}/assets/img/MVC.PNG){: width="80%"}