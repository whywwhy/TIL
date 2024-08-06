# IIFE(즉시 실행 함수)

### 1️⃣ IIFE(즉시 실행 함수)란?
<hr/>

**IIFE**
(**I**mmediately **I**nvoked **F**unction **E**xpression)

함수 **정의와 동시**에 **즉시 호출** 되는 함수

### 2️⃣ 사용?
<hr/>

✅ 단 한번만 사용할 함수

✅ 자바스크립트 모듈

### 3️⃣ 형식
<hr/>

```
//익명 즉시 실행함수
(function () {
  var a = 3;
  var b = 5;
  return a * b;
})();
```

이름이 없는 **익명함수**를 사용하는것이 일반적임 <br/>
-> 기명인 즉시 실행 함수도 사용은 ㄱㄴ, 근데 어차피 다시 호출 불가 하니까

### 4️⃣ 사용 이유
<hr/>

1. 필요없는 전역 변수 생성 X -> 전역 스코프 오염 X <br/>
(IIFE -> 내부 변수가 전역으로 저장 안됨)

2. private 변수 생성

외부에서 접근할 수 없는 자체 스코프, 내부를 private하게 보호<br/>
(클로저와 유사한 목적.....)