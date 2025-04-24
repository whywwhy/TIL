![프심일.png](attachment:3b8df789-360a-4292-aea0-94305d910490:프심일.png)

### **Virtual DOM이 실제 DOM보다 성능이 좋은 이유는?**

Virtual DOM은 메모리 상의 가상 트리로, 변경 사항이 생겼을 때 전체 DOM을 다시 렌더링하지 않고 변경된 부분만 계산(diffing)해서 최소한의 업데이트만 실제 DOM에 적용하기 때문에 성능이 좋습니다.

- React는 어떤 방식으로 변경된 부분을 감지하나요?
→ React는 diffing 알고리즘을 사용해 이전 Virtual DOM과 새로운 Virtual DOM을 비교합니다.
- diffing의 시간 복잡도는 어떻게 되나요?
→ 일반적으로 O(n)입니다. React는 key 값을 활용하여 더 효율적으로 비교합니다.

### **React의 useEffect는 어떤 상황에서 실행되나요?**

useEffect는 컴포넌트가 마운트될 때, 의존성 배열의 값이 변경될 때, 또는 언마운트될 때 실행됩니다.

- 의존성 배열이 비어 있으면 언제 실행되나요?
→ 컴포넌트가 마운트될 때만 실행되고, 업데이트나 언마운트에는 반응하지 않습니다.
- 클린업 함수는 언제 호출되나요?
→ 언마운트되거나 다음 useEffect가 실행되기 직전에 호출됩니다.

### **Closure를 실무에서 어떻게 활용해봤나요?**

예를 들어, 이벤트 리스너를 동적으로 설정할 때 바깥 변수에 접근해야 했던 경우나, 비공개 상태를 유지하는 모듈 패턴을 만들 때 Closure를 활용했습니다.

- 클로저 사용 시 메모리 누수가 생길 수 있는 경우는?
→ 참조가 계속 유지되면 가비지 컬렉터가 수거하지 못해 누수가 발생할 수 있습니다.

### **Reconciliation 알고리즘이란?**

Reconciliation은 React에서 상태가 변경되었을 때 Virtual DOM 간의 차이를 계산하고 최소한의 변경만 실제 DOM에 적용하는 과정입니다.

- key 값이 왜 중요한가요?
→ key가 없으면 React가 요소를 재사용하지 않고 다시 생성하므로 성능이 저하됩니다.
- key는 어떤 기준으로 설정하는 게 좋나요?
→ 고유한 값(예: 데이터 ID)을 사용하는 것이 바람직하며, index는 재정렬 시 오류가 날 수 있어 지양합니다.

### **브라우저 렌더링 과정 설명해보세요.**

HTML 파싱 → DOM 트리 생성 → CSS 파싱 → CSSOM 생성 → Render Tree 생성 → Layout 계산 → Paint → Composite

- Reflow와 Repaint의 차이는?
→ Reflow는 레이아웃 계산, Repaint는 색상/스타일 등만 변경될 때 발생합니다.
- 어떤 CSS 속성이 Reflow를 유발하나요?
→ width, height, padding, margin 등의 속성은 Reflow를 유발합니다.

### **CSR과 SSR의 차이는 무엇이고, 각각 언제 사용하는 게 적절한가요?**

CSR(Client-Side Rendering)은 브라우저에서 렌더링하고, SSR(Server-Side Rendering)은 서버에서 렌더링된 HTML을 전송합니다. SSR은 초기 로딩 속도와 SEO에 유리합니다.

- SSR의 단점은 무엇인가요?
→ 서버 부하 증가, 복잡한 코드 구조 등이 있습니다.
- Next.js는 어떤 렌더링 방식인가요?
→ 기본적으로 SSR을 지원하지만, CSR과 SSG도 선택적으로 사용할 수 있습니다.

### **이벤트 위임을 사용하면 어떤 이점이 있나요?**

이벤트 리스너를 부모 요소에만 등록하면, 자식 요소에 많은 리스너를 달 필요 없이 효율적으로 이벤트를 관리할 수 있습니다. 메모리 절약과 성능 향상에 도움이 됩니다.

- 이벤트 버블링과 캡처링의 차이는?
→ 버블링은 자식 → 부모 방향, 캡처링은 부모 → 자식 방향입니다.
- stopPropagation()을 언제 써야 하나요?
→ 이벤트가 상위로 전파되는 것을 막고 싶을 때 사용합니다.

### **useCallback과 useMemo의 차이는 무엇인가요?**

useMemo는 값을 메모이제이션하고, useCallback은 함수를 메모이제이션합니다.

- useCallback을 언제 써야 하나요?
→ 자식 컴포넌트에 콜백을 props로 전달할 때 불필요한 렌더링을 방지하기 위해 사용합니다.
- useMemo는 언제 과용하면 안 되나요?
→ 무조건적으로 남용하면 오히려 성능이 저하될 수 있습니다.

