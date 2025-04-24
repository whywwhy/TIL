![넥면.png](attachment:08295a11-0ac6-4f0a-a5db-5eae2d5a713f:넥면.png)

### **Next.js란 무엇인가요?**

Next.js는 React 기반의 프레임워크로, 서버사이드 렌더링(SSR)과 정적 사이트 생성(SSG), API 라우팅, 이미지 최적화 등 다양한 기능을 제공하여 SEO와 성능 최적화를 지원합니다.

- React와 Next.js의 차이는 무엇인가요?
→ React는 라이브러리이고, Next.js는 프레임워크입니다. React는 UI 구성만 담당하고 라우팅, SSR 등은 직접 설정해야 하지만, Next.js는 이를 내장 기능으로 제공합니다.

### **Next.js에서 라우팅은 어떻게 처리되나요?**

Next.js는 파일 기반 라우팅을 사용합니다. pages 디렉토리에 생성한 파일 이름에 따라 URL이 자동으로 매핑됩니다.

- 동적 라우팅(dynamic routing)은 어떻게 하나요?
→ [id].js 같은 파일명을 사용해 파라미터 기반 라우팅이 가능하고, getStaticPaths와 getStaticProps를 함께 사용하여 SSG로 처리할 수 있습니다.

### **Next.js의 렌더링 방식 종류는?**

1. **SSR** (Server-Side Rendering): 요청 시 서버에서 렌더링
2. **SSG** (Static Site Generation): 빌드 시 정적 HTML 생성
3. **ISR** (Incremental Static Regeneration): 특정 조건에서 정적 페이지 재생성
4. **CSR** (Client-Side Rendering): 브라우저에서 렌더링
- 각 방식의 장단점은 무엇인가요?
→ SSG는 빠르지만 동적 데이터엔 불리, SSR은 유연하지만 서버 부하 ↑, ISR은 둘의 장점 조합, CSR은 초기 렌더링이 느릴 수 있음.

### **getStaticProps, getServerSideProps, getInitialProps의 차이점은?**

getStaticProps: 빌드 시 정적 데이터 주입

getServerSideProps: 요청마다 서버에서 실행

getInitialProps: 페이지 로딩 시 클라이언트/서버 모두 실행 (비추천)

- ISR은 어떤 함수와 함께 사용할 수 있나요?
→ getStaticProps와 함께 사용하며 revalidate 옵션으로 갱신 주기를 설정합니다.

### **Next.js에서 API 라우팅은 어떻게 구현하나요?**

pages/api 디렉토리 내에 파일을 생성하여 REST API 엔드포인트처럼 사용할 수 있습니다. 서버리스 함수 형태로 작동합니다.

- 이 API 라우팅은 서버 배포 환경이 아닌 곳에서도 사용할 수 있나요?
→ 일반적으로 Vercel 등 서버리스 플랫폼에서 사용되며, 별도의 서버 없이도 작동하지만 Node.js 서버에서도 사용할 수 있습니다.

### **이미지 최적화는 어떻게 하나요?**

Next.js는 next/image 컴포넌트를 통해 자동으로 이미지 리사이징, 포맷 변경(WebP), lazy loading 등을 지원합니다.

- 외부 이미지도 최적화 가능한가요?
→ 가능합니다. next.config.js에서 외부 도메인을 허용해주면 next/image에서 처리됩니다.

### **Next.js에서 코드 스플리팅은 어떻게 처리되나요?**

Next.js는 기본적으로 자동 코드 스플리팅을 지원합니다. 각 페이지 단위로 분리된 번들이 생성되어 초기 로딩 성능을 향상시킵니다.

- 특정 컴포넌트를 동적으로 로딩하려면?
→ next/dynamic을 사용하여 코드 스플리팅을 수동으로 적용할 수 있습니다.

### **Next.js에서 _app.js, _document.js의 역할은?**

_app.js: 모든 페이지의 공통 레이아웃과 상태 관리를 담당

_document.js: HTML 문서의 구조 커스터마이징 (예: lang, meta 설정 등)

- _app.js에서는 데이터를 미리 불러올 수 있나요?
→ getInitialProps를 사용해 데이터를 미리 불러올 수 있지만, SSR 성능에 영향을 줄 수 있어 주의가 필요합니다.

### **next.config.js는 어떤 역할을 하나요?**

Next.js의 설정 파일로, 이미지 도메인 허용, 리다이렉트, 환경 변수, 웹팩 설정 확장 등을 지정할 수 있습니다.

- 웹팩 설정을 커스터마이징하려면?
→ webpack(config, options) 콜백을 통해 설정을 확장할 수 있습니다.

### **Next.js의 SEO 관련 기능은?**

SSR/SSG를 통해 HTML이 미리 렌더링되어 검색 엔진 최적화가 용이하며, next/head를 통해 메타 태그를 개별 페이지마다 설정할 수 있습니다.

- CSR만 사용한다면 SEO는 어떻게 해결하나요?
→ 별도로 메타태그를 렌더링하는 서버나, pre-rendering 서비스를 사용해야 합니다.

### **Next.js에서 Middleware란 무엇인가요?**

Middleware는 요청이 처리되기 전에 실행되는 코드로, Next.js 12 이상에서 사용 가능합니다. 경로 보호, 리다이렉트, 인증 검사 등에 사용됩니다.

- Middleware는 어떤 시점에 실행되며 클라이언트에서 실행되나요?
→ 서버 측에서 실행되며 Edge Function(가장 가까운 위치)에서 처리되어 빠른 응답을 제공합니다. 클라이언트에서는 실행되지 않습니다.

### **Incremental Static Regeneration(ISR)은 어떻게 동작하나요?**

