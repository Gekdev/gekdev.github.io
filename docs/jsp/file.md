---
layout: default
title: File
parent: JSP
nav_order: 13
---

# JSP File
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## JSP File Processing

### 

<input type="file"> 은 파일을 선택할 수 있는 창을 만든다. 

선택된 파일을 전송할 수 있도록 enctype을 지정해준다.



<form method="post"> 의 형태로 전송한 폼에 담겨진 파라미터들은 

request 객체를 통해 이름에 해당되는 값을 얻어낼 수 있다 .



하지만 enctype="multipart/form-data"로 지정한 폼은 

request객체로 파라미터의 값을 얻어낼 수 없다.



때문에 enctype= "multipart/form-data"로 전송한 폼의 파라미터들에 대한 값을 얻어내기 위해,

<input type="file" 로 지정된 파일을 서버상의 한 폴더에 업로드 하기 위해 특별한 컴포넌트가 필요하다.

---

## cos.jar

파일 업로드 라이브러리

최신버전을 다운받고 싶다면[mvnrepository](https://mvnrepository.com/search?q=cos)로...


---

## Reference Site 

* [daraeK blog](https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=darae9108&logNo=220761003181)

