# NextJS - `_app`과 `_document`

### # `_app`

<br>

- 참고 : https://nextjs.org/docs/advanced-features/custom-app

- 특징

  1. 가장 먼저 실행되는 컴포넌트입니다. (`_app` -> `page component` -> `_documnet`(Server side))

  2. 모든 페이지는 이 컴포넌트를 통합니다. (각 Route 구성 요소를 래핑하는 역할)

  3. 페이지에 적용할 공통 레이아웃 역할을 합니다. (ex header, footer, layout component 등)

  4. 페이지 전환 시 전체 레이아웃을 유지할 수 있습니다.

  5. 페이지 전환 후 상태를 유지시킬 수 있습니다.

  6. 글로벌 CSS를 적용시킬 수 있습니다.

  7. 추가적인 데이터를 페이지로 주입시켜주는게 가능합니다.

  8. 각종 Provider 설정할 수 있습니다. (ex Redux, Apollo 등)

  9. props로 받는 Component는 페이지에 보여줄 컴포넌트이며, 페이지 전환 시 이 props의 값이 변경됩니다.

  10. props로 받는 pageProps는 데이터 패칭 메소드를 통해 가져온 초기 객체입니다.

  11. `_app` 내부에서는 getStaticProps 또는 getServerSideProps 메서드를 지원하지 않습니다.

  12. `_app` 내부에 getInitialProps가 있는 경우 자동 정적 최적화가 비활성화 됩니다. 자동 정적 최적화란 요구사항이 없는 경우 자동으로 페이지를 정적으로 생성하는 것을 말합니다.

<br>

### # `_document`

<br>

- 참고 : https://nextjs.org/docs/advanced-features/custom-document

- 특징

  1. `_document`는 `_app` 다음에 실행되며, 공통적으로 활용할 head(ex meta태그)나 body 태그 안에 들어갈 내용들을 커스텀할 때 활용합니다.

  2. 폰트 import, CDN 등을 연결하여 사용할 수 있습니다.

  3. Document 클래스를 상속받는 클래스 컴포넌트로 작성해야한다는 규칙이 있습니다.

  4. 렌더 함수는 꼭 Html, Head, Main, NextScript를 포함해야 합니다.

  5. 페이지 별 공통적인 사항이 아닌 title같은 경우 app에서 처리합니다.

  6. 서버 사이드에서 동작하기 때문에 onClick과 같은 이벤트나, CSS 스타일 파일은 작동하지 않습니다. 테스트해보기 위해 useEffect hook을 사용하여 console에 문자열이 찍히는지 확인해보았는데 역시 `_document`는 찍히지 않고 `_app`은 찍힙니다.

  7. 커스텀이 필수는 아니며 커스텀하지 않을 경우 Next 모듈에 존재하는 document.js을 실행하게 됩니다.

  8. Head 컴포넌트 조작 시 import 위치를 주의해야 합니다. `_document` 내부에 사용하는 모든 페이지에 공통적으로 적용시킬 Head의 경우 next/document에서 가져온 Head를 사용해야 합니다. 또 title 태그와 같이 페이지별로 다른 Head 설정을 할 경우에는 next/head에서 가져온 Head를 사용해야 합니다.

  9. `_app`과 마찬가지로 `_document` 내부에서는 getStaticProps 또는 getServerSideProps 메서드를 지원하지 않습니다.

  10. `_document`는 페이지 별 오버라이딩이 가능합니다. 하지만 공통으로 사용하고 있는 `_document`가 있다면 페이지 별로 지정 된 `_document`로 대체되어 문제가 발생할 수 있습니다.

<br>

### # `_document`는 `_app` 한 줄 정리

<br>

- `_document`는 정적인 상태로 적용시킬 공통 사항을 적용시킬 때 사용하며 react의 `index.html`과 유사한 기능을 수행합니다. `_app`는 동적인 상태로 적용시킬 공통 사항을 적용시킬 때 사용하며 react의 router 설정 컴포넌트와 유사한 기능을 수행합니다.

<br>

## # Next.js의 데이터 패칭 방식

<br>

Next.js의 pre-rendering(사전 렌더링)을 위한 데이터 패칭 방식은 크게 4가지가 있습니다. 각각의 데이터 패칭 방식을 통해 받아온 데이터는 컴포넌트에 props로 전달받아 사용할 수 있습니다.

