![리면.png](attachment:f39a5d8b-9cfb-43b6-8d8d-6999faf29509:리면.png)

### **리액트에서 불변성을 유지하는 이유는 무엇인가요?**

React는 상태(state)의 변경을 감지하고 컴포넌트를 다시 렌더링하기 위해 참조값을 비교합니다. 불변성을 유지하면 이전 상태와 새로운 상태의 참조를 쉽게 비교할 수 있어, 성능을 높이고 예측 가능한 코드 작성이 가능해집니다.

- immer.js는 어떤 역할을 하나요?
→ immer.js는 JavaScript 객체의 **불변성을 유지하면서도** 마치 **가변처럼 직관적인 코드를 작성**할 수 있게 도와주는 라이브러리입니다. produce 함수를 이용해 기존 상태를 바탕으로 **새로운 상태를 불변하게 생성**할 수 있습니다.

### **코드 스플리팅(Code Splitting)이란?**

코드 스플리팅은 애플리케이션의 코드를 여러 청크로 나눠서, 사용자가 필요로 할 때 로드하게 하는 기법입니다. React에서는 React.lazy와 Suspense를 사용해 컴포넌트 단위 코드 스플리팅이 가능합니다.

- React에서 Suspense는 정확히 어떤 역할을 하나요?
→ Suspense는 **비동기 컴포넌트가 로딩될 동안 보여줄 UI**를 지정하는 컴포넌트입니다. 주로 React.lazy로 로딩하는 컴포넌트를 감쌀 때 사용됩니다.

### **React에서 컴포넌트 언마운트 시 리소스 해제를 어떻게 처리하나요?**

useEffect 훅의 클린업(clean-up) 함수를 사용하여 이벤트 리스너 제거, 타이머 해제, 구독 해제 등을 처리합니다. 이는 메모리 누수를 방지하는 데 중요합니다.

- useEffect 클린업이 실행되는 시점은 언제인가요?
→ 클린업 함수는 다음 두 경우에 실행(**컴포넌트가 언마운트될 때, useEffect가 다시 실행되기 전에)
즉, 의존성 배열에 변화가 생겨 effect가 재실행될 때, 이전 effect를 먼저 정리하고 새로 실행됩니다.**

### **트랜스파일링과 번들링의 차이는?**

트랜스파일링은 최신 JS 문법을 하위 호환되는 코드로 변환하는 과정(Babel 사용), 번들링은 여러 파일을 하나로 묶어주는 과정(Webpack 사용)입니다.

- Webpack에서 트리쉐이킹(Tree Shaking)은 무엇인가요?
→ Tree Shaking은 **사용되지 않는(dead code)** JavaScript 코드를 **번들에서 제거**하는 최적화 기법입니다. ES Modules의 정적 구조를 기반으로 작동하며, 코드 사이즈를 줄이는 데 유용합니다.

### **React의 주요 특징은 무엇인가요?**

1. 컴포넌트 기반 구조
2. Virtual DOM을 통한 효율적 렌더링
3. JSX 문법
4. 단방향 데이터 흐름
5. Hook을 통한 상태 및 생명주기 관리

### **React에서 이벤트 처리 방법을 설명해주세요.**

React에서는 DOM 이벤트와 유사한 SyntheticEvent를 사용합니다. JSX 문법에서 onClick, onChange 등의 props로 이벤트를 처리합니다.

- SyntheticEvent의 이점은 무엇인가요?
→ React의 SyntheticEvent는 **브라우저 이벤트를 래핑**한 이벤트 객체로, **브라우저 간 호환성을 보장**하며 **일관된 API**를 제공합니다. 또한 React에서 이벤트 풀링을 통해 **성능 최적화**도 지원합니다.

### **조건부 렌더링을 구현하는 방법은 무엇인가요?**

1. 삼항 연산자: isLoggedIn ? <Home /> : <Login />
2. && 연산자: isReady && <Spinner />
3. if 문 사용한 함수 내부 분기

