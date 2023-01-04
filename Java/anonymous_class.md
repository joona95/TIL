# 익명 클래스 (Anonymous Class)

## 익명 클래스란?

```
public class Test {
    public void print() {
        System.out.println("hello");
    }
}

public class Main {
    public static void main(String[] args) {
        Test test = new Test() {
            @Override
            public void print() {
                System.out.println("bye");
            }
        }
        test.print();
    }
}
```

- 프로그램에서 일시적으로 한 번 사용되고 버려지는 일회용 클래스로 말 그대로 이름이 없는 클래스를 의미

- 클래스 정의 없이 메소드 내에서 상속받아 바로 클래스 생성해서 인스턴스화할 수 있음

- 부모 클래스의 자원을 상속받아 재정의하여 사용할 자식 클래스가 한번만 사용될 경우 지역 변수처럼 익명 클래스로 정의하고 스택 끝나면 삭제되도록 하여 유지보수나 메모리 면에서 유리하도록 함

- 재사용하지 않는 일회성 클래스는 익명 클래스를 통해 코드를 줄일 수 있음

```
public class Test {
    public void print() {
        System.out.println("hello");
    }
}

public class Main {
    public static void main(String[] args) {
        Test test = new Test() {
            @Override
            public void print() {
                System.out.println("bye");
            }

            public void go() {
                System.out.println("go");
            }
        }
        test.print(); 
        test.go(); // error
    }
}
```

- 익명 클래스 방식은 오버라이딩한 메서드만 사용 가능하고 새로 정의한 메서드는 외부에서 사용 불가

```
Interface Itest {
    public void print();
}

public class Main {
    public static void main(String[] args) {
        Itest test = new Itest() {
            @Override
            public void print() {
                System.out.println("bye");
            }
        }
        test.print();
    }
}
```

- 인터페이스를 익명 객체로 선언하여 사용 가능

- 오로지 하나의 인터페이스만 구현하여 객체 생성 가능

```
Test test = new Test() {
    public void print(String str) {
        System.out.println(str);
    }
}

Test test = (s) -> { System.out.println(s) };
```

- 익명 클래스는 복잡한 자바를 간결하게 하기 때문에 java8 람다식 문법과 같이 많이 사용됨

