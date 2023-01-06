# 함수형 인터페이스

## 객체지향 프로그래밍과 함수형 프로그래밍

- 객체지향 프로그래밍

    - 외부 변수에 영향을 받아 언제든지 값이 변돌될 위험이 있음

- 함수형 프로그래밍

    - 외부 변수에 영향을 받지 않고 동일한 input에 동일한 output을 보장함

    - 함수의 인자를 함수로 전달 가능하여 함수 자체도 재사용 가능함


## 익명 내부 클래스

```java
Collections.sort(words, new Comparator<String>() {
    @Override
    public int compare(String o1, String o2) {
        return o1.compareTo(o2);
    }
});
```

- 익명 내부 클래스로 함수 인자 전달 가능

- 그러나 익명 클래스를 선언하여 함수를 오버라이드해줘야 함


## 람다식

```java
Collections.sort(words, (o1, o2) -> o1.compareTo(o2));
```

- Java8부터 람다식으로 익명 클래스 대신 람다식을 사용하며 더 간결한 표현 가능

```java
public interface Comparable<T> {
    public int compareTo(T o);
}
```

- 람다식은 컴파일러가 위와 같은 인터페이스의 추상 메서드를 통해 해당 함수가 어떤 일을 하는지 추론이 가능해야 함


## 함수형 인터페이스

- 람다식은 인터페이스의 추상 메서드의 매개변수 타입, 반환 타입으로 추론이 가능해야 함

- 람다식을 이용할 때 해당 인터페이스에 추상 메서드가 여러 개면 컴파일러가 추론하지 못하여 람다식 이용 불가

- 인터페이스의 추상 메서드는 오직 하나만 있어야 함

- 함수형 인터페이스: 단 하나의 추상 메서드를 가지는 인터페이스


## 함수형 인터페이스의 특징

### @FunctionalInterface

```java
@FunctionalInterface
inteface Operator {
    int calculate(int leftOperand, int rightOperand);
}
```

- 이 어노테이션은 추상 메서드가 하나임을 알려줌

- 추상 메서드가 하나가 아닌 경우에는 오류를 발생시킴

### static 메서드, default 메서드

```java
@FunctionalInterface
inteface Operator {
    int calculate(int leftOperand, int rightOperand);

    default int returnZero() {
        return 0;
    }

    static int returnOne() {
        return 1;
    }
}
```

- 함수형 인터페이스는 static 메서드, default 메서드를 가질 수 있음

- static 메서드와 default 메서드는 추상 메서드 개수와 관계 없음


### 함수형 인터페이스 사용 예시

```java
public static void main(String[] args) {
    Operator plus = (leftOperand, rightOperand) -> leftOperand + rightOperand;
    Operator minus = (leftOperand, rightOperand) -> leftOperand - rightOperand;
    Operator multiply = (leftOperand, rightOperand) -> leftOperand * rightOperand;
    Operator divide = (leftOperand, rightOperand) -> leftOperand / rightOperand;

    plus.calculate(1, 2);
    minus.calculate(1, 2);
    multiply.calculate(1, 2);
    divide.calculate(1, 2);
}

@FunctionalInterface
inteface Operator {
    int calculate(int leftOperand, int rightOperand);
}
```

- 람다식을 이용하여 추상 메서드를 통해 함수 단위로 재사용 가능


## 함수형 인터페이스 패키지

```java
public static void main(String[] args) {
    BinaryOperator<Integer> plus = (leftOperand, rightOperand) -> leftOperand + rightOperand;
    BinaryOperator<Integer> minus = (leftOperand, rightOperand) -> leftOperand - rightOperand;
    BinaryOperator<Integer> multiply = (leftOperand, rightOperand) -> leftOperand * rightOperand;
    BinaryOperator<Integer> divide = (leftOperand, rightOperand) -> leftOperand / rightOperand;

    plus.calculate(1, 2);
    minus.calculate(1, 2);
    multiply.calculate(1, 2);
    divide.calculate(1, 2);
}
```

- Java에서 미리 제공하는 함수형 인터페이스 패키지 존재

- java.util.function 에 40여개의 함수형 인터페이스 존재

    - 참고: https://docs.oracle.com/javase/8/docs/api/java/util/function/package-summary.html

- Java에서 제공하는 함수형 인터페이스 사용 시 코드가 더 간결해짐

- 기본 함수형 인터페이스 대부분은 기본 타입만 지원하므로 박싱된 기본 타입을 넣어 사용하지 않는 것이 좋음

    - 동작은 하지만 계산량이 많을 때는 성능이 느려질 수 있음

    - 원시타입인 int를 받도록 되어 있는 IntConsumer 같은 함수형 인터페이스는 불필요한 박싱으로 객체 생성을 하지 않도록 도와줌

- 제네릭 함수형 인터페이스

    - 함수형 인터페이스에 있는 추상메서드에 제네릭 타입을 사용하여 모든 타입에 대해 허용하거나 타입에 대해 제약이 있는 인터페이스

    - 인자를 받아 어떤 값을 반환할지 제네릭 타입을 통해 명시 가능






