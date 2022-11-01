---
layout: post
title: "[Oracle] 7. 조인(JOIN)"
subtitle: "조인(JOIN)의 종류 및 활용 예제 알아보기"
author: SeHyeok Park
categories : Database, DB, Oracle
tags: [Database, DB, Oracle]
comments : True
---
<div id='preview' class='display-none'>
조인(JOIN)의 종류 및 활용 예제 알아보기
</div>

## 1. 조인(JOIN)
##### - 두 개 이상의 테이블에 저장된 데이터를 한 번에 조회하여 원하는 결과를 얻고자할 때 사용하는 쿼리문.
<br><br>

## 2. 조인 4가지 방법
#### (1) 이퀴 조인(Equi Join) -> <mark>★모든 RDBMS에서 사용 가능★</mark>
- 두 개 이상의 테이블의, 조인 조건을 where절에서 equal(=) 연산자를 사용하여 조인하는 방법.
- 조인 조건을 where 절에 기술함.
<br>

#### <span style="color:cornflowerblue">예제</span>
###### Q: 사번이 7788인 사원의 사번, 사원명, 부서번호, 부서명을 출력하시오.
```sql
SELECT e.eno, e.ename, e.dno, d.dname
FROM employee e, department d
WHERE e.dno = d.dno
AND e.eno = 7788;
```
<br><br>

#### (2) Natural Join -> <u>Oracle에서만 사용하는 조인 방법</u>
<b>< 이퀴 조인의 2가지 문제점을 해결하는 방법 - Oracle에서만 사용 ></b>
1. 2개의 테이블에 모두 존재하는 컬럼에 대해서 테이블명(or 알리아스명).컬럼명을 정확하게 명시하는 문제 해결.
2. 조인 조건을 where 절에 명시하므로 일반 조건과 구분이 어려운 문제 해결.
<br>

##### <span style="color:red">※ Natural Join을 사용할 때 주의점</span>
1. 알리아스를 사용하지 않음. 사용해도 무방하나, 두 테이블에 모두 존재하는 컬럼에 사용하면 에러 발생.
2. 두 개의 테이블에 대한 조인 조건의 컬럼명이 동일하다는 전제하에 사용.
3. 조인 조건이 되는 컬럼명의 파악이 어려움.
<br>

##### <span style="color:red">※ Natural Join을 사용할 수 없는 경우(제약 사항)</span>
- 두 개의 테이블에 조인 조건이 되는 컬럼이, 같은 이름이 아닐 때는 사용 불가.
<br>

#### <span style="color:cornflowerblue">예제</span>
###### Q: 사번이 7788인 사원의 사번, 사원명, 부서번호, 부서명을 출력하시오.
```sql
SELECT eno, ename, dno, dname
FROM employee NATURAL JOIN department
WHERE eno = 7788;
```
<br><br>

#### (3). Join ~ Using -> <u>Oracle에서만 사용하는 조인 방법</u>
- Natural Join에서 어떤 컬럼을 기준으로 조인하고 있는지 파악하기 어려운 문제를 해결.
- Using절에 조인되는 컬럼몀을 정확하게 기술.
- Using절은 FROM절과 WHERE절 사이에 기술.
<br>

##### <span style="color:red">※ Join ~ Using을 사용할 때 주의점</span>
1. 알리아스를 사용하지 않음. 사용해도 무방하나, 두 테이블에 모두 존재하는 컬럼에 사용하면 에러 발생.
2. 두 개의 테이블에 대한 조인 조건의 컬럼명이 동일하다는 전제하에 사용.
3. Using절에 조인 컬럼을 정확하게 명시함.
<br>

##### <span style="color:red">※ Join ~ Using을 사용할 수 없는 경우(제약 사항)</span>
- 두 개의 테이블에 조인 조건이 되는 컬럼이, 같은 이름이 아닐 때는 사용 불가.
<br>

#### <span style="color:cornflowerblue">예제</span>
###### Q: 사번이 7788인 사원의 사번, 사원명, 부서번호, 부서명을 출력하시오.
```sql
SELECT eno, ename, dno, dname 
FROM employee JOIN department
USING(dno)
WHERE eno = 7788;
```
<br><br>

#### (4). Join ~ On -> <mark>★모든 RDBMS에서 사용 가능★</mark>
- Inner Join 이라고 부르기도 함.
- Oracle에서는 Inner를 생략할 수 있음.
- 테이블 사이에 Inner Join을 기술.
- FROM절과 WHERE절 사이에 ON절을 사용하여 조인 조건을 기술함.
<br>

