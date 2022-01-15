# node-cron으로 Node.js 스케줄러 설정

## Cron

- 유닉스 계열 컴퓨터 운영 체제의 시간 기반 Job 스케줄러

- 작업을 고정된 시간, 날짜, 간격에 주기적으로 실행할 수 있도록 스케줄링하기 위해 사용

## node-cron

- Node.js용 모듈로 GNU crontab 기반으로 하는 JavaScript로 된 작업 스케줄러

- node-cron 모듈 사용하면 전체 crontab 구분 사용해서 Node.js 에서 스케줄링 작업 가능

- npm 사이트: https://www.npmjs.com/package/node-cron

- github 사이트: https://github.com/node-cron/node-cron

## node-cron 사용 방법

```
npm install --save node-cron
```

- npm 사용하여 node-cron 모듈 설치

```js
var cron = require('node-cron');

cron.schedule('* * * * *', () => {
  console.log('매 분마다 실행');
});
```

- '* * * * *' 부분에 원하는 실행 주기 설정을 하면 됨

    - 실행 주기 설정 

    ```
    # ┌────────────── second (optional) : 0 ~ 59
    # │ ┌──────────── minute : 0 ~ 59
    # │ │ ┌────────── hour : 0 ~ 23
    # │ │ │ ┌──────── day of month : 1 ~ 31
    # │ │ │ │ ┌────── month : 1 ~ 12 (or names)
    # │ │ │ │ │ ┌──── day of week : 0 ~ 7 (or names, 0 or 7 are sunday)
    # │ │ │ │ │ │
    # │ │ │ │ │ │
    # * * * * * *
    ```

    - 다중 값 주기 설정

    ```js
    cron.schedule('1,5,7 * * * *', () => {
        console.log('매 1,5,7분마다 실행');
    });
    ```

    - 범위 주기 설정

    ```js
    cron.schedule('1-7 * * * *', () => {
        console.log('매 1-7분마다 실행');
    });
    ```

    - '/' 사용해서 step 뛰어넘게 주기 설정

    ```js
    cron.schedule('1-10/2 * * * *', () => {
        console.log('매 2,4,6,8,10분마다 실행');
    });
    ```
    ```js
    cron.schedule('*/2 * * * *', () => {
        console.log('2분 지날 때마다 실행');
    });
    ```
    
    - 이름/약어 사용해서 주기 설정

    ```js
    cron.schedule('* * * January,September Sunday', () => {
        console.log('1월과 9월의 일요일마다 실행');
    });
    ```
    ```js
    cron.schedule('* * * Jan,Sep Sun', () => {
        console.log('1월과 9월의 일요일마다 실행');
    });
    ```
    
- console.log() 함수 대신 주기적으로 실행하고 싶은 함수를 넣으면 됨


