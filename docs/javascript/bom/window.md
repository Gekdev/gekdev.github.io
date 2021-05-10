---
layout: default
title: Window 
parent: Browser BOM
grand_parent: JavaScript
nav_order: 1
---

# JavaScript Window
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## The Browser Object Model (BOM)

### Charset

// 1. window객체
// 1. open() : 새로운 window객체를 생성
//       : window형태옵션
//      1) height : 새윈도우의 높이
//          2) width : 새윈도우의 너비
//          3) location : 주소입력창유무(yes,no,1,0)
//          4) menubar : 메뉴바유무(yes,no,1,0)
//          5) resizable : 화면크기조절유무(yes,no,1,0)
//          6) status : 상태표시줄유무(yes,no,1,0)
//          7) toolbar : 툴바유무(yes,no,1,0)
// 2. moveBy(x,y) : 윈도우위치를 상대적으로 이동
// 3. moveTo(x,y) : 윈도우위치를 절대적으로 이동
// 4. resizeBy(x,y) : 윈도우크기를 상대적으로 이동
// 5. resizeTo(x,y) : 윈도우크기를 절대적으로 이동
// 6. scrollBy(x,y) : 윈도우스크롤 위치를 상대적으로 이동
// 7. scrollTo(x,y) : 윈도우스크롤 위치를 절대적으로 이동
// 8. focus() : 윈도우에 초점맞춤
// 9. blur() : 위도우에 초점을 제거
// 10. close() : 윈도우를 담음	

<script>
for(var key in window) {
document.write(key + " = " + window[key] + '<br>');
}

// window.open('http://www.google.com', 'child', 'width=300, height=300', true);
var child = window.open('', '', 'width=300, height=300');
child.moveTo(0,0);

setInterval(function() {
    child.moveBy(10,10);
}, 1000);
</script>

---

// window.onload 이벤트
// window객체의 onload속성처럼 문서객체의 속성중에
// 'on'으로 시작하는 속성을 '이벤트속성'이라고 하며
// 이 이벤트속성은 함수를 할당한다.
// onload이벤트는 window객체가 로드가 완료되면 자동으로
// 할당된 함수를 실행한다.
// 즉, HTML페이지에 존재하는 모든 태그들이 화면(메모리)에
// 로딩이 완료되는 순간 onload에 할당된 함수를 실행한다.
window.onload = function() {
    alert('1st Process');
};

---
2. screen객체
		 웹브라우저의 화면이 아니라 운영체제화면의 속성을 갖는 객체
		 가장 많이 사용하는 속성은 width, height

		 1. width : 화면의 너비
		 2. height : 화면의 높이
		 3. availWidth : 실제 화면에서 사용가능한 너비
		 4. availHeight : 실제 화면에서 사용가능한 높이
		 5. colorDepth : 사용가능한 색수
		 6. pixelDepth : 한 픽셀당 비트수		
		for(var key in screen) {
			document.write(key + " = " + screen[key] + '<br>');
		}
	</script>
	<script>
		var child = window.open('', '', 'width=300, height=200');
		var width = screen.width;
		var height = screen.height;
		
		child.moveTo(0,0);
		child.resizeTo(width, height);
		
		setInterval(function() {
			child.resizeBy(-20,-20);
			child.moveBy(10,10);
		}, 1000)
	</script>
    
---
// 3. location객체
// 웹브라우저의 주소표시줄과 관련된 객체.
// location객체는 프로토콜의 종류, 호스트이름, 문서위치등의 정보를 제공
// location객체는 페이지를 이동할 때 많이 사용한다. 
// 아래 4가지방법으로 이동가능
// location = 'http://www.goolgle.com'
// location.href = 'http://www.goolgle.com'
// location.assign('http://www.goolgle.com')
// location.replace('http://www.goolgle.com')

// 메서드
// 1. assign(link) : 현재위치를 이동
// 2. reload() : 새로고침
// 3. replace(link) : 현재위치를 이동(뒤로가기 버튼을 사용할 수 없다)


// 속성
// 1. href : 문서 URL주소
// 2. host : 호스트이름과 포트 localhost:8080
// 3. hostname : localhost
// 4. port : 포트번호 8080
// 5. pathname : 디렉토리경로
// 6. hash : 앵커이름(#~)
// 7. search : 요청매개변수 ?param=10
// 8. protocol : 프로토콜의 종류 http, ftp	

for(var key in location) {
    document.write(key + " = " + location[key] + '<br>');
}

---

// 4. navigator
// 웹페이지를 실행하고 있는 브라우저에 대한 정보를 제공

// 속성
// 1. appCodeName: 브라우저의 코드명
// 2. appName : 브라우저의 이름
// 3. appVersion : 브라우저의 버전
// 4. platform : 사용중인 운영체제의 시스템환경
// 5. userAgent : 브라우저의 전체적인 정보	

for(var key in navigator) {
    document.write(key + " = " + navigator[key] + '<br>');
}		
        
        
