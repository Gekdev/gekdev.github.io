---
layout: default
title: Examples
parent: AJAX
grand_parent: JavaScript
nav_order: 4
---

# AJAX Examples
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## XML

### XML Example

```js
<script>
function loadDoc() {                                                    // 1. 버튼을 누르면 loadDoc()이 실행됨
  var xhttp = new XMLHttpRequest();                                     // 2. XMLHttpRequest 객체 생성
  xhttp.onreadystatechange = function() {                               // 3. 서버 응답이 준비 될 때 실행될 함수를 추가 한 후 서버로 요청
    if (this.readyState == 4 && this.status == 200) {                   // 4. 서버 응답이 준비되면 myFunction실행 
      myFunction(this);
    }
  };
  xhttp.open("GET", "cd_catalog.xml", true);
  xhttp.send();
}

function myFunction(xml) {
  var i;
  var xmlDoc = xml.responseXML;                                                 
  var table="<tr><th>Artist</th><th>Title</th></tr>";
  var x = xmlDoc.getElementsByTagName("CD");
  for (i = 0; i <x.length; i++) {                                       // 5. 노드 (요소)를 XML 파일에서 추출
    table += "<tr><td>" +
    x[i].getElementsByTagName("ARTIST")[0].childNodes[0].nodeValue +
    "</td><td>" +
    x[i].getElementsByTagName("TITLE")[0].childNodes[0].nodeValue +
    "</td></tr>";
  }
  document.getElementById("demo").innerHTML = table;                    // 6. 위의 요소들로 HTML 테이블 작성후 "demo"요소 업데이트
}
</script>
```