ISR은 getStaticProps와 revalidate 옵션을 활용해 빌드 이후에도 특정 페이지를 주기적으로 다시 생성합니다.

- 최초 요청은 어떻게 처리되며, 이전 캐시는 어떻게 관리되나요?
→ 최초 요청은 기존 캐시를 보여주고, 백그라운드에서 새 페이지를 빌드해 다음 요청부터 교체됩니다.

### **next export 명령어는 언제 사용하나요?**

정적 사이트(SSG)만 사용하는 프로젝트를 완전히 HTML로 내보낼 때 사용합니다. SSR이나 API routes는 사용할 수 없습니다.

- next export를 했을 때 사용할 수 없는 기능은 어떤 게 있나요?
→ SSR(getServerSideProps), API Routes, Middleware 등 서버 기능은 모두 사용할 수 없습니다.

### **Next.js의 App Router와 Pages Router 차이는? (v13 기준)**

Pages Router: pages/ 디렉토리 기반의 기존 라우팅 방식.

App Router: app/ 디렉토리 기반의 최신 라우팅 방식으로 React Server Components 지원, 레이아웃 기능 내장.

- React Server Components(RSC)는 어떤 장점이 있나요?
→ 서버에서만 렌더링되므로 JS 번들 크기를 줄일 수 있고, 클라이언트 성능이 향상됩니다.

### **Next.js에서 Layouts을 재사용하려면 어떻게 하나요?**

App Router 기반에서는 app/layout.tsx 파일을 활용해 각 페이지의 공통 레이아웃을 구성할 수 있습니다.

- 레이아웃에 데이터를 어떻게 주입하나요?
→ generateMetadata, generateStaticParams 등을 활용하거나 서버 컴포넌트 내에서 직접 fetch 할 수 있습니다.

### **Next.js에서 환경변수는 어떻게 설정하고 사용하는가요?**

.env.local 파일 등에 NEXT_PUBLIC_ 접두사를 붙여 사용하며, 클라이언트에서도 접근 가능합니다.

- 클라이언트에서 접근 가능한 변수와 아닌 변수의 차이는?
→ NEXT_PUBLIC_이 붙은 것만 클라이언트에서 접근 가능. 나머지는 서버에서만 사용됩니다.

### **Next.js에서 이미지 최적화가 어떻게 이루어지나요?**

next/image는 브라우저에 맞게 자동 포맷(WebP 등), 크기 최적화, lazy loading을 적용하여 성능을 개선합니다.

- CDN을 통한 이미지 최적화도 가능한가요?
→ Vercel 등에서는 기본적으로 자동 CDN 최적화가 되며, 외부 이미지의 경우 next.config.js에서 domain을 등록해야 합니다.

### **Next.js에서 TypeScript는 어떻게 지원되나요?**

npx create-next-app --typescript로 프로젝트를 생성하거나 .ts/.tsx 파일을 추가하면 자동으로 설정 파일이 생성됩니다.

- App Router에서 generateStaticParams의 타입은 어떻게 설정하나요?
→ ReturnType<typeof generateStaticParams>를 활용하거나 InferGetStaticPropsType을 사용할 수 있습니다.

### **Next.js에서 SEO 최적화를 위해 어떤 기술을 쓰나요?**

SSR, SSG를 통한 미리 렌더링, next/head의 메타태그 작성, Open Graph/JSON-LD 적용 등.

- 페이지마다 동적으로 메타 태그를 설정하려면?
→ App Router에서는 generateMetadata를 활용해 동적으로 설정 가능합니다.

### **Next.js에서 prefetch는 어떻게 작동하나요?**

<Link> 컴포넌트는 뷰포트에 보이면 해당 링크의 페이지 코드를 미리 로딩하여 사용자의 클릭 속도를 향상시킵니다.

- prefetch를 비활성화할 수 있나요?
→ <Link prefetch={false}>로 설정하여 비활성화할 수 있습니다.

### **서버리스 환경에서 Next.js의 동작 방식은?**

API routes, SSR은 서버리스 함수(Lambda)로 분리되어 요청 시 개별 실행됩니다.

- 서버리스 함수의 단점은 무엇인가요?
→ cold start 시간 지연, timeout 제한, DB 연결 유지 어려움 등이 있습니다.

### **Next.js에서 동적 import의 용도는?**

next/dynamic을 통해 특정 컴포넌트를 필요 시점에 로딩하여 초기 렌더링 성능을 높일 수 있습니다.

- SSR이 필요한 컴포넌트는 어떻게 처리하나요?
→ ssr: false로 설정하여 클라이언트 사이드에서만 렌더링되도록 설정할 수 있습니다.

### **Static 파일은 어디에 위치시키나요?**

public/ 폴더에 위치시키며, /favicon.ico처럼 루트 경로에서 접근됩니다.

- static/ 폴더는 사용할 수 없나요?
→ Next.js 9 이후부터는 public/ 폴더만 사용하며, static/은 deprecated 되었습니다.

### **Next.js의 Build Output은 어떤 구조인가요?**

next/ 디렉토리 아래에 HTML, JSON, chunks 등이 구성되며, 각각 페이지 단위로 나뉩니다.

- 이 디렉토리를 직접 수정하면 어떻게 되나요?
→ 직접 수정은 금지되어 있으며, 모든 파일은 빌드 시 자동으로 생성됩니다.

### **App Router의 서버 컴포넌트와 클라이언트 컴포넌트 차이는?**

서버 컴포넌트는 서버에서만 실행되어 클라이언트 JS 번들 크기를 줄이며, 클라이언트 컴포넌트는 브라우저에서 실행됩니다.

- 서버 컴포넌트 안에서 useState를 쓸 수 있나요?
→ 사용할 수 없습니다. use client 지시어를 통해 클라이언트 컴포넌트로 바꿔야 합니다.