# moment.js

## 오늘 요일 구하는 법

```js
moment().day();
```
- 0=일, 1=월, 2=화, 3=수, 4=목, 5=금, 6=토

## 이번주/다음주 요일 구하는 법

```js
moment().day(0).format("YYYY-MM-DD"); //이번주 일요일 날짜
moment().day(1).format("YYYY-MM-DD"); //이번주 월요일 날짜 
moment().day(7).format("YYYY-MM-DD"); //다음주 일요일 날짜 (0+7)
moment().day(8).format("YYYY-MM-DD"); //다음주 월요일 날짜 (1+7)
```