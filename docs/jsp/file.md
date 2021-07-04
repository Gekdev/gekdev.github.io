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

### File Transfer Method

게시판이나 자료실 등에서 제품 이미지 등의 파일을 업로드 할 경우 request 기본객체 등에서 제공하는 기능으로는 파일 업로드를 할 수 없음

일반 파라미터를 전송할 때 사용하는 인코딩 자료와 파일을 업로드할 때 사용하는 인코딩 자료의 형식은 다름

파일을 업로드 할 경우 스트림 기반의 전송 방식에는 인코딩 방식에 따라 전송하는 데이터 형식이 달라짐

**파일을 업로드하기 위해서는 "multipart/form-data"인코딩 방식을 사용해야 함**

데이터를 "multipart/form-data" 인코딩 방식으로 전송하기 위해서는 form태그의 enctype 속성값을 "multipart/form-data"로 지정해야 함

그리고 "multipart/form-data" 인코딩 방식은 post 방식의 한 종류이기 때문에 method 속성도 post로 지정해야 함

### View Uploaded File Datas

Basic Upload Form
{: .label .label-purple .mt-2}
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
<head>
</head>
<body> 
<form action="jsp02_multipart_data.jsp" method="post" enctype="multipart/form-data">
	<table>
		<tr>
			<td>작성자</td>
			<td><input type="text" name="text" placeholder="작성자"/></td>
		</tr>		
		<tr>
			<td>업로드할 파일1</td>
			<td><input type="file" name="file1"/></td>
		</tr>
		<tr>
			<td>업로드할 파일2</td>
			<td><input type="file" name="file2"/></td>
		</tr>
		<tr>
			<td>업로드할 파일3</td>
			<td><input type="file" name="file3"/></td>
		</tr>
	</table>
	<input type="submit" value="파일 업로드" />
</form>
</body>
</html>
```

업로드된 파일들을 읽는 jsp02_multipart_data.jsp
{: .label .label-purple .mt-2}
```jsp
<%@page import="java.io.InputStream"%>
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<%

	request.setCharacterEncoding("utf-8");

	InputStream is = null;

	out.println("[");
	out.println(request.getContentType());
	out.println("]");
	
	try{
		is = request.getInputStream();
		int data = -1;
		
		//읽을게 있으면 계속 프린트 하세요
		while((data = is.read()) != -1){
			out.print((char)data); //한글자씩 찍는것
		}
	}finally{
		if(is!=null){
			try{ is.close(); } catch(Exception e) {}
		}
	}

%>
```

### Create UploadServlet 

위 코드는 값을 읽어오긴 하지만 너무 복잡하게 읽어오기 때문에 사실상 읽는게 불가능함

**따라서 업로드 서블릿을 생성해서 딱 필요한 정보만 가져오게 하는게 좋음**

UploadServlet
{: .label .label-purple .mt-2}
```java
package com.lec.file;

import java.io.IOException;
import java.io.PrintWriter;
import java.util.Collection;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import javax.servlet.http.Part;


public class UploadServlet extends HttpServlet {

	//Post타입으로만 넘어오기 때문에 Post만 지정함
	protected void doPost(HttpServletRequest req, HttpServletResponse res) 
			throws ServletException, IOException {

		//넘어온 문자값과 컨텐츠들을 utf-8로 인코딩 해줌
		req.setCharacterEncoding("utf-8");
		res.setContentType("text/html; charset=UTF-8" );
		
		//웹 브라우저에 출력할 out객체 생성 
		PrintWriter out = res.getWriter();
		out.println("<html><body>");
		
		//넘어온 값들의 컨텐츠 타입을 받아옴
		String contentType = req.getContentType();
		
		//값이 비어있지 않거나 multipart타입이 아닌 컨텐츠면 printPartInfo()메소드 실행
		if(contentType!=null && contentType.toLowerCase().startsWith("multipart/")) {
			printPartInfo(req, out);
		} else {
			//그 외는 false출력
			out.println("컨텐트타입인 multipart 타입이 아닙니다!");
		}
		
		out.println("</body></html>");
	}

