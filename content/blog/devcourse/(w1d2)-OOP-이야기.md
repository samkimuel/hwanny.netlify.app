---
title: (W1D2) OOP 이야기
date: 2021-08-04 11:08:57
category: devcourse
draft: false
---

## 객체지향 프로그래밍

- 프로그램을 객체로 구성하는 것
- 프로그램이 거대화하면서 등장

'어떻게 큰 프로그램을 만들 것인가? 어떻게 만드는 것이 효율적이고 관리하기 좋은 것인가?' -> 작게 나눠서 만들고 합친다.

- 개념적인 용어 : `객체` / 기술적인 용어 : `class`, `instance`
  - `class` : 어떤 문제를 해결하기 위한 데이터를 만들기 위해 추상화를 거쳐 집단에 속하는 속성과 행위를 변수와 메서드로 정의한 것
  - `instance` : 클래스에서 정의한 것을 토대로 실제 메모리상에 할당된 것



## 객체지향의 특성

### 1. 캡슐화

- 하나의 객체에 대해 그 객체가 특정한 목적을 위한 필요한 변수나 메소드를 하나로 묶는 것을 의미한다.
- 목적 : 외부의 잘못된 사용으로 인해 객체가 손상되지 않도록 하기 위함
- 기능을 수행하는 단위로써 완전함을 갖는다.
- 정보가 은닉되어 있다.
- 객체의 정보가 밖에서 접근하거나, 밖에서 객체 내의 정보에 접근하지 못하게 한다.
  - 외부 객체는 객체 내부의 구조를 알지 못하며 객체가 노출해서 제공하는 필드와 메소드만 이용 가능

| 접근지정자 | 접근 범위                        |
| ---------- | -------------------------------- |
| private    | 해당 클래스 내                   |
| protected  | 동일 패키지 내, 상속 받은 클래스 |
| (friendly) | 동일 패키지 내 (패키지 가시성)   |
| public     | 접근 제한 없음                   |

### 2. 상속

- 객체의 특성을 그대로 물려받는 또 다른 객체를 만드는 것을 의미한다.
- 목적 : 연관된 일련의 클래스에 대한 공통적인 규약을 정의하고 적용하기 위함
- 상위, 부모, super, [추상] | 하위, 자식, (this), [구체]
  - 상위클래스로 갈수록 더 추상화되고 일반화된다.
  - 하위클래스로 갈수록 더 구체화되고 특수화된다.
- 공통된 기능을 여러 객체에게 전달하고 싶을 때가 아닌, 추상과 구체 관계에서 상속이 이루어진다.
  - 계층 X, 확장 O
- 효과 
  - 코드의 중복을 줄여준다.
  - 객체의 다형성을 구현할 수 있다.

### 3. 추상화

- 목적과 관련이 없는 부분을 제거하여 필요한 부분만을 표현하기 위한 개념이다.
- 객체의 공통적인 속성과 기능을 추출하여 정의하는 것을 말한다.
- 추상화화된 객체 `추상체` / 구체화된 객체 `구상체`

### 4. 다형성

- 하나의 객체가 여러 가지 형태를 가질 수 있음을 의미한다.
- 상속과 연관되어 있는 개념이다.
- 한 객체가 상속을 통해 기능을 확장하거나 변경하여 다른 여러 형태(객체)로 재구성 되는 것을 말한다.



## 객체지향 설계

### 1. UML

- Usecase Diagram
- Sequence Diagram
- Package Diagram
- **Class Diagram**

### 2. 객체지향 설계

- 객체지향 설계를 하는 5가지 원칙(SOLID)
  1. SRP(단일 책임 원칙)
     - 모든 클래스는 하나의 책임만 가지며, 그 책임은 완전히 **캡슐화**되어야 한다.
     - 객체를 만들면 그 객체가 가진 기능은 하나! 수정이 필요할 경우 수정되는 이유는 하나 때문이어야 한다.
     - 하나의 클래스에 다양한 기능이 들어간 경우, 해당 클래스를 수정했을 때 다른 모듈에 어떠한 영향을 미치는 지 그 범위를 추측하기 힘들 수 있다.
  2. OCP(개방 폐쇄 원칙)
     - 클래스, 모듈 함수 등의 소프트웨어 개체는 확장에 대해 열려있어야 하고, 수정에 대해서는 닫혀 있어야 한다.
     - 수정이 일어나더라도 기존의 구성요소에서는 수정이 일어나지 않아야 하며, 쉽게 확장이 가능하여 재사용을 할 수 있도록 해야한다. 
       - **추상화**와 **다형성**이 중요하다.
  3. LSP(리스코프 치환 원칙)
     - 상위 타입의 객체를 하위 타입의 객체로 치환해도 상위 타입을 사용하는 프로그램은 정상적으로 동작해야 한다.
     - 부모 클래스가 들어갈 자리에 자식 클래스를 넣어도 잘 구동되어야 한다는 원칙이다.
       - **상속**에 대한 개념
     - 제대로 준수하지 않을 경우, 클래스 계층이 지저분해질 수 있으며, 서브클래스 인스턴스를 파라미터로 전달했을 때 메서드가 이상하게 동작할 수 있다.
  4. ISP(인터페이스 분리 원칙)
     - 클라이언트에서는 클라이언트 자신이 이용하지 않는 기능에는 영향을 받지 않아야 한다.
     - 인터페이스를 클라이언트에 특화되도록 분리시키라는 설계 원칙이다.
  5. DIP(의존관계 역전 원칙)
     - 상위 모듈이 하위 모듈에 의존하는 전통적인 의존 관계를 반전시킴으로써, 상위 모듈이 하위 모듈의 구현으로부터 독립되어야 한다.
     - 상위 모듈과 하위 모듈 모두 추상화된 내용에 의존해야 한다.
       - 구체적인 클래스보다 인터페이스나 추상 클래스와 관계 맺기

- 디자인패턴 
  - 소프트웨어 개발 과정에서 발견된 설계의 노하우를 축적하여 그 방법에 이름을 붙여서 이후에 재사용하기 좋은 형태로 특정 규약을 만들어서 정리한 것이다. - `효율적인 코드를 만들기 위한 방법론`
  - 효과
    - 재사용이 가능한 설계를 가능하게 하고, 재사용을 방해하는 설계는 배제하도록 도와준다.
    - 이미 만든 시스템의 유지보수나 문서화를 개선할 수 있다.
    - 클래스의 명세를 정확하게 할 수 있고, 객체 간의 상호작용 또는 설계 의도까지 명확하게 정의할 수 있다.
