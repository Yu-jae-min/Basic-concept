## # NextJs

# NextJs - 코딩앙마 강좌 2022.08.14

- create-next-app 으로 설치하면?

1. 컴파일과 번들링이 자동으로 된다. (webpack과 bable)
2. 자동 refresh 기능으로 수정하면 화면에 바로 반영된다. (yarn dev)
3. server side rendering이 지원된다.
4. static file을 지원한다.

- pages 디렉토리 하위에 js 파일 생성하면 정적 라우팅 기능 제공 (ex pages -> about.js 생성 : http://localhost:3000/about)

- pages 디렉토리 하위에 디렉토리 생성 후 `[id].js` 파일 생성하면 다이나믹 라우팅 기능 제공 (ex pages -> view -> `[id].js` : http://localhost:3000/view/3

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
