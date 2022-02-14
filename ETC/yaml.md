# YAML(Yet Another Markup Language)

- 이메일 양식에서 힌트를 얻어 만든 텍스트 기반 데이터 규격으로 사람이 쉽게 읽기 쉬움

- YAML 고유한 기능인 앵커, 별칭, 주석 제외하면 JSON과 호환 가능

- 중괄호나 큰따옴표 사용하지 않기 때문에 JSON보다 적은 용량으로 데이터 직렬화 가능

- 바이너리 규격에 비해 비효율적임

- JSON만큼 범용적으로 사용되는 규격은 아님

## 특징

- 주석 지원

- UTF-8과 UTF-16 지원

  - JSON은 UTF-8만 지원

  - UTF-16을 기본으로 사용하는 윈도우, 자바에서 만든 소프트웨어 설정 파일로 사용 가능

- 앵커(anchors)와 별칭(aliases) 기능

  - 원본 데이터에 앵커 설정하고 이를 가리키는 여러 별칭 만들 수 있음

  - 공통으로 사용하는 값들을 한 곳에서 관리 가능

## 구조

```
number: 12345
pi: 3.14
str: string
null_key: ~
object:
    str2: string2
    object2:
        number2: 12345
num_array:
- 1
- 2
- 3
- 4
- 5
str_array:
- one
- two
- three
- four
- five
```

- JSON 구조와 비슷

- 키와 값 표현할 때 큰따옴표 쓰지 않음

- 중괄호 대신 스페이스로 띄어쓰기하여 들여쓰기 사용

- 대괄호 대시 하이픈(-) 사용하여 배열 요소 구분

- null 대신 ~ 를 사용하여 NULL 표현

## 주석

- \# 으로 시작하는 모든 줄과 # 이후 모든 문자열이 주석 처리됨

- \######... 을 사용하여 설정 파일 안 내용 명시적 구부 가능

## 앵커와 별칭

```
number: &num 12345
object:
    number2: *num # number2는 12345가 됨
```

- 앵커는 &으로 시작하는 식별자

- 별칭은 \*로 시작하는 식별자

- 별칭을 사용하면 앵커로 지정된 값 사용 가능

```
definitions:
    default: &default
        min_log_level: info
        app_name: app
        log_dir: logs
        secure_mode: false
    configurations:
        dev:
            <<: *default
            min_log_level: verbose
            server_url: http://dev.app.com
        production:
            <<: *default
            min_log_level: warning
            secure_mode: true
            server_url: http://www.app.com
```

- <<: 키워드 사용하면 앵커로 참조하는 값에 더 맣은 값 추가하거나 기존 값 덮어쓸 수 있음
