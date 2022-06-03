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

## 제어문


