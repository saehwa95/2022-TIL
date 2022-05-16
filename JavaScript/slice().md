# slice()
```Javascript
arr.slice([begin[, end]])
```
+ ```slice()```는 원본을 대체하지 않는다.
+ 원본 배열에서 요소의 얕은 복사본을 반환한다. 
+ ```String``` 및 ```Number``` 객체가 아닌 문자열과 숫자의 경우 ```slice()```는 문자열과 숫자를 새 배열에 복사한다. 
+ 한 배열에서 문자열이나 숫자를 변경해도 다른 배열에는 영향을 주지 않는다.

## 매개변수 ```begin``` ```end```
```begin```
- 0을 시작으로 하는 추출 시작점에 대한 인덱스를 의미한다. 
- 음수 인덱스는 배열의 끝에서부터의 길이를 나타낸다. 
- ```slice(-2)```는 배열에서 마지막 두 개의 엘리먼트를 추출한다. 
- ```begin```이 ```undefined```인 경우에는 0번 인덱스부터 ```slice```한다. 
- ```begin```이 배열의 길이보다 큰 경우에는 빈 배열을 반환한다.
 
```end```
- 추출을 종료 할 0 기준 인덱스.
- ```slice``` 는 ```end``` 인덱스를 제외하고 추출한다.
ex) ```slice(1,4)```는 두번째 요소부터 네번째 요소까지 (1, 2 및 3을 인덱스로 하는 요소) 추출한다.
- 음수 인덱스는 배열의 끝에서부터의 길이를 나타낸다.
ex) ```slice(2,-1)``` 는 세번째부터 끝에서 두번째 요소까지 추출한다.
- ```end```가 생략되면 ```slice()```는 배열의 끝까지(```arr.length```) 추출한다.
- 만약 ```end``` 값이 배열의 길이보다 크다면, ```silce()```는 배열의 끝까지(```arr.length```) 추출한다.

## 예시
```Javascript
const arr = ['a', 'b', 'c', 'd'];

const arr = arr.slice(1,3); // ['b', 'c']
const arr2 = arr.slice(1); // ['b', 'c', 'd']
const arr3 = arr.slice(-3,-1); // ['b', 'c']
```

- arr.slice(1, 3);
배열의 arr[1] ~ arr[3] 까지(arr[3]은 미포함)를 복사한, 새 배열을 리턴한다.

- arr.slice(1);
두번째 파라미터인 end 값이 입력되지 않으면 시작 index부터 배열의 끝까지를 복사한 새 배열을 리턴한다.

- arr.slice(-3,-1);
begin index나 end index가 음수이면, 배열의 끝에서부터의 길이를 나타낸다.



### 참고
- https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/repeat
- https://hianna.tistory.com/398
