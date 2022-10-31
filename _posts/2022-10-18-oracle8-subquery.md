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
##### - 연산자: in(=any), not in, any(some), all
<br><br>

## 4. 다중행 서브쿼리에서 any와 all의 사용 방법
##### &emsp; 1. any(some): 서브쿼리의 여러 결과 중에서 한 가지만 만족해도 결과를 출력하는 경우.
&emsp;&emsp; - <b>\< any:</b> 서브쿼리의 여러 결과 중에서 최대값보다 작은 값을 출력<br>
&emsp;&emsp; - <b>\> any:</b> 서브쿼리의 여러 결과 중에서 최소값보다 큰 값을 출력
<br>

##### &emsp; 2. all: 서브쿼리의 여러 결과를 모두 만족해야 결과를 출력하는 경우.
&emsp;&emsp; - <b>\< all:</b> 서브쿼리의 여러 결과 중에서 최소값보다 작은 값을 출력<br>
&emsp;&emsp; - <b>\> all:</b> 서브쿼리의 여러 결과 중에서 최대값보다 큰 값을 출력
<br><br>

#### <span style="color:cornflowerblue">예제1 - 단일행 서브쿼리</span>
###### Q: \'CLARK\'와 같은 부서에서 근무하는 사원의 사번, 사원명, 업무, 부서번호를 출려하시오.
```
SELECT eno, ename, job, dno
FROM employee
WHERE dno = (SELECT dno 
               FROM employee 
              WHERE ename = 'CLARK');
```
<br><br>

#### <span style="color:cornflowerblue">예제2 - 단일행 서브쿼리</span>
###### Q: 최고급여를 받는 사원의 사번, 사원명, 급여를 출력하시오.
```
SELECT eno, ename, salary
FROM employee 
WHERE salary = (SELECT MAX(salary) from employee);
```
<br><br>

#### <span style="color:cornflowerblue">예제3 - 단일행 서브쿼리</span>
###### Q: 부서위치가 \'DALLAS\'인 사원의 사원명, 부서번호, 업무를 출력하시오.
```
SELECT ename, dno, job
FROM employee
WHERE dno = (SELECT dno FROM department WHERE loc = 'DALLAS');
```
<br><br>