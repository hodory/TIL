# 커버링 인덱스

## 정의
인덱스가 하나의 질의를 모두 커버한다는 뜻.
데이터 페이지에 저장되어 있는 레코드를 읽어오지 않아도 인덱스의 키값만으로도 결과를 얻을 수 있음. 

> 출처 : https://d2.naver.com/helloworld/1155

## 예시

```sql
select * from users where tel like '0101234%' limit 0, 15;
```

일반적으로 회원의 연락처로 회원을 검색시 위와 같은 쿼리를 많이 작성한다.<br/>
연락처는 주로 varchar와 같이 문자열 형태로 저장을 하게 되는데, 문자열을 like로 검색시에 Full-Scan을 타게된다<br/>
이러한 문제는 row의 수가 많아질수록 쿼리의 실행이 느려지게 된다.

해당 쿼리는 아래와 같이 변환 하면 인덱스만으로 처리가 가능하다.
```sql
# id는 users 테이블의 PK(Primary Key)입니다. 
select a.* from
(
    select id from users where tel like '0101234%' limit 0, 15
) a join users b on a.id = b.id
```

이와 같이 실행할 경우, InnoDB 테이블의 모든 보조 인덱스의 값에는 PK를 가지고 있기때문에
인덱스의 접근만으로도 원하는 데이터에 접근할 수 있다고 한다.

> 출처 : http://gywn.net/2012/04/mysql-covering-index/

---

> 참고자료

- [MySQL에서 커버링 인덱스로 쿼리 성능을 높여보자!!](http://gywn.net/2012/04/mysql-covering-index/ "해당 링크로 이동")
- [성능 향상을 위한 SQL 작성법](https://d2.naver.com/helloworld/1155 "해당 링크로 이동")
