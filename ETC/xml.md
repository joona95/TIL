# XML

- 웹에서 규격화된 데이터를 효율적으로 주고받기 위해 만든 마크업 언어

- JSON, YAML보다 먼저 등장

- JAVA/C# 애플리케이셔 설정 파일, 클라이언트와 서버 간 규격화된 메시지 주고받는 용도로 활용

- 호환성 유지하기 위해 XML사용하는 경우도 있고, 상대적으로 익숙하 XML을 선택하는 경우도 있어서 아직 많이 사용됨

## 특징

- 텍스트 기반 데이터

  - 디버깅이 편하고 사람이 읽기 쉬움

  - JSON과 YAML보다 더 많은 데이터 사용

- 문자열 인코딩 지원

  - XML은 문자 인코딩을 직접 지정할 수 있음

    - JSON은 UTF-8 지원, YAML은 유니코드(UTF-8, UTF-16, UTF-32) 지원

  - 인코딩 정보 읽으려면 파일의 인코딩 정보를 미리 알고 있어야 함

  - 대부분 실무 개발 환경은 인코딩으로 UTF-8, UTF-16 사용하므로 장점이라 보기 어려움

## 구조

```
<?xml version="1.0" encoding="UTF-8"?>
<message>
    <number>12345</number>
    <pi>3.14</pi>
    <str option1="1" option2="2">string</str>
    <null_tag />
    <object>
        <str2>string2</str2>
        <object2>
            <number2>12345</number2>
        </object2>
    </object>
    <num_array>
        <element>1</element>
        <element>2</element>
        <element attribute="value">3</element>
        <element>4</element>
        <element>5</element>
    </num_araay>
    <str_array>
        <element>one</element>
        <element>two</element>
        <element>three</element>
        <element>four</element>
        <element>five</element>
    </str_array>
</message>
```

- 모든 구성 요소들은 \<로 시작해서 >로 끝나는 태그 사용

- 같은 이름을 가진 요소가 여러 개 있을 때 배열로 취급

- 요소 아에 추가적으로 속성(attribute) 값 설정 가능

  - 속성은 요소에 대한 부가 정보를 나타내는 메타 데이터

  - 요소 인수, 설정을 표현할 때 유용하게 사용 가능
