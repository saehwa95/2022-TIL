# parseInt(), parseFloat()

## parseInt()
```JavaScript
parseInt(string)
```
- ```parseInt``` 함수는 첫 번째 인자를 문자열로 변환하고, 그 값을 파싱하여 정수나 ```NaN```을 반환한다.
- ```parseInt```는 양의 부호 ```+```와 음의 부호 ```-```를 인식한다. 
- 부호를 찾은 경우 부호를 제거하고, 나머지 문자열에 대해 숫자 파싱을 진행합니다.

## 예제
- ```4```를 반환
```JavaScript
parseInt(4.7, 10)
parseInt(4.7 * 1e22, 10)        // 매우 큰 숫자가 4가 됨
parseInt(0.00000000000434, 10)  // 매우 작은 숫자가 4가 됨
```

- ```NaN```을 반환
```JavaScript
parseInt('Hello', 8); // 숫자가 전혀 아님
parseInt('546', 2);   // 0과 1을 제외한 숫자는 2진법에서 유효하지 않음
```


## parseFloat()
```JavaScript
parseFloat(string)
```
- ```parseFloat```은 전역 객체의 함수 속성
- ```parseFloat```이 양의 부호```+```, 음의 부호```-```, 숫자(```0```-```9```), 소수점(```.```), 지수(```e```, ```E```) 외의 다른 글자를 발견할 경우 해당 문자 이전까지의 문자만 사용해 파싱하며 문제의 문자와 그 이후는 모두 무시한다.
- 소수점이 두 개 이상 존재할 경우 두 번째 소수점 역시 위와 같이 무시된다.
- 주어진 값의 선행 및 후행 공백은 무시한다.
- 주어진 값의 첫 글자를 숫자로 변환할 수 없는 경우 NaN을 반환한다.

## 예제
- ```3.14```를 반환
```JavaScript
parseFloat(3.14);
parseFloat('3.14');
parseFloat('  3.14  ');
parseFloat('314e-2');
parseFloat('0.0314E+2');
parseFloat('3.14와 숫자가 아닌 문자들');
parseFloat({ toString: function() { return "3.14" } });
```

## 참고
[parseInt() 설명](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/parseInt)
[parseFloat() 설명](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/parseFloat)
