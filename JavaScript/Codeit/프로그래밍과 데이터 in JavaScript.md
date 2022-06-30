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
```JavaScript
let courseRanking = [
  '자바스크립트 프로그래밍 기초',
  'Git으로 배우는 버전 관리',
  '컴퓨터 개론',
  '파이썬 프로그래밍 기초'
];
```
- 배열 안에 있는 값들은 ```요소``` 즉, ```element```라고 부름
- 대괄호 안에 각 요소별로 순서를 알려주는 숫자가 매겨짐
- 이 숫자 값을 ```index```라고 부르고 이 ```index```가 객체랑 비교했을때 ```PropertyName```의 역할
- ```index```를 통해서 배열의 요소를 가져올 수 있음
- 배열의 요소를 가져오는 방법은 객체의 대괄호 표기법과 동일

```JavaScript
//indexing(0부터 시작)
console.log(배열이름[index]);

//배열의 첫번째 요소에 접근하려면
console.log(courseRanking[0]);        // 출력 : 자바스크립트 프로그래밍 기초
```
- 순서가 있는 값을 만들때는 객체보다 배열을 활용하는게 좀 더 간결
- 순서가 있는 여러 값들의 묶음은 객체보다 배열 활용

### 2-2. 배열 다루기
```JavaScript
//배열
let members = ['쿤갈레', 'Zerrard66', '우리생각해써', '흙토끼', 'End Miracle'];

console.log(members.length);                // 출력값 : 5
console.log(members['length']);             // 출력값 : 5
console.log(members[members.length - 1]);   // 출력값 : End Miracle
```

### 2-3. 배열 메소드 1
```JavaScript
//배열의 메소드
let members = ['쿤갈레', 'Zerrard66', '우리생각해써', '흙토끼', 'End Miracle'];

//배열의 메소드 삭제 splice
members.splice(4);
console.log(members);             // 출력값 : (4) ['쿤갈레', 'Zerrard66', '우리생각해써', '흙토끼']

members.splice(1,1);
console.log(members);             // 출력값 : (4) ['쿤갈레', '우리생각해써', '흙토끼', 'End Miracle']
``` 
- 삭제를 시작할 인덱스를 첫번째 파라미터로 넣어주고, 삭제할 갯수를 입력 : ```splice(startIndex, deleteCount)```
- 삭제할 갯수를 전달하지 않으면 시작한 인덱스 이후의 모든 요소들 삭제
- splice 메소드로 요소를 삭제한 다음 새로운 요소를 더 추가할 수 있음 : ```splice(startIndex, deleteCount, item)```
- splice 메소드에 세번째 파라미터는 값을 전달하게 되면 삭제한 요소 자리에 그 값이 추가됨

```JavaScript
//배열의 메소드
let members = ['쿤갈레', 'Zerrard66', '우리생각해써', '흙토끼', 'End Miracle'];

//splice(startIndex, deleteCount, item)
members.splice(1, 1, 'NiceCodeit', 'HiCodeit');
console.log(members);        // 출력값 : (6) ['쿤갈레', 'NiceCodeit', 'HiCodeit', '우리생각해써', '흙토끼', 'End Miracle']
``` 


### 2-4. 배열 메소드 2
```JavaScript
//배열의 메소드 (Array's Method)
let members = ['쿤갈레', 'Zerrard66', '우리생각해써', '흙토끼', 'End Miracle'];

// 배열의 첫 요소를 삭제 : shift()
members.splice(0, 1);
members.shift();

// 배열의 마지막 요소를 삭제 : pop()
members.splice(members.length -1, 1);
members.pop();

// 배열의 첫 요소로 값 추가 : unshift(value)
members.splice(0, 0, 'NiceCodeit');
members.unshift('NiceCodeit');

// 배열의 마지막 요소로 값 추가 : push(value)
members.splice(members.length, 0, 'HiCodeit');
members.push('HiCodeit');
```

### 2-5. for ...of 반복문
```JavaScript
  for (변수 of 배열) {
    동작부분;
  }
```

