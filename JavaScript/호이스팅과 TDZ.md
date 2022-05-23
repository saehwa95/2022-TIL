# 호이스팅과 TDZ란?

## 스코프, 호이스팅, TDZ
### 스코프
- 참조 대상 식별자를 찾아내기 위한 규칙이다.
- 변수에 접근할 수 있는 범위로 전역 스코프와 지역 스코프가 있다. 
- 전역 스코프 : 전역에 선언되어있어 코드의 어느곳에서든 해당 변수에 접근할 수 있다. 
- 지역 스코프 : 코드블록, 함수내에서의 범위이며 자기 자신과 하위 범위에서만 참조할 수 있다. 이곳에서 선언된 변수는 지역 변수(Local Variable)가 되며 해당 지역과 그 하위 지역에서만 참조가 가능하다.

### 호이스팅
함수 안에 있는 선언을 모두 끌어 올려서 해당 함수 유효 스코프의 최상단에 선언하는 것을 말한다. 

#### 호이스팅의 대상
- 자바스크립트는 ES6에서 도입된 let, const를 포함하여 모든 선언(var, let, const, function, function*, class)을 호이스팅한다.
- 호이스팅(Hoisting)이란, var 선언문이나 function 선언문 등을 해당 스코프의 선두로 옮긴 것처럼 동작하는 특성을 말한다.
- let/const 변수 선언과 함수 표현식 에서는 호이스팅이 발생하지 않는다.

### TDZ
- TDZ(Temporal Dead Zone)
- 선언 전에 변수를 사용하는것을 허용하지 않는 개념상의 공간

### TDZ의 영향을 받는 구문
#### const 변수
const 변수는 선언 및 초기화 전 줄까지 TDZ에 있다. 
```JavaScript
// Does not work!
pi; // throws `ReferenceError`
const pi = 3.14;
```
const 변수는 선언한 후에 사용해야 한다. 
```JavaScript
const pi = 3.14;

// Works!
pi; // => 3.14
```

#### let 변수
let도 선언 전 줄 까지 TDZ의 영향을 받는다. 
```JavaScript
// Does not work!
count; // throws `ReferenceError`
let count;

count = 10;
```

#### class 구문
머리맡 부분에서 보았듯이 선언 전에는 class를 사용할 수 없다. 
```JavaScript
// Does not work!
const myNissan = new Car('red'); // throws `ReferenceError`

class Car {
  constructor(color) {
    this.color = color;
  }
}
```
위 예제가 동작하려면 class를 선언한 후 사용하도록 수정해야한다.
```JavaScript
class Car {
  constructor(color) {
    this.color = color;
  }
}

// Works!
const myNissan = new Car('red');
myNissan.color; // => 'red'
```

#### var, function, import 구문
var, function 선언은 TDZ에 영향을 받지 않고 현재 스코프에서 호이스팅이 된
 
var 변수는 선언하기 전에 접근하면, Undefined를 얻게 된다.
```JavaScript
// Works, but don't do this!
value; // => undefined
var value;
```
하지만 함수는 선언된 위치와 상관없이 동일하게 호출된다.
```JavaScript
// Works!
greet('World'); // => 'Hello, World!'
function greet(who) {
  return `Hello, ${who}!`;
}

// Works!
greet('Earth'); // => 'Hello, Earth!'
```
함수 선언 전에 호출해도 에러가 발생하지 않는 이유는 호이스팅 때문이다. 

## 함수 선언문과 함수 표현식에서 호이스팅 방식의 차이
### 함수 선언문에서의 호이스팅
- 함수 선언문은 코드를 구현한 위치와 관계없이 자바스크립트의 특징인 호이스팅에 따라 브라우저가 자바스크립트를 해석 할 때 맨위로 끌어 올려진다.

### 함수 표현식에서의 호이스팅 
- 함수 표현식은 함수 선언문과 달리 선언과 호출 순서에 따라서 정상적으로 함수가 실행되지 않을 수 있다.
- 함수 표현식에서는 선언과 할당의 분리가 생긴다.

