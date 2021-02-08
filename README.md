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

```jsx
<link rel="subresource" href="gibberish.js">
```

# <noscript>

```jsx
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

```jsx
let diff = a - b // 권장 안함 
let diff = a - b; // 권장 
```

- 생략때문에 생기는 에러를 사전에 방지할 수 있다. 예를 들어 타이핑이 끝나지 않았다는 것을 알수 있다는 점
- 어떠한 상황에서는 세미콜론을 넣으면 parsers 가 syntax 에러를 바로잡을려고 하기 때문에  퍼포먼스도 증가한다

```jsx
if (test) 
	console.log(test);  // 돌아가지만 비추천 error-prone

if (test) { console.log(test); // 추천
}  
```

- 이 문장에서 code blocks 를 사용하는 것이 더 직관적이며 문장에 무언가가 추가될때 에러를 줄일 수 있다

## 변수 (variables)

- 변수를 생략하고 값을 대입하면 전역 변수로 정의됨 ( not recommended )
- 호이스팅  : interpreter 가 선언된 var 변수들을 해당 scope 에서 가장 위에 배치 시킨다. 중복 선언이 가능하다.
- let 은 블록 scoped, var 은 function scoped

```jsx
if (true) {
	var name ='Paul';
	console.log(name); // Paul
}
console.log(name); // Paul

if (true) {
	let age = 29;
	console.log(age); //29
}
console.log(age); // ReferenceError: age is not defined
```

- age 변수는 if 블록 밖에서 참조 될 수 없음 , 블록 밖 scope 은 다르기 때문
- 블록 scope 은 function scope의 stict 한 부분집합이다
- 떄문에 var의 모든 scope 제한은 let에도 포함된다
- let 은 같은 block scope 안에서 중복 변수 선언 불가능 ( Syntax Error )
- let 은 var 과 다르게 호이스팅이 동작하지 않는다
- var 과 다르게 let은 전역 변수로 선언할지라도 window object 에 속하지 않는다

 

## 데이터 타입 ( Data Type )

- 6개의 simple 데이터 타입이 있다 ( also called primitive types)
- Undefined, Null, Boolean, Number, String, and Symbol
- 1개의 complex 데이터 타입이 있다
- Object

## 연산자 타입 ( Type of Operator )

- ECMAScript 는 loosely typed 이기 때문에 변수의 데이터 타입을 알 수 있는 방법이 있어야한다. typeof 를 사용하여 알 수 있다
- typeof 는 function 이 아닌 연산자 이기 때문에 중괄호가 필요 없다
- typeof null 은 "object"를 반환한다. special value 인 null 은 빈 object 참조 이기 때문이다
- null type 의 값은 empty object pointer 이다. 그렇기 때문에 typeof null 은 object 이다.
- undefined 은 null 로부터 파생되었기 때문에 null == undefined 는 true 가 된다
- 넘버 타입의 소수점 (floating-point value) 는 interger value가 차지하는 메모리보다 두배를 더 차지하지만 자바스크립트는 .0으로 끝나는 소수점을 interger로 변환해서 저장한다

```jsx
//예시
let floatNum = 10.0; // 이 소수점은 integer 10 으로 interpreted 된다 
```

- NaN - 에러는 아니지만 넘버 연산이 실패했다는 뜻
- NaN == NaN 는 false 이며 ECMAScript 는 NaN을 구별 할 수 있는 isNaN() 함수를 제공함
- number() → true 는 1 false 는 0 으로 convert 됨
- number() → null 은 0 , undefined 는 NaN

### String 의 특성

- ECMAScript에서 String 은 immutable 하다 ( 불변 : 생성된 값은 변할 수 없다. 기존 값을 제거하고 새로운 값을 넣어줘야함)

```jsx
let lang = "Java:
lang = lang + "Script";
// 10 charater 크기의 new String 을 만들어서 "Java" 와 "Script" 로 채운 것 
// 그리고 "Java"와 "Script"는 삭제 된다. 
// 이러한 이유 때문에 오래된 브라우저에서는 string concatenation의 비용이 상당하다. 
```

- string conversion → use .toString() . Numbers, booleans, objects, string 에서만 사용 가능하다.
- template literals 는 정확히 말하면 string 이 아니라 string 으로 즉시 평가 되는 자바스크립트의 특별한 문법 표현이다.
- template literals 의 interpolated variables 는 toString() 을 통해 string 으로 변환 된다.

### Template Literal Tag Functions

```jsx
let a = 6;
let b = 9;

