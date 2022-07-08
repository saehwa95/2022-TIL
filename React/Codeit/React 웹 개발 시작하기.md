# React 웹 개발 시작하기 
## React 시작하기 
- 환경 세팅 
  - node.js 설치 / 최신 버전 말고 LTS버전 설치 권장
  - 설치 버전 확인 방법 : ```node -v```, ```npm -v```
  - vscode 설치
  - Chrome 브라우저 설치
- 프로젝트 생성 명령어
  - ```yarn create react-app .```  =>  새로 만든 폴더 내에 react 패키지 설치
- React에서는 자바스크립트 코드 안에 태그를 섞어서 사용 => 이런 문법을 JSX 문법이라 말함
- yarn start : 개발 모드를 실행
- ctrl + c : 개발 모드 종료
- react 개발자 도구 설치(Chrome 확장 프로그램)

## React 개발 기초
### 프로젝트 세팅
- pubilc : index.html

  ```html
  <!DOCTYPE html>
  <html lang="ko">
    <head>
      <meta charset="utf-8" />
      <title>주사위 게임</title>
    </head>
    <body>
      <div id="root"></div>
    </body>
  </html>
  ```
- src : index.js

   ```JSX
  import ReactDOM from 'react-dom/client';

  const root = ReactDOM.createRoot(document.getElementById('root'));
  root.render(
  <h1>안녕 리액트!</h1>
  );
  ```
### 인덱스 파일에서 하는 일
- index.html : 웹브라우저에서 가장 먼저 실행되는 파일
- index.js : ```index.html```파일이 열리고난 후 실행되는 파일, 리액트 코드들 중 가장 먼저 실행되는 파일

### JSX
- 자바스크립트와 html을 섞어서 사용할 수 있는 자바스크립트의 확장된 문법
- ```class``` 속성을 작성하기 위해서는 ```className```으로 작성
- 속성명은 카멜케이스로 작성
- 자바스크립트 예약어와 같은 속성명은 사용 불가(ex. for, class => htmlFor, className 으로 작성)

### 프래그먼트
- 2개의 태그를 연달아 작성할 경우 오류 발생
- JSX 요소들은 하나의 태그로 감싸줘야함
- 예시

  ```JSX
    <div>
      <h1>안녕</h1>
      <h1>리액트!</h1>
    </div>
  
    // 그런데 내가 불필요한 태그를 작성하고 싶지 않다면 Fragment 태그 활용
    <>
      <h1>안녕</h1>
      <h1>리액트!</h1>
    </>
  ```

### JSX에서 자바스크립트 사용하기
- JSX 문법에서 자바스크립트 코드를 활용하려면 ```중괄호{ }```로 감싸주기 
- 중괄호 안에는 변수를 그대로 사용할 수 있을뿐만 아니라 자바스크립트로된 표현식은 뭐든지 사용 가능

  ```JSX
    import ReactDOM from 'react-dom/client';

    const root = ReactDOM.createRoot(document.getElementById('root'));
    const product = '맥북';

    root.render(
      <h1>나만의 {product} 주문하기</h1>     //{product} 언뜻 보면 템플릿 문자열과 비슷해보이지만 앞에 $가 없음
    );
  ```

  ```JSX
    import ReactDOM from 'react-dom/client';

    const root = ReactDOM.createRoot(document.getElementById('root'));
    const product = 'MacBook';
    const model = ' Air';
    const item = product + model

    root.render(
      <h1>나만의 {item} 주문하기</h1>
    );
  ```

- 중괄호를 활용하면 요소 내부 뿐만 아니라 속성값에도 자바스크립트 코드 작성 가능

  ```JSX
    import ReactDOM from 'react-dom/client';

    const root = ReactDOM.createRoot(document.getElementById('root'));
    const product = 'MacBook';
    const model = ' Air';
    const item = product + model
    const imageUrl = 'https://image.zdnet.co.kr/2020/11/11/34110ff219b1ae4e197c153a7b15e263.jpg'

    function handleClick(){
      alert('곧 도착합니다!')
    }

    root.render(
      <>
        <h1>나만의 {item} 주문하기</h1>
        <img src={imageUrl} alt="제품 사진"></img>
        <button onClick={handleClick}>확인</button>
      </>
    );
  ```

