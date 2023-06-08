# [react] Map함수 적용 시 Key props

## # Map함수

Map함수는 자바스크립트에서 사용하는 고차 함수 중 하나이다.

```javascript
const numbers = [1, 2, 3, 4, 5];
const doubled = numbers.map((number) => number * 2);
console.log(doubled); // [2, 4, 6, 8, 10]
```

> **고차함수(Higher order function)란?**
> 고차 함수는 함수를 인자로 전달받거나 함수를 결과로 반환하는 함수를 말한다.

<br>

## # 여러개의 컴포넌트 렌더링 하기

컴포넌트 UI를 렌더링 해주는 리액트에서는 여러 개의 컴포넌트를 렌더링 할 때 사용되기도 한다.

```javascript
const numbers = [1, 2, 3, 4, 5];
const listItems = numbers.map((number) => <li>{number}</li>);
```

위와 같은 방식으로 생성 가능하며 컴포넌트를 분리하여 props를 전달받아 props의 갯수
만큼 렌더링하거나, props의 값을 넣어 생성하는 등 다양한 방식으로 컴포넌트를 렌더링 할 수 있다.

하지만 위와 같이 생성할 때 리스트의 각 항목에 key를 넣어야 한다는 경고가 표시된다.

![react_Map함수_적용_시_Key_props_01](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/26de68ff-0ba8-41b1-8821-ed89dcdb96ef)

<br>

## # Key props

Key는 React가 어떤 항목을 변경, 추가 또는 삭제할지 식별하는 것을 도우며 말 그대로
고유한 식별자 역할을 하기 때문에 배열 내부의 엘리먼트에 지정해야 한다.
Key를 선택할 때의 가장 좋은 방법은 데이터의 ID를 key로 사용하는 것이다.

```javascript
const numbers = [1, 2, 3, 4, 5];
const listItems = numbers.map((number) => <li>{number}</li>);
```

만약 안정적인 ID가 없다면 최후의 수단으로 항목의 인덱스를 key로 사용할 수 있다.
하지만 인덱스를 key로 사용 중 배열이 재배열되면 컴포넌트의 state와 관련된 문제가 발생할 수 있다. 컴포넌트 인스턴스는 key를 기반으로 갱신되고 재사용된다. 인덱스를 key로 사용하면, 항목의 순서가 바뀌었을 때 key 또한 바뀔 것이다. 그 결과로, 컴포넌트의 state가 엉망이 되거나 의도하지 않은 방식으로 바뀔 수도 있습니다.
아래의 사항들을 충족해야 인덱스를 key로 사용하는데에 문제가 발생하지 않는다.

> - 목록과 항목은 정적이다. 계산되지 않고 변경되지 않는다.
> - 목록의 항목에는 ID가 없다.
> - 목록은 재정렬되거나 필터링 되지 않는다.

<br>

## # JSX에 map() 포함시키기

```javascript
// JSX에 map() 포함시키기
function NumberList(props) {
  const numbers = props.numbers;
  const listItems = numbers.map((number) => (
    <ListItem key={number.toString()} value={number} />
  ));
  return <ul>{listItems}</ul>;
}
```

JSX를 사용하면 중괄호 안에 모든 표현식을 포함 시킬 수 있다. 그러므로 map() 함수의 결과를 인라인으로 처리할 수 있습니다.

```javascript
// JSX에 map() 인라인으로 처리
function NumberList(props) {
  const numbers = props.numbers;
  return (
    <ul>
      {numbers.map((number) => (
        <ListItem key={number.toString()} value={number} />
      ))}
    </ul>
  );
}
```

<br>

---

<br>

참고자료

1. <a href="https://ko.reactjs.org/docs/lists-and-keys.html" target='_blank'>리스트와 Key</a>
2. <a href="https://robinpokorny.medium.com/index-as-a-key-is-an-anti-pattern-e0349aece318" target='_blank'>Index as a key is an anti-pattern</a>
3. <a href="https://ko.reactjs.org/docs/reconciliation.html#recursing-on-children" target='_blank'>자식에 대한 재귀적 처리</a>
