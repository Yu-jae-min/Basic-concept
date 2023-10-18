# [Next.js] Next 13 RSC vs SSR

2023년 10월 18일

<br>

# 1. 렌더링 방식의 변화

최근 렌더링 방식의 변화는 클라이언트 사이드 렌더링(CSR)에서 서버 사이드 렌더링(SSR)로 변화 중이다. 클라이언트 사이드 렌더링이란 용어는 React.js와 같은 도구의 등장으로 등장했다. 또한 서버 사이드 렌더링(SSR)이란 용어는 Next.js와 같은 도구의 등장으로 등장했다.

![Nextjs_Next_13_RSC_vs_SSR_01](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/11bf1c04-5d25-4002-947b-33ce3c66ec59)

하지만 SSR은 이전에도 있었다. 고전적인 렌더링 방식이 `멀티 페이지 애플리케이션(MPA)` 방식이다. 하지만 멀티 페이지 애플리케이션은 명확하게 SSR이라고 하기는 애매하다. 특정 사이트(example.com)에 접속하면 HTML, CSS, Javascript와 같은 리소스를 받아와 출력하였다. 그리고 다른 페이지(example.com/about)로 이동하는 경우 다시 HTML, CSS, Javascript를 받아와 출력하였다. 이와 같이 보여지는 것은 원래 완성된 HTML 일 수도 있고, 템플릿 도구(JSP, PHP, PUG)를 사용하여 만든 HTML 일 수도 있다. 이러한 의미에서 서버 사이드 렌더링이라고도 볼 수 있다.

이러한 멀티 페이지 애플리케이션 방식의 렌더링 방식은 문제점이 존재했다. 전체 페이지를 매번 다시 받거나 그리기 때문에 서버 부하가 존재한다는 것이다. 또한 페이지 이동마다 리소스를 다시 받아오기 때문에 흰 화면이 노출된다는 문제점이 있었다.

![Nextjs_Next_13_RSC_vs_SSR_02](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/dc2faed0-bbc4-43b7-840f-57bc156fc3de)

이러한 문제점으로 `React.js`와 같은 도구가 등장하게 되어 이 때부터 싱글 페이지 애플리케이션(SPA)이 가능하게 되었다. 싱글 페이지 애플리케이션이 가능하게 된 것은 클라이언트 사이드 렌더링이라는 렌더링 방식이 등장했기 때문이다. 서버로부터 HTML을 받고 Javascript를 사용하여 웹 페이지를 동적으로 렌더링하는 방식이다. 클라이언트 사이드 렌더링은 한 번 페이지가 로드되면 다른 페이지로 이동하더라도 새로고침이 발생하지 않아 앱과 같은 부드러운 UX를 제공한다.

하지만 이와 같은 방식에도 문제점이 있었다. 페이지가 많아지고 기능이 많아질수록 Javascript 파일이 커지고 Javascript 파일이 큰 경우 초기 로딩 시간이 길어진다는 문제가 있었다. 또한 싱글 페이지 애플리케이션과 같은 경우 초기 HTML 이슈로 인한 SEO 문제가 발생한다는 문제가 있었다. 결국 이러한 문제들로 인해 다시 고전처럼 완성된 HTML이 필요하게 되었다.

![Nextjs_Next_13_RSC_vs_SSR_03](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/365e0a77-cbb3-41b7-b192-fad56ddd6fec)

그래서 등장한 것이 `Next.js`다. Next.js는 서버 사이드 렌더링 방식으로 React.js의 문제점들을 해결하게 된다. 완성된 HTML로 검색 엔진이 해석하기 쉬워지고 사용자의 체감 로딩 속도가 향상된다. 또한 Javascript를 받아와 하이드레이션이라는 기술로 클라이언트 사이드 렌더링도 가능하다. 하이드레이션 이후 인터렉션이 가능하다. 그 때부터는 클라이언트 사이드 렌더링이기 때문에 다른 페이지로 이동하더라도 HTML을 받아오지 않는다.