- getInitialprops (SSR : Server Side rendering)

  - 최초에 앱이 렌더링되거나, 클라이언트 라우팅이 일어나는 순간 데이터를 패칭합니다. getServerSideProps와 비슷하지만 route로 접근할 때 새로고침이나 직접 URL을 입력하는 방식으로 접근하면 서버에서, Next.js에서 제공하는 Link 컴포넌트를 통해 접근한다면 클라이언트에서 호출됩니다.

<br>

- getServerSideProps (SSR : Server Side rendering)

  - 페이지 접근 시 매번 새로 데이터를 패칭합니다.

<br>

- getStaticProps (SSG: Static Site Generation)

  - 빌드 시 데이터를 패칭하고 CDN에 캐싱하여 모든 요청에 재사용합니다. 빌드 된 디렉토리에 접근해보면 빌드 시점에 맞는 데이터가 `index.html`에 채워져있는 것을 확인해볼 수 있습니다. 즉 빌드 시점 후에 서버에 데이터 변화가 일어나게 되면 빌드되지 않은 경우에는 데이터가 최신화되지 않습니다.

  - development 환경에서 getStaticProps는 매 요청마다 실행되며 production 모드에서는 getStaticProps는 빌드 시 실행됩니다.

<br>

- getStaticProps + revalidate (ISR: Incremental Static Regeneration)

  - getStaticProps 사용 시 Data의 최신화가 이루어지지 않는다는 단점이 있는데 revalidate 속성을 활용하여 해결할 수 있습니다. 초기에 캐싱 된 페이지를 보여준 후 revalidate 주기마다 데이터의 업데이트를 확인하여 페이지를 재생성합니다.

  - 트래픽이 발생하면 재생성이 이루어지기 때문에 사이트를 이용하는 유저가 없는 경우 revalidate 주기를 넘어도 페이지가 재생성되지 않습니다.

<br>

## # 프로젝트 분석

<br>

- `_document.tsx`

  ```tsx
  // 페이스북에서는 광고효과를 측정하기 위해서 사용하는 페이스북 픽셀 측정 도구를 사용하기 위한 스크립트입니다.
  const META_SDK_SNIPPET = `!function(f,b,e,v,n,t,s){if(f.fbq)return;n=f.fbq=function(){n.callMethod?n.callMethod.apply(n,arguments):n.queue.push(arguments)};
              if(!f._fbq)f._fbq=n;n.push=n;n.loaded=!0;n.version='2.0';
                n.queue=[];t=b.createElement(e);t.async=!0;
                t.src=v;s=b.getElementsByTagName(e)[0];
                s.parentNode.insertBefore(t,s)}(window, document,'script',
              'https://connect.facebook.net/en_US/fbevents.js');
              fbq('init', '${META_ID}');
              fbq('track', 'PageView');`;

  class _document extends Document<{
    stylesheets: Sheet[];
  }> {
    /*
      찾아보니 segment가 제공하는 analytics.js 스니펫을 렌더링할 때 사용한다는데 무슨 말인지 잘 이해가 가지 않습니다.
      Google analytics처럼 페이지 추적해서 사용자 흐름 분석하기 위해 적용시키는 것이 아닐까 싶습니다.
      그렇기 때문에 개발 모드를 구분하는 조건문이 포함되어 있는 것 같습니다.
    */
    renderSnippet() {
      const opts = {
        apiKey: ANALYTICS_WRITE_KEY,
        page: true,
      };
      if (NODE_ENV === "development") {
        return snippet.max(opts);
      }
      return snippet.min(opts);
    }

    /*
    	공식문서에서는 getInitialProps보다 getServerSideProps나 getStaticProps로 데이터 패칭하는 것을 권장하고 있습니다.
    	getInitialProps는 서버 사이드에서 실행되며 서버 사이드 렌더링 적용 시 사용합니다.
    	아래 코드에서 사용한 이유는 styletron을 우선적으로 적용시키기 위해 사용한 것이 아닌가 싶습니다.
    	nextjs의 Pre-rendering 과정은 html을 먼저 로드하여 보여주는 inital load html 과정과 hydration 과정으로 나누어 이루어지는데
    	이 hydration 과정에서 js가 로드되어 우선적으로 로드한 html과 동기화하게 된다고 합니다.
    	그렇기 때문에 js내부에 작성되는 css-in-js인 styletron은 html이 보여질 때 바로 적용되는 것이 아닌 그 후에 로드되게 되는 것입니다.
    	이를 해결하기 위해서 renderPage 함수를 사용해야 한다고 합니다.
    	공식 페이지에도 renderPage 함수를 커스터마이징하는 것은 css-in-js 라이브러리를 사용할 때만 하라고 나와있습니다.
    	renderPage 함수를 통해 렌더링 되는 조건을 설정하여 렌더링할 수 있습니다.
    */
    static getInitialProps(props: any) {
      // eslint-disable-next-line react/display-name
      const page = props.renderPage((App: any) => (props: any) => (
        <StyletronProvider value={styletron}>
          <App {...props} />
        </StyletronProvider>
      ));
      const stylesheets = (styletron as Server).getStylesheets() || [];
      return { ...page, stylesheets };
    }

    /*
    	return 내부에서 모든 페이지에 공통적으로 적용 될 html 문서의 구조를 커스텀할 수 있습니다.
    	페이지가 제대로 렌더링되기 위해서는 `<Html>`, `<Head />`, `<Main />` 및 `<NextScript />`가 필요하며 폰트를 적용시키거나 글로벌 CSS를 정의할 수 있습니다.
    	title과 같이 페이지 별로 다르게 적용되는 태그는 `_document`가 아닌 `_app`에서 관리합니다.
    	main같은 경우는 `_app`에 의해 동적으로 변경되는 부분입니다.
    */
    render() {
      return (
        <Html>
          <Head>...</Head>
          <body>
            <Main />
            <NextScript />
          </body>
        </Html>
      );
    }
  }
  ```

