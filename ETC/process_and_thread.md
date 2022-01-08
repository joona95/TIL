# Process 와 Thread

## 프로세스 (Process)

- 프로세스는 운영체제로부터 자원을 할당받는 작업의 단위

### 멀티 프로세스 

- 하나의 프로그램을 여러 개의 프로세스로 구성하여 각 프로세스가 하나의 작업을 처리

- 하나의 프로세스가 잘못 되어도 프로그램 동작 가능

- 동시적, 병렬적, 혹은 둘의 혼합으로 이루어짐

    - 동시성(Concurrency)은 프로세스 하나가 여러 작업을 일부분씩 돌아가며 진행하는 것

        - 이렇게 CPU에서 여러 프로세스를 돌아가면서 작업 처리하는 과정이 context switching

        - 이 작업이 빠르게 이루어져서 사람들은 동시에 여러 작업이 되고 있다고 느낌

    - 병렬성(Parallelism)은 프로세스 하나에 코어 여러 개가 달려서 각각 작업을 진행

        - 듀얼코어, 쿼드코어, 옥타코어 등의 멀티코어 프로세서가 달린 컴퓨터에서 가능한 작업


## 스레드 (Thread)

- 스레드는 프로세스마다 할당 받는 자원을 이용하는 실행의 단위이고 프로세스 내에 여러 개 생성될 수 있음

### 멀티 스레드

- 프로그램을 여러 개의 쓰레드로 구성하고 각 쓰레드가 작업 처리

- 시스템 자원 소모 감소

- 실행 속도 향상

- 하나의 쓰레드의 오류로 전체 프로세스에 문제 발생 가능

- 공유되는 자원에 각각의 스레드가 접근할 경우 오류 발생 가능

- 디버깅이 어려움