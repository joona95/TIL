# CSS

## CSS란

- Cascading Style Sheet 

- https://en.wikipedia.org/wiki/CSS

## Cascading

- 웹사이트 스타일링 타입 3가지 : Author style > User style > Browser 순서대로 적용되는 것이 Cascading
    
    - Author style : 웹사이트 만들 때 제공하는 css 파일

    - User style : 사용자가 지정한 스타일

    - Browser : 브라우저 상에서 정의된 스타일

- '! important' 는 Cascading을 끊어내고 제일 중요한 스타일이라고 주장

    - important는 가능하면 쓰지 않는 것이 좋음

## selectors 

- html에서 어떤 태그들을 고를 건지 규정하는 문법

- '*' : 모든 태그들 고르는 것. universal selector.

- 'tag 이름' : 해당 태그를 고르는 것. type selector.

- '#id' : 해당하는 id만 골라냄

- '.class' : 해당하는 class만 골라냄

- ':' : 태그 옆에 써서 해당하는 state 골라냄

- '[]' : 해당하는 attribute 골라냄

- MDN CSS selectors: https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Selectors

## CSS 문법

```css
/*
selector {
    property: value;
}
*/

* {
    color: green;
}

li {
    color: blue;
}

li#special { 
    color: pink;
}

#special {
    color: pink;
}

.red {
    width: 100px;
    height: 100px;
    background: yellow;
}

button:hover {
    color: red;
    background: beige;
}

a[href] {
    color: purple;
}

a[href="naver.com"] {
    color: purple;
}

a[href^="naver"] { /* naver로 시작하는 것들만 */
    color: purple;
}

a[href$=".com"] { /* .com으로 끝나는 것들만 */
    color: purple;
}
```

- 구체적으로 태그 가까이 설정한 값이 우선순위가 높아짐

- 태그들도 묶어서 사용할 수 있음

```css
.red {
    border-width: 2px;
    border-style: solid;
    border-color: pink;
}
```s
```css
.red {
    border: 2px solid pink;
}
```

- 한 줄로 간단하게 표현 가능

- MDN CSS Reference: https://developer.mozilla.org/en-US/docs/Web/CSS/Reference

- MDN CSS Properties Reference: https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Properties_Reference

## padding & margin

- padding : 컨텐츠 안에 들어가는 spacing

     ```css
    .red {
        width: 100px;
        height: 100px;
        padding-top: 20px;
        background: yellow;
    }
    ```

    - padding-top, padding-bottom, padding-left, padding-right 로 각각 사이즈 따로 넣을 수 있음

    ```css
    .red {
        width: 100px;
        height: 100px;
        padding: 20px 20px 20px 20px;
        background: yellow;
    }
    ```

    - 한번에 top, right, bottom, left 순으로 지정 가능

    ```css
    .red {
        width: 100px;
        height: 100px;
        padding: 20px 0px;
        background: yellow;
    }
    ```

    - 위아래, 왼오른쪽 따로도 가능함

- margin : 컨텐츠 밖에 들어가는 spacing

## Display

```html
<body>
    <!-- Block level -->
    <div></div>
    <div></div>
    <div></div>

    <!-- Inline level -->
    <span>1</span>
    <span>1</span>
    <span>1</span>

</body>
```
```css
div, span {
    width: 80px;
    height: 80px;
    margin: 20px;
}

div {
    background: red;
    display: inline-block;
}

span {
    background: blue;
    display: block; 
}
```

- display 통해서 div를 block 에서 inline 으로, span을 inline에서 block으로 변경 가능

- 'display: inline' 과 'display: inline-block' 은 다름

    - inline 을 하면 처음 span 처럼 컨텐츠 자체만을 꾸며줌

    - inline-block 은 box의 width, height에 맞춰서 꾸며줌

## Position

```html
<body>
    <article class="container">
        <div></div>
        <div class="box">I'm Box</div>
        <div></div>
        <div></div>
        <div></div>
        <div></div>
        <div></div>
        <div></div>
        <div></div>
        <div></div>
        <div></div>
        <div></div>
        <div></div>
    </div>
</body>
```
```css
div {
    width: 50px;
    height: 50px;
    margin-bottom: 20px;
    background: red;
}

.container {
    background: yellow;
    left: 20px;
    top: 20px;
    position: relative;
}

.box {
    background: blue;
    left: 20px;
    top: 20px;
    position: relative;
}
```

- position은 기본값으로 static을 가지고 있음

- static : html에 정의된 순서대로 자연스럽게 브라우저에 보여지는 것

