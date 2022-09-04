# @Value 어노테이션으로 properties 값 읽어오기

- @Value 어노테이션: 데이터베이스 연결 정보, 외부 API 주소 등의 메타 정보를 관리하기 위한 properties, yml, yaml 파일에서 메타 정보를 가져오기 위해 사용하는 어노테이션

```yml
spring:
    test:
        name: hello
        age: 20
        list: a,b,c
```

```java
@Value("${spring.test.name}")
private String name;
@Value("${spring.test.age}")
private int age;
@Value("${spring.test.list}")
private String[] array;
@Value("#{'${spring.test.list}'.split(',')}")
private List<String> list;
```


