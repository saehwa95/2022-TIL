# Math.abs()

``` JavaScript
Math.abs(x)
```

- ```Math.abs()``` 함수는 주어진 숫자의 절대값을 반환한다.
- ```x```가 양수이거나 0이라면 ```x```를 리턴하고, ```x```가 음수라면 ```x```의 반대값, 즉 양수를 반환한다.
- ```abs()```는 ```Math```의 정적 메서드이므로, 사용자가 생성한 ```Math``` 객체의 메서드로 호출할 수 없고 항상 ```Math.abs()```를 사용해야한다. 


## 예제
### Math.abs()의 작동 방식
- 빈 객체, 하나 이상의 요소를 가진 배열, 숫자가 아닌 문자열, ```undefined```나 빈 매개변수를 받으면 ```NaN```을 반환한다. 
- ```null```, 빈 문자열이나 빈 배열을 제공하면 0을 반환한다.
  
  
``` JavaScript
Math.abs('-1');     // 1
Math.abs(-2);       // 2
Math.abs(null);     // 0
Math.abs('');       // 0
Math.abs([]);       // 0
Math.abs([2]);      // 2
Math.abs([1,2]);    // NaN
Math.abs({});       // NaN
Math.abs('string'); // NaN
Math.abs();         // NaN
```

### 참고
[Math.abs() 설명](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Math/abs)
