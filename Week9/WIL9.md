WIL9

JavaScript

1. 브라우저 동작 원리

자바스크립트 – 웹 브라우저 환경에서 동작하는 웹페이지/애플리케이션에서 많이 사용되며, 서버 사이드 애플리케이션 개발에서도 사용되는 범용 개발 언어가 됨. 웹 애플리케이션의 자바스크립트는 브라우저에서 HTML, CSS와 함께 실행되기에 브라우저 환경을 고려할 때 보다 효율적인 자바스크립트 프로그래밍이 가능.

브라우저의 핵심 기능 : 사용자가 참조하고자 하는 웹페이지를 서버에 요청하고 서버의 응답(HTML, CSS, Javascript, 이미지 파일 등)을 받아 브라우저에 표시. -> HTML, CSS 파일은 렌더링 엔진의 HTML 파서와 CSS 파서에 의해 파싱되어 DOM, CSSOM 트리로 변환, 렌더 트리로 결합. 생성된 렌더 트리를 기반으로 브라우저는 웹페이지를 표시.

자바스크립트 - 자바스크립트 엔진이 처리. HTML 파서가 script 태그 남 -> 자바스크립트 코드를 실행하기 위해 DOM 생성 프로세스 중지, 자바스크립트 엔진으로 제어 권한을 넘김 -> 자바스크립트 엔진(제어 권한을 넘겨 받음)은 script 태그 내의 자바스크립트 코드 또는 script 태그의 src 어트리뷰트에 정의된 자바스크립트 파일을 로드, 파싱 -> 실행 -> 실행 완료 -> HTML 파서로 제어 권한을 넘김 -> 브라우저가 중지했던 시점부터 DOM 생성 재개

브라우저는 동기(Synchronous)적으로 HTML, CSS, Javascript을 처리함 = script 태그의 위치에 따라 블로킹이 발생하여 DOM의 생성이 지연될 수 O => script 태그의 위치는 중요한 의미

body 요소의 가장 아래에 자바스크립트를 위치시키는 것은 좋은 아이디어인 이유 : HTML 요소들 - 스크립트 로딩 지연으로 인해 렌더링에 지장 받는 일이 발생 X -> 페이지 로딩 시간 단축, DOM 미완성 상태에서 자바스크립트가 DOM 조작 시 에러 발생

2. 객체

객체 : 키(key)과 값(value)으로 구성된 프로퍼티(Property, 자바스크립트에서 사용할 수 있는 모든 값 사용 O, 함수도 O - 메소드)들의 집합 = 프로퍼티(=데이터를 의미)와 메소드(데이터를 참조하고 조작할 수 있는 동작을 의미, 객체에 제한되어 있는 함수)로 구성된 집합

자바스크립트의 객체 – 객체지향의 상속 구현을 위해 프로토타입이라고 불리는 객체의 프로퍼티와 메소드를 상속 받을 수 O

-객체 생성 방법 : 객체 리터럴(객체 구현), Object 생성자 함수(new 연산자 + Object 생성자 함수 -> 빈 객체 생성), 생성자 함수
Object 생성자 함수 : new 연산자 + Object 생성자 함수 -> 빈 객체 생성 -> 프로퍼티 또는 메소드 추가하여 객체 완성 (유용하지 X)

객체 리터럴 방식으로 생성된 객체 = Object 생성자 함수(빌트인 함수)로 객체를 생성하는 것을 단순화시킨 축약 표현임 => 자바스크립트 엔진은 객체 리터럴로 객체 생성하는 코드를 만남 -> 내부적으로 Object 생성자 함수를 사용하여 객체를 생성 => 개발자가 일부러 Object 생성자 함수 사용해 객체를 생성해야 할 일 거의 없음

생성자 함수 – 객체 구현을 인자를 받는 함수로 선언 -> 인스턴스 생성이 간편해짐

