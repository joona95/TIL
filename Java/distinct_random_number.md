# 중복없이 난수(Random Number) 생성 (Stream 활용)

```
ThreadLocalRandom.current()
                .ints(0, 10)
                .distinct()
                .limit(5)
                .boxed()
                .collect(Collectors.toList());
```

- ints 메서드는 IntStream을 생성해줌

```
IntStream.generate(RandomUtil::createRandomNumber)
                .distinct()
                .limit(5)
                .boxed()
                .collect(Collectors.toList());
```

- RandomUtil 의 createRandomNumber 메서드가 0 ~ 9 범위 사이 난수 생성하는 함수

    ```
    new Random().nextInt(10)
    ```

