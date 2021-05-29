---
layout: default
title: IIS
parent: Basic
grand_parent: SQL / Oracle
nav_order: 1
---

# Basic IIS
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## IIS Installation

1. IIS설치명령

   1) winkey + r : appwiz.cpl
   
      or (menu)설정 > 앱 > 프로그램 및 기능
      
   2) windows 기능 켜기/끄기 클릭
   
   3) 메뉴 : 인터넷정보서비스(IIS)를 체크
   
   4) 설치진행

2. IIS실행

   1) 웹브라우저 주소창에 
   
      http://192.168.0.190
      
      or http://127.0.0.1
      
      or http://localhost
      
   2) c:\inetpub\wwwroot\index.html을 생성

    ipconfig 

3. IIS root 변경

   1) windows menu > windows 관리도구 > IIS(인터넷정보서비스)관리
   
   2) (menu tree) : Default Web Site
   
      a. 오른쪽 사이드 메뉴 : 기본설정 
      
      b. 실제경로 : 본인이 지정할 폴더 선택화 확인
  