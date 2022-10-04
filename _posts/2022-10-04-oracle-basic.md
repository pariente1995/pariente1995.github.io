---
layout: post
title: "[Oracle] 1. 데이터베이스 관련 간략한 정보 및 Oracle 계정 생성 및 권한 부여"
subtitle: "데이터베이스에 대한 대략적인 정보와 Oracle 계정 생성 및 권한 부여 방법 알아보기"
author: SeHyeok Park
categories : Database, DB, Oracle
tags: [Database, DB, Oracle]
comments : True
---
<div id='preview' class='display-none'>
데이터베이스 관련 기본 정보 및 Oracle 계정 생성, 권한 부여 방법 알아보기
</div>

## 1. 데이터
- Datum: 데이터 1개, 단수형
- Data: 데이터의 모음, 복수형
- **<mark>Database: <u>데이터의 집합</u></mark>**
<br><br>

## 2. DBMS
- **DBMS:** DataBase Management System, 데이터베이스 관리 시스템
<br><br>

## 3. DBMS의 종류
- 객체형 DBMS, 계층형 DBMS, 관계형 DBMS 등등이 있음.
- 일반적으로 가장 많이 사용하는 DBMS: ***관계형 DBMS(Relational DBMS, RDBMS)***
- cf.) ***No-SQL:*** DB를 간편하게 다룰 수 있도록 한 시스템.
  - <span style="color:red">But) 보안이 취약.</span>
  - ex) 트위터, 페이스북, 인스타그램 등에서 사용됨.
<br><br>

## 4. RDBMS(Relational Database Management System)
- 관계형 DBMS.
- 표준 SQL의 규칙에 따르고, 각 회사별로 내용을 변형, 추가해서 사용하고 있는 추세.
- Oracle, MySQL, MS-SQL(SQL Server), Sybase, MariaDB, PostgreDB, H2 등등이 있음.
- Relation(릴레이션)이란 테이블(table)을 말함.
- 행과 열을 통해서 데이터를 표의 형태로 다룸.
<br><br>

## 5. SQL(Structured Query Language, 구조화된 질의 언어)
- RDBMS에서 사용하는 언어.
- 표준 SQL + 각 회사에서 추가한 SQL.

## 6. SQL 명령의 종류
**(1) DCL(Data Control Language, 데이터 제어어)**
- 관리자급의 기능.
- 권한을 부여하고, 회수하는 기능.
- **<mark>명령어:</mark> grant, revoke ...**
<br>

**(2) DDL(Data Definition Language, 데이터 정의어)**
- 테이블을 생성, 구조를 변경, 삭제하는 기능.
- **<mark>명령어:</mark> create, alter, drop ...**
<br>

**(3) DML(Data Manipulation Language, 데이터 조작어)**
- 테이블에 데이터를 추가, 수정, 삭제, 검색.
- **<mark>명령어:</mark> insert, update, delete, select ...**
<br>

**(4) TCL(Transaction Control Language, 트랜잭션 제어어)**
- 트랜잭션을 제어하는 기능.
- **<mark>명령어:</mark> commit, rollback, savepoint ...**
<br>

## 7. Oracle 기본 사용법
- **Oracle Version**
  - Oracle Standard 버전: 보통 회사에서는 11~18 버전을 많이 사용(유료).
  - Oracle Express 버전: 학생 교육용(무료), 11버전과 18버전 2개의 종류만 지원.

  ##### <span style="color:red">※ 필자는 Oracle Express 11 Version을 사용하였다!</span>
  <br>

- **Oracle 계정**
  - DBMS에 접근해서 사용할 수 있는 사용자.
  - 관리자 계정: system, sys(불완전 복구)
  - 사용자 계정: ex) aws01
  <br>

- **계정 생성 및 권한 부여(cmd에서 실행)**
  ```sql
  sqlplus system/[비밀번호]; -- 관리자 계정 로그인, 오라클 설치 시 입력한 비밀번호
  ex) sqlplus system/1234;

  create user [아이디] identified by [비밀번호]; -- 사용자 계정 생성
  ex) create user aws01 identified by 1234;

  /* 
    - DB 접속 권한과 개체를 생성/수정/삭제 권한 부여.
    - 관리자처럼 모든 권한을 가질 수 있게 권한 부여.
  */
  grant connect, resource, dba to [아이디]; -- 사용자 계정에 권한 부여
  ex) grant connect, resource, dba to aws01;

  sqlplus [아이디]/[비밀번호];
  ex) sqlplus aws01/1234; -- 사용자 계정 로그인

  show user; -- 현재 로그인한 계정 확인

  exit; -- 로그인 종료
  ```
