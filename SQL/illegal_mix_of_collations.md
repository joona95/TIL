# [ERROR] Illegal mix of collations (utf8mb4_unicode_ci,IMPLICIT) and (utf8mb4_general_ci,IMPLICIT) for operation '='

- JOIN 조건에 있는 각 테이블 컬럼의 문자셋이 상이해서 발생하는 오류

- 해결 방법

    - 테이블 문자셋 확인

    ```sql
    SHOW VARIABLES WHERE Variable_name LIKE 'character_set_%' OR Variable_name LIKE 'collation%';
    ```

    - 테이블 문자셋 변경

    ```sql
    ALTER TABLE 테이블명 CONVERT TO CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
    ```