##### <span style="color:red">※ Join ~ On을 사용할 때 주의점</span>
1. 두 개의 테이블 모두 존재하는 컬럼에 대해서는 정확하게 명시해야함.
2. ON절에 조인 조건을 기술함으로써 조인 조건과 일반 조건이 명확하게 구분됨.
<br>

#### <span style="color:cornflowerblue">예제</span>
###### Q: 사번이 7788인 사원의 사번, 사원명, 부서번호, 부서명을 출력하시오.
```sql
SELECT eno, ename, e.dno, dname
FROM employee e JOIN department d 
ON e.dno = d.dno
WHERE eno = 7788;
```
<br><br>

## 3. Non-이퀴 조인
##### - 조인 조건이 equal(=)이 아닌 연산자를 사용하는 조인.
##### - 조인 조건이 특정 범위 내에 있는지를 판별하기 위한 조인 방법.
<br>

#### <span style="color:cornflowerblue">예제1</span>
###### Q: 사번, 사원명, 업무, 급여, 급여등급을 출력하시오.
###### - 급여등급은 각 사원의 급여를 사용하여 급여등급 테이블의 급여등급을 사용하시오.
```sql
SELECT eno, ename, job, salary, grade
FROM employee, salgrade
WHERE salary BETWEEN losal AND hisal;
```
<br><br>

#### <span style="color:cornflowerblue">예제2</span>
###### Q: 사원명, 부서명, 급여, 급여등급을 출력하시오.
###### - 급여등급은 각 사원의 급여를 사용하여 급여등급 테이블의 급여등급을 사용하시오.
```sql
SELECT e.ename, d.dname, e.salary, s.grade
FROM employee e JOIN department d ON e.dno = d.dno, salgrade s
WHERE e.salary BETWEEN s.losal AND s.hisal;
```
<br><br>

## 4. 셀프 조인(Self Join)
##### - 1개의 테이블을 2개의 테이블로 생각하여 조인하는 방법.
##### - 조인 대상이 같은 테이블이므로 알리아스를 다르게 설정해야 함.
##### - 하나의 테이블을 2개로 생각한다는 것만 제외하면, 사용하는 방법은 이퀴조인과 동일.
<br>

#### <span style="color:cornflowerblue">예제</span>
###### Q: 사원번호, 사원명, 관리자번호, 관리자명을 출력하시오.
```sql
SELECT e.eno, e.ename, m.eno, m.ename
FROM employee e, employee m
WHERE e.manager = m.eno;
```
<br><br>

## 5. 아우터 조인(Outer Join)
##### - 이퀴 조인은 한쪽의 결과값이 null인 데이터는 출력하지 않음.
##### - 아우터 조인은 이퀴 조인의 결과값이 널인 데이터도 출력하도록 함.
##### - 아우터 조인을 할 대상 테이블의 컬럼에 \"(+)\" 기호를 붙여서 조인도 가능.
- <span style="color:red">단, 한쪽에만 \"(+)\" 기호를 붙여서 사용이 가능하다!</span>

##### - Left Outer Join: 왼쪽 결과값이 기준이고, 널인 데이터가 오른쪽에 있을 때
##### - Right Outer Join: 오른쪽 결과값이 기준이고, 널인 데이터가 왼쪽에 있을 때
##### - Full Outer Join: 양쪽 테이블을 모두 읽어서. 중복 데이터는 삭제한 결과
<br>

#### <span style="color:cornflowerblue">예제</span>
###### Q: 사원번호, 사원명, 관리자번호, 관리자명을 출력하시오. 관리자가 없는 사원도 출력하도록 하시오.
###### <mark>1번 방법</mark>
```sql
SELECT e.eno, e.ename, m.eno, m.ename
FROM employee e 
LEFT OUTER JOIN employee m ON e.manager = m.eno;
```
<br>

###### <mark>2번 방법</mark>
```sql
SELECT e.eno, e.ename, m.eno, m.ename
FROM employee e 
INNER JOIN employee m ON e.manager = m.eno(+);
```
<br><br>

## 6. 크로스 조인(Cross Join)
##### - 조인 조건 없이 테이블끼리 조인한 경우
##### - 카테시안 곱(cartesian product): 크로스 조인의 결과
##### - 열의 개수: 테이블1의 열수 + 테이블2의 열수
##### - 행의 개수: 테이블1의 행수 * 테이블2의 행수
<br>
ex) SELECT * FROM employee, department;<br>
ex) SELECT * FROM employee CROSS JOIN department;<br>