### **React Router를 어떻게 설정하고 사용하나요?**

React Router를 설치 후, <BrowserRouter>, <Routes>, <Route> 컴포넌트를 사용해 URL에 따라 컴포넌트를 렌더링합니다.

- 동적 라우팅(Dynamic Routing)은 어떻게 구현하나요?
→ URL의 일부를 변수로 다루는 라우팅입니다. :id 형식으로 경로를 설정하고, useParams 훅으로 값을 추출합니다.

### **컴포넌트 간의 데이터 전달 방법은?**

1. 부모 → 자식: props
2. 자식 → 부모: 콜백 함수 전달
3. 전역 상태: Context API, Redux 등

### **React에서 key의 역할과 중요성은 무엇인가요?**

key는 리스트 렌더링 시 항목을 식별해 변경된 항목만 효율적으로 업데이트할 수 있게 도와줍니다.

- 인덱스를 key로 쓰는 건 왜 지양하나요?
→ 리스트의 순서가 **변경될 가능성이 있을 경우**, 인덱스를 key로 사용하면 **렌더링 최적화가 무력화**되어 버그나 성능 저하가 발생할 수 있습니다. 특히 요소 추가/삭제 시 문제가 발생합니다.

### **React에서 스타일링 방법은 어떤 게 있나요?**

1. CSS Modules
2. Styled-components / Emotion (CSS-in-JS)
3. 일반 CSS
4. Tailwind CSS

### **React Hooks는 무엇이며 어떤 기능을 하나요?**

Hooks는 함수형 컴포넌트에서 상태 관리(useState)와 사이드 이펙트(useEffect) 등을 사용할 수 있게 합니다.

### **Redux에서 액션, 리듀서, 스토어의 역할은?**

1. **액션**: 상태 변경을 알리는 객체
2. **리듀서**: 액션을 기반으로 새 상태를 리턴
3. **스토어**: 상태를 보관하는 객체

### **Redux Thunk vs Redux Saga**

**Thunk**: 함수 기반, 비동기 로직을 Action으로 처리

**Saga**: 제너레이터 기반, 비동기 흐름을 직관적으로 표현

- Redux Saga에서 takeEvery와 takeLatest 차이점은?
→ **takeEvery**: 모든 액션에 대해 각각 처리 (동시 실행 O)
→ **takeLatest**: 가장 마지막 액션만 처리, 이전 작업은 **취소됨**

### **React 성능 최적화 방법은?**

React.memo

useMemo, useCallback

Virtualization (예: react-window)

Lazy Load / 코드 스플리팅

### **React의 Portals란?**

컴포넌트를 부모 DOM 계층 외부에 렌더링할 수 있도록 하는 기능 (ReactDOM.createPortal 사용)

- 모달을 만들 때 Portals을 사용하는 이유는?
→ 모달은 **시각적으로 화면 최상단**에 렌더링돼야 하고, z-index나 오버플로우에 영향을 받지 않아야 합니다. Portals는 **부모 컴포넌트 DOM 밖**에 렌더링함으로써 **레이아웃 구조를 깨지 않고도 독립적인 UI**를 구현할 수 있게 합니다.

### **React에서 SEO 대응 방법은?**

기본 CSR은 SEO에 불리하므로, SSR(Next.js), meta tag 설정, sitemap 생성 등을 활용해야 합니다.

### **Error Boundary란?**

자식 컴포넌트에서 발생하는 JS 오류를 캐치해 UI 붕괴를 방지하는 컴포넌트 (componentDidCatch, getDerivedStateFromError 사용)

### **렌더 프롭(Render Props) 패턴이란?**

컴포넌트의 children 또는 prop으로 함수를 전달해 렌더링 결과를 제어하는 패턴입니다.

### **React와 Webpack의 관계는?**

Webpack은 React 프로젝트를 번들링하고 트랜스파일링하는 도구입니다. Babel과 함께 사용해 최신 JS와 JSX를 브라우저가 이해할 수 있게 변환합니다.