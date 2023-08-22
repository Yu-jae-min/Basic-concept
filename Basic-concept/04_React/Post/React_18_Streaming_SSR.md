# **[React.js] React 18 Streaming SSR**

2023년 08월 22일

<br>

## **1. 기존 SSR의 문제점**

우선 SSR을 사용하는 이유는 초기 로딩 속도, 검색 엔진 최적화 등의 이유를 대표적으로 꼽을 수 있다. CSR 경우 JS가 로드되기 전 사용자가 빈 페이지만 보게 되는 경우가 있는데 초기 로딩 속도가 빠르고 HTML을 우선 보여주는 SSR의 경우 이러한 문제를 해결할 수 있다.

[ CRS의 문제점 ]

![Reactjs_React_18_Streaming_SSR_01](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/cf811343-9a16-4979-8f1b-78f1a5537e60)

기존 SSR의 동작 방식은 브라우저가 서버에서 렌더링이 완료된 HTML 파일(static)을 받아온 뒤 이 HTML 파일을 파싱한 후 사용자에게 우선적으로 보여준다. 그 후 JS가 로드되면 하이드레이션을 통해 사용자와 상호작용 가능하도록 한다.

[ SSR HTML 렌더링과 하이드레이션 ]

| ![Reactjs_React_18_Streaming_SSR_02-1](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/cdb73f40-e92c-44d3-b1b6-aa20a6540727) | ![Reactjs_React_18_Streaming_SSR_02-2](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/b9466a36-3895-424e-9715-c12dc8bd7924) |
| :--------------------------------------------------------------------------------------------------------------------------------------: | :--------------------------------------------------------------------------------------------------------------------------------------: |

여기서 응답 데이터의 바이트가 브라우저에 처음 전달된 시점이 `TTFB(Time To First Byte)`, HTML 파일을 받아온 뒤 뷰포트 내 의미있는 콘텐츠 일부가 처음 화면에 렌더링 될 때 까지의 시간이 `FCP(First Contentful Paint)`, 하이드레이션까지 완료된 시간이 `TTI(Time To Interact)`이다.

[ TTFB / FCP / TTI ]

![Reactjs_React_18_Streaming_SSR_03](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/99443611-9ab3-41fe-810b-31d592e7b947)

이 때 브라우저가 첫 바이트를 읽는 데 걸린 시간인 TTFB가 늦어지면 연달아 FCP와 TTI가 늦어지게 되어 사용자 경험에 좋지 않은 영향을 미친다. 만약 서버에서 렌더링이 지연되어 TTFB가 계속 늦어지는 경우 상황에 따라 CSR보다 FCP가 느린 상황이 연출되기도 한다.

[ TTFB의 지연 ]

![Reactjs_React_18_Streaming_SSR_04](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/8f3d50f4-52a7-407c-b3bd-7ec8c15c627c)

