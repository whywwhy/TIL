# SCSS

![alt text](img/이글을봐scss.png)

### 1️⃣ SCSS 가 뭘까?
<hr/>

CSS는 HMTL 태그를 꾸미거나 효과를 넣어 주는 등 디자인 요소를 추가할 때 사용하는 전처리 과정

but 프로젝트 규모가 커지거나 작업이 고도화 -> CSS는 불가피하게 `가독성이 떨어지는 등 유지보수의 어려움을 주는 요소`가 됨.
<br/> `코드의 재사용성을 올리고, 가독성을 올리는 등` CSS에서 보이던 단점을 보완하고, 개발의 효율을 올리기 위해 등장한 개념이 SASS / SCSS

Sass (Syntactically Awesome Style Sheets: 문법적으로 짱 멋진 스타일시트) 는 CSS pre-processor! 

CSS의 태생적 한계를 보완하기 위해 Sass는 유용한 도구들을 제공한다

### 설치 방법 
```
npm i sass --save
```

```
yarn add sass 
```

### 2️⃣ Sass와 SCSS 차이
<hr/>

Sass (Syntactically Awesome Style Sheets)의 3버전에서 새롭게 등장한 SCSS는 CSS 구문과 완전히 호환되도록 새로운 구문을 도입해 만든 Sass의 모든 기능을 지원하는 CSS의 상위집합~!

즉, SCSS는 CSS와 거의 같은 문법으로 Sass 기능을 지원

### Sass
```
.list
  width: 100px
  float: left
  li
    color: red
    background: url("./image.jpg")
    &:last-child
      margin-right: -10px
```

### SCSS
```
.list {
  width: 100px;
  float: left;
  li {
    color: red;
    background: url("./image.jpg");
    &:last-child {
      margin-right: -10px;
    }
  }
}
```

간단한 차이는 {}(중괄호)와 ; (세미콜론)의 유무......

또 하나의 차이점은 mixin (재사용 가능한 기능을 만드는 방식)

기능을 재사용하기 위해서 Sass의 경우 =로 선언하고 +로 적용

SCSS의 경우 @mixin으로 선언하고 @include로 적용

```
=border-radius($radius)
  -webkit-border-radius: $radius
  -moz-border-radius:    $radius
  -ms-border-radius:     $radius
  border-radius:         $radius

.box
  +border-radius(10px)
```
```
@mixin border-radius($radius) {
  -webkit-border-radius: $radius;
     -moz-border-radius: $radius;
      -ms-border-radius: $radius;
          border-radius: $radius;
}

.box { @include border-radius(10px); }
```

- Sass는 좀 더 간결하고 작성하기 편리, **{}**나 **;**를 사용하지 않아도 되니 코드가 훨씬 깔끔
- SCSS는 인라인 코드(한 줄 작성)를 작성, CSS와 유사한 문법을 가지기 때문에 코드 통합이 훨씬 쉬움

### 3️⃣ 장점
<hr/>

- CSS보다 심플한 표기법으로 CSS를 구조화하여 표현 ㄱㄴ
- 스킬 레벨이 다른 팀원들과의 작업 시 발생할 수 있는 구문의 수준 차이를 평준화 ㄱㄴ
- CSS에는 존재하지 않는 Mixin 등의 강력한 기능을 활용하여 CSS 유지보수 편의성을 큰 폭으로 향상 O


SCSS는 중첩, 변수 선언, 연산자 등 많은 장점

대표적인 장점인 셀렉터 중첩기능

### CSS
```
nav ul {
  margin: 0;
  padding: 0;
  list-style: none;
}
nav li {
  display: inline-block;
}
nav a {
  display: block;
  padding: 6px 12px;
  text-decoration: none;
}
```
### Sass
```
nav
  ul
    margin: 0
    padding: 0
    list-style: none

  li
    display: inline-block

  a
    display: block
    padding: 6px 12px
    text-decoration: none
```
### SCSS
```
nav {
  ul {
    margin: 0;
    padding: 0;
    list-style: none;
  }

  li { display: inline-block; }

  a {
    display: block;
    padding: 6px 12px;
    text-decoration: none;
  }
}
```

셀렉터 안에 셀렉터를 넣어 중첩을 시켜 가독성이 좋아졋당~~ 야호...