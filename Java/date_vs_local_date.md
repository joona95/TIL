# Date와 LocalDate의 차이점

- Java8 이전에는 자바 기본 날짜 타입인 Date 클래스 혹은 Calendar 클래스를 주로 사용

- Date 클래스 / Calendar 클래스 문제점

    - 변하지 않는 객체가 아님

    - Calendar.OCTOBER 숫자 값이 9로 설정되어 헷갈림

- Date 클래스나 Calendar 클래스의 문제를 피하기 위해 오픈소스 주로 활용 많이 함

- Java8부터 LocalDate 와 LocalTime, LocalDateTime, ZonedDateTime 이 등장하면서 기존 불편 사항을 많이 해소해줌