# for문

- for 반복문은 어떤 특정한 조건이 거짓으로 판별될 때까지 반복한다. 
- 자바스크립트의 반복문은 C의 반복문과 비슷하다. 
- for 반복문은 다음과 같다.
```JavaScript
for ([초기문]; [조건문]; [증감문])
  문장
```

- for문이 실행될 때, 다음과 같이 실행된다.
#### 1.초기화 구문인 초기문이 존재한다면 초기문이 실행된다.이 표현은 보통 1이나 반복문 카운터로 초기 설정 된다.그러나 복잡한 구문으로 표현 될 때도 있다. 또한 변수로 선언 되기도 한다.
#### 2.조건문은 조건을 검사하고, 만약 조건문이 참이라면 그 반복문은 실행된다. 만약 조건문이 거짓이라면, 그 for문은 종결된다. 만약 그 조건문이 생략된다면, 그 조건문은 참으로 추정한다.
#### 3.문장이 실행된다. 많은 문장을 실행할 경우엔, { } 를 써서 문장들을 묶어준다.
#### 4.갱신 구문인 증감문이 존재한다면 실행되고 2번째 단계로 돌아간다.

## 예시
```JavaScript
function howMany(selectObject) {
  var numberSelected = 0;
  for (var i = 0; i < selectObject.options.length; i++) {
    if (selectObject.options[i].selected) {
      numberSelected++;
    }
  }
  return numberSelected;
}
```

### 참고
[for문 설명](https://developer.mozilla.org/ko/docs/Web/JavaScript/Guide/Loops_and_iteration#for_%EB%AC%B8)
