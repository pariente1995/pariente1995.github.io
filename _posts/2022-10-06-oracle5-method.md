---
layout: post
title: "[Oracle] 5. Oracle 함수 모음"
subtitle: "Oracle에서 사용하는 함수 알아보기"
author: SeHyeok Park
categories : Database, DB, Oracle
tags: [Database, DB, Oracle]
comments : True
---
<div id='preview' class='display-none'>
Oracle에서 사용하는 다양한 함수 알아보기
</div>

## 1. Dual 테이블
- 한행 한컬럼을 가지고 있는 가상 테이블.
- 간단한 계산 결과를 확인하는 용도로 사용.
ex) SELECT * FROM DUAL;
![DUAL 테이블]({{ site.baseurl }}/assets/img/oracle-post5-1.png){: width="40%"}

## 2. Oracle 함수 모음
##### (1) 문자열을 처리하는 함수
- **UPPER()**
  - 문자열을 대문자로 변환하는 함수.<br>
  ex) SELECT UPPER('oracle') FROM DUAL;<br>
  <br>

- **LOWER()**
  - 문자열을 소문자로 변환하는 함수.<br>
  ex) SELECT LOWER('ORACLE') FROM DUAL;<br>
  <br>

- **INITCAP()**
  - 문자열의 첫 글자만 대문자, 나머지 글자는 소문자로 변환하는 함수.<br>
  ex) SELECT INITCAP('oracle') FROM DUAL;<br>
  <br>

- **LENGTH()**
  - 문자열의 길이를 반환하는 함수.<br>
  - 영어/한글의 구분없이 사용.<br>
  ex) SELECT LENGTH('oracle') FROM DUAL;<br>
  ex) SELECT LENGTH('오라클') FROM DUAL;<br>
  <br>

- **LENGTHB()**
  - 문자열의 길이를 바이트로 반환하는 함수.<br>
  - 영어는 1글자가 1byte, 한글은 1글자 3byte로 취급.<br>
  - <span style="color:red">스탠다드 버전에서 한글은 1글자를 2byte로 취급!</span><br>
  ex) SELECT LENGTHB('oracle') FROM DUAL;<br>
  ex) SELECT LENGTHB('오라클') FROM DUAL;<br>
  <br>

- **CONCAT()**
  - 문자열 2개를 하나로 합치는 함수.<br>
  ex) SELECT CONCAT('DCL', 'DDL') FROM DUAL;<br>
  **<mark>cf) ||: 문자열 연결 연산자</mark>**<br>
  ex) SELECT '오라클 ' || '공부를' || ' 해보아요.' FROM DUAL;<br>
  <br>

- **SUBSTR(문자열, 시작위치, 개수)**
  - 문자열의 시작위치에서 개수만큼 문자열을 추출하는 함수.<br>
  ex) SELECT SUBSTR('sing for gold', 10, 4) FROM DUAL;<br>
  <br>

- **SUBSTRB(문자열, 바이트 시작위치, 바이트수)**
  - 문자열의 시작위치에서 바이트수만큼 문자열을 추출하는 함수.<br>
  ex) SELECT SUBSTRB('오라클', 2, 2) FROM DUAL;<br>
  ex) SELECT SUBSTRB('오라클', 4, 6) FROM DUAL;<br>
  <br>

- **INSTR()**
  - 문자열에서 특정문자의 위치를 찾는 함수.<br>
  - **INSTR(문자열, 찾는 문자):** 문자열에서 찾는 문자가 나오는 첫번째 위치.<br>
    ex) SELECT INSTR('HELLO ORACLE', 'E') FROM DUAL;<br><br>
  
  - **INSTR(문자열, 찾는 문자, 찾는 위치):** 문자열에서 찾는 문자를, 찾는 위치부터 시작하여 나오는 위치.<br>
    ex) SELECT INSTR('HELLO ORACLE', 'E', 3) FROM DUAL;<br><br>

  - **INSTR(문자열, 찾는 문자, 찾는 위치, 몇번째):** 문자열에서 찾는 문자를 찾는 위치부터 시작하여 몇번째로 나오는 위치.<br>
    ex) SELECT INSTR('HELLO ORACLE', 'E', 1, 2) FROM DUAL;
  <br><br>

