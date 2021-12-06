# Visual Studio Code C / C++ 세팅


## [MAC OS]

<br>

## 1. 'C/C++' Extension 설치

<img width="1031" alt="스크린샷 2021-12-06 오후 11 04 11" src="https://user-images.githubusercontent.com/39457533/144862780-d1b1eb7e-8d12-483f-b03b-42d862f14c11.png">

<br>
<br>

## 2. 'Code Runner' Extension 설치

<img width="1042" alt="스크린샷 2021-12-06 오후 11 05 10" src="https://user-images.githubusercontent.com/39457533/144862796-b57ae435-2013-4f64-8b1c-899d2d07cdec.png">

<br>
<br>

## 3. 'Code Runner' 의 Extension settings 클릭

<img width="448" alt="스크린샷 2021-12-06 오후 11 08 04" src="https://user-images.githubusercontent.com/39457533/144862803-1709af04-0e04-44b8-b89f-086f240f4e7d.png">

<br>
<br>

## 4. 'Run In Terminal' 에 체크

<img width="758" alt="스크린샷 2021-12-06 오후 11 08 27" src="https://user-images.githubusercontent.com/39457533/144862806-90fd25b3-8829-4350-8b08-39b3edf432df.png">

<br>
<br>

## 5. 'Executor Map' 에 'Edit in settings.json' 클릭

<img width="676" alt="스크린샷 2021-12-06 오후 11 08 56" src="https://user-images.githubusercontent.com/39457533/144862810-d56d49ad-b484-4c24-9f65-2d588662b9c8.png">

<br>
<br>

## 6. 'settings.json' 안의 'code-runner.executorMap' 에 c/cpp 설정 추가

<img width="834" alt="스크린샷 2021-12-06 오후 11 10 12" src="https://user-images.githubusercontent.com/39457533/144862815-027ab45c-24d6-467d-bc11-7cff89fd9299.png">

- clang++ : g++ 처럼 c/c++ 파일 빌드 툴. mac에 거의 기본으로 깔려있음. 터미널에 'g++ -v' 라고 치면 clang 깔려있다고 뜨는 것을 볼 수 있음.

    <img width="563" alt="스크린샷 2021-12-06 오후 11 39 01" src="https://user-images.githubusercontent.com/39457533/144865415-402d8919-7254-446c-9b1c-1d5703ff4004.png">

- std=c++17 로 버전 설정 추가해줘야 함.

<br>
<br>

## 7. cpp 파일 생성하고 오른쪽 상단의 실행 버튼 누른 후 터미널에서 실행 결과 확인

<img width="1052" alt="스크린샷 2021-12-06 오후 11 13 14" src="https://user-images.githubusercontent.com/39457533/144862817-77d10c8b-939b-4893-866e-b11be94e841b.png">
