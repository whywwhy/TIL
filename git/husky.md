# Husky??

### 1️⃣ Husky가 뭘까?
<hr/>

### 1. git hook 이란?
1. Git Hooks?  Git 과 관련한 어떤 이벤트가 발생했을 때 특정 스크립트를 실행할 수 있도록 하는 기능 (ex. commit, push)

2. git hook 설정은 까다롭, 모두가 메뉴얼하게 사전 과정을 수행해야지만 hook이 실행을 보장할 수 있고, 실수로라도 사전 과정을 시행하지 않는다면 hook이 실행되지 X

-> Git Hooks 을 `반드시 적용하게끔 강제`하는 방법은?  만약 프로젝트가 모듈 의존성을 관리하기 위해 npm 을 사용하고 있다면 `husky` 는 모든 팀원과 공유할 수 있는 좋은 방법

### 2. Husky 란?
```1. git hook 설정을 도와주는 npm package
2. 번거로운 git hook 설정이 편함
3. npm install 과정에서 사전에 세팅해둔 git hook을 다 적용시킬 수 있어서 모든 팀원이 git hook 실행이 되도록 하기가 편함
```

`-> 코드형식이 맞지 않거나 오류가 발생했을 때 푸쉬를 막아준다!`

### 2️⃣ 사용해보기
<hr/>

yarn add -D husky로 husky 설치

package.json에 아래 코드 작성

```
  "scripts": {
    "prepare": "husky install",
```

yarn prepare 로 husky 폴더 생성

아래 코드로 특정 이벤트에 실행할 스크립트 넣기