\*참고 : 객체 내 메소드 선언
this.sayHello = function(){ console.log('Hi! My name is ' + this.name); };
처럼 function() 함수가 들어감

-객체 프로퍼티 접근

프로퍼티 키 : 일반적으로 문자열(빈 문자열 포함)을 지정 - ‘’ 또는 “” 사용, 문자열이나 symbol 값 이외의 값을 지정 -> 암묵적 타입 변환 -> 문자열 됨(문자열 타입의 값으로 수렴될 수 있는 표현식도 가능)

프로퍼티값 접근 방법 : 마침표 표기법, 대괄효 표기법(대괄호 내에 들어가는 프로퍼티 이름은 반드시 문자열이어야 함)

새로운 값을 할당 -> 프로퍼티 값은 갱신 O
객체가 소유하고 있지 않은 프로퍼티 키에 값을 할당 -> 주어진 키와 값으로 프로퍼티를 생성 -> 객체에 추가
delete 연산자를 사용하면 객체의 프로퍼티를 삭제 O

-Pass-by-reference

참조 타입 = 객체의 모든 연산이 실제값이 아닌 참조값으로 처리됨
원시 타입 = 값이 한번 정해지면 변경 X, 값(value)으로 전달(pass-by-value), 런타임(변수 할당 시점)에 메모리의 스택 영역에 고정된 메모리 영역을 점유하고 저장
객체 = 프로퍼티 변경, 추가, 삭제가 가능 -> 변경 가능한 값 => 객체 타입은 동적으로 변화할 수 있음 -> 어느 정도의 메모리 공간을 확보해야 하는지 예측할 수 없음 -> 런타임에 메모리 공간을 확보하고 메모리의 힙 영역에 저장 => 객체는 참조(Reference) 방식으로 전달(Pass-by-reference)

Built-in Object(내장 객체)는 웹페이지 등을 표현하기 위한 공통의 기능을 제공
-Standard Built-in Objects (or Global Objects)
-BOM (Browser Object Model)
-DOM (Document Object Model)

3. 함수

함수 = 어떤 작업을 수행하기 위해 필요한 문들의 집합을 정의한 코드 블록. 이름과 매개변수를 가짐, 필요한 때에 호출하여 코드 블록에 담긴 문들을 일괄적으로 실행 O

함수 정의 : 함수 선언문, 함수 표현식, Function 생성자 함수

-함수 선언문 : function 키워드 + 함수명 + 매개변수 목록 + 함수 몸체로 구성
ex) function square(number) { return number \* number; }

-함수 표현식 :함 수의 일급객체 특성(무명의 리터럴로 표현이 가능, 변수나 자료 구조(객체, 배열 등)에 저장 가능, 함수의 파라미터로 전달 가능, 반환값으로 사용 가능)을 이용하여 함수 리터럴 방식으로 함수를 정의하고 변수에 할당하는 방식

익명 함수(함수명 생략)
ex) var square = function(number) { return number \* number; };

\*주의 : 함수 = 일급객체 -> 변수에 할당 가능(할당된 함수를 가리키는 참조값 저장) => 함수 호출 시 함수를 가리키는 변수명을 사용해야함(함수명X)

함수가 할당된 변수를 사용해 함수를 호출하지 않고 기명 함수의 함수명을 사용해 호출하게 되면 에러가 발생함(함수 표현식에서 사용한 함수명은 외부 코드에서 접근 불가능), 함수 선언문도 함수 표현식과 동일하게 함수 리터럴 방식으로 정의되는 것임

-Function 생성자 함수(일반적으로 사용 X)
함수 선언문, 함수 표현식 모두 함수 리터럴 방식으로 함수를 정의 => 내장 함수 Function 생성자 함수로 함수를 생성하는 것을 단순화시킨 축약법

함수 호이스팅

자바스크립트는 let, const 포함 모든 선언(var, let, const, function, function\*, class)을 호이스팅(Hoisting)함

