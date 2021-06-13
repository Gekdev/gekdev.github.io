---
layout: default
title: Modifier
parent: Java
nav_order: 9
---

# Java Modifier
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Modifier

**제어자, 클래스와 클래스 멤버의 선언 시 사용하여 부가적인 의미를 부여하는 키워드**

&#9656; 접근 제어자(access modifier)와 기타 제어자로 구분

&#9656; 접근 제어자는 여러개 사용 불가능, 기타제어자는 두개 이상 사용가능

&#9656; 접근 제어자와 기타 제어자는 조합에 따라 함께 사용가능

&#9656; 클래스나 멤버를 선언할 때, 접근을 허용할 범위에 맞는 접근 제어자를 선택하는 것이 매우 중요

---

## Access Modifier

정보 은닉(data hiding): 사용자가 굳이 알 필요가 없는 정보는 사용자로부터 숨겨야 한다는 개념

&#8594; 사용자는 언제나 최소한의 정보만으로 프로그램을 손쉽게 사용

**이러한 정보 은닉을 위해 접근제어자라는 기능을 제공**

클래스 외부에서의 직접적인 접근을 허용하지 않는 멤버를 설정하여 정보 은닉을 구체화

1. private

2. public

3. default

4. protected

### Private

외부에 공개되지 않으며, 외부에서는 직접 접근할 수 없음 즉,

**같은 패키지의 같은 클래스 안에서만 사용가능**

* 필드

     private 멤버에 직접 접근할 수 없으며, 해당 객체의 public 메소드를 통해서만 접근
    
     public 인터페이스를 직접 구성하지 않고, 클래스 내부의 세부적인 동작을 구현

* 메소드 

