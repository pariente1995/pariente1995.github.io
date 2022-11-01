---
layout: post
title: "[Oracle] 13. DDL - TRUNCATE"
subtitle: "DDL(Data Definition Language) 중 TRUNCATE 명령어 알아보기"
author: SeHyeok Park
categories : Database, DB, Oracle
tags: [Database, DB, Oracle]
comments : True
---
<div id='preview' class='display-none'>
DDL(Data Definition Language) 중 TRUNCATE 명령어 알아보기
</div>

## 1. TRUNCATE 명령어 
- 테이블의 모든 데이터를 삭제하는 명령어.
<br><br>

## 2. TRUNCATE 구문 형식
> <b>형식: TRUNCATE TABLE 테이블명;</b>

<br>

#### <span style="color:cornflowerblue">예제</span>
###### Q: DEPT 테이블의 모든 데이터를 삭제하시오.
```sql
TRUNCATE TABLE DEPT;
```
<br><br>

## 3. DELETE와 TRUNCATE의 차이점

||<span style="color:orange">DELETE</span>|<span style="color:orange">TRUNCATE</span>|
|:---:|------|--------|
|**명령어 종류**|DML|DDL|
|**COMMIT**|직접 처리|자동|
|**ROLLBACK 가능 여부**|가능|불가능|
|**데이터 공간**|그대로 남음|데이터 공간도 삭제|