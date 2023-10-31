# [Next.js] Next 13 App Router Docs 정독 - Routing

2023년 10월 27일

<br>

# 1. [Routing](https://nextjs.org/docs/app/building-your-application/routing)

<br>

## 1-1. [Terminology](https://nextjs.org/docs/app/building-your-application/routing#terminology)

- 계층 구조 용어

  ![Next_13_App_Router_Docs_정독_Routing_01](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/37591387-25f2-43e5-a144-c94ce4d1ce65)

- URL 구조 (예 abc.com/dashboard/settings)

  - URL Segment: 슬래시로 구분된 URL 경로, 위에 dashboard 혹은 settings 모두가 URL 세그먼트

  - URL Path: 도메인 뒤에 오는 부분, 세그먼트로 구성되어있다. 위 예시중 도메인 abc.com 뒤 dashboard/settings가 URL 패쓰

<br>

## 1-2. [The `app` Router](https://nextjs.org/docs/app/building-your-application/routing#the-app-router)

- app 라우터와 page 라우터 둘 다 존재 시 app 라우터가 우선 순위가 높고 동일한 경로 존재 시 빌드 에러가 발생한다.

- 기본적으로 모든 컴포넌트는 서버 컴포넌트이다.

<br>

## 1-3. [Component Hierarch](https://nextjs.org/docs/app/building-your-application/routing#component-hierarchy)

- 예약 파일(특수 파일)은 특정 계층 구조로 렌더링된다.

  ![Next_13_App_Router_Docs_정독_Routing_02](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/e05575ce-07e9-4b6f-961e-8293696040e8)

- 중첩된 경우 세그먼트 구성 요소는 상위 세그먼트의 구성 요소 안에 중첩된다.

  ![Next_13_App_Router_Docs_정독_Routing_03](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/b8806bb3-2531-4501-a61a-31a3d067ff78)

<br>

## 1-4. [Colocation](https://nextjs.org/docs/app/building-your-application/routing#colocation)

- 프로젝트 디렉토리 구조는 기존과 같이 사용할 수 있다. URL에 매핑되는 파일은 page.js 혹은 route.js만 매핑되기 때문이다.

  ![Next_13_App_Router_Docs_정독_Routing_04](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/c9639cef-fed9-4f38-8e6e-59728d7deae3)

<br>
<br>

# 2. [Defining Routes](https://nextjs.org/docs/app/building-your-application/routing/defining-routes)

<br>

## 2-1. [Creating Routes](https://nextjs.org/docs/app/building-your-application/routing/defining-routes#creating-routes)

- Next.js는 파일 시스템 기반 라우터를 사용하며 폴더로 경로를 정의할 수 있다. 각 폴더는 URL 세그먼트에 매핑되는 경로 세그먼트를 나타낸다. 중첩된 경로를 만들기 위해 폴더를 중첩할 수 있다.

  ![Next_13_App_Router_Docs_정독_Routing_05](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/0e866eb5-f276-4d65-afda-d2308d7ed6b2)

<br>

## 2-2. [Creating UI](https://nextjs.org/docs/app/building-your-application/routing/defining-routes#creating-ui)

- 각 경로 세그먼트에 대한 UI를 생성하기 위해 특별한 파일 규칙이 사용된다. 가장 일반적인 것은 경로에 고유한 UI를 표시하는 페이지와 여러 경로에서 공유되는 UI를 표시하는 layout 파일이다.

<br>
<br>

# 3. [Pages and Layouts](https://nextjs.org/docs/app/building-your-application/routing/pages-and-layouts)

<br>

## 3-1. [Pages](https://nextjs.org/docs/app/building-your-application/routing/pages-and-layouts#pages)

- page.js 파일에서 컴포넌트를 내보내 페이지를 정의할 수 있다. 중첩 폴더를 사용하여 경로를 정의하고 page.js 파일을 사용하여 경로를 공개적으로 액세스할 수 있도록 한다.

  ```tsx
  export default function Page() {
    return <h1>Hello, Home page!</h1>;
  }
  ```

- page.js는 기본적으로 서버 컴포넌트이지만 클라이언트 컴포넌트로 설정할 수 있다.

<br>

## 3-2. [Layouts](https://nextjs.org/docs/app/building-your-application/routing/pages-and-layouts#layouts)

- 레이아웃은 여러 페이지 간에 공유되는 UI이다. 페이지 이동 시 레이아웃은 상태, 인터렉션 등을 유지하며 다시 렌더링되지 않는다.

- 레이아웃은 기본적으로 layout.js 파일에서 react 컴포넌트를 내보내 정의할 수 있다. 컴포넌트는 렌더링 중 자식 레이아웃(있는 경우) 또는 자식 페이지로 채워질 자식 프로퍼티를 받아야한다.

  ```tsx
  export default function DashboardLayout({
    children, // will be a page or nested layout
  }: {
    children: React.ReactNode;
  }) {
    return (
      <section>
        {/* Include shared UI here e.g. a header or sidebar */}
        <nav></nav>

        {children}
      </section>
    );
  }
  ```

- 가장 위에 있는 레이아웃을 루트 레이아웃이라고 한다. 애플리케이션의 모든 페이지에서 공유된다.

- 루트 레이아웃에는 HTML 및 본문 태그가 포함되어야 한다.

- 모든 경로 세그먼트는 자체 레이아웃을 정의할 수 있다. 자체 레이아웃은 해당 세그먼트 모든 페이지에서 공유된다.

- 경로의 레이아웃은 기본적으로 중첩된다. 각 부모 레이아웃은 children 프로퍼티를 사용해 그 아래의 자식 레이아웃을 감싸준다.

- Route Groups를 사용하여 공유 레이아웃 안팎에서 특정 경로 세그먼트를 선택할 수 있다. 즉 원하는 경로 세그먼트만 해당 레이아웃을 선택적으로 적용시킬 수 있다.

- 레이아웃은 기본적으로 서버 컴포넌트이지만 클라이언트 컴포넌트로 설정할 수 `있다`.

- 레이아웃은 일반 컴포넌트와 마찬가지로 데이터를 패칭할 수 있다.

- 부모 레이아웃과 자식 레이아웃 간에 데이터를 전달할 수 없다. 하지만 동일 경로에서 동일한 데이터를 중복 요청하는 경우 react는 성능에 영향을 주지 않고 자동으로 중복 요청을 제거한다.

