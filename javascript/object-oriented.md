# JS는 객체지향

### 1️⃣ 객체지향 개발
<hr/>

객체지향 개발을 할 수 있으려면 위 두 가지 특성을 가질 수 있도록 언어에 장치를 두어야 함.

```
1. 대체 가능성
2. 내적 일관성, 내적 동일성
```
자바스크립트는 Prototype으로 두가지 특징을 만족시킴

### 2️⃣ 대체가능성(Polymorphism)
<hr/>

확장한 자식이 부모를 대신 할 수 있음

```
const Parent = class {};
const Child = class extends Parent {};
const a = new Child();
console.log(a instanceof Parent);
```

자바스크립트는 프로토타입 체인을 통해 대체가능성을 보장

### 3️⃣ 내적 동질성
<hr/>

```
const Parent = class {
  wrap() {
    this.action();
  }
  action() {
    console.log("Parent");
  }
};
const Child = class extends Parent {
  action() {
    console.log("Child");
  }
};

const a = new Child();
a.action();
a.wrap();

```

아무리 확장 되기 전 메소드를 호출해도 나의 본질은 변하지 않음