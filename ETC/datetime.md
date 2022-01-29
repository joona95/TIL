# 날짜와 시간

## 타임스탬프 (timestamp)

- 컴퓨터가 시간을 표현하기 위해 사용하는 값

- 1970년 1월 1일 0시 0분 0초부터 1초 단위로 증가

- 1초보다 작은 시간인 밀리초는 타임스탬프의 소수점 자릿값으로 측정 가능 (모든 컴퓨터가 1초 미만 값 측정 지원하는 것은 아님)

- 타임스탬프로는 컴퓨터가 직접 계산하는 단조 시간과 우리가 사는 세계의 실제 시간으로 두 종류 표현 가능

## 단조 시간 (monotonic time)

- 운영체제 또는 CPU 같은 하드웨어에서 직접 계산하는 시간

- 실제 세계 시간과는 다르지만 운영체제 시작 이후 시점부터 바뀌지 않음

- 사용자가 직접 값 변경 가능

- 외부 요인에 의해 바뀌지 않으므로 불벼성 보장하는 시간 값 필요할 때 유용

    - 두 작업 사이에 걸린 시간 측정할 때, 일정한 시간 간격마다 수행해야 하는 작업 시간을 측정할 때 사용됨

## 실제 시간 (real time)

- 실제 시간도 컴퓨터가 직접 계산하지만 주기적으로 시간 서버로부터 값을 가져와 동기화함

- 언제든지 시간 바뀔 수 있으므로 단조 시간처럼 시간 차이를 구하거나 일정한 간격 측정하기 위해서 사용 불가

- 특정 날짜에 반드시 실행해야 하는 작업할 때, 한 달이 넘는 주기(매달 1일)로 수행되는 작업할 때, 실제 시간 표기할 때 사용됨

- 외부 환경(사용자, 시스템)에 의해 언제든 바뀔 수 있으므로 예상하지 못한 곳에서 시간 값 바뀌는 경우 끝나야 할 작업 끝나지 않거나 끝나지 말아야 할 작업이 끝날 수 있음

## 타임 존 (time zone)

- 혐정 세계시(UTC = Coordinated Universal Time)는 표준시

    - 그리니치 평균시(GMT = Greenwich Mean Time)은 여러 타임 존 중 하나일 뿐응로 UTC로 표기하는 게 옳음

- 실제 시간 사용 시에는 타임 존 설정 확인 필요

- 나라마다 사용하는 표준 시간이 다름

- 타임 존은 운영체제 또는 모바일 기기 설정에 의해 바뀔 수 있음

- 여러 서버 사용 시에는 서버 간 시간 차이로 오동작 방지하기 위해서 전체 서비스 구성하는 여러 프로그램이나 서버를 동일한 타임 존으로 설정해야 함

    - 서로 다른 두 서버의 로그 함께 보기 어려움

    - 여러 서버가 특정 시간에 동시에 수행하는 작업에 문제 발생 가능