# 람다 (Lambda)

## 람다란?

- 람다 함수는 함수형 프로그래밍 언어에서 사용되는 식별자 없이 실행 가능한 함수

- Java8부터 지원되며 불필요한 코드를 줄이고 가독성 향상시키는 것을 목적으로 함

- 람다식의 도입으로 객체지향 언어인 자바가 동시에 함수형 언어의 기능을 갖추게 됨

- @FunctionalInterface 지정하게 되면 해당 인터페이스가 함수형 인터페이스인지 체크 가능

```
//객체를 생성해서 메서드를 매개변수로 전달
public static void main(String[] args) {
    new Thread(new Runnable() {
        @Override
        public void run() {
            System.out.println("Hello world");
        }
    }).start();
}

//객체 자체를 직접 생성할 필요 없이 람다식 표현 (런타임 시 익명 구현 객체 생성)
public static void main(String[] args) {
    new Thread(() -> System.out.println("Hello world")).start();
}
```

- 장점

    - 코드의 라인 수를 줄여서 가독성이 향상됨

    - 병렬 프로그래밍이 가능하여 멀티스레드 환경에서 용이함

- 단점

    - 재사용이 불가능함

    - 디버깅이 어려움

## 람다식

```
(a) -> { System.out.println(a); }
```

- 매개변수 타입은 런타임 시에 대입되는 값에 따라 자동으로 인식되므로 일반적으로 생략

```
a -> System.out.println(a)
```

- 매개변수가 하나일 때는 괄호 생략 가능

- 실행문이 한 줄이라면 중괄호 생략 가능

```
() -> System.out.println("Hello world")
```

- 매개변수가 없다면 빈괄호를 반드시 사용해야함

```
(x, y) -> { return x + y; }
(x, y) -> x + y;
```

- 리턴문만 있는 경우 return을 생략

## 함수형 인터페이스

- 람다식은 하나의 메서드를 정의하기 때문에 두 개 이상의 추상 메서드가 선언된 인터페이스는 람다식을 이용해 구현 객체 생성 불가

- 하나의 추상 메서드가 선언된 인터페이스만 람다식의 타겟 타입이 될 수 있고 이 인터페이스를 함수형 인터페이스라고 함

interface | Descriptor | Abstract method
----------|------------|------------
Runnable|매개값X,리턴값X|void run();
Consummer\<T\>|매개값O, 리턴값 X|void accept(T t);
Supplier\<T\>|매개값X, 리턴값O|T get();
Function\<T,R\>|매개값O, 리턴값O|R apply(T t);
UnaryOperator\<T\>|매개값O, 리턴값O|T apply(T t);
Predicate\<T\>|매개값O, 리턴값boolean|boolean test(T t);


## 람다 캡쳐링

- 자유변수는 람다에 파라미터로 넘겨진 변수가 아닌 외부에서 정의된 변수

- 람다 캡쳐링은 람다 바디에서 자유변수 참조 가능한 것

- 지역변수를 람다 캡쳐링할 때는 제약 조건이 존재함

    - Java8 이전에는 final로 선언된 변수가 아니면 컴파일 에러 발생

    - Java8 이후에는 final로 선언되지 않은 자유변수는 초기화된 이후 값이 한 번도 변경되지 않아 final처럼 동작한 경우 참조 가능 (effectively final)

    - JVM에서 힙영역에 생성되는 인스턴스 변수와 달리 지역 변수는 스택 영역에 생성되는데 스택 영역은 쓰레드마다 별도로 생성됨. 람다는 별도의 스레드에서 실행 가능하므로 람다 캡쳐링이 될 때 지역변수의 값을 복사하여 사용하는데 이 때 멀티스레드 환경에서 변경될 경우 동시성 이슈 발생 가능.

    ```
    public class LambdaCapturing {
        private int a = 1;

        public void test() {
            final Runnable r = () -> {
                a = 2;
                System.out.println(a);
            }
        }
    }
    ```

    - 인스턴스 변수 a는 final로 선언되지 않아도 문제 없음

    - 인스턴스 변수 a는 final처럼 재할당되지 않아야 한다는 제약조건이 적용되지 않음

    ```
    public class LambdaCapturing {
        public void test() {
            final int a = 1;

            final Runnable r = () -> System.out.println(a);
        }
    }
    ```

    - 지역변수 a는 final로 선언돼있기 때문에 문제 없음

    ```
    public class LambdaCapturing {
        public void test() {
            int a = 1;

            final Runnable r = () -> System.out.println(a);
        }
    }
    ```

    - 지역변수 a는 final로 선언돼있지는 않지만 final로 선언한 것과 같이 변수에 값을 재할당하지 않았으므로 문제 없음

    ```
    public class LambdaCapturing {
        public void test() {
            int a = 1;

            a = 2;
            final Runnable r = () -> System.out.println(a);
        }
    }
    ```

    - 지역변수 a는 final로 선언돼있지 않으면서 값의 재할당이 일어나서 final처럼 동작하지 않으므로 에러 발생

## 메서드 레퍼런스

- 메서드를 간결하게 지칭할 수 있는 방법으로 람다가 쓰이는 곳에서 사용 가능

- 이중 콜론 연산자(::)

- 람다식 표현에서 단 하나의 베서드만 호출하는 경우에 해당 람다식에서 불필요한 매개변수 제거하여 파라미터의 중복 피할 수 있음

- 간결해질 수 있지만 익숙하지 않은 사람에게는 오히려 가독성을 해칠 우려가 있음

- 정적 메서드 참조

    ```
    public class Print {
        public void printNum(int n) {
            System.out.println(n);
        }
        public static void printStaticNum(int n) {
            System.out.println(n);
        }
    }

    Consumer<Integer> printName = num -> Print.printStaticNum(num);
    Consumer<Integer> printName = Print::printStaticNum;
    ```

- 인스턴스 메서드 참조

    ```
    Print print = new Print();
    Consumer<Integer> printName = num -> print.printNum(num);
    Consumer<Integer> printName = print::printNum
    ```

- 생성자 참조

    - 3개 이상의 인자를 받는 경우는 함수형 인터페이스가 제공되지 않으므로 직접 함수형 인터페이스 만들어야 함

    ```
    public class User {
        private String name;

        public User() {}
        public User(String name) {
            this.name = name;
        }
    }

    Supplier<User> userSupplier = () -> new User();
    Supplier<User> userSupplier = User::new;
    User user = userSupplier.get();

    Function<String, User> userFunction = (name) -> new User(name);
    Function<String, User> userFunction = User::new;
    User user = userFunction.apply("abc");
    ```