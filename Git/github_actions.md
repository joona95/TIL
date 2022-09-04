# Github Actions

## 주요 개념

- Events

    - 깃허브에서 발생할 수 있는 이벤트(머지, 커밋, 이슈 등) 지정 가능

- Workflows

    - 이벤트가 발생했을 때 shell 로 수행할 작업들 자동화

    - 하나의 워크플로우 안에 여러 Job 존재 가능

- Jobs

    - 기본적으로는 병렬적, 동시다발적으로 수행됨

    - 순차적으로 수행되도록 지정도 가능

    - Job 수행하기 위한 step 설정을 script 형태로 작성 가능

    - step 내에서 github 에서 제공하는 action 설정 가능

- Actions

    - 재사용 가능한 이미 정의되고 공개된 actions

- Runners

    - 각각의 Job 을 독립적인 Runner 컨테이너에서 실행됨


## 사용 방법

1. .github/workflows/ 폴더 생성 필요

2. .github/workflows/ 폴더 내에 yml 파일 생성

    - 파일 명은 어떤 workflow인지에 따라 정하면 됨
    
    - ex) main.yml , develop.yml , ...

3. yml 문서 작성

```yml
name: github-actions  # workflow 이름 명시
on: [push] # 어떤 event 발생했을 때 workflow 실행할지 (push: commit이 push될 때 마다)
jobs: # 여러 job 
    check-bats-version: # 하나의 job, job의 이름 명시
        runs-on: ubuntu-latest # runner 사용 시 어떤 runner(VM) 사용할건지 명시
        steps: # 어떤 순서대로 job 을 수행할건지
            - uses: actions/checkout@v3 # action 사용하여 checkout 실행
            - uses: actions/setup-node@v3 # action 사용하여 node setup 
              with:
                node-version: '14' # with 문법 통해서 node version 명시
            - run: npm install -g bats # 쉘스크립트 작성
            - run: bats -v 
```


