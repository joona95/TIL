# Visual Studio 한글 깨짐

## 1. 다른 이름으로 저장
파일 > 다른이름으로 저장 > 저장 ▼ (화살표 클릭) > 인코딩하여 저장 > 유니코드(서명 있는 UTF-8) - 코드 페이지 65001 > 확인

<br>

## 2. .editorconfig 파일
.editorconfig 파일이란? 코딩 스타일을 일관되게 설정할 수 있게 해주는 설정 파일
<br>

<pre>
<code>
root = true
[*]              /* 적용할 파일 포맷 지정 가능 ex) [*.{cpp}] */
charset = utf-8
</code>
</pre>

