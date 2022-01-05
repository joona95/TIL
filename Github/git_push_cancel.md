# Git Remotes에 Commit을 잘못 Push 했을 때 Push 취소 방법

1. 돌아가길 원하는 Commit 선택 후 Reset Hard 로 되돌림

```
git reset --hard HEAD^
```

- 소스트리: Reset Branch to this Commit > Using mode: Hard > OK

- reset 옵션

    - soft: 워킹 디렉터리의 파일 보존 (add한 상태, staged 된 상태)

        ```
        git reset --soft HEAD^
        ```

    - mixed: 워킹 디렉터리의 파일 보존 (add하기 전 상태, unstaged 상태)

        ```
        git reset --mixed HEAD^
        git reset HEAD^
        git reset HEAD~2 //최근 2개의 commit 취소
        ```

    - hard: 워킹 디렉토리의 파일 삭제 (add하기 전 상태, unstaged 상태)

        ```
        git reset --hard HEAD^
        ```

2. 변경하고 싶은 내용 추가 수정 후 Commit Add 해줌

3. push를 하는데 오류가 날 때 터미널 통해서 강제 푸시 진행

```
git push --force origin branch명
```