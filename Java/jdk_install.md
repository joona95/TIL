# Java 설치

## Mac 에서 Java 설치

### 1. homebrew 로 Java 11 설치

```
brew tap adoptopenjdk/oepnjdk
brew install adoptopenjdk11 --cask
```

- homebrew : Mac 용 패키지 관리자로 개발자에게 필요한 도구 쉽게 설치 가능
    
### 2. Oracle 에서 직접 설치

- https://www.oracle.com/java/technologies/downloads/#java11-mac

<br>

## Java 버전 변경

### 1. 현재 자바 버전 확인

```
java -version
```

### 2. 설치된 전체 자바 버전 확인

```
/usr/libexec/java_home -V
```

- /usr/libexec : 실행파일이 모여있는 디렉토리

- java_home : PC에 세팅된 Java와 JVM 정보 조회하는 파일

### 3. Java 11 로 버전 변경

(1) 비번 입력 후 파일 열기 

```
sudo vi ~/.bash_profile
```

(2) export 를 버전 11로 변경 후 저장

```
export JAVA_HOME=$(/usr/libexec/java_home -v 11)
```

(3) source 명령어로 변경된 패스 실행

```
source ~/.bash_profile
```

(4) 변경된 버전 확인

```
java -version
```