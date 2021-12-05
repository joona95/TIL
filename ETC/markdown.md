# 1. 마크다운이란
일반 텍스트로 서식이 있는 문서를 작성하는 데 사용. 주로 github README.md 파일 작성에 많이 사용.
<br>
<br>

# 2. 마크다운 문법
## 1) 제목
* '#' 사용
```
# 제목1
## 제목2
### 제목3
#### 제목4
##### 제목5
###### 제목6
```
# 제목1
## 제목2
### 제목3
#### 제목4
##### 제목5
###### 제목6
<br>
* '===' 혹은 '---' 사용

```
제목
====
```
제목
====
```
부제목
---
```
부제목
---
<br>

## 2) 목록
* 순서가 있는 목록
```
1. 첫번째
2. 두번째
3. 세번째

1. 첫번째
12. 두번째
100. 세번째
```
1. 첫번째
2. 두번째
3. 세번째
<br>

1. 첫번째
12. 두번째
100. 세번째
<br>

* 순서가 없는 목록(```*```, ```+```, ```-```)
```
* 하나
  * 둘
    * 셋

+ 하나
  + 둘
    + 셋
    
- 하나
  - 둘
    - 셋
    
* 하나
  + 둘
    - 셋
      * 넷
```
* 하나
  * 둘
    * 셋

+ 하나
  + 둘
    + 셋
    
- 하나
  - 둘
    - 셋
    
* 하나
  + 둘
    - 셋
      * 넷

<br>

## 3) 인용문
```
> 인용문
> > 인용문
> > > 인용문
```
> 인용문
> > 인용문
> > > 인용문
<br>

## 4) 강조 (```*```, ```_``` 사용)
```
*이탤릭체*
_이탤릭체_
**볼드체**
__볼드체__
**_이탤릭체와 볼드체_**
~~취소선~~
```
*이탤릭체*
<br>
_이탤릭체_
<br>
**볼드체**
<br>
__볼드체__
<br>
**_이탤릭체와 볼드체_**
<br>
~~취소선~~
<br>

## 5) 띄어쓰기
```
&nbsp;&nbsp;&nbsp;
```
띄어&nbsp;&nbsp;&nbsp;쓰기
<br>

## 6) 줄바꿈
```
문장 뒤 세칸 띄어쓰기
문장 뒤 <br>
<p>문장</p>
```
문장 뒤 세칸 띄어쓰기.  
문장 뒤 <br>
<p>문장</p>

<br>

## 7) 링크
* 참조링크 : 같은 링크 URL 을 여러번 입력해야하거나 글 안의 링크를 따로 관리하고 싶을 때 사용
```
Link : [Google][googlelink]
[googlelink]: https://google.com "google"
```
Link : [Google][googlelink]
[googlelink]: https://google.com "google"
<br>

* 외부링크
```
Link : [Google](https://google.com, "google")
Link : <a href="https://google.com" target="_blank" title="google">Google</a>
```
Link : [Google](https://google.com, "google")
Link : <a href="https://google.com" target="_blank" title="google">Google</a>
<br>

* 일반적인 URL 링크, 이메일 링크
```
URL 링크: <https://google.com>
이메일 링크: <juna052@naver.com>
```
URL 링크: <https://google.com>
이메일 링크: <juna052@naver.com>
<br>

* 다른 md파일로 이동 : 상대 경로 이용
```
[README.md로 이동](../README.md)
```
[README.md로 이동](../README.md)

<br>

## 8) 수평선 : 페이지 나눌 때 많이 사용
```
* * *

***

*****

- - -

------------------
```
* * *

***

*****

- - -

------------------

<br>

## 9) 코드블록 
* "```" 사용

<pre>
<code>
```  
코드블록
```
</code>
</pre>

```
코드블록
```

<br>

* ```<pre><code></code></pre>``` 태그 사용
```
<pre>
<code>
코드블록
</code>
</pre>
```
<pre>
<code>
코드블록
</code>
</pre>

<br>

## 10) 요약
```
<details>
<summary>요약</summary>
  <div>내용</div>
</details>
```
<details>
<summary>요약</summary>
  <div>내용</div>
</details>

<br>

## 11) 이미지
```
![엑박시 보여질 이미지명](이미지주소 "마우스 댔을 때 나타날 문구")
<img src="이미지주소" width="100px" height="100px" title="마우스 댔을 때 나타날 문구" alt="이미지 대체 텍스트"></img>
```

<br>

## 12) 이모티콘
```
:blush:
:cry:
:heart:
:fire:
:+1:
:pray:
```
:blush:
:cry:
:heart:
:fire:
:+1:
:pray:
<br>

[이모지 참고](https://gist.github.com/rxaviers/7360908)
<br>

## 13) 테이블
```
제목1|제목2
-|-
내용1|내용2
내용3|내용4

제목1|제목2|제목3
:-|:-:|-:
내용1|내용2|내용3
```
제목1|제목2
-|-
첫번째 내용|두번째 내용
세번째 내용|네번째 내용

제목1|제목2|제목3
:-|:-:|-:
첫번재 내용|두번째 내용|세번째 내용

