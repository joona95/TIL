# varchar ID값 채번



```sql
INSERT INTO 테이블명 (
    id,
    ...
) VALUES (
    (SELECT CONCAT('Y', LPAD(SUBSTR(MAX(id), 2, 8) + 1, 8, '0')) FROM 테이블명 A),
    ...
)
```

- INSERT 할 때 id 값을 예를 들어 'Y00000001' 에서 순서대로 올라가는 채번을 하고 싶을 때

- MAX(id)

    - 가장 높은 아이디값을 가져오기

- SUBSTR(대상문자열, 시작위치, 길이): 문자열을 특정 위치부터 자르는 함수

    - 앞에 붙는 문자열 (ex: 'Y') 를 제외하고 값을 가져와서 +1 해주기

- LPAD(문자열 or 열이름, 만들어질 자릿수, 채워질 문자): 특정 문자로 자릿수 채우기

    - LPAD는 왼쪽부터, RPAD는 오른쪽부터 특정문자로 자릿수 채우는 함수

    - 기존 값에서 +1된 값을 자리 수 맞춰서 '0' 채워주기

- CONCAT(문자열, 문자열, ...) : 문자열 텍스트 결합해주는 함수

    - 앞에 오는 문자열 (ex: 'Y')를 앞에 붙여주기

- FROM 테이블명 A

    - A 라는 별칭을 붙여주지 않으면 오류 발생

    ```
    SQL Error [1093] [HY000]: (conn=20) Table '테이블명' is specified twice, both as a target for 'INSERT' and as a separate source for data
    ```