- **LPAD(문자열, 전체크기, 채울문자)**
  - 문자열의 왼쪽에 패딩을, 지정한 문자로 채우는 함수.<br>
  ex) SELECT LPAD('ORACLE', 10, '@') FROM DUAL;<br>
  <br>

- **RPAD(문자열, 전체크기, 채울문자)**
  - 문자열의 오른쪽에 패딩을, 지정한 문자로 채우는 함수.<br>
  ex) SELECT RPAD('ORACLE', 10, '@') FROM DUAL;<br>
  <br><br>

##### (2) 숫자를 처리하는 함수
- **ROUND(): 반올림 함수.**
  - 반올림하여 1의 자리까지 표현<br>
  ex) SELECT ROUND(98.7654) FROM DUAL;<br>

  - 반올림하여 소수점 첫째자리까지 표현<br>
  ex) SELECT ROUND(98.7654, 1) FROM DUAL;<br>

  - 반올림하여 소수점 둘째자리까지 표현<br>
  ex) SELECT ROUND(98.7654, 2) FROM DUAL;<br>

  - 반올림하여 10의 자리까지 표현<br>
  ex) SELECT ROUND(34567, -1) FROM DUAL;<br>

  - 반올림하여 100의 자리까지 표현<br>
  ex) SELECT ROUND(34567, -2) FROM DUAL;<br>
  <br>

- **TRUNC(): 버림 함수.**
  - 소수점 이하 버림<br>
  ex) SELECT TRUNC(98.7654) FROM DUAL;<br>

  - 소수점 첫째자리가지 표현, 나머지는 버림<br>
  ex) SELECT TRUNC(98.7654, 1) FROM DUAL;<br>

  - 소수점 둘째자리가지 표현, 나머지는 버림<br>
  ex) SELECT TRUNC(98.7654, 2) FROM DUAL;<br>

  - 10의 자리까지 표현, 나머지는 버림<br>
  ex) SELECT TRUNC(34567, -1) FROM DUAL;<br>

  - 100의 자리까지 표현, 나머지는 버림<br>
  ex) SELECT TRUNC(34567, -2) FROM DUAL;<br>
  <br>

- **MOD(나누어지는 수, 나누는 수): 나머지를 계산하는 함수.**<br>
ex) SELECT MOD(10, 3) FROM DUAL;<br>
ex) SELECT MOD(10, 4) FROM DUAL;<br>
<br><br>

##### (3) 날짜를 처리하는 함수
- SYSDATE: 시스템에서 현재 날짜를 획득하는 함수.
- 날짜는 홑따옴표(\' \')로 감싸서 표현.
- 날짜는 +, -는 가능, *, /는 불가능.
- \>, >=, <, <=, =, <>의 비교 연산은 가능.
- 년월일의 구분은 / 또는 -를 사용. 
<br><br>

- **TO_DATE(): 날짜 형식을 가진 문자열을 날짜형으로 변환하는 함수.**
  - '2022/10/06' -> 문자열
  - TO_DATE('2022/10/06') -> 날짜형
  - TO_DATE('2022/10/06', 'yyyy/mm/dd') -> 2022/10/06
  - TO_DATE('2022/10/06', 'yyyy-mm-dd') -> 2022/10/06
  <br><br>

- **MONTHS_BETWEEN(날짜1, 날짜2) - 날짜1과 날짜2 사이의 개월수를 구하는 함수.**
  - 날짜1이 최근 날짜1, 날짜2가 이전 날짜<br>
  ex) SELECT MONTHS_BETWEEN(TO_DATE('2022/10/06'), TO_DATE('2022/05/06')) FROM DUAL;
  <br><br>
    
