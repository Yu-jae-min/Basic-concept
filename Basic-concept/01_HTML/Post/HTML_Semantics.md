# # HTML Semantics

## # 시맨틱 웹(Semantic Web)

시맨틱(Semantic)은 "의미의, 의미론적인"이라는 뜻이며 시맨틱 웹(Semantic Web)은
웹에 존재하는 수많은 웹페이지들에 메타데이터(Metadata)를 부여하여, 기존의 잡다한 데이터 집합이었던 웹페이지를 ‘의미’와 ‘관련성’을 가지는 거대한 데이터베이스로 구축하고자 하는 발상이다. HTML 요소는 non-semantic 요소, semantic 요소로 구분할 수 있다.

- **non-semantic 요소**

  div, span 등이 있으며 이들 태그는 content에 대하여 어떤 설명도 하지 않는다.

- **semantic 요소**

  form, table, img 등이 있으며 이들 태그는 content의 의미를 명확히 설명한다.

<br>
<br>

## # 시맨틱 태그(Semantic Tag)

<br>

HTML5에 도입된 시맨틱 태그는 개발자와 브라우저에게 의미있는 태그를 제공한다.

```html
<font size="6"><b>Hello</b></font>
<h1>Hello</h1>
```

1행과 2행의 요소는 같은 결과를 출력하지만 1행은 폰트의 크기와 굵기를 지정하는 메타데이터만을 브라우저에게 알리고 있다. 하지만 2행의 h1 태그는 제목 태그 중 가장 상위 레벨이라는 의미를 내포하고 있어 개발자의 의도를 명확하게 나타내고 있다. 이것은 코드의 가독성을 높이고 유지보수를 쉽게한다.

h1 태그와 같이 시맨틱 요소로 구성되어 있는 웹페이지는 검색엔진에 보다 의미론적으로 문서 정보를 전달할 수 있고 검색엔진 또한 시맨틱 요소를 이용하여 보다 효과적인 크롤링과 인덱싱이 가능해졌다. 즉, 시맨틱 태그란 브라우저, 검색엔진, 개발자 모두에게 콘텐츠의 의미를 명확히 설명하는 역할을 한다. 시맨틱 태그에 의해 컴퓨터가 HTML 요소의 의미를 보다 명확히 해석하고 그 데이터를 활용할 수 있는 시맨틱 웹이 실현될 수 있다.

즉 개발자는 비지니스를 위한 검색엔진 최적화(SEO: Search Engine Optimization)를 고려하며 사용자들에게 많은 노출을 하기 위해 시맨틱 태그를 사용하는 것이다.

- **크롤링**

  검색엔진의 로봇이라는 프로그램을 이용해 매일 전세계의 웹사이트 정보를 수집하는 것

- **인덱싱**

  크롤러가 수집한 자료를 분류 및 색인작업하는 것. 이 때 수집한 자료는 결국 웹사이트의 HTML코드이며 검색엔진은 HTML코드 만으로 그 의미를 인지하여야 하는데 이때 시맨틱 요소를 해석

시맨틱 태그의 종류는 아래와 같다.

- article
- aside
- details
- figcaption
- figure
- footer
- header
- main
- mark
- nav
- section
- summary
- time

<br>

## # img 태그와 background-image 속성

- **img 태그**

  alt속성을 통해 이미지가 어떠한 의미를 담고 있거나, 이미지가 컨텐츠의 중심으로써 가장 중요하여 검색엔진 최적화를 고려해야할 경우 활용한다.

- **background-image 속성**

  아무런 정보를 담지 않은 순수 디자인의 목적만을 가질 경우 활용한다.

<br>

---

<br>

참고자료

1. <a href="https://poiemaweb.com/html5-semantic-web" target='_blank'>시맨틱 요소와 검색 엔진</a>
2. <a href="https://stackoverflow.com/questions/492809/when-to-use-img-vs-css-background-image" target='_blank'>스택오버플로우</a>
