![jslivecodingtest.png](attachment:2f26280f-b4b8-49fe-9d5e-a8aebb0a9cad:jslivecodingtest.png)

### **1. Explain what a callback function is and provide a simple example**

콜백함수는 **다른 함수에 전달되어 일부 작업이 완료된 후 호출되는 함수**이다.

- 콜백이 뭔지, 콜백 예시?
    
    쉬운 ver → 다른 함수가 실행을 끝낸 뒤 실행되는 callback되는 함수 를 말한다. 그리고, 함수를 만들때, parameter 를 함수로 받아서 쓸 수 있는데 그 함수는 callback이다.
    
    자세한 ver → js에서 함수는 object라고 한다. 그래서, 함수는 다른 함수의 인자로 쓰일 수도 어떤 함수에 의해 리턴될 수도 있다. 이런 함수를 고차 함수라고 한다. 결국, 인자로 넘겨지는 함수를 콜백 함수라고 한다. 또한, 단지 함수를 등록하기만 하고 어떤 이벤트가 발생했거나 특정 시점에 도달했을 때 시스템에서 호출하는 함수!
    
    콜백 함수를 설명할 떄에는 변수의 유효범위(스코프)에 대한 이야기, 동기/비동기에 대한 이야기도 하면 좋을 것 같다. 
    
    1. 동기 : 하나의 요청이 오면 완료가 된 후 다음 요청을 실행하는 방식 - 순차적 로직흐름
    2. 비동기 : 어떤 요청이 오면 완료가 되기 전에 다음 요청을 실행하는 방식- 동시 효율적 처리 가능, 즉시 응답X 때문에 예상 밖 결과 나올수도 있음.,콜백함수는 때로는 가독성이나 코드 재사용 면에서도 사용 된다.비동기 방식으로 작성된 함수를 동기 처리하기 위해 필요 하다.
    

```jsx
function modifyArray(arr, callback) {
//일부 작업
    arr.push(100);
//콜백 함수 호출
    callback();
}

const arr = [1,2,3,4,5];

modifyArray(arr, function() {
//익명함수로 콜백함수 전달console.log('array has been modified', arr);//"array has been modified" [1,2,3,4,5,100]
});
```

### **2.Given a string, reverse each word in the sentence**

**[문제]**

```bash
"Hello! Welcome to my Velog. Ask me anything.";
```

해당 문자열을 글자별로 뒤집기, 단어별로 뒤집기를 출력하세요.

**[답]**

```jsx
let str = "Hello! Welcome to my Velog. Ask me anything.";

function reverseBySeparator(str, separator) {
  return str.split(separator).reverse().join(separator);
}

let reverseEntireSentence = reverseBySeparator(str, "");
let reverseEachWord = reverseBySeparator(str, " ");

console.log(reverseEntireSentence, reverseEachWord);
```

### **3. How to check if an object is an arrray of not? Provied some code.**

자바스크립트에서 함수를 호출하는 방법에는,

1. **함수 뒤에 ()를 붙여 호출**하는 방법

2. **call(), apply()를 사용하여 호출**하는 방법이 있다. => **this를 명시적 바인딩 해주는 메서드**

this는 기본적으로 **전역객체인 window**를 가르키거나 **메서드를 호출한 객체**를 가르킨다.

apply()와 call() 메서드는 Function Object에 기본적으로 정의된 메서드로, 첫번째 매개변수를 this로 만들어주는 기능을 한다.

- **Function.prototype.call()**

```jsx
func.call(thisArg[, arg1[, arg2[, ...]]])
```

- thisArg: func 호출에 제공되는 this의 값
- arg1, arg2, ...: func이 호출되어야 하는 **인수**

첫번째 매개변수는 this를 지정하는 값이 들어가야하고, 두번째 매개변수는 호출할 함수의 인수들이 들어가야한다.

```jsx
let person1 = {
    name: 'Jo'
};

let person2 = {
    name: 'Kim',
    study: function() {
        console.log(this.name + '이/가 공부를 하고 있습니다.');
    }
};

person2.study();// Kim이/가 공부를 하고 있습니다.// call()
person2.study.call(person1);// Jo이/가 공부를 하고 있습니다.
```

위와 같이 원래라면 study()를 호출한 person2의 name인 Kim을 가리켜야하지만

call() 메서드를 통해 this가 person1을 가리키면서 this.name의 값이 Jo가 된다.

