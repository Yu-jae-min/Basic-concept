# # 쓰로틀링(throttling)과 디바운싱(debouncing)

쓰로틀링(throttling)과 디바운싱(debouncing)는 프로그래밍 기법 중 하나이다.

- 쓰로틀링(throttling): 마지막 함수가 호출된 후 일정 시간이 지나기 전에 다시 호출되지 않도록 하는 것, 스크롤을 올리거나 내릴 때 자주 쓰인다.
- 디바운싱(debouncing): 연이어 호출되는 함수들 중 마지막 함수(또는 제일 처음)만 호출하도록 하는 것, ajax 검색에 자주 쓰인다.

> 쓰로틀링(throttling)과 디바운싱(debouncing)는 underscore에도 있는 기능이다. underscore나 lodash를 쓴다면 그 라이브러리의 메소드를 쓰는게 편하다.

<br>

### # 디바운싱(debouncing) 구현

검색어를 input에 입력하여 input의 value가 변할 때마다 api를 요청하여 디바운싱(debouncing)을 구현하였다. 디바운싱 사용 전에는 예를 들어 토끼를 검색 시 'ㅌ', '토', '톢', '토끼'와 같이 input에 값이 변할 경우 모두 요청이 된다. (한글같은 조합형 언어는 더 많이 이벤트가 발생할 수도 있다).

```tsx
// 디바운싱 구현
  const [query, setQuery] = useState(''); // 디바운싱 처리 후 input을 저장하는 state
  const [searchText, setSearchText] = useState<string>(query); // input 입력 값을 그대로 저장하는 state

  // 검색어 저장
  const HandleSearchWord = (event: ChangeEvent<HTMLInputElement>): void => {
    setSearchText(event.currentTarget.value);
  };

  // 디바운스 구현
  useEffect(() => {
    const debounce = setTimeout(() => {
      return setQuery(searchText); // input 값을 저장한 state를 새로운 state에 담는다. 즉 마지막으로 호출될 때의 input value값을 넣는 것이다.
    }, 300); // setTimeout 설정, 이와 같은 경우 최소 300밀리초마다 요청을 보낸다.
    return () => clearTimeout(debounce); // clearTimeout 바로 타이머 제거
  }, [searchText]); // 결국 마지막 이벤트에만 setTimeout이 실행된다.

  // react query api 호출
  const { data, isLoading } = useQuery(
    ['diseaseApi', query],
    () => diseaseApi({ searchText: query }).then((res) => res.data.response.body.items.item),
    {
      refetchOnWindowFocus: true,
      staleTime: 3000,
      cacheTime: Infinity,
      onSuccess: HandleAPICounter,
      onError: HandleAPICounter,
    }
  );

  return (
    ...
          <form>
            <input type='text' value={searchText} onChange={HandleSearchWord} />
          </form>
    ...
```

<br>

### # 쓰로틀링(throttling) 구현

```tsx
function SearchResult({ query }: searchResultProp) {
  const [page, setPage] = useState(1);
  const [result, setResult] = useState<Array<any>>([]);
  const [throttle, setThrottle] = useState(false);

  const handleScroll = () => {
    if (throttle) return;
    if (!throttle) {
      setThrottle(true);
      setTimeout(async () => {
        setPage((page) => page + 1);
        setThrottle(false);
      }, 300);
    }
  };

  useEffect(() => {
    if (query.length === 0 || isEmpty || page === 0) return;
    (async () => {
      try {
        const data = await getSearchResult(query, page);
        if (data.length) setResult((result) =>
        	(result === data ? [...data] : [...result, ...data]));
      } catch (e) {
        setResult([]);
      }
    })();
  }, [page]);


  return (
    <SearchResultBlock onScroll={handleScroll}>
        {result.map((data: searchDataType) =><ProductCard key={data.id}/>}
    </SearchResultBlock>
  );
}
```

<br>

---

<br>

참고자료

- <a href="https://www.zerocho.com/category/JavaScript/post/59a8e9cb15ac0000182794fa" target='_blank'>쓰로틀링과 디바운싱</a>
- <a href="https://velog.io/@skawnkk/debounce-throttle" target='_blank'>Debounce 와 Throttle 리액트로 구현하기</a>
