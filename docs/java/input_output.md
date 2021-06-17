---
layout: default
title: Input and Output
parent: Java
nav_order: 16
has_children: true
---

# Java Input and Output
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Input and Output
{: .no_toc}
 
### Stream

**스트림(stream) : 실제의 입력이나 출력이 표현된 데이터의 이상화된 흐름**

자바에서는 파일이나 콘솔의 입출력을 직접 다루지 않고, 스트림(stream)이라는 흐름을 통해 다룸

운영체제에 의해 생성되는 가상의 연결 고리를 의미 (중간 매개자 역할)

![](img_c_stream.png)

!Note
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
Stream API와는 다른개념
</div>

### 

입출력 스트림

스트림은 한 방향으로만 통신할 수 있으므로, 입력과 출력을 동시에 처리할 수는 없기 때문에 사용 목적에 따라 입력 스트림과 출력 스트림으로 구분됩니다. 

java.io 패키지를 통해 InputStream과 OutputStream 클래스를 제공하고 있음

즉, 자바에서의 스트림 생성이란 이러한 스트림 클래스 타입의 인스턴스를 생성한다는 의미


InputStream 클래스에는 read() 메소드가, OutputStream 클래스에는 write() 메소드가 각각 추상 메소드로 포함되어 있습니다.

사용자는 이 두 메소드를 상황에 맞게 적절히 구현해야만 입출력 스트림을 생성하여 사용할 수 있습니다.