호이스팅 = var 선언문이나 function 선언문 등 모든 선언문이 해당 Scope의 선두로 옮겨진 것처럼 동작하는 특성 => 모든 선언문(var, let, const, function, function\*, class)이 선언되기 이전에 참조 가능

함수 선언문으로 정의된 함수 = 자바스크립트 엔진이 스크립트가 로딩되는 시점에 바로 초기화하고 VO에 저장 => 함수 선언, 초기화, 할당이 한 번에 이루어짐 -> 함수 선언의 위치와는 상관없이 소스 내 어디든지 호출 가능

함수 표현식 = 변수 호이스팅 발생(변수 생성 및 초기화와 할당이 분리되어 진행, 호이스팅된 변수는 undefined로 초기화, 실제값의 할당은 할당문에서 이루어짐), 스크립트 로딩 시점에 변수 객체(VO)에 함수를 할당하지 않고 runtime에 해석되고 실행

일급 객체(first-class object) = 생성, 대입, 연산, 인자 또는 반환값으로서의 전달 등 프로그래밍 언어의 기본적 조작을 제한 없이 사용할 수 있는 대상 -> 4가지 조건 만족하면 일급 객체(무명의 리터럴로 표현이 가능, 변수나 자료 구조(객체, 배열 등)에 저장 가능, 함수의 파라미터로 전달 가능, 반환값으로 사용 가능)

함수와 다른 객체 구분 특징 = 호출할 수 있다

반환값 : 배열 등 이용하여 한 번에 여러 개의 값을 리턴 가능
자바스크립트 해석기는 return 키워드를 만나면 함수의 실행을 중단 -> 함수를 호출한 코드로 되돌아감(return 키워드 이후에 다른 구문이 존재 시, 그 구문은 실행 X)

함수의 프로퍼티 특징
함수는 객체이기 때문에 함수도 프로퍼티 가질 수 O, arguments 객체는 함수 외부에서는 사용 X, 매개변수(parameter)는 인수(argument)로 초기화됨(매개변수의 갯수보다 인수를 적게 전달했을 때 인수가 전달되지 않은 매개변수는 undefined으로 초기화, 매개변수의 갯수보다 인수를 더 많이 전달한 경우 초과된 인수는 무시)

arguments 객체(유사배열객체) - 매개변수 갯수가 확정되지 않은 가변 인자 함수를 구현할 때 유용

caller 프로퍼티, length 프로퍼티(매개변수 갯수), name 프로퍼티(함수명), **proto** 접근자 프로퍼티( [[Prototype]] 내부 슬롯이 가리키는 프로토타입 객체에 접근하기 위해 사용하는 접근자 프로퍼티, 내부 슬롯 직접 접근X, 간접적인 접근방법 제공하는 경우 접근 O), prototype 프로퍼티(함수 객체만 소유하는 프로퍼티)

프로토타입 객체 = 프로토타입 기반 객체 지향 프로그래밍의 근간을 이루는 객체. 객체간의 상속을 구현하기 위해 사용 => 프로토타입 객체 = 다른 객체에 공유 프로퍼티를 제공하는 객체

함수의 종류 : 즉시 실행함수(최초 한번만 호출, 다시 호출X (function () { ... }()); ), 내부 함수(함수 내부에 정의된 함수, 부모는 자식 변수에 접근X, 자식은 부모의 변수에 접근 O), 재귀함수(자기 자신 호출), 콜백함수(특정 이벤트가 발생했을 때 시스템에 의해 호출되는 함수)

콜백함수 예시

<body>
  <button id="myButton">Click me</button>
  <script>
    var button = document.getElementById('myButton');
    button.addEventListener('click', function() {
      console.log('button clicked!');
    });
  </script>
</body>

4. 배열

배열 = Array 생성자로 생성된 Array 타입의 객체. 프로토타입 객체는 Array.prototype

