---
layout: default
title: SQL
parent: Basic
grand_parent: Database
nav_order: 3
---

# Basic SQL 
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## 데이터 언어 SQL

데이터 언어 : 데이터 언어는 표준 데이터베이스 언어인 SQL(structured Query Language)을 의미하며 3가지 종류가 있음

데이터베이스를 조작하는 언어
다른 시스템으로의 이식성이 좋음 (ex: python 등)
클라이언트/서버 구조


언어 종류 | 특징 | 명령어 예

데이터 정의어 DDL

(Data Definition Language)

새로운 데이터베이스 구조를 정의하고 기존 데이터베이스 구조를 변경하는 명령어 집합

데이터베이스 구조를 표현하는 데이터베이스 스키마를 명세하기 위해 사용

CREATE ALTER

DROP

데이터 조작어 DML

(Data Manipulation Language)

데이터베이스 안의 데이터를 실제 조작하는 명령어 집합

DBMS에게 데이터의 입력, 수정, 삭제 및 검색을 요청하기 위해 사용

INSERT UPDATE

DELETE SELECT

데이터 제어어 DCL

(Data Control Language)

데이터베이스를 제어하고 통제하기 위해 사용하는 명령어 집합

데이터베이스가 무결성을 유지하도록 각종 제약이나 옵션을 설정함

Mutual exclusion( 상호배제 )를 통한 transaction이 서로 방해를 받지 않도록 병행 제어

GRANT REVOKE

CREATE USER

COMMIT ROLLBACK

---

## Representative Site 

### Information

* [데이터베이스 기초 강의 (DQL/DML)](https://nackwon.tistory.com/95?category=796152)
