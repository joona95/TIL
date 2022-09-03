# createdAt, updatedAt 컬럼 생성 시 날짜 기본값 자동 설정


## 테이블 생성 시 생성일, 수정일 기본값 자동 설정

```sql
CREATE TABLE 테이블명 (
    ...
    createdAt TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updatedAt TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    ...
)
```

- TIMESTAMP, DATETIME 둘 다 적용 가능



## 이미 존재하는 생성일, 수정일 컬럼에 기본값 적용

```sql
ALTER TABLE 테이블명 MODIFY createdAt DATETIME DEFAULT CURRENT_TIMESTAMP;
ALTER TABLE 테이블명 MODIFY updatedAt DATETIME DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP; 
```