- **ADD_MONTHS(날짜, 개월): 날짜에 개월을 더한 날짜를 구하는 함수.**
  - 개월에 음수를 사용하면 이전 날짜가 됨.
  ex) SELECT ADD_MONTHS(TO_DATE('2022/10/06'), 3) FROM DUAL;
  <br><br>

- **NEXT_DAY(날짜, 요일): 날짜로부터 다가오는 요일의 날짜를 구하는 함수.**
  ex) SELECT NEXT_DAY(SYSDATE, '일요일') FROM DUAL;
  <br><br>

- **LAST_DAY(날짜): 날짜에 해당하는 월의 마지막 날짜를 구하는 함수.**
  ex) SELECT LAST_DAY(SYSDATE) FROM DUAL;
  <br><br>

##### (4) 날짜, 숫자 관련 출력 서식
- 형 변환 함수
  - **TO_CHAR()**
  - 날짜와 숫자를 다양한 포맷으로 형변환하여 문자열로 출력하는 함수.
  - 날짜와 숫자를 다양한 형식으로 출력할 때 사용함.
  <br><br>

- **<mark>날짜와 시간과 관련된 서식</mark>**
  - /: 년월일을 /로 구분하여 출력
  - -: 년월일을 -로 구분하여 출력
  - yyyy: 년도 4자리, mm: 월 2자리, dd: 일 2자리, day: 긴 요일명, dy: 짧은 요일명
  - hh: 12시간, hh24: 24시간, mi: 분, ss: 초, am 또는 pm: 오전 오후 표시

    ex) SELECT TO_CHAR(TO_DATE('2022/10/06'), 'yyyy-mm-dd') FROM DUAL;<br>
    ex) SELECT TO_CHAR(TO_DATE('2022/10/06'), 'yyyy-mm-dd day') FROM DUAL;<br>
    ex) SELECT TO_CHAR(TO_DATE('2022/10/06'), 'yyyy-mm-dd dy') FROM DUAL;<br>
    ex) SELECT TO_CHAR(SYSDATE, 'hh:mi:ss') FROM DUAL;<br>
    ex) SELECT TO_CHAR(SYSDATE, 'pm hh:mi:ss') FROM DUAL;<br>
    ex) SELECT TO_CHAR(SYSDATE, 'pm hh24:mi:ss') FROM DUAL;<br>
    ex) SELECT TO_CHAR(SYSDATE, 'yyyy-mm-dd day pm hh24:mi:ss') FROM DUAL;<br>
<br>

- **<mark>숫자와 관련된 서식</mark>**
  - 0 : 무효한 자리의 값을 0으로 표현
  - 9 : 무효한 자리의 값은 생략
  - , : 천단위 구분 기호
  - . : 소수점
  - $ : 숫자 앞에 $ 통화기호 표시
  - L : 숫자 앞에 해당 지역의 통화기호 표시

  ex) SELECT TO_CHAR(1600, '9,999,999') FROM DUAL;<br>
  ex) SELECT TO_CHAR(1600, '0,000,000') FROM DUAL;<br>
  ex) SELECT TO_CHAR(1600, '$9,999,999') FROM DUAL;<br>
  ex) SELECT TO_CHAR(1600, 'L9,999,999') FROM DUAL;<br>
  ex) SELECT TO_CHAR(4567.76543, '9,999.999') FROM DUAL;<br>
  ex) SELECT TO_CHAR(4567.76543, '9,999,9999') FROM DUAL;<br>
  ex) SELECT TO_CHAR(4567.76543, '9,999,99999') FROM DUAL;<br>
  ex) SELECT TO_CHAR(4567.76543, '9,999,99999999') FROM DUAL;<br>
  ex) SELECT TO_CHAR(4567.76543, '0,000.000') FROM DUAL;<br>
  ex) SELECT TO_CHAR(4567.76543, '0,000,0000') FROM DUAL;<br>
  ex) SELECT TO_CHAR(4567.76543, '0,000,00000') FROM DUAL;<br>
  ex) SELECT TO_CHAR(4567.76543, '0,000,00000000') FROM DUAL;<br>
