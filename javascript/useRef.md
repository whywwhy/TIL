# useRef란?

### 1️⃣ useRef란?
<hr/>

> useRef 는 .current 프로퍼티로 전달된 인자(initialValue)로 초기화된 변경 가능한 ref 객체를 반환합니다. 반환된 객체는 컴포넌트의 전 생애주기를 통해 유지될 것입니다. 

= **저장공간 또는 DOM요소에 접근하기 위해 사용되는 React Hook**<br/>
여기서 Ref는 reference, 즉 참조를 뜻한다.

자스 사용시, 우리가 특정 DOM 을 선택하기 위해서 querySelector 등의 함수를 사용함.

React를 사용하는 프로젝트에서도 가끔씩 DOM 을 직접 선택해야 하는 상황이 필요. 그럴때 우리는 useRef라는 React Hook을 사용


### 2️⃣ 변수 관리
<hr/>

내 컴포넌트가 몇번 렌더링됐는지 알고싶은 상황

```jsx
function App() {
  const [count, setCount] = useState(1);
  const [renderingCount, setRedneringCount] = useState(1);
 
  useEffect(() => {
    console.log("rendering Count : ", renderingCount);
    setRedneringCount(renderingCount + 1);
  });

  return (
    <div>
      <div>Count : {count}</div>
      <button onClick={() => setCount(count + 1)}> count up </button>
    </div>
  );
}
```

이렇게 로직을 짜면, useEffect 안에있는 setRenderingCount()가 계속해서 컴포넌트를 리렌더링해서 무한 루프에 빠짐 

이를 useRef를 통해 효율적으로 관리 ㄱㄴ

```jsx
function App() {
  const [count, setCount] = useState(1);
  const renderingCount = useRef(1);

  useEffect(() => {
    console.log("renderingCount : ", renderingCount.current);
    ++renderingCount.current;
  });

  return (
    <div>
      <div>Count : {count}</div>
      <button onClick={() => setCount(count + 1)}> count up </button>
    </div>
  );
}
```


### 3️⃣ DOM 요소 선택
<hr/>

최신 웹사이트들을 보면 로그인 화면에 들어가자마자 아이디 input에 포커스되어있는 경우가 대부분

이를 useRef를 통해 DOM요소를 선택하여 구현 ㄱㄴ
