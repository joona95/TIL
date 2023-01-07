# Enum (Enumerated Type)

- 서로 연관된 상수들의 집합

- enum 등장 이전까지는 클래스 형식의 패턴으로 일반적으로 상수 표현

    ```java
    class FRUIT {
        public static final FRUIT APPLE = new FRUIT();
        public static final FRUIT PEACH = new FRUIT();
        public static final FRUIT BANANA = new FRUIT();
    }

    enum FRUIT {
        APPLE, PEACH, BANANA;
    }
    ```

- enum 또한 클래스에 해당됨

- 타입의 안전성과 가독성을 향상시키고 클래스 형태가 주는 강력한 기능 사용 가능

- 열거형은 암시적으로 java.lang.Enum 클래스를 상속해서 자바에선 클래스의 다중 상속 허용하지 않으므로 열거형이 다른 열거형이나 클래스 상속 불가'

    - 대신 인터페이스를 구현할 수는 있음

- final이 달려있어서 클래스가 열거형을 상속받을 수도 없음

### static 메서드

- values() : 해당 열거체의 모든 상수들이 담긴 배열 반환

- valueOf(String arg) : 인자로 받은 String 값에 해당하는 Enum 타입 리턴

- valueOf(Class/<T> class, String arg) : 인자로 받은 EnumType 클래스에 해당하는 Enum타입 리턴

### 일반 메서드

- name() : 해당 Enum 값의 이름을 String으로 리턴

- ordinal() : 해당 Enum이 정의된 순서(0부터 시작)를 반환

### class 기본 제공 메서드

- equals()

- compareTo()

- toString()

### 생성자

```java
enum FRUIT {
    APPLE, PEACH, BANANA;
    FRUIT() {
        ...
    } 
}
```

- enum도 클래스 형태이므로 생성자 존재함

- enum의 생성자는 private로만 가능

- 클라이언트에서 인스턴스를 직접 생성하거나 확장 불가

- 처음에 지정한 상수들만이 유일한 인스턴스가 됨

- 인스턴스 생성을 제어하며 외부적으로 하나의 인스턴스만 가지고 사용되므로 싱글턴 방식

### 필드

```java
enum FRUIT {
    APPLE("red"), PEACH("pink"), BANANA("yellow");
    private final String color;
    FRUIT() {
        this.color = color;
    } 
}

- 필드는 생성자를 통해 추가가 가능

- 각 열거 타입의 상수들이 final로 만들어진 불변 객체이므로 모든 필드 역시 final이어야 함



