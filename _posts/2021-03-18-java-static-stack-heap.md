---
title: JAVA/ Static, Stack, Heap 메모리 영역의 이해
category: java
tags:
  - java
  - memory
toc: true
toc_sticky: true
toc_label: "목차"
canonical_url: "https://roxy.iro.ooo/irostub/2021/03/18/java-static-stack-heap"
redirect_to: https://roxy.iro.ooo/irostub/2021/03/18/java-static-stack-heap
---

# JAVA 메모리 영역의 이해

JAVA에서 사용되는 대표적인 메모리는 Static, Stack, Heap 이 있다. 이 세가지의 주요한 특징과 사용되는 방식에 대해서 알아보자.

## Static

흔히 스태틱(Static) 이라고 부르는 이 메모리 영역은 글자 뜻 그대로 '정적 메모리'라는 뜻을 가지고 있다. 이는 컴파일 시간 동안 할당 된 메모리이며 고정된 공간을 차지하고 런타임 중에 변경할 수 없는 특징을 가지고 있다. 정적 메모리를 잘 사용할 경우 (Singleton 등) 메모리 사용에 있어 이점을 볼 수 있다. 단, 잘못 사용할 경우 정적 메모리는 공유되는 자원으로써 멀티 쓰레드 환경에서 치명적인 버그를 불러올 수 있기에 주의가 필요하다.

### 사용 예

```java
public class Card{
	static int number;
	static long code;
}
```

## Stack

스택(Stack) 이라고 부르는 메모리 영역은 글자 뜻 처럼 위에서 아래로 쌓아가는 방식으로 작동하는 메모리이다. LIFO(Last In First Out) 방식을 취하고 있다. LIFO는 가장 처음에 들어간 것이 먼저 나간다는 뜻이다. Stack 메모리에 데이터를 넣는 행위를 Push라 하며 데이터를 내보내는 행위를 Pop이라 한다.
기본 자료형 `int, long, boolean 등` 의 지역변수와 매개변수의 데이터값이 저장되며 추가적으로 객체 생성 시 참조 주소값도 저장된다.

### 사용 예

```java
public class Card{
	public void getZero(){
		int num = 0;
		return num;
	}
}
```

## Heap

힙(Heap) 이라고 부르는 메모리 영역은 글자 뜻은 쌓아올린 더미 라는 뜻인데, 이 자체만으론 무슨 일을 할지 잘 예상이 가지 않는다. 힙은 참조형의 데이터 객체(Object)의 실제 데이터들이 담기는 공간이다.
가령 Java에서 아래와 같은 코드를 작성한다하면,

```java
Instance instance = new Instance();
```

`new Instance();` 로 인해 만들어진 객체의 데이터는 힙에 존재하게 된다. 그럼 이 데이터를 어떻게 찾아서 쓸 수 있을까? 그 방법은 바로 객체 데이터를 참조하고 있는 주소 사용하여 찾는 것이다. 이 참조 주소는 객체를 만들 때 Stack 메모리에 생성이 된다.

### 사용 예

```java
public class Card{}
public class Main{
	public static void main(String[] args){
		Card card = new Card();
	}
}
```
