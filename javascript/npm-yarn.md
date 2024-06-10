# npm, yarn 차이

### 1️⃣ npm / yarn
<hr/>

npm, yarn -> 자바스크립트 런타임 환경인 노드(Node.js)의 패키지 관리자

자바스크립트로 만든 다양한 패키지를 npm 온라인 데이터베이스 (opens new window)에 올리면 npm, yarn과 같은 패키지 관리자를 통해 설치 및 삭제 O

명령 줄 인터페이스(Command-line interface, CLI)를 통해 패키지 설치 및 삭제뿐 아니라 패키지 버전 관리, 의존성 관리도 편리하게 O

### 자바스크립트 패키지 관리자? 
패키지 -> npm에 업로드된 노드 모듈

다양한 자바스크립트 프로그램이 패키지라는 이름으로 npm에 등록, 패키지가 다른 패키지를 사용할 경우 의존 관계를 가짐

이러한 패키지들을 사용하기 위해서는 다운로드, 설치, 업데이트, 의존성 관리, 제거 등 복잡한 상황들이 많이 생기는데 패키지 매니저는 이러한 과정들을 자동화하여 편리하고 안전하게 수행할 수 있게

### 2️⃣ npm
<hr/>
NPM(Node Package Manager)-> 자바스크립트 언어를 위한 패키지 관리자

Node.js의 기본 패키지 관리자

NPM 툴을 이용하여사람들이 Node패키지를 만듦
업로드하며 공유할 수 있어서 누구나 게시된 패키지를 사용할 O

개발자 입장에서는 단 몇 줄의 command로 게시된 패키지들을 설치받아서 사용할 수 O

Node.js를 설치(기본적으로 npm은 Node.js 내에 내장되어 있습니다) 

-> 명령어 한 줄로 기능의 추가가 가능합니다.

### 명령어

```
npm init : package.json 생성
npm install : package.json 파일 및 해당 종속성에 나열된 모든 모듈 설치
npm install package_name@버전 : 특정 패키지의 특정 버전 설치
npm install 주소 : 특정 저장소 내 패키지 설치. 주로 github을 이와 같이 설치
npm install package_name -g : 옵션. 글로벌로 설치 / 로컬의 다른 프로젝트도 이 패키지를 사용 가능하게
npm uninstall : 패키지 삭제 명령어
npm update : 설치한 패키지들을 업데이트
npm dedupe : 중복 설치된 패키지들을 정리해주는 명령어
```

### 3️⃣ yarn
<hr/>

yarn은 2016년 페이스북에서 개발한 패키지 관리자

리액트(React)와 같은 프로젝트를 진행하며 겪었던 어려움을 해결하기 위해 개발됨.

npm과 같은 기능을 수행, npm 레지스트리와 호환하면서 속도나 안정성 측면에서 npm보다 향상

### 명령어

```
> yarn init : package.json 생성
yarn or yarn install : package.json 파일 및 해당 종속성에 나열된 모든 모듈을 설치
yarn add package_name@버전 : 특정 패키지의 특정 버전 설치
yarn add 주소 : 특정 저장소 내 패키지 설치. 주로 github을 이와 같이 설치
yarn global add package_name : 옵션. 글로벌로 설치. 로컬의 다른 프로젝트도 이 패키지를 사용 가능하게
yarn remove : 패키지 삭제 명령어
yarn upgrade : 설치한 패키지들을 업데이트
npm dedupe : 중복 설치된 패키지들을 정리
```

### 4️⃣ npm vs yarn
<hr/>

### 속도

npm과 yarn의 주요 차이점 

-> 패키지 설치 프로세스를 처리하는 방법

 npm은 패키지를 한 번에 하나씩 순차적으로 설치
yarn은 여러 패키지를 동시에 가져오고 설치하도록 최적화, 패키지 설치 속도 측면에서 yarn이 npm보다 빠름.

### 보안

npm은 자동으로 패키지에 포함된 다른 패키지 코드를 실행
 
 -> 이 특징은 편리하지만 안정성을 위협 이로 인해 보안 시스템에 몇 가지 취약성이 발생, 나중에 심각한 문제가 발생할 수 O
 
yarn은 yarn.lock 또는 package.json파일에 있는 파일만을 설치

 보안은 yarn의 핵심 기능 중 하나, 최근 npm의 업데이트에서 npm의 보안 업데이트도 크게 향상