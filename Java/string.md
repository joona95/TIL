# String vs String Builder vs String Buffer

## String 이란

- 문장의 형태로 문자열을 나타내는 자료형

- 가장 많이 사용되는 자료형 중 하나

- 불변성을 가지고 있음

- 생성 방법

    ```
    String str = "abc";
    ```

    - String 리터럴로 생성

        ```
        String str1 = "abc";
        String str2 = "abc";
        String str3 = new String("abc").intern();

        //셋 다 동일한 주소값 가진 객체
        ```

        - Java Constant Pool에 저장되어 재사용이 가능함

        - 내부적으로 intern() 메소드 사용으로 String pool에 동일한 문자열 있는지 여부 확인 후 있으면 해당 문자열의 주소값 반환

            - String pool의 위치는 버전에 따라 다름

                - Java6까지는 Perm 영역, Java7부터는 Heap 영역

                - Perm 영역은 Runtime 중 메모리를 동적으로 늘리지 못하여 OutOfMemory 문제가 발생하여 변경됨

    ```
    String str = new String("abc");
    ```

     - new 연산자 사용해서 생성

        ```
        String str1 = new String("abc");
        String str2 = new String("abc");
        
        //str1 과 str2 의 값은 동일하나 다른 객체
        ```

        - 각자 독립적인 객체로 Heap에 저장됨

- 이미 생성된 String 에 `concat()` 이나 `+` 를 이용하여 문자열 수정 가능

    - 기존 문자열 수정하는 것이 아니라 새로운 문자열을 생성하고 기존의 문자열과의 맵핑 해제

    - 맵핑이 해제된 문자열은 Garbage Collector가 처리함

- String은 불변성을 지녀 멀티쓰레드 환경에서 안전함 (thread-safe)

- StringBuilder 나 StringBuffer 는 String 과 달리 가변성 가지고 있어서 동일 객체 안에서 문자열 변경하는 것이 가능

    - 문자열 수정이 빈번할 때는 StringBuilde, StringBuffer 사용하는 것이 나음

    - StringBuilder 와 StringBuffer는 동기화 여부가 다름

- 불변성을 가진 String 이 StringBuilder 와 StringBuffer 보다 수정이 적은 경우에는 효율적

    - StringBuilder 와 StringBuffer 는 초기에 buffer 크기를 설정해줘야 하고 문자열 수정 시에도 buffer 크기 조정이 필요하면 크기 조정 필요하여 생성 시간이 오래 걸림

## 문자열 + 문자열

```
String str1 = "abc";
String str2 = "def";
str1 += str2;
```

- JDK 5 이전 버전에서 + 연산 시 매 연산마다 String 객체가 생성됐음

- 이후 버전에서 성능 향상을 목적으로 StringBuilder 혹은 StringBuffer 를 사용하여 중간단계 객체가 생성되지 않도록 함

- 많은 수의 문자열 연결할 경우 StringBuilder를 만드는 비용이 더 클 수 있음

- for loop문을 돌 때마다 + 는 내부 컴파일러에서 toString() 으로 반환함

## concat

```
String str1 = "abc";
String str2 = "def";
str1.concat(str2);
```

- 연결할 문자열 길이가 0이 아니라면 내부적으로 새 문자 배열 버퍼를 만들어 해당 문자 배열 기반으로 새 문자열 반환

- 적은 수의 문자열 연결할 경우 + 보다 더 유리

## StringBuilder

```
StringBuilder sb = new StringBuilder("abc");
sb.append("def");
String str = sb.toString();
```

- StringBuilder는 동기화를 지원하지 않아서 멀티쓰레드 환경에 적합하지 않음

- 단일쓰레드에서의 성능은 StringBuffer 보다 뛰어남

## StringBuffer

```
StringBuffer sb = new StringBuffer("abc");
sb.append("def");
String str = sb.toString();
```

- StringBuffer는 동기화 키워드를 지원하여 멀티쓰레드 환경에서 안전함 (thread-safe)

- 각 메소드 별로 Synchronized keyword가 존재함

- synchronized 키워드가 들어가서 입력은 보장하지만 순서를 보장해 주지는 않음



