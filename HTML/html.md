# HTML

## HTML이란

- 웹 브라우저에서 보여지도록 디자인된 표준화된 마크업 언어를 사용하는 문서

    - Markup 언어란? 
    
        일반적인 텍스트와 문법적으로 구분하기 위해서 문서에 annotating 된 것을 말함

        https://en.wikipedia.org/wiki/Markup_language

- 브라우저에서 실행 가능한 가장 기본적인 파일

- https://en.wikipedia.org/wiki/HTML

## HTML 문법

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <meta name="viewport" content="width=device-width">
        <title>HTML</title>
    </head>
    <body>
        <h1>heading1</h1>
        <h2>heading2</h2>
        <button>Click me</button>
        <a href="https://naver.com" target=_blank>Click</a>
        <p> This is a sentence. <b>That</b> is...</p>
        <p> This is a sentence. <span>That</span> is...</p>
        <p> This is a sentence. <div>That</div> is...</p>
        <ol type="i" reversed>
            <li>1</li>
            <li>2</li>
            <li>3</li>
        </ol>
        <ul>
            <li>1</li>
            <li>2</li>
            <li>3</li>
        </ul>
        <label for="input_name">Name: </label>
        <input id="input_name" type="text">
    </body>
</html>
```

- document type은 html 이란 의미

- html 태그는 html 파일의 제일 상위 태그

- html 안에는 head 와 body 로 나누어짐

- head 는 사용자에게 보여지는 ui적인 요소는 전혀 없고 검색할 때 나오는 타이틀, 부가설명 혹은 북마크할 때 나오는 제목이나 아이콘 등이 정의되어 있음. css를 연결하는 것도 이루어짐. 사용자에게 보여지는 정보는 없고 meta 데이터를 가지고 있음.

- body 는 사용자에게 보여지는 최상위의 컨테이너. 안에 작성되는 것들이 유저에게 보여지는 것.

- 이 페이지에서 사용할 character set 은 utf-8 로 사용할 것
    
    - utf-8은 현존하는 모든 사람들이 쓰는 언어를 사용하므로 기본으로 사용하면 됨

    - https://en.wikipedia.org/wiki/UTF-8

- viewport는 device screen 넓이를 다 사용한다는 의미

- a tag의 href, target은 attribute

- b와 span은 inline 태그, div는 block 태그

- order list item 은 순서가 지정됨. unorder list item 은 dot 상태로 나타남.

- MDN 사이트에서 태그 안에 속성값이 뭐가 있는지 확인하여 사용

- input 은 사용자에게 입력을 받음. input만 사용하지 않고 label과 함께 어떤 값을 받고 싶은지 알림. input과 label은 inline 태그. 한 페이지에 여러 input이 있는 경우가 많으므로 id로 고유한 식별자 줌. input의 type은 text, button, checkbox, color, file, password 등 다양하게 있음.

## W3C (World Wide Web Consortium)

- 웹의 표준화를 추진하는 단체

- 유효한 태그를 썼는지 확인하는 사이트 : https://validator.w3.org

## MDN web docs

- 태그 종류들 확인하고 싶으면  HTML elements reference 참고: https://developer.mozilla.org/en-US/docs/Web/HTML/Element

- Mozilla에서 추진해서 만든 웹사이트로 정보도 가장 빠르게 업데이트되고 있음

- Document and website structure: https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Document_and_website_structure

## tag 종류

#### <b>형태 없이 section 나누기 위한 태그</b>

- header

- footer

- nav

- aside

- main

- section

- article: 좀 더 재사용성이 있을 때

- div: 묶어서 스타일링을 하고 싶을 때

- span

- form

#### <b>형태가 있어서 눈에 보이는 태그</b>

- a

- button

- input

- label

- img

- video

- audio

- map

- canvas

- table

#### <b>사용자에게 보여지는 태그 구분</b>

- Block: 충분한 공간이 있어도 한 줄에 하나 차지하는 것

- Inline: 충분한 공간이 있다면 다른 태그 옆에 배치가 가능

## Tag & Element

```html
<p>this is content</p>
```

- \<p\> : opening tag

- \</p\> : closing tag

- this is content : content

- \<p\>this is content\</p\> : element

## Attributes

```html
<p class="something">this is content</p>
```

- class="something" : Attribute