배열 리터럴은 객체 리터럴과 달리 프로퍼티명이 없고 각 요소의 값만이 존재. 요소에 접근하기 위해 대괄호 표기법만을 사용(인덱스). 자바스크립트 배열은 어떤 데이터 타입의 조합이라도 포함 O

배열 = 일반적으로 배열 리터럴 방식으로 생성
배열 리터럴 방식 = 내장 함수 Array() 생성자 함수로 배열을 생성하는 것을 단순화시킨 것 Array() 생성자 함수는 Array.prototype.constructor 프로퍼티로 접근 가능

const arr = new Array(2); vs const arr = new Array(1, 2, 3);

배열 요소 삭제 : delete 연산자 사용O -> 요소의 값만 삭제됨. 완전히 삭제를 원하는 경우 Array.prototype.splice 메소드를 사용

자바스크립트는 배열의 순회를 위해 for ... in 문을 사용함(for문, for ... of 문도 사용 가능)

Array.length = length 프로퍼티 = 요소의 개수(배열의 길이) \*주의 : 배열 요소의 개수와 length 프로퍼티의 값이 반드시 일치하지는 않음(희소배열 = 배열의 요소가 연속적이지 않은 배열. 배열의 요소 개수 < length 프로퍼티 -> 메모리 낭비)

length 프로퍼티의 값은 명시적으로 변경 가능 -> length 프로퍼티의 값을 현재보다 작게 변경 -> length 프로퍼티 값보다 크거나 같은 인덱스의 요소는 모두 삭제

Array Method -정적 메소드 Array.isArray : 주어진 인수가 배열이면 true, 배열이 아니면 false를 반환
-Array.from() 메소드 : 유사 배열 객체 또는 이터러블 객체를 변환하여 새로운 배열을 생성
-Array.of()는 전달된 인수를 요소로 갖는 배열 생성. Array 생성자 함수와 다르게 전달된 인수가 1개이고 숫자이더라도 인수를 요소로 갖는 배열을 생성
-.indexOf()는 원본 배열에서 인수로 전달된 요소를 검색하여 인덱스 반환(중복 시 첫 번째 인덱스, 요소가 없으면 –1, 두 번째 인수는 검색을 시작할 인덱스)
-.concat()은 인수로 전달된 값들(배열 또는 값)을 원본 배열의 마지막 요소로 추가한 새로운 배열을 반환. 배열인 경우, 배열을 해체하여 새로운 배열의 요소로 추가(원본 배열은 변경X)
-.join()은 원본 배열의 모든 요소를 문자열로 변환한 후, 구분자(기본은 ‘,’임, 인자로 설정 가능)로 연결한 문자열을 반환
-.push()은 인수로 전달받은 모든 값을 원본 배열의 마지막에 요소로 추가하고 변경된 length 값을 반환(원본 배열 직접 변경), 배열인 경우 배열을 그대로 원본 배열의 마지막 요소로 추가( length 프로퍼티를 사용하여 직접 요소를 추가하는 것이 push 메소드보다 빠름)
-.pop()은 원본 배열에서 마지막 요소를 제거하고 제거한 요소를 반환(원본 배열 직접 변경)
-.reverse()는 배열 요소의 순서를 반대로 변경함
-.shift()는 배열의 첫 요소를 제거, 제거한 요소 반환
-.slice(start=0, end=this.length)는 인자로 지정된 배열의 부분을 복사하여 반환(원본 배열 변경X) -> 음수인 경우 끝에서 요소를 반환, 없으면 모두 반환, 1이면 [1]이후의 모든 요소 반환 => 메소드에 인자 전달 안하면 원본 배열의 복사본 생성해서 반환(얕은 복사, 새로운 복사본을 생성)
-.splice(start: number, deleteCount=this.length-start, …items: T[])는 기존의 배열의 요소를 제거하고 그 위치에 새로운 요소를 추가(원본 배열 변경), 제거된 요소를 반환함

