---
layout: default
title: Type Conversion
parent: Data types
grand_parent: JavaScript
nav_order: 3
---
 
# Type Conversion
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Type Conversion

**JavaScript 변수는 새 변수 및 다른 데이터 유형으로 변환 할 수 있음**

* JavaScript function을 사용

* JavaScript 자체에 의해 자동으로

### Numbers to Strings

[String()](https://gekdev.github.io/docs/javascript/array/methods/#tostring)

### Booleans to Strings

### Dates to Strings

### Strings to Numbers

### The Unary + Operator

### Booleans to Numbers

### Dates to Numbers

### Automatic Type Conversion

### Automatic String Conversion

### JavaScript Type Conversion Table

| Original Value 	| Converted to Number | Converted to String	| Converted to Boolean |
|:------------------|:--------------------|:--------------------|:---------------------|
| false	            | 0                   | "false"	            | false                |	
| true	            | 1                   |	"true" 	            | true	               |
| 0	                | 0                   |	"0"		            | false                |	
| 1	                | 1                   |	"1"		            | true	               |	
| "0"	            | 0                   |	"0"		            | true	               |	
| "000"	            | 0                   |	"000"		        | true	               |	
| "1"	            | 1                   |	"1"		            | true	               |	
| NaN	            | NaN	              | "NaN"		        | false                |	
| Infinity	        | Infinity            |	"Infinity"		    | true	               |	
| -Infinity	        | -Infinity	          | "-Infinity"		    | true	               |	
| ""	            | 0                   |	""		            | false                |	
| "20"	            | 20                  |	"20"		        | true	               |	
| "twenty"	        | NaN	              |	"twenty"		    | true	               |	
| [ ]	            | 0	                  | ""		            | true	               |	
| [20]	            | 20	              | "20"		        | true	               |	
| [10,20]	        | NaN	              | "10,20"		        | true	               |	
| ["twenty"]	    | NaN	              | "twenty"		    | true	               |	
| ["ten","twenty"]	| NaN	              | "ten,twenty"		| true	               |	
| function(){}	    | NaN	              | "function(){}"		| true	               |	
| { }	            | NaN	              | "[object Object]"	| true	               |	
| null	            | 0	                  | "null"		        | false                |	
| undefined	        | NaN	              | "undefined"		    | false                |

