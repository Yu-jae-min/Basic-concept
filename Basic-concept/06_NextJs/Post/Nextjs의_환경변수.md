# **[next.js] Next.js의 환경변수**

23년 06월 23일

<br>

## **1. Next.js 환경 변수의 종류**

![스크린샷 2023-06-23 19.06.18.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e036d8e2-78fa-49fb-999c-c7ca865f4a1b/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2023-06-23_19.06.18.png)

Next.js의 환경 변수는 `.env`, `.env.development`, .`env.local`, `.env.production`, `.env.test` 까지 총 다섯 가지가 존재한다.

<br>

### **1-1. .env**

가장 우선순위가 낮다. 모든 환경에서 공통으로 사용할 디폴트 키를 관리한다.

<br>

### **1-2. .env.development**

개발 환경(process.env.NODE_ENV === 'development') 에서 적용된다.
개발환경일 경우, .env에 같은 환경변수가 있다면 덮어쓴다.

<br>

### **1-3. .env.production**

배포/빌드 환경(process.env.NODE_ENV === 'production') 에서 적용된다.

배포환경일 경우, .env에 같은 환경변수가 있다면 덮어쓴다.

<br>

### **1-4. .env.local**

모든 환경 변수보다 우선순위가 높다.
다른 환경 변수 파일에 동일한 환경 변수가 있다면 해당 값들을 덮어쓴다.

<br>

### **1-5. .env.test**

테스트 환경(process.env.NODE_ENV === 'test') 에서 적용된다.

<br>
<br>

## **2. 구동 환경 체크**

구동 환경을 체크하기 위해서는 react에서 사용하던 방법과 마찬가지로 `process.env.NODE_ENV`를 사용할 수 있다. next.js는 자동으로 `process.env.NODE_ENV` 변수를 생성한다.

1. development : 개발 환경(npm run dev로 구동한 경우)
2. production : 배포 환경(npm run build로 빌드한 경우)
3. test : 테스트 환경

```jsx
const production = NODE_ENV === "production";
const develop = NODE_ENV === "development";
const test = NODE_ENV === "test";
```

<br>
<br>

## **3. Prefix**

환경변수 파일 내부에서 환경변수 생성 시 브라우저에서 사용해야할 환경변수의 경우 `NEXT_PUBLIC_` Prefix를 붙여줘야 한다.

```jsx
### .env 파일
# 서버에서만 사용 가능(getServerSideProps, getStaticProps 등)
NODE_VALUE=default_value

# 서버와 브라우저 모두 사용 가능 (앞에 NEXT_PUBLIC_를 붙여서 생성한다)
NEXT_PUBLIC_API_KEY=default_api_key
```

`NEXT_PUBLIC_` 가 붙어있지 않은 환경변수는 서버에서만 사용 가능하며 `NEXT_PUBLIC_` 가 붙은 환경변수는 서버와 브라우저 모두에서 사용 가능하다.

```jsx
import type { GetServerSideProps, NextPage } from "next";

// ### 브라우저 실행 환경(리액트 컴포넌트)
const Home: NextPage = () => {
  // NEXT_PUBLIC_이 없는 변수는 브라우저에서 참조할 수 없다.
  console.log(process.env.NODE_VALUE); // undefined

  // NEXT_PUBLIC_이 앞에 붙은 변수는 브라우저에서도 참조할 수 있다.
  console.log(process.env.NEXT_PUBLIC_API_KEY); //default_api_key

  return (
    <>
      <main>index</main>
    </>
  );
};

// ### 서버 실행 환경 (SSR)
export const getServerSideProps: GetServerSideProps = async (context) => {
  // 서버에서는 모든 환경변수를 참조할 수 있다.
  console.log(process.env.NODE_VALUE); // default_value
  console.log(process.env.NEXT_PUBLIC_API_KEY); // default_api_key

  return { props: { message: `Next.js is awesome` } };
};

export default Home;
```

<br>