```jsx
function HowisThis() {
  console.log(this);
}

HowisThis();//window

var obj = {
  x: great,
};

HowisThis.call(obj);//{x:great} HowisThis.apply(obj)로 써도 똑같습니다.
```

함수를 호출하면 this를 콘솔에 찍는데, 함수의 주인인 window 전역객체가 역시 찍힌다.

하지만 call() 메서드를 통해 this를 obj 객체로 바인딩해주면 {x: great} 즉, 객체 obj가 콘솔에 찍힌다.

- **Function.prototype.apply()**

```jsx
fun.apply(thisArg, [argsArray])
```

- thisArg: func 호출에 제공되는 this의 값
- argsArray: func이 호출되어야 하는 인수를 지정하는 유사 배열 객체

call() 메서드와 같이 this를 지정하는 메서드지만, 차이점은 두번째 매개변수가 **배열 형태로 들어가야한다는 점**이다.

(배열 또는 유사배열 객체)

```jsx
function add(c, d) {
  return this.a + this.b + c + d;
}

var o = {a: 3, b: 3};

// 첫 번째 인자는 'this'로 사용할 객체이고,// 이어지는 인자들은 함수 호출에서 인수로 전달된다.
add.call(o, 6, 6);// 18// 첫 번째 인자는 'this'로 사용할 객체이고,// 두 번째 인자는 함수 호출에서 인수로 사용될 멤버들이 위치한 배열이다.
add.apply(o, [20, 10]);// 36
```

---

```jsx
toString() method는 개체를 나타내는 문자열을 반환한다.
그리고 기본적으로 모든 object에 상속되어 있다.
method가 custom object에 의해 재정의되지 않으면,
toString();은 [object type]을 반환한다. 여기서 type은 object type을 의미한다.

function person(name, age) {
      this.name = name;
      this.age = age;
  }
  const thePerson = new person('conut', 30);
  console.log(thePerson);
  console.log(thePerson.toString());// return [object Object]
```

=> **Object.prototype.toString**을 통해 object type을 반환해서 array인지 아닌지를 판별 할 수 있다.

```jsx
const arr = [];

//call을 안쓰면 전역객체를 가리켜서 쓰는건가?console.log(Object.prototype.toString(arr));//"[object Object]"console.log(Object.prototype.toString.call(arr));//"[object Array]"
```

**[답]**

```jsx
const arr = [];
const number = 18;

//1.solutionfunction isArray(arr){
  if(Object.prototype.toString.call(arr) === '[object Array]'){
    console.log('yes');
  }else{
    console.log('no');
  }
}

isArray(arr);//yes
isArray(18);//no//2.solutionfunction isArray2(arr){
  console.log(Array.isArray(arr));
}

isArray2(arr);//true
isArray2(number);//false
```

- Object.prototype.toString.call(array)
- Array.isArray(array)

두가지의 방법이 있다.

### **4. How to empty an array in JavaScript?**

- solution 1

```jsx
let arrayList = ['a','b','c','d','e','f'];

//solution 1
arrayList = [];

console.log(arrayList);// []
```

하지만 해당 방법은 다른 곳에 원래 배열에 대한 참조가 없는 경우에만 권장된다.

```jsx
let arrayList = ['a','b','c','d','e','f'];

let anotherArrayList = arrayList;

arrayList = [];

console.log(anotherArrayList);//['a','b','c','d','e','f']
```

- solution 2

```jsx
let arrayList = ['a','b','c','d','e','f'];

let anotherArrayList = arrayList;

arrayList.length = 0;

console.log(anotherArrayList);// []
```

위와 같이 원래 배열의 길이를 0으로 설정주면 **원래 배열을 가리키는 모든 참조 변수를 업데이트**한다.

- solution 3

```jsx
let arrayList = ['a','b','c','d','e','f'];

let anotherArrayList = arrayList;

arrayList.splice(0, arrayList.length);//원본 배열을 수정console.log(anotherArrayList, arrayList);//[],[]
```

해당 방법도 완벽하게 작동한다. arrayList의 원본을 잘라서 다 날리는 방법인 것같다.

- solution 4

```jsx
let arrayList = ['a','b','c','d','e','f'];

//arrayList가 빌 때까지 계속 popwhile(arrayList.length){
  arrayList.pop();
}

console.log(arrayList);// []
```

