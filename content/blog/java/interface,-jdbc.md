---
title: interface, JDBC
date: 2020-08-09 01:08:56
category: java
draft: false
---

## 인터페이스(규약)와 JDBC의 관계

JAVA 에서 인터페이스를 제공하고, 벤더들은 그 인터페이스를 구현하는 클래스들을 만든다.

벤더들이 구현한 클래스들을 Driver class 라고 부른다.

각 벤더들의 데이터베이스를 연동하려면 JDBC Driver가 필요하다

개발자들은 벤더들의 구현 클래스가 어떻게 구현돼있는지 알지 못하더라도 인터페이스를 통해서 기능을 동작시킬 수 있다. (구현 내용을 알 필요가 없다)


## 인터페이스의 상속 관계

```java
// 인터페이스가 인터페이스를 상속 - extends
public interface A {
    public void m();
}

public interface B extends A {
    public void n();
}
```

다중 상속 관계에 있는 클래스 구조
```java
// Animal은 abstract class, Pet과 Robots은 interface
public class Dog extends Animal implements Pet, Robots {

}
```