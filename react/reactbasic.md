![리액트.png](attachment:4a6d6322-c264-4c7c-ba7a-ea6f1d1d881d:리액트.png)

### **react-router**

리액트는 SPA(Single Page Application)라서 페이지 이동 시 전체를 새로고침하지 않음.

이를 가능하게 해주는 게  **react-router**입니다.

```
npm install react-router-dom
```

```jsx
// App.jsx
import { BrowserRouter, Routes, Route } from 'react-router-dom';
import Home from './Home';
import About from './About';

function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
      </Routes>
    </BrowserRouter>
  );
}
```

### events **(이벤트 핸들러)**

사용자의 클릭, 입력 등의 **행동을 처리하는 함수**입니다.

```jsx
function Button() {
  const handleClick = () => {
    alert('클릭됨!');
  };
  return <button onClick={handleClick}>Click me</button>;
}
```

onClick, onChange, onSubmit 등 다양한 이벤트가 있음.

### JSX

JavaScript 안에서 HTML처럼 작성할 수 있게 해주는 문법입니다.

**JSX는 결국 JavaScript 객체로 변환**

```jsx
const element = <h1>Hello, world!</h1>;
```

조건문, 변수 삽입 등도 가능:

```jsx
const name = '이름';
const greeting = <h1>Hello, {name}!</h1>;
```

### props

부모 컴포넌트 → 자식 컴포넌트로 **데이터를 전달**하는 방식입니다.

```jsx
function Greeting({ name }) {
  return <h1>안녕, {name}</h1>;
}

<Greeting name="이름" />
```

props는 읽기 전용입니다!

### **components life cycle**

![image.png](attachment:406b8fae-d299-471e-86a0-a4f2b9383a4b:image.png)

컴포넌트는 **생성 → 업데이트 → 제거**의 과정을 거칩니다.

클래스 컴포넌트에서는 메서드로, 함수 컴포넌트에서는 useEffect로 다룹니다.

- mount (처음 렌더링)
- update (상태 변경 시)
- unmount (제거될 때)

```jsx
useEffect(() => {
  console.log('컴포넌트 마운트됨');

  return () => {
    console.log('컴포넌트 언마운트됨');
  };
}, []);
```

### list & keys

여러 항목을 반복 렌더링할 때 key를 꼭 줘야 합니다.

key는 항목을 고유하게 식별하는 용도!

```jsx
const items = ['사과', '바나나', '포도'];

<ul>
  {items.map((item, index) => (
    <li key={index}>{item}</li>
  ))}
</ul>
```

가능하면 index보다 **고유 ID**를 쓰는 게 좋아요.

### **conditional rendering**

조건에 따라 다른 UI를 보여주는 기법입니다.

```jsx
{isLoggedIn ? <Profile /> : <LoginForm />}
```

간단히 && 도 사용 가능:

```jsx
{messages.length > 0 && <Notification />}
```

### hooks (훅)

함수형 컴포넌트에서 상태나 생명주기 기능을 쓸 수 있도록 도와주는 함수입니다.

**기본 훅**

**📍 useState**

컴포넌트의 **상태 값을 관리**합니다.

```jsx
const [count, setCount] = useState(0);

<button onClick={() => setCount(count + 1)}>+</button>
```

---

**📍 useEffect**

렌더링 이후에 **사이드 이펙트**를 처리합니다 (데이터 fetch, 타이머 등).

```jsx
useEffect(() => {
  console.log('렌더링 후 실행됨');
}, [count]); // count가 바뀔 때마다 실행
```

 **추가 훅들**

**📍 useId**

고유한 ID를 생성할 때 사용합니다 (접근성 등에서 유용).

```jsx
const id = useId();
<label htmlFor={id}>이름</label>
<input id={id} />
```

---

**📍 useRef**

- DOM 요소를 참조하거나
- 렌더링과 무관한 값을 저장할 때 사용합니다.

```jsx
const inputRef = useRef();

function focusInput() {
  inputRef.current.focus();
}
```

---

**📍 useMemo**

값을 **캐싱(메모이제이션)**해서 성능 최적화할 때 사용합니다.

```jsx
const expensiveValue = useMemo(() => {
  return slowFunction(input);
}, [input]);
```

---

**📍 useReducer**

