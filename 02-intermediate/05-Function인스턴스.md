# Function 인스턴스

## Function 인스턴스 기준

-   Function 구분하기
    -   빌트인 Function 오브젝트
    -   Function 오브젝트: function 키워드로 생성
    -   Function 인스턴스: new 연산자로 생성
-   Function 오브젝트도 인스턴스이다
    -   왜냐하면 빌트인 Function 오브젝트로 생성하기 때문이다
    -   성격상 인스턴스라고 봐야 하지만 new 연산자로 생성된 function instance와 구별하기 위해서 Function 오브젝트라고 표기할 것임
-   new 연산자로 생성하는 인스턴스는 일반적으로 prototype에 프로퍼티를 작성한다.

    ```js
    function Book(point) {
        this.point = point;
    }

    Book.prototype.getPoint = function () {
        return this.point + 200;
    };

    var obj = new Book(100);
    obj.getPoint();
    ```

### 인스턴스 생성 과정

-   `function Book(...){}`

    -   Book 오브젝트 생성한다.
    -   Book.prototype이 만들어진다 (자동으로 엔진이 생성함)

-   함수/메서드 기준
    -   (일단은) 프로토타입에 연결되어 있으면 메서드, 아니면 함수라고 보는 것이 타당하다고 생각하기

## 생성자 함수

-   new 연산자와 함께 인스턴스를 생성하는 함수이다.
    -   `new Book()`에서 Book()이 생성자 함수이다.
-   코딩 관례로 생성자 함수의 첫 문자는 대문자로 시작한다.
    -   new Number(), new Array(), new Book()

```js
function Book(point) {
    this.point = point;
}

Book.prototype.getPoint = function () {
    return this.point;
};

var bookObj = new Book();
```

```js
Book_인스턴스: {
    point: 10,
    __proto__: {
        constructor: Book,
        getPoint: function(){},
        __proto__: Object,
    }
}
```

## Constructor 프로퍼티

-   생성하는 function 오브젝트를 참조한다.
    -   function 오브젝트를 생성할 때 설정되며 prototype에 연결되어 있다.

```js
const Book_Function_오브젝트= {
    prototype: {
        constructor: Book;
    }
}
```

### Constructor의 특징

1. Book === Book.prototype.constructor
2. Book === book인스턴스.constructor
3. typeof Book: function
4. typeof book인스턴스: object

### prototype 오브젝트의 목적

-   prototype을 확장한다.
    -   prototype에 프로퍼티를 연결하여 prototype을 확장하기 이ㅜ함이다.
    -   Book.prototype.getPoint = function(){}
-   프로퍼티 공유
    -   생성한 인스턴스에서 원본 prototype의 프로퍼티를 공유한다.
        ```js
        var obj = new Book(123);
        obj.getPoint();
        ```
        굳이 인스턴스별로 가져야 하는 메서드가 아닌 이상 prototype에 공유하면 자원을 절약할 수 있다.

### 인스턴스 상속

    - 프로토타입에 연결된 프로퍼티로 인스턴스를 생성하여 상속 받을 prototype에 연결하는 것이다.
    - prototype-based 상속이라고도 한다.
    - prototype은 자바스크립트에서 상속보다는 프로퍼티의 연결이라는 의미가 더 크다.

### prototype 확장 방법

-   prototype에 프로퍼티를 연결하여 작성한다.

    -   prototype.name = value 형태이다.
    -   name에 프로퍼티 이름을 작성하고
    -   value에 JS데이터 타입을 작성하는데 일반적으로는 function을 사용한다.
    -   prototype에 null을 설정하면 더는 확장하지 않겠다는 뜻이다.

-   prototype을 `{name:value}`꼴의 형태로 한꺼번에 할당해도 된다.
    -   그러나 constructor가 prototype에 존재하는데 덮어씌우면 지워지므로 constructor 연결하는 작업이 반드시 필요하다.

```js
function Book() {}
Book.prototype = {
    constructor: Book, // 연결 작업을 수행한다.
    setPoint: function () {},
};
var obj = new Book();
console.log(obj.constructor);
```

## prototype 프로퍼티 공유 시점

-   사용하는 시점(메서드 호출 시점) prototype의 프로퍼티 공유
-   인스턴스의 메서드를 호출하면 원본 prototype의 메서드를 호출한다.

## 인스턴스 프로퍼티

-   prototype에 연결된 프로퍼티도 인스턴스의 프로퍼티가 된다.
-   직접 인스턴스에 연결된 프로퍼티와는 차이가 있다.
-   인스턴스의 프로퍼티를 prototype에 연결된 인스턴스 프로퍼티보다 먼저 사용된다.
-   이런 우선순위대로 사용되는 이유는 인스턴스마다 값을 다르게 가질 수 있기 때문이다.
