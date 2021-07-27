# 오브젝트

## 오브젝트 구분

-   `빌트인` 오브젝트
    -   사전에 만들어 둔 오브젝트로 Number, String이 여기에 속한다.
-   `네이티브` 오브젝트
    -   JS스펙에서 정의한 오브젝트 (Argument 오브젝트)
    -   빌트인 오브젝트가 이곳에 포함되므로 네이티브 오브젝트가 좀 더 큰 개념이다.
-   `호스트` 오브젝트
    -   빌트인, 네이티브 오브젝트를 제외한 것
    -   window, DOM 오브젝트 관련 (DOM 스펙에 작성된 함수)

## Object 프로퍼티 리스트

### ES3

-   인스턴스를 만드는 모든 Object에 포함된다.
    -   valueOf
    -   hasOwnProperty
    -   propertyIsEnumerable
    -   isPrototypeOf
    -   toString
    -   toLocaleString

### Object()

```js
var obj = Object({ name: '홍길동' });
console.log(obj); // {name: '홍길동'}

var emptyObj = Object(); // 파라미터를 작성하지 않으면 new Object()와 같다.
console.log(emptyObj); // {}

var abc = {}; // Object인스턴스가 생성됨
```

## 빌트인 오브젝트 구조

-   오브젝트 이름 (Object, String, Number)
-   오브젝트.prototype
    -   인스턴스 생성 가능 여부 기준
        -   `Math에는 prototype이 없어서 인스턴스를 만들 수 없다`
    -   프로퍼티를 연결하는 오브젝트
-   오브젝트.prototype.constructor
    -   오브젝트의 생성자
-   오브젝트.prototype.method
    -   `메서드` 이름과 함수 작성
-   오브젝트 구조

## 함수와 메서드

-   `함수(function)`와 `메서드(method)`의 구별법
-   함수
    -   오브젝트에 연결
    -   Object.create()
-   메서드
    -   오브젝트의 prototype에 연결
    -   Object.prototype.toString()

### 함수 및 메서드 호출 방법

-   함수는 `Object.create()`
-   메서드는 `Object.prototype.toString()` 혹은 인스턴스를 생성하여 호출할 수도 있다.

### 프로퍼티 처리 메서드

-   hasOwnProperty
    -   상속받은 프로퍼티의 경우 false를 반환한다.
    ```js
    console.log({}.hasOwnProperty('hasOwnProperty')); // false
    ```
-   propertyIsEnumerable()
    -   오브젝트에서 프로퍼티를 열거할 수 있으면 true, 아니면 false

## 빌트인 Object의 특징

-   인스턴스를 만들 수 있는 모든 빌트인 오브젝트의 `__proto__`에 `Object.prototype`의 6개 메서드가 설정된다.