	//값이 비어있지 않거나 multipart타입이 아닌 컨텐츠들을 가져옴
	private void printPartInfo(HttpServletRequest req, PrintWriter out) 
			throws IOException, ServletException {
		
		String fileName = "dummy";
		int lastIndex = 0;
		
		//전달받은 값들을 collection으로 받아옴
		Collection<Part> parts = req.getParts();
		
		//값들을 루핑돌림
		for(Part part:parts) {
			//이름출력
			out.println("<br> name = " + part.getName());
			//콘텐츠 타입 찾고 출력
			String contentType = part.getContentType();
			out.println("<br> contentType = " + contentType);
			
			//헤더가 Content-Disposition이름에 filename이 있으면 (파일을 입력받았다면)
			if(part.getHeader("Content-Disposition").contains("filename=")) {
				//그 파일의 사이즈를 출력
				out.println("<br> size = " + part.getSize());
				
				//그 파일의 전체경로를 찾기위해 getFileName() 메소드를 실행함
				fileName = getFileName(part);
				//마지막 \\값을 찾고 파일이름을 추출함
				lastIndex = fileName.lastIndexOf("\\");
				fileName = fileName.substring(lastIndex+1);
				//추출한 파일이름을 출력
				out.println("<br> filename = " +fileName);
				
				//파일이 다 출력되면 끝내기
				if(part.getSize() > 0) {
					part.write(fileName);
					part.delete();
				}
			} else {
				//이름을 입력받았다면 value만 추출
				String value = req.getParameter(part.getName());
				out.println("<br> value = " + value);
			}
			out.println("<hr>");
		}
		
	}
	
	//파일의 전체경로를 찾는 getFileName() 메소드
	private String getFileName(Part part) {
		
		for(String cd:part.getHeader("Content-Disposition").split(";")) {
			if(cd.trim().startsWith("filename")) {
				return cd.substring(cd.indexOf('=') + 1).trim().replace("\"", "");
			}
		}
		return null;
	}
}
```

실행될 수 있도록 web.xml파일에 코드를 추가해줌

web.xml
{: .label .label-purple .mt-2}
```xml
<servlet-mapping>
<servlet-name>FileUpload</servlet-name>
<url-pattern>/upload</url-pattern>
</servlet-mapping>

<servlet>
<servlet-name>FileUpload</servlet-name>
<servlet-class>com.lec.file.UploadServlet</servlet-class>
<multipart-config>
    <location>e:\lec\00.share\temp</location>
    <max-file-size>-1</max-file-size>
    <max-request-size>-1</max-request-size>
    <file-size-threshold>1024</file-size-threshold>
</multipart-config>
</servlet>
```

실행이 되는지 파일업로드 확인

파일업로드 : jsp03_fileupload.jsp
{: .label .label-purple .mt-2}
<div class="code-example" markdown="1">
![](https://gekdev.github.io/docs/jsp/example/uploading.jpg)
</div>
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
<head>
</head>
<body>
<form action="upload" method="post" enctype="multipart/form-data">
	<p>text1: <input type="text" name="text1" /></p>
	<p>file1: <input type="file" name="file1"/></p>
	<p>file2: <input type="file" name="file2"/></p>		
	<input type="submit" value="업로드하기" />
</form>
</body>
</html>
```