useState보다 복잡한 상태 로직을 관리할 때 사용합니다.

**Redux 스타일**의 상태 관리 방식입니다.

```jsx
function reducer(state, action) {
  switch (action.type) {
    case 'increment':
      return { count: state.count + 1 };
  }
}

const [state, dispatch] = useReducer(reducer, { count: 0 });
```

---

**📍 useContext**

컴포넌트 트리 전체에서 **전역 데이터를 공유**할 때 사용합니다.

```jsx
const ThemeContext = createContext();

function App() {
  return (
    <ThemeContext.Provider value="dark">
      <Header />
    </ThemeContext.Provider>
  );
}

function Header() {
  const theme = useContext(ThemeContext); // 'dark'
}
```

---

**📍 useTransition**

UI의 상태 업데이트를 **더 부드럽게 처리**하는 데 사용합니다.

느린 업데이트를 우선순위를 낮춰서 처리할 수 있습니다.

```jsx
const [isPending, startTransition] = useTransition();

startTransition(() => {
  setInputValue(newValue); // 이건 낮은 우선순위로 실행됨
});
```

- useState, useEffect 차이
    
    
    | **항목** | useState | useEffect |
    | --- | --- | --- |
    | 역할 | **상태(state)**를 저장하고 업데이트함 | **부수 효과(side effects)**를 처리함 |
    | 사용하는 경우 | 값이 바뀌면 **화면이 다시 렌더링**되어야 할 때 | 렌더링 후 **무언가를 실행해야 할 때** (ex. API, 타이머) |
    | 리렌더 트리거 | setState 호출 시 | 상태/props 변경 후 자동 실행됨 (deps 기준) |
    | 실행 시점 | 초기값으로 렌더링 시 | 렌더링 이후 실행됨 (비동기처럼 동작) |
    | 반환값 | [state, setState] 배열 | 없음 (콜백 함수 실행만 함) |
    
    ---
    
    **useState 예시: 버튼 클릭 시 숫자 증가**
    
    ```jsx
    import { useState } from 'react';
    
    function Counter() {
      const [count, setCount] = useState(0); // 상태 정의
    
      return (
        <div>
          <p>현재 카운트: {count}</p>
          <button onClick={() => setCount(count + 1)}>증가</button>
        </div>
      );
    }
    ```
    
    상태 값 count를 렌더링하고, 버튼 클릭 시 setCount로 값을 업데이트.
    
    → 이때 **컴포넌트가 다시 렌더링**됨
    
    ---
    
    **useEffect 예시: 컴포넌트가 화면에 뜰 때 API 요청**
    
    ```jsx
    import { useEffect, useState } from 'react';
    
    function UserInfo() {
      const [user, setUser] = useState(null);
    
      useEffect(() => {
        // 마운트 시 1회 실행
        fetch('/api/user')
          .then(res => res.json())
          .then(data => setUser(data));
      }, []); // 의존성 배열 비어 있음 → 최초 1회 실행
    
      return (
        <div>
          {user ? <p>{user.name}님 환영합니다!</p> : <p>로딩 중...</p>}
        </div>
      );
    }
    ```
    
    화면에 **처음 그려질 때만 실행**해서 API 요청.
    
    이건 state만으로는 못하는 **사이드 이펙트**
    
    ---
    
    - useState → 컴포넌트 안에서 데이터를 **기억**해줌
    - useEffect → 렌더링 이후 **행동**해줌
    
    ---
    
    |  **** | **사용하는 훅** |
    | --- | --- |
    | 숫자 증가/감소, 토글 상태 관리 | useState |
    | 버튼 클릭해서 모달 열기 | useState |
    | API 호출 (컴포넌트 처음 뜰 때) | useEffect |
    | 타이머 설정 / 이벤트 리스너 등록 | useEffect |
    | 로컬스토리지에서 값 읽고 세팅 | useEffect + useState |

- 상태 관리: **useState vs useReducer**
    
    
    | **항목** | useState | useReducer |
    | --- | --- | --- |
    | 사용 목적 | 간단한 상태 값 (ex. 토글, 숫자 증가) | 복잡한 상태 로직 (ex. 여러 상태, 상태 간 관계) |
    | 상태 갯수 | 하나씩 관리 | 여러 상태를 하나의 객체로 관리 가능 |
    | 업데이트 방식 | 직접 값 설정 | dispatch를 통해 액션 전달 |
    | 구조 | [state, setState] | [state, dispatch] |
    | 예시 | setCount(count + 1) | dispatch({ type: 'increment' }) |
    
    useState는 빠르고 간단함.
    
    useReducer는 상태 변화가 복잡한 폼, 토글 조합 등에 적합.
    
