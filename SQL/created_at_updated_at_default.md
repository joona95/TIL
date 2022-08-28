# createdAt, updatedAt 컬럼 생성 시 날짜 기본값 자동 설정

```sql
CREATE TABLE 테이블명 (
    ...
    createdAt timestamp default CURRENT_TIMESTAMP,
    updatedAt timestamp default CURRENT_TIMESTAMP,
    ...
)
```