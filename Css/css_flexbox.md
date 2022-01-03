# CSS Flexbox

- justify-content
    
    - flex-start: 요소들을 컨테이너 왼쪽에 정렬

    - flex-end: 요소들을 컨테이너 오른쪽에 정렬
    
    - center: 요소들을 컨테이너 한 가운데 정렬
    
    - space-between: 요소들 사이에 동일한 간격
    
    - space-around: 요소들 주위에 동일한 간격

- align-items
    
    - flex-start: 요소들을 컨테이너 꼭대기로 정렬
    
    - flex-end: 요소들을 컨테이너 바닥으로 정렬
    
    - center: 요소들을 컨테이너의 세로선 상의 가운데로 정렬
    
    - baseline: 요소들을 컨테이너의 시작 위치에 정렬
    
    - stretch: 요소들을 컨테이너에 맞도록 늘림

- flex-direction
    
    - row: 요소들을 텍스트의 방향과 동일하게 정렬
    
    - row-reverse: 요소들을 텍스트의 반대방향으로 정렬
    
    - column: 요소들을 위에서 아래로 정렬
    
    - column-reverse: 요소들을 아래에서 위로 정렬

    - row-reverse나 column-reverse를 사용하는 경우 요소들의 start와 end 순서도 뒤바뀜

    - flex-direction 이 column 인 경우 justify-content 방향이 세로, align-items 방향이 가로로 바뀜

- order 

    - 기본 값은 0이며, 양수나 음수로 바꿀 수 있음

    - 작은 값이 있는 요소부터 출력

    - 컨테이너의 row나 column 순서를 역으로 바꾸는 것만으로는 충분하지 않을 때 order 속성 적용하여 순서 바꿀 수 있음

- align-self

    - 개별 요소에 적용할 수 있는 속성

    - align-items가 사용하는 값들(flex-start, flex-end, center, baseline, stretch)을 인자로 받으며 지정한 요소에만 적용됨

- flex-wrap

    - nowrap: 모든 요소들을 한 줄에 정렬
    
    - wrap: 요소들을 여러 줄에 걸쳐 정렬
    
    - wrap-reverse: 요소들을 여러 줄에 걸쳐 반대로 정렬

- flex-flow

    - flex-direction 과 flex-wrap 은 자주 같이 사용되므로 flex-flow가 이를 대신할 수 있음

- align-content

    - flex-start: 여러 줄들을 컨테이너의 꼭대기에 정렬

    - flex-end: 여러 줄들을 컨테이너의 바닥에 정렬

    - center: 여러 줄들을 세로선 상의 가운데에 정렬

    - space-between: 여러 줄들 사이에 동일한 간격

    - space-around: 여러 줄들 주위에 동일한 간격

    - stretch: 여러 줄들을 컨테이너에 맞도록 늘림

    - align-content는 여러 줄들 사이의 간격을 지정하며, align-items는 컨테이너 안에서 어떻게 모든 요소들이 정렬하는지를 지정

    - 한줄만 있는 경우 align-content는 효과가 나타나지 않음

    