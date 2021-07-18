# Arguments 처리 메커니즘

## Argument 처리 구조

-   파라미터는 `{key: value}` 값의 형태로 저장한다.
    -   파라미터 수만큼 0부터 인덱스를 부여하게 된다.
    -   그리고 이 인덱스를 key로 사용한다.
    -   파라미터로 받은 값은 value에 설정하게 된다.
        ```js
        function foo() {}
        console.log(foo(1, 2)); // {0: 'A', 1: 'B'}
        ```
-   Array-like (아😲! 유사 배열!?)
    -   key값이 0부터 1씩 증가한다.
    -   length 프로퍼티가 있어야 한다.
