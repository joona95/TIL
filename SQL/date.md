# MySQL 날짜 관련 함수

## DATE_ADD(date, INTERVAL 계산수 계산형식)

- 계산형식 : MONTH, DAT, HOUR, MINUTE, SECOND
- 계산수 : 뺄 때는 마이너스로 
- 예시 :

계산형식 | 예
-|-
월 | DATE_ADD('2022-08-08 08:00:00, INTERVAL 1 MONTH)
일 | DATE_ADD('2022-08-08 08:00:00, INTERVAL -1 DAY)
시간 | DATE_ADD('2022-08-08 08:00:00, INTERVAL 1 HOUR)
분 | DATE_ADD('2022-08-08 08:00:00, INTERVAL -1 MINUTE)
초 | DATE_ADD('2022-08-08 08:00:00, INTERVAL 1 SECOND)

## DATE_SUB(date, INTERVAL 계산수 계산형식)

- 계산형식 : MONTH, DAT, HOUR, MINUTE, SECOND
- 계산수 : 빼고 싶은 숫자
- DATE_ADD와 같은 방식으로 이용