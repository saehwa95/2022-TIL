# while

- while문은 조건문이 참일 때 실행되는 반복문이다. 
- 조건은 문장안이 실행되기 전에 참, 거짓을 판단한다. 

``` 
while (condition)
  statement 
  ```

```조건```
  
반복이 시작되기 전에 조건문은 참,거짓을 판단받게 된다. 만약 조건문이 참이라면, while문 안의 문장들이 실행된다. 거짓이라면, 문장은 그냥 while 반복문 후로 넘어간다.
  
```문장```
  
조건문이 참일 때만 while문 속의 문장들이 실행된다. 반복문 속에 여러개의 문장을 사용하고 싶다면 중괄호 { } 를 통해 문장들을 하나로 묶어야 한다.


## 예제
  다음의 while문은 n이 3보다 작을때까지 반복한다. 
  
``` JavaScript
var n = 0;
var x = 0;

while (n < 3) {
  n++;
  x += n;
}
```
반복을 살펴보면, n을 x에 계속 더하게 된다. 그러므로 x와 n 변수는 다음의 값을 갖는다.

  
첫번째 반복; n=1 과 x=1

  
두번째 반복; n=2 과 x=3

  
세번째 반복; n=3 과 x=6

### 참고
[while 설명](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Math/abs)](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/Conditional_Operator)](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Statements/while)
