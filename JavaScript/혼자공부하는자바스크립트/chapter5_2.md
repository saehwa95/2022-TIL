# chapter 5 함수
## ✔️ 5_2 함수 고급
### ✅ 콜백함수
- 자바스크립트 안에서는 함수도 하나의 자료형이라서 매개변수로 전달할 수 있다. 
- 이렇듯 매개변수로 전달하는 함수를 ```콜백 함수```라고 한다. 
  ```javaScript
    // 기본 구조
      function (value, index, array) { }
  ```
#### 🔸 콜백함수를 활용하는 함수 : ```forEach()```
- ```forEach``` 메소드는 배열이 가지고 있는 함수
- 단순히 배열 내부의 요소를 사용해 콜백 함수를 호출
```javaScript
  // 예시
    const arr =  [273, 52, 103, 32, 57]
    arr.forEach(function (value, index) {
      console.log(`${index}번째의 값은 ${value}`)
    })
  
  // 출력
  0번째의 값은 273
  1번째의 값은 52
  2번째의 값은 103
  3번째의 값은 32
  4번째의 값은 57
```

#### 🔸 콜백함수를 활용하는 함수 : ```map()```
- 콜백 함수에서 리턴한 값들을 기반으로 새로운 배열을 만드는 함수
```javaScript
  // 예시 1
    arr2 = [273, 52, 103, 32, 57]
    arr2 = arr2.map(function (value, index) {
      return value + "!!"
    })
    console.log(arr2)
      
  // 출력
  [ '273!!', '52!!', '103!!', '32!!', '57!!' ]
  
  // 예시 2
  let arr2 = [273, 52, 103, 32, 57]
  arr2 = arr2.map(function (value, index) {
    return value % 2 === 0
  })
  console.log(arr2)
  
  // 출력
  [ false, true, false, true, false ]
```

#### 🔸 콜백함수를 활용하는 함수 : ```filter()```
- 콜백 함수에서 리텅하는 값이 true인 것들만 모아서 새로운 배열을 만드는 함수
- 이때 새로운 배열은 원래 배열을 변경한 것 NO!! 
```javaScript
  // 예시
    let arr3 = [273, 52, 103, 32, 57]
    arr3 = arr3.filter(function (value, index) {
      return value % 2 === 1
    })
    console.log(arr3)
          
  // 출력
  [ 273, 103, 57 ]
```

### ✅ 화살표 함수
```javaScript
  // 예시
  // (매개변수) => {본문}
  arr3 = [273, 52, 103, 32, 57]
  arr3 = arr3.filter((value, index) => value % 2 === 0)
  console.log(arr3)
  
  // 출력
  [ 52, 32 ]
```

### ✅ 타이머 함수
- 시간 관련 처리가 가능한 함수
- 1000 = 1초
- 타이머 생성 함수
  - ```setTimeout()``` : 특정한 시간 후에 한 번
  - ```setInterval()``` : 특정한 시간 마다
- 타이머 제거 함수
  - ```clearTimeout()```
  - ```clearInterval()```

### ✅ 예제 풀이 
- 1번 문제
```javaScript
  // 변수 선언
  let numbers = [273, 25, 75, 52, 103, 32, 57, 24, 76]

  // 비파괴적 함수이기 때문에 결과로 나온 return 값을 활용해야 함 그래서 재할당으로 numbers = 로 시작

  // 홀수만 추출
  numbers = numbers.filter((value, index) => value % 2 === 1)
  console.log(numbers)

  // 100이하의 수만 추출
  numbers = numbers.filter((value, index) => value <= 100)
  console.log(numbers)

  //5로 나눈 나머지가 0인 수
  numbers = numbers.filter((value, index) => value % 5 === 0)
  console.log(numbers)

  // 출력
  [ 273, 25, 75, 103, 57 ]
  [ 25, 75, 57 ]
  [ 25, 75 ]

  // 꼭 기억해야 할 것  
  // 나는 100 이하의 수만 추출된다면 [25, 75, 52, 32, 57, 24, 76]가 출력될 것이라고 생각했다. 
  // 하지만 filter() 메서드에서 활용되는 배열은 비파괴적 함수이기 때문에 결과로 나온 return 값을 활용한다. 
  // 그래서 새로운 문제 코드 작성 시 numbers.filter로 시작하는게 아니라!! numbers = numbers.filter로 시작하는 것이다. 
  // return된 numbers 값. 그 numbers로 다시 다음 문제 시작
```
- 2번 문제
```javaScript
  const arr = ['사과', '배', '귤', '바나나']

  console.log('# for in 반복문')
  for (const i in arr) {
    console.log(i)
  }

  // 익명함수 구현
  arr.forEach(function (value, index) {
    console.log(index)
  })

  console.log('# for of 반복문')
  for (const i of arr) {
    console.log(i)
  }

  // 익명함수 구현
  arr.forEach((value, index) => {
    console.log(value)
  })
  
  // 출력
  # for in 반복문
  0
  1
  2
  3
  # for of 반복문
  사과
  배
  귤
  바나나
```

## ✔️ 오늘 기록하고 싶은 내용
### 🌼 1. 기술매니저님께 질문하여 해소한 내용
- for in, for of 내가 추출하고 싶은 값이 value 인지 index 인지에 따라 활용이 가능한 것인가?? 아니면 for in은 index, for of는 value로만 활용할 수 있는가? <br>
➡️ for in은 index, for of는 value로만 활용할 수 있다.
- 선언적 함수와 익명 함수 중 더 많이 사용하는 함수가 존재하는가? <br>
➡️ 어떤 함수를 더 많이 사용한다기 보다 프로젝트마다 기존에 사용하는 함수에 맞추거나, convention을 정해서 사용하는 편이다. 
### 🌱 2. 도와준 내용
- ```setTimeout()```, ```setInterval()``` 사용시 콘솔창에 1,2,3,4 등의 숫자가 같이 출력된다. 이 숫자는 무엇일까??
- 내가 알아본 방법 ❗ <br>
➡️ mdn 공식 문서에 ```setTimeout()``` 메서드를 검색했고, ```setTimeout()``` 메서드를 사용하면 timeoutID를 반환한다는걸 알았다. <br>
➡️ 반환하는 ```timeoutID```는 양의 정수로서 ```setTimeout()```이 생성한 타이머를 식별할 때 사용하고, 이 값을 ```clearTimeout()```에 전달하면 타이머를 취소할 수 있다는 내용을 알았다. <br>
➡️ 구글 검색창에 ```자바스크립트 setTimeout() 아이디```라고 검색해서 여러 자료를 확인했고, 같은반 수강생처럼 콘솔창을 활용한 블로그를 발견했다. <br>
➡️ 위의 내용을 같은 조원들에게 공유하고, 내가 검색한 순서, 도움받은 블로그 링크를 공유했다. <br>
➡️ 기술매니저님도 함께 찾아보셨고, 그 결과 내가 찾은 고유아이디 값이 맞다고 이야기해주셨다. <br>
