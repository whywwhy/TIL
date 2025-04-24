![자습문법.png](attachment:f0285365-6036-408a-960e-87a030a8df94:자습문법.png)

| **문법** | **주 용도** |
| --- | --- |
| Hoisting | 변수/함수 선언 위치와 실제 실행 순서 이해 |
| Scope | 변수 접근 가능 여부 파악 |
| Closures | 외부 상태 기억하는 함수 만들기 |
| Async/Await | 비동기 로직을 깔끔하게 |
| Callback | 비동기 처리의 기본 |
| try/catch | 오류 안전하게 처리 |
| Rest/Spread | 유연한 배열·객체 처리 |
| Destructuring | 객체/배열 분해해서 쓰기 |
| Ternary | 간결한 조건 처리 |
| Optional Chaining 등 | 안전한 접근, 기본값 설정 |
| map/filter/reduce | 배열의 핵심 변형 도구 |

### 비동기 프로그래밍

**Async/Await**

비동기 작업을 마치 **동기 코드** 처럼 보이게 해주는 문법.

Promise 기반 함수 앞에 await를 붙이면 해당 작업이 완료될 때까지 기다립니다.

```jsx
async function fetchData() {
  try {
    const res = await fetch('https://api.example.com/data');
    const json = await res.json();
    console.log(json);
  } catch (err) {
    console.error('에러 발생:', err);
  }
}
```

**Callback**

**함수를 인자로 넘겨서**, 특정 작업이 끝난 후 실행되도록 만드는 방식입니다.

```jsx
function greeting(name, callback) {
  console.log(`안녕, ${name}`);
  callback(); // 작업 완료 후 실행
}

greeting('이름', () => {
  console.log('콜백 함수 실행');
});
```

### try/catch

코드 실행 중 오류가 발생했을 때 프로그램이 멈추지 않도록 예외 처리를 해줍니다.

```jsx
try {
  // 오류가 날 수 있는 코드
  let result = riskyFunction();
} catch (error) {
  console.error('에러가 발생했어요:', error);
}
```

### scope (스코프)

변수가 **어디에서 접근 가능한지**를 정의합니다. (변수 유효 범위)

- **Global Scope**: 어디서나 접근 가능
- **Function Scope**: 함수 안에서만 접근 가능
- **Block Scope** (let, const 사용 시): {} 내부에서만 접근 가능

```jsx
function test() {
  let a = 10;
  console.log(a); // 가능
}
console.log(a); // 에러! 함수 밖에서는 접근 불가
```

### fetch API

브라우저 내장 함수로, 서버에 **HTTP 요청**을 보내고 결과를 받아옵니다.

```jsx
fetch('https://api.example.com')
  .then(response => response.json())
  .then(data => console.log(data));
```

### hoisting (호이스팅)

변수나 함수 선언이 **코드 실행 전에 끌어올려지는 현상**입니다.

**주의**: 선언만 끌어올려지고, 할당은 끌어올려지지 않음.

```jsx
console.log(x); // undefined (var만 해당)
var x = 5;

foo(); // 실행됨
function foo() {
  console.log('Hello');
}
```

let, const는 호이스팅은 되지만 초기화 전엔 접근 불가(**“Temporal Dead Zone”** 때문에) → (ReferenceError 발생)

### rest & spread operator (…)

- **Rest**: 남은 값을 배열로 모음
- **Spread**: 배열이나 객체를 **펼침**

```jsx
// Rest 예시
function sum(...numbers) {
  return numbers.reduce((a, b) => a + b);
}

// Spread 예시
const arr1 = [1, 2];
const arr2 = [...arr1, 3, 4]; // [1, 2, 3, 4]
```

### ternary operator (삼항 연산자)

조건에 따라 **값을 간단히 선택**할 수 있습니다.

```jsx
const age = 18;
const msg = age >= 18 ? '성인입니다' : '미성년자입니다';
```

### **destructuring** (구조분해할당)

배열이나 객체에서 **값을 쉽게 꺼내서 변수로 만드는 문법**입니다.

```jsx
const user = { name: '철수', age: 20 };
const { name, age } = user; // name='철수', age=20

const arr = [1, 2, 3];
const [first, second] = arr; // first=1, second=2
```

### closures (클로저)

**함수 안의 함수가 바깥 함수의 변수에 접근**할 수 있는 개념입니다.

→ 함수가 **자신이 선언될 때의 외부 변수**를 기억하여 나중에 접근할 수 있는 특성.

```jsx
function outer() {
  let count = 0;
  return function inner() {
    count++;
    console.log(count);
  };
}

const counter = outer();
counter(); // 1
counter(); // 2
```

counter는 outer()의 count 변수에 계속 접근 가능 

### **optional chaining / nullish coalescing / short circuit**

**📍 optional chaining ?.**

객체의 깊은 속성을 접근할 때, **존재하지 않아도 에러가 나지 않도록** 해줍니다.

```jsx
const user = {};
console.log(user.profile?.name); // undefined (에러 아님!)
```

**📍 nullish coalescing ??**

값이 null 또는 undefined일 경우에만 **기본값**을 설정합니다.

```jsx
const name = null;
const displayName = name ?? '익명'; // '익명'
```

**📍 short circuit (&&)**

앞의 조건이 참일 때만 뒤의 코드 실행합니다.

```jsx
isLoggedIn && showProfile(); // 로그인 상태일 때만 실행
```

### **map, filter, reduce**

배열을 다룰 때 유용한 메서드들입니다.

**📍 map: 배열 요소를 변형**

```jsx
const nums = [1, 2, 3];
const doubled = nums.map(n => n * 2); // [2, 4, 6]
```

**📍 filter: 조건에 맞는 요소만 필터링**

```jsx
const nums = [1, 2, 3, 4];
const even = nums.filter(n => n % 2 === 0); // [2, 4]
```

**📍 reduce: 배열을 누적 처리해서 하나의 값으로 만듦**

```jsx
const nums = [1, 2, 3];
const sum = nums.reduce((acc, cur) => acc + cur, 0); // 6
```