그래서 React 18에서는 Streaming을 통해 이러한 문제를 해결한다. (Next 13 버전에서는 app 디렉토리를 통해 HTML Streaming을 지원한다. https://nextjs.org/docs/app/building-your-application/routing/loading-ui-and-streaming)

<br>
<br>

## **2. Streaming SSR**

<br>

### **2-1. Stream이란?**

[ Stream ]

![Reactjs_React_18_Streaming_SSR_05](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/a5a1a7bc-bead-4465-b3ce-c5622b47dd80)

우선 Stream이란 시간이 지남에 따라 사용할 수 있게 되는 일련의 데이터 요소이다. 쉽게 이해하면 서버에서 클라이언트로 데이터를 한 번에 전송하는 게 아니라, 청크를 나눠서 보내는 거라고 이해할 수 있다. HTML을 Streaming 한다면 위의 그림에서는 `data`가 HTML의 부분 부분이 되는 것이다.

즉, Streaming SSR이란 서버에서 HTML을 여러 Chunk로 나눠 렌더링 하고, 렌더링이 완료된 부분만 먼저 클라이언트에 응답하는 기술이라고 할 수 있다. 이를 통해 TTFB를 빠르게 하고, 최초 HTML을 응답받은 후에는 `<script>` 태그와 함께 스트림 형태의 추가 콘텐츠를 받을 수 있다.

또한 브라우저에서는 전달받은 HTML 부분을 먼저 렌더링하고 렌더링이 완료된 부분 먼저 하이드레이션을 수행한다.

[ Streaming SSR ]

| ![Reactjs_React_18_Streaming_SSR_06-1](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/5b9a567c-fc1c-4488-91a9-98f201c3415f) | ![Reactjs_React_18_Streaming_SSR_06-2](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/b4b1963e-5b64-45b4-8de6-5d6a1a410e81) | ![Reactjs_React_18_Streaming_SSR_06-3](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/364f92e3-54c9-467b-b818-a06b16bc5eaa) | ![Reactjs_React_18_Streaming_SSR_06-4](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/a74a9fc2-f447-45c4-8386-2283e537a0aa) |
| :--------------------------------------------------------------------------------------------------------------------------------------: | :--------------------------------------------------------------------------------------------------------------------------------------: | :--------------------------------------------------------------------------------------------------------------------------------------: | :--------------------------------------------------------------------------------------------------------------------------------------: |

아래 이미지는 Streaming HTML의 시연 이미지이다. HTML Stream을 응답받음에 따라서 각 리스트의 색상이 하늘색으로 변하고, 해당 응답까지 몇 초가 걸렸는지 나타내고 있다. 여기에서는 맨 위에 위치한 리스트가 1.5초로 가장 오래 걸렸음을 알 수 있다. 또한 HTML의 응답의 waterfall을 보면 다운로드가 1.49초 걸린 것을 확인할 수 있다. 결론적으로 HTML의 부분 부분을 stream으로 지속적으로 응답받으면서 DOM을 업데이트했다고 이해할 수 있다.

[ Streaming HTML의 시연과 응답의 waterfall ]

| ![Reactjs_React_18_Streaming_SSR_07-1](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/260aa068-3074-4674-9e7f-66128ed1a6c4) | ![Reactjs_React_18_Streaming_SSR_07-2](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/ca7ede34-5be0-4d2f-b0a6-023d43ab0a15) |
| :--------------------------------------------------------------------------------------------------------------------------------------: | :--------------------------------------------------------------------------------------------------------------------------------------: |

<br>

### **2-2. React에서 Streaming SSR 적용 방법**

- 참고 URL : https://codesandbox.io/s/kind-sammet-j56ro?file=/src/App.js

[ server/server.js, express server 생성 ]

![Reactjs_React_18_Streaming_SSR_08](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/60f2bdd1-f564-4ac8-9ea7-39be1af5acc1)

서버는 Express로 구현하며 서버에서 GET 요청에 대한 기본적인 라우트를 만들고, 콜백을 정의한다. 여기서 `waitForWebpack`은 추후에 `bootstrap`할 번들 파일을 읽기 위한 함수이고, 중요한 것은 `render` 부분이다.

[ server/server.js, HTML 변환 ]

![Reactjs_React_18_Streaming_SSR_09](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/cfd1da9f-851d-4db8-b4ce-61250b4c69a3)

왼쪽은 stream을 사용하지 않는 예전 버전의 렌더링이고, 오른쪽은 stream을 사용하는 최신 버전이다. 왼쪽은 `renderToString`을 사용해 ReactNode를 렌더링 해서 `HTML String`으로 변환하고 있다. 오른쪽은 `renderToPipeableStream`을 사용해서 HTML String이 아닌 `Stream`으로 변환하고 있다. 또한 `stream.pipe`는 `stream`으로 되어 있는 HTML의 일부분을 `res` 객체에 연결하는 역할을 한다.

[ src/App.js, App과 하위 컴포넌트 ]

![Reactjs_React_18_Streaming_SSR_10](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/813e9fb0-437d-4ecb-a80b-c1b1be113d67)

위 코드는 서버에서 렌더링 했던 `App` 컴포넌트(code line 7)의 코드이다. 이처럼 React 18은 SSR에서 `Suspense`와 `lazy`를 통해 코드 스플리팅이 가능하도록 설계되었기 때문에 점진적, 선택적 하이드레이션이 가능한 것이다. (자세한 내용은 아래 [Discussion](https://github.com/reactwg/react-18/discussions/37)에서 확인할 수 있다.)

[ react의 code splitting ]

![Reactjs_React_18_Streaming_SSR_11](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/0846c7ae-245b-4478-8930-052304199422)

그리고 렌더링 과정에서 실행되는 `renderToPipeableStream` 메서드에서는 Suspense로 감싼 컴포넌트에서 비동기 작업이 완료될 때까지 fallback 컴포넌트를 포함한 나머지 컴포넌트를 Stream으로 렌더링한다. 그리고 이후 Suspense의 children에 속하는 컴포넌트에서 비동기 작업이 완료되면 다시 해당 부분을 렌더링해서 Stream에 추가해서 응답한다.

만약 이전 버전의 `renderToString` 메서드를 사용한다면 모든 컴포넌트를 즉각적으로 HTML String으로 렌더링해야 하기 때문에 비동기 작업이 지연되는 특정 컴포넌트가 있다면 렌더링 전체의 과정이 지연되었을 것이고, Suspense를 사용하더라도 추가적으로 렌더링된 부분 데이터를 Stream과 같이 전달할 방법이 없기 때문에 fallback 컴포넌트만 렌더링될 것이다.

이것이 바로 [React 18 이전 버전 SSR 환경에서 Suspense가 동작하지 않는 이유](https://react.dev/reference/react-dom/server/renderToString#when-a-component-suspends-the-html-always-contains-a-fallback)이다.

[ stream을 통해 받아오는 hidden div 엘리먼트 ]

![Reactjs_React_18_Streaming_SSR_12](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/246facb3-77de-42e9-9699-7a29ed711f86)

[ template 엘리먼트 교체 ]

![Reactjs_React_18_Streaming_SSR_13](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/3641718e-d094-40bc-bc05-42bd45209724)

최종적으로 브라우저가 응답받은 HTML을 보면 추가 stream으로 받은 `hidden` div element가 있고, 인라인 `<script>` 태그에서는 id가 `S:0`인 요소인 `hidden` div element를 `B:0` 위치에 교체하는 명령을 실행한다. `B:0`는 `Suspense`로 감쌌던 원래 위치에 해당한다.

즉 `B:0` 위치는 초기에 `Suspense`의 `fallback 컴포넌트`를 보여주다가 stream을 통해 뒤늦게 들어온 `hidden` div element로 교체하게 되는 것이다.

뒤늦게 받은 stream이더라도 react에서는 원래 위치를 알고 있기 때문에 이 위치로 교체만 하면 우리가 원하는 최종 결과물을 얻을 수 있게 되는 것이다.

<br>

### **2-3. 기타 Q&A**

- Streaming SSR을 하기 위해서 `Next.js`에서 어떤 API를 사용해야 하나요?

  - 베타 버전의 `app` 디렉토리를 사용하면 기본적으로 HTML을 스트리밍 합니다.

- Suspense를 함께 사용하지 않으면 어떻게 되나요?

  - 모든 스트리밍이 완료되기까지 기다리므로, 기존 SSR과 동일한 화면을 보여줍니다.

    ![Reactjs_React_18_Streaming_SSR_14](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/05e6e104-a7be-4d2b-9cc8-8ccb6d3ab2e5)

- Streaming SSR을 사용했을 때 얼마나 성능 향상을 체감했나요?

  - 이번에 처음 관심을 갖고 조사한 기술이라 아직 프로덕션에 도입하진 못했습니다. 현재는 Next.js에서 베타 기능으로 구현되어 있고, [성능 저하 이슈](https://github.com/vercel/next.js/issues/44766)가 있는 것으로 보입니다. 빠른 TTFB, 점진적 하이드레이션의 장점이 있지만, [벤치 마크](https://github.com/SuperOleg39/react-ssr-perf-test)를 보면 Streaming에 서버 리소스를 기존보다 월등히 많이 사용하는 것으로 보입니다.

<br>
<br>

## **3. 레퍼런스**

- https://sanoo.dev/streaming-ssr
- https://velog.io/@ckstn0777/New-Suspense-SSR-Architecture-React-18-Streaming
- https://nextjs.org/docs/app/building-your-application/routing/loading-ui-and-streaming
- https://react.dev/reference/react/Suspense
- https://github.com/reactwg/react-18/discussions/37
- https://codesandbox.io/s/kind-sammet-j56ro?file=/src/App.js
- https://nextjs.org/docs/app/building-your-application/routing/loading-ui-and-streaming#what-is-streaming
- https://shopify.github.io/hydrogen-v1/tutorials/streaming-ssr
- https://react.dev/reference/react-dom/server/renderToPipeableStream
