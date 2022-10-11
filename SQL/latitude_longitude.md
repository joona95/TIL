# MySQL에서 위도, 경도 로 거리 계산하는 법

```sql
SELECT (6371 * acos(cos(radians(현재경도)) 
    * cos(radians(테이블명.latitude))
    * cos(radians(테이블명.longitude) - radians(현재위도))   
    + sin (radians(현재경도)) * sin(radians(테이블명.latitude)) 
    )) AS distance
    FROM 테이블명
    HAVING distance < 2
    ORDER BY distance
```

- 현재위치의 위경도와 비교해서 테이블 내 저장된 위경도를 비교해서 거리순서대로 정렬
- km 기준 비교
    - 2km 내에 있는 목록을 가져오는 조건으로 2는 원하는 km 로 변경 가능