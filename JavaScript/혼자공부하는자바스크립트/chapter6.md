# chapter 6 객체
## ✔️ 6_1 객체의 기본
```javaScript
const arr = [100, 20, '문자열', true, function () {} , () => {}]
const object = {
  키 : 값,
  키 : 값,
  키 : 값,
  키 : 값,
}
```
- 배열에는 여러 자료를 한꺼번에 다를 수 있다.
- 객체도 여러 자료를 한꺼번에 다룰 수 있다. 
- 배열도 객체다.
  - ```typeof([]) = object```
### ✅ 객체
- 객체는 키```key```와 값```value```으로 이루어져 있고, ```key```에는 식별자를 사용한다. 
  - 식별자 조건
  - 숫자로 시작하지 않는다.
  - 기호는 ```$```와 ```_```만 포함한다.
```javaScript
const object = {
  이름 : '니모',
  견종 : '푸들',
  나이 : 10,
  좋아하는것 : '간식',
  싫어하는것 : '뽀뽀'
}
```
- 접근방법
  - ```object['이름']```
  - ```object.name```

### ✅ 속성과 메서드
```javaScript
const dog = {
  name : '니모',
  breed : '푸들',
  age : 10,
  like : '간식',
  hate : '뽀뽀'
  bark : function () {
    console.log(`${dog.neme}가 짖습니다.`)
  }
  sleep : () => {
    console.log(`${dog.name}가 잡니다.`)
  }
}
```
- 배열 내부에 있는 값을 ```요소```라고 말한다. 
- 객체 내부에 있는 값은 ```속성```이라고 말한다.
- 객체 내부에 있는 속성 중 함수 자료형을 ```메서드```라고 말한다.
- 메서드 사용하기
  - ```dog.bark()```
  - ```dog.sleep()```

### ✅ this
- 위에서 볼 수 있는 익명 함수와 화살표 함수의 차이 발생
- 익명함수는 내부에서 ```this```를 사용했을때 자기 자신을 나타낸다. (= this 바인딩을 한다.)
  ```javaScript  
  bark : function () {
    console.log(`${dog.neme}가 짖습니다.`)
    console.log(`${this.neme}가 짖습니다.`)
  }
  // 두 콘솔의 값은 동일
  ```
- 화살표 함수에서는 ```this```객체가 따로 연결되지 않는다. (= this 바인딩을 안한다.)
- 그래서 ```this.name```을 출력하면 엉뚱한 값을 출력할것이다. => window 객체가 출력된다...

### ✅ 객체에 동적으로 속성 추가하기
- 처음 만들 때 같이 만드는 것 : 정적으로 생성한다. 
- 나중에 만드는 것 : 동적으로 생성한다. 

```javaScript
// 객체의 키와 값을 정적으로 생성한다. 
const pet = {
  name : '니모',
  age : 10
}

// 객체의 키와 값을 동적으로 생성한다.
pet.color = 'black'

console.log(pet)
// 출력
{name: '니모', age: 10, color: 'black'}
```
- 동적으로 제거 : ```delete객체.속성``` => ```delete pet.color```


## ✔️ 6_2 객체의 속성과 메소드 사용하기
### ✅ 기본 자료형과 객체 자료형
- 기본 자료형 : 숫자, 문자열, 불 => 스택에 값을 저장 => 속성과 메서드를 가질 수 없다.
- 객체 자료형 : 함수, 배열, 객체, 등등 => 스택과 힙을 연결 => 속성과 메서드를 가질 수 있다.
- 배열인지 확인하는 메소드 : ```Array.isArray()```

### ✅ Number 객체
- ```toFixed()```
  - 소수점 이하 몇 자리까지만 출력
- ```isNaN(), isFinite()```
  - Not a Number 확인, 무한한지 확인
  - Number 뒤에 점을 찍고 사용

### ✅ String 객체
- ```trim()```
  - 문자열 양쪽 끝의 공백 없애기
- ```split()```
  - 문자열을 매개변수(다른 문자열)로 잘라서 배열을 만들어 리턴

### ✅ Math 객체
- ```Math.random()```
  - 랜덤한 숫자를 생성
- ```Math.floor()```
  - 내림
  - ```Math.floor(10.1)``` => 10
- ```Math.ceil()```
  - 올림
  - ```Math.ceil(10.1)``` => 11
- ```Math.round()```
  - 반올림
  - ```Math.ceil(10.1)``` => 10
- ```Math.max()```
  - 최대값 구하기
  - ```Math.max(52, 273, 103)``` => 273
- ```Math.min()```
  - 최소값 구하기
  - ```Math.min(52, 273, 103)``` => 52

## ✔️ 6_3 객체와 배열 고급
- 객체의 기본값을 지정하는 내용
### ✅ 객체 기본 매개변수 지정 방법
```javaScript
  const test = function (object) {
    return `${object.name} : ${object.age} : ${object.color} : ${object.status}`
  }
  console.log(test ({
    name: '니모',
    age: 7,
    color: '검정'
  }))
```
- 과거에 사용하던 방법
  - ```object.status = object.status !== undefined ? object.status : '이상 없음'```
  - ```object.status = object.status ? object.status : '이상 없음'```
  - ```object.status = object.status || '이상 없음'```
- 현대에 사용하는 방법
  - ```object = {status: '이상 없음', ...object}```
    ```javaScript
      fun = function ({name, age, color, status = '이상 없음'}) {
        return `${name} : ${age} : ${color} : ${status}`
       }
    ```