- relative : 원래 있어야 하는 자리에서 상대적으로 옮겨가는 것

- absolute : 내 아이템이 담겨있는 가장 가까운 박스 안에서 위치 변경이 일어나는 것

- fixed : 상자 안에서 벗어나서 웹 페이지(윈도우)를 기준으로 이동하는 것

- sticky : 원래 있던 자리에 있는데 스크롤링되어도 없어지지 않고 그 자리에 그대로 있는 것

## float

- 이미지와 텍스트를 어떻게 배치할 것인지에 대한 것

- float: left / float: center / float: right

- MDN Float: https://developer.mozilla.org/en-US/docs/Web/CSS/float

## 100% vs 100vh

- % : 컨테이너가 들어있는 부모 높이의 100%를 채우겠다는 의미

- vh : 보이는 viewport의 얼마만큼 쓰겠다는 의미

## FlexBox

- container에 꾸며줄 수 있는 속성값들

    - display

    - flex-direction

    - flex-wrap

    - flex-flow

    - justify-content

    - align-items

    - align-content

- item을 꾸며줄 수 있는 속성값들

    - order

    - flex-grow

    - flex-shrink

    - flex

    - align-self

- main axis / cross axis : 중심축을 수평으로 두냐 수직으로 두냐에 따라 반대축도 달라짐

```css
.container {
    background: beige;
    height: 100vh;
    display: flex;
    flex-direction: row;
    flex-wrap: nowrap;
    /* flex-flow: column nowrap; */
    justify-content: flex-start;
}
```

- display: flex; 로 flex box 임을 알려줘야 함

- flex-direction 기본 값은 row
    
    - row: 왼쪽에서 오른쪽 방향

    - row-reverse" 오른쪽에서 왼쪽 방향

    - column: 위에서 아래 방향

    - column-reverse: 아래에서 위 방향

- flex-wrap 기본 값은 nowrap

    - nowrap: 아이템들이 한 줄에 빼곡하게 붙어있음

    - wrap: 아이템들이 한 줄에 꽉 차게 되면 자동적으로 다음 라인으로 넘어가는 것

    - wrap-reverse: 반대로 wrapping 되는 것

- flex-flow: flex-direction과 flex-wrap 한 번에 작성 가능

- justify-content 기본 값은 flex-start. 아이템 순서는 유지하고 중심축에서 아이템을 어떻게 배치해줄 건지 결정.

    - flex-start

    - flex-end

    - center

    - space-around: 박스를 둘러싸게 spacing 이 들어감

    - space-evenly: 똑같은 간격 넣어줌

    - space-between: 끝쪽 아이템은 딱 붙이고 사이에 있는 아이템들만 사이에 spacing 넣어줌

- align-items 반대축에서 아이템을 어떻게 배치해줄 건지 결정.

    - center

    - baseline: 텍스트가 균등하게 보여질 수 있도록 baseline에 맞춰서 배치

- align-content 반대축의 아이템 배치
    
    - flex-start

    - flex-end

    - center

    - space-around

    - space-evenly

    - space-between

```css
.container {
    background: beige;
    height: 100vh;
    display: flex;
}

.item {
    width:40px;
    height: 40px;
    border: 1px solid black;
}

.item1 {
    background: red;
    order: 0;
    /*
    flex-grow: 1;
    flex-shrink: 1;
    flex-basis: 60%;
    */
    flex: 2 2 auto; /* grow, shrink, basis */
    align-self: center;
}
```

- order 지정으로 아이템 순서 바꿀 수 있음

- flex-grow 없으면 container 크기가 아무리 커져도 크기 그대로, 크기가 작아지면 어쩔 수 없이 작아짐. flex-grow를 쓰면 container를 다 채우려고 크기 늘어남. 기본값은 0.

- flex-shrink는 container가 작아졌을 때 어떻게 행동할지 지정하는 것. 기본값은 0.

- flex-basis 는 아이템들이 공간 얼마나 차지해야할지 세부적으로 명시할 수 있도록 도와줌. 기본 값은 auto. auto는 grow, shrink에 지정한 것에 맞춰서 아이템 변형됨. 

- align-self 아이템별로 아이템들을 정렬할 수 있음. 아이템 하나만 정렬하고 싶을 때 사용.

- CSS Tricks for Flexbox: https://css-tricks.com/snippets/css/a-guide-to-flexbox/

- MDN Flexbox: https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flexible_Box_Layout/Basic_Concepts_of_Flexbox