<br>

- `_app.tsx`

  ```tsx
  const debouncedCalculateAlternativeViewportUnit = debounce(
    calculateAlternativeViewportUnit,
    700
  );

  interface DefaultStaticProps {
    isPublic?: boolean;
    appHeaderConfig?: Omit<AppHeaderProps, "theme">;
    hasAppBar?: boolean;
    isNoProfileUserAccessible?: boolean;
  }

  // dayjs 사용 시 global로 한국어 locale 사용합니다.
  dayjs.locale("ko");

  /*
    - Component : 렌더링 될 컴포넌트, 요청한 페이지를 말한다. GET `/` 요청을 보냈다면, Component 에는 /pages/index.js 파일이 props로 내려오게 됩니다.
    - pageProps : getInitialProps을 통해 내려받은 props 입니다. (getInitialProps, getStaticProps, getServerSideProps 를 통해 가져온 초기 속성값을 의미합니다. 위의 값들이 없다면 빈 객체를 반환합니다.) appHeaderConfig, isPublic, hasAppBar는 각 페이지 getStaticProps로 빌드 타임 시 해당 속성들의 값을 props로 패칭하여 각 페이지 별 접근 및 헤더 등을 페이지 별로 제어합니다.
    - router : 요청한 페이지의 정보를 가진 객체입니다.
  */
  const _App: FC<AppProps> = ({
    Component,
    pageProps: {
      appHeaderConfig,
      isPublic = false,
      hasAppBar = false,
      isNoProfileUserAccessible = false,
      ...pageProps
    },
    router,
  }) => {
    const [isBrowserModalOpen, setBrowserModalOpen] = useState(false);
    const [historyArr, setHistoryArr] = useState<string[]>([]);

    useMount(function didMounted() {
      // 초기 렌더링 시 디스플레이 크기에 대응합니다.
      calculateAlternativeViewportUnit();
      // 브라우저를 감지하여 크로스 브라우징에 대응, 모달 띄워서 크롬으로 사용 유도합니다.
      const client = detectBrowser();
      client === browser.SAFARI && setBrowserModalOpen(true);

      const { asPath } = router;
      setHistoryArr((prevState) => [...prevState, asPath]);
    });
    // 윈도우 리사이징 시 디스플레이 크기 대응, 여러번 호출 시 0.7초마다 실행되도록 디바운스 걸어 과부하를 방지합니다.
    useEvent("resize", debouncedCalculateAlternativeViewportUnit);
    // 페이지 history 기록, 현재 페이지가 마지막 배열 요소와 같지 않을 경우 누적해서 쌓이는 형식으로 저장됩니다.
    // 이런 식으로 전체 페이지에서 사용 될 로직의 경우 `_app` 내부에 작성하여 상태를 유지시킬 수 있습니다.
    useEffect(() => {
      const { asPath } = router;
      console.log(router);
      if (historyArr[historyArr.length - 1] !== asPath) {
        setHistoryArr((prevState) => [...prevState, asPath]);
      }
    }, [pageProps]);

    return (
      <StyleTronProvider value={styletron}>
        {/* SEO를 위한 타이틀 및 메타태그를 설정합니다. */}
        <DefaultSeo {...SEO} />
        {/* 로그인 상태를 전달하는 Provider 입니다. */}
        <WithRealmAppProvider appId={process.env.NEXT_PUBLIC_REALM_ID ?? ""}>
          {/* Graphql API와 연동 가능하도록 ApolloProvider로 감싸줍니다. */}
          <WithApolloProvider pageProps={pageProps}>
            {/* baseui를 사용하기 위해 BaseProvider로 감싸줍니다.*/}
            <WithBaseProvider
              appHeaderConfig={appHeaderConfig}
              hasAppBar={hasAppBar}
            >
              {/* 조건에 따른 헤더 노출. AppHeader가 잘 이해가 가지 않습니다.. */}
              {appHeaderConfig && (
                <Layer>
                  {appHeaderConfig && <AppHeader {...appHeaderConfig} />}
                </Layer>
              )}
              {/* props로 전달받은 프로필 입력 상태나 유저의 로그인 상태를 구분하여 사용자에게 보여줄 children(컴포넌트 페이지)를 결정합니다.*/}
              <WithAuth
                isPublic={isPublic}
                isNotFound={router.route.includes("404")}
                isNoProfileUserAccessible={isNoProfileUserAccessible}
              >
                <Component {...pageProps} historyArr={historyArr} />
              </WithAuth>
              {/* 각 페이지 별로 getStaticProps를 사용하여 빌드 타임 시 해당 속성들의 값을 props로 패칭하고
              이 props를 통해 hasAppBar의 boolean값을 제어합니다. */}
              {hasAppBar && (
                <Layer>
                  <AppBar items={DEFAULT_APP_BAR_SETS} />
                </Layer>
              )}
              {/* 브라우저를 감지하여 크로스 브라우징에 대응, 모달 띄워서 크롬으로 사용 유도,
              다른 브라우저(ex 사파리)로 테스트 시 확인 가능합니다. */}
              <MAModal
                type="exit"
                status="error"
                isOpen={isBrowserModalOpen}
                title="We work best in Google Chrome"
                content="Go and experience Matchark in Google Chrome!"
                okText="I got it"
                cancelText="Cancel"
                onOk={() => setBrowserModalOpen(false)}
                onModalClose={() => setBrowserModalOpen(false)}
              />
            </WithBaseProvider>
          </WithApolloProvider>
        </WithRealmAppProvider>
      </StyleTronProvider>
    );
  };
  ```