5. 문서 객체 모델 DOM

텍스트 파일로 만들어져 있는 웹 문서를 브라우저에 렌더링하려면 웹 문서를 브라우저가 이해할 수 있는 구조로 메모리에 올려야 함.
브라우저의 렌더링 엔진 - 웹 문서를 로드 -> 파싱 -> 웹 문서를 브라우저가 이해할 수 있는 구조로 구성하여 메모리에 적재 = DOM = 모든 요소와 요소의 어트리뷰트, 텍스트를 각각의 객체로 만들고 객체를 부자 관계를 표현할 수 있는 트리 구조로 구성한 것. 자바스크립트를 통해 동적으로 변경 가능, 변경된 DOM은 렌더링에 반영됨 -> 웹 문서의 동적 변경을 위해 DOM은 프로그래밍 언어가 자신에 접근하고 수정할 수 있는 방법을 제공 -> 일반적으로 프로퍼티와 메소드를 갖는 자바스크립트 객체로 제공(DOM API)
=>정적인 웹페이지에 접근하여 동적으로 웹페이지를 변경하기 위한 유일한 방법은 메모리 상에 존재하는 DOM을 변경하는 것이고, 이때 필요한 것이 DOM에 접근하고 변경하는 프로퍼티와 메소드의 집합인 DOM API

DOM은 HTML, ECMAScript에서 정의한 표준이 아닌 별개의 W3C의 공식 표준. 플랫폼/프로그래밍 언어 중립적.

DOM의 기능 : HTML 문서에 대한 모델 구성(브라우저는 HTML 문서를 로드한 후 해당 문서에 대한 모델을 메모리에 생성 -> 모델은 객체의 트리로 구성 = DOM tree), HTML 문서 내의 각 요소에 접근 / 수정(모델 내 각 객체에 접근, 수정할 수 있는 프로퍼티와 메소드를 제공. DOM이 수정되면 브라우저를 통해 사용자가 보게 될 내용 또한 변경됨)

DOM tree = 브라우저가 HTML 문서를 로드한 후 파싱하여 생성하는 모델을 의미(객체의 투리로 구조화됨)

모든 요소, 어트리뷰트, 텍스트는 하나의 객체이며 Document 객체의 자식임.
DOM tree는 네 종류의 노드로 구성 : 문서노드, 요소 노드, 어트리뷰트 노드, 텍스트 노드

문서 노드 = DOM tree에 접근하기 위한 시작점(entry point). 트리의 최상위에 존재. 각각 요소, 어트리뷰트, 텍스트 노드에 접근하려면 문서 노드를 통해야 함
요소 노드 = HTML 요소를 표현. 중첩에 의해 부자 관계를 가지며 이 부자 관계를 통해 정보를 구조화. 문서의 구조를 서술. 어트리뷰트, 텍스트 노드에 접근하려면 먼저 요소 노드를 찾아 접근해야함. 요소별 특성을 표현하기 위해 HTMLElement 객체를 상속한 객체로 구성.
어트리뷰트 노드 = HTML 요소의 어트리뷰트 표현. 해당 어트리뷰트가 지정된 요소의 자식이 아니라 해당 요소의 일부로 표현됨 => 해당 요소 노드를 찾아 접근하면 어트리뷰트를 참조, 수정 가능
텍스트 노드 = HTML 요소의 텍스트를 표현. 요소 노드의 자식이며 자신의 자식 노드를 가질 수 X(DOM tree의 최종단)

DOM Query – 하나의 요소 노드 선택(document.getElementById, document.querySelector. .className으로 크랫스 어트리뷰트 값 변경), 여러개의 요소 노드 선택( document.getElementsByClassName(class), document.getElementsByTagName(tagName), document.querySelectorAll(selector))

