# Vue 의 .env variable이 작동하지 않는 문제

## 문제

```
TOKEN=abcde
```

- .env 파일 내에 토큰 variable을 추가했으나 `console.log(process.env.TOKEN)`으로 확인 시 undefined 가 계속 뜨는 문제 발생

<br>

## 해결방안

```
VUE_APP_TOKEN=abcde
```

> Note that only NODE_ENV, BASE_URL, and variables that start with VUE_APP\_ will be statically embedded into the client bundle with webpack.DefinePlugin. It is to avoid accidentally exposing a private key on the machine that could have the same name.

- variable 앞에 'VUE_APP\_' 을 붙이니 해결됨
