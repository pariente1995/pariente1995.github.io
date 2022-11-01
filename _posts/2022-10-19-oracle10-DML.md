---
layout: post
title: "[Oracle] 10. DML - INSERT"
subtitle: "DML(Data Manipulation Language) 중 INSERT 명령어 알아보기"
author: SeHyeok Park
categories : Database, DB, Oracle
tags: [Database, DB, Oracle]
comments : True
---
<div id='preview' class='display-none'>
DML(Data Manipulation Language) 중 INSERT 명령어 알아보기
</div>

## 1. INSERT 명령어 
- 테이블에 데이터를 추가(삽입)하는 명령어.
<br><br>

## 2. INSERT 구문 형식
##### 1. 모든 컬럼을 명시하고, 값을 입력하는 경우
> <b>형식: INSERT INTO 테이블명(컬럼명, ...) VALUES(값, ...);</b>

```
INSERT INTO EMP(eno, ename, job, manager, hiredate, salary, commission, dno)
VALUES(8001, 'STEVE', 'MANAGER', 7839, to_date('1990/06/13'), 3300, null, 40);
```
<br>

##### 2. 모든 컬럼에 대한 값을 누락없이 순서대로 입력하는 경우
##### &emsp; - 테이블명 뒤의 컬럼명 부분을 생략할 수 있음.
> <b>형식: INSERT INTO 테이블명 VALUES(값, ...);</b>

```
INSERT INTO EMP
VALUES(8002, 'TOM', 'SALESMAN', 7698, to_date('1991/09/20'), 2200, 1000, 30);
```
<br>

##### 3. 생략한 컬럼이 있고, 순서가 바뀐 경우
##### &emsp; - 컬럼명과 값을 정확하게 순서대로 일치하여야 함.
##### &emsp; - 생략 가능한 컬럼은 NULL인 경우이고, NOT NULL은 생략 불가.
> <b>형식: INSERT INTO 테이블명(넣고 싶은 컬럼명, ...) VALUES(넣고 싶은 컬럼에 대한 값, ...);</b>

```
INSERT INTO EMP(eno, ename, dno, job, hiredate, salary, manager) 
VALUES (8003, 'JERRY', 10, 'CLERK', to_date('1992/12/12'), 1800, 7788);
```