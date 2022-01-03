# CSS Selector

```css
div {}
div button {}
```
- 태그 이름 : 해당 태그명의 element 선택
- 연달아서 쓰는 경우 div 안에 button element 의미함

```css
#small {}
div#small {}
```
- #아이디값 : 해당 id값을 가진 element들 선택

```css
.small {}
div.small {}
```
- .클래스명 : 해당 클래스 이름을 가진 element들 선택

```css
* {}
div * {}
```
- 전체 element 선택
- div의 전체 element 선택

```css
p + .intro {}
div + a {}
```
- p 다음으로 오는 (인접한) class명 intro인 element들
- div 다음으로 오는 (인접한) a 태그명의 element들

```css
A ~ B {}
```
- A 다음으로 오는 모든 B element들

```css
A > B {}
```
- A 의 direct로 자식인 element들

```css
p:first-child {}
div p:first-child {}
```
- 부모한테서 첫번째 자식이 p element들

```css
span:only-child {}
ul li:only-child {}
```
- span 중 어떤 부모에게서 유일한 자식 element인 경우

```css
span:last-child {}
```
- 부모한테서 마지막 자식인 span element들

```css
div p:nth-child(2) {}
```
- :nth-child(x) 는 부모한테서 x번째 자식 element들을 의미

```css
div p:nth-last-child(2) {}
```
- :nth-last-child(x)는 부모한테서 뒤에서부터 x번째 자식 element 의미


```css
span:first-of-type {}
```
- :first-of-type은 특정 타입의 첫번째 element를 가져옴

```css
div:nth-of-type(2) {}
div:nth-of-type(odd) {}
div:nth-of-type(even) {}
div:nth-of-type(An+B) {}
```
- :nth-of-type(x)는 어떤 타입의 x번째 element를 가져옴
- odd를 넣으면 모든 홀수번째 element들, event 넣으면 모든 짝수번째 element들 가져옴
- An+B 같은 함수 넣어서 모든 A번째 값들에서 B번째 element들 가져올 수 있음 (n은 0부터 시작)

```css
p span:only-of-type {}
```
- p 안에 span 타입이 유일한 경우

```css
div:last-of-type {}
```
- 특정 타입의 마지막 element를 가져옴

```css
div:empty {}
```
- 자식이 없는 element들 가져옴

```css
div:not(:first-child) {}
```
- :not(x) 는 x가 아닌 경우의 element들

```css
a[href] {}
input[type="checkbox"] {}
.toy[category^="Swim"] {}
img[src$=".jpg"] {}
img[src*="/thumbnailes/"] {}
```
- [attribute]는 해당 attribute를 가지고 있는 element들 의미
- [attribute="value"]는 attribute 값이 value인 모든 element들 의미
- [attribute^="value"]는 attribute 값이 value로 시작하는 element들 의미
- [attribute$="value"]는 attribute 값이 value로 끝나는 element들 의미
- [attribute*="value"]는 attribute 값에 value를 포함하고 있는 element들 의미

