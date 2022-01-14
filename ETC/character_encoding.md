# 문자열 인코딩

## 문자열 인코딩(character encoding)

- 2진법을 사용하는 컴퓨터가 인간의 언어를 일정한 규칙에 따라 2진수로 변환하는 방식

- 문자열 인코딩 규칙으로 아스키코드, EUC-KR, UTF-8, UTF-16, UTF-32 가 있음

- 컴퓨터 등장 시에는 영어와 일부 특수 문자만 지원했으나 여러 국가에서 국가별로 사용하는 언어 표현을 위해 독자적인 규칙을 만들기 시작. 이후 모든 언어를 같은 규칙으로 표현 가능한 유니코드 방식 등장.

- 모든 개발 환경이 유니코드 동일하게 처리하지 않아 서로 호환되지 않은 유니코드 문자열 인코딩 방식(UTF-8, UTF-16, UTF-32) 중 하나 선택 필요

- EUC-KR은 유니코드 등장 전에 만들어진 독자적인 한글 인코딩 방식

- 웹브라우저나 프로그램에서 글자가 깨지는 경우는 호환되지 않는 문자열 인코딩 사용하여 문자 읽기 때문


## 문자 집합(charset)

- 문자열 인코딩은 문자를 코드로 표현하는 방식이라면 문자 집합은 사용할 수 있는 문자들의 집합.

- 유니코드, ISO-8859, ASCII 등이 있음


## 아스키 코드(ASCII)

- 처음으로 표준 정립한 문자열 인코딩 방식

- 사용 가능한 문자의 종류는 대문자, 소문자, 아라비아 숫자, 공백 및 특수 문자들이 있음

- 문자 표현 시 총 128개의 숫자 사용 (0~127)

- 과거에는 7비트 2진수만 사용했지만 현대 운영체제들은 성능 향상과 편의를 위해 8비트(1바이트) 사용하여 아스키 코드 표현 -> 메모리 4바이트 정렬(memory 4-byte alignment)

- 영어를 제외한 다른 언어 표현 불가


## EUC-KR(CP949)

- 한국에서 한글을 표현하는 방법으로 EUC-KR 문자 집합 만듦

- 한국 산업 표준(KS)으로 지정된 한국어 문자 집합으로 문자 하나 표현을 위해 2바이트 사용

- 아스키 코드 문자 표현 시에는 1바이트 사용하기 때문에 아스키 코드와 호환됨

- 모든 글자가 완성된 형태로만 존재하기 때문에 초성, 중성, 종성을 조합해 문장을 만들 수 없어서 표현할 수 없는 한글이 일부 존재

- 실제 문자열 길이는 눈에 보이는 문자 길이, 버퍼 길이는 컴퓨터가 문자 표현하는데 사용한 바이트 수 의미로, 문자열 길이와 버퍼 크기는 다를 수 있음 (한글은 5글자, 10바이트)


## 유니코드(UTF-8, UTF-16, UTF-32)

- 국가별로 독자적인 문자열 인코딩 사용하는 문제 해결하기 위해 국제표준화기구(ISO)에서 동일한 규칙으로 모든 언어 표현 가능한 유니코드 문자 집합 만듦

- 유니코드 문자 집합 표현하는 문자열 인코딩은 UTF-8, UTF-16, UTF-32가 있음


## UTF-8

- 8비트(1바이트)로 인코딩하는 것

- 아스키 코드와 완벽하게 호환됨

- 문자에 따라 최소 1바이트에서 최대 6바이트까지 사용

- 일반적인 문자는 3바이트 내로 처리되며 4바이트 영역에는 이모지 문자 존재. 고대 문자 사용하지 않는 한 5바이트 이상 쓰는 경우 거의 없음.

- 실무에서는 대부분 라이브러리나 프로그래밍 언어에서 제공하는 UTF-8 유틸리티 함수 사용

- 윈도우, 자바, 임베디드를 제외한 거의 모든 환경에서의 문자열 처리 표준으로 봐도 좋음

- JSON은 UTF-8 인코딩만 사용하며 다른 문자열 인코딩은 표준에서 지원하지 않음

- MySQL의 UTF-8 타입에는 utf8과 utf8mb4가 존재. utf8은 3바이트까지 정상으로 처리하나 4바이트 영역 문자는 처리 못함. UTF-8과 완벽히 호환되는 문자 집합 쓰고 싶으면 utf8mb4 사용해야 함.


## UTF-16

- 16비트(2바이트)로 인코딩하는 것

- 2바이트 또는 4바이트 사용하기 때문에 아스키 코드와 호환되지 않음

- 유니코드에는 문자의 종류에 따라 기본 다국어 평면(Basix Multilingual Plane), 보충 다국어 평면(Supplementary Multilingual Plane), 상형 문자 보충 평명(Supplementary Ideographic Plane), 특수 목적 보충 평면(Supplementary Special-purpose Plane) 등 평면 4개 존재

- 바이트 수는 표현하려는 문자가 어떤 평면에 속하는지에 따라 결정

- 일반 글자(BMP)는 2바이트로 인코딩하고 특별한 글자(BMP 범위를 벗어나는 문자)들은 4바이트로 인코딩

- UTF-16과 UTF-32는 바이트 순서 표시(Byte Order Mark) 사용

- BOM은 문자열 가장 맨 앞 2바이트에 0xFEFF로 표기하여 사용

- 0xFE와 0xFF 중 어떤 문자가 먼저 오는 지에 따라 리틀 엔디언과 빅 엔디언으로 나뉨. 두 방식에 따라 문자열 인코딩 시 바이트 데이터 조합하는 순서 바뀜. (0xFFFE : 리틀 엔디언, 0xFEFF : 빅 엔디언)

- 빅 엔디언은 문자 구성하는 바이트 두 개 중 큰 단위를 먼저 읽음 (0x1234 -> 12 34)

- 리틀 엔디언은 문자 구성하는 바이트 두 개 중 작은 단위를 먼저 읽음(0x1234 -> 34 12)

- UTF-8는 1바이트 단위로 글자 변환하기 때문에 글자 읽는 순서가 달라도 영향 받지 않아서 BOM 사용할 필요 없고 권장하지 않음

- UTF-16 기반 환경에서 UTF-8 사용 시 사용 영역 명확히 구분하는 게 좋음(ex. 기본으로 UTF-16 사용하되 데이터베이스나 브라우저 간 통신시 UTF-8 변환 등)


## UTF-32

- 모든 문자를 고정된 4바이트 길이로 사용

- UTF-16과 동일한 규칙 사용하므로 더 많은 바이트 사용하는 것 외에 별다른 특징이 없음

- 사용이 점점 줄고 있음

- 반드시 UTF-32 사용해야 하는 환경 아니라면 사용하지 않음