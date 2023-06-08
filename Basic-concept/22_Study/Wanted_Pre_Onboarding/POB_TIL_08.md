## # Today I Learn - 2022.05.16

### # Pre Onboarding Course

#### **리액트 쿼리**

- **리액트 쿼리의 장점**

1. 캐싱
2. get을 한 데이터에 대해 update를 하면 자동으로 get을 다시 수행 (예를 들면 게시판의 글을 가져왔을 때 게시판의 글을 생성하면 게시판 글을 get하는 api를 자동으로 실행)
3. 데이터가 오래 되었다고 판단되면 다시 get (invalidateQueries)
4. 동일 데이터 여러번 요청하면 한번만 요청 (옵션에 따라 중복 호출 허용 시간 조절 가능)
5. 무한 스크롤 (Infinite Queries (opens new window))
6. 비동기 과정을 선언적으로 관리
7. react hook과 사용하는 구조가 비슷함

<br>

- **리액트 쿼리 세팅**

1. react프로젝트에서 yarn install react-query && npm i react-query로 패키지 설치
2. 가장 기본이 되는 index.js에 아래와 같이 QueryClient, QueryClientProvider, ReactQueryDevtools를 import한 후 컴포넌트 배치

```tsx
// root index.js
import { QueryClient, QueryClientProvider } from "react-query";
import { ReactQueryDevtools } from "react-query/devtools";

const queryClient = new QueryClient();

const root = ReactDOM.createRoot(
  document.getElementById("root") as HTMLElement
);
root.render(
  <React.StrictMode>
    <QueryClientProvider client={queryClient}>
      <ReactQueryDevtools initialIsOpen />
      <Routes />
    </QueryClientProvider>
  </React.StrictMode>
);
```

<br>

- **useQuery** : 데이터를 get 하기 위한 api. post, update는 useMutation을 사용

<br>

- **useQuery 사용법**

1. 첫번째 파라미터는 unique Key, 두번째 파라미터는 비동기 함수(api호출 함수(promise))
2. 첫번째 파라미터 unique Key를 사용하면 다른 컴포넌트에서도 호출 가능
3. unique Key는 string과 배열을 받음. 배열로 넘기면 0번 값은 string값으로 다른 컴포넌트에서 부를 값이 들어가고 두번째 값을 넣으면 query 함수 내부에 파라미터로 해당 값이 전달
4. return 값은 api의 성공&실패 여부, api return 값을 포함한 객체
5. useQuery는 비동기로 작동. 즉, 한 컴포넌트에 여러개의 useQuery가 있다면 하나가 끝나고 다음 useQuery가 실행되는 것이 아닌 두 개의 useQuery가 동시에 실행. 여러개의 비동기 query가 있다면 useQuery보다는 useQueries권장
6. enabled를 사용하면 useQuery를 동기적으로 사용 가능

<br>

- **useQuery 문법** : 아래는 useQuery 기본 문법이다.

```tsx
const result = useQuery({
  queryKey,
  queryFn,
  enabled,
});
```

<br>

- **useQuery 사용 예시** : 아래는 useQuery 사용 예시이다.

```tsx
import { useQuery } from "react-query";

const Test = () => {
  // fetch api 함수
  const HandleFetch = (): Promise<any> => {
    return fetch("/mock.json", {}); // promise를 반환해야 하기 떄문에 return해준다.
  };

  // useQuery 사용
  const { isLoading, isError, data, error } = useQuery(
    ["HandleFetch", params1, params2]], // string은 unique Key,
    () => HandleFetch() .then((res) => res.json())
        .then((res) => setTest(res)),
    {
      refetchOnWindowFocus: false, // 사용자가 사용하는 윈도우가 다른 곳을 갔다가 다시 화면으로 돌아오면 이 함수를 재실행 하는 지 여부 설정
      retry: 0, // 호출 실패 시 재호출 몇번 할지
      suspense: true, // suspense 컴포넌트를 사용하여 isLoading을 대체할 수 있다.
      useErrorBoundary: true, // useErrorBoundary 컴포넌트를 사용하여 isError를 대체할 수 있다.
      // refetchInterval: 3000, // 해당 시간마다 반복하여 호출
      onSuccess: () => {
        console.log(test); // 성공 시 실행
      },
      onError() {
        console.log(error); // 실패 시 실행 (401, 404 같은 error가 아니라 정말 api 호출이 실패한 경우만 호출)
      },
    }
  );

  return (
    <ul>
      {isLoading && "loading..."}
      {isError && "Error!"}
    </ul>
  );
};

export default Test;
```

