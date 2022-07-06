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
- 컴포넌트에 전달된 속성을 모두 가르키고, 각각의 속성은 Prop이라고 부름

### children

### State

### 참조형 State

## React 배포하기


