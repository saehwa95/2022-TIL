# String.substring()

```str.substring(indexStart[, indexEnd])```

- ```substring()``` 메서드는 ```string``` 객체의 시작 인덱스로부터 종료 인덱스 전까지 문자열의 부분 문자열을 반환한다.
- ```indexStart``` 는 반환문자열의 시작 인덱스
- ```indexEnd``` 는 반환문자열의 마지막 인덱스(포함하지 않음)
- ```substring()``` 메서드는 ```indexStart``` 부터 문자를 추출하지만 ```indexEnd``` 가 포함되지 않아도 괜찮다.
- 만약 ```indexEnd``` 가 생략된 경우, ```substring()``` 문자열의 끝까지 모든 문자를 추출한다.
- 만약 ```indexStart``` 가 ```indexEnd```와 같을 경우, ```substring()``` 빈 문자열을 반환한다.
- 만약 ```indexStart``` 가 ```indexEnd```보다 큰 경우, ```substring()``` 메서드는 마치 두 개의 인자를 바꾼 듯 작동하게 된다. 



### 참고
[String.substring() 설명](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/substring#description)
