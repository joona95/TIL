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
  console.log('running a task every minute');
});
```

- '* * * * *' 부분에 원하는 실행 주기 설정을 하면 됨

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

    - 여러 값들 선택, 범위 선택, 이름 사용 등 더 다양한 이용하고 싶으면 [github 문서 확인](https://github.com/node-cron/node-cron)

- console.log() 함수 대신 주기적으로 실행하고 싶은 함수를 넣으면 됨


