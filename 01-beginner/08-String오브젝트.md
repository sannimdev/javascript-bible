# String 오브젝트

## String 오브젝트 개요

-   "가나다"처럼 문자를 처리하기 위한 객체
-   String 오브젝트에는 함수와 프로퍼티가 포함되어 있으며 함수를 호출하여 문자를 처리할 수 있음.

## 주요 함수

-   `fromCharCode()`: 유니코드 문자열로 변환하여 반환
-   `valueOf()`: 프리미티브 값으로 반환

```js
var str = String(123);
console.log(typeof str); // string
```

## length 프로퍼티

-   문자 수를 반환한다.

```js
var value = '123';
console.log(value.length); //3
```

-   위 코드에서 value는 string인데 어떻게 `value.length`라는 프로퍼티를 사용할 수 있는 걸까?
    1. 자바스크립트 엔진이 내부에서 `new String('123')`으로 object를 만든다.
    2. 그 뒤 `length`라고 하는 프로퍼티를 이용하여 length에 관련된 결괏값을 찾는다.
    3. 추출한 결괏값을 바탕으로 결괏값을 반환한다.
-   그래서 value가 string 타입이라고 할지라도 length와 같은 string 관련 프로퍼티를 사용할 수 있는 것이다.

## 화이트 스페이스 삭제

-   `trim()`

## 함수 호출과 `__proto__` 구조

### toString이 필요한 이유?

-   string type에서 `toString()`이 굳이?
    -   string prototype에 toString()이 있다. ()
    -   object의 prototype 속성에도 toString()이 있다.
        -   `'str'.__proto__.__proto__ === {}.__proto__` => true ()

## charAt (인덱스를 이용하여 문자열 처리하기)

-   인덱스의 문자열을 반환한다.
-   문자열의 길이보다 인덱스카 크면 빈 문자열을 반환
-   일반적으로 존재하지 않으면 `undefined`를 반환한다.
-   es5부터 배열의 index 표기법인 `str[1]`과 같이 사용할 수 있음.

## indexOf 함수 익혀두기 (TODO)