function simpleTag(strings, aval, eval, sum) {
	console.log(strings);
	console.log(aval);
	console.log(eval);
	console.log(sum);

	return 'foobar';
}

let untaggedResult = `${ a } + ${ b } = ${ a + b }`;
let taggedResult = simpleTag`${ a } + ${ b } = ${ a + b }`;
// ["", " + ", " = ", ""]
// 6 
// 9 
// 15

console.log(untaggedResult) //"6 + 9 = 15"
console.log(taggedResult); // "foobar"
```

### 심볼 타입 (Symbol Type)

- ECMAScript 6 에서 처음 나옴
- primitive values
- unique and immutable
- 객체(Object) 의 unique 한 속성을 보장하고 싶을때 사용함

```jsx
let sym = Symbol() // symbol 인스턴스화 
typeof sym = symbol // symbol primitive type 
```

- new 키워드로 초기화 시킬 수 없음
- 각자 다른 runtime 간 Sybol 을 공유하거나 사용하고 싶을때 string-keyed global symbol registry 를 사용 할 수 있음

```jsx
let fooGlobalSymbol  = Symbol.for();
console.log(typeof fooGlobalSymbol) // symbol
```

- Symbol.for()의 각각의 string key는  idenpotent ( 연산을 여러번해도 결과가 달라지지 않는 성질) 연산자 성질을 갖고있다.
- 가장 처음에 콜 될때 global runtime registry 를 체크 하고 없다면 new symbol instance를 생성하고 registry에 추가 한다. 만약 체크 했을때 있다면 해당 instance를 재사용 한다.

```jsx
let localSymbol = Symbol('foo');
let globalSymbol = Symbol.for('foo');
console.log(localSymbol === globalSymbol) // false
```

### Symbol.hasInstance

- 해당 부모의 인스턴스인지 알 수 있음

```jsx
function Foo() {
	let f = new Foo();
	console.log(Foo[Symbol.hasInstance](f)); //true
```

### Symbol.iterator

- 객체의 default Iterator 를 반환하는 메소드
- called by for-of statement

### Symbol.match

- Called by String.prototype.match() 메소드

## Object  타입 (Object Type)

- nonspecific groups of data and functionality
- new 연산자를 통해 생성
- 모든 Object 는 다음과 같은 base 속성과 메소드를 가지고 있다
    1. constructor (function)
    2. hasOwnProperty (property name)  
    3. isPrototypeof (object) - 해당 object 가 다른 object의 프로토타입인지 알아보는것
    4. propertyIsEnumerable - for-in statement 로 enumerate 가능한지
    5. toLocaleString() - returns string that is appropriate for the locale of 실행환경
    6. toString() - return string
    7. valueOf() - object 의 value

## 곱셈 연산자

- multiply, divide, modulus.
- empty  string → 0, Boolean value of true → 1
- modulus ( a.k.a remainder )

## 지수 함수 ( Exponential function )

- ECMAScript 7 부터 Math.pow() 는 ** operator 을 따로 갖게 됨

```jsx
console.log(Math.pow(3, 2)l //9
console.log(3 ** 2) //9

let squared = 3;
squared **= 2;
console.log(squared); //9
```

## Equal and Not Equal

- null == undefined → true
- "NaN" == NaN → false
- 5 == NaN → false
- NaN == Nan → false
- false == 0 → true
- true == 1 → true
- null == 0 → false

## Comma Operator

- single statement 로 실행시켜준다

```jsx
let num1 = 1, num2 =2, num3 = 3

let num = (5, 1, 4, 8, 0); // always num becomes 0 
```

## for loop

- 아래와 같이 for-loop 을 while 문과 비슷하게 만들 수 있다

```jsx
let count = 10;
let i = 0;
for (; i < count; ) {
	console.log(i);
	i++;
}
```

- 이러한 유연성 때문에 for statement는 어떠한 언어에서도 쓰인다

## for-in Statement

- 객체에서 문자열로 키가 지정된 모든 열거 가능한 속성에 대해 반복함
- ECMAScript의 Object 프로퍼티의 순서는 보장되어있지 않기때문에 해당 statement도 order는 보장하지 않음

## for-of Statement

- iterable object 에 대해 반복함
- next() 메소드를 통해 order 를 보장함

## Labeled Statement

- 나중에 사용하기 위해 statement 를 label 할 수 있다

```jsx
start: for (let i = 0; i < count; i++ ) {
	console.log(i);
}
```

- 반복문에 레이블을 붙이고 break나 continue 구문을 사용해 반복문의 어느 위치에서 작업을 멈추고 어느 위치에서 다시 수행할지를 알려줄 수 있다.

## Switch Statement

- 원치않는 다음 case statement를 타지 않게 각각의 케이스 안에 break statement 를 넣는것이 가장 좋다
- 자바스크립트의 switch case 는 numbers type 만 되는 많은 언어와 달리 모든 데이터 타입을 받을 수 있다. strings, object 등등
- case 값이 constants 값이 아닌 아래와 같은 표현식이 될 수 있다

```jsx
switch ("hello world") {
	case "hello" + "world":
		console.log("Greeting was found.");
		break;
	default:
		console.log("asdfadf")
}
```

# 간단 요약

- basic type : Undefined, Null, Boolean, Number, String, and Symbol
- 다른 언어와는 다르게 숫자 타입이 integer 와 float 로 나눠져 있지 않고 numbers 하나로 통일됨
- 모든 언어의 기본이 되는 Object 는 complex data type
- strict mode 는 에러를 유발시킬 수 있는 부분들을 미리 차단해주는 제한 방법론
- 반환 값이 없는 함수라도 undefined 라는 special value 를 반환함

# Variables, Scope and Memory

## Primitive과 Reference values

- ECMAScript의 변수는 두가지의 다른 데이터 type 을 가지고 있다.
    1. primitive values 
    2. reference values
- primitive values 는 atomic 한 데이터다
- reference values 는 수많은 values 들로 이루어진 데이터다
- 값이 변수에 할당될떄 자바스크립트 엔진은 이 값이 primitive 인지 reference 인지 판별한다.
- reference values 는 메모리에 저장되는 object 이다.
- 자바스크립트는 메모리에 직접 접근을 하지 못해서 reference (참조) 를 통해서 접근한다.
- 수 많은 언어들은 String이 object이며 reference type 으로 여기는데 ECMAScript는 그렇지 않다.

### Copying values

- Reference Type 은 변수를 복사할 때 주소값을 복사하기 때문에 복사본의 값을 바꾸어도 원본의 값이 바뀐다

### Determining Type

- 연산자 type 은 primitive type 을 가려낼 수 있는 좋은 방법이다. (sting, number, Boolean, undefined 인지)
- type of null is object
- obejct 의 type 을 알아내기 위해선 instanceof operator 를 사용하면 좋다

### 실행 컨텍스트와 스코프

- 웹브라우저 → global context는 window object 이다
- var 키워드로 생성된 전역변수와 함수들은 window 객체의 properties와 함수로 종속된다.
- let과 const 키워드로 생성된 window 객체로 종속되지 않고 해당 스코프체인에 등록된다.
- 실행 컨텍스트가 모든 코드를 실행하고 나면 자신에게 정의 된 모든 변수와 함수를 지운다. 애플리케이션이 종료될때까지 전역 컨텍스트는 지워지지 않는다. ( web page close)
- 함수를 호출할때는 함수 각각의 컨텍스트가 있다.
- 함수가 코드를 실행하면 함수의 컨텍스트가 context stack 으로 push 된다. 함수가 모두 끝나고 나면 stack 가 pop 이 되고 그 전에 실행되던 컨텍스트로 돌아간다.
- 코드가 컨텍스트 안에서 실행되면 변수 객체의 스코프 체인이 생성된다.
- 스코프 체인의 생성 목적은 실행 컨텍스트의 변수와 함수 접근 할때 순차적으로 접근해야 하기 때문이다.
- 전역 컨텍스트 변수 객체는 항상 스코프 체인 마지막이다

### 스코프 체인 Augmentaion

- 2가지 실행 컨텍스트 타입(global , function) 이 있지만 스코프체인의 augmentation을 할 수 있는 다른 방법이 있다.
    1. try-catch 문의 catch 블록 
    2. with 문 

### var 선언

- 호이스팅에 의해서 함수의 가장 윗단이나 전역 스코프의 가장 윗단에 위치하게 됨
- 떄문에 선언이 앞에 안되어 있어도 값을 할당 할 수 있음

### let 선언

- var와 비슷하지만 블록레벨에 스코프 되어 있다.
- 블록 스콥은 중가로 안에 있는 세트 라고 보면 된다.
- var와 다르게 같은 블록 안에서 중복으로 생성 할 수 없다. (syntaxError)
- let 은 기술적으로 자바스크립트 실행환경에서 호이스팅이 되지만 "temporal dead zone" 때문에 선언 전에 사용하는 것이 막혀져 있다. 호이스팅이 var 과 다르게 동작한다.

### const 선언

- const 선언은 primitive 혹은 object 의 top-level 에만 적용된다. 다시 말해 const 선언을 한 object는 다른 참조 값으로 대체 될 수 없지만 object 안에 key들에게까지 적용되지 않는다.
- object 안에 있는 값까지 immutable(불면) 만들고 싶다면 Object.freeze() 를 사용해야한다.

# Garbage Collection (GC)

- 자바스크립트는 garbaged-collected 언어이다.
- 코드 실행시 메모리 관리는 실행환경이 책임 진다는 소리
- 브라우저에서 사용되는 두개의 전통적 방식의 GC 관리법
    1. mark-and-sweep
    2. reference counting

### Mark-and-Sweep

- most popular form of garbage collection
- 변수가 함수안에서 선언되면 컨텍스트 안에 있다고도 표현된다
- 컨텍스트 안에 있는 변수는 메모리 해제가 되어선 안되지만 ( 변수를 언제 또 사용할 지 모르니 ) 컨텍스트에서 벗어난다면 메모리가 해제 된다
- "in-context" 혹은 "out-of-context"
- GC 가 실행될때 메모리에 들어있는 변수들을 모두 마킹한다.
- GC Root들은 힙 외부에서 접근할 수 있는 변수나 오브젝트를 뜻하고 여기서 시작해 모든 오브젝트와 오브젝트들이 참조하는 다른 오브젝트들을 탐색해서 mark 한다 (mark)
- 그리고 GC가 힙 내부를 돌면서 Mark 되지 않은 메모리를 reclaim 한다. (sweep)

### Reference Counting

- less popular type of garbage collection
- 모든 값은 자신이 참조하는 모든것을 기록한다
- 변수가 선언되고 참조값이 할당되면 reference count는 1이다.
- 같은 값에 다른 변수가 항당되면 reference count는 늘어난다.
- 막얀 참주된 변수값이 다른 값으로 overwritten 이 된다면 reference count 는 줄어든다.
- reference count 가 0이 된다면 메모리를 안전하게 해제할 수 있다.

```jsx
// reference counting 방식의 문제점 

function problem() {
	let objectA = new Object();
	let objectB = new Object();

	objectA.someOtherObject = objectB;
	objectB.anotherObject = objectA;
}

// 각각의 objectA 와 objectB는 각자를 참조하고 있고 reference count 는 2이다. 
// mark-and-sweep system에서는 이 두 object는 함수가 실행된 후 scope에서 사라지니 문제가 없다.
// 하지만 reference counting 방식에선 함수가 종료되도 계속해서 종료 하기 때문에 reference count 가 절대로 0 이 될 수 없음으로 
// 무한 반복 되어 메모리 해제가 되지 않고  낭비가 될것이다. 
```

### 메모리 해제 예시

```jsx
let element = document.getElementById("some_element");
let myObject = new Object();
myObject.element = element;
element.someObject = myObject;
```

위의 코드를 보면 DOM element 와 native JavaScript 객체인 myObject 는 서로를 참조(순환 참조) 하고 있다. myObject 변수는 element를 가르키는 element 속성을 지녔고, element 변수는 myObject를 가르키는 someObject 라는 속성을 지녔다. 이런 순환 참조 때문에 해당 DOM element가 페이지에서 사라지더라도 메모리 reclaimed (재할당) 을 할 수 없다.

이러한 낭비를 해결하기 위해서는 사용을 끝낸 native JavaScript 객체와 DOM elements 의 참조 관계를 끊어 주어야 한다. 

```jsx
myObject.element = null;
element.someObject = null;
```

변수에 null 값을 할당하면 변수와 참조하고 있던 값을 끊어 줄 수 있다. Garbage Collector 가 실행될 때 이 값은 삭제되고 메모리는 재할당 된다.

### Performance

Garbage collector는 주기적으로 실행되고 변수가 많이 할당 되어 있는 메모리에선 비용이 많이 들기 때문에 시행 타이밍이 중요하다. 예를 들어 모바일기기의 시스템 메모리는 굉장히 한정적이기 때문에 garbage collection은 기기의 속도와 랜더링 속도에 지장을 줄 수 있다. Garbage collection은 언제 실행될지 모르기 때문에 garbarge collection이 빠르고 최적의 상태로 지나갈 수 있게 코드를 잘 organize 하는것이 best strategy 이다.### 메모리 관리

### 메모리 관리

GC 프로그래밍 환경에서는 개발자는 메모리 관리에 신경쓰지 않아도 되지만 자바스크립트가 특별한 환경에서 실행될때는 신경을 써야 한다. 브라우저에서 사용가능한 메모리의 양은 데스크톱 어플리케이션보다 현저하게 낮다. (mobile 브라우저는 훨씬 심하게 좋지 않다). 변수 할당과 콜 스택과 싱글스레드안에서 실행되는 statement 들이 영향을 받을 수 있다. 

메모리 관리에 가장 좋은 방법은 코드 실행에 필수적인 데이터만 사용하는 것이다. 데이터가 더이상 필수적이지 않을때, null 처리를 해주는 것이 좋다. 참조를 끊어주는 것이 좋다. (it is call dereferencing). 보통 전역 값이나 전역 객체의 property에 해당한다. 로컬 변수는 context 밖으로 나갈 시 자동으로 dereferenced 되기 때문에이다. 

```jsx
function createPerson(name) {
	let localPerson = new Object();
	localPerson.name = name;
	return localPerson;
}

let globalPerson = createPerson("Nicholas");

// do something with globalPerson

globalPerson = null;
```

위의 코드에서 globalPerson 변수는 createPerson() 의 return 값이 할당 되어 있다. createPerson() 안에는 localPerson 이 객체를 만들고 name property를 추가한다. localPerson 변수는 return 되고 globalPerson에 할당된다. localPerson 은 createPerson()의 실행이 끝나면 context에서 나가기 때문에 따로 dereferencing 을 해줄 필요가 없다. 하지만 globalPerson은 전역변수 이기때문에 사용하지 않는다면 null 값을 할당해주면서 dereferencing 을 해줄 필요가 있다. 

### const 와 let 선언은 performance를 증가시켜준다

- const 와 let 키워드는 코드스타일을 세련되게 만들어 줄뿐더러 garbage collection 프로세스에도 도움이 된다.  garbage collection은 var선언의 함수 스코프보다 const , let의 블록 스코프에 더 빨리 접근한다.

### Object pools

- 객체가 초기화된 후 scope 에서 나가게 되면 브라우저는 더 공격적으로 garbage collection 을 실행시키기 때문에 애플리케이션의 성능은 하락합니다.

```jsx
// 좋지않은 객체 초기화 방법
function add(a, b) {
	let result = new Vector();
	result.x = a.x + b.x;
	result.y = a.y + b.y;
	return result;
}
```

- 위의 함수안에서 Vector 객체를 초기화시키면 힙에 올라갑니다. 그리고 호출한곳으로 return 됩니다. 만약 이 vector object 의 생명이 짧다면 금방 참조가 끊길테고 GC의 대상이 됩니다. 그리고 이 함수가 주기적으로 호출된다면 GC 스케쥴러는 이를 감지해 주기적으로 감지하게 됩니다. 때문에 이렇게 함수내부에서 객체를 초기화하는 dynamic vector creation 방식 보다 vector object를 넘겨 받는 방식으로 만드는 것이 좋습니다.

# 간단 요약

- 두개의 타입으로 저장할 수 있다. 1. primitive value 2. reference values
- primitive values는 6가지의 primitive type을 지니고 있는 값이다. (Undefined, Null, Boolean, Number, String and Symbol)
- Primitive value 의 사이즈는 정적이기 때문에 stack memory에 저장된다.
- primitive value 를 복사하면 완전 복사가 된다.
- reference value 는 object 이며 heap memory에 저장된다.
- 실제로 reference value 를 지닌 변수는 object 자체를 변수로 저장하고 있는게 아니라 object 를 가르키는 pointer 를 지니고 있다.
- reference value를 복사하면 pointer를 복사하는 것이기 때문에 같은 object를 참조하고 있다.
- typeof 연산자는 값의 primitive type을 판별하고  instanceof 연산자는 reference type 을 판별한다.
- 모든 변수(primitvie, reference)는 해당 변수의 생명주기를 판별하는 컨텍스트 실행(scope) 시 존재한다.
- 실행 컨택스트는 전역에, 함수안에, blocks 안ㅇ 존재한다.
- 새로운 실행 컨텍스트가 들어오면 스콥 체인을 만들어 변수와 함수를 찾는다.
- 블록이나 함수에 종속되어 있는 local context는 자신의 스콥 안에서만 변수를 찾지 않고 자신에게 속한 모든 컨텍스트안에서 찾는다. + global context.
- 변수의 실행 컨택스트가 언제 메모리를 해제시킬 지 도와준다
- 자바스크립트는 가비지 콜렉터를 이용하는 프로그래밍 환경이기 때문에 개발자는 메모리 할당이나 재할당을 수동적으로 할 필요가 없다.
- 스콥에서 나가게 되는 value는 자동적으로 makred for reclamation 이 되며 가비지 콜렉터가 돌아갈때 타겟이 된다.

#기본 Reference Type

- object (reference value) 는 어떠한 reference type을 갖은 인스턴스이다
- reference type 의 개념은 class 와 같아보이지만 그렇지 않다.
- 새로운 Object 는 new 연산자와 constructor 를 통해 생성된다.

```jsx
let now = new Date();
// 새로운 Date type의 instance를 생성하고 now 변수 안에 저장됨
// 사용된 constructor는 Date() 이다. (기본 프로퍼티와 메소드로 생성된 simple 한 object)
```

## The Date Type

- ECMAScript 의 Date type 은 자바의 [java.util.Date](http://java.util.Date) 으로 부터 파생됨.
- 01-01-1970 으로 부터 millisecond 단위, 28만 오천 육백십육 년 까지 표현 가능함
- new Data() 로 인스턴스를 생성할 때 arguments 가 없이 생성하면 현재 날짜와 시간을 반환함.

```jsx
let someDate = new Date(Date.parse("May 23, 2019"));

let someDate = new Date("May 23, 2019"); // Date constructor 는 Date.parse()를 자동적으로 호출한다.

// 위 두개의 코드는 같은 방식으로 동작한다.
```
