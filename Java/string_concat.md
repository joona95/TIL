# String 연결 최적화

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

- String은 불변성을 지녀 멀티쓰레드 환경에서 안전함 (thread-safe)

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



