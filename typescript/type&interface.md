# Type & Interface 차이점

### 1️⃣ 타입 확장 방법
<hr/>

 ```
 type Age = number;       // 타입 별칭
type Birth = Age | string;   // 타입 연산자

interface Food {
  calories: number;
  tasty: boolean;
}

interface Sushi extends Food {
  salty: boolean;
}

interface Cake extends Food {
  sweet: boolean;
}
 ```

인터페이스가 반드시 인터페이스만 상속받아야 하는 것 X

인터페이스는 객체 타입, 클래스, 다른 인터페이스 모두를 상속받을 수 O


### 2️⃣ 상속 시 상위 Interface와 충돌 나면 금지, Type은 최대한 허용
<hr/>

```
type Age = number;       // 타입 별칭
type Birth = Age | string;   // 타입 연산자

interface Food {
  calories: number;
  tasty: boolean;
}

interface Sushi extends Food {
  salty: boolean;
}

interface Cake extends Food {
  sweet: boolean;
}
인터페이스가 반드시 인터페이스만 상속받아야 하는 것은 아니다. 사실 인터페이스는 객체 타입, 클래스, 다른 인터페이스 모두를 상속받을 수 있다.

4-2 Interface는 상속할 때 상위 Interface와 충돌 나면 안되지만, Type은 최대한 허용하는 형태로 동작한다.
interface A {
  good(x: number): string;
  bad(x: number): string;
}

interface B extends A {
  good(x: number): string;
  bad(x: number): number;    // A의 bad의 리턴 타입과 달라서 에러
}

type A = {
  good(x: number): string;
  bad(x: number): string;
};

type B = A & {
  good(x: number): string;
  bad(x: number): number;
};

const b: B = {
  good(x: number): string {
    return x.toString();
  },
  bad(x: number): string | number {
    return x % 2 === 0 ? x : x.toString();
  },
};
```

`type B`는 `bad(x: number): string` 와 `bad(x: number): number` 를 둘 다 가질 수  O

### 3️⃣   Interface 선언
<hr/>

```
interface Mask {
  color: string;
}

interface Mask {
  size: number;
}

const mask: Mask = {
  color: "White",
  size: 12,
};
```

인터페이스 같은 이름으로 여러번 정의 가능 -> 각 정의 하나로 합쳐짐

### 4️⃣ 함수 프로퍼티
<hr/>

```
type Callback = {
  (message: string): void;
  (message: string, line: number): void;
  isfulfilled: boolean;
};

const callback: Callback = function callback(message: string, line?: number) {
  console.log(message + "call");
  callback.isfulfilled = true;
};
callback.isfulfilled = false;

callback("foo");
console.dir(callback);
```