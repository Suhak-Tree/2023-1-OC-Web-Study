1. 리뷰

팀 버너스 리 -> HTML, HTTP, WWW 만듦
골격 구조 -> 4가지. DOCTYPE -> HTML 로봇(크롤링하는)이 이 문서가 글인지, html인지 구분함.

2. 본 수업
   CSS : Cascading style sheet -> 왜 cascade 인가? 스타일을 지정해줄 수 있는 시트인데 상속과 우선순위가 있기 때문에 cascading.

cascading : 폭포수가 떨어지듯 위에서부터 아래로 내려가는 이미지. -> 상속. 우선순위.(CSS의 특징) - 서열관계가 있음.

1. 수많은 html 태그가 있는데, 자식에게 부모의 스타일을 상속할 수 있다면? -> 편리할것
2. 만약 한 요소에 여러 스타일이 적용 된다면? -> 어떤 걸 적용할지 선택
   -> 이 문제를 해결하기 위해 상속과 우선순위를 적용. -> <div> <div> 의 style 지정 및 사용
   domy : document object model -> 트리 구조를 만들어서 관리 -> 빨강의 특성 상속!
   위에서 red를 줬는데 아래에서 red를 무시하고 blue로 적용한 것 -> 우선순위에 의한 결과 (red와 blue중 어떤 것을 선택하는지 -> blue 선택)

스타일 시트 - 브라우저 기본 스타일 - 사용자 스타일 - 인라인 스타일, 내부 스타일 시트, 외부 스타일 시트

1. 사용자 스타일 : 개발자가 직접 만지고 코딩하는 부분 -> 컴퓨터 사용자
2. 제작자 스타일 -> 개발자 우선순위 : !import - 인라인 스타일 - id 스타일 - 클래스 스타일 - 타입 스타일 -> selector를 통해 지정 O
3. 브라우저 기본 스타일 -> 크롬이나, 파이어 폭스 등의 기본 스타일
   head 안에 - style 태그 -> red로 적용 -> body의 내용 -> red
   hq {color : red; font-size:12} -> property -> 이런게 이런게 있다

셀렉터
id 선택자 : #아이디 {속성 : 값 , ... } : 특정 아이드를 가진 요소에 적용
클래스 선택자 : .클래스 {속성 : 값, ...} : 특정 클래스를 가진 모든 요소에 적용 -> .클래스명 {} 으로 선언 -> class=""으로 적용(여러개 적용 가능)
타입 선택자 : 태그 {속성 : 값, ...} : 특정 태그를 사용한 모든 요소에 적용 ex) div -> 태그를 골라서 속성 적용 가능
전체 선택자 : _{속성 : 값, ...} : 문서의 모든 요소에 적용 <style> _ {속성 : 값}

id = "green" , class ="red" -> 우선순위에 의해서 class를 무시하고 id의 속성을 적용한다.
인라인 스타일 : 라인 내에서 지정해서 속성을 적용(내부 스타일 시트)
color : red !important -> 다 무시하고 빨간색으로 변경

3. 필수과제

HTML 내용 정리

HTML (HyperText Markup Language) = 웹페이지를 기술하기 위한 마크업 언어(웹페이지의 내용(content)과 구조(structure)를 담당하는 언어, HTML 태그를 통해 정보 구조화)
HTML document는 .html 확장자를 갖는 순수한 텍스트 파일 -> editor or IDE(Integrated Development Environment)를 사용하여 편집하는 것이 일반적. ex) Visual Studio Code, WebStorm

TML 요소 -> <?> : 시작태그 content </?> : 종료태그 (?는 소문자 사용 추천), 요소는 중첩될 수 O(요소가 다른 요소 포함 O -> 부자관계 성립 ex. 들여쓰기로 구분), non-semantic, semantic 구분
non-semantic 요소 : div, span 등, content에 대하여 어떤 설명 X
semantic 요소 : form, table, img, tag, header, nav, aside, section, article, footer등, content의 의미를 명확히 설명
빈 요소 : content를 가질 수 없는 요소. attribute만 가질 수 O. ex) br, hr, img, input, link. meta
attribute : 요소의 성질 및 특징을 정의하는 명세. 요소에 추가적 정보 제공(이미지 파일 경로, 크기 등) -> 시작 태그에 위치. 이름과 값의 쌍을 이룸(name = "value") ex. <img src="html.png">
src = 이미지 파일의 경로, 파일명. width = 이미지의 너비, height = 이미지의 높이 정보 -> 브라우저가 정보 사용해서 img 요소를 화면에 출력
글로벌 attribute : 모든 HTML 요소가 공통으로 사용할 수 있는 어트리뷰트(대체로 모든) ex. Attribute, id(유일한 식별자 요소에 지정. 중복X), class(class를 요소에 지정. 중복O), hidden(브라우저에 노출X), lang(요소 언어 지정. 검색엔진의 크롤링 시 웹페이지 언어 인식 O), style(인라인 스타일 지정), tabindex(키보드로 페이지 네비게이션 시 이동 순서 지정), title(제목)

