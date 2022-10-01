# 아무 입력 없이 Enter 누르는 경우 while 문 종료하여 입력 종료하기

## 문제 상황

- while 문으로 Scanner 통해서 input 을 무한히 받는 중

- 아무 입력 없이 Enter 키를 누르면 while 문이 종료되도록 하고 싶었음

## 해결

```Java
while(scanner.hasNextLine() && !((line = scanner.nextLine()).isEmpty())) {
    //입력받은 line 값으로 하고 싶은 행위 추가
    //아무 입력 없이 Enter 를 누르거나 EOF 인 경우 while문 종료
}
```