### **5. How would you check if a number is an integer?**

이 방법은 간단하다. **1로 나눴을 때 나머지가 0이면 정수**이다.

```jsx
function isInt(num){
  console.log(num % 1 === 0 ? true : false);
}

isInt(1);//true
isInt(0.1);//false
```

### **6. Implement enqueue and dequeue using only two stacks**

enqueue는 push와 같이 뒤로 추가하고, dequeue는 가장 앞에 원소가 빠지는 것이다.

```jsx
const inputStack = [];
const outputStack = [];

function enqueue(stackInput, item){
  return stackInput.push(item);
}

function dequeue(stackInput, stackOutput){
//길이가 0보다 작거나 같으면?if(stackOutput.length <= 0){
    while(stackInput.length > 0){
//inputStack에 있는 걸 빼서 다 stackOutput에 넣어//그럼 거꾸로 들어가는 거랑 다르지않아let elementToOut = stackInput.pop();
      stackOutput.push(elementToOut);
    }
  }

//0보다 크면//그럼 거꾸로 들어갔으니깐 pop해주면 가장 앞에 원소를 빼줄 수 있는거지..return stackOutput.pop();
}
```

### **7. Make this work**

**[문제]**

```jsx
duplicate([1, 2, 3, 4, 5]);// [1,2,3,4,5,1,2,3,4,5]
```

**[답]**

```jsx
const arr = [1,2,3,4,5];

function duplicate(arr){
//concatconsole.log(arr.concat(arr));

//spread operatorconsole.log([...arr,...arr]);
}

duplicate(arr);
```

- concat
    - 기존의 배열을 변경하지 않으면서 배열 끝에 요소를 추가해 **새 배열을 반환**한다.

```jsx
const arr = [1,2,3,4,5];
const newArr = arr.concat(6);

console.log(arr, newArr);//[1,2,3,4,5] [1,2,3,4,5,6]
```

- spread operator(...)
    - 배열 or 문자열 or 객체 요소 하나를 **펼쳐 복사해서 따로 불러온다.**
    - 큰 배열로 작업할 땐 메모리 부족으로 오류가 발생할 수 있다.

### **8.Write a "mul" function which will properly when invoked as below syntax**

**[문제]**

```jsx
console.log(mul(2)(3)(4));//24console.log(mul(4)(3)(4));//48
```

closure를 사용해서 구현을 할 수 있다.

**함수 내에서 함수를 바로 실행시키는 대신 반환값으로 함수를 내보낸다.**

**[답]**

```jsx
function mul(x){
	return function(y){
            return function(z){
                return x * y * z;
            }
    }
}
```

### **9. Write a function that would allow you to do this?**

**[문제]**

```jsx
let addSix = createBase(6);
addSix(10);// 16
addSix(21);// 27
```

**[답]**

해당 문제로 closure를 사용해서 **함수 밖에 선언된 수를 기억하고 가져온다.**

```jsx
function createBase(baseNumber){
	return function(N){
    		return baseNumber + N;
    }
}
```

### **10. FizzBuzz Challenge**

100까지 반복문을 돌리면서 3의 배수일 때는 fizz를 출력하고 5의 배수일 때는 buzz를 출력하고 3과 5의 배수일 때는 fizzbuzz를 출력한다.

**[답]**

```jsx
for(let i=1; i<=100; i++){
  let f = i % 3 === 0;
  let b = i % 5 === 0;

//3의 배수일 때 5의 배수이면 fizzbuzz//아니면 그냥 3의 배수니깐 fizz//3의 배수아닐 때 5의 배수이면 buzz//둘다 아니면 그냥 iconsole.log(f ? (b ? "fizzbuz" : "fizz") : b ? "buzz" : i);
}
```

### **11. Given two strings, return true if they are anagrams of one another**

애너그램 : 같은 단어의 문자를 재배열하여 다른 뜻을 가지는 다른 단어로 바꾸는 것이다.

그래서 두 단어가 서로의 애너그램이면 true를 리턴해라.

**[답]**

```jsx
let firstWord = "Mary";
let secondWord = "Army";

function isAnagram(first, second){
  let rowfirst = first.toLowerCase();
  let rowsecond = second.toLowerCase();

  rowfirst = [...rowfirst].sort().join('');
  rowsecond = [...rowsecond].sort().join('');

  console.log(rowfirst === rowsecond);
}

isAnagram(firstWord, secondWord);
```

