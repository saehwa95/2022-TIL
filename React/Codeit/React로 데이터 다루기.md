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

## 데이터 가져오기
### useEffect 
- 처음 한 번만 실행하기
  - useEffect는 컴포넌트가 처음 렌더링 되고 나면 리액트가 콜백 함수를 기억해뒀다가 실행
  - 그 이후로 콜백 함수 실행 X

     ```JavaScript
       useEffect(() => {
        // 실행할 코드
      }, []);
     ```
     
- 값이 바뀔 때마다 실행하기
  - 컴포넌트가 처음 렌더링 되고 나면 리액트가 콜백 함수를 기억해뒀다가 실행
  - 그 이후 렌더링시 디펜던시 리스트에 있는 값들을 확인하여 하나라도 바뀌면 콜백 함수를 기억해뒀다가 실행

     ```JavaScript
       useEffect(() => {
        // 실행할 코드
      }, []);
     ```
     
### 논리 연산자 활용법
- AND 연산자 활용 : ```show``` 값이 ```true```이면 렌더링, ```flase```이면 렌더링 X

  ```JavaScript
    import { useState } from 'react';

    function App() {
      const [show, setShow] = useState(false);

      const handleClick = () => setShow(!show);

      return (
        <div>
          <button onClick={handleClick}>토글</button>
          {show && <p>보인다 👀</p>}
        </div>
      );
    }

    export default App;
  ```
  
- OR 연산자 활용 : ```hide``` 값이 ```true```이면 렌더링  X, ```flase```이면 렌더링

  ```JavaScript
    import { useState } from 'react';

    function App() {
      const [hide, setHide] = useState(true);

      const handleClick = () => setHide(!hide);

      return (
        <div>
          <button onClick={handleClick}>토글</button>
          {hide || <p>보인다 👀</p>}
        </div>
      );
    }

    export default App;
  ```
  
- 삼항 연산자 활용 : ```toggle``` 값이 참일 경우 ```✅```, 거짓일 경우에는 ```❎```를 렌더링

  ```JavaScript
    import { useState } from 'react';

    function App() {
      const [toggle, setToggle] = useState(false);

      const handleClick = () => setToggle(!toggle);

      return (
        <div>
          <button onClick={handleClick}>토글</button>
          {toggle ? <p>✅</p> : <p>❎</p>}
        </div>
      );
    }

    export default App;
  ```
  
### useState
- 초깃값 지정하기 : ```useState``` 함수에 값을 전달하면 초깃값으로 지정 가능
  ```JavaScript
    const [state, setState] = useState(initialState);
  ```
  - 콜백으로 초깃값 지정하기
    ```JavaScript
      const [state, setState] = useState(() => {
        // 초기값을 계산
        return initialState;
      });
    ```
    
    ```JavaScript
      function ReviewForm() {
        const [values, setValues] = useState(() => {
          const savedValues = getSavedValues(); // 처음 렌더링할 때만 실행됨
          return savedValues
        });
        // ...
      }
    ```
 - ```getSavedValues ```라는 함수를 통해서 컴퓨터에 저장된 초깃값을 가져올때 위처럼 콜백 형태로 초깃값을 지정해주면 처음 렌더링 할 때 한 번만 콜백을 실행해서 초깃값을 만들고, 그 이후로는 콜백을 실행하지 않기 때문에 ```getSavedValues```를 불필요하게 실행하지 않음
 - 주의해야하는건 콜백 함수의 실행이 오래 걸릴 수록 초기 렌더링이 늦어진다는 점 


- Setter 함수 사용하기
  - 기본
  
    ```JavaScript
      const [state, setState] = useState(0);

      const handleAddClick = () => {
        setState(state + 1);
      }
    ```
    
  - 참조형 State 사용의 잘못된 예
  
      ```JavaScript
        const [state, setState] = useState({ count: 0 });

        const handleAddClick = () => {
          state.count += 1; // 참조형 변수의 프로퍼티를 수정
          setState(state); // 참조형이기 때문에 변수의 값(레퍼런스)는 변하지 않음
        }
      ```
      
  - 참조형 State 사용의 올바른 예
  
      ```JavaScript
        const [state, setState] = useState({ count: 0 });

        const handleAddClick = () => {
          setState({ ...state, count: state.count + 1 }); // 새로운 객체 생성
        }
      ```
    
  - 콜백으로 State 변경
  
      ```JavaScript
        setState((prevState) => {
          // 다음 State 값을 계산
          return nextState;
        });
      ```
      
  - 콜백으로 State를 변경하는 예시
  
    ```JavaScript
      const [count, setCount] = useState(0);

      const handleAddClick = async () => {
        await addCount();
        setCount((prevCount) => prevCount + 1);
      }
    ```
    
 ## 입력 폼 다루기
 ### onChange
