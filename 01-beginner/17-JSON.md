# Json 오브젝트

## 개요

-   JavaScript Object Notation
    -   빌트인 오브젝트
    -   new 연산자로 인스턴스를 생성할 수는 없음

```js
var bookshelf = {
    book: ['책'],
    title: 123,
};
var result = JSON.stringify(bookshelf);
console.log(result);
```

```json
{ "book": ["책"], "title": 123 }
```

## JSON 타입 파싱

-   parse()
    ```js
    var value = 111;
    try {
        var result = JSON.parse(value);
    } catch (e) {
        console.log(e, '파싱 오류');
    }
    console.log(result); // 111
    console.log(typeof result); // number
    ```
    -   parse의 두 번째 파라미터
    ```js
    var data = '{"book": "책", "movie": "영화"}';
    var check = function (key, value) {
        return key === 'book' ? 'Javascript' : value;
    };
    var result = JSON.parse(data, check); // check callback
    console.log(result);
    ```
