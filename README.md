# Professional JavaScript for Web Developers, 4th Edition 공부 자료

![JavaScriptForWebDevelopers](https://user-images.githubusercontent.com/51187508/104849536-8aae2100-592d-11eb-8098-70236d364e1a.jpg)

### 책의 주요 포인트만 뽑아서 정리함

---


# What is JavaScript ?

- 자바스크립트 1995 탄생
- input validation 을 handling 하기 위해 탄생
- input field 에 blank 값 혹은 invalid 한 값도 서버로 보내져 비효율적이였기 때문
- 현재 자바스크립트는 data validation 뿐만 아니라 브라우저의 거의 모든 부분과 상호작용을 한다
- Netscape 사의 Brendan Eich 라는 사람이 Mocha 라는 스크립트 언어를 개발 Mocha → liveScript → JavaScript
- 자바스크립트와 ECMAScript 가 동의어로 혼용되기도 한다
- 자바스크립트는 크게 3가지로 나눌 수 있다
1. ECMAScript ( The Core )
2. DOM ( The Document Object Model )
3. BOM ( The Browser Object Model )

# ECMAScript

- ECMA-262 에 정의된 language
- 브라우저에 의존하는 언어가 아님, 브라우저를 하나의 도구로 사용함
- DOM 은 ECMAScript 의 코어를 이용하여 동작한다
- NodeJS 는 브라우저와 다른 host environment 이다

# The Document Object Model

- DOM 은 XML의 application programming interface 이며 HTML 에서 사용가능하게 확장되었다.
- DOM 은 page 를 노드 계층화 시킨다
- DOM level 1 의 goal 은 document의 구조를 map out 시키는 것
- DOM level 2 의 goal 은
    1. DOM views - keep track of various views of a document ( document before and after css styling)
    2. DOM events - events and event handling
    3. DOM style - CSS-based styling
    4. DOM traversal and range - document tree 를 수정한다 

- DOM level 3의 goal 은 document 를 load 와 save 할 수 있는 DOM Load and Save model, DOM 을 validate 할 수 있는 DOM Validation model 등이 있다

# The Browser Object Model

- BOM 을 이용하여 브라우저의 페이지 밖 영역과도 상호작용을 할 수 있게 됬다
- 새로운 브라우저를 popup 시키는 기능
- 브라우저크기를 줄이고 움직이고 닫는 기능
- navigator object, location object, screen object, performance object, cookies, XMLHttpRequest
- 오랫동안 standard 가 없었기에 다양한 브라우저들이 각자만의 implementaion 기준이 생겼지만 HTML5로 인해 많이 통일되고 개선되었다.

# 간단 요약

- 자바스크립트는 스크립트 언어 이며 웹 페이지와 상호작용을 하기 위해 만들어 졌고 아래의 3가지 파트로 나뉜다
- ECMAScript - 코어 functionality 를 제공
- Document Object Model (DOM) - 웹 페이지와 소통하기 위한 메소드와 인터페이스를 제공
- Browser Object Model (BOM) - 브라우저와 소통하기위한 메소드와 인터페이스를 제공

# <Script> Element

- 자바스크립트를 HTML 에 insert 하기 위한 primary 방식이다
- 네트스케이프가 개발함
- 훗날 HTML 의 스팩에 추가됨
- 총 6가지의 attributes 들이 있음
    1. async - script가 다운로드 진행 하는 동시에 다른 작업도 동시에 하기 위해  ( Optional )
    2. charset - character set of code 잘 안쓰임 (Optional)
    3. crossorigin - CORS 세팅, 사용하지 않는 방식이 default, crossorigin="use-credentials" 는 앞으로 나갈 요청에 credentials 값이 포함 될것이라는 플래그 값이다. (Optional)
    4. defer - Document의 contents 가 파싱이 완료되며 display가 잘 될때까지 스크립트의 실행을 지연시키는 것
    5. integrity - verification of Subresource Integrity (SRI) 를 허락 by checking the resources against provided cryptographic signature.  
    6. language - 코드 블록이 사용하는  스크립트 언어를 표시 ( deprecated )
    7. src - 코드 형식의 external file 을 사용할다는 표시 (Optional)
    8. type - language를 대체함, 코드 블록에서 사용하는 content type ( a.k.a MIME type ) 을 표시함, 전통적으로 해당 값은 text/javascript , text/exmascript 였다. 둘다 deprecated. 자바스크립트 파일은 보통 application/x-javascript 타입이다. 

- <script> 는 페이지에 직접적으로 embed 될 수 있으며 external file 에서 불러올 수 있다
- <script> element 안에 있는 자바스크립트 코드는 위에서 아래로 interpret 된다.
- 예를 들어 정의한 function은 interpret 되어 인터프리터 환경 속에 저장된다. 나머지 page content 는 <script>안에 있는 코드들이 모두 평가될때 까지 load 되지 않는다.
- <script src = "example.js" /> 처럼 script 닫기 태그를 생략하고 하나로 퉁치는 것은 피해야한다. 해당 방식을 다루지 않는 브라우저들이 있다 특히나 인터넷 익스플로러
