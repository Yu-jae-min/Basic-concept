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

- 클래스의 접근자 프로퍼티인 게터와 세터

접근자 프로퍼티(게터, 세터)
나머지는 데이터 프로퍼티

게터와 세터는 접근자 프로퍼티이고 나머지는 데이터 프로퍼티라고 한다. 게터와 세터는 클래스 바디에 생성해서 사용할 수 있다. 외부에서 접근 시 일반 프로퍼티와 같은 방식으로 접근하여 동작시킬 수도 있으며 멤버 변수와 같은 이름으로 생성하여 멤버 변수에 접근 시 혹은 값 할당 시 멤버 변수의 값을 제어할 수 있다.

1. 바깥 코드에선 접근자 프로퍼티를 일반 프로퍼티처럼 사용할 수 있습니다. 접근자 프로퍼티는 이런 아이디어에서 출발했습니다. 접근자 프로퍼티를 사용하면 함수처럼 호출 하지 않고, 일반 프로퍼티에서 값에 접근하는 것처럼 평범하게 user.fullName을 사용해 프로퍼티 값을 얻을 수 있습니다.

```js
let user = {
  name: "John",
  surname: "Smith",

  get fullName() {
    return `${this.name} ${this.surname}`;
  },
  fullName2() {
    return `${this.name} ${this.surname}`;
  },
};

alert(user.fullName); // John Smith
alert(user.fullName2()); // John Smith
```

2. 비공개로 설정할 필요가 있는 속성을 private로 설정한 후, 이 속성에 접근하여 값을 읽거나, 쓰기 위한 Getter, Setter 함수를 사용하여 속성을 정의할 수 있습니다. private 속성의 경우 클래스 내부에서만 접근 가능하도록 제어한다. 그래서 getter나 setter가 함께 사용된다.

```js
class Plant {

  // 비공개 속성 '종(Species)'
  private _species:string|null = null;

  // getter 함수
  get species(): string {
    return this._species;
  }

  // setter 함수
  set species(value:string) {
    if ( value.length > 3 ) { this._species = value; }
  }

}


/* 인스턴스 생성 ------------------------------------------------ */

let plant = new Plant();

console.log(plant.species); // null

plant.species = '줄기';

console.log(plant.species); // null

plant.species = '푸른 식물';
```

3. getter와 setter를 ‘실제’ 프로퍼티 값을 감싸는 래퍼(wrapper)처럼 사용하면, 프로퍼티 값을 원하는 대로 통제할 수 있습니다.

```js
let user = {
  get name() {
    return this._name;
  },

  set name(value) {
    if (value.length < 4) {
      alert(
        "입력하신 값이 너무 짧습니다. 네 글자 이상으로 구성된 이름을 입력하세요."
      );
      return;
    }
    this._name = value;
  },
};

user.name = "Pete";
alert(user.name); // Pete

user.name = ""; // 너무 짧은 이름을 할당하려 함
```

- next.js SSG vs ISR
- Rest 파라미터 vs Spread 연산자
- TDD
- Next.js
- 스켈레톤UI
- 동적 이미지 로딩
- 컴포넌트 레이지 로딩
- 반응형
- 게시판
- git action
- AWS 배포
- 다크모드
- 다국적 i8
- redux-chunk
- redux-saga
- 빌드 파일 사용
- 웹팩 바벨 옵션
- 커밋 메세지 종류
  (1) feat : 새로운 기능 추가
  (2) fix : 버그 수정
  (3) docs : 문서의 수정
  (4) style : (코드의 수정 없이) 스타일(style)만 변경(들여쓰기 같은 포맷이나 세미콜론을 빼먹은 경우)
  (5) refactor : 코드를 리펙토링
  (6) test : Test 관련한 코드의 추가, 수정
  (7) chore : (코드의 수정 없이) 설정을 변경
