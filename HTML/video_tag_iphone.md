# \<video\> tag 사용 시 iPhone 작동 이슈

## 0. 문제

```html
<video
poster="img.jpg"
muted
autoplay
loop
>
```

- \<video\> tag로 동영상 삽입하였는데 iPhone 에서 재생이 안됨

- poster : 업로드 안 될 시 표시될 이미지

- muted : 음성 제거. 자동재생을 원한다면 muted 추가해줘야 함.

- autoplay : 자동 재생

- loop : 반복 재생


<br/>

## 1. 해결

```html
<video
poster="img.jpg"
playsinline
muted
autoplay
loop
>
```
- playsinline 추가

    - PC 나 안드로이드에서는 자동재생 처리 시 인라인으로 볼 수 있지만 아이폰이나 아이패드에서는 전체 화면으로 처리됨

