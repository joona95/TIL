# 포스트맨에서 스크립트 작성하기

- 포스트맨은 Node.js 기반의 런타임 포함하여 Request와 Collection에 동적으로 동작 추가도 가능

    - Pre-request Script: 요청이 서버로 가기 전에 Request 헤더에 key 추가하거나 URL 매개변수에 문자열 추가할 때 사용

        - 공식 문서 참고: https://learning.postman.com/docs/sending-requests/variables/#defining-variables-in-scripts

    - Test Script: .test 함수 사용해서 요청이 서버로 간 이후 응답이 반환된 후에 실행하며 .response, .expect 객체 등에 접근 가능

        - 공식 문서 참고: https://learning.postman.com/docs/writing-scripts/intro-to-scripts/

## 문제사항

- 포스트맨에서 로그인한 후 얻은 access token, refresh token 을 헤더에 매번 추가하여 API 호출을 해야 했음

- 그런데 일정 시간이 지나면 access token, refresh token 이 만료가 돼서 새로 로그인 API 호출 통해서 얻은 걸 복사 붙여넣기 반복해야 했음

- 그러다보니 복사 붙여넣기가 잘못된 경우 호출이 안되는데 원인을 찾기 어려웠고 비효율적인 문제가 있었음

## 해결

- 포스트맨에서 제공하는 스크립트를 통해서 쉽게 진행 가능

- 로그인 API 포스트맨 리퀘스트창에서 Tests 항목에서 API 호출로 받은 response의 헤더에서 받은 access token 명칭과 refresh token 명칭을 찾아서 global variable로 세팅해줌

```
pm.globals.set("jwt_access_token", pm.response.headers.get("access-token"));
pm.globals.set("jwt_refresh_token", pm.response.headers.get("refresh-token"));
```

- 이후 access token과 refresh token이 필요한 다른 API 포스트맨 리퀘스트창에서 Headers 항목에 세팅한 명칭을 입력해주면 됨

```
{{jwt_access_token}}
{{jwt_refresh_token}}
```

- 스크립트를 활용하면 Postman을 더 효과적으로 쓸 수 있다는 것을 알게됨
