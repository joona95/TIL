# 스프링부트 프로젝트 환경설정

## 프로젝트 생성

### 스프링 부트 스타터

- 스프링 부트 스타터 사이트: https://start.spring.io

    - Generate 로 다운로드 받기

- Maven / Gradle

    - 라이브러리 가져오고 빌드하는 라이프 사이클 관리해주는 툴

    - 요새는 Gradle을 더 많이 사용하는 추세

- 스프링 부트 버전

    - SNAPSHOT : 아직 만들고 있는 버전

    - M1 : 정식 릴리즈된 버전이 아님

- Group

    - 보통 기업 도메인명을 적음

- Artifact

    - 빌드 됐을 때 결과물

- Dependencies

    - 스프링부트 실행 시 어떤 라이브러리 쓸 건지 결정

    - Spring Web : 웹프로젝트 만들 시 사용

    - Thymeleaf : html을 만드는 템플릿 엔진

 

### 스프링 부트 구조

- java 폴더 : 실제 패키지와 소스 파일 존재

- resources 폴더 : 실제 자바 코드 소스를 제외한 xml, properties 같은 설정파일, html 등

- test 폴더 : 테스트 코드와 관련된 소스들 존재

- build.gradle : 버전 설정하고 라이브러리 가져옴

- sourceCompatibility : 자바 버전 호환

- repositories { mavenCentral() } : mavenCentral이라는 사이트에서 라이브러리들 다운로드 하라는 의미

- dependencies : 가져올 라이브러리들

 

### 스프링 부트 실행

- (IntelliJ > Preferences > 빌드, 실행, 배포 > 빌드 도구 > Gradle > 다음을 사용하여 빌드 및 실행, 테스트 실행) 에서 IntelliJ 로 변경

    - Gradle 통해서 돌리는 것보다 더 빠르게 실행됨


## 라이브러리

### 스프링부트 라이브러리

- spring-boot-starter-web

    - spring-boot-starter-tomcat: 웹서버 톰캣 관련 라이브러리

    - spring-webmvc: 스프링 웹 MVC

- spring-boot-starter-thymeleaf: 타임리프 템플릿 엔진

- spring-boot-starter: 공통으로 들어가는 라이브러리. 스프링부트 + 스프링 코어 + 로깅

    - spring-boot
        
        - spring-core: 스프링부트를 돌아가게 하는 중심적인 역할

    - spring-boot-starter-logging: 현업에서는 System.out.println 대신 로깅 사용. 두가지 제일 많이 사용.

        - logback: 요새 가장 많이 사용

        - slf4j

### 테스트 라이브러리

- spring-boot-starter-test

    - junit: 자바에서 테스트 할 때 주로 사용하는 테스트 프레임워크. 4에서 5로 넘어가는 추세.
    
    - mockito: 목 라이브러리

    - assertj: 테스트 코드를 편하게 작성하도록 도와주는 라이브러리

    - spring-test: 스프링 통합 테스트 지원


## View 환경설정

### Welcome Page

- 스프링부트는 'static/index.html' 파일을 올려두면 Welcome Page 기능 제공

### thymeleaf 템플릿 엔진

- thymeleaf 공식 사이트: https://www.thymeleaf.org/

- 스프링 공식 튜토리얼: https://spring.io/guides/gs/serving-web-content/

- 스프링부트 메뉴얼: https://docs.spring.io/spring-boot/docs/

<br>

```html
<html xmlns:th="http://www.thymeleaf.org">
...
</html>
```

- html에 thymeleaf 선언 후 thymeleaf 문법 사용 가능

```java
@Controller
public class HelloController {
 @GetMapping("hello")
 public String hello(Model model) {
 model.addAttribute("data", "hello!!");
 return "hello";
 }
}
```

- 컨트롤러에서 리턴 값으로 문자 반환하면 viewResolver 가 화면을 찾아서 처리

    - 스프링부트 템플릿엔진 기본 viewName 매핑

## 빌드하고 실행

### 스프링부트 빌드

```
./gradlew build
```

- build 폴더 생성됨

- build/libs 폴더에 jar 파일 생성됨

### 스프링부트 실행

```
java -jar 빌드파일명.jar
```

- 루트 폴더에서 실행시키고 싶으면 빌드파일명 앞에 위치 path 적어주면 됨

### 스프링부트 빌드 클린

```
./gradlew clean
```

- 빌드 폴더 삭제됨

```
./gradlew clean build
```

- 기존 빌드 폴더 완전히 지우고 새로 빌드