<br>

- **useQuery suspense와 useErrorBoundary** : useQuery의 옵션 중 suspense와 useErrorBoundary를 true로 설정하면 Suspense 컴포넌트와 useErrorBoundary 컴포넌트를 사용할 수 있다.

```tsx
import { useQuery } from "react-query";
import { Suspense } from "react";
import { ErrorBoundary } from "react-error-boundary";

const Test = () => {
  const HandleFetch = (): Promise<any> => {
    return fetch("/mock.json", {});
  };

  const { data } = useQuery(
    ["HandleFetching"],
    () =>
      HandleFetch()
        .then((res) => res.json())
        .then((res) => setTest(res)),
    {
      refetchOnWindowFocus: false,
      retry: 0,
      suspense: true, // suspense 컴포넌트를 사용하여 isLoading을 대체할 수 있다.
      useErrorBoundary: true, // useErrorBoundary 컴포넌트를 사용하여 isError를 대체할 수 있다.
    }
  );

  // 아래와 같이 Suspense, ErrorBoundary 컴포넌트를 사용하며 true가 되면 fallback 컴포넌트가 렌더링 된다.
  return (
    <ul>
      <Suspense fallback={<LoadingPage />}>
        <ErrorBoundary fallbackRender={<ErrorPage />}>
          <ul>
            {data.map((el) => (
              <li key={el.id}>{el.name}</li>
            ))}
          </ul>
        </ErrorBoundary>
      </Suspense>
    </ul>
  );
};
```

<br>

- **useQuery 그 외의 옵션들**

```tsx
const {
   data,
   dataUpdatedAt,
   error,
   errorUpdatedAt,
   failureCount,
   isError,
   isFetched,
   isFetchedAfterMount,
   isFetching,
   isIdle,
   isLoading,
   isLoadingError,
   isPlaceholderData,
   isPreviousData,
   isRefetchError,
   isRefetching,
   isStale,
   isSuccess,
   refetch,
   remove,
   status,
 } = useQuery(queryKey, queryFn?, {
   cacheTime,
   enabled,
   initialData,
   initialDataUpdatedAt
   isDataEqual,
   keepPreviousData,
   meta,
   notifyOnChangeProps,
   notifyOnChangePropsExclusions,
   onError,
   onSettled,
   onSuccess,
   placeholderData,
   queryKeyHashFn,
   refetchInterval,
   refetchIntervalInBackground,
   refetchOnMount,
   refetchOnReconnect,
   refetchOnWindowFocus,
   retry,
   retryOnMount,
   retryDelay,
   select,
   staleTime,
   structuralSharing,
   suspense,
   useErrorBoundary,
 })
```

<br>

- **useQueries** : 여러 개의 비동기를 처리할 경우 사용할 수 있다. promise.all과 마찬가지로 하나의 배열에 각 쿼리에 대한 상태 값이 객체로 들어온다.

- **proxy로 우회하기** : CORS에러를 피하기 위해 package.json에 "proxy" 값을 설정하여 우회할 수 있다.

```json
// package.json
{
  ...
    ...
    "prettier": "^2.6.2",
    "sass": "^1.51.0",
    "sass-loader": "^12.6.0",
    "style-loader": "^3.3.1",
    "stylelint": "^14.8.1",
    "stylelint-config-recess-order": "^3.0.0",
    "stylelint-config-standard-scss": "^3.0.0",
    "stylelint-declaration-strict-value": "^1.8.0",
    "typescript": "^4.4.2"
  },
  "proxy": "http://apis.data.go.kr/"
}

```
