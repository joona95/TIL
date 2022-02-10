# Mocking (with Jest)

## mocking

- mocking은 테스트하려는 코드에 외부 의존성 있을 때 단위 테스트에서 사용되는 프로세스

- mocking을 통해서 실제 객체를 대체 객체로 대체함

- 대체 객체에는 fake, stub, mock 세가지 유형 존재

## mocking 하는 이유

- 테스트하려는 코드가 의존하고 있는 객체를 가짜로 만들어 의존성 제거하고 객체의 동작 통제 가능

- 의존성 있는 코드 테스트하다가 테스트 실패할 경우 어떤 코드가 문제인지 알기 어려운데 mocking하면 테스트 중인 코드에만 집중해서 테스트 가능

- 일반적으로 테스트하려는 코드가 의존하는 부분을 직접 생성하기 너무 부담스러운 경우 많이 사용됨

## Jest 의 Mocking

### **jest.fn()**

```js
const mockFn = jest.fn();
```

- 가짜 함수(mock function) 생성

```js
mock(1); // 어떤 값 리턴해야할지 알려주지 않았으므로 undefined
```

- 가짜 함수는 일반 자바스크립트 함수와 동일한 방식으로 인자 넘겨 호출

```js
mockFn.mockReturnValue("hello");
console.log(mockFn()); // hello
```

- `mockReturnValue(리턴 값)` 함수 이용하면 가짜 함수의 리턴값 설정 가능

```js
mockFn.mockResolvedValue("hello");
mockFn().then((res) => {
    console.log(res); // hello
})
```

- `mockResolvedValue(Promise가 resolve하는 값)` 함수 이용하면 가짜 비동기 함수 생성 가능

```js
mockFn.mockImplementation((a, b) => a + b);
console.log(mockFn(1, 2)); //3
```

- `mockImplementation(구현 코드)` 함수 이용해서 함수 재구현 가능

```js
mockFn("a");
mockFn(["b", "c"]);

expect(mockFn).toBeCalledTimes(2);
expect(mockFn).toBeCalledWith("a");
expect(mockFn).toBeCalledWith(["b", "c"]);
```

- 테스트 작성 시 가짜함수가 유용한 이유는 자신이 어떻게 호출되었는지 모두 기억함 

- 가짜 함수가 몇 번 호출되었고 인자로 무엇을 사용했는지 검증 가능

### **jest.spyOn(object, methodName)**

- 테스트 작성 시 어떤 객체에 속한 함수 구현을 가짜로 대체하지 않고 해당 함수의 호출 여부와 어떻게 호출되었는지만을 알아내야 할 때 사용

```js
const caculator = {
    add: (a, b) => a + b,
};
const spyFn = jest.spyOn(caculator, "add");
const result = caculator.add(2, 3);

expect(spyFn).toBeCalledTimes(1);
expect(spyFn).toBeCalledWith(2, 3);
expect(result).toBe(5);
```

- 함수 호출 횟수와 어떤 인자가 넘어가쓴지 검증 가능하지만 가짜 함수로 대체한 것은 아니므로 결과 값은 원래대로 나옴

