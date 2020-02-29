# 오류

## `Illuminate\Session\TokenMismatchException : CSRF token mismatch.`

해당 오류는 CSRF Token이 맞지 않을때 나오는 오류이다.

PHPUnit 테스트중 의도치 않은 `CSRF token mismatch`가 나온다면 이를 해결하기 위해서는<br/>
`vendor/laravel/framework/src/Illuminate/Foundation/Http/Middleware/VerifyCsrfToken.php`의 `handle()`에서 `$this->runningUnitTests()`로 테스트 여부를 체크하는데,<br/>
이때 참조하는 값인 환경변수인 `APP_ENV`를 testing으로 변경하면된다.

---

동일 API에 요청을 보내면

```shell script
Tests\Feature\ProjectsTest::a_project_requires_a_title Session is missing expected key [errors]. Failed asserting that false is true.
```

오류가 나오는데 위의 테스트 코드를 주석 처리하거나,
`phpunit.xml`에서 `APP_ENV` 값을 확인하여 application이 `testing`으로 동작하는지 확인하도록한다.
또는 해당 테스트에 `$this->wihtoutMiddleware()`를 사용하면 임시로 해결할 수 있다.
