# This

## This 개요

-   키워드이다.
-   실행 콘텍스트의 this 바인딩 컴포넌트에 바인딩한다.
-   글로벌 오브젝트에서 this는 글로벌 오브젝트로 참조한다.

### Host Object

-   window 오브젝트와 같이 다른 오브젝트를 마치 내것처럼 사용하는 개념을 Host 오브젝트라고 한다.
-   DOM 오브젝트도 Host 오브젝트이다.

```js
window.onload = function () {
    var value = 100; // window.onload의 프로퍼티로써 value가 존재하는 것이다.
    console.log(this.value); // undefined => 여기서 this는 window의 프로퍼티를 참조하려고 하는 것이다.
};
```

## This와 인스턴스

-   인스턴스에서 this의 목적?

    -   this로 인스턴스를 참조하여 this.name 형태로 프로퍼티에 접근하기 위함.

-   this.call
    -   파라미터 수가 고정일 때 사용하는 게 편리하다
-   this.apply (배열)
    -   파라미터 수가 유동적이므로 arguments가 편리하다.
-   this.bind()
    -   두 번에 나누어 처리한다
        -   function 오브젝트 생성
        -   생성한 function 오브젝트를 함수로 호출해야 한다.
