---
layout: default
title: Singleton
parent: Class
grand_parent: Java
nav_order: 5
---

# Class Singleton
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

### Public class

다른패키지에서 클래스 접근가능

### Public field

다른 패키지의 다른클래스 사용가능, 다른패키지라서 임포트해야함  

### Default field / method

같은 패키지의 다른 클래스까지 사용가능


### Private field / method

같은 패키지의 같은 클래스 안에서만 사용가능 


### final field

final필드는 초기값이 저장되면 최종값이 되어 더이상 수정할 수 없음
	
필드의 초기값을 주는 방법

1) 필드 선선시 초기값을 부여하는 방법

2) 생성자를 통해서 부여하는 방법

단순값이라면 필드선언시에 부여하는 것이 제일 간단하지만

복잡한 초기화 코드가 필요하거나 객체 생성시에 외부데이터로서 초기화해야 한다면 생성자에서 객체가 생성될 때 초기값을 부여할 수 있다

생성자는 final 필드를 초기화해야 하는 만약 초기화 되지 않은 final필드가 있을 경우에는 컴파일(문법)에러가 발생된다

### static final field

일반적으로 불변의 값을 상수라고 함. 불변의 값은 수학에서 자주 사용되는 원주율 Pi값 또는
지구의 무게, 지구의 둘레 등이 해당

이런 불변의 값을 저장하는 필드를 자바에서는 상수(Constant)라고 함

final필드는 한번초기화가 되면 수정할 수 없는 필드이지만 상수라고 부르진 않음.

왜나하면 불변의 값은 객체마다 저장할 필요가 없는 공통으로 사용되는 값으로서 
여러가지 값으로 초기화 될 수없기 때문

final필드는 객체마다 저장되고 생성자의 매개값을 통해서 여러가지 값을 가질 수 있기 때문에
상수가 될 수 없음

그래서 상수는 final이면서 static이어야 함. 

static final 필드는 객체마다 저장되지 않고 클래스에만 포함됨

그리고 한번 초기화가되면 변경될 수 없음

 
### Static 변수 초기화하기

static block으로 초기화

static블럭은 여러개 정의할 수 있음

이 블럭의 실행순서는 먼저 정의된 블럭을 순차적으로 실행함

```java
public class Earth {
	
	static final double EARTH_RADIUS = 6400;
	//static final double EARTH_SURFACE_AREA = 4* Math.PI+ EARTH_RADIUS * EARTH_RADIUS;
	static final double EARTH_SURFACE_AREA;
	
	//static block
	static {
		EARTH_SURFACE_AREA = 4* Math.PI+ EARTH_RADIUS * EARTH_RADIUS;
	}
	static {
		// static블럭은 여러개 정의할 수 있음
		// 이 블럭의 실행순서는 먼저 정의된 블럭을 순차적으로 실행함 
	}
	
}
```