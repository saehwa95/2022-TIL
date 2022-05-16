# Repeat()
```
str.repeat(count);
```
+ ```repeat()``` 메서드는 문자열을 주어진 횟수만큼 반복해 붙인 새로운 문자열을 반환한다. 

## 예시
```Javascript
'abc'.repeat(-1);   // RangeError
'abc'.repeat(0);    // ''
'abc'.repeat(1);    // 'abc'
'abc'.repeat(2);    // 'abcabc'
'abc'.repeat(3.5);  // 'abcabcabc' (count will be converted to integer)
'abc'.repeat(1/0);  // RangeError
```

## 참고
- https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/repeat
