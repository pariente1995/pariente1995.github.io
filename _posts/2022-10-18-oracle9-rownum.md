---
layout: post
title: "[Oracle] 9. ROWNUM 컬럼(의사 컬럼)"
subtitle: "ROWNUM 컬럼(의사 컬럼) 알아보기"
author: SeHyeok Park
categories : Database, DB, Oracle
tags: [Database, DB, Oracle]
comments : True
---
<div id='preview' class='display-none'>
ROWNUM 컬럼(의사 컬럼) 알아보기
</div>

## 1. ROWNUM 컬럼
- 테이블의 검색 데이터에 대한 행번호를 붙여주는 가상의 컬럼(의사 컬럼).
- 출력하는 행의 수를 제한하는 것이 가능.
<br><br>

#### <span style="color:cornflowerblue">1. 행번호를 포함한 전체 데이터 출력</span>
```
SELECT ROWNUM, e.* 
FROM employee e;
```
<br>

#### <span style="color:cornflowerblue">2. 처음부터 제한하여 출력</span>
```
SELECT * 
FROM employee 
WHERE ROWNUM <= 3;
```
<br>

#### <span style="color:cornflowerblue">3. 출력할 데이터를 지정하여 행번호를 함께 출력 시, 인라인 뷰를 사용</span>
###### <mark>인라인 뷰(Inline View):</mark> FROM절에서 서브쿼리를 사용하여 테이블처럼 사용하는 것.
> 3-1. 처음부터 사원명 5건 출력
```
SELECT * 
FROM (SELECT ROWNUM AS list, ename FROM employee) 
WHERE list <= 5;
```
<br>

> 3-2. 행번호를 출력하고, 몇번부터 몇번까지 중간의 범위를 출력
```
SELECT * 
FROM (SELECT ROWNUM AS list, ename FROM employee) 
WHERE list BETWEEN 6 AND 10;
```
<br>

###### <span style="color:red">※ ORDER BY절을 사용하여 행번호 출력 시 행번호의 정렬이 틀어지기에,</span>
###### <span style="color:red">인라인 뷰를 사용하여 데이터 정렬 후 행번호를 부여한다.</span>
> 3-3. 데이터를 정렬하여 행번호를 부여 후 출력

```
SELECT ROWNUM, e.*
FROM (SELECT * FROM employee ORDER BY salary DESC) e;
```
<br>