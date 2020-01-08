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

PHPUnit을 사용할때에는 기본적으로 phpunit.xml 파일에 `DB_CONNECTION`이 `sqlite`로 되어있고,<br/>
`DB_DATABASE`는 `memory`로 되어있기 때문에 `pdo_sqlite`의 주석도 풀어주도록 한다.
 
```ini
extension=pdo_sqlite
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

#### Valet으로 띄운 프로젝트에 접근이 안될때
`valet-for-windows`를 사용할때 dnsmasq인 Acrylic DNS Proxy가 윈도우10에서 제대로 동작하지 않는 경우가 있다.

`$ valet tld localhost`를 이용해서 `.localhost`를 tld로 사용하면 동작하긴 하지만, 이것은 어디까지나 임시방편이고,<br/>
[Acrylic DNS Proxy Windows 10 Configuration](https://mayakron.altervista.org/wikibase/show.php?id=AcrylicWindows10Configuration)을 먼저 설정 한 후,<br/>
`%appdata%\Composer\vendor\cretueusebiu\valet-windows\bin\acrylic\AcrylicConfiguration.ini`의 `LocalIPv4BindingAddress` 값을 `0.0.0.0` 에서 `127.0.0.1`으로 변경하고
`$ valet restart`를 실행하여 주면된다.

기본적으로 https로 요청을 하기때문에 http로 프로토콜을 바꿔주면 성공 할 수 있다.

[AcrylicDNS not working](https://github.com/cretueusebiu/valet-windows/issues/91)


**Homestead와 달리 MYSQL을 별도로 설치해주어야한다.**


## 참고자료

> [정광섭님 - Windows 에서 Valet 으로 PHP 개발 환경 만들기](https://www.lesstif.com/pages/viewpage.action?pageId=39126153)