### 컴포넌트
- 리액트 컴포넌트는 리액트 엘리먼트를 조금 더 자유롭게 다루기 위한 하나의 문법
- 컴포넌트를 만드는 가장 간단한 방법은 자바스크립트의 함수를 활용
- 아래 코드에서 JSX 문법으로 작성된 하나의 요소를 리턴하는 ```Hello``` 함수가 바로 하나의 컴포넌트
- 아래 코드에서 element 변수 안의 JSX 코드에서 볼 수 있듯 컴포넌트 함수 이름을 통해 하나의 태그처럼 활용 가능
- 리액트 컴포넌트의 이름은 반드시 첫 글자를 대문자로 작성

  ```JSX
    import ReactDOM from 'react-dom';

    function Hello() {
      return <h1>안녕 리액트</h1>;
    }

    const element = (
      <>
        <Hello />
        <Hello />
        <Hello />
      </>
    );

    ReactDOM.render(element, document.getElementById('root'));
  ```
  
### Props
- 컴포넌트에 지정한 속성
- Props는 Properties의 줄임말
- 각 속성이 하나의 객체로 모여서 컴포넌트를 정의한 함수의 첫 번째 파라미터로 전달
- 컴포넌트에 전달된 속성을 모두 가르키고, 각각의 속성은 Prop이라고 부름

### children
- props에 있는 특별한 프로퍼티
- JSX 문법으로 컴포넌트를 작성할 때 컴포넌트를 단일 태그가 아니라 여는 태그와 닫는 태그의 형태로 작성하면, 그 안에 작성된 코드가 바로 이 children 값에 담겨짐
- 컴포넌트 함수에서 따로 가공하지 않고, 단순히 보여주기만 하는 모습은 children prop 사용 
- 코드를 좀 더 직관적으로 구성하는데 도움

### State
- 리액트에서 화면을 그려내는 중요한 역할
- State라는 단어는 '상태'라는 뜻 => 상태가 바뀔 때마다 화면을 새롭게 그려내는 방식으로 동작을 하는 것
- 리액트에서 state를 만들고, state를 바꾸기 위해서는 일단 ```useState```라는 함수를 활용해야 함
- ```useState``` 함수는 초깃값을 아규먼트로 받고 그에 따른 실행 결과로 요소 2개를 가진 배열의 형태로 리턴
- 이때 첫 번째 요소가 state, 두 번째 요소가 이 state를 바꾸는 setter 함수
- 첫 번째 변수는 원하는 state의 이름을 지어주고, 두 번째 변수에는 state 이름 앞에 set을 붙인 다음 카멜 케이스로 이름을 지어주는 것이 일반적
- state는 변수에 새로운 값을 할당하는 방식으로 변경하는 것이 아니라 이 setter 함수를 활용해야 함
- setter 함수는 호출할 때 전달하는 아규먼트 값으로 state 값을 변경해 줌

### 참조형 State
- 자바스크립트의 자료형은 크게 기본형(Primitive type)과 참조형(Reference type)로 나누어짐
  ```JSX
    const [gameHistory, setGameHistory] = useState([]);

    const handleRollClick = () => {
      const nextNum = random(6);
      gameHistory.push(nextNum);
      setGameHistory(gameHistory); // state가 제대로 변경되지 않는다!
    };
  ```
- 위 코드에서 볼 수 있듯 배열 값을 가진 ```gameHistory```에 ```push``` 메소드를 이용해서 배열의 값을 변경한 다음, 변경된 배열을 setter 함수로 state를 변경하려고 하면 코드가 제대로 동작하지 않음
- ```gameHistory state```는 배열 값 자체를 가지고 있는 게 아니라 그 배열의 주솟값을 참조하고 있음
- 그래서 ```push``` 메소드로 배열 안에 요소를 변경했다고 하더라도 결과적으로 참조하는 배열의 주솟값은 변경된 것이 아님
- 결과적으로 리액트 입장에서는 ```gameHistory``` state가 참조하는 주솟값은 여전히 똑같기 때문에 상태(state)가 바뀌었다고 판단하지 않는 것
- 참조형 state를 활용할 때는 반드시 새로운 참조형 값을 만들어 state를 변경해야 함 => Spread 문법 활용하기
  ```JSX
    const [gameHistory, setGameHistory] = useState([]);

    const handleRollClick = () => {
      const nextNum = random(6);
      setGameHistory([...gameHistory, nextNum]); // state가 제대로 변경된다!
    };
  ```
- 🌟참조형 state를 활용할 땐 반드시 새로운 참조형 값을 만들어서 state를 변경해야함🌟

### 컴포넌트가 좋은 이유
### 컴포넌트 재사용하기
### 코드 정리하기
### 리액트가 렌더링하는 방식
### 인라인 스타일
### CSS 클래스 네임


## React 배포하기



