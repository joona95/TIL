# nohup 백그라운드 실행

- nohup: 백그라운드 작업을 위해 실행하는 명령어

## 백그라운드에서 실행하기

```
nohup 실행하고싶은명령 &
```

- 이 경우 nohup.out 로그 파일이 생성됨

- 로그가 계속 생겨서 용량이 감당이 안 될 수 있으므로 초기화/삭제가 필요함

```
nohup 실행하고싶은명령 1> /dev/null 2>&1 &
```

- 로그 없이 nohup 실행

```
cp /dev/null nohup.out
```

- nohup.out 로그 파일 초기화

- /dev/null 파일은 항상 비어 있음