```JavaScript
let influencer = ['suwonlog', 'small.tiger', 'Minam.ludens', 'cu_convenience24']

for (let i = 0; i < influencer.length; i++) {
  console.log(influencer[i]);
}

//위 내용을 for...of 사용 
for (let element of influencer) {
  console.log(element);
}
```

### 2-6. 다차원 배열
```JavaScript
// 다차원 배열
let twoDimensional = [[1, 2], [3, 4]]

console.log(twoDimensional[0])       //출력값 : [1, 2]
console.log(twoDimensional[0][1])    //출력값 : 2
```

## 3. 자료형 심화
### 3-1. 다양한 숫자 표기법
```JavaScript
// 숫자 표기법
let millionaire = 1000000000;
let myNumber = 1e9; // 지수 표기법 : 알파벳 왼편에 있는 수에 오른쪽에 있는 수만큼 10의 거듭제곱을 곱하는 의미

// 16진법 (Hexadecimal)
let hex1 = 0xff; // 255
let hex2 = 0xFF; // 255

// 8진법 (Octal)
let octal - 0o377; // 255

// 2진법 (binary numeral system)
let binary = 0b11111111; // 255
```

### 3-2. 숫자형 메소드
- toFixed(0 ~ 100)
```JavaScript
//Number
let myNumber = 0.3591;

// toFixed(0 ~ 100)
console.log(myNumber.toFixed(7))

// 타입을 확인했을때 string이 출력
// 만약 숫자로 사용하고 싶은 경우 Number 함수 활용하기
// Number(myNumber.toFixed(7))
// Number 말고 +를 붙여줘도 숫자로 출력
```

- toString(2 ~ 36)
```JavaScript
//Number
let myNumber = 255;

//  toString(2 ~ 36)
console.log(myNumber.toString(2));    //출력 : 11111111
console.log(myNumber.toString(8));    //출력 : 377
console.log(myNumber.toString(16));   //출력 : ff

// 주의사항
// 숫자를 바로 사용할 경우 정수 형태의 숫자값은 메소드로 사용할때 점 두개 사용
console.log(255..toString(2));
```

### 3-3. 바보 자바스크립트?
- 사람과 컴퓨터는 숫자를 다루는 방식이 다름
- 모든 코드는 0과 1로만 이루어져있음

### 3-4. 문자열 심화
- 문자열은 배열과 비슷한 부분이 많음
```JavaScript
// String
let myString = 'Hi Codeit'

// 부분 문자열 접근 slice(start, end)
console.log(myString.slice(0, 2));            // 0번 index부터 1번 index까지 리턴
console.log(myString.slice(3));               // 시작 지점부터 끝까지 리턴
console.log(myString.slice());                // 문자열 전체 리턴

// 대소문자 변환
console.log(myString.toUpperCase());          // 대문자
console.log(myString.toLowerCase());          // 소문자

// 요소 탐색
console.log(myString.indexOf('i'));           // 앞 부터
console.log(myString.lastIndexOf('i'));       // 뒤 부터

// 요소 접근
console.log(myString[3]);                     // 대괄호 표기법
console.log(myString.charAt(3));              // charAt 메소드

// 문자열 길이
console.log(myString.length);                 // length 프로퍼티
```

### 3-5. 기본형과 참조형
- 기본형 : String, number, undefined, null, boolean
- 참조형 : object
     
- 자바스크립트에서 변수에 객체값을 할당한 경우 객체값이 어딘가에서 만들어지고, 변수에는 그 객체값으로 가는 주소가 저장
- 변수 상자와 객체값 사이에 길이 열리는것
   
- 기본형 값을 변수에 담아 사용할 때는 값이 그대로 할당
- 참조형 값을 변수에 담아 사용할 때는 해당 객체를 가리키는 주솟값이 할당
- 참조형의 경우 변수를 통해 다른 변수에 할당하면 값 자체가 복사되는 것이 아니라 주솟값이 복사되기 때문에 결국 같은 객체를 가리킴
- 결과적으로 한쪽을 수정하면 다른 한쪽도 같이 수정됨

### 3-6. 참조형 복사하기


### 3-7. const, 변수와 상수 사이




