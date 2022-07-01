# 프로그래밍 핵심 개념 in JavaScript

## 자료형
### 숫자형
- 더하기```+```
- 빼기```-```
- 곱하기```*```
- 나누기```/```
- 나머지```%```
- 사칙 연산 규칙을 따른다.
  
### 문자열
- "", ''를 사용하여 생성
- 같은 따옴표 사용
- 한 문자열 안에 따옴표를 두 번 사용하는 경우 백틱으로 감싸주자
```JavaScript
`He said "I'm Iron man"`
 ```
  
### 불 대수
- 불 대수를 사용하기 위해서 명제를 확실히 알고, 그 명제가 참인지 거짓인지 알아야 한다. 
#### AND 연산
- x와 y가 모두 참일때만 xANDy가 참이다.
 
#### OR 연산
- x와 y중 하나라도 참이면 xORy는 참이다.

#### NOT 연산
- 반대로 뒤집어주는 역할
- 참이면 거짓으로 만들어주고, 거짓이면 참으로 만들어준다.
- NOT 대한민국의 수도는 서울이다. = 대한민국의수도는 서울이 아니다. --> 대한민국의 수도는 서울이 맞기 때문에 이 문장은 False
  

### 불린형
- True & False
- 등호를 부등호 뒤에 작성해야한다. 
- ```&& = AND 연산자```
- ```|| = OR연산자```
- ```! = NOT연산자```


### typeof 연산자
- 내가 사용하는 값이 어떤 자료형인지 확인할 수 있는 방법
```JavaScript
console.log(typeof 'Hello' + 'codeit');
console.log(typeof 8 - 3);
=> console 결과
stringCodeit
NaN(Not a Number)

console.log(typeof ('Hello' + 'codeit'));
console.log(typeof (8 - 3));
=> console 결과
string
string
```
  
### 형 변환

### 템플릿 문자열
- 특별한 형식을 가진 문자열
```
let year = 2018;
let month = 3;
let day = 11;

console.log('생년월일은' + year + '년 ' + month + '월 ' + day + '일 입니다.')
console.log(`생년월일은 ${year}년 ${month}월 ${day}일 입니다.`)
``` 
### null과 undefined
#### null 
- 의도적으로 표현할 때 사용하는 값
- 의도적인 없음

#### undefined
- 값이 없다는 것을 확인하는 값
- 처음부터 없음


## 추상화

### 할당 연산자
```JavaScript
let name = '코드잇'
let x = 5

x = x - 2
```
- x의 값을 2만큼 줄여주는 코드
- 등호는 '서로 같다' 라는 의미가 아니라 '오른쪽에 있는 피연산자를 왼쪽에 있는 피연산자에 할당한다.'로 의미한다.

### 복합 할당 연산자
- 할당 연산자와 결합해서 자주 쓰이는 표현을 더 간략하게 쓸 수 있게 해주는 연산자
```JavaScript
// 다음 두 줄은 같습니다
x = x + 1;
x += 1;

// 다음 두 줄은 같습니다
x = x + 2;
x += 2;

// 다음 두 줄은 같습니다
x = x * 2;
x *= 2;

// 다음 두 줄은 같습니다
x = x - 3;
x -= 3;

// 다음 두 줄은 같습니다
x = x / 2;
x /= 2;

// 다음 두 줄은 같습니다
x = x % 7;
x %= 7;
```

### 증가, 감소 연산자
- 변수의 값을 1씩 증가시키거나 감소시킬 때는 복합 할당 연산자보다 더 간략하게 사용 가능
- 더하기 기호를 연달아 사용 ```++``` or 빼기 기호를 연달아 사용 ```--```

```JavaScript
// 다음 세 줄은 같은 의미입니다.
x = x + 1;
x += 1;
x++;

// 다음 세 줄은 같은 의미입니다.
x = x - 1;
x -= 1;
x--;
```

### 함수 실행순서
- 위에서 아래로, 왼쪽에서 오른쪽 순서로 실행

### return문 이해하기
```JavaScript
function square(x) {
console.log('return 전');
  return x * x;
  console.log('return 후');//Dead Code
}

console.log('함수 호출 전');
console.log(square(3));
console.log('함수 호출 후');

** 실행 결과
- 함수 호출 전
- return 전
- 9
- 함수 호출 후
```

### 상수(constant)
- 변하지 않는 일정한 값
- 이름을 지을때 대문자와 밑줄로 작성해주는 암묵적인 규칙 존재
- ex) const pi = 3.14  // const PI = 3.14


## 제어문

### if문(if statement)
- 어떤 특별한 조건에 따라 코드를 실행할지 말지 결정하는 문법
- 즉, 조건을 충족하지 못하면 코드를 실행하지 않음
```JavaScript
if (조건부분) {
  동작부분
}
```

```JavaScript
let temperature = 0;

if (temperature <= 0) {
  console.log('물이 업니다.')
} else {
  console.log('물이 얼지 않습니다.')
}
```

### else if문(if statement)
- 여러가지 조건이 있는 코드를 작성할때는 else if문 활용 가능
```JavaScript
let temperature = 0;

if (temperature <= 0) {
  console.log('물이 업니다.')
} else {
  if (temperature < 100) {
  console.log('물이 얼지도 끓지도 않습니다.')
  } else {
  console.log('물이 끓습니다.')
  }
} 
```
이 내용을 else if문으로 사용하면 
```JavaScript
let temperature = 0;

if (temperature <= 0) {
  console.log('물이 업니다.')
} else if (temperature < 100) {
  console.log('물이 얼지도 끓지도 않습니다.')
} else {
  console.log('물이 끓습니다.')
} 
```

### switch
- 어떤 값을 입력했는지에 따라 다르게 동작하는 문법
```JavaScript
switch (비교할_값) {
  case 조건값_1 : 
    동작부분;
    break;
  case 조건값_2 : 
    동작부분;
    break;
  default :
    동작부분;
}
```
- '비교할_값' 과 '조건값_1'이 일치할때 동작할 코드를 '동작부분'에 작성하고 'break'를 사용해서 switch문을 빠져나오는 방식
- default : 비교할 값이 모든 조건과 일치하지 않을 경우에 동작하는 코드
- switch문은 조건값과 일치하는 경우를 찾은 다음 break문을 만나기 전까지 그 아래 모든 동작을 실행

### for문
```JavaScript
for (초기화부분; 조건부분; 추가동작부분) {
  동작부분
}
```
- 조건 부분이 충족되면 계속해서 동작부분을 반복
- 초기화부분 : for반복문이 시작할때 가장 먼저 딱 한 번만 실행되는 부분
- 조건부분 : 조건부분에 작성한 코드를 boolean 형태로 평가한 다음 true로 판단되면 동작부분 실행
- 추가동작부분 : 조건부분이 true로 판단됐을때 동작부분을 실행하고 그 다음 추가적으로 동작할 부분을 작성하는 것

```JavaScript
for (let i = 1; i <=10; i++) {
  console.log('코드잇 최고')
}
```

### while문
```JavaScript
while (조건부분) {
  동작부분
}
```

```JavaScript
let i = 1;
while (i <= 10) {
  console.log(`${i} 코드잇 최고`);
  i++;
}
```
