# CI / CD

## CI (Continuous Integration) : 지속적인 통합

- 버그 수정이나 새로운 기능들이 메인 레파지토리에 주기적으로 빌드되고 테스트가 되어 merge 되는 것을 의미

- 1991 Grady Booch 에 의해 사용되다가 extreme programming에 채택됨

- 코드 변경사항을 주기적으로 빈번하게 merge해야 함

    - 서로 다른 개발자가 각각 코드를 수정하고 merge를 할 때 너무 많은 변화가 일어난 뒤에 merge하려고 하면 충돌이 너무 많이 일어나서 merge가 힘들 수 있음

    - 어떻게 작은 단위로 나누어 merge 하거나 사용자에게 배포할 수 있을지가 중요함

- 통합을 위한 단계 (빌드, 테스트, 머지) 의 자동화

    - 메인 레파지토리에 머지하기 전에 코드리뷰를 통해서 코드가 적절한지 확인 받고 merge가 되면, 자동으로 팀에서 만든 CI script를 통해서 추가된 코드와 함께 레파지토리가 빌드되고, 잘 빌드가 된다면 팀에서 작성한 테스트들도 스크립트 통해서 실행됨

    
- 장점: 

    - 개발 생산성 향상

    - 코드 결함이나 문제점 빠르게 발견 가능

    - 발견한 문제 빠르게 버그 수정 용이

    - 코드의 퀄리티 향상

<br>

## CD (Continuous Delivery/Deployment) : 지속적인 제공/배포

- CI를 통해서 빌드와 테스트 통과하고 머지가 되면 release를 위한 준비를 함

- 최종단계가 자동화되었는지에 따라 Delivery와 Deployment가 나누어짐

<br>

## CI / CD

- 어플리케이션 개발 단계부터 배포 때까지모든 단계들을 자동화하여 더 효율적이고 빠르게 사용자에게 빈번이 배포할 수 있도록 만드는 것

- 회사마다 팀마다 CI / CD 다를 수 있음

- Tools : Jenkins, Buildkite, GitLab CI/CD, GitHub Actions, Bitbucket Pipelines, circleci 등

    - Jenkins는 설치형으로 서비스가 돌아갈 서버에 직접 다운받아 사용. 해당 서버에서 CI/CD 설정할 수 있는 웹사이트 이용. 오픈소스.

    - Travis ci, circleci, Team city(Team city는 설치형으로도 사용 가능)는 기본적으로 클라우드로 제공된 컴퓨팅 공간에서 CI/CD 설정. 유료이거나 제한적으로 무료.

    - GitHub Actions, GitLab CI/CD, Bitbucket Pipelines 에서 아예 자체적으로 CI/CD 제공. 얼마까지는 공짜, 그 이상은 유료.

    - AWS에서 자체적으로 제공하는 CodePipeline

    - Netlify, Vercel 는 그 자체가 배포 자동화인 서비스

