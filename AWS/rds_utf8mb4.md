# AWS RDS 이모지 입력 가능하도록 DB 파라미터 변경

1. AWS RDS 콘솔 파라미터 그룹 수정

```
character_set_client = utf8mb4
character_set_connection = utf8mb4
character_set_database = utf8mb4
character_set_filesystem = binary
character_set_results = utf8mb4
character_set_server = utf8mb4
collation_connection = utf8mb4_unicode_ci
collation_server = utf8mb4_unicode_ci
```

- 파라미터 그룹에서 설정 변경

    - 이미 구동중인 파라미터인 경우 수정 시 오류 발생하므로 새로운 파라미터 그룹 만든 후 즉시 적용

    - 수정된 후 재부팅을 하면 적용됨

    - 적용 확인하기

        ```
        show variables where variable_name like 'c%';
        ```

2. 이모지가 들어갈 테이블 설정 변경

```
alter table 테이블명 COLLATE='utf8mb4_unicode_ci', convert to charset utf8mb4;
```