<br>

##### (5) NULL 데이터 관련 함수
- **NVL(컬럼명, 값1):** 컬럼에 해당하는 값이 NULL일 때, 값1을 사용하는 함수.<br><br>
- **NVL2(컬럼명, 값1, 값2):** 컬럼에 해당하는 값이 NULL이 아닐 때 값1, NULL일 때 값2를 사용하는 함수.<br><br>
- **NULLIF(값1, 값2):** 두 값이 같다면 NULL, 같지 않으면 첫번째 값을 사용하는 함수.<br><br>
- **COALESCE(컬럼명1, 컬럼명2, 컬럼명3 ... 기본값)**
  - 컬럼1이 NULL이 아니면 컬럼1을 사용하고,<br>
    컬럼1이 NULL이고, 컬럼2가 NULL이 아니면 컬럼2를 사용하고,<br>
    컬럼2가 NULL이고, 컬럼3이 NULL이 아니면 컬럼3을 사용하고,<br>
    컬럼3이 NULL이면 기본값을 사용.
<br><br>

##### (6) 기타 함수
- **DECODE(컬럼 또는 수식, 조건1, 결과1, 조건2, 결과2, 조건3, 결과3 ... 기본값)**
  - SWITCH ~ CASE문과 비슷.
  - 컬럼 또는 수식이 조건1과 같으면 결과1, 조건2와 같으면 결과2, 조건3과 같으면 결과3, 그 나머지는 기본값을 사용.<br><br>
  - **Q:** 부서명은 10이면 ACCOUNTING, 20이면 RESEARCH, 30이면 SALES, 40이면 OPERATIONS, 그 나머지는 DEFAULT로 출력하시오.
    ```sql
    SELECT ename, dno, 
    decode(dno, 10, 'ACCOUNTING', 20, 'RESEARCH', 30, 'SALES', 40, 'OPERATIONS', 'DEFAULT') AS DNAME 
    FROM employee;
    ```
    <br><br>

- **CASE 함수**
  - IF문 비슷한 구조를 갖는 함수. 
  - 프로그래밍적인 형태를 갖는 함수. 
  - DECODE() 함수와 비슷한 용도로 사용.
  - 컬럼 또는 수식이 조건1과 같으면 결과1, 조건2와 같으면 결과2, 조건3과 같으면 결과3, 그 나머지는 기본값을 사용.<br><br>
  - <mark>형식 1</mark>
    ```sql
    CASE 컬럼 또는 수식
        WHEN 조건1 THEN 결과1
        WHEN 조건2 THEN 결과2
        WHEN 조건3 THEN 결과3
        ...
        ELSE 기본값
    END
    ```
    <br>

  - <mark>형식 2</mark>
    ```sql
    CASE
        WHEN 컬럼 = 조건1 THEN 결과1
        WHEN 컬럼 = 조건2 THEN 결과2
        WHEN 컬럼 = 조건3 THEN 결과3
        ...
        ELSE 기본값
    END
    ```
    <br>

  - **Q:** 부서명은 10이면 ACCOUNTING, 20이면 RESEARCH, 30이면 SALES, 40이면 OPERATIONS, 그 나머지는 DEFAULT로 출력하시오.
    ```sql
    -- 형식 1
    SELECT ename, dno, 
    (CASE dno 
        WHEN 10 THEN 'ACCOUNTING'
        WHEN 20 THEN 'RESEARCH'
        WHEN 30 THEN 'SALES'
        WHEN 40 THEN 'OPERATIONS'
        ELSE 'DEFAULT'
    END) AS dname
    FROM employee;

    -- 형식 2
    SELECT ename, dno, 
    (CASE
        WHEN dno = 10 THEN 'ACCOUNTING'
        WHEN dno = 20 THEN 'RESEARCH'
        WHEN dno = 30 THEN 'SALES'
        WHEN dno = 40 THEN 'OPERATIONS'
        ELSE 'DEFAULT'
    END) AS dname
    FROM employee;
    ```
    <br><br>