# @Transactional

## 트랜잭션의 성질

- 원자성(Atomicity) : 한 트랜잭션 내에서 실행한 작업들은 하나로 간주하여 모두 성공하거나 모두 실패한다

- 일관성(Consistency) : 트랜잭션은 일관성 있는 데이터베이스 상태를 유지한다

- 격리성(Isolation) : 동시에 실행되는 트랜잭션들이 서로 영향을 미치지 않도록 격리한다

- 지속성(Durability) : 트랜잭션을 성공적으로 마치면 결과가 항상 저장되어야 한다

## 스프링에서 트랜잭션 처리

- 스프링에서 어노테이션 방식으로 @Transactional 선언하여 트랜잭션 처리 지원

- 선언적 트랜잭션

## @Transactional 옵션

```
@Transactional(isolation=Isolation.DEFAULT)
``` 

- isolation : 트랜잭션에서 일관성 없는 데이터 허용 수준 설정 옵션

    - DEFAULT : 기본 격리 수준. DB의 Isolation Level을 따름.

    - READ_UNCOMMITED (level 0) : 커밋되지 않은 데이터에 대한 읽기를 허용. Dirty Read 발생 가능.

    - READ_COMMITED (level 1) : 커밋된 데이터에 대한 읽기 허용. Dirty Read 방지.

    - REPEATABLE_READ (level 2) : 동일 필드에 대해 다중 접근 시 모두 동일한 결과를 보장. 트랜잭션 완료될 때까지 다른 사용자는 그 영역에 해당되는 데이터 수정 불가. Non-Repeatable Read 방지.

    - SERIALIZABLE (level 3) : 가장 높은 격리. 성능 저하의 우려 있음. 트랜잭션 완료시까지 그 영역에 해당되는 데이터에 대한 수정 및 입력 불가. Phantom Read 방지.

    - 격리 수준에 따른 문제

        - Dirty Read : 트랜잭션 1이 수정중인 데이터를 트랜잭션 2가 읽을 수 있음

        - Non-repeatable Read : 트랜잭션 1이 회원 1 조회 중에 트랜잭션 2가 회원 1 수정하고 커밋하면, 트랜잭션 1이 다시 회원 1 조회하면 수정된 데이터가 조회돼서 이전 정보를 다시 조회 불가. 반복해서 같은 데이터를 읽을 수 없는 경우.

        - Phantom Read : 트랜잭션 1이 90점 이상 학생 조회 시 트랜잭션 2가 100점 학생을 추가하고 커밋하면 트랜잭션 1이 다시 90점 이상 학생 조회 시 한 명이 추가로 조회됨. 반복 조회 시 결과가 달라져서 보였다가 안 보였다가 하는 경우.

```
@Transactional(propagation=Propagation.REQUIRED)
```

- propagation : 트랜잭션 동작 도중 다른 트랜잭션을 호출할 때, 어떻게 할 것인지 지정하는 옵션

    - REQUIRED : Default값. 이미 진행중인 트랜잭션이 있다면 해당 트랜잭션 속성을 따르고, 진행중이 아니라면 새로운 트랜잭션 생성.

    - REQUIRES_NEW : 항상 새로운 트랜잭션 생성. 이미 진행중인 트랜잭션이 있다면 보류하고 해당 트랜잭션 작업을 먼저 진행.

    - SUPPORT : 이미 진행 중인 트랜잭션이 있다면 해당 트랜잭션 속성을 따르고, 없다면 트랜잭션을 설정하지 않음.

    - NOT_SUPPORT : 이미 진행중인 트랜잭션이 있다면 보류하고 트랜잭션 없이 작업 수행

    - MANDATORY : 이미 진행중인 트랜잭션이 있어야만 작업을 수행. 없다면 Exception 발생.

    - NEVER : 트랜잭션이 진행중이지 않을 때 작업 수행. 트랜잭션이 있다면 Exception 발생.

    - NESTED : 진행중인 트랜잭션이 있다면 중첩된 트랜잭션이 실행되며 존재하지 않으면 REQUIRED와 동일하게 실행.

```
@Transactional(noRollbackFor=Exception.class)
```

- noRollbackFor : 특정 예외 발생 시 rollback 하지 않는 옵션

```
@Transactional(rollbackFor=Exception.class)
```

- rollbackFor : 특정 예외 발생 시 rollback 하는 옵션

```
@Transactional(timeout=10)
```

- timeout : 지정한 시간 내에 메소드 수행이 완료되지 않으면 rollback하는 옵션. Default=-1. -1일 경우 no timeout.

```
@Transactional(readonly=true)
```

- readOnly : 트랜잭션을 읽기 전용으로 설정하는 옵션. Default=false. true 일 때 insert, update, delete 실행 시 예외 발생.

## 문제상황

- @Transactional을 사용하니 예외 발생시 롤백을 하고 있는데, 예외처리를 하되 롤백이 되지 않았으면 하는 상황 발생

- 이유를 찾아보니 @Transactional 사용 시 default값으로 RuntimeException 발생 시 롤백이 되고 있었음

- @Transactional은 기본적으로 Unchecked Exceiption. Error 만을 rollback 하고 있음. 모든 예외에 대해서 rollback 진행하고 싶으면 (rollbackFor=Exception.class) 붙여햐 함.

- CheckedException은 예상 가능한 예외라서 롤백을 하지 않고 UnCheckedException은 예상치 못한 예외라서 롤백이 됨.