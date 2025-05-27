## # Next.js(13버전 이전)

### # Next.js 사용 이유

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
