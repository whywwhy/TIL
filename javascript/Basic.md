# 자스 기본 문법 사용하기 1

! 자칫하면 실수 할 수 있는 내용을 먼저 중심으로 하겠습니다. 

### 코드 구조

여러개의 구문은 세미콜론을 기준으로 구분할 수 있습니다

```jsx
alert('Hello'); alert('World');
```

줄 바꿈도 여러 개의 구문을 구분하는 데 사용되므로 아래 코드는 정상적으로 동작합니다

```jsx
alert('Hello')
alert('World')
```

이런 동작 방식을 **'세미콜론 자동 삽입(automatic semicolon insertion)'**이라고 합니다. 

그런데 세미콜론 자동 삽입이 동작하지 않을 때도 있습니다.

```jsx
alert("이 메시지가 출력된 후에 에러가 발생합니다.")

[1, 2].forEach(alert)
```

코딩 컨벤션과 같은 코드 스타일 지침서 대부분은 문장의 끝에 세미콜론을 붙이는 걸 권장

코드 블록(`{...}` )이나 코드 블록과 함께 구성되는 문법(예: 반복문) 끝엔 세미콜론을 붙이지 않아도 괜찮습니다.

```jsx
function f() {
  // 함수 선언문 끝엔 세미콜론이 필요 없습니다.
}

for(;;) {
  // 반복문 끝엔 세미콜론이 필요 없습니다.
}
```

세미콜론이 없어도 되는 자리에 ‘여분의’ 세미콜론을 붙이더라도 해당 세미콜론은 무시되기 때문에 에러가 발생하지 않습니다.

### 변수

변수는 아래와 같은 키워드를 이용해 선언

- var.
    - ES5ㄱ 까지 변수를 선언 할 수 있는 유일한 방법은 var 키워드였습니다.(그런데 지금은 아니니 3개가 잇겟죠?)
    - 함수 레벨 스코프 : 전역 변수의 남발 / for loop 초기화식에서 사용한 변수를 for loop 외부 또는 전역에서 참조 할 수 있어요 .
    
    함수 레벨 스코프?
    함수 내에서 선언된 변수는 함수 내에서만 유효, 함수 외부에서는 참조 할 수 없다. 
    즉, 함수 내부 에서 선언한 변수는 지역변수이고 함수 외부에서 선언한 변수는 모두 전역 변수인것.
        
        ```jsx
        function exampleFunc() {
            if (true) {
                var x = 10;
            }
            console.log(x); // 10, 블록 외부에서도 접근 가능
        }
        exampleFunc();
        ```
        
    - var 키워드 생략 허용 : 의도 하지 않은 변수의 전역화
        
        ```jsx
        function globalVarExample() {
            y = 20; // var 키워드 생략
        }
        globalVarExample();
        console.log(y); // 20, 전역 변수로 정의됨
        ```
        
    - 변수 중독 선언 허용 : 의도하지 않은 변수값으 변경
        
        ```jsx
        var z = 30;
        var z = 40; // 중복 선언 허용
        console.log(z); // 40
        ```
        
    - 변수 호이스팅 : 변수를 선언하기 이전에 참조할 수 있어요
    
    호이스팅 : JavaScript에서 변수와 함수 선언이 실제 코드 작성 위치에 상관없이 **해당 범위의 최상단으로 끌어올려지는 것처럼 보이는** 동작
        
        ```jsx
        console.log(a); // undefined, 변수 호이스팅
        var a = 50;
        console.log(a); // 50
        ```
        
- let
    - 블록 레벨 스코프
    
    const로 선언된 변수는 **블록 레벨 스코프**를 가지며, **한 번 값을 할당하면 재할당할 수 없습니다**. 또한, 반드시 선언과 동시에 초기화해야 합니다.
    
    블록 레벨 스코프?
    모든 코드 블록 내에서 선언된 변수는 코드 블록 내에서만 유효, 코드 블록 외부에서는 참조할 수 없다. 
    즉, 코드 블록 내부에서 선언한 변수는 지역변수인 것
        
        ```jsx
        function testLet() {
          if (true) {
            let letVariable = '블록 안에서';
            console.log(letVariable); // '블록 안에서'
          }
        
          // letVariable은 블록 바깥에서 접근할 수 없습니다
          try {
            console.log(letVariable); // ReferenceError: letVariable is not defined
          } catch (error) {
            console.log('letVariable은 블록 밖에서 접근할 수 없습니다');
          }
        }
        
        testLet();
        ```
        
- const
한 번 값을 할당하면 더는 값을 바꿀 수 없는 상수를 정의 할 때 사용됨. 
const는 반드시 선언과 동시에 할당이 이루어져야함 
아니면 SyntaxError 발생. 