> 하이드레이션이라는 기술로 클라이언트 사이드 렌더링이 가능하다..? 이 부분에 대해서는 잘 이해가 가지 않는다. 클라이언트 사이드 렌더링과 같은 경우에는 클라이언트 사이드 라우팅을 통해 페이지를 이동할 때 Javasciprt를 통해 페이지를 전환하는 것인데 클라이언트 사이드 렌더링과 같은 경우 이미 Javasciprt 번들이 로드 된 상태라 하이드레이션이 필요 없는데 하이드레이션을 통해 클라이언트 사이드 렌더링이 가능하다는 말이 무슨 말일까..?

![Nextjs_Next_13_RSC_vs_SSR_04](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/79010bc0-6413-4045-81ec-ed86deed192d)

그렇다면 `리액트 서버 컴포넌트(RSC)`는 어떤 문제를 해결한 것일까?

우선 요청 위치가 바뀜으로서 강점을 가진다. 기존 Next.js는 세 가지의 서버 사이드 렌더링 방식을 가지고 있다. 그리고 이 세 가지 방식 중 스태틱 사이트 제너레이션(SSG)를 권장하고 있다. 또한 페이지 내부에 자주 바뀌는 컴포넌트가 있다면 `getServerSideProps`를 활용한 서버 사이드 렌더링이 사용되었다.

하지만 기존 getServerSideProps를 활용한 서버 사이드 렌더링 방식은 페이지 단위이므로 페이지 단위로 전략을 세워야한다는 문제가 있었다. 예를 들어 특정한 페이지가 있고 내부 컴포넌트 중 어떠한 컴포넌트는 데이터가 자주 바뀌는 컴포넌트이고, 어떠한 컴포넌트는 자주 바뀌지 않는 컴포넌트인 경우 하나의 컴포넌트의 데이터가 자주 바뀌는 컴포넌트이기 때문에 해당 페이지는 서버 사이드 렌더링을 통해 구현해야했다. 이유는 위에서 말한 것과 같이 getServerSideProps는 pages 디렉토리 내의 상위 레벨 컴포넌트에서 동작하여 페이지 단위로 서버 사이드 렌더링이 적용되기 때문이다. (여기서 상위 레벨이란 예를 들어 부모 컴포넌트 내부의 자식 컴포넌트1과 자식 컴포넌트2가 있는 경우 컴포넌트 트리 중 최상위 컴포넌트인 부모 컴포넌트 내부에서 getServerSideProps를 실행시켜야 한다는 것이다.)

하지만 리액트 서버 컴포넌트는 한 페이지 내부에서 데이터가 자주 바뀌지 않는 컴포넌트는 캐시(SSG)를 사용하고 데이터가 자주 바뀌는 컴포넌트는 항상 새로 그리는 등(SSR)의 전략이 가능하게 되었다. 즉 `서버 사이드 렌더링 방식이 페이지 단위에서 컴포넌트 단위로 세분화` 되었다는 것이다. 해당 전략을 통해 적절하게 서버의 부하를 조절할 수 있게 되었다. 결과적으로 TTI(Time to Interaction)가 개선되고 번들 사이즈 또한 줄어들었다.

<br>
<br>

# 2. Next.js

우선 Next.js에 대해 다시 한번 알아보자. 공식문서에서는 Next.js를 The React Framework for the Web이라고 소개하고 있다. React.js를 기반으로 한 웹 프레임워크이며 Full Stack Web Application을 만들 수 있다. 즉 서버가 존재한다는 것이다. 또한 Next.js의 핵심 기능은 서버 사이드 렌더링(SSR)이다.

![Nextjs_Next_13_RSC_vs_SSR_05](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/6ab20eb3-75b4-49c4-89b6-1cc0e2bae4b6)

React 18 개발 당시 리액트 서버 컴포넌트(RSC)라는 개념이 등장하게 되었다. 컴포넌트 단위로 서버에서 생성할 수 있다는 가능성을 시사했고 극단적으로 본다면 브라우저에 Javascript가 필요없을 수 있다는 의미였다. 하지만 기술적인 이슈로 React.js는 Vercel과 협업하여 Next.js에 Server Components라는 이름으로 추가가 되었다. 그렇기 때문에 React 공식문서에도 최신 리액트 기능을 사용하려면 Next.js를 사용하는 것을 권장하고 있다.

