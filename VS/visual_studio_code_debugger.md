# Visual Studio Code Debugger

## 0. 들어가기전
- 디버그(디버깅) : 프로그래밍 과정 중 발생한 버그(오류나 비정상적인 연산)를 찾아서 수정하는 것
- 기존에는 console에 log 찍어보는 형식으로 테스트

<br>

## 1. 사용 방법

<br>

### 1) 코드 작성 후 컴파일을 위해 tasks.json 수정

<br>

<img width="266" alt="스크린샷 2021-12-08 오후 5 10 13" src="https://user-images.githubusercontent.com/39457533/145172791-03054614-d58d-428f-b6ff-06e233e66ad5.png">

- Terminal > Configure Default Build Task... 선택하면 tasks.json 생성

<br>

<img width="645" alt="스크린샷 2021-12-08 오후 5 06 23" src="https://user-images.githubusercontent.com/39457533/145172775-ef165463-72b9-441e-94fb-0db8fc3458e1.png">

- tasks.json 설정을 원하는대로 설정 (사용 언어에 따라 검색)
- 예시는 c++

<br>

### 2) 코드 빌드 수행

<br>

<img width="266" alt="스크린샷 2021-12-08 오후 5 10 13" src="https://user-images.githubusercontent.com/39457533/145172791-03054614-d58d-428f-b6ff-06e233e66ad5.png">

- Terminal > Run Build Task... 수행

<br>

### 3) 디버깅을 위해 launch.json 수정

<br>

<img width="273" alt="스크린샷 2021-12-08 오후 5 23 24" src="https://user-images.githubusercontent.com/39457533/145173962-4b8ffa0d-43be-4d5e-a2b1-77e93b7880b5.png">

- Run > Add Configuration... 클릭

<br>

<img width="793" alt="스크린샷 2021-12-08 오후 4 43 39" src="https://user-images.githubusercontent.com/39457533/145172758-7cee901d-bd07-45d1-9308-8f8d2d6255fb.png">

- environment에 맞는 기본 디버거 선택
- c++ 는 C++ (GDB/LLDB)

<br>

<img width="713" alt="스크린샷 2021-12-08 오후 5 06 31" src="https://user-images.githubusercontent.com/39457533/145172776-5e6e0849-8b04-4b5a-8af2-abdb8660b210.png">

- 사용 언어/환경에 맞게 lauch.json 수정
- stopAtEntry 를 true 로 바꿔줌 (멈춰서 확인할 수 있는 기능)

<br>

### 4) 디버깅 시작

<br>

<img width="273" alt="스크린샷 2021-12-08 오후 5 23 24" src="https://user-images.githubusercontent.com/39457533/145173962-4b8ffa0d-43be-4d5e-a2b1-77e93b7880b5.png">

- Run > Start Debugging 선택

<br>

### 5) 상황에 맞게 디버깅 활용

<br>

<img width="445" alt="스크린샷 2021-12-08 오후 5 06 58" src="https://user-images.githubusercontent.com/39457533/145172778-d6c95a0e-dbfa-46ca-a04f-25fef71a30b2.png">

- 빨간점은 breakpoint 로 멈춰서 확인하고 싶은 위치 설정

<br>

<img width="181" alt="스크린샷 2021-12-08 오후 5 07 05" src="https://user-images.githubusercontent.com/39457533/145172780-377e9dd5-0553-419b-b160-008df29edd5d.png">

- 다음 breakpoint로 넘어가기, 다음줄실행, 함수안으로 들어가기, 함수 밖으로 나오기, 디버깅 시작, 디버깅 멈춤

<br>

<img width="182" alt="스크린샷 2021-12-08 오후 5 07 24" src="https://user-images.githubusercontent.com/39457533/145172781-b86fc4b6-dbe5-4666-a3ff-d12124b6ee0b.png">

- 변수 값이 변하는 걸 볼 수 있음

<br>

<img width="183" alt="스크린샷 2021-12-08 오후 5 07 49" src="https://user-images.githubusercontent.com/39457533/145172782-25ead31c-ae1e-434f-95de-590bff857ad2.png">

- variable 표시되는 변수 중 더 중요하게 보고 싶은 변수 설정
- 어떤 변수가 어떤 조건일 때 값도 살펴볼 수 있음

<br>

<img width="300" alt="스크린샷 2021-12-08 오후 5 09 04" src="https://user-images.githubusercontent.com/39457533/145172785-6aeb4b0b-dc9a-4339-bbaf-bdfd0ce99db0.png">

- breakpoint 만들고 싶은 위치에서 오른쪽 마우스 클릭 후 add conditional breakpoint 클릭
- 어떤 위치에서 어떤 조건일 때 break 하고 싶을 때 사용