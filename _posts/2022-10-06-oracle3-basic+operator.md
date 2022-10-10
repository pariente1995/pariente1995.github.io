---
layout: post
title: "[Oracle] 3. Oracle 기본적인 데이터 타입(Data Type) 및 연산자"
subtitle: "Oracle 데이터 타입(Data Type) 및 연산자 알아보기"
author: SeHyeok Park
categories : Database, DB, Oracle
tags: [Database, DB, Oracle]
comments : True
---
<div id='preview' class='display-none'>
Oracle 기본적인 데이터 타입(Data Type) 및 연산자 알아보기
</div>

## 1. 데이터 타입(Data Type)
- 문자열, 숫자(정수, 실수), 날짜 등등...
<br><br>

- **문자열**
  - 홑따옴표(\' \')로 묶음.
  - **CHAR:** 고정 문자열.
  - **VARCHAR2:** 가변 문자열. (오라클에서만 뒤에 2를 붙임.)
<br><br>

- **숫자**
  - **NUMBER(크기):** 정수 
    - ex) NUMBER(5)
  - **NUMBER(크기, 소수점자리수):** 실수 
    - ex) NUMBER(7, 2)
<br><br>

- **날짜**
  - 홑따옴표(\' \')로 묶음.
  - 년월일을 yyyy(yy)/mm/dd, yyyy(yy)-mm-dd의 형태로 설정.*(yy로만 쓸 경우, 1900년대로 인식한다.)*
  - **DATE:** 날짜.
  - **TIMESTAMP:** 날짜와 시간.
<br><br>

- **대용량의 데이터**
  - **BLOB(Binary Large Object)**
    - 대용량의 바이너리 데이터를 저장.
    - 최대 4GB.
    - 특별한 경우가 아닌 이상 거의 사용하지 않음.
  - **CLOB(Character Large Object)**
    - 대용량의 텍스트 데이터를 저장.
    - 최대 4GB.
    - 특별한 경우가 아닌 이상 거의 사용하지 않음.
<br><br>

## 2. 기본적인 연산자
- **(1). 산술 연산자:** +, -, *, /(나눈 전체 결과), java와 같은 나머지 연산자(%)는 없음.
- **(2). 비교 연산자:** >, >=, <, <=, =, <>(!=, ^= 은 같은 연산자)
  - 이상, 이하: >=, <=
  - 초과, 미만: >, <
- **(3). 논리 연산자:** AND, OR, NOT
- ***<mark>우선 순위:</mark>*** 산술 > 비교 > 논리
<br><br>

## 3. 기타 연산자
- **(1) BETWEEN**
  - 특정 범위의 데이터를 조회하고자 할 경우 사용.
  - **사용법:** 컬럼명 BETWEEN A AND B
  - A와 B 사이(A, B 포함).
  - ex) SELECT * FROM employee WHERE salary BETWEEN 1000 AND 1500;
<br><br>

- **(2) IN**
  - 소괄호 안의 값이 포함되는 데이터를 조회하고자 할 경우 사용.
  - **사용법:** 컬럼명 IN (A, B, C...)
  - ex) SELECT * FROM employee WHERE salary IN (1300, 1500, 1600);
<br><br>

- **(3) IS**
  - NULL 혹은 NULL이 아닌 데이터를 조회하고자 할 경우 사용.
  - **사용법:** 컬럼명 IS (NOT) NULL
  - ex) SELECT * FROM employee WHERE commission IS NULL;
  - ex) SELECT * FROM employee WHERE commission IS NOT NULL;
<br><br>

- **(4) LIKE**
  - 특정 문자를 포함하는 데이터를 조회하고자 할 경우 사용.
  - **사용법:** 컬럼명 LIKE 검색할 값
    - 와일드 카드 - 특별한 의미를 가지는 문자.
      - %(퍼센트): 없거나, 하나 이상의 어떠한 문자가 와도 상관이 없음.
      - _(언더바): 하나의 문자가 어떤 값이 와도 상관이 없음.
  - ex) SELECT * FROM employee WHERE ename LIKE \'S%\';
<br><br>