![](https://gekdev.github.io/docs/java/class/example/img_java_access_private.png)

예제
{: .label .label-purple .mt-2}
```java
public class SameClass {
    private String var = "같은 클래스만 허용"; // private 필드
    private String getVar() {                  // private 메소드
        return this.var;
    }
}
```

### Public

외부로 공개되며, 해당 객체를 사용하는 프로그램 어디에서나 직접 접근 즉,

**다른 패키지의 다른 클래스도 사용가능**

public 메소드를 통해서만 해당 객체의 private 멤버에 접근가능

&#8594; public 메소드는 private 멤버와 프로그램 사이의 인터페이스(interface) 역할을 수행

* 클래스 : 다른패키지에서 클래스 접근가능

* 필드, 메소드 : 다른 패키지의 다른 클래스도 사용가능, 다른패키지라서 임포트해야함 

![](https://gekdev.github.io/docs/java/class/example/img_java_access_public.png)

예제
{: .label .label-purple .mt-2}
```java
public class Everywhere {
    public String var = "누구든지 허용"; // public 필드
    public String getVar() {             // public 메소드
        return this.var;
    }
}
```

### Default

**접근제어의 기본값**

default를 위한 접근 제어자는 따로 존재하지 않음 = 접근 제어자가 지정되지 않으면 자동적으로 default 접근 제어자를 가짐

default 접근 제어를 가지는 멤버는 같은 클래스의 멤버와 같은 패키지에 속하는 멤버에서만 접근 즉, 

**같은 패키지의 다른 클래스까지 사용가능**

![](https://gekdev.github.io/docs/java/class/example/img_java_access_default.png)

예제
{: .label .label-purple .mt-2}
```java
package test;

public class SamePackage {
    String sameVar = "같은 패키지는 허용"; // default 필드
}
```

### Protected

**부모 클래스에 대해서는 public 멤버처럼 취급, 외부에서는 private 멤버처럼 취급**

&#9656; 클래스의 protected 멤버에 접근할 수 있는 영역

1. 이 멤버를 선언한 클래스의 멤버

2. 이 멤버를 선언한 클래스가 속한 패키지의 멤버

3. 이 멤버를 선언한 클래스를 상속받은 자식 클래스(child class)의 멤버

![](https://gekdev.github.io/docs/java/class/example/img_java_access_protected.png)

예제
{: .label .label-purple .mt-2}
```java
package test;

public class SameClass {
    protected String sameVar = "다른 패키지에 속하는 자식 클래스까지 허용"; // protected 필드
}

...
package test.other;
import test.SameClass; // test 패키지의 SameClass 클래스를 불러들여 포함시킴.

public class ChildClass extends SameClass {
    public static void main(String[] args) {
        SameClass = new SameClass();
        System.out.println(sp.sameVar); // 다른 패키지에 속하는 자식 클래스까지 허용
    }
}
```

### Access Modifier Range

접근 제어자의 접근 범위가 보다 많은 제어자부터 적은 제어자 순으로 나열

**public > protected > default > private**

|접근 제어자	|같은 클래스의 멤버|	같은 패키지의 멤버|	자식 클래스의 멤버|	그 외의 영역|
|:---|:---|:----|:-----|:-----|
|public	    |○	|○	|○	|○|
|protected	|○	|○	|○	|X|
|default	|○	|○	|X	|X|
|private	|○	|X	|X	|X|

---

## Other Modifier

### Final Modifier

**final 제어자는 '변경할 수 없다'는 의미로 사용**

&#9656; final필드는 초기값이 저장되면 최종값이 되어 더이상 수정할 수 없음
 
* final 제어자를 사용할 수 있는 대상 - 클래스, 메소드, 필드, 지역 변수

    1) 필드, 지역 변수 : 값을 변경할 수 없는 상수(constant)가 됨

    2) 클래스 : 해당 클래스는 다른 클래스가 상속받을 수 없음

    3) 메소드에 사용 : 오버라이딩(overriding)을 통한 재정의를 할 수 없음

    !overriding
    {: .label .label-yellow .mt-2}
    <div class="code-example" markdown="1">
    자바에서는 상속이라는 것을 통해 다른 클래스의 private 멤버를 제외한 모든 메소드를 상속받을 수 있음

    이렇게 상속받은 메소드는 그대로 사용해도 되고, 필요한 동작을 위해 재정의하여 사용할 수도 있음

    메소드 오버라이딩(method overriding)이란 상속받은 부모 클래스의 메소드를 재정의하여 사용하는 것을 의미
    </div>
    
    예제
    {: .label .label-purple .mt-2}
    ```java
    final class Car {                    // 이 클래스는 상속을 통해 서브 클래스를 생성할 수 없음.
        final int VAR;                   // 이 필드는 상수화되어 값을 변경할 수 없음.
        final void brake() {             // 이 메소드는 오버라이딩을 통해 재정의할 수 없음.
            final double MAX_NUM = 10.2; // 이 지역 변수는 상수화되어 값을 변경할 수 없음.
        }
    }
    ```

* final 필드의 초기값을 주는 방법

    1) 필드 선선시 초기값을 부여하는 방법

    2) 생성자를 통해서 부여하는 방법

    단순값이라면 필드선언시에 부여하는 것이 제일 간단하지만 복잡한 초기화 코드가 필요하거나 객체 생성시에 외부데이터로서 초기화해야 한다면 생성자에서 객체가 생성될 때 초기값을 부여할 수 있다

    생성자는 final 필드를 초기화해야 하는 만약 초기화 되지 않은 final필드가 있을 경우에는 컴파일(문법)에러가 발생된다
    
### Static Modifier

**static 제어자는 '공통적인'이라는 의미로 사용**

&#9656; static 제어자를 변수에 사용하면 해당 변수를 클래스 변수로 만들어주고, 메소드에 사용하면 해당 메소드를 클래스 메소드로 만들어 줌

&#9656; 초기화 블록에도 사용할 수 있음

&#9656; static 제어자를 사용할 수 있는 대상 - 메소드, 필드, 초기화 블록

&#9656; static 제어자 특징

1. 프로그램 시작시 최초에 단 한 번만 생성되고 초기화됩니다.

2. 인스턴스를 생성하지 않고도 바로 사용할 수 있게 됩니다.

3. 해당 클래스의 모든 인스턴스가 공유합니다.

