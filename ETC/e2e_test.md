# E2E(End-to-End) 테스트

## E2E 테스트란?

- 사용자 중심으로 처음부터 끝까지 어플리케이션 흐름을 테스트하는 소프트웨어 테스트 방법

- 실제 사용자 시나리오를 시뮬레이션하고 어플리케이션 구성 요소의 통합 및 데이터 무결성을 검증하는 것

- 단위 테스트를 진행하더라도 E2E 테스트를 통해 최종 배포 전 어플리케이션 주요 기능들이 문제 없이 작동하는지 검증할 수 있음

- 소프트웨어가 요구사항(인수 조건)대로 잘 작동하는지에 대한 검증으로 소프트웨어 내부 코드에 관심 가지지 않는 블랙박스 테스트인 인수 테스트와 거의 동일한 의미로 쓰이는 듯 함

## E2E 테스트 구축 방법

- 프레임워크 및 라이브러리에 따라 지원하는 E2E 테스트 도구가 있음

    - 웹 환경에서는 대부분 selenium, testCafe, cypress, nightwatch 등을 많이 사용함

- Java Spring 테스트 

    - Java Spring 의 인수 테스트는 RestAssured, MockMvc 를 통해 주로 이루어진다고 함

    - Mock 또한 E2E 테스트로 보는 것인지 여러 곳마다 다르게 적혀 있어서 헷갈림

    - RestAssured

        - REST Assured Java 라이브러리 사용하여 애플리케이션의 HTTP EndPoint에 초점을 맞춘 테스트 도구

        - 어플리케이션으로 오는 요청과 응답에 대해서 테스트 가능
        
        - End-to-End Test (전 구간 테스트)에 사용됨

        - 실제 웹 환경을 사용하여 테스트

        - @SpringBootTest 사용하여 수행하여 느림

        - Spring test가 아니므로 이용하기 위해서는 외부 의존성 추가 필요

        ```
        dependencies {
            testImplementation 'io.rest-assured:rest-assured:3.3.0'
        }
        ```

    - MockMvc 

        - 웹 애플리케이션을 애플리케이션 서버에 배포하지 않고 스프링 MVC 동작 재현 가능

        - 대부분 Controller Layer Unit Test에 사용됨

        - 가짜 객체 Mock 사용

        - @WebMvcTest 사용하여 수행 가능하여 빠름 (@SpringBootTest도 사용 가능)

        - Spring Framework Test 클래스 중 하나로 Spring test 의종성이 추가되어 있는 경우 별도의 의존성 추가 필요 없음

- 백엔드에서는 E2E 테스트를 인수 테스트와 거의 비슷하게 보고 있는 듯 하고, 일반적으로 E2E 테스트는 웹 클라이언트에서 백엔드 요청이 가고 응답이 클라이언트에 오는 전 과정 테스트로 프론트엔드에서 이루어지는 걸 말하는 것 같음

