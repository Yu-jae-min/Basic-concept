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
