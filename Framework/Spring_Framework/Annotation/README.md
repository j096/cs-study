# Annotation
자바 어노테이션은 소스코드에 추가해서 사용할 수 있는 메타데이터의 일종이다. 메타데이터란 애플리케이션이 처리해야할 데이터가 아니라 컴파일 과정과 실행 과정에서 코드를 어떻게 처리해야하는지를 알려주기 위한 추가 정보이다.

스프링에서는 이 자바 어노테이션 기능을 적극적으로 이용하는데(Annotation-based Container Configuration), 이 페이지에서는 스프링에서 자주 사용하는 어노테이션을 정리해보았다.



## Bean 등록 관련

### @Component vs @Named vs @ManagedBean

`@Named` 는 JSR-330, `@ManagedBean` 은 JSR-250은 표준이며, `@Component` 대신 사용할 수 있다.

### Stereotype 어노테이션

빈 등록 관련 고정 의미 어노테이션이다. @Component 와 역할은 같지만 특정 어노테이션을 갖는 그룹에 부가적인 기능을 부여하거나, AOP 적용 대상 그룹을 만드는 등과 같은 구현이 가능해진다.

- @Component: 스프링이 관리하는 클래스(Bean) 에 사용한다.

- @Service: @Component와 역할은 같지만 서비스 계층의 빈에 부여하며, 의미론적으로 쓰인다.
- @Controller: @Component와 역할은 같지만 MVC에서 컨트롤러 역할의 빈에 부여하며, 의미론적으로 쓰인다.
- @Repository: @Component와 역할은 같지만 DAO(Data Access Object) 빈에 부여하며 의미론적으로 쓰인다.



## Bean Lifecycle 관련

### @PostContruct & @PreDestory

 빈의 initialization callback 과 destruction callback 을 제공한다.



## DI 관련

### @Autowired vs @Inject

의존성 주입에 사용되는 어노테이션이다.

둘 다 같은 방식으로 작동하며, Autowired는 스프링에서 지원하고 Inject는 JSR 330 표준 어노테이션이다.

같은 방식으로 빈을 스캔하지만 빈을 찾는 순서가 다르다.

- @Autowired: 타입 -> 이름 -> @Qualifier -> 실패
- @Inject: 타입 -> @Qualifier -> 이름 -> 실패

- 생성자(constructor)에 사용한 예시

  ```java
  public class MovieRecommender {
  
      private final CustomerPreferenceDao customerPreferenceDao;
  
      @Autowired
      public MovieRecommender(CustomerPreferenceDao customerPreferenceDao) {
          this.customerPreferenceDao = customerPreferenceDao;
      }
  
      // ...
  }
  ```

  

- setter 메서드에 사용한 예시

  ```java
  public class MovieRecommender {
  
      private MovieCatalog movieCatalog;
  
      private CustomerPreferenceDao customerPreferenceDao;
  
      @Autowired
      public void prepare(MovieCatalog movieCatalog,
              CustomerPreferenceDao customerPreferenceDao) {
          this.movieCatalog = movieCatalog;
          this.customerPreferenceDao = customerPreferenceDao;
      }
  
      // ...
  }
  
  ```

  

- 필드에 사용한 예시

  ```java
  public class MovieRecommender {
  
      private final CustomerPreferenceDao customerPreferenceDao;
  
      @Autowired
      private MovieCatalog movieCatalog;
  
      @Autowired
      public MovieRecommender(CustomerPreferenceDao customerPreferenceDao) {
          this.customerPreferenceDao = customerPreferenceDao;
      }
  
      // ...
  }
  ```

  

### @Resource

JSR-250 표준인 어노테이션이다. 필드와 setter 메서드에 사용할 수 있으며, name 어트리뷰트를 설정해주어야 한다. 스프링은 디폴트로 지정해준 name 값으로 주입한다. 만약 name 을 설정해 주지 않으면 암묵적으로 필드 주입의 경우 필드명에서, setter 메서드 주입의 경우 파라미터 변수 명에서 가져와 설정한다.

- 스캔 순서

  ```
  이름 -> 타입 -> @Qualifier -> 실패
  ```

  

- 예시

```java
public class SimpleMovieLister {

    private MovieFinder movieFinder;

    @Resource(name="myMovieFinder") (1)
    public void setMovieFinder(MovieFinder movieFinder) {
        this.movieFinder = movieFinder;
    }
}

```



### @Value

외부에 설정된 속성값을 가져와 주입하는데 사용된다. 

예시

```Java
@Component
public class MovieRecommender {

    private final String catalog;

    public MovieRecommender(@Value("${catalog.name}") String catalog) {
        this.catalog = catalog;
    }
}

--------------------------------------------------------------------------------
    
@Configuration
@PropertySource("classpath:application.properties")
public class AppConfig { }

--------------------------------------------------------------------------------    
[application.properties]
catalog.name=MovieCatalog
```



## AOP 관련

### @Transactional

DB와 관련된, 트랜잭션이 필요한 서비스 클래스 혹은 메서드에 사용한다. 

적용된 범위에서는 트랜잭션 기능이 포함된 프록시 객체가 생성되어 자동으로 commit 혹은 rollback을 진행해준다.

