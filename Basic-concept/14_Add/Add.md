- 트리쉐이킹
- Storybook
- package lock json
- 테스트케이스 관련 : https://lumiloves.github.io/2018/08/21/my-first-frontend-test-code-experience
  - 테스트 케이스 예시
  1. useToggle은 길이가 3인 배열을 리턴한다. [state, onToggle, setState]
  2. 매개변수로 initialState 값을 입력하지 않으면 기본 state 값은 false로 설정된다.
  3. 매개변수로 initialState 값을 입력하면 state에 그 값이 설정된다.
  4. onToggle 함수를 이용해서 state 값을 toggle 할 수 있다.
  5. setState 함수를 이용해서 직접 state 값을 변경할 수 있다.
- 캐노니컬 태그(SEO 관련)
- useTransition
- 구글어낼리틱스 구현 방법
- 스켈레톤 UI 구현 방법
- 초기세팅
  1. yarn create react-app my-app --template typescript
  2.
- 웹팩 동작 과정
- slice 메소드 2차원 복사 다시 공부해보기, 왜 2차원 배열 값 수정 시 같은 참조를 바라보게 되는지.. 아래 예제와 같이 `a[1][0] = 100`에 의해 변경되는 2차원 배열 내부의 값도 원시 타입이기 때문에 새로운 메모리를 생성해서 아래의 나의 예상 값과 같은 결과를 예상했지만 틀렸다.

  ```js
  const a = [100, [1, 2, 3]];
  const b = a;
  const c = a.slice();

  a[0] = 200;
  a[1][0] = 100;

  // 나의 예상값.. 틀렸다..
  console.log(a); // [200, [100, 2, 3]]
  console.log(b); // [200, [100, 2, 3]]
  console.log(c); // [100, [1, 2, 3]]

  // 실제 출력 값
  console.log(a); // [200, [100, 2, 3]]
  console.log(b); // [200, [100, 2, 3]]
  console.log(c); // [100, [100, 2, 3]]
  ```
