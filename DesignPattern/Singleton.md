# Singleton Pattern(싱글턴 패턴)

웹 어플리케이션 실행중 특정 클래스는 단 하나의 인스턴스만 존재하여,<br/>
모든 곳에서 해당 인스턴스만 사용하도록 하는 경우에 사용.


- ### 장점
 - 매번 객체를 생성할 필요 없이, 한번만 생성하여 인스턴스를 얻어오기때문에 메모리를 효율적으로 사용할 수 있다.
 - 다른 클래스에서 사용하기 쉽다.

- ### 단점
 - **상태와 같은 정보를 가지게 되기 때문에, 유의해서 사용해야 한다.**
## Spring Framework

- 스프링에서는 모든 Bean들을 싱글톤으로 관리하고 있다.
  - Bean으로 등록된 클래스의 프로퍼티는 애플리케이션 실행동안 유지되기때문에 유의해서 사용해야한다. 
 
## 예제

```java
public class User {
    private static User user = new User();

    // 생성자를 외부에서 호출하지 못하도록 접근 제한자를 private로 설정 
    private User() {
    }
    
    private static User getInstance() {
        return user;
    } 
}


public class Main {
    public static void main(String[] args) {
        User user = User.getInstance();
    }
}
```

```php
class User {
    public static function getInstance() {
        static $instance = null;
        if (null === $instance) {
            $instance = new static();
        }

        return $instance;
    }
    
    // 외부에서 생성 금지하도록 설정 
    protected function __construct() {}

    // 인스턴스 복제 방지
    private function __clone() {}

    // 인스턴스 unserialize 방지
    private function __wakeup() {}
}

$user = User::getInstance();
```