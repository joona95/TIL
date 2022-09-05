# Git Cherry Pick 

- 다른 브랜치의 일부 커밋만 반영하고 싶을 때 사용하는 깃 명령어

## 소스트리 사용법

1. 반영되어야 하는 브랜치로 체크아웃

2. 반영하고 싶은 브랜치의 커밋에 오른쪽 마우스 눌러서 체리픽 클릭

## 깃 명령어 사용법

- git branch develop의 특정 커밋을 main에 적용하고 싶을 때

```
$ git checkout develop
$ git log //가져오고 싶은 커밋의 id 확인
$ git checkout main
$ git cherry-pick 커밋id
```