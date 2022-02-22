# commit 날짜 및 시간 변경

- 직전 커밋 날짜를 현재 날짜로 변경하기

```
git commit --amend --no-edit --date "$(date)"
```

- 직전 커밋 날짜를 원하는 날짜로 변경

```
git commit --amend --no-edit --date "Wed 23 Feb 2022 12:00:00 KST"
```
