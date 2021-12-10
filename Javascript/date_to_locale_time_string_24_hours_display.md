# Date.toLocaleTimeString() 함수의 시간 표시 포맷

## 0. 문제

<br>

####  **<기존 코드>**

```ts
console.log(event.toLocaleTimeString('en', { timeZone: 'Asia/Seoul', hour: '2-digit', minute: '2-digit', hour12: false }));
```

- 표현하고 싶었던 시각은 '00:00' 이었으나 '24:00' 으로 표시되는 문제 발생

<br>
<br>

## 1. 해결

<br>

```ts
// US English uses 12-hour time with AM/PM
console.log(date.toLocaleTimeString('en-US'));
// → "7:00:00 PM"

// sometimes even the US needs 24-hour time
console.log(date.toLocaleTimeString('en-US', { hour12: false }));
// → "19:00:00"
```
- 원래 사용 중이던 'en' 은 12시간 기준으로 'en-US'에 해당되는 것. 

- 'hour12: false'가 추가되었으나 '01:00 ~ 24:00' 기준으로 표시됨.

<br>

```ts
// British English uses 24-hour time without AM/PM
console.log(date.toLocaleTimeString('en-GB'));
// → "03:00:00"
```

- 'en-GB' 설정을 하면 기본이 24시간 기준. 'hour12: false' 설정은 필요 없음. 

- 확인해보니 '00:00 ~ 23:00' 기준으로 표시됨.

<br>

#### **<변경 코드>**

```ts
console.log(event.toLocaleTimeString('en-GB', { timeZone: 'Asia/Seoul', hour: '2-digit', minute: '2-digit' }));
```

<br>
<br>

참고 링크 : https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/toLocaleTimeString