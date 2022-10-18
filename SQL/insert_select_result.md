# SELECT 결과를 INSERT 하기

## SELECT한 테이블의 모든 컬럼 저장

```sql
INSERT INTO 테이블1 
SELECT * FROM 테이블2
```

## SELECT한 테이블의 특정 컬럼 저장

```sql
INSERT INTO 테이블1(컬럼1, 컬럼2, 컬럼3)
SELECT 컬럼1, 컬럼2, 컬럼3
FROM 테이블2
```