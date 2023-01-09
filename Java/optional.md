# Optional

```java
public final class Optional<T> {
    private final T value;
    ...
}
```

- 자바8부터 NullPointerException 예외를 일으키는 null 값에 대한 처리를 더 깔끔하게 하기 위해 Optional 클래스가 추가됨

- null 값일 수도 있는 변수를 감싸주는 Wrapper 클래스

- 단순한 값을 얻기 위한 용도라면 Optional 사용보다는 null 체크 통해서 직접 비교하는 편이 나음

    ```java
    Optional.orNullable(value).orElse("unknown");

    value == null ? "unknown" : value;
    ```

- Optional은 메서드 파라미터로 사용하지 않음



## Optional 객체 생성

### Optional.of()

```java
Optinal<String> optional = Optional.of(value);
```

- value 값을 넣어서 Optinal 객체 생성

- value 값이 null인 경우에는 NullPointerException 예외 발생

### Optional.ofNullable()

```java
Optinal<String> optional = Optional.ofNullable(value);
```

- value 값을 넣어서 Optional 객체 생성

- value 값이 null 인 경우 Optional.empty() 가 리턴돼서 NullpointerException 예외 발생하지 않음

### Optional.empty()

```java
Optional<String> optional = Optional.empty();
```

- 빈 Optional 객체 생성

- Optional 객체 자체는 있지만 내부에서 가리키는 참조가 없는 경우를 빈 객체라고 함

## Optional 중간 처리

- Optional 객체 가져와서 처리 후 다시 Optional 객체 반환하는 메서드

### filter()

- filter 메서드의 인자로 받은 람다식이 참이면 Optional 객체 그대로 통과시키고 거짓이면 Optioanl.empty() 반환하여 추가 처리 안되도록 함

- Java Stream의 filter와 유사함

### map()

- Optional 객체 값에 어떤 수정을 가해서 다른 값으로 변경하는 메서드


## Optional 객체 값 가져오기

### isPresent()

- Optional 객체 값이 null인지 여부 판단하여 boolean 값 반환

### ifPresent()

```java
Optional.ofNullable(null).ifPresent(System.out::println);
```

- 람다식을 인자로 받아 값이 존재할 때 그 값에 람다식 적용해주고 값이 없다면 람다식 실행하지 않음

### get()

```java
Optional<String> optional = Optional.of(value);

if(optional.isPresent()) {
    System.out.println(optional.get());
}
```

```java
public T get() {
    if (value == null) {
        throw new NoSuchElementException("No value present");
    }
    return value;
}
```

- Optional 객체가 가지고 있는 value 값을 가져옴

- Optional 객체에 값이 없다면 NoSuchElementException 발생하므로 isPresent() 로 null 체크 필요

### orElse()

```java
String value1 = "hello";
Optional<String> optional1 = Optional.ofNullable(value1);
System.out.println(optional1.orElse("unknown")); // hello

String value2 = null;
Optional<String> optional2 = Optional.ofNullable(value2);
System.out.println(optional2.orElse("unknown")); // unknown
```

- 중간 처리 메서드를 거치면서 원래 Optional 객체 비어 있었다면 지정된 값이 기본값으로 리턴됨

- 메서드의 인자가 항상 평가되며 객체 생성되므로 객체 생성 비용이 크면 orElse() 메서드 사용 피해야 함

### orElseGet()

```java
String value1 = "hello";
Optional<String> optional1 = Optional.ofNullable(value1);
System.out.println(optional1.orElseGet(() -> "unknown")); // hello

String value2 = null;
Optional<String> optional2 = Optional.ofNullable(value2);
System.out.println(optional2.orElseGet(() -> "unknown")); // unknown
```

- Optioanl 객체가 비어있다면 메서듸 인자로 입력되어 있는 Supplier 함수를 적용하여 객체 얻어옴

- Optional 객체가 비어있는 경우에만 Supplier 함수를 실행하므로 객체 생성 비용이 크다면 orElseGet() 메서드 사용

### orElseThrow()

- Optional 객체가 비어있었다면 Supplier 함수를 실행해 예외를 발생시킴