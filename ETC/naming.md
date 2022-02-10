# 변수 이름 네이밍

- 이해하기 쉬운 이름

    - 이해하기 어려운 것보다 차라리 긴 이름이 나음

    - 임의로 줄여쓰지 않기

    - 사용하는 스코프에 따라 짧은 스코프는 관례적으로 짧은 이름 사용할 수 있지만(ex. for 문에서 i 사용), 전역 변수/클래스/함수 등 긴 스코프 사용하는 경우 최대한 명시적으로 이해하기 쉬운 이름 사용

- 정확한 이름
    
    - 이름이 길어지더라도 하는 일을 정확하게 설명해야 함

    - 특정 함수는 한 가지 일을 해야 한다는 단일 책임 원칙 위반이 더 쉽게 드러나서 구조 개선에 도움이 됨

- 의도를 설명하는 이름

    - 구현이 아니라 의도를 드러내는 게 좋음

    - 의도 함수가 그저 구현 함수를 래핑하는 함수일 때 함수 하나 추가하는 비용보다 직관적인 코드로 얻는 이득이 더 큼

- 주석이 불필요한 이름

    - 주석이 필요 없는 명확한 코드를 만드는 게 코드 품질 향상에 좋음

- 예상되는 이름

    - 예상되는 곳에 예상되는 이름이 있어야 함

    - ex. Get&Set, Get&Release, Create&Destroy, Create&Delete, Load&Unload, Map&Unmap, Edit/Modify보다는 Update

    - 이름을 보고 동작을 예상할 수 있으면 코드 이해하기 좋음