<br>
<br>

# 3. Pages Router의 SSR vs App Router의 RSC

Next.js의 공식 문서는 두 가지 버전이 존재한다. 13버전 이후인 Using App Router 방식과 13버전 이전인 Using Pages Router 방식이다. 여기서 13버전 이전인 `Pages Router` 방식의 서버 사이드 렌더링과 13버전 이후인 `App Router` 방식의 서버 컴포넌트를 비교해보자. (13버전 이후도 cna로 프로젝트 생성 시 Use App Router를 사용할 지 사용하지 않을 지 결정해서 사용할 수 있다.) 페이지는 총 3개의 간단한 웹 사이트이다.

![Nextjs_Next_13_RSC_vs_SSR_06](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/4dceeeac-c24b-4710-8114-d591611757cf)

<br>

## 3-1. Pages Router의 SSR 코드 구현

![Nextjs_Next_13_RSC_vs_SSR_07](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/383aee48-c5a7-40e2-91c4-98c4dff58867)

우선 Pages Router의 서버 사이드 렌더링 방식을 살펴보자. 페이지 기반 라우팅은 파일 기반으로 동작하며 해당 파일들은 아래 주소의 페이지를 의미한다.

- `pages/index.tsx` : `/`의 페이지를 의미
- `pages/todos/index.tsx` : `/todos`의 페이지를 의미
- `pages/todos/[id].tsx` : `/todos/1`과 같은 다이나믹 라우팅 페이지를 의미
- `pages/_app.tsx` : 전체 공통 레이아웃을 담당

![Nextjs_Next_13_RSC_vs_SSR_08](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/dde225e7-b2cf-472d-924e-189e37872f3e)

메인 페이지 코드를 살펴보자. `index.tsx`에 메인 페이지를 코드를 작성하였다. 또한 `_app.tsx`에 공통 레이아웃인 네비게이션 바를 사용하였고 나머지는 기본 설정으로 설정하였다.

![Nextjs_Next_13_RSC_vs_SSR_09](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/797df8d4-05cb-48ae-ba93-7035f96dfeab)

다음은 투두 리스트 페이지이다. `pages/todos/index.tsx`에 작성되었으며 SSR을 사용하기 위해 `getServerSideProps`를 활용하였다. 그리고 getServerSideProps를 통해 받아온 데이터를 TodoList 컴포넌트에 넘겨주고 있다.

![Nextjs_Next_13_RSC_vs_SSR_10](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/e3babb73-ba3e-4ed9-9af0-56299e86def2)

그리고 TodoList 컴포넌트에서는 전달받은 props를 활용하여 `map`을 통해 li과 Link를 작성하였다.

![Nextjs_Next_13_RSC_vs_SSR_11](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/ded961d4-0aa9-4f65-8c9f-63b7905c311b)

다음은 상세 페이지이다. `pages/todos/[id].tsx`에 작성되었으며 마찬가지로 SSR을 사용하기 위해 `getServerSideProps`를 활용하였다. 또한 파라미터의 id의 값을 동적으로 꺼내기 위해 context를 사용하였다. context를 사용해가져온 id를 통해 API를 요청하고 있다. 그리고 받아온 데이터는 Todo 컴포넌트에 props를 활용하여 가져와 사용하고 있다.

<br>

## 3-2. App Router의 RSC 코드 구현

![Nextjs_Next_13_RSC_vs_SSR_12](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/9f16ec43-5eb2-4f61-be9d-205d950ca775)

다음은 App Router의 서버 컴포넌트 방식을 살펴보자. 앱 라우터 방식은 Next.js 13 버전에 새로 도입되었다. 해당 방식은 폴더 기반으로 Nested하게 동작한다. Nested하게 동작한다는 것은 위 이미지와 같이 todos 디렉토리 내의 loading이 들어가있는데 이러한 경우 상세 페이지에서도 loading이 동일하게 동작할 수 있다는 것을 의미한다.