### **12. How would you use a closure to create a private counter?**

closer(함수를 return)를 이용해서 private 변수를 업데이트해라.

외부함수는 private 변수를 건들 수 없다.

```jsx
function counter(){
    let _counter = 0;

    return {
        add : function(increment) { _counter += increment },
        retrieve : function() { console.log(`the counter is currently at ${_counter}`); }
    }
}

let c = counter();

c.add(5);
c.add(9);

c.retrieve();//"the counter is currently at 14"
```

### 

### **13. Write a function that would allow you to do this**

**[문제]**

```jsx
multiply(5)(6);//30
```

**[답]**

```jsx
function multiply(a){
    return function(b){
        return a * b;
    }
}
```

### **14. How does the this keyword work? Provide some code examples**

```jsx
function foo(){
	console.log(this.bar);
}

var bar = 'global';

var obj1 = {
    bar: 'obj1',
    foo: foo
};

var obj2 = {
	bar: 'obj2'
};

foo();// 함수의 this는 전역객체를 가르키고 그럼 global
obj1.foo();//obj1이 호출했으니 obj1
foo.call(obj2);//obj2로 call() 메서드를 통해 바인딩 해줬으니 obj2new foo();//생성자 함수로 만든 객체를 가르키는데 객체 안에는 bar가 없으니 undefined?
```

### **15. How would you create a private variable in JavaScript?**

**[문제]**

```jsx
function func(){
	let priv = "secret code";
}

console.log(priv)//throw Error
```

위와 같이 let으로 변수를 선언하면 let은 블록 스코프이기 때문에 블록 밖에서는 접근할 수가 없다.

**[답]**

```jsx
function func(){
	let priv = "secret code";
    return function(){
    	return priv;
    }
}

let gerPriv = func();
console.log(gerPriv());//secret code
```

### **16. When would you use the bind function?**

```jsx
let person1 = {
	name: 'jo'
};

let person2 = {
	name: 'kim',
    study: function() {
    	console.log(this.name + '이/가 공부를 하고 있습니다.');
    }
}

person2.study();//kim이/가 공부를 하고 있습니다.//변수를 할당하여 호출하는 형태로 사용해야한다.let student = person2.study.bind(person1);

student();//jo이/가 공부를 하고 있습니다.
```

### **17. Write a recursive function that performs a binary search**

재귀함수를 통한 이진탐색(**정렬된 리스트에서 검색 범위를 줄여 나가면서** 검색 값을 찾는 알고리즘)

```jsx
function recursiveBinarySearch(array, value, leftPosition, rightPosition){
//종료조건(찾지 못했을 때)if(leftPosition > rightPosition) return -1;

    let middlePivot = Math.floor((leftPosition + rightPosition) / 2);

    if(array[middlePivot] === value){
    	return middlePivot;
    }else if(array[middlePivot] > value){
//찾는 value값보다 중앙값이 더 크면return recursiveBinarySearch(array, value, leftPosition, middlePivot - 1);
    }else{
//중앙값이 더 작으면return recursiveBinarySearch(array, value, middlePivot + 1, rightPosition);
    }
}
```

반복문을 이용한 방법도 있다.

```jsx
function binarySearch(array, value, leftPosition, rightPosition){
	while(leftPosition <= rightPosition){
    	let mid = Math.floor((leftPosition + rightPosition)/2));

        if(array[mid] === value){
        	return mid;
        }else if(array[mid] > value){
        	rightPosition = mid - 1;
        }else{
        	leftPosition = mid + 1;
        }
    }

//못찾으면return -1;
}
```

### **18. closure**

