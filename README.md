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
    
# 태그 위치

전통적으로 <script> 엘리먼트는 <head> 엘리먼트 안에서 CSS file 과 함께 위치했었지만 그 뜻은 페이지가 렌더링을 시작하기 전에 ( 렌더링은 브라우저가 <body> 태그를 받을떄 시작한다 ) 모든 자바스크립트 코드가 다운로드 되고 파싱이 되고 interpre 가 된다는 의미이다. 만약 자바스크립트 코드의 양이 많다면 페이지가 렌더링 될떄 인지할만한 지연이 일어날것이다. 이러한 이유때문에 modern web application 에서는 <body>태그 안에 위치 한다. ( 자바스크립 코드가 processed 되기 전에 페이지가 모두 렌더링 된다) 사용자 입장에서 더 좋은 경험을 제공 받는다. 

# Dynamic Script Loading

<script> 태그로 자바스크립트 자원을 불러오는 것으로 국한되어 있지 않다. DOM API 를 사용해서 불러오는 방법도 있다. 

<pre><code>
let script = document.createElement('script');
script.scr = 'gibbersh.js';
document.head.appendChild(scipt);
</code></pre>

하지만 이러한 방식은 브라우저 preloaders 가 알지 못한다. 그렇기 때문에 자원을 fetch 하는 queue의 우선순위에 지장을 준다. 아래와 같은 방식으로 preloaders 에 해당 스크립트를 사용할것이라고  인지 시켜줄 수 있다. 

```JSX
<link rel="subresource" href="gibberish.js">
```

# <noscript>

```JSX
<body>
 <noscript>
  <p>This page requires a Javascript-enabled browser.</p>
 </noscript>
</body>
```

해당 메시지는 오직 자바스크립트를 지원하지 않는 브라우저 환경에서만 보인다. 

# 간단 요약

- 자바스크립트는 <script> 엘리먼트를 통해 HTML 페이지에 insert 된다
- HTML페이지에 직접 인라인 형식으로 마크업과 같이 있을 수 있거나 외부 파일에서 불러올 수 있다
- async 속성은 다른 스크립트가 로딩될떄까지 기다린다거나 렌더링을 block 시키지 않는다. 그렇기 떄문에 로딩속도가 더 빠르지만 순서를 보장 못하기 때문에 불러오는 스크립트 간의 의존성이 있는지 확실히  하고 주의해서 사용해야한다.
- defer 속성은 document가 렌더링이 끝날때까지 스크립트의 실행을 지연시켜준다. deffered scrpt 는 순차적으로 실행된다.
- <nosciprt> 엘리먼트는 script를 지원하지 않는 브라우저에서 실행된다. 반대로 말하면 scipt를 지원하는 환경에서는 렌더링 되지 않는다.

# Syntax

## 식별자 (Identifiers)

- first letter은 letter , _ (underscore) , $ (dollar sign)
- 나머지는 letter,  _ (underscore) , $ (dollar sign), numbers
- 식별자엔 다양한 letter, 즉 extended ASCII 혹은 Unicode letter characters를 사용할 수 있지만 을 권고하지는 않음.
- 컨벤션은 카멜케이스

## 주석 (Comments)

- // single line comment
- /* block comment 혹은 
multi-line comment *

## 문장 (Statements)

- 문장은 세미콜론 (; ) 을 끝으로 완료됨

```
let diff = a - b // 권장 안함 
let diff = a - b; // 권장 
```

- 생략때문에 생기는 에러를 사전에 방지할 수 있다. 예를 들어 타이핑이 끝나지 않았다는 것을 알수 있다는 점
- 어떠한 상황에서는 세미콜론을 넣으면 parsers 가 syntax 에러를 바로잡을려고 하기 때문에  퍼포먼스도 증가한다

```
if (test) 
	console.log(test);  // 돌아가지만 비추천 error-prone

if (test) { console.log(test); // 추천
}  
```

- 이 문장에서 code blocks 를 사용하는 것이 더 직관적이며 문장에 무언가가 추가될때 에러를 줄일 수 있다
