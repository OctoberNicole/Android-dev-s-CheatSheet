## 📁 org.springframework.context.annotation
### @Bean 
> 메소드가 Spring 컨테이너가 관리 할 Bean을 생성 함을 나타냅니다.
```java
@Target(value={METHOD,ANNOTATION_TYPE})
@Retention(value=RUNTIME)
@Documented
public @interface Bean
```
> example
```java
@Bean({"b1", "b2"}) // bean available as 'b1' and 'b2', but not 'myBean'
public MyBean myBean() {
    // instantiate and configure MyBean obj
    return obj;
}
```
### Configuration
> 클래스가 하나 이상의 @Bean 메소드를 선언하고 Spring 컨테이너가 런타임에 Bean 정의 및 서비스 요청을 생성하도록 처리 할 수 있음을 나타냅니다.
```java
@Target(value=TYPE)
@Retention(value=RUNTIME)
@Documented
@Component
public @interface Configuration
```
> example
```java
@Configuration
public class AppConfig {

    @Bean
    public MyBean myBean() {
        // instantiate, configure and return bean ...
    }
}
```
## 📁 lombok
### @Getter
> 모든 필드에 @Getter 및 / 또는 @Setter에 주석을 달아 lombok이 기본 getter / setter를 자동으로 생성하도록 할 수 있습니다.
```java
@Target({ElementType.FIELD, ElementType.TYPE})
@Retention(RetentionPolicy.SOURCE)
public @interface Getter 
```
> example
```java
import lombok.AccessLevel;
import lombok.Getter;
import lombok.Setter;

public class GetterSetterExample {
    /**
    * Age of the person. Water is wet.
    * 
    * @param age New value for this person's age. Sky is blue.
    * @return The current value of this person's age. Circles are round.
    */
    @Getter @Setter private int age = 10;

    /**
    * Name of the person.
    * -- SETTER --
    * Changes the name of this person.
    * 
    * @param name The new value.
    */
    @Setter(AccessLevel.PROTECTED) private String name;

    @Override public String toString() {
        return String.format("%s (age: %d)", name, age);
    }
}
```
