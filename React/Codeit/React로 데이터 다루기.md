# React로 데이터 다루기
## 배열 렌더링하기
- 각 데이터를 구분하는 값 ```id```
- 이름을 값으로 하는 ```name``` 프로퍼티
- 속성인 ```types``` 프로퍼티


### ```map```으로 렌더링하기
- 배열 메소드 ```map```에서 콜백 함수의 리턴 값으로 리액트 엘리먼트를 리턴 
- JSX 중괄호 안에서 map 함수 사용
  ```JavaScript
  function Pokemon({ item }) {
    return (
      <div>
        No.{item.id} {item.name}
      </div>
    );
  }

  function App() {
    return (
      <ul>
        {items.map((item) => (
          <li key={item.id}>
            <Pokemon item={item} />
          </li>
        ))}
      </ul>
    );
  }

  export default App;
  ```
  
- 변수에 map 함수 사용
  ```JavaScript
  function Pokemon({ item }) {
    return (
      <div>
        No.{item.id} {item.name}
      </div>
    );
  }

  function App() {
    const renderedItems = items.map((item) => (
      <li key={item.id}>
        <Pokemon item={item} />
      </li>
    ));

    return (
      <ul>
        {renderedItems}
      </ul>
    );
  }

  export default App;
  ```
  
### 반드시 ```key```를 내려주자
- 각 요소를 렌더링 할 때 ```key``` prop을 가장 바깥쪽에 있는 태그에 지정
- ```id```는 각 요소를 구분할 수 있는 고유한 값
- ```key```는 반드시 ```id```가 아니어도 괜찮고, 각 데이터를 구분할 수 있는 고유한 값이면 무엇이든 가능