DOM Traversing (탐색) - parentNode(부모 노드 탐색), firstChild, lastChild(자식 노드 탐색), hasChildNodes(자식 노드가 있는지 확인하고 Boolean 값 반환), childNodes(자식노드의 컬렉션 반환. 텍스트 요소를 포함한 모든 자식 요소 반환), children(자식 노드의 컬렉션을 반환. 자식 요소 중 Element type 요소만을 반환), previousSibling, nextSibling(형제 노드를 탐색. text node를 포함한 모든 형제 노드 탐색), previousElementSibling, nextElementSibling(형제 노드 탐색. 형제 노드 중 Element type 요소만 탐색)

DOM Manipulation (조작)
텍스트 노드에의 접근/수정 : 해당 텍스트 노드의 부모 노드를 선택(텍스트 노드는 요소 노드의 자식) -> firstChild 프로퍼티를 사용하여 텍스트 노드 탐색 -> 텍스트 노드의 유일한 프로퍼티(nodeValue)를 이용하여 텍스트 취득 -> nodeValue를 이용하여 텍스트 수정(노드의 값 반환. nodeName, nodeType을 통해 노드의 정보를 취득 O)
어트리뷰트 노드에의 접근/수정 : className(class 어트리뷰트의 값을 취득 또는 변경. className 프로퍼티에 값을 할당하는 경우, class 어트리뷰트가 존재하지 않으면 class 어트리뷰트를 생성하고 지정된 값을 설정), classList(add, remove, item, toggle, contains, replace 메소드를 제공), id(id 어트리뷰트의 값을 취득 또는 변경), hasAttribute(attribute) - 지정한 어트리뷰트를 가지고 있는지 검사, getAttribute(attribute) - 어트리뷰트의 값을 취득, setAttribute(attribute, value) - 어트리뷰트와 어트리뷰트 값 설정. removeAttribute(attribute) - 지정한 어트리뷰트를 제거
HTML 콘텐츠 조작(Manipulation) : textContent - 요소의 텍스트 콘텐츠를 취득 또는 변경(마크업 무시). 요소에 새로운 텍스트를 할당하면 텍스트를 변경 가능. 순수한 텍스트만 지정해야 함(마크업을 포함시키면 문자열로 인식되어 그대로 출력), innerText - 요소의 텍스트 콘텐츠에만 접근 가능(권장X), innerHTML - 해당 요소의 모든 자식 요소를 포함하는 모든 콘텐츠를 하나의 문자열로 취득가능(문자열은 마크업 포함)

DOM 조작 방식 : createElement(tagName) - 태그이름 인자로 전달하여 요소를 생성createTextNode(text) - 텍스트를 인자로 전달하여 텍스트 노드를 생성, appendChild(Node) - 인자로 전달한 노드를 마지막 자식 요소로 DOM 트리에 추가, removeChild(Node) - 인자로 전달한 노드를 DOM 트리에 제거

insertAdjacentHTML(position, string) - 인자로 전달한 텍스트를 HTML로 파싱하고 그 결과로 생성된 노드를 DOM 트리의 지정된 위치에 삽입. 첫번째 인자는 삽입 위치(‘beforebegin’, ‘afterbegin’, ‘beforeend’, ‘afterend’), 두번째 인자는 삽입할 요소를 표현한 문자열

style 프로퍼티 사용 -> inline 스타일 선언을 생성. 특정 요소에 inline 스타일을 지정하는 경우 사용

6. 이벤트

이벤트의 종류 : UI Event, Keyboard Event

<UI Event>
load - 웹페이지의 로드가 완료되었을 때
unload	- 웹페이지가 언로드될 때(주로 새로운 페이지를 요청한 경우)
error - 브라우저가 자바스크립트 오류를 만났거나 요청한 자원이 존재하지 않는 경우
resize - 브라우저 창의 크기를 조절했을 때
scroll - 사용자가 페이지를 위아래로 스크롤할 때
select - 텍스트를 선택했을 때

