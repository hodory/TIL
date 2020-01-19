# Model Mapper

## 무엇인가
Java에서 클래스간 복사를 할 때 유용하게 사용할 수 있는 라이브러리.

## 언제 사용 하는가
개인적으로는 builder 패턴이나 getter/setter를 이용해서 객체를 생성하는것을 선호하지만,<br/>
결국 귀찮으니까 사용합니다.

JPA Entity Model을 수정할 경우, 그 값이 실제로 데이터베이스에 반영되기때문에 DTO 객체를 만들어서 사용했는데,<br/>
이때 modelMapper를 사용하면 매우 편리합니다.(Entity의 컬럼이 추가되었을때 누락되는 문제 발생을 줄여줍니다.)

## 매핑 설정 방법

[Docs - Model Mapper_Propery Mapping](http://modelmapper.org/user-manual/property-mapping/)

TypeMap을 사용하여 커스터마이징 할 수 있습니다.

개인적으로는 스프링에서 주로 Config 파일으로 만들어 별도로 정의합니다.
```java
@Configuration
public class ModelMapperConfig {
    @Bean
    public ModelMapper modelMapper() {
        final ModelMapper modelMapper = new ModelMapper();
        modelMapper.typeMap(Member.class, MemberDTO.class)
                .addMapping(Member::getProfile, MemberDTO::setPicture); //addMapping
        return modelMapper;
    }
}
```


## 참고자료
[Deliwind Blog - ModelMapper 사용하기](https://blog.deliwind.com/posts/235)
