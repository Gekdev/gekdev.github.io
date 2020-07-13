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
function loadDoc() {                                                    //1. 버튼을 누르면 loadDoc()이 실행됨
  var xhttp = new XMLHttpRequest();                                     //2. XMLHttpRequest 객체 생성
  xhttp.onreadystatechange = function() {                               //
    if (this.readyState == 4 && this.status == 200) {
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
```