- 폴더 내의 `page.tsx`가 페이지 담당
- 폴더 내의 `layout.tsx`가 레이아웃 담당
- 폴더 내의 `loading.tsx`가 로딩 UI 담당
- 폴더 내의 `error.tsx`가 에러 UI 담당

![Nextjs_Next_13_RSC_vs_SSR_13](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/48ac1c92-b4db-49ea-b6c3-794ef98876d0)

메인 페이지 코드를 살펴보자. 크게 달라진 부분은 없다. Pages Router 방식의 `pages/index.tsx` 파일의 역할은 `app/page.tsx` 파일이 담당하고 Pages Router 방식의 `_app.tsx` 파일의 역할은 `app/layout.tsx` 파일이 담당한다.

![Nextjs_Next_13_RSC_vs_SSR_14](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/f57b07e1-8ce5-4902-b172-f31467889c1d)

다음은 투두 리스트 페이지이다. Pages Router 방식의 투두 리스트 페이지와 달리 서버 요청 코드가 없는 것을 볼 수 있다. 코드가 매우 깔끔해졌다. 기존에는 탑 레벨의 페이지에서만 서버 사이드 렌더링 관련 함수를 사용 가능하였고 받아온 데이터를 하위 컴포넌트의 props로 넘겨야했다. 하지만 App Router 방식의 경우 곧바로 해당 데이터를 사용하는 컴포넌트에서 데이터를 가져올 수 있다. 여기서 느낄 수 있는 점은 부모 컴포넌트와 자식 컴포넌트 간의 의존성이 떨어진 것을 알 수 있다. 즉 부모 컴포넌트의 경우 뷰만을 담당하는 것을 볼 수 있다. 투두 리스트 컴포넌트는 어떻게 구성되었는지 확인해보자.

![Nextjs_Next_13_RSC_vs_SSR_15](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/c0d73d06-aa02-4bd0-a72a-8d7f4e0bf43a)

투두리스트 컴포넌트에서는 Pages Router 방식에서 사용하던 props를 전달받아서 사용하는 방식이 아닌 getTodos라는 함수를 생성하여 함수 내부에서 데이터를 패칭해오는 것을 볼 수 있다. 그리고 해당 함수를 투두리스트 컴포넌트 내부에서 호출하여 해당 함수의 리턴 값을 바로 사용하고 있다. 이것이 가능한 이유는 컴포넌트는 기본적으로 서버 컴포넌트이기 때문에 위와 같이 바로 데이터를 패칭해올 수 있다. 훨씬 직관적이고 사용하기 쉬운 것을 알 수 있다.

![Nextjs_Next_13_RSC_vs_SSR_16](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/766a4ff3-e72b-43cb-9b53-0d640f218bad)

다음은 상세 페이지이다. `app/todos/[id].tsx`에 작성되었으며 마찬가지로 getTodo라는 함수를 생성하여 데이터를 패칭해오고 컴포넌트 내부에서 호출하여 사용하고 있다. 또한 데이터 패칭 시 필요한 id 값을 가져오기 위해 params의 id를 가져와 인자로 넘겨주고 있다.

<br>
<br>

# 4. 비교

이제 위에서 구현한 Pages Router의 SSR 방식과 App Router의 RSC 방식을 비교해보자. 우선 비교하기 전 원활한 비교를 위해 스타일링은 module-css로 작성하였다. 왜냐하면 만약 styled-component와 같이 css-in-js로 작성하게되면 서버 컴포넌트에서 javascript 파일을 필요로 한다. 스타일 코드만 받아오는 것이지만 학습 및 비교 차원에서 javascript 파일을 받아오는지 차이를 확인하기 위해 module-css로 작성되었다.

또한 App Router에서 fetch쪽 로직을 수정하여 비교한다. 위에서 작성한 fetch는 디폴트로 작성했기 때문에 SSG로 동작하게 된다. SSR의 비교를 위해 fetch 속성을 `no-store`로 바꾸어 비교한다.

