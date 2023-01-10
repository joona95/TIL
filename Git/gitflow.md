# Git Flow

## Git Flow 란?

![99CD994C5E69CCF223](https://user-images.githubusercontent.com/39457533/211559714-9f261d1c-4c65-4a2c-88c8-cd31f5d6c8e6.png)


- 여러 명이 개발할 때 소스 형상관리를 해주고 branch를 전략적으로 관리하게 도와주는 전략

- branch 종류

    - master: 기준이 되는 브랜치로 제품 배포 브랜치

    - develop: 개발 브랜치로 개발자들이 각자 작업한 기능들을 merge하는 브랜치
    
    - feature: 단위 기능 개발하는 브랜치로 기능 개발 완료되면 develop 브랜치에 merge함
        
        - develop 브랜치에 merge 되면 바로 삭제

    - release: 배포를 위해 main 브랜치로 보내기 전에 QA를 하기 위한 브랜치

    - hotfix: main 브랜치로 배포를 했는데 버그가 생겼을 때 긴급 수정하는 브랜치

## Source Tree 에서 Git Fow 사용하는 법

1. 소스트리 프로젝트를 열어서 프로젝트명이 있는 곳에서 마우스 오른쪽 버튼 눌러서 '도구 막대 사용자화' 클릭

<img width="149" alt="스크린샷 2023-01-10 오후 10 11 57" src="https://user-images.githubusercontent.com/39457533/211562221-c435b8fd-70d9-4a74-8919-3f75a34472ae.png">

2. '깃 플로우' 버튼을 도구 막대로 드래그

<img width="665" alt="스크린샷 2023-01-10 오후 10 14 27" src="https://user-images.githubusercontent.com/39457533/211562278-29473d2c-f4cf-43f6-9046-b2db69b9d642.png">

3. '깃 플로우' 버튼이 도구 막대에 생성됨

<img width="657" alt="스크린샷 2023-01-10 오후 10 14 39" src="https://user-images.githubusercontent.com/39457533/211562330-74c2d2d8-7573-4abf-a3ab-aea2382ff251.png">

4. '깃 플로우' 버튼을 눌러서 기본 브랜치명 설정 후 확인 버튼 클릭

<img width="428" alt="스크린샷 2023-01-10 오후 10 15 33" src="https://user-images.githubusercontent.com/39457533/211562407-f02a76ac-e267-43df-9596-8d47af3dcd87.png">

5. 이후 다시 '깃 플로우' 버튼 클릭 시 쉽게 깃 플로우 작업 가능

<img width="219" alt="스크린샷 2023-01-10 오후 10 15 52" src="https://user-images.githubusercontent.com/39457533/211562462-327822cc-23a0-4c45-bbd9-4161a7c593b6.png">