예제
{: .label .label-purple .mt-2}
```java
class Car {
    static int var;       // 클래스 필드(static 변수)
    static {              // static 초기화 블록
    // 보통 클래스 필드의 초기화를 진행함.
    {
    static void brake() { // 클래스 메소드(static 메소드)
         ...
    }
}
```

#### Static Field Initalize

두가지 방법이 있음 

1. 선언할 때 초기화

2. static block으로 초기화

    static블럭은 여러개 정의할 수 있음

    이 블럭의 실행순서는 먼저 정의된 블럭을 순차적으로 실행함

예제
{: .label .label-purple .mt-2}
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

### Abstract Modifier

**abstract 제어자는 '추상적인'이라는 의미로 사용**

&#9656; 선언부만 있고 구현부가 없는 메소드를 추상 메소드라 하며, 반드시 abstract 제어자를 붙여야 함

&#9656; **하나 이상의 추상 메소드가 포함하고 있는 추상 클래스도 반드시 abstract 제어자를 붙여야 함**

&#9656; abstract 제어자를 사용할 수 있는 대상 - 클래스, 메소드

예제
{: .label .label-purple .mt-2}
```java
abstract class Car {       // 추상 클래스
    abstract void brake(); // 추상 메소드
}
```

---

## Modifer Combination 

접근 제어자와 기타 제어자를 한 대상에 함께 사용할 수 있음, 조합표는 아래와 같음

|대상	|함께 사용할 수 있는 제어자|
|:---|:----------------------|
|클래스|	public, (default), final, abstract|
|메소드|	모든 접근 제어자, final, static, abstract|
|필드	|모든 접근 제어자, final, static|
|지역 변수	|final|
|초기화 블록	|static|

### Static Final Field

일반적으로 불변의 값을 상수라고 함. 불변의 값은 수학에서 자주 사용되는 원주율 Pi값 또는
지구의 무게, 지구의 둘레 등이 해당

이런 불변의 값을 저장하는 필드를 자바에서는 상수(Constant)라고 함

final필드는 한번초기화가 되면 수정할 수 없는 필드이지만 상수라고 부르진 않음.

왜나하면 불변의 값은 객체마다 저장할 필요가 없는 공통으로 사용되는 값으로서 
여러가지 값으로 초기화 될 수없기 때문

final필드는 객체마다 저장되고 생성자의 매개값을 통해서 여러가지 값을 가질 수 있기 때문에
상수가 될 수 없음

**그래서 상수는 final이면서 static이어야 함**

static final 필드는 객체마다 저장되지 않고 클래스에만 포함됨

그리고 한번 초기화가되면 변경될 수 없음

### Combination Features

1. 클래스에 final과 abstract는 함께 사용할 수 없음

    final 제어자를 가지는 클래스는 다른 클래스가 상속받을 수 없게 되며, abstract 제어자를 가지는 클래스는 다른 클래스가 상속해서 오버라이딩해야만 사용할 수 있으므로, 이 두 제어자는 클래스에 함께 사용할 수 없음

2. 메소드에 static과 abstract는 함께 사용할 수 없음

    abstract 제어자를 가지는 메소드는 선언부만 있고 구현부가 없는 메소드인데, static 제어자를 가지는 메소드는 인스턴스를 생성하지 않고도 바로 사용할 수 있어야 하므로, 이 두 제어자는 메소드에 함께 사용할 수 없음

3. 메소드에 private과 abstract는 함께 사용할 수 없음

    abstract 제어자를 가지는 메소드는 다른 클래스가 상속하여 오버라이딩해야만 사용할 수 있는데, private 제어자를 가지는 메소드는 자식 클래스에서 접근할 수 없게 되므로, 이 두 제어자는 메소드에 함께 사용할 수 없음

4. 메소드에 private과 final은 함께 사용할 필요가 없음

    메소드에 사용된 final 제어자와 private 제어자는 모두 해당 메소드가 오버라이딩을 통한 재정의를 할 수 없다는 의미를 가지므로, 둘 중에 하나만 사용해도 의미가 충분히 전달될 수 있음
 