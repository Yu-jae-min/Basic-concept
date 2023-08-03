# **[React.js] axios와 모듈화**

2023년 08월 04일

<br>

## **1. Axios**

서버와 통신을 하기 위해서 `fetch`와 `axios`를 사용한다. 하지만 나는 더 많은 기능을 제공하는 `axios`를 더 선호하며 자주 사용한다. `axios`의 간략한 사용법은 아래와 같다.

```jsx
// example
axios.post(
  "https://example.com/api/resource",
  { data: "some data" },
  {
    headers: {
      Authorization: `Bearer ${token}`,
      "Content-Type": "application/json",
    },
  }
);
```

1. **URL (String)**: 요청을 보낼 URL 주소
2. **데이터 (Object)**: 요청에 포함될 데이터 객체이다. 예를 들어 POST 요청의 경우, 이 객체가 서버로 보내질 데이터를 담고 있다. 이 매개변수는 HTTP 요청 메서드에 따라 다르게 사용될 수 있다. 예를 들어, GET 요청에서는 이 데이터가 쿼리 매개변수로 변환되어 URL에 추가된다.
3. **옵션 (Object, Optional)**: 요청에 대한 추가적인 옵션을 설정하기 위한 객체입니다. 헤더, 타임아웃 등을 설정할 수 있다. 이 객체의 **`headers`** 속성을 통해 헤더 정보를 설정할 수 있다.

<br>
<br>

## **2. Axios 모듈화**

클라이언트에서 서버로 보내는 요청은 무수히 많기 때문에 모듈화가 거의 필수적이라고 볼 수 있다. 이미 설계된 모듈을 가져와 method, path, param 등을 넣어 사용하여 생산성 향상과 유지보수를 용이하게 할 수 있다. 이럴 때 `axios.create`를 사용할 수 있다.

<br>
<br>

## **3. Axios 인스턴스 만들기**

구현한 코드는 투두 리스트 CRUD를 위한 요청을 만들기 위한 코드이다.
아래와 같이 공통으로 사용할 옵션 `baseURL`, `headers` 등을 지정하여 axios 인스턴스를 생성할 수 있다.

```tsx
// api/axiosInstance.js
import axios from "axios";

export const apiClient = axios.create({
  baseURL: process.env.REACT_APP_API_URL,
  headers: {
    "Access-Control-Allow-Origin": "*",
    "Content-Type": "application/json",
  },
});
```

<br>
<br>

## **4. 요청을 가로채기 위한 Interceptors**

```tsx
// api/axiosInstance.js
apiClient.interceptors.request.use((config) => {
  const accessToken = localStorage.getItem("access_token");

  if (accessToken && config.headers) {
    config.headers["Authorization"] = `Bearer ${accessToken}`;
  }
  return config;
});
```

인스턴스를 만든 후에는 `interceptors`를 활용하여 요청 시 해당 요청을 가로챈 후 추가 로직을 구현할 수 있다. 위 코드는 토큰을 심기 위해 사용하였다.

<br>
<br>

## **5. 사용 예시 및 결론**

```tsx
// api/todos.js
import { apiClient } from "./axiosInstance";

export const getTodos = async () => {
  return apiClient.get("/todos");
};

export const createTodo = async (todo) => {
  return apiClient.post("/todos", { todo });
};

export const updateTodo = async (id, todo, isCompleted) => {
  return apiClient.put(`/todos/${id}`, { todo, isCompleted });
};

export const deleteTodo = async (id) => {
  return apiClient.delete(`/todos/${id}`);
};
```

2-3번에서 구현한 내용을 바탕으로 위와 같이 사용할 수 있다. `interceptors`를 사용함으로써 아래와 같은 이점을 얻을 수 있었다.

1. **일관성 유지**: 인터셉터를 사용하면 여러 곳에서 헤더에 토큰을 추가하는 것을 일관성 있게 관리할 수 있다.
2. **재사용성**: 인터셉터를 설정하면 다른 API 호출에서도 자동으로 헤더에 토큰이 추가된다.
3. **유지보수성 향상**: 코드를 보다 간결하고 관리하기 쉽게 만든다.

토큰 기반 인증 시 간혹 `Unauthorized` 에러가 발생하는 것을 볼 수 있다. 이는 서버로 전송되는 요청에 인증 헤더가 올바르게 추가되지 않았기 때문이다. 따라서 `interceptors`를 사용하여 모든 요청에 헤더를 자동으로 추가하게 되면 토큰이 누락되거나 잘못된 헤더로 인한 문제를 방지할 수 있다.

<br>
