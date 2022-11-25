# SA 과제를 통해 얻은 경험
## submit()
### SA 과제 요구 사항
- 입력 양식 작성 후 미 작성 있을 경우 경고 문구 띄워주기
- 제출 버튼 클릭 시 제출 완료 알림 창 띄워주기

### 내가 마주한 문제
- 입력 양식 미작성 후 제출 버튼 클릭 시 제출완료 알림 창이 뜨고 미작성 태그에 경고 문구가 뜬다...

### 문제 코드
```html
  // 코드 길이 상 문제 코드만 작성
  <script>
    function submit() {
      return alert('제출완료')
    }
  </script>
  <body>
    <form action="" onsubmit="submit()">
```

### 해결 코드
```html
    <script>
        function done(event) {
            event.preventDefault()
            return alert('제출 완료!')
        }
    </script>
    <body>
        <form action="" onsubmit="done(event)">
```

### 파악하기
- submit()은 html에서 제공하는 예약어이다. 
- 나는 그걸 모르고 작성했으니 당연히 내가 작성한 함수는 실행되지 않는다. 


## index.html
### 내가 마주한 문제
- 배포를 완료하고 링크로 접속하니 404 Not found를 마주했다. 

### 원인
- 컴퓨터는 index.html 파일을 제일 먼저 찾는다. 
- index.html 파일이 뿌리!!!
- 나는 html 파일 이름을 homework라고 지었다. 
- 컴퓨터가 뿌리를 찾는데 아무것도 없으니 404 에러가 나타난것이다. 

### 해결 방법
- homework.html 파일을 index.html 파일로 이름을 바꿨다. 

## 추가 배움
- form 태그는 양식이 제출될 때 url에 그 내용이 같이 보여진다. 
- 이를 막을 수 있는 방법은 ```preventDefault()``` 사용하기
- 리액트에서는 form태그를 사용하기 보다 div태그와 input 태그를 사용해서 만들어보자.
