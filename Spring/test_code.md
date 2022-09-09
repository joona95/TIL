# 테스트 코드

## 테스트 코드 작성 프레임워크: JUnit

- 테스트 시 자바의 main 메서드 통해서 실행하거나 웹 애플리케이션의 컨트롤러 통해서 해당 기능 실행 가능
    - 단점:
        - 준비하고 실행하는데 오래 걸림
        - 반복 실행하기 어려움
        - 여러 테스트 한번에 실행하기 어려움
- 이를 해결하기 위해 자바는 JUnit 프레임워크로 테스트 실행

## 테스트 코드 작성

- @Test : 테스트 메서드 위에 적으면 테스트 실행 가능
- org.junit.jupiter.api.Assertions : 성공하지 않으면 테스트 실패처리 하기 위해서 사용
    - Assertions.assertEquals(기대하는값, 실제값)
- org.assertj.core.api.Assertions : junit 의 Assertions 보다 좀 더 편하게 사용 가능
    - Assertions.assertThat(실제값).isEqualTo(기대하는 값) : asseertEquals는 기대값과 실제값 위치를 헷갈릴 수 있는데 더 명확함
- 테스트 순서는 보장되지 않음. 테스트는 서로 의존관계 없이 설계가 돼야 함
- @AfterEach : 테스트가 하나 끝날 때 마다 실행되는 함수
    - 테스트 끝날 때마다 공용 데이터는 클리어해줘야 함
- TDD (테스트 주도 개발) : 테스트 코드를 먼저 작성해놓고 코드를 작성하는 것
