# Java8 Stream 의 limit 과 skip

## limit

```Java
List<String> list = Arrays.asList("1", "2", "3", "4", "5");
list.stream()
    .limit(3)
    .forEach(System.out::println);

/* 결과
1
2
3
*/
```

- 사용방법: Stream.limit(숫자)

- 스트림에서 일정 숫자 개수만큼만 가져와서 새로운 스트림을 생성하여 리턴

## skip

```Java
List<String> list = Arrays.asList("1", "2", "3", "4", "5");
list.stream()
    .skip(3)
    .forEach(System.out::println);

/* 결과
4
5
*/
```

- 사용방법: Stream.skip(숫자)

- 스트림에서 일정 숫자만큼 아이템을 건너띄고 그 이후의 아이템들로 새로운 스트림을 생성하여 리턴