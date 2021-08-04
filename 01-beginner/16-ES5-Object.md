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
