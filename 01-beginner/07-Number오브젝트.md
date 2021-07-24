# Number 오브젝트

-   변환 예시

```js
console.log(Number(123) + 1); // 124
console.log(Number('aaa')); // NaN
console.log(Number(0x14)); // 10진수로 20
console.log(Number(true)); // 1
console.log(Number(false)); // 0
console.log(Number(null)); //0
console.log(Number(undefined)); // NaN
```

-   Number 상수값도 제공하지만 이는 변경하거나 삭제할 수 없음.
-   영대문자 사용이 관례이다.
-   `Number.MAX_VALUE` 형태로 값을 사용하는 것이 일반적

## New 연산자

```js
var obj = new Number();
console.log(typeof obj); // object
```

1. 빌트인 Number 오브젝트로 인스턴스를 생성하여 반환한다.
2. 생성한 인스턴스 타입은 object이다.

-   원본을 복사하는 개념이며 new 연산자를 사용하면 인스턴스이다.
-   인스턴스 생성하는 목적은 인스턴스마다 값을 가지기 위한 것이다.
    `new Number('123')` vs `new Number('456')`

```js
var obj = new Number('123');
console.log(obj.valueOf()); // valueOf함수를 사용하면 숫자로 변환한다.
```

obj의 구조는 다음과 같다. (`__proto__`에 집중)

-   Number가 제공하는 함수를 사용하려면 `__proto__`를 거쳐간다.

```
obj: Number
    __proto__ : Number
    [[PrimitiveValue]]: 123
```

## 프리미티브 값

-   언어에서 가장 낮은 단계의 값
-   `var book = '책';`

    -   책이라고 하는 것은 분해나 전개할 수 없음(가장 낮은 단계의 값이므로)

-   프리미티브 타입
    -   Number, String, Boolean: 인스턴스 생성 가능
    -   Null, Undefined: 인스턴스 생성 불가
    -   Object: 프리미티브 값을 제공하지 않는다.

## String으로 변환하기

-   `toString()`: 진수를 기입하지 않으면 10진수로 변환한다.

```js
var value = 20;
console.log(value.toString()); // 20을 10진수로 string
console.log(value.toString(16)); // 20을 16진수로 string
```

-   지역화 지원 및 형태를 브라우저 개발사에 일임했으므로 다를 수 있음.
-   지역화를 지원하지 않으면 toString()으로 변환한다.
-   ES5에서는 파라미터를 사용할 수 없다.
-   파라미터에 언어 타입을 사용할 수 있는 것은 ES6부터이다.

```js
var value = 1234.56;
console.log(value.toLocaleString()); //1,234.56
console.log(value.toLocaleString('de-DE')); // 1.234,56
console.log(value.toLocaleString('zh-Hans-CN-u-nu-hanidec')); // 1.234,56
```

## 지수 및 고정소수점 표기

-   toExponential(): 지수
    -   숫자 지수를 표기로 변환하여 문자열로 반환한다.

```js
var value = 1234;
console.log(value.toExponential()); // 1.234e+3

value = 123456;
console.log(value.toExponential(3)); // 1.235e+5
```

-   toFixed(): 고정소수점

```js
var value = 1234.567;
console.log(value.toFixed(2)); // 1234.57
console.log(value.toFixed()); // 1235
console.log(value.toFixed(8)); // 1234.56700000
```
