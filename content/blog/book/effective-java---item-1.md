---
title: Effective Java - Item 1
date: 2021-11-10 14:11:80
category: book
draft: false
---

## 생성자 대신 정적 팩터리 메서드를 고려하라

### 정적 팩터리 메서드가 생성자보다 좋은 장점 다섯 가지

1. 이름을 가질 수 있다.

- 생성자에 넘기는 매개변수와 생성자 자체만으로는 반환될 객체의 특성을 제대로 설명하지 못한다.
- 정적 팩터리 메서드는 이름만 잘 지으면 반환될 객체의 특성을 쉽게 묘사할 수 있다.

한 클래스에 시그니처가 같은 생성자가 여러 개 필요할 것 같으면, 생성자를 정적 팩터리 메서드로 바꾸고 각각의 차이를 잘 드러내는 이름을 지어주자.

2. 호출될 때마다 인스턴스를 새로 생성하지는 않아도 된다.

- 불변 클래스는 인스턴스를 미리 만들어 놓거나 새로 생성한 인스턴스를 캐싱하여 재활용하는 식으로 불필요한 객체 생성을 아예 생성하지 않는다.
- 같은 객체가 자주 요청되는 상황이라면 성능을 상당히 끌어올려 준다. - 플라이웨이트 패턴


3. 반환 타입의 하위 타입 객체를 반환할 수 있는 능력이 있다.

- 반환할 객체의 클래스를 자유롭게 선택할 수 있게 하는 `엄청난 유연성`을 선물한다.
- API를 만들 때 이 유연성을 응용하면 구현 클래스를 공개하지 않고도 그 객체를 반환할 수 있어 API를 작게 유지할 수 있다.


4. 입력 매개변수에 따라 매번 다른 클래스의 객체를 반환할 수 있다.

- 반환 타입의 하위 타입이기만 하면 어떤 클래스의 객체를 반환하든 상관없다.


5. 정적 팩터리 메서드를 작성하는 시점에는 반환할 객체의 클래스가 존재하지 않아도 된다.

- 이런 유연함은 서비스 제공자 프레임워크(service provider framework)를 만드는 근간이 된다.
  > 대표적인 서비스 제공자 프레임워크로는 JDBC가 있다.
  - 서비스 제공자 프레임워크의 3개 핵심 컴포넌트
  - 서비스의 동작을 정의하는 서비스 인터페이스
  - 제공자가 구현체를 등록할 때 사용하는 서비스 인터페이스
  - 클라이언트가 서비스의 인스턴스를 얻을 때 사용하는 서비스 접근 API


### 단점

1. 상속을 하려면 public이나 protected 생성자가 필요하니 정적 팩터리 메서드만 제공하면 하위 클래스를 만들 수 없다.

- 이 제약은 상속보다 컴포지션을 사용하도록 유도하고 불변 타입으로 만들려면 이 제약을 지켜야 한다는 점에서 오히려 장점으로 받아들일 수도 있다.

2. 정적 팩터리 메서드는 프로그래머가 찾기 어렵다.

- 생성자처럼 API 설명에 명확히 드러나지 않으니 사용자는 정적 팩터리 메서드 방식 클래스를 인스턴스화할 방법을 알아내야 한다.


### 정적 팩터리 메서드에 흔히 사용하는 명명 방식들

- `from` : 매개변수를 하나 받아서 해당 타입의 인스턴스를 반환하는 형변환 메서드
- `of` : 여러 매개변수를 받아 적합한 타입의 인스턴스를 반환하는 집계 메서드
- `valueOf` : from과 of의 더 자세한 버전
- `instance` 혹은 `getInstance` : (매개변수를 받는다면) 매개변수로 명시한 인스턴스를 반환하지만, 같은 인스턴스임을 보장하지는 않는다.
- `create` 혹은 `newInstance` : `instance` 혹은 `getInstance`와 같지만, 매번 새로운 인스턴스를 생성해 반환함을 보장한다.
- `getType` : `getInstance`와 같으나, 생성할 클래스가 아닌 다른 클래스에 팩터리 메서드를 정의할 때 쓴다.
- `newType` : `newInstance`와 같으나, 생성할 클래스가 아닌 다른 클래스에 팩터리 메서드를 정의할 때 쓴다.
- `type` : `getType`과 `newType`의 간결한 버전