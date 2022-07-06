# this
### this = 호출한 놈
### this ? 
- 대부분의 경우 ```this```의 값은 함수를 호출한 방법에 의해 결정
  - ```this```는 호출한 놈
  - 호출한 놈이 없을 경우 기본값으로 ```this```는 ```window``` 객체
- 예외
  - 전역스코프에서 ```this```는 window 객체 
  - 화살표 함수에서 this가 조금 달라짐

```JavaScript
let person = {
  fullname: '장세화',
  age : 28,
  printThis : function () {
    console.log(this);                // 출력 : {fullname: '장세화', age : 28, printThis : f}
    console.log(this === person);     // 출력 : true
  },
};
person.printThis();
```

- window 전역객체

```JavaScript
let person = {
  fullname: '장세화',
  age : 28,
  printThis : function () {
    console.log(this);                // 출력 : {window : Window, self : Window ...}
    console.log('this === person: ', this === person);     // 출력=> this === person: false
    console.log('this === window: ', this === window);     // 출력=> this === window: true
  },
};
let printThis = person.printThis;
printThis();
```
