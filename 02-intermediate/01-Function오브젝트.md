# Function 오브젝트

## 1. 함수의 호출 과정

-   함수가 호출되면
-   엔진은 함수의 변수와 함수를 `{name:value}`의 형태로 실행 환경 설정 후 함수 코드 실행한다.
-   `function(){}` 👉 `{name: value}`의 형태로 연상하는 것에 익숙해져야 한다.

## 2. 생성 과정

1.  `function foo(){..}` 형태에서function을 만나면
2.  오브젝트를 생성하고 저장한다.
    -   `{foo: {...}}`
    -   foo는 function 오브젝트의 이름이다.
    -   오브젝트 {...}에 프로퍼티가 없는 상태
    -   이제부터 빈 오브젝트의 형태를 채움.
        ```js
        const foo = function () {};
        ```
3.  `foo` 오브젝트에 `prototype` 오브젝트를 첨부한다.
    ```js
    foo = {
        prototype: {
            constructor: foo,
            __proto__: {},
        },
    };
    ```
4.  foo에 constructror 프로퍼티 첨부
5.  foo에 `__proto__` 오브젝트 첨부
    -   엔진이 사용한다는 뉘앙스로 정의
    -   ES6부터 `__proto__`가 스펙에 기술되어 있음
    -   ES5 기준으로는 표준이 아니나 2000년대부터 파이어폭스를 사용
6.  빌트인 Object.prototype의 메서드로 Object인스턴스를 생성하여 `prototype.__proto__`에 첨부
    ```js
    foo = {
        // 초깃값 설정
        arguments: {},
        caller: {},
        length: 0,
        name: 'foo',
        // prototype의 __proto__와 __proto__ 계층이 다르다는 것에 유의할 것.
        prototype: {
            constructor: foo,
            __proto__: Object.prototype,
        },
        __proto__: Function.prototype, // String이면 String.prototype이 Array면 Array.prototype이 여기에 지정된다.
    };
    ```

-   사람이 살필 때 function은 `함수`라고 생각할 수 있지만 엔진의 관점에서는 `{key:value}`로 구성된 object라고 보인다는 것을 고려하자.

## 3. 함수 실행 환경 인식

-   함수가 호출되었을 때 실행될 환경을 알아야 실행환경에 맞춰 실행할 수 있다.
-   function 오브젝트를 생성하고 바로 실행하지 않으므로 함수가 호출될 수 있도록 환경 자체를 저장해야 한다.
-   생성한 function 오브젝트에 환경이 `{name:value}`꼴로 저장된다. `[[Scope]]`
-   내부 프로퍼티는 엔진이 처리하기 위해 사용하는 속성이며 외부에서는 사용할 수 없다.

## 4. 내부 프로퍼티

-   공통 프로퍼티
    -   모든 오브젝트(빌트인)에 공통으로 설정되는 프로퍼티
-   선택적 프로퍼티
    -   오브젝트에 따라 선택적으로 설정되는 프로퍼티이다.
    -   Array Object에는 설정되나 Number Object에는 설정되지 않는 것들

## 5. 함수 정의 형태

-   함수?
    -   함수 코드가 실행될 수 있도록 JS문법에 맞게 함수를 작성한다.
        -   함수 선언문
        -   함수 표현식
        -   new Function(param, body) 문자열로 작성

## 6. 엔진 해석 방법

-   자바스크립트는 스크립팅 언어이다.
-   작성된 코드르 위에서부터 한 줄씩 해석하지만, 자바스크립트는 이와는 조금 다르다.
-   중간에 있는 코드가 먼저 해석될 수 있다.
-   함수 선언문을 작성한 순서대로 해석한 뒤 표현식을 작성한 순서대로 해석한다.

## 7. 함수 코드 해석 순서

```js
function post() {
    debugger;
    var title = '오늘의 일기';
    function getPost() {
        return title;
    }
    var readPost = function () {};
    getPost();
}
post();
```

### 변수 초기화 과정

1. 코드 안에서 함수 선언문을 해석한다.
    - function getPost()
2. 변수 초기화
    - `var title = undefined`
    - `var readPost = undefined`
3. 코드 실행
    - `var title = '오늘의 일기'`
    - `var getPost = function(){}`
    - `getPost()`

### 실행 과정 (코드 실행 자세히)

1. `post()` 호출
2. debugger를 만난다.
3. `var title = '오늘의 일기'` 할당
4. `var readBook = function(){}` 할당
5. `getBook()` 호출

## 8. 호이스팅

-   함수 선언문은 초기화 단계에서 `function` 오브젝트를 생성한다.
-   따라서 함수 선언문을 작성한 순서보다 앞선 곳(코드 줄)에서도 함수 선언문으로 작성된 함수 이름을 호출하여도 바로 실행할 수 있음.
-   이를 호이스팅(Hoisting)이라고 하는데 용어를 익히기보다는 개념으로 접근하는 것이 낫다.

```js
var result = getValue();
console.log(result);

function getValue() {
    return '호이스팅';
}
result = function getValue() {
    return '함수 표현식';
};
console.log(result());
```

-   코딩시간

```js
function book() {
    function getBook() {
        return '책1';
    }
    // 여기서 함수 호출하기
    console.log(getBook()); // 책2
    function getBook() {
        return '책2';
    }
}
book();
```

## 9. 오버로딩

-   함수 이름이 같더라도 파라미터 수 또는 값 타입이 다르면 각각 존재한다.
-   🔥 그러나 JS에서는 오버로딩을 지원하지 않는데 JS는 파라미터 수와 값 타입을 구분하지 않고 `{name: value}`의 형태로 저장하기 때문이다.
-   위의 book 예제에서 `'책1'`을 반환하는 function 오브젝트가 `{getBook:function(){...}}` 형태로 있었는데
    다음 선언문에서 호이스팅될 때 `'책2'`를 반환하는 function 오브젝트가 `{getBook:function(){...}}` 형태로 대체된다.