만약 const 변수 타입이 객체 → 객체에 대한 참조를 변경 할 수 없음. 
but 재할당은 불가능하지만 할당된 객체의 내용(프로퍼티 추가, 삭제, 프로퍼티 갑 변경)은 가능함
    - const로 선언된 변수가 선언과 동시에 초기화되지 않아서 발생하는 SyntaxError
        
        ```jsx
        const myVariable;
        ```
        
    - const 변수 타입이 객체일 때 객체에 대한 참조를 변경할 수 없음
        
        ```jsx
        const myObject = { key: 'value' };
        myObject = { newKey: 'newValue' }; 
        ```
        
        위 코드에서는 myObject가 처음에 { key: 'value' }로 선언된 후, 
        
        객체에 대한 참조를 변경하려고 시도함. 
        
         const로 선언된 변수는 객체의 참조를 변경할 수 없으므로 TypeError가 발생합니다.
        
    - const 변수의 객체에 대한 내용(프로퍼티 추가, 삭제, 값 변경)은 가능함
        
        ```jsx
        // 객체의 내용 수정 가능 예제
        const myObject = { key: 'value' };
        
        // 프로퍼티 값 변경
        myObject.key = 'newValue';
        console.log(myObject.key); // 'newValue'
        
        // 프로퍼티 추가
        myObject.newKey = 'anotherValue';
        console.log(myObject.newKey); // 'anotherValue'
        
        // 프로퍼티 삭제
        delete myObject.key;
        console.log(myObject.key); // undefined
        ```
        

### 데이터 타입

- number : 정수, 부동 소수점 저장하는데 사용
- string : 문자열을 저장하는데 사용
- boolean : 논리값 true/false 저장 사용
- null : 비어있음, 존재하지 않음 - null 값만을 위한 독립 자료형
- undefined : 값이 할당 되지 않은 상티 - undefined 값을 위한 독립 자료형
- symbol : 고유한 식별자를 사용(es6부터 추가됨)
- object : 자료 구조를 저장하는데 사용됨.

타입을 확인하고 싶으면 typeof 연산자를 사용하면 됩니다. 

! 여기서 널 값은 오브젝트로 찍히니 그 점은 기억해주세요(자바 스크립트 설계상 오류입니다)

```jsx
const num = 12;
const str = "안녕하세요";
const bol = true;
const foo = null;
let joo;
let sym = Symbol('key');

console.log(typeof num); //output : number
console.log(typeof str); //output : string
console.log(typeof bol); //output : boolean
console.log(typeof foo); //output : object
console.log(typeof joo); //output : undefined
console.log(typeof sym); //output : symbol
```

### 연산자

- 산술 연산자
    
    ![스크린샷 2024-07-31 00.07.43.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/c1519b20-cc66-4086-827f-0fd75e392faf/9f31a02f-8a8a-4b01-ab7d-6736883612c2/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-07-31_00.07.43.png)
    
    - 이항 연산자와 단항 산순 연산자로 구분할 수 있음. 산술 연산이 없는 경우 NaN을 반환함
    - 이항 산술 연산자는 2개의 피연산자를 대상으로 연산해 숫자 타입의 값을 만듦
    - 단항 산술 연산자는 1개의 피연산자를 대상으로 연산함
    - + 연산자는 피연사자  중 하나 이상이 문자열인 경우 문자열 연결 연산자로 동작합니다.
    
    ```jsx
    var x = 5;
    var y = 2;
    var a = 'cns';
    var b = 'is best';
    
    // 이항 산술 연산자
    console.log(x + y);  // 덧셈: 7
    console.log(x - y);  // 뺄셈: 3
    console.log(x * y);  // 곱셈: 10
    console.log(x / y);  // 나눗셈: 2.5
    console.log(x % y);  // 나머지: 1
    console.log(x ** y); // 제곱: 25
    
    // 문자열 연결
    console.log(a + ' ' + b); // 'cns is best'
    ```
    

- 할당 연산자
    
    ![스크린샷 2024-07-31 00.08.34.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/c1519b20-cc66-4086-827f-0fd75e392faf/d407ed31-9e85-443a-acd1-e6cff4eaccf6/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-07-31_00.08.34.png)
    
    - 할당 연산자는 우향에 있는 피연산자의 결과를 좌항에 있는 변수에 할당함

- 비교 연산자
    
    ![스크린샷 2024-07-31 00.10.39.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/c1519b20-cc66-4086-827f-0fd75e392faf/97c022b1-0660-45cc-a627-bd4db055e7f6/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-07-31_00.10.39.png)
    
    - 좌항과 우항의 피연산자를 비교해서 boolean 값을 반환함
    - if문이나 for 문과 같은 제어문의 조건식에서 주로 사용됩니다~
    - 동등 비교 연산자 (==) 는 좌항과 우항의 연산자가 타입이 같지 않더라도 타입을 일치시킨 후 비교함.
    이러한 경우에서 많은 부작용이 나기때문에 일치 비교 (===)를 사용하는게 좋습니다.
    
    ```jsx
    let i = '5';     // 문자열
    let j = 5;       // 숫자
    
    console.log(i == j);  // 출력: true  (타입 변환 후 비교)
    console.log(i === j); // 출력: false (타입과 값 모두 비교)
    
    // if문 사용 예제
    if (i == j) {
        console.log("동등"); // 출력: 동등
    } else {
        console.log("비동등");
    }
    
    if (i === j) {
        console.log("일치");
    } else {
        console.log("비일치"); // 출력: 비일치
    }
    ```
    
    ==는 타입 변환 후 비교
    ===는 타입과 값 모두 비교
    
- 논리 연산자
    
    ![스크린샷 2024-07-31 00.14.01.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/c1519b20-cc66-4086-827f-0fd75e392faf/fe597b62-1eb4-4d32-ad19-10c3303b8db9/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-07-31_00.14.01.png)
    
    - 좌항과 우항의 피연산자를 논리 연산함
    - and 연산자 ( && )와 or연산자( || )는 단락 평가를 수행, 평가가 멈춘 시점에 값을 반환함.

