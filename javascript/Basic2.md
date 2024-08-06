# 자스 기본 문법 2 

### 조건문

- if … else
    - 조건문의 평가 결과가 ture면 다음 코드 블록 실행, false면 else 문 다음 코드 블록 실행시킴
    
    ```jsx
    let userInput = prompt("숫자를 입력하세요:");
    
    let number = parseInt(userInput, 10);
    
    if (number > 10) {
        console.log("입력한 숫자는 10보다 큽니다.");
    } else {
        console.log("입력한 숫자는 10 이하입니다.");
    }
    ```
    

- switch
    - 표현식 평가하며 그 값과 일치하는 표현식을 갖는 case문으로 실행 순서를 이동시킴
    
    ```jsx
    let userInput = prompt("숫자를 입력하세요:");
    
    let number = parseInt(userInput, 10);
    
    switch (true) {
        case (number > 10):
            console.log("입력한 숫자는 10보다 큽니다.");
            break;
        default:
            console.log("입력한 숫자는 10 이하입니다.");
            break;
    }
    ```
    

### 반복문

- for문
    - 조건식이 거짓으로 판별될 때 까지 코드 블록을 반복해서 실행시킵니다.
    
    ```jsx
    for (let i = 0; i < 10; i++) {
    	console.log(i);
    }
    ```
    
- while문
    - 조건문의 true면 코드 블록을 계속 반복하고 false면 실행 종료하는.
    - 무한루프 탈출하려면 조건에 if문 부여, break문으로 코드 블록 탈출
    
    ```jsx
    let i = 0;
    
    while( i < 3 ){
    	console.log(i);
    	i++;
    }
    ```
    
- do-while문
    - 코드 블록을 실행시키고 조검눔을 평가함
    
    ```jsx
    let i = 0;
    
    do {
    	console.log(i);
    	i++;
    } while(i<3);
    ```
    

### 함수

- 함수는 지역변수 성질을 가집니다. 지역 변수는 함수 본문에 선언된 변수로 함수 내부에서만 접근 가능해요
- 매개 변수에 기본값을 설정할 수 있다.
- 함수는 항상 무언가를 반환함. return이 없으면 undifiend를 반환함
- 함수를 정의하는 방식은 3개임

1. 함수 선언문
- 함수명, 매개변수 목록, 함수 몸체로 주요 코드 흐름을 차지하는 방식 
    
    ```jsx
    function sum(a, b){
    	let result = a + b;
    	
    	return result;
    }
    ```
    
2. 함수 표현식
- 표현식 형태로 선언된 함수. 함수명 생략 할 수 있음.
- 함수 정의하고, 변수를 할당할 수 있는데 이러한 방식입니다. 
    
    ```jsx
    let x = 1;
    let y = 2;
    
    // 기명함수
    const foo = function multiply(x, y){
    	return x * y;
    };
    
    // 익명함수 
    const bar = function(x, y){
    	retrun x * y;
    };
    ```
    
3. 화살표 함수 
- 함수 표현식 보다 단순하고 간결한 문법 
    
    ```jsx
    let sum = function(a, b){
    	return a+ b;
    };
    ```