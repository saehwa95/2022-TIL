# props

### props?
- properties 의 줄임말
- 어떠한 값을 컴포넌트에게 전달해줘야 할 때, props 를 사용
- 전달된 후에는 변수를 통하여 접근 가능
- props는 오직 부모 컴포넌트에서 자식 컴포넌트로 전달
- props는 오로지 읽기 전용

<hr>

## 예시
### props 사용 전
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

### props 사용 후
```JavaScript
function Header(props){
  return <header>
    <h1><a href="/">{props.title}</a></h1>
  </header>
}

function nav(props){
  const lis = []
    for(let i=0; i<props.topics.length; i++){
    let t= peops.topics[i];
    lis.push(<li key={t.id}><a href={'/read/'+t.id}>{t.title}</a></li>)
    }
  return <nav>
    <ol>
      {lis}
    </ol>
  </nav>
}

function App() {
  const topics = [
  {id:1, title:'html', body:'html is ...'}
  {id:2, title:'css', body:'css is ...'}
  {id:3, 'title':'javascript', body:'javascript is ...'}
  ]
  return (
    <div>
      <Header title="WEB"></Header>
       <Nav topics={topics}></Nav>
    </div>
)}
```