- 레이아웃은 아래 경로 세그먼트에 접근할 수 없다. 모든 경로 세그먼트에 접근하려면 클라이언트 컴포넌트에서 `useSelectedLayoutSegment` 혹은 `useSelectedLayoutSegments` 를 사용하여 접근할 수 있다.

- layouy.js 파일과 page.js 파일은 같은 디렉토리에 정의할 수 있다. 레이아웃이 페이지를 감싸게 된다.

<br>

## 3-3. [Root Layout (Required)](https://nextjs.org/docs/app/building-your-application/routing/pages-and-layouts#root-layout-required)

- 루트 레이아웃은 앱 디렉터리 최상위 레벨에 정의되며 모든 경로에 적용된다. 루트 레이아웃을 사용하면 서버에서 반환된 초기 HTML을 수정할 수 있다.

  ```tsx
  export default function RootLayout({
    children,
  }: {
    children: React.ReactNode;
  }) {
    return (
      <html lang="en">
        <body>{children}</body>
      </html>
    );
  }
  ```

- app 디토리에 루트 레이아웃이 포함되어야 한다.

- Next.js가 자동으로 생성하지 않기 때문에 루트 레이아웃에 html 태그 및 body 태그를 정의해야한다.

- [기본 제공 SEO 서포트](https://nextjs.org/docs/app/building-your-application/optimizing/metadata)를 사용하여 head 태그 HTML 요소(ex title 태그)를 관리할 수 있다.

- Route Groups를 사용하여 여러 루트 레이아웃을 만들 수 있다. 즉 그룹별 루트 레이아웃을 설정할 수 있다.

- 루트 레이아웃은 기본적으로 서버 컴포넌트이며 클라이언트 컴포넌트로 설정할 수 `없다`.

- 루트 레이아웃이 page router에서 `_app.js` 및 `_document.js` 파일을 대체한다.

<br>

## 3-4. [Nesting Layouts](https://nextjs.org/docs/app/building-your-application/routing/pages-and-layouts#nesting-layouts)

- 디렉토리(예: app/dashboard/layout.js) 내에 정의된 레이아웃은 특정 경로 세그먼트(예: acme.com/dashboard)에 적용되며 해당 세그먼트가 활성화될 때 렌더링된다. 기본적으로 파일 계층 구조의 레이아웃은 중첩되어 있으므로 children 프로퍼티를 통해 하위 레이아웃을 감싸게 된다.

- 예를 들어 app에 있는 루트 레이아웃(예: `app/layout.js`)이 특정 디렉토리 내의 레이아웃(예: `app/dashboard/layout.js`)을 감싸고 특정 디렉토리 내의 레이아웃은 특정 디렉토리 내의 경로 세그먼트(예: `app/dashboard/*`)를 감싸게 된다.

  ![Next_13_App_Router_Docs_정독_Routing_06](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/08b76205-c78a-427c-9e90-457b688f49e4)

- 루트 레이아웃에만 html 태그 및 body 태그를 포함할 수 있다.

- Route Gropus를 사용하여 경로 세그먼트 별로 네스팅 레이아웃을 지정할 수 있다.

<br>

## 3-5. [Templates](https://nextjs.org/docs/app/building-your-application/routing/pages-and-layouts#templates)

- 템플릿은 각 하위 레이아웃 또는 페이지를 래핑한다는 점에서 레이아웃과 유사하다. 하지만 경로 전체에서 지속되고 상태를 유지하는 레이아웃과 달리 템플릿은 페이지 이동 시 각 하위 레이아웃에 대해 새 인스턴스를 생성한다. 즉 사용자가 템플릿을 공유하는 경로 사이를 이동할 때 컴포넌트의 새 인스턴스가 마운트되고, DOM 요소가 다시 생성되며, 상태가 보존되지 않고 효과가 다시 동기화된다.

- 예를 들어 useEffect 혹은 useState의 의존하는 기능은 레이아웃보다 템플릿이 더 적합할 수 있다.

- 기본 프레임워크 동작을 변경할 수도 있다. 예를 들어 레이아웃 내부의 서스펜스 바운더리는 레이아웃을 처음 로드할 때만 fallback을 표시하고 페이지를 전환할 때는 표시하지 않는다. 이 때 템플릿을 대신 사용하면 각 탐색에 fallback이 표시된다.

- template.js 파일을 통해 사용할 수 있다.

  ```tsx
  export default function Template({
    children,
  }: {
    children: React.ReactNode;
  }) {
    return <div>{children}</div>;
  }
  ```

- 중첩되는 측면에서 템플릿은 레이아웃과 그 자식 사이에 렌더링된다. 다음은 단순화 된 출력 결과이다.

  ```tsx
  <Layout>
    {/* Note that the template is given a unique key. */}
    <Template key={routeParam}>{children}</Template>
  </Layout>
  ```

<br>

## 3-6. [Modifying `<head>`](https://nextjs.org/docs/app/building-your-application/routing/pages-and-layouts#modifying-head)

- 앱 디렉토리에서 [기본 제공 SEO 서포트](https://nextjs.org/docs/app/building-your-application/optimizing/metadata)을 사용하여 제목 및 메타 등의 head 태그 HTML 요소를 수정할 수 있다.

- 메타데이터는 메타 데이터 객체(아래 예시)를 내보내거나 layout.js 또는 page.js 파일에서 generateMetadata 함수를 사용하여 정의할 수 있다. 메타 데이터 객체는 페이지가 정적인 경우 사용하고 generateMetadata 함수는 페이지가 동적(예 `app/products/[id]/page.jsx`)인 경우 사용한다.

  ```tsx
  // 메타 데이터 사용 : 메타 데이터 객체 (정적)
  import { Metadata } from "next";

  export const metadata: Metadata = {
    title: "Next.js",
  };

  export default function Page() {
    return "...";
  }
  ```

  ```tsx
  // 메타 데이터 사용 : generateMetadata 함수 사용 (동적)
  import { Metadata, ResolvingMetadata } from "next";

  type Props = {
    params: { id: string };
    searchParams: { [key: string]: string | string[] | undefined };
  };

  export async function generateMetadata(
    { params, searchParams }: Props,
    parent: ResolvingMetadata
  ): Promise<Metadata> {
    // read route params
    const id = params.id;

    // fetch data
    const product = await fetch(`https://.../${id}`).then((res) => res.json());

    // optionally access and extend (rather than replace) parent metadata
    const previousImages = (await parent).openGraph?.images || [];

    return {
      title: product.title,
      openGraph: {
        images: ["/some-specific-page-image.jpg", ...previousImages],
      },
    };
  }

  export default function Page({ params, searchParams }: Props) {}
  ```

- 루트 레이아웃에 title 태그 혹은 meta 태그와 같은 head 태그를 수동으로 추가해서는 안된다. 대신 head 요소의 스트리밍 및 중복 제거와 같은 고급 요구 사항을 자동으로 처리하는 [메타 데이터 API](https://nextjs.org/docs/app/api-reference/functions/generate-metadata)를 사용해야한다.

<br>
<br>

# 4. [Linking and Navigating](https://nextjs.org/docs/app/building-your-application/routing/linking-and-navigating)

- Next.js에서 경로 사이를 네비게이션하는 방법은 Link 컴포넌트를 사용하거나 useRouter Hook을 사용하는 두 가지 방법이 있다.

<br>

## 4-1. [`<Link>` Component](https://nextjs.org/docs/app/building-your-application/routing/linking-and-navigating#link-component)

- Link 컴포넌트는 a 태그를 확장하여 경로 간 프리페칭 및 클라이언트 사이드 라우팅(탐색)을 제공하는 기본 제공 컴포넌트이다.

  ```tsx
  import Link from "next/link";

  export default function Page() {
    return <Link href="/dashboard">Dashboard</Link>;
  }
  ```

- Link 컴포넌트에 전달할 수 있는 다른 optional props가 있다. (참고 URL : https://nextjs.org/docs/app/api-reference/components/link)

- [동적 세그먼트에 링크](https://nextjs.org/docs/app/building-your-application/routing/linking-and-navigating#linking-to-dynamic-segments)할 때 템플릿 리터럴 및 보간을 사용하여 링크 목록을 생성할 수 있다.

  ```tsx
  import Link from "next/link";

  export default function PostList({ posts }) {
    return (
      <ul>
        {posts.map((post) => (
          <li key={post.id}>
            <Link href={`/blog/${post.slug}`}>{post.title}</Link>
          </li>
        ))}
      </ul>
    );
  }
  ```

- `usePathname()`을 사용하여 링크가 활성 상태인지 확인할 수 있다. 예를 들어 활성 링크에 클래스를 추가하려면 현재 경로명이 링크의 href와 일치하는지 확인할 수 있다.

  ```tsx
  "use client";

  import { usePathname } from "next/navigation";
  import Link from "next/link";

  export function Links() {
    const pathname = usePathname();

    return (
      <nav>
        <ul>
          <li>
            <Link
              className={`link ${pathname === "/" ? "active" : ""}`}
              href="/"
            >
              Home
            </Link>
          </li>
          <li>
            <Link
              className={`link ${pathname === "/about" ? "active" : ""}`}
              href="/about"
            >
              About
            </Link>
          </li>
        </ul>
      </nav>
    );
  }
  ```

- Next.js App Router의 기본 동작은 새 경로의 상단으로 스크롤하거나 뒤로 및 앞으로 탐색을 위해 스크롤 위치를 유지시키는 것이다.

- 탐색 시 특정 ID로 스크롤하려면 `#`해시 링크를 URL에 추가하거나 해시링크를 href 속성에 전달할 수 있다. 이게 가능한 이유는 Link 컴포넌트가 a 태그로 렌더링되기 때문에 가능하다.

  ```tsx
  <Link href="/dashboard#settings">Settings</Link>

  // Output
  <a href="/dashboard#settings">Settings</a>
  ```

- Next.js 앱 라우터의 기본 동작은 새 경로의 상단으로 스크롤하거나 뒤로 및 앞으로 탐색을 위해 스크롤 위치를 유지하는 것이다. 이 동작을 비활성화하려면 Link 컴포넌트에 `scroll={false}`를 전달하거나, `router.push()` 또는 `router.replace()`에 `scroll: false`를 전달하면 된다.

  ```tsx
  // next/link
  <Link href="/dashboard" scroll={false}>
    Dashboard
  </Link>
  ```

  ```tsx
  // useRouter
  import { useRouter } from "next/navigation";

  const router = useRouter();

  router.push("/dashboard", { scroll: false });
  ```

<br>

## 4-2. [`useRouter()` Hook](https://nextjs.org/docs/app/building-your-application/routing/linking-and-navigating#userouter-hook)

- useRouter hook을 사용하면 프로그래밍 방식으로 경로를 변경할 수 있다.

- useRouter hook은 클라이언트 컴포넌트 내에서만 사용할 수 있다.

  ```tsx
  "use client";

  import { useRouter } from "next/navigation";

  export default function Page() {
    const router = useRouter();

    return (
      <button type="button" onClick={() => router.push("/dashboard")}>
        Dashboard
      </button>
    );
  }
  ```

- useRouter 관련 API 목록은 다음 [링크](https://nextjs.org/docs/app/api-reference/functions/use-router)에서 확인할 수 있다.

- useRouter를 사용해야하는 특별한 요구 사항이 있지 않은 경우 Link 컴포넌트를 사용하는 것이 좋다.

<br>

## 4-3. [How Routing and Navigation Works](https://nextjs.org/docs/app/building-your-application/routing/linking-and-navigating#how-routing-and-navigation-works)

- App Router는 라우팅 및 탐색에 하이브리드 접근 방식을 사용한다. 서버에서는 애플리케이션 코드가 경로 세그먼트별로 자동으로 코드 스플리팅된다. 그리고 클라이언트에서는 Next.js가 경로 세그먼트를 프리페치하고 캐싱한다. 즉, 사용자가 새 경로로 이동할 때 브라우저가 페이지를 새로고침하지 않고 변경된 경로 세그먼트만 다시 렌더링하여 내비게이션 환경과 성능을 개선한다.

<br>

### 4-3-1. [Prefetching](https://nextjs.org/docs/app/building-your-application/routing/linking-and-navigating#1-prefetching)

- 프리페칭은 사용자가 경로를 방문하기 전 백그라운드에서 경로를 미리 로드하는 방법이다.

- Next.js에서 경로를 프리페치하는 방법에는 두 가지가 있다.

  - `Link 컴포넌트` : 경로는 사용자의 뷰포트에 표시될 때 자동으로 프리페칭된다. 프리페칭은 페이지가 처음 로드될 때 또는 스크롤을 통해 페이지가 시야에 들어올 때 발생한다.

  - `router.prefetch()` : useRouter hook을 사용하면 프로그래밍 방식으로 경로를 프리페칭할 수 있다. 프리페칭을 위해 useRouter 리턴 객체의 메소드인 prefetch를 사용한다.

- Link 컴포넌트의 프리페칭 동작은 정적 경로와 동적 경로에 따라 다르다.

  - 정적 경로 : 프리페치가 기본적으로 true이며 모든 경로가 프리페치되고 캐시됨다.

  - 동적 경로 : 프리페치가 기본적으로 automatic이며 첫 번째 loading.js 파일이 프리페치되고 30초 동안 캐시될 때까지 공유 레이아웃만 다운된다. 이렇게 하면 전체 동적 경로를 가져오는 비용이 줄고 로딩 화면을 표시함으로서 사용자에게 더 나은 시각적 피드백을 제공할 수 있다.

- Link 컴포넌트의 프리페치는 프로덕션 모드에서만 활성화된다.

- [Link 컴포넌트 API](https://nextjs.org/docs/app/api-reference/components/link)

<br>

### 4-3-2. [Caching](https://nextjs.org/docs/app/building-your-application/routing/linking-and-navigating#2-caching)

- Next.js에는 라우터 캐시라는 인메모리 클라이언트 측 캐시가 있다. 사용자가 앱을 탐색할 때 미리 가져온 경로 세그먼트와 방문한 경로의 React 서버 컴포넌트 페이로드가 캐시에 저장된다. 즉 페이지 이동 시 서버에 새로운 요청을 하는 대신 캐시를 최대한 재사용하여 요청 및 데이터 전송 횟수를 줄여 성능을 개선한다.

- 라우터 캐시의 작동 방식과 구성 방법 : https://nextjs.org/docs/app/building-your-application/data-fetching/fetching-caching-and-revalidating#caching-data

<br>

### 4-3-3. [Partial Rendering](https://nextjs.org/docs/app/building-your-application/routing/linking-and-navigating#3-partial-rendering)

- 부분 렌더링은 내비게이션에서 변경되는 경로 구간만 클라이언트에서 다시 렌더링하는 것을 의미한다. 모든 공유 구간은 유지된다. 예를 들어 /dashboard/settings와 /dashboard/analytics 경로에 컴포넌트들이 있을 때 setting 페이지에서 analytics 페이지로 전환한다고 했을 때 dashboard 하위 컴포넌트가 공유하는 layout.tsx 부분은 유지되며 analytics 컴포넌트만 부분 렌더링된다. 전체 페이지를 다시 렌더링하는 것이 아니기 때문에 서버 비용과 렌더링 비용이 감소한다.

  ![Next_13_App_Router_Docs_정독_Routing_07](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/71cf882c-49d7-4818-9a3d-fff0de78407c)

<br>

### 4-3-4. [Soft Navigation](https://nextjs.org/docs/app/building-your-application/routing/linking-and-navigating#4-soft-navigation)

- 기본적으로 브라우저는 페이지 간 하드 네비게이션을 수행한다. 즉, 브라우저는 페이지를 다시 로드하고 앱의 사용 상태 후크와 같은 React 상태와 사용자의 스크롤 위치 또는 포커싱된 요소와 같은 브라우저 상태를 재설정한다. 하지만 Next.js에서 앱 라우터는 소프트 내비게이션을 사용한다. 즉, React는 React와 브라우저 상태를 유지하면서 변경된 세그먼트만 렌더링하며 전체 페이지를 다시 로드하지 않는다.

<br>

### 4-3-5. [Back and Forward Navigation](https://nextjs.org/docs/app/building-your-application/routing/linking-and-navigating#5-back-and-forward-navigation)

- 기본적으로 Next.js는 뒤로 및 앞으로 탐색을 위한 스크롤 위치를 유지하고 라우터 캐시에서 경로 세그먼트를 재사용한다.

<br>
<br>

# 5. [Route Groups](https://nextjs.org/docs/app/building-your-application/routing/route-groups)

- 일반적으로 app내의 디렉토리는 URL에 매핑되지만 Route Group을 사용하면 관련 페이지를 그룹으로 묶어 사용할 수 있다. Route Group으로 작성된 디렉토리는 URL에 매핑되지 않고 그룹을 나눌 때 사용할 수 있다.

<br>

## 5-1. [Convention](https://nextjs.org/docs/app/building-your-application/routing/route-groups#convention)

- 디렉토리 이름을 괄호로 묶어 라우트 그룹을 만들 수 있다. (ex `(folderName)`)

<br>

## 5-2. [Examples](https://nextjs.org/docs/app/building-your-application/routing/route-groups#examples)

<br>

### 5-2-1. [Organize routes without affecting the URL path](https://nextjs.org/docs/app/building-your-application/routing/route-groups#organize-routes-without-affecting-the-url-path)

- URL에 영향을 주지 않고 경로를 정리하려면 라우트 그룹을 만들어 보관할 수 있다.

  ![Next_13_App_Router_Docs_정독_Routing_08](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/70768926-82a7-4d9e-a11f-1f4f9e1dab46)

- ()로 나누어진 그룹은 그룹 내에서만 사용하는 layout.js를 사용할 수 있다. 그룹이 다르거나 그룹 외부 컴포넌트는 해당 레이아웃을 공유할 수 없다.

  ![Next_13_App_Router_Docs_정독_Routing_09](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/26d46adb-5778-408b-949a-afc67ec2751f)

<br>

### 5-2-2. [Creating multiple root layouts](https://nextjs.org/docs/app/building-your-application/routing/route-groups#creating-multiple-root-layouts)

- 여러 LootLayout을 생성하려면 최상위 layout.js 파일을 제거하고 각 경로 그룹 내에 layout.js 파일을 추가한다. 이는 완전히 다른 UI나 경험을 가진 섹션으로 애플리케이션을 분할하는 데 유용하다. html 태그 및 body 태그를 각 루트 레이아웃에 추가해야 한다. (html 및 body는 루트 레이아웃에만 존재할 수 있으며 존재해야한다.) 즉 그룹별 자체 루트 레이아웃을 적용시키는 것이다. 아래 예시에서 marketing 라우트 그룹과 shop 라우트 그룹은 모두 자체 루트 레이아웃을 가지고 있다.

  ![Next_13_App_Router_Docs_정독_Routing_10](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/af3cd18f-2a11-4620-a438-33bacf5ec7f7)

- 라우트 그룹은 그룹을 나누기 위해서만 사용되며 특별한 의미는 없다. URL 경로에는 영향을 미치지 않는다.

- 라우트 그룹을 포함하는 경로는 다른 경로와 동일한 URL 경로로 해석되어서는 안된다. 예를 들어 경로 그룹은 URL 구조에 영향을 주지 않으므로 (marketing)/about/page.js 및 (shop)/about/page.js는 모두 /about으로 확인되어 오류를 발생시킨다.

- 최상위 layout.js 파일 없이 여러 루트 레이아웃을 사용하는 경우 메인이 되는 page.js 파일은 경로 그룹 중 하나에 정의되어야 한다. (예: app/(marketing)/page.js).

- 라우트 그룹을 사용할 때 그룹별 별도의 루트 레이아웃을 사용하는 경우 그룹이 다른 페이지로 페이지 전환 시 클라이언트 사이드 렌더링이 아닌 전체 렌더링이 발생한다.

<br>
<br>

# 6. [Dynamic Routes](https://nextjs.org/docs/app/building-your-application/routing/dynamic-routes)

- 정확한 세그먼트 이름을 미리 알지 못하고 동적 데이터로 경로를 생성하려는 경우 요청 시 채워지거나 빌드 시 미리 렌더링되는 동적 세그먼트를 사용할 수 있다.

<br>

## 6-1. [Convention](https://nextjs.org/docs/app/building-your-application/routing/dynamic-routes#convention)

- 동적 세그먼트는 폴더 이름을 대괄호로 묶어 만들 수 있다:(예: `[id]` 또는 `[slug]`)

- 동적 세그먼트는 레이아웃, 페이지, 라우트 및 생성 메타데이터 함수에 매개변수로 전달된다.

<br>

## 6-2. [Example](https://nextjs.org/docs/app/building-your-application/routing/dynamic-routes#example)

- 예를 들어 블로그에는 다음과 같은 경로 `app/blog/[slug]/page.js`가 포함될 수 있으며, 여기서 `[slug]`는 블로그 게시물의 동적 세그먼트다.

  ```tsx
  // app/blog/[slug]/page.tsx
  export default function Page({ params }: { params: { slug: string } }) {
    return <div>My Post: {params.slug}</div>;
  }
  ```

- app/blog/[slug]/page.js의 경우 /blog/a는 `{ slug: 'a' }`, /blog/b는 `{ slug: 'b' }`, /blog/c는 `{ slug: 'c' }`가 된다.

- 세그먼트에 대한 파라미터를 생성하는 방법은 [generateStaticParams()](https://nextjs.org/docs/app/building-your-application/routing/dynamic-routes#generating-static-params) 를 참조한다.

<br>

## 6-3. [Generating Static Params](https://nextjs.org/docs/app/building-your-application/routing/dynamic-routes#generating-static-params)

- generateStaticParams 함수는 동적 경로 세그먼트와 함께 사용하여 요청 시 온디맨드가 아닌 빌드 시점에 경로를 정적으로 생성할 수 있다.

  ```tsx
  export async function generateStaticParams() {
    const posts = await fetch("https://.../posts").then((res) => res.json());

    return posts.map((post) => ({
      slug: post.slug,
    }));
  }
  ```

- generateStaticParams 함수의 가장 큰 장점은 데이터를 스마트하게 검색할 수 있다는 점이다. 가져오기 요청을 사용하여 generateStaticParams 함수 내에서 콘텐츠를 가져오면 요청이 자동으로 메모화된다. 즉, 여러 generateStaticParams, 레이아웃 및 페이지에 걸쳐 동일한 인수가 포함된 가져오기 요청은 한 번만 수행되므로 빌드 시간이 단축된다.

- 자세한 정보는 해당 URL에서 확인 : https://nextjs.org/docs/app/api-reference/functions/generate-static-params

<br>

## 6-4. [Catch-all Segments](https://nextjs.org/docs/app/building-your-application/routing/dynamic-routes#catch-all-segments)

- 동적 세그먼트는 괄호 안에 줄임표를 추가하여 `[...폴더이름]` 안에 모든 후속 세그먼트를 포함하도록 확장할 수 있다.

- 예를 들어 `app/shop/[...slug]/page.js`는 `/shop/clothes` 뿐만 아니라 `/shop/clothes/tops`, `/shop/clothes/tops/t-shirts` 등과도 일치한다.
  | Route | Example URL | params |
  | -------------------------- | ----------- | ------------------------- |
  | `app/shop/[...slug]/page.js` | /shop/a | { slug: ['a'] } |
  | `app/shop/[...slug]/page.js` | /shop/a/b | { slug: ['a', 'b'] } |
  | `app/shop/[...slug]/page.js` | /shop/a/b/c | { slug: ['a', 'b', 'c'] } |

<br>

## 6-5. [Optional Catch-all Segments](https://nextjs.org/docs/app/building-your-application/routing/dynamic-routes#optional-catch-all-segments)

- 옵셔널 캐치올 세그먼트는 매개 변수를 이중 대괄호 안(`[[...folderName]]`)에 포함하여 선택 사항으로 만들 수 있다.

- 예를 들어 `app/shop/[[...slug]]/page.js`는 `/shop/clothes`, `/shop/clothes/tops`, `/shop/clothes/tops/t-shirts` 외에 `/shop`과도 일치한다.

- 캐치올 세그먼트와 옵셔널 캐치올 세그머트의 차이점은 옵셔널 캐치올 세그먼트를 사용하면 매개변수가 없는 경로도 일치한다는 점이다.

  | Route                          | Example URL | params                    |
  | ------------------------------ | ----------- | ------------------------- |
  | `app/shop/[[...slug]]/page.js` | /shop       | {}                        |
  | `app/shop/[[...slug]]/page.js` | /shop/a     | { slug: ['a'] }           |
  | `app/shop/[[...slug]]/page.js` | /shop/a/b   | { slug: ['a', 'b'] }      |
  | `app/shop/[[...slug]]/page.js` | /shop/a/b/c | { slug: ['a', 'b', 'c'] } |

<br>

## 6-6. [TypeScript](https://nextjs.org/docs/app/building-your-application/routing/dynamic-routes#typescript)

- TypeScript를 사용하는 경우 구성된 경로 세그먼트에 따라 매개변수에 대한 유형을 추가할 수 있다.

  ```tsx
  export default function Page({ params }: { params: { slug: string } }) {
    return <h1>My Page</h1>;
  }
  ```

  | Route                               | params Type Definition                 |
  | ----------------------------------- | -------------------------------------- |
  | `app/blog/[slug]/page.js`           | { slug: string }                       |
  | `app/shop/[...slug]/page.js`        | { slug: string[] }                     |
  | `app/[categoryId]/[itemId]/page.js` | { categoryId: string, itemId: string } |

<br>
<br>

# 7. [Loading UI and Streaming](https://nextjs.org/docs/app/building-your-application/routing/loading-ui-and-streaming)

- 특수 파일 loading.js를 사용하면 React Suspense로딩 UI를 만들 수 있다. 이 규칙을 사용하면 경로 세그먼트의 콘텐츠가 로드되는 동안 서버에서 즉각적인 로딩 상태를 표시할 수 있다. 렌더링이 완료되면 새 콘텐츠가 자동으로 교체된다.

<br>

## 7-1. [Instant Loading States](https://nextjs.org/docs/app/building-your-application/routing/loading-ui-and-streaming#instant-loading-states)

- 즉시 로딩 상태는 탐색 시 즉시 표시되는 폴백 UI이다. 스켈레톤, 스피너와 같은 로딩 표시기를 미리 렌더링하거나 표지 사진, 제목 등과 같이 향후 화면에서 작지만 의미 있는 부분을 미리 렌더링할 수 있다. 이를 통해 사용자가 앱이 응답하고 있음을 이해하고 더 나은 사용자 경험을 제공할 수 있다.

- 폴더 내에 loading.js 파일을 추가하여 로딩 상태를 생성한다.

- 같은 폴더에서 loading.js는 layout.js 안에 중첩된다. 그러면 page.js 파일과 그 아래의 모든 하위 파일이 Suspense 컴포넌트 경계로 자동 래핑된다.

  ![Next_13_App_Router_Docs_정독_Routing_10](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/397150ac-b9e2-458c-8b46-e941165e7c94)

- 서버 중심 라우팅을 사용하더라도 즉각적인 탐색이 가능하다.

- 네비게이션(페이지 전환)은 중단할 수 있으므로 경로를 변경할 때 다른 경로로 이동하기 전에 경로의 컨텐츠가 완전히 로드될 때까지 기다릴 필요가 없다.

- 새 경로 세그먼트가 로드되는 동안 공유 레이아웃은 대화형 상태로 유지된다.

<br>

## 7-2. [Streaming with Suspense](https://nextjs.org/docs/app/building-your-application/routing/loading-ui-and-streaming#streaming-with-suspense)

- `loading.js`를 외에도 자체 UI 컴포넌트에 대해 Suspense 바운더리를 수동으로 생성할 수 있다. App Router는 Node.js 및 Edge 런타임 모두에 대해 Suspense를 사용한 스트리밍을 지원한다.

<br>

### 7-2-1. [What is Streaming?](https://nextjs.org/docs/app/building-your-application/routing/loading-ui-and-streaming#what-is-streaming)

- 기존 SSR은 다음과 같이 동작한다.

  - (1) 먼저 특정 페이지의 모든 데이터를 서버에서 가져온다.

  - (2) 그런 다음 서버에서 페이지의 HTML을 렌더링한다.

  - (3) 페이지의 HTML, CSS 및 JavaScript가 클라이언트로 전송된다.

  - (4) 생성된 HTML과 CSS를 사용해 비대화형(non-interactive) 사용자 인터페이스가 표시된다.

  - (5) 마지막으로 React는 사용자 인터페이스에 수분을 공급(hydrates)하여 대화형(interactive) 인터페이스로 만든다.

    ![Next_13_App_Router_Docs_정독_Routing_11](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/8fd40f8a-17e7-4202-a7c9-0f2aa629c9a7)

- 위와 같은 단계는 순차적이고 차단적이므로 서버는 모든 데이터를 가져온 후에만 페이지의 HTML을 렌더링할 수 있다. 그리고 클라이언트에서는 페이지의 모든 컴포넌트에 대한 코드가 다운로드 된 후에야 React가 UI에 수분을 공급(hydrates)할 수 있다.

  ![Next_13_App_Router_Docs_정독_Routing_12](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/a2035ac1-889d-497c-b249-7335bd5079d3)

- 이러한 단점에도 SSR을 사용했던 이유는 사용자에게 비대화형 페이지를 최대한 빨리 보여줌으로서 체감 로딩 성능을 개선하려고 했다.

- 하지만 사용자에게 페이지를 표시하기 전에 서버에서 모든 데이터 가져오기를 완료해야 하므로 여전히 느릴 수 있다.

- `스트리밍`을 사용하면 페이지의 HTML을 더 작은 청크로 나누고 해당 청크를 서버에서 클라이언트로 점진적으로 전송할 수 있다. 이렇게 하면 UI가 렌더링되기 전에 모든 데이터가 로드될 때까지 기다리지 않고 페이지의 일부를 더 빨리 표시할 수 있다.

  ![Next_13_App_Router_Docs_정독_Routing_13](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/2fe03d74-e2a9-4470-8ab8-d788acd59b6a)

- 스트리밍은 각 컴포넌트를 하나의 청크로 간주한다. 우선순위가 높거나(예: 제품 정보) 데이터에 의존하지 않는 컴포넌트를 먼저 전송할 수 있고 React의 하이드레이션을 더 일찍 시작할 수 있다. 우선순위가 낮은(예: 리뷰, 관련 제품) 컴포넌트는 데이터를 가져온 후 동일한 서버 요청으로 전송할 수 있다.

- 스트리밍은 긴 데이터 요청으로 인해 페이지 렌더링이 차단되는 것을 방지할 때 특히 유용하다. 스트리밍은 [Time To First Byte (TTFB)](https://web.dev/ttfb/)와 [First Contentful Paint (FCP)](https://web.dev/first-contentful-paint/)를 줄일 수 있기 때문이다. 또한 특히 느린 디바이스에서 [Time to Interactive (TTI)](https://developer.chrome.com/en/docs/lighthouse/performance/interactive/)를 개선하는데 도움이 된다.

  ![Next_13_App_Router_Docs_정독_Routing_14](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/3fdcdc72-7184-40fc-bae2-02868a17a971)

<br>

### 7-2-2. [Example](https://nextjs.org/docs/app/building-your-application/routing/loading-ui-and-streaming#example)

- Suspense 컴포넌트는 비동기 액션을 수행하는 컴포넌트를 래핑하고 액션이 진행되는 동안 fallback UI(예: 스켈레톤, 스피너)를 표시한 다음 액션이 완료되면 컴포넌트를 교체한다.

  ```tsx
  import { Suspense } from "react";
  import { PostFeed, Weather } from "./Components";

  export default function Posts() {
    return (
      <section>
        <Suspense fallback={<p>Loading feed...</p>}>
          <PostFeed />
        </Suspense>
        <Suspense fallback={<p>Loading weather...</p>}>
          <Weather />
        </Suspense>
      </section>
    );
  }
  ```

- Suspense를 사용 시 이점

  - 스트리밍 서버 렌더링을 통해 HTML을 점진적으로 렌더링한다.

  - React는 사용자 상호작용에 따라 어떤 컴포넌트를 먼저 인터렉티브하게 만들지 우선순위를 정해 선택적으로 하이드레이션을 진행한다.

<br>

### 7-2-3. [SEO](https://nextjs.org/docs/app/building-your-application/routing/loading-ui-and-streaming#seo)

- Next.js는 클라이언트에 UI를 스트리밍하기 전에 `[generateMetadata](https://nextjs.org/docs/app/api-reference/functions/generate-metadata)` 내부에서 데이터 가져오기가 완료될 때까지 기다린다 이렇게 하면 스트리밍된 응답의 첫 부분에 head 태그가 포함되도록 보장한다.

- 스트리밍은 서버에서 렌더링되므로 SEO에 영향을 미치지 않는다. Google의 [Mobile Friendly Test](https://search.google.com/test/mobile-friendly) 도구를 사용하여 Google의 웹 크롤러에 페이지가 어떻게 표시되는지 확인하고 직렬화된 HTML([소스](https://web.dev/rendering-on-the-web/#seo-considerations))을 볼 수 있다.

<br>

### 7-2-4. [Status Codes](https://nextjs.org/docs/app/building-your-application/routing/loading-ui-and-streaming#status-codes)

- 스트리밍할 때 요청이 성공했음을 알리는 200 상태 코드가 반환된다.

- 서버는 [redirect](https://nextjs.org/docs/app/api-reference/functions/redirect) 또는 [notFound](https://nextjs.org/docs/app/api-reference/functions/not-found) 등을 사용하여 스트리밍된 컨텐츠 자체 내에서 오류나 문제를 클라이언트에 전달할 수 있다. 응답 헤더가 이미 클라이언트에 전송되었으므로 응답의 상태 코드는 업데이트할 수 없고 이는 SEO에 영향을 미치지 않는다.

<br>
<br>

# 8. [Error Handling](https://nextjs.org/docs/app/building-your-application/routing/error-handling)

- `error.js`를 사용하면 중첩된 경로(예 app/dashboard/settings)에서 예기치 않은 런타임 오류를 우아하게 처리할 수 있다.

  - 경로 세그먼트와 그 중첩된 자식들을 [React Error Boundary](https://react.dev/reference/react/Component#catching-rendering-errors-with-an-error-boundary)에서 자동으로 래핑한다.

  - 파일 시스템 계층 구조를 사용하여 특정 세그먼트에 맞춘 오류 UI를 생성하여 세분성을 조정할 수 있다.

  - 애플리케이션의 나머지 기능은 유지하면서 영향을 받는 세그먼트에 대한 오류를 격리한다.

  - 전체 페이지를 다시 로드하지 않고 오류에서 복구를 시도하는 기능을 추가한다.

- 경로 세그먼트 내에 error.js 파일을 추가하고 React 컴포넌트를 내보내서 오류 UI를 생성한다.

  ![Next_13_App_Router_Docs_정독_Routing_15](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/99ee11ca-1fca-4fbb-92d1-ead2765441f2)

  ```tsx
  // app/dashboard/error.tsx
  "use client"; // Error components must be Client Components

  import { useEffect } from "react";

  export default function Error({
    error,
    reset,
  }: {
    error: Error & { digest?: string };
    reset: () => void;
  }) {
    useEffect(() => {
      // Log the error to an error reporting service
      console.error(error);
    }, [error]);

    return (
      <div>
        <h2>Something went wrong!</h2>
        <button
          onClick={
            // Attempt to recover by trying to re-render the segment
            () => reset()
          }
        >
          Try again
        </button>
      </div>
    );
  }
  ```

<br>

## 8-1. [How `error.js` Works](https://nextjs.org/docs/app/building-your-application/routing/error-handling#how-errorjs-works)

![Next_13_App_Router_Docs_정독_Routing_16](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/9c6e22a5-4d8d-491a-80d8-2df0e61941a8)

- error.js는 중첩된 자식 세그먼트 또는 page.js 컴포넌트를 감싸는 React Error Boundary를 자동으로 생성한다.

- error.js 파일에서 내보낸 React 컴포넌트가 fallback 컴포넌트로 사용된다.

- 에러 경계 내에서 에러가 발생하면 에러가 포함되고 fallback 컴포넌트가 렌더링된다.

- fallback 에러 컴포넌트가 활성화되면 에러 경계 위의 레이아웃은 해당 상태를 유지하고 대화형 상태를 유지하며 오류 컴포넌트는 오류를 복구하는 기능을 표시할 수 있다.

<br>

## 8-2. [Recovering From Errors](https://nextjs.org/docs/app/building-your-application/routing/error-handling#recovering-from-errors) (오류 복구)

- 오류의 원인은 일시적인 것일 수 있다. 이러한 경우 다시 시도하면 문제가 해결될 수 있다.

- 에러 컴포넌트는 `reset()` 함수를 사용하여 사용자에게 에러 복구를 시도하라는 메세지를 표시할 수 있다. 이 함수가 실행되면 Error Boundary 내의 컨텐츠를 다시 렌더링하려고 시도한다. 에러 복구가 성공하면 fallback 에러 컴포넌트가 다시 렌더링한 결과로 대체된다.

  ```tsx
  "use client";

  export default function Error({
    error,
    reset,
  }: {
    error: Error & { digest?: string };
    reset: () => void;
  }) {
    return (
      <div>
        <h2>Something went wrong!</h2>
        <button onClick={() => reset()}>Try again</button>
      </div>
    );
  }
  ```

<br>

## 8-3. [Nested Routes](https://nextjs.org/docs/app/building-your-application/routing/error-handling#nested-routes)

- 특수 파일(예: layout, loading, error 등)을 통해 생성된 React 컴포넌트는 특정 중첩 계층 구조로 렌더링된다.

- 예를 들어 layout.js 파일과 error.js 파일이 모두 포함된 두 개의 세그먼트가 있는 중첩된 경로는 다음과 같은 단순화된 컴포넌트 계층 구조로 렌더링된다.

  ![Next_13_App_Router_Docs_정독_Routing_17](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/7c14d8d5-087f-4a76-81f4-792b9f78af13)

- 중첩된 컴포넌트 계층 구조는 중첩된 경로에서 error.js 파일의 동작에 영향을 미친다.

  - 컴포넌트의 에러는 가까운 상위 에러 바운더리까지 퍼진다. 즉 error.js 파일은 중첩된 모든 하위 세그먼트에 대한 에러를 처리한다. 경로의 중첩된 디렉토리에 error.js 파일을 서로 다른 레벨에 배치하면 어느 정도 세분화된 에러 UI를 구현할 수 있다.

  - 에러 바운더리가 해당 레이아웃의 컴포넌트 안에 중첩되어 있기 때문에 error.js 경계는 동일한 세그먼트의 layout.js 컴포넌트에서 발생한 오류를 처리하지 못한다.

<br>

## 8-4. [Handling Errors in Layouts](https://nextjs.org/docs/app/building-your-application/routing/error-handling#handling-errors-in-layouts) (레이아웃에서 오류 처리하기)

- error.js 경계는 같은 세그먼트(디렉토리)의 layout.js 또는 template.js 컴포넌트에서 발생한 오류를 포착하지 않는다. 이 의도적인 계층 구조는 오류가 발생했을 때 형제 경로(예: 네비게이션) 간에 공유되는 중요한 UI가 계속 표시되고 작동하도록 하기 위함이다.

- 특정 레이아웃 또는 템플릿 내에서 오류를 처리하려면 레이아웃 상위 세그먼트에 error.js 파일을 배치한다.

- 루트 레이아웃 또는 템플릿 내에서 오류를 처리하려면 `global-error.js`라는 error.js의 변형을 사용한다.

<br>

## 8-5. [Handling Errors in Root Layouts](https://nextjs.org/docs/app/building-your-application/routing/error-handling#handling-errors-in-root-layouts) (루트 레이아웃에서 오류 처리하기)

- 루트 app/error.js 바운더리는 루트 app/layout.js 또는 app/template.js 컴포넌트에서 발생한 오류를 처리하지 못한다.

- 이러한 루트 컴포넌트의 에러를 구체적으로 처리하려면 루트 앱 디렉터리에 있는 `app/global-error.js`라는 error.js의 변형을 사용해야한다.

- 루트 error.js와 달리 global-error.js 에러 바운더리는 전체 애플리케이션을 감싸며, 해당 fallback 컴포넌트가 활성화되면 루트 레이아웃을 대체한다. 따라서 global-error.js는 자체 html 태그 및 body 태그를 정의해야 한다는 점에 유의해야 한다. (이유는 루트 레이아웃에는 html 태그 및 body 태그를 포함하는데 여기서 에러가 발생하는 경우 html 태그 및 body 태그를 대체해야하기 때문인 것 같다.)

- global-error.js는 가장 세분화된 에러 UI이며 전체 애플리케이션에 대한 "포괄적인" 에러 처리로 간주할 수 있다. 루트 컴포넌트는 일반적으로 덜 동적이며 다른 error.js 바운더리가 대부분의 에러를 포착하므로 자주 트리거 되지 않을 가능성이 높다.

- global-error.js가 정의되어 있더라도 전역적으로 공유되는 UI 및 브랜딩을 포함하는 루트 레이아웃 내에서 렌더링 될 폴백 컴포넌트가 있는 루트 error.js를 정의하는 것이 좋다.

```tsx
// app/global-error.tsx
"use client";

export default function GlobalError({
  error,
  reset,
}: {
  error: Error & { digest?: string };
  reset: () => void;
}) {
  return (
    <html>
      <body>
        <h2>Something went wrong!</h2>
        <button onClick={() => reset()}>Try again</button>
      </body>
    </html>
  );
}
```

<br>

## 8-6. [Handling Server Errors](https://nextjs.org/docs/app/building-your-application/routing/error-handling#handling-server-errors) (서버 에러 처리)

- 서버 컴포넌트 내부에서 오류가 발생하면 Next.js는 프로덕션 환경에서 민감한 오류 정보가 제거된 오류 객체를 가장 가까운 error.js 파일의 error 프로퍼티로 전달한다.

- [Securing Sensitive Error Information](https://nextjs.org/docs/app/building-your-application/routing/error-handling#securing-sensitive-error-information) (민감한 오류 정보 보호)

  - 프로덕션 중에 클라이언트에 전달되는 오류 개체에는 일반 메시지와 다이제스트 속성만 포함된다.

  - 이는 오류에 포함된 잠재적으로 민감한 세부 정보가 클라이언트에 유출되지 않도록 하기 위한 보안 예방 조치이다.

  - 메시지 속성에는 오류에 대한 일반 메시지가 포함되며, 다이제스트 속성에는 서버 측 로그에서 해당 오류와 일치하는 데 사용할 수 있는 오류의 자동 생성된 해시가 포함된다.

  - 개발 중에 클라이언트로 전달되는 오류 객체는 직렬화되며 디버깅을 쉽게 할 수 있도록 원래 오류의 메시지를 포함한다.

<br>
<br>

# 9. [Parallel Routes](https://nextjs.org/docs/app/building-your-application/routing/parallel-routes)

- 병렬 라우팅(Parallel Routing)을 사용하면 동일한 레이아웃이나 하나 이상의 페이지를 동시에 또는 조건부로 렌더링할 수 있다. 소셜 사이트의 대시보드 및 피드와 같이 앱에서 매우 동적인 섹션의 경우 병렬 라우팅을 사용하여 복잡한 라우팅 패턴을 구현할 수 있다.

- 예를 들어 팀 페이지와 분석 페이지를 동시에 렌더링할 수 있다.

  ![Next_13_App_Router_Docs_정독_Routing_18](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/02351e54-a8e9-4145-aae8-669572d8d49a)

- 병렬 라우팅을 사용하면 각 경로가 독립적으로 스트리밍 될 때 각 경로에 대해 독립적인 에러 및 로딩 상태를 정의할 수 있다.

  ![Next_13_App_Router_Docs_정독_Routing_19](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/7eff656d-b0ff-41bb-bf62-5d7c9ff550cd)

- 병렬 라우팅을 사용하면 인증 상태와 같은 특정 조건에 따라 조건부로 슬롯을 렌더링할 수도 있다. 이를 통해 동일한 URL에서 완전히 분리된 코드를 사용할 수 있다.

  ![Next_13_App_Router_Docs_정독_Routing_20](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/3982bddd-e7ff-49d5-af09-965c7f1317d5)

<br>

## 9-1. [Convention](https://nextjs.org/docs/app/building-your-application/routing/parallel-routes#convention)

<br>
