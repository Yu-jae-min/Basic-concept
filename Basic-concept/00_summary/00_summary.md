## # HTML

### # 시멘틱 태그와 SEO

- 시멘틱 태그란?

  시멘틱은 의미론적이라는 단어이며 의미가 있는 태그를 얘기한다. 예를 들어 div같은 경우에 태그 이름만으로 컨텐츠를 유추하기 어렵지만
  header, nav, footer와 같은 태그는 태그 이름만으로도 컨텐츠를 유추할 수 있다. 또 검색 엔진은 태그를 기반으로 페이지 내 검색 키워드의
  우선 순위를 판단하게 되므로(검색엔진의 랭킹 과정) SEO 측면에서도 시멘틱 태그를 사용하는 것이 좋고 시각장애가 있는 사용자에게
  스크린 리더를 사용하여 웹 접근성을 높여줄 수 있는데 시멘틱 태그가 스크린 리더 활용에도 도움이 된다고 한다.
  그렇기 때문에 시멘틱 태그를 사용하여 시멘틱 마크업을 하는 것은 여러 면에서 중요하다.

- 웹 접근성

  - 웹 접근성이란?

    장애인, 고령자 등이 웹 사이트에서 제공하는 정보에 비장애인과 동등하게 접근하고 이해할 수 있도록 보장하는 것이다. 시각, 운동성, 청각, 발작, 인지 등을 고려해야한다.
    웹 접근성에 도움을 주는 기능으로는 스크린 리더, 화면 확대 도구, 음성 인식, 키보드 오버레이 등이 있다.

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
  또 이런 방식으로 동작하게 된다면 DOM 트리가 생성되기전에 로드 된 자바스크립트가 실행되면서 생성되지도 않은 DOM의 조작을 시도하는 문제가 발생할 수도 있다.
  그렇기 때문에 script태그는 body 태그 최하단에 위치하는게 좋다. 만약 script 태그를 꼭 상단에 위치시켜야 한다면 async나 defer 키워드를 통해 문제를 해결할 수 있다.
  async는 html 파싱 과정 중 비동기적으로 js 파일을 다운로드 받고 html 파싱 완료 여부와 관계없이 js 파일을 실행한다.
  반면 defer은 html 파싱 과정 중 비동기적으로 js 파일을 다운로드만 받고 html 파싱 완료 후 js 파일을 실행한다.
  defer이 가장 좋은 옵션이다.

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
2. 인라
3. id
4. class
5. 태그이름(ex div)

<br>

### # 네이밍 설계 규칙 BEM 방식

- BEM은 Block, Element, Modifier를 뜻하며 이 세 가지를 활용하여 목적의 명확성, 재사용성, 클래스 충돌 방지를 위해 사용하는 규칙이다.
  `__`, `--`로 구분하며 재사용과 확장을 위해 id를 사용하지 않고 class만 사용한다.
  Block은 독립적으로 재사용 가능한 기본 단위 (ex button, card, form), Element는 Block 내부의 구성 요소 (ex `button__icon`, `form__label`),
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

<br>

### # 이미지 리플레이스먼트(Image Replacement)

- 이미지 리플레이스먼트(Image Replacement) 기법이란?

  이미지 리플레이스먼트(Image Replacement) 기법은 스크린 리더 사용자들을 위한, 이미지를 대신하는 대체 텍스트를 제공하는 기법으로 웹 접근성 준수하기 위해 사용하는 기법이다. img 태그에 alt과 같은 목적으로 사용한다. 만약 background-img와 같이 사용되는 경우 대체 텍스트가 없기 때문에 이미지 리플레이스먼트(Image Replacement) 기법을 통해 대체 텍스트를 제공해주어야한다. 단 스크린 리더 사용자들을 위한 텍스트이므로 일반 사용자들에게 보여지지 않도록 숨겨주어야한다. text-indent 속성을 활용한 방법, 추가 태그와 z-index 속성을 활용한 방법, clip 속성을 활용한 방법등이 있다. 주의할 점은 display none, 요소 크기 0, opacity 0 등의 방법은 스크린 리더가 읽을 수 없으므로 사용하지 않아야한다.

- 이미지 리플레이스먼트(Image Replacement) 기법 적용 방법 (텍제클)

  (1) text-indent 활용 : text-indent 속성(들여쓰기)을 -9999px로 주어 화면 밖으로 텍스트를 날리는 방법

  (2) z-index 활용 : 추가 태그(span)를 사용하고 position relative와 z-index -1로 설정하여 이미지 아래로 텍스트를 숨기는 방법

  (3) clip 속성 활용 : position을 absolute로 설정한 뒤 width와 height를 1px로 주고 화면 상 숨기기 위해 margin -1px을 설정하고 overflow hidden을 설정한다. 그 후 클리핑 범위를 0으로 설정하여 숨겨버린다.

<br>

### # 브라우저 스펙 차이에 따른 스타일링 이슈 처리

- 브라우저마다 렌더링 엔진이 달라 디폴트 스타일이 다르기 때문에 reset.css 파일을 이용하여 모든 디폴트 스타일을 초기화한 후 프로젝트를 진행한다.
  reset 파일 내부에서 태그별 기본 margin, padding, border 등을 제거해주거나 list-style 혹은 line-height 등을 기본 값으로 할당한다.
  또한 css 속성 사용 시 호환되는 브라우저를 확인한 후 사용한다.

<br>

### # CSS(Cascading Style Sheets)에서 Cascading에 의미

- 케스케이딩은 흐르는, 종속하는 의미를 가지고 있고 어떤 스타일로 브라우저에 표현할 지 결정해주는 시스템을 의미한다.
  케스케이딩 시스템을 사용하였을 때의 장점은 부모 요소의 스타일이 자식 요소에게 상속되는 점을 활용하여 부모 요소에 적절한 스타일을
  부여할 경우 되므로 코드의 양을 줄여 성능 향상에 기여할 수 있다. 일반적으로 박스 모델과 관련된 속성(margin, padding, border, witdh, height 등)은
  상속되지 않고 폰트와 관련된 속성(color, font-family, font-size, text-align 등)들은 상속된다.
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

  기계어와 일대일 대응이 되는 컴퓨터 프로그래밍의 저급 언어이다. 기계어는 사람이 이해하기 어렵기 때문에 기계어를 사람이 이해할 수 있게 하기 위해 어셈블리어가 등장했다.
  하지만 기계어는 CPU 제조사나 버전에 따라 다르기 때문에 그에 대응되는 어셈블리어도 각각 다르다는 문제가 발생했다.
  이 때문에 통일된 언어체계로 작성한 코드의 필요성이 대두되고, 여기서 고급 프로그래밍 언어가 나오게 된다.
  또한 고급 프로그래밍 언어를 CPU가 해석할 수 있는 기계어로 번역해주는 것이 컴파일러와 인터프리터이다.

- 컴파일러 인터프리터 차이

  | 특징      | 컴파일러                                       | 인터프리터                                   |
  | --------- | ---------------------------------------------- | -------------------------------------------- |
  | 번역 단위 | 전체 소스를 한 번에 기계어로 변환              | 소스를 한 줄씩 읽고 즉시 실행                |
  | 실행 속도 | 실행 속도 빠르다 (이미 기계어로 변환되어 있음) | 상대적으로 느리다 (실행 시 즉시 해석)        |
  | 실행 파일 | 실행 파일 생성됨 (예: .exe)                    | 생성되지 않음 (바로 실행됨)                  |
  | 에러 발생 | 전체 코드 분석 후 에러 보고                    | 에러가 발생하면 그 이후 코드는 실행되지 않음 |
  | 대표 언어 | C, C++, Go (Java는 컴파일 + JVM 실행) 등       | Python, Ruby, 전통적인 JS 등                 |

- 자바스크립트는 컴파일러일까 인터프리터일까?

  자바스크립트는 원래 인터프리터 언어로 출발했지만 유저 인터렉션이 점점 늘어나고 애플리케이션의 구조가 커지게 되며 실행 속도를 빠르게 개선하기 위해
  V8엔진이 등장했고 V8엔진은 JITC(Just In Time Compiler)인 터보팬(TurboFan)과 이그니션 인터프리터(Ignition)를 함께 사용하는 하이브리드 방식으로 동작한다.
  V8엔진은 반복 수행 정도에 따라 유동적으로 다른 최적화 방식을 사용하여 실행 속도를 높인다.

- V8엔진의 JITC(Just In Time Compiler)

  1. 자바스크립트 엔진 V8엔진에 JS 파일(JS 코드)을 넘긴다.

  2. 파서가 소스 코드를 분석하여 추상 구문 트리(AST) 생성한다.

  3. 이그니션(Ignition) 인터프리터가 추상 구문 트리(AST)를 바이트 코드(중간 코드)로 변환하고 실행한다.

  4. 실행 과정 중 프로파일러가 프로파일링을 통해 자주 반복 실행되는 과열 지점(hot spot)을 찾는다.

  5. 과열 지점(hot spot)을 찾게 되면 해당 코드를 터보팬 컴파일러(TurboFan)으로 전달되어 최적화된 기계어로 컴파일한다.

<br>

### # 바이너리 코드, 기계어, 바이트 코드

- 바이너리 코드

  바이너리 코드는 컴퓨터(CPU)가 인식할 수 있는 0과 1로 구성된 이진코드 혹은 데이터

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

- window 객체는 웹 브라우저에서 브라우저 창을 나타내는 객체이다. 또 최상위 객체이기 때문에 전역 객체라고도 하며 자바스크립트의 모든 객체, 전역 함수, 전역 변수들은
  자동으로 window 객체의 프로퍼티가 된다. window 객체는 브라우저 환경에서만 존재하며 Node.js와 같은 다른 자바스크립트 환경에서는 window 객체가 존재하지 않는다.

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
  HTMLElement는 Element의 자식이고 Element는 Node의 자식이다. Node는 Object의 자식이다. 이러한 관계를 DOM Tree라고 한다.
  특정 Element를 지정하는 것은 텍스트 노드를 제외하고, 흔히 생각하는 태그만 가리키는 것이다. (`ex) <a>하이</a>의 경우 'a' 태그`)

- HTMLCollection 객체

  Element들의 컬렉션, Live 객체(노드 변경 반영 O, 동적 상태), 예를 들어 3개의 li를 생성해놓고 이 li를 HTMLCollection를 반환하는
  getElementsByClassName로 선택 후 for 반복문을 통해 색상을 변경하려고 할 때 첫번째, 세번째 li만 색상이 바뀐다.
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

  브라우저마다 렌더링 엔진이 다르기 때문에 렌더링 되는 결과물에 차이가 있을 수 있는데 이 때 모든 브라우저에서 화면을 동일하게 보이게 하는 것이
  아닌 모든 브라우저에서 동등한 수준의 정보, 기능 제공을 할 수 있도록 하는 것을 목표로 하는 방법론

- 크로스 브라우징 대응 방법 예시

  1. 타깃 설정 : 모든 브라우저 대응이 어려운 경우 구글 어낼리틱스나 navigator 객체의 userAgent를 통해 서비스를 사용하는 사용자의 기기를 확인 후 많은 점유를 차지하는 기기 순서대로 대응하였다.

  2. 호환성 확인 : 메소드, 스타일 속성 사용 시 Can I Use와 같은 사이트를 통해 브라우저 호환성 체크

  3. 스타일 초기화 : 프로젝트 세팅 시 브라우저 마다 차이가 있는 기본 스타일 값을 초기화 시켰다.

  4. 바벨 사용 : 바벨의 플러그인이나 프리셋을 활용하여 자바스크립트 최신 문법을 하위 문법으로 트랜스파일링한다.

  5. 폴리필 사용 : 지원하지 않는 메소드의 경우 폴리필 코드를 통해 메소드를 직접 추가한다.

  6. CSS 벤더 프리픽스 사용 (`ex -webkit-display: flex, -moz-display: flex`) : 벤더 프리픽스를 활용하였다.

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
  Web API에서 처리된 후, 그 결과(콜백)는 태스크 큐에 등록되고, 자바스크립트 엔진의 콜 스택이 비워졌을 때 이벤트 루프가 이를 꺼내 콜 스택에 전달하여 실행함으로써
  싱글 스레드 환경에서도 마치 멀티 스레드처럼 비동기 처리가 가능해진다. 이 때 비동기의 문제점은 비동기 요청 시 메인 스레드의 작업 또한 수행되고 있기 때문에
  비동기 요청이 완료되기 전 비동기 요청이 반환하는 결과 값에 접근하게 되면 undefined나 에러를 발생시킬 수 있다.
  그렇기 때문에 콜백 패턴, Promise, async/await 문법을 활용한 비동기 처리를 통해 비동기 API 처리 시점을 명확하게 한 후 후속 처리를 해야한다.
  Promise는 pending(대기), fulfilled(이행), rejected(거부) 세 가지 상태를 가지며, .then(), .catch(), .finally() 등의 메서드를 통해 후속 처리를 정의할 수 있다.
  하지만 콜백 패턴은 예외 처리의 어려움과 함수의 중첩으로 인해 가독성과 유지보수성이 떨어지는 콜백 지옥(callback hell)을 유발할 수 있다.

  - Promise는 내부적으로 class처럼 동작하는 생성자 함수다. 즉, constructor 함수이기 때문에 new 키워드로 호출해야만 인스턴스를 만들 수 있다.
  - 생성자 함수란 객체를 만들기 위한 함수이다. 쉽게 말해 어떤 틀(템플릿) 역할을 해서 그걸로 여러 개의 객체(인스턴스)를 찍어낼 수 있다.

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

  - 표준 빌트인 객체 (Standard Built-in Objects) : ECMAScript 사양에 정의된 객체들. Object, Array, Function, Date, Math, JSON, Error, Promise 등
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

- 자바스크립트 언어의 문법을 보다 엄격히 적용하여 오류를 발생시킬 가능성이 높거나 자바스크립트 엔진의 최적화 작업에 문제를 일으킬 수 있는 코드에 대해
  명시적인 에러를 발생시킨다. 전역에서 선언하면 모든 소스코드가 대상이고, 로컬(함수 내부)로 선언하면 함수 내에서만 대상이 된다.
  use strict 모드에서는 삭제가 불가능한 프로퍼티를 삭제하거나 함수의 매개변수를 중복해서 사용하는 것 등이 금지된다. 
  use strict 모드를 사용하면 엄격한 동작으로 코드 작성 단계(컴파일 타임)에서 에러를 사전에 발견할 수 있다는 장점과 디버깅이 쉬워진다는 장점이 있다.
  하지만 단점의 경우 대부분의 브라우저가 use strict 모드를 지원하지만 아주 오래된 브라우저의 경우 엄격 모드의 코드가 다른 방식으로 동작할 수 있다.

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

### # ECMAScript 와 JavaScript 의 차이

- ECMA 인터내셔널이라는 비영리 표준화 기구에서 정보 통신에 대한 표준을 제정하는데 ECMAScript는 ECMA 인터내셔널이 명세한 스크립트 언어를
  어떻게 만들어야 하는지를 설명하는 일종의 표준화 설명서이고, JavaScript는 ECMAScript의 사양을 바탕으로 만들어진 언어이다.

<br>

### # 순수 함수

- 순수 함수란

  1. 동일한 인자 전달 시 항상 동일한 값 반환

  2. 외부에 영향을 주거나 받지 않음

  3. 사이드 이펙트가 발생하지 않음

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

  자신의 스코프에서 참조하고자 하는 식별자를 찾은 후 존재하지 않는다면 상위 스코프로 올라가며 마지막 최상위 스코프까지 순차적으로 식별자를 찾게 된다.
  이와 같이 자신의 스코프부터 최상위 스코프까지 스코프가 연결되어 있는 형태를 스코프 체인이라고 한다.

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

  ```jsx
  // 브라우저에서 "테스트"라는 텍스트를 클릭했을 때 span이 event.target
  // 실제 클릭되는 요소는 버튼이 아닌 "테스트"라는 텍스트
  <button onClick={onClick}>
    <span>테스트</span>
  </button>
  ```

  2. event.currentTarget : 이벤트 리스너가 달린 요소

  ```jsx
  // 브라우저에서 "테스트"라는 텍스트를 클릭했을 때 button이 event.currentTarget
  // 실제 클릭되는 요소는 버튼이 아닌 "테스트"라는 텍스트지만, 이벤트 리스너는 버튼에 달려있음
  <button onClick={onClick}>
    <span>테스트</span>
  </button>
  ```

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

  ```js
  <button id="myBtn">Click me</button>;

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

  변수 선언조차 되지 않은 상태, 타입 undefined

- null

  의도적인 빈 값, 타입 객체

<br>

### # **IntersectionObserver에 대해서 아는지, 그리고 사용해봤는지**

<br>

- IntersectionObserver는 WebAPI로 비동기적으로 실행되며 관찰 대상과 뷰포트의 교차점을 관찰하고 뷰포트 안으로 들어오는 시점에 정보를 제공하는 기능을 하는 것으로 알고 있다. 사용해본 경험은 없지만 무한 스크롤이나 페이지 스크롤 시 다른 컨텐츠나 이미지 레이지 로딩 등에 사용되는 것으로 알고 있다.

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

### # **Object Literal, Template Literal**

<br>

- Template Literal이란?

  Template Literal은 벡틱으로 감싸 사용하는 문자열 표기법이다. 다른 문자열이나 객체 등을 편리하게 결합하여 사용할 수 있다.

<br>

- Object Literal이란?

  Object Literal은 중괄호 안에 프로퍼티를 정의하여 객체를 생성한다. 손쉽게 객체를 생성하기 위해 사용한다.

<br>

### # **얕은 복사와 깊은 복사**

<br>

- 얕은 복사와 깊은 복사란?

  얕은 복사란 객체를 복사할 때 객체만 복사하여 기존 객체와 복사된 객체가 같은 참조를 가리키는 복사를 말한다. 깊은 복사란 객체를 복사할 때 객체와 참조 값을 모두 복사하여 기존 객체와 복사된 객체의 참조가 완전히 끊어진 복사를 말한다. 자바스크립트에서 값은 원시값과 참조값 두 가지 데이터 타입의 값이 존재한다. 자바스크립트에서 원시 타입의 경우 값이 수정(새로운 값 할당)되면 새로운 메모리 공간에 독립적인 값을 저장하기 때문에 깊은 복사가 되고 참조 타입의 경우 값이 수정(새로운 요소 추가)되면 원본을 직접 수정하므로 얕은 복사가 된다. 얕은 복사의 경우 메모리를 새로 할당받지 않아 메모리 공간을 아낄 수 있지만 원본이 변화될 수 있는 위험이 있고 깊은 복사는 메모리 공간을 새로 할당받아 메모리 공간을 소비하지만 원본이 변화되지 않아 안전하다.

<br>

- 얕은 복사 방법 (슬오스)

  (1) slice() : 기본적으로 얕은 복사를 수행한다. 1차원 배열을 복사하면 깊은 복사처럼 보이는데 원시 타입은 기본적으로 깊은 복사이므로 깊은 복사처럼 보인다. 하지만 2차원 배열을 복사하면 얕은 복사가 된다.

  (2) Object.assign() : 1차원 객체는 깊은 복사, 2차원 객체는 얕은 복사

  (3) Spread 연산자 : 1차원 객체는 깊은 복사, 2차원 객체는 얕은 복사

<br>

- 깊은 복사 방법 (제로)

  (1) JSON.parse(JSON.stringify(obj))

  (2) Lodash 라이브러리의 cloneDeep 메소드

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

<br>

### # **0.2 + 0.1 의 결과 값이 왜 이상한가?**

<br>

- 보통 계산 할때 사용하는 10진법과 달리 컴퓨터는 2진법으로 동작하는데, 몇몇 소수는 10진법에서 2진법으로 변환하는 과정에서 무한 소수가 되어버린다.
  저장공간에 한계가 있는 컴퓨터는 무한 소수를 유한 소수로 바꾸게 되는데, 이 과정에서 미세한 오차가 발생해서 오류가 발생한 것이다.
  이러한 오차를 부동 소수점 연산 오차라고 한다. 이러한 문제를 해결하기 위해서는 bigNumber와 같은 라이브러리를 활용하여 계산할 수 있다.

<br>

### # **함수 선언식 표현식 설명**

<br>

- 함수 선언식

  (1) 함수 선언을 function으로 시작하는 함수

  (2) 함수명이 정의되어 있어야 함

  (3) 호이스팅 발생

  ```javascript
  function 함수명() {
    구현 로직
  }
  ```

<br>

- 함수 표현식

  (1) 정의한 function을 별도의 변수에 할당한 함수

  (2) 익명 함수 사용 가능

  (3) 선언부만 호이스팅 되므로 호이스팅의 영향을 받지 않음

  ```javascript
  var 함수명 = function () {
    구현 로직
  };
  ```

<br>

### # 클래스가 무엇인가?

<br>

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

### # **원시형 타입과 참조형 타입에 대해서 이야기 해달라**

<br>

- 원시형 타입 (스넘불언널브심)

  String, Number, Boolean, Undefined, Null, BigInt, Symbol

<br>

- 참조형 타입 (객배)

  원시 타입을 제외한 나머지, 객체나 배열 등이 대표적이다.

<br>

- BigInt 타입

  Number 타입은 2의53승-1만큼의 정수만 안전하게 표현가능하지만 BigInt 타입은 길이의 제약 없이 정수를 다룰 수 있게 해주는 숫자형이다.
  정수 뒤에 n을 붙여 사용하거나 BigInt를 호출하여 인자로 숫자를 넘겨줄 수 있다. 나누기에 경우 소수점 없이 정수만 반환한다.

<br>

### # **CDN(Content Delivery Network)이란?**

<br>

- 콘텐츠를 효율적으로 전달하기 위해 넓은 지리적 영역에 분산된 서버에 데이터를 저장해 사용자에게 전달하는 시스템이다. 사용자에게 요청이 왔을 때 요청 위치로부터 가장 가까운 서버에서 데이터를 전송해주는 것이다. HTML, CSS, JavaScript, Image 파일 등을 전송할 수 있다. CDN을 사용하는 이유는 분산된 서버를 통해 서버의 트래픽 부하를 줄일 수 있고 호스팅 비용이 절감되고, 물리적으로 가까운 서버에 요청하므로 응답이 빠르며, 디도스(의도적으로 트래픽을 폭주시켜 해당 시스템의 서비스가 거부되도록 하는 공격) 공격과 같은 일부 악의적인 공격으로부터 상대적으로 안전하다. 로드 밸런서와 유사하다고 볼 수 있지만 CDN의 주요 목적은 넓은 지리적 영역에 컨텐츠를 분산시키는 것이지만, 로드 밸런서의 주요 목적은 지리적으로 근접한 서버 네트워크에 트래픽을 분산시키는 것이다. CDN 사용 방법은 script 태그 src 프로퍼티에 CDN URL을 입력하여 적용시키거나 AWS Cloudfront를 사용하여 적용시킬 수 있다.

<br>

### # **실행컨텍스트**

<br>

- 실행 컨텍스트란?

  실행 컨텍스트란 코드 실행에 필요한 환경을 저장해놓은 객체이다. 전역 컨텍스트와 함수 컨텍스트로 구분할 수 있고 자바스크립트 엔진에 콜스택에 쌓이게 된다.
  실행 컨텍스트의 생성 과정을 설명하기 전 일단 자바스크립트 런타임의 구조는 자바스크립트 엔진의 콜스택, 메모리 힙과 브라우저의 Web API, 테스크 큐, 이벤트 루프로 구성되어 있다. 전역 컨텍스트는 프로그램이 시작될 때 바로 생성된다. 즉 콜스택에 전역 컨택스트가 바로 쌓이게 되는 것이다.
  실행 컨텍스트는 기본적으로 생성과 실행 단계로 나누어 생성된다. 생성 단계에서 환경 레코드에 식별자 정보를 저장, 스코프 체인 형성, this 바인딩을 수행하고 실행 단계에서 코드를 위에서부터 한줄 씩 실행하게 되는 것이다. 이 때 식별자에 값을 할당하게 된다. 만약 실행 단계에서 함수 호출 문을 만나게 되면 전역 컨텍스트에 실행 단계를 멈춘 뒤 새로운 함수 컨텍스트를 콜스택에 쌓는다. 그 후 새롭게 쌓인 함수 컨텍스트로 제어권을 넘긴 뒤 생성 단계와 실행 단계를 거치게 된다. 이렇게 생성 단계와 실행 단계를 반복하며 콜스택이 비워지는 경우 이벤트 루프가 확인하여 WebAPI를 통해 실행되어 테스크 큐 쌓인 비동기 콜백 함수 선입선출 방식으로 밀어넣게 된다. 이 때 한번에 다 밀어넣는 것이 아닌 하나를 밀어넣고 하나가 실행되어 콜스택이 비어질 때 또 하나를 밀어넣는 방식으로 수행된다.

<br>

- 실행 컨텍스트 구조 (콜메웹테이)

  (1) 콜스택 : 실행 컨텍스트를 저장하는 자료 구조이며 원시 타입의 데이터가 저장된다.

  (2) 메모리 힙 : 참조타입(객체 등) 데이터가 저장되며 구조적이지 않다.

  (3) WebAPI : 웹 브라우저에서 제공하는 API로 AJAX나 Timeout등의 비동기 작업을 실행한다.

  (4) 테스크 큐 : WebAPI에서 넘겨받은 콜백 함수를 저장하며 선입선출 방식이다.

  (5) 이벤트 루프 : 콜스택이 비어있다면 테스크 큐의 작업을 콜스택으로 밀어넣는다.

<br>

### # **이터러블, 이터레이터와 제너레이터**

<br>

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

<br>

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

### # **HTML 렌더링 중 js가 실행되면 렌더링이 멈추는데 그 이유는?**

<br>

- HTML 파서는 스크립트 태그를 만나게되면 렌더링 제어 권한을 자바스크립트 엔진으로 넘겨주게 되고, 문서를 파싱하는 과정을 중단한다. 자바스크립트의 엔진의 권한이 끝나면 렌더링 과정으로 다시 돌아가서 중단된 시점부터 다시 파싱을 시작한다. 이러한 원리로 스크립트 태그는 바디 끝에 위치하도록 권장한다. 하지만 부득이하게 스크립트 태그를 상단에 위치시켜야하는 경우 스크립트를 비동기적으로 다운로드할 수 있는 async나 defer키워드를 사용한다. 두 가지의 차이점은 async는 스크립트를 다운로드 완료 후 바로 실행하고 defer은 HTML 로드가 완전히 다 완료된 후 실행하므로 defer을 사용하는 것이 좋다.

<br>

### # CJS(CommonJS)의 require과 ESM(ECMAScript Modules)의 import의 차이점

<br>

- 초창기 javascirpt의 경우 모듈 시스템이 없기 때문에 한 파일에 모든 기능을 담았다. 그렇기 때문에 가독성이 현저히 떨어지고 파일 분리 시 동일 변수를 참조하는 문제 등이 발생했다. 그래서 등장한 것이 javasipcrt를 별도의 모듈로 관리하기 위한 모듈 시스템이고 대표적인 모듈 시스템으로 CJS와 ESM이 있다. require와 import는 외부 파일이나 라이브러리를 불러올 때 사용하는 모듈 키워드이다. CJS는 node.js에서 채택해서 사용하고 있는 모듈 시스템이고 ESM은 ES6부터 추가된 js 표준 모듈 시스템이다.

  (1) 내보내기 : cjs는 module.exports 또는 exports.모듈이름, esm은 export 또는 export default를 사용

  (2) 가져오기 : cjs는 require로 모듈을 불러오는데 require의 인자로 불러올 모듈 지정, esm은 import로 모듈을 불러오는데 import에 from이나 as 키워드로 불러올 모듈 지정

  (3) 가져오기 위치 : cjs의 require는 어느 지점이나 상관 없음, esm의 import는 파일의 시작 부분에서만 실행 가능하지만 비동기로 개선 가능

  (4) 트리쉐이킹 여부 : 트리쉐이킹은 번들링 시 패키지 내부의 필요한 코드만 가져오고 필요없는 코드를 제거하여 최적화하는 기법을 말한다. 즉 번들 사이즈를 줄일 수 있다. 단 트리쉐이킹은 ESM을 사용하는 패키지에 대해서만 적용된다. 적용되지 않는다면 사용 중인 패키지가 ESM 구문을 사용하여 메서드를 내보내는지 확인해야한다. 주의할점은 바벨 사용 시 ESM의 import가 CJS의 require로 변환되어 트리쉐이킹이 되지 않을 수 있다. 이렇게 동작하는 이유는 ESM은 컴파일 타임에 모듈을 로딩하기 때문에 트리쉐이킹이 가능하고 CJS는 런타임에 모듈을 로딩하기 때문에 트리쉐이킹이 불가능한 것으로 알고 있다.

  (5) 성능/메모리 : cjs의 require보다 esm의 import가 트리쉐이킹을 통해 필요한 부분만 로드할 수 있어 성능이 우수하고 메모리가 절약 됨

  ```js
  // require
  module.exports = moment;
  const moment = require("moment");

  // import
  export default moment;
  import moment from "moment";
  ```

<br>

### # **객체지향 프로그래밍 OOP에 대해 설명해달라(상속, 캡슐화, 추상화, 다형성)**

<br>

- 객체지향 프로그래밍(OOP, Object Oriented Programming)란?

  Object Oriented Programming이며 객체지향 프로그래밍이라고 한다. 상태나 행위를 가진 독립적인 여러 객체들을 레고 블럭처럼 조립하여 프로그래밍하는 방식을 말한다. 상속, 다형성, 캡슐화, 추상화 등의 특징과 모듈화를 통해서 재사용성을 증가시키고 유지보수가 용이하도록 한다.

<br>

- 객체지향 프로그래밍 특징 (상다캡추)

  (1) 상속 : 부모 객체의 메소드나 변수를 자식 객체가 그대로 물려받을 수 있다. 예를 들어 클래스에서는 상위 클래스의 클래스 필드를 하위 클래스가 상속받는다.

  (2) 다형성 : 같은 객체임에도 상황에 따라 다르게 동작할 수 있다. 예를 들어 함수는 매개변수에 따라 출력 값이 다르다.

  (3) 캡슐화 : 메소드나 변수를 하나로 묶고 필요에 따라 접근 권한을 나누어 외부에서 접근하지 못하게 제한을 두는 것을 말한다. 캡슐화를 통해 객체의 손상을 방지하고 정보를 은닉할 수 있다.

  (4) 추상화 : 연관된 메소드나 변수를 따로 묶어 표현한다. 예를 들어 동물이라는 변수에 강아지, 고양이를 배열에 담아 할당하는 것을 말한다.

<br>

- 현실에 상황을 예로 들어 OOP의 개념으로 설계과정을 설명해주시겠어요?

  빵집에는 여러가지 시스템이 있다. 빵을 만드는 시스템 고객의 결제를 도와주는 시스템 그리고 다양한 종류의 빵이 제공된다. 이 빵집에 비유해서 객체지향의 요소들을 설명해 보겠다. 먼저 빵의 종류는 굉장히 다양하지만 그 다양한 종류의 빵의 반죽 및 재료들을 각각의 종류별로 준비 할 수는 없다. 그래서 반죽과 재료의 베이스를 갖추고 필요한 재료들만 선택(호출)하여서 각기 다른 빵을 만든다(추상화) 대부분 빵집들은 고객이 직접 빵을 고른다.(public) 하지만 돈이 있는 계산대에는 함부로 접근하게 해서는 안된다.(pivate)(캡슐화) 빵집의 여러가지 빵들은 기본적으로 밀가루를 부풀려만든 것에 기반한다. 그 반죽에 다른 재료를 넣으면 다른빵이 되는것인데 모든 '빵'이라는 식품의 근간은 이 밀가루 반죽의 특징을 상속받았다고 볼 수 있다.(상속성) 단팥빵이 있다고 치자 이 평범한 단팥빵은 평소 단것을 굉장히 좋아하는 사람에게는 평범한 빵일 수 있지만 단것을 싫어하고 밋밋한 빵만 좋아하는 사람에게는 굉장히 달게 느껴질 수도 있다.(다형성)

<br>

- 객체지향 프로그래밍의 5가지 설계 원칙, SOLID (단개리인의) : 자바스크립트는 완전한 객체지향 언어가 아니므로 SOLID 적용이 어렵다.

  (1) 단일 책임의 원칙 : 모든 클래스는 각각 하나의 기능만 가진다.

  (2) 개방 폐쇄 원칙 : 클래스, 모듈, 함수 등 모든 구성요소는 확장에는 열려있고, 변경에는 닫혀있어야한다.

  (3) 리스코프 치환 원칙 : 부모 클래스의 자리에 자식 클래스를 넣어도 정상적으로 동작하여야 한다. 자식 클래스는 부모 클래스의 역할을 정확히 해내야한다는 뜻이다.

  (4) 인터페이스 분리 원칙 : 목적과 관심이 각기 다른 클라이언트(호출)가 있다면 인터페이스(메소드)를 통해 적절하게 분리한다는 원칙

  (5) 의존 역전 원칙 : 상위 모듈은 하위 모듈에 종속되면 안되고 하위 모듈은 상위 모듈에서 정의한 추상 타입에 의존해야 한다.

<br>

### # **함수형 프로그래밍(Function Programming)**

<br>

- 함수형 프로그래밍에 대해 설명해달라.

  함수형 프로그래밍은 순수 함수와 보조 함수의 조합을 통해 복잡한 로직 제거(조건문, 반복문) 및 변수 사용을 억제하여 상태 변경을 피하려는 프로그래밍 패러다임이다. 함수형 프로그래밍의 주요 특징으로는 순수 함수를 통한 불변성 유지, 고차 함수(함수를 인자로 전달받거나 함수를 결과로 반환하는 함수)나 재귀 함수를 통한 반복문 제거 등의 특징이 있다. 함수형 프로그래밍의 장점으로는 재사용성이 높고, 동작 예측이 쉽다는 장점이 있다.

<br>

- 함수형 프로그래밍에 개념에서 순수함수란 무엇인가?

  순수함수는 같은 입력이 주어지면, 같은 출력을 반환해야하는 함수를 말한다. 즉 사이드 이펙트가 없는 함수를 말한다.

<br>

- 객체지향 프로그래밍과 함수형 프로그래밍 차이

  객체지향 프로그래밍의 경우, 상호작용하는 객체들의 관계를 중심으로 코드 작성이 이루어진다. 그렇기 때문에 객체의 상태, 변수, 메서드 등이 긴밀한 관계를 가지고 있다.
  함수형 프로그래밍의 경우, 값의 연산 및 결과 도출 중심으로 코드작성이 이루어진다. 함수 내부에서 인자로 받은 값을 별도로 저장하거나 하지 않고 간결한 과정으로 처리하는 데에 주목적을 둔다.

<br>

### # **절차지향 프로그래밍(procedural programming)**

<br>

- 절차지향 프로그래밍이란?

  순차적인 처리가 중요시 되며 프로그램 전체가 유기적으로 연결되도록 만드는 프로그래밍 기법이다. 컴퓨터의 작업 처리 방식과 유사하기 때문에 객체지향 프로그래밍에 비해 처리가 빨랐지만 하드웨어의 발달로 인해 소프트웨어 개발 속도가 하드웨어의 처리 속도를 따라가지 못하는 상황이 발생하였다. 이로 인해 하드웨어의 성능을 깎아내리면서 소프트웨어 개발 속도를 빠르게 할 수 있는 객체지향 프로그래밍이 탄생하게 되었다. 절차지향 프로그래밍은 프로그램 전체가 연결되어 있기 때문에 유지보수가 어렵고 재사용성이 낮다. 객체지향 프로그래밍은 캡슐화, 상속, 다형성, 추상화 같은 특징으로 재사용성을 증가시키고 모듈화를 통해 유지보수를 용이하도록 하였다. 반면 어떤 모듈에 있는 하나의 기능만 필요하더라도 모듈 전체를 가져와야 하기 때문에 절차지향 프로그래밍보다 프로그램 사이즈가 더 커질 수도 있다.

<br>

- 절차지향 프로그래밍 VS 객체지향 프로그래밍 차이

  객체지향 프로그래밍이 절차지향 프로그래밍의 단점을 보완하기 위해 등장했지만 엄연히 다른 개념이다. 절차지향 프로그래밍의 경우 데이터를 중심으로 코드가 작성되며 객체지향 프로그래밍의 경우 상호작용하는 객체들의 관계를 중심으로 코드가 작성된다. 절차지향 프로그래밍이 실행 속도는 더 빠르지만 객체지향 프로그래밍이 유지보수가 용이하고 재사용성이 높다.

<br>

### # **자바스크립트의 Number Type은 다른 언어들과 차이점이 무엇인가, 왜 하나만 존재하는가**

<br>

- 자바스크립트의 넘버 타입은 정수(1, 2, 3..)와 실수(0.1, 0.2, 0.3..)를 따로 구분하지 않고 모든 수를 실수 하나로만 표현하며 64비트의 부동소수점을 이용해 프로그래밍에 필요한 모든 수 체계를 지원한다. 따라서 자바처럼 float, int 같은 별도의 타입 대신 number 하나로 표현할 수 있다.

<br>

### # **호스트 객체, 네이티브 객체**

<br>

- 호스트 객체

  호스트 객체는 호스트 환경에 정의된 객체를 말한다. 예를 들어 브라우저에서 동작하는 환경과 브라우저 외부에서 동작하는 환경의 자바스크립트(NodeJS)는 다른 호스트 객체를 사용할 수 있다. 브라우저에서 동작하는 환경의 호스트 객체는 전역객체인 window(BOM,브라우저 오브젝트 모델), DOM, XMR(XMLHttpRequest) 같은 객체가 있다.

<br>

- 네이티브 객체

  네이티브 객체는 ECMAScript 명세에 정의된 객체를 말하며 애플리케이션의 환경과 관계없이 항상 사용할 수 있다. 예시로 Object, String, Function, Array, RegExp, Date, Math와 같은 객체가 있다.

<br>

### # **기능 검출과 기능 추론**

<br>

- 기능 검출(Feature detection)

  스크립트가 호출하는 기능을 사용자의 브라우저가 지원하는지 체크하는 것이다. if('localStorage' in window){...}과 같이 localStorage 기능이 존재하는지 체크할 수 있다.

<br>

- 기능 추론(Feature inference)

  만약 기능을 브라우저가 지원한다면 다른 기능도 존재할 것이라고 추론하는 것이다. 예를 들어 localStorage 기능을 지원한다면 sessionStorage 기능을 지원 할 것이라고 추론하는 것이다.

<br>

### # 사용하는 디버깅 툴

<br>

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

- Object.entries : 객체의 키와 벨류를 배열로 반환한다. (ex { key1 : “value1”, key2 : “value2”} -> [["key1", "value1"], ["key2", "value2"]])

- Object.fromEntries : 배열로 된 키와 벨류를 객체로 반환한다. Object.entries의 반대이다. (ex [["key1", "value1"], ["key2", "value2"]] -> { key1 : “value1”, key2 : “value2”})

- Object.keys, Object.values : 객체의 키나 벨류를 배열로 반환한다. (ex { key1 : “value1”, key2 : “value2”} -> ["key1", "key2"])

- Object.is : 두 값이 같은지 확인하여 boolean을 반환한다. 원시 타입의 경우 값만 비교하고 참조 타입의 경우 같은 참조를 가리키는지 비교한다.

- Object.prototype.hasOwnProperty : 객체 내부의 해당 프로퍼티가 프로토체인을 통한 상속이 아닌 직접 존재하는지 확인하여 boolean을 반환한다.

<br>

### # **객체 속성, 배열 항목 반복(iterate)에 어떤 방법을 사용하는가?**

<br>

- 객체 속성 반복하는 방법

  for-in + hasOwnProperty, Object.keys

<br>

- 배열 항목 반복하는 방법

  for-of, Array 메서드

<br>

### # **Javascript 내장 객체를 확장하는 것이 왜 좋은 방법이 아닌가?**

<br>

- 내장 객체를 확장하는 것은 위험한 방법이다. 내장 객체를 확장하게 되면 이 내장 객체를 상속받아 사용하는 모든 객체에 영향이 갈 수 있으므로 확장하지 않는 것이 좋다. 내장 객체를 확장해야 하는 경우는 대체 코드(polyfill)을 추가해야 할 때 뿐이다. 예를 들어 특정 브라우저에서 지원하지 않는 메소드가 있는 경우 대체 코드인 폴리필을 추가해야 할 필요가 생긴다. (ex IE 브라우저가 지원하지 않는 Array.prototype.includes를 사용하려 할 때, Array.prototype에 includes 메소드를 추가)

<br>

### # **옵셔널 체이닝의 장점은 무엇인가요?**

<br>

- 옵셔널 체이닝을 붙인 왼쪽 평가 대상에 값이 없으면 평가를 멈추게 된다. 옵셔널 체이닝을 사용하면 중첩 프로퍼티들을 안전하게 사용할 수 있다. 예를 들어 서버에서 배열 데이터 가져와 map 메서드로 리스트를 생성한다고 할 때 데이터가 없는 경우 에러가 발생할 수 있다. 이럴 때 옵셔널 체이닝을 활용하여 데이터가 유효한 경우에만 map 메서드를 활용하여 리스트를 생성할 수 있다.

<br>

### # **쓰로틀링과 디바운싱에 대해 설명해주세요.**

<br>

- 쓰로틀링

  마지막 함수가 호출된 후 일정 시간이 지나기 전에 다시 호출되지 않도록 하는 것이다. 스크롤 이벤트에 자주 쓰인다. Lodash 라이브러리의 쓰로틀(throttle)을 사용하거나, 타이머 관련 api를 사용하여 직접 구현할 수 있다. (쓰로틀링 체크하는 boolaen타입의 state와 setTimeout으로 호출 막기)

  ```javascript
  const handleScroll = () => {
    if (throttle) return;
    if (!throttle) {
      setThrottle(true);
      setTimeout(async () => {
        setPage((page) => page + 1);
        setThrottle(false);
      }, 300);
    }
  };
  ```

<br>

- 디바운싱

  연이어 호출되는 함수들 중 마지막 함수(또는 제일 처음)만 호출하도록 하는 것이다. 검색 결과에 따른 ajax 요청 시 자주 쓰인다. Lodash 라이브러리의 디바운스(debounce)를 사용하거나, 타이머 관련 api를 사용하여 직접 구현할 수 있다. (setTimeout으로 호출 지연시키기)

  ```javascript
  useEffect(() => {
    const debounce = setTimeout(() => {
      return setQuery(searchText);
    }, 300);

    return () => clearTimeout(debounce);
  }, [searchText]);
  ```

<br>

### # **불변 객체(immutable)를 만드는 방법은 어떤게 있나요?** (참고 : https://spiderwebcoding.tistory.com/8)

<br>

- 기본적으로 원시 타입을 제외한 모든 값은 변경 가능한 값(mutable)이다. 즉 새로운 값을 다시 만들 필요없이 직접 변경이 가능하다는 것이다. 불변 객체를 만들기 위해서는 const와 Object.freeze 메소드를 사용하여 만들 수 있다. 하지만 const로 만드는 경우 재할당은 불가능하지만 할당된 값이 참조 타입인 경우 메모리 힙에 참조 값은 변경(객체 재할당 X 객체 프로퍼티 재할당 O)될 수 있으므로 완전한 불변 객체가 아니다. 또 Object.freeze 메소드는 동결된 객체를 반환하지만 객체의 재할당(객체 재할당 O 객체 프로퍼티 재할당 X)이 가능하므로 완전히 불변 객체가 아니다. 완전한 불변 객체를 만들기 위해 const와 Object.freeze 메소드를 함께 사용할 수 있다. 먼저 const로 바인딩 된 변수를 상수화 시킨 다음, Object.freeze()로 해당 변수를 동결 객체를 만들면 객체의 재할당과 객체의 속성 둘 다 변경 불가능한 불변 객체(객체 재할당 X 객체 프로퍼티 재할당 X)가 된다. 아니면 immutable.js와 같은 라이브러리를 활용하여 불변 객체를 만들 수 있다.

  ```js
  const test = {
    name: "jam",
  };

  Object.freeze(test);
  ```

<br>

### # **자바스크립트의 람다식**

<br>

- 람다식이란 메서드를 하나의 식으로 표현한 것을 뜻하며 식별자 없이 실행 가능한 익명 함수가 람다 함수이다. 자바스크립트에서는 화살표 함수가 람다 함수이다.

<br>

### # **싱글톤 패턴**

<br>

- 싱글톤 패턴은 전체 시스템에서 클래스의 인스턴스를 하나만 존재하도록 하는 패턴이다. 객체 리터럴이 싱글톤 패턴의 대표적인 예이다. 하지만 객체 리터럴을 통해 만들어진 객체는 모든 속성이 다 공개되어 있다는 단점이 있다. 비공개로 만드는 게 제대로 된 싱글톤 패턴이다. 즉시 실행 함수를 통해 객체의 비공개 변수를 가질 수 있게 만들어주어 싱글톤 패턴을 구현할 수 있다.

  ```js
  const singleton = (() => {
    let instance;
    const a = "hello";

    const initiate = () => {
      return {
        a: a, // 비공개 변수
        b: () => {
          alert(a);
        },
      };
    };

    return {
      getInstance: () => {
        if (!instance) {
          instance = initiate();
        }
        return instance;
      },
    };
  })();

  const first = singleton.getInstance();
  const second = singleton.getInstance();
  console.log(first === second); // true
  ```

<br>

### # **event.preventDefault() 의 역할이 무엇인지 설명하세요.**

<br>

- 해당 이벤트에 대한 기본 동작을 실행하지 않도록 지정한다. 예를 들어 a태그 링크 이동, form태그의 submit 기능과 같은 경우가 있다.

<br>

### # **performance API가 무엇인지 설명하세요**

<br>

- 함수 성능을 측정할 때 사용하는 API이다. 측정 결과는 퍼포먼스 버퍼(performance buffer)에 수집된다. 측정 데이터를 수집하는 메소드로는 performance.now, performance.mark, performance.measure이 있고 결과를 확인하는 메소드는 performance.getEntries, performance.getEntriesByName, performance.getEntriesByType이 있다. 사용 경험은 알고리즘 문제를 풀이할 때 다른 풀이에 대해 함수 실행 속도를 비교하기 위해 performance.now 메소드를 사용해보았는데 console.time 메소드가 더 편해 console.time 메소드를 사용하였다.

<br>

### # **숫자 포멧을 바꾸는 방법** (투인정)

<br>

- 숫자 포멧을 바꾸는 방법으로는 toLocaleString, Intl 객체의 NumberFormat, 정규식을 통해 변환하는 것으로 알고 있다. 실행 속도는 toLocaleString -> Intl.NumberFormat -> 정규식 순으로 toLocaleString가 제일 빠르므로 toLocaleString를 사용하는 것이 좋다고 알고 있다.

<br>

### # **재귀 함수** (참고 : https://joooing.tistory.com/entry/%EC%9E%AC%EA%B7%80-%E2%86%92-%EA%BC%AC%EB%A6%AC-%EC%9E%AC%EA%B7%80-Tail-Recursion)

<br>

- 함수가 자기 자신을 호출하는 것을 재귀함수라고 한다. 재귀함수는 종료조건이 있어야 하며, 종료조건을 설정해주지 않으면 무한 반복을 하게된다. 재귀 함수를 사용하는 이유는 알고리즘 자체가 재귀적으로 표현하기 자연스러울 때 혹은 변수 사용을 줄이기 위해 사용한다. 재귀 함수의 단점으로는 콜스택의 부하로 인한 메모리 낭비인데 꼬리 재귀(재귀 호출이 끝나면 아무 일도 하지 않고 결과만 바로 반환되도록 하는 방법)를 통해 해결할 수 있다. 꼬리 재귀를 사용하면 이전 함수의 상태를 유지하지도 않고 추가 연산을 하지도 않아서 콜스택의 부하 문제를 해결할 수 있게 된다.

  ```js
  // 재귀 함수
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

<br>

- 애니메이션의 프레임(frame)

  사람은 1초에 60개의 프레임을 볼 수 있다고 한다. 그 이상의 프레임을 더 찍어내더라도 사람이 느끼기엔 거의 차이가 없다는 말이다. 그래서 자바스크립트로 애니메이션을 구현할때도 1초에 60프레임 정도를 찍어내면 된다. 그 말은, 1프레임을 찍어내는데 16.6ms(1000ms / 60frame)를 넘겨서는 안된다는 말이다. 16.6ms마다 프레임을 찍어내기 위해 첫번째로 사용할 수 있는 방법은 setInterval과 requestAnimationFrame이 있다. 또한 빈번하게 호출되는 이벤트 핸들러에는 보통 3~4ms 정도로 실행을 마치게끔 해야한다. 그래야, 자바스크립트 실행 이후 리플로우 과정까지 총 16ms내에 프레임을 찍어낼 수 있게 된다.

<br>

- requestAnimationFrame(rAF) (재최리백)

  (1) 재귀 호출 방식 : 함수를 반복할 때 사용할 수 있는 메서드이다. 애니메이션을 구현할 때 사용되며 일반적으로 재귀적인 호출 방식을 통해 반복한다.

  (2) 최대 호출 횟수 : Web API에서 동작하며 최대 1초에 60번 동작한다. 다수 애니메이션에도 각각 타이머를 생성하지 않고 동일한 타이머를 참조하게 된다.

  (3) 리페인트 전 호출 : 다음 리페인트가 진행되기 전에 함수를 호출(정확한 타이밍에 호출) 시키기 때문에 프레임 누락을 방지할 수 있다. 즉 프레임 시작 시간에 애니메이션 움직임을 업데이트하는 함수를 시작하게 되는 것이다. 애니메이션 함수의 실행과 실제 픽셀을 채우는 리페인트하는 과정에 순서를 보장하여 프레임 누락을 방지할 수 있는 것이다.

  (4) 백그라운드 동작 및 비활성화시 중지 : WebAPI에서 실행되며 브라우저창이 숨겨지거나 최소화되어 보여지지 않는 경우 애니메이션을 중지시키고 보여질 때 다시 실행시킨다. 이를 통해 CPU 리소스를 절약할 수 있다.

<br>

- cancelAnimationFrame(cAF)

  setTimeout의 clearTimeout과 같이 반복되는 requestAnimationFrame 함수를 정지시킬 때 사용한다.

<br>

### # **직렬화 / 역직렬화란?**

<br>

- 직렬화

  컴퓨터 메모리 상에 존재하는 객체(ex Object)를 저장 혹은 전송 가능한 형태로 변환(ex JSON)하는 것을 말한다. 예시로 자바스트립트에서는 JSON.stringify를 통해 객체를 직렬화하여 JSON 문자열 데이터로 변환한다.

<br>

- 역직렬화

  전송 받은 데이터 혹은 문자열(ex JSON)을 컴퓨터 메모리 상에서 사용할 수 있는 객체로 변환(ex Object)하는 것을 말한다. 예시로 자바스크립트에서 JSON.parse를 통해 JSON 문자열 데이터를 역직렬화하여 객체(ex Object)로 변환한다. 또한 fetch API의 response 객체는 json() 메소드를 제공하고 있기 때문에 JSON.parse를 대체하여 사용할 수 있다.

<br>

### # **HTML 문서의 생명주기 이벤트** (돔로비)

<br>

- DOMContentLoaded

  브라우저가 HTML을 전부 읽고 DOM 트리를 완성하는 즉시 발생한다. 이미지 파일(img 태그)이나 스타일시트 등의 기타 자원은 기다리지 않는다.
  DOMContentLoaded 이벤트는 document 객체에서 발생한다. 따라서 이 이벤트를 다루려면 addEventListener를 사용해야 한다.

  ```js
  document.addEventListener("DOMContentLoaded", () => {
    alert("DOM이 준비되었습니다!");
  });
  ```

<br>

- load

  HTML로 DOM 트리를 만드는 게 완성되었을 뿐만 아니라 이미지, 스타일시트 같은 외부 자원도 모두 불러오는 것이 끝났을 때 발생한다.
  onload 프로퍼티로 발생시킬 수 있다.

  ```js
  window.onload = function () {
    // window.addEventListener('load', (event) => {...}와 동일
    alert("페이지 전체가 로드되었습니다.");
  };
  ```

<br>

- beforeunload/unload

  사용자가 페이지를 떠날 때 발생한다. window 객체에서 발생시킬 수 있다.

  ```js
  window.onbeforeunload = function () {
    return "저장되지 않은 변경사항이 있습니다. 정말 페이지를 떠나실 건 가요?";
  };
  ```

<br>

### # **함수 호출 방법 Call by value & call by Reference**

<br>

- Call by value(값에 의한 호출)

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

<br>

- Call by reference(참조에 의한 호출)

  인자로 참조 타입의 객체를 넘기는 것을 말한다. 함수의 파라미터는 인자와 같은 데이터의 주소 값을 참조하고 있어 함수 내부에서 파라미터를 수정하는 경우 원본이 변화된다. 복사하지 않고 직접 참조를 하기에 처리가 빠르고 새로운 메모리를 할당받지 않지만 원본의 변화가 생길 수 있다. 만약 원본의 변화를 방지하려면 함수 내부에서 파라미터를 깊은 복사하여 참조를 끊어준 뒤 사용하면 된다.

  ```js
  // Call by reference(참조에 의한 호출)
  const arr = [1, 2, 3];

  const callByReference = (param) => {
    param.push(4);

    return param;
  };

  console.log(callByReference(arr)); // [1, 2, 3, 4]
  console.log(arr); // [1, 2, 3, 4], 원본 변경 O
  ```

<br>

### # **ajax란 무엇인가?**

<br>

- ajax

  AJAX(Asynchronous JavaScript and XML)는 자바스크립트를 이용해서 비동기적(Asynchronous)으로 서버와 브라우저가 데이터를 교환할 수 있는 통신 방식을 의미한다. 즉, AJAX는 자바스크립트에서 비동기 HTTP 통신이 가능하도록 해주며 서버와 통신 시 XMLHttpRequest 객체를 사용하여 XML, JSON, HTML 등 다양한 데이터 포맷을 주고 받는다.

<br>

- ajax 사용 이유

  자바스크립트는 싱글 스레드 언어로 한번의 하나의 테스크만 수행하게 된다. 이렇게 동기적으로 작업을 수행되게 되면 원하는 데이터를 원하는 시점에 불러올 수 없는 문제가 발생할 수 있다. 이 때 ajax 비동기 통신을 사용하게 되는데 ajax의 경우 자바스크립트 엔진이 아닌 Web API에서 처리되기 때문에 자바스크립트 엔진이 다른 작업을 수행하고 있다고 해도 블로킹되지 않고 수행되게 된다. 즉 Web API를 통해 멀티 스레드와 같은 효과를 볼 수 있는 것이다. 하지만 ajax는 코드가 직관적이지 않고 요청의 상태나 변경을 구독하기 위해서는 이벤트를 등록해서 변경사항을 받아야 하며 요청의 성공, 실패 여부나 상태에 따라 처리하는 로직이 들어가기 좋지 않다는 문제가 있다. 그렇기 때문에 ajax를 대체하여 프로미스 기반의 axios 라이브러리를 사용하거나 내장 라이브러리인 fetch를 사용할 수 있다.

<br>

- xml(eXtensible Markup Language)

  XML은 데이터 포맷 중 하나로 HTML과 유사한 마크업 언어이다. 데이터를 저장하고, 전달할 목적으로 고안되었다. 불필요한 태그들이 들어가 파일의 사이즈가 커질 뿐만 아니라 가독성도 좋지 않아 XML대신 JSON이 사용된다.

  ```xml
  <dog>
    <name>식빵</name>
    <family>웰시코기<family>
    <age>1</age>
    <weight>2.14</weight>
  </dog>
  ```

<br>

- json(JavaScript Object Notation)

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

### # **fetch와 axios 써본적 있나?**

<br>

- 사용해본 적이 있다. 처음에 별도의 설치가 필요없는 fetch를 사용하다가 그 이후 axios를 사용하게 되었다. fetch에 비해 자동 json 변환, 타임아웃 설정, 요청 취소 등 상대적으로 더 많은 내장 기능을 제공하고 있고 더 많은 브라우저에서 지원하기 때문에 axios를 사용하고 있다.

<br>

### # **axios의 withCredential과 fetch의 credential**

<br>

- withCredential을 직역해보면 자격 증명을 함께라고 해석할 수 있다. 단어의 의미만 봐도 알 수 있듯이 무언가 인증할 때 필요한 옵션인 것을 알 수 있다. 정확히 withCredential 옵션의 역할은 서로 다른 도메인(크로스 도메인)에 요청을 보낼 때 요청에 Credential 정보를 담아서 보낼 지를 결정하는 옵션이다. axios에서는 withCredential , fetch에서는 credential로 지정할 수 있다. 예를 들어 쿠키를 요청 헤더에 포함해야할 때 같은 도메인 요청 시 자동으로 포함되지만 서로 다른 도메인인 경우 해당 옵션을 true로 설정해주어야 요청 헤더에 포함된다.

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

  credential 정보가 포함되어 있는 요청은 아래 두 가지 경우를 의미한다.

  (1) 쿠키를 첨부해서 보내는 요청

  (2) 헤더에 Authorization 항목이 있는 요청

<br>

### # **가비지 컬렉팅이 뭐냐? 어떨때 필요할것 같나?**

<br>

- 가비지 컬렉터

  가비지 컬렉터는 메모리 힙에서 메모리 관리를 수행한다. 즉 메모리를 차지하는 데이터 중 사용하지 않는 데이터를 자동으로 삭제한다. 또한 자바스크립트는 자동으로 가비지 컬렉팅을 수행한다. 자바스크립트에서 데이터는 원시타입의 경우 콜스택, 참조타입의 경우 메모리 힙에 저장되는데 주소와 값에 형태로 저장되고 저장 된 데이터가 사용될 때는 주소와 값 중 주소 값을 참조하여 사용되게 된다. 만약 메모리 힙에서 객체나 배열 자신의 주소 값을 참조하는 식별자가 없는 경우 사용하지 않는 데이터이기 때문에 가비지 컬렉터에 의해 삭제되게 되는 것이다. 반면 콜스택의 원시 타입 데이터의 경우 전역 컨텍스트나 함수 컨텍스트가 종료될 때 자동으로 메모리에서 함께 제거된다.

<br>

### # **비즈니스 로직에 대한 개념 설명**

<br>

- 비지니스 로직

  유저의 눈에 보이지는 않지만, 유저가 바라는 결과물을 올바르게 도출할 수 있게 짜여진 로직을 말한다. 예를 들어 유저가 회원가입 시 아이디가 사용되고 있는 아이디인지 검사 후 메세지를 통해 중복인지 아닌지를 확인할 수 있는 로직을 짯다고 가정했을 때 중복 아이디를 검사하는 로직이 비지니스 로직이 되고 비지니스 로직을 통한 결과를 단순히 메세지를 통해 유저에게 보여주기 위한 로직이 뷰 로직이 된다.

<br>

### # **DOM이란 무엇이고 DOM을 직접 접근할 때의 문제점**

<br>

- DOM(Document Object Model)

  DOM이란 문서 객체 모델이며 XML, HTML 문서의 각 항목을 계층으로 표현하여 생성, 변형, 삭제할 수 있도록 돕는 일종의 인터페이스이다. 브라우저의 렌더링 엔진은 HTML 문서를 로드한 후 HTML 파싱 과정에서 계층화 된 트리 형식의 자료 구조인 DOM 트리를 형성하여 메모리에 적재하여 브라우저가 해당 문서를 읽을 수 있도록 한다. 이 DOM 트리를 통해 HTML 문서에 접근할 수 있다. DOM 트리는 크롬 개발자 도구 엘리먼트 탭에 하위 탭인 프로퍼티 탭에서 확인할 수 있다.

<br>

- HTML과 DOM의 차이

  HTML은 웹 페이지를 표시하기 위해 태그, 속성 등 정해진 규칙에 따라 작성되는 언어이며 DOM은 브라우저의 HTML 파서가 HTML 파싱한 후 생성되는 객체 모델로 HTML 문서에 접근하기 위한 일종의 인터페이스이다.

<br>

- DOM을 직접 접근할 때의 문제점

  DOM에 직접 접근해도 문제가 되진 않지만, DOM이 직접 변경된다면 사소한 변경 사항에도 전체가 리렌더링 되기 때문에 성능 저하에 원인이 될 수 있다. 따라서 최대한 DOM에 직접 접근하지 말아야 한다. 이러한 문제를 해결하기 위해 나온 것이 react의 바츄얼 돔이라고 할 수 있다.

<br>

### # **오버로딩(Overloading) vs 오버라이딩(Overriding)**

<br>

- 오버라이딩(Overriding)

  상위 클래스가 가지고 있는 메소드를 하위 클래스가 재정의(복붙)하여 사용하는 방식이다. 자바스크립트의 클래스 확장 시 상속받는 클래스 내부에 super 키워드를 활용하여 오버라이딩 할 수 있다. constructor 내부에서 선언 시 생성자 오버라이딩을 할 수 있고 클래스 바디에 선언 시 메소드 오버라이딩을 할 수 있다.

<br>

- 오버로딩(Overloading)

  같은 이름의 함수를 여러 개 만든 뒤 각각의 함수에 매개변수의 타입, 갯수를 다르게 지정하여 호출 시 전달되는 인자에 타입이나 갯수에 따라 실행 될 함수를 매칭하여 다른 출력 값을 받는 방식을 말한다. 자바스크립트에서는 arguments 객체의 바인딩 되는 인자를 조건으로 하여 구현하거나, 조건문과 인자의 타입이 함수(function)인지를 평가하는 typeof 연산자를 함께 활용하여 구현할 수 있다.

<br>

### # **symbol 타입**

<br>

- 심볼은 변경 불가능한 원시 타입의 값이며, 다른 값과 중복되지 않는 고유한 값이다. 심볼은 객체의 프로퍼티 키로 사용할 수 있고 심볼 값을 키로 갖는 프로퍼티는 다른 어떠한 프로퍼티와도 충돌하지 않는다. 또 심볼 객체의 프로퍼티 중 Symbol.iterator을 사용하여 객체를 이터러블 객체로 만들어 반복할 수 있다. Symbol 함수나 Symbol.for 메소드를 통해 심볼을 생성할 수 있고 사용한 심볼은 자바스크립트 엔진에 전역 심볼 레지스트리에 저장된다.

```javascript
// 예시 1
let symbolWithDesc = Symbol("ungmo2");

console.log(symbolWithDesc); // Symbol(ungmo2)

// 예시 2
const obj = {};

const mySymbol = Symbol("mySymbol");
obj[mySymbol] = 123;

console.log(obj); // { [Symbol(mySymbol)]: 123 }
```

<br>

### # 블로킹(Blocking) vs 논블로킹(Non-Blocking)

<br>

- 제어권

  함수 코드를 실행할 권리, 제어권을 가진 함수는 자신의 코드를 끝까지 실행한 후, 자신을 호출한 함수에게 돌려준다.

<br>

- 블로킹(Blocking) vs 논블로킹(Non-Blocking)

  블로킹과 논블로킹은 함수가 다른 함수를 호출했을 때, 제어권이 누구에게 있는지의 여부에 따라 나뉜다.

  (1) 블로킹(Blocking) : 다른 함수를 호출함과 동시에 제어권을 넘겨주는것을 말한다. 제어권이 넘어갔기 때문에 호출 이후 자신의 코드는 제어권을 다시 받기 전까지 실행하지 않는다.

  (2) 논블로킹(Non-Blocking) : 다른 함수를 호출했지만 제어권은 바로 다시 가져오는것을 말한다. 제어권을 여전히 소유하고있기 때문에, 호출된 함수는 호출된 함수대로 돌아가며 제어권을 다시 받은 함수도 실행된다.

<br>

- 동기(Synchronous) vs 비동기(Asynchronous)

  (1) 동기(Synchronous) : 현재 작업의 응답이 끝남과 동시에 다음 작업이 요청된다. 함수를 호출하는 곳에서 호출되는 함수가 결과를 반환할 때까지 기다린다.
  작업 완료 여부를 계속해서 확인한다.

  (2) 비동기(Asynchronous) : 현재 작업의 응답이 끝나지 않은 상태에서 다음 작업이 요청된다. 함수를 호출하는 곳에서 결과를 기다리지 않고, 다른 함수(callback)에서 결과를 처리한다. 작업 완료 여부를 확인하지 않는다.

<br>

- 동기와 비동기, 블로킹과 논블로킹 동작 예시 (블로킹의 관점은 제어권이고 싱크의 관점은 결과의 처리)

  (1) 블로킹 + 동기 : A함수가 B함수를 호출하면 B함수가 실행되는 동안 동작하지 않고 (블로킹), B함수가 결과를 반환한 이 후 A함수를 처리한다. (동기)

  (2) 블로킹 + 비동기 : A 함수는 B 함수의 리턴값에 신경쓰지 않고, 콜백함수를 보낸다 (비동기).그런데, B 함수의 작업에 관심없음에도 불구하고, A 함수는 B 함수에게 제어권을 넘긴다 (블로킹). 따라서, A 함수는 자신과 관련 없는 B 함수의 작업이 끝날 때까지 기다려야 한다.

  (3) 논블로킹 + 동기 : A함수가 B함수를 호출하고 자신의 코드를 계속 실행하는데(논블로킹), 실행 중 B함수의 결과가 필요하기 때문에 B함수의 결과를 계속 확인하고 결과 반환 시 결과를 사용하여 처리한다. (동기)

  (4) 논블로킹 + 비동기 : A함수가 B함수를 호출하고 자신의 코드를 계속 실행하는데(논블로킹), B 함수를 호출할 때 콜백함수를 함께 주고 B 함수는 자신의 작업이 끝나면 A 함수가 준 콜백 함수를 실행한다. (비동기)

<br>

### # **Parameter와 Argument의 차이**

<br>

- 매개변수(Parameter)

  함수를 호출할 때 인수로 전달받은 값을 담는 변수이다. 함수 내부에서 사용할 수 있다.

<br>

- 인수(Argument)

  함수를 호출할 때 매개변수로 전달되는 값이다.

<br>

### # **동적 언어 vs 정적 언어**

<br>

- 동적 언어 (동적 타이핑 언어)

  런타임에 타입(자료형)이 결정되는 언어이다. 즉, 소스가 빌드될 때 타입을 결정하는 것이 아니라 런타임 시 결정된다. 매번 타입을 써줄 필요가 없기 때문에 빠르게 코드를 작성할 수 있다. 하지만 런타임 시 타입 관련 에러가 발생할 수 있다. 대표적인 동적 언어로는 JavaScript, Ruby, Python 등이 있다.

<br>

- 정적 언어 (정적 타이핑 언어)

  컴파일 타임에 타입(자료형)이 결정되는 언어이다. 즉, 컴파일 시에 타입을 결정하게 된다. 명시적 타입 선언으로 가독성이 좋아지고 안정성이 향상되고 디버깅이 쉬워진다. 대표적인 정적 언어로는 C, C++, Java, Typescript등이 있다.

<br>

### # **크롤링**

<br>

- 웹 크롤링

  웹 크롤링이란 웹 페이지의 원하는 데이터를 수집해서 분류하고 저장하는 것을 뜻한다. 셀레니움같은 관련 라이브러리를 통해 구현할 수 있다. 크롤링 시 유의사항은 크롤링 대상 서버에 과한 부하를 걸지 않기, 컨텐츠 저작권을 지키기, 거부 의사를 밝힌 웹 페이지에 대해서는 크롤링 하지않기 등의 유의사항을 지켜야한다.

<br>

### # **테스트 코드에 대해서 배웠는가?**

<br>

- TDD(Test Driven Development)

  테스트 주도 개발을 의미하며 테스트 코드를 작성한 후 테스트를 통과하는 코드를 작성해나가며 구현하고 테스트에 대한 피드백을 적극적으로 활용하는 프로그래밍 방식을 말한다.

<br>

- TDD(Test Driven Development) 장점

  (1) 철저한 모듈화 : 테스트 작성을 위한 철저한 모듈화를 통해 가독성 , 재사용성, 유지보수를 용이하게 한다.

  (2) 효율적인 설계 : 테스트 작성 전 다양한 예외사항에 대해 생각해볼 수 있으며 전체적인 설계가 변경되는 일을 방지할 수 있다.

  (3) 디버깅 시간 단축 : 자동화 된 유닛테스팅을 전제하므로 특정 버그를 손 쉽게 찾아낼 수 있다.

  (4) 테스트 정의서 대체 : 테스트 정의서를 직접 작성하는 것보다 테스트를 자동화하여 테스트 시간을 작성하고 테스트를 빼먹는 등의 휴먼 에러를 방지할 수 있다.

<br>

- TDD(Test Driven Development) 단점

  (1) 생산성의 저하 : 테스트 코드를 추가로 작성해야하고 중간 중간 테스트 후 코드를 수정해야하므로 생산성이 저하된다.

<br>

- 테스팅 피라미드와 종류

  Google Test Automation Conference에서 제안된 테스트 피라미드와 테스트 비중

  (1) UI 테스팅(E2E Testing) (10%) : 사용자 시점에서 시나리오에 맞춰 테스트하고 예상되는 결과가 나오는지 테스트하는 방법이다. 예시로는 회원가입 후 로그인이 잘 되는지 확인하는 경우가 있을 것 같다.

  (2) 통합 테스팅 (Integrating Testing) (20%) : 최소 두개 이상의 모듈을 연결하여 테스트하는 방법이다. 보통 유닛 테스트가 끝난 모듈을 묶어서 확인한다. 여러 컴포넌트들이 잘 상호작용하고 렌더되는지, DOM 이벤트가 발생했을 때 원하는 UI 변화가 일어나는지 등을 테스트한다.

  (3) 단위 테스팅 (Unit Testing) (70%) : 가장 작은 단위의 모듈을 실행하여 올바른 결과물이 출력되는 지 테스트하는 방법이다. 일반적으로 클래스, 메서드, 컴포넌트 단위로 테스트하며 컴포넌트가 잘 렌더되는지, 특정 함수가 잘 작동하는지 등을 테스트한다. 테스트 방법 중 가장 간단하고 명확하며 빠르다.

<br>

- 테스트 자동화가 무엇인가?

  말 그대로 소프트웨어 코드를 자동으로 테스트하는 것을 말한다. 테스트 자동화를 하는 이유는 반복성 때문이다. 테스트 주도 개발 시 테스트를 반복적으로 수행해야하기 때문에 테스트 자동화를 통해 소모되는 시간을 줄일 수 있고 수동 테스트 중 테스트를 빼먹는 경우와 같이 의도치 않은 이슈를 방지할 수 있다. 대표적인 테스트 자동화 라이브러리로 jest가 있다.

<br>

- 대표적인 테스팅 라이브러리 및 프레임워크

  react에서 대표적으로 사용하는 테스팅 라이브러리로는 jest와 react testing library가 있다. 두 라이브러리는 서로 대체되는 것이 아닌 상호 보완하는 관계를 가지며 react의 컴포넌트를 테스트하기 위해서는 두 라이브러리 모두 필요하다. jest는 테스트를 찾고 실행하고 통과 혹은 실패 여부를 결정하며 react testing library는 컴포넌트 테스트를 위한 가상 돔(ex render 함수를 활용)을 제공한다.

  테스트 방법은 test나 it 함수로 테스트 케이스를 작성하고 테스트 케이스 내부에 expect 함수로 테스트 함수의 결과를 반환하고 반환 된 결과를 toBe와 같은 매치 함수(Test Mathcher)를 통해 테스트 케이스가 통과하는 지 체크할 수 있다. 이 때 테스트 케이스가 여러개인 경우에는 describe 함수를 사용하여 테스트 케이스를 묶을 수 있다. 또한 react testing library에서 제공하는 getByText와 같은 함수를 통해 컴포넌트 내부 엘리먼트를 체크할 수 있고 fireEvent 함수를 사용하여 특정 이벤트 후 컴포넌트 내부 엘리먼트의 변화를 체크해볼 수 있다.

  테스트의 실행은 npm test 스크립트를 통해 실행할 수 있고 자동화 테스트는 npm run watch 스크립트를 통해 실행할 수 있다.

  ```javascript
  import React from "react";
  import { render } from "@testing-library/react";
  import List from "./List";

  // describe 함수 첫번째 인자  "List"는 테스트 설명
  // render 함수는 컴포넌트 렌더링
  // expect 함수의 인자는 검증 대상
  // toXX 함수의 인자는 기대 결과
  describe("List", () => {
    it("renders tasks", () => {
      const { container } = render(<List />);

      expect(container).toHaveTextContent("안녕");
    });
  });
  ```

<br>

- 테스트 케이스 예시 (참고 : https://lumiloves.github.io/2018/08/21/my-first-frontend-test-code-experience)

  아래는 React Testing Library을 활용한 커스텀 훅 테스트 케이스 예시이다.

  ```jsx
  // 예시 코드
  import { useCallback, useState } from "react";

  export default function useToggle(initialState = false) {
    const [state, setState] = useState(initialState);
    const onToggle = useCallback(() => setState(!state), [state]);

    return [state, onToggle, setState] as const;
  }
  ```

  (1) useToggle은 길이가 3인 배열을 리턴한다. [state, onToggle, setState]

  (2) 매개변수로 initialState 값을 입력하지 않으면 기본 state 값은 false로 설정된다.

  (3) 매개변수로 initialState 값을 입력하면 state에 그 값이 설정된다.

  (4) onToggle 함수를 이용해서 state 값을 toggle 할 수 있다.

  (5) setState 함수를 이용해서 직접 state 값을 변경할 수 있다.

  ```jsx
  // 테스트 코드 작성 예시
  import { act, renderHook } from "@testing-library/react-hooks";
  import useToggle from "../useToggle";

  describe("useToggle", () => {
    test("useToggle은 길이가 3인 배열을 리턴한다. (state, onToggle, setState)", () => {
      const { result } = renderHook(() => useToggle(false));
      expect(result.current).toHaveLength(3);
    });

    test("매개변수로 initialState 값을 입력하지 않으면 기본 state 값은 false로 설정된다.", () => {
      const { result } = renderHook(() => useToggle());
      expect(result.current[0]).toBe(false);
    });

    test("매개변수로 initialState 값을 입력하면 state에 그 값이 설정 된다.", () => {
      const { result } = renderHook(() => useToggle(true));
      expect(result.current[0]).toBe(true);
    });

    test("onToggle 함수를 이용해서 state 값을 toggle 시킬 수 있다.", () => {
      const { result } = renderHook(() => useToggle(false));

      act(() => {
        result.current[1]();
      });

      expect(result.current[0]).toBe(true);
    });

    test("setState 함수를 이용해서 직접 state 값을 변경할 수 있다.", () => {
      const { result } = renderHook(() => useToggle(false));

      act(() => {
        result.current[2](true);
      });

      expect(result.current[0]).toBe(true);
    });
  });
  ```

<br>

### # **DRY원칙**

<br>

- DRY 원칙

  돈 리피트 유얼셀프(Don’t Repeat Yourself)로 반복하지 않는 원칙으로 중복 코드 제거를 말한다. DRY 원칙의 장점은 코드 길이가 줄어 가독성이 좋아지고, 재사용성이 높아지며, 유지보수가 쉬워진다.

<br>

### # for문에서의 비동기 함수 사용 시 문제, var와 let 그리고 클로저

<br>

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

<br>

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

<br>

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

<br>

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

<br>

### # **Spread 문법과 Rest 파라미터**

<br>

- Spread 문법

  Spread 라는 단어가 가지고 있는 의미는 확산의 의미를 가지고 있다. 이 문법을 사용하면, 객체 혹은 배열을 펼칠수 있다. 즉, Spread 문법(...)은 대상을 개별 요소로 분리한다. 단, Spread 문법의 대상은 이터러블이어야 한다.

  ```javascript
  const animals = ["개", "고양이", "참새"];
  const anotherAnimals = [...animals, "비둘기"];

  console.log(animals); // ['개', '고양이', '참새']
  console.log(anotherAnimals); // ['개', '고양이', '참새', '비둘기']
  ```

<br>

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

### # **함수의 인자 복사**

<br>

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

### # "==" 와 "==="의 차이

- `==`는 동등 연산자로, 두 값을 비교할 때 자료형 타입이 다른 경우 형변환을 수행한 뒤 비교한다. 이러한 형변환은 때로 예측하지 못한 결과를 초래할 수 있다. `===`는 일치 연산자로 형변환없이 자료형 타입과 값 모두 비교한다. 따라서 일치 연산자를 활용하여 비교하는 것이 더 안전하다. 또한 두 연산자 모두 참조 타입을 비교할 때는 동일한 참조 주소를 가리키는지 비교한다. 만약 참조 타입의 내부 값을 비교하려면 Object.entries, toString과 같은 메소드를 통해 원시 타입으로 변경해서 비교하거나 Lodash의 isEqual 메소드를 활용하여 비교할 수 있다.

  ```javascript
  console.log(100 == "100"); // true
  console.log(100 == 100); // true

  console.log(100 === "100"); // false
  console.log(100 === 100); // true
  ```

<br><br><br>

## # React

<br>

### # **SSR / CSR**

<br>

- SSR / CSR 이란?

  - SSR

    서버 사이드 렌더링으로 서버로부터 이미 그려진 최소한의 데이터가 포함된 정적인 HTML을 전달받아 페이지를 우선 렌더링하고 병렬적으로 js 로드가 완료되면 하이드레이션을 통해 사용자와 상호작용할 수 있도록하는 방식이다. SPA(Single page application)인 nextjs에서는 getServerSideProps나 React Server Component를 통해 구현이 가능하다. 여기서 이미 그려진 정적인 HTML이란 nextjs의 경우 react dom 파싱과 runtime css in js를 사용하는 경우 css를 심어준 상태를 이야기한다.

  - CSR

    클라이언트 사이드 렌더링으로 서버에서 빈 HTML을 전달받아 js 번들 로드가 완료되면 동적으로 태그들과 스타일을 생성하여 페이지를 렌더링하는 방식이다. react가 사용하는 렌더링 방식이다.

<br>

- SSR / CSR 장단점이 무엇인가?

  - SSR 장점 (빠S/서떨T)

    (1) 빠른 초기 로딩 : 서버로 부터 화면 구성을 위한 HTML을 먼저 받아오기 때문에 초기 로딩이 빠름

    (2) SEO 유리 : 각각의 페이지가 존재하므로 SEO에 유리

  - SSR 단점

    (1) 서버 부하 높음 : 새로운 요청 시 서버가 모든 리소스를 준비해서 응답하므로 서버 부하 높고 로딩 속도 늦음

    (2) 떨어지는 사용자 경험(UX) : 새로운 요청 시 페이지가 새로고침 되므로 사용자 경험이 떨어짐

    (3) TTV와 TTI : HTML을 받아온 후 띄워놓고 JS를 받아오기 때문에 Time To View와 Time To Interact간에 시간 간격이 존재하여 이벤트 반응 없을 수 있음

  - CSR 장점 (서자/느S)

    (1) 서버 부하 낮음 : 새로운 요청 시 필요한 부분에 관련된 데이터만 응답하므로 서버부하가 낮고 로딩 속도 빠름

    (2) 자연스러운 사용자 경험(UX) : 새로운 요청 시 페이지가 새로고침 되지 않아 자연스러운 사용자 경험

  - CSR 단점

    (1) 느린 초기 로딩 : 초기에 모든 js 파일을 받아와야 하기 때문에 초기 로딩이 느림, 사용자에게 현재 불필요한 코드나 중복되는 코드 없이 적절한 사이즈의 코드가 적절한 타이밍에 동적으로 로드되도록 하는 code splitting 으로 해결 가능

    (2) SEO 불리 : 자바스크립트로 사용자와 상호 작용하기 전인 초기 html에는 데이터가 없어 SEO에 불리, react-helmet로 페이지별 메타 태그를 설정해주거나 pre-rendering을 통해 페이지별 정보를 제공하는 html파일을 생성할 수 있는 react-snap과 같은 라이브러리를 활용하여 SEO 최적화 가능

    (3) 화면 변하는 모습 노출 : 데이터가 없는 화면이 먼저 표시된 후, 비동기 요청을 통해 데이터를 서버로부터 받아온 후 화면을 재구성하게 된다. 해결 방법은 로딩 스피너 혹은 스켈레톤 UI를 통해 해결할 수 있다.

<br>

- SSR / CSR 동작 순서

  - SSR

    (1) 브라우저가 서버에 HTML, CSS, Javascript 파일 등 렌더링에 필요한 리소스 순서대로 요청

    (2) 서버에서 HTML, CSS 응답

    (3) 브라우저가 HTML/CSS파싱 -> 스타일 -> 레이아웃 -> 페인트 -> 컴포지트 단계를 거쳐 컨텐츠 렌더링

    (4) 컨텐츠 렌더링 후 Javascript 파일 요청, Javascript 파일이 로드되면 사용자와 DOM 요소 간 상호 작용 가능

  - CSR

    (1) 브라우저가 서버에 HTML 파일 요청

    (2) 서버에서 비어있는 HTML 파일 응답

    (3) HTML 파일 구성을 위한 Javascript 파일 요청

    (4) Javascript 파일 응답 받은 후 동적으로 HTML 파일 구성

    (5) 브라우저가 구성 된 HTML 파일을 로드 및 파싱하여 컨텐츠 렌더링

<br>

- React SSR 구현 방법 : https://velog.io/@kwonh/SSR-%EC%84%9C%EB%B2%84%EC%82%AC%EC%9D%B4%EB%93%9C%EB%A0%8C%EB%8D%94%EB%A7%812-SSR-%EC%A7%81%EC%A0%91%EA%B5%AC%ED%98%84-ReactDOMServer

<br>

- Next.js

  (1) CSR로 동작하는 react에서 SSR 혹은 SSG를 사용하기 위해 사용하는 프레임워크

  (2) 첫 페이지에서는 SSR(서버 사이드 렌더링)방식으로 데이터가 채워진 html을 받아 SEO 문제를 해결

  (3) 다음 페이지에서부터는 CSR(클라이언트 사이드 렌더링)방식으로 필요한 데이터만 서버에 요청

  (4) react의 csr은 경우 초기 렌더링 속도가 느리다는 단점이 있어 nextjs의 ssr 혹은 ssg를 통해 초기 렌더링 속도를 향상시킬 수 있다.

<br>

### # **React vs Vue vs Angular**

<br>

- Libraries, Frameworks 차이

  라이브러리는 흐름을 개발자가 직접 제어한다. 필요한 기능이 있을 때 라이브러리를 가져다 사용하는 것이다. 반대로 프레임워크는 프레임워크가 흐름을 가지고 있다. 프레임워크가 짜 놓은 틀에서 코드를 작성하게 된다.

<br>

- Libraries, Frameworks 사용하는 이유

  규모가 커지고 복잡한 애플리케이션을 개발하며 생산성을 향상시키고 많은 양의 데이터 관리와 코드 유지 보수를 더욱 편리하게 하기 위해 다양한 Frontend Framework,Library가 등장하고 사용하게 되었다.

<br>

- React(라이브러리), Vue(프레임워크), Angular(프레임워크) 중 React를 사용하는 이유

  처음 프레임워크, 라이브러리 사용하여 개발을 시작하게 되었을 때 React, Vue, Angular 중 React를 선택한 이유는 더 큰 개발 생태계를 가지고 있기 때문이었습니다. 현재도 npm 패키지 다운로드 수를 비교해보면 React 패키지 다운로드 수가 압도적입니다. 또한 React나 Vue 모두 오픈 소스이고 정기적으로 버전을 릴리즈하고 있지만 개인이 기업에 후원을 받아 관리되는 Vue보다 Facebook이 직접적으로 관리하는 React가 지속적으로 신뢰할 수 있는 라이브러리라고 생각했습니다.

<br>

### # **React란?**

<br>

- React의 특징

  (1) 가상 돔(Virtual DOM) : 가상 돔은 실제 DOM에 적용시키기 전 가상 DOM에 변화된 부분을 먼저 적용시킨 후 변화된 부분만 렌더링 되도록 하여 최소한의 연산을 통해 성능을 증가시킨다.

  (2) 단방향 데이터 바인딩 : 리액트는 데이터의 흐름은 단방향이다. 즉, 위에서 아래, 부모에서 자식, 한방향으로만 흐르며 거꾸로 부모의 데이터를 바꿔주기 위해서는 state를 이용해야 한다.

  (3) JSX 문법을 통한 선언형 프로그래밍 : JSX 문법을 사용한다. HTML을 작성하듯 사용하며 자바스크립트와 동시에 사용하고 HTML에 자바스크립트의 변수들을 바로 사용할 수 있는 일종의 템플릿 언어이다. JSX 문법을 사용하여 선언적으로 프로그래밍한다. 결과만 기술함으로써 코드 의도 파악이 쉽다. 예를 들어 렌더단에 js와 html 동시 사용하는 map이 있다.

  (4) 컴포넌트 기반 UI : 개별적인 뷰인 컴포넌트를 통해 UI를 구성한다.

<br>

- React의 장단점

  - 장점

    (1) 컴포넌트화 : 컴포넌트를 통해 재사용성을 증가시키고 유지보수 용이하게 함

    (2) 가상 돔 : 데이터 변경 -> 가상 DOM에 적용 -> 이전 가상 DOM과 비교 -> 변경된 부분 실제 DOM에 적용의 과정을 거쳐 DOM 연산 횟수를 줄이고 서버 부하를 줄임

    (3) 넓은 생태계 : Vue나 Angular에 비해 사용자가 압도적으로 많고 커뮤니티나 자료가 방대

  - 단점

    (1) 브라우저 호환성 : IE8 이하 버전은 지원하지 않음

    (2) 내장 기능 부족 : view 이외의 기능은 직접 구현하거나 써드파티 라이브러리(패키지,모듈)를 사용해야한다는 번거로움이 있음

<br>

### # **React Lifecycle Methods**

<br>

- 리액트 라이프사이클 순서

  생성(mount) -> 갱신(update) -> 제거(unmount)

<br>

- 각 메소드들을 언제 사용하는지?

  (1) componentDidMount : 컴포넌트가 생성된 직 후 호출

  (2) shouldComponentUpdate : props 또는 state가 새로운 값으로 갱신되어 렌더링이 발생하기 직전에 호출

  (3) componentDidUpdate : 리렌더링 완료 후 호출

  (4) componentWillUnmount : 컴포넌트가 화면에서 사라지기 직전에 호출

  (5) componentDidCatch : render 함수 에러 발생 시 호출

<br>

- 라이프사이클 중 써본 메소드가 뭐가 있는지?

  클래스형으로 작업하지 않기 때문에 라이프사이클 메소드는 사용해본 적이 없다. 대신 생명주기 메서드를 대체할 수 있는 useEffect hook을 자주 사용하였다. useEffect에 의존성 배열로 빈 대괄호를 사용하면 componentDidMount의 역할을 하고, 함수를 return하면 componentWillUnmount 역할을 한다. 또한 의존성 배열을 아예 사용하지 않거나, 의존성 배열에 값을 넣어 componentDidUpdate를 대체할 수 있다.

<br>

- componentDidMount 와 render 중 무엇이 먼저 실행되는지?

  componentDidMount 메서드보다 render 메서드가 먼저 실행되는 것으로 알고 있다.

<br>

### # useEffect hook

useEffect는 클래스형 컴포넌트의 생명주기 메소드를 대체하기 위해 사용한다. 컴포넌트 마운트(컴포넌트가 화면에 그려짐, 즉 렌더링 과정 중 페인트까지 완료), 컴포넌트 언마운트(컴포넌트가 화면에서 사라짐), 의존성 배열 값 변경 시 실행할 수 있다.

- (1) 의존성배열 값 x, return 함수 x : 내부 로직이 컴포넌트 마운트 시 실행

  ```javascript
  useEffect(() => {
    ...
  }, []);
  ```

- (2) 의존성배열 값 o, return 함수 x : 내부 로직이 컴포넌트 마운트 시 실행, 의존성 배열 값 변경 시 실행

  ```javascript
  useEffect(() => {
    ...
  }, [abc]);
  ```

- (3) 의존성배열 값 x, return 함수 o : 내부 로직이 컴포넌트 마운트 시 실행, return 함수는 컴포넌트 언마운트 시 실행

  ```javascript
  useEffect(() => {
    ...

    return () => {...};
  }, []);
  ```

- (4) 의존성배열 값 o, return 함수 o : 내부 로직이 컴포넌트 마운트 시 실행, 의존성 배열 값 변경 시 실행, return 함수는 컴포넌트 언마운트 시 실행, 의존성 배열 값 변경 직전 실행

  ```javascript
  useEffect(() => {
    ...

    return () => {...};
  }, [abc]);
  ```

- (5) 의존성배열 x : 컴포넌트 리렌더링마다 실행

  ```javascript
  useEffect(() => {
    ...
  });
  ```

<br>

### # **가상 돔(Virtual DOM)**

<br>

- 하나의 DOM 노드가 조작될 때마다 DOM 트리와 스타일 규칙들이 수정되므로 렌더 트리 생성, 레이아웃(리플로우), 페인트(리페인트) 단계를 다시 거친다. 이처럼 DOM객체의 크기나 위치가 변경되었을 때, 연관되는 DOM객체들의 위치와 크기를 재연산하여 배치하는 레이아웃 단계를 다시 거치는 것을 리플로우라고 하며, 리플로우가 일어나거나 DOM객체의 색상 혹은 글 내용 등이 바뀌었을 때 페인트 단계를 다시 거치는 것을 리페인트라고 한다. DOM 노드 하나를 조작할 때마다 리플로우나 리페인트 작업이 되면 브라우저의 성능 저하를 유발하게 된다. react에서 리플로우와 리페인트를 최소화하기 위해 등장한 것이 버츄얼 돔이다. 버츄얼 돔은 실제 DOM의 상태를 메모리에 저장해놓고 메모리 상에서 변경 전과 변경 후의 상태를 비교한 뒤 최소한의 내용만 실제 DOM에 반영 하는 프로그래밍 개념이다. 싱글 페이지 애플리케이션은 클라이언트 사이드 렌더링 방식을 채택하여 사용하는데 클라이언트 사이드 렌더링 방식에서는 잦은 DOM의 변화가 일어난다는 특징이 있다. 그런데 DOM에 변화가 일어날 때마다 리렌더링 과정을 반복하게 되면 많은 연산 비용이 발생하게 되므로 성능 이슈가 발생할 수가 있다. 하지만 버츄얼 돔은 실제 렌더링하는 것이 아닌 메모리 상에서 동작하기 때문에 훨씬 빠르고 여러 번에 상태 변화 시 버츄얼 돔에 우선 적용 후 배치처리를 통해 한번만 실제 돔에 반영시키므로 리렌더링도 한번만 발생시키므로 연산 비용이 적어 큰 성능 향상에 이득을 얻게 된다.

<br>

### # **Props / State**

<br>

- Props란?

  상위 컴포넌트가 하위 컴포넌트에 전달하는 데이터를 가진 객체이다. 단방향 데이터 흐름을 가지며 자식 입장에서는 직접 수정할 수 없다는 특징이 있다. 변수, state, 함수 등 모두 전달할 수 있다.

<br>

- State란?

  컴포넌트 내부에서 가지고 있는 컴포넌트의 상태값이다. 유동적인 데이터를 다루기 위한 객체이다.

<br>

- let으로 변수 선언해서 관리하면 될껄 왜 state로 관리하나?

  state는 일반 변수와 다르게 setState를 통해 값이 변하게 되면 render 함수를 호출하여 리렌더링이 발생한다. 값이 변함에 따라 컴포넌트를 최신으로 유지해야 하기 때문에 render 함수를 호출하는 state를 사용하는 것이다.

<br>

- Props와 State의 차이

  (1) props는 자식 컴포넌트로 전달되고 state는 컴포넌트가 직접 관리한다.

  (2) props는 직접 변경할 수 없고 state는 직접 변경이 가능하다.

<br>

- 왜 state를 직접 변경하지 않고 setState를 이용하나요?

  컴포넌트는 현재의 state와 setState를 얕은 비교해서 setState의 참조가 바뀌게 되면 업데이트 됬다고 감지하게 되어 render 함수를 호출하는데, state를 직접 setState의 참조가 바뀌지 않아 render 함수를 호출하지 않게 되어 상태 변경이 일어나도 리렌더링이 일어나지 않는다. 상태 변경을 추적하고 변경에 따라 구성 요소의 최신화를 유지하기 위해서는 setState를 사용해야 한다. (추가 내용 : setState를 통해 root.render 함수 호출 시 리렌더링이 되는 이유는 컴포넌트 return 함수 내부에서 최신 state 값이 포함된 React.createElement 함수를 호출하여 새로운 react element를 생성하는데 이 element들을 렌더링하는 것이 renter 함수이다. 그렇기 때문에 state 값 변경 시 setState를 사용하여 render 함수가 정상적으로 호출되게 해야한다.)

<br>

- 리액트에서 setState는 비동기 동작인가요, 동기 동작인가요? (+ react batch update)

  setState는 비동기로 동작한다. 비동기로 동작하는 이유는 일정 시간동안 변화하는 상태를 모아 한번에 렌더링하기 위해서이다. 이러한 업데이트 방식을 배치 업데이트라고 한다. 리액트의 배치 업데이트(batch update)는 16ms(밀리세컨드)당 한번만 일어난다. 만약 배치 업데이트를 하지 않는다면 setState를 100번 연속 호출했을 때 100번의 리렌더링이 발생하여 성능 저하가 발생할 수 있다. 그러므로 react는 배치 업데이트를 사용하여 16ms마다 업데이트 된 state를 한번에 처리하여 리렌더링의 횟수를 줄여 성능을 향상시켰다. 하지만 배치 업데이트로 인해 state 업데이트 후 바로 state 값을 참조하여 다른 작업을 할 때 문제가 발생할 수 있다. 이런 경우 이전 state를 바로 참조할 수 있는 prevState를 활용하여 상태를 동기적으로 업데이트 한 후 사용하는 방식으로 해결 할 수 있다. prevState는 setState 인자로 함수를 전달하고 해당 함수의 파라미터로 이 전 state를 전달하는 방식으로 사용할 수 있다. (ex : `setState((prev) => prev + 1`)

<br>

### # **react 리렌더링 조건**

<br>

- 기본 리렌더링 조건

  (1) 부모 컴포넌트가 렌더링 될 때

  (2) 자신의 state가 변경 될 때, 단 setState를 사용하여 변경해야한다. state를 직접 변경할 경우 state의 변경을 감지하지 못하기때문에 render 함수가 호출 되지 않는다.

  (3) 자신이 전달받은 props가 변경될 때

- React에서 리렌더링을 막아야하는 경우

  무분별하게 막아야하기 보다는 필요한 상황에 막아야한다. 가상 돔을 사용하여 컴포넌트를 업데이트시키는데 이유없이 리렌더링을 막으려고 한다면 큰 이점없이 코드만 더 복잡해질 수 있다. 예를 들어 사용자 입력 값이 있고 해당 값을 유지시켜야하는 상황에서 리렌더링으로 인해 해당 값이 초기화 되버리거나 리렌더링으로 인해 불필요한 API 호출이 발생하는 등 필요 상황에 따라 리렌더링을 막아줘야한다.

- 리액트의 2가지 렌더링과 2가지 렌더링 단계

  - 리액트 렌더링 단계와 브라우저 렌더링 단계

    리액트로 웹 개발할 때에 리액트 렌더링 단계와 브라우저 렌더링 단계로 나뉜다. 리액트 렌더링에 의한 돔 업데이트가 발생하면 브라우저 렌더링이 진행된다.

  - 리액트의 렌더링

    - 컴포넌트 렌더링 : 컴포넌트를 실행하여 리액트 엘리먼트(ReactElement)를 리턴하는 것이다. (jsx 문법으로 작성 된 컴포넌트가 js로 번들링 된 후 js 내부에서 createElement를 통해 react 엘리먼트의 정보를 담고 있는 객체를 리턴한다.)

    - 엘리먼트 렌더링 : 엘리먼트를 DOM에 반영하는 것이다. 이 과정에서 fiber(React V15 이전에는 Virtual DOM)를 구성 및 업데이트하고, 트리와 트리를 비교하는 재조정(Reconciliation) 과정을 거쳐서 변경된 부분만 DOM을 업데이트한다. (가상 돔 구성 및 업데이트 -> 재조정 -> 실제 돔 업데이트)

  - 리액트의 렌더링 단계

    - Render phase 단계 : 컴포넌트 렌더링부터 엘리먼트 렌더링의 업데이트 피버(가상 돔), 재조정까지이다. 즉 이전 렌더링과 비교하여 변경된 부분을 파악까지만 한다.

    - Commit phase 단계 : 변경 된 부분만 DOM을 업데이트한다. 엘리먼트 렌더링의 실제 돔 업데이트하는 단계를 말한다.

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

    (1) 부모 컴포넌트를 감싸고 있는 컨테이너가 빈번하게 렌더링 되지 않는 조건일 때 사용한다. 왜냐하면 이와 같은 환경에서 자식 컴포넌트를 children으로 받아오게 되면 컨테이너가 리렌더링 될 때 마다 부모 컴포넌트는 불가피하게 함께 리렌더링 되기 때문이다. 이런 경우 부모 컴포넌트 내부에서 자식 컴포넌트를 그대로 사용하고 부모 컴포넌트를 React.memo로 감싸 최적화할 수 있다.

    (2) 반복적으로 쓰이는 디자인 레이아웃을 제작할 때 사용한다. 코드 재사용성을 극대화하여 생산성과 가독성을 증가시킬 수 있다.

- React.memo

  - React.memo란?

    React.memo는 컴포넌트를 메모이징 하기 위해 사용하는데 컴포넌트가 렌더링할 때 해당 결과를 메모이징하여 저장하고 다음 렌더링이 일어날 때 props가 같다면 메모이징 된 값을 사용한다. 단 매번 변하는 props를 받아오는 컴포넌트나 레퍼런스가 계속 변하는 콜백 함수를 props로 받는 컴포넌트의 경우 React.memo를 사용하면 오히려 성능 저하가 올 수 있으므로 성능 향상의 이점이 있을 때에만 사용하는 것이 좋다.

  - children props를 전달 받는 컴포넌트에서 React.memo가 동작하지 않는 이유

    우선 React.memo는 참조 주소만 비교하는 얕은 비교를 통해 메모이징 된 컴포넌트를 사용할 지 결정하는데 children props를 사용하는 컴포넌트 내부에서 React.memo가 동작하지 않는다는 것은 props로 전달 받는 children의 참조 주소가 변경되었다는 것을 의미한다. 내부 children의 참조 주소가 변경되었기 때문에 메모이징한 컴포넌트를 사용하지 않는 것이다.

    children props를 자식 컴포넌트로 전달하는 부모 컴포넌트가 리렌더링 될 때 children props에 해당하는 컴포넌트의 createElement가 새로 호출된다. 부모 컴포넌트 내부에서 createElement가 새로 호출 되면 새로운 react 엘리먼트 객체를 리턴하게 되고 해당 객체를 다시 자식 컴포넌트의 children props로 전달하게 된다. 이렇게 되면 이전에 전달했던 react 엘리먼트 객체와 리렌더링 후 새롭게 생성 된 react 엘리먼트 객체의 참조는 다르게 되어 children을 사용하고 있는 자식 컴포넌트 내부에서는 React.memo가 동작하지 않게 된다.

<br>

### # **컴포넌트**

<br>

- 컴포넌트에 대해 설명해달라

  재사용이 가능한 UI 구성 단위이다. 컴포넌트는 재사용이 가능하고, 개별로 관리되기 때문에 유지 보수에 좋고 렌더단(render 함수 내)에서 페이지 구성을 파악하기 편하다.

<br>

- 컴포넌트를 나누는 기준

  (1) 페이지를 구성하는 요소 (nav, footer 등)

  (2) 재사용이 필요한 반복되는 요소인 경우

  (3) 한 컴포넌트 내에 코드 길이가 길어 가독성이 떨어지는 경우

<br>

### # **Hooks 란?**

<br>

- Hooks란?

  공식 문서에서는 Hook은 함수 컴포넌트에서 React state와 생명주기 기능을 연동할 수 있게 해주는 함수라고 한다. react를 클래스 없이 사용할 수 있게 해준다. 클래스형 컴포넌트의 단점을 보완하기 위해 만들어졌다. 최상위 레벨에서 호출해야하며 함수 컴포넌트 내에서 호출해야한다.

<br>

- Hooks가 만들어진 이유는?

  클래스형 컴포넌트에

  (1) extends와 super(props)를 매번 작성

  (2) 함수, props 등 사용 시 매번 this에 bind 후 사용

  (3) 고차 컴포넌트 지옥

  와 같은 문제로 인해 Hooks가 만들어지게 되었다.

<br>

- Hooks를 어떻게 사용했는지?

  useState, useEffect, useNavigate, useCallback, useMemo, useRef, useQuery, useInview, custom hook 등을 사용하였다.

<br>

- 클래스형 컴포넌트와 함수형 컴포넌트의 차이

  (1) 선언 방식 (클래스 class로 시작하고 컴포넌트로 상속, 함수 일반 함수 생성과 동일)

  (2) lifeCycle 관련 기능 사용 여부 (클래스 O, 함수 X)

  (3) 메모리 자원 사용량 (클래스 > 함수)

  (4) state, props 사용 방법 (클래스 this로 사용, 함수 this없이 사용)

<br>

### # **hook을 사용할 때의 가장 큰 장점은?**

<br>

- 로직의 재사용 가능, 관리가 쉽다

  Hook은 함수형 컴포넌트 이므로 함수 안에서 다른 함수를 호출하는 것으로 새로운 Hook을 만들어 볼 수 있기 때문이다. 따라서 리액트의 내장되어있는 Hook과 다른 사람들이 만든 여러 custom Hook을 레고처럼 조립해서 쉽게 custom Hook을 만들 수 있다.

<br>

- 로직을 한 곳으로 모을수 있어서 가독성이 좋다

  클래스형 컴포넌트의 라이프사이클 API는 서로 다른 로직이 하나의 메서드에 섞여 있어서 가독성이 좋지 않다. Hook은 같은 로직을 한 곳으로 모을 수 있다.

<br>

- Wrapper 컴포넌트양 감소

  고차 컴포넌트를 커스텀 훅으로 대체하면, Wrapper 컴포넌트를 사용하지 않아도 간단하게 구현할 수 있다.

<br>

- 정적 타입 언어로 타입을 정의하기 쉽다

  고차 컴포넌트의 타입 정의에 비해 정적 타입 언어로 타입을 정의 하기 쉬워졌다고 한다.

<br>

### # 리액트에서 객체가 {...spread} 사용하여 리턴해주는데, 그 이유가 무엇인가(불변성)

불변성은 변하지 않는 상태나 값을 말한다. 리액트에서의 불변성은 값을 직접적으로 변경을 하지 않고, 기존의 값을 수정하지 않으면서 새로운 값을 만들어내는 것을 의미한다. 원시 타입의 경우 값이 변경되는 경우 기존 값을 직접 변경하는 것이 아닌 콜스택에 새로운 메모리를 생성하여 새로운 메모리를 참조하도록 동작한다. 즉 불변성을 가지고 있다. 하지만 객체 타입의 경우 값이 변경되는 경우 메모리힙에 새로운 메모리를 생성하지않고 값을 직접 변경하도록 동작한다. 리액트에서는 이러한 객체 타입의 불변성을 지켜주고자 spread 문법을 사용했다. 리액트는 얕은 비교를 통해 state의 업데이트를 감지한다. 얕은 비교는 실제 내부 값까지 비교하는 것이 아닌 참조하는 값에 메모리 주소를 비교하는 것이다. 기존 값과 최신 값에 얕은 비교를 수행하여 최신 값이 새로운 메모리 주소를 참조할 때 업데이트가 발생하게 되는 것이다. 이 때 배열이나 객체의 상태를 업데이트 하는 경우 리액트에서는 새로운 메모리 주소를 생성하기 위해 setState에 배열이나 객체를 할당하고 배열이나 객체 내부에 스프레드 연산자를 활용한 기존 값의 복사본과 최신 값을 할당해준다. (`setState([...state, newState]), setState({...state, [key]: value})`) 이렇게 복사본을 활용한 방식과 새로운 메모리 주소를 생성하는 방식을 통해 불변성을 지킬 수 있고 불변성을 지켜줌으로서 예상치 못한 사이드 이펙트를 방지할 수 있고 얕은 비교를 통해 효과적인 상태 업데이트를 할 수 있다. 만약 불변성을 지키지 않고 기존 값을 직접 변경할 경우 참조하는 값에 메모리 주소가 동일하기 때문에 리액트는 상태 변화를 감지할 수 없어 컴포넌트의 최신화를 유지할 수 없게 된다. 이 때 setState의 동작 방식을 확인해보면 만약 setState로 이전 값과 동일한 값으로 업데이트한다고 했을 때 원시 타입의 경우 동일한 값이면 리렌더링이 발생하지 않고 객체 타입의 경우 동일한 값이라도 리렌더링이 발생하게 된다. 이유는 위와 같이 객체 타입의 경우 내부 값은 상관하지 않고 spread 문법을 통해 새로운 메모리 주소를 가진 데이터를 항상 만들어내기 때문에 이전 state와 최신 state 얕은 비교 시 참조 주소가 변경되었기 때문에 계속해서 리렌더링이 발생하는 것이다. 하지만 원시 타입의 경우 같은 값으로 업데이트되는 경우 이전 state와 최신 state는 여전히 동일한 메모리를 가리키고 있기 때문에 리렌더링이 발생하지 않는다.

<br>

### # **Redux란?**

<br>

- 리덕스를 사용해 봤는지.

  리덕스는 전역 상태 관리 라이브러리이다. 사용해보았는데 학습 목적으로만 사용해보고 실제 프로젝트에는 적용시켜보지 않았다. 프로젝트에서 전역 상태 관리가 필요할 때는 리코일을 사용하거나 리덕스에서 공식적으로 만든 리덕스 툴킷을 사용했었다.

<br>

- 리덕스의 디자인 패턴은 무엇이며, 그 패턴이 갖는 장점과 단점은 무엇인지?

  리덕스 디자인 패턴은 FLUX 패턴이다. MVC 패턴의 단점으로 FLUX 패턴이 생겨났는데 MVC 패턴은 양방향 데이터 흐름을 가지고 있어 프로젝트 규모가 커지게 되면 구조가 매우 복잡해지고 예측 불가능한 결과를 나타낼 수 있다. 그래서 생겨난 것이 단방향 데이터 흐름을 가지고 있는 FLUX 패턴이다. FLUX 패턴의 데이터 흐름은 항상 Dispatcher에서 Store로, Store에서 View로, View는 Action을 통해 다시 Dispatcher로 데이터가 흐르게 된다. 단방향 데이터 흐름의 장점은 데이터 변화에 따른 성능 저하 없이 DOM 객체 갱신이 가능하고 데이터 흐름이 단방향이기 때문에 코드를 이해하기 쉽고 데이터 추적과 디버깅이 쉽다. 단점은 변화를 감지하고 화면을 업데이트하는 코드를 매번 작성해야 한다는 단점이 있다.

<br>

- 리덕스 용어와 동작 순서 (https://ivorycode.tistory.com/entry/Redux%EC%9D%98-%ED%9D%90%EB%A6%84%EA%B3%BC-%EC%98%88%EC%A0%9C, https://devlog-h.tistory.com/14)

  (1) 액션 생성 : 액션은 state의 액션을 정의한다. 리듀서는 이 액션을 참고하여 state를 어떻게 변화시킬 지 결정하게 된다.

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

  (2) 리듀서 생성 : 리듀서는 액션의 결과를 보고 state를 업데이트시켜 반환한다.

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

  (3) 컴바인리듀서 생성 : 컴바인리듀서는 모든 리듀서를 하나로 합쳐준다.

  컴바인 리듀서 생성을 위해 필요한 컴바인리듀서 함수, 생성해놓은 리듀서 함수를 임포트한다.
  그 후 컴바인리듀서 함수에 인자로 리듀서 함수를 객체로 전달하고 스토어 생성 시 사용해야하므로 익스포트하여 내보낸다.

  ```js
  export default combineReducers({
    // 리듀서 이름: import한 리듀서
    counterData: counter,
  });
  ```

  (4) 스토어 생성 : 스토어는 state가 저장되는 저장소이다.

  스토어가 가지고 있는 state를 전체 컴포넌트에서 공유하기 위해서 최상위 컴포넌트에 스토어를 연결해야한다.
  스토어 연결을 위해 필요한 크리에이터스토어 함수, 프로바이더 컴포넌트, 컴바인리듀서 함수(네이밍은 rootReducer를 많이 사용)를 임포트한다.
  그 후 store 변수를 생성하여 크리에이터스토어 함수를 할당하는데 인자로 컴바인리듀서 함수를 전달하고
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

  (5) 디스패처 생성 : 디스패치는 리듀서에 액션을 전달한다.

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

  (6) 셀렉터 생성 : 셀렉터는 스토어에 state를 가져온다.

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

<br>

- 리덕스 미들웨어가 무엇인가?

  리덕스 미들웨어를 사용하면 액션이 디스패치 된 다음, 리듀서에서 해당 액션을 받아와서 업데이트하기 전에 추가적인 작업을 할 수 있다. 즉 디스패치 함수를 결합해서 새로운 디스패치 함수를 반환하는 고차함수를 만들어낸다. 리듀서에서는 비동기 로직이 존재할 수 없기 때문에 비동기 작업을 처리하기 위해 미들웨어를 사용한다. 리덕스 미들웨어 라이브러리로는 redux-thunk, redux-saga, redux-observable, redux-promise-middleware 등이 있다.

<br>

- redux-thunk, redux-saga 설명

  (1) redux-thunk : redux-thunk는 리덕스를 사용하는 어플리케이션에서 비동기 작업을 처리할 때 사용하는 미들웨어 중 하나이다. dispatch 함수, 스토어에 접근할 수 있는 getState 등을 파라미터로 전달받을 수 있는 고차함수를 만들고 고차함수 내부에서 특정 작업을 수행한 후 디스패치할 수 있게 해준다. 즉 redux-thunk를 사용하면 액션 객체를 디스패치하던 기존의 방식과 다르게 함수를 디스패치할 수 있게 해준다. 예를 들어 특정 액션이 몇 초 뒤에 실행하게 하거나, 특정 조건에만 디스패치하거나, 비동기 로직을 처리하는 등의 작업을 할 수 있다. redux-thunk를 사용하는 가장 큰 이유는 리덕스가 비동기 로직을 처리하지 못하기 때문에 비동기 처리를 하기 위해 사용한다. 또한 추가로 redux toolkit에서는 비동기 로직 처리 시 내장되어 있는 createAsyncThunk를 사용하여 처리할 수 있다.

  ```js
  // 참고 : https://react.vlpt.us/redux-middleware/04-redux-thunk.html
  // 1. 스토어 연결 시 미들웨어 적용
  const store = createStore(
    rootReducer,
    composeWithDevTools(applyMiddleware(ReduxThunk, logger))
  );

  // 예시1.
  // 액션 생성 함수
  export const increase = () => ({ type: INCREASE });
  export const decrease = () => ({ type: DECREASE });

  // thunk 함수 생성 -> async/await 사용해도 된다.
  export const increaseAsync = () => (dispatch) => {
    setTimeout(() => dispatch(increase()), 1000);
  };
  export const decreaseAsync = () => (dispatch) => {
    setTimeout(() => dispatch(decrease()), 1000);
  };

  const onIncrease = () => {
    dispatch(increaseAsync());
  };
  const onDecrease = () => {
    dispatch(decreaseAsync());
  };

  return (
    <Counter number={number} onIncrease={onIncrease} onDecrease={onDecrease} />
  );

  // 예시2.
  export const fetchData = () => {
    // 이 액션 생성자(fetchData)는 함수를 반환한다.
    // 함수는 dispatch와 getState를 매개변수로 가진다.
    return async function (dispatch, getState) {
      const response = await APIadress.get("/data");

      // 요청이 완료되면 여기서 직접 dispatch 한다.
      dispatch({ type: "FETCH_DATE", payload: response });
    };
  };
  ```

  (2) redux-saga : 액션 모니터링 후 액션이 실행되면 제너레이터 문법을 활용하여 사이드 이펙트를 발생시킨다. 비동기 처리를 위해 자주 사용된다. 또한 put 메소드를 통해 디스패치 할 수 있다.

  ```js
  // 참고 : https://react.vlpt.us/redux-middleware/10-redux-saga.html
  // 1. 액션 생성 함수
  export const increaseAsync = () => ({ type: INCREASE_ASYNC });
  export const decreaseAsync = () => ({ type: DECREASE_ASYNC });

  // 2. 사가 생성
  function* increaseSaga() {
    yield delay(1000);
    yield put(increase()); // put은 특정 액션을 디스패치 해준다.
  }

  function* decreaseSaga() {
    yield delay(1000);
    yield put(decrease()); // put은 특정 액션을 디스패치 해준다.
  }

  // 3. 사가의 액션을 모니터링하는 함수 생성
  export function* counterSaga() {
    yield takeEvery(INCREASE_ASYNC, increaseSaga); // 모든 INCREASE_ASYNC 액션을 처리
    yield takeLatest(DECREASE_ASYNC, decreaseSaga); // 가장 마지막으로 디스패치된 DECREASE_ASYNC 액션만을 처리
  }

  // 4. 루트 사가 생성
  export function* rootSaga() {
    yield all([counterSaga()]); // all 은 배열 안의 여러 사가를 동시에 실행시켜준다.
  }

  // 5. 스토어 연결 시 미들웨어 적용
  const sagaMiddleware = createSagaMiddleware(); // 사가 미들웨어를 생성

  const store = createStore(
    rootReducer,
    composeWithDevTools(
      applyMiddleware(
        ReduxThunk.withExtraArgument({ history: customHistory }),
        sagaMiddleware
      )
    )
  );

  sagaMiddleware.run(rootSaga); // 6. 루트 사가를 실행, 이 떄 먼저 연결되어있어야 함
  ```

<br>

- Redux vs MobX vs ContextAPI vs Recoil vs Redux toolkit 비교

  (1) Redux : action, reducer, selector, store를 세팅하는 보일러플레이트 코드는 분명 유지보수에 큰 장점을 가지고 있기도 하지만, 상태의 개수가 적더라도 보일러플레이트 코드가 크기 때문에 불편함이 존재한다. 또한 리덕스의 경우 비동기 데이터 처리를 하기 위해서는 사가와 같은 별도의 라이브러리를 추가적으로 사용해야 한다. 또 데이터 관리에 대해 상당히 보수적인 접근방식을 취하고 있어 높은 러닝커브와 큰 보일러플레이트 코드를 가지고 있지만 확장 및 디버깅에 있어서는 엄청난 강점을 가지고 있다.

  (2) MobX : MobX의 경우 리덕스와 달리 store가 여러 개가 될 수 있어 분리가 용이해 편리할 수도 있는 반면 상태 변경시 다수의 스토어가 영향을 받을 수 있다. 또 리덕스와 다르게 스토어의 데이터를 액션의 발행없이 업데이트 할 수 있는데 구현은 쉽고 용이하지만 테스트나 유지보수의 측면에서는 문제를 일으킬 수도 있다. 그렇기에 장기적인 프로젝트, 유지보수 및 확장성을 고려해야 하는 프로젝트의 경우에는 적합하지 않다. 리덕스에 비해 러닝커브가 낮고 보일러플레이트 코드의 양 또한 적기 때문에 프로젝트의 규모가 크지 않은 경우 사용하기 좋다.

  (3) Context API : Context API는 리액트가 자체적으로 가지고 있다. 정적인 데이터 위주로 처리하거나 업데이트가 빈번하지 않을 때 적합하다. 빈번하고 복잡한 업데이트를 처리 시에는 비효율적이다.

  (4) Recoil : 리코일은 아톰과 셀렉터로 이루어져 있다. 아톰은 상태의 단위로, 유니크한 키값으로 구분된다. 해당 아톰을 구독하고 있으면 해당 컴포넌트들만 선택적으로 리렌더링 된다. 아톰의 상태변화는 순수함수를 통해 일어나는데, 이를 셀렉터라고 한다. 셀렉터에서는 비동기처리 뿐만 아니라 데이터 캐싱 기능도 제공하기 때문에 비동기 데이터를 다루기에도 용이하다. 하지만 상대적으로 최근에 나온 라이브러리이기 때문에 안정성 측면에서는 좋지 못할 수도 있다.

  (5) Redux toolkit : 리덕스는 큰 보일러 플레이트 코드를 가지고 있어 상태의 개수가 적어도 작성해야 할 코드가 많다. 또 비동기 데이터 처리를 하기 위해 별도의 라이브러리를 추가로 사용해야한다는 단점이 있다. 리덕스 툴킷은 리덕스가 공식적으로 만든 라이브러리로 다양한 내장 기능을 제공하고 있어 패키지 의존성이 적고 보일러 플레이트 코드가 적다는 장점이 있다.

<br>

- redux toolkit 사용법

  (1) store파일을 생성한다. 파일명은 store로 한다. store는 전역 상태 관리가 되는 모든 createSlice를 관리하는 곳이다. store에 reducer에 만들어진 createSlice name을 import해서 넣어줘야한다. 또한 store를 만든 뒤 루트 디렉토리 컴포넌트(ex App컴포넌트)를 Provider 컴포넌트로 감싸 Provider prop를 store={store}로 지정해야한다. 또한 store는 프로젝트에 하나만 존재해야한다.

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

  (2) createSlice파일을 생성한다. 파일명은 상관없다. 전역 state와 전역 state를 조작하는 함수를 저장할 createSlice를 만들어야한다. 이 createSlice는 프로젝트에 여러 개가 존재할 수 있다. 전역으로 관리 할 state당 하나가 생성되는 것이다.

  (3) createSlice에 initialState는 그냥 state라고 생각하면 된다. 또한 reducers는 이 initialState를 조작할 액션(state값을 조작하는 함수 혹은 state값 재할당 등등 state를 변화시킬 행동)이라고 생각하면 된다.

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

  (4) createSlice에 저장 된 action인 reducers로 state를 업데이트하기 위해서는 useDispatch hook을 사용한다. 디스패치라는 이름에서 알 수 있듯이 파라미터를 담아 보내는 역할을 한다. 파라미터를 보내면 createSlice 내부에 reducers에 전달되어 state를 업데이트 시키는 것이다. 또한 initialState나 업데이트 된 state를 사용할 때는 useSelector hook으로 가져와 사용한다.

  (5) store에 devTools : 환경변수를 이용해서 현재 서버가 개발자모드인지 프로덕션모드인지를 구분해준다. 보통 boolean타입으로 활용하여 구분한다. devTools: process.env.NODE_ENV !== 'production' 과 같이 사용하는데 이 뜻은 로컬에 있는 환경 변수를 사용하면 true가 되면서 개발 모드가 활성화 된다.

  (6) store에 middleware : middleware: (getDefaultMiddleware) => getDefaultMiddleware({ serializableCheck: false }) 와 같이 사용한다. 클라이언트와 서버 중간에 위치해서 중간 기능을 넣는 역할을 한다. getDefaultMiddleware() 는 기본 미들웨어를 적용하기 위해 사용한다. 위와 같이 작성하면 기본 미들웨어에 사용자 미들웨어를 추가하여 함께 사용한다는 뜻이다. 기본 미들웨어는 불변성 검사 미들웨어와 직렬화 기능성 검사 미들웨어가 있다. 불변성 검사 미들웨어는 값을 직접 수정한 경우 (mutation) error를 발생시키는 역할 (redux-immutable-state-invariant)을 하며 직렬화 가능성 검사 미들웨어는 직렬화 할 수 없는 Promise와 같은 객체를 받았을때 error를 발생시키는 역할을 한다.

<br>

- 리덕스가 state를 업데이트시킬때 리액트에서는 해당 상태값을 어떻게 감지하는지?

  dispatch를 통해 변경한 state는 이전의 state와 참조 값이 다르기 때문에 virtualDOM에서 상태가 업데이트 됨을 감지할 수 있다.

<br>

- 어떤 기준으로 상태관리 여부 구분하는지

  1. Props Drilling이 발생

  2. 여러 컴포넌트에서 공통적으로 사용해야하는 상태의 경우

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

- 전역 상태 관리 라이브러리는 언제 써야 할까?

  Redux, MobX, Recoil, Jotai, Zustand 등의 전역 상태 관리 라이브러리를 때때로 Context와 비교하기도 한다. 하지만 `상태 관리 라이브러리`와 `Context`는 완전히 별개의 개념임을 잘 이해해야한다

  Context는 전역 상태 관리를 할 수 있는 수단일 뿐이고, 상태 관리 라이브러리는 상태 관리를 더욱 편하고, 효율적으로 할 수 있게 해주는 기능들을 제공해주는 도구이다.

  예를 들어, Redux의 경우에는 액션과 리듀서라는 개념을 사용하여 상태 업데이트 로직을 컴포넌트 밖으로 분리 할 수 있게 해주며, 상태가 업데이트 될 때 실제로 의존하는 값이 바뀔 때만 컴포넌트가 리렌더링 되도록 최적화를 해줍니다. 만약 Context를 쓴다면, 각기 다른 상태마다 새롭게 Context를 만들어주어야 하는데, 이 과정을 생략할 수 있기에 편리하다.

  MobX의 경우엔 Redux와 마찬가지로 상태 업데이트 로직을 컴포넌트 밖으로 분리할 수 있게 해주고, 함수형 리액티브 프로그래밍 방식을 도입하여 mutable한 상태가 리액트에서도 잘 보여지게 해주고 상태 업데이트 로직을 더욱 편하게 작성할 수 있게 해주며 최적화도 잘 해준다.

  Recoil, Jotai, Zustand의 경우엔 Context를 일일이 만드는 과정을 생략하고 Hook 기반으로 아주 편하게 전역 상태 관리를 할 수 있게 해주며 최적화 기능도 제공한다.

  전역 상태 라이브러리는 결국 상태 관리를 조금 더 쉽게 하기 위해서 사용하는 것이며 취향에 따라 선택해서 사용하면 된다.

<br>

### # **리액트 패턴이란?**

<br>

- 리액트 패턴

  기능만을 담는 컴포넌트와, 뷰만을 담는 컴포넌트로 분리하는 패턴이다. 담당하는 기능이 분리되어 있기 때문에 가독성이 높고, 유지보수가 쉽고 재사용성이 뛰어나다. 또 같은 state를 다른 container에게 props 내림으로 상태를 공유 할 수 있다.

<br>

- 프레젠테이셔널 컴포넌트(present component)

  뷰를 담는 컴포넌트이다. 상태가 없는 컴포넌트(stateless component)라고도 불린다. state를 직접 조작하지 않으며, 컨테이너 컴포넌트가 내려준 props를 사용한다. state 관련 훅을 사용하지 않고 state를 거의 가지지 않으며 만약 state를 가지고 있다면 데이터에 관한것이 아닌 ui 상태에 관한 state를 가지고 있다.

<br>

- 컨테이너 컴포넌트(container component)

  기능을 담는 컴포넌트이다. 상태가 있는 컴포넌트(stateful component)라고도 불린다. 어떤 동작을 하고 어떤 로직을 수행하는지와 관련이 있다. 마크업을 하지 않고 스타일을 사용하지 않는다. 데이터와 데이터 조작에 관한 함수를 만들고 프레젠테이셔널 컴포넌트에 제공한다.

<br>

- 리액트 패턴의 장점

  컨테이너와 프레젠테이셔널 컴포넌트를 나누게 되면 뷰와 로직을 컴포넌트 단위로 나누게 되어 가독성이 높아지고 유지보수가 쉬워진다. 하지만 뷰와 로직을 무조건 나누어 사용하는 것이 아닌 재사용하지않는 컴포넌트나 로직과 UI가 밀접하게 관련이 있는 컴포넌트의 경우 나누어 사용하는 것이 오히려 가독성이나 유지보수를 어렵게 할 수 있으므로 상황에 맞게 나누어 사용하는 것이 좋다.

<br>

### # **Headless UI 라이브러리**

<br>

- Headless UI란?

  프론트엔드 웹 개발을 하다보면 생산성 향상을 위해 UI 라이브러리를 사용하고는 한다. 일반적인 Component 기반 UI 라이브러리는 개발자가 해당 컴포넌트를 바로 사용할 수 있도록 고유의 스타일이 적용되어있는데 거의 모든 사용되는 서비스 디자인에 맞게 커스텀이 필요하게 된다. 하지만 커스텀하는 과정 중 한계에 부딪히는 경우가 발생할 수 있고 커스텀이 까다로운 경우도 발생할 수 있다. 이러한 경우 Headless UI 라이브러리를 사용할 수 있다.

<br>

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

<br>

- Headless Component 만들기

  - Compound Component

    사용되는 컴포넌트들의 상태(state) 값을 공유할 수 있게 만들어주는 패턴이다. (ex ContextAPI 활용)

  - Function as Child Component

    자식에 어떤 것이 들어올지 예상할 수 없기 때문에 children prop으로 받아 그대로 전달한다.

  - Custom hooks

    React를 사용해본 사람이라면 가장 익숙할 법한 Custom hooks이다.

<br>

### # **Bundling과 code splitting**

<br>

- 번들링(Bundling)

  서로 연관있는 여러 파일을 하나의 파일로 병합(js, img, scss 등)하는 것을 말한다. 하나로 병합 된 번들로 요청/응답을 받음으로써 HTTP 요청 횟수를 줄일 수 있다. 또한 번들링은 코드 스플리팅과도 연관이 있는데 코드 스플리팅을 통해 번들을 분할하여 메인 번들과 번들인 조각 청크로 번들을 쪼갤 수 있다. 쪼개진 번들은 필요에 따라 순차적으로 클라이언트에 전달된다. 대표적인 모듈 번들러로 웹팩이 있고 그 외에 바이트, 롤업, 파셀 등도 있다.

<br>

- 코드 스플리팅(code splitting)

  프로젝트 규모가 커지면 번들 사이즈도 커지게 된다. 그렇게 되면 성능 저하가 일어날 수 있다. 이럴 때 코드 스플리팅을 사용한다. 코드 스플리팅은 하나의 번들을 여러 개의 번들(청크)로 나누어준다. 코드 스플리팅으로 번들을 나눈 후 실제 로드될 화면에 필요한 번들 파일만 불러오고 나머지 번들 파일은 호출하지 않고 지연시키는 비동기 로딩으로 로딩 속도를 향상시킬 수 있다.

<br>

- react에서의 코드 스플리팅 방법

  (1) dynamic import 문법 사용 : 자바스크립트 함수 비동기 로딩 시 import() 함수 형태로 메서드 안에서 사용하게 되면 필요할 때 해당 스크립트를 불러와서 사용할 수 있다. import를 함수로 사용하면 Promise를 반환한다. nextjs에서는 기본적으로 page 디렉토리 내부 컴포넌트들은 빌드 단계에서 자동으로 코드스플리팅된다. 또한 다른 컴포넌트들은 next/dynamic의 dynamic 메소드를 사용하여 구현할 수 있다. 첫번째 인자로 import 함수, 두번째 인자로 옵션을 지정할 수 있다. 옵션에서는 로딩 시 보여줄 UI, SSR 여부 등을 지정할 수 있다.

  ```js
  // react
  const onClick = () => {
    import("./subPage").then((result) => result.default());
  };

  // next
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

### # **React Native**

<br>

- 리액트 네이티브 개발을 해본 적이 있는지

  부트캠프 교육 시 한달 정도 기업협업에 나가 경험해 본 경험이 있다. react native, typescript, mobx 등의 기술을 사용했었다. 마일리지를 이용하여 기프티콘을 구매하는 서비스였는데 기능을 추가하는 작업을 했었다. 카카오맵API, 웹뷰를 활용하여 지도 주소 검색 기능, 지번 도로명 주소 변환, 새 페이지 추가, 작은 버그 수정 등의 작업을 했었다.

<br>

- 웹뷰

  웹뷰는 모바일 앱 어플리케이션의 일부 부분 및 페이지를 웹 어플리케이션 및 웹 페이지로 제공하는 기능을 말한다. 안드로이드와 iOS 모두에서 제공하고 있다. 웹뷰를 사용한 장점은 배포 주기를 빠르게 가져갈 수 있다는 점이다.

<br>

- 웹뷰 사용 경험

  웹뷰에 보여질 카카오 map api, 버튼 등을 생성하여 프로젝트를 따로 만들어 준 뒤 배포하고 웹뷰를 생성할 프로젝트에서 WebView 컴포넌트와 WebView 컴포넌트의 source 옵션을 통해 배포된 프로젝트와 연결하고 다른 옵션들을 통해 웹뷰에서 받은 주소 데이터를 저장하고, 로딩 시 스피너를 구현하였다.

<br>

### # **Progressive rendering이란 무엇인가요?**

<br>

- 서버에서 중요한 컨텐츠를 렌더링한 후, 중요하지 않은 콘텐츠를 기다리지 않고 클라이언트로 스트리밍하는 기술이다. 그런 다음 서버에서 렌더링되면 나중에 중요하지 않은 콘텐츠를 스트리밍한다. 관련 기술로는 Image Lazy Loading, DOMContentLoaded 이벤트의 사용 등이 있다.

<br>

### # **JSX(JavaScript XML)**

<br>

- JSX는 Javascript에 XML을 추가하여 확장한 문법이다. 공식적인 자바스크립트 문법은 아니며 브라우저에서 실행하기 전 번들링 과정 중 바벨을 사용하여 일반 자바스크립트로 변환된다. JSX문법의 사용은 react의 특징 중 하나이다.

<br>

### # Link, NavLink, useNavigate 차이

<br>

- Link

  페이지 이동 시 사용

  ```javascript
  <Link to="경로">내용</Link>
  ```

<br>

- NavLink

  페이지 이동 시 사용, Link 와의 차이점은 자체적으로 boolean을 반환하는 isActive 속성을 가지고 있으며 NavLink 컴포넌트 to 프로퍼티에 할당 된 url로 이동 시 isActive는 true가 된다. 이 boolean 값을 사용하여 페이지로 이동 시 스타일을 동적으로 변경시켜줄 수 있다.

  ```javascript
  <NavLink
    to="/"
    className={({ isActive }) => (isActive ? classes.active : undefined)}
  >
    Home
  </NavLink>
  ```

<br>

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

### # **비즈니스 로직을 리액트를 사용 시 어떻게 모듈화시키는게 좋은지?**

<br>

- 일단 전체적인 구조는 뷰와 로직을 분리하는 것이 가장 좋다고 생각한다. return 함수 안 렌더단에서는 컴포넌트를 적극적으로 활용하여 가독성을 최대한으로 끌어올리고 로직이 최대한 들어가지 않도록 작성하는 것이 중요하고 return 함수 외부에 로직이 집중되도록 작성하는 것이 중요하다고 생각한다. 또한 로직단에서도 중복 로직이나 너무 긴 로직의 경우 custom hook이나 별도의 함수로 빼서 가독성을 높이는 것이 중요하다고 생각한다. 또한 return 함수 상단 로직단은 관심사 별(서버 통신 관련, 돔 조작 관련, state 관련, 이벤트 핸들러 등)로 로직을 나누고 공통 로직인지 개별 로직인지 구분하여 컴포넌트 내부에 작성하거나 별도로 유틸 파일을 만들어 관리한다.

<br>

### # **성능을 측정해 본 적이 있는지, 어떤 방법을 사용해보았는지?**

<br>

- 함수 성능 측정

perpomance.now, console.time

<br>

- 컴포넌트 렌더링 속도 및 리렌더링 측정

react developer tools 크롬 익스텐션 설치 후 개발자 도구에 profiler탭 활용 (ms 단위)

<br>

- 웹 페이지 퍼포먼스, 웹접근성, SEO, 표준 모범 사례를 따르고 있는지 확인하는 Best Practices 측정

개발자 도구에 Lighthouse탭 활용

<br>

### # **lighthouse을 활용한 사이트 퍼포먼스 측정**

<br>

- 크롬 개발자 도구에 lighthouse를 사용하여 사이트 퍼포먼스를 측정해보았다. 실제 성능을 측정하는 Performance, 표준 모범 사례를 따르고 있는지 측정하는 Best Practices, 웹과 네이티브 앱의 이점을 모두 가진 서비스인지 체크하는 Progressive Web App, 웹 접근성을 측정하는 Accessibility, 검색 엔진 수집 최적화를 측정하는 SEO 등이 있다.

<br>

### # 성능 개선 지표

<br>

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

    FCP는 페이지 로드가 시작된 후 뷰포트내의 의미있는 콘텐츠 일부가 처음 화면에 렌더링 될 때까지의 시간을 측정한다. FCP는 사용자가 화면에서 무슨 일이 일어나고 있구나 라고 인지하는 시점을 알려주는 아주 중요한 지표이다.

  - LCP (Largest Contentful Paint), 25%

    LCP는 뷰포트의 컨텐츠 중 가장 큰(넓은) 영역을 차지하는 이미지나 텍스트 요소가 처음 로딩되는 시점을 의미한다. 가장 큰 영역을 차지하는 요소를 페이지의 주요 콘텐츠로 판단하며, 이 지표를 기준으로 사용자 중심의 페이지 로드 속도를 판단하고 있다.

  - TBT (Total Blocking Time), 30%

    TBT는 TTI와 비슷한 측정 기준을 갖고 있다. 페이지가 클릭, 키보드 입력 같은 사용자와 상호 작용하지 못했던 시간의 총합을 측정한다. 여기서 말하는 차단 시간(Blocking Time)은 Long Task(50ms를 초과하는 Task)로 인해 메인 스레드가 오랫동안 점유되어 사용자와 상호작용 하지 못하는 시간을 의미한다. FCP와 TTI 사이에 일어난 작업만을 기준으로 한다.

  - CLS (Cumulative Layout Shift), 15%

    CLS는 사용자가 예상하지 못한 레이아웃 이동을 경험하는 빈도를 정량화해서 시각적인 안정성을 판단한다. 모든 레이아웃의 이동이 나쁜 것은 아니라고 명시하며 “사용자가 예상하지 못한” 이란 이동을 측정하는 것이 핵심이라고 하고 있다. 라이트하우스 지표중 가장 낮은 비중을 갖고 있지만 절대 얕봐서는 안되는 지표 중 하나이다.

  - SI (Speed Index), 10%

    Speed Index는 뷰포트내의 콘텐츠가 눈에 띄게 채워지는 속도를 보여주는 페이지 로드 성능을 측정한다. 콘텐츠가 시각적으로 표시되는 진행 속도를 측정(ex. 리로드되는 페이지의 비디오를 캡쳐하여 프레임 간의 속도를 계산)하는 것이다.

  - TTI (Time To Interactive), 10%

    TTI는 페이지가 완전히 사용자와 상호 작용할 수 있는 상태가 되는데 걸리는 시간을 의미한다.

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

### # **useMemo, useCallback에 대한 설명**

<br>

- 메모제이션이란?

일단 useMemo와 useCallback에서는 메모이제이션이라는 개념이 나오는데 메모이제이션이란 이전 값을 메모리에 저장해두어 동일한 계산의 반복을 제거해 빠른 처리를 가능하게 하는 기술이다. useMemo는 메모이제이션 된 값을 반환하고 useCallback은 메모이제이션 된 함수를 반환한다. useMemo와 useCallback은 의존성 배열에 넘겨준 값이 변경되었을 때만 메모리제이션된 값을 다시 계산하고 아닌 경우 동일한 값을 반환한다.

<br>

- useMemo를 사용해야 하는 경우

- 값의 연산 비용이 높은 경우 리렌더링 비용 절감이 필요한 경우

- 컴포넌트 내부에서 동일한 계산을 계속해서 수행하여 최적화가 필요한 경우

- 계산 시 사용하는 특정 값이 변경 될 때만 해당 값을 다시 계산하고 싶을 때 사용

- map 혹은 filter 등을 사용하여 UI를 업데이트할 때 리렌더링 이후 동일한 참조를 사용할 가능성이 높은 경우

- 자식 컴포넌트와 관계없는 state 업데이트로 인한 부모 컴포넌트 리렌더링 발생 시 자식 컴포넌트 자체를 래핑하여 리렌더링 방지, 자식 컴포넌트는 자신이 사용하는 props를 의존성 배열에 넣어 해당 값이 변경될 때만 새로 컴포넌트가 생성될 수 있도록 함

<br>

- useCallback을 사용해야 하는 경우

- 함수 자체가 매우 복잡하거나 다시 계산하는데 드는 비용이 높은 경우

- 자식 컴포넌트에 함수를 props로 넘길 때 함수의 동등성(참조 주소를 동일하게 유지)을 유지해주기 위해 사용

- 함수 내부에서 사용하는 props가 변경될 때만 해당 함수를 재생성하고 싶을 때 사용

- callback ref가 필요할 때 사용, 자식 컴포넌트의 ref를 다룰 때 forwardRef를 사용하는데 이 때 useEffect로 ref를 핸들링하면 자식 컴포넌트 내부 렌더링이 완료되기 전 ref의 값은 null이 되어 문제가 발생한다. 이럴 때 callback ref를 사용하여 해결할 수 있다. 간단하게 기본적으로 ref는 렌더링 여부를 체크할 수 없는데 useCallback을 활용하여 렌더링과 연관시켜 작업할 수 있게 되는 것이다. 즉 컴포넌트 생명주기에 바인드되던 ref를 DOM 노드의 생명주기로 바인드시키는 방식이다.

<br>

- useMemo와 useCallback을 사용하지 말아야 하는 경우

- 연산이 복잡하지 않은 값이나 함수의 경우, 연산이 복잡하지 않은 경우 메모이징하는 것이 오히려 메모리 낭비가 될 수 있다.

- 의존성 배열의 값이 자주 변화하는 경우, 자주 변하는 값이나 함수의 경우 메모이징하는 의미가 없다.

- 의존성 배열의 요소가 많은 경우, 의존성 배열의 요소가 많은 경우 자주 변하는 값이나 함수일 확률이 높기 떄문에 메모이징하는 의미가 없다.

<br>

### # **HOC(High Order Component)가 무엇인지 아는지?**

<br>

- HOC(High Order Component)는 고차 컴포넌트이며 다른 컴포넌트를 감싸는 리액트 컴포넌트다. 리액트 컴포넌트를 인자로 받아서 새로운 리액트 컴포넌트를 반환하는 함수로 볼 수 있다. 비지니스 로직을 담당하는 컨테이너 컴포넌트와 뷰를 담당하는 프레젠테이셔널 컴포넌트를 분리하여 사용 할 때, 컨테이너 컴포넌트를 고차 컴포넌트로 만들어서 사용한다.

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

### # **고차함수(Higher order function)란?**

- 고차 함수는 함수를 인자로 전달받거나 함수를 결과로 반환하는 함수를 말한다.

<br>

### # **컴포넌트와 엘리먼트의 차이점은?**

<br>

- 엘리먼트

  DOM element(태그)를 나타내는 일반적인 객체

<br>

- 컴포넌트

  props를 받아 DOM 엘리먼트의 정보를 담은 react 엘리먼트 객체를 출력하는 함수 혹은 클래스이다. react에서 index 파일 내부 ReactDOM.createRoot 함수를 통해 컨테이너 돔(ex `<div id="root"></div>`)을 지정하고 컴포넌트에서 return 되는 react 엘리먼트 객체를 컨테이너 돔의 메소드인 render 메소드를 통해 컨테이너 돔 내부에 렌더링한다.

  ```javascript
  // 컨테이너 돔 지정
  const root = ReactDOM.createRoot(document.getElementById("root"));

  const element = <h1>Hello, world</h1>; // DOM 엘리먼트의 정보를 담은 리액트 엘리먼트 객체 생성
  root.render(element); // 컨테이너 돔 내부에 리액트 엘리먼트 렌더링
  ```

<br>

### # **useEffect에서 unmount 하는 방법**

<br>

- useEffect에 의존성 배열을 넣지 않은 빈 의존성 배열을 넣은 상태에서 return 값을 지정하게 되면 componentWillUnmount 역할을 할 수 있다. 만약 의존성 배열을 넣은 후 return 값을 지정하게 되면 의존성 배열이 바뀌기 전 사이드 이펙트를 실행할 수 있다.

<br>

### # **useEffect와 useLayoutEffect 차이**

<br>

- 둘의 사용법은 완전히 동일하다. 둘의 차이점은 useEffect는 DOM이 화면에 그려진 후(브라우저 렌더링 단계 중 페인트 완료 후)호출되고 useLayoutEffect는 DOM을 그리기 전(렌더, 커밋 페이즈 단계가 완료 된 후 브라우저의 페인트 단계 전) 호출된다. 예를 들어 useEffect 내부에서 state를 업데이트하여 DOM에 내용을 채운다고 가정했을 때 DOM을 렌더링 한 후 useEffect를 호출하여 state를 업데이트하고 리렌더링을 수행하여 DOM에 내용을 채우는 것이다. 하지만 DOM에 갯수가 많아지고 복잡해지면 렌더링 시간이 증가하게 되어 useEffect 사용 시 state가 업데이트 되지 않은 상태를 사용자가 볼 위험이 생긴다. 이런 경우 useLayoutEffect를 사용하여 문제를 해결할 수 있다.

  ```
  // useEffect
  (1) `<div>그의 이름은 이며, 나이는 0살 입니다.</div>` 를 페인트
  (2) useEffect 이펙트 내부의 setAge(31), setName("재민") 호출
  (3) 재렌더링 수행 -> `<div>그의 이름은 재민이며, 나이는 31살 입니다.</div>`

  // useEffectLayout
  (1) useEffectLayout 이펙트 내부의 setAge(31), setName("재민") 호출
  (2) 재렌더링 수행 -> `<div>그의 이름은 재민이며, 나이는 31살 입니다.</div>`
  ```

<br>

### # useReducer가 무엇인가?

<br>

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

### # **SVG를 스타일링하는데 익숙하신가요?**

<br>

- SVG 스타일링을 위해 svgr/webpack 패키지를 활용하여 SVG를 컴포넌트로 사용하였다. SVG를 컴포넌트로 사용해서 크기, 색상 등 커스텀을 가능하게 만들어 재사용성을 증가시켰다.

<br>

### # **렌더함수 안에서 hooks를 사용하면 안되는 이유?**

<br>

- react 공식 문서에 나와있는 이유로는 최상위에서만 hook을 호출해야 컴포넌트가 렌더링 될 때마다 항상 동일한 순서로 Hook이 호출되는 것이 보장된다고 한다. 예를 들어 useEffect의 경우 DOM의 렌더링 이후 실행되는데 만약 렌더 함수 스스로 useEffect를 실행하게 되면 이 useEffect와 관련 된 DOM이나 함수들이 보장할 수 없는 값들을 출력할 수 있다. 그렇기 때문에 렌더 함수 외부에 hook을 호출하여 react가 권장하는 순서대로 DOM의 렌더링과 hooks이 동작할 수 있도록 해야한다.

<br>

### # 리액트는 어떻게 렌더링되죠? (확실 x, 검증 필요)

<br>

(1) React.createDOM을 통해 컨테이너 돔을 지정한다.

(2) 컨테이너 돔의 메소드인 render 함수가 호출된다. render 함수의 역할은 컴포넌트가 반환하는 react 엘리먼트 객체를 React DOM으로 렌더링하는 역할을 한다.

(3) 컨테이너 돔부터 시작해서 마주친 컴포넌트의 react 엘리먼트 객체의 타입을 검사하여 업데이트가 필요한 컴포넌트를 찾는다.

(4) 업데이트가 필요한 컴포넌트를 만나면 props를 제공하여 새로운 react 엘리먼트 객체를 얻는다.

(5) 가상 돔을 통해 새로운 react 엘리먼트 트리를 이전 react 엘리먼트 트리와 비교하여 바뀐 부분만 실제 DOM에 적용시킨다.

<br>

### # 커스텀 훅(custom hook)

<br>

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

### # **로그인 버튼을 누른 후 처리가 지연 되고 있는 순간에 다른 UI 버튼을 클릭한다면 처리는 어떻게 되는가? 비동기 처리라고 한다면 이건 문제가 있지 않은가?**

<br>

- 대부분 로그인이 필요한 서비스의 경우 로그인 하지 않은 사용자가 UI를 조작하게 되면 로그인 페이지로 리다이렉트 시키는데 만약 비동기 통신을 통해 액세스 토큰을 받아오는 로그인 과정이 지연되는 경우 스피너같은 로딩 화면을 띄워 토큰을 받아오기 전 사용자가 다른 UI를 누를 수 없도록 방지할 것 같다. 만약 예외 처리를 하지 않은 경우 API를 요청한 컴포넌트가 언마운트되면 이후 동기적으로 처리하는 로직에서 문제가 발생하거나 메모리 누수가 발생할 수 있다.

<br>

### # API 요청 처리 전 컴포넌트 언마운트

- 만약 특정 컴포넌트 내에서 API 요청 후 페이지를 이동하여 컴포넌트가 언마운트되는 경우 해당 API가 POST 요청이라면 요청 후 서버에서 처리되기 때문에 상관없지만 GET 요청이라면 문제가 발생할 수 있다. 대부분 GET 요청 이후 받아오는 데이터를 동기적으로 처리하는데 이 과정에서 이슈가 발생할 수 있고 메모리 누수가 발생할 수 있다.

<br>

### # **무작위 데이터 테스트는 어떻게 하시나요?**

<br>

- 제이슨 제너레이터(https://json-generator.com/)와 같은 무작위 더미데이터를 생성해주는 사이트를 활용하여 무작위 데이터를 만든 뒤 테스트를 진행할 수 있을 것 같다.

<br>

### # **제어 컴포넌트와 비제어 컴포넌트 차이**

<br>

- 제어 컴포넌트

  컴포넌트의 state나 props로 입력 폼 값이 제어되는 컴포넌트이다. 예시로 input의 value 값을 useState로 값을 업데이트 시키는 것이 대표적인 제어 컴포넌트의 예시이다. 데이터와 UI가 항상 동기화되어 입력 값 발생 시 계속 리렌더링 되어 최신화가 유지된다. 유효성 검사나 조건부 버튼 활성화에 사용한다.

  ```jsx
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

<br>

- 비제어 컴포넌트

  DOM 자체에서 입력 폼 데이터를 다루는 컴포넌트이다. 예시로 input에 ref 속성을 할당하여 입력 폼을 제출할 때 값을 업데이트 시키는 것이 대표적인 비제어 컴포넌트의 예시이다. 데이터와 UI가 동기화되어 있지 않아 입력 값 발생 시 리렌더링 되지 않고 입력 폼을 제출할 때 렌더링된다. 일회성 정보 검색이나 제출 시 값 검증에 사용한다.

  ```jsx
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

### # **리액트의 렌더링 성능 향상을 위해 어떻게 해야 하나?**

<br>

(1) 렌더링 성능 측정 : react developer tools 익스텐션으로 컴포넌트 렌더링 성능을 측정하고 구글 라이트하우스를 활용하여 FCP, LCP, TBT, CLS, SI, TTI 등의 성능을 측정한다. 구글 라이트하우스 기준으로 FCP는 최소 3초 LCP는 최소 4초 이내에 들어야한다. 해당 시간이 벗어나면 사용자가 서비스에서 이탈할 확률이 증가한다. 또한 함수 성능 측정은 perpomance API나 console.time 메소드를 활용하여 측정하고 개선할 수 있다.

(2) useMemo, useCallback : useMemo, useCallback 등을 사용하여 값이나 함수를 메모이제이션 해 사용한다.

(3) 코드 스플리팅 : Lazy와 Suspense를 사용하여 코드 스플리팅하고 번들의 크기를 줄여 당장 필요한 컴포넌트만 우선적으로 렌더링하도록 한다.

(4) 이미지 사이즈 최적화 : 이미지를 압축율이 좋은 이미지 포맷으로 변경한다. 예를 들면 avif 포맷으로 변경할 수 있다. 하지만 이와 같은 경우 해당 이미지 포맷의 호환되는 브라우저 확인은 필수이다. 다만 nextjs에서는 이미지 컴포넌트가 자동으로 사용자 브라우저에 호환되는 이미지 포맷으로 변환해주기 때문에 확인이 불필요하다. 또한 이미지를 사용자에게 보여지는 레이아웃 크기를 고려하여 사이즈를 줄인다. 예를 들면 canvas를 사용하여 이미지를 리사이징해서 사용 및 저장하거나 img 태그의 srcset 속성을 활용하여 뷰포트 별 이미지를 제공할 수 있다. 또한 고정 사이즈를 사용하여 리플로우를 최소화할 수 있다. 또한 nextjs의 경우 기본적으로 사용하는 이미지 로더를 squoosh에서 sharp로 바꾸는 것만으로도 이미지 최적화에 도움이 된다. -> 이미지 최적화 라이브러리인 sharp의 경우 next15 버전부터 자동으로 sharp를 사용하므로 수동으로 설치할 필요가 없다.

(5) 이미지 레이지 로딩 : IntersectionObserver API와 같이 뷰포트를 감지하는 API를 활용하여 해당 이미지 보여져야 할 때 서버에 요청을 보내 이미지를 가져온다.

(6) 애니메이션 최적화 : 애니메이션은 리플로우와 리페인트를 발생시키는 원인이다. witdh와 같은 크기를 직접적으로 변경하는 애니메이션의 경우 cpu에서 처리하게 되는데 transform의 scale을 활용하여 크기를 변경시키는 경우 gpu에서 처리하게 되므로 성능 향상에 도움이 된다.

(7) 웹폰트 경량화 : 사용할 글자만 남겨놓은 서브셋 파일을 활용하여 웹폰트 파일의 크기를 줄인다.

(8) state와 props변경 최소화 : state와 props의 변경을 최소화하여 리렌더링을 최소화한다. 또한 한 컴포넌트에 state를 몰아서 사용하는 경우 state 변화가 빈번하게 발생할 수 있기 때문에 state를 사용하는 컴포넌트 내부에 작성할 수 있도록 한다. 또한 객체 형태의 state의 경우 객체 프로퍼티 중 하나만 사용하는 컴포넌트가 있거나 하는 경우 분리해서 사용하는 것이 좋다.

(9) 프롭시 드릴링(props drilling) 피하기 : 부모 컴포넌트에서 자식 컴포넌트로 전달하는 프롭스의 깊이가 깊어질수록 성능에 좋지 않다. 부모의 state가 변경되면 자식 컴포넌트 모두 리렌더링되기 때문이다. 또한 해당 props를 사용하지 않는 컴포넌트를 거치는 경우도 생기며 컴포넌트끼리 결속되어 재사용성이 떨어진다. 개인적으로 2번 이상 넘겨주지 않도록 기준을 정해서 작업하고 있다. 넘어가는 경우 전역 상태 관리 라이브러리를 사용하여 해결할 수 있다.

(10) 패키지 정리 : 사용하지 않는 패키지 제거 및 dependencies와 devDependencies를 잘 구분하여 디벨롭 환경에서만 필요한 패키지가 번들에 포함되지 않도록 함

(11) 캐싱 데이터 사용 : 자주 사용되는 정적 데이터의 경우 캐싱 데이터를 사용하여 불필요한 리패치를 막는다.

<br>

### # **key는 어떻게 사용되나요?**

<br>

- index값은 사용하지 않는다. 만약 배열의 순서가 수정될 경우 중복되는 key값이 발생할 수 있기 때문이다. 그렇기 때문에 유니크한 값을 사용하기 위해 map 메소드를 사용한 배열 요소가 id값을 가지고 있다면 id값을 사용하도록 하고 있다. id값이 존재하지 않다면 가지고 있는 다른 유니크한 값을 사용하거나 배열 요소 자체를 문자열로 변환 후 조합하여 사용하기도 한다.

<br>

### # **prop drilling은 무엇이고 어떻게 피할 수 있나요?**

<br>

- prop drilling은 부모 컴포넌트에서 하위 컴포넌트로 props를 전달하는 것을 과정을 말한다. prop drilling이 깊어지게 되면 해당 props의 추적이 어려워져 유지보수가 힘들어지고 실제 props를 사용하는 컴포넌트 사이에 props를 사용하지 않는 컴포넌트도 포함될 수 있다. 또한 부모에 props가 변경되면 하위 컴포넌트들도 모두 리렌더링 되기 때문에 성능 저하에 원인이 될 수 있다. 그렇기 떄문에 prop drilling을 최대한 피해주는 것이 좋은데 prop drilling을 피하는 방법으로는 대표적으로 전역 상태 관리 라이브러리를 사용하거나 컴포넌트를 잘게 쪼개지 않고 가장 가까운 부모 컴포넌트와 props를 공유할 수 있도록 유도하는 것이다.

<br>

### # **얕은 비교(shallow equal)와 깊은 비교(deep equal)에 대해서 설명해주세요.**

<br>

- 얕은 비교

  얕은 비교는 실제 내부 값까지 비교하는 것이 아닌 참조하는 값에 메모리 주소를 비교한다. react의 경우 state, props, hook의 의존성 배열 값 등은 참조 주소를 비교하는 얕은 비교를 통해 값의 변화를 감지한다.

<br>

- 깊은 비교

  객체 내부 값까지 비교한다.

<br>

### # 리액트 에러바운더리 컴포넌트와 서스펜스 컴포넌트

<br>

- ErrorBoundary 컴포넌트는 자식 컴포넌트의 런타임 시 에러가 발생하는 경우 fallback 속성에 할당한 대체 레이아웃을 제공하기 위해 사용한다. 또한 react query 사용 시 useErrorBoundary 옵션을 true로 설정하여 isError를 대체할 수 있다. 또 ErrorBoundary는 Suspense와 함께 많이 사용된다. Suspense 컴포넌트는 자식 컴포넌트의 렌더링 지연 시 fallback 속성에 할당한 대체 레이아웃을 제공하기 위해 사용한다. React.lazy와 함께 코드스플리팅을 위해 많이 사용된다. 또한 ErrorBoundary와 마찬가지로 react query와 함께 사용할 수 있다. useQuery에 suspence 옵션을 true로 설정하여 isLoading을 대체할 수 있다. nextjs 13 버전에서는 Suspense 컴포넌트를 loading 파일, ErrorBoundary 컴포넌트를 error 파일로 대체해서 사용할 수 있다.

<br>

### # **리액트 라우터같은 Client Side Routing 에 대해서 설명하세요.**

<br>

- 라우팅은 사용자가 웹사이트의 다른 페이지로 이동하는 프로세스를 말한다. 서버 사이드 라우팅의 경우 페이지 이동 시 모든 데이터를 새로 요청하게 되어 화면 깜빡임이 발생한다. 반면 클라이언트 사이드 라우팅은 실제 페이지를 이동하는 것이 아닌 주소 값만 변경한 후 HTML5 History API가 만들어내는 임의의 히스토리 기록을 만들어 해당 페이지로 이동하며 모든 데이터가 아닌 필요한 추가 데이터만 요청하여 라우팅 속도도 빠르고 화면 깜빡임이 발생하지 않는다. react와 마찬가지로 nextjs에서도 Link 컴포넌트를 사용하면 클라이언트 사이드 라우팅을 할 수 있다. 반면 a태그를 사용하면 서버 사이드 라우팅한다.

<br>

### # **react-query**

<br>

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

<br>

- staleTime

  데이터가 fresh 상태로 유지되는 시간을 지정한다. fresh 상태일 때는 해당 데이터를 재요청하지 않는다. stale 상태가 되는 경우 캐싱 데이터와 무관하게 재요청하여 최신 데이터 상태를 유지하도록 한다.

<br>

- cacheTime

  데이터가 캐싱되는 시간을 결정한다. 해당 시간이 지나면 가비지 콜렉터로 수집되어 사용할 수 없게 된다. 나같은 경우 보통 cacheTime을 Infinity로 설정하고 staleTime을 설정하여 캐싱 데이터를 업데이트하였다.

<br>

- enable

  enable 내부에 삼항연산자나 조건을 할당하여 조건에 맞는 시기에 호출할 수 있다.

<br>

### # **React batch update**

<br>

- 싱글 페이지 애플리케이션의 클라이언트 사이드 렌더링의 경우 자바스크립트를 통해 동적으로 dom을 조작하는데 이 때 잦은 상태 변화가 일어나게 된다. 상태 변화가 일어나는 시점마다 렌더링을 발생시키면 성능 이슈가 발생할 수 있어 react는 batch update를 16ms 단위로 진행한다. 즉 16ms동안 변경 된 상태 값들을 모아서 단 한번 리렌더링을 진행한다. 하지만 이렇게 state가 비동기적으로 동작함으로써 원하는 결과 값을 얻지 못하는 경우가 생긴다. 이 때 prevState같은 updater 함수를 사용하여 비동기로 동작하는 state를 동기적으로 동작하게 할 수 있다. setState()의 인자로 함수를 전달하는것을 함수형 setState라고 하는데 함수형 setState를 사용하면 리액트가 state를 변경하기 위해 setState의 변경 내용을 합치는 것이 아니라 하나의 큐(queue)에 setState를 올리고 이것들이 호출된 순서에 따라 state를 변경하게 된다. 이 때 updater의 인자로 state를 넣어주면 updater 인자 state는 항상 최신 상태로 유지하기 때문에 state가 동기적으로 업데이트 된다.

<br>

### # **동적 라우팅**

<br>

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

### # **페이지 네이션 구현 방법**

<br>

- 한 페이지에 보여 줄 데이터 수, 페이지 넘버 등의 정보가 담겨있는 쿼리 스트링을 백엔드와 지정하여 맞춘 뒤 url에 useSearchParams와 같은 hook을 이용하여 url에 백엔드와 맞춘 쿼리 스트링이 포함되도록 지정하고 이전 페이지나 다음 페이지로 이동 시 url의 포함 된 쿼리 스트링을 useLocation과 같은 hook으로 가져온 뒤 location에 search key에 접근하여 해당 데이터를 요청하면 페이지 네이션을 구현할 수 있을 것 같다.

<br>

### # **디자인 패턴** (https://velog.io/@iamjoo/mvc-mvp-mvvm-flux-%EB%94%94%EC%9E%90%EC%9D%B8-%ED%8C%A8%ED%84%B4-86ocg4bf)

<br>

- MVC 패턴

  - 구조 : 모델, 뷰, 컨트롤러

    (1) 모델 : 데이터와 그 데이터(내부 비지니스 로직)를 처리하는 부분

    (2) 뷰 : 사용자에서 보여지는 UI 부분

    (3) 컨트롤러 : 사용자의 입력을 받고 모델과 뷰에 중간 역할을 함

  - 동작

    ![mvc](https://user-images.githubusercontent.com/85284246/178215067-a4f2ddbe-0f4a-41be-9683-e22f62d37771.png)

    (1) 사용자의 액션들은 컨트롤러에 들어오게 된다.

    (2) 컨트롤러는 사용자의 액션을 확인하고, 모델을 업데이트한다.

    (3) 컨트롤러는 모델을 나타내줄 뷰를 선택한다.

    (4) 선택 된 뷰는 업데이트 된 모델을 이용하여 화면을 나타낸다.

  - 장점 : 패턴의 사용이 단순하다.

  - 단점 : 뷰와 모델 사이의 의존성이 높다. 높은 의존성 때문에 어플리케이션이 커질수록 복잡하지고 유지보수가 어렵게 만들 수 있다.

<br>

- MVP 패턴

  - 구조 : 모델, 뷰, 프레젠터

    (1) 모델 : 데이터와 그 데이터(내부 비지니스 로직)를 처리하는 부분

    (2) 뷰 : 사용자로부터의 입력을 받고 사용자에게 보여지는 UI부분을 표시

    (3) 프레젠터 : 뷰와 모델 사이에 자료 전달 역할

  - 동작

    ![mvp](https://user-images.githubusercontent.com/85284246/178215069-6c1d8fb3-201e-4d31-b138-b4b1457cca66.png)

    (1) 사용자의 액션들은 뷰를 통해 들어오게 된다.

    (2) 뷰는 데이터를 프레젠터에 요청한다. 이 때 관계는 1대1 관계이다.

    (3) 프레젠터는 모델에게 뷰 업데이트에 필요한 데이터를 요청한다.

    (4) 모델은 프레젠터에게 요청받은 데이터를 응답한다.

    (5) 프레젠터는 뷰에게 데이터를 응답한다.

    (6) 뷰는 프레젠터가 응답한 데이터를 이용하여 화면을 나타낸다.

  - 장점 : 프레젠터를 통해서만 데이터를 전달 받기 때문에 뷰와 모델의 의존성이 없다.

  - 단점 : 뷰와 프레젠터 사이의 의존성이 높다.

<br>

- MVVM 패턴

  - 구조 : 모델, 뷰, 뷰모델

    (1) 모델 : 데이터와 그 데이터(내부 비지니스 로직)를 처리하는 부분

    (2) 뷰 : 사용자로부터의 입력을 받고 사용자에게 보여지는 UI부분을 표시

    (3) 뷰모델: 뷰와 모델 사이에 매개체 역할

  - 동작

    ![mvvm](https://user-images.githubusercontent.com/85284246/178215072-2a197512-1d58-458d-8bef-3893678a5bef.png)

    (1) 사용자의 액션들은 뷰를 통해 들어오게 된다.

    (2) 뷰는 데이터를 뷰모델에 요청한다.

    (3) 뷰모델은 모델에게 뷰 업데이트에 필요한 데이터를 요청한다.

    (4) 모델은 뷰모델에게 요청받은 데이터를 응답한다.

    (5) 뷰는 뷰모델과의 데이터 바인딩(데이터를 묶어 동기화시킨다)을 이용해 화면을 갱신한다.

  - 장점 : 뷰와 모델 사이의 의존성이 없고 뷰모델은 모델하고만 소통을 하고 데이터만 관리하는 방식으로 뷰와의 의존성을 없앴다.

  - 단점 : 뷰모델의 설계가 어렵다.

<br>

- FLUX 패턴 : FLUX패턴은 MVC 패턴의 단점을 개선하고자 등장했다. 페이스북에서는 뷰에서 사용자 입력을 받아 모델과 뷰 사이에 양방향 데이터 흐름을 가지도록 만들었는데 애플리케이션의 규모가 커질수록 데이터 흐름을 파악하기가 어렵고 복잡도가 증가하여 예상치 못한 에러가 발생한다는 문제가 있었다. 그래서 나온 것이 FLUX 패턴이다. FLUX패턴은 항상 디스패치, 스토어, 뷰, 액션으로 데이터가 전달되며 액션을 통해 다시 디스패치로 데이터가 전달되는 단방향 데이터 흐름을 가지고 있다. 또한 FLUX 패턴의 일부분을 적용시킨 것이 전역 상태 관리 라이브러리인 리덕스와 몹엑스이다.

  - 구조와 동작순서 : 액션, 디스패처, 스토어, 뷰(컨트롤러 뷰)

    ![flux](https://user-images.githubusercontent.com/85284246/178215058-06245ee4-fa91-46ce-9497-c21dc423131b.png)

    (1) 액션 : 액션 생성자를 통해 디스패처에게 액션 객체를 전달한다.

    (2) 디스패처 : 액션 객체를 받아 액션 객체의 타입을 정의하여 스토어에 전달한다.

    (3) 스토어 : 액션 객체 타입을 받아 참고하여 상태를 업데이트 시키고 상태를 저장한다.

    (4) 뷰 : 컨트롤러 뷰는 스토어의 상태 변경 시 스토어의 데이터를 가져와 자식 뷰에게 분배한다.

  - 장점 : 단방향 데이터 흐름으로 데이터 흐름을 파악하기 쉽기 때문에 예상하지 못한 에러를 방지할 수 있다.

  - 단점 : FLUX 패턴을 적용한 라이브러리는 비교적 러닝 커브가 높은 편이다.

<br>

### # **웹사이트 scrolling 성능을 향상시키기 위한 몇가지 방법에 대해 설명해보세요.**

<br>

- 스크롤 이벤트의 특성 상 반복적으로 이벤트를 호출되게 되는데 스크롤 이벤트와 같이 반복적으로 호출되는 이벤트는 사용하지 않는 이벤트를 제거(실행 중지)하기 위해 클린업 함수를 적용시켜야한다. 만약 스크롤 이벤트에서 클린업 함수로 클리어 처리를 하지 않는 경우 모든 이벤트가 실행되거나 메모리에서 제거되지 않기 때문에 성능 이슈가 발생한다. removeEventListener를 통해 클린업 함수를 만들어 클리어 처리를 해주어야 메모리 누수가 발생하지 않는다. 또한 스크롤 이벤트의 경우 쓰로틀링을 구현하여 일정 시간동안 한번만 실행되도록 구현할 수 있다. 쓰로틀링은 로대쉬(Lodash)라이브러리의 쓰로틀(throttle)로 구현하거나 직접 구현할 수 있다. 쓰로틀링 구현은 직접 구현할 경우 setTimeout을 통해 일정 시간동안 스크롤 이벤트를 실행시키고 쓰로틀링을 체크하는 boolean타입의 state를 함께 사용하여 구현할 수 있다. 또한 추가로 스크를 되는 컨텐츠 중 사용자가 보는 뷰포트 영역의 컨텐츠만 렌더링하기 위해 windowing 기법을 적용할 수 있다. windowing 기법을 편리하게 적용시키기 위한 react 라이브러리로는 react-window와 react-virtualized가 있다.

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

### # **Lazy Loading은 무엇인가요?**

<br>

- Lazy Loading은 무엇인가요?

  레이지 로딩은 말 그대로 지연 로딩을 말한다. 필요한 리소스만 우선 받아온 뒤 나머지 리소스를 필요할 때 받아오는 기법을 말한다. 예를 들어 사용자가 웹 사이트를 접속할 때 모든 리소스를 받아오게 되면 렌더링이 지연될 수 있다. 또한 사용자가 모든 컨텐츠를 보지 않고 나가는 경우 리소스 낭비가 발생할 수 있다. 이런 경우 코드 스플리팅을 통해 레이지 로딩 기법을 적용하여 최적화할 수 있다. 코드 스플리팅은 모듈 번들링 통해 생성되는 메인 번들을 더 작은 번들로 분할하는 것을 말한다. 렌더링 시 필요한 번들만 우선적으로 로드하고 나머지 번들은 레이지 로딩할 수 있다.

  컴포넌트를 기준으로 코드 스플리팅하는 방법은 react에서는 컴포넌트의 경우 suspense 컴포넌트와 함께 react.lazy 메소드를 활용하여 코드스플리팅 할 수 있고 next의 경우 페이지 디렉토리 내부 컴포넌트들이 자동으로 코드 스플리팅 된다. 또한 페이지 디렉토리 외부 컴포넌트들은 next/dynamic의 dynamic 메소드를 사용하여 코드스플리팅 할 수 있다.

  또한 이미지 레이지 로딩의 경우 react에서는 Intersection Observer 혹은 scroll 이벤트를 통해 이미지가 뷰포트 내에 포함되는 경우 노출되도록 구현하거나 img 태그의 loading 속성을 lazy로 변경하여 구현할 수 있고 next의 경우 image 컴포넌트를 사용하면 자동으로 적용된다.

  이렇게 레이지 로딩을 적용하여 렌더링 최적화 및 리소스 낭비를 막을 수 있다.

  ```jsx
  import React, { lazy, Suspense } from "react";

  const AvatarComponent = lazy(() => import("./AvatarComponent"));

  const renderLoader = () => <p>Loading</p>;

  const DetailsComponent = () => {
    return (
      <Suspense fallback={renderLoader()}>
            <AvatarComponent />
      </Suspense>
    );
  };
  ```

<br>

### # **서버에 트래픽이 주어졌을 때 어떻게 응답속도를 개선할 수 있는가?**

<br>

- 트래픽이란 서버와 스위치 등 네트워크 장치에서 일정 시간 내에 흐르는 데이터의 양을 말한다. 트래픽 초과를 막기 위해서는 지리적으로 인접한 서버에 데이터를 요청하는 CDN, 여러 서버로 트래픽을 분산하는 로드 밸런싱, 클라이언트 단에서는 리소스 크기 줄이기 등을 할 수 있을 것 같고 상황이 허락된다면 AWS와 같은 확장성이 좋은 클라우드 컴퓨팅을 활용하여 필요에 따라 서버를 확장하는 방식을 활용할 수 있을 것 같다.

  (참고 사항 : CDN과 로드 밸런서는 기본적으로 다른 유형의 도구이다. CDN의 주요 목적은 넓은 지리적 영역에 컨텐츠를 분산시켜 물리적으로 가까운 서버에 요청을 하는 방식이고, 로드 밸런서의 주요 목적은 트래픽 분산을 위해 서버를 분산하는 것을 말한다.)

<br>

### # **프로젝트를 하면서 메모리 누수(leak) 이슈가 있었는지?**

<br>

- useEffect를 사용하여 api를 요청하고 응답에 따라 state를 업데이트 시킬 때 api 요청 후 서버에서 응답이 지연되는 경우 응답을 받기 전 해당 컴포넌트가 언마운트되면 api 호출 완료 후 state 업데이트 시도 시 메모리 누수가 발생한다. 즉 이전 컴포넌트에서 작업이 완료되기 전 컴포넌트가 언마운트 되는 경우 메모리 누수가 발생하는 것이다. 클린업 함수를 통해 컴포넌트가 언마운트 될 때 해당 작업을 종료하는 방식으로 문제를 해결할 수 있다. 또한 이미지 미리보기 구현 시 URL.createObjectURL을 통해 이미지 미리보기를 구현하였는데 해당 URL은 생성한 페이지에서만 유효하고 문서가 닫히거나 페이지를 이동하는 경우 유효하지 않기 때문에 메모리 누수가 발생한다. 이 때 URL.revokeObjectURL을 통해 생성한 객체 URL을 메모리에서 제거해주어야한다.

<br>

### # Webpack

- 웹팩

  최신 프론트엔드 프레임워크에서 가장 많이 사용되는 모듈 번들러이다. 모듈 번들러란 웹 애플리케이션을 구성하는 자원(HTML, CSS, Javscript, Images 등)을 모두 각각의 모듈로 보고 이를 압축하고 병합해서 하나의 번들 파일을 만드는 도구를 의미한다. 또한 모듈 번들러의 종류로는 웹팩 이 외에도 rollup, vite, esbuild 등이 있다. 모듈 시스템의 한계로 인해 등장하게 되었다.

- 웹팩 사용 이유

  웹 페이지를 구성하기 위해 HTTP 요청으로 html, css, js, 이미지, 웹 폰트, json 데이터 등 많은 파일을 받아오게 되는데 받아오는 파일이 많을수록 HTTP 요청이 많아지고 주로 사용하는 HTTP 1.1에서는 하나의 커넥션에서 하나의 요청이 끝난 후 다음 요청을 보낼 수 있으므로 HTTP 요청이 많아지면 성능 저하가 발생할 수 있다. 이런 경우 웹팩을 통해 js, css, 이미지 등을 하나로 압축하여 번들 파일을 만들어 파일의 크기를 줄이고 HTTP 요청 횟수를 줄일 수 있다. (물론 브라우저에서 HTTP1.1에 추가된 파이프라이닝이라는 기술로 요청을 여러 개씩 보낼 수 있는데 그것도 동시에 6개 정도 뿐이고, 근본적인 해결 방법은 아니다) 즉 웹팩을 사용하면 html, css, js 등의 모듈화와 코드 축소, 이미지 압축으로 인한 네트워크 비용 감소 및 요청 회수 감소 등에 장점이 있다.

  웹팩을 사용하지 않았을 경우 발생하는 문제에 대해 더 자세한 예시를 보자. 과거 ES6 모듈 시스템이 등장하기 전에는 a.js, b.js, c,js의 각 javasciprt 파일이 있다고 했을 때 이 javascript 파일들을 각 script 태그로 나누어 모듈처럼 사용하였다. 하지만 이러한 경우 전역을 공유하는 문제가 발생하였다.

  이러한 문제를 해결하기 위해 ES6 모듈 시스템이 등장하였다. ES6 모듈 시스템을 적용하는 경우 위와 같이 script 태그로 나뉘는 것이 아닌 하나의 script 태그 내부에서 a.js, b.js, c,js의 각 javasciprt 파일을 import문을 통해 가져오는 구조가 된다. 그렇게 되면 javascript 파일들은 각각의 모듈이 되는 것이다. 하지만 이 경우에도 문제가 발생한다. 해당 프로젝트의 구조 전체를 정적으로 배포한다고 했을 때 모듈로 나뉘어진 javascript 파일을 각각 요청해서 받아오게 된다. 이로 인해 네트워크 요청이 많아져 퍼포먼스가 떨어지는 문제가 발생하게 된다.

  그러면 여기서 생기는 의문이 하나의 javascript 파일에 모든 코드를 작성하면 되지 않느냐는 의문이 생길 수 있다. 이런 방식은 과거 ES6 모듈 시스템이 추가된 이유를 생각해보면 된다. 만약 하나의 javascript에 모든 javascript를 작성한다면 파일 크기가 매우 커지고 유지 보수가 어려워지며 코드 재사용 또한 어려워지는 문제가 발생할 수 있다.

  이와 같은 문제들로 인해 웹팩이나 vite 같은 번들러는 필수적으로 사용해야한다.

- 웹팩의 기본 옵션

  - Entry

    앱이 번들 처리를 시작할 지점. index.js부터 시작해서 import문을 따라서 빌드를 진행

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

  바벨은 ES6+ 버전 이상의 자바스크립트나 JSX, 타입스크립트 코드를 하위 버전의 자바스크립트 코드로 변환 시켜주는 자바스크립트 트랜스파일러이다. 크로스 브라우징 이슈를 해결하기 위해 사용한다. 바벨의 빌드 단계는 파싱(바벨 코어가 수행) -> 변환(플러그인이 수행) -> 출력(바벨 코어가 수행) 단계로 이루어지며 Webpack과 같은 정적 모듈 번들러들을 통해 함께 사용 가능하다.

- 플러그인

  바벨에 파싱, 변환, 출력 빌드 단계 중 변환 단계를 담당하며 어떤 코드를 어떻게 변환할지에 대한 규칙을 정의한다.

- 프리셋

  목적에 맞게 여러 가지 플러그인을 세트로 모아놓은 것이다. 제공되는 프리셋으로는 preset-env (최신 문법 ES5로 변환), preset-flow (플로우(타입 체크 라이브러리) 변환), preset-react (리액트 변환), preset-typescript (타입스크립트 변환) 등이 있다.

- 폴리필

  바벨은 ES6 이후 버전을 ES5 버전으로 변환할 수 있는 코드만 변환한다. 만약 최신 기능을 사용하였는데 이 기능이 ES5 버전에는 존재하지 않아 빌드가 누락 된 부분을 폴리필을 통해 변환할 수 있다. 코어제이에스(corejs), 폴리필아이오(polyfill.io) 등이 대표적인 폴리필 패키지이다.

<br>

### # **SWC(Speedy Web Compiler)**

- SWC(Speedy Web Compiler)란?

  SWC는 컴파일과 번들링 모두를 수행하는 자바스크립트 빌드 툴이다. next 12버전부터 바벨을 대체하도록 설정되어 있다. next 빌드 과정 중 트랜스파일링을 수행했던 바벨과, 코드 경량화를 수행했던 터서(Terser)가 SWC를 대체할 수 있다. SWC는 러스트(Rust)로 작성되어 싱글 스레드인 자바스크립트로 작성 된 바벨과 테서와는 다르게 병렬 처리가 가능하기 때문에 훨씬 빠르다.

- 빌드 시간 측정

  특정 커맨드의 결과가 나오기까지의 시간을 체크해주는 패키지를 사용하여 측정할 수 있다. (ex gnomon)

<br>

### # **prettier, eslint란?**

<br>

- eslint란?

  자바스크립트 언어와 소스코드를 분석하는 도구로 코드에 특정 스타일과 규칙을 적용해 에러를 찾고 패턴을 적용시킬 수 있는 분석 툴이다. 코드 구현 방식을 지정하여 에러를 사전에 방지하고 코드 퀄리티를 보장하도록 도와준다. 또한 prettier와 같이 코드 스타일과 관련 된 코드 포멧팅도 지원한다. 예를 들면 변수 사용 규칙, 콘솔 사용 방지, 사용되지 않는 객채 등에 경고나 에러를 선택하여 띄워줄 수 있다.

<br>

- prettier란?

  prettier는 코드 스타일을 통일되도록 도와주는 코드 포멧터이다. eslint와 같이 코드 구현 방식이 아닌, 줄 바꿈, 공백, 들여 쓰기 등 에디터에서 '텍스트'를 일관되게 작성되도록 도와준다.

<br>

- stylelint란?

  css및 scss를 코드를 분석하는 도구이다. 공백, 따옴표, 들여쓰기와 같이 작성 규칙이나 스타일 순서 등 css의 코드 스타일 규칙을 지정할 수 있다.

<br>

- 옵션을 알고 사용하는가?

  모든 옵션에 내용들을 아직 외우지는 못했다. 서칭을 통해 조합하여 사용하고 있다.

<br>

### # 사용자 경험 개선 방법으로 무엇이 있나? (로스비드이쿼)

<br>

(1) 스피너 사용 : 페이지 전환이나 api 호출 등 지연 되는 작업의 경우 로딩 중임을 사용자에게 알리는 스피너를 사용한다.

(2) 스켈레톤 UI 사용 : 컨텐츠 로딩 지연 시 사용자의 지루함을 막아주기 위해 로딩 바 혹은 스피너 대신 스켈레톤 UI(대체 UI)를 사용할 수 있다.

(3) 비디오 사용 시 대체 이미지 : 동영상 사용 시 동영상이 보이지 않는 유저들을 위해 대체 이미지를 깔아준다.

(4) 텍스트 드래그 막기 : 드래그 앤 드롭 기능 구현 시 타겟 css에 `use-select: none` 속성을 주어 텍스트가 드래그되는 것을 막을 수 있다.

(5) 이미지 태그의 onError 속성 : api로 이미지를 불러와 띄워줄 경우 이미지를 불러오지 못하는 경우(이미지 주소가 N/A로 오는 경우)가 발생할 수 있는데 이 때 이미지 태그의 onError를 사용하여 대체 이미지를 사용하여 에러 처리를 할 수 있다.

(6) 쿼리 스트링 활용 : 검색 기능 구현 시 쿼리 스트링을 활용하면 사용자가 검색 결과를 다른 사용자들과 공유할 수 있다.

(7) 연관 검색어 기능 구현 시 디바운싱 적용 : 연관 검색어 기능 구현 시 디바운싱을 적용하여 검색하는 과정 중 원하지 않는 결과물을 노출하지 않도록 함

<br>

### # 패키지 매니저

- npm : nodejs 표준 패키지 매니저, 별도 설치 필요없음, 직렬적(순차적) 설치, 보안성 취약

- yarn : 병렬적 설치, 패키지 데이터 캐시 및 재사용, 과거에는 npm보다 빠르고 안전하였으나 현재는 큰 차이없음

- yarn berry : yarn의 두번째 버전, Plug n Play 방식(패키지들에 대한 의존성을 zip파일로압축하고 pnp.cjs에 패키지를 찾기위한 정보 기록)으로 npm과 yarn에서 발생하는 유령 의존성 문제를 해결, 패키지 클론 시 install 하지 않아도 되는 제로인스톨 가능, CI에서 의존성 설치 시간 감소

  - 유령 의존성 : 사용 중인 패키지에 의존성 패키지, 즉 개발자가 직접 사용하고 있지 않은 패키지를 말한다. 이러한 패키지들은 직접 설치하지 않아도 해당 패키지를 사용할 수 있게 된다. 이런 유령 의존성의 묹는 버전 관리가 어렵기 때문에 버전 호환 에러가 발생할 수 있다.

- pnpm : 글로벌 저장소에서 패키지를 관리하여 중첩 설치하지 않아 디스크 공간 절약하고 패키지제이슨에 명시된 패키지만 글로벌 저장소에서 기져와 사용하므로 유령 의존성 문제 해결, yarn berry에 비해 모노레포 설정이 간단하고 속도가 더 빠르다는 장점이 있다.

<br>

### # **package.json파일의 역할을?**

<br>

- package.json의 역할

  현재 프로젝트에 관한 정보와 패키지 매니저를 통해 설치한 모듈들의 의존성을 관리하는 파일이다.

<br>

- package.json에서 dependencies와 devDependencies의 차이

  devDependencies의 개발용 라이브러리는 빌드 시 번들에 포함되지 않는다. 개발용과 배포용 라이브러리를 구분해서 설치해야 번들에 불필요한 라이브러리를 포함시키지 않아 빌드 시간 및 번들 사이즈를 줄일 수 있다.

  (1) dependencies : 개발과 배포 시 모두 의존하는 패키지를 관리한다. 배포 후에도 포함되기 때문에 애플리케이션 동작과 연관된 모듈을 설치한다. 예를 들어 리액트 돔, 엑시오스, 전역 상태 관리 라이브러리, ui 라이브러리 등이 있다.

  (2) devDependencies : 개발 시에만 의존하는 패키지를 관리한다. 배포 시 포함되지 않기 때문에 애플리케이션 동작과 직접적인 연관은 없지만, 개발할 때 필요한 라이브러리를 설치하면 된다. 예를 들어 웹팩, 바벨, 사스, 린트, 타입스크립트, 테스팅 라이브러리 등이 있다. 패키지 설치 시 ‘-D' 접미사를 붙여 설치할 수 있습니다.

<br>

- package-lock.json 이란?

  (요약 : 의존성 패키지의 버전을 명시하고 있다. 협업 시 레파지토리에 필수적으로 함께 커밋해주어야한다. 해당 파일없이 인스톨하는 경우 다른 버전이 설치될 수 있기 때문에 협업하는 팀원들과의 패키지 버전을 맞추기 위해 사용한다.)

  package-lock.json 파일은 npm을 사용해서 node_modules 트리나 package.json 파일을 수정하게 되면 자동으로 생성되는 파일이다.
  이 파일은 파일이 생성되는 시점의 의존성 트리에 대한 정확한 정보를 가지고 있다. package.json 파일의 의존성 선언에는 version range가 사용됩니다. version range란 특정 버전이 아니라 버전의 범위를 의미한다. 가장 흔한 예로 npm install express를 실행하게 되면 package.json 파일에는 “^4.16.3”(Caret Ranges)로 버전 범위가 추가된다. 저 package.json 파일로 npm install을 실행하면 현재는 4.16.3 버전이 설치되지만 express의 새로운 minor, patch가 publish 되면 동일한 package.json 파일로 npm install을 실행해도 4.17.3, 이나 4.16.4 같은 업데이트된 버전이 설치된다. 물론 대부분의 경우에는 문제가 없지만 간혹 업데이트된 버전이 오류를 발생시키는 경우가 있다. package-lock.json 파일은 의존성 트리에 대한 정보를 가지고 있으며 package-lock.json 파일이 작성된 시점의 의존성 트리가 다시 생성될 수 있도록 보장한다. package-lock.json 파일은 npm에 의해서 프로젝트의 node_modules나 package.json이 수정되는 경우 생성되거나 업데이트되며 당시 의존성에 대한 정보를 모두 가지고 있다. 따라서 생성된 package-lock.json 파일은 소스 저장소에 커밋해야 한다.

  (1) 의존성 트리에 대한 정보를 모두 가지고 있다.

  (2) 저장소에 꼭 같이 커밋해야 한다. 반드시 커밋할 필요는 없지만 협업 시 저장소에 커밋하는 것이 좋다. 없는 경우 협업 시 pull 받은 대상자가 npm install로 패키지 설치 시 의존성 트리의 일부 버전이 간혹 다르게 설치되어 오류를 발생시킬 수 있다.

  (3) node_modules 없이 배포하는 경우 반드시 필요하다.

<br>

### # **웹 태스크 매니저란?**

<br>

- 웹 태스크 매니저

  개발 업무 시 코드 수정 후 브라우저에서 새로고침을 눌러야 변경된 내용을 볼 수 있으며, 배포 시 HTML, CSS, JS등의 파일을 압축하거나 변환해야 했는데 이러한 과정을 자동화해주는 도구를 웹 태스크 매니저라고 한다. 예를 들어 Grunt(그런트), Gulp(걸프) 등이 있는 것으로 알고 있다. 하지만 그런트와 걸프 같은 경우 웹팩으로 대체하여 사용하는데 완벽히 대체한다기 보다는 웹팩은 모듈 번들러이고 그런트와 걸프는 태스크 러너로 서로 다르지만 웹팩에 그런트와 걸프의 기능이 포함되어 있고 더 많은 기능(Browserify와 같은 의존성 관리 기능)이 포함되어 있기 때문에 웹팩으로 대체하여 사용하는 것으로 알고 있다.

<br>

### # 안티 패턴 알고 있는 것?

<br>

(1) 삼항연산자 : 렌더단에서는 삼항연산자를 사용

(2) map의 key : map 메서드 사용 시 key 값으로 index 사용

(3) 다중 컴포넌트 : 컴포넌트 두 개를 한 파일에 선언

<br>

### # **FileReader와 URL.createObjectURL**

이미지 미리보기와 같이 파일 입출력 관련 기능을 구현할 때 사용하는 대표적인 메소드로는 FileReader와 URL.createObjectURL 방식이 있다.

<br>

- Blob 객체와 File 객체

  Blob 객체(바이너리 라지 오브젝트)는 이미지, 오디오, 영상 등을 다룰 때 사용하는 멀티미디어 객체이다. 사이즈나 타입 등의 정보를 담고 있다. File 객체도 Blob 객체와 유사하다. Blob을 상속받는 객체로 라스트모디파이드(최종수정날짜), 네임 등 조금 더 많은 정보를 담고 있다.

- FileReader

  FileReader 객체는 File객체나 Blob객체에 저장된 바이너리 데이터를 비동기적으로 읽어들이는 객체이다.

<br>

- URL.createObjectURL

  File객체나 Blob객체를 인자로 받아 임시 URL을 생성하여 사용한다. 해당 URL은 생성된 페이지 내에서만 유효하다.
  URL.createObjectURL 사용 시 주의할 점은 문서가 닫히거나(페이지 이동) URL.revokeObjectURL 를 호출하지 않으면 생성한 고유 URL은 메모리에 계속 상주하게 된다. 즉 메모리 누수가 발생할 수 있다. 그러므로 사용하지 않을 때에는 URL.revokeObjectURL를 통해 생성한 객체 URL을 제거해주어야한다.

<br>

- FileReader vs URL.createObjectURL

  (1) 메모리 사용량 : FileReader는 base64 인코딩 string을 사용하고 URL.createObjectURL는 포인터를 사용하기 때문에 FileReader의 메모리 사용량이 더 크다.

  (2) 속도 및 편의성 : FileReader는 파일이나 blob을 읽고 base64 인코딩 string으로 변환하는데 많은 작업이 필요하고 URL.createObjectURL은 읽기 과정 없이 고유한 URL을 즉시 생성하므로 속도가 더 빠르다.

  (3) 수용 가능 용량 : FileReader는 10mb, URL.createObjectURL는 800md 정도 용량까지 수용한다.

<br>

### # **import 중괄호 {}의 유무**

<br>

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

### # **트리 쉐이킹 (Tree Shaking)**

<br>

- 웹팩에서도 찾아볼 수 있고 네이밍에서도 알 수 있듯이 나무를 흔들어 필요없는 나뭇잎들을 떨어뜨린다는 뜻이다. 즉, 트리쉐이킹을 통해 모듈의 필요한 부분만 가져와 사용하여 빌드 시 불필요한 코드를 제거해 번들 사이즈나 빌드 시간을 줄일 수 있다. 웹팩은 ES6 이상의 import, export 표준 모듈 시스템을 사용하는 모듈에 대해 기본적인 트리쉐이킹을 지원한다. import 하는 패키지 내부에 사용하지 않는 export를 제거하는 것이다. 주의할 점은 ES5 이하 CommonJS 모듈 시스템을 사용하는 경우 트리쉐이킹이 적용되지 않는다. 또한 바벨의 babel-preset-env 사용 시 import가 require로 변환될 수 있기 때문에 트리쉐이킹이 적용되지 않을 수 있다. 이 때 bable preset env 속성 중 modules 속성을 false로 설정하여 문제를 해결할 수 있다.

  ```javascript
  // Import only some of the utilities!
  import { unique, implode, explode } from "array-utils";
  ```

<br>

### # JavaScript Module, ESM(ES Module)과 CJS(CommonJS)

- 모듈 시스템이 생겨난 이유

  모듈 시스템이 생기기 전 Javascript는 기본적으로 script 태그로 불려져 사용했었다. 하지만 script 태그로 불려진 여러 자바스크립트는 서로 관계가 없음에도 전역 객체 간에 의존성을 가지거나 스크립트 파일 로드 순서 등 여러 문제가 발생했다. 그래서 생겨난 것이 모듈 시스템이다. 모듈 시스템의 대표적인 포맷(문법)으로는 ESM(ES Module)과 CJS(CommonJS)가 있다.

<br>

- ESM(ES Module)과 CJS(CommonJS) 차이

  (1) ES Module은 js 표준 모듈화 시스템이고 CommonJS는 표쥰 모듈화 시스템은 아니지만 nodejs에서 채택해서 사용하고 있다.

  (2) CJS는 동기적으로, ESM은 비동기적으로 동작하며 CJS는 파일을 불러오는 동안 메인 스레드를 차단한다. 반면 ESM은 파일을 불러오는 동안 메인 스레드를 차단하지 않는다.

  (3) 파일의 구분은 package.json type field 또는 확장자를 보고 알 수 있다. type field의 기본 값은 CommonJS이고 타입이 CommonJS인 경우 js는 CommonJS로 해석되고 module인 경우 ES Module로 해석된다. 또한 확장자는 cjs와 esm으로 구분된다.

  (4) CommonJS의 module.export의 경우 동적(특정 조건에 따른) 실행에 아무 조건이 없는 반면 ESM의 export는 항상 최상위 스코프에서 사용할 수 있고 import path는 동적일 수 없다는 제약이 있다. 그렇기 때문에 빌드 단계에서 cjs의 경우 정적 분석하기가 어렵고 mjs는 정적 분석을 통해 모듈 간의 의존성을 파악하고 트리쉐이킹을 적용할 수 있다. 그렇기때문에 트리쉐이킹을 적용하는 경우 바벨 사용에도 주의해야한다. 만약 babel-preset-env를 사용한다면 mjs를 cjs로 변환하기 때문에 트리쉐이킹을 적용하기 어려워진다. 이를 위해 .babelrc에서 CommonJS로 변환하지 못하도록 설정을 추가해 줘야 한다.

  ```json
  {
    "presets": [
      [
        "env",
        {
          "modules": false
        }
      ]
    ]
  }
  ```

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

### # **useTransition / useDeferredValue**

react 18에서 useTransition, useDeferredValue 두 가지 hook이 추가되었다. 이 두가지 hook은 기존 debouncing과 throttling이 필요한 경우 사용할 수 있다.

<br>

- useTransition

  useTransition는 state의 업데이트를 늦춰준다. 일반 setState는 긴급 업데이트로 처리되고 useTransition의 startTransition로 래핑한 setState는 일반 setState보다 느리게 동작한다. 즉 비동기로 동작하며 배치업데이트 되던 setState의 우선 순위를 지정할 수 있다. 사용법은 useTransition가 반환하는 첫번째 객체로 state 업데이트가 진행 중임을 감지할 수 있고 두번째 객체로 업데이트를 늦출 state를 래핑할 수 있다. 예시로 사용자 입력에 따른 값이 큰 setState의 연산이 있는 경우 입력할 때마다 딜레이가 발생할 수 있는데 해당 setState 연산을 useTransition로 래핑하여 사용자 입력이 딜레이되지 않도록 하고 연산 시 isPending을 통해 로딩 UI를 노출해주며 사용자 경험을 향상시킬 수 있다.

  ```javascript
  function App() {
    const [isPending, startTransition] = useTransition();
    const [firstCount, setFirstCount] = useState(1);

    const handleClick = () => {
      startTransition(() => {
        setSecondCount((prev) => prev + 10);
      });

      setFirstCount((prev) => prev + 1);
    };

    return (
      <div>
        {isPending ? (
          <div>로딩...</div>
        ) : (
          arr2.map((el, index) => {
            return (
              <button key={index} onClick={handleClick}>
                {secontCount}
              </button>
            );
          })
        )}
      </div>
    );
  }
  ```

<br>

- useDeferredValue

  useTransition는 업데이트 순서에 직접 관여하는 반면 useDefferredValue는 업데이트 되는 값에 관여한다. useDefferredValue를 적용하는 경우 값이 완전히 처리되기 전까지 이전 값을 표시한다. 사용법은 setState의 업데이트 값인 state를 전달받아 사용한다. 예시로 검색어 입력 중 입력 값에 따른 결과물 노출 시 검색어 입력이 완료되기 전 원하지 않는 결과물이 노출되는 것을 막을 수 있다.

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

### # **React 18 Streaming SSR**

<br>

- 기존 SSR의 동작 방식은 브라우저가 서버에서 렌더링이 완료된 HTML 파일(static)을 받아온 뒤 이 HTML 파일을 파싱한 후 사용자에게 우선적으로 보여준다. 그 후 javascript가 로드되면 하이드레이션을 통해 사용자와 상호작용 가능하도록 한다. 이 때 서버에서 렌더링이 지연될 경우 TTFB가 늦어지고 이어서 FCP도 느려질 수 있다. 또한 javascript 로드가 지연되는 경우 하이드레이션이 지연되어 TTI(사용자와 상호작용 시간)가 느려져 사용자 경험이 좋지 않아질 수도 있다. 이러한 상황을 개선하고자 React 18에서는 Streaming SSR가 추가되었다. Streaming SSR이란 Suspense 컴포넌트를 기준으로 서버에서 HTML을 여러 청크로 나눠 렌더링 하고, 렌더링이 완료된 부분 먼저 스트리밍 형태로 클라이언트에 응답하고 하이드레이션 또한 우선적으로 처리한다. 이러한 방식을 통해 TTFB, FCP, TTI를 개선하였다.

  - TTFB(Time to first byte) : 브라우저가 HTTP 요청 후 첫 번째 응답 byte를 받는 시간

  - FCP(First Contentful Paint) : 첫 번째 의미있는 컨텐츠가 렌더링되는 시간

  - TTI(Time to Interation) : 컨텐츠가 렌더링된 후 js 로드가 되고 하이드레이션하여 사용자와 상호작용하는 시간

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

- 미래의 리액트 컴포넌트

  서버 컴포넌트가 도입됨으로써 백엔드 데이터 직접 접근, 번들 사이즈 감소, 자동 Code Splitting이 가능하게 되었고, 이로 인해 미래의 리액트 애플리케이션은 각 컴포넌트의 역할에 집중하여 개발할 수 있으며 애플리케이션의 퍼포먼스 또한 향상될 수 있을 것이다.

  ```jsx
  // Note.server.jsx
  import { format } from "date-fns"; // 번들사이즈에 영향 없음
  import { readFile } from "react-fs"; // 번들사이즈에 영향 없음
  import path from "path";

  import NotePreview from "./NotePreview"; // 공유 컴포넌트
  import EditButton from "./EditButton.client"; // 클라이언트 컴포넌트, 자동 코드 분할됨

  export default function Note({ selectedId }) {
    const note = readFile(path.resolve(`./notes/${selectedId}.md`), "utf8"); // 파일 시스템에서 data fetching

    if (note === null) {
      return (
        <div className="note--empty-state">
          <span className="note-text--empty-state">
            노트를 찾을 수 없어요 🥺
          </span>
        </div>
      );
    }

    // 노트가 존재하지 않을 시 아래의 코드는 클라이언트에 전달되지 않음
    let { id, title, body, updated_at } = note; // serializable한 props 클라이언트 컴포넌트로 전달 가능
    const updatedAt = new Date(updated_at);

    return (
      <div className="note">
        <div className="note-header">
          <h1 className="note-title">{title}</h1>
          <div className="note-menu" role="menubar">
            <small className="note-updated-at" role="status">
              마지막 변경 시간 {format(updatedAt, "yyyy MMM d 'at' h:mm bb")}
            </small>
            <EditButton noteId={id}>수정</EditButton>
          </div>
        </div>
        <NotePreview body={body} />
      </div>
    );
  }
  ```

<br>

- 서버 컴포넌트(RSC)와 서버 사이드 렌더링(SSR)의 차이

  (1) 브라우저로 번들 전달 여부 : 서버 컴포넌트 번들은 클라이언트로 전달되지 않는다. 하지만 서버 사이드 렌더링의 모든 컴포넌트의 코드는 자바스크립트 번들에 포함되어 클라이언트로 전송된다.

  (2) 렌더링 전략 : 서버 컴포넌트는 페이지 레벨에 상관없이 모든 컴포넌트에서 서버에 접근 가능하여 컴포넌트 단위 SSR 전략을 세울 수 있다. 하지만 getServerSideProps의 경우 상위 레벨의 페이지에서만 사용할 수 있기 때문에 페이지 단위 SSR 전략을 세워야한다.

  (3) 데이터 리패치 시 상태 유지 : 서버 컴포넌트는 브라우저에 HTML이 아닌 RSC 객체로 전달되기 때문에 클라이언트 상태를 유지하며 데이터를 리패치 할 수 있다. 하지만 SSR의 경우 HTML로 전달되기 때문에 데이터 리패치 시 HTML 전체를 리렌더링이 하며 클라이언트 상태를 유지할 수 없다.

  (4) 결론 : 서버 컴포넌트는 서버 사이드 렌더링 대체가 아닌 보완의 수단으로 사용할 수 있다. 서버 사이드 렌더링으로 초기 HTML 페이지를 빠르게 보여주고, 서버 컴포넌트로는 브라우저로 전송되는 자바스크립트 번들 사이즈를 감소시킬 수 있다.

<br>

### # React 실행 순서

1. 함수 컴포넌트 호출
2. 구현부 실행
   - props 취득, hook 실행, 내부 변수 및 함수 생성
   - 단, hook 에 등록해둔 상태값, 부수함수 효과 등은 별도 메모리에 저장되어 관리된다.
3. return 실행
   - 렌더링 시작
4. 렌더 단계 (Render Phase)
   - 가상DOM을 생성한다.
5. 커밋 단계 (Commit Phase)
   - 실제 DOM에 반영한다.
6. useLayoutEffect
   - 브라우저가 화면에 Paint 하기 전에, useLayoutEffect에 등록해둔 effect(부수효과함수)가 '동기'로 실행된다.
   - 이 때, state, redux store 등의 변경이 있다면 한번 더 재렌더링 된다.
7. Paint
   - 브라우저가 실제 DOM을 화면에 그린다. didMount가 완료된다.
8. useEffect
   - Mount되어 화면이 그려진 직후, useEffect에 등록해둔 effect(부수효과함수)가 '비동기'로 실행된다.

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

    위 코드는 RenderParent 컴포넌트 내부에 RenderChild1, RenderChild2, RenderChild3, RenderChild4를 자식 컴포넌트로 받아 렌더링하고 있다. 이 때 RenderChild1은 children props로 RenderChild2를 받고 있고 RenderChild2 또한 RenderChild3을 children props로 받고 있다. 이 때 콘솔 출력 결과는 위와 같다.

    1. 가장 상위 컴포넌트인 RenderParent 부터 시작해서 함수 몸체 부분의 콘솔이 찍힌다. 그리고 자식 컴포넌트들도 순차적으로 몸체 부분이 실행된다.
    2. useEffect는 가상 돔의 변화를 실제 돔에 적용시키는 Commit Phase 단계 후 브라우저 페인트 단계까지 마치고 나서 실행된다고 알고 있다. 그렇기 때문에 자식 컴포넌트를 가지고 있는 경우 자식 컴포넌트가 우선적으로 컴포넌트 렌더링 되어 리액트 엘리먼트 객체를 반환해야하므로 자식 컴포넌트의 컴포넌트 렌더링이 먼저 처리된다. 위 1번과 같은 함수 몸체 부분은 리액트 엘리먼트 객체를 반환하는 것이 아닌 몸체 부분만 실행하는 것이기 때문에 우선적으로 실행되는 것이다. 그렇기 때문에 자식 컴포넌트의 리액트 엘리먼트 객체를 반환하는 작업이 완료가 되면 자식 컴포넌트 먼저 useEffect가 돌기 때문에 useEffect는 3 -> 2 -> 1 -> 4 -> parent 순으로 실행이 된다. 이유는 useEffect는 동기적으로 실행되지만 1과 4는 같은 레벨을 가지고 있고 1의 자식으로 2와 3을 받고 있기 때문에 1의 자식 컴포넌트들의 리액트 엘리먼트 객체들이 먼저 반환되기 때문에 useEffect도 우선적으로 처리된다. depth가 가장 깊은 3이 먼저 실행되는 것을 확인할 수 있다. 그렇게 자식 컴포넌트인 3과 2가 먼저 실행된 후 렌더링 단에서 상위에 위치한 1이 실행되고 그 후 4가 실행되는 것을 볼 수 있다. 그리고 자식 컴포넌트들의 useEffect가 모두 완료된 후 최상위 부모의 useEffect가 실행된다.
    3. 최상위 부모의 useEffect가 실행되고 setState는 비동기로 동작하여 콜스택이 비어있을 때 state를 업데이트시키는데 state 업데이트가 완료되면 리렌더링이 발생한다. 그렇기 때문에 위 1 ~ 2번 과정을 반복한다. 다만 차이점은 2번에서 발생하는데 초기에 props는 비어있는 상태였다가 state가 변경되었기 때문에 props로 전달받은 state의 최신 값인 "테스트"라는 문구가 추가된 것을 볼 수 있다.
    4. 또한 추가로 최상위 부모의 useEffect는 state 변경으로 인해

<br><br><br>

## # Next.js

<br>

### # **Next.js 사용 이유**

<br>

1. 다양한 렌더링 전략 : CSR, SSR, SSG, ISR 등 다양한 렌더링 전략을 선택해서 사용할 수 있다.

2. 프리 렌더링 : 기본적으로 모든 페이지를 프리 렌더한다. 프리 렌더를 통해 빌드 타임에 필요한 페이지들을 미리 생성한다. 또한 Link 컴포넌트 사용 시 해당 컴포넌트가 뷰포트에 포함되는 경우 프리 페치하여 클라이언트 사이드 라우팅 시 빠르게 페이지를 전환할 수 있다.

3. 자동 코드스플리팅 : 페이지 디렉토리 내의 페이지들을 빌드 타임에 자동으로 코드스플리팅한다.

4. 디렉토리 기반 자동 라우팅 : 페이지 하위 디렉토리를 기반으로 자동 라우팅된다.

5. 이미지 최적화 : sqooush와 같은 이미지 최적화 모듈을 통해 자동으로 이미지를 최적화한다.

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

### # **getStaticProps, getStaticPath, getInitialProps, getServerSideProps**

<br>

- getStaticProps

  getStaticProps는 정적 사이트 생성(SSG, Static Site Generation) 및 점진적 정적 생성(ISR, Incremental Static Regeneration)을 위해 사용되는 메소드로 빌드 타임에 호출되며 pre-rendering 시 외부 데이터를 받아오기 위해 사용한다.

  SSG와 ISR을 나누는 기준은 return 객체의 revalidate 옵션이며 revalidate 없다면 SSG로 동작하여 빌드 시 딱 한번만 호출된다는 특징이 있다. 단, 데이터 업데이트를 위해서는 재빌드 및 배포가 필요하다는 단점이 있다.

  revalidate가 존재하면 ISR로 동작하며 revalidate의 value 값에 따라 특정 주기마다 Next.js의 백그라운드에서 정적 페이지를 재생성한다. 만약 재생성 실패 시 기존 정적 페이지를 제공한다.

<br>

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

### # **Next.js의 환경 변수**

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

<br>

### # Nextjs 13 둘러보기

- Next 13 App Router Docs 정독 포스트 참고

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

<br>

(1) String : 문자열

```ts
let str: string = "hi";
```

(2) Number : 숫자

```ts
let num: number = 10;
```

(3) Boolean : 진위 값

```ts
let isLoggedIn: boolean = false;
```

(4) Array : 배열

```ts
let arr: number[] = [1, 2, 3];
let arr: Array<number> = [1, 2, 3]; // 제네릭 사용
```

(5) Tuple : 고정 된 길이와 각 요소의 타입이 지정되어 있는 배열, 만약 정의하지 않은 타입, 인덱스로 접근할 경우 오류 발생

```ts
let arr: [string, number] = ["hi", 10];
arr[1].concat("!"); // 에러
arr[5] = "hello"; // 에러
```

(6) Enum : 특정 값(상수)들의 집합, 인덱스 번호로도 접근할 수 있고 인덱스를 지정할 수도 있다. 일반 객체와 차이점은 수정이 불가하다.

```ts
enum Avengers {
  Capt = 2,
  IronMan,
  Thor,
}
let hero: Avengers = Avengers[2]; // Capt
let hero: Avengers = Avengers[4]; // Thor, IronMan과 Thor에 자동으로 인덱스 번호가 부여된다.
```

(7) Any : 모든 타입에 대해서 허용

```ts
let str: any = "hi";
let num: any = 10;
let arr: any = ["a", 2, true];
```

(8) Void : 변수에 사용 시 undefined와 null만 할당을 허용하고, 함수에 사용 시 반환 값이 없다는 것을 의미하는 타입

```ts
let unuseful: void = undefined;
function notuse(): void {
  console.log("sth");
}
```

(9) Null

(10) Undefined

(11) Never : 함수의 끝에 절대 도달하지 않는다는 의미를 지닌 타입, 예시로 무한 루프를 발생시키는 함수나 항상 에러를 반환하는 함수의 출력 값으로 지정할 수 있다. void와의 차이점은 void는 null 혹은 undefined 값의 반환을 허용한다는 것이고 never는 never 이외에는 허용하지 않는다.

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

<br>

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

<br>

- 여러타입을 합쳐서 사용하는 타입, AND 연산자와 같이 모든 타입을 만족해야한다. 하지만 옵션 속성을 활용하여 특정 타입을 옵셔널하게 사용할 수 있다. 또한 extends를 통해 확장도 가능하다.

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
  ```

<br>

### # 클래스에서의 타입스크립트 활용

<br>

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

<br>

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

<br>

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

<br>

- 제네릭이란?

  함수나 클래스의 재사용을 목적으로 선언 시점이 아닌 사용 시점에 타입을 선언하는 타입이다. 함수나 클래스에서 사용할 타입을 인수로 넘겨서 사용하는 개념이다.

  ```ts
  function getText<T>(text: T): T {
    return text;
  }

  getText<string>("hi");
  getText<number>(10);
  getText<boolean>(true);
  ```

<br>

- 제네릭 프로퍼티 체크

  함수이 제네릭 타입 사용 시 함수 내부에서 파라미터의 관련 메소드 사용 시 에러가 발생할 수 있다. 이유는 제네릭 타입의 경우 파라미터의 프로퍼티 체크 시 타입의 범위가 넓은 경우 관령 메소드가 있다는 단서를 찾을 수 없기 때문이다. 그렇기 때문에 함수 내부에서 타입 가드나 파라미터의 명시적인 타입 선언을 통해서 타입 범위를 좁혀야한다.

  ```ts
  // 에러 발생 : 명시적인 타입 미선언
  function logText<T>(text: T): T {
    console.log(text.length); // Error: T doesn't have .length
    return text;
  }

  // 에러 미발생 : 명시적인 타입 선언
  function logText<T>(text: T[]): T[] {
    console.log(text.length); // 제네릭 타입이 배열이기 때문에 `length`를 허용합니다.
    return text;
  }
  ```

<br>

- 제네릭 인터페이스

  ```ts
  // 변형 전
  function logText<T>(text: T): T {
    return text;
  }

  let str: <T>(text: T) => T = logText; // #1
  let str: { <T>(text: T): T } = logText; // #2

  // 변형 후
  interface GenericLogTextFn {
    <T>(text: T): T;
  }
  function logText<T>(text: T): T {
    return text;
  }
  let myString: GenericLogTextFn = logText; // Okay
  ```

<br>

- 제네릭 클래스

  ```ts
  class GenericMath<T> {
    pi: T;
    sum: (x: T, y: T) => T;
  }

  let math = new GenericMath<number>();
  ```

<br>

### # 타입 추론

<br>

- 타입 추론이란?

  타입 추론이란 타입을 따로 정의하지 않아도 자동으로 타입을 추론해주는 기능을 말한다. 정적 타입 언어의 단점은 타입을 정의하는데 많은 시간과 노력이 들기 때문에 생산성이 저하될 수 있다는 점이다. 하지만 타입스크립트의 경우 타입 추론을 제공하기 때문에 필요한 경우에만 타입 정의를 할 수 있어 코드를 덜 작성하면서도 같은 수준의 타입 안정성을 유지할 수 있다. 타입 추론은 몇 개의 표현식을 참고하여 최적의 공통 타입(베스트 커먼 타입 알고리즘)을 추론하거나 코드가 작성되는 흐름을 기반으로 타입(문맥상의 타이핑)을 추론한다.

<br>

- 타입스크립트의 타입 추론 방법

  (1) 최적의 공통 타입(Best Common Type) : 타입은 보통 몇 개의 표현식(코드)을 바탕으로 타입을 추론한다. 그리고 그 표현식을 이용하여 가장 근접한 타입을 추론하게 되는데 이 가장 근접한 타입을 Best Common Type(최적의 공통 타입)이라고 한다. Best Common Type 알고리즘으로 다른 타입들과 가장 잘 호환되는 타입을 선정한다.

  ```ts
  let x = [0, 1, null]; // let x: (number | null)[]
  ```

  (2) 문맥상의 타이핑(Contextual Typing) : 문맥상의 타이핑(타입 결정)은 코드의 위치(문맥)를 기준으로 일어난다.

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

<br>

- 타입 가드는 타입의 범위가 넓을 때 컴파일러가 타입을 예측할 수 있도록 타입의 범위를 축소시키는 것을 말한다. as를 사용한 타입 단언(A as number), if문과 typeof 연산자 활용(typeof A === "number"), if문과 in 연산자 활용("toString" in A) 등을 활용하여 타입 가드를 적용시킬 수 있다.

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

  // 방법2: typeof 활용
  function someFuncTypeof(val: string | number) {
    if (typeof val === "number") {
      val.toFixed(2);
      isNaN(val);
    } else {
      val.split("");
      val.toUpperCase();
      val.length;
    }
  }

  // 방법3: in연산자 활용
  function someFuncIn(val: any) {
    if ("toFixed" in val) {
      val.toFixed(2);
      isNaN(val);
    } else if ("split" in val) {
      val.split("");
      val.toUpperCase();
      val.length;
    }
  }

  // 방법4: instanceof연산자 활용
  class Cat {
    meow() {}
  }
  class Dog {
    woof() {}
  }
  function sounds(ani: Cat | Dog) {
    if (ani instanceof Cat) {
      ani.meow();
    } else {
      ani.woof();
    }
  }
  ```

<br>

### # 타입 단언

<br>

- 타입 단언은 타입을 강제적으로 지정해줄 떄 사용하며 as 키워드를 통해 타입 단언을 할 수 있다. 타입 추론보다 더 정확한 타입을 아는 경우에 사용할 수 있다. 주의할 점은 런타임 에러가 절대 발생하지 않을 것이라는 확신이 있을 때만 사용해야한다. 예를 들어 var a, a = 20, var b = a와 같은 순서로 변수 값을 복사할 때 b 변수는 a 변수가 생성될 때의 타입인 any 타입을 가지게 된다. 이러한 경우 타입 단언을 사용할 수 있다. 또한 타입 단언은 DOM API 조작 시에도 많이 사용된다. DOM API로 이미 존재하는 DOM에 접근 시 엘리먼트 타입과 null을 포함한 유니온 타입으로 추론되는데 이 때 타입 단언을 통해 엘리먼트 타입으로 지정하여 null인 경우에 예외처리를 생략할 수 있다.

<br>

### # 타입 호환성

<br>

- 타입 호환성이란 구조적 서브 타이핑을 기반으로 두 타입에 멤버만으로 타입이 호환되는지 판별하여 관계시키는 규칙이다. 타입 호환성을 통해 예상치 못한 에러를 방지하여 안정성을 향상시켰다. 타입 별 호환성 예시로는 인터페이스의 경우 객체 프로퍼티를 비교하고 함수의 경우 파라미터와 반환 타입 등을 비교하고 제네릭의 경우 전달받는 타입을 비교한다.

  ```tsx
  // (1) 인터페이스 호환성 예시
  // 인터페이스 A와 B 정의
  interface A {
    x: number;
  }

  interface B {
    x: number;
    y: number;
  }

  // A는 B로 할당 가능합니다. (넘치는건 가능)
  let a: A = { x: 1 };
  let b: B = a; // 가능

  // B는 A로 할당 불가능합니다. (부족한건 불가능)
  let bb: B = { x: 1, y: 2 };
  let aa: A = bb; // 오류! Property 'y'가 필요합니다.
  ```

  ```tsx
  // (2) 함수 호환성 예시
  type FuncA = (x: number) => number;
  type FuncB = (x: number, y: number) => number;

  // FuncA는 FuncB로 할당 가능합니다. (매개변수가 적어지는건 가능)
  let fnA: FuncA = (x) => x * 2;
  let fnB: FuncB = fnA; // 가능

  // FuncB는 FuncA로 할당 불가능합니다.  (매개변수가 많아지는건 불가능)
  let fnBB: FuncB = (x, y) => x + y;
  let fnAA: FuncA = fnBB; // 오류! 불필요한 매개변수 'y'가 있습니다.
  ```

  ```tsx
  // (3) 제네릭의 호환성 예시
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

### # strict 모드에서 null 에러

<br>

- strict 모드 활성화 시 엄격하게 타입이 관리되어 null 타입 관련 문제가 발생할 수 있다. 타입 가드로 null 타입이 아닌 조건을 추가하여 해결할 수 있다. as 타입 단언, if문, 삼항연산자, 옵셔널체이닝, 논널 단언 연산자 등을 사용할 수 있다.

  (1) as : const confirmedTotal = $('.confirmed-total') as HTMLSpanElement;

  (2) if문 : if (!rankList) return; rankList.addEventListener('click', handleListClick);

  (3) 삼항연산자 : selectedId = event.target.parentElement ? event.target.parentElement.id : undefined;

  (4) 옵셔널체이닝 : deathsList?.appendChild(li)

  (5) ! (Non-null assertion operator) : deathsList!.appendChild(li);

<br>

### # 타입 별칭(타입 앨리어스)

<br>

- 타입 별칭은 특정 타입에 별칭을 부여하여 새로운 타입을 만들어내는 타입이다. 인터페이스와 같은 객체 타입이나 원시 타입 혹은 값, 유니온 타입, 튜플 타입, 함수 타입 등을 지정할 수 있다.

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

<br>

### # 타입 별칭과 인터페이스 차이

(1) 확장 : 타입 별칭은 확장이 불가능하고 인터페이스는 확장이 가능하다.

(2) 생성 타입 형태 : 타입 별칭은 객체 형태의 타입 외에도 원시 타입 혹은 값, 유니온 타입, 튜플 타입 등을 지정할 수 있고 인터페이스는 객체 형태의 타입을 지정한다.

(3) 프리뷰 : 타입 별칭은 프리뷰 시 타입의 구조를 모두 보여주고 인터페이스는 타입명을 보여준다.

<br>

### # 유틸리티 타입

<br>

- 유틸리티 타입이란?

  유틸리티 타입은 이미 정의해 놓은 타입을 변환하여 새로운 타입을 만들 때 사용하는 타입이다. 유틸리티 타입의 종류는 매우 다양하지만 대표적으로 파셜, 오밋, 픽 등의 타입이 있다.

<br>

- 자주 사용되는 유틸리티 타입

  (1) 파셜(Partial) : 파셜 타입은 특정 타입의 부분 집합을 만족하는 타입을 정의한다. 파셜을 사용하면 옵셔널 속성의 남발을 막을 수 있다.

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

  (2) 픽(Pick) : 픽 타입은 특정 타입에서 몇 개의 속성을 선택하여 타입을 정의한다.

  ```ts
  interface Hero {
    name: string;
    skill: string;
  }
  const human: Pick<Hero, "name"> = {
    name: "스킬이 없는 사람",
  };
  ```

  (3) 오밋(Omit) : 오밋 타입은 픽과 반대로 특정 타입에서 지정된 속성만 제거한 타입을 정의한다.

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

<br>

- 맵드 타입이란?

  맵드 타입은 기존에 정의된 타입을 map 메소드와 같이 순회하여 새로운 타입을 정의한다. 마치 자바스크립트 map 메소드를 타입에 적용한 것과 같은 효과를 가진다.

<br>

- 맵드 타입 사용법

  in 연산자를 활용하여 순회하며 in 연산자를 기준으로 좌항은 일반 변수, 우항은 순회 대상이다. 타입은 콜론 뒤에 지정해준다. 사용 예시로 유니온 타입을 순회하여 객체 타입을 정의하거나 인터페이스 타입을 순회하여 속성을 모두 옵셔널로 변경한 타입을 정의할 수 있다.

  ```ts
  // 예제1 : 기본 문법
  { [ P in K ] : T }
  { [ P in K ] ? : T }
  { readonly [ P in K ] : T }
  { readonly [ P in K ] ? : T }

  // 예제2 : 기본 예제
  type Heroes = "Hulk" | "Capt" | "Thor";
  type HeroAges = { [K in Heroes]: number };
  const ages: HeroAges = {
    Hulk: 33,
    Capt: 100,
    Thor: 1000,
  };

  // 예제3 : 실용 예제, 맵드 타입인 Subset은 키와 값이 있는 객체를 정의하는 타입을 받아 그 객체의 부분 집합을 만족하는 타입으로 변환해주는 문법이다. key of의 경우 인터페이스 속성 키를 유니온 타입으로 반환한다. 예를 들면 Person과 같은 인터페이스가 있다고 할 때 Subset 타입을 적용하면 ageOnly, nameOnly, ironman, empty과 같은 객체를 모두 정의할 수 있다.

  type Subset<T> = {
    [K in keyof T]?: T[K];
  }

  interface Person {
    age: number;
    name: string;
  }

  const ageOnly: Subset<Person> = { age: 23 };
  const nameOnly: Subset<Person> = { name: 'Tony' };
  const ironman: Subset<Person> = { age: 23, name: 'Tony' };
  const empty: Subset<Person> = {};
  ```

<br>

### # 유니온 타입 vs 인터섹션 타입

<br>

- 유니온 타입 (|) : 유니온 타입이란 OR 연산자와 같이 A이거나 B다를 의미하는 타입이다. 유니온 타입으로 인터페이스 타입 두 개를 연결하는 경우 공통 된 속성만 접근할 수 있다.

<br>

- 인터섹션 타입 (&) : 인터섹션 타입은 AND 연산자와 같이 A와 B를 모두 만족하는 하나의 타입이다. 인터섹션 타입으로 인터페이스 타입 두 개를 연결하는 경우 두 인터페이스가 가진 모든 속성에 접근이 가능하다.

<br>

### # **타입스크립트 데코레이터**

<br>

- 데코레이터란?

  데코레이터가 붙은 클래스, 메소드(함수) 및 변수 등에 데코레이터에서 정의된 기능이 동작하는 것을 의미한다.

<br>

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

<br>

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

<br>

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

### # **타입스크립트가 실행되는 과정**

<br>

- 2-4번은 TSC가 수행, 5-7번은 브라우저, NodJS, 기타 자바스크립트 엔진 같은 자바스크립트 런타임이 실행

  (1) 소스 코드 작성 by 프로그래머

  (2) 타입스크립트 소스 코드를 파싱하여 AST (추상문법트리)로 변환

  (3) 타입 검사기가 AST를 확인 (여기서 타입 검사가 이루어짐)

  (4) 컴파일러가 AST를 bytecode가 아닌 JavaScript로 변환한다.

  (5) JavaScript 소스를 AST로 변환

  (6) AST -> 바이트코드

  (7) 런타임이 바이트코드를 평가

<br>

### # **keyof와 typeof**

- keyof `example` : `example`의 모든 프로퍼티의 키값을 union 형태로 반환, “T extends keyof 인터페이스명”을 통해서 인터페이스의 있는 한 가지만 제네릭으로 설정한다. 인터페이스 내부의 key값으로 제네릭의 범위를 제한하는 것이다.

<br>

- typeof `example` : `example`(변수/함수등)의 type을 반환, enum 타입과 같은 객체를 반환하는 타입에 사용하면 이 객체 자체가 타입이 된다.

<br>

- 예제

  ```ts
  // 예제1 : enum
  enum BrandEnum {
    Nike = "nike",
    Adidas = "adidas",
    Puma = "puma",
  }

  let type1: typeof BrandEnum = {
    Nike: BrandEnum.Nike,
    Adidas: BrandEnum.Adidas,
    puma: BrandEnum.puma,
  }; // 마우스 오버 시 : let type1: typeof BrandEnum
  let type2: keyof BrandEnum; // 마우스 오버 시 : let type2: number | typeof Symbol.iterator | "toString" | "charAt" ...
  let type3: keyof typeof BrandEnum; // 마우스 오버 시 : let type3: "Nike" | "Adidas" | "Puma"
  ```

  type1은 마우스를 올려보면 typeof BrandEnum가 찍힌다. enum은 객체로 변환되기 때문에 typeof를 사용하게 되면 그냥 그 객체 자체가 type이 되어버려 똑같이 사용해야만 한다. 그럼 이 typeof 를 했을 때 만들어진 type이 interface와 비슷하다고 생각된다.
  type2의 마우스를 올려보면 객체의 프로퍼티들이 찍히는걸 볼 수 있다. Brand가 Object이기 때문에 나오는 것이다.
  type3은 typeof Brand가 enum 객체 그 자체이고 그것의 key들을 뽑아냈기 때문에 key값이 유니온으로 반환된다.

  ```ts
  // 예제2 : interface
  interface BrandInterface {
    Nike: "nike";
    Adidas: "adidas";
    Puma: "puma";
  }

  let type: keyof BrandInterface; // 마우스 오버 시 : 'Nike' | 'Adidas' | 'Puma'
  ```

  이런식으로 작성하고 type에 마우스를 올려보면 아까 위와 똑같이 'Nike' | 'Adidas' | 'Puma'로 나오는것을 확인할 수 있다.
  즉, enum의 keyof typeof는 interface의 keyof와 똑같다고 볼 수 있을 것 같다. enum은 객체이기 때문에 keyof만 했을 때는 객체의 key들이 나오고 keyof typeof를 했을 때 원하는 값이 나왔다. interface는 객체가 아니기 때문에 keyof만 했을 때도 바로 원하는 값이 나온다.

  ```ts
  // 예제3 : 객체
  const object = {
    Nike: "nike",
    Adidas: "adidas",
    Puma: "puma",
  };

  let type: keyof typeof object;
  ```

  객체의 경우에도 enum과 똑같이 작동하는 것을 볼 수 있었다. 즉 enum 객체로 변환 되기 때문이다.

<br>

### # **any와 Generic 차이**

<br>

(1) 반환 타입 유추 : 함수의 any타입의 경우 함수의 반환 타입을 알기 어렵지만 제네릭 타입의 경우 호출 시 명시적으로 타입을 선언해줌으로서 반환 타입을 유추하기 쉽다.

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

(2) 프로퍼티 체크 : 함수의 any 타입은 매개변수의 프로퍼티를 체크하지 않고 제네릭 타입은 프로퍼티를 체크하므로 타입가드가 필요하기 때문에 사전에 에러를 방지할 수 있다.

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

<br>

- 타입스크립트 설정 파일은 타입스크립트 컴파일 규칙을 정의하는 파일이다. 컴파일 규칙 이 외에도 strict 모드 관련 규칙, 타입 작성 규칙 등을 설정할 수 있다.

<br><br><br>

## # Next.js

<br>

### # 클라이언트 컴포넌트와 서버 컴포넌트 (수정 필요)

- 클라이언트 컴포넌트

  - 역할

  - 렌더링 과정

    1. 기본적으로 서버 사이드 렌더링(SSR)을 수행한다. 초기 페이지 접근 시나 새로고침 시 서버에서 HTML을 렌더링하고, 클라이언트는 그 HTML을 하이드레이션하여 상호작용할 수 있도록 만든다.
    2. 클라이언트 사이드 라우팅 시에는 클라이언트 CSR을 수행한다. 클라이언트 컴포넌트는 React Element 객체(JSX로 작성된 React 컴포넌트)를 반환하며, 해당 객체는 Virtual DOM에 Fiber로 확장된다. 이후, Fiber를 통해 Virtual DOM을 생성하고, 이를 바탕으로 실제 DOM을 변환한다.

  - 언제 사용하나요?

    1. 상호작용이 필요한 UI 요소가 있을 때.
    2. 애니메이션이나 동적 UI 업데이트가 필요한 경우.

- 서버 컴포넌트

  - 역할

    1. 이벤트 핸들러나 React 내장 훅(useState, useEffect)을 사용할 수 없습니다.
    2. 서버에서 데이터 fetching을 처리하여, API나 데이터베이스와 연결하고, 서버에서 데이터를 미리 가져와 HTML을 생성합니다. 이 방식은 클라이언트의 데이터 요청을 줄이고 성능을 최적화하는 데 도움을 줍니다.

  - 렌더링 과정

    - 서버 측

      1. 리액트 서버에서 서버 컴포넌트를 RSC payload로 렌더링한다. RSC payload는 서버 컴포넌트의 렌더링 결과, 플레이스홀더 (클라이언트 컴포넌트의 렌더링 되는 위치에 대한 빈자리 표시와 필요한 js 파일에 대한 참조), 서버 컴포넌트가 클라이언트 컴포넌트에 전달하는 props를 가지고 있다.
      2. nextjs 서버에서는 해당 rsc payload와 클라이언트 컴포넌트 자바스크립트 인스트럭션(최소한의 js, 예를 들면 state의 초기 값)을 조합하여 정적인 HTML을 생성한다. 여기까지가 서버에서의 동작이다.

    - 클라이언트 측

      3. 서버에서 생성한 HTML을 전달받아 즉시 보여준다. 다만 초기 라우팅, 즉 서버 사이드 라우팅인 경우만 이 HTML을 활용한다. 이후 클라이언트 사이드 라우팅인 경우에는 활용하지 않는다.
      4. 재조정(reconcile)한다. 재조정이란 클라이언트 컴포넌트와 서버 컴포넌트 트리를 구성하는데 이것이 리액트 컴포넌트 트리이며 이 리액트 컴포넌트 트리(버츄얼 돔)에서 클라이언트 컴포넌트 트리에 빈자리(플레이스홀더)를 RSC payload에 포함되어있는 플레이스홀더 정보를 활용하여 채워주는데 이 과정을 재조정이라고 한다.
      5. 재조정을 통해 버츄얼 돔 클라이언트 컴포넌트 트리에 빈자리를 채운 뒤 인터렉션이 가능하도록 하이드레이션(수화)한다. 하이드레이션 시에는 서버에서와 마찬가지로 클라이언트 컴포넌트 자바스크립트 인스트럭션을 활용하는데 다른 점은 정적인 최소한의 js가 아닌 setState나 이벤트 핸들러 등과 같이 동적인 자바스크립트 인스트럭션(해당 자바스크립트 인스트럭션은 웹팩을 통해 쪼개진 js 청크이다. 네트워크를 통해 클라이언트, 즉 브라우저에서 전달받는다.)을 활용해서 하이드레이션하여 정적인 HTML이 인터렉션이 가능하도록 한다. (JavaScript instructions로 클라이언트 컴포넌트만 hydration 한다)

  - 언제 사용하나?
    1. 비상호작용적인 콘텐츠를 렌더링할 때.
    2. 서버에서 데이터 fetching을 처리할 때.
    3. SEO 최적화를 고려할 때.
    4. 정적 콘텐츠나 대규모 데이터 처리가 필요할 때.

- 검증해야할 점
  - https://nextjs.org/docs/app/building-your-application/rendering/client-components 해당 공식문서를 보면 클라이언트 컴포넌트는 초기 방문, 새로고침 등에서 서버 컴포넌트 렌더링 과정과 거의 흡사하게 렌더링된다. 왜 그런지 찾아봐야겠다.. 또한 서버 컴포넌트는 서버 사이드 라우팅인 경우만 정적인 HTML을 사용하는데 이유가 뭘까.. 즉 두 컴포넌트가 거의 동일하게 동작하는데 차이점은 정확히 뭘까..
    - 서버 컴포넌트만 사용하는 경우 하이드레이션 과정이 없다.
    - 서버 컴포넌트의 경우 브라우저로 전달되는 js 번들에 포함되지 않는다.
    - 위와 같이 비슷하게 동작하는 이유는 아마 함께 사용할 때에 이점을 가져가기 위해서인 것 같다. 서버 컴포넌트와 클라이언트 컴포넌트를 함꼐 사용할 때 페이지 전체를 서버 컴포넌트, 인터렉션이 필요한 부분에만 클라이언트 컴포넌트로 분리해서 js 번들 사이즈를 최소화하는 것이다.
    - 클라이언트 컴포넌트의 경우 서버 컴포넌트와 다르게 SSR 시에 정적인 html과 함께 인터렉션을 위한 js 번들을 같이 내려준다.
    - 즉 최종적으로 정리해보면 클라이언트 컴포넌트도 SSR을 수행하는데 정적인 부분에 HTML을 생성하고 필요한 js 번들을 클라이언트로 보내 하이드레이션한다. 서버 컴포넌트의 경우 HTML 생성 후 하이드레이션하지 않는다. 즉 JS 번들에 포함되지 않는다.
    - RSC payload에 클라이언트 컴포넌트에 대한 참조를 포함하고 있느냐의 차이

<br><br><br>

## # Network

<br>

### # **네트워크 용어**

<br>

- 노드

  데이터를 송신, 수신, 작성, 저장할 수 있는 네트워크 내의 연결 지점이다.

<br>

- 네트워크

  노드들이 데이터를 공유할 수 있게 하는 디지털 통신망, 네트워크에서 여러 장치들이 노드 간 연결을 사용해 서로 데이터 교환

<br>

- 인터넷(Internet)

  전 세계 네트워크를 하나로 연결하는 거대한 컴퓨터 통신망

<br>

- 월드 와이드 웹(WWW)

  세계 최초의 웹 브라우저로서 인터넷에 연결된 사용자들이 서로의 정보를 공유할 수 있는 공간 및 상호연결 시스템이다.

<br>

- 프로토콜(Protocol)

  컴퓨터나 원거리 통신 장비(네트워크 장비)에서 데이터 통신을 원활하게 하기 위해 정해놓은 통신 규약이다.

<br>

### # **쿠키, 세션, 웹 스토리지**

<br>

- 쿠키, 세션, 웹 스토리지란?

  - 쿠키

    사용자가 웹 사이트 접속 시 해당 웹 사이트의 서버가 사용자의 웹 브라우저에 전송하는 작은 기록 정보 데이터, 브라우저는 이 데이터를 저장해놓고 필요시 정보를 참조하거나 재사용

  - 세션

    세션은 일정 기간 동안 들어오는 사용자 요청을 하나의 상태로 보고 그 상태를 유지시키는 기술이다. 쿠키를 기반으로 동작하지만 사용자 정보를 클라이언트 측이 아닌 서버 측에서 관리하여 보안이 취약하다는 쿠키의 단점을 극복하고자 사용한다. 동작 방식은 클라이언트에서 로그인 요청 시 서버에서 세션을 생성하고 저장한다. 그 후 유니크한 세션 ID를 생성하여 세션 ID를 클라이언트로 전달한다. 클라이언트는 전달받은 세션 ID를 쿠키에 저장하고 이후 요청 시 요청 헤더 쿠키에 세션 ID를 보내고 서버는 세션 ID를 통해 사용자를 식별한다. 세션은 사용자가 로그아웃하거나 만료 시간이 지날 때 삭제된다.

  - 웹 스토리지

    웹 스토리지는 클라이언트에서 데이터 저장하기 위한 브라우저 저장소이다. Key, value 구조로 저장되며 로컬 스토리지와 세션 스토리지로 나뉜다. 로컬 스토리지는 모든 창에서 접근 가능, 의도적으로 삭제하지 않는 이상 영구적이고 세션 스토리지는 동일한 탭에서만 접근 가능, 탭이나 창을 닫을 때 제거된다. 웹 스토리지는 쿠키의 단점을 보완하고자 추가되었는데 쿠키는 서버 요청을 할 때마다 자동으로 서버에 전송되며 임의로 고치는 것이 가능해서 보안이 취약하다는 단점이 있지만 웹 스토리지는 필요한 경우에만 사용하므로 자동 전송의 위험이 없고 트래픽 비용을 줄여준다.

<br>

- 쿠키, 세션, 웹 스토리지 사용 이유

  데이터 유지와 지속적인 데이터 교환을 위해 사용한다. 클라이언트와 서버는 데이터 통신 시 HTTP 프로토콜을 사용하는데 HTTP 프로토콜의 특징은 클라이언트 요청과 서버의 응답 후 서버에서는 해당 요청과 응답에 대한 상태를 기억하지 않는 무상태 프로토콜이다. 그렇기 때문에 클라이언트에서는 데이터가 필요한 경우 매번 다시 요청해야한다. 이러한 특징으로 인해 문제가 발생할 수 있는데 예시로 클라이언트에서 사용자 아이디와 비밀번호를 담아 로그인 API를 요청하여 로그인하였는데 서버에서는 로그인 했다는 상태를 기억하고 있지 않기 때문에 이후 로그인이 필요한 데이터 요청 시 또 다시 로그인을 해야하는 문제가 발생할 수 있다. 이러한 문제를 해결하기 위해 세션 기반 인증, 토큰 기반 인증 방식을 활용하여 브라우저 저장소에 사용자 인증 정보를 담은 JWT나 세션 ID를 저장한 후 매 요청 시 재사용하는 방식을 통해 이런 문제를 해결할 수 있다.

<br>

- 서버 여러 대일 때 세션 처리 (세션 동기화 전략, 세션 클러스터링이라고 함) -> 정확 x, 조사 필요

  서비스의 규모가 커지면 서버를 여러 대 두고 운용하게 된다. 이 때 트래픽을 여러 서버로 분산해서 사용하게 되는데 이 기술을 로드 밸런싱이라고 한다. 세션은 서버에 저장되는데 로드 밸런싱에 의해 요청이 분산될 경우 서버마다 세션이 공유되지 않기 때문에 세션을 제대로 활용 못하는 상황이 생겨버린다. 이러한 방식을 해결하기 위해 세션 클러스터링 방식을 사용할 수 있다.

  세션 클러스터링 방식은 각 서버의 세션 저장소를 하나로 묶어서 관리하는 것이다. 모든 서버가 동일한 세션을 공유하기 때문에 특정 서버로만 트래픽이 몰릴 필요가 없으며, 하나의 서버가 죽어도 세션 정보를 잃어버릴 일은 없게 된다. 하지만 모든 서버의 세션 데이터를 동일하게 유지하기 위해서 하나의 세션이 생기면 모든 서버의 세션 저장소를 업데이트해줘야 하며 그만큼 많은 메모리가 필요하기 때문에 성능 저하가 발생하게 된다.

  이러한 번거로움을 없애기 위해 세션만 관리하는 별도의 서버를 하나 두는 방식이 바로 세션 클러스터링 방식 중 세션 서버 방식이다. 세션 서버 방식은 서버마다 세션 저장소를 둬서 관리하지 말고 세션만 관리하는 별도의 서버를 하나 두는 방식이다. 세션 서버를 사용하기 때문에 모든 서버의 세션 저장소를 업데이트해줄 필요가 없으며, 클러스터링할 필요도 없다. 또한, Redis 같은 In-memory(인메모리) 데이터 저장소를 사용함으로써 빠르게 세션을 조회할 수 있다.

<br>

### # **JWT 토큰(JSON Web Token)**

<br>

- JWT 토큰이란?

  JSON Web Token으로 로그인과 같은 인증(유저 아이디 및 비밀번호 확인)/인가(로그인 유저가 요청하는 요청을 처리할 수 있는 지 권한 확인)에서 사용한다. 로그인을 처리하는 방식으로 세션 기반 인증과 토큰 기반 인증이 있는데 토큰 기반 인증에서 사용한다. 세션 기반 인증은 서버에서 세션 ID를 전달받아 쿠키에 저장하여 인증하는 방식이고 토큰 기반 인증은 서버에서 발행해주는 토큰을 전달받아 쿠키나 웹 스토리지에 저장하여 인증하는 방식이다.

<br>

- 토큰 기반 인증을 사용하는 이유

  세션 기반 인증은 세션을 서버에 저장하기 때문에 서버의 확장성이 떨어지고, 서버 확장 시 세션을 동기화하기 위한 세션 클러스터링과 같은 별도의 처리가 필요하며 사용자 수가 증가할 수록 서버 메모리의 부담이 증가한다는 단점이 있다. 반면 토큰 기반 인증은 인증 정보를 서버에 저장하지 않기 때문에 서버에 확장성이 상대적으로 높고 서버 메모리의 부담을 주지 않는다.

<br>

- JWT 토큰을 사용하는 이유는?

  (1) 데이터 크기 : JWT는 XML 기반의 SAML(Security Assertion Markup Language) 방식보다 크기가 작다.

  (2) 보안성 : SMT(Simple Web Token) 방식은 대칭키 방식으로 해싱하지만 JWT와 SAML 토큰은 공개키/개인키 방식을 사용한다. 인증 과정에서 대칭키 방식은 인증 확인자가 같은 키로 데이터를 만들어 다른 인증 확인자에게 잘못 사용될 수 있다는 문제가 있다. 또한 인증 과정은 인증 확인자가 데이터를 생성할 필요 없이 확인만 하면 되기 때문에 공개키/개인키 방식이 더 적합하다.

  (3) 호환성 : JSON은 대부분 언어에서 객체로 바로 변환될 수 있기 때문에 대부분의 언어에서 지원하고 있다.

<br>

- JWT 토큰 구조

  (1) Header (헤더) : Token의 기본요소, 헤더에는 일반적으로 토큰의 타입과 해싱 알고리즘 명시

  (2) Payload (페이로드) : 전달하려는 데이터, key-value 페어로 클레임 정보를 포함한다. 클레임의 종류로는 등록된 클레임, 공개 클레임, 비공개 클레임이 있다.

  (3) Signature (시그니쳐) : 서명된 값, header와 payload를 해싱 알고리즘에 의해 계산한 결과를 포함

<br>

- JWT 동작 방식

  (1) 클라이언트에서 id, pw 정보를 서버로 보냄

  (2) 서버에서 id, pw 정보를 이용하여 JWT token 을 생성함

  (3) 서버에서 클라이언트로 JWT token 을 보냄

  (4) 클라이언트에서 서버로 서비스 요청시, JWT token 을 같이 보냄.

  (5) 서버에서 서비스 처리시, JWT token 을 검증, 일치하면 서비스를 동작시켜 클라이언트로 응답

<br>

- JSON 사용 이유

  웹 애플리케이션에서 데이터를 주고받을 때 사용하는 대표적인 데이터 포맷으로는 XML과 JSON이 있다. XML은 HTML과 유사한 마크업 언어이다. XML의 단점은 불필요한 태그들이 포함되어 파일의 사이즈가 크고 가독성도 좋지 않으며 배열을 파싱할 수 없기 때문에 배열을 사용할 수 없다는 단점이 있다. 반면 JSON은 자바스크립트의 객체와 같은 구조로 구성되어 있어 가독성도 높고 작성하기도 편리하며 호환성도 뛰어나고 배열도 사용할 수 있다는 장점이 있다.

<br>

- JWT 안전하게 사용하는 방법

  (1) 사용자 로그인 시 서버에서 사용자 확인 후 액세스 토큰, 리프레쉬 토큰 발급하고 리프레쉬 토큰 값은 DB에 저장, 이 때 이 때 액세스 토큰의 시간 유효기간은 짧게, 리프레쉬 토큰의 시간 유효기간은 길게 설정

  (2) 서버에서 리프레쉬 토큰의 실제 값이 아닌 index값이나 해쉬 값을 액세스 토큰과 함께 클라이언트에 전달

  (3) 클라이언트에서 리프레쉬 토큰 인덱스 혹은 해쉬 값은 쿠키로 관리한다. 왜냐하면 가장 필수로 막아야하는 XSS 보안(클라이언트 단에서 실행되는 악의적 스크립트, 가장 필수적으로 막아야하는 공격)에 유리하기 때문이다. 또한 서버에서는 httpOnly 속성을 쿠키로 설정(document.cookie와 같은 자바스크립트로 쿠키를 조회하는 것을 막는 옵션)해서 XSS 공격을 막고 또 추가로 secure (https가 아닌 통신에서 쿠키전송 x), SameSite (strict의 경우 같은 도메인만 허용, lax의 경우 strict과 비슷하지만 일부 예외)와 같은 옵션을 지정한다.

  (4) 클라이언트에서 액세스 토큰은 로컬 변수로 관리, 권한 필요 시 Authorization 헤더에 access token을 담아 요청

  (5) 매 요청 시마다 액세스 토큰과 리프레쉬 토큰 index 혹은 해쉬 값을 같이 담아서 보내어 매번 액세스 토큰을 새로 발급받는 방식을 사용한다. 매 요청 시 담아 보내는 이유는 매 요청 시 액세스 토큰을 새로 발급하여 탈취당하더라도 이전 액세스 토큰을 만료시켜버리기 위함이다. 그리고 필요 시 매 요청 시 리프레시 토큰도 새로 발급 받는 방식도 사용할 수 있다.

  (6) 리프레쉬 토큰의 index 혹은 hash 값이 저장된 쿠키는 외부 경로와 자바스크립트 상에서의 접근이 불가능하여 CSRF, XSS 공격에서 모두 안전성이 확보된다. 액세스 토큰이 저장된 로컬 변수는 XSS에 상대적으로 안전하며 매 요청 시 재발급을 통해 보안을 더욱 강화한다.

  (7) 결론 : 즉 이런 방식을 사용해서 CSRF 공격에 의해 서버에 있는 리프레쉬 토큰을 탈취당해도 공격자는 실제 인증 정보가 담긴 액세스 토큰에 대해서는 알 수 없게 되고 쿠키를 사용해서 XSS 공격을 막을 수 있다. 또한 만약 액세스 토큰이 탈취당하더라도 유효 기간이 매우 짧고 매 요청 갱신되기 때문에 이러한 방식은 보안에 효과적이다.

<br>

### # **만약 토큰이 만료됐다면 이 요청을 어떻게 다시 처리할것인가?**

<br>

- 액세스 토큰과 리프레쉬 토큰을 함께 사용하는 방식으로 처리할 수 있다. 액세스 토큰은 그 자체로 인증 정보를 모두 가지고 있어서 탈취되면 매우 위험한 상황이 발생할 수 있다. 그러므로 만료 기간을 지정해주어야 하는데 만료 기간이 다 했을 경우에는 액세스 토큰을 재발급 할 수 있는 리프레쉬 토큰을 사용해야한다. 리프레쉬 토큰은 새로운 액세스 토큰을 생성하는 용도로만 사용된다. 굳이 별도의 리프레쉬 토큰을 두고 새로운 액세스 토큰을 발급받도록 한 이유는 보안 때문이다. 액세스 토큰의 유효기간을 짧게 설정하고 리프레쉬 토큰의 유효기간을 길게 설정한 뒤 둘 다 서버에 전송하여 액세스 토큰으로 인증하고 만료 시 리프레쉬 토큰으로 액세스 토큰을 새로 발급받는다. 만약 공격자에 의해 액세스 토큰을 탈취 당하더라도 유효 기간이 짧기 때문에 유효 기간이 지나면 사용할 수 없고 정상적인 클라이언트는 리프레쉬 토큰으로 액세스 토큰을 재발급 받은 뒤 사용할 수 있다. 단 리프레쉬 토큰은 서버에 저장해두어야 한다고 한다. 서버에 실제 리프레쉬 토큰 값을 저장하고 index값을 쿠키나 로컬스토리지에 저장하는 방식으로 유효기간이 긴 리프레쉬 토큰이 탈취당하는 것을 방지할 수 있다고 한다. 또 index값 또한 단순 index값이 아닌 hash값을 생성해 사용하면 보안에 더욱 유리하다고 한다.

<br>

### # Oauth 2.0

- Oauth2(Open Authorization 2.0)란 인증을 위한 표준 프로토콜이다. 이 프로토콜에서는 써드파티 프로그램에게 리소스 소유자를 대신해 리소스 서버에서 제공하는 자원에 대한 접근 권한을 위임하는 방식으로 작동된다. 구글, 페이스북 등 외부 소셜 계정을 기반으로 간편하게 인증하는 기능이다. 기존의 인증방식과 달리 인증을 중개해주는 방식이라고 생각하면 된다. Resource Owner(유저), Client(애플리케이션 서버), Authorization Server, Resource Server, Access Token, Refresh Token로 구성된다.

<br>

### # **SOP정책과 CORS**

<br>

- SOP(same-origin)정책이란?

  same-origin policys는 동일 출처 정책인데 동일 출처 정책은 출처(origin)에서 로드된 문서나 스크립트가 다른 출처에 자원과 상호작용하지 못하도록 제약하는 정책이다. 통신을 주고 받는 두 URL의 프로토콜, 호스트, 포트번호 모두 동일한 경우만 동일 출처가 된다. 만약 다른 출처에서 리소스를 불러오려면 그 출처에서 올바른 CORS 헤더를 포함한 응답을 반환해야 한다.

<br>

- CORS란?

  CORS는 교차 출처 리소스 공유(Cross-Origin Resource Sharing)라고 하며 교차 출처의 리소스 공유를 허용하는 정책이다. HTTP 프로토콜을 사용하여 요청을 보낼 때 브라우저는 요청 헤더에 Origin 필드에 요청을 보내는 출처를 담아보낸다. 이후 서버가 이 요청에 대한 응답을 할 때 응답 헤더 Access-Control-Allow-Origin 필드에 요청이 허용된 출처를 담아 응답하고 이후 응답을 받은 브라우저는 자신이 보냈던 요청의 Origin 필드와 서버가 보내준 응답의 Access-Control-Allow-Origin 필드를 비교하여 허용된 요청인지 판단하고 아닌 경우 CORS 에러를 반환한다. CORS 에러를 해결하는 방법은 서버에 Access-Control-Allow-Origin 필드에 허용 출처로 추가할 것을 요청하거나 프록시로 우회하여 요청 출처를 바꿔 해결할 수 있다.

<br>

### # **Local storage에 Token을 사용한 이유**

<br>

- 브라우저 저장소 중 로컬 스토리지를 처음으로 활용해보았기 때문에 로컬 스토리지에 저장하였다. 그 후 학습해보니 JWT 토큰은 자동 로그인과 같은 기능을 위해 쿠키나 로컬 스토리지에 많이 저장한다고 알고 있다. 두 가지는 장단점이 있는데 로컬 스토리지는 CSRF 공격에는 안전하고 XSS 공격에는 취약하다. 쿠키는 반대로 XSS 공격으로부터 localStorage에 비해 안전하며 CSRF 공격에 취약하다고 알고있다. 결론으로 가장 좋은 방법은 refresh token을 사용하는 방법이 있다고 한다. 백엔드 api 개발자와 소통이 가능하다면 refresh token을 httpOnly 쿠키로 설정하고 url이 새로고침 될 때마다 refresh token을 request에 담아 새로운 accessToken을 발급 받는다. 발급 받은 accessToken은 js private variable에 저장한다. 이런 방식을 사용하는 경우, refresh token이 CSRF에 의해 사용된다 하더라도 공격자는 accessToken을 알 수 없다. CSRF는 피해자의 컴퓨터를 제어할 수 있는 것이 아니기 때문이다. 요청을 위조하여 피해자가 의도하지 않은 서버 동작을 일으키는 공격 방법이기 때문에 refresh token을 통해 받아온 response(accessToken)는 공격자가 확인할 수 없다. 따라서 쿠키를 사용하여 XSS를 막고 refresh token 방식을 이용하여 CSRF를 막을 수 있다.

<br>

- XSS(Cross Site Scripting)는 무엇인가요?

  XSS은 공격자가 의도하는 악의적인 js 코드를 피해자 웹 브라우저에서 실행시키는 것이다. 희생자 클라이언트 PC에서 실행되며 사용자의 정보를 탈취하는 것이다. XSS 공격을 막는 것은 웹 보안을 위한 최소한의 조치이다.

<br>

- CSRF(Cross site request forgery)는 무엇인가요?

  정상적인 request를 가로채 피해자인 척 하고 백엔드 서버에 변조된 request를 보내 악의적인 동작을 수행하는 공격을 의미한다. CSRF는 위조된 요청을 서버에 보내어 서버단에서 스크립트가 실행된다.

<br>

- XSS 대응방법

  (1) 입/출력값 검증 : 입출력 값에 대해 목적에 맞는지 다양한 검증

  (2) 보안 라이브러리 사용 : 오픈소스 보안 라이브러리를 활용하여 XSS를 방지한다.

  (3) HttpOnly 속성 사용 : 스크립트에서 쿠키에 접속하는 것을 방지하는 HttpOnly 옵션을 사용한다.

  (4) CSP(Content Security Policy) : 사이트에서 직접 컨텐츠별로 정책을 정의하여 사이트에서 허용한 컨텐츠에만 접근하도록 하는 브라우저 표준 보안 정책을 적용한다.

  (5) 올바른 Content-Type 사용 : 적절한 Content-Type을 지정하여 악성 스크립트가 실행되지 않도록 해준다.

<br>

- CSRF 대응방법

  (1) Referrer 검증 : request의 header에 존재하는 referrer 속성을 확인하여 요청을 한 페이지의 정보를 검증하고 차단하는 방법이다.

  (2) Security Token(CSRF Token) 검증 : 특정 조건(로그인 등)일 때 사용자의 세션에 임의의 난수 값을 저장하고, 사용자의 요청 마다 해당 난수를 포함시켜 전송한다. 그리고 요청이 들어올 때 마다 세션에 저장된 값과 요청으로 전송된 난수값이 일치하는지 서버에서 검증하는 방법이다.

  (3) Double Sumbit Cookie 검증 : 세션을 사용 못하는 환경에서 사용하는 방법으로 웹브라우저의 Same Origin 정책으로 인해 자바스크립트에서 타 도메인의 쿠키 값을 확인/수정하지 못한다는 것을 이용한 방법이다. 스크립트 단에서 요청 시 난수 값을 생성하여 쿠키에 저장하고, 동일한 난수 값을 요청 파라미터로 서버에 전송한다. 서버에서는 쿠키의 토큰 값과 요청시 들어온 파라미터의 토근 값이 일치하는 지 검사하는 방법이다.

<br>

### # RESTful API, GraphQL, Path Parameter, Query Parameter

<br>

- API란?

  API(Application Programming Interface)란 단어 자체의 뜻 처럼 어플리케이션 프로그래밍 인터페이스를 말한다. 인터페이스란 쉽게 말해 자판기의 버튼과 같은 역할을 하며 소프트웨어와 소프트웨어 간의 정보교환 창구이다. 지정된 형식으로 요청, 명령을 받을 수 있는 수단을 말한다. 예를 들어 기상청서버로부터 미리 작성된 소프트웨어(지정된 형식, 공개된 메뉴얼)를 통해 날씨 정보를 요청하고 전송 받을 수가 있다.

<br>

- Restful API란?

  REST란 자원을 URI로 구분하여 해당 자원의 상태를 주고 받는 아키텍처이다. REST API는 REST의 특징을 지키며 설계된 API이며 자원, 행위, 표현으로 구분되어 있다. 가장 중요한 REST API의 설계 규칙은 URI로 자원을 명시하고, 자원에 대한 행위는 HTTP 메소드(GET, POST, PUT, DELETE, PATCH)로 표현해야 한다는 것이다. 즉 RESTful 하다는 것은 REST API를 제공하는 웹 서비스를 RESTful 하다고 할 수 있다.

  (참고 : 자원 - URL, 행위 - HTTP 메소드, 표현 - 클라이언트의 자원 조작 요청 시 서버의 응답, JSON 등)

<br>

- GraphQL 이란?

  페이스북에서 만든 API 요청을 위한 쿼리 언어이다. 하나의 엔드 포인트를 사용하고, 요청 시 사용한 쿼리 문에 따라 응답의 구조가 달라진다. 서로 다른 모양에 응답이 필요할 때, 대부분의 요청이 CRUD에 해당할 때 사용한다. 원하는 필드만 요청하기 때문에 데이터 오버 패칭을 해결할 수 있고 언더패칭으로 인한 API 추가 호출을 막을 수 있다. 또한 응답 데이터 가공 로직이 상대적으로 간결해진다는 장점이 있다.

<br>

- REST API 와 GraphQL 차이

  (1) 엔드 포인트 : RESTful API 는 Resource 마다 하나의 Endpoint 를 가지고, 그 Endpoint 에서 그 Resource 에 대한 거의 모든 것을 담당한다. 반면, GraphQL 은 전체 API 를 위해서 단 하나의 Endpoint 만을 사용한다.

  (2) 응답 구조 : Restful API 는 하나의 Endpoint 에서 돌려줄 수 있는 응답의 구조가 정해져 있는 경우가 많다. 반면, GraphQL 은 사용자가 응답의 구조를 자신이 원하는 방식으로 바꿀 수 있다. 그렇기 때문에 필요한 데이터만 뽑아올 수 있다.

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

<br>

- 패스 파라미터(Path Parameter)

  슬래시로 구분하며 동적 라우팅과 같이 리소스를 식별할 때 사용한다. (예시 : `localhost:3000/product/2`)

<br>

- 쿼리 파라미터(Query Parameter)

  물음표로 시작하고 key, value로 구성되며 엔드로 연결한다. 정렬, 필터, 검색 시 사용한다. (예시 : `localhost:8000/products?limit=10&offset=5`)

<br>

### # 아폴로 클라이언트(Apollo Client)

아폴로 클라이언트(Apollo Client)는 GraphQL로 서버와 통신 후 결과 값을 캐싱, 재사용, 공유할 수 있게 해주는 상태 관리 라이브러리이다. 또한 꼭 서버와 통신하지 않아도 로컬 쿼리와 스키마를 생성하고 해당 쿼리 결과 값을 캐싱 및 재사용할 수도 있다. 사용 경험은 코드제너레이트 돌려서 원격 스키마로부터 타입을 추출한 후 Apollo Client의 useQuey나 useMutation 사용 시 해당 타입의 도큐먼트를 매개변수로 전달하여 요청을 하였다.

<br>

- SDK란?

  소프트웨어 개발 키트로 일반적으로 운영체제나 프로그래밍 언어 제작사 등이 제공하며 SDK를 활용한 개발을 위한 툴이나 리소스를 제공한다. 예를 들어 카카오톡 소셜 로그인 기능 구현 시 SDK를 script에 연결하여 구현하는 방식과 REST API를 활용하여 구현하는 방식 등으로 구분된다.

<br>

- SDK와 API 차이

  API는 SDK에 비해 가볍지만 SDK가 더 많은 유틸리티 및 개발 도구를 포함하도 있어 API의 경우 특정 기능 및 데이터를 요청하기 위해 사용한다면 SDK는 특정 애플리케이션을 구축하거나 복잡한 기능을 수행하기 위해 사용할 수 있다. 이러한 점에서 API는 SDK의 일부가 될 수 있고 SDK가 API보다 더 큰 개념이라고 할 수 있다.

<br>

### # **apllo client useQuery의 fetchPolicy / nextFetchPolicys**

<br>

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

### # **사용자가 주소를 입력하고 화면이 나타날 때까지의 과정은? (참고 : https://deveric.tistory.com/97)**

<br>

(1) 주소창에 URL을 입력후 엔터를 치면 브라우저는 URL파싱(프로토콜,도메인,포트) 후 DNS서버에 해당 URL에 IP주소 요청

(2) DNS서버에 요청하여 해당 URL을 IP주소로 변환하여 응답

(3) IP주소를 응답받은 뒤 라우터를 통해 접속하고자 하는 해당 서버의 게이트웨이를 찾아 해당 서버의 네트워크로 이동

(4) 해당 네트워크 내부에 있는 컴퓨터 중 IP주소에 해당하는 컴퓨터를 찾기 위해서는 MAC주소가 필요, 해당 네트워크 내 MAC주소를 조회해주는 ARP(Address Resolution Protocol) 프로토콜을 통해 논리 주소인 IP주소(변할수 있는 주소)를 물리 주소인 MAC주소(고유한 주소)로 변환

(5) MAC주소 확보 후 대상 서버와 통신을 위해 TCP 소켓 연결

(6) TCP 소켓 연결 후 대상 서버에 페이지 구성을 위해 필요한 리소스 자원을 HTTP 프로토콜로 요청하고 응답받음

(8) 응답받은 리소스 자원을 통해 웹 브라우저는 렌더링 과정 진행 후 화면에 표시

<br>

### # **HTTP에 대해 말해달라**

<br>

- HTTP 프로토콜

  컴퓨터 네트워크에서 데이터를 주고 받을 때 사용하는 통신 규약이다.

<br>

- HTTP 프로토콜 특징

  (1) 구조 : 요청과 응답으로 이루어져있고 start line, headers, body 구조로 이루어져있다.

  (2) 무상태(Stateless) 프로토콜 : 각각의 요청이 독립적이고 서로 관련이 없다. 현재 요청은 이전 요청에 대한 상태를 전혀 알 수 없다.

  (3) 비연결 지향(Connectionless) 프로토콜 : 요청과 응답이 완료되면 연결을 끊어버린다.

<br>

- HTTP 프로토콜 구조 설명

  - start line

    한 줄로 표현되며 요청 start line은 `GET /post/94 HTTP/1.1`과 같이 http메소드(GET), 요청 패스 혹은 쿼리(/post/94), http 버전(HTTP/1.1)을 표현하고 응답 start line은 `HTTP/1.1 200 OK`와 같이 http 버전(HTTP/1.1)과 응답 메세지(200 OK)를 표현한다.

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

<br>

- HTTP 프로토콜 메소드

  (1) GET : 데이터를 조회(Read)할 때 사용한다.

  (2) POST : 새로운 정보를 추가/생성(Create)할 때 사용한다. body가 있어 데이터 담아 전송할 수 있다.

  (3) DELETE : DELETE는 삭제(Delete)시에 사용한다.

  (4) PUT & PATCH : PUT 또는 PATCH는 수정(Update)시에 사용한다. 작업자에 따라 PUT 하나만 사용하는 경우도 있지만, 두 가지를 구분하면 PUT은 데이터를 통째로 갈아끼울 때, PATCH는 정보 중 일부를 특정 방식으로 갈아 끼울 때 사용한다. body가 있어 데이터 담아 전송할 수 있다.

<br>

- UDP, TCP/IP란?

  (0) 패킷 : 라우팅되는 데이터 단위, 라우팅 시 효율적인 데이터 교환을 위해 나눈 데이터 조각

  (1) TCP/IP : 데이터를 메세지의 형태로 보내기 위해 IP와 함께 사용하는 연결 지향적 프로토콜이다. IP가 패킷 전달을 수행한다면 TCP는 패킷을 추적 및 관리하게 된다. 연결 지향 프로토콜이란 클라이언트와 서버가 연결된 상태에서 데이터를 주고받는 프로토콜을 의미한다. 클라이언트가 연결 요청(SYN 데이터 전송)을 하고, 서버가 연결을 수락하면 통신 선로가 고정되고, 모든 데이터는 고정된 통신 선로를 통해서 순차적으로 전달된다.

  (2) UDP : 데이터를 데이터그램 단위로 처리하는 프로토콜이다. 여기서 데이터그램이란 독립적인 관계를 지니는 패킷이라는 뜻이다. TCP와 달리 UDP는 비연결 지향적 프로토콜이다. 비연결 지향적이란 데이터를 주고받을 때 연결 절차를 거치지 않고 발신자가 일방적으로 데이터를 발신하는 방식을 의미한다.

  (3) TCP/IP, UDP 차이

  |                | TCP                  | UDP                    |
  | -------------- | -------------------- | ---------------------- |
  | 연결 방식      | 연결 지향적 프로토콜 | 비연결 지향적 프로토콜 |
  | 패킷 교환 방식 | 가상 회선 방식       | 데이터그램 방식        |
  | 전송 순서      | 보장                 | 비보장                 |
  | 수신 여부 확인 | 확인                 | 확인하지 않음          |
  | 통신 방식      | 1:1 통신             | 1:1, 1:N, N:N 통신     |
  | 신뢰성         | 높다                 | 낮다                   |
  | 속도           | 느리다               | 빠르다                 |

<br>

- SSL(Secure Sockets Layer)

  통신 데이터(패킷)을 암호화하여 통신하는 보안 프로토콜이다. SSL/TLS를 사용하는 웹사이트의 URL 프로토콜은 HTTP 대신 HTTPS를 사용하며 SSL은 SSL인증서가 있는 웹사이트에서만 실행할 수 있다.

<br>

- SSL 통신 과정 (참고: https://wayhome25.github.io/cs/2018/03/11/ssl-https/)

  (1) 클라이언트에서 서버로 랜덤 데이터와 사용 가능한 암호화 방식을 전송

  (2) 서버에서 클라이언트로 랜덤 데이터, 사용할 암호화 방식과 SSL 인증서 전송

  (3) 클라이언트에서는 자신이 보낸 랜덤 데이터와 서버로부터 받은 랜덤 데이터를 조합하여 대칭키로 활용할 임시키 생성한 후 서버로부터 받은 인증서를 신뢰할 수 인증서인지 CA를 통해 검증 후 인증서의 공개키로 생성한 임시키를 암호화하여 서버에게 전송

  (4) 서버는 자신이 들고 있던 비밀키로 임시키를 복호화

  (5) 클라이언트와 서버는 임시키를 활용하여 대칭 키 생성한 후 생성 된 대칭 키로 암호화된 데이터를 주고 받으며 세션 종료 시 대칭 키 폐기

<br>

- HTTP와 HTTPS의 차이

  HTTP 프로토콜은 컴퓨터 네트워크에서 데이터를 주고 받을 때 사용하는 통신 프로토콜이다. HTTPS는 HTTP 프로토콜에 데이터 암호화가 추가된 프로토콜이다. 공개키/개인키 방식을 활용해 데이터를 암호화한다. HTTPS는 암호화가 추가되어 안전하게 데이터를 주고 받을 수 있다. 단점은 SSL 인증서를 발급하고 유지하는데 추가 비용이 발생한다.

<br>

- HTTP 버전별 차이 (참고: https://withbundo.blogspot.com/2021/02/http-http-10-http-11.html)

  (1) HTTP/0.9 : GET 메서드만 지원, HTTP 헤더 없음

  (2) HTTP/1.0 : 메서드, 헤더 추가(⇒ HTML 이외 다른 파일 전송 가능), 한 커넥션 당 한개의 요청, 요청과 응답이 이루어진 후 다음 요청 가능

  (3) HTTP/1.1 : 동시에 여러 개(최대 6개)의 요청과 각각의 응답을 받을 수 있는 파이프라이닝 추가, 버츄얼 호스팅(하나의 IP에 여러 도메인)을 가능하게 하는 호스트 헤더 추가, 한 커넥션 당 여러개의 요청을 할 수 있는 커넥션 유지 기능 추가, 현재 HTTP/1.1가 가장 많이 사용ㄴ

  (4) HTTP/2 : HTTP/1.1 까지는 한번에 하나의 파일만 전송이 가능했다. 이로인해 여러 파일을 전송 할 경우, 선행하는 파일의 전송이 늦어지면, 전체 파일 전송의 시간이 늘어나는 문제가 발생하였다. HTTP/2에서는 여러 파일을 한번에 병렬 전송하여, 이러한 문제를 해결하였다. 이 외에도 다른 HTTP/1.1의 성능을 개선한 버전이다.

  (5) HTTP/3 : 개발 진행 중, TCP 대신에 UDP 사용, 성능 개선

<br>

- 에러 상태 코드 차이

  (1) 200번대 : 200번대의 상태 코드는 대부분 통신 성공을 의미한다.

  (2) 300번대 : 300번대의 상태 코드는 대부분 클라이언트가 이전 주소로 데이터를 요청하여 서버에서 새 URL로 리다이렉트를 유도하는 경우이다.

  (3) 400번대 : 400번대 상태 코드는 대부분 클라이언트의 코드가 잘못된 경우이다. 유효하지 않은 자원을 요청했거나 요청이나 권한이 잘못된 경우 발생한다. (400 요청 에러, 401 인증 에러, 404 자원 에러)

  (4) 500번대 : 500번대 상태 코드는 서버 쪽에서 오류가 난 경우이다.

<br>

### # **DNS란?**

<br>

- DNS란 도메인 네임 시스템으로 IP 주소와 도메인 주소를 연결해주는 시스템으로 네임 서버라고도 불린다. 사용자가 주소창에 도메인 주소를 입력하면 해당 도메인 주소를 가지고 있는 네임 서버에 요청을 보내고 네임 서버는 도메인 주소에 IP 주소를 찾은 후 응답해준다.

<br>

### # **인공지능 > 머신러닝 > 딥러닝**

<br>

- 인공지능

  인공지능이란 인간이 가지고 있는 지적 능력을 컴퓨터에서 구현하는 다양한 기술이나 소프트웨어, 컴퓨터 시스템 등을 말한다.

<br>

- 머신러닝

  컴퓨터가 스스로 학습할 수 있도록 도와주는 알고리즘이나 기술을 개발하는 분야, 머신러닝에서는 컴퓨터가 학습을 통해 새로운 규칙을 생성할 것을 기대한다.

<br>

- 딥러닝

  머신러닝 모델의 한 종류로 인공신경망을 여러 개 연결하여 인간의 뇌와 유사한 정보 입출력 계층을 만듦으로써 데이터를 학습하게 하는 기술이다.

<br>

### # **인터넷의 발전**

<br>

(1) 컴퓨터 <-> 컴퓨터

인터넷의 가장 기본적인 것은, 컴퓨터들이 서로 통신 가능한 거대한 네트워크라는 것이다. 케이블 또는 무선으로 연결을 지속한다.

(2) 컴퓨터 <-> 라우터 <-> 컴퓨터

여러 대의 컴퓨터가 연결될 때 많은 플러그와 케이블이 필요하게 되는데 이런 문제를 해결하기 위해 라우터가 연결된다. 중간에 라우터가 위치하여 컴퓨터와 라우터 혹은 컴퓨터 사이에서 통신을 전달한다. 라우터 끼리의 연결도 가능하다.

(3) 컴퓨터 <-> 라우터 <-> 모뎀 <-> 라우터 <-> 컴퓨터

먼 곳에 있는 컴퓨터와 연결하기 위해 네트워크를 전화 시설과 연결하게 된다. 이 때 모뎀이라는 장비를 활용하여 네트워크의 정보를 전화 시설에서 처리할 수 있는 정보로 바꾸어 어느 곳에 있는 라우터와 통신이 가능하도록 한다.

(4) 컴퓨터 <-> 라우터 <-> 모뎀 <-> ISP1 <-> ... <-> ISP2 <-> 모뎀 <-> 라우터 <-> 컴퓨터

모뎀을 통해 전화시설에 연결 후 ISP(인터넷 서비스 제공 업체)를 통해 도달해야 할 컴퓨터 혹은 네트워크까지 도달하게 한다. ISP는 네트워크 연결을 담당하며 다른 ISP와 통신할 수 있도록 한다.

<br>

### # **왜 VPN 연결이 필요한지?**

<br>

- VPN(Virtual Private Network)

  가상 사설망이라고 하며 두 대 이상의 장치 간의 암호화 된 보안 터널이다.

<br>

- VPN 사용 이유

  (1) 대체 IP 사용 : 대체 IP 주소를 사용하기 때문에 위치 추적이 불가능하다.

  (2) 데이터 암호화 : 모든 데이터를 암호화한다. 데이터 암호화를 통해 ISP가 사용자 데이터를 판매하는 것을 방지할 수 있고 개방형 와이파이를 안전하게 사용할 수 있다.

  (3) 추가적인 보안 : 악성 웹사이트, 애드, 트래커를 차단한다.

  (4) 지역별 차단 우회 : IP를 사용한 지역별 차단을 우회하여 거주자 전용 컨텐츠 등을 확인할 수 있다.

<br>

### # **URI와 URL,URN**

<br>

- URI

  URI 통합 자원 식별자로 URL과 URN을 포함하는 개념이다. 가장 흔한 URI는 URL이다.

<br>

- URL

  우리가 아는 일반적인 웹 주소 형식이다, 리소스의 location을 가리키는데 사용된다.

<br>

- URN

  http와 같은 프로토콜을 제외한다, 리소스의 name을 가리키는데 사용된다.

<br>

- URI, URL 구성

  | 부분                             | 명칭     | 설명                                                                                |
  | -------------------------------- | -------- | ----------------------------------------------------------------------------------- |
  | file://, http://, https://       | scheme   | 통신 프로토콜                                                                       |
  | 127.0.0.1, www.google.com        | hosts    | 웹 페이지, 이미지, 동영상 등의 파일이 위치한 웹 서버, 도메인 또는 IP                |
  | :80, :443, :3000                 | port     | 웹 서버에 접속하기 위한 통로                                                        |
  | /search, /Users/username/Desktop | url-path | 웹 서버의 루트 디렉토리로부터 웹 페이지, 이미지, 동영상 등의 파일이 위치까지의 경로 |
  | q=JavaScript                     | query    | 웹 서버에 전달하는 추가 질문                                                        |

<br>

### # **폴링, 롱폴링, 소켓 통신, 웹소켓, Server-Sent Event에 대해 설명해주세요.**

<br>

- 폴링(Polling)

  리얼타입 웹을 위한 기법, 브라우저가 일정한 주기로 HTTP 요청을 보내는 방식이다. 보통 실시간 데이터의 업데이트 주기는 예측하기 어려우므로, 그에 따른 불필요한 서버 및 네트웍 부하가 늘어난다.

<br>

- 롱폴링(Long-Polling)

  리얼타입 웹을 위한 기법, HTTP 요청 시 서버는 해당 요청을 일정 시간 동안 대기 시킨다. 만약, 대기 시간 안에 데이터가 업데이트되었다면, 그 즉시 클라이언트에게 응답을 보내고 전달받은 데이터를 처리 후 서버로 재요청을 시작한다.

<br>

- 웹소켓

  HTTP 프로토콜은 비연결지향 프로토콜로 요청과 응답이 완료된 후 커넥션 연결을 끊어버리는 특징이 있지만 웹소캣의 경우 커넥션을 유지하여 언제든 양방향 통신이 가능하도록 하는 기술이다. 최초 연결은 HTTP 프로토콜을 통해 이루어지고 이후 웹소캣 연결이 완료되면 독자적인 프로토콜을 사용한다. 실시간 채팅과 같이 리얼타임 같은 기능에 사용된다.

<br>

- SSE(Server-Sent Event)

  웹소켓이 양방향 통신이라면 SSE는 단방향 통신으로 클라이언트가 데이터를 받을 수만 있게 하는 통신 방법이다. 웹소켓과 달리 HTTP프로토콜을 사용하며 알람 같은 기능에 사용된다.

<br>

### # **telnet, SSH, FTP, SFTP**

<br>

- telnet

  인터넷이나 로컬 영역 네트워크 연결에 쓰이는 TCP/IP 기반의 네트워크 프로토콜, 보안 문제 때문에 원격 제어를 위해 SSH(Secure Shell)를 사용하는 것이 좋다. (신호/명령 제어 21번 포트, 데이터 전송 20번 포트)

<br>

- FTP(File Transfer Protocol)

  TCP/IP 프로토콜을 가지고 서버와 클라이언트 사이의 파일 전송을 위한 프로토콜, 보안이 취약하다. (기본 21번 포트)

<br>

- SSH(Secure Shell)

  네트워크를 통한 원격 호스트 연결 과정을 보호하기 위해 설계된 프로토콜로 텔넷의 보안 버전이다. 강력한 인증방법을 제공하거나 보안통신 기능을 제공한다. 또한 암호화 기법을 사용하기 때문에 통신이 노출되어도 암호화된 문자로 보여진다. (기본 22번 포트)

<br>

- SFTP(Secure File transfer protocol)

  SFTP는 SSH방식을 이용하여 안전하게 암호화된 구간에서 FTP 기능을 이용 가능하도록 한 프로토콜 (SSH가 사용하는 포트)

<br>

### # **공인 IP, 사설 IP**

<br>

- 공인 IP

  인터넷 사용자의 로컬 네트워크(LAN)를 식별하기 위해 ISP(인터넷 서비스 공급자)가 제공하는 IP 주소이다. 공용 IP 주소라고도 불리며 외부에 공개되어 있는 IP 주소이다.

<br>

- 사설 IP

  로컬 IP, 가상 IP라고도 불리며, 외부에서 접근할 수 없는 IP를 의미한다. 일반 가정이나 회사 내부에서 사용할 목적으로 할당된 IP 주소이며, 공인 IP가 할당된 라우터나 공유기를 통해 로컬 네트워크에 연결된 기기에 사설 IP가 할당된다.

<br>

### # **포트 포워딩, 내부포트, 외부포트**

<br>

- 포트(Port)

  프로세스를 식별하기 위해 호스트 내부적으로 프로세스가 할당받는 고유한 값이다. 어떠한 데이터가 송수신을 할 때 데이터링크 계층에서는 호스트(네트워크에 연결된 컴퓨터)의 NIC로 MAC 주소를 판별하고 네트워크 계층에서는 IP 주소로 목적지를 판별한다. 이렇게 MAC 주소와 IP 주소를 통해 목적지 호스트까지 도달한 후에는 어떤 프로세스에서 데이터를 받을 것인지를 알아야 하는데 이 때 쓰이는 것이 포트 번호이다.

<br>

- 포트 포워딩(Port-Forwarding)

  포트 포워딩이란 컴퓨터 네트워크에서 패킷이 라우터나 방화벽 같은 네트워크 게이트웨이를 통과하는 동안 네트워크 주소를 변환해주는 것을 의미한다. 사용자가 외부IP를 통해 접속을 요청했을 때 내부IP에 접속할 수 있도록 포트를 연결해주는 것을 말한다.

<br>

- 내부포트

  내부 포트란 외부에서 8080 포트로 접속한 기기를 내부의 어떤 포트 번호로 연결해 주느냐에 대한 포트 번호이다.

<br>

- 외부포트

  외부 포트란 웹 브라우저에서 공인 IP를 통해 내부 웹서버(컴퓨터)로 접속할 때 공인 IP 뒤의 ":"(콜론) 뒤에 붙는 숫자가 외부 포트 번호이다. 사용자가 외우기 쉬우면서 기존 포트 번호와 겹치지 않는 번호로 설정해야한다.

<br>

### # **OSI 7계층이란? 각 계층은?** (물데네전세표응)

<br>

- OSI(Open Systems Interconnection Reference Model) 7계층

  OSI 7계층은 국제표준화기구(ISO)에서 개발한 모델로, 네트워크에서 통신이 일어나는 과정을 7단계로 나누어 표현한 모델이다. 7계층으로 나눈 이유는 통신의 흐름을 파악하기 쉽게 하고 통신 장애 발생 시 특정 단계에 이슈만 해결하면 되기 때문에 7계층으로 나누게 되었다고 한다.

<br>

- 1계층 물리계층(Physical Layer)

  물리적 장치를 통해 데이터 전송한다. (케이블, 리피터, 허브 등)

<br>

- 2계층 데이터 링크계층(DataLink Layer)

  물리계층에서 송수신되는 정보에 대한 에러검출, 재전송, 흐름제어를 하여 정보가 안전하게 전달되도록 도와준다. (브릿지, 스위치 등)

<br>

- 3계층 네트워크 계층(Network Layer)

  라우터를 통해 이동할 경로를 선택하여 IP 주소를 지정하고, 해당 경로에 따라 패킷을 전달해준다. (라우터, IP 등)

<br>

- 4계층 전송 계층(Transport Layer)

  TCP와 UDP 프로토콜을 통해 통신을 활성화한다. 포트를 열어두고, 프로그램들이 전송을 할 수 있게 한다. (TCP, UDP)

<br>

- 5계층 세션 계층(Session Layer)

  데이터가 통신하기 위한 논리적 연결을 담당한다. TCP/IP 세션 생성, 유지, 종료, 복구 등을 수행한다. (API, Socket)

<br>

- 6계층 표현 계층(Presentation Layer)

  코드 변환, 데이터 암호화, 압축, 구문 검색, 정보 형식 변환, 문맥관리 등의 기능을 수행한다. (JPEG, MPEG 등)

<br>

- 7계층 응용 계층(Application Layer)

  네트워크 소프트웨어 UI 부분, 사용자의 입출력(I/O)부분이다. (HTTP, FTP, DNS 등)

<br>

### # **캡슐화와 역캡슐화**

<br>

- 캡슐화와 역캡슐화

  컴퓨터의 웹 브라우저에 URL을 입력할 때부터 웹 서버에 데이터가 도착할 때까지 각 과정에서는 캡슐화와 역캡슐화가 이루어진다.

<br>

- 캡슐화

  데이터를 보내는 송신 측에서 데이터를 보낼 때 데이터의 앞부분에 전송 시 필요한 정보가 담긴 헤더를 붙여서 다음 계층으로 보내는데 이 과정을 캡슐화라고 한다. 헤더에는 추가적인 정보 데이터와 데이터를 전달받을 상대방에 대한 정보가 담겨져 있다. 캡슐화가 진행되는 방향은 상위 계층에서 하위 계층이다. (응용 -> 물리)

<br>

- 역캡슐화

  데이터를 받는 수신 측에서 데이터와 추가 된 헤더를 분리하여 헤더를 하나 씩 제거해나가는 과정을 역캡슐화라고 한다. 역캡슐화가 진행되는 방향은 하위 계층에서 상위 계층이다. (물리 -> 응용)

<br>

### # 캐시기억장치의 캐시란? (레지스터, 캐시기억장치, 주기억장치, 보조기억 장치 중 캐시기억장치)

<br>

- 캐시

  자주 사용하는 데이터나 값을 미리 복사해 놓는 임시 장소를 가리킨다. 저장 공간이 작고 비용이 비싼 대신 빠른 성능을 제공한다. 캐시는 비용이 비싸기 때문에 데이나 값을 선별하여 저장하는데 선별할 때는 지역성이 고려되어야 한다. 쿠키/세션과 같은 경우 정보 저장을 통해 사용자 인증을 도와주는 반면 캐시는 웹 페이지가 빠르고 효율적인 처리를 할 수 있도록 도와준다.

<br>

- 캐시의 지역성

  (1) 시간적 지역성 : 최근 액세스 된 기억 장소가 가까운 미래에 다시 액세스 가능성 높음 (공통 변수)

  (2) 공간적 지역성 : 액세스된 기억장소와 인접한 기억장소가 액세스될 가능성 높음 (배열)

<br>

- 캐시 동작 방식

  (1) 데이터 요청이 들어오면 캐시 탐색

  (2) 캐시가 없거나 오래된 경우 원본 데이터가 저장된 곳에서 데이터 조회 후 캐시에 데이터를 복사 및 갱신

  (3) 캐시에 데이터가 있으면 캐시의 저장된 데이터를 제공

  (4) 오래된 데이터는 삭제

<br>

- 로컬 캐시 vs 글로벌 캐시

  속도는 로컬 캐시(로컬 서버 메모리, 디스크 등의 장비에 리소스 사용)가 더 빠르고 글로벌 캐시(별도의 캐시 서버에 저장)는 데이터 공유가 쉽다.

<br><br><br>

## # Web

<br>

### # **브라우저 동작 원리**

<br>

- 브라우저란?

  브라우저란 웹 페이지, 이미지와 같은 콘텐츠를 수신하고 전송하고 표현하는 소프트웨어다. 대표적인 브라우저로 크롬, 사파리 등이 있다. 브라우저의 주요 기능은 사용자가 선택한 URI 주소의 자원을 서버에 요청하고 브라우저에 표시하는 것이다.

<br>

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

<br>

- 브라우저의 동작 과정

  (0) 사용자가 브라우저 주소표시줄에 검색하고자 하는 URL을 입력한다.

  (1) DNS 조회

  검색 주소의 웹 서버 IP 주소를 찾기 위해 브라우저, OS, 라우트, ISP 캐시에 캐싱 된 DNS 기록을 우선적으로 확인하고 캐싱 된 기록이 없다면 IP 주소를 응답 받을 때 까지 루트, 탑 레벨, 세컨드 레벨, 써드 레벨 네임 서버까지 순차적으로 IP 주소를 요청한다.

  (2) TCP/IP 연결

  도메인 주소에 맞는 웹 서버의 IP 주소를 알고난 후에는, 브라우저는 웹 서버와 TCP 3방향 핸드셰이크라는 프로세스를 통해 연결을 설정한다. TCP 3방향 핸드셰이크는 단어 그대로 브라우저와 웹 서버가 SYN과 ACK 메세지들을 가지고 3번의 프로세스를 거친 후에 연결되는 것을 말한다. 이 과정이 완료되면 TCP 연결이 완료된다.

  (3) HTML 파일 요청

  TCP/IP 연결이 완료되면 브라우저는 HTTP GET 요청을 보내 HTML 파일을 요청한다. 웹 서버가 요청을 받으면, 관련 응답 해더와 함께 HTML의 내용을 응답하게 된다. 그 후 브라우저는 렌더링 과정을 통해 사용자에게 해당 페이지의 결과를 나타내게 된다.

<br>

- 브라우저 렌더링 엔진의 동작 과정

  (0) 리소스 요청 및 응답 : 사용자가 웹 페이지 접근 시 해당 페이지에 관한 리소스(HTML, CSS, Javascript, 이미지 파일 등)를 서버에 요청 후 응답 받은 뒤 렌더링 진행

  (1) Parsing : 렌더링 엔진의 HTML 파서가 HTML 파싱하여 DOM(Document Object Model) 트리 생성, CSS 파서가 CSS 파싱하여 CSSOM(Css Object Model) 트리 생성

  (2) Style : 두 트리를 결합하여 렌더 트리 생성

  (3) Layout/Reflow : 렌더 트리에서 각 노드의 위치와 크기를 계산한다.

  (4) Paint/Repaint : 계산된 값을 이용해 각 노드를 화면상의 실제 픽셀로 변환하고, 레이어를 만든다.

  (5) Composite : 레이어를 합성하여 실제 화면에 나타낸다.

  (6) Javascript : 자바스크립트는 렌더링 엔진이 아닌 자바스크립트 엔진이 처리한다. HTML 파서는 script 태그를 만나면 자바스크립트 코드를 실행하기 위해 DOM 생성 프로세스를 중지하고 자바스크립트 엔진으로 제어 권한을 넘긴다. 제어 권한을 넘겨 받은 자바스크립트 엔진은 script 태그 내의 자바스크립트 코드 또는 script 태그의 src 어트리뷰트에 정의된 자바스크립트 파일을 로드하고 파싱하여 실행한다. 자바스크립트의 실행이 완료되면 다시 HTML 파서로 제어 권한을 넘겨서 브라우저가 중지했던 시점부터 DOM 생성을 재개한다.

  (7) Reflow/Repaint : 렌더링 과정을 거친 뒤에 최종적으로 페이지가 그려진다고 해서 렌더링 과정이 다 끝난것이 아니다. 어떠한 액션이나 이벤트에 따라 html 요소의 크기나 위치등 레이아웃 수치를 수정하면 그에 영향을 받는 자식 노드나 부모 노드들을 포함하여 Layout 과정을 다시 수행하게 된다. 이렇게 되면 Render Tree와 각 요소들의 크기와 위치를 다시 계산하게 된다. 이러한 과정을 Reflow라고 한다. Reflow만 수행되면 실제 화면에 반영되지 않는다. Render Tree를 다시 화면에 그려주는 과정이 필요하다. 결국은 Paint 단계가 다시 수행되는 것이며 이를 Repaint 라고 한다.

<br>

### # **Web Server와 WAS**

<br>

- Web Server

  Web Server란 클라이언트(브라우저)로부터 HTTP 요청을 받아 HTML 문서나 각종 리소스를 전달하는 서버이다. 클라이언트의 요청을 기다리고 요청에 대한 데이터를 만들어서 응답한다. 응답하는 데이터는 즉시 응답이 가능한 정적 컨텐츠 (HTML, CSS, 이미지 등)로 한정된다. 이 때 Web Server가 동적 컨텐츠를 요청 받으면 WAS에게 해당 요청을 넘겨주고 WAS에서 처리한 결과물을 클라이언트에게 전달하는 역할도 수행한다. 이러한 웹 서버에는 Apache, NginX 등이 있다.

<br>

- Nginx vs Apache

  Nginx 웹 서버는 Apache 웹 서버의 성능 제한을 해결하기 위해 탄생한 웹 서버, 대용량 트래픽 처리에 적합

<br>

- WAS (Web Application Server)

  WAS란 DB 조회 혹은 다양한 로직 처리를 요구하는 동적 컨텐츠를 제공하기 위해 만들어진 애플리케이션 서버이다. HTTP 프로토콜을 기반으로 사용자 컴퓨터나 장치에 애플리케이션을 수행해주는 미들웨어로서, 주로 데이터베이스 서버와 같이 수행된다. WAS는 JSP, Servlet 구동환경을 제공해주기 때문에 서블릿 컨테이너 혹은 웹 컨테이너로 불린다.

  이러한 WAS는 웹 서버의 기능들을 구조적으로 분리하여 처리하고자 하는 목적으로 제시되었다. 분산 트랜잭션, 보안, 메시징, 쓰레드 처리 등의 기능을 처리하는 분산 환경에서 사용된다. WAS는 프로그램 실행 환경과 DB 접속 기능을 제공하고 DB와 소통한다. 이 때 사용하는 언어가 SQL이다. 또 여러 개의 트랜잭션을 관리 가능하고 비즈니스 로직을 수행할 수 있다. 즉 WAS 역할은 Web Server + Web Container라고 볼 수 있다.

  이러한 WAS에는 Tomcat, JBoss, WebSphere 등이 있다.

<br>

- WAS가 필요한 이유

  웹 페이지는 정적 컨텐츠와 동적 컨텐츠가 모두 존재한다. 이 때 정적 컨텐츠를 제공하는 Web Server만을 사용한다면 사용자가 원하는 요청에 대한 결과 값을 미리 모두 만들어놓은 후 서비스해야 한다. 하지만 이러한 작업을 수행하기에는 자원이 절대적으로 부족하다. 그렇기 때문에 WAS를 통해 요청에 맞는 데이터를 DB에서 가져와 비지니스 로직에 맞게 결과를 만들어 제공함으로써 자원을 효율적으로 사용할 수 있다.

<br>

### # **프론트엔드 서버와 백엔드 서버**

<br>

- 웹 서버

  주소창에 도메인을 검색하면 해당 도메인의 서버(서버는 보통 3가지로 구성된다. 웹 서버, 웹 애플리케이션 서버, 디비 서버)가 해당 요청에 대한 응답을 하는데 이 때 서버는 보통 프론트엔드 서버와 백엔드 서버로 나뉜다.

<br>

- 프론트엔드 서버

  프론트엔드 서버는 클라이언트(브라우저)에서 요청이 왔을 때 번들링하여 미리 준비해둔 HTML, CSS, Javascript 파일들을 제공한다. 예를 들어 react로 개발한 프론트엔드 애플리케이션을 배포할 때 nginx, apache http server와 같은 웹 서버에 react 빌드 파일을 배포한다. 즉 프론트엔드 서버를 웹 서버라고 볼 수 있다.

<br>

- 백엔드 서버

  백엔드 서버는 클라이언트(브라우저) 혹은 프론트엔드 서버에서 필요한 데이터를 전달해준다. 이 때 데이터를 전달해주는 역할만 수행할 뿐 페이지 렌더링에 필요한 정적 리소스를 제공하는 것은 아니기 때문에 API 서버라고도 부른다.

<br><br><br>

## # Data Structure

<br>

### # **자료구조**

<br>

- 자료구조

  자료구조란 데이터를 효율적으로 관리할 수 있는 데이터 구조를 의미한다. 선형구조(직선모양)와 비선형구조(곡선모양)로 나뉜다. 선형구조로는 배열(Array), 연결 리스트(Linked List), 데크(Deque), 스택(Stack), 큐(Queue)가 있고 비선형구조로는 트리(Tree), 그래프(Graph)가 있다.

  ![자료구조](https://user-images.githubusercontent.com/85284246/178629531-dfac3453-33c7-4b5d-8317-5c4af5c1da2b.png)

<br>

- Array

  데이터를 나열하고 각 데이터를 인덱스에 대응하도록 구성한 데이터 구조, 고정 길이이다.

<br>

- Stack

  스택은 늦게 넣은 데이터를 가장 먼저 꺼낼 수 있는 자료구조이다. 후입선출 방식이다.

<br>

- Queue

  큐란 가장 먼저 넣은 데이터를 가장 먼저 꺼낼 수 있는 자료구조이다. 선입선출 방식이다.

<br>

- Deque

  삽입과 삭제가 리스트의 양쪽 끝에서 모두 발생할 수 있는 자료구조이다. 스택과 큐의 장점들을 모두 가지고 있는 방식으로 선입선출, 후입선출 모두 가능하다.

<br>

- Heap

  최대값과 최소값을 빠르게 찾아내도록 만들어진 완전이진트리를 기본으로 하는 자료구조로 반정렬 상태이다.

<br>

- Hash table

  해시 테이블은 해시 함수를 사용하여 키를 해시 값으로 매핑하고, 이 해시 값을 색인(인덱스) 또는 주소 삼아 데이터를 key와 함께 저장하는 자료구조이다. 키(key)와 값(value)이 하나의 쌍을 이루는 데이터 구조이다.

<br>

- Graph

  단순히 노드(정점)와 그 노드(정점)를 연결하는 간선(링크)을 하나로 모아 놓은 자료 구조이다.

<br>

- Tree

  노드들이 나무 가지처럼 연결된 비선형 자료구조이다. Graph의 한 종류이다. 그래프와 차이점은 트리는 한 개의 루트 노드가 존재하고, 노드 간 부모 자식 관계를 가지고 있으며 사이클이 존재하지 않는 방향 그래프이다. 또 간선의 수는 노드 당 1개를 가지고 있고 계층 모델이다.

<br>

- Binary tree

  이진트리라고도 하며 모든 노드들이 최대 두 개의 자식 노드를 가진 트리 자료구조이다.

<br>

- LinkedList

  각 노드가 데이터와 포인터를 가지고 한 줄로 연결되어 있는 방식으로 데이터를 저장하는 자료구조이다. 각 노드의 포인터는 다음 노드의 주소를 값으로 가지고 있다. 일반적으로 링크드 리스트의 시작이 되는 노드는 헤드, 마지막 노드는 테일이라고 부른다.

<br>

- ArrayList

  데이터를 나열하고 각 데이터를 인덱스에 대응하도록 구성한 데이터 구조, Array와 차이점은 길이가 가변한다는 것이다.

<br>

- List, Map, Set 차이

  (1) List : 기본적으로 데이터들이 순서대로 저장되며 중복을 허용한다.

  (2) Map : 순서가 보장되지 않고 Key값의 중복은 허용하지 않지만 Value값의 중복은 허용된다.

  (3) Set : 순서가 보장되지 않고 데이터들의 중복을 허용하지 않는다.

<br><br><br>

## # Algorithm

<br>

### # **알고리즘**

<br>

- 알고리즘

  어떤 문제를 해결하기 위해 사용되는 풀이과정을 말한다. 즉, 문제 해결 방법을 말한다. 효율적인 알고리즘이란 수행을 시작하여 결과가 도출될 때까지 실행에 걸리는 시간이 짧고 연산하는 컴퓨터 내의 메모리와 같은 자원을 덜 사용하는 것이 효율적이라고 할 수 있다.

<br>

- 시간 복잡도

  알고리즘을 수행에 필요한 시간, 표기법으로 빅오엔, 빅세타, 빅오메가 등이 있으며 보통 최악의 수행 시간을 나타내는 빅오엔 표기법 O(n)을 활용한다.

<br>

- 공간 복잡도

  알고리즘 수행에 필요한 메모리 크기

<br>

- Big-O 표기법

  알고리즘에 시간 복잡도와 공간 복잡도를 표기하는 데 사용한다.

<br>

- 정렬 알고리즘

  (1) 선택소트 : 미정렬 부분의 데이터 중에서 가장 작은 값을 선택하고, 선택된 값과 미정렬 부분의 첫 번째 데이터와 교환을 반복하는 알고리즘이다. 최선, 최악, 평균 O(n^2)

  (2) 버블소트 : 한쪽 방향에서부터 시작하여 두 인접한 원소를 순차적으로 검사하며 정렬하는 알고리즘이다. 최선 O(n), 최악 O(n^2)

  (3) 힙소트 : 최대 힙 트리나 최소 힙 트리를 구성해 정렬을 하는 알고리즘으로, 내림차순 정렬을 위해서는 최소 힙을 구성하고 오름차순 정렬을 위해서는 최대 힙을 구성하면 된다.

  (4) 삽입소트 : 정렬이 완료되지 않은 자료를 선택하여 이미 정렬이 완료된 앞(왼쪽)의 자료들과 비교하여 삽입할 위치를 지정한 후 자료를 뒤로 옮기고 지정한 자리에 자료를 삽입하여 정렬하는 알고리즘이다. 최선 O(n), 최악 O(n^2)

  (5) 퀵소트 : 하나의 리스트를 선택한 요소(피벗)를 기준으로 두 개의 비균등한 크기로 분할하고 분할된 부분 리스트를 정렬한 다음, 두 개의 정렬된 부분 리스트를 합하여 전체가 정렬된 리스트가 되게 하는 알고리즘이다. 최선 O(nlogn), 최악 O(n)

  (6) 머지소트 : 하나의 리스트를 두 개의 균등한 크기로 분할하고 분할된 부분 리스트를 정렬한 다음, 두 개의 정렬된 부분 리스트를 합하여 전체가 정렬된 리스트가 되게 하는 알고리즘이다. 최선, 최악, 평균 O(nlogn)

<br>

- 탐색 알고리즘

  (1) 순차 탐색 알고리즘(Sequential Search) : 순차 탐색 알고리즘, 또는 선형 탐색 알고리즘은 리스트에서 특정한 값을 찾는 알고리즘의 하나다. 이것은 리스트에서 찾고자 하는 값을 맨 앞에서부터 끝까지 차례대로 찾아 나가는 것이다.

  (2) 이진 탐색 알고리즘(Binary Search) : 오름차순으로 정렬된 리스트에서 특정한 값의 위치를 찾는 알고리즘이다. 처음 중간의 값을 임의의 값으로 선택하여, 그 값과 찾고자 하는 값의 크고 작음을 비교하는 방식을 채택하고 있다.

<br>

- 완전 탐색 알고리즘

  (1) 재귀 알고리즘(Recursion) : 다른 말로는 재귀 함수라고 하며 자신을 다시 호출하여 작업을 수행하는 방식을 의미한다. 종료 조건이 꼭 포함되어야하며 반복문을 사용하는 코드는 항상 재귀 함수로 구현할 수 있다.

  (2) 깊이 우선 탐색 DFS(Depth-First Search) : 루트 노드 혹은 다른 임의의 노드에서 시작해서 다음 분기로 넘어가기 전에 해당 분기를 완벽하게 탐색하는 알고리즘이다.

  (3) 너비 우선 탐색 BFS(Breadth First Search) : 루트 노드 혹은 다른 임의의 노드에서 시작해서 분기와 관계없이 인접한 노드를 먼저 탐색하는 알고리즘이다.

  ![깊이우선탐색_너비우선탐색_비교](https://user-images.githubusercontent.com/85284246/178636275-17ac00fe-d3d3-4f81-991e-85ec041264f1.gif)

<br>

- 최단 경로 알고리즘

  (1) 다익스트라 알고리즘(Dijkstra) : 그래프에서 한 정점(노드)에서 다른 정점까지의 최단 경로를 구하는 알고리즘 중 하나이다. 이 과정에서 도착 정점 뿐만 아니라 모든 다른 정점까지 최단 경로로 방문하며 각 정점까지의 최단 경로를 모두 찾게 된다.

<br>

- 분할 정복 알고리즘(Divide and Conquer)

  분할 정복 알고리즘은 주어진 문제를 작은 문제로 분할하여 문제를 해결하는 방법이나 알고리즘이다. 정렬 알고리즘의 퀵소트나 머지소트 문제와 고속 푸리에 변환(FFT) 문제가 대표적인 분할 정복 알고리즘이다.

<br>

- 동적 계획법(Dynamic Programming)

  이미 계산된 결과(하위 문제)는 별도의 메모리 영역에 저장하여 다시 계산하지 않도록 설계함으로써 메모리를 적절히 사용하여 수행 시간 효율성을 향상시키는 알고리즘이다.

<br>

- 탐욕 알고리즘(Greediness)

  미래를 생각하지 않고 각 단계에서 가장 최선의 선택을 하는 알고리즘이다. 이렇게 각 단계에서 최선의 선택을 한 것이 전체적으로도 최선이기를 기대한다.

<br>

- 몬테 카를로 알고리즘(Monte Carlo)

  난수를 이용하여 어떤 함수의 답을 확률적으로 근접하게 계산하는 방식이다.

<br>

### # **퍼지 문자열 검색이란?**

<br>

- 퍼지 검색 알고리즘은 유사한 문자열을 찾는 알고리즘으로 알고 있다. 예를 들어 초성 입력을 통해 추천 검색어를 나타내는 기능을 퍼지 검색 알고리즘으로 구현하는 것이다. 직접 퍼지 검색을 구현해본 적은 없으며 연습삼아 한글 퍼지 검색 라이브러리를 활용하여 구현해본 적은 있다.

<br>

### # **경쟁상대 알고리즘에 대해 분석하시고, 우리사이트에 어떻게 적용할 수 있을까요?**

<br>

- 당장 생각나는 방법은 개발자 탭에서 직접 소스 코드를 확인하는 방법 밖에 생각나지 않습니다. 하지만 소스 코드 분석은 매우 어려운 것으로 알고 있기 때문에 더욱 공부해야할 것 같습니다. 이 부분에 대해서는 더 공부하겠습니다.

<br><br><br>

## # Infra

<br>

### # **AWS 란?**

<br>

- 배포 자동화란?

  말 그대로 배포를 자동화하는 것이고 명령어 하나만으로 배포를 자동적으로 진행하는 것을 말한다. 배포 자동화를 통해 개발자는 개발에만 더욱 집중할 수 있고 주기적인 배포를 통해 사용자가 빠르게 최신 애플리케이션을 접할 수 있게 할 수 있다. 배포 자동화에서 자주 쓰이는 방식으로 CI/CD 방식이 있다. 나는 이전에 nextjs 프로젝트를 vercel을 통해 배포하였는데 vercel은 레파지토리를 연결하기만 하면 CI/CD를 자동으로 구축해주기 때문에 편리하다.

<br>

- CI, CD 방식이 무엇인지 아는지?

  (1) CI(Continuous Integration) : 지속적인 통합을 의미하며 여러 개발자가 작성 및 수정한 코드를 주기적으로 빌드 및 테스트하면서 공유 레파지토리에 통합(merge)하는 것을 뜻한다. 즉 CI/CD 방식에서 CI의 역할은 빌드 및 테스트 자동화이다.

  (2) CD(Continuous Delivery/Continuous Deployment) : 지속적인 서비스 제공 또는 지속적인 배포를 뜻한다. 공유 레파지토리에 CI를 통해 성공적으로 통합 된 내역을 사용자가 사용할 수 있는 배포 환경까지 릴리즈(출시)하는 것을 뜻한다. 즉 CI/CD 방식에서 CD의 역할은 배포 자동화이다. 또한 CD를 수행하기 전 코드의 테스트, 빌드, 통합은 필수이므로 CI가 항상 선행되어야 한다. CI를 성공적으로 마친 후 테스트 서버와 운영 서버에 곧바로 배포되는 환경을 CD라고 한다.

  (3) CI/CD 방식 : 종합적으로 CI/CD 방식은 개발, 빌드, 통합, 배포, 릴리즈 등의 단계를 자동화하는 방식을 말하고 CI/CD 방식을 활용하면 개발 편의성이 증가되고 코드 품질을 유지할 수 있고 출시 기간 단축할 수 있다.

  (4) CI/CD 파이프라인 : CI/CD 방식을 단계 별로 나누어 연결해놓은 구조를 말한다. CI/CD 방식의 파이프라인의 요소로는 빌드(소프트웨어 컴파일), 테스트(호환성 및 오류 검사), 릴리즈(버전 제어 저장소의 애플리케이션 업데이트), 배포(개발에서 프로덕션 환경으로의 변환), 규정 준수 및 유효성 검사 등이 있다.

<br>

- 클라우드 서비스(클라우드 컴퓨팅)란?

  클라우드 서비스란 클라우드 컴퓨팅 기술을 사용하여 제공하는 서비스를 말한다. 클라우드 컴퓨팅 기술이란 인터넷을 통한 구독 기반의 기술로 서버, 스토리지, 소프트웨어 등 필요한 IT 자원을 자신의 컴퓨터가 아닌 클라우드에 연결된 다른 컴퓨터에서 제공해주는 기술을 의미한다.

<br>

- 클라우드 서비스 사용 이유

  (1) 시간 절약 : 직접 하드웨어 인프라나 서버를 갖추지 않아도 되기 때문에 장비 비용 절감 및 빠른 출시가 가능하다.

  (2) 유연한 대응 : 서비스 범위에 따라 유연하게 자원을 증감할 수 있다. 이를 통해 예상치 못한 트래픽 폭주에도 신속하게 대응할 수 있다.

  (3) 비용 절약 : 서비스를 이용한 만큼만 비용을 지불한다.

<br>

- AWS 관련 용어

  (1) EC2 (Elastic Compute Cloud) : AWS에서 제공하는 가상머신 서비스로 AWS의 데이터 센터에서 독립된 서버용 컴퓨터 한대를 임대해서 사용할 수 있게 해주는 서비스이다. AWS가 제공하는 URL(Public DNS)를 통해 이 컴퓨터에 접근할 수 있으며 다양한 사양 옵션을 제공한다. (EC2 인스턴스란 한 대의 컴퓨터를 의미)

  (2) Secuirty Group : EC2 인스턴스에 대한 네트워크 트래픽을 제어하는 가상 방화벽 역할을 한다. 즉 Secuirty Group 설정을 해줘야 EC2 인스턴스에 HTTP와 SSH 접속이 가능하다.

  (3) RDS(Relational Database Service) : AWS의 데이터베이스 서비스이다. RDS를 사용하면 사용자가 직접 서버를 생성해서 데이터베이스를 설치하고 설정하고 관리하지 않아도 된다. 그러면서 동시에 비용도 더 저렴하다. 사용자가 직접 데이터 베이스를 설치하고 운영하는 것보다 RDS를 사용하는것이 더 저렴하다.

  (4) ELB(Elastic Load Balancing) : AWS에서 제공하는 로드 밸런서이다. 등록된 여러 서버의 상태를 모니터링 하면서 상태가 양호한 서버로만 트래픽을 라우팅(HTTP 요청 분산)하여 서버가 죽지 않도록 자동으로 관리해준다.

  (5) Route 53 : AWS의 DNS 서비스이다. 도메인 등록, DNS 라우팅, 상태 확인 등 도메인과 관련된 다양한 서비스를 제공한다.

  (6) CloudFront : AWS의 CDN 서비스이다. 전 세계에 엣지 서버를 두고 클라이언트가 데이터 요청 시 가까운 엣지 서버에서 데이터를 제공할 수 있도록 하여 빠른 속도로 데이터를 제공할 수 있도록 한다. 또 추가적인 기능으로 HTTP로의 접속을 HTTPS로 리다이렉션 시켜주는 기능도 제공한다.

  (7) S3(Simple Storage Service) : AWS의 파일 서버의 역할을 하는 서비스이다. 이름 그대로 파일을 쉽게 저장할 수 있는 공간을 제공한다. 파일을 저장 할 수 있을 뿐만이 아니라 파일마다 고유 주소를 부여해주기 때문에 S3에 저장한 파일을 웹상에서 쉽게 읽을 수 있다. 주로 사이트상의 이미지들을 저장하고 사이트에서 읽어들여 렌더링 해주는데 사용한다.

  (8) PM2(Process Manager) : 노드js용 프로세스 관리 매니저이다. 무중단 배포를 지원하고 노드js는 싱글 스레드 기반이지만 클러스터 모드로 실행하여 프로세스를 원하는 수 만큼 쉽게 늘리고 줄일 수 있다. 프로세스가 늘어나면 성능과 안정성을 높일 수 있다.

  (9) 젠킨스(Jenkins) : CI툴이라고도 하며 소프트웨어 개발 시 지속적으로 통합 서비스를 제공하는 툴이다. 다수의 개발자들이 하나의 프로그램을 개발할 때 버전 충돌을 방지하기 위해 각자 작업한 내용을 공유영역에 있는 저장소에 빈번히 업로드함으로써 지속적 통합이 가능하도록 해준다.

  (10) IAM(Identity and Access Management) : AWS의 리소스에 개별적인 접근 권한을 제어하는 서비스이다. 한 루트 계정에 계정 또는 그룹 등 여러 개의 IAM 계정을 생성하여 각 게정마다 접근 가능한 서비스에 제한을 둘 수 있다.

  (11) VPC(Virtual Private Cloud) : 사용자가 정의하는 가상의 네트워크이다. VPC를 적용하면 VPC별로 EC2 인스턴스를 묶어 독립적인 네트워크를 구성할 수 있고 각각의 VPC에 따라 네트워크 설정을 다르게 할 수 있다.

  (12) WAF (Web Application Firewall) : 웹 애플리케이션 방화벽(WAF)은 웹의 비정상 트래픽을 탐지하고 차단하기 위한 방화벽이다.

<br>

- AWS S3, AWS EC2, AWS Amplify를 활용한 각 프론트 배포 방법 차이

  - AWS EC2

    AWS EC2는 웹 서버 구축 과정이 필요하고, 비용이 S3보다 더 높고, S3보다 많은 설정(운영체제, 보안그룹, 스케일링 관리 등)이 필요하다는 단점이 있지만 그에 따라 많은 제어 또한 가능하다는 장점이 있다. AWS EC2는 웹 서버가 구축되어 있기 때문에 SSR 프로젝트에 적합하다. EC2로 배포하게 된 후 사용자가 접속하면 EC2 인스턴스에 요청이 전달되고 EC2 인스턴스에서 요청을 처리(SSR)하여 HTML 생성 후 응답하게 된다.

  - AWS S3

    AWS S3는 웹 서버 구축 과정이 필요없고 정적인 컨텐츠(build 결과물인 HTML, CSS, Javascript 번들 등)를 배포할 수 있다. EC2에 비해 비용이 상대적으로 저렴하고 배포도 간편하며 보통 AWS CDN 서비스인 Cloudfront(HTTPS 사용, 캐시, 빠른 데이터 제공 등을 위해 사용)와 함께 사용된다. S3로 배포할 프로젝트는 정적 웹페이지로 CSR를 사용하는 프로젝트에 적합하다. S3를 통해 배포한 서비스에 SSR을 구현하기 위해서는 추가적인 작업이 필요하다. S3로 배포하게 된 후 사용자가 접속하면 Cloudfront에 요청이 전달되고 캐시서버에 캐싱 된 데이터가 없다면 S3에 요청을 전달하여 개발자가 업로드한 빌드 결과물을 응답한다. 브라우저는 응답받은 결과물 중 js를 통해 렌더링한다. 그리고 사용자가 다시 접속하게 되면 Cloudfront 캐시서버에 캐싱 된 데이터를 활용하여 응답한다.

  - AWS Amplify

    AWS Amplify로 배포하게 되면 업로드 후, 빌드, 배포 과정을 거치기 때문에 SSR 적용이 가능하다.

  - 대표 프론트 배포 방법

    (1) Nginx : 정적 콘텐츠를 배포하게 해주는 웹 서버이다.

    (2) AWS EC2 : 웹 서버와 WAS 서버 배포가 가능하다.

    (3) AWS S3 + Cloudfront : 정적 콘텐츠(프론트 서버)를 배포하게 해준다.

    (4) AWS Amplify : 정적 콘텐츠(프론트 서버)를 배포하게 해줌. S3+ cloudfront 방법보다 간편하게 배포 가능하며 배포 자동화, 그리고 자동으로 S3와 Cloudfront가 구현된다.

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

### # presigned URL

- AWS의 presigned URL은 미리 서명된 URL을 통해 접근 권한이 없는 S3 버킷에 특정 유효기간동안 get, put이 가능하도록 하는 것이다. presigned URL을 생성하기 위한 createPresignedPost 메소드를 활용할 수 있다.

- 동작 방식

  1. 사용자가 이미지 업로드를 한다.

  2. 클라이언트는 서버에 filename을 보내며 PresignedUrl 요청을 보낸다.

  3. 서버는 응답값으로 PresignedUrl과 파일 이름뒤에 날짜가 추가된 filename을 보낸다.

  4. 클라이언트는 PresignedUrl에 Put 메소드로 file을 함께 넘겨주면 업로드가 완료된다.

  5. 업로드 후 받은 이미지 경로를 String 형태로 서버에 전달한다.

<br>

### # **서버리스 아키텍처**

<br>

- 서버리스 아키텍처란?

  서버리스(Serverless)를 직역하면 `서버가 없다`라는 의미이다. 하지만 사실상 서버가 없다는 것이 아니다. 개발자가 서버를 직접 관리할 필요가 없는 아키텍처를 말한다.

<br>

- 기존 서비스 모델

  - 자체적 시스템 설계 (PaaS, Packaged Software)

    시스템에서 필요한 모든 인프라를 직접 관리하는 것을 의미한다. 공간, 하드웨어, 네트워크, 운영체제 등 모두 직접 관리하는 것이다. 단점은 시간과 비용 소모가 크다.

  - 클라우드 서비스 모델

    - 서비스형 인프라 (IaaS, Infrastructure as a Service)

      서버, 스토리지, 네트워킹 및 가상화된 컴퓨팅 인프라를 제공한다. 해당 서비스 모델을 제공받는 클라이언트는 서버자원, 네트워크, 전력 등의 인프라를 직접 구축할 필요 없이 관리자 패널에서 인프라를 구성하고 사용하면 된다. 가상머신을 만들고, 네트워크를 설정하고, 하드웨어도 설정하고, 거기에 운영체제를 설치해서 애플리케이션을 구동 할 수 있고 사용량을 쉽게 모니터링 할 수 있다. 또한 트래픽이 증가하거나 감소함에 따라 유연한 방식으로 컴퓨팅 리소스를 운영할 수 있다. IaaS의 예시로는 AWS, Microsoft Azure 등이 있다.

    - 플랫폼을 통한 서비스 (PaaS, Platform as a Service)

      IaaS 에서 한번 더 추상화된 모델이라고 생각하면 된다. 네트워크, 그리고 런타임까지 제공된다. 해당 서비스 모델을 제공받는 클라이언트는 응용 프로그램을 구축하는 데에만 집중할 수 있고 애플리케이션만 배포하면 바로 구동시킬 수 있게 된다. PaaS의 예시로는 Hiroku, AWS Elastic Beanstalk, Azure App Services 등이 있다. 이를 사용하면 `Auto Scaling(요청 양에 따른 가상 서버 대수 증가)` 및 `Load Balancing(여러 가상 서버에 요청 분산)`도 손쉽게 적용 할 수 있다.

    - 서비스형 소프트웨어 (SaaS, Software as a Service)

      공급업체가 모든 물리적 및 가상 핵심 인프라, 미들웨어, 데이터베이스 관리 시스템, 개발 툴 등을 제공하고 호스팅한다. 여기에 추가로 `데이터`와 `응용 프로그램`이 포함된다. 즉, 특정 앱 또는 웹 포털을 통해 액세스하는 서비스로, 클라이언트 조직의 최종 사용자에게 제공되는 완전한 소프트웨어 솔루션을 말한다. 사용자는 별도의 설치없이 인터넷 연결만 가능하다면 해당 소프트웨어를 즉시 사용할 수 있다. SaaS의 예시로는 웹 메일, 구글 클라우드, 아이 클라우드, 드롭박스 등이 있다.

<br>

- 서버리스 컴퓨팅 서비스

  - BaaS (Backend as a Service)

    BaaS는 백엔드 관리자 영역을 모듈화하여 서비스로 제공한다는 개념인데 앱 개발에 있어서 필요한 기능들(데이터베이스, 소셜서비스 연동, 파일시스템 등)을 API로 제공해준다. 이 기능들을 제공해줌으로서 개발자들이 서버 개발을 하지 않고도 필요한 기능을 쉽고 빠르게 구현할 수 있고 사용한 만큼 비용을 지불한다. 대표적인 BaaS의 예시로는 Auth0, AWS Cognito, Firebase 등이 있다.

  - FaaS (Function as a Service)

    코드, 즉 함수를 서비스로 제공한다. 애플리케이션 개발에서 서버를 프로비저닝하거나 관리하지 않고도 코드를 실행할 수 있도록 해주는 컴퓨팅 서비스이다. 함수를 실행하기 위해 서버를 올리고 런타임을 구성하고 코드를 배포해서 실행해야 하는 일련의 과정을 없애고, 원하는 로직을 함수로 등록해놓고 각 클라우드 서비스 제공사의 조건만 충족하면 특정 이벤트가 발생했을 때 함수가 호출된다. 함수가 호출되면 컨테이너나 가상머신(VM)이 실행되며 정의한 함수가 런타임 내에서 실행된 다음 작업을 마치면(혹은 최대 타임아웃 시간이 지나면) 종료된다. 그리고 이 함수들이 실행되는 횟수, 시간에 비례하여 비용을 지불하게 된다.

    FaaS는 백엔드 구현, 크롤링, 이미지 업로드 시 리사이징, AWS Cloudwatch 및 CloudTrail과의 연동을 통한 로그 분석 및 실시간 모니터링, 기타 자동화 작업 등 다양한 방식으로 활용이 가능하다. 넷플릭스의 경우 동영상 인코딩, 검증, 태깅, 공개, 백업 등의 작업들을 `AWS Lambda`를 통해 자동화 시켰다.

    하지만 FaaS 사용 시 함수에서 사용 가능한 자원에 제한(AWS에서는 최대 1500MB 메모리 사용, 최대 300초의 처리 시간), 콜드 스타트(호출 시 함수가 구동되는데 시간이 걸림), 로컬 데이터 사용 불가능(함수들은 무상태적이므로 로컬 스토리지 사용 불가 및 변수와 데이터 공유 불가능)하다는 특징을 고려하며 사용해야한다.

<br><br><br>

## # Operating System

<br>

### # 리눅스 쉘 명령어

<br>

- man : 다양한 리눅스 명령어의 사용법을 알 수 있다.

- mkdir : 디렉토리 생성

- ls : 현재 폴더의 폴더 및 파일 확인

- pwd : 현재 디렉토리 경로 출력

- cd : 디렉토리 이동

- echo : 텍스트 출력

- sudo : 다른 사용자의 권한을 얻음

- cp : 디렉토리 복사

- mv : 디렉토리 경로 이동 및 이름 수정

- clear : 쉘 창에 있는 기록 지우기

- cat : 텍스트 출력, 여러 파일을 붙혀서 실행 가능

- history : 실행했던 명령어 리스트 출력

- find : 파일 및 디렉토리 검색

- ps : 프로세스 목록 및 상태 출력

- curl : Client URL, 웹서버에 요청을 보낼 수 있음

- grep : 정규표현식 사용으로 파일 내에 특정 문자열 찾은 후 출력

- chmod : 파일 권한 변경

- nohup : 터미널 종료 후에도 계속 백그라운드에서 작업 유지

<br>

### # **비트, 바이트, 32비트 64비트 차이**

<br>

- 비트(bit)

  컴퓨터의 처리 정보의 최소 단위이다. 비트는 바이너리 디짓의 약자로 바이너리는 2진수를 뜻하고 디짓은 자릿 수를 뜻한다. 0또는 1이 하나의 비트가 된다. 컴퓨터는 0 또는 1의 나열로 일을 처리하는데 결국 비트열(비트의 나열)로 모든 것을 표현하게 되는 것이다.

<br>

- 바이트(byte)

  컴퓨터는 일반적으로 8bit를 하나의 단위로 묶어 사용하는데 이것이 바이트이다.

<br>

- 32비트와 64비트 차이

  CPU가 정보를 처리하는 최소단위를 레지스터라고 하며 레지스터는 CPU 내부의 메모리이다. 레지스터는 명령어 해석이나 연산시에 사용되는 데이터를 순간적으로 저장한다. 여기서 32비트와 64비트의 차이는 CPU가 한번에 처리하는 레지스터의 크기가 32비트 혹은 64비트냐에서 차이가 나는 것이다. 또한 처리량의 한계치가 단순히 두 배가 차이나는 것이 아닌 32비트는 2의 32제곱이고, 64는 2의 64제곱이므로 차이가 크다.

<br>

### # **Parsor에 대해 설명하시오**

<br>

- 파싱(Parsing)

  구문 분석이라고도 하며 구문 분석의 통해 문서나 문장을 구성 성분으로 분해하고 위계 관계를 분석하여 문장의 구조를 결정하는 것을 말한다. 예를 들어 브라우저 렌더링 엔진에 HTML 파서가 HTML 문서를 파싱하여 DOM트리를 형성하는 것을 말한다.

<br>

- 파서(Parser)

  컴파일러의 일부로 parsing을 수행하는 프로그램

<br>

### # **커넥션 풀(Connection Pool)**

<br>

- 커넥션 풀(Connection Pool)이란?

  커넥션 풀이란 DB와 미리 커넥션(connection, 연결)을 해놓은 객체들을 풀(pool, 웅덩이)에 저장해두었다가, 클라이언트 요청이 오면 커넥션을 빌려주고, 처리가 끝나면 다시 커넥션을 반납받아 풀에 저장하는 방식을 말합니다.

<br>

- 커넥션 풀(Connection Pool)을 쓰는 이유와 단순히 커넥션을 새로 만드는 것의 차이

  (1) 빠른 접속 : DB 접속 설정 객체를 미리 만들어 연결하여 메모리 상에 등록해 놓기 때문에 불필요한 작업(커넥션 생성, 삭제)이 사라지므로 클라이언트가 빠르게 DB에 접속이 가능하다.

  (2) 서버 자원 고갈 방지 : DB Connection 수를 제한할 수 있어서 과도한 접속으로 인한 서버 자원 고갈 방지가 가능하다.

  (3) 쉬운 유지 보수 : DB 접속 모듈을 공통화하여 DB 서버의 환경이 바뀔 경우에도 쉬운 유지 보수가 가능하다.

  (4) 비용 절감 : 연결이 끝난 Connection을 재사용함으로써 새로 객체를 만드는 비용을 줄일 수 있다.

<br>

### # **프로세스와 스레드의 차이**

<br>

- 프로그램

  특정 작업을 실행하기 위한 규칙 또는 순서를 나타내는 명령어들의 모음이다.

<br>

- 프로세스

  프로그램이 운영체제에 의해 메모리 공간(코드,데이터,스택,힙)을 할당받아 실행 중인 상태로 실행 중인 프로그램을 말한다.

<br>

- 스레드

  프로세스 내에서 실제로 작업을 수행하는 주체(실행 흐름 단위)를 의미한다. 모든 프로세스에는 한 개 이상의 스레드가 존재하며 프로세스 자원을 공유한다.

<br>

### # **싱글스레드(Single Thread)언어와 멀티스레드(Multi Thread) 언어의 차이점은?**

<br>

- 싱글 스레드

  프로세스가 단일 스레드로 동작하는 방식이다. 하나의 레지스터, 스택으로 표현한다. 가장 대표적으론 자바스크립트가 싱글 스레드 언어이다.

<br>

- 싱글 스레드 장점

  (1) 동기화 X : 멀티 스레드와 같이 자원의 동기화를 신경 쓸 필요가 없다.

  (2) 문맥 전환 X : 단일 스레드로 동작하기 때문에 문맥을 교환할 필요가 없다.

  (3) 낮은 난이도 : 프로그래밍이 쉽다.

<br>

- 싱글 스레드 단점

  (1) CPU 활용 : 싱글 스레드는 하나의 물리적 코어밖에 사용하지 못해 멀티 코어 머신에서 CPU 사용을 최적화할 수 없다. 최적화를 위해선 Cluster 모듈을 이용하여 여러 프로세스를 사용할 수 있다. 하지만 프로세스끼리의 자원 공유는 어렵기 때문에 Redis와 같은 부가 인프라가 필요하다.

  (2) 동기적 실행 : 이전 작업이 수행되어야 다음 작업을 할 수 있다.

  (3) 에러 시 멈춤 : 싱글 스레드는 에러 처리를 못하는 경우 실행이 멈춘다.

<br>

- 멀티 스레드

  프로세스의 두 개 이상의 스레드가 프로세스 내부에서 자원을 공유하여 작업을 수행한다. 각각의 스레드가 고유 레지스터와 스택으로 표현된다. 이러한 작업은 문맥 전환(컨텍스트 스위칭)을 통해 이루어지며 매우 빠르기 때문에 유저는 동시에 수행되는 것처럼 보이는 것이다.

<br>

- 멀티 스레드 장점

  (1) 응답성 : 스레드 중 하나가 지연되거나 중단되어도 다른 스레드로 극복

  (2) 경제성 : 프로세스 내 자원 공유로 메모리 공간과 시스템 자원 소모가 줄어든다.

  (3) 비동기적 실행 : 작업이 병렬적으로 처리될 수 있다.

<br>

- 멀티 스레드 단점

  (1) 느림 : 스레드 간의 문맥 전환, 동기화 등의 이유로 싱글 스레드보다 느릴 수 있다.

  (2) 동기화 O : 스레드는 데이터와 힙 영역을 공유하므로 공유하는 변수나 자료구조에 여러 스레드가 동시 접근 시 예상치 못한 값을 수정하거나 가져올 수 있기 때문에 동기화가 필요하다. (스레드 스케쥴링을 신경써야 함)

  (3) 높은 난이도 : 프로그래밍이 어렵다.

<br>

- 싱글 스레드, 멀티 스레드 차이

  (1) 스레드 수 : 싱글 하나 / 멀티 하나 이상

  (2) 에러 시 멈춤 : 싱글 O / 멀티 X

  (3) 문맥 전환 : 싱글 X / 멀티 O

  (4) 동기 비동기 : 싱글 동기 / 멀티 비동기

  (5) 프로래밍 난이도 : 낮음 / 멀티 어려움

  (6) 자원 소모 : 싱글 싱글 스레드 덜 사용 하므로 상대적으로 낮음 / 멀티 상대적으로 높음

  (7) 스레드 스케쥴링 : 싱글 신경안씀 / 멀티 신경써야함

<br>

### # **메모리가 어떻게 구성되어 있는지 설명해 주세요.**

<br>

(1) 코드 영역 : 실행될 프로그램의 코드가 저장되어 있는 영역

(2) 데이터 영역 : 전역 변수와 정적 변수가 저장되어 있는 영역

(3) 스택 영역 : 지역 변수와 매개 변수가 저장되어 있으며, 함수의 호출과 함께 할당되는 영역

(4) 힙 영역 : 사용자에 의해 동적으로 할당되고 해제될 수 있는 메모리 영역으로 스택 영역은 컴파일 타임(코드가 컴파일 되는 과정, 신택스 오류나 타입체크 오류같은 컴파일링을 방해하는 에러가 컴파일 에러)에 크기가 결정되고, 힙 영역은 런타임(프로그램이 실제 실행되는 과정, 0나누기 오류나 Null참조 오류 등 런타임을 방해하는 에러가 런타임 에러)에 크기가 결정

<br>

### # **사용자 수준 스레드, 커널 수준 스레드, 혼합 스레드**

<br>

- 스레드(Thread)

  프로세스는 커널 위에서 실행되고 있는 작업인데 이 프로세스 내에서 실행되는 흐름의 단위가 스레드이다. 프로세스는 이러한 스레드를 한 개 이상으로 나눌 수 있다. 스레드는 프로그램 카운터와 스택 포인터 등을 비롯한 스레드 실행 환경 정보, 지역 데이터, 스택을 독립적으로 가지면서 코드, 전역 데이터, 힙을 다른 스레드와 공유한다. 스레드는 크게 커널 영역과 사용자 영역으로 구분된다.

<br>

- 사용자 수준 스레드

  스레드 라이브러리를 이용하여 작동하고, 사용자 영역에 있는 스레드 여러 개가 커널 영역의 스레드 한 개에 다대일로 매핑된다.

<br>

- 커널 수준 스레드

  커널에서 지원하고 사용자 영역 스레드별로 커널 영역 스레드가 일대일로 매핑된다.

<br>

- 혼합형 스레드

  사용자 수준 스레드와 커널 수준 스레드를 혼합한 형태로 사용자 영역에서 스레드를 생성하고 다수의 사용자 수준 스레드에 다수의 커널 스레드가 다대다로 매핑된다.

<br>

### # CPU 권한 모드 중 커널모드와 유저모드의 차이는?

<br>

- 커널모드

  모든 자원(드라이버, 메모리, CPU 등)에 접근 및 명령할 수 있는 모드, OS가 CPU를 쓸 때 사용하는 모드

<br>

- 유저모드

  사용자가 접근할 수 있는 영역을 제한적으로 두고 프로그램의 자원에 함부로 접근하지 못하도록 제어하는 모드, 응용 프로그램이 실행되는 모드로 보통 애플리케이션 코드는 유저모드에서 실행

<br>

### # **스레드 세이프가 뭔지 아는지?**

<br>

- 멀티 스레드 프로그래밍에서 하나의 함수가 한 스레드로부터 호출되어 실행 중일 때, 다른 스레드가 그 함수를 호출하여 동시에 함께 실행되더라도 각 스레드에서의 함수의 수행 결과가 올바르게 나오는 것을 말한다.

<br>

### # **문맥 전환(Context Switching)이 무엇인가요?**

<br>

- CPU가 한 개의 Task(프로세스/스레드)를 실행하고 있는 상태에서 다른 Task(프로세스/스레드)로 실행이 전환되는 과정에서 기존의 Task(프로세스/스레드) 상태 및 Register 값들에 대한 정보(문맥, Context)를 저장하고 새로운 Task의 정보(문맥, Context)으로 교체하는 작업을 말한다. 이때 Task(프로세스/스레드)의 정보는 레지스터에 저장되며 PCB로 관리된다.

<br>

### # **교착상태(데드락)가 무엇이고 발생하는 조건을 설명해 주세요.**

<br>

- 교착 상태는 프로세스가 자원을 얻지 못해 다음 처리를 하지 못하는 상태로, 시스템적으로 한정된 자원을 여러 곳에서 사용하려고 할 때 발생한다. 상호 배제, 점유 대기, 비선점, 순환 대기 네 가지 조건을 모두 만족해야 교착 상태가 발생한다. 순환 대기의 경우 점유 대기와 비선점 조건을 만족해야 성립하므로 4가지 조건은 완전히 서로 독립적이지 않다.

<br>

### # **가상 메모리(Virtual Memory)에 대해 설명해 주세요.**

<br>

- 가상 메모리는 멀티 프로세스 환경에서 프로세스마다 충분한 메모리를 할당하기에 물리 메모리의 한계가 있어서 나타난 개념이다. 가상 메모리에서 프로세스는 가상 주소를 사용하고, 실제 해당 주소에서 데이터를 읽고 쓸 때 물리 주소로 바꿔주게 된다.

<br>

### # **페이지 폴트가 무엇인가요?**

<br>

- 가상 메모리의 페이지 테이블에는 페이지가 물리 메모리에 있는지, 스왑 영역에 있는지 표시하는 유효 비트를 사용한다. 프로세스가 페이지를 요청했을 때 그 페이지가 메모리에 없는 경우를 페이지 폴트라고 한다. 페이지 폴트가 발생하면 프레임을 새로 할당 받아야 하며, 프로세스가 해당 페이지를 사용할 수 있도록 스왑 영역에서 물리 메모리로 옮겨야 한다. 그리고 페이지 테이블을 재구성 하고, 프로세스의 작업을 재시작한다.

<br>

### # **DTO(Data Transfer Object)가 무엇이죠?**

<br>

- DTO는 프로세스 간에 데이터를 전달하는 객체로 로직을 가지지 않는 순수한 데이터 객체이다. 어떠한 값이 어떤 타입을 가지고 이 값이 필수인지 옵션인지 정의하기 위한 파일이라고 알고 있다. 데이터를 검증할 때 데이터를 정의하는 용도로 사용한다.

<br>

### # **PCB(Process Control Block)에 저장되는 정보는 어떤 것들이 있나요?**

<br>

(1) 프로세스의 고유 번호

(2) 프로세스 상태 (준비, 대기, 실행 등)

(3) 프로세스를 위해 실행 될 다음 명령어 주소를 포함하는 카운터

(4) 레지스터 관련 정보

(5) CPU 스케줄링 및 프로세스 우선순위

(6) 메모리 관리 시스템 정보

(7) 프로세스의 현재 위치를 나타내는 포인터

(8) 열린 파일 목록

<br>

### # **CQRS, 이벤트 소싱에 대해 아는지?**

<br>

- 이벤트 소싱은 도메인 모델에서 발생하는 모든 이벤트를 기록하는 데이터 저장 기법이다. 또한 CQRS는 시스템의 상태를 변경하는 작업과 시스템의 상태를 반환하는 작업의 책임을 분리하는 것이다. 이벤트 소싱과 CQRS와 함께 사용되면 도메인 모델은 비즈니스 요구에 적합한 다양한 비정규 형상을 가질 수 있다고 알고 있다.

<br><br><br>

## # Data Base

<br>

### # **데이터베이스**

- 데이터베이스(Database)

  컴퓨터 시스템에 저장된 정보나 데이터를 모두 모아 놓은 집합이다. 데이터베이스를 사용하는 이유는 메모리에 존재하는 데이터는 오래 보존이 되지 않기 때문에 데이터를 체계적으로 보존하고 관리하기 위해 사용한다.

<br>

### # DBMS(Database Management System, 데이터베이스 관리 시스템)

- DBMS란?

  데이터베이스를 ‘데이터의 집합’이라고 정의한다면, 이런 데이터베이스를 관리하고 운영하는 소프트웨어를 DBMS(Database Management System)라고 힌디. 데이터베이스를 운영하고 관리하는 소프트웨어로 계층형, 망형, 관계형 DBMS 중 대부분의 DBMS가 테이블로 구성된 관계형 DBMS(RDMBS)형태로 사용된다.

<br>

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

  데이터 사이의 관계에 기초를 둔 데이터베이스 시스템을 말하고 2차원 테이블로 표현한다. 원투원(두 테이블이 서로가 서로의 오로지 한 로우에만 연결), 원투매니(한 테이블의 로우 하나에 다른 테이블의 로우 여러개가 연결), 매니투매니(중간테이블로 연결, 하나에 다른 테이블의 로우 여러개가 연결)의 관계로 테이블을 연결하며 식별 정보를 나타내는 프라이머리 키와 테이블 관계를 나타내는 폴인 키를 활용하여 각 테이블의 값을 참조한다.

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

    - 외래 키(FK, Foreign Key)

  - 관계 차수 종류

    - 일대일 1:1(one to one)

    - 일대다 1:N(one to many)

    - 다대다 N:M(many to maty)

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

### # 정규화

테이블 간에 중복된 데이터를 허용하지 않는 프로세스이다. 중복된 데이터를 허용하지 않음으로써 무결성를 유지할 수 있으며, DB의 저장 용량 역시 줄일 수 있다.

<br>

### # 인덱스

추가적인 쓰기 작업과 저장 공간을 활용하여 데이터베이스 테이블의 검색 속도를 향상시키기 위한 자료구조이다.

<br>

### # SQL

구조화된 질의 언어라는 뜻으로 관계형 데이터베이스에서 사용되는 언어. 표준 SQL을 배우면 대부분의 DBMS를 사용할 수 있다. 즉 DBMS에서 사용하는 언어이다. SQL이 데이터베이스를 조작하는 ‘언어’이긴 하지만 일반적인 프로그래밍 언어(C, 자바, 파이썬 등)와는 조금 다른 특성을 갖는다. SQL은 특정 회사에서 만드는 것이 아니라 국제표준화기구에서 SQL에 대한 표준을 정해서 발표하고 있다. 이를 표준 SQL이라고 한다. 그런데 문제는 SQL을 사용하는 DBMS를 만드는 회사가 여러 곳이기 때문에 표준 SQL이 각 회사 제품의 특성을 모두 포용하지 못한다는 점이다. 그래서 DBMS를 만드는 회사에서는 되도록 표준 SQL을 준수하되, 각 제품의 특성을 반영한 SQL을 사용한다. 3가지 DBMS 제품(오라클, SQL 서버, MySQL)이 모두 표준 SQL을 포함하고 있다. 그래서 표준 SQL을 익히면 대부분의 DBMS에 공통적으로 적용할 수 있다. 각 DBMS는 추가로 자신만의 기능도 가지고 있어서 이렇게 변경된 SQL을 오라클은 PL/SQL, SQL서버는 T-SQL, MySQL은 SQL로 부른다.

<br><br><br>

## # Architecture

<br>

### # 모노레포(Monorepo) 구성을 위한 터보레포(Turborepo)

- 프로젝트 구성 방식

  - 모놀리식(Monolithic)

    최초의 `모놀리식` 방식은 소스 코드를 모듈화하지 않고 하나의 리포지터리에 모두 넣었다고 생각하면 된다. 모든 코드가 `단일 버전`으로 서로 직접 의존하기 때문에 코드 재사용이 용이하고 빌드 및 배포 과정도 단순하여 소수의 개발자가 빠르게 개발할 수 있다는 장점이 있다.

    하지만 관심사 분리가 어렵고 기능 추가나 삭제가 레파지토리 전체에 영향을 줄 수 있으며 매번 거대한 프로젝트를 배포해야한다는 단점이 있다.

    이러한 단점을 해결하고자 멀티 레포가 등장하게 된다.

  - 멀티레포(Multi-Repo)

    `멀티레포` 방식에서는 소스 코드를 모듈화한 뒤 각 모듈에 `독자적인 영역을 부여(별도의 저장소)하고 버전 관리를 통해` 관심을 분리해서 기능 변경이 다른 레파지토리에 직접 영향을 미치지 않도록 개선했다. 다른 프로젝트와 의존성을 가지고 있지 않아 독립적으로 개발이 가능하고 관심사 분리가 쉬우며 개발, 테스트, 빌드 배포가 각각 존재한다.

    하지만 각 모듈이 서로 독립된 영역에 존재하기 때문에 코드 코드 컨벤션 통일 및 코드 재사용이 어려워지고 관리 포인트가 증가하며 빌드와 배포 과정이 복잡해진다는 단점이 있다.

  - 모노레포(Mono-Repo)

    `모노레포`는 이와 같은 모놀리식 레파지토리와 멀티레포의 장점을 모두 취하고자 등장했다. 단일 레파지토리에 여러 개의 서브 프로젝트가 존재하는 방식이다. 모노레포의 장점은 아래와 같다.

    (1) 프로젝트 파악 수월 : 모든 커밋 히스토리가 한 레파지토리에 남기 때문에 히스토리를 추적하거나 전체 레파지토리의 개발 방향을 이해하는 게 쉬워지며 모든 프로젝트의 코드와 자원(assets) 간의 관계와 의존성을 한눈에 확인할 수 있다.

    (2) 코드 재사용성 증가 : 여러 곳에서 중복으로 사용하는 자산들(테스트 코드 등)을 공유하고 재사용할 수 있다.

    (3) 배포, 빌드, 테스트 속도 향상 : 배포와 빌드, 테스트와 같은 작업을 병렬로 한 번에 처리할 수 있으므로 한 번의 명령으로 여러 개의 레파지토리에서 작업을 진행할 수 있다.

    모노레포 구성을 도와주는 프레임워크는 Lerna, yarn workspace, Nx, Turborepo 등이 있다.

- 터포레포(Turborepo)

  - 터포레포(Turborepo)란?

    Vercel이 인수한 Turborepo는 JavaScript와 TypeScript 코드 베이스의 모노레포를 위한 고성능 빌드 시스템이다. Vercel과 AWS, Miro, PayPal, Discord, LINE+의 Universal Video Player 등 여러 프로젝트에서 프로덕션 단계로 사용하고 있으며 지금도 활발하게 개발이 진행되고 있다.

    Turborepo의 주요 미션은 모노레포 환경에서 개발자가 조금 더 쉽고 빠르게 개발할 수 있도록 빌드 도구를 제공하는 것이다. 고급 빌드 시스템을 구축하는 복잡한 과정을 Turborepo가 대신해 주기 때문에 개발자는 복잡한 설정과 스크립트에 신경 쓰는 대신 개발에 더 집중할 수 있다. Turborepo의 기본 원칙은 한 번 작업을 수행하며 수행한 계산은 이후 다시 수행하지 않는 것이다. 따라서 두 번째 실행할 때는 이전에 계산한 작업은 건너뛰고 이전에 캐싱해 놓은 로그를 다시 보여준다.

  - 터보레포 특징

    1. Incremental builds : 작업 진행을 캐싱해 이미 계산된 내용은 건너 뛰는 것을 의미한다. 빌드는 딱 한 번만 하는 것을 목표로 한다.
    2. Content-aware hasing : 타임스탬프가 아닌 콘텐츠를 인식하는 방식으로 해싱을 지원한다. 이를 통해 모든 파일을 다시 빌드하는 것이 아니라 변경된 파일만 빌드한다.
    3. Cloud caching : 클라우드 빌드 캐시를 팀원 및 CI/CD와 공유한다. 이를 통해 로컬 환경을 넘어 클라우드 환경에서도 빠른 빌드를 제공한다.
    4. Parallel execution : 모든 코어를 사용하는 병렬 실행을 목표로 한다. 지정된 태스크 단위로 의존성을 판단해 최대한 병렬적으로 작업을 진행한다. (멀티태스킹 능력 극대화)
    5. Task Pipelines : 태스크 간의 연결을 정의해서 빌드를 언제 어떻게 실행할지 판단해 최적화한다.
    6. Zero Runtime Overhead : 런타임 코드와 소스 맵을 다루지 않기 때문에 런타임 단계에서 파악하지 못한 리스크가 불거질 위험이 없다.
    7. Pruned subsets : 빌드에 필요한 요소만으로 모노 레포의 하위 집합을 생성해 PaaS(Platform as a Service) 배포 속도를 높인다.
    8. JSON configuration : 별도의 코드 작업 없이 JSON 설정으로 터보를 사용할 수 있다.
    9. Profile in browser : 빌드 프로필로 빌드 과정을 시각화하면 병목 지점을 쉽게 찾을 수 있다.

<br>

### # Micro Frontends Architecture

- Micro Frontends Architecture

  마이크로 프론트엔드 아키텍처란 마이크로 서비스 아키텍처(MSA)의 개념을 프론트엔드 세계로 확장한 개념이다. 마이크로 서비스는 아키텍처는 하나의 서비스가 여러 개의 작은 서비스로 구성되어 독립적으로 개발되고 배포되는 구조를 말한다. 마이크로 서비스처럼 전체 화면을 작동할 수 있는 단위로 나누어 개발한 후 서로 조립하는 방식이다. 여기서 단위는 페이지나 UI 등이 될 수 있다.

- Micro Frontends의 적용 시점, 장단점

  - 적용 시점

    페이지마다 복잡한 공통 UI가 반복되어 포함되고 그런 와중에도 각 페이지들의 UI 유사성이 높고 크게 연관되어 있으며 여기에 더불어 분절된 각 앱의 크기가 이미 충분히 크고, 복잡도와 도메인 난이도가 높아 배포 단위를 더 잘게 쪼개고 싶은 요구사항이 있는 웹 애플리케이션

  - 메인 컨셉

    - 컨텍스트 독립성

      - 각 작동 단위들이 같은 프레임워크를 사용하더라도 컨텍스트를 공유해서는 안된다.

      - 독립적인 애플리케이션을 자체적으로 구축해야하고 상태 공유나 전역 변수에 의존해서는 안된다.

    - 네임스페이스를 활용한 분리

      - 각 작동 단위의 격리가 불가능한 경우 네이밍 컨벤션에 따라 prefix 등으로 네임스페이스를 활용한다.

      - CSS, 로컬 스토리지, 이벤트, 쿠키에 네임스페이스를 부여하여 충돌을 방지하고 명확히 분리한다.

    - 통신 시스템에 기본 브라우저 기능 활용

      - 작동 단위 간의 통신을 위한 시스템을 자체 구축하는 것보다 브라우저 이벤트를 사용한다.

      - 만약 정말로 작동 단위 간 커스텀 API가 필요한 경우 가능한 간단하게 유지한다.

    - 탄력적인 웹 디자인 구축

      - 자바스크립트에서 에러가 나거나 실행할 수 없더라도 기능은 사용 가능해야 한다.

      - 범용 렌더링(Universal Rendering)과 점진적 향상(Progressive Enhancement)을 통해 성능을 향상시킬 수 있다.

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

    마이크로 앱들을 개발 후, 어떻게 통합할지 고려해야 한다. 여러 방식이 있는데, 공통적으로 존재하는 아키텍처가 있다. 일반적으로 마이크로 애플리케이션들이 있고(작동 단위), 그것들을 구성하는 단일 컨테이너 애플리케이션이 있다. 단일 컨테이너 애플리케이션은 다음과 같은 것들을 한다.

    - 공통 페이지 요소를 렌더링한다.

    - 인증 및 탐색과 같은 공통적으로 고려되어야 하는 문제들을 해결한다.

    - 다양한 마이크로 앱들을 페이지에 모으고, 각 앱들에게 언제 어디서 렌더링할지 알려준다.

  - 서버 사이드 템플릿 통합

    각 서버로 html 템플릿을 요청하고, 최종 응답 서버에서 각 템플릿을 조합해서 응답을 보낸다. 서버 측에서 최종 화면을 조합한다. 웹앱 단위 이상으로 배포단위를 쪼개는 것과 같다.

  - 빌드타임 통합

    분리된 UI(마이크로 프론트엔드)를 패키징해 패키지로 배포하고 빌드타임에 통합시키는 방법이다. 특정 UI의 한 부분을 NPM 패키지로 만들어 애플리케이션의 package.json에 의존성과 버전을 표기한 후 빌드해 배포하는 방법이다. 컨테이너 앱이 그것들을 라이브러리 종속성으로 포함하도록 한다. 특정 패키지를 번들링해서 미리 트랜스파일하고 빌드해놓는 데서 발생하는 이점으로 어느정도 빌드 및 배포 사이클을 빠르게 할 수 있는 장점도 있기는 하지만 각각의 마이크로 앱에 변경사항이 있을 때마다, 그 변경사항을 반영한 단일 번들을 만들기 위해 다시 컴파일하고 릴리즈해야 한다는 문제가 있다.

  - iframe을 통한 런타임 통합

    여기서부터는 확실히 페이지 단위 이하로 배포 단위를 분리할 수 있는 방법들이며 분절된 UI 컴포넌트를 런타임에 통합하는 방식이다. 이 방식은 전통적인 방식이면서 가장 쉬운 방식이다. iframe을 사용하면 각 마이크로 페이지들을 독립적인 하위 페이지로 쉽게 만들 수 있다. 특정 외부 URL로 배포해놓은 UI의 일부를 HTML째로 넣어 기존 앱에 쉽게 통합하여 배포 단위를 UI 단위로 분리할 수 있다. 하지만 어플리케이션의 서로 다른 부분들을 통합 구축하는 것이 어렵다. 따라서 라우팅, 히스토리, 컴포넌트간 상태값 공유 등이 더욱 복잡해지고, 반응형 페이지 개발에도 추가적인 어려움들이 따르며 UX가 iframe안에 갇히기 때문에 어색한 UI 표현을 가질 수 있다.

  - Web Components를 통한 런타임 통합

    비교적 최신 web 스펙인 web-components를 이용한 런타임 통합 방식으로 컨테이너 앱에서 인스턴스화 할 HTML Custom Element를 정의하는 방식이다. iframe과 웹 컴포넌트를 통한 런타임 통합 방식의 경우, 이미 그것으로 완결되어 런타임에서 다른 컴포넌트와 상호작용할 필요가 없는 소수의 UI 컴포넌트들을 런타임에 통합하는데 사용하기 좋은 방식이다. 하지만 다수의 분리된 다른 UI 컴포넌트가 iframe이나 web-components로 런타임에 통합되는 경우 기존의 UI 컴포넌트와 약간 거리가 있는 곳에서 상태값들을 저장하고, 이를 기존 UI 컴포넌트들의 라이프사이클에 연동시켜야하기 때문에 복잡해질수록 관리가 어려워질 가능성이 높다.

  - Javascript를 통한 런타임 통합

    UI 컴포넌트를 자바스크립트 번들 단위로 배포 단위를 나누고, 필요할 때 번들을 로딩하여 런타임에 통합시키는 방식이다. React를 사용한다고 가정한다면 이 방법에서는 “정의한 컴포넌트들을 그냥 툭 떼서 별도의 배포단위로 만들고 런타임에서 합치는 것” 이 가능하다. 해당 컴포넌트부터 런타임에 만들 수 있는 독립된 번들로 만드는 것이다. 이 방법이 주는 가장 큰 장점은 배포 단위를 유연하게 가져갈 수 있게 한다는 것이다. 배포 단위간 상태 공유를 위한 작업이 앞선 두 런타임 통합 방법보다 많거나 이질적이지 않고, 모두 웹 앱 내부에서 가능하니 기존 배포 단위를 합치거나 나누는 것이 비교적 간편하다.

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

### # **git flow(process)**

<br>

- git으로 어떻게 일했는지 프로세스 설명

  (0) 기본적으로 커맨드(CLI, Command-Line Interface)를 사용하여 git을 사용하였다.

  (1) 기능 개발을 위한 feature 브랜치 생성하였다.

  (2) 기능 단위로 작업 완료 후 add -> commit -> PR을 날렸다.

  (3) 팀원들에게 리뷰받은 뒤 수정 후 직접 스쿼시 머지 (커밋을 하나로 합쳐 머지)

<br>

- git branch 종류

  (1) Master Branch : 제품으로 출시될 수 있는 브랜치

  (2) Develop Branch : 다음 출시 버전을 개발하는 브랜치

  (3) Feature branch : 기능을 개발하는 브랜치

  (4) Release Branch : 이번 출시 버전을 준비하는 브랜치

  (5) Hotfix Branch : 출시 버전에서 발생한 버그를 수정 하는 브랜치

<br>

- git merge, git rebase, git squash 차이

  (1) git merge : merge는 일반적인 병합 방법이다. 모든 커밋이 시간 순서대로 병합된다. 충돌이 일어났을 경우 맨 마지막 커밋에 머지 커밋을 추가하여 해결한다.

  (2) git squash : squash 병합은 여러 개의 커밋을 하나의 커밋으로 합친 후 merge하는 방식이다. 충돌이 일어났을 경우 충돌 해결 후 squash 병합을 진행하므로 마지막에 머지 커밋이 추가되지 않는다. 이러한 방식은 feature branch에서 develop branch로 머지할 때 적합하다. 기능 단위로 개발된 feature의 commit을 하나로 모아줌으로써 기능 단위의 commit을 만들어 develop branch에 머지하는 것이다. 이러한 방식을 통해 이슈를 추적하기가 용이해진다.

  (3) git rebase : rebase는 커밋의 시간에 관계없이 마지막에 merge 되는 branch의 commit을 가장 뒤로 병합된다. 충돌이 연쇄적으로 발생할 수 있기 때문에 주의해서 병합해야한다. 또한 브랜치 병합 시 머지 커밋 기록이 남지 않는다. 따라서 마치 하나의 브랜치에서 작업한 것처럼 보여진다. 쉽게 말해서 rebase는 이름과 같이 base commit을 재정의하고 재정의한 base commit 뒤에 해당 commit들을 이어붙힌다. 이어붙히기 때문에 연쇄적 충돌이 발생할 수 있는 것이다. 이러한 방식은 develop branch에서 main branch로 머지할 때 적합하다. main branch의 마지막 commit에 develop의 commit을 이어붙히는 것이다. 만약 이런 경우 squash를 해버리면 develop의 commit이 하나로 합쳐지기 때문에 이슈를 추적하기가 어려워질 수 있다.

<br>

- 커밋 메시지 종류

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

- 디자인 시스템이란 디자인 원칙, 규격, 재사용 가능한 UI 패턴과 컴포넌트 코드를 포괄하는 시스템이라고 정의할 수 있다. 단순한 스타일 가이드, 패턴 라이브러리 역할을 하는 디자인 시스템이 있는가 하면, 브랜드 원칙과 UX 원칙에 이르는 하나의 철학을 구성하는 시스템도 있다고 한다. 정리하자면, 디자인 시스템은 정해진 디자인 패턴과 컴포넌트를 재사용하여 제품을 구축과 개선 시간을 단축시켜주는 시스템이다. 프론트 단에서 디자인 시스템을 사용하면 반복되는 요소들을 재사용함으로써 생산성이 증가하고 일관성 있는 UI를 제공함으로써 사용자 경험을 향상시킬 수 있다. 또한 디자이너와 개발자 사이의 공통 원칙을 지정하여 협업 시 원활한 소통도 가능해진다.

<br>

### # CDD, 컴포넌트 주도 개발

- 말 그대로 재사용이 가능한 컴포넌트를 우선적으로 개발하여 이 컴포넌트의 조합으로 페이지를 구성하는 개발 방식이다.

<br>

### # 스토리북(Storybook)

- react에서 컴포넌트 주도 개발을 하기 위해 사용하는 툴이다. 스토리북이 제공하는 독립적인 환경에서 컴포넌트를 만들고 컴포넌트의 스토리를 생성하여 다양한 케이스를 테스트해볼 수 있다. 또한 Docs로 문서화를 지원하여 컴포넌트에 대한 설명을 문서화할 수 있다. 쉽게 말해 스토리북은 디자인 시스템 구축을 위해서 사용할 수 있다. 사용 방법은 스토리북 디렉토리에서 전역적으로 사용될 포멧을 세팅해주고 스토리즈 디렉토리에서 컴포넌트 스토리를 생성한다. 작업 순서는 테스트할 컴포넌트를 우선적으로 만들고 컴포넌트 스토리즈 파일 내부에서 템플릿 생성 후 bind 메소드로 컴포넌트 스토리를 생성한다. 그리고 args 프로퍼티를 통해 스토리에 필요한 인자를 전달하는 방식으로 작업한다.

- 참고 URL

1. https://velog.io/@zer0jun/%EC%8A%A4%ED%86%A0%EB%A6%AC%EB%B6%81-%EC%82%AC%EC%9A%A9%EB%B2%95

2. https://iyu88.github.io//storybook/2023/04/07/storybook-docs.html

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

### # **최근에 관심있게 읽거나 참고하는 기술서적이 있나요?**

<br>

(1) 자바스크립트 : 모던 자바스크립트 Deep Dive

(2) 리액트 : 리액트를 다루는 기술

(3) 노드 js : Node.js 교과서

(4) 깃/깃허브 : 팀 개발을 위한 깃/깃허브 시작하기

(5) 기본 용어 : 비전공자를 위한 이해할 수 있는 IT지식

<br>

### # **정기적으로 참석하는 밋업이나 컨퍼런스, 세미나가 있는지?**

<br>

- 아직 정기적으로 참석하는 밋업이나 컨퍼런스는 없다. 하지만 최근 삼성동 코엑스에서 진행되었던 넥스트라이즈 컨퍼런스에 참여하게 되면서 다양한 기업들의 개발 문화나 기업이 추구하고자 하는 방향성 등에 대해 알 수 있었다. 특히 직방같은 경우에는 게더타운과 비슷한 메타폴리스라는 서비스를 개발하여 메타폴리스를 이용한 회의,근무 등을 진행하고 있었다. 코로나 이후 근무 환경이 참 많이 달라졌다는 것을 느낄 수 있었다. 넥스트라이즈에 다녀오면서 밋업이나 컨퍼런스 참여에 대한 필요성을 느껴 앞으로 적극적으로 참여하려고 한다.

<br>

### # **백앤드쪽은 어느정도 알고있니?**

<br>

- 아직 서버와 데이터베이스 쪽은 잘 모르고 있습니다. 그래서 최근에 서버와 데이터베이스 공부하는 차원에서 웹소캣, 노드익스프레스 서버, MySQL DB를 이용하여 실시간 채팅 프로젝트를 만들어보려고 시도해본 적이 있었는데 익스프레스 서버와는 연동이 됬었는데 DB와 연동이 안되서 실패한 경험이 있다. 그래서 추후에 다시 시도해 볼 생각이다. 그리고 아직 프론트엔드 분야에 대해 공부할 것이 더 많이 남아있다고 생각이 되서 프론트엔드 위주로 공부하면서 어느 정도 수준까지 공부를 했거나 당장 서버와 데이터베이스 쪽에 대한 지식이 필요한 경우가 생긴다면 공부해볼 계획이다.

<br>

### # **애자일 방법론과 워터폴 방법론의 차이**

<br>

- 애자일

  스프린트라는 짧고 점진적인 개발 주기로 구성된 프로젝트 관리 방법론이다. 개발과정이 빠르고 유연하며 이슈를 빠르게 발견하고 수정할 수 있고 짧은 스프린트로 움직이기 때문에 프로젝트 변경에 자유롭다. 하지만 반복적이고 빠른 작업에 능숙한 인원이 필요하며 많은 변경사항이 발생할 수 있다.

<br>

- 워터폴

  프로젝트 시작부터 최종 결과물 전달까지 특정 순서에 따라 이루어지는 프로젝트 관리 방법론이다. 팀 규모에 상관없이 따르고 쉽고, 요구사항이 정의되어 있기 때문에 목표가 변경되지 않으며 개발 주기가 정해져있어 안정적인 스케줄 관리가 가능하다. 하지만 개발 속도가 느리고 유연성이 떨어지고 테스팅 단계에서 이슈를 발견하는 일이 생길 수 있으며 요구사항이 정해져 있어 프로젝트 변경을 자유롭게 할 수 없다.

<br>

### # 가독성 확보 방법

<br>

(1) 일관성 있는 코드 작성

(2) 코드의 중복 제거

(3) 렌더단과 로직단의 분리

(4) 기능을 유추할 수 있는 식별자 이름 및 네이밍 컨벤션

<br>

### # **잘 만든 사이트란? 혹은 좋은 개발자란?**

<br>

(1) 가독성이 높고 유지보수가 용이한 클린 코드가 짜여진 사이트

(2) 퍼포먼스, 웹표준, 웹접근성, SEO 고려한 사이트

(3) 깔끔한 UI(유저인터페이스)/UX(유저익스피리언스) 디자인 적용 된 사이트

<br>

### # **몽고DB, mysql같은 데이타베이스에 관심이 있는지? 배울 생각이 있는지?**

<br>

- 현재 서버나 데이터베이스는 잘 모르고 있지만 배울 생각이 있다. 프론트엔드 개발자지만 서버나 데이터베이스도 알고 있어야 백엔드 개발자와 협업할 때 더욱 원활한 소통을 할 수 있다고 생각한다. 하지만 프론트엔드 개발자에 맞게 프론트엔드 쪽에 대한 지식을 더욱 쌓은 뒤 배우는게 맞다고 생각한다.

<br>

### # **개발자로서 새로운 기술, 트렌드가 있다는 걸 어떻게 알 수 있을까?**

<br>

- 기존에는 개발자 커뮤니티나 카카오톡 오픈채팅방 혹은 유명 개발자들의 블로그 혹은 유튜브 채널을 통해서 확인했었다. 하지만 얼마 전 개발 관련 밋업과 컨퍼런스 등이 있는 것을 알게 되었고 삼성동 코엑스에 넥스트 라이즈 컨퍼런스에 참여했었다. 이런 밋업이나 컨퍼런스 등에 참여를 통해서도 다양한 정보를 얻을 수 있다고 생각한다. 개발자 커뮤니티 혹은 밋업이나 컨퍼런스 등을 적극적으로 활용하면 새로운 기술이나 트렌드 파악에 큰 도움이 된다고 생각한다.

<br>

### # **이미지 포맷의 차이는?**

<br>

- 비트맵 이미지

  픽셀로 표현한 이미지

<br>

- 벡터 이미지

  점과 선의 연결로 표현한 이미지

<br>

- JPG

  비트맵 이미지, 손실 압축, 24비트 컬러 지원

<br>

- PNG

  비트맵 이미지, 비손실 압축, 투명도 지원, 8비트/24비트 컬러 지원

<br>

- WebP

  비트맵 이미지, 구글에서 개발한 이미지 포맷, 손실/비손실 동시 지원, 투명도 지원, 익스플로러에서는 지원하지 않음

<br>

- SVG

  마크업 기반의 벡터 이미지, 해상도로부터 자유롭고 코드 혹은 파일로 사용 가능

<br>

- 동일 화질 파일 크기 비교

  WebP > PNG > JPG

<br>

### # **최근 했던 프로젝트의 패키지 구조에 대해 설명해주세요.**

<br>

- src 디렉토리의 구조는 assets, components, hooks, models, routes, services, states, styles, types 디렉토리로 나누어 사용한다.

  (1) assets : 이미지 혹은 svg를 관리하는 디렉토리이다.

  (2) components : 공통으로 사용되는 컴포넌트를 관리하는 디렉토리이다. routes 내부에 `_shared` 디렉토리와의 차이는 전체적으로 반복해서 재사용하는 컴포넌트들을 관리하는 디렉토리이다.

  (3) hooks : 커스텀 훅을 관리하는 디렉토리이다.

  (4) models : 상수 데이터를 관리하는 디렉토리이다.

  (5) routes : 실제 렌더링되는 컴포넌트들을 관리하는 디렉토리이다. 라우팅 경로를 설정하기도 하고 각 컴포넌트들의 디렉토리를 생성하여 관리한다. 또한 `_shared` 디렉토리를 생성하여 전체 페이지에 렌더링되는 헤더, 푸터, 네비게이션과 같은 컴포넌트들을 관리한다.

  (6) services : api 호출 함수를 관리하는 디렉토리이다.

  (7) states : 전역으로 관리하는 state를 관리하는 디렉토리이다.

  (8) styles : 공통으로 사용되는 스타일을 관리하는 디렉토리이다.

  (9) types : 공통으로 사용되는 타입을 관리하는 디렉토리이다.

<br>

### # **구글 어낼리틱스(GA)**

<br>

- 구글 어낼리틱스는 방문자의 데이터를 수집하여 온라인 비지니스의 성과를 측정하고 개선하기 위해 사용하는 것으로 알고 있다. 직접 사용해본 적은 없지만 구글 어낼리틱스를 적용하는 동영상을 본 경험은 있다.

<br>

### # **회사를 선택하는 기준은?**

<br>

- 사용하는 기술 스택

  첫번째로 회사에서 사용하는 기술 스택이 내가 사용하는 기술스택과 일치하는지를 확인한다. 내가 당장 소화할 수 있는 기술 스택이어야 그 회사에 필요한 구성원이 될 수 있다고 생각하기 때문이다.

<br>

- 서비스 운영 여부

  두번째로 회사에서 직접 운영하는 서비스가 있는지 확인한다. 개인적으로 클린 코드를 지양하고 웹 사이트의 퍼포먼스, 웹표준, 웹접근성, SEO 등을 모두 고려하여 개발자가 좋은 개발자라고 생각하기 때문에 외주 프로젝트를 받아 프로젝트의 완성만을 목표로 업무를 진행하는 회사보다는 직접 서비스를 운영하며 서비스의 퍼포먼스 최적화를 목표로 업무를 진행하는 회사가 향후에 내가 목표로 하는 개발자의 모습과 훨씬 더 부합하다고 생각해서 실제 서비스를 운영하고 있는지 확인한다.

<br>

- 제공하는 서비스

  세번째로 회사에서 제공하는 서비스가 무엇인지 확인한다. 회사가 운영하는 서비스가 나의 관심사와 어느 정도 일치할 때 개발할 때도 사용자 입장을 더 고려할 수 있고 효율적으로 개발할 수 있다고 생각하기 때문에 제공하는 서비스가 무엇인지도 고려한다.

<br>

### # **어려운 일을 마주했을 때 어떻게 해결하는지?**

<br>

- 상황에 따라 다르게 해결할 것 같다. 우선 프로젝트 일정에 차질이 생기지 않는 선에서 최대한 혼자서 해결하고 만약 사수분이 계시고 혼자 해결하는 시간이 길어질 것 같다고 판단되는 경우 질문할 것 같다. 여기서 질문은 구체적으로 한번에 답변을 받을 수 있도록 좋은 질문을 하는 것이 중요한 포인트라고 생각한다. 만약 사수분이 계시지 않고 혼자 해결하는 시간이 길어질 것 같다고 판단되는 경우 미리 팀장님께 보고를 드려 해결책을 강구할 것 같다.

<br>

### # **백엔드 개발자와 작업을 하는 데 서로 생각이 다를 때 어떻게 할거냐? 수긍? 설득?**

<br>

- 서로에 의견을 다를 경우 그만한 이유가 있을 것이라고 생각하기 때문에 무조건 적으로 수긍하거나 설득하지는 않을 것 같다. 만약 시간이 가능하다면 두 가지의 방법 모두 적용시켜보고 퍼포먼스 최적화에 더욱 도움이 되는 쪽으로 선택할 것 같다. 시간이 가능하지 않다면 백엔드 개발자분과 둘이서 결정하는 것이 아닌 팀원들과 협의해서 결정하거나 서칭을 통해 해당 이슈에 대해 더 알아보고 결정할 것 같다.

<br>

### # **백엔드와 협업하면서 어려웠던 점**

<br>

- 카카오 로그인 api를 활용하여 소셜 로그인 기능을 구현했었던 적이 있었는데 당시 백엔드 개발자분의 재택 작업으로 인해 소통의 부재가 생겼었다. 그래서 소통의 오류로 이어지게 되었는데 프론트엔드 단과 백엔드 단 모두에서 소셜 로그인 기능을 구현하는 중복 작업의 문제가 발생하게 되었다. 그 때 프론트엔드 개발자와 백엔드 개발자 간에 소통의 중요성을 느끼게 되었고 개발 과정 중에 백엔드 개발자분과의 적극적인 소통은 정말 필수적으로 해야한다고 느꼈다.

<br>

### # **프로젝트 미완성 부분 아쉬움이 있었는지? 있다면 무엇이었는지?**

<br>

- 클래스101을 레퍼런스로 작업했던 낫파운드 404라는 프로젝트가 있는데 이 프로젝트에 크레이터 페이지가 미완성되었다. 크레이터 페이지는 사용자가 직접 클래스를 등록하여 다른 사용자가 해당 클래스에 신청하여 참가할 수 있게 하는 기능을 제공하는 페이지인데 프로젝트 설계 당시 프로젝트 진행 기간을 고려하여 클래스를 만드는 과정까지만 구현하기로 했었다. 하지만 해당 페이지를 담당했던 프론트엔드 개발자분이 진행하는 부분에 대해 착각하여 볼륨을 너무 크게 잡게 되어 결국 미완성하게 되었다. 이 부분은 소통의 오류로 인해 발생한 문제이기 때문에 팀원 모두에 잘못이라고 생각한다. 개발자에게 소통이 왜 중요한 것인지 다시 한번 느낄 수 있었다.

<br>

### # **본인이 작성한 코드 중 자신있는 코드를 보여주세요.**

<br>

- 지금 당장 생각나는 코드는 매드업이라는 프로젝트에 테이블 부분이 생각난다. 개인적으로 렌더단과 로직단을 최대한 구분하는 것이 중요하고 렌더단은 가독성을 최대한으로 끌어올려 페이지 구조를 한 눈에 파악할 수 있어야한다고 생각하는데 이 부분에서 (POB_Madup -> src -> routes -> DashBoard -> MediaStatus -> MediaTable -> MediaTable.tsx) 유즈메모를 사용하여 렌더단에서 페이지 구조를 파악하기 쉽도록 잘 설계한 것 같다고 생각한다.

<br>

### # **구체적인 질문이란?**

<br>

- 주고 받는 질답의 형식보다는 한번에 질문을 통해 답변을 받을 수 있도록 정리되어 있는 질문이 좋은 질문이라고 생각한다.

  (1) 실행 환경 : 어떤 환경, 어떤 언어, 어떤 도구쓰는지를 포함

  (2) 시도 및 실패 결과 : 어떤 시도를 했는지 포함, 시도에는 어떤 과정과 어떤 결과가 발생했는지에 대한 코드를 포함

  (3) 코드 해석 : 코드가 긴 경우 해석이 어려울 수 있으므로 코드 설명도 포함

  (4) 기대 결과 : 기대하는 결과를 포함

<br>

### # **회사에 궁금한 점이 있나요?**

<br>

(1) 개발 팀의 구성 원이 어떻게 이루어졌는지 궁금합니다.

(2) 구체적인 코드를 여쭤보는 것은 아니지만 최근 프로젝트에서 발생한 이슈나 현재 진행중인 이슈가 무엇인지 궁금합니다.

(3) 기획부터 배포까지 진행되는 워크 플로우가 어떻게 되는 지 궁금합니다.

(4) 팀원들간의 소통하는 방식이나 코드 리뷰 문화가 어떻게 이루어져있는지 궁금합니다.

(4) 인재 채용 시에 가장 중요하다고 생각하는 부분이 궁금합니다.

<br>

### # **면접 전 준비 사항**

<br>

(1) 면접 전 프로젝트 코드 파악하고 가기

(2) 지원 동기

(3) 지원한 회사에 대한 정보와 제공하는 서비스

<br>

### # 메인 프로젝트 - 매치아크

- 서비스 소개 : 잉글랜드 9부 리그 이하 아마추어 클럽과 플레이어를 매칭시켜주는 서비스

- 기술스택 : Next.js, Typescript, Apollo Client, GraphQL, BaseUI, Styletron-react, Vercel, next-pwa, react-hook-form, AWS S3, AWS Cloudfront, AWS Lambda, analytics/amplitude

- 프로젝트 아키텍처 : 프론트는 react 기반 프레임워크인 nextjs를 활용했고 서버는 nodejs 기반 프레임워크인 nestjs를 활용했다. db는 mysql을 사용했다. 또한 캐시 서버인 redis를 사용했다. 그리고 파일 서버로 aws s3를 사용했고 cloudfront와 함께 사용했다. 그리고 유저가 이미지 업로드 시 aws lambda를 통해서 이미지를 리사이징하였고 S3 파일 서버에서 이미지 제공 시 리사이징된 이미지를 제공하였다. 또한 프론트 배포 및 ci/cd 구축은 vercel을 사용하였다. 백엔드 배포는 도커를 통해 도커라이징하여 이미지 생성 후 해당 이미지를 ec2를 통해 배포하였다.

- 페이지별 기능 구현 방법

  - 공통

    - 빌드 및 배포 : 프론트 웹은 버셀을 활용하여 적용하였다. 버셀을 활용하는 경우 CI/CD가 자동으로 적용되기 때문에 PR 생성 시 빌드 및 테스트를 자동화할 수 있었고 연결된 레파지토리 메인 브랜치에 머지 시 자동으로 배포할 수 있었다. 또한 앱의 경우 next-pwa와 bubble wrap을 활용한 안드로이드 apk 파일 빌드 후 배포하였다.

    - UI 구현 : UI 프레임워크는 BaseUI를 사용하였고 CSS 라이브러리는 css-in-js인 Styletron-react를 활용하였다. 자주 묶어서 사용되는 flex, font와 같은 스타일의 경우는 스타일 객체를 반환하는 유틸 함수로 생성하여 공통적으로 사용하였다. styletron-react를 사용한 이유 중 가장 큰 이유는 SSR에 최적화되어있다. 서버 사이드 렌더링 시 HTML에 스타일 태그 내부에 각 스타일을 유일한 클래스로 지정하고 각 태그마다 필요한 클래스를 할당하여 클라이언트로 보낸다. 개발자 도구 네트워크 탭에서 페이지 로드 시 전달받은 도큐먼트 프리뷰를 확인해보면 클래스를 할당하여 보내는 것을 볼 수 있다. 또한 아토믹 CSS 방식을 채택하여 사용하기 때문에 각 스타일이 유일한 클래스로 지정되어 중첩된 스타일 시트를 방지하며 스타일 적용 시 자동으로 클래스가 부여된다.

    - Typescript 활용 : Typescript를 활용한 정적 타이핑으로 안정성 향상시켰다.

    - AWS S3와 Cloudfront 활용 : AWS 파일 서버인 S3를 활용하여 유저 업로드 이미지나 비디오를 관리하였고 AWS의 CDN인 Cloudfront를 활용하여 가까운 리전(지리적 분포 서버)의 엣지 서버에서 데이터를 제공해주어 빠르게 데이터가 제공되도록 하였다.

    - GraphQL 활용 : Apollo Client, GraphQL을 활용한 데이터 패칭 및 캐싱을 통해 데이터 오버 패칭이나 언더 패칭을 해결하고 API 호출을 최적화하였다. 또한 로컬 스키마를 생성하고 캐싱하여 전역 상태 관리 라이브러리를 대체하여 사용하였다. (설명 : 쿼리를 생성 후 코드제너레이터를 돌려서 로컬 및 리모트 스키마에 대한 타입을 생성한 뒤 쿼리 도큐먼트를 아폴로 클라이언트에 useQuery 혹은 useMutation의 인자로 활용하여 api를 요청하였다. REST API에 비해 필요한 데이터만 적절히 요청해서 데이터 오버 패칭이나 언더 패칭이 없고 캐싱도 가능해서 편리하게 사용했던 것 같다. 캐싱의 경우 writeQuery, readQuery, modify 메소드를 활용하여 캐싱 데이터를 관리하였다.)

    - SSG를 활용한 조건부 UI 처리 : getStaticProps를 활용한 header, bottom navigation 등 조건부 UI 핸들링 및 페이지 접근 권한 처리, 접근 권한 없는 경우 대체 페이지 노출하였다. 초기 값은 app 디렉토리에 컴포넌트의 props로 내려주고 이 props를 빌드 타임에 업데이트 시키는 방식으로 구현하였다.

    - Skeleton UI 적용 : 사용자 경험 향상 및 layout shift 방지를 위한 Skeleton UI 적용하였다. if문 혹은 삼항 연산자 등을 활용하여 패칭 된 데이터가 유효하지 않은 경우 대체 UI로 제공하였다. 이 부분에서 스켈레톤 UI를 컴포넌트 단위로 적용한 점에서 아쉬운 것 같다. 전체 페이지의 데이터가 로드될 때 까지 스크롤 없는 스켈레톤 UI를 적용한다면 사용자 경험이 더 좋아졌을 것 같다.

    - Code splitting 적용 : 다이나믹 임포트를 활용한 코드 스플리팅 적용, 기본적으로 next js에서는 페이지 디렉토리 내의 페이지들은 자동 코드스플리팅을 적용하기 때문에 그 외에 페이지 디렉토리 외부에 있는 공통 컴포넌트를 사용하는 경우 다이나믹 임포트를 통해 코드 스플리팅을 적용시켰다.

    - REST API 공통 herders 관리 : REST API 사용 시 Interceptor를 활용한 Content-type 및 Authorization 등 공통 headers 메타 데이터 관리하였고 switch 문과 같은 추가적인 내부 로직을 사용하여 토큰이 필요한 요청의 경우 토큰을 심어주고 기타 다른 추가 데이터가 필요한 요청 등을 묶어서 관리하였다. (ex window.fetch = () = { … })

    - Context API과 HOC를 활용한 전역 상태 관리 : Context API 커스텀 훅을 활용한 로그인, 모달, 토스트 관련 전역 상태 관리하였다. 구현 방법은 재사용 가능한 Context API 훅을 만들고 제네릭 타입을 할당한 뒤 Context의 값과 프로바이더를 배열로 반환하도록 하였다. 그 후 app 디렉토리 내부 컴포넌트를 감싸는 전역 상태 관리를 담당하는 고차 컴포넌트 내부에서 해당 Context API 훅을 사용하는데 이 때 제네릭 타입의 인자로 전역 state로 사용할 state들을 interface 타입으로 묶어 전달하여 프로바이더가 관리할 값의 타입을 지정하였다. 그 후 고차 컴포넌트 내부에서 로그인, 로그아웃 등 필요 조건에 따라 전역적으로 사용되는 state를 업데이트하였고 이 state를 Context API 훅이 반환하는 프로바이더의 value로 넘겨주어 프로바이더가 최신 값을 반환할 수 있게 하였다. 여기까지 프로바이더가 반환하는 값의 세팅을 마친 후 고차 컴포넌트 내부에 있는 Context API 훅이 반환하는 Context의 값을 export 하여 모든 컴포넌트에서 import로 해당 state를 참조할 수 있게 하였다.

    - HOC를 활용한 Provider 래핑 : app 디렉토리 내부에 여러 프로바이더 연결 시 props로 인해 가독성이 저하될 수 있는데 각 프로바이더를 HOC 만들고 래핑하여 가독성이 향상되도록 하였다.

    - SVG 컴포넌트 활용 : SVG 재사용성을 증가시키기 위해 @svgr/webpack 패키지를 활용하여 컴포넌트로 사용하였다. svg 파일을 컴포넌트 내부로 import 할 때 컴포넌트 형태로 import 할 수 있다.

    - SEO 향상을 위한 동적 메타 태그 적용 : next-seo를 활용하여 기본 메타 태그 및 페이지 별 동적 메타 태그 적용

    - Next API Routes 활용 : Next API Routes를 활용한 Apply/Offer API, Apply/Offer 시 필요한 JWT 발급 및 검증 API, S3 파일 업로드 API 생성 및 유저 거주 지역의 좌표를 가져오는 외부 API 주소 마스킹 처리 등을 하였다. 페이지 디렉토리 내부 api 디렉토리에 생성하고 해당 파일의 경로를 api url로 사용하여 호출하였다. (ex /api/jwtSign/)

    - Debounce 적용 : 사용자 입력을 통한 API 요청 시 Debounce를 적용하여 API 호출 횟수 최적화하였다. lodash에 debounce를 사용하였다. 사용법은 debounce로 콜백 함수를 인자로 넘겨주기만 하면 된다. (ex debounce(() => {}))

    - useMemo, useCallback 활용 : 연산이 비용이 큰 값 혹은 함수의 경우 useMemo, useCallback을 활용한 메모이징하였다. 예를 들어 검색 페이지에 경우 클라이언트에서 처리 시 연산이 매우 컸는데 이러한 경우 메모이징하여 사용하였다.

    - userAgent를 활용한 조건부 모달 노출 : 지원하지 않는 브라우저의 경우 userAgent를 활용한 경고 모달 노출, 점진적으로 대응하여 제거된 기능이지만 사파리 브라우저를 사용하는 빈도가 적었기 때문에 이러한 방식으로 대응하였었다.

    - Mailchimp API 사용 : Mailchimp API를 활용한 유저 Offer, Apply 시 알림 메일 발송

    - 웹 접근성 향상을 위한 aria 속성 및 alt 속성 활용 : 스크린 리더 사용자들을 위한 aria-label, aria-labelledby, aria-disabled 등의 속성 활용 및 이미지 태그의 alt 속성 활용

    - OG Tag 적용 : 서비스 공유 및 마케팅 효과 향상을 위한 OG tag 적용 (ex `<meta property="og:url" content=https://${NEXT_PUBLIC_DOMAIN}.com>`, `<meta property="og:image" content=https://${NEXT_PUBLIC_DOMAIN}.com/images/>static/og-image.png>`)

    - 사용자 행동 추적 및 분석 : Amplitude의 analytics 활용 및 useAnalytics hook을 활용한 사용자 행동 추적

    - ESLint : ESLint를 활용한 Airbnb 스타일 룰 적용 및 Airbnb javascript 스타일 가이드 참조

  - 메인 페이지

    - ISR을 활용한 정적 페이지 업데이트 : 빌드 타임에 getStaticProps로 패칭한 Apply/Offer 카운트, 방금 가입한 유저 목록 데이터 등을 업데이트 하기 위해 revalidate 속성을 활용한 정적 페이지 재생성하였다. getStaticProps의 revalidate 속성을 활용하였다. 빌드 주기는 60초로 설정했었다.

    - 외부 링크 이동 시 새창 열림 : 외부 링크 이동 시 target 속성의 `_blank`를 활용한 새창 열림으로 사용자 경험 향상시켰다.

  - 검색 페이지

    - Google Map API 활용 : Google Map API를 활용한 좌표 추출 및 좌표를 활용한 마커 및 마커 클러스터 표시, 마커 클릭 시 해당 좌표를 가진 유저 카드 노출

    - Query String을 활용한 필터 처리 : Query String을 활용한 검색 결과 필터 처리 및 사용자들간 URL을 통한 필터 결과 값 공유로 사용자 경험 향상

    - 캐싱을 활용한 세부 옵션 값 유지 : GraphQL 로컬 스키마 생성 및 캐싱을 활용하여 페이지 전환 후 되돌아오는 경우 세부 옵션 사항 유지하였다. 예를 들어 유저 상세 옵션을 지정하고 유저 상세 페이지를 본 뒤 다시 검색 페이지로 돌아왔을 때 세부 옵션 값이 유지되도록 하였다. 세부 옵션 값을 유지하는 조건은 페이지 히스토리를 체크하여 이전 페이지가 유저 상세 페이지인 경우에만 유지되도록 하였다.

    - Windowing 기법 적용 : 유저 카드 목록에 react-cool-virtual 패키지를 활용한 windowing 기법 적용으로 렌더링 최적화하였다. react-cool-virtual의 useVirtual hook이 반환하는 OuterRef와 InnerRef를 윈도우윙에 적용시킬 DOM에 ref와 연결하여 구현하였다.

  - 유저 상세 페이지

    - 주소 공유 기능 구현 : navigator.clipboard.writeText을 활용한 URL Copy 기능 구현

    - 동적 페이지 SSR 적용 : getStaticPath fallback 속성을 blocking 으로 설정하여 사용자가 프리 렌더되지 않은 동적 페이지에 접근 시 SSR로 페이지를 제공하고 캐싱하여 이후 접근 시에는 캐싱된 페이지를 제공하도록 하였다.

  - 포스트 상세 페이지

    - 포스트 비디오 구현 : react-player의 ReactPlayer를 활용한 비디오 구현 및 마우스 혹은 키보드 입력에 따른 비디오 액션 커스텀, 아쉽게도 머지되지 않았다. 리액트플레이어 컴포넌트의 파라미터인 onReady, onProgess와 같이 비디오가 준비 되었을 때, 비디오가 실행 중일 때 등의 조건이나 비디오의 시간을 제어할 수 있는 seekTo 메소드 등을 이용하여 구현하였다.

    - 프로필 업데이트 구현 : react hook form을 활용하여 프로필 업데이트 페이지 구현, FormProvider와 useFormContext을 활용한 프로필 step 별 form 데이터 일괄 업데이트하였다. 단일 페이지의 form의 경우 useForm의 control으로 컨트롤러를 해당 폼에 등록하여 사용하고 FormProvider로 외부를 래핑한 후 별도의 컴포넌트 등에서 useFormContext을 통해 해당 form에 현재 상태를 조회하고 Controller로 해당 form을 업데이트 시킬 수 있게 하였다. 또한 form의 상태는 watch(컨트롤러에 작성 중인 값), resetField, getValues(폼에 저장된 값을 가져옴), setValue, formState의 dirtyFields, isValid, isDirty, errors 등을 통해 핸들링하였다.

    - AWS Lambda를 활용한 이미지 리사이징 : AWS S3에서 유저가 썸네일 혹은 포스트 이미지 업로드 시 AWS lamdba를 활용하여 이미지 리사이징 후 요청 시 해당 리사이징 파일 제공 -> 이미지 리사이징 방법이 개선되어야 할 것 같다. 리사이징 이미지를 생성해서 S3에 저장한 후 제공하는 것이 아닌 이미지 요청 시 리사이징 이미지를 생성해서 제공하는 방법도 있다. 해당 방식을 사용하면 S3에 원본만 저장하면 되기 때문에 더 효율적으로 관리가 가능하다.

    - 스크롤 이벤트 최적화 : 포스트 상세 페이지의 풀페이지 기능에 적용 된 스크롤 이벤트 트리거 시 메모리 누수 방지를 위한 클린업 처리 및 throttling 적용으로 이벤트 호출 최적화, lodash의 thottle 사용, useEffect의 경우 return으로 클린업 처리

  - 채팅 페이지

    - getStream.io API를 활용한 채팅 페이지 구현, 채널 연결 시도 시 토큰 발급 후 채널 연결, 채팅방 나가는 경우 채널 연결 해제, 채팅 채널 개수 제한, 스타일 커스텀 등의 기능 구현

  - 로그인 페이지

    - 회원 가입 페이지 구현 : react-hook-form의 useForm, useFormContext, Controller 등을 활용한 회원 가입 페이지 구현

    - 일반 로그인 구현 : JWT 토큰 기반 인증 방식을 활용한 일반 로그인 기능 구현, 액세스 토큰은 로컬 스토리지에서 관리하였으며 리프레쉬 토큰은 쿠키로 관리하였다. 액세스 토큰 만료 시 리프레쉬 토큰을 활용하여 재발급 받았다. 로그인 API 요청이 완료된 후 로컬 스트로지에 액세스 토큰을 저장하고 리프레시 토큰은 set-Cookie로 응답 헤더에 포함되어 쿠키에 저장되었다. 그 후 app 디렉토리 내부에 래핑 된 인증 관련 HOC 내부에서 state를 생성하여 관리하였다.

    - 소셜 로그인 구현 : Oauth2 방식으로 소셜 로그인 구현 (설명 : Oauth2 방식으로 구현, 소셜 로그인 버튼 클릭 시 ${process.env.NEXT_PUBLIC_MATCHARK_API_ENDPOINT}/auth/apple 과 같은 소셜 아이디 로그인 페이지로 리다이렉트 -> 소셜 아이디 로그인 후 서버에서 빈 화면인 verify/sns?key=… 페이지로 인증 key를 담아서 리다이렉트 -> 빈 화면인 verify/sns?key… 페이지에서 useEffect를 통해 쿼리 파라미터에 담긴 key를 사용하여 사용자 인증 API 요청, 해당 사용자 인증 API는 이미 존재하는 유저인지 확인하여 boolean 값 응답, 존재하지 않는 다면 바로 쿼리 파라미터의 key를 활용하여 자동 회원가입이 되는 로그인 API 요청 -> 이미 존재하는 유저인 경우 로그인 타입을 소셜 타입으로 변경할 지 물어보는 모달 노출 및 확인 시 자동 로그인 타입이 변경되는 로그인 API 요청 -> 요청 완료 후 메인 페이지로 리다이렉트)

  - 프로필 수정 페이지

    - 프로필 수정 페이지 구현 : react-hook-form의 useForm, useFormContext, Controller 등을 활용한 프로필 수정 페이지 구현

    - 프로필 이미지 업로드 : 사용자 프로필 이미지 업데이트 시 이미지 영역에 맞는 크기의 이미지로 리사이징 후 업로드하여 이미지 최적화, 사용자가 업로드 시도 시 해당 이미지에 블랍을 전달받고 createObjectURL로 임시 URL 생성한다. 그 후 createElement로 이미지 엘리먼트 생성 후 해당 엘리먼트의 src 어트리뷰트로 해당 임시 URL을 지정해준 뒤 해당 엘리먼트의 load 이벤트 리스너를 걸어 이미지 로드가 완료되면 캔버스를 통해 새로 이미지를 그린 후 해당 이미지의 Blob을 만들어 사용했다. 업로드 과정은 AWS-SDK를 활용하여 생성한 S3 객체 createPresignedPost 메소드로 파일을 업로드하고 업로드 URL을 DB에 저장하였다.

    - 포스트 업로드 구현

      - 업로드 파일 사이즈 체크 : 포스트 업로드 시 blob을 활용하여 format, size 체크 후 경고 토스트 노출 및 업로드 진행

      - 업로드 시 미리보기 제공 : 포스트 업로드 시 이미지 및 비디오를 분기 처리하여 이미지인 경우 createObjectURL을 활용한 미리보기 생성 및 노출, 비디오인 경우 썸네일 생성 후 video, canvas를 활용한 미리보기 생성 및 노출하였다.

      - 포스트 업로드 구현 : AWS-SDK를 활용하여 생성한 S3 객체 createPresignedPost 메소드를 활용하여 presigned URL 방식을 활용한 포스트 이미지 업로드를 구현하였고 포스트 비디오 업로드의 경우 abortMultipartUpload 메소드를 활용하여 Multiipart Upload 방식을 활용한 포스트 비디오 업로드를 구현하였다. 또한 업로드 시 useMutaion을 활용하여 DB에는 해당 포스트에 대한 정보를 함께 저장하였다.

      - 포스트 삭제 구현 : Next API routes를 활용하여 AWS S3에 해당 포스트를 삭제하는 API 생성, aws-sdk 패키지의 AWS 객체로 AWS 클라이언트를 생성하고 해당 객체 내부에서 S3 클라이언트, 클라우드프론트 클라이언트를 각각 생성하였다. 그 후 생성한 S3 클라이언트를 통해 S3 객체를 생성하는데 인증 액세스 키와 인증 시크릿 키를 함께 전달하여 생성한다. 그 후 S3 객체의 deleteObject 메소드의 파라미터로 버킷 이름과 이미지 URL을 넘겨주어 삭제한다.

    - 캐싱을 활용한 경고 모달 노출 : GraphQL 로컬 스키마 생성 및 캐싱을 활용하여 프로필 수정 중인 경우 경고 모달 노출, 프로필 수정 페이지에서 사용하는 useForm의 isDirty가 true가 되는 경우 로컬 스키마로 생성한 사용자 입력 수정 중임을 나타내는 boolean 값을 true로 업데이트하여 캐싱한 후 사용자가 페이지 벗어나려고 하는 경우 cache-only를 통해 해당 값을 체크하여 경고창을 노출

  - 비밀번호 재설정 페이지

    - SSR을 활용한 동적 쿼리 접근 : 비밀번호 재설정 페이지의 경우 유저에게 확인 이메일을 보낸 후 해당 이메일 내의 버튼을 이용하여 비밀번호 재설정 페이지로 접근하는데 이 때 쿼리 스트링에 컨펌 토큰을 포함해서 접근하게 된다. 이 토큰은 매 요청 시 변하는 해쉬 값이기 때문에 동적 쿼리 스트링을 받아올 수 없는 getStaticProps 대신 getServerSideProps를 사용하였다. 만약 사용자가 페이지 접근 시 쿼리 스트링에 토큰이 포함되어 있지 않은 경우 해당 페이지에 접근을 막고 대체 페이지를 제공해주기 위해 getServerSideProps의 파라미터로 쿼리에 담긴 토큰을 받아 검증 후 대체 페이지가 노출되도록 하였다. useEffect가 아닌 getServerSideProps를 사용한 이유는 useEffect는 컴포넌트 마운트 후 실행되기 때문에 잠시동안 사용자가 페이지를 볼 수도 있기 떄문에 getServerSideProps를 사용하였다.

- 프로젝트에서 기술적으로 어려웠던 점과 해결 방법에 대해 설명해주세요. (작성 중)

  - 기술적으로 어려웠던 상황은 구체적으로 생각나는 것은 없는 것 같습니다. 다만 처음 입사하여 온보딩 시 Nextjs, GraphQL, baseUI, styletron-react, react-hook-form 등 사용해보지 않았거나 현업에서 적용하는 것이 처음이었던 라이브러리들이 상당히 많았기 때문에 한꺼번에 많은 내용을 숙지해야하는 상황에 놓였었습니다. 그렇기 때문에 회사에서는 온보딩 과정을 3~6주 정도 가지며 천천히 적응하길 원하셨습니다. 하지만 저는 1주 정도의 온보딩 과정을 거친 후 바로 프로젝트에 투입되어 간단한 작업부터 처리해보는 것이 프로젝트 적응에 있어 더 큰 도움이 될 것이라고 생각하여 해당 사항을 회사에 요구하였고 회사에서는 제 요구를 받아들여 바로 간단한 작업들을 처리할 수 있도록 해주셨습니다. 그 결과로 회사에서 생각했던 기간보다 더 빠르게 프로젝트에 투입되어 성공적으로 적응할 수 있었습니다.

- 프로젝트에서 협업은 어떤 식으로 진행하셨나요?

  - 환경 변수 공유 및 디자인 시스템, 화면정의서 등은 컨플루언스를 통해 공유하였고 기능 개발 시 스프린트 기간을 설정해두고 티켓 별로 나누어 개발하였는데 이 때 지라를 통해 티켓을 관리했었습니다. 또한 GraphQL 테스트는 플레이그라운드를 사용했고 REST API 테스트는 스웨거를 사용했습니다. 또한 PR은 기능 단위로 PR을 올렸으며 커밋은 개발자 별로 자유롭게 하되 잘게 쪼개는 방식을 사용했었습니다. 또한 커밋 메세지 컨벤션은 지라의 티켓 번호와 연동되도록 작성하였고 프리픽스로 feat, fix, docs, reafactor 등을 사용했습니다. 그리고 데일리 미팅과 위클리 미팅을 통해 작업 내용 및 이슈 사항을 공유하였습니다. 코드 리뷰는 PR 코멘트로 진행되었습니다. 또한 프로젝트 빌드 및 배포는 사수 개발자 분이 담당하셨으며 그 외 업무는 차등을 두지 않고 나누어 작업하였습니다.

- 프로젝트에서 아쉬웠던 부분에 대해 설명해주세요.

  - 검색 결과 필터 시 클라이언트에서 모두 처리 : 또한 유저 검색 기능 중 필터 처리에 대한 아쉬움이 있습니다. 유저 검색 기능 중 필터 처리를 통해 유저를 필터링 하는 로직이 있었는데 해당 부분을 프론트 단에서 모두 처리하다보니 필터 처리 후 유저 목록 및 구글 맵 마커 노출이 늦는다는 단점이 있었습니다. 해당 부분을 필터 요청 시 API를 통해 필터 처리 된 목록을 요청하는 방식으로 변경한다면 더 빠르게 처리가 가능할 수 있을 것이라는 생각이 들었습니다.

  - 포스트 디테일 윈도우윙 미적용 : 포스트 디테일 페이지에 윈도우윙 기법을 적용하지 못한 아쉬움이 있습니다. 검색 페이지에서는 윈도우윙이 적용되어 사용자에게 노출되는 부분만 유저 목록이 렌더링 되도록 최적화가 되어있었는데 포스트 디테일 페이지에서는 윈도우윙이 적용되지 않아 불필요한 컨텐츠들이 모두 렌더링된다는 문제점이 있었습니다. 해당 부분에 윈도우윙 기법이 적용되었다면 렌더링 최적화에 도움이 되었을 것이라고 생각됩니다.

  - 스타일 린트 미사용 : 스타일 컨벤션에 관한 아쉬움이 있었습니다. 컴포넌트를 스타일링할 때 스타일 속성 순서를 정해놓지않고 스타일링하였는데 개인 작업에서는 항상 가독성 향상을 위해 속성의 순서를 정해놓고 스타일링을 하였습니다. (모질라에서 제안한 CSS속성 기술 순서 : display(객체의 노출여부/표현방식), list-style, position(위치/좌표), float, clear, width/height(크기/여백), padding/margin, border/background(윤곽/배경), color/font(글자/정렬), text-decoration, text-align/vertical-align, white-space, other text, content (내용))

  - 외부 폰트 사용 시 그대로 사용 : 외부 폰트 사용 시 폰트를 그대로 사용했었는데 불필요한 글자를 제거한 서브셋 폰트를 사용하였다면 폰트 경량화가 가능했을 것 같습니다.

  - 스켈레톤 UI 적용 시 컴포넌트 별 적용 : 컴포넌트 별로 적용하는 것보다 전체 페이지에 대해 적용시키는 것이 사용자 경험에 더 좋을 것 같다.

<br>

## # SQL

<br>

### # 테이블 조회 기본

<br>

- SELECT 컬럼명 FROM 테이블명

<br>

### # 테이블 조회 정렬

- 기본 정렬 : ORDER BY 컬럼명 ASC

  - ASC : 오름차순

  - DESC : 내림차순

- 여러 기준 정렬 : ORDER BY 컬렴명1 ASC, 컬럼명2 DESC

  - 컬럼명1을 기준으로 오름차순 정렬 후, 컬럼명1이 동일하다면 컬럼명2로 한번 더 내림차순 정렬한다.

<br>

## # interview

### # 스토리북 구축 및 배포

- 스토리북을 구성하기 위해 기본 애드온 사용

  - @storybook/preset-create-react-app: CRA 환경에서 Storybook 세팅 쉽게 해줌
  - @storybook/addon-onboarding: Storybook 입문자용 가이드 제공
  - @storybook/addon-links: 스토리 간 링크 연결
  - @storybook/addon-essentials: 인기 애드온 세트 (controls, actions, docs, viewport 등)
  - @storybook/addon-interactions: 플레이 기능 및 상호작용 테스트 지원

- stories 파일을 통해 스토리 생성

  - meta를 통해 스토리의 메타 데이터 설정 (title, component, tags, parameters, argTypes 등)
  - 그 외 스토리는 미리보기용 컴포넌트

- 기타 설정

  - Autodocs 설정을 통해 자동 문서화
  - main 파일에 `*.stories.tsx` 파일 생성 시 자동으로 추가되도록 구현

- 배포

  - 공유를 위해 배포하는데 S3, cloudfront를 활용해서 배포

- 모노레포 구축 및 배포

  - 터보레포의 book-it-now-shop에서 로컬 패키지가 dependencies인 이유, 그리고 peerDependencies

    - apps/bookitnow-shop/package.json 분석

      - peerDependencies : peerDependencies의 역할은 해당 라이브러리가 특정 버전으로 설치되어있어야함을 명시하는 것이다. 우리 프로젝트의 구조 중 book-it-now-shop의 경우 peerDependencies 내부 패키지들의 버전을 와일드 카드(`*`)로 설정하였는데 이런 경우에는 root package.json에 명시된 버전으로 설치되어있어야 함을 의미한다. 즉 root package.json에 의해 이미 설치되어 있는 패키지 버전을 따라간다는 것이다.

      - dependencies : dependencies의 경우 운영 환경에서 필요한 패키지를 설치한다고 알고 있는데 터보레포에서 생성되는 로컬 패키지(`ex @repo/ui`) 또한 여기에 포함되어야한다. peerDependencies에 포함될 수 없는 이유는 외부 라이브러리와 같이 root package.json에 버전을 명시하여 설치하는 방식이 아닌 로컬에서 생성한 패키지이기 때문이다. 그렇기 떄문에 별도로 생성된 로컬 패키지의 package.json을 참고하여 설치하게 된다. `(ex { "name": "@repo/ui", "version": "1.0.0", … })`

    - peerDependencies vs dependencies 요약

      - peerDependencies는 특정 패키지가 다른 패키지를 필요로 하지만, 그 패키지를 직접 포함하지 않고, 상위 프로젝트(패키지를 설치하는 프로젝트)에서 해당 의존성을 설치하도록 요구하는 방식

  - turbo.json

    - tasks 내부에서 bookitnow-client#build와 같이 각 프로젝트 혹은 build로 공통 빌드 설정을 적용, dependsOn의 경우 ^build로 설정하여 부모 혹은 의존하는 패키지들의 build 작업을 먼저 실행

  - packages

    - 공통 패키지 package.json 공통 요소

    - type의 경우 docker + openapitools/openapi-generator-cli를 통해 타입을 자동생성

  - 공통 apis, icons, logics, types, ui를 관리

<br>
