---
layout: post
title: "[Oracle] 2. SELECT 구문"
subtitle: "SELECT 구문 기본 형식 및 예제 알아보기"
author: SeHyeok Park
categories : Database, DB, Oracle
tags: [Database, DB, Oracle]
comments : True
---
<div id='preview' class='display-none'>
SELECT 구문의 기본 형식 및 예제 알아보기
</div>

## 1. SELECT 구문
- 데이터를 검색(조회)하는 명령문.
- *: 모든 컬럼(필드).
- SELECT, FROM절은 필수.

##### < 알리아스(Alias) >
- 컬럼이나 테이블에 대한 별칭, 별명을 붙이는 것.
- 컬럼: 컬럼명을 보기 편하게 바꾸기 위함.
- **알리아스 사용법 3가지**
  - 컬럼명 AS "알리아스명"
  - 컬럼명 "알리아스명" -> AS 생략 가능.
  - 컬럼명 AS 알리아스명 -> \" \" 생략 가능 <span style="color:red">(단, 공백이나 특수기호를 포함한다면 \" \"로 감싸야 함.)</span>
<br>

##### < 조회 정렬 방법 >
- ORDER BY 절 사용.
- **<mark>사용법:</mark>** ORDER BY 컬럼명 ASC(or DESC);
  - ASC: 오름차순, ascending, 생략 가능
  - DESC: 내림차순, descending
  - 정렬에 사용하는 이름: 컬럼명, 수식명, 알리아스명, 열번호(앞에서부터 1번)
<br><br>

## 2. SELECT 구문 기본 형식
```sql
SELECT 컬럼명을 나열
    FROM 테이블명
 WHERE 조건
 ORDER BY 정렬할 컬럼명;
```
<br><br>

## 3. SELECT 구문 예제
- **<mark>예제1</mark>**
  - **Q:** 사원 테이블에서 부서번호가 10인 사원 정보를 확인하시오.
  ```sql
  SELECT *
     FROM employee
   WHERE dno = 10;
  ```
  <br><br>

- **<mark>예제2</mark>**
  - **Q:** 사원 테이블에서 업무를 확인하시오.
  ```sql
  SELECT job 
   &nbsp;FROM employee;
  ```
  <br><br>

- **<mark>예제3</mark>**
  - **Q:** 사원 테이블에서 부서번호를 사원이름을 기준으로 내림차순하여 확인하시오.
  ```sql
  SELECT dno
   &nbsp;FROM employee;
   ORDER BY ename DESC;
  ```
  <br><br>

- **<mark>예제4</mark>**
  - **Q:** 사원 테이블에서 사번, 사원명, 급여, 성과급, 총급여(급여+성과급)를 총급여가 높은 순으로 출력하시오.<br>
  다음 필드는 별칭을 사용하시오. (총급여: TOTAL SALARY)
  ```sql
  SELECT eno, ename, salary, commission, salary+commission as "TOTAL SALARY"
   &nbsp;FROM employee 
   ORDER BY "TOTAL SALARY" DESC;
  ```
<br><br>