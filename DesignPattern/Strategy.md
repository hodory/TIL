# 전략 패턴

알고리즘을 캡슐화 하며, 해당 코드를 사용하는 쪽에서는 실제 구현체의 상세를 모르더라도 사용 가능 하도록 하는 패턴

## 장점
- 유연하여 교체가 용이하게 구현이 가능하다.
  - 예를 들어 해당 인터페이스를 구현한 구현체에 따라 리턴타입을 다르게 줄 수 있다.

## 단점
- 캡슐화 된 코드에 새로운 기능이 추가될 경우 기존의 코드에 영향을 미치게 됨. (결합도가 크다)
- 실행시간동안 사용되는 객체 수가 증가하게됨.
  
## 예제

```php
/*
 * UserInterface.php
 */
 
namespace App\Http\Services;

interface UserInterface
{
    public function getUser($userId);
}

---

/*
 * ArrayFormatUser.php
 */
 
namespace App\Http\Services;

use App\Users;

class ArrayFormatUser implements UserInterface
{
    public function getUser($userId) {
        return Users::find($userId)->toArray();
    }
}

---

/*
 * JsonFormatUser.php
 */
 
namespace App\Http\Services;

use App\Users;

class JsonFormatUser implements UserInterface
{
    public function getUser($userId) {
        return Users::find($userId)->toJson();
    }
}

---

/*
 * User.php
 */

namespace App\Http\Controllers;

class UserController extends Controller
{
    protected $user;
     
    public function __construct(UserInterface $user)
    {
        $this->user = $user;    
    }
 
}
```

```java
@Slf4j
@RestController
public class UserController {
    
    private UserService userService;
    
    UserController(UserServiceImpl userService) {
        this.userService = userService;
    }
    
    @GetMapping("/user/{userId}")
    public function getUser(@PathVariable int userId) {
        User user = userService.getUser(userId);
        ...
    }
    
}

---

interface UserService {
    User getUser(int userId);
}

---

@Service
public class UserServiceImpl implements UserService {

    @Override
    public Members getMember(int userId) {
        ...
    }
}
```