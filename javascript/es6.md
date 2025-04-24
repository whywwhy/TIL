![es6.png](attachment:e8e44bbd-2309-4ced-adda-d9c2884c7cbf:es6.png)

### ES6란

ES6(ECMAScript 6)는 2015년에 도입된 자바스크립트의 6번째 표준안이다. 현대적인 코드를 사용하면, 코드가 간결해지고 생산성이 향상된다. 이것이 ES6를 사용해야 하는 이유다.

### 변수 선언 방식의 차이 (var, let, const)

- `var`은 재정의와 재선언 모두 가능하다.
- `let`은 가변변수로 재정의가 가능하지만 재선언은 불가능하다.
- `const`는 불변변수로 재선언과 재정의 모두 불가능하다.
- 재선언: 똑같은 이름의 변수를 다시 만드는 것
- 재정의: 값이 지정된 변수에 값을 바꾸려는 것
- `스코프(scope)` : 식별자(ex. 변수명, 함수명, 클래스명 등)의 유효범위

```jsx
{
  let x = 10;
  const y = 20;
  // var z = 30;
}
console.log(x); // ReferenceError
console.log(y); // ReferenceError
```

- `var`의 문제점
    - ① 변수 선언이 유연하기 때문에 예기치 못한 값을 반환할 수 있다.
    - ② 코드가 길어진다면 어디에서 어떻게 사용 될지 파악하기 힘들다.
    - ③ 함수 레벨 스코프로 인해 함수 외부에서 선언한 변수는 모두 전역 변수로 된다.
    - ④ 변수 선언문 이전에 변수를 참조하면 언제나 undefined를 반환한다. (호이스팅 발생) → 따라서, var은 잘 사용하지 않으며, let과 const 키워드를 사용하는 것을 권장한다.

### **템플릿 리터럴 (Template Literals)**

