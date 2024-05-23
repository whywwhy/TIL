# 번들러(Bundler)가 뭘까? 

### 1️⃣ 번들러(Bundler)
<hr/>
사실 나는 번들러가 모르던 상태에서 번들러를 처음 쓰게 되었다. 

동아리 내 create-react 명령어에 vite가 기본 내장되어있었다. 

번들러 = 여러 개로 모듈화된 자바스크립트 파일을 하나로 합치는 즉, ‘bundle’ 해주는 도구이다. 
<br>
브라우저는 모듈화된 자바스크립트는 읽지 못하기 때문에 브라우저에서 코드를 실행하려면 반드시 번들러가 필요함. 

*번들러가 없이 어떻게 프로젝트를 볼 수 있었나?*

` Create React App`은 기본으로 **Webpack을 내장**하고 있기에 가능했다.

### 2️⃣ 번들러(Bundler) 기능 
<hr/>

1. `Bundling`: 하나의 번들된 파일을 만들어 배포와 실행이 가능하게<br><br>
2. `Transpile`: 브라우저가 이해할 수 없는 확장자(tsx, jsx 등)을 js 파일로 변환. <br> process.env… 등의 Environment variable 의 값을 치환해주는 것도 번들러!.<br><br>
3. `Dependencies`: ‘node_moudles’에 패키지들을 설치<br>‘node_modules’의 버전과 패키지의 버전이 일치하는지 확인 & 관리<br><br>
4. `Automating tasks`: linting, testing, building 등을 자동화

### 3️⃣ 어떤 번들러가 있나?
<hr/>

1. `Webpack`: 에셋 매니지먼트, 코드 분할, 트랜스파일링 등을 포함 오래된 번들러
<br> 레퍼런스가 많. 안정적 / 설정이 복잡하고 느리다.
2. `Rollup`: 번들링과 최적화에 초점을 설정 쉽고 Webpack보다 가볍게
3. `Esbuild`: go로 작성된 번들러, 코드 분할, 트랜스파일링 등을 포함<br> build 속도가 Webpack과 Rollup에 비해 100배 정도 빠름. / 설정이 어렵
4. `Vite`: Vue.js의 제작자인 Evan You가 개발한 최근에 출시된 번들러<br> Dev 서버 실행 속도를 개선 위해, 설정이 쉬우며, 가볍고 빠름