![Nextjs_Next_13_RSC_vs_SSR_17](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/8efc65b1-3904-45d6-ad92-93f46cff1542)

여기서 궁금한 것이 생길 수 있다. 위에서 사용한 fetch 메소드는 흔히 사용하던 브라우저의 호스트 객체인 window의 fetch 메소드일까? 아니다. 위에서 사용하고 있는 fetch 메소드는 Next.js에 내장되어 있는 fetch 메소드로 window 객체의 fetch 메소드와는 차이가 있다. Next.js의 내부 코드를 보면 globalThis에 fetch가 작성되어있다. 여기서 globalThis는 전역 객체이다.

![Nextjs_Next_13_RSC_vs_SSR_18](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/e25726af-827c-4ed7-a3a7-cb8832acbe85)

fetch와 유사하긴 하지만 자체적인 옵션들과 로직이 추가되어있다. 이제 본격적으로 비교해보자.

<br>

## 4-1. 서버 사이드 렌더링 비교

![Nextjs_Next_13_RSC_vs_SSR_19](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/67264abb-f0c3-4e6c-912a-45b3da16adfc)

우선 둘 다 최초 메인페이지(`/`) 진입 시 html을 확인할 수 있다.

![Nextjs_Next_13_RSC_vs_SSR_20](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/1c7853b9-b333-4519-bc09-0b45e4182794)

그 후 네비게이션 바의 `next/Link`로 된 todos 버튼을 클릭하여 페이지 이동(`/todos`) 시 새로 html을 받아오지 않는 것을 확인할 수 있다. 새로 고침이 없어 흰 화면이 보이지 않고 단순히 추가 청크 파일들만 받아오는 것을 볼 수 있다. 즉 클라이언트 사이드 렌더링이 발생하는 것이다.

그렇다면 메인 페이지만 서버 사이드 렌더링인 것은 아닐까?

|                                                                                                                                     |                                                                                                                                     |
| :---------------------------------------------------------------------------------------------------------------------------------: | :---------------------------------------------------------------------------------------------------------------------------------: |
| ![Nextjs_Next_13_RSC_vs_SSR_21_1](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/25f0ffda-0f61-469f-a81d-8dccd0a34f93) | ![Nextjs_Next_13_RSC_vs_SSR_21_2](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/a8ddaa15-127c-4dc9-8a9f-67a4f7600f7e) |

이것을 확인해보기 위해 현재 페이지 `/todos`에서 새로고침을 해보자. 그렇다면 위 이미지와 같이 흰 화면이 나타난 후 렌더링 되는 것을 볼 수 있다. 여기서 알 수 있는 점은 서버 사이드 렌더링이 정상적으로 동작하며 서버에서 API를 내부적으로 호출하고 HTML을 완성해서 보낸다는 것을 알 수 있다. 네트워크 탭에서 리소스 목록 중 HTML을 선택하여 Preview를 확인해보면 완성 된 HTML을 보내는 것을 확인해볼 수 있다.

즉 서버 컴포넌트도 기존과 동일한 서버 사이드 렌더링으로 동작하고 있다. 서버 컴포넌트 등장 전에도 Next.js는 기본적으로 SSG 혹은 SSR 렌더링 방식으로 페이지 구현 시 해당 페이지에 최초 접근하는 경우 SSG 혹은 SSR 방식으로 동작하며 `Link` 컴포넌트를 활용한 클라이언트 사이드 라우팅 시 CRS 방식으로 동작하였고 `a` 태그를 활용한 서버 사이드 라우팅 시 SSR 방식으로 동작하였다. 이러한 동작 방식이 동일하게 적용되고 있는 것이다.

<br>

## 4-2. 네트워크 요청 비교

이제 네트워크 요청을 비교해보자.

먼저 Pages Router 방식이다.

![Nextjs_Next_13_RSC_vs_SSR_22](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/47d02d6d-ced0-4539-bab4-1ed60018673b)

