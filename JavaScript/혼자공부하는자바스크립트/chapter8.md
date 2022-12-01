# chapter 6 예외처리
- 구문 오류 : 괄호의 개수를 잘못 입력하는 등의 오류로 코드가 실행조차 되지 않는 오류
- 예외 : 문법적 오류를 제외한 코드 실행 중간에 발생하는 오류
- 예외 처리 : 예외를 처리하는 것 

## ✔️ 8_1 구문 오류와 예외
### ✅ 구문 오류
- 프로그램 실행 전에 발생하는 오류
- 구문 오류가 발생하면 웹 브라우저가 코드를 분석조차 하지 못하므로 실행되지 않음
```javaScript
    console.log("# 프로그램이 시작되었습니다!")
    console.log("괄호를 닫지 않는 실수를 했습니다."
```
![image](https://user-images.githubusercontent.com/100126319/205055887-ff3934e1-2bdc-43c1-9a95-e74793afabe3.png)

### ✅ 예외 or 런타임 오류
- 예외 or 런타임 오류 : 프로그램 실행 중에 발생하는 오류
```javaScript
    console.log("# 프로그램이 시작되었습니다!")
    console.rog("log를 rog로 잘못 입력했습니다.")
```
![image](https://user-images.githubusercontent.com/100126319/205055985-146e5318-6756-4df0-ab6e-66a1e8a542e1.png)
### ✅ 기본 예외 처리
```javaScript
    document.addEventListener('DOMContentLoaded', () => {
      const h1 = document.querySelector('h1')
      h1.textContent = '안녕하세요'
    })
```
- body 태그 내부에 h1 태그가 없는 경우 예외가 발생한다.

![image](https://user-images.githubusercontent.com/100126319/205057019-7fca8be0-0ca1-4c32-90d2-5d6d7a2bf463.png)
- 조건문을 활용하여 예외 처리를 할 수 있다.
```javaScript
    document.addEventListener('DOMContentLoaded', () => {
      const h1 = document.querySelector('h1')
      if(h1) {
        h1.textContent = '안녕하세요'
      } else {
        console.log('h1 태그를 추출할 수 없습니다.')
      }
    })
```
![image](https://user-images.githubusercontent.com/100126319/205057479-be281ca1-1a19-49ae-a533-22b35f7d3a81.png)

### ✅ try catch 구문
```javaScript
    try {
      //예외가 발생할 가능성이 있는 코드
    } catch (error) {
      // 예외가 발생했을 때 실행할 코드
    } finally {
      // 무조건 실행할 코드
    }
```
- try 구문 안에서 예외를 발생하면 이를 catch 구문에서 처리
- finally 구문은 필수 사항은 아니고, 필요한 경우에만 사용
```javaScript
    try {
      //예외가 발생할 가능성이 있는 코드
      willExcept.byeBye()
      console.log("try 구문의 마지막 줄")
    } catch (exception) {
      // 예외가 발생했을 때 실행할 코드
      console.log("catch 구문의 마지막 줄")
    }
```
![image](https://user-images.githubusercontent.com/100126319/205060126-0f705d28-9028-443a-adbb-d0440666cb0b.png)

```javaScript
    try {
      //예외가 발생할 가능성이 있는 코드
      willExcept.byeBye()
      console.log("try 구문의 마지막 줄")
    } catch (exception) {
      // 예외가 발생했을 때 실행할 코드
      console.log("catch 구문의 마지막 줄")
    } finally {
      // 무조건 실행할 코드
      console.log("finally 구문의 마지막 줄")
    }
```
![image](https://user-images.githubusercontent.com/100126319/205060443-040331d1-73b7-4fb1-9b5f-b79a9f87cb9b.png)
- try 구문에서 예외가 발생하여 catch 구문이 실행되고, 무조건 실행되는 finally 구문도 실행

#### 기본적으로 어떤 예외가 어디서 어떤 문제가 발생할 지 예측할 수 있다면 if 조건문을 활용하겠지만 어떤 예외가 발생할지 예측하기 힘든 경우가 있다면 ```try catch```로 처리해주는것이 좋다. 

## ✔️  8_1 예외 처리 고급
