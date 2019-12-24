# 오류

## `Illuminate\Session\TokenMismatchException : CSRF token mismatch.`

해당 오류는 CSRF Token이 맞지 않을때 나오는 오류이다.

PHPUnit 테스트중 의도치 않은 `CSRF token mismatch`가 나온다면 이를 해결하기 위해서는<br/>
`vendor/laravel/framework/src/Illuminate/Foundation/Http/Middleware/VerifyCsrfToken.php`의 `handle()`에서 `$this->runningUnitTests()`로 테스트 여부를 체크하는데,<br/>
이때 참조하는 값인 환경변수인 `APP_ENV`를 testing으로 변경하면된다.
