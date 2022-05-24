# Math.random()

``` JavaScript
Math.random()
```

## 0 이상 1 미만의 난수 생성
```JavaScript
function getRandom() {
  return Math.random();
}
```
## 두 값 사이의 난수 생성
- 이 예제는 주어진 두 값 사이의 난수를 생성한다. 
- 함수의 반환값은 min보다 크거나 같으며, max보다 작다.
```JavaScript
function getRandomArbitrary(min, max) {
  return Math.random() * (max - min) + min;
}
```
## 두 값 사이의 정수 난수 생성
- 두 값 사이의 정수인 난수를 생성한다. 
- 반환값은 min(단, min이 정수가 아니면 min보다 큰 최소의 정수)보다 크거나 같으며, max보다 작다.
```JavaScript
function getRandomInt(min, max) {
  min = Math.ceil(min);
  max = Math.floor(max);
  return Math.floor(Math.random() * (max - min)) + min; //최댓값은 제외, 최솟값은 포함
}
```

### 참고
[Math.random() 설명](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Math/random))