위 이미지는 Pages Router 방식에서 첫 메인 페이지 진입 후 상단 todos 버튼을 클릭하여 페이지를 이동한 경우의 네트워크 탭의 모습이다. 우선 HTML은 메인 페이지 HTML을 받아온 것을 확인할 수 있다. 왜냐하면 첫 페이지 진입이 메인 페이지이기 때문이다. 또한 여러가지 javascript 파일과 json 파일을 받아온 것을 볼 수 있다.

우선 첫번째 부분부터 확인해보자.

![Nextjs_Next_13_RSC_vs_SSR_23](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/222c482a-15c1-46a0-b7c4-fa1aabf768ea)

첫 부분은 todos와 관련된 청크파일이다. 메인 페이지 진입 시 받아온다. 왜냐하면 `next/Link`는 기본적으로 접근 가능성이 있는 페이지에 대해 프리페치(or 프리로드)하기 때문이다.

![Nextjs_Next_13_RSC_vs_SSR_24](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/07b70625-02c5-408b-a3c5-6efa999ed440)

두번째 todos.json은 상단 todos 버튼을 클릭할 때 받아온다. 즉 해당 버튼을 클릭하여 페이지를 이동할 때 API 요청이 이루어지는 것이다. 해당 요청으로 가져온 json 파일과 메인 페이지 진입 시 미리 받아온 todos의 청크 파일을 활용하여 클라이언트 사이드 라우팅 시 CSR로 동작하게 된다.

![Nextjs_Next_13_RSC_vs_SSR_25](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/8b2302cb-a8ef-40ba-982e-bbc6f1be032f)

마지막 부분은 위와 동일하게 자세히 버튼으로 인해 접근 가능성이 있다고 판단하여 상세 페이지에 대한 청크가 프리페치 된 것이다.

두번째로 App Router 방식이다.

![Nextjs_Next_13_RSC_vs_SSR_26](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/9632fd44-dbe1-49e7-a335-d14cec640c06)

위 이미지는 App Router 방식에서 첫 메인 페이지 진입 후 상단 todos 버튼을 클릭하여 페이지를 이동한 경우의 네트워크 탭의 모습이다. 우선 HTML은 Pages Router 방식과 마찬가지로 메인 페이지 HTML을 받아온 것을 확인할 수 있다. 왜냐하면 첫 페이지 진입이 메인 페이지이기 때문이다. 또한 적은 양의 javascript 파일과 rsc 파일을 확인할 수 있다.

우선 첫번째 부분부터 확인해보자.

![Nextjs_Next_13_RSC_vs_SSR_27](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/1bb1bba4-c2ae-4dc8-b5aa-c062f9b9a959)

우선 첫번째 부분은 처음에 메인 페이지에 진입했을 때는 스타일이나 번들 설정으로 인한 일부 javascript 파일을 받아온 것이다. 그리고 페이지 전환이 이루어졌음에도 불구하고 최초 javascript 파일 이후에는 javascript 파일을 받아오지 않는 것을 확인할 수 있다.

![Nextjs_Next_13_RSC_vs_SSR_28](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/1507c373-9264-486b-a159-456f2f46d088)

또한 메인 페이지 진입 시 todos에 관련 된 rsc 파일을 받아오는데 이것은 Link 태그 사용으로 인해 접근 가능성이 있다고 판단하여 받아오는 것이다. 그러나 메인 페이지 진입 후 todos 경로로 페이지를 이동했을 때 json은 받아오지 않는 것을 확인할 수 있다.

![Nextjs_Next_13_RSC_vs_SSR_29](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/8982e042-5f4d-4577-87c7-1c1d675d4812)

그리고 todos 페이지로 이동하는 경우 Link 태그를 사용한 상세 페이지로 이동하는 자세히 보기 버튼으로 인해 접근 가능성이 있다고 판단하여 상세 페이지의 rsc 파일을 프리페치 하는 것을 확인할 수 있다.

