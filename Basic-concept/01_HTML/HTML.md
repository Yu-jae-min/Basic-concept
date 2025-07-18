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
