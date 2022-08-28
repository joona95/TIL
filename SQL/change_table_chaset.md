# MySQL 테이블에 데이터로 한글 입력

- 한글 데이터 추가 시 오류 발생

```
ERROR 1366 (HY000): Incorrect string value: '\xEC\x9D\xB4\xEB\xAF\xB8...' for column 'name' at row 1
```

- 해결 방안

```sql
ALTER TABLE 테이블명 convert to charset utf8;
```
