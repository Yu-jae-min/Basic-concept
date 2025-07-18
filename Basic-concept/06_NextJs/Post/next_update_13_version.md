# NextJS - NextJS 13

### # NextJS 13 업데이트 내용

<br>

- 업데이트 내용 요약 (https://nextjs.org/blog/next-13)

  - app/Directory(Beta)

    - Layout : 리렌더링 방지를 기본으로 구현한 Layout

    - React 서버 컴포넌트 : React 의 새로운 Server Component 지원하여 로딩 속도 개선

    - Streaming : 점진적으로 스트리밍 되어 UI 렌더링 할 수 있는 Streaming

  - Turbopack : 웹팩보다 700배 빠른 Rust 기반의 대체품

  - New next/image : 빨라진 lazy loading (Google과 협업으로 기존 로딩 퍼포먼스를 저해하던 요소들 개선)

  - New @next/font(Beta) : 빌드타임 때 최적화를 시키면 구글 폰트가 기본으로 내장 (폰트 최적화)

  - Improved next/link : 기존 `<Link>`안에 사용되던 `<a>` 태그 불필요

<br>
<br>

### # app/디렉토리(Beta)

<br>

- New app Directory (Beta) : https://nextjs.org/blog/next-13#new-app-directory-beta

  - 현재 pages 디렉토리를 대체할 수 있다.

  - Layouts : https://nextjs.org/blog/next-13#layouts

    - 공통 UI를 배치하는데 사용할 수 있다.

    - 페이지 이동 시에도 리렌더링 되지 않고 현재 상태를 유지한다.

    - 전역 state를 관리할 때도 사용할 수 있을 것 같다.

  - Server Components : https://nextjs.org/blog/next-13#server-components

    - app 디렉토리 내부 요소는 기본적으로 서버 컴포넌트이다.

    - 리액트 서버 컴포넌트는 서버 사이드 렌더링을 실시한다.

    - 클라이언트로 전송되는 자바스크립트 번들 크기를 줄여주기 때문에 로딩 속도가 향상된다.

    - 클라이언트 컴포넌트를 사용하기 위해서는 import 전 최상단에 'use client' 키워드를 사용해야한다.

    - 서버 컴포넌트와 서버 사이드 렌더링의 차이

      - react의 문제

        - 많은 수의 네트워크 요청 발생

        - 번들 크기

      - 서버 컴포넌트 이점

        - 서버 컴포넌트는 번들에 포함되지 않는다. 브라우저에서 다운로드 하지 않기 때문에 번들 크기에 영향을 주지 않는다.

        - 정적/렌더링 전용 컴포넌트를 서버측으로 이동하여 번들 크기를 줄일 수 있다.

        - 서버 컴포넌트는 서버측 리소스에 접근할 수 있다.

      - 서버 컴포넌트와 서버 사이드 렌더링 차이

        - 서버 사이드 렌더링은 단순히 HTML로 렌더링 된 컴포넌트를 클라이언트에 전송하여 빠른 응답을 보이는 것처럼 하는 것이다.

        - 서버 컴포넌트는 클라이언트로 스트리밍되는 특수 형식으로 렌더링 된다. 응답 형식은 JSON 형식과 유사하다.

        - 서버 사이드 렌더링은 한 번만 사용되는 반면 서버 컴포넌트는 데이터를 다시 렌더링 하기 위해 여러 번 다시 가져올 수 있다.

  - Streaming : https://nextjs.org/blog/next-13#server-components

    - app 디렉토리 내부에 예약 파일(ex loading.js, error.js)을 생성하여 로딩 스피너 혹은 스켈레톤 UI를 렌더링할 수 있다. -> 사용자 경험 향상

    - 디렉토리별 예약파일 사용으로 구조가 복잡해질 수 있다.

  - Data Fetching : https://nextjs.org/blog/next-13#data-fetching

    - data fetch 시 react use hook을 함께 사용한다.

    - 컴포넌트 바깥에서 페칭해온 뒤 컴포넌트 내부에서 사용하면 된다.

    - data fetch 시 두번째 props를 사용하여 SSG, SSR, ISR를 모두 대체할 수 있다.

      - SSG(getStaticProps) : 빌드 시 딱 한번만 호출

        ```js
        fetch(URL, { cache: "force-cache" });
        ```

      - SSR(getServerSideProps) : 매 요청때마다 호출

        ```js
        fetch(URL, { cache: "no-store" });
        ```

      - ISR(getStaticProps + revalidate) : 빌드 시 호출한 뒤 revalidate 옵션에 설정 된 시간마다 호출

        ```js
        fetch(URL, { next: { revalidate: 10 } });
        ```

<br>

- 실습 내용

  - 공식 문서에도 나와있는 것처럼 app 디렉토리는 현재 베타버전으로 실제 프로젝트에 적용은 불가한 상태이다.

  - app 디렉토리는 트리 구조를 띄고 있다. (참고 : https://beta.nextjs.org/docs/routing/fundamentals#terminology)

  - app 디렉토리를 사용하기 위해서는 `experimental: { appDir: true }` 과 같은 옵션을 `next.config.js` 에 추가해주어야 한다.

  - app 디렉토리 생성 후 pages 디렉토리를 삭제하면 자동으로 `head.js`, `layout.js`, `page.js`가 생성된다.

  - app 디렉토리 내부에 디렉토리 생성 후 `page.js`를 생성하면 자동 라우팅이 적용되는 것을 확인해볼 수 있다. `page.js`가 이전 버전에 `index.js`를 대체한다고 보면 될 것 같다.

<br>
<br>

### # Introducing Turbopack (Alpha)

<br>

- Introducing Turbopack (Alpha) : https://nextjs.org/blog/next-13#introducing-turbopack-alpha

  - 웹팩 개발자가 vercel에서 러스트로 작성하였다.

  - 중복 연산을 방지해주는 터보레포 솔루션과 결합하여 웹팩보다 700배, vite보다 10배 빠르다.

  - 현재 실제 프로젝트에 적용하기에는 무리가 있으며 안정화 된 후에 사용하는 것이 좋을 것 같다.

  - 부정적 의견

    - 이미 esbuild도 충분히 엄청 빠른데 오버 엔지니어링이다.

    - 원래도 next.js는 vercel을 통해 배포하며 돈을 냈는데, 이 솔루션 때문에 돈 낼 이유가 또 생겼다.

    - 기존 아키텍처의 러스트 버전 재작성에 불과하다.

<br>
<br>

### # next/image

<br>

- next/image : https://nextjs.org/blog/next-13#nextimage

  - 이미지가 로드될 때 다른 UI가 밀리는 Layout Shift 현상이 발생하는데 이를 방지하기 위해 이미지의 width와 height를 설정해야만 한다. Next.js 13 버전에서는 이를 자동으로 처리해준다.

  - alt 속성이 필수 속성이 되었다.

  - 큰 변화없이 쉬워진 스타일 지정, 더 빨라진 lazy loading 등 기본 기능이 향상되었다.

<br>
<br>

### # next/font

<br>

- next/font : https://nextjs.org/blog/next-13#nextfont

  - 이미지와 동일하게 Layout Shift 현상 자동 처리

  - 구글 폰트 내장

  - 커스텀 폰트를 포함하여 글꼴을 자동으로 최적화

  - 개인 정보 보호 및 성능 향상을 위해 외부 네트워크 요청 제거

  - 모든 글꼴 파일에 대한 자체 호스팅

  - CSS 및 글꼴 파일은 빌드 시 다운로드되며 나머지 정적 파일과 함께 자체 호스팅을 지원

  - 사용 예시

    ```js
    // 구글 폰트 사용
    import { Inter } from "@next/font/google";

    const inter = Inter();
    <html className={inter.className}></html>;

    //  사용자 정의 글꼴
    import localFont from "@next/font/local";

    const myFont = localFont({ src: "./my-font.woff2" });
    <html className={myFont.className}></html>;
    ```

<br>
<br>

### # next/link

<br>

- next/link : https://nextjs.org/blog/next-13#nextlink

  - link 태그 내부에 a태그 사용하지 않아도 자동으로 a태그를 렌더링한다. 그렇기 때문에 link 태그에 바로 props를 전달하여 사용할 수 있다.

  - 사용 예시

    ```js
    import Link from 'next/link'

    // Next.js 12
    <Link href="/about">
      <a>About</a>
    </Link>

    // Next.js 13
    <Link href="/about">
      About
    </Link>
    ```

<br>
<br>

### # OG Image Generation

<br>

- OG Image Generation : https://nextjs.org/blog/next-13#og-image-generation

  - OG(Open Graph)란 콘텐츠가 표시되는 방식을 관리하기 위한 메타정보들을 정의해놓은 프로토콜이다. 주로 url로 공유할때 해당 콘텐츠의 요약내용이 보이도록 미리보기를 제공해준다.

  - @vercel/og 라이브러리를 사용하여 동적 소셜 카드를 새로 생성할 수 있다.

  - 기존 솔루션보다 5배 빠르다.

  - 사용 예시 : 아래와 같이 작성한 뒤 url을 공유하면 ImageResponse안에서 입력한 텍스트가 이미지로 바뀐다.

    ```js
    // pages/api/og.jsx
    import { ImageResponse } from "@vercel/og";

    export const config = {
      runtime: "experimental-edge",
    };

    export default function () {
      return new ImageResponse(
        (
          <div
            style={{
              fontSize: 128,
              background: "white",
              width: "100%",
              height: "100%",
              display: "flex",
              textAlign: "center",
              alignItems: "center",
              justifyContent: "center",
            }}
          >
            Hello world!
          </div>
        ),
        {
          width: 1200,
          height: 600,
        }
      );
    }
    ```

<br>
<br>

### # Middleware API Updates

<br>

- Middleware API Updates : https://nextjs.org/blog/next-13#middleware-api-updates

  - request에 대한 header를 더 쉽게 설정할 수 있다.

  - rewrite나 redirect를 사용할 필요 없이 직접 미들웨어에서 response를 제공할 수 있다. - 미들웨어에서 response를 제공하려면, next.config.js에 다음과 같은 코드를 추가해야한다.

    ```js
    const nextConfig = {
      ...
      experimental: {
        allowMiddlewareResponseBody: true
      },
    };
    ```

  - 사용 예시

    ```js
    // middleware.ts
    import { NextResponse } from "next/server";
    import type { NextRequest } from "next/server";

    export function middleware(request: NextRequest) {
      const requestHeaders = new Headers(request.headers);
      requestHeaders.set("x-version", "13");

      const response = NextResponse.next({
        request: {
          headers: requestHeaders,
        },
      });

      response.headers.set("x-version", "13");
      return response;
    }

    // middleware.ts
    import { NextRequest, NextResponse } from "next/server";
    import { isAuthenticated } from "@lib/auth";

    export const config = {
      matcher: "/api/:function*",
    };

    export function middleware(request: NextRequest) {
      if (!isAuthenticated(request)) {
        return NextResponse.json(
          {
            success: false,
            message: "Auth failed",
          },
          {
            status: 401,
          }
        );
      }
    }

    // next.config.js
    const nextConfig = {
      experimental: {
        allowMiddlewareResponseBody: true,
      },
    };
    ```

<br>