<span class="fs-2">
[W3C Example](){https://www.w3schools.com/js/tryit.asp?filename=tryjs_ajax_xml2}
</span>

### XML Applications

HTML applications using XML, HTTP, DOM, and JavaScript

#### The XML Document Used

XML file called [cd_catalog.xml](https://www.w3schools.com/js/cd_catalog.xml)

#### Display XML Data in an HTML Table

```html
<html>
<head>
<style>
table, th, td {
  border: 1px solid black;
  border-collapse: collapse;
}

th, td {
  padding: 5px;
}
</style>
</head>
<body>

<table id="demo"></table>

<script>
function loadXMLDoc() {
  var xmlhttp = new XMLHttpRequest();
  xmlhttp.onreadystatechange = function() {
    if (this.readyState == 4 && this.status == 200) {
      myFunction(this);
    }
  };
  xmlhttp.open("GET", "cd_catalog.xml", true);
  xmlhttp.send();
}
function myFunction(xml) {
  var i;
  var xmlDoc = xml.responseXML;
  var table="<tr><th>Artist</th><th>Title</th></tr>";
  var x = xmlDoc.getElementsByTagName("CD");
  for (i = 0; i <x.length; i++) {
    table += "<tr><td>" +
    x[i].getElementsByTagName("ARTIST")[0].childNodes[0].nodeValue +
    "</td><td>" +
    x[i].getElementsByTagName("TITLE")[0].childNodes[0].nodeValue +
    "</td></tr>";
  }
  document.getElementById("demo").innerHTML = table;
}
</script>

</body>
</html>
```

<span class="fs-2">
[W3C Example](https://www.w3schools.com/js/tryit.asp?filename=tryjs_ajax_display_table){: .btn  .btn-outline .mt-2}
</span>

#### Display the First CD in an HTML div Element

```js
displayCD(0);

function displayCD(i) {
  var xmlhttp = new XMLHttpRequest();
  xmlhttp.onreadystatechange = function() {
    if (this.readyState == 4 && this.status == 200) {
      myFunction(this, i);
    }
  };
  xmlhttp.open("GET", "cd_catalog.xml", true);
  xmlhttp.send();
}

function myFunction(xml, i) {
  var xmlDoc = xml.responseXML;
  x = xmlDoc.getElementsByTagName("CD");
  document.getElementById("showCD").innerHTML =
  "Artist: " +
  x[i].getElementsByTagName("ARTIST")[0].childNodes[0].nodeValue +
  "<br>Title: " +
  x[i].getElementsByTagName("TITLE")[0].childNodes[0].nodeValue +
  "<br>Year: " +
  x[i].getElementsByTagName("YEAR")[0].childNodes[0].nodeValue;
}
```

<span class="fs-2">
[W3C Example](https://www.w3schools.com/js/tryit.asp?filename=tryjs_ajax_app_first){: .btn  .btn-outline .mt-2}
</span>

#### Navigate Between the CDs

```js
function next() {
  // display the next CD, unless you are on the last CD
  if (i < len-1) {
    i++;
    displayCD(i);
  }
}

function previous() {
  // display the previous CD, unless you are on the first CD
  if (i > 0) {
    i--;
    displayCD(i);
  }
}
```

<span class="fs-2">
[W3C Example](https://www.w3schools.com/js/tryit.asp?filename=tryjs_ajax_app_navigate){: .btn  .btn-outline .mt-2}
</span>

#### Show Album Information When Clicking On a CD

```js
function displayCD(i) {
  document.getElementById("showCD").innerHTML =
  "Artist: " +
  x[i].getElementsByTagName("ARTIST")[0].childNodes[0].nodeValue +
  "<br>Title: " +
  x[i].getElementsByTagName("TITLE")[0].childNodes[0].nodeValue +
  "<br>Year: " +
  x[i].getElementsByTagName("YEAR")[0].childNodes[0].nodeValue;
}
```

<span class="fs-2">
[W3C Example](https://www.w3schools.com/js/tryit.asp?filename=tryjs_ajax_app){: .btn  .btn-outline .mt-2}
</span>

---

## PHP

### PHP Example

```html
<body>

<p><b>Start typing a name in the input field below:</b></p>

<p>Suggestions: <span id="txtHint"></span></p>

<form>
First name: <input type="text" onkeyup="showHint(this.value)">              <!-- 1. onkeyup이벤트 에 의해 트리거-->
</form>

<script>
function showHint(str) {                                                    // 2. 사용자가 입력 필드에 문자를 입력하면 호출 된 함수 showHint()가 실행, str 변수는 입력 필드의 내용을 보유
  if (str.length == 0) {                                                    // 3. 입력 필드가 비어있으면
    document.getElementById("txtHint").innerHTML = "";                      // 4. txtHint 자리 표시 자의 내용을 지우고 함수를 종료
    return;
  } else {                                                                  // 3. 입력 필드가 비어 있지 않으면
    var xmlhttp = new XMLHttpRequest();                                     // 4. XMLHttpRequest 객체 생성
    xmlhttp.onreadystatechange = function() {                               // 5. 서버 응답이 준비 될 때 실행될 함수를 작성
      if (this.readyState == 4 && this.status == 200) {                     
        document.getElementById("txtHint").innerHTML = this.responseText;   // 6. 문자열로 response 데이터를 리턴
      }
    };
    xmlhttp.open("GET", "gethint.php?q=" + str, true);                      // 7. 서버의 PHP 파일 (gethint.php)로 요청, q 매개 변수가 추가
    xmlhttp.send();
  }
}
</script>

</body>
```

PHP 파일
{: .label .label-purple .mt-3}
```php
<?php
// Array with names
$a[] = "Anna";
$a[] = "Brittany";
$a[] = "Cinderella";
$a[] = "Diana";
$a[] = "Eva";
$a[] = "Fiona";
$a[] = "Gunda";
$a[] = "Hege";
$a[] = "Inga";
$a[] = "Johanna";
$a[] = "Kitty";
$a[] = "Linda";
$a[] = "Nina";
$a[] = "Ophelia";
$a[] = "Petunia";
$a[] = "Amanda";
$a[] = "Raquel";
$a[] = "Cindy";
$a[] = "Doris";
$a[] = "Eve";
$a[] = "Evita";
$a[] = "Sunniva";
$a[] = "Tove";
$a[] = "Unni";
$a[] = "Violet";
$a[] = "Liza";
$a[] = "Elizabeth";
$a[] = "Ellen";
$a[] = "Wenche";
$a[] = "Vicky";

// get the q parameter from URL
$q = $_REQUEST["q"];

$hint = "";

// lookup all hints from array if $q is different from ""
if ($q !== "") {
  $q = strtolower($q);
  $len=strlen($q);
  foreach($a as $name) {
    if (stristr($q, substr($name, 0, $len))) {
      if ($hint === "") {
        $hint = $name;
      } else {
        $hint .= ", $name";
      }
    }
  }
}

// Output "no suggestion" if no hint was found or output correct values
echo $hint === "" ? "no suggestion" : $hint;
?>
```

이름 배열을 확인하고 해당 이름을 브라우저에 반환

---

## ASP 

### ASP Example

**더 많은 대화식 응용 프로그램을 만드는 데 사용**

PHP 파일과 비슷한 방식으로 돌아감

```html
<html>
<head>
<script>
function showHint(str) {
  if (str.length == 0) {
    document.getElementById("txtHint").innerHTML = "";
    return;
  } else {
    var xmlhttp = new XMLHttpRequest();
    xmlhttp.onreadystatechange = function() {
      if (this.readyState == 4 && this.status == 200) {
        document.getElementById("txtHint").innerHTML = this.responseText;
      }
    };
    xmlhttp.open("GET", "gethint.asp?q=" + str, true);
    xmlhttp.send();
  }
}
</script>
</head>
<body>

<p><b>Start typing a name in the input field below:</b></p>
<form>
First name: <input type="text" onkeyup="showHint(this.value)">
</form>
<p>Suggestions: <span id="txtHint"></span></p>
</body>
</html>
```

ASP 파일
{: .label .label-purple .mt-3}
```asp
<%
response.expires=-1
dim a(30)
'Fill up array with names
a(1)="Anna"
a(2)="Brittany"
a(3)="Cinderella"
a(4)="Diana"
a(5)="Eva"
a(6)="Fiona"
a(7)="Gunda"
a(8)="Hege"
a(9)="Inga"
a(10)="Johanna"
a(11)="Kitty"
a(12)="Linda"
a(13)="Nina"
a(14)="Ophelia"
a(15)="Petunia"
a(16)="Amanda"
a(17)="Raquel"
a(18)="Cindy"
a(19)="Doris"
a(20)="Eve"
a(21)="Evita"
a(22)="Sunniva"
a(23)="Tove"
a(24)="Unni"
a(25)="Violet"
a(26)="Liza"
a(27)="Elizabeth"
a(28)="Ellen"
a(29)="Wenche"
a(30)="Vicky"

'get the q parameter from URL
q=ucase(request.querystring("q"))

'lookup all hints from array if length of q>0
if len(q)>0 then
  hint=""
  for i=1 to 30
    if q=ucase(mid(a(i),1,len(q))) then
      if hint="" then
        hint=a(i)
      else
        hint=hint & " , " & a(i)
      end if
    end if
  next
end if

'Output "no suggestion" if no hint were found
'or output the correct values
if hint="" then
  response.write("no suggestion")
else
  response.write(hint)
end if
%>
```

이름의 배열을 확인하고 해당 이름을 브라우저에 반환

---

## Database

### Database Example

AJAX는 데이터베이스와의 대화식 통신에 사용될 수 있음

```js
function showCustomer(str) {
  var xhttp;
  if (str == "") {                                          // 고객이 선택되었는지 확인
    document.getElementById("txtHint").innerHTML = "";
    return;
  }
  xhttp = new XMLHttpRequest();                             // XMLHttpRequest 객체 생성
  xhttp.onreadystatechange = function() {                   // 서버 응답이 준비 될 때 실행될 함수를 작성
    if (this.readyState == 4 && this.status == 200) {
    document.getElementById("txtHint").innerHTML = this.responseText;
    }
  };
  xhttp.open("GET", "getcustomer.php?q="+str, true);       // 서버의 파일로 요청, 드롭 다운 목록의 내용과 함께 매개 변수 (q)가 URL에 추가
  xhttp.send();
}
```

php 파일
{: .label .label-purple .mt-3}
```php
<?php
$mysqli = new mysqli("servername", "username", "password", "dbname");
if($mysqli->connect_error) {
  exit('Could not connect');
}

$sql = "SELECT customerid, companyname, contactname, address, city, postalcode, country
FROM customers WHERE customerid = ?";

$stmt = $mysqli->prepare($sql);
$stmt->bind_param("s", $_GET['q']);
$stmt->execute();
$stmt->store_result();
$stmt->bind_result($cid, $cname, $name, $adr, $city, $pcode, $country);
$stmt->fetch();
$stmt->close();

echo "<table>";
echo "<tr>";
echo "<th>CustomerID</th>";
echo "<td>" . $cid . "</td>";
echo "<th>CompanyName</th>";
echo "<td>" . $cname . "</td>";
echo "<th>ContactName</th>";
echo "<td>" . $name . "</td>";
echo "<th>Address</th>";
echo "<td>" . $adr . "</td>";
echo "<th>City</th>";
echo "<td>" . $city . "</td>";
echo "<th>PostalCode</th>";
echo "<td>" . $pcode . "</td>";
echo "<th>Country</th>";
echo "<td>" . $country . "</td>";
echo "</tr>";
echo "</table>";
?>
```

소스 코드는 데이터베이스에 대해 쿼리를 실행하고 결과를 HTML 테이블에 반환