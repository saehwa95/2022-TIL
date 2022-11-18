# JavaScript의 자료형과 JavaScript만의 특성

## 느슨한 타입의 동적 언어
- 모든 프로그래밍 언어에는 내장된 자료구조가 존재하지만 보통 그 내용은 언어마다 다르다. 
   
 #### 동적 타입
+ JavaScript는 느슨한 타입(loosely typed)의 동적(dynamic) 언어
+ JavaScript의 변수는 어떤 특정 타입과 연결되지 않으며, 모든 타입의 값으로 할당 (및 재할당) 가능하다.
+ 장점 : 런타임까지 타입에 대한 결정을 끌고 갈 수 있기 때문에 유연성이 높다. 

## 느슨한 타입(loosely typed)의 동적(dynamic) 언어의 문제점 & 보완 방법
C언어나 Java와 같은 언어들은 변수 선언 시 변수에 저장할 값의 종류를 사전에 지정한다. 
  
그렇기 때문에 타입에 맞지 않는 값이 있으면 실행 이전에 에러가 발생한다. 
  
하지만 동적언어는 다르다. 실행(런타임)을 하며 에러를 발생시키기 때문에 에러를 늦게 찾아내게 된다.
  
런타임 시 확인할 수 밖에 없기 때문에 코드가 길고 복잡해질 경우 타입 에러를 찾기가 어려워 진다. 

##### 정리해보자면, 
정적 언어(C, java 등)는 런타임 시 타입이 정해져있기 때문에 개발 속도는 높아진다. 
  
다만, 코드를 수정하면서 타입을 변경하기 까다로울 수 있다. 
  
반면 동적 언어(JS, python 등)는 컴파일 시 타입을 결정하기 때문에 안정성이 높고 실행 속도가 빠르다. 
  
하지만 런타임 시 타입을 자동으로 변경하게 되기 때문에 타입 에러를 발생시킬 수 있다.

에러가 발생했을때 코드가 길고 복잡해질 경우 타입 에러를 찾기 어려워지는데, 이때 TypeScript나 Flow 등을 사용해 보완할 수 있다.

- 컴파일에 대한 이해를 위해 참고한 자료 : https://devlog-of-yein.tistory.com/6


## JavaScript 형변환
- 변수 선언

```JavaScript
let a = 5   //  숫자형
let a = '5' //  문자형
```

- 문자형 -> 숫자형

```JavaScript
let 변수 = parseInt(문자);   // 문자를 정수형 숫자로 변환
let 변수 = parseFloat(문자); // 문자를 실수형 숫자로 변환
let 변수 = Number(문자);     // 문자를 정수&실수형 숫자로 변환

let a = 100

let a = "100" // 문자형 100
let b = "99.99" // 문자형 99.99
let c = parseInt(a) // 숫자형 정수 100
let d = parseInt(b) // 숫자형 정수 99
let e = parseFloat(a) // 숫자형 실수 100
let f = parseFloat(b) // 숫자형 실수 99.99
let g = Number(a) // 숫자형 정수 99
let h = Number(b) // 숫자형 실수 99.99
```

- 숫자형 -> 문자형


```JavaScript
let a = String(숫자); // 숫자를 문자로 변환해줌
let a = 숫자.toString(진법) // 숫자를 문자로 변환해줌. 변환하면서 진법을 바꿀 수 있음.
let a = 숫자.toFixed(소수자릿수); // 숫자를 문자로 변환해줌. 실수형의 소수점자리를 지정할 수 있음.
let a = 숫자 + "문자열" // 숫자와 문자열을 한 문자열로 더해줌.

let a = 123; // 숫자형 123
let b = String(a);    //문자형 123
let c = a.toString();    //문자형 123
let d = a.toString(2);    //문자형 1111011(2진법)
let e = a.toString(16);    //문자형 7b(16진법)
let f = a.toFixed();    //문자형 123
let g = a.toFixed(1);    //문자형 123.0
```

## ```동등 연산자==```, ```일치 연산자===```
#### ```==```(동등 연산자)
- 동등 연산자(```==```)는 두 개의 피연산자가 동일한지 확인하며, ```Boolean```값을 반환한다.
- 일치 연산자(```===```)와는 다르게 다른 타입의 피연산자들끼리의 비교를 시도한다.
```
x == y
```
- 두 피연산자가 모두 객체일때, 두 피연산자가 동일한 객체를 참조할때에만 ```true```를 반환한다.
- 하나의 피연산자가 ```null```이고 다른 하나가 ```undefined```일때, ```true```를 반환한다.
- 두 피연산자의 타입이 다를 경우, 비교하기 전에 동일한 타입으로 변환하도록한다. 
  - 숫자와 문자열을 비교할 경우, 문자열을 숫자로 변환하도록 한다.
  - 하나의 피연산자가 ```Boolean```일 경우, ```Boolean``` 피연산자가 ```true```일 경우 1로 변환하고, ```false```일 경우, +0으로 변환한다.
  - 하나의 피연산자가 객체이고 다른하나가 숫자나 문자열이면, 객체를  ```valueOf()```나 ```toString()```를 사용해 기본 데이터 타입으로 변환하도록한다.
 - 두개의 피연산자가 동일한 타입일 경우, 다음과 같이 비교
   - ```String```: 두 피연산자가 동일한 문자순서가 동일한 문자열일 경우, ```true```를 반환한다.
   - ```Number```: 두 피연산자가 동일한 값을 가질 경우, ```true```을 반환합니다. +0 과 -0 은 동일한 값으로 취급합니다. 어느 한쪽이 ```NaN일``` 경우, ```false```를 반환한다.
   - ```Boolean```: 두 피연산자가 모두 ```true```이거나, 모두 ```false```일 경우, ```true```를 반환한다.
  - [다양한 예시를 확인하고싶다면 링크 클릭!](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/Equality)
   

#### ```===```(일치 연산자)
```
x === y
```
- 일치 연산자(```===```)는 피연산자들의 갑과 타입을 모두 비교한다. 

#### ```==```, ```===``` 차이
- 일치 연산자(```===```)는 타입변환을 시도하지 않는다는것. 
- 동등 연산자(```==```)는 ```0```과 ```false```를 구별하지 못하지만 일치 연산자(```===```)는 데이터 타입의 변환 없이 값을 비교할 수 있다. 
- 일치 연산자(```===```)는 데이터타입의 동등여부까지 검사하기 때문에, 피연산자의 데이터타입이 다를 경우 ```false```를반환한다. 




## undefined와 null의  차이
 #### Undefined
 - ```undefined```는 원시값으로, 선언한 후 값을 할당하지 않은 변수 혹은 값이 주어지지 않은 인수에 자동으로 할당된다.
 ```JavaScript
 var x; // 값을 할당하지 않고 변수 선언

console.log("x's value is", x) // "x's value is undefined" 출력
```

 #### Null
- 컴퓨터 과학에서 ```null``` 값은 일반적으로 존재하지 않거나 유효하지 않은 object 또는 주소를 의도적으로 가리키는 참조를 나타낸다.
- null 참조의 의미는 언어의 구현에 따라 다양하다.
```JavaScript
 typeof null === 'object' // true
```


### 참고
- [JavaScript의 타입](https://developer.mozilla.org/ko/docs/Web/JavaScript/Data_structures)
- [동적타입](https://devuna.tistory.com/82)
- [JavaScript 형변환](https://silvesteryan.tistory.com/9)
- [동등연산자 ==](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/Equality)
- [일치연산자 ===](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Strict_equality)