<Keyboard Event>
keydown - 키를 누르고 있을 때
keyup - 누르고 있던 키를 뗄 때
keypress - 키를 누르고 뗏을 때

<Mouse Event>
click - 마우스 버튼을 클릭했을 때
dbclick - 마우스 버튼을 더블 클릭했을 때
mousedown - 마우스 버튼을 누르고 있을 때
mouseup - 누르고 있던 마우스 버튼을 뗄 때
mousemove - 마우스를 움직일 때 (터치스크린에서 동작하지 않는다)
mouseover - 마우스를 요소 위로 움직였을 때 (터치스크린에서 동작하지 않는다)
mouseout - 마우스를 요소 밖으로 움직였을 때 (터치스크린에서 동작하지 않는다)

<Focus Event>
focus/focusin - 요소가 포커스를 얻었을 때
blur/foucusout - 요소가 포커스를 잃었을 때

<Form Event>
input - input 또는 textarea 요소의 값이 변경되었을 때
change - select box, checkbox, radio button의 상태가 변경되었을 때
submit - form을 submit할 때 (버튼 또는 키)
reset - reset 버튼을 클릭할 때 (최근에는 사용 안함)

<Clipboard Event>
cut - 콘텐츠를 잘라내기할 때
copy - 콘텐츠를 복사할 때
paste - 콘텐츠를 붙여넣기할 때

이벤트 핸들러 등록 : 인라인 이벤트 핸들러 방식, 이벤트 핸들러 프로퍼티 방식, addEventListener 메소드 방식

<인라인 이벤트 핸들러 방식> : HTML 요소의 이벤트 핸들러 어트리뷰트에 이벤트 핸들러를 등록하는 방법, 더 이상 사용되지 않으며 사용해서는 안됨

<!DOCTYPE html>
<html>
<body>
  <button onclick="myHandler1(); myHandler2();">Click me</button>
  <script>
    function myHandler1() {
      alert('myHandler1');
    }
    function myHandler2() {
      alert('myHandler2');
    }
  </script>
</body>
</html>

<이벤트 핸들러 프로퍼티 방식> : HTML과 Javascript가 뒤섞이는 문제는 해결할 수 있는 방식. 이벤트 핸들러 프로퍼티에 하나의 이벤트 핸들러만을 바인딩할 수 있다는 단점이 있음

<addEventListener 메소드 방식> : addEventListener 메소드(IE9~ 사용가능. 8까지는 attachEvent 메소드 사용)를 이용하여 대상 DOM 요소에 이벤트를 바인딩하고 해당 이벤트가 발생했을 때 실행될 콜백 함수(이벤트 핸들러)를 지정. 하나의 이벤트에 대해 하나 이상의 이벤트 핸들러를 추가 가능, 캡처링과 버블링 지원, HTML 요소뿐만아니라 모든 DOM 요소(HTML, XML, SVG)에 대해 동작, 브라우저는 웹 문서(HTML, XML, SVG)를 로드한 후, 파싱하여 DOM을 생성

EventTarget.addEventListener(‘eventType’, functionName, [, useCapture]);

 <script>
    addEventListener('click', function () {
      alert('Clicked!');
    });
  </script>

DOM 요소(target)를 지정하지 않으면 전역객체 window(DOM 문서를 포함한 브라우저의 윈도우)에서 발생하는 click 이벤트에 이벤트 핸들러를 바인딩 => 브라우저 윈도우 어디를 클릭하여도 이벤트 핸들러가 동작

<body>
  <label>User name <input type='text'></label>
  <em class="message"></em>

  <script>
    const input = document.querySelector('input[type=text]');
    const msg = document.querySelector('.message');

    input.addEventListener('blur', function () {
      if (input.value.length < 2) {
        msg.innerHTML = '이름은 2자 이상 입력해 주세요';
      } else {
        msg.innerHTML = '';
      }
    });
  </script>
</body>
