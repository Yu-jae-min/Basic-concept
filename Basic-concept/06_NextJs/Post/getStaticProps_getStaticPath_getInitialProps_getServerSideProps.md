# [next.js] getStaticProps, getStaticPath, getInitialProps, getServerSideProps

## **1. getStaticProps**

`getStaticProps`는 정적 사이트 생성(SSG, Static Site Generation) 및 점진적 정적 생성(ISR, Incremental Static Regeneration)을 위해 사용되는 메소드로 빌드 타임에 pre-rendering을 위해 호출된다.

SSG와 ISR을 나누는 기준은 return 객체의 `revalidate` 옵션이며 `revalidate` 없다면 `SSG`로 동작하여 빌드 시 딱 한번만 호출된다는 특징이 있다. 단, 데이터 업데이트를 위해서는 재빌드 및 배포가 필요하다는 단점이 있다.

`revalidate`가 존재하면 `ISR`로 동작하며 `revalidate`의 value 값에 따라 특정 주기마다 페이지를 재생성한다.

```jsx
const component = (props) => {
  ...
};

export default component;

export const getStaticProps = async () => {
  ... // API 호출 혹은 파일 시스템 접근 등의 코드 작성

  return {
    props: {
      key: value, // 페이지 컴포넌트에 넘겨줄 props
    },
    revalidate: 10,  // 점진적 정적 생성(ISR, Incremental Static Regeneration) 구현 시 사용
  };
};
```

<br>
<br>

## **2. getStaticPath**

`getStaticPaths`는 `getStaticProps`와 마찬가지로 pre-rendering 위해 사용하는 메소드이다. `getStaticProps`와의 차이점은 `pages/**/[id].tsx`과 같이 동적 라우팅 페이지 중 빌드 시 정적으로 생성할 페이지를 결정할 수 있다.

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

### **2-1. getStaticPath의 fallback 옵션**

#### **2-1-1. false**

getStaticPaths가 반환한 path들 pre-rendering하며 getStaticPaths가 반환하지 않은 모든 path에 대해서 404 페이지를 반환한다.

- **사용 시기**

  - 적은 숫자의 path만 프리렌더링 해야하는 경우 사용

  - 새로운 페이지가 추가 될 일이 많지 않은 경우 사용, 새로운 페이지가 자주 추가 된다면 추가될때마다 다시 재빌드 해야한다.

<br>

#### **2-1-2. true**

getStaticPaths가 반환한 path들 pre-rendering하며 getStaticPaths가 반환하지 않은 path를 요청하는 경우 fallback 버전을 먼저 사용자에게 보여주고 백그라운드에서 getStaticProps 함수를 사용하여 static하게 페이지를 생성한 뒤 해당 페이지를 사용자에게 보여준다. 그 후 생성된 페이지에 대해서는 getStaticPaths에 path로 추가한다.

- **주의 사항**

  - getStaticPaths가 반환하지 않은 path를 요청하는 경우 router.isFallback을 사용하여 fallback 버전을 설정하지 않으면 404 페이지를 반환한다.

- **사용 시기**

  - 데이터에 의존하는 정적 페이지를 많이 가지고 있으나, 빌드 시에 모든 페이지를 생성하는건 너무나 큰 작업일 때 사용, 몇몇 페이지들만 정적으로 생성하게 하고, fallback 옵션을 true로 설정해주면 이후 요청이 오는 것에 따라서 정적 페이지들을 추가하게 된다. 이런 방식을 통해 빌드 시간도 단축하고, 대부분 사용자들의 응답 속도도 단축할 수 있다.

<br>

#### **2-1-3. blocking**

getStaticPaths가 반환한 path들 pre-rendering하며 getStaticPaths가 반환하지 않은 path를 요청하는 경우 fallback 상태를 보여주지 않고 SSR처럼 동작한다. 그 후 생성된 페이지에 대해서는 getStaticPaths에 path로 추가한다.

<br>
<br>

## **3. getServerSideProps vs getInitialProps**

`getServerSideProps`와 `getInitialProps` 모두 서버 사이드 렌더링 시 사용하며 `getServerSideProps`는 Next.js 9.3버전 이후 도입된 메소드이다. 두 메소드 모두 페이지 요청이 들어올 때 마다 매번 호출된다. 그렇다면 두 메소드의 공통점과 차이점은 무엇일까?

<br>

### **3-1. 공통점**

#### **3-1-1. 한 페이지에서 하나만 실행된다.**

next.js의 `서버 사이드 사이클`은 아래와 같이 동작한다.

