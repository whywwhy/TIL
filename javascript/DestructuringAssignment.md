# 구조 분해 할당(Destructuring assignment)

### 1️⃣ 구조 분해 할당(Destructuring assignment)이란?
<hr/>

구조 분해 할당 구문은 배열이나 객체의 속성을 해체하여 그 값을 개별 변수에 담을 수 있게 하는 JavaScript 표현식

체나 배열에 저장된 데이터 전체가 아닌 일부만 필요한 경우가 

이럴 때 객체나 배열을 변수로 '분해’할 수 있게 해주는 특별한 문법인 구조 분해 할당(destructuring assignment) 을 사용

### 2️⃣ 배열 분해
<hr/>

```
let [firstName, surname] = []

alert(firstName); // undefined
alert(surname); // undefined
```

할당하고자 하는 변수의 개수가 분해하고자 하는 배열의 길이보다 크더라도 에러 발생 X
 
why??? 할당할 값이 없으면 undefined로 취급되기 때문

`=`을 이용하면 할당할 값이 없을 때 기본으로 할당해 줄 값인 '기본값(default value)'을 설정 ㄱㄴ

```
// 기본값
let [name = "Guest", surname = "Anonymous"] = ["Julius"]

alert(name)    // Julius (배열에서 받아온 값)
alert(surname) // Anonymous (기본값)
```

복잡한 표현식이나 함수 호출도 기본값 ㄱㄴ

기본식으로 표현식이나 함수를 설정하면 할당할 값이 없을 때 표현식이 평가되거나 함수가 호출됨

### 3️⃣ 객체 분해
<hr/>

```
let options = {
  title: "Menu",
  width: 100,
  height: 200
}
//  할당 연산자 우측엔 분해하고자 하는 객체를, 좌측엔 상응하는 객체 프로퍼티의 '패턴’을 넣는다. //
let {title, width, height} = options

alert(title)  // Menu
alert(width)  // 100
alert(height) // 200
```

`프로퍼티 options.title`과 `options.width, options.height`에 저장된 값이 상응하는 변수에 할당된 것을 확인. 

**참고로 순서는 중요하지 않**

```
let options = {
  title: "Menu",
  width: 100,
  height: 200
}

// { 객체 프로퍼티: 목표 변수 }
let {width: w, height: h, title} = options 

// width -> w
// height -> h
// title -> title

alert(title)   // Menu
alert(w)       // 100
alert(h)       // 200
```

콜론은 '분해하려는 객체의 프로퍼티: 목표 변수’와 같은 형태로 사용

 위 예시에선 프로퍼티 `width를 변수 w`에, 프로퍼티 `height를 변수 h`에 저장함

**프로퍼티가 없는 경우를 대비하여 =을 사용해 기본값을 설정하는 것도 가능~**

```
let options = {
  title: "Menu"
};

let {width: w = 100, height: h = 200, title} = options 

alert(title)   // Menu
alert(w)       // 100
alert(h)       // 200
```

콜론, 할당 연산자 동시 사용 가능

### 4️⃣ 중첩 구조 분해 (nested destructuring)
<hr/>

객체나 배열이 다른 객체나 배열을 포함하는 경우, 좀 더 복잡한 패턴을 사용하면 중첩 배열이나 객체의 정보를 추출할 수 있

이를 중첩 구조 분해(nested destructuring)

아래 예시에서 객체 `options`의 `size` 프로퍼티 값은 또 다른 객체<br/>
` items` 프로퍼티는 배열을 값으로 가지고 있다.

```
let options = {
  size: {
    width: 100,
    height: 200
  },
  items: ["Cake", "Donut"],
  extra: true
}
```

대입 연산자 좌측의 패턴은 정보를 추출하려는 객체` options`와 같은 구조

```
// 코드를 여러 줄에 걸쳐 작성해 의도하는 바를 명확히 드러냄
let {
  size: { // size는 여기,
    width,
    height
  },
  items: [item1, item2], // items는 여기에 할당함
  title = "Menu" // 분해하려는 객체에 title 프로퍼티가 없으므로 기본값을 사용함
} = options

alert(title)   // Menu
alert(width)   // 100
alert(height)  // 200
alert(item1)   // Cake
alert(item2)   // Donut
```

예시에서 size와 items 전용 변수는 없다는 점에 유의해야 함

 전용 변수 대신 size와 items 안의 정보를 변수에 할당했음