- 상태 변화 감지, 처리: **useEffect vs useLayoutEffect**
    
    
    | **항목** | useEffect | useLayoutEffect |
    | --- | --- | --- |
    | 실행 시점 | 브라우저 페인트 후 | 페인트 전에 (즉시) |
    | 사용 예 | API 요청, 타이머 설정 | DOM 측정, 위치 계산 |
    | 렌더링 차단 여부 | 안 함 | 함 (렌더 전 실행됨) |
    
    useLayoutEffect는 거의 안 쓰지만, 
    **정확한 DOM 사이즈를 측정하거나 애니메이션 시작 전** 꼭 필요한 경우 사용함.
    
- 전역 상태 공유: **props vs useContext**
    
    
    | **항목** | props | useContext |
    | --- | --- | --- |
    | 전달 방식 | 부모 → 자식 직접 전달 | 전역적으로 공유 |
    | 깊이 있는 구조에서 | 전달 코드가 많아짐 | 중간 단계 생략 가능 |
    | 유연성 | 더 명확하고 직관적 | 전역화로 구조 파악 어려움 가능 |
    
    props는 데이터 흐름이 명확해서 **작은 규모**에서 좋습니다.
    
    useContext는 **테마, 인증 정보, 언어 설정** 등 전역적일 때 좋습니다.
    
- 렌더링 최적화: **useMemo vs useCallback**
    
    
    | **항목** | useMemo | useCallback |
    | --- | --- | --- |
    | 반환값 | **값을 캐싱** | **함수를 캐싱** |
    | 사용 목적 | 계산 결과 재사용 | 함수 재생성 방지 (불필요 렌더 방지) |
    | 타입 | const result = useMemo(...) | const fn = useCallback(...) |
    
    useMemo는 **무거운 계산 최적화**에,
    useCallback은 **자식 컴포넌트에 함수 전달 시** 유용.
    
- DOM 제어: **useRef vs useId**
    
    
    | **항목** | useRef | useId |
    | --- | --- | --- |
    | 용도 | DOM 참조 / 값 저장 | 고유 ID 생성 (접근성/렌더링 구분용) |
    | 렌더링 영향 | 없음 (변경해도 렌더 안 됨) | 고정된 값 |
    | 예시 | inputRef.current.focus() | <input id={id} /> |
    
    useRef: 포커스, 스크롤 등 **DOM 직접 제어**
    useId: SSR/CSR 간 ID 불일치 방지 등 **접근성**에 적합
    
- 사용자 상호작용: **events vs conditional rendering**
    
    
    | **항목** | events | conditional rendering |
    | --- | --- | --- |
    | 목적 | 사용자 입력/클릭 등 반응 | 조건에 따라 다른 컴포넌트 렌더 |
    | 사용 방식 | onClick={handleClick} | {isLoggedIn ? <User /> : <Login />} |
    | 반응 대상 | 이벤트 트리거 | 상태 변화나 조건 값 |
- 라우팅 vs 렌더링 제어: **react-router vs conditional rendering**
    
    
    | **항목** | react-router | conditional rendering |
    | --- | --- | --- |
    | 용도 | 페이지 이동 제어 | 한 페이지 내에서 조건부 UI |
    | 예시 | <Route path="/about" /> | {show ? <Modal /> : null} |
    | 주 사용처 | SPA에서 경로에 따라 컴포넌트 전환 | 버튼 클릭, 로그인 여부 등 UI 제어 |
- 비동기 렌더링 제어: **useTransition vs 일반 setState**
    
    
    | **항목** | useTransition | **일반** setState |
    | --- | --- | --- |
    | 우선순위 | 낮은 우선순위 업데이트 | 항상 즉시 렌더링 |
    | 부하 처리 | 부드럽게 처리 | 렌더링 끊김 가능 |
    | 사용 예 | 검색 필터링, 긴 리스트 변경 | 숫자 카운트, 간단 UI |