![](https://gekdev.github.io/docs/jsp/example/servletfinal.jpg)

---

## File Processing with Library

### multipart/form-data Problem

&#9656; `<input type="file">` 은 파일을 선택할 수 있는 창을 만듦. 선택된 파일을 전송할 수 있도록 enctype을 지정해줘야 함

&#9656; `<form method="post">` 의 형태로 전송한 폼에 담겨진 파라미터들은 request 객체를 통해 이름에 해당되는 값을 얻어낼 수 있음

&#9656; 하지만 enctype="multipart/form-data"로 지정한 폼은 request객체로 파라미터의 값을 얻어낼 수 없음

**enctype= "multipart/form-data"로 전송한 폼의 파라미터들에 대한 값을 얻어내기 위해, input type="file" 로 지정된 파일을 서버상의 한 폴더에 업로드 하기 위해 특별한 컴포넌트가 필요함**

### Download File Upload Library 

**cos.jar 파일에는 필요한 컴포넌트(파일 업로드 라이브러리)가 있음**

<span class="fs-2">
[Servlets](http://servlets.com/){: .btn .btn-outline .mt-2}
</span>

여기서는 [cos.jar](https://gekdev.github.io/docs/jsp/example/cos.jar), [commons-fileupload-1.3.3.jar](https://gekdev.github.io/docs/jsp/example/commons-fileupload-1.3.3.jar), [commons-io-2.5.jar](https://gekdev.github.io/docs/jsp/example/commons-io-2.5.jar)을 사용했음

### File Upload Form

**파일을 업로드할 폼을 작성**

jsp04_fileuploadForm
{: .label .label-purple .mt-2}
<div class="code-example" markdown="1">
![](https://gekdev.github.io/docs/jsp/example/uploadform.jpg)
</div>
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
<head>
</head>
<body>
<h3>파일업로드 하기</h3>
<form action="jsp05_fileupload.jsp" method="post" enctype="multipart/form-data">
	<table>
		<tr>
			<td>올린사람</td>
			<td><input type="text" name="name"/></td>
		</tr>
		<tr>
			<td>제목</td>
			<td><input type="text" name="subject"/></td>
		</tr>
		<tr>
			<td>파일1</td>
			<td><input type="file" name="fileName1"/></td>
		</tr>
		<tr>
			<td>파일2</td>
			<td><input type="file" name="fileName2"/></td>
		</tr>
	</table>
	<input type="submit" value="파일업로드" />
</form>
</body>
</html>
```

### File Upload 

**선택된 파일들을 확인해주고 실질적으로 업로드하게 하는 jsp파일**

uploadPath에 업로드 할 경로를 적어줌

jsp05_fileupload
{: .label .label-purple .mt-2}
<div class="code-example" markdown="1">
![](https://gekdev.github.io/docs/jsp/example/upload.jpg)
</div>
```jsp
<%@page import="java.util.Enumeration"%>
<%@page import="com.oreilly.servlet.multipart.DefaultFileRenamePolicy"%>
<%@page import="com.oreilly.servlet.MultipartRequest"%>
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<%

	//E:/lec/05.jsp/.metadata/.plugins/org.eclipse.wst.server.core/tmp0\wtpwebapps/jsp05_fileupload/upload
	//즉, 이클립스 경로가 나옴
	String uploadPath = request.getRealPath("upload");
	//다른곳에 업로드 할 예정이라서 따로 설정했음	
	uploadPath = "e:\\lec\\00.share\\upload";
	
	int size = 1024*1024*1024; //10mb
	String name = "";
	String subject = "";
	String filename1 = "";
	String filename2 = "";
	String orgfilename1 = "";
	String orgfilename2 = "";
	
	try{
		//MultipartRequest 이 코드가 실제로 파일 업로드를 담당하는 부분
		//MultipartRequest 객체를 생성해서 파일에 대한 정보들을 업데이트 하고 업로드 함
		//cos.jar파일을 이용해서 하는 방법
		MultipartRequest multi = new MultipartRequest(
				request,	//폼에서 가져온 인자 값을 얻기 위해 request객체를 전달해 주는 것
				uploadPath, //업로드 될 파일의 위치를 의미
				size,		//한번에 업로드할 크기를 의미하며 최대 크기를 넘는경우 Exception이 발생
				"utf-8",	//한글 이름이 넘어올 경우 한글에 문제되지 않도록 지정
				new DefaultFileRenamePolicy() //똑같은 파일을 업로드 할 경우 중복되지 않도록 파일이름을 변환해 주는 기능
				);
		
		//MultipartRequest객체가 가져온 파라미터의 이름, 비밀번호, 파일들의 값들을 가져옴
		name = multi.getParameter("name");
		subject = multi.getParameter("subject");
		//파일들은 Enumeration 값으로 여러개를 가져옴
		Enumeration files = multi.getFileNames();

		//가져온 파일들의 값을 하나씩 추출하기
		//마지막에 저장된 값이 (file2)가 먼저 추출됨
		String file2 = (String)files.nextElement();
		//추출한 파일의 이름을 가져오기
		filename2 = multi.getFilesystemName(file2);
		//추출한 파일의 원래 이름을 가져오기
        orgfilename2 = multi.getOriginalFileName(file2);
        
        String file1 = (String)files.nextElement();
        filename1 = multi.getFilesystemName(file1);
        orgfilename1 = multi.getOriginalFileName(file1);
        
	}catch(Exception e){
		e.printStackTrace();
	}
	
%>
<!DOCTYPE html>
<html>
<head>
</head>
<body>

<h3>파일업로드</h3>	   
<p>아래 정보가 맞는지 확인하세요!</p>            
<form action="jsp06_filecheck.jsp" method="post" name="filecheck">
	<table>
		<tr>
			<td>올린사람: </td>
			<td><input type="text" name="name" value="<%=name%>" readonly/></td>
		</tr>
		<tr>
			<td>제목: </td>
			<td><input type="text" name="subject" value="<%=subject%>" readonly/></td>
		</tr>
		<tr>
			<td>파일1: </td>
			<td><input type="text" name="filename1" value="<%=filename1%>" readonly/></td>
		</tr>
		<tr>
			<td>파일1 원래이름: </td>
			<td><input type="text" name="orgfilename1" value="<%=orgfilename1%>" readonly/></td>
		</tr>
		<tr>
			<td>파일2: </td>
			<td><input type="text" name="filename2" value="<%=filename2%>" readonly/></td>
		</tr>
		<tr>
			<td>파일2 원래이름: </td>
			<td><input type="text" name="orgfilename2" value="<%=orgfilename2%>" readonly/></td>
		</tr>
	</table>
</form>
<div><a href="#" onclick="javascript:filecheck.submit()">파일업로드및 다운로드페이지로 이동</a></div>
<div><a href="jsp04_fileuploadForm.jsp">돌아가기</a></div>

</body>
</html>
```

### File Check

**업로드 된 파일을 확인시켜주고 다운로드하게 만듦**

jsp06_filecheck
{: .label .label-purple .mt-2}
<div class="code-example" markdown="1">
![](https://gekdev.github.io/docs/jsp/example/filecheck.jpg)
</div>
```jsp
<%@page import="java.net.URLEncoder"%>
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<%
	//jsp05_fileupload에서 가져온 파라미터들을 인코딩
	request.setCharacterEncoding("utf-8");

	//jsp05_fileupload에서 가져온 파라미터들
	String name = request.getParameter("name");
	String subject = request.getParameter("subject");
	String filename1 = request.getParameter("filename1");
	String filename2 = request.getParameter("filename2");
	String orgfilename1 = request.getParameter("orgfilename1");
	String orgfilename2 = request.getParameter("orgfilename2");

	//크롬에서는 한글을 인코딩 하지 않아도 자동으로 인코딩해서 전달하지만, IE는 인코딩해서 전달해야함
	filename1 = URLEncoder.encode(filename1, "utf-8");
	filename2 = URLEncoder.encode(filename2, "utf-8");
%>
<!DOCTYPE html>
<html>
<head>
</head>
<body>
<h3>파일이 업로드 되었습니다! 아래 링크를 눌러 다운로드 하세요</h3>
<table>
	<tr>
		<td>올린 사람</td>
		<td><%= name %></td>
	</tr>
	<tr>
		<td>제목</td>
		<td><%= subject %></td>
	</tr>
	<!-- 파일명 링크  -->
	<tr>
		<td>파일명 1</td>
		<td><a href="jsp07_filedownload.jsp?fn=<%=filename1%>"><%=orgfilename1 %></a></td>
	</tr>
	<tr>
		<td>파일명 2</td>
		<td><a href="jsp07_filedownload.jsp?fn=<%=filename2%>"><%=orgfilename2 %></a></td>
	</tr>
</table>
</body>
</html>
```

### File Download Process

jsp07_filedownload
{: .label .label-purple .mt-2}
<div class="code-example" markdown="1">
![](https://gekdev.github.io/docs/jsp/example/download.jpg)
</div>
```jsp
<%@page import="java.net.URLEncoder"%>
<%@page import="java.io.FileInputStream"%>
<%@page import="java.io.File"%>
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<%
	//jsp06_filecheck에서 가져온 파라미터들을 인코딩
	request.setCharacterEncoding("utf-8");
	//파일명 링크에서 a태그의 파라미터값으로 던져준 filename(fn)을 filename으로 가져옴 
    String filename = request.getParameter("fn");
    
    //다운로드부터 경로를 따로 잡아줬기 때문에 이건 안됨
  	//String downloadPath = context.getRealPath(savePath);
	//ServletContext context = getServletContext();		//context = org.apache.catalina.core.ApplicationContextFacade@65ffa18
	//String dnPath = context.getRealPath("download");	//dnPath = E:\lec\05.jsp\.metadata\.plugins\org.eclipse.wst.server.core\tmp0\wtpwebapps\jsp05_fileupload\download
    
    String downloadPath = "e:\\lec\\00.share\\upload\\";	//e:\lec\00.share/upload\
    String saveFilePath = downloadPath + filename;  	//jquery-migrate-1.4.1.min1.js
    

    File f = new File(saveFilePath);
    
    FileInputStream fis = new FileInputStream(saveFilePath);
    
    //확장자를 minetype이라고 생각하면 됨, sMineType값 생성
    String sMineType = getServletContext().getMimeType(saveFilePath);
    
    //System.out.println("sMineType >>" + sMineType);	//sMineType >>application/javascript
    
    //octet-stream 은 8비트로 된 일련의 데이터를 뜻함 
    //지정되지 않은 파일 형식을 의미
    if(sMineType == null) {
        sMineType = "application/octet-stream";
    }
    
 	// 파일명 한글 인코딩 업로드 (한글명이 깨지는 것을 방지);
    String sEncoding = new String(filename.getBytes("utf-8"), "8859_1");
    // String sEncoding = URLEncoder.encode(filename, "utf-8"); //이 방법도 가능
    
    //응답객체 헤더에 값을 저장하기
    response.setContentType(sMineType);
    response.setHeader("Content-Transfer-Encoding", "binary");
    response.setHeader("Content-Disposition", "attachment; filename= " + sEncoding);
    
    //ServletOutputStream 객체 os 생성, 응답객체
    ServletOutputStream os = response.getOutputStream();

    //바이트 배열 b 생성
    byte[] b = new byte[4096];
    int numRead;
    
    //바이트 배열 b의 0번 부터 numRead 번까지 브라우저 출력
    while((numRead = fis.read(b, 0, b.length)) != -1 ){
    	//응답객체에 출력하기
    	os.write(b, 0, numRead);
    }
    
    //모두 사용후 종료
    os.flush();
    os.close();
    fis.close();
%>
```

---

## Reference Site

* [daraeK blog](https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=darae9108&logNo=220761003181)
