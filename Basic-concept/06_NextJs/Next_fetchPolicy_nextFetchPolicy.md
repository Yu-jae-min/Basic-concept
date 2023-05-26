# **fetchPolicy / nextFetchPolicys**

<br>

주중 작업 중 QA를 진행하는데 메인 데이터가 최신 데이터로 반영되지 않는 이슈가 있었다.
분명 DB에도 최신 데이터가 정확히 반영되어 있고 Redis에도 최신 데이터가 정확히 반영되어 있었다.
그래서 쿼리치는 코드를 확인해보았는데 여기서 문제가 있었다.
쿼리를 칠 때 캐시 정책을 조정하기 위해 `fetchPolicy` 속성을 활용하는데 이 속성의 문제였다.
`fetchPolicy` 가 사용되지 않고 `nextFetchPolicy` 가 단독으로 사용되고 있었다.
`nextFetchPolicy` 를 단독으로 사용하는데 왜 문제가 발생했을까?
일단 `nextFetchPolicy` 를 알아보기 전 흔히 알고 있는 `fetchPolicy` 에 대해 짚어보자.

<br>
<br>

## **# fetchPolicy**

<br>

`fetchPolicy` 는 속성 네이밍에서 알 수 있듯이 가져오는 정책을 컨트롤하는 속성이다.
이 속성을 통해 쿼리를 칠 때 서버에서 데이터를 받아올 지, 아니면 아폴로 클라이언트에 의해 저장되어있는
캐시에서 데이터를 받아올 지 결정할 수 있다.

```jsx
const { loading, error, data } = useQuery(GET_DOGS, {
  fetchPolicy: "network-only", // Doesn't check cache before making a network request
});
```

기본적으로 `fetchPolicy` 는 cache-first 정책을 사용한다.
또한 이 외에도 아래와 같은 속성들을 사용하여 정책을 변경할 수 있다.

| option           | description                                                                                                                                                                                       |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| cache-first      | 디폴트이다. 캐시에 해당 데이터가 있으면 캐시를 사용하고 없다면 graphQL서버에 요청한후에 데이터를 캐시하고 데이터를 반환한다. 네트워크 요청을 최소화 한다.                                         |
| cache-only       | 서버에 쿼리를 보내지 않고 캐시만 사용한다. 만약 캐시에 해당 데이터가 없으면 error를 뱉는다.                                                                                                       |
| cache-and-networ | 캐시와 graphQL서버 모두에 대해 전체 쿼리를 실행한다. 서버측 쿼리의 결과로 캐시된 필드가 수정되면 쿼리는 자동 업데이트 된다. 캐시된 데이터를 서버 데이터와 일관되게 유지하며 빠른 응답을 제공한다. |
| network-only     | 캐시를 체크하지 않고 graphQL서버에 대해 쿼리를 실행한다. 쿼리의 결과는 캐시에 저장된다. 캐시 데이터가 있더라도 사용하지 않는다.                                                                   |
| no-cache         | network-only와 비슷하다. 다만 쿼리 결과가 캐시에 저장되지 않는다.                                                                                                                                 |
| standby          | cache-first와 같은 로직을 사용하지만, 기본 필드 값이 변경되어도 쿼리는 자동 업데이트 하지 않는다. refetch 및 updateQueries를 사용하여 수동 업데이트 할 수 있다.                                   |

<br>
<br>

## **# nextFetchPolicy**

<br>

두번째로 `nextFetchPolicy` 또한 `fetchPolicy` 와 같은 속성들을 사용한다.
그럼 이 두 가지 속성의 차이점은 무엇일까? 두 속성의 차이는 바로 타이밍이다. 우왕,,

| props           | description                                                                       |
| --------------- | --------------------------------------------------------------------------------- |
| fetchPolicy     | fetchPolicy는 쿼리가 첫번째 실행될때 사용되는 옵션이다.                           |
| nextFecthPolicy | nextFetchPolicy는 쿼리가 이후 캐시 업데이트에서 어떻게 반응할지 정할 때 사용된다. |

이 두 가지 속성을 아래와 같이 함께 사용할 수 있다.

```jsx
const { loading, error, data } = useQuery(GET_DOGS, {
  fetchPolicy: "network-only", // Used for first execution
  nextFetchPolicy: "cache-first", // Used for subsequent executions
});
```

위에서 정리한 내용을 바탕으로 최신 데이터가 발생되지 않는 이슈에 대해 알 수 있었다.
`nextFetchPolicy` 가 단독으로 사용되고 있었고 사용되지 않은 `fetchPolicy` 는 디폴트 옵션을 바라보고
있었기 때문에 `nextFetchPolicy` 의 옵션과는 무관하게 페이지에 접근하는 경우 캐시에 저장된 데이터를
받아와 해당 이슈가 발생하게 되었던 것이었던 것이었다~~
옵션을 잘 확인하자. 끝!

<br>
<br>

## **# reference**

- fetchPolicy : https://www.apollographql.com/docs/react/data/queries/#setting-a-fetch-policy
- nextFetchPolicy : https://www.apollographql.com/docs/react/data/queries/#nextfetchpolicy

<br>