검색엔진의 웹사이트 정보 수집 방법
크롤링 : 로봇(robot)이라는 프로그램을 이용 -> 매일 전세계의 웹사이트 정보 수집(검색엔진의 크롤러가 수행)
-> 인덱싱 : 검색 사이트 이용자가 검색할 만한 키워드 미리 예상해서 검색 키워드에 대응하는 인덱스(색인) 만듦 (검색엔진의 인덱서가 수행). 사용되는 정보 = 검색 로봇이 수집한 정보 = 웹 사이트 HTML 코드 -> 웹 사이트는 HTML 코드 만으로 그 의미 인지, 시맨틱 요소를 해석 (
시맨틱 태그 = 브라우저, 검색엔진, 개발자 모두에게 콘텐츠의 의미를 명확히 설명하는 역할.
시맨틱 웹 = 웹에 존재하는 수 많은 웹페이지들에 메타 데이터를 부여, 기존의 잡다한 데이터 집합이었던 웹페이지를 '의미'와 '관련성'을 가지는 거대한 DB로 구축하고자 하는 발상

문서 형식 정의 태그(DTD) : <!DOCTYPE html>으로 시작. 문서 형식(document type)을 HTML5로 지정

html tag : html 요소의 부모 요소. , 실제 내용은 <html>과 </html> 사이에 기술. <!DOCTYPE html> 예외. lang attribute를 많이 사용함

head tag : <head>와 </head> 사이 : document title, 외부 파일의 참조, 메타데이터(HTML 문서의 title, style, link, script에 대한 데이터)의 설정 등 위치, 이 정보들은 브라우저에 표시되지 X, 웹 페이지에 단 하나만 존재
-title tag : 문서 제목 정의. 브라우저 탭에 표시됨
-style tag : HTML 문서를 위한 style 정보 정의
-link tag : 외부 리소스와의 연계 정보를 정의. 주로 HTML과 외부 CSS 파일 연계에 사용
-script tag : client-side JavaScript를 정의. scc 어트리뷰트 사용 -> 외부 JavaScript 파일 로드 O
-meta tag : description, keyword, author, 기타 메타데이터 정의에 사용. 브라우저 검색 엔진 등에 의해 사용됨. charset attribute - 브라우저가 사용할 문자셋 정의
<예시>
SEO(검색엔진 최적화)를 위해 검색엔진이 사용할 keywords을 정의 : <meta name="keywords" content="HTML, CSS, XML, XHTML, JavaScript">
웹페이지의 설명을 정의 : <meta name="description" content="Web tutorials on HTML and CSS">
웹페이지의 저자을 명기 : <meta name="author" content="John Doe">
웹페이지를 30초 마다 Refresh : <meta http-equiv="refresh" content="30">

body tag : <body>와 </body> 사이, 메타데이터 제외한 웹페이지 구성으로 출력되는 대부분의 요소, 단 하나만 존재.

제목(Headings) 태그 : 제목을 나타냄, h1(큼) ~ h6(작음) -> 시맨틱 웹의 의미를 살려 제목 외 사용 안하는 것을 권장.
글자형태(Text Formatting) 태그
-b : bold체 지정(굵게). 의미론적 중요성 X.
-strong : bold체 지정(굵게). 의미론적 중요성 O. 웹 표준 준수 시 사용
-i : Italic체 지정(기울기). 의미론적 중요성 X
-em : emphasized(강조, 중요) text 지정. Italic체 지정(기울기). 의미론적 중요성 O
-small : small text(좀 더 작은 글꼴) 지정
-mark : highlighted text(형광펜) 지정
-del : deleted text(중앙 가로줄 쳐짐) 지정
-ins : inserted text(밑줄) 지정
-sub / sup : subscripted(아래에 쓰임) / superscripted(위에 쓰임) text 지정
본문 태그
-p : 단락(paragraphs) 지정
-br : 빈요소. 종료태그 X. 개행 지정(line break. 줄바꿈). 1개 이상 연속된 공백, 줄바꿈-> 1개의 공백, 줄바꿈으로 표시. &nbsp;으로 연속된 공백 삽입 O
-pre : 형식화된(preformatted) text 지정. pre 태그 내의 content 작성된 그대로 브라우저에 표시.
-hr : 수평줄 삽입
-q : 짧은 인용문 지정. ""사이에 content, 요소가 들어감
-blockquote : 긴 인용문 블록 지정. 들여쓰기함. CSS 이용하여 다양한 style 적용 O

CSS 내용 정리

CSS(Cascading Style Sheets) : HTML이나 XML 등 구조화 된 문서(Document) 화면, 종이 등에 어떻게 렌더링할 것인지를 정의하기 위한 언어(HTML의 각 요소(Element)의 style(design, layout etc)을 정의하여 화면(Screen) 등에 어떻게 렌더링하면 되는지 브라우저에게 설명) -> HTML는 정보와 구조화, CSS는 styling의 정의(HTML은 CSS를 포함 O, HTML없이 단독으로 존재하는 CSS는 의미 X)
셀렉터 (Selector, 선택자) : 스타일을 적용하고자 하는 HTML 요소를 선택. Rule Set(또는 Rule) - 셀렉터에 의해 선택된 특정 HTML 요소를 어떻게 렌더링(Rendering)할 것인지 브라우저에 지시하는 역할 -> RuleSet 집합 = 스타일 시트 -전체 셀렉터 (Universal Selector) : \*. HTML 문서 내의 모든 요소(head 포함) -태그 셀렉터 (Type Selector) : 태그명. 지정된 태그명을 가지는 요소를 선택
-ID 셀렉터 (ID Selector) : #id 어트리뷰트 값. id 어트리뷰트 값을 지정하여 일치하는 요소를 선택(값 중복될 수 없음) -클래스 셀렉터 (Class Selector) : .class 어트리뷰트 값. class 어트리뷰트 값 지정 -> 일치 요소 선택(중복 O) -어트리뷰트 셀렉터 (Attribute Selector) : 셀렉터[어트리뷰트]. 지정된 어트리뷰트 갖는 모든 요소 선택 / 셀렉터[어트리뷰트=”값”]. 지정된 어트리뷰트를 가지며 지정된 값과 어트리뷰트의 값이 일치하는 모든 요소를 선택 .... -복합 셀렉터 (Combinator) : 후손 셀렉터 (Descendant Combinator), 자식 셀렉터 (Child Combinator), 형제(동위) 셀렉터 (Sibling Combinator)(인접 형제, 일반 형제) -가상 클래스 셀렉터 (Pseudo-Class Selector) : 요소의 특정 상태에 따라 스타일을 정의할 때 사용(마우스 올라옴, 링크 방문 아직 안함, 포커스 들어옴) ex. link 셀렉터, 동적 셀렉터 / UI 요소 상태 셀렉터(UI element states pseudo-classes) / 구조 가상 클래스 셀렉터(Structural pseudo-classes) / 부정 셀렉터(Negation pseudo-class) / 정합성 체크 셀렉터(validity pseudo-class) -가상 요소 셀렉터 (Pseudo-Element Selector) : 요소의 특정 부분에 스타일을 적용

프로퍼티 (Property / 속성) : 셀렉터로 HTML 요소 선택 -> {} 내에 프로퍼티(속성)와 값 지정하는 것. 표준 스펙으로 이미 지정되어 있는 것을 사용해야함. 사용자가 임의로 정의할 수 X. 여러개 지정 O, ;으로 구분

- 단위 : px, %(백분율 상대 단위), em(배수단위. 상대단위.), rem(최상위 요소-html의 사이즈를 기준)
- Viewport 단위 : vh(높이), vw(너비), vmin(너비, 높이 작은쪽의 100분의 1), vmax(너비, 높이 큰쪽의 100분의 1)
- 색상 표현 단위 : HTML COLOR CODES 참조

Box는 콘텐트(Content) - 요소의 텍스트나 이미지 등의 실제 내용이 위치하는 영역(width, height), 패딩(Padding) - 테두리(Border) 안쪽에 위치하는 요소의 내부 여백 영역. 패딩 영역의 두께를 의미, 테두리(Border) - 테두리 영역. 테두리의 두께 , 마진(Margin) - 테두리(Border) 바깥에 위치하는 요소의 외부 여백 영역. 마진 영역의 두께 / 으로 구성 -> 브라우저는 박스 모델의 크기(dimension)와 프로퍼티(색, 배경, 모양 등), 위치를 근거로 하여 렌더링을 실행
웹디자인 = 콘텐츠를 담을 박스 모델을 정의하고 CSS 프로퍼티를 통해 스타일(배경, 폰트와 텍스트 등)과 위치 및 정렬을 지정하는 것

HTML과 CSS의 연동
-Link style : HTML에서 외부에 있는 CSS 파일을 로드. 가장 일반적으로 사용
-Embedding style : HTML 내부에 CSS를 포함시키는 방식. 권장 X
-Inline style : HTML요소의 style 프로퍼티에 CSS를 기술하는 방식. JavaScript가 동적으로 CSS를 생성할 때 사용
Reset CSS 사용 : 본적인 HTML 요소의 CSS를 초기화하는 용도로 사용, 브라우저 별로 제각각인 디폴트 스타일을 하나의 스타일로 통일 ex)Eric Meyer’s reset, normalize.css
