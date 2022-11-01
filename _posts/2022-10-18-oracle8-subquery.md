---
layout: post
title: "[Oracle] 8. 서브쿼리(Sub Query)"
subtitle: "서브쿼리(Sub Query) 알아보기"
author: SeHyeok Park
categories : Database, DB, Oracle
tags: [Database, DB, Oracle]
comments : True
---
<div id='preview' class='display-none'>
서브쿼리(Sub Query) 알아보기
</div>

## 1. 서브쿼리(Sub Query)
##### - 서브쿼리: 쿼리문 내부에 기술된 쿼리문.
##### - 메인쿼리: 쿼리문 외부에 기술한 쿼리문.
##### - 일반적으로 메인쿼리가 서브쿼리를 감싸고 있는 형태의 쿼리문을 서브쿼리라고 부름.
<br><br>

## 2. 단일행 서브쿼리 
##### - 서브쿼리의 결과가 1개인 경우.
##### - 연산자: >, >=, <, <=, =, <>
<br><br>

## 3. 다중행 서브쿼리
##### - 서브쿼리의 결과가 2개 이상인 경우.
##### - 연산자: IN, NOT IN, ANY(=SOME), ALL
<br><br>

## 4. 다중행 서브쿼리에서 ANY와 ALL의 사용 방법
##### &emsp; 1. ANY(=SOME): 서브쿼리의 여러 결과 중에서 한 가지만 만족해도 결과를 출력하는 경우.
&emsp;&emsp; - <b>\< ANY:</b> 서브쿼리의 여러 결과 중에서 최대값보다 작은 값을 출력<br>
&emsp;&emsp; - <b>\> ANY:</b> 서브쿼리의 여러 결과 중에서 최소값보다 큰 값을 출력
<br>

##### &emsp; 2. ALL: 서브쿼리의 여러 결과를 모두 만족해야 결과를 출력하는 경우.
&emsp;&emsp; - <b>\< ALL:</b> 서브쿼리의 여러 결과 중에서 최소값보다 작은 값을 출력<br>
&emsp;&emsp; - <b>\> ALL:</b> 서브쿼리의 여러 결과 중에서 최대값보다 큰 값을 출력
<br><br>

#### <span style="color:cornflowerblue">예제1 - 단일행 서브쿼리</span>
###### Q: \'CLARK\'와 같은 부서에서 근무하는 사원의 사번, 사원명, 업무, 부서번호를 출려하시오.
```sql
SELECT eno, ename, job, dno
FROM employee
WHERE dno = (SELECT dno FROM employee WHERE ename = 'CLARK');
```
<br>

#### <span style="color:cornflowerblue">예제2 - 단일행 서브쿼리</span>
###### Q: 최고급여를 받는 사원의 사번, 사원명, 급여를 출력하시오.
```sql
SELECT eno, ename, salary
FROM employee 
WHERE salary = (SELECT MAX(salary) from employee);
```
<br>

#### <span style="color:cornflowerblue">예제3 - 단일행 서브쿼리</span>
###### Q: 부서위치가 \'DALLAS\'인 사원의 사원명, 부서번호, 업무를 출력하시오.
```sql
SELECT ename, dno, job
FROM employee
WHERE dno = (SELECT dno FROM department WHERE loc = 'DALLAS');
```
<br>

#### <span style="color:cornflowerblue">예제4 - 다중행 서브쿼리</span>
###### Q: 부서별 최고급여를 받는 사원의 사원번호와 이름, 부서번호, 급여를 출력하시오.
```sql
SELECT eno, ename, dno, salary
FROM employee
WHERE salary IN (SELECT MAX(salary) FROM employee GROUP BY dno);
```
<br>

#### <span style="color:cornflowerblue">예제5 - 다중행 서브쿼리</span>
###### Q: 업무가 \'SALESMAN\'이 아니면서, 급여가 임의의 \'SALESMAN\'보다 낮은 사원의 사원번호, 사원명, 급여를 출력하시오.
```sql
SELECT eno, ename, salary
FROM employee
WHERE job <> 'SALESMAN'
AND salary < ANY (SELECT salary FROM employee WHERE job = 'SALESMAN');
```
<br>

#### <span style="color:cornflowerblue">예제6 - 다중행 서브쿼리</span>
###### Q: 업무가 \'SALESMAN\'이 아니면서, 급여가 모든 \'SALESMAN\'보다 낮은 사원의 사원번호, 사원명, 급여를 출력하시오.
```sql
SELECT eno, ename, salary
FROM employee
WHERE job <> 'SALESMAN'
AND salary < ALL (SELECT salary FROM employee WHERE job = 'SALESMAN');
```