<br>

## # 회의 후 추가 내용

- 하위 페이지 컴포넌트를 확인해보면 가장 하단에 데이터 패칭 메소드와 자기 자신을 export하는 것을 볼 수 있다. 이렇게 export된 컴포넌트와 데이터 패칭 메소드가 `_app`으로 전달되게 되는 것이다.

  ```tsx
  // src/pages/myPage/index.tsx
  const Index: FC<MyPageProps> = () => {
      ...

  return (
      <Main>
        ...
      </Main>
    );
  };

  const getStaticProps: GetStaticProps<DefaultStaticProps> = async () => ({
    props: {
      isPublic: true,
      hasAppBar: true,
    },
  });

  export default Index;
  export { getStaticProps };
  ```

  그러면 아래와 같이 `_app`은 Props로 전달받은 Component를 return하는데 이 때 하위 페이지 컴포넌트에서 전달받아 업데이트 된 pageProps를 Component에 Props로 전달하여 return한다. 즉 하위 페이지 컴포넌트에서 getStaticProps 데이터 패칭 메소드를 그대로 전달받아 빌드 시 `_app`에 getStaticProps 메소드를 실행하여 업데이트 된 pageProps를 얻고 그 객체를 하위 페이지 컴포넌트에 Props로 전달하는 것이다. 만약 하위 페이지에서 전달되는 데이터 패칭 메소드가 없는 경우 `_app` 내부에 작성 된 initial Props가 적용된다.

  ```tsx
  const _App: FC<AppProps> = ({
    Component,
    pageProps: {
      appHeaderConfig,
      isPublic = false,
      hasAppBar = false,
      isNoProfileUserAccessible = false,
      ...pageProps
    },
    router,
  }) => {

    ...

    return (
      ...       /*
                  하위 페이지로부터 전달받은 Component를 return하는데 이 때 하위 페이지로부터 전달받은 데이터 패칭 메소드로      pageProps를 업데이트 시켜 이 pageProps를 Component의 Props로 전달한다.
                */
                <Component {...pageProps} historyArr={historyArr} />
      ...
  ```

<br>
