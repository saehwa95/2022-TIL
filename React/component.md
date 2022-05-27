# component :memo:

### component?
- 리액트로 만들어진 앱을 이루는 최소한의 단위
- 컴포넌트 이름은 항상 대문자로 시작
- UI를 재사용 가능한 개별적인 여러 조각으로 나누고, 각 조각을 개별적으로 나누어 코딩
- 리액트에서 정의하는 컴포넌트 종류 : 함수형 컴포넌트, 클래스형 컴포넌트 
- React 공식적으로 컴포넌트 사용 시 함수형 컴포넌트는 권장, 클래스형 컴포넌트는 비권장

## 함수형 컴포넌트 
```JavaScript
function Mycomponent(props) {
return <div>Hello, {props.name}</div>
}
```
  
## 클래스형 컴포넌트 
```JavaScript
class Mycomponent extends React.Component {
  constructor(props) { //생성함수
          super(props);
}

componentDidMount() { //상속받은 생명주기 함수
}

render() { //상속받은 화면 출력 함수, 클래스형 컴포넌트는 render() 필수
        return <div>Hello, {this.props.name}</div>
}
}
```
  
<hr>

## 함수형 예시
### component 만들기 전
```JavaScript
function App() {
  return (
    <div>
      <header>
        <h1><a href="/">WEB</a></h1>
      </header>
    <nav>
      <ol>
        <li><a href="/read/1">html</a></li>
        <li><a href="/read/2">css</a></li>
        <li><a href="/read/3">js</a></li>
      </ol>
    </nav>
    </div>
)}
```

### component 사용 후
```JavaScript
function Header(){
  return <header>
    <h1><a href="/">WEB</a></h1>
  </header>
}

function nav(){
  return <nav>
    <ol>
        <li><a href="/read/1">html</a></li>
        <li><a href="/read/2">css</a></li>
        <li><a href="/read/3">js</a></li>
      </ol>
  </nav>
}

function App() {
  return (
    <div>
      <Header></Header>
       <Nav></Nav>
    </div>
)}
```

