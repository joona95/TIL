# 웹 성능 최적화 테스트 (WebPageTest, Lighthouse)

## WebPageTest

### WebPageTest란

- 웹페이지의 성능을 진단하는 방법을 알려주는 페이지

### 성능 정보 

- Load Time: 사용자가 페이지 탐색 시작하고 완료시점까지의 시간 (모든 페이지 로딩시간)

- First Byte: 백엔드 시간으로 서버가 사용자를 위해 페이지 만드는데 소비한 시간

    - 일반적으로 500ms 이하 속도가 나오도록 최적화 권장

    - SEO 측면에서도 중요

- Keep-alive Enabled: Keep-alive 활성화하면 일정시간 동안 접속 끊지 않고 다음 접속 기다림

- Compress Transfer: 압축 전송으로 콘텐츠를 압축하면 트래픽 자원 아끼고 사이트 속도 향상 가능

- Compress Images: 이미지는 많은 트래픽 유발하며 로딩 지연 발생시킴

- Cache static content: 브라우저 캐시가 적용되지 않은 리소스들의 목록 볼 수 있음

- Effective use of CDN: CDN 이용하면 전 세계 사용자들에게 빠르게 웹 페이지 전달 가능

- Start Render: 웹페이지 화면에 무엇인가 표시된 첫 시점

- Speed Index: 사용자가 볼 수 있는 컨텐츠를 렌더링하는데 걸린 속도 (낮을수록 좋음)

- Document Complete: 페이지 로드 수집 정보 (js 및 내부프로그램 제외)

- Fully Loaded: 페이지 로드 수집 정보 (js 및 내부프로그램 포함)

## Lighthouse

### Lighthouse란

- 웹페이지의 성능 지표를 비롯한 항목들을 검사하고 개선할 수 있도록 도움을 주는 자동화 도구

- 웹 성능, 접근성, PWA, SEO 등 여러 항목 분석하고 메트릭스 점수 알려줌

### 성능 정보

- Performance: 웹페이지가 얼마나 빠르게 로딩되는지

- Accessibility: 사용자가 얼마나 쉽게 웹 페이지의 기능들 사용할 수 있는지

- Best Practice: 웹 페이지 제작시 일반적인 기능들이 얼마나 적용되었는지

- SEO: 검색 엔진에 의해 검색될 수 있도록 웹페이지 구조가 만들어졌는지

- Progressive Web App: PWA 관점에서 확인