1. Next Server가 GET 요청을 받는다.
2. 요청에 맞는 Page를 찾는다.
3. `_app.js`의 `getInitialProps`가 있다면 실행한다.
4. Page Component의 `getInitialProps`가 있다면 실행한다. pageProps들을 받아온다.
5. `_document.js`의 `getInitialProps`가 있다면 실행한다. pageProps들을 받아온다.
6. 모든 props들을 구성하고, `_app.js` > `page Component` 순서로 rendering.
7. 모든 Content를 구성하고 `_document.js`를 실행하여 html 형태로 출력한다.

위 사이클에서는 `getInitialProps`가 `_app`, `_document`, `Page Component` 모두에서 동작하는 것처럼 설명하고 있다. 하지만 공식 문서를 확인해보면 기본적으로 `getInitialProps`, `getServerSideProps`는 한 페이지에서 하나만 실행된다고 나와있다. 이게 무슨 말일까?

즉, 공식문서에 나온것처럼 기본적으로 `getInitialProps`와 `getServerSideProps`는 한 페이지에서 하나만 실행된다. 페이지가 렌더링 될때 next 내부에서 거치는 순서는 위 서버 사이드 사이클에서 알 수 있듯이  `_app` -> `page component` 이다. 공식 문서에 나와있는대로 상위(ex `_app`)에서 해당 메소드가 실행되면 하위 컴포넌트에서는 `getInitialProps`나 `getServerSideProps`가 있어도 실행되지 않는다. 그렇기 때문에 공식 문서에도 최상위에서 사용하기를 권장하고 있고 전역적 데이터 패칭이 필요한 경우 적합하다. 하지만 하위 컴포넌트에서 개별로 실행시키는 것이 완전 불가능한 것은 아니다. 하위 컴포넌트에서 `getInitialProps`나 `getServerSideProps`를 개별로 실행시키기 위해서는 아래와 같이 처리할 수 있다.

```jsx
// src/_app.tsx
import "./globals.css";

function MyApp({ Component, pageProps }) {
  return <Component ponent {...pageProps} />;
}

MyApp.getInitialProps = async ({ Component, ctx }) => {
  let pageProps = {};
  // 하위 컴포넌트에 getInitialProps가 있다면 추가 (각 개별 컴포넌트에서 사용할 값 추가)
  if (Component.getInitialProps) {
    pageProps = await Component.getInitialProps(ctx);
  }

  // _app에서 props 추가 (모든 컴포넌트에서 공통적으로 사용할 값 추가)
  pageProps = { ...pageProps, posttt: { title: 11111, content: 3333 } };

  return { pageProps };
};

export default MyApp;
```

<br>

#### **3-1-2. 자동 정적 최적화 미지원**

`자동 정적 최적화(Automatic Static Optimization)`란 Next.js에서 별도의 데이터 요구 사항이 없는 페이지의 pre-rendering 여부를 자동으로 결정하는 기능이다. getInitialProps나 getServerSideProps 함수를 사용하는 경우가 아니라면 Next.js는 해당 페이지를 자동으로 pre-rendering하여 성능을 최적화한다.

> 💡 **- 관련 링크** : https://nextjs.org/docs/pages/building-your-application/rendering/automatic-static-optimization

<br>

### **3-2. 차이점**

#### **3-2-1. 호출 사이드**

`getInitialProps`는 URL을 통한 초기 로드 및 `<a/>`태그의 `href`속성으로 이동하는 경우에는 서버에서 실행되지만 `next/link`, `next/router`를 사용하여 이동하는 경우, 즉 클라이언트 측에서 페이지를 이동하는 경우 서버가 아닌 클라이언트에서 작동한다.

이렇게 작동하는 것에 가장 큰 문제점은 `getInitialProps` 내부에 클라이언트 측에서 수행할 수 없는 로직(직접 데이터베이스에 접근 등)이 존재하는 경우 문제가 발생한다. 또한 서버에서만 수행하는 로직만 존재한다 하더라도 클라이언트 측에서도 작동하기 때문에 클라이언트 측 번들에 포함되어 불필요하게 번들 사이즈가 커지게 된다.

반면 `getServerSideProps`는 URL을 통한 초기 로드 및 `<a/>`태그의 `href`속성으로 이동하는 경우와 `next/link`, `next/router`를 사용하여 이동하는 경우에도 서버에서 렌더링을 실행하고 결과를 클라이언트 측에 전달한다. 이는 `getServerSideProps` 내부에서 클라이언트 측에서 수행할 수 없는 로직이 존재해도 문제가 발생하지 않는다는 것을 의미한다.