```JavaScript
try {
    eat();  // 함수 선언문 실행
    run(); // 함수 표현식 실행
    
} catch(error){
    console.log("에러 발생");
}

function eat(){
    console.log("eat");
};

const movemove = () => console.log("run");

// 실행 결과
// eat
// 에러 발생
```
- 원래 바자스크립트의 모든 선언에는 호이스팅이 일어난다. 
- 하지만 let/const/var을 이용한 선언문은 마치 호이스팅이 발생하지 않는 것처럼 동작한다. 
- var로 선언된 변수와 달리 let으로 선언된 변수를 선언문 이전에 참조하면 참조에러가 발생한다.
-  이는 let 키워드로 선언된 변수가 스코프의 시작에서 변수의 선언까지 "일시적 사각지대(TDZ, Temporal Dead Zone)에 빠지기 때문이다. 

## 실행 컨텍스트와 콜 스택
### 실행 컨텍스트
어떤 실행 컨텍스트가 활성화될 때, 자바스크립트 엔진은 해당 컨텍스트의 코드를 실행하는데 필요한 환경 정보들을 수집해서 실행 컨텍스트에 저장한다. 
 
다시 말해, 실행 컨텍스트란 코드가 실행되기 위해 필요한 정보들을 가진 범위를 추상화하기 위해 객체 형태로 나타낸 것을 말한다.

### 콜 스택(= 호출 스택)
- 자바스크립트는 단일 스레드 프로그래밍 언어로 한 번에 하나의 일을 처리할 수 있습니다. 
- 단일 스레드에서 코드를 실행하는 것은 멀티 스레드 환경에서 발생하는 복잡한 시나리오를 고려할 필요가 없으므로 매우 쉽습니다. 
- 그러나 자바스크립트에서는 하나의 호출 스택만 있기 때문에, 하나의 함수 처리가 엄청 느려서 다른 함수 실행에 지장을 줄 수 있습니다.

## 스코프 체인, 변수 은닉화
### 스코프 체인
- 스코프체인은 해당 코드의 유효한 범위 안에 있는 변수를 정의하는 객체의 리스트
- 변수 값을 얻으려 할 때 스코프 체인에서 변수를 찾는다. 

### 변수 은닉화
#### 클로저
- 클로저는 생성될 당시의 환경을 기억하는 함수 
- 여기서 환경은 스코프체인 자체를 말하고, 스코프체인을 통해 접근할 수 있는 변수나 함수가 스코프가 해제되어야 할 시점에도 사라지지 않는다는 말이다. 
- 이런 스코프는 객체가 갖는 성질인 캡슐화와 은닉화를 구현하는데 사용될 수 있다. 

## 실습

```JavaScript
let b = 1;

function hi () {

const a = 1;

let b = 100;

b++;

console.log(a,b);

}

//console.log(a);

console.log(b);

hi();

console.log(b);
```

```JavaScript
const a = 1;
let b = 1;

function hi () {



let b = 100;

b++;

console.log(a,b);

}

console.log(a);

console.log(b); // 값 : 1 (전역변수 let b = 1)

hi(); // hi() 로 찍은 console.log(a,b) 값 : 1, 101

console.log(b); // 값 : 1 (전역변수 let b = 1)

// 주석의 오류 원인 : a의 선언을 function hi () 내부에서 했기때문에 값을 불러올 수 없다. 전역변수로 선언해주면 오류가 발생하지 않는다. 
```

### 참고
- [호이스팅](https://velog.io/@jangwonyoon/%ED%98%B8%EC%9D%B4%EC%8A%A4%ED%8C%85%EA%B3%BC-TDZ%EB%8A%94-%EB%AC%B4%EC%97%87%EC%9D%B4%EA%B3%A0-%EC%96%B4%EB%96%A4-%EC%97%B0%EA%B4%80%EC%9D%B4-%EC%9E%88%EC%9D%84%EA%B9%8C%EC%9A%94)
- [전체적인 내용(유시니버스)](https://usiniverse.tistory.com/13)
