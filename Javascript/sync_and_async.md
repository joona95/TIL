# 동기(Synchronous)와 비동기(Asynchronous)

## 동기식 (Synchronous) 과 비동기식 (Asynchronous)

### **1) 동기식 (Synchronous)**

- 작업 실행이 순차적으로 일어남

- 특정 코드의 연산이 끝날 때까지 다음 코드의 연산을 실행하지 않고 기다린 후 끝나면 다음 코드의 연산을 시작하는 방식

### **2) 비동기식 (Asynchronous)**

- 특정 코드의 연산이 끝날 때까지 코드의 실행 멈추지 않고 다음 코드를 먼저 실행하는 방식

- 나중에 시작된 작업이 먼저 끝나는 경우도 발생함

<br>

## JavaScript 비동기 처리

- JavaScript는 싱글 스레드로 한 번에 한 가지 일만 수행할 수 있음. 런타임에서 자체적으로 비동기 API 지원하지 않음.
    
    - Q. 싱글 스레드 인데 어떻게 비동기식 동작을 할 수 있을까?

        A. Javascript는 브라우저 환경에서 실행되기 때문에 비동기 작업들을 Web api에게 넘겨줌으로써, 해당 작업이 완료될때까지 다른 코드들을 실행할 수 있음
    - Web api 에서는 타이머 실행하거나, AJAX로 http 요청 보내거나, 파일 읽는 시간 소요하는 작업 수행

- 비동기식 동작

    ```js
    console.log("before waiting");
    setTimeout(function(){
        console.log("wait");
    }, 3000);
    console.log("after waiting");
    ```

    ```
    결과:
    before waiting
    after waiting
    wait
    ```

    1. 코드가 호출 스택에 쌓이고 실행되면 자바스크립트 엔진에서 비동기 작업을 Web api에게 줌
    
    2. Web api 에서 해당 작업 수행 후 콜백 함수를 이벤트 루프 통해서 콜백 큐에 줌
    
    3. 이벤트 루프는 콜스택에 쌓인 함수가 없을 때 콜백 큐에서 대기하던 콜백함수를 콜스택으로 넘겨줌

    4. 콜스택에 쌓인 콜백함수 실행하고 콜스택에서 제거

## JavaScript 비동기 처리 방법

### **1) 콜백 함수**

- JavaScript에서 비동기 처리하기 위해 제일 처음으로 등장했던 방식

- 콜백 함수는 특정 함수에 매개변수로 전달된 함수로, 보통 함수 선언 시 함수 타입의 파라미터를 맨 마지막에 하나 더 선언

- 콜백 함수는 어떤 이벤트가 발생했거나 특정 시점에 도달했을 때 시스템에서 호출하는 함수로, 함수를 전달받은 함수 안에서 호출됨

```js
function callprint(callback){
    console.log("callprint");
    callback();
}
callprint(function (){
    console.log("callback");
}) 
```
- 콜백함수를 사용하지 않으면 함수 실행이 끝나기 전에 다음 프로세스 진행하게 될 수 있음

```js
function something(callback){
    function something2(callback){
        function something3(callback){
            callback();
        }
    }
}
```

- 무한 콜백 발생할 수 있음

- 가독성이 떨어지고 실수 위험이 커짐

<br>

### **2) Promise**

- 기본적으로 콜백함수와 하는 일이 같음

- 작업이 끝난 후 실행할 함수를 제공하는 것이 아니라 promise 자체 메소드인 .then() 호출

```js
function something(value){ 
    return new Promise((resolve, reject) => {
        resolve(value);
    });
}
something("value")
  .then((value) => {
    console.log(value);
  })
  .catch((err) => {
    console.log(err);
  });
```

- 콜백함수 사용할 때보다 코드 작성과 이해가 쉬움

- Promise 사용 시 잘 이행되면 작업이 끝났음을 알려주는 resolve 메소드를 호출, 거부된다면 reject 메소드를 호출

- 작업이 실패한 경우 .catch()로 예외 처리

<br>

### **3) async / await

```js
async function something(){
    const a = await getValue("value");
    const b = await getValue(a);
    console.log(a, b);
}
something();
```

- Promise보다 더 쉽게 비동기 처리 가능

- async와 await 사용하려면 우선 사용할 함수 앞에 async 키워드 붙여서 선언

- 선언된 async 함수 안에서 await 키워드 사용 가능

- await은 함수의 작업이 끝나고 결과값 반환할 때까지 대기하여 결과 값이 리턴된다면 다음 작업으로 넘어감

- Promise를 리턴하므로 Promise가 지원하는 메소드 사용 가능

- .catch() 나 try-catch 이용하여 예외 처리