### **웹 성능 최적화 방법을 설명해주세요.**

코드 스플리팅, 이미지 최적화, Lazy Loading, 캐싱, gzip 압축, 불필요한 렌더링 방지 등을 통해 웹 성능을 향상시킬 수 있습니다.

- Lighthouse 점수를 높이기 위해 한 작업은?
→ 이미지 포맷 변경(WebP), useMemo/React.memo를 활용하여 불필요한 렌더링 제거 등을 했습니다.

### **JavaScript에서 비동기 처리를 어떻게 하나요?**

콜백 함수, Promise, async/await를 사용하여 비동기 처리를 합니다. 최근에는 async/await가 가독성과 유지보수에 유리합니다.

- async/await 내부 에러 처리는 어떻게 하나요?
→ try/catch 문을 사용하여 처리합니다.
- Promise.all과 Promise.race의 차이는?
→ all은 모두 성공해야 결과를 반환, race는 가장 먼저 끝나는 Promise를 반환합니다.

### **React에서 상태가 많을 때 상태 관리 어떻게 하시나요?**

컴포넌트 상태로 감당이 어려울 경우 Context API, Redux, Zustand 같은 상태 관리 라이브러리를 사용합니다. 전역 상태와 지역 상태를 구분해서 관리합니다.

- Context API를 많이 사용하면 성능 저하가 생기지 않나요?
→ Context를 자주 업데이트하면 하위 컴포넌트 전체가 리렌더링되어 성능 문제가 생길 수 있습니다. 그래서 상태가 자주 바뀌는 값은 Context보다 다른 전역 상태 관리 툴로 분리합니다.

### **Redux의 미들웨어는 무엇인가요?**

미들웨어는 액션이 디스패치되고 리듀서에 도달하기 전 중간에 개입할 수 있는 로직입니다. 예: 비동기 처리용 thunk, 로깅용 logger

- thunk와 saga의 차이점은?
→ thunk는 함수 기반, saga는 generator 기반으로 비동기 흐름을 제어합니다. saga는 복잡한 플로우를 다루기 편합니다.

### **React에서 컴포넌트 리렌더링은 언제 일어나나요?**

state나 props가 바뀔 때, 부모가 리렌더링되면 자식도 리렌더링, context 값 변경

- memoization을 언제 활용하시나요?
→ React.memo, useMemo, useCallback을 사용해 리렌더링을 줄입니다. 성능 병목이 있는 컴포넌트에서만 선택적으로 사용합니다.

### **React key props의 정확한 역할은?**

key는 요소의 identity를 React가 식별할 수 있도록 도와줍니다. 리스트가 변경되었을 때 효율적으로 diffing할 수 있게 합니다.

- index를 key로 쓰면 안 되는 이유는?
→ 요소 순서가 바뀌거나 삽입될 때 의도치 않은 재사용이 발생해 UI 이상이 생깁니다.

### **웹 접근성이란 무엇이며 어떻게 구현했나요?**

모든 사용자(장애인 포함)가 웹을 이용할 수 있도록 돕는 기술입니다. 시맨틱 태그 사용, ARIA 속성, 키보드 접근성 등을 고려했습니다.

- 스크린 리더에 읽히게 하기 위해 어떤 속성을 사용했나요?
→ aria-label, role, tabIndex, 시맨틱 HTML 태그

### **IntersectionObserver를 써본 경험이 있나요?**

무한 스크롤 구현 시 사용해봤습니다. 사용자가 특정 요소에 도달했을 때 콜백을 트리거할 수 있어 스크롤 이벤트보다 효율적입니다.

- 어떻게 옵저버를 해제하나요?
→ unobserve() 또는 컴포넌트 언마운트 시 disconnect() 호출

### **CSR 페이지에서 SEO를 해결하는 방법은?**

메타 태그 동적 설정(Open Graph), 검색엔진에 sitemap 제출, SSR/SSG 전환, prerender.io 같은 프리렌더링 툴 활용 등을 고려했습니다.

- React만 사용하는 경우 검색엔진 크롤러는 어떤 한계가 있나요?
→ 일부 크롤러는 JS 실행 없이 HTML만 파싱하므로 CSR만 사용하면 콘텐츠를 읽지 못할 수 있습니다.

### **useLayoutEffect와 useEffect의 차이는?**

useLayoutEffect는 DOM이 그려지기 전에 실행되고, useEffect는 브라우저가 paint를 완료한 후 실행됩니다.

- 언제 useLayoutEffect를 써야 하나요?
→ 레이아웃 계산 전 DOM을 읽거나 조작해야 할 때 사용합니다. 예: 스크롤 위치 조정, 치수 측정

### **웹팩(Webpack)의 역할은?**

모듈 번들러로, JS/CSS/이미지 등의 파일을 의존성을 분석해 하나로 묶고 최적화합니다.

