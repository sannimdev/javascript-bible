# Function 오브젝트

-   call() 함수 호출
-   apply() 함수 호출 (단, 배열을 파라미터로 사용한다)
-   bind(): 새로운 오브젝트를 생성한다.함수를 실행하는 과정이 분절되어 있음.

```js
var obj = new Function('book', 'return book;');
obj('혼자 공부하는 Javascript');
```

## 함수 생명 주기

-   funciton의 분류

    -   빌트인 function 오브젝트
    -   function 오브젝트 (← getBook)
    -   function 인스턴스 (new 연산자 사용)

-   function 오브젝트 생성 방법
    -   function 키워드 사용
    -   `function getBook(title){return title};`
-   자바스크립트 엔진이 functino이라는 키워드를 만나면 이름이 getBook인 function 오브젝트를 생성한다.

## 함수 형태

-   함수 선언문
    -   Function Declaration
    -   `function getBook(book){...}`
-   함수 표현식
    -   Function Expression
    -   `var getBook = function(book){...}`

```js
var getBook = function inside(value) {
    if (value === 103) {
        return value;
    }
    console.log(value);
    return inside(value + 1);
};
getBook(101);
```

## 함수 호출

-   call()
-   apply()
-   bind()
-   toString(): function 오브젝트에서 toString()은 함수 코드를 문자열로 변환하여 반환한다.

## Argument Object

-   함수가 호출되어 함수 안으로 이동했을 때는 `arguments`의 이름으로 생성되는 오브젝트이다.
-   파라미터라고 부른 것은 Argument Object와의 구별을 위한 것.
-   apply()와 argument object를 잘 조합하면 nice한 코드가 나올 수 있음.
