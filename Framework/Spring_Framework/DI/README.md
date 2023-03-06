# DI (Dependency Injection)
 스프링의 핵심은 의존 관계 주입 컨테이너이다.
 
 ## 의존관계 주입
 프로그래밍에서 의존성(Dependency)란, 어떤 클래스가 자신의 임무를 다하기 위해 필요한 값(필드 값)이나 사용할 다른 클래스와의 관계를 말한다.
 주입(Injection)이란, 어떤 클래스의 인스턴스에 대해 외부로부터 '의존성'을 설정하는 것을 말한다.
 
 의존관계 주입 컨테이너가 하는 역할은 어떤 클래스가 필요로 하는 값이나 인스턴스를 생성, 취득하고 그 클래스의 인스턴스에 대해 설정하는 것이다. 즉, 필요한 인스턴스를 생성, 취득하는 코드를 직접 작성하지 않아도 된다. 그 결과 클래스간 관계가 느슨한 결합이 되어 의존성은 약해진다.
 
 ## 의존관계 주입 방법
 주입에는 몇몇방법이 있지만, 스프링은 다음과 같은 대표적인 두 가지 주입을 지원한다.
 
 - 생성자를 통한 주입
   생성자를 통한 주입이란 생성자를 사용해 의존 관계를 주입하는 것이다.
```
public class Foo{
  private Bar bar;
  
  public Foo(Bar bar){
    this.bar = bar;
  }
}
```
  설정파일(beans.xml)에서의 주입
```
<bean id="foo" class="Foo">
  <constructor-arg>
    <value>
      <ref bean="bar" />
    </value>
  </constructor-arg>
</bean>

<bean id="bar" class="Bar">
  <property name="...">
    <value>...</value>
  </property>
</bean>

```
 - 설정 메서드를 통한 주입
  설정 메서드를 통한 주입이란, 설정 메서드를 사용해서 의존 관계를 주입하는 것이다.
```
public class Foo{
  private Bar bar;
  
  public setBar(Bar bar){
    this.bar = bar;
  }
}
```
  설정파일(beans.xml)에서의 주입
```
<bean id="foo" class="Foo">
  <property name="bar">
    <value>
      <ref bean="bar" />
    </value>
  </property>
</bean>

<bean id="bar" class="Bar">
  <property name="...">
    <value>...</value>
  </property>
</bean>

```

## Autowiring
BeanFactory에는 '오토와이어링(Autowiring)'이라는 기능이 있다. 어떤 Bean이 참조하는 형태와 실제 상요할 클래스를 자동으로 연결해준다.

설정파일 예시
```
<bean id="foo" class="Foo" autowire="byName" />
```

어노테이션 예시 (설정파일에 <context:annotation-config/> 추가 필요)
```
public class Foo{
  @Autowired
  Bar bar;
}
```
Autowiring 설정 방법은 2가지이다.
1. <beans> 요소의 default-autowire 속성을 이용하여 그 자식 요소인 모든 <bean> 요소에 설정이 적용된다,
2. <bean> 요소의 autowire 속성을 이용하여 각각의 <bean> 마다 Autowiring을 설정한다.

- autowire 속성에 지정 가능한 값
  - no: Autowiring을 하지 않는다. 기본 값.
  - byName: Bean 필드 이름과 같은 이름의 id를 갖는 Bean을 연결해준다.
  - byType: Bean 필드에 대한 Setter 메서드의 인수 타입을 사용해 연결해준다.
  - constructor: 생성자에 대해 byType을 사용해 연결해준다.
  - autodetect: constructor인지 byType인지 자동으로 판단한다. 기본 생성자가 정의되어있지 않은 경우는 consturctor를, 정의되어있는 경우는 byType을 사용해 연결해준다.
