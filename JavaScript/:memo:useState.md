# useState :memo:

### useState?
```JavaScript
const[state, setSetstate] = useState(초기값);

const[time, setTime] = useState(5);
```
- 우리의 현재 상태값은 ```state``` 변수에 들어있다. 
-  ```state``` 를 변경시켜주고 싶을때  ```setState``` 함수를 이용한다.
-  ```state```와 ```setState```이름은 우리의 입맛에 맞게 바꿔줘도 괜찮다. (ex.time)
-  ```setState```함수를 사용해서 ```state```를 변경하면 해당 컴포넌트가 화면에 다시 업데이트(렌더링)된다.

<hr>

## 예시 1
### useState 사용 전
```JavaScript
function App() {
  return (
    <div>
      <span>현재 시각 : 1시</span>
      <button>Update</button>
    </div>
  );
}
```

### useState 사용 후
```JavaScript
import { useState} from 'react';

function App() {
  const [time, setTime] = useState(1);
  
  const handleClick = () => {
  let newTime;
  if (time >= 12) {
  newTime = 1;
  } else {
  newTime = time + 1;
  }
  setTime(newTime);
  };
  
  return (
    <div>
      <span>현재 시각 : {time}시</span>
      <button onClick={handleClick}>Update</button>
    </div>
  );
}

export default App;
```

## 예시 2
### useState 사용 전
```JavaScript
function App() {
  return (
    <div>
      <input type="text" />
      <button>Upload</button>
    </div>
  );
}
```

### useState 사용 후
```JavaScript
import { useState} from 'react';

function App() {
  const [names, setNames] = useState(["홍길동", "김민수"]);
  const [input, setInput] = useState('');
  
  const handleInputChange = (e) => {
    setInput(e.target.value);
    };
    
  consr handleUpload = () => {
  setNames((prevState) => {
  return[input, ...prevState];
  });
  };
  
  return (
    <div>
      <input type="text" value={input} onChange={handleInputChange}/>
      <button onClick={handleUpload}>Upload</button>
      {names.map((name, idx) => {
        return <p key={idx}>{name}</p>
      })}
    </div>
  );
}

export default App;
```
