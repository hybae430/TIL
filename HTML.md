# HTML

> 웹 컨텐츠의 의미와 구조를 정의할 때 사용하는 언어
>
> "Hyper Text Markup Language"



## HTML 기초

- **Hyper**: 텍스트 등의 정보가 다중으로 연결되어 있는 상태
- **Hyper Text**: 참조(하이퍼링크)를 통해 사용자가 한 문서에서 다른 문서로 즉시 접근할 수 있는 텍스트
  - Http, Html은 하이퍼텍스트가 쓰인 대표적인 기술
- **Markup Language**: 특정 텍스트에 역할을 부여하는(마킹하는) 언어
  - ex) h1 태그는 단순히 글자가 커지는 것이 아니라, 그 페이지에서 가장 핵심 주제를 표시하는 것



## HTML 기본 구조

**DOM (Document Object Model)**

- DOM은 문서의 구조화된 표현(structured representation)을 제공하며 프로그래밍 언어가 DOM 구조에 접근할 수 있는 방법을 제공하여 그들이 문서 구조, 스타일, 내용 등을 변경할 수 있게 도움
- DOM은 동일한 문서를 표현하고, 저장하고, 조작하는 방법을 제공
- 웹 페이지의 객체 지향 표현

**요소 (Element)**

- HTML 요소는 시작 태그와 종료 태그, 그 사이에 위치한 내용으로 구성
  - 태그(Tag)는 내용을 감싸 그 정보의 성격과 의미를 정의한다.
  - 태그는 <p>, </p> 자체를 가리킴(요소와 다르다!)
- 내용이 없는 태그들: br, hr, img, input, link, meta
- 요소는 중첩될 수 있으며 이러한 중첩들로 하나의 문서를 완성해나간다.
  - 이 때 HTML은 오류를 띄우지 않고 그냥 레이아웃이 깨지기 때문에 태그의 쌍을 잘 맞추지 않으면 디버깅이 좀 더 힘들다.

**속성 (Atrribute)**

- 태그의 부가적인 정보이다.
- 속성은 요소에 추가 정보(이미지 파일의 경로, 크기 등)를 제공한다.
- 요소의 시작 태그에 위치해야 하며 **이름**과 **값**의 쌍을 이룬다.
- 태그와 상관없이 사용 가능한 속성들(html global attribute)도 있다.



## 시맨틱 태그 (Semantic Tag)

> 브라우저, 검색엔진, 개발자 모두에게 콘텐츠의 의미를 명확히 설명하는 태그

**장점**

1. 읽기 쉬워진다. (개발자)
   - 개발자가 의도한 요소의 의미가 명확히 드러나기 때문에 코드의 가독성이 높아지고 유지보수가 쉬워진다.
2. 접근성이 좋아진다. (검색엔진 및 보조기술 → 시력장애용 스크린리더 → 더 나은 경험 제공)
   - 검색 엔진이 HTML을 잘 이해하도록 시맨틱 태그 사용이 권장된다.

**시맨틱 웹**

- **"의미론적인 웹"**이라는 뜻으로, 기계가 이해할 수 있는 형태로 제작된 웹을 의미한다.
- 기계가 사람을 대신해서 웹 페이지의 정보를 이해하고, 우리에게 필요한 정보만 보여주거나 정보를 가공해서 우리가 필요로 하는 형태로 제공하는 것을 의미한다.