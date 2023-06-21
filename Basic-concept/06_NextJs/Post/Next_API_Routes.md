# **[next.js] Next API Routes**

23년 6월 21일

<br>

## **1. Next API Routes**

[Routing: API Routes](https://nextjs.org/docs/pages/building-your-application/routing/api-routes)

`Next.js API Routes`는 Next.js 프레임워크에서 제공하는 기능으로, 서버사이드 또는 클라이언트사이드에서 동작하는 API Endpoint를 손쉽게 생성할 수 있도록 도와준다.

`API Routes`를 사용하면 api 디렉토리 내에 작성한 파일들이 서버사이드에서 실행되는 API 엔드포인트로 자동으로 매핑되며, 클라이언트사이드에서도 해당 API Endpoint를 호출할 수 있다.

해당 코드는 서버 측 번들로 클라이언트 번들에 포함되지 않으며 해당 기술을 통해 백엔드 서버 없이 서버리스 함수 형태로 프론트엔드에서 API를 만들고 개발할 수 있다.

<br>
<br>

## **2. Next API Routes 사용 방법**

### **2-1. req와 res**

각 API Routes 파일은 기본적으로 `req` (요청) 객체와 `res` (응답) 객체를 받는 핸들러(default function)를 export 해야한다. 이 핸들러 함수는 Endpoint로의 각 요청에 대해 Next.js가 호출한다. 즉, `req` 와 `res` 파라미터를 받아서 `handle` 해줄 `export default function` 이 반드시 있어야 한다.

- `req`: node.js 에서 제공하는 [http.IncomingMessage](https://nodejs.org/api/http.html#class-httpincomingmessage) 의 인스턴스이다.
  - [pre-built middlewares](https://nextjs.org/docs/api-routes/api-middlewares) 를 통해 사이즈 제한, CORS 설정 등 편의 기능을 이용할 수 있다.
  - 동적 경로 정보는 `req query`에 포함되어있어 코드 상에서 쉽게 사용할 수 있다.
- `res`: node.js 에서 제공하는 [http.ServerResponse](https://nodejs.org/api/http.html#class-httpserverresponse) 의 인스턴스이다.
  - [next.js response helper functions](https://nextjs.org/docs/api-routes/response-helpers) 에서 편리한 기능을 제공한다.

`pages/api/user.js` 파일을 다음과 같이 작성하면, 상태코드 `200 OK` 와 함께 `{ name: 'John Doe' }` 를 응답하는 API 를 만들 수 있다.

```jsx
export default function handler(req, res) {
  res.status(200).json({ name: "John Doe" });
}
```

타입스크립트를 사용한다면 필요한 타입을 import 해야한다.

```jsx
import type { NextApiRequest, NextApiResponse } from "next";

export default function handler(req: NextApiRequest, res: NextApiResponse) {
  res.status(200).json({ name: "John Doe" });
}
```

<br>

### **2-2. HTTP 메서드별 핸들링**

HTTP 메서드마다 다른 응답을 해주고 싶다면, 위처럼 `req.method` 에 대한 if 문 등으로 처리할 수 있다.

```jsx
export default function handler(req, res) {
  if (req.method === "POST") {
    // Process a POST request
  } else {
    // Handle any other HTTP method
  }
}
```

<br>

### **2-3. Restful API**

Restful API를 예시로 들어보자. 예를 들어 post를 받아오는 API라고 가정했을 때 `/api/posts.ts` , `/api/posts/[postId].ts` 와 같이 만들 수 있을 것이다. 이를 GET으로 호출할 때 아래와 같은 결과 값을 기대할 수 있다.

- `/api/posts.ts` : 포스트 리스트
- `/api/posts/[postId].ts` : ID에 맞는 단일 포스트

만약 `/api/posts/100` 으로 호출한다면 아래 코드의 결과는 `John Doe 100`이 될 것이다.

```jsx
export default function handler(req, res) {
  const { id } = req.query;

  res.status(200).json({ name: "John Doe" + id });
}
```

<br>

### **2-4. 하위 경로 모두 포함하기**

`/api/posts/[postId].ts` 과 같이 작성 시 `/api/posts/1` 과 같이 하나의 URL에만 매칭되었다면 `/api/posts/1/comment` 나 `/api/posts/1/comment/1` 과 같이 여러 depth에 걸친 API를 함께 다룰 수 있다. 방법은 아래와 같이 파일명에 `…` 을 붙이는 방식으로 구현할 수 있다.

- `/api/post/[…multiPostId].ts`

<br>

### **2-5. 상위 경로 모두 포함하기**

추천되지 않는 방법이지만 상위 경로를 포함하여 다룰 수도 있다. 예를 들면 `/api/posts` 와 `/api/posts/1` 등을 함께 다루는 것이다. 방법은 아래와 같이 파일명에 중첩 대괄호를 붙이는 방식으로 구현할 수 있다.

- `/api/posts/[[…multiPostId]].ts`

<br>

### **2-6. 클라이언트에서 호출하기**

만들어놓은 Next API Routes를 어떻게 사용할 수 있을까? 단순히 호출해주기만 하면 된다.
앞에 만들어 놓은 api를 다음과 같이 호출 할 수 있다.

```jsx
const fetchPokemon = async () => {
  const res = await fetch("/api/posts/1");
  const data = await res.json();
  return data;
};
```

<br>

### **2-7. 미들웨어 사용**

Next.js는 미들웨어도 지원한다. 미들웨어는 요청 핸들러 전에 실행되는 함수로, 수신된 요청을 더 세밀하게 관리할 수 있도록 도와준다. 이는 특히 요청을 더 세밀하게 처리해야 할 때 유용한다.

<br>
<br>

## **3. Next API Routes 사용 시 유의 사항**

### **3-1. Content-Type 헤더 설정과 파싱**

body 로 `"{email: "my_email@naver.com"}"` 이라는 문자열을 받았다고 가정하자. api 의 handler 는 아래와 같이 작성되었다.

```jsx
export default async function handler(
  req: NextApiRequest,
  res: NextApiResponse
) {
  console.log(req.body.email); // undefined
  res.status(200).json({ result: "success" });
}
```

위의 `console.log(req.body.email)` 의 결과는 `undefined` 이다. 그 이유는 파싱이 되지 않았기 때문이다. `(JSON.parse(req.body)).email` 을 하면 원했던 결과인 `my_email@naver.com` 이 잘 나올 것이다.

위와 같이 직접 파싱하지 않아도 자동으로 파싱된 형태로 데이터를 받아볼 수도 있는데, 그러기 위해서는 `headers` 에 `{"Content-Type": "application/json"}` 을 적어주면 된다. `Content-Type` 을 참조하여 미들웨어 단계에서 문자열을 파싱해줄 것이다.

생각보다 많은 개발자들이 실수하는 부분이니 유의하자.

<br>

### **3-2. Live Connection이 필요한 경우 부적합**

Next.js에서 제공하는 `API Routes`는 `serverless function`이기 때문에 stateless하여 지속적인 DB 커넥션을 유지하거나 web socket 등을 이용한 실시간 통신 등의 live connection이 필요한 경우에는 적합하지 않을 수 있다.

<br>

### **3-3. 중복된 API fetch 주의**

`API Routes`를 `getServerSideProps`나 `getStaticProps` 등에서 사용하면 불필요하게 API를 중복 호출하는 문제가 발생할 수 있다. 아래 예시는 중복 호출 문제를 방지하는 예시이다.

```jsx
// lib/load-posts.js

export async function loadPosts() {
  const res = await fetch("https://.../posts/");
  const data = await res.json();

  return data;
}
```

`loadPosts`는 `lib/*`와 같은 디렉토리에서 공통 함수로 관리하면 `getStaticProps`와 `API Routes`에서 모두 접근할 수 있다.

```jsx
// api/post

import { loadPosts } from "@lib/load-posts";

export default async function handler(req, res) {
  // ...

  const posts = await loadPosts();

  res.status(200).json(posts);
}
```

```jsx
// pages/blog.js

import { loadPosts } from "@lib/load-posts";

export async function getStaticProps() {
  const posts = await loadPosts();

  return { props: { posts } };
}
```

`API Routes`를 사용하는 대신에 API를 직접 조회하는 함수를 호출해서 불필요한 API 중복 호출을 방지할 수 있다.

<br>

### **3-4. 기타 주의점**

- CORS 헤더를 따로 지정하지 않아서, 기본 값이 `same-origin only` 로 설정되어 있다.
  - 단, [CORS Middleware](https://nextjs.org/docs/api-routes/api-middlewares#connectexpress-middleware-support) 를 통해 변경 가능하다.
- API Routes 는 [next export](https://nextjs.org/docs/advanced-features/static-html-export) 와 함께 사용될 수 없다.

<br>
<br>

## **4. Next API Routes 사용 사례**

### **4-1. 유효성 검사**

`API Routes`를 이용하면 실제 외부 API 호출 전에 요청 및 응답 객체에 접근하여 `Authorization`, `CORS` 등 여러 목적을 위한 프록시 역할을 수행할 수 있다. 다음은 HTTP Request에서 `Authorization` 헤더를 검사해 API 요청 조건을 만족하는지 판단하는 간단한 예시 코드이다.

```jsx
import { NextApiRequest, NextApiResponse } from "next";

export async function handler(req: NextApiRequest, res: NextApiResponse) {
  const role = req.headers.get("authorization");

  if (["user", "admin"].includes(role)) {
    return res.status(401).send("unauthorized");
  }

  // ...
}
```

<br>

### **4-2. 외부 API 주소 마스킹**

API Routes를 이용해 프로젝트에서 사용하는 외부 API를 은닉화 할 수 있다. 만약 실제 외부 API 주소가 `https://external-api.hub/comment`라면 `/api/external` 이라는 요청으로 실제 요청 주소를 숨길 수 있다.

```jsx
// pages/api/external

import { NextApiRequest, NextApiResponse } from "next";

const API_BASE_URL = process.env.API_BASE_URL;

export async function handler(req: NextApiRequest, res: NextApiResponse) {
  // ...

  const requestUrl = `${API_BASE_URL}/${req.path}`;
  const response = await fetch(requestUrl);
}
```

<br>

### **4-3. 쿠키 저장**

애플리케이션을 개발하면서 클라이언트에서 쿠키를 다루다보면 발생하는 이슈가 하나 있는데, 바로 쿠키의 `expires` 문제이다.

- 브라우저별 쿠키 expires 정책 확인하기 : https://www.cookiestatus.com/

위 사이트의 쿠키 정책을 확인해보면 `safari` 나 `brave` 브라우저에서는 `document.cookie` 를 사용해서 쿠키를 설정하면 `최대 expires 설정 기간`이 `7일` 밖에 되지 않는다. 즉, `클라이언트단에서 쿠키를 설정하면 브라우저에 따라 최대 7일까지만 쿠키가 남는다`는 것이다.

개발을 할 때 세션이나 기간에 대한 요구사항이 있으면 일정 기간동안 쿠키에 담아서 확인하는 경우가 생기는데, 이 기간이 7일을 넘어가면 상당히 난감한데 이 때 `API Routes`를 사용해서 Server를 통한 쿠키를 저장하면 expires의 제한이 없이 설정이 가능해진다.

```jsx
export default async function setCookie(req, res) {
  try {
    if (req.method === "POST") {
      if (req?.body) {
        const { key, value, expires } = req.body;

        if (key && value && expires) {
          res.setHeader(
            "Set-Cookie",
            `${key}=${value}; path=/; expires=${expires}; sameSite=lax;`
          );
        }

        res.status(200).json({ data: "set cookie success" });
      } else {
        res.status(400).json({ message: "400 Error" });
      }
    } else {
      res.status(400).json({ message: "400 Error" });
    }
  } catch (e) {
    res.status(400).json(e);
  }
}
```

<br>

### **4-4. 외부 이미지 CORS 우회**

`Next Image`를 사용하다 보면 `remotePatterns` 에 등록된 도메인만 사용을 할 수 있는데, 프론트단에서 외부 이미지를 끌어다 쓰는 경우 `remotePatterns`를 모두 열어주는 수밖에 없다. 하지만 이런 경우에, 외부 이미지를 `API Routes`를 사용해서 한번 우회해서 `base64` 형태로 변환하여 보여주면 `remotePatterns`을 특정 도메인만 한정하면서 외부 이미지를 사용할 수가 있다.

```jsx
function getUrlImageToBase64(url) {
  return axios
    .get(url, {
      responseType: "arraybuffer",
    })
    .then((response) =>
      Buffer.from(response.data, "binary").toString("base64")
    );
}

export default async function getExternalImage(req, res) {
  try {
    if (req.method === "POST") {
      if (req.body?.url) {
        const response = await getUrlImageToBase64(req.body.url);
        res.status(200).json({ data: response });
      } else {
        res.status(400).json({ message: "400 Error" });
      }
    } else {
      res.status(400).json({ message: "400 Error" });
    }
  } catch (e) {
    console.error(e);
    res.status(400).json(e);
  }
}
```

<br>
<br>

## **5. Edge API Routes (experimental)**

`Edge API Routes`는 Next v12에서 추가된 기능으로 기존의 Node.js 기반의 런타임보다 가볍고 빠른 환경을 제공한다. 현재는 베타 버전으로 다음과 같이 edge runtime을 활성화 시키고 싶은 라우트에서 runtime config를 export하면 설정할 수 있다.

```jsx
import type { NextRequest } from "next/server";

export default (req: NextRequest) => {
  return new Response(`Hello, from ${req.url} I'm now an Edge API Route!`);
};

export const config = {
  runtime: "experimental-edge",
};
```

`Edge API Routes`는 표준 WEB API를 기반으로 만들어졌기 때문에 사용 시 [몇 가지 제약사항](https://nextjs.org/docs/pages/api-reference/edge#unsupported-apis)이 있다. 대신 stream response를 통해 보다 빠른 TTFB(Time To First Byte)로 성능 향상을 노려볼 수 있다는 장점이 있다. 요약하면 `Edge API Routes`는 `Edge Runtime`을 사용하고, `API Routes`는 `Node.js Runtime`을 사용한다. `Edge API Routes`는 서버에서 응답을 스트리밍하고 캐시된 파일 (예: `HTML`, `CSS`, `JavaScript`)에 액세스한 후 실행된다. 서버 측 스트리밍은 더 빠른 `Time To First Byte` (`TTFB`)로 성능을 향상시킬 수 있다. 주의할 점은 `getServerSideProps`와 `Edge Runtime`을 함께 사용하면 응답 객체에 액세스할 수 없다. 응답 객체에 액세스해야하는 경우 runtime: 'nodejs'로 Node.js Runtime을 사용해야한다.

<br>
<br>

## **# 레퍼런스**

- [06) Next.js API Routes](https://wikidocs.net/197687#:~:text=%EC%97%90%EC%84%9C%20%EB%AF%B8%EB%93%A4%EC%9B%A8%EC%96%B4%20%EC%82%AC%EC%9A%A9-,Next.js%20API%20Routes%20%EC%86%8C%EA%B0%9C,%EC%89%BD%EA%B2%8C%20%EC%83%9D%EC%84%B1%ED%95%A0%20%EC%88%98%20%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4.)
- [Next.js 의 API routes](https://jake-seo-dev.tistory.com/175)
- [Next.js - API 만들기](https://ppsu.tistory.com/67)
- [[Next js] API Route 십분 활용하기](https://velog.io/@rkd028/Next-js-API-Route-%EC%8B%AD%EB%B6%84-%ED%99%9C%EC%9A%A9%ED%95%98%EA%B8%B0)

<br>
