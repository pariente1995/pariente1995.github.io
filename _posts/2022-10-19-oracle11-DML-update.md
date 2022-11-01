---
layout: post
title: "[Oracle] 11. DML - UPDATE"
subtitle: "DML(Data Manipulation Language) 중 UPDATE 명령어 알아보기"
author: SeHyeok Park
categories : Database, DB, Oracle
tags: [Database, DB, Oracle]
comments : True
---
<div id='preview' class='display-none'>
DML(Data Manipulation Language) 중 UPDATE 명령어 알아보기
</div>

## 1. UPDATE 명령어 
- 테이블의 데이터를 수정(변경)하는 명령어.
<br><br>

## 2. UPDATE 구문 형식
> <b>형식: UPDATE 테이블명 SET 변경할 값 WHERE 조건;</b>

<br><br>

#### <span style="color:cornflowerblue">예제1</span>
###### Q: EMP 테이블에서 업무가 \'SALESMAN\'인 사원의 급여를 200씩 인상하시오.
```
UPDATE EMP 
SET salary = salary + 200
WHERE job = 'SALESMAN';
```
<br>

#### <span style="color:cornflowerblue">예제2</span>
###### Q: EMP 테이블에서 사원번호가 7566인 사원의 입사일을 일주일 전으로 수정하시오.
```
UPDATE EMP 
SET hiredate = hiredate - 7
WHERE eno = 7566;
```
<br>

#### <span style="color:cornflowerblue">예제3</span>
###### Q: DEPT 테이블에서 40번 부서의 부서명을 \'PROGRAMMING\', 지역명을 \'SEOUL\'로 변경하시오.
```
UPDATE DEPT
SET dname = 'PROGRAMMING', loc = 'SEOUL'
WHERE dno = 40;
```
<br>

#### <span style="color:cornflowerblue">예제4</span>
###### Q: DEPT 테이블에서 30번 부서의 부서명과 지역명을 20번 부서의 부서명과 지역명으로 변경하시오.
```
UPDATE DEPT 
SET dname = (SELECT dname FROM DEPT WHERE dno = 20),
loc = (SELECT loc FROM DEPT WHERE dno = 20)
WHERE dno = 30;
```
<br>

~~~
UPDATE DEPT 
   SET dname = (SELECT dname FROM DEPT WHERE dno = 20),
       loc   = (SELECT loc FROM DEPT WHERE dno = 20)
 WHERE dno = 30;
~~~