WIL6

Flex(Flexible Box) : 명확한 개념, 속성으로 레이아웃을 쉽게 구성할 수 있음 -> 수직, 수평 구성 가능, 요소 크기가 불분명 or 동적임에도 각 요소를 정렬 O
Container : Items를 감싸는 부모 요소, Items 정렬을 위해서 필수, display, flex-flow, justify-content 등의 속성 사용 O
Items : order, flex, align-self 등의 속성 사용 O

Container
\*display : Flex Container를 정의. 같은 요소를 Flex로 정의함.
사용 예시 : display: flex;

\*flex-flow : flex-direction + flex-wrap (단축 속성). 주 축 설정 + Items의 여러 줄 묶음(줄 바꿈)도 설정 (default는 row, nowrap)
사용 예시 : flex-flow: column wrap;

\*flex-direction : Flex의 주 축 설정.
row : 좌에서 우로( 수평 배치. 왼쪽에서부터 A B C
row-reverse : 우에서 좌로 수평 배치. 오른 쪽에 붙어서 왼쪽부터 C B A(시작점이 바뀜)
column : 위에서 아래로 수직 배치. 세로로 위에서부터 A B C
column-reverse : 아래에서 위로 수직 배치. 아래쪽으로 붙어서 위에서부터 C B A(시작점이 바뀜)
row의 주축은 수평, column의 주축은 수직
사용 예시 flex-direction: row;

\*flex-wrap : Flex Items의 여러 줄 묶음(줄 바꿈) 설정
nowrap : Items를 1행에 배치(default 값)
wrap : flex items width 합계 > flex 컨테이너 width -> items을 복수행에 배치
wrap-reverse : wrap;과 동일 but, 아래에서 위로 배치.
사용 예시 : flex-wrap: wrap;

\*justify-content : 주 축의 정렬 방법 설정
flex-start: 요소들을 컨테이너의 왼쪽으로 정렬
flex-end: 요소들을 컨테이너의 오른쪽으로 정렬
center: 요소들을 컨테이너의 가운데로 정렬
space-between: 요소들 사이에 동일한 간격
space-around: 요소들 주위에 동일한 간격
사용 예시 : justify-content: flex-end;

\*align-content : 교차 축의 정렬 방법 설정(2줄 이상). flex container의 cross axis를 기준으로 flex item을 수직 정렬
stretch : 모든 flex item은 행 이후에 균등하게 분배된 공간에 정렬되어 배치
flex-start: 모든 flex item은 flex container의 cross start 기준으로 stack 정렬
flex-end: 모든 flex item은 flex container의 cross end 기준으로 stack 정렬
center: 모든 flex item은 flex container의 cross axis의 중앙에 stack 정렬
space-between : 첫번째 flex item의 행은 flex container의 상단에. 마지막 flex item의 행은 flex container의 하단에 배치되며 나머지 행은 균등 분할된 공간에 배치 정렬
space-around : 모든 flex item은 균등 분할된 공간 내에 배치 정렬
사용 예시 : align-content: space-around;

\*align-items : 교차 축에서 Items의 정렬 방법 설정(1줄). flex container의 수직 방향(cross axis)으로 정렬(모든 flex item에 적용)
flex-start: 요소들을 컨테이너의 꼭대기로 정렬
flex-end: 요소들을 컨테이너의 바닥으로 정렬
center: 요소들을 컨테이너의 세로선 상의 가운데로 정렬
baseline: 요소들을 컨테이너의 시작 위치에 정렬
stretch: 요소들을 컨테이너에 맞도록 늘림
사용 예시 : align-items: flex-end;

스테이지 1
justify-content: flex-end;
스테이지 2
justify-content: center;
스테이지 3
justify-content: space-around;
스테이지 4
justify-content: space-between;
스테이지 5
align-items: flex-end;
스테이지 6
justify-content: center;
align-items: center;
스테이지 7
justify-content: space-around;
align-items: flex-end;
스테이지 8
flex-direction: row-reverse;
스테이지 9
flex-direction: column;
스테이지 10
flex-direction: row-reverse;
justify-content: flex-end;
스테이지 11
flex-direction: column;
justify-content: flex-end;
스테이지 12
flex-direction: column-reverse;
justify-content: space-between;
스테이지 13
flex-direction: row-reverse;
justify-content: center;
align-items: flex-end;
스테이지 18
flex-wrap: wrap;
스테이지 19
flex-direction: column;
flex-wrap: wrap;
스테이지 20
flex-flow: column wrap;
