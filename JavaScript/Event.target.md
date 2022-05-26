# Event.target
- Event 인터페이스의 target 속성은 이벤트가 발생한 대상 객체를 가리킨다. 
- ```Event.target``` 속성을 사용하여 이벤트 위임을 구현할 수 있다. 

## 예제 1
```JavaScript
// 목록 생성
const ul = document.createElement('ul');
document.body.appendChild(ul);

const li1 = document.createElement('li');
const li2 = document.createElement('li');
ul.appendChild(li1);
ul.appendChild(li2);

function hide(evt) {
  // e.target은 사용자가 클릭한 <li> 요소를 가리킴
  // 여기서 e.currentTarget은 부모인 <ul>을 가리킬 것
  evt.target.style.visibility = 'hidden';
}

// 목록에 수신기 부착
// 각각의 <li>를 클릭할 때 호출됨
ul.addEventListener('click', hide, false);
```

## 예제 2
```JavaScript
const Point = (props) => {
  const {day} = useParams();

  const [circleScore, setCircleScore] = useState(0);
  const onClickCircle = (event) => {
    let circledId = event.target.id;
    setCircleScore(circledId);
    console.log(circledId)
  }

    return(
      <div className="Detail">
        <h3><span>{day}요일</span>평점 남기기</h3>
          <div className="Circles">
          <Circle id="1" onClick={onClickCircle} score={circleScore}/>
          <Circle id="2" onClick={onClickCircle} score={circleScore} />
          <Circle id="3" onClick={onClickCircle} score={circleScore} />
          <Circle id="4" onClick={onClickCircle} score={circleScore} />
          <Circle id="5" onClick={onClickCircle} score={circleScore} />
          </div>
        <Link to={`/`} style={{textDecoration:"none"}}>
          <button className="Point">평점 남기기</button>
        </Link>
      </div>
    );
}
```
- onClick 기능을 구현할때 Circle에 id값을 준 뒤 그 id에 Event.target 속성을 사용했다. 
