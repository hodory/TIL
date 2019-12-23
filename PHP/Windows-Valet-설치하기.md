# Windows Valet 설치하기

Valet을 설치하기 위해서는 PHP와 Comopser가 필요하다.<br/>
물론 Docker로 설치하는게 가장 깔끔하지만 Valet을 한번 사용해보고자 설치해보았다.


## PHP 설치하기
```shellscript
$ scoop install php
```

## php.ini 설정하기
기본적으로 `php.ini-production`을 참조하는데, 값을 변경해야 ssl 관련 composer 설치오류를 해결할 수 있고,<br/> 
valet 설치시 `php.ini`를 참조하기때문에 `php.ini`를 생성해두어야한다.
```
# php.ini 복사
$ cp ~/scoop/apps/php/current/php.ini-production ~/scoop/apps/php/current/php.ini
```

`php.ini`의 4개의 항목의 주석을 풀도록한다.
```ini
# php.ini
extension=curl
extension=fileinfo
extension=mbstring
extension=openssl
```

## Composer 설치하기
```
scoop install composer
```

## Valet 설치하기
```shellscript
$ composer global require cretueusebiu/valet-windows
```
`laravel/valet`에서 fork 되고, 관리가 안되는 패키지인줄 알았는데, 아직 잘 동작한다.

valet 명령어를 사용하기 위해서는 composer global 패키지를 Path에 등록한다.<br/>
환경변수 Path에 `%HOMEPATH%\scoop\persist\composer\home\vendor\bin`을 추가하고 커맨드창을 다시 열면 valet 명령어가 동작한다.

그 후 관리자 권한으로 `$ valet install`을 실행해서 valet을 설치하고, 네트워크 설정에서 DNS를 로컬로 설정한다.

### 기본 TLD 변경하기
`$ valet tld app` 과 같이 명령어를 입력하면 `homestead.app`과 같이 프로젝트와 도메인을 연결할 수 있다.

### 프로젝트와 도메인 연결하기
하위 디렉토리를 도메인과 연결하기 위해서는 `$ valet park`를 실행하면 된다.

`디렉토리명.app`으로 접근할 수 있다.

## 참고자료

> [정광섭님 - Windows 에서 Valet 으로 PHP 개발 환경 만들기](https://www.lesstif.com/pages/viewpage.action?pageId=39126153)
