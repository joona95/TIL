# 화살표 함수(Arrow Function)

## 화살표 함수란

- 기존 함수 표현식에 비해 간결한 표현으로 사용 가능한 함수

```js
//기존 함수
function doSomething() { ... }

//화살표 함수
const doSomething = () => { ... };
```

## 화살표 함수와 일반 함수의 차이

### **this**

```js
//일반 함수
function doSomething() {
    this.name = "abc";
    return {
        name: "def";
        print: function () {
            console.log(this.name);
        }
    }
}
const fun = new doSomething();
fun.print(); // "def"
```

- 함수 선언 시 this에 바인딩할 객체가 정적으로 결정되지 않음

- 함수 호출 시 함수가 어떻게 호출되었는지에 따라 this에 바인딩할 객체가 동적으로 결정됨

```js
//화살표 함수
function doSomething() {
    this.name = "abc";
    return {
        name: "def";
        print: () => {
            console.log(this.name);
        }
    }
}
const fun = new doSomething();
fun.print(); // "abc"
```
- 화살표 함수는 함수 선언 시 this에 바인딩할 객체가 정적으로 결정됨

- 화살표 함수의 this는 언제나 상위 스코프의 this를 가리킴

### **생성자 함수 사용 가능 여부**

```js
//일반 함수
function doSomething() {
    console.log("hello");
}
const fun = new doSomething(); // 가능
```

- 일반 함수는 생성자 함수로 사용 가능

```js
//화살표 함수
const doSomething = () => {
    console.log("hello");
};
const fun = new doSomething(); // 불가능(Error 발생)
```

- 화살표 함수는 생성자 함수 사용 불가능

### **arguments 사용 가능 여부**

```js
function doSomething() {
    console.log(arguments);
}
doSomething(1); //가능
```

- 일반 함수는 함수 실행 시 암묵적으로 arguments 벼수 전달하여 사용 가능

```js
const doSomething = () => {
    console.log(arguments);
};
doSomething(1); //불가능(Error 발생)
```

- 화살표 함수는 arguments 변수 전달되지 않음

