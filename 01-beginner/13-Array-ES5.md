# Array ES5 (배열 응용하기)

## 프로퍼티 리스트

-   isArray
    -   배열은 객체인데 `typeof`만 가지고 배열인지를 확인하기가 힘들다.
-   indexOf
-   lastIndexOf
-   forEach
    -   반환하는 것 없이 배열을 순회하면서 콜백함수 실행만
-   every
    -   false일 때까지만 콜백 함수 실행
-   some
    -   true일 때까지만 콜백 함수 실행
-   filter
-   map
    -   콜백함수에서 반환한 값을 이용하여 새로운 배열을 만들어냄
-   reduce
-   `reduceRight`

## index 처리 메서드

-   indexOf
    -   좌에서 우로 순회하면서 값이 같은 요소가 있으면 검색을 종료한다. (이후에 등장하는 값이 같은 요소는 검색하지 않음)
    -   데이터 타입도 체크한다
-   lastIndexOf

## 콜백 함수를 가지는 메서드

-   시맨틱과 독립성을 염두에 두고 학습할 것

### forEach

-   배열의 요소를 하나씩 읽으면서 콜백함수를 호출한다.
-   콜백 함수를 분리할 수 있음. (독립성)
-   콜백함수는 break, continue를 사용할 수가 없음
-   throw는 사용할 수 있음.

## forEach, for문의 차이

-   처음부터 끝까지 반복하고 반복 중간에 끝나지 않는다는 것을 의미한다. (시맨틱)
-   뒤에서 앞으로 읽을 수도 없다. 이것 또한 시맨틱이다.
-   forEach를 시작할 때 반복 범위를 결정하고 시작한다.
    -   따라서 대상 배열의 중간에 요소를 추가하더라도 처리되지 않는다.
    -   그런데 대상 배열에서 삭제된 요소는 또 반영된다.

*   프로그램은 코드가 아닌 `시나리오`로 푼다.

## true, false를 반환하는 메서드

### every

-   false를 반환할 때까지 콜백 함수를 호출한다.
-   false가 반환되면 반복을 종료한다.
-   false가 끝까지 반환되지 않으면 true를 반환한다.
-   false가 되는 조건이 배열의 앞에 있을 때 효율이 높다.

### some

-   every처럼 시맨틱 접근을 한다.
-   단, true를 반환할 때까지 콜백 함수를 호출한다.
    -   끝까지 true를 반환하지 않으면 false를 반환한다.

## filter, map

### filter

-   forEach() 처럼 시맨틱 접근
-   배열의 요소를 하나씩 읽어가면서 true를 반환하면 현재 읽은 요소를 반환하여 배열을 구성한다.
-   조건에 맞는 요소만을 추려낼 때 사용한다.

### map

-   배열의 요소를 하나씩 읽어가면서 콜백 함수에서 반환한 값을 새로운 배열에 첨부하여 반환한다.

## 반환 값을 파라미터 값으로 사용

### reduce, reduceRight

-   배열 끝까지 콜백 함수를 호출하나 파라미터 작성 여부에 따라 처리가 달라진다
-   reduceRight는 반대 방향으로 읽어 나가는 것