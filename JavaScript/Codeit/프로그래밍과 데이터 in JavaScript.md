# 프로그래밍과 데이터 in JavaScript

## 1. 객체
### 1-1.객체와 프로퍼티
- "자바스크립트의 모든 것이 다 객체다!"라는 말이 있을 정도로 자바스크립트의 거의 모든 문법에 녹아있는 개념
- 자바스크립트를 잘 다루기 위해서 객체를 이해하는 것이 중요
- 객체는 중괄호 ```{}```를 통해서 만들어질 수 있고, 중괄호 안에는 여러가지 다양한 값들을 쉼표로 구분해서 저장 가능
- 객체는 다양한 값들이 들어갈 수 있기 때문에 각 값들을 좀 더 명확하게 하기 위해 콜론```,```과 함께 이 값의 이름을 붙여주어야 함
```JavaScript
{
  key : value
  brandName : "코드잇",
  bornYear : 2017,
  isVeryNice : true,
  worstCourse : null
}
```
- ```key : value``` 한 쌍을 객체의 속성 즉 Property라고 함
- ```PropertyName:PropertyValue```
- PropertyName은 문자열(String)타입을 PropertyValue는 모든 자료형 값을 사용 가능
- PropertyValue는 문자열, 숫자, boolean, null, 심지어 객체 안에 객체를 넣을 수 있음
- PropertyName의 자료형은 문자열이지만 반드시 따옴표로 감싸줘야할 필요는 없다. 다만 아래 세 가지의 경우 따옴표로 감싸주어 사용해야함
- 첫 번째 글자가 반드시 ```문자```, 밑줄```_```, 달러 기호```$``` 중 하나로 시작하지 않는 경우
- 띄어쓰기를 해야하거나 하이픈을 사용해야 하는 경우

#### PropertyName 주의 사항
- 첫 번째 글자는 반드시 ```문자```, 밑줄```_```, 달러 기호```$``` 중 하나로 시작
- 띄어쓰기 금지
- 하이픈 ```-``` 금지

### 1-2.객체에서 데이터 접근하기
```JavaScript
let codeit = {
  name : '코드잇'
  bornYear : 2017,
  isVeryNice : true,
  worstCourse : null,
  bestCourse: {
    title : '자바스크립트 프로그래밍 기초',
    language : 'JavaScript'
  }
};
```
#### 객체의 Property에 접근하는 방법은 2가지
##### 점 표기법(objectName.PropertyName)
```JavaScript
console.log(codeit.bornYear);
```
##### 대괄호 표기법(objectName['PropertyName'])
```JavaScript
console.log(codeit['bornYear']);
```
- 대괄호 표기법은 propertyName을 좀 더 유연하게 구성 가능

#### 객체 안에 객체
propertyName을 계속 연결해서 접근
```JavaScript
console.log(codeit.bestCourse.title);
```

### 1-3. 객체 다루기
- 객체 property 추가하기
 
```JavaScript
console.log(codeit.ceo);
codit.ceo = '강영훈';
console.log(codeit.ceo);
```

- 객체의 property 삭제하기(delete 연산자)
```JavaScript
console.log(codeit.worstCourse);
delete codit.worstCourse;
console.log(codeit.worstCourse);
```

#### 객체의 property 존재여부 확인 방법
##### undefind
```JavaScript
console.log(codeit.name !== undefind);
```

##### in 연산자
```JavaScript
// 'propertyName' in object
console.log('name' in codeit);
```
- propertyName은 문자열로 작성한 다음 ```in```이라는 키워드를 써주고, 그 다음 확인할 객체를 작성해주면 객체안에 'name'이라는 이름을 가진 property가 있는지 확인해서 boolean 형태로 값을 return
- 왜 ```in``` 이라는 연산자가 존재할까?
- property를 확인할때 좀 더 안전하게 하기 위함
- if문에서 조건 부분에 활용하기 좋음


### 1-4. 객체와 메소드
- 연관성 있는 여러 함수들을 하나로 묶고싶은 경우도 존재
- property 값으로 함수를 넣어주면 가능
```JavaScript
let greetings = {
  sayHello: function () {
    console.log('Hello!');
  },
  sayHi: function () {
    console.log('Hi!');
  },
  sayBye: function () {
    console.log('Bye!');
  }
};
```
- 점표기법 호출 시 
```JavaScript
greetings.sayHello();
```
- 파라미터가 필요한 경우
```JavaScript
let greetings = {
  sayHello: function (name) {
    console.log(`Hello! ${name}!`);
  }
};

greetings.sayHello('codeit');
```

### 1-5. for ...in 반복문
- 객체의 property를 가져오는 반복문이기 때문에 일반적인 for문으로는 대체할 수 없는 특별한 반복문
- 기본구조
```JavaScript
  for (변수 in 객체) {
  동작 부분
  }
```
- 예제
```JavaScript
let codeit = {
  name : '코드잇',
  bornYear : 2017,
  isVeryNice : true,
  worstCourse : null,
  bestCourse: '자바스크립트 프로그래밍 기초'
}
  
for (let key in codeit) {
  console.log(key);
}

// let key : key라는 변수 , in codeit : codeit 객체의 property 개수만큼 반복
// 위 console 안에는 codeit 객체의 propertyName이 출력
```

### 1-6. Date 객체
#### 내장 객체
- 자바스크립트가 미리 가지고 있는 객체
- month는 0부터 시작 -> 1월은 0번째
- date는 일자
- day는 요일 : 일요일부터 0 ~ 6 까지

## 2. 배열
### 2-1. 배열

### 2-2. 배열 다루기

### 2-3. 배열 메소드 1

### 2-4. 배열 메소드 2

### 2-5. for ...of 반복문

### 2-6. 다차원 배열

## 3. 자료형 심화
### 3-1. 다양한 숫자 표기법

### 3-2. 숫자형 메소드

### 3-3. 바보 자바스크립트?

### 3-4. 문자열 심화

### 3-5. 기본형과 참조형

### 3-6. 참조형 복사하기

### 3-7. const, 변수와 상수 사이