- 리액트에서는 순수 HTML과 다르게 ```onChange``` prop을 사용하면 입력 값이 바뀔 때마다 핸들러 함수를 실행 
- ```oninput``` 이벤트와 동일 

 ### 폼을 다루는 기본적인 방법
 - state를 만들고 ```target.value``` 값을 사용하여 값을 변경할 수 있음 
 - 이때, ```value``` prop으로 state 값을 내려주고, ```onChange``` prop으로 핸들러 함수를 넘겨줌
    
    ```JavaScript
      function TripSearchForm() {
      const [location, setLocation] = useState('Seoul');
      const [checkIn, setCheckIn] = useState('2022-01-01');
      const [checkOut, setCheckOut] = useState('2022-01-02');

      const handleLocationChange = (e) => setLocation(e.target.value);

      const handleCheckInChange = (e) => setCheckIn(e.target.value);

      const handleCheckOutChange = (e) => setCheckOut(e.target.value);

      return (
        <form>
          <h1>검색 시작하기</h1>
          <label htmlFor="location">위치</label>
          <input id="location" name="location" value={location} placeholder="어디로 여행가세요?" onChange={handleLocationChange} />
          <label htmlFor="checkIn">체크인</label>
          <input id="checkIn" type="date" name="checkIn" value={checkIn} onChange={handleCheckInChange} />
          <label htmlFor="checkOut">체크아웃</label>
          <input id="checkOut" type="date" name="checkOut" value={checkOut} onChange={handleCheckOutChange} />
          <button type="submit">검색</button>
        </form>
      )
     }
    ```
    

 ### 폼 값을 객체 하나로 처리하기
 - 이벤트 객체의 ```target.name```과 ```target.value``` 값을 사용해서 값을 변경해 줄 수도 있음 
    ```JavaScript
      function TripSearchForm() {
      const [values, setValues] = useState({
        location: 'Seoul',
        checkIn: '2022-01-01',
        checkOut: '2022-01-02',
      })

      const handleChange = (e) => {
        const { name, value } = e.target;
        setValues((prevValues) => ({
          ...prevValues,
          [name]: value,
        }));
      }

      return (
        <form>
          <h1>검색 시작하기</h1>
          <label htmlFor="location">위치</label>
          <input id="location" name="location" value={values.location} placeholder="어디로 여행가세요?" onChange={handleChange} />
          <label htmlFor="checkIn">체크인</label>
          <input id="checkIn" type="date" name="checkIn" value={values.checkIn} onChange={handleChange} />
          <label htmlFor="checkOut">체크아웃</label>
          <input id="checkOut" type="date" name="checkOut" value={values.checkOut} onChange={handleChange} />
          <button type="submit">검색</button>
        </form>
      )
    }
    ```
    
### 기본 submit 동작 막기
- HTML 폼은 ```submit``` 타입의 버튼을 눌렀을 때 페이지를 이동
- 이벤트 객체의 ```preventDefault``` 를 사용하면 이 동작을 막을 수 있음
  ```JavaScript
    const handleSubmit = (e) => {
    e.preventDefault();
    // ...
  }
  ```
  
### Ref 객체 생성
  ```JavaScript
    import { useRef } from 'react';

    // ...

    const ref = useRef();
  ```
  
- 예시
  ```JavaScript
    import { useRef } from 'react';

    function Image({ src }) {
      const imgRef = useRef();

      const handleSizeClick = () => {
        const imgNode = imgRef.current;
        if (!imgNode) return;

        const { width, height } = imgNode;
        console.log(`${width} x ${height}`);
      };

      return (
        <div>
          <img src={src} ref={imgRef} alt="크기를 구할 이미지" />
          <button onClick={handleSizeClick}>크기 구하기</button>
        </div>
      );
    }
  ```