- 백틱(`)을 사용해 문자열을 더 직관적으로 표현할 수 있음.
- ${변수} 문법으로 **문자열 안에서 변수나 표현식 삽입 가능**.

```jsx
const name = "이름";
const message = `안녕하세요, ${name}님!`;
console.log(message); // "안녕하세요, 이름님!"
```

### **화살표 함수 (Arrow Functions)**

- function 키워드 없이 함수를 간결하게 작성
- **this 바인딩이 없음** → 콜백에서 유용

```jsx
// 일반 함수
const add1 = function (a, b) {
  return a + b;
};

// 화살표 함수
const add2 = (a, b) => a + b;
```

**this 차이:**

```jsx
function Timer() {
  this.seconds = 0;
  setInterval(() => {
    this.seconds++;
    console.log(this.seconds); // 'this'가 Timer를 가리킴
  }, 1000);
}
```

- 인수가 하나밖에 없다면 인수를 감싸는 괄호를 생략할 수 있다.
- 인수가 하나도 없을 땐 괄호를 비워놓으면 된다. 다만, 이 때 괄호는 생략할 수 없다.
- 본문이 한 줄 밖에 없다면 중괄호를 생략할 수 있다.
- 중괄호는 본문 여러 줄로 구성되어 있음을 알려주며, 중괄호를 사용했다면 return으로 결괏값을 반환해주어야 한다.

## 모듈 내보내고 가져오기 (export/import)

모듈을 내보내는 방법으로는 named export와 default export가 있다.

```jsx
// named export 기본 형식
export { 모듈명1, 모듈명2 };
import { 모듈명1, 모듈명2 } from 'js 파일 경로';

// default export 기본 형식
export default 모듈명;
import 모듈명 from 'js 파일 경로';
```

`named export`는 한 파일에서 여러 개를 export할 때 사용 가능.
export한 이름과 동일한 이름으로 import해야 하며, 중괄호에 묶어서 import 해야 한다.

다른 이름으로 import 하려면 `as`를 사용하고, 한 파일에 있는 클래스나 변수들을 한 번에 import 하려면 `* as`를 사용한다.

```jsx
// named export는 중괄호 포함 import
import { named1, named2 } from './example.js';

// named export에서 as를 사용하여 다른 이름으로 import
import { named1 as myExport, named2 } from './example.js';

// 한 파일에 있는 모든 클래스나 변수를 * as를 사용하여 한 번에 import
import * as Hello from './example.js';
```

`default export`는 하나의 파일에서 단 하나의 변수 또는 클래스 등등만 export 할 수 있다. 
또한 import 할 때 아무 이름으로나 자유롭게 import 가능하며, 중괄호에 묶지 않아도 된다.

```jsx
// default export 는 중괄호 없이 import
import default1 from './example.js';
```

## 클래스 (class)

Class는 객체를 생성하기 위한 템플릿으로, 틀과 같은 역할

- 클래스를 선언하려면 `class` 키워드와 함께 클래스의 이름을 작성한다.
- 클래스는 함수로 호출될 수 없다.
- 클래스 선언은 let과 const처럼 블록 스코프에 선언되며, 호이스팅(hoisting)이 일어나지 않는다. 클래스는 반드시 정의한 뒤에 사용한다.
- 클래스의 메소드 안에서 `super` 키워드를 사용할 수 있다.
- `static` 키워드를 메소드 이름 앞에 붙여주면 해당 메소드는 정적 메소드가 됩니다.
- `Getter` 혹은 `Setter`를 정의하고 싶을 때는 메소드 이름 앞에 `get` 또는 `se`t을 붙여주면 된다.
- `extends` 키워드를 사용하여 클래스에서 다른 클래스로 상속하면서 클래스의 기능을 확장해 나갈수 있다.
- 클래스에서 일반적인 방식으로 프로퍼티를 선언하고 할당하면 `Public Property(공개 프로퍼티)` → 외부에서 프로퍼티에 접근하여 값을 사용하거나 수정이 가능
- 클래스에서 프로퍼티 앞에 `#` 키워드를 작성하여 선언하면 `Private Property (비공개 프로퍼티)`가 된다. → 오직 클래스 안에서만 사용, 변경이 가능. 외부 접근 불가

```jsx
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }
  nextYearAge() {  // 메서드 생성
    return Number(this.age) + 1;
  }
}

// 클래스 상속
class introducePerson extends Person {
  constructor(name, age, city, futureHope) {
    // super 키워드를 이용해서 자식 class에서 부모 메서드를 호출
    super(name, age, city);
    this.futureHope = futureHope
  }
  introduce () {
    return `저는 ${this.city}에 사는 ${this.name} 입니다.
	내년엔 ${super.nextYearAge()}살이며,
	장래희망은 ${this.futureHope} 입니다.`}
}

let kim = new introducePerson('kim','23','seoul', '개발자');
console.log(kim.introduce())
```

### **Destructuring (구조 분해 할당)**

객체나 배열에서 값을 **한 번에 꺼내는 문법**

객체와 배열의 값을 쉽게 변수로 저장할 수 잇다.

객체에서 값을 꺼낼 때는 중괄호를 사용해서 key와 같은 이름으로 꺼내올 수 있고, key와 다른 이름으로 꺼낼 때는 변수이름: 키값으로 꺼내올 수 있다.

```jsx
const introduce = {name: 'unknown', age: 23};
// key와 같은 이름으로 변수 선언
const { name, age } = introduce;
// 다른 이름으로 변수 선언 -> 변수이름: 키값
const { myName: name, myAge: age } = introduce;

console.log(myName) // unknown
console.log(myAge) // 23
```

배열에서 값을 꺼낼 때는 대괄호를 사용해서 앞에서부터 순차적으로 꺼내올 수 있다.

```jsx
const fruits = ['apple', 'mango', 'grape'];
// 앞에서부터 순차적으로 변수 선언 가능
const [zero, one, two] = fruits;

console.log(zero) // apple
```

### **Rest & Spread 연산자 (…연산자)**

**Rest (…args): 여러 값을 하나의 배열로 모음**

Rest Operator(나머지 매개변수)는 나머지 후속 매개변수들을 묶어 하나의 배열에 저장해서 사용하는 것이다. 묶어줄 매개변수 앞에 `...`을 붙여서 작성하면 된다.

즉, Rest Operator는 배열과 함수의 인자 중 나머지를 가리키며, 객체의 나머지 필드를 가리킨다.

```jsx
function sum(...numbers) {
  return numbers.reduce((acc, cur) => acc + cur, 0);
}
console.log(sum(1, 2, 3)); // 6
```

Rest Operator는 함수 정의에는 하나의 `...`만 존재할 수 있으며, 반드시 마지막 매개변수여야 한다.

**Spread: 배열/객체를 펼쳐서 복사하거나 합침**

Spread Operator(전개 구문)는 묶인 배열 혹은 객체를 개별적인 요소로 분리한다. 즉, Rest와 반대 개념이라고 생각하면 되고, 마찬가지로 전개할 매개변수 앞에 `...`을 붙여서 작성하면 된다.

따라서, 배열과 함수에선 또 다른 배열과 함수의 인자로의 전개를, 객체에선 또 다른 객체로의 전개를 한다.

```jsx
const arr = [1, 2];
const newArr = [...arr, 3]; // [1, 2, 3]

const obj = { a: 1 };
const newObj = { ...obj, b: 2 }; // { a: 1, b: 2 }
```

Spread Operator도 Rest Operator와 마찬가지로 `...`의 작성 순서에 주의해야 한다. 등장 순서에 따라, 덮어씌워 질 수 있기 때문이다.

### **삼항 연산자 (Ternary Operator)**

조건 ? 참일 때 : 거짓일 때 형태로 **간단한 조건문 처리**

```jsx
const age = 18;
const status = age >= 18 ? "성인" : "미성년자";
```

### **Optional Chaining (?.)**

**객체가 존재할 때만** 속성에 접근 → 에러 방지

```jsx
const user = { profile: { name: "이름" } };
console.log(user?.profile?.name); // "이름"
console.log(user?.job?.title); // undefined (오류)
```

### **Nullish Coalescing (??)**

null 또는 undefined일 때만 기본값 제공

```jsx
const input = null;
const value = input ?? "기본값"; // "기본값"
```

||는 falsy 값도 기본값 처리함 → 0, "", false도 걸러짐

??는 **null, undefined만** 걸러줌 → 더 정확함

### **Short-Circuit Evaluation (&&, ||)**

조건식이 **참/거짓이면** 이후 표현식 평가

```jsx
const isLogin = true;
isLogin && console.log("로그인 완료!"); // 조건이 true면 실행

const username = "";
console.log(username || "익명"); // username이 falsy면 "익명"
```

### **Default Parameters (기본 매개변수)**

함수 인자에 기본값을 줄 수 있음

```jsx
function greet(name = "손님") {
  console.log(`안녕하세요, ${name}님`);
}
greet(); // 안녕하세요, 손님님
greet("이름"); // 안녕하세요, 이름님
```

## forEach() / map() / reduce()

forEach()와 map()은 반복문을 돌며 배열 안의 요소들을 1대1로 짝지어 주는 역할

- `forEach()` : 배열 요소마다 한 번씩 주어진 함수(콜백)를 실행

> 배열.forEach((요소, 인덱스, 배열) => { return 요소 });
> 
- `map()` : 배열 내의 모든 요소 각각에 대하여 주어진 함수(콜백)를 호출한 결과를 모아 새로운 배열을 반환

> 배열.map((요소, 인덱스, 배열) => { return 요소 });
> 

하지만 forEach()와 map()은 역할은 같지만, 리턴값의 차이가 있다.

forEach()는 기존의 배열을 변경하는 반면, map()은 결과값으로 새로운 배열을 반환한다.

```jsx
var arr = [1,2,3,4,5];
// forEach()
var newArr = arr.forEach(function(e, i) {
  return e;
});
// return -> undefined

// map()
var newArr = arr.map(function(v, i, arr) {
  return v + 1;
});
// return -> 2, 3, 4, 5, 6
```

---

`reduce()` : 배열의 각 요소를 순회하며 callback함수의 실행 값을 누적하여 하나의 결과값을 반환

> 배열.reduce((누적값, 현잿값, 인덱스, 요소) => { return 결과 }, 초깃값);
> 

```jsx
result = sum.reduce((prev, curr, i) => {
  console.log(prev, curr, i);
  return prev + curr;
}, 0);
// 0 1 0
// 1 2 1
// 3 3 2
result; // 6
```

- 초깃값을 적어주지 않으면 자동으로 초깃값이 0번째 인덱스의 값이 된다.
- reduce()는 초깃값을 배열로 만들고, 배열에 값들을 push하면 map과 같아진다.