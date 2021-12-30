# 서버 사이드 렌더링 (SSR) 과 클라이언트 사이드 렌더링 (CSR)

## Static Sites (1990)

- 페이지 내에서 링크를 클릭하면 다시 서버에서 해당 페이지 html을 받아와서 전체 페이지가 업데이트됨

- 전체 페이지가 업데이트되기 때문에 페이지 이동 시에 깜빡거리는 blinking issue 발생

<br>

## iframe (1996)

- html 문서 내에 또 다른 문서를 담을 수 있는 iframe 태그 도입

- 페이지 내에서 부분적으로 문서를 받아와서 일부분만 업데이트할 수 있게 됨

<br>

## XMLHttpRequest (1998)

- fetch API의 원조인 XMLHttpRequest 개발

    - fech API 란?

        XMLHttpRequest와 비슷하지만 Promise를 기반으로 구성되어 있어서 비동기 http요청을 좀 더 쓰기 편하게 해주는 API

- html 문서 전체가 아니라 JSON과 같은 포맷으로 서버에서 필요한 데이터만 받아올 수 있게 됨

- 데이터를 받아서 JavaScript에서 html 요소를 동적으로 생성해서 페이지를 업데이트함

<br>

## AJAX (2005)

- XMLHttpRequest 방식이 공식적으로 AJAX라는 이름을 가지게 됨

- 구글에서 AJAX를 이용하여 Gmail, Google Maps 같은 어플리케이션 만듦

- SPA (Single Page Application) 
    - 하나의 앱을 사용하는 것처럼 웹에서도 한 페이지에서 필요한 부분적인 정보들만 업데이트

<br>

## CSR (Client Side Rendering)

- html은 거의 비어있고 링크된 js 파일을 서버에서 다운로드하고 필요한 데이터는 JSON 데이터로 받아옴

- 링크된 js 파일에는 어플리케이션에 필요한 로직들과 어플리케이션을 구동하는 프레임워크와 라이브러리의 소스코드들도 다 포함되어 사이즈가 굉장히 큼.

- 번들링해서 보내주는 js 파일을 어떻게 분리해서 필수적인 아이만 먼저 보낼 수 있을지 고민이 필요

#### **장점**

- 첫 로딩만 기다리면 url이 바뀌어도 html을 다시 내려받지 않고 동적으로 빠르게 렌더링 되기 때문에 사용자 경험에 좋음

- 서버에게 요청하는 횟수가 적어 서버의 부담이 덜함

#### **단점**
- 모든 파일이 로드될 때까지 기다려야 하므로 클라이언트가 첫화면 보기까지 오래걸림

    - 프로젝트가 커질수록 파일의 크기가 커지므로 처음에 파일 로드하는 시간이 더 오래 걸림

    - 코드 분리로 일정 부분 해결 가능. url 마다 각각의 번들링된 js파일을 만들어서 요청 시에 다운받게 하는 방식으로 완화 가능하지만 완전 해결은 불가능.

- 좋지 않은 SEO(Search Engine Optimization) 
    - 많은 검색 엔진들이 html 분석하여 이용되는데 빈 html을 가진 CSR은 불리함

<br>

## SSR(Sever Side Rendering)

- CSR의 문제점들 때문에 Static Sites에서 영감 받아 도입됨

- 서버에서 필요한 데이터를 모두 가져와서 html을 만들고 만들어진 html을 동적으로 제어할 수 있는 js와 함께 클라이언트에 보내줌

- 시간의 단차를 어떻게 줄일 수 있을지와 어떻게 유연한 UX를 보여줄지에 대한 고민이 필요

#### **장점**

- 첫번째 페이지 로딩이 빨라짐

- 모든 컨텐츠가 html에 담겨져서 더 나은 SEO

#### **단점**

- Static Sites에서 존재했던 blinking issue 여전히 존재
    
    - 사용자가 클릭하게 되면 전체 페이지를 서버에서 받아오는 것과 동일하기 때문에 사용자 경험에 좋지 않음

- 서버 과부하 걸리기 좋음

    - 사용자 클릭 시 서버에 요청이 들어가는데 사용자가 많을 수록 문제 생길 수 있음

- 사용자가 빠르게 웹사이트확인할 수 있어도 동적으로 데이터 처리하는 js를 아직 다운 못해서 클릭해도 반응이 없는 경우 발생 가능

<br>

## TTV(Time to view)와 TTI(Time to interact)

#### **CSR**

1) 클라이언트에서 서버에 요청

2) 서버에서 html 파일 제공 (html은 비어있어서 웹에서 아무것도 확인 불가)

3) 클라이언트에서 html에 링크된 js 서버에 요청

4) 서버에서 js를 받아오게됨. 이 순간부터 웹사이트를 확인할 수 있어짐 이순간 클릭도 가능

- 사용자가 웹사이트 볼 수 있을 때(TTV) 클릭하거나 인터랙션(TTI)도 가능

#### **SSR**

1) 클라이언트에서 서버에 요청

2) 서버에서 잘 만들어진 html 제공. 이순간 웹사이트 확인 가능(TTV). 아직 동적으로 사용가능한 js 못받아옴.

3) 서버에 js 요청

4) js 제공받으면 사용자가 클릭하거나 인터랙션 가능(TTI) 

- 사용자가 화면을 볼 수 있는 시간과 실제 인터랙션 가능한 시간 사이에 공백이 존재

<br>

## SSG(Static Site Generation)
- React + Gatsby(static site generator) -> 정적 + 동적 사용 가능

- SSR(Server Site Rendering)
React + Next.js -> Static generation도 지원

<br>

## +)

- 로그인이 필요없는 페이지는 SEO때문에 SSR로, 로그인이 필요한 페이지는 어차피 SEO에 영향을 안받으니까 CSR로 만든후에 ServiceWorker를 붙이는 방식 사용하면 좋음