지금까지 보았을 때는 json 파일도 없고 javascript 파일도 없기 때문에 페이지 전환 시 렌더링이 어떻게 발생하는지 예측하기 어렵다. 그렇다면 이 상태에서 자세히 보기 버튼을 클릭하여 상세 페이지로 이동하면 어떤 네트워크 요청이 발생할까?

![Nextjs_Next_13_RSC_vs_SSR_30](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/547627b5-1cd8-4344-af69-ca9919202a31)

놀랍게도 별다른 네트워크 요청없이 페이지를 렌더링하는 것을 확인할 수 있다. 어떻게 이런 방식이 가능할까?

rsc가 들어간 파일을 자세히 살펴보면 동작을 추측할 수 있다.

![Nextjs_Next_13_RSC_vs_SSR_31](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/66713dc0-93f5-4b16-8725-5d1fc7909d6e)

![Nextjs_Next_13_RSC_vs_SSR_32](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/6a91967c-d5c2-4218-bb3a-80fe011c5e10)

rsc 파일을 살펴보면 json은 아니지만 json과 비슷한 형태로 되어있다. 이 부분을 자세히 살펴보면 달러도 보이고 아이디도 보이며 뭔가 선택자와 같은 느낌이 들고 자신의 정보에 대한 위치 값으로 추정되는 데이터로 가지고 있는 것 같다.

![Nextjs_Next_13_RSC_vs_SSR_33](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/41117ddc-5104-4c83-b6dc-9da2ccd8a83d)

