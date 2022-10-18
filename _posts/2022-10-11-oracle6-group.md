---
layout: post
title: "[Oracle] 6. SELECT 구문 중, GROUP BY & HAVING 절"
subtitle: "SELECT 구문 중, GROUP BY & HAVING 절 알아보기"
author: SeHyeok Park
categories : Database, DB, Oracle
tags: [Database, DB, Oracle]
comments : True
---
<div id='preview' class='display-none'>
SELECT 구문 중, GROUP BY & HAVING 절 알아보기
</div>

## 1. 그룹 함수
- **※ 그룹 함수를 사용하는 목적:** 컬럼을 그룹해서 그룹별로 통계를 구하기 위함.
- SUM(), AVG(), MAX(), MIN(), COUNT()
- GROUP BY절, HAVING절을 사용
- <span style="color:red">주의) 그룹함수는 NULL 값을 제외하고 계산!</span>
  - <span style="color:red">단, 각 함수 소괄호 안에 *을 사용할 경우, NULL 값을 포함.</span>
  <br><br>
- **(1) SUM()**
  - 그룹의 합계를 구하는 함수
  - ex) SELECT SUM(salary) FROM employee;
  <br>

- **(2) AVG()**
  - 그룹의 평균을 구하는 함수
  - ex) SELECT AVG(salary) FROM employee;
  <br>

- **(3) MAX()**
  - 그룹의 최대값을 구하는 함수
  - ex) SELECT MAX(salary) FROM employee;
  <br>

- **(4) MIN()**
  - 그룹의 최소값을 구하는 함수
  - ex) SELECT MIN(salary) FROM employee;
  <br>

- **(5) COUNT()**
  - 그룹의 개수를 구하는 함수
  - ex) SELECT COUNT(salary) FROM employee;
  <br><br>

## 2. 그룹 함수 관련 예제

### <span style="color:cornflowerblue">예제1</span>
###### Q: 사원 테이블에서 부서별 급여의 평균을 평균급여가 높은순으로 구하시오.
###### - 평균급여는 별칭을 사용하시오. (AVG_SALARY)
###### - 평균급여는 소수점 둘째자리까지 반올림하여 표현하시오.
```sql
SELECT dno, ROUND(AVG(salary), 2) AS "AVG_SALARY"
FROM employee
GROUP BY dno
ORDER BY dno DESC;
```
<br><br>

### <span style="color:cornflowerblue">예제2</span>
###### Q: 사원 테이블에서 급여의 합계를, 각 부서 안에서 업무별로 사원수와 함께 출력하시오.
###### - 급여의 합계, 사원수는 별칭을 사용하시오. (SUM, COUNT)
###### - 부서번호를 기준으로 오름차순으로 정렬하고, 부서번호가 같다면 업무를 기준으로 오름차순하여 정렬하시오.
```sql
SELECT dno, job, SUM(salary) AS SUM, COUNT(*) AS COUNT
FROM employee
GROUP BY dno, job
ORDER BY dno, job;
```
<br><br>

#### <span style="color:cornflowerblue">★ HAVING</span>
##### - 그룹에 대한 조건을 지정하여 그룹의 결과를 제한하여 출력.
<br>

### <span style="color:cornflowerblue">예제3</span>
###### Q: 부서별 급여총액이 10000이상인 부서의 부서번호, 사원수, 급여총액을 출력하시오.
###### - 사원수, 급여총액은 별칭을 사용하시오. (COUNT, SUM)
```sql
SELECT dno, COUNT(*) AS COUNT, SUM(salary) AS SUM
FROM employee
GROUP BY dno
HAVING SUM(salary) >= 10000;
```
<br><br>

### <span style="color:cornflowerblue">예제4</span>
###### Q: 급여총액이 5000을 넘는 업무에 대해서 업무와 급여총액을 출력하되, 업무가 'MANAGER'인 사원은 제외하여 출력하시오.
###### - 급여총액은 별칭을 사용하시오. (SUM)
###### - 급여총액을 기준으로 내림차순하여 정렬하시오.
```sql
SELECT job, SUM(salary) AS SUM
FROM employee
WHERE job <> 'MANAGER'
GROUP BY job
HAVING SUM(salary) > 5000
ORDER BY SUM DESC;
```
<br><br>