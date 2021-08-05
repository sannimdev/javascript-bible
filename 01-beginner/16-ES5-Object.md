# ES5 Object 특징

-   ES5 Object에 함수가 추가되었음.
    -   빌트인 Object의 모든 메서드는 대부분의 빌트인 오브젝트에 첨부된다.
    -   빌트인으로 오브젝트를 생성하므로 연결이 많이 발생한다.
-   함수는 첨부되지 않으므로 연결 부하를 줄일 수 있음

## ES5 함수

-   defineProperty(): 프로퍼티 추가 및 속성 변경
-   defineProperties(): 다수의 프로퍼티 추가 및 속성 변경
-   keys()
-   freeze()

### 프로퍼티 디스크립터

-   value: 설정할 값
-   writable: 프로퍼티 값 변경 가능 여부
-   get: 값 반환 프로퍼티 함수
-   set: 값 설정 프로퍼티 함수
-   enumerable: 프로퍼티 열거 가능 여부
-   configurable: 프로퍼티 삭제 가능 여부

## 오브젝트에 프로퍼티 추가하기

-   defineProperty
    -   프로퍼티마다 상태를 가진다.
        -   상태? 변경, 삭제, 열거를 할 수 있는지의 여부
        -   상태가 `가능`일 때만 처리할 수 있음.
        -   프로퍼티를 추가할 때 상태를 결정한다.

```js
var obj = {};

Object.defineProperty(obj, 'book', {
    value: "You Don't know JS",
    enumerable: true, // ES5 default값이 false이다.
});
console.log(obj);
```

-   defineProperties
    -   다수의 프로퍼티를 추가하기 위함

```js
var obj = {};
Object.defineProperties(obj, {
    javascript: {
        value: 'Javascript',
        enumerable: true,
    },
    java: {
        value: 'Java',
        enumerable: true,
    },
});

for (var name in obj) {
    console.log(name + ': ' + obj[name]);
}
```

## 프로퍼티 디스크립터 🤔

-   프로퍼티 속성 이름과 속성의 값을 정의한다.
    -   디스크립터 타입에 속한 속성만 같이 사용할 수 있다.
-   디스크립터 타입 인식은 value나 writable 작성을 먼저 체크한다.
    -   작성돼 있으면 데이터 프로퍼티 디스크립터로 인식
    -   작성돼 있지 않으면 액세스 프로퍼티 디스크립터 타입으로 인식한다.

같이 작성할 수 없는 예시 코드

```js
var obj = {};
Object.defineProperty(obj, 'language', {
    value: '한국어',
    // get: function () {},
});
```

```
Uncaught TypeError: Invalid property descriptor. Cannot both specify accessors and a value or writable attribute, #<Object>
    at Function.defineProperty (<anonymous>)
    at <anonymous>:2:8
(anonymous) @ VM544:2
```

```js
var obj = {};
Object.defineProperty(obj, 'language', {
    value: '한국어',
    writable: true,
    // get: function () {},
});
obj.language = '영어';
console.log(obj.language);
```

```js
var obj = {};
Object.defineProperty(obj, 'language', {
    value: '한국어',
    writable: false, // 쓰기를 금지하더라도 변경을 시도하는 부분에서 오류가 나지 않는다는 점을 유의하자.
    // get: function () {},
});
obj.language = '일본어';
console.log(obj.language);
```

## getter, setter

-   getter
    -   `var result = obj.language` 코드를 만나면
    -   get 함수에서 특정 값을 반환한다.
    -   반환된 특정 값을 result 변수에 할당하는 원리이다.
        ```js
        var obj = {};
        Object.defineProperty(obj, 'language', {
            get: function () {
                console.log('getter 실행됨');
                return '자바스크립트';
            },
        });
        var result = obj.language;
        console.log(result);
        ```
-   setter

    -   `obj.language = 'Javascript'` 코드를 만나면
    -   'Javascript'를 파라미터 값으로 넘긴다.
    -   data의 value 프로퍼티에 `'Javascript'` 값을 설정한다.
        -   또한, `obj.language` 코드를 만나면 get 함수가 호출되며
        -   get 함수에서 `data.value`를 반환한다.
        -   `setter`에서 설정한 `'Javscript'`가 다시 반환될 것이다.

    ```js
    var obj = {},
        data = {};
    Object.defineProperty(obj, 'language', {
        set: function (value) {
            console.log('Setter: 방금 받은 값인 ' + value + '가 data.value에 저장된다...');
            data.value = value;
        },
        get: function () {
            console.log(
                'Getter: 방금 요청한 값인 language 프로퍼티의 값은 data.value에서 인출된다. (' +
                    data.value +
                    ')'
            );
            return data.value;
        },
    });
    obj.language = 'Javascript';
    console.log(obj.language);
    ```

-   getOwnPropertyNames()

    -   오브젝트 프로퍼티 이름을 배열로 반환한다.
    -   `열거 가능 여부에 관계없이` 반환한다.

-   keys()
    -   열거 가능한 프로퍼티만 추출한다.

## 프로젝트 디스크립터 함수

-   프로퍼티 디스크립터의 속성 이름과 값을 반환한다.
-   getOwnPropertyDescriptor()
-   preventExtensions
    -   오브젝트에 프로퍼티 추가를 금지 (삭제나 변경은 가능하다)
    -   추가 금지로 설정한 뒤에 추가 가능으로 바꿀 수 없다.
-   isExtensible()
    -   프로퍼티 추가 금지 여부 반환
-   seal()
    -   프로퍼티 추가, 삭제 금지 설정
    -   isSealed()
-   freeze()
    -   프로퍼티 추가, 삭제, 변경 금지
    -   isFrozen()