위 이미지는 Next.js의 코드를 까본 것이다. [Next.js 레파지토리](https://github.com/vercel/next.js/tree/canary/packages/next/src/compiled/react-server-dom-webpack)의 컴파일된 공간이 존재하고 이 경로를 타고 들어가 [React.js의 레파지토리](https://github.com/facebook/react/blob/main/packages/react-server/src/ReactFlightReplyServer.js)를 보면 같은 위와 같은 함수가 존재한다.

또한 이 상태에서 서버 로그를 확인해보면 프리페치 시 이미 모든 요청이 발생한 것을 확인할 수 있다.

![Nextjs_Next_13_RSC_vs_SSR_34](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/fc3a11fb-7603-48db-9034-693fd5c14dac)

즉 이 결과로 추측할 수 있는 부분은 프론트 서버는 위 정보를 바탕으로 브라우저에 RSC 파일을 보낸 것이고 결과적으로 javascript가 필요 없어지며 API 요청을 완전히 감출 수 있게 된다. 또한 한명이 보낸 이 RSC 파일을 캐시하여 다른 사람들이 todos나 상세 페이지에 접근할 때 재활용할 수 있어 캐시 활용성이 매우 높아지게 된다.

<br>

## 4-3. 스트리밍 서버 사이드 렌더링(Streaming SSR)

다음은 Next.js 13에서 추가 된 스트리밍 서버 사이드 렌더링(Streaming SSR)이다. 스트리밍 서버 사이드 렌더링은 필수적인 데이터를 우선적으로 렌더링하는 점진적인 렌더링 기술이다.

![Nextjs_Next_13_RSC_vs_SSR_35](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/4fca1378-5e6d-4ece-b8fe-efffa901e08b)

위 이미지 타임 테이블에 대한 설명은 아래와 같다.

- A : 서버에서 필요한 데이터를 받아온다.
- B : 데이터를 바탕으로 서버에서 HTML을 그려 보낸다. (TTFB)
- C : 클라이언트에서 non-interactive UI가 우선 표시된다. (FCP)
- D : Javascript 로드가 완료되면 하이드레이션을 통해 interaction이 가능해진다. (TTI)

기존 SSR의 경우 서버에서 완성된 HTML 받아와 사용자에게 우선적으로 보여준 뒤 Javascript가 로드되면 하이드레이션을 통해 사용자와 상호작용 할 수 있도록 했었다. 여기서 문제점은 서버에서 렌더링하는 동안 사용자는 흰 화면을 보게 된다는 문제점이 발생한다. UI를 우선 표시한다지만 결국 서버에서도 데이터 로드가 끝나야한다는 것이다. 또한 UI를 표시한 후 Javascript 로드가 되고 하이드레이션이 완료될 때 까지 사용자 상호작용이 불가능한 블로킹이 발생하게 된다.

![Nextjs_Next_13_RSC_vs_SSR_36](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/0f5767f1-47f9-481d-8a24-dc2ab51a403e)

반면 Next.js 13의 경우 Suspense와 함께 스트리밍 서버 사이드 렌더링을 지원한다. 스트리밍 서버 사이드 렌더링의 경우 필요한 부분의 HTML을 잘게 쪼갠 청크로 분할하여 클라이언트로 전송해 해당 부분에 대한 UI 노출 및 하이드레이션을 우선적으로 진행하고 나머지 부분의 HTML 청크도 병렬적으로 로드 및 하이드레이션 하여 점진적인 방식으로 렌더링한다. 이러한 렌더링 방식으로 인해 유저는 완전한 페이지가 서버에서 그려질 때 까지 흰 화면을 보며 기다리는 것이 아닌 점진적으로 그려지는 페이지를 볼 수 있게 되는 것이다. 즉 직렬적으로 처리되던 기존 서버 사이드 렌더링 방식에서 병렬적으로 처리할 수 있도록 스트리밍 서버 사이드 렌더링이 도입 된 것이다. 또한 로드 중인 부분에 대해서는 직접 Suspense 경계를 만들거나 로딩 컨벤션(loading.tsx)을 사용하여 로딩 페이지를 띄워줄 수도 있다.

위 이미지의 타임 테이블을 보면 가장 최상위의 컨텐츠의 경우 A를 제외하고 B부터 보내고 있는데 데이터 패칭이 필요없는 경우 데이터 패칭 단계를 생략하고 바로 HTML을 전송하게 된다. 예를 들어 네비게이션 바 혹은 스켈레톤과 같은 경우 데이터 패칭이 필요없기 때문에 데이터 패칭 단계가 생략되게 되는 것이다. 이러한 동작 방식으로 인해 페이지 일부를 더 빨리 전송하여 확실하게 TTFB를 개선하였고 우선 순위가 높거나 데이터에 의존하지 않는 컴포넌트를 먼저 표시함으로서 FCP 또한 개선되었다. 그리고 먼저 로드 된 HTML에 대해 하이드레이션 또한 병렬적으로 처리하여 TTI를 개선하였다.

![Nextjs_Next_13_RSC_vs_SSR_37](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/277efbf5-2c0d-4669-805e-e62e36e82f8f)

실제로 위 예시에서 스트리밍 서버 사이드 렌더링을 테스트해보기 위해 `todos/loading.tsx`를 작성해서 넣으면 스트리밍 서버 사이드 렌더링의 동작을 확인해볼 수 있다. 초기 HTML에는 TodoList 컴포넌트를 제외하고 로딩 컴포넌트로 HTML을 보낸 후 서버에서 데이터 호출이 완료된 이후 컴포넌트가 완전히 그려지게 된다. 즉 사용자는 처음에 로딩 컴포넌트를 보게 되고 프론트 서버에서 데이터 호출이 완료 된 이후 RSC 파일을 보내면 완전한 컴포넌트를 렌더링하여 사용자는 완전한 페이지를 보게 되는 것이다.

<br>

## 4-4. 요청 위치

작성 중

<br>
<br>

# # 참고 URL

- Next.js13으로 알아보는 FE렌더링 방식(SSR vs RSC) : https://youtu.be/qqhtdTV7Kqk
- App Router 방식의 page.js : https://nextjs.org/docs/app/api-reference/file-conventions/page
- react repo ReactFlightReplyServer 함수 : https://github.com/facebook/react/blob/main/packages/react-server/src/ReactFlightReplyServer.js
- next repo server dom webpack : https://github.com/vercel/next.js/tree/canary/packages/next/src/compiled/react-server-dom-webpack
- Loading UI and Streaming : https://nextjs.org/docs/app/building-your-application/routing/loading-ui-and-streaming
