# 스프링 웹 기초: 정적 컨텐츠, MVC와 템플릿 엔진, API

## 정적 컨텐츠

- 스프링부트는 기본적으로 '/static' 폴더에서 정적 컨텐츠 제공

- 해당 폴더('/static') 내에 html 파일 생성 후 'localhost:8080/파일명.html' 접속 시 접근 가능

- url로 요청이 오면 스프링은 관련 컨트롤러 있는지 먼저 확인 후, static 폴더에서 정적 컨텐츠 찾아봄

    - 컨트롤러가 우선순위를 가짐

## MVC와 템플릿 엔진

- 이전에는 JSP 등에서는 Controller와 View를 구분하지 않고 View에서 모든 걸 처리했었음

- MVC: Model, View, Controller

    - View: 화면을 그리는 역할

    - Controller: 비지니스 로직 관련, 내부적인 처리

    - Model: 화면에 필요한 정보 담아서 넘겨주는 역할

## API

- @RequestParam : url 뒤에 쿼리스트링 (?name=spring') 을 통해 전달되는 값 받기
    - name: 명칭
    - value: 값
    - required: 필수값 여부. default는 true.

- @ResponseBody : 기본으로 JSON 형식 객체 반환
    - JSON 형식 : key, value 형식으로 이루어짐
    - 과거에는 xml 형식도 많이 쓰였으나 무거워서 현재는 JSON 형식 주로 사용
    - Controller에서 @ResponseBody가 있을 경우 HttpMessageConverter 가 동작 
        - 단순문자일 경우 StringConverter(StringHttpMessageConverter)가 기본 문자 처리 
        - 객체일 경우 JsonConverter(MappingJackson2HttpMessageConverter)가 기본 동작해서 JSON 형식으로 바꿔서 요청 웹브라우저에 넘겨줌
            - JSON으로 바꿔주는 라이브러리: Jackson, GSON
            - 스프링은 기본적으로 Jackson으로 사용
        - byte 처리 등등 여러 HttpMessageConverter가 기본으로 등록되어 있음

        



