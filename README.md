# 자바스크립트 개념 총정리

> 자바스크립트를 더 모국어스럽게 만들어 주는 강의

## ✔ 강의 선택 동기

-   [[주간 인프런 #22] 여기 40년 경력의 개발자가 있다](https://www.inflearn.com/pages/weekly-inflearn-22)

### 🎫 40년 경력의 김영보 선생님의 강의를 듣자

우연히 주간인프런에서 `김영보` 개발자 대선배님의 칼럼을 접한 적이 있습니다.
지금과는 조금 다른 풍조이지만, 불과 10여 년 전만 하더라도 `개발자`라고 하면 경력이 매우 짧고 은퇴 코스로는 `치킨집 사장님`이라는 자조 섞인 이야기가 돌던 시절이 있습니다.
사실 개발을 오랫동안 하고 싶었기 때문에 `개발자`로서 개발을 오래 할 수 없다면, 취미의 영역으로만 남겨두려고 했었던 시절이 제게도 있었습니다.
그런데 김영보 선배님께서는 경력이 무려 `40년`이라고 하십니다.

지금은 여건이 많이 나아져서 개발자로서 커리어를 성장해 나가기 이전보다 좋아진 환경이라고 생각하는데 김영보 선생님은 이전의 어려운 환경에서 미래의 후배들을 위해 꿋꿋이 세월의 풍파를 헤쳐 나가면서 모범사례를 만들어 나가셨다는 생각이 듭니다. 꼭 개발이 아니더라도 한 분야에서 `40년` 동안 전문가로서 성장해 왔다는 것은 존경을 높이 살 부분이라고 생각합니다.
2021년 기준, 제가 가장 좋아하는 `자바스크립트`의 강좌를 인프런에 올려주셨으니 이건 꼭 들어야겠다고 다짐했던 적이 있습니다.

### 😍 자바스크립트를 좋아하니까

자바스크립트의 ES6 문법을 최초로 접한 것은 2018~2019년 무렵이었던 것 같습니다. 최근 약 5년 동안 자바스크립트의 문법은 진화하였으며 부족했던 부분은 점차 사용하기 편해지고 있고 깔끔해진 문법으로 더욱 사랑받게 되었습니다. 그때부터 제가 자바스크립트에 본격적으로 애정을 갖기 시작해서인지, 그저 `jQuery`로써 간접적으로만 접한 리눅스나 도스의 명령어를 입력하듯 대했던 자바스크립트를 언어로써 대하게 되었습니다. 그전까지는 가장 익숙했던 언어는 Java였지만, Javascript의 자유분방함에 빠져드는 순간 저의 생각을 가장 잘 옮길 수 있는 그릇은 자바스크립트라는 것을 깨닫게 되고 나서부터 저는 자바스크립트로 말하는 세계에 좀 더 푹 빠져보고 싶다는 생각이 들었습니다.

### ✍ 자바스크립트 빠르게 환기하기

리액트, 뷰를 배우고 나서 이 라이브러리(혹은 프레임워크)를 잘 이용하기 위해서는 자바스크립트라는 언어에 관해 좀 더 학습할 필요가 있다는 것을 느꼈습니다.
자바스크립트의 문법을 좀 더 알고 나면 라이브러리나 프레임워크를 배울 때 좀 더 빠른 속도로 학습할 수 있을뿐더러 현업에서 낯설게 느낄 수밖에 없는 첫 프로젝트의 로직을 파악하는 데 도움이 되지 않을까 생각했습니다. 그래서 [모던 Javascript 튜토리얼](https://ko.javascript.info/)에 나온 예제를 따라 치며 학습했던 적이 있습니다.
이제는 `모던 Javascript 튜토리얼`에서 시각적으로 배운 내용을 `청각`을 이용해 학습하며 새롭게 자극하면서 이미 배운 내용을 빠르게 환기하고자 하는 목적으로 수강하게 되었습니다.

## 🚩 학습 전략

-   튼튼한 기본기를 만들기 위해서는 너무 방대한 양을 다루고 있습니다.
-   자바스크립트의 문법이나 세부적인 항목을 학습하기보다는 메커니즘(실행 문맥, 스코프 체인 등)을 위주로 이해하고자 하였기 때문에 기초적인 부분은 중고급 강좌와 병행하고
    중고급 강좌의 수강이 끝나면 다시 기초적인 부분에 집중해서 놓친 부분을 챙겨가는 것이 지금으로써는 최고의 방법이라고 생각하였습니다.

## 1. 자바스크립트 비기너: 튼튼한 기본 만들기

### 1회독: 🚄급행

-   [x] 1장. 기본 문법
-   [x] 2장. 연산자(Operator)
-   [x] 3장. 문장(Statement)
-   [x] 4장. 함수(Function)
-   [x] 5장. 오브젝트(Object)
-   [x] 6장. 빌트인(Built-in)
-   [x] 7장. Number 오브젝트 (📌: 현재)
-   [x] 8장. String 오브젝트
-   [x] 9장. Object 오브젝트(ES3 기준)
-   [x] 10장. Function 오브젝트
-   [x] 11장. Global 오브젝트
-   [x] 12장. Array 오브젝트 (ES3 기준)
-   [ ] 13장. Array 오브젝트 (ES5 기준)
-   [ ] 14장. Boolean 오브젝트
-   [ ] 15장. 자바스크립트 특징
-   [ ] 16장. Object 오브젝트 (ES5 기준)
-   [ ] 17장. JSON 오브젝트
-   [ ] 18장. Date 오브젝트
-   [ ] 19장. Math 오브젝트

## 2. 자바스크립트 중고급: 근본 핵심 이해

### 1회독: 🚄급행

-   [x] 소개 (📌: 현재)
-   [x] Function 오브젝트
-   [x] Argument
-   [x] 스코프
-   [x] Execution Context
-   [x] Function instance
-   [x] this
-   [x] 논리적 정리
