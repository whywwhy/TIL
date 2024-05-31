# Bun?

### 1️⃣ Bun이란?
<hr/>
Bun은 Node 또는 Deno와 같은 JavaScript 런타임 및 패키지 관리자.

`
Bun : https://bun.sh/ 
github : https://github.com/oven-sh/bun
`

### 2️⃣ 왜 빠를까?
<hr/>

Bun은 V8엔진을 사용하는 기존의 Node, Deno와는 달리 일반적으로 더 빠른것으로 간주되는 WebKit의 JavaScriptCore를 기반으로 구축, 

C++, Rust가 아닌 시스템 하드웨어에서 읽을 수 있는 저수준 프로그래밍 언어인 Zig로 작성되어있어 더 빠르게 동작할 수 있음=

### 3️⃣ 특징
<hr/>

1. 속도를 우선으로 개발
2. React를 서버로 렌더링하거나 데이터베이스 쿼리를 실행할 때 Node 및 Deno보다 약 3배 정도 빠름
3. npm과 호환할 수 있는 패키지 매니저를 포함
4. yarn install을 bun install로 바꾸기만 해도 최대 20배 정도 빠르게 설치 가능
5. V8 엔진 대신 WebKit에서 사용하는 JavaScriptCore을 엔진을 사용
6. 기존에 작업 중인 JavaScript / TypeScript의 개발환경을 그대로 쓸 수 있도록 설계
7. Node.js의 모듈 resolution 알고리즘을 구현 -> node_modules을 그대로 사용 가능
8. ESM 및 CommonJS를 모두 지원, 내부적으로는 ESM을 사용
9. 모든 파일이 트랜스파일 되기 때문에 TypeScript 및 JSX를 모두 지원
10. .env 파일로부터 자동으로 환경변수를 불러옴, 더 이상 require("dotenv").config() 를 작성할 필요가 없음

### 4️⃣ 번 설치
<hr/>

`
curl -fsSL https://bun.sh/install | bash
`

Bun의 설치 및 사용 명령어들은 Node와 비슷한 부분이 매우 많다

- bun dev : 로컬 서버 실행
- bun create : 프로젝트 생성
ex) bun create react [project-name] (react cli 설치)
- bun run : bun 스크립트 실행
- bun install : package.json에 대한 종속성 설치
- bun add : 새로운 패키지 종속성 추가
- bun remove : 설치된 패키지 종속성 제거