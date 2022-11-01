---
layout: post
title: "[Oracle] 12. DML - DELETE"
subtitle: "DML(Data Manipulation Language) 중 DELETE 명령어 알아보기"
author: SeHyeok Park
categories : Database, DB, Oracle
tags: [Database, DB, Oracle]
comments : True
---
<div id='preview' class='display-none'>
DML(Data Manipulation Language) 중 DELETE 명령어 알아보기
</div>

## 1. DELETE 명령어 
- 테이블의 데이터를 삭제하는 명령어.
<br><br>

## 2. DELETE 구문 형식
> <b>형식: DELETE (FROM) 테이블명 WHERE 조건;</b>

<br><br>

#### <span style="color:cornflowerblue">예제1</span>
###### Q: DEPT 테이블에서 부서번호가 40 또는 50인 데이터를 삭제하시오.
```sql
DELETE FROM DEPT
WHERE dno in (40, 50);
```
<br>

#### <span style="color:cornflowerblue">예제2</span>
###### Q: EMP 테이블에서 부서명이 \'ACCOUNTING\'인 사원의 데이터를 삭제하시오. 
```sql
DELETE FROM EMP 
WHERE dno = (SELECT dno FROM DEPT WHERE dname = 'ACCOUNTING');
```
<br>

#### <span style="color:cornflowerblue">예제3</span>
###### Q: EMP 테이블의 모든 데이터를 삭제하시오.
```sql
DELETE FROM EMP;
```
<br>