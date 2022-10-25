# GIT 레파지토리에 새롭게 생성된 브랜치로 checkout 하려고 했을 때 에러 발생

## 에러 발생

```
error: pathspec '브랜치명' did not match any file(s) known to git.
```

## 해결 방안

1) 

```
git remote update 
git fetch
git checkout 브랜치명
```

- 이 방법은 또 다른 에러가 뜨면서 잘 되지 않음

    ```
    error: cannot update the ref 'refs/remotes/origin/브랜치명': unable to append to '.git/logs/refs/remotes/origin/브랜치명': Not a directory
    ```



2)

```
git checkout -t origin/브랜치명
```

- 이 방법으로 해결
