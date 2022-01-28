# NVM

## NVM (Node Version Manager)

- Node.js 여러 버전을 설치해두고 편하게 관리 가능하게 해주는 도구

<br>

## 설치 방법 (Mac OS)

- nvm 설치
```
$ brew install nvm
```

- nvm 명령어 사용가능하게 환경변수 설정

    - ~/.nvm 디렉토리 생성
    ```
    $ mkdir ~/.nvm
    ```

    - 명령어 사용 가능하게 환경변수 설정 파일 생성
    ```
    $ vi ~/.zshrc
    ```

    - 환경변수 추가하고 저장 (:wq)
    ```
    export NVM_DIR="$HOME/.nvm" [ -s "/usr/local/opt/nvm/nvm.sh" ] && . "/usr/local/opt/nvm/nvm.sh" # This loads nvm [ -s "/usr/local/opt/nvm/etc/bash_completion.d/nvm" ] && . "/usr/local/opt/nvm/etc/bash_completion.d/nvm" # This loads nvm bash_completion
    ```

- nvm 설치 확인
```
$ nvm -v
```

- Node.js 설치
```
$ nvm install <version>
```

- 설치한 node 버전 사용

```
$ nvm use <version>
```

- .nvmrc 사용 하는 경우

    - .nvmrc 생성
    ```
    $ echo "5.9" > .nvmrc

    $ echo "lts/*" > .nvmrc # to default to the latest LTS version

    $ echo "node" > .nvmrc # to default to the latest version
    ```

    - 해당 프로젝트 .nvmrc에 설정된 node 버전 사용

    ```
    $ nvm use
    ```