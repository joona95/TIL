# js, css 없이 사용 가능한 유용한 html 태그들

## progress

```html
<progress value="50" min="0" max="100"></progress>
```
- 작업의 진행상황 전달

## meter

```html
<meter min="0" max="100" low="20" high="65" optimum="15" value="10"></meter>
```
- 값이 높고 낮음에 따라 색상 변경됨

- 작업의 진행상황 전달하지 않고 값의 상태만 전달

- ex. 미세먼지 측정 정도

- css pseudo classes 활용해서 커스터마이징 가능

## details

```html
<details>
    <summary>this is summary</summary>
    <span>this is content</span>
</details>
```

- summary 태그는 클릭 가능한 영역으로 클릭 전에 볼 수 있는 영역

- summary 후에 나오는 내용은 유저가 클릭한 이후에 볼 수 있음

- 클릭 여부에 따라 움직이는 화살표가 자동 구현됨

- open 이라는 css selector 존재함

    ```html
    <details id="details"></details>
    ```
    ```css
    #details[open] {
        ...
    }
    ```

## 날짜, 달력

- 날짜 선택

    ```html
    <input type="date"> 
    ```

- 달 선택

    ```html
    <input type="month">
    ```
- 주 선택
    
    ```html
    <input type="week">
    ```

- 시간 선택

    ```html
    <input type="time">
    ```


## picture

```html
<picture>
    <source srcset="src/01.jpeg" media="(min-width:1200px)" />
    <source srcset="src/02.jpeg" media="(min-width:900px)" />
    <source srcset="src/03.jpeg" media="(min-width:500px)" />
    <img src="src/04.jpeg" />
</picture>
```

- 유저의 장치나 환경에 따라 각기 다른 버전의 이미지 표시 가능

- picture 태그는 img 태그나 source 태그와 함께 이용됨

- media 속성에서 midea query 사용

- img 태그는 디폴트 값으로 사용됨. 브라우저가 picture 나 source 태그를 지원하지 않는 경우에 사용됨.

- 화면이 작을 경우 대형 화면용으로 지정된 html 내 이미지들을 다운로드 하지 않아서 페이지 로딩속도를 높여줌.


## datalist

```html
<label for="movie">What is your favorite movie?</label>
<input type="text" list="movie-options" />
<datalist id="movie-options">
    <option value="ABCD" />
    <option value="EFGH" />
    <option value="IJKL" />
    <option value="MNOP" />
    <option value="QRST" />
</datalist>
```

- js 작성 없이 자동완성을 가능하게 함

- input에 입력하면 해당 단어로 시작하지 않아도 포함되는 단어가 필터링돼서 나타남