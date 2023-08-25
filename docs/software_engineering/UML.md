---
layout: default
title: UML
nav_order: 6
parent: Software Engineering
---



## 📑 UML

- 표준 모델링 언어
- 개발 규모, 개발 프로세스, 개발 언어에 관계 없이 적용
- 정적 모델 : 시스템의 구조
  - 클래스 다이어그램 : 클래스의 관계 나타냄
  - 객체 다이어그램 : 객체의 정적 구조 나타냄
  - 컴포지트 다이어그램 : 컴포넌트의 합성구조와 커넥션
  - 컴포넌트 다이어그램 : 코드 구조 
  - 패키지 다이어그램 : 패키지로 선언한 모듈의 구조
  - 배치 다이어그램 : 소프트웨어와 하드웨어 배치 나타냄

- 동적 모델 : 시스템의 내부 동작
  - 시퀀스 다이어그램 : 객체들 간의 `메시지 교환`을 시각화
  - 커뮤니케이션 다이어그램 : 객체의 메시지 호출을 네트워크 형태로 표현
  - 타이밍 다이어그램 : 시간의 흐름에 따른 구성 요소의 상호작용과 상태 변화
  - 상태 다이어그램 : 여러 유즈케이스들 사이의 한 객체가 수행하는 기능 나타냄

- 기능 모델 : 사용자 측면에서 본 시스템의 기능
  - 유즈케이스 다이어그램 : 사용사례와 액터로 구성




## 📑 관계

### ⭐ 연관 관계

- 연관 관계 : 방향성 없는 실선, 상호 연관
- 직접 연관 관계 : 방향성 있는 실선
  - A -> B : A만 B를 인지

- 집합 연관 관계 : part ----- 빈 마름모 whole -> 전체 소멸해도 part 사용 가능
- 합성 연관 관계 : part ----- 꽉 찬 마름모 whole -> 전체 소멸하면 part도 소멸

### ⭐ 의존관계

- 점선 화살표
- 한쪽 사물의 변화가 다른 사물에 영향을 줄 수 있음 표기

### ⭐ 일반화 관계

- 부모 클래스와 자식 클래스의 관계
- 실선 + 빈 삼각형 화살표
  - A -> B : A는 B의 특성을 상속하였다


### ⭐ 실체화 관계

- 인터페이스와 구현 클래스의 관계
- 점선 + 빈 삼각형 화살표
  - A -> B : A는 B를 실현 했다




## 📑 클래스 다이어그램

### ⭐ 연관 관계, 의존관계

- 어떤 클래스가 다른클래스를 참조

```java
//연관관계 : 어떤 클래스가 다른클래스 참조를 가지는 필드
class User {
	List<Address> list;
}

//의존관계 : 다른 클래스의 객체 참조
class User {
    //다른 객체 생성 및 리턴
    public Order createOrder() {
        return new Order();
    }
    //다른 객체를 매개변수로 받아 사용
    public void useOrder(Order order) {
        Order myOrder = order.getOrder();
    }
}
```

### ⭐ 집합 관계

- 전체에 빈 다이아몬드 붙임
- 부분이 소멸되어도 전체는 남아있음
- 구성 요소는 하나 이상의 전체 집합에 소속될 수 있음

### ⭐ 복합 관계

- 전체에 꽉 찬 다이아몬드 붙임
- 부분이 소멸되면 전체도 소멸 됨

### ⭐ 일반화 관계

- 실선 + 부모에 삼각형 화살표가 붙음
- 상위로 올라갈 수록 일반화 관계, 아래로 내려갈 수록 특수화 또는 구체화

### ⭐ 실체화 관계

- 점선 + 빈 삼각형
- `<<interface>>` 의 메서드 구현
