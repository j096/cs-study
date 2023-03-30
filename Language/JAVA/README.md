# JAVA

일반적인 프로그램은 윈도우 또는 리눅스와 같은 운영체제 위에서 실행된다. 하드웨어 기반으로 운영체제가 동작하고, 그 위에서 프로그램이 실행되는 구조이다.

그러나 자바 프로그램은 운영체제가 **자바 가상머신(Java Virtual Machine)**을 실행시키고, 자바 가상머신이 자바 프로그램을 실행시키는 구조로 동작한다. 이는 **자바 프로그램을 운영체제에 상관없이 실행시키기 위함**이다. 따라서 자바 프로그램은 코드 수정 없이 JVM만 바꿔주어 다양한 운영체제에서 실행시킬 수 있다.

- 자바 컴파일러

  자바 컴파일러는 자바 가상머신이 이해할 수 있는 코드를 생성해 낸다. 사용자가 작성한 'ㅁㅁㅁ.java' 을 가리켜 소스파일이라 하며, 이 소스파일을 JVM이 이해할 수 있는 '자바 바이트코드'로 변환하여 'ㅁㅁㅁ.class' 파일을 만들어 낸다.
  
  

## OOP (Object Oriented Programming) 

프로그래밍에서 필요한 데이터를 추상화 시켜 **상태와 행위를 가진 객체** 로 만들고, 이들간의 상호작용을 통해 로직을 구성하는 프로그래밍 방법이다. 객체란, 하나의 **역할** 을 수행하는 '메소드와 변수(데이터)'의 묶음을 지칭한다.

- OOP의 4가지 특징

  1. 추상화(Abstraction) : 객체들의 공통적인 속성이나 동작을 하나로 묶어 표현하는 것

  2. 상속(Inheritance) : 여러 객체들이 가진 공통적인 속성을 부각시켜 하나의 개념이나 법칙으로 성립하는 것으로, 상위 클래스의 자료와 연산을 하위 클래스가 물려받아 이용할 수 있는 특성을 말한다.

  3. 다형성(Polymorphism) : 하나의 메소드나 클래스가 다양한 방법으로 동작하는 것 (오버라이딩, 오버로딩)

  4. 캡슐화(Encapsulation) : 객체의 데이터와 메서드를 외부에서 직접 접근하지 못하도록 은닉하는 것

     

- OOP in JAVA

  추상 자료형 = class

  class를 실제로 구현한 것 = instance

  class 내의 data = member variable

  class 내의 operation(function) = method

  캡슐화 : private 변수의 getter/setter 함수



## 변수와 자료형

## 상수와 형 변환

## [컬렉션 프레임워크](https://github.com/j096/cs-study/tree/master/Language/JAVA/Collection_Framework)

## 정렬

- [Array](https://github.com/j096/cs-study/tree/master/Language/JAVA/Sorting/Array)
- [List](https://github.com/j096/cs-study/tree/master/Language/JAVA/Sorting/List)
- [Set](https://github.com/j096/cs-study/tree/master/Language/JAVA/Sorting/Set)
- [Map](https://github.com/j096/cs-study/tree/master/Language/JAVA/Sorting/Map)

## 메소드와 변수의 스코프

## 클래스와 인스턴스

- 클래스 변수와 클래스 메소드
- 메소드 오버로딩과 String 클래스
- 정보 은닉과 캡슐화
- 클래스의 상속
- 인터페이스와 추상 클래스

## 자바의 기본 클래스

- 자바 가상머신의 메모리 모델
- Object 클래스
- 래퍼 클래스 (Wrapper 클래스)
- BigInteger 클래스 & BigDecimal 클래스
- Math 클래스
- Arrays 클래스

## 제네릭(Generics)

## 열거형, 가변 인자, 어노테이션

## 네스티드 클래스

## 람다(Lambda)

## 메소드 참조와 Optional

## 스트림

## 쓰레드와 동기화

