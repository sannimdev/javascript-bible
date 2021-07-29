# Global 오브젝트

## Global 오브젝트 개요

-   `<script>`를 통틀어 단 하나만 존재함
-   new 연산자로 인스턴스를 생성할 수 없음
-   모든 코드에서 공유됨
-   Global이라는 이름은 있으나 오브젝트 실체가 없다.

## Global 오브젝트 함수, 변수

-   Global 오브젝트의 함수, 변수를 Global 함수, Global 변수라고 부름.
-   함수 안에 작성한 것
    -   지역 함수, 로컬 함수라고 부른다.

## 프로퍼티 리스트

-   eval: 문자열을 js코드로 간주하여 실행한다. (보안에 취약하지만, 일단 알고만 있자)

## Global 과 Window의 관계

-   글로벌 오브젝트는 Javscript가 주체이다.
-   window오브젝트는 window가 주체이다. (자바스크립트 spec이 아니다)

### isNaN

-   `NaN === NaN` => false
    -   설계 miss
-   but `Object.is(NaN, NaN)`은 true (ES6부터)
