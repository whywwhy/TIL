# 보여지는 속성

### 1️⃣ display
<hr/>
css에서 렌더링을 결정할 때 display 속성에 의해 크게 좌우됨

display 속성은 상속하지 X.

### block
1. block 엘리먼트가 등장 -> 항상 새로운 라인 시작

2. 부모의 width 전체를 차지 (width를 부모의 width보다 적게 주어도 나머지 공간은 비움 / 공간적으로는 부모의 width를 전부 차지)

3. block 레벨 요소
(div, h1 ~ h6, p, ol, ul, li, hr, table)

### inline
1. content의 너비만큼 가로폭을 차지

2. width, height, margin-top, margin-bottom, padding-top, padding-bottom 프로퍼티를 사용 X

3. inline 레벨 사이 정의 X 4px 여백이 기본적 생김

4. inline 요소가 하나라도 생성 -> 가상의 라인 박스 공간이 발생

5. inline 요소 안에 block 요소가 O -> 그 즉시 새로운 block 공간 부모의 영역을 벗어나 생김

6. `<span><div></div></span>`

7. `<span>a</span>`

8. inline 레벨 요소 예
(span, a, strong, img, br, input, select, textarea, button)

### Positioning Schemes

1. Normal flow: block 요소들은 block formatting context에 의해, inline 요소들은 inline formatting context에 의해 레이아웃이 결정 <br/>block, inline 모두 relative positioning에 추가적인 렌더링 존재

2. Floats: float이 적용된 요소 normal flow로 부터 빠져나와 텍스트 및 인라인 요소들이 자신보다 좌우로 배치

3. Absolute positioning: absolute positioning 모델은 특정 기준에 따라 블록의 위치를 새롭게 할당

### Line box
inline 요소들을 연속적으로 나열하면 위에서 부터 쌓이게 됨.
-> `vertical-align` 속성을 사용하여 중앙으로 정렬

모두 중앙으로 정렬을 할 때, 중앙이라고 판단해야 할 기준 -> vertical-align에서 받을 수 있는 속성 baseline, bottom, initial, middle, sub, super, text-bottom, text-top, top, unset 등

이러한 값들이 적용되게 하려면 어떤 명확한 기준이 필요
-> 기준이 line-box.

 inline 요소가 존재하면 바로 line-box 모델이 inline 요소를 감싸게. 
 
 line-box는 가상의 엘리먼트로 DOM에는 표현이 되지 않지만, layout을 할 때 기준이 되기 때문에 명확히 존재

 -> 이 존재를 strut라고 함


### 2️⃣ Visibility
<hr/>

visibility는 요소가 보일지 말지를 정의

- visible : 요소를 보이게
- hidden : 요소를 보이지 않게
- collapse : table 요소에 사용하며 행이나 열을 보이지 않게
- none : table 요소의 row나 column을 보이지 않게

display : none 과 visibility : hidden 의 차이점?

visibility 는 공간이 존재하고 보이지만 않는 것 -> `display : none` 은 공간도 존재 X

### 3️⃣ Opacity
<hr/>

요소의 투명도를 정의하며, 0.0 ~ 1.0의 값의 범위를 갖는다. 0.0은 투명, 1.0은 불투명이다.

opacity 요소는 자식 요소들에게도 영향을 미치게