- 코드 스플리팅은 어떻게 하나요?
→ import()로 동적 임포트하거나 SplitChunksPlugin 사용

### **브라우저에서 CORS 문제 해결 방법은?**

서버가 Access-Control-Allow-Origin 헤더로 클라이언트를 허용해야 합니다. 프론트엔드 개발 단계에서는 프록시 서버를 두어 우회하기도 합니다.

- OPTIONS preflight 요청은 언제 발생하나요?
→ 비단순 요청(예: PUT, PATCH, custom headers)이 있을 때 사전 요청(preflight)이 발생합니다.

### **React의 동적 import는 무엇이며 언제 사용하나요?**

코드를 실행 시점에 로드할 수 있는 기능입니다. 페이지 단위, 컴포넌트 단위로 lazy loading하여 초기 로딩 속도를 개선합니다.

- Suspense는 왜 필요할까요?
→ 컴포넌트 로딩 중 로딩 UI를 보여주기 위해 필요합니다.

### **크로스 브라우징 이슈를 경험한 적이 있나요?**

IE에서 Flexbox 지원 미비로 레이아웃 깨짐을 겪었고, PostCSS 및 Autoprefixer를 통해 해결했습니다.

- 어떻게 브라우저 호환성을 사전에 검증하나요?
→ Can I use 사이트 참고, devtools의 에뮬레이터, 실제 디바이스 테스트

### **이벤트 루프(Event Loop)의 동작 방식을 설명해 주세요.**

JS는 단일 스레드 언어로, 콜스택이 비워졌을 때 태스크 큐의 작업이 실행됩니다. Microtask Queue가 Macrotask Queue보다 우선됩니다.

- setTimeout과 Promise의 우선순위는?
→ Promise는 Microtask, setTimeout은 Macrotask이므로 Promise가 먼저 실행됩니다.

### **React에서 커스텀 훅을 만들어본 경험이 있나요?**

API 호출, 폼 상태 관리, resize 감지 등 공통 로직을 분리할 때 커스텀 훅으로 만들어 재사용했습니다.

- 훅 내부에서 setState가 무한 반복되는 문제를 경험해보셨나요?
→ 의존성 배열을 잘못 관리하면 발생합니다. useEffect의 의존성 최적화가 중요합니다.

### **styled-components의 장단점은?**

장점은 CSS-in-JS로 컴포넌트 단위 스타일 관리가 편하고, 동적 스타일을 쉽게 적용할 수 있다는 점입니다. 단점은 빌드 시 번들 사이즈 증가 가능성입니다.

- styled-components를 SSR에서 사용할 때 주의할 점은?
→ 스타일 플래시(FoUC)를 방지하려면 SSR 지원 설정이 필요합니다.

### **Next.js의 getServerSideProps와 getStaticProps의 차이는?**

getServerSideProps: 요청마다 서버에서 실행 (SSR)

getStaticProps: 빌드 시 실행되어 정적 파일 생성 (SSG)

- 동적 경로를 사용할 때 getStaticPaths가 필요한 이유는?
→ 빌드 시 어떤 경로가 필요한지 명시해야 정적 페이지로 미리 생성할 수 있기 때문입니다.

### **프론트에서 보안적으로 신경 써야 할 점은?**

XSS, CSRF 방어, HTTPS 사용, JWT 토큰의 안전한 저장(localStorage 대신 HttpOnly 쿠키) 등이 있습니다.

- XSS 방어를 위해 어떤 방법을 사용하셨나요?
→ 사용자 입력을 escape하거나 DOMPurify 같은 라이브러리로 필터링합니다.

### **클라이언트 라우팅 방식 설명해주세요.**

브라우저의 history API를 활용하여 페이지 새로고침 없이 URL을 변경하고 컴포넌트를 교체합니다. React Router가 대표적입니다.

- SPA에서 뒤로 가기 버튼이 정상 작동하지 않을 때 원인은?
→ history stack 관리 문제 또는 라우팅 미스매치

### **컴포넌트의 역할 분리는 어떻게 하시나요?**

UI는 Dumb(프레젠테이셔널) 컴포넌트, 로직은 Container(스마트) 컴포넌트로 나누고, 커스텀 훅으로 공통 로직을 분리합니다.

- Atomic Design이나 다른 디자인 패턴 써보셨나요?
→ Atomic Design을 적용해 Button, Card 같은 작은 단위부터 페이지 단위까지 구성했습니다.

### **프론트엔드 아키텍처 설계에서 중요하게 생각하는 것은?**

재사용성, 확장성, 유지보수성입니다. 코드 스플리팅, 폴더 구조 설계, 상태 관리, 공통 컴포넌트 추출을 통해 효율적인 구조를 만듭니다.

- 프로젝트 초기에 어떤 기준으로 폴더 구조를 설계했나요?
→ 기능별(feature-based) 구조로 구성해 각 기능이 독립적으로 관리되도록 했습니다.