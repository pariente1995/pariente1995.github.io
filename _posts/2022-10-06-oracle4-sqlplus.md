---
layout: post
title: "[Oracle] 4. Oracle SQL PLUS 명령어"
subtitle: "Oracle SQL PLUS 명령어 알아보기"
author: SeHyeok Park
categories : Database, DB, Oracle
tags: [Database, DB, Oracle]
comments : True
---
<div id='preview' class='display-none'>
Oracle의 다양한 SQL PLUS 명령어 알아보기
</div>

## 1. SQL PLUS 명령어
- ***오라클에서만 사용할 수 있는 명령어***
<br><br>

## 2. SQL PLUS 명령어 모음
- **ed(edit)** 
: 바로 직전에 사용한 SQL문을 임시 버퍼로 불러와서 메모장으로 보여주는 명령어.
![ed 명령어 예제]({{ site.baseurl }}/assets/img/oracle-post3-1.png){: width="70%"}

- **l(list)**
: 바로 직전에 사용한 SQL문을 보여주는 명령어.
![ed 명령어 예제]({{ site.baseurl }}/assets/img/oracle-post3-2.png){: width="70%"}

- **/**
: 바로 직전에 사용한 SQL문을 실행하는 명령어.
![ed 명령어 예제]({{ site.baseurl }}/assets/img/oracle-post3-3.png){: width="70%"}

- **r(run)**
: 바로 직전에 사용한 SQL문을 보여주고 실행하는 명령어.
![ed 명령어 예제]({{ site.baseurl }}/assets/img/oracle-post3-4.png){: width="70%"}
<br><br>

***<mark>※ 바로 위의 3가지 명령어는 긴 내용, 수정 내용 등의 SQL문을 불러와서 사용할 수 있는 편리한 기능을 가진 명령어이다.</mark>***
<br><br>

##### < 바로 직전에 사용한 SQL문을 파일로 저장할 수 있도록 하는 명령어 > 
- **save 경로명\파일명.sql**
: 지정한 경로에 sql 파일로, 바로 직전에 사용한 SQL문을 저장.<br>
ex) save c:\tmp\o1005.sql;
<br>

- **save 경로명\파일명.sql append**
: 지정한 경로에 있는 sql 파일 뒤에, 새로 작성한 SQL문을 추가.<br>
ex) save c:\tmp\o1005.sql append;
<br>

- **save 경로명\파일명.sql replace**
: 지정한 경로에 있는 sql 파일의 내용을 새로 작성한 SQL문으로 대체.<br>
ex) save c:\tmp\o1005.sql replace;
<br>

- **@경로명\파일명.sql**
: 지정한 경로에 있는 sql 파일 안의 모든 명령문을 실행.<br>
ex) @c:\tmp\o1005.sql;
<br><br>

***<mark>※ save 명령을 사용할 때는 .sql을 생략 가능.</mark>***
<br><br>
<hr>

- **host**
: sqlplus 환경에서 oracle의 설정을 유지한 채로 dos 환경으로 나가는 명령어.

- **exit**
: dos 환경에서 sqlplus환경으로 돌아올 때 필요한 명령어.
<hr>

##### < 쿼리 실행 화면을 파일로 저장할 수 있도록 하는 명령어 > 
- **spool 경로명\파일명.확장자;**
: 지정한 경로에 파일명.확장자 파일로 저장.<br>
<span style="color:red">확장자를 지정하지 않으면, .lst 확장자 파일로 저장됨.</span><br>
ex) spool c:\tmp\o1005.txt;
<br>

- **spool off;** 
: spool off; 명령어 실행 시, 이전까지의 모든 실행 쿼리문 및 결과 전체를 파일로 저장.<br>
<span style="color:red">주의) spool off 명령어를 사용하지 않으면, 파일이 저장되지 않음!</span>
<br>

- **ed 경로명\파일명.확장자**
: spool로 저장된 파일을 확인.
<br><br>

##### < SQL PLUS 화면 출력 설정 관련 명령어 >
- **show linesize 값;**
: 한 라인에 표시할 글자수 설정, 기본값: 80.<br>
ex) set linesize 120; // 라인사이즈를 120으로 변경.

- **show pagesize 값;**
: 한 페이지에 표시할 행수 설정, 기본값: 14.<br>
ex) et pagesize 20; // 페이지사이즈를 20으로 변경.

- **set heading off/on;** 
: 결과에 컬럼명을 보이지 않게/보이게 하는 명령어, 기본값: on.

- **set timing on/off;**
: 쿼리 실행 시간을 보이게/보이지 않게 하는 명령어, 기본값: off.
<br><br>

##### < 출력할 컬럼의 포매팅을 설정하는 명령어 > 
- **column 컬럼명 format 형식;**
<br>
  - ***※ 형식에서 사용하는 출력 형태***
    - 문자열: a길이<br>
    ex) column ename format a10; // 문자열 10자리
    - 숫자: 9를 표현하는 자리수만큼 지정<br>
    ex) column eno format 9999; // 숫자 4자리
  <br>
  - ***※ 숫자를 표현하는 2가지 방식***
    - 9의 방식: 의미없는 숫자의 자리는 생략.
    - 0의 방식: 의미없는 숫자의 자리도 0으로 채워 넣음.
    - ,(콤마): 천단위 구분 기호.
    - 통화단위: \$(달러), L(지역화폐)를 숫자 앞에 써주면 됨.<br>
    ex) column salary format $9,999,999;<br>
    ex) column commission format L0,000,000;<br>
    ![column format 예제]({{ site.baseurl }}/assets/img/oracle-post3-5.png){: width="80%"}