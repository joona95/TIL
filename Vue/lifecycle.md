# Vue Lifecycle

## Lifecycle

### beforeCreate

- component의 data, events, computed, methods, watcher 가 정의되지 않은 시점

- component가 DOM에 부착되기 전이라서 DOM 조작 불가 (ref 속성으로 태그 가져올 수 없음)

### created

- beforeCreate 다음으로 실행됨

- data, events, computed, methods, watcher 가 활성화되어 사용 가능

- component가 DOM에 부착되기 전이라서 DOM 조작 불가 (ref 속성으로 태그 가져올 수 없음)

### beforeMount

- DOM에 부착되기 직전에 호출되므로 DOM에 아직 부착되지 않은 상태 (ref 속성으로 태그 가져올 수 없음)

### mounted

- 실제 DOM에 부착되고 난 이후에 실행됨

- DOM에 직접 접근 가능하고 제어가 가능함

### beforeUpdated

- component에서 사용되는 data의 값이 변해서 DOM에 변화가 적용되기 직전에 실행됨

### updated

- component가 DOM에 부착된 이후 DOM의 변화가 발생한 경우 감지

### beforeDestroyed

- component의 소멸 직전에 호출됨

- component의 기능을 그대로 가지고 있는 상태

### destroyed

- component의 소멸 후에 호출됨

- beforeDestroyed와 다르게 component의 기능이 모두 해제된 상태

## 부모와 자식 호출에 따른 Lifecycle

- 부모 created -> 자식 created -> 자식 mounted -> 부모 mounted