- 클로저의 개념
    - 클로저는 ‘함수’를 지칭하고 또 ‘그 함수가 선언된 환경과의 관계’의 개념이다.
    - 클로저는 ‘자신이 선언될 당시의 환경을 기억하는 함수’이다.
    - 클로저는 ‘내부함수가 외부함수의 context에 접근’할 수 있는 것을 가리킨다.
    
    1. **전역변수 사용의 최소화**
        - 전역변수가 많으면 의도치 않게 어디에서든 접근하는 상황이 발생할 수 있다. 클로저를 이용하여 전역변수를 최소한으로 사용함으로써 이러한 실수나 예외적인 상황을 방지할 수 있다.
    2. **데이터 보존 가능**
        - 클로저 함수는 외부 함수의 실행이 끝나더라도 외부 함수 내 변수를 사용할 수 있다. 따라서 특정 데이터를 스코프 안에 가두어 둔 채로 계속 사용할 수 있게하는 `폐쇄성`을 갖는다.
    3. **모듈화를 통한 코드 재사용에 편리**
        - 클로저 함수를 각각의 변수에 할당하면 각자 독립적으로 값을 사용하고 보존 가능하다. 이와 같이 함수의 재사용성을 극대화하고 함수 하나를 독립적인 부품의 형태로 분리하는 것을 `모듈화`라고 한다. 클로저를 통해 데이터와 메소드를 묶어다닐 수 있기에 클로저는 모듈화에 유리하다.
    4. **정보의 접근 제한 (캡슐화)**
        - `클로저 모듈 패턴`을 사용해 객체에 담아 여러 개의 함수를 리턴하도록 만들어 정보의 접근을 제한할 수 있는데, 이를 `캡슐화`라고 한다.

**[문제]**

```jsx
sum(1)(2)();//3
sum(1)(2)(3)(4);//10
```

**[답]**

클로저랑 재귀를 이용해서 풀이하면 된다.

```jsx
function sum(a){
	return function(b){
    	if(b){
        	return sum(a+b);
        }else{
        	return a;
        }
    }
}
```

### **19. delay**

**[문제]**

```jsx
const delay = () => {}

const main = async() => {
    console.log('1번');
    delay(4);

//4초 딜레이 시킨 다음에console.log('2번');
}

main();
```

**[답]**

```jsx
const delay = (n) => {
//resolve() 함수를 실행하는 것 자체만으로도 Promise는 fullfilled 상태가 된다.//비동기 처리를 n초 있다가 성공하는거구나..return new Promise((resolve) => setTimeout(resolve, n*1000));
}

const main = async() => {
    console.log('1번');
    await delay(4);

//4초 딜레이 시킨 다음에console.log('2번');
}

main();
```

### **20. array 중복 요소 제거**

**[답]**

```jsx
const exampleArray = [4, 2, 9, 2, 4, 6, 8, 9];

//indexOf는 맨 앞의 원소의 인덱스를 리턴하기 때문에 뒤의 중복 원소를 삭제할 수 있다.const uniqueArray = exampleArray.filter((v,i) => exampleArray.indexOf(v) === i);

console.log(uniqueArray);
```

```jsx
const exampleArray = [4, 2, 9, 2, 4, 6, 8, 9];

return [...new Set(exampleArray)];
```

### **21. str 중복 요소 제거**

```jsx
const exampleStr = 'aabbbeedudaacca'

return [...new Set(exampleStr)].join('');
```

```jsx
let exampleStr = 'aabbbeedudaacca';

exampleStr = [...exampleStr];

let uniquestr = exampleStr.filter((v,i) => exampleStr.indexOf(v) === i);

return uniquestr.join('');
```

### **22. Math.max**

**[문제]**

숫자형 array를 매개변수로 갖게 하고, Math.max를 활용해 최댓값을 출력하세요.

(단, 스프레드 연산자를 쓰지 않고)

만약 스프레드 연산자를 쓴다면

```jsx
const exampleArray = [4, 2, 8, 1, 1, 3]

return Math.max(...exampleArray);
```

하지만 쓰지 않는다면,

**apply() 메서드**를 통해 배열형태로 인수를 넘겨주거나..(근데 이건 너무 큰 배열이면 메모리 초과)

아니면 reduce를 통해 구해준다.

```jsx
const exampleArray = [4, 2, 8, 1, 1, 3]

return Math.max.apply(null, exampleArray);
```

왜 null 이냐?? apply 메서드 첫번쨰 인자로 this값 전달하기 때문 

apply 는 자스 함수 호출 방식 중 하나 

근데 math.max는 this(지금 실행하고 있는 문맥 컨텍스트), 즉 math.max 동작 this 값 영향 ㄴㄴ 그래서 null은 관행적으로 넣음

1넣어도 작동함

```jsx
const exampleArray = [4, 2, 8, 1, 1, 3]

//계속 큰 값을 대입하면서 max를 찾아낸다.return exampleArray.reduce((a,b) => Math.max(a,b), -Infinity);
```