# 프로그래밍 시작하기 in JavaScript

## 프로그래밍 맛보기
### 자료형 개요
- 자바스크립트의 자료형
  - Number(숫자) : 정수, 소수
  - String(문자열)
  - Boolean(불린)

### 추상화 개요
- 프로그래밍의 추상화
- 복잡한 것들을 목적에 맞게 단순화 하는것
  - 목적을 명확히
  - 불필요한 것들은 숨기기
  - 핵심만 드러내기

### 변수
- 프로그래밍에서는 값의 이름을 부여하기 위해 변수라는 것을 활용
- 프로그래밍에서 값을 저장하는 가장 기본적이고 중요한 요소
 
- 변수 선언
```JavaScript
let espressoPrice;
espressoPrice = 3000;

let espressoPrice = 3000;

console.log(espressoPrice)

위 두줄과 아래 한줄의 의미는 동일
```
- 위 코드에서 볼 수 있는 등호```=```는 프로그래밍에서 할당연산자로 불리며 '오른쪽에 있는 값을 왼쪽에 할당한다.'라는 의미

### 꼭 지켜야하는 룰(지키지 않으면 오류 발생)
- JavaScript 식별자는 '문자(a-z, A-Z)', '언더바_' 혹은 '달러 기호($)'로 시작, 두 번째 글자부터는 '숫자'도 가능
-  '대문자'와 '소문자'는 구별합니다. ```myname```과 ```myName```은 다른 이름
-  '예약어(JavaScript가 찜해놓은 단어)'는 사용하면 X!! 예) ```if```, ```for```, ```let```

### 지키면 좋은 룰(더 좋은 스타일을 위해)
- 의미 없는 이름은 좋지 않다.
- 너무 추상적인 이름은 좋지 않다. 
- 모든 변수 이름은 'camelCase'로 쓰는 것이 좋다.

### 함수
```JavaScript
// 함수 선언
function greetings() {
  console.log('Hi');
  console.log('안녕');
  console.log('こんにちは');
  console.log('你好');
  console.log('Guten Tag');
  console.log('Bonjour');
  console.log('Buongiorno');
}

//함수 호출
greetings();
```

### 파라미터
```JavaScript
// 함수 선언
function greetings(sentence) {
  console.log('Hi');
  console.log('안녕');
  console.log('こんにちは');
  console.log('你好');
  console.log('Guten Tag');
  console.log('Bonjour');
  console.log('Buongiorno');
  console.log(sentence);
}

//함수 호출
greetings('Hola');
```
- ```Hola```라는 문자열이 함수 선언 부분에서 ```sentence```라는 파라미터로 전달되고 함수 내부에서는 ```sentence```라는가 ```Hola```라는 변수처럼 활용

```JavaScript
function welcome(name) {
console.log('안녕하세요 ' + name + '님!');
};
welcome('코드잇');

출력 : 안녕하세요 코드잇님!
```
#### 실습해보기
```JavaScript
function teraToGiga(volume) {
  console.log(volume + 'TB는');
  console.log(volume * 1024 + 'GB 입니다.');
}

function teraToMega(volume) {
  console.log(volume + 'TB는');
  console.log(volume * 1024 * 1024 + 'MB 입니다.');
}

출력 예시 
2TB는
2048GB 입니다.
2TB는
2097152MB 입니다.
```

### 여러개의 파라미터
#### 실습해보기
```JavaScript
function bmiCalculator(name, weight, tall) {
console.log(name + '님의 체질량지수는 ' + weight / (tall * tall / 10000) + '입니다.');
}
bmiCalculator('홀쭉이', 43.52, 160);
bmiCalculator('코린이', 61.25, 175);
bmiCalculator('통통이', 77.76, 180);

출력 예시 
홀쭉이님의 체질량지수는 17입니다.
코린이님의 체질량지수는 20입니다.
통통이님의 체질량지수는 24입니다.
```

### return문
- '반환한다'는 뜻
- 함수가 실행된 자리에 어떤 값을 돌려줄 수 있다.
