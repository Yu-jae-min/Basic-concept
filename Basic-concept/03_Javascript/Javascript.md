## # Javascript

<br>

### # 프로그램 실행 과정

- 프로그램 실행 과정

  컴파일 -> 링크 -> 런타임

- 컴파일

  개발자가 작성한 소스코드를 기계어로 변환하는 과정, 컴파일 과정은 컴파일러에 의해 실행되는데 기계어로 변환된 파일은 목적 파일로 만들어진다.

- 링커

  컴파일 후 생성 된 목적 파일들을 합쳐서 하나의 실행 파일을 만들어주는 역할을 한다.

- 로더

  운영체제의 로더는 실행 파일을 로드 한 후 메모리에 적재하고 실행하는 역할을 한다.

  - 프로그램 실행 예시

    1. 프로그램은 처음엔 디스크에 저장되어 있는 상태입니다. (ex. 브라우저, Node.js 앱, 게임 등)

    2. 사용자가 프로그램을 실행하면 운영체제(OS)가 작동해서 실행 파일을 메모리(RAM)에 로드(올리고)하고 코드, 데이터, 스택, 힙 영역을 설정한다.

    3. 이때부터 CPU가 메모리에 적재된 명령어를 읽어 실행하면서 프로그램이 동작하게 된다.

- 런타임

  컴파일 과정을 마친 프로그램이 실행되고 있는 상태(혹은 실행되고 있는 때) 혹은 환경

- 빌드

  소스코드 파일을 실행 가능한 파일로 만드는 일련의 과정을 말한다.
  컴파일 -> 링크 절차가 빌드이다. 빌드가 완성 된 실행 가능한 파일을 사용자가 접근할 수 있는 환경에 배치시키는 것을 배포라고 한다.
  빌드 절차는 아래와 같다.

  1. 코드 작성

  2. 컴파일러가 소스 코드 분석 후(분석 시 문법 오류나 타입체크 에러 시 컴파일 에러 발생) 컴파일하여 0과 1로 이루어진 기계어로 변환하여 목적 파일 생성

  3. 링커가 목적 파일과 외부 라이브러리 등을 연결하여 사용자가 실행할 수 있는 실행 파일 생성

  4. 실행 파일 실행 시 운영체제의 로더를 통해 메인 메모리(RAM)에 적재되고 실행 됨

<br>

### # 컴파일러 vs 인터프리터

- 어셈블리어

  기계어와 일대일 대응이 되는 컴퓨터 프로그래밍의 저급 프로그래밍 언어이다. 기계어는 사람이 이해하기 어렵기 때문에 기계어를 사람이 이해할 수 있게 하기 위해 어셈블리어가 등장했다. 하지만 기계어는 CPU 제조사나 버전에 따라 다르기 때문에 그에 대응되는 어셈블리어도 각각 다르다는 문제가 발생했다. 이 때문에 통일된 언어체계로 작성한 코드의 필요성이 대두되고, 여기서 고급 프로그래밍 언어가 나오게 된다. 또한 고급 프로그래밍 언어를 CPU가 해석할 수 있는 기계어로 번역해주는 것이 컴파일러와 인터프리터이다.

- 컴파일러 인터프리터 차이

  | 특징      | 컴파일러                                       | 인터프리터                                   |
  | --------- | ---------------------------------------------- | -------------------------------------------- |
  | 번역 단위 | 전체 소스를 한 번에 기계어로 변환              | 소스를 한 줄씩 읽고 즉시 실행                |
  | 실행 속도 | 실행 속도 빠르다 (이미 기계어로 변환되어 있음) | 상대적으로 느리다 (실행 시 즉시 해석)        |
  | 실행 파일 | 실행 파일 생성됨 (예: .exe)                    | 생성되지 않음 (바로 실행됨)                  |
  | 에러 발생 | 전체 코드 분석 후 에러 보고                    | 에러가 발생하면 그 이후 코드는 실행되지 않음 |
  | 대표 언어 | C, C++, Go (Java는 컴파일 + JVM 실행) 등       | Python, Ruby, 전통적인 JS 등                 |

- 자바스크립트는 컴파일러일까 인터프리터일까?

  자바스크립트는 원래 인터프리터 언어로 출발했지만 유저 인터렉션이 점점 늘어나고 애플리케이션의 구조가 커지게 되며 실행 속도를 빠르게 개선하기 위해 V8엔진이 등장했고 V8엔진은 JITC(Just In Time Compiler)인 터보팬(TurboFan)과 이그니션 인터프리터(Ignition)를 함께 사용하는 하이브리드 방식으로 동작한다. V8엔진은 반복 수행 정도에 따라 유동적으로 다른 최적화 방식을 사용하여 실행 속도를 높인다.

### # 구글 크롬 Javascript V8엔진의 JITC(Just In Time Compiler)

- V8엔진의 JITC(Just In Time Compiler)

  1. 자바스크립트 엔진 V8엔진에 JS 파일(JS 코드)을 넘긴다.

  2. 파서가 소스 코드를 분석하여 추상 구문 트리(AST) 생성한다.

  3. 이그니션(Ignition) 인터프리터가 추상 구문 트리(AST)를 바이트 코드(중간 코드)로 변환하고 실행한다.

  4. 실행 과정 중 프로파일러가 프로파일링을 통해 자주 반복 실행되는 과열 지점(hot spot)을 찾는다.

  5. 과열 지점(hot spot)을 찾게 되면 해당 코드를 터보팬 컴파일러(TurboFan)으로 전달되어 최적화된 기계어로 컴파일한다.

<br>

### # v8 엔진의 히든 클래스

- v8 엔진의 히든 클래스

  - v8 엔진은 c++로 작성되어 오픈소스로 공개되어 있다.

  - 크롬, nodejs에서 사용하는 자바스트립트 엔진이다.

  - 자바스크립트는 동적 타이핑 언어로 정적 타이핑 언어에 비해 객체 프로퍼티에 접근하는 속도가 느려질 수 있다. 그렇기 때문에 히든 클래스를 통해 객체 프로퍼티 접근 속도를 향상시켰다.

- 히든 클래스 특징

  - 객체는 반드시 하나의 히든 클래스를 참조한다.

  - 히든 클래스는 각 프로퍼티에 대해 메모리 오프셋을 가지고 있다.

  - 동적으로 새로운 프로퍼티가 만들어질 때, 혹은 기존 프로퍼티가 삭제되거나 기존 프로퍼티의 데이터 타입이 바뀔 때는 신규 히든 클래스가 생성되며, 신규 히든 클래스는 기존 프로퍼티에 대한 정보를 유지하면서 추가적으로 새 프로퍼티의 오프셋을 가지게 된다.

  - 히든 클래스는 프로퍼티에 대해 변경이 발생했을 때 참조해야 하는 히든 클래스에 대한 정보를 갖는다.

  - 객체에 새로운 프로퍼티가 만들어지면, 현재 참조하고 있는 히든 클래스의 전환 정보를 확인한 후, 현재 프로퍼티에 대한 변경이 전환 정보의 조건과 일치하면, 객체의 참조 히든 클래스를 조건에 명시된 히든 클래스로 변경시킨다.

- 히든 클래스의 실제 활용 방법

  - 1. 객체를 일관된 방식으로 초기화하라

    ```javascript
    // 나쁨 (동적으로 프로퍼티 추가)
    function makeUserBad() {
      const user = {};
      user.name = "Alice";
      user.age = 30;
      return user;
    }

    // 좋음 (생성 시점에 한 번에 정의)
    function makeUserGood() {
      return {
        name: "Alice",
        age: 30,
      };
    }

    // → 이렇게 하면 V8은 makeUserGood이 반환하는 모든 객체에 대해 같은 히든 클래스를 재사용할 수 있어.
    ```

  - 2. 객체에 프로퍼티를 동적으로 추가하지 말 것

    ```javascript
    const obj = { x: 1 };
    obj.y = 2; // 런타임에 추가됨 → 히든 클래스가 변경됨 → 성능 저하

    // → 가능한 한 초기화 시점에 필요한 모든 프로퍼티를 다 선언하는 게 좋아.
    ```

  - 3. 프로퍼티 추가 순서를 일관되게 유지하라

    ```javascript
    // 히든 클래스가 다르게 만들어짐
    const a = { x: 1, y: 2 };
    const b = { y: 2, x: 1 }; // 순서가 다르면 V8이 다른 히든 클래스로 인식할 수 있음

    // → 초기화 순서도 가능하면 일관되게 유지하는 게 좋아.
    ```

  - 4. 삭제는 하지 말것

    ```javascript
    const obj = { x: 1, y: 2 };
    delete obj.y; // 히든 클래스가 바뀌어서 인라인 캐시 무효화됨

    // → delete 연산은 성능 최적화에 악영향을 줘. 될 수 있으면 사용하지 말 것.
    ```

  - 5. 배열도 조심하라

    ```javascript
    // 배열도 비슷한 최적화가 있는데, 다음은 성능 저하 원인이 될 수 있다:

    // 희소 배열(sparse array)
    const arr = [];
    arr[10000] = 1; // 중간이 비어 있는 배열 → 빠른 배열에서 일반 객체 배열로 퇴화

    // 배열에 다양한 타입 섞기
    const arr = [1, 2, "three"]; // 타입 혼합 → 타입 안정성 깨짐 → 성능 하락
    ```

- 인라인 캐시

  - 자바스크립트에서 객체의 프로퍼티를 읽거나 쓸 때, 최근 접근한 정보(예: 프로퍼티 위치, 히든 클래스 등)를 캐시에 저장해 두고 다음 접근을 빠르게 처리하는 기술이야.

  - 인라인 캐시는 자바스크립트 객체의 프로퍼티 접근을 빠르게 만든다.

  - 같은 구조(히든 클래스)를 계속 사용하면 이 캐시가 잘 작동해서 성능이 매우 좋아져.

  - 다른 구조가 섞이면 캐시가 무효화되고 성능이 떨어짐.

<br>

### # 바이너리 코드, 기계어, 바이트 코드

- 바이너리 코드

  바이너리 코드는 컴퓨터(CPU)가 인식할 수 있는 0과 1로 구성된 이진코드 혹은 데이터, 0과 1로 이루어진 여러 비트가 모여서 만든 코드

- 기계어

  1. 기계어는 0과 1로 이루어진 바이너리 코드이다.

  2. 기계어는 특정한 언어가 아니다. 단지 CPU 제조사에서 CPU를 만들 때 해당 CPU에서 사용하는 명령어 집합을 공개하는데, 이것을 기계어라고 부를 뿐이다. 그렇기 때문에 CPU가 변경되면 기계어가 달라진다.

  3. 같은 회사의 CPU라도 버전 별로 다른 명령을 포함할 수 있으며 다른 회사라도 같은 명령어 집합을 공유할 수도 있다.

  4. 기계어가 이진코드로 이루어졌을 뿐이지 모든 이진코드가 기계어인 것은 아니다. (바이너리 코드 != 기계어) 바이너리 코드는 데이터일뿐, CPU에서 실행되기 위해서는 해당 CPU 아키텍처에 맞는 기계어야 실행할 수 있다.

- 바이트 코드

  1. CPU가 이해할 수 있는 언어가 기계어라면, 바이트 코드는 가상 머신이 이해할 수 있는 0과 1로 이루어진 이진코드

  2. 바이트 코드는 고급 언어로 작성된 소스 코드를 가상 머신이 처리할 수 있는 형태로 변환한 것이다. 예를 들어, Java는 중간 코드인 바이트 코드로 컴파일되어 JVM에서 실행된다. 이는 하드웨어 종속성이 없고 가상 머신만 있으면 다양한 플랫폼에서 실행할 수 있다.

<br>

### # window 객체

- window 객체는 호스트 객체로서 웹 브라우저에서 브라우저 창을 나타내는 객체이다. 또 최상위 객체이기 때문에 전역 객체라고도 하며 자바스크립트의 모든 객체, 전역 함수, 전역 변수들은 자동으로 window 객체의 프로퍼티가 된다. window 객체는 브라우저 환경에서만 존재하며 Node.js와 같은 다른 자바스크립트 환경에서는 window 객체가 존재하지 않는다.

  ```js
  var x = 10;
  console.log(window.x); // 10
  ```

<br>

### # 선택자 메소드 종류

- getElementById

  주어진 id 속성 값을 가진 요소를 선택, 리턴 값은 HTMLElement 객체

  ```js
  document.getElementById("username");
  ```

- getElementsByClassName

  주어진 클래스 이름을 가진 모든 요소를 선택, 리턴 값은 HTMLCollection 객체

  ```js
  document.getElementsByClassName("input");
  ```

- querySelector

  CSS 선택자를 사용하여 첫 번째 요소를 반환, 리턴 값은 Element 객체

  ```js
  document.querySelector("#userForm #username");
  ```

- querySelectorAll

  CSS 선택자를 사용하여 모든 일치하는 요소를 선택, 리턴 값은 NodeList 객체

  ```js
  document.querySelectorAll("#userForm #username");
  ```

<br>

### # Node, Element, HTMLCollection, NodeList

- Node 객체

  DOM API상에 존재하는 모든 것들이 Node 객체이다. 문서 노드(document node), 요소 노드(element node), 속성 노드(attribute node),
  텍스트 노드(text node), 주석 노드(comment node) 등이 있다. 특정 Node를 지정하는 것은 특정 태그 노드와 그 내부에 텍스트 노드 전체를 가리키는 것이다.
  (`ex) <a>하이</a>의 경우 'a' 태그 노드안에 '하이' 텍스트 노드`)

- Element 객체

  Element는 Node의 자식으로 노드 타입 중 하나로 요소 노드 타입이다. 속성 노드(`ex href`)를 가질 수 있는 유일한 노드이다.
  HTMLElement는 Element의 자식이고 Element는 Node의 자식이다. Node는 Object의 자식이다. 이러한 관계를 DOM Tree라고 한다. 특정 Element를 지정하는 것은 텍스트 노드를 제외하고, 흔히 생각하는 태그만 가리키는 것이다. (`ex) <a>하이</a>의 경우 'a' 태그`)

- HTMLCollection 객체

  Element들의 컬렉션, Live 객체(노드 변경 반영 O, 동적 상태), 예를 들어 3개의 li를 생성해놓고 이 li를 HTMLCollection를 반환하는 getElementsByClassName로 선택 후 for 반복문을 통해 색상을 변경하려고 할 때 첫번째, 세번째 li만 색상이 바뀐다.
  이유는 첫번째 루프에서 index 0의 li가 색상이 변하고 실시간으로 노드 변경이 반영되어 HTMLCollection은 두 개의 li만 남게 된다.
  이 때 반복문은 두번째 루프로 index 1의 li 색상이 변경되는 것이다. 그렇기 때문에 최종적으로 첫번째, 세번째 li만 색상이 바뀐다.

  ```html
  <body>
    <ul id="fruits">
      <li class="red">Apple</li>
      <li class="red">Banana</li>
      <li class="red">Orange</li>
    </ul>
    <script>
      const $fruits = document.getElementsByClassName("red");
      for (let i = 0; i < $fruits.length; i++) {
        // li 요소들의 클래스명을 blue로 변경, 첫번째 세번째 li의 클래스가 blue로 변경된다.
        $fruits[i].className = "blue";
      }
    </script>
  </body>
  ```

- NodeList 객체

  Node들의 컬렉션, 대부분 Non-Live 객체(노드 변경 반영 X, 정적 상태), 예를 들어 3개의 li를 생성해놓고 이 li를 NodeList를 반환하는
  querySelectorAll로 선택 후 for 반복문을 통해 색상을 변경하려고 할 때 전체 li 색상이 바뀐다. 이유는 HTMLCollection과 달리 정적 상태를
  유지하므로 중간에 요소의 상태가 바뀌어도 실시간으로 반영되지 않기 때문이다. 하지만 childNodes 프로퍼티가 반환하는 NodeList 객체는
  HTMLCollection 객체와 같이 실시간으로 노드 객체의 상태 변경을 반영하는 live 객체로 동작하므로 주의해야한다.

  ```html
  <body>
    <ul id="fruits">
      <li class="red">Apple</li>
      <li class="red">Banana</li>
      <li class="red">Orange</li>
    </ul>
    <script>
      const $fruits = document.querySelectorAll(".red");
      // li 요소들의 클래스명을 blue로 변경, 전체 li의 클래스가 blue로 변경된다.
      for (let i = 0; i < $fruits.length; i++) {
        $fruits[i].className = "blue";
      }
    </script>
  </body>
  ```

<br>

### # 크로스 브라우징

- 크로스 브라우징이란?

  브라우저마다 렌더링 엔진이 다르기 때문에 렌더링 되는 결과물에 차이가 있을 수 있는데 이 때 모든 브라우저에서 화면을 동일하게 보이게 하는 것이 아닌 모든 브라우저에서 동등한 수준의 정보, 기능 제공을 할 수 있도록 하는 것을 목표로 하는 방법론

- 크로스 브라우징 대응 방법 예시

  1. 타깃 설정 : 모든 브라우저 대응이 어려운 경우 구글 어낼리틱스나 navigator 객체의 userAgent를 통해 서비스를 사용하는 사용자의 기기를 확인 후 많은 점유를 차지하는 기기 순서대로 대응하였다.

  2. 호환성 확인 : 메소드, 스타일 속성 사용 시 Can I Use와 같은 사이트를 통해 브라우저 호환성 체크

  3. 바벨 사용 : 바벨의 플러그인이나 프리셋을 활용하여 자바스크립트 최신 문법을 하위 문법으로 트랜스파일링한다.

  4. 스타일 초기화 : 프로젝트 세팅 시 브라우저 마다 차이가 있는 기본 스타일 값을 초기화 시켰다. reset 파일 내부에서 태그별 기본 margin, padding, border 등을 제거해주거나 list-style 혹은 line-height 등을 기본 값으로 할당한다.

  5. CSS 벤더 프리픽스 사용 (`ex -webkit-display: flex, -moz-display: flex`) : 벤더 프리픽스를 활용하였다.

  6. 폴리필 사용 : 지원하지 않는 메소드의 경우 폴리필 코드를 통해 메소드를 직접 추가한다.

  7. 컨디셔널 코멘트(Conditional Comments) 사용 (`ex <!--[if IE 9 | !IE]>`) : HTML 문서 내에 IE 용 주석을 이용한 방법으로 IE 사용자가 접근하지 못하도록 막았었다.

<br>

### # 브라우저 렌더링 원리

0. 리소스 요청 및 응답 : 사용자가 웹 페이지 접근 시 해당 페이지에 관한 리소스(HTML, CSS, Javascript, 이미지 파일 등)를 서버에 요청 후 응답 받은 뒤 렌더링 진행

1. Parsing : 렌더링 엔진의 HTML 파서가 HTML 파싱하여 DOM(Document Object Model) 트리 생성,
   CSS 파서가 CSS 파싱하여 CSSOM(Css Object Model) 트리 생성

2. Style : 두 트리를 결합하여 렌더 트리 생성

3. Layout/Reflow : 렌더 트리에서 각 노드의 위치와 크기 등 레이아웃 값을 계산한다.

4. Paint/Repaint : 계산된 레이아웃 값을 이용해 각 노드를 화면상의 실제 픽셀로 변환하고, 레이어를 만든다. 레이어가 분리되는 경우는 아래와 같다.

- overflow scroll, auto를 통해 스크롤되는 요소

- position fixed, sticky가 적용되어 있는 요소

- will-change 속성이 적용되어 있는 요소

- `<video>`, `<iframe>`, `<img>` 태그로 로드된 미디어 요소

5. Composite : 레이어를 합성하여 실제 화면에 나타낸다.

6. Javascript : 자바스크립트는 렌더링 엔진이 아닌 자바스크립트 엔진이 처리한다. 자바스크립트 엔진은 자바스크립트 파일을 로드하고 파싱하여 실행하는데
   이 때 정적인 DOM에 javascript가 바인딩되어 하이드레이션이 발생하고 사용자 상호 작용이 가능해진다.

7. Reflow/Repaint : 렌더링 과정을 거친 뒤에 최종적으로 페이지가 그려진다고 해서 렌더링 과정이 다 끝난것이 아니다.
   어떠한 액션이나 이벤트에 따라 html 요소의 크기나 위치 등이 변경되면 그에 영향을 받는 자식 노드나 부모 노드들을 포함하여 Layout 과정을 다시 수행하게 된다.
   이렇게 되면 Render Tree와 각 요소들의 크기와 위치를 다시 계산하게 된다. 이러한 과정을 Reflow라고 한다.
   Reflow만 수행되면 실제 화면에 반영되지 않는다. Render Tree를 다시 화면에 그려주는 과정이 필요하다.
   결국은 Paint 단계가 다시 수행되는 것이며 이를 Repaint라고 한다.

<br>

### # Reflow(레이아웃 재계산) 발생 예시

1. 요소 크기 변경 (width, height, padding, margin 등)

2. 요소의 위치 혹은 정렬 변경 (top, left, right, bottom, position, transform, flex, grid, text-align 등)

3. 요소의 내용 변경 (예: 텍스트 내용 변경, 이미지 크기 변경, 폰트 크기 변경)

4. 디스플레이 속성 변경 (display, visibility, position 등)

5. DOM 트리에서 요소 추가/삭제 (예: appendChild, removeChild)

6. 브라우저 창 크기 조정

<br>

### # Repaint(화면 재그리기) 발생 예시

1. 배경 색상 변경 (background-color, color, border, box-shadow 등)

2. 글꼴 색상 변경 (font-family, font-size, font-weight, color 등)

3. 글꼴 스타일 변경 (font-style, text-transform 등)

4. 투명도 변경 (opacity)

5. 이미지나 비디오 콘텐츠 변경 (src, background-image 변경)

6. 애니메이션 및 변환 (transform, opacity 변화 등)

7. visibility 속성 변경 (단, visibility: hidden은 Reflow가 발생하며, display: none은 Reflow와 함께 트리에서 제거됨)

8. Reflow가 발생한 경우

<br>

### # 브라우저 렌더링 최적화 기법

1. 프레임워크 사용 : Nextjs와 같은 프레임워크를 활용

2. 웹팩 사용 : 웹팩과 같은 모듈 번들러를 사용하여 요청 파일 용량을 줄이고, 요청 파일 개수를 감소시킬 수 있다.

3. 이미지 최적화 : 이미지 사이즈 수정, 압축율이 좋은 이미지 포맷을 사용, 디스플레이 크기별 이미지 설정, 고정 값 사용, 이미지 스프라이트, 이미지 레이지 로딩, 이미지 CDN 사용 등 이미지 최적화 작업을 수행한다.

4. 코드 스플리팅 : 코드 스플리팅을 이용하여 필요한 모듈만 로드하여 요청 지연 시간을 줄인다. 다이나믹 임폴트 문법, 레이지 컴포넌트, 웹팩 엔드 포인트 설정 등의 방법 등이 있다.

5. 리플로우/리페인트 최소화 : 리플로우와 리페인트 발생을 최소화한다. 또한 리플로우가 발생하는 속성보다 리페인트만 발생하는 속성을 우선적으로 사용하는 것이 좋다.

6. 영향을 주는 노드 최소화 : 애니메이션이 자주 발생하거나 크기가 수시로 변하는 요소에 경우 주변 노드들과 연관성을 줄인다.

<br>

### # Promise

- Promise 객체

  Promise는 비동기 처리(비동기 API를 동기적으로 처리)를 위해 사용한다. 자바스크립트 엔진은 싱글 스레드 언어로 한 번에 하나의 테스크만 수행하며
  수행되는 동안 다른 테스크의 수행을 블로킹한다. 이로 인해 무거운 작업이나 네트워크 요청 등에서 블로킹이 발생할 수 있다.
  자바스크립트에서는 이러한 문제를 해결하기 위해 fetch, setTimeout과 같은 비동기 API를 사용한다. 비동기 작업은 js 브라우저 런타임 환경에서 제공되는
  Web API 영역에서 처리된 후, 먼저 완료된 순서에 따라 그 결과(콜백)는 마이크로태스크 큐(Microtask Queue)나 매크로태스크 큐(Macrotask Queue)에 등록되고, 자바스크립트 엔진의 콜 스택이 비워졌을 때 이벤트 루프가 이를 꺼내 콜 스택에 전달하여 실행함으로써 싱글 스레드 환경에서도 마치 멀티 스레드처럼 비동기 처리가 가능해진다. 하지만 메인 스레드는 차단되지 않아 아직 준비되지 않은 데이터에 접근해 undefined나 에러가 발생할 수 있다. 그렇기 때문에 콜백 패턴, Promise, async/await 문법을 활용한 비동기 처리를 통해 비동기 API 처리 시점을 명확하게 한 후 후속 처리를 해야한다. Promise는 pending(대기), fulfilled(이행), rejected(거부) 세 가지 상태를 가지며, .then(), .catch(), .finally() 등의 메서드를 통해 후속 처리를 정의할 수 있다. 하지만 콜백 패턴은 예외 처리의 어려움과 함수의 중첩으로 인해 가독성과 유지보수성이 떨어지는 콜백 지옥(callback hell)을 유발할 수 있다.

  - Promise는 내부적으로 class처럼 동작하는 생성자 함수다. 즉, constructor 함수이기 때문에 new 키워드로 호출해야만 인스턴스를 만들 수 있다.
  - 생성자 함수란 객체를 만들기 위한 함수이다. 쉽게 말해 어떤 틀(템플릿) 역할을 해서 그걸로 여러 개의 객체(인스턴스)를 찍어낼 수 있다.

  ```js
  // promise 사용 전 : 에러 케이스
  const data = fetch("/api/user");
  console.log(data.name); // ❌ undefined 또는 TypeError

  // promise 사용 후 : 정상 케이스
  fetch("/api/user")
    .then((response) => response.json()) // 응답 본문을 JSON으로 파싱 (또한 비동기)
    .then((data) => {
      console.log(data.name); // ✅ 여기서 접근 가능
    })
    .catch((err) => {
      console.error("Error:", err);
    });
  ```

  ```js
  // 콜백 패턴의 문제점 1. : 콜백 지옥(Callback Hell)
  const f1 = (callback) => {
    setTimeout(function () {
      console.log("1번 주문 완료");
      callback();
    }, 1000);
  };

  const f2 = (callback) => {
    setTimeout(function () {
      console.log("2번 주문 완료");
      callback();
    }, 3000);
  };

  const f3 = (callback) => {
    setTimeout(function () {
      console.log("3번 주문 완료");
      callback();
    }, 2000);
  };

  f1(function () {
    f2(function () {
      f3(function () {
        console.log("끝");
      });
    });
  });
  ```

  ```js
  // 콜백 패턴의 문제점 1. : Promise, async/await 활용
  const f1 = () => {
    return new Promise((resolve) => {
      setTimeout(() => {
        console.log("1번 주문 완료");
        resolve();
      }, 1000);
    });
  };

  const f2 = () => {
    return new Promise((resolve) => {
      setTimeout(() => {
        console.log("2번 주문 완료");
        resolve();
      }, 3000);
    });
  };

  const f3 = () => {
    return new Promise((resolve) => {
      setTimeout(() => {
        console.log("3번 주문 완료");
        resolve();
      }, 2000);
    });
  };

  // Promise
  f1()
    .then(() => f2())
    .then(() => f3())
    .then(() => {
      console.log("끝");
    })
    .catch((err) => {
      console.error("에러 발생!", err);
    })
    .finally(() => {
      console.log("모든 주문 처리 종료");
    });

  // async/await
  const handleOrders = async () => {
    try {
      await f1();
      await f2();
      await f3();
      console.log("끝");
    } catch (err) {
      console.error("에러 발생!", err);
    } finally {
      console.log("모든 주문 처리 종료");
    }
  };

  handleOrders();
  ```

  ```js
  // 콜백 패턴의 문제점 2. : 에러 처리의 한계
  try {
    setTimeout(() => {
      throw new Error("Error!");
    }, 1000);
  } catch (e) {
    console.log("에러를 캐치하지 못한다..");
    console.log(e);
  }
  ```

- Promise.all

  여러 개의 Promise를 동시에 실행하고 모두 이행(fulfilled) 되었을 때만 결과를 배열로 반환합니다.
  만약 하나라도 거부(rejected) 되면 전체가 실패로 간주되어 그 에러를 즉시 반환합니다.

- Promise.race

  여러 Promise를 동시에 실행하지만 가장 먼저 완료(이행 or 거부) 된 하나의 결과만 반환합니다.

<br>

### # async/await

- function 앞에 async를 붙여 사용하며 async를 붙이면 해당 함수는 항상 Promise를 반환한다. await는 async 함수 내부에서만 사용되며
  Promise가 처리(settled)될 때까지 함수 실행을 기다리게 만든다. 메인 스레드의 작업들은 멈추지 않고 await을 포함하고 있는 async 함수 내부만 일시정지된다.
  (async 키워드가 붙은 함수를 통째로 백그라운드 Web API로 넘긴다고 보면 된다. async 키워드가 붙은 함수를 비동기 api로 판별하여 바로 실행 후 해당 함수의
  컨텍스트를 콜스택에서 제거한 뒤 해당 함수를 통째로 Web API에서 처리한다고 이해했다. 그렇기 때문에 다음 작업들이 블로팅되지 않는다.)
  그 후 Promise가 처리되면 그 결과와 함께 실행이 재개된다. Promise가 처리되길 기다리는 동안엔 엔진이 다른 일(다른 스크립트를 실행, 이벤트 처리 등)을
  할 수 있기 때문에, CPU 리소스가 낭비되지 않는다. async/await의 사용하는 이유는 then 메소드 사용을 억제하여 코드가 더 간결해지고 가독성이 높아진다는 장점이 있다.

  ```js
  // 예제1 : 일반 비동기 통신
  const TestOne = () => {
    fetch("https://jsonplaceholder.typicode.com/posts/1").then((response) =>
      console.log("1")
    );

    console.log("2");
  };

  console.log("3");

  TestOne(); // 3 -> 2 -> 1

  // 예제2 : async를 사용한 비동기 통신
  const TestTwo = async () => {
    await fetch("https://jsonplaceholder.typicode.com/posts/1").then(
      (response) => console.log("1")
    );

    console.log("2");
  };

  console.log("3");

  TestTwo(); // 3 -> 1 -> 2
  ```

  TestOne 함수에서 3이 먼저 출력되는 이유는 메인 스레드 동작은 멈추지 않기 때문이고 TestOne 함수 내부에서 비동기 api는 다른 작업의 실행을 블로킹하지 않으므로
  2가 먼저 출력된다. 그 후 마지막으로 1이 출력된다. 반면 async/await를 활용한 TestTwo에서는 순서가 다르다.
  3이 먼저 출력되는 이유는 동일하고 TestTwo 함수 내부에서 1이 먼저 출력되는 이유는 비동기 api의 처리 시 다음 작업의 수행을
  블로킹하기 때문에 비동기 처리가 완료된 후 1을 출력하고 그 후 다음 작업을 수행하기 때문에 2를 출력한다.

<br>

### # var, let, const

- var, let, const 기본적인 차이

  1. var : 재선언 O, 재할당 O, 함수 레벨 스코프

  2. let : 재선언 X, 재할당 O, 블록 레벨 스코프

  3. const : 재선언 X, 재할당 X, 블록 레벨 스코프

- 변수가 메모리에 저장될 때 var, let, const의 차이

  변수는 콜스택 내부 실행 환경을 저장하는 객체인 실행컨텍스트의 Environment Record(환경 레코드)에 저장되는데
  var의 경우 환경 레코드의 베리어블 환경(`[[VariableEnvironment]]`), let과 const의 경우 환경 레코드의 렉시컬 환경(`[[LexicalEnvironment]]`)에 저장된다.
  또한 변수에 할당된 값은 콜스택 혹은 메모리 힙에서 주소와 값을 가지고 저장된 데이터인데 이 데이터의 주소를 참조하여 값을 할당하는 것이다.
  만약 참조하는 데이터가 원시 타입이라면 콜스택, 참조 타입이라면 메모리힙에 데이터 주소를 참조한다. 변수에 재선언 재할당의 경우 참조하는 주소 값이 바뀌게 되는 것이고
  const의 경우 재선언 재할당 모두 불가능한데 이 말은 참조하는 주소 값 변경이 불가능하다는 것이다. 다만 참조 타입의 경우 객체 프로퍼티 변경이 가능하다.

  ```js
  const obj = { a: 1 };
  obj.a = 2; // 가능

  obj = { b: 3 }; // ❌ TypeError: Assignment to constant variable
  ```

- Hoisting과 Temporal Dead Zone(TDZ) 관점에서 var, let, const의 차이

  호이스팅은 변수를 유효 스코프 최상단으로 끌어올리는 듯한 현상을 말한다. 즉 선언문 전에 변수에 접근할 경우 접근이 가능한 현상을 말하는 것이다.
  이 때 스코프 시작점과 변수 초기화 시작점까지의 구간을 템퍼럴 데드존이라고 한다. let과 const는 호이스팅이 발생하지 않는 것처럼 보이는데 그 이유는
  변수는 실행 컨텍스트 생성 단계에서 실행 컨텍스트에 변수를 등록하는 선언 단계, 변수를 위한 메모리 확보 후 undefined로 초기화하는 초기화 단계,
  실행 컨텍스트 실행 단계에서 선언문에 도달하여 실제 값을 할당하는 할당 단계로 나누어 생성되는데 var는 선언, 초기화가 동시에 이루어지고
  let과 const는 선언, 초기화가 나누어 이루어지는데 const는 초기화와 동시에 할당이 필수적으로 이루어져야한다.
  그렇기 때문에 실행 컨텍스트 실행 단계에서 선언문 변수 선언문 이전에 let, const에 접근하게 될 경우 아직 초기화 및 할당이 이루어지지 않은 상태이기 때문에 에러가 발생하게 된다.
  결론은 let, const의 경우 선언문 이전에 접근 시 실행 컨텍스트에 등록되어 있는 상태로 호이스팅은 발생하지만 초기화 및 할당된 값이 없기 때문에 에러가 발생하는 것이다.

<br>

### # Prototype

- 프로토타입이란?

  프로토타입을 통해 모든 객체들이 메소드와 속성들을 상속받을 수 있다. `[[Prototype]]`은 모든 객체가 가지는 숨겨진 내부 슬롯이다.
  `[[Prototype]]`은 `__proto__ (던더 프로토)`로 접근 가능하다. 또한 함수 객체는 `[[Prototype]]`과 함께 `prototype 프로퍼티`도 가지는데
  이 `prototype 프로퍼티`는 그 함수로 생성된 인스턴스가 상속받게 될 객체를 지정한다. 즉 부모 객체의 인스턴스인 자식 객체는 자신의 부모 `prototype 프로퍼티`를
  가리키는 `[[Prototype]]`을 가지고 있는 것이다. 함수 객체의 `prototype 프로퍼티`에는 자식에게 상속하기 위한 값이 담겨져있고
  `prototype 프로퍼티` 내부에 `constructor 프로퍼티`는 자기 자신을 생성한 함수를 가리키고 있다. 이처럼 객체의 `[[Prototype]]`, `prototype 프로퍼티`는
  console.dir을 통해 확인해볼 수 있다.

  - `[[Prototype]]`은 모든 객체가 가지는 숨겨진 내부 슬롯 (`__proto__`로 접근 가능)
  - `prototype 프로퍼티`는 함수 객체만 가지고 있는 일반 프로퍼티, 예를 들어 Array 함수 객체의 경우 `prototype 프로퍼티`에 map 메소드를 내장하고 있음

- 프로토타입 체인이란?

  어떤 객체에서 존재하지 않는 프로퍼티나 메소드에 접근하려고 하면 자바스크립트는 해당 객체의 `[[Prototype]]`이 가리키는 링크를 따라 위로 거슬러 올라가며
  자신의 부모 역할을 하는 프로토타입 객체의 프로퍼티 혹은 메소드를 차례대로 탐색한다. 이 연결 구조를 프로토타입 체인이라 한다.
  프로토타입 체인의 최상단은 Object의 `prototype 프로퍼티`(Object.prototype)이며, 프로토타입 체인의 종점이므로 `[[Prototype]]` 체인이 없다.

  - 표준 빌트인 객체 (Standard Built-in Objects) 중 생성자 함수 : ECMAScript 사양에 정의된 객체들. Object, Array, Function, String, Number, Boolean, Date, RegExp, Error, Promise 등

  - 예를 들어 배열 관련 메소드들을 사용할 수 있는 것도 내장 함수 객체인 Array에 `prototype 프로퍼티`를 상속받아 사용할 수 있는 것이다.

<br>

### # Closure

- 자신을 포함하고 있는 외부함수보다 내부함수가 더 오래 유지되는 경우, 외부 함수가 실행되어 제거된 후 내부함수가 호출되더라도
  외부함수의 지역 변수에 접근할 수 있는데 이러한 함수를 클로저라고 한다. 이것이 가능한 이유는 내부 함수 렉시컬 환경에 `[[Scopes]](스코프)`는 자신이 생성될 때의
  환경을 기억하기 때문이다. `[[Scopes]]`는 함수를 호출할 때가 아니라 함수를 어디에 선언하였는지에 따라 결정된다. 이러한 방식을 렉시컬 스코핑이라고 한다.
  console.dir을 통해 내부 함수를 콘솔에 찍어보면 `[[Scopes]]`에 클로저(`ex Closure (outerFunc)`)가 저장되어 있고 이 클로저에 이미 실행되어 사라진
  외부함수의 값이 담겨있는 것을 확인할 수 있다. 즉 가비지 컬렉터에게 이 함수가 아직 필요하다고 알려 메모리에 해당 값을 유지시키는 것이다.
  이러한 클로저를 활용하여 데이터를 보존하거나 정보의 은닉을 통해 의도치 않은 에러를 방지할 수 있다.

  ```js
  function outerFunc() {
    var x = 1;
    return function inner() {
      console.log(x * 2);
    };
  }

  var inner = outerFunc(); // outerFunc의 실행 컨텍스트는 사라지지만
  inner(); // inner가 outerFunc의 x에 접근 가능 → 클로저

  console.dir(inner);
  console.dir(outerFunc);
  ```

<br>

### # this

- this란 무엇인가?

  this란 자신이 속한 객체 또는 자신이 생성할 인스턴스를 가리키는 자기 참조 변수이다.
  실행 컨텍스트의 생성 단계에서는 전역 객체에 바인딩되며 실행 단계에서 동적으로 결정된다.

  1. 일반 함수의 this : 기본적으로 전역 객체(window)를 가리키지만, 엄격 모드(use strict mode)에서는 undefined

  2. 생성자 함수 this : 생성할 인스턴스

  3. 객체의 메소드 this : 메소드의 this는 객체를 가리키지만, 내부 함수에서는 전역 객체를 가리킬 수 있음.
     이를 해결하려면 this를 변수에 할당하거나, 화살표 함수를 사용할 수 있다.

     ```js
     const obj = {
       name: "Alice",
       sayName: function () {
         const self = this; // `this`를 self에 할당
         console.log(self.name); // self는 obj를 가리킴

         function inner() {
           console.log(self.name); // self는 obj를 가리킴
         }
         inner();
       },
     };

     obj.sayName(); // "Alice", "Alice"
     ```

- this 바인딩 메소드 bind, call, apply

  일반 함수의 경우 bind, call, apply 함수 메소드를 통해 명시적으로 this를 바꿀 수 있다. 세 가지 메소드의 공통점은 첫번째 파라미터로 this를 바인딩할 수 있고
  두번째 파라미터로 해당 함수에 인자를 전달한다. 차이점은 bind는 this바인딩 후 함수를 실행하지 않고, call은 this바인딩 후 함수를 실행하는데
  함수의 인자를 개별로 전달하고 apply는 this바인딩 후 함수를 실행하는데 함수의 인자를 배열로 묶어 전달한다.

  ```javascript
  var obj2 = { c: "d" };

  function b() {
    console.log(this);
  }

  b(); // Window
  b.bind(obj2).call(); // obj2
  b.call(obj2); // obj2
  b.apply(obj2); // obj2
  ```

- 일반함수의 this vs 화살표 함수의 this

  일반 함수는 호출 방식에 따라 this에 바인딩할 객체를 결정하고 화살표 함수는 언제나(메소드 사용해도 바뀌지 않음) 상위 스코프 객체를 this에 바인딩한다.

  ```js
  const obj = {
    value: 100,
    normalFunc: function () {
      console.log("normalFunc this:", this); // obj
    },
    arrowFunc: () => {
      console.log("arrowFunc this:", this); // 전역 객체(window or undefined in strict mode)
    },
  };

  obj.normalFunc(); // this → obj
  obj.arrowFunc(); // this → 상위 스코프 (여기선 전역)
  ```

<br>

### # 일반 함수와 화살표 함수의 차이

<br>

- 일반 함수와 화살표 함수의 차이

  1. this 바인딩 방식 : 일반 함수는 호출 방식(객체의 메소드로 호출, this 바인딩 메소드에 의한 호출 등)에 따라 this가 결정되고,
     화살표 함수는 언제나 상위 스코프 this를 가리킨다.

  2. 생성자 함수로 사용 가능 여부 : 일반 함수는 생성자 함수로 사용 가능하지만 화살표 함수는 생성자 함수로 사용할 수 없다.
     왜냐하면 prototype 프로퍼티를 가지고 있지 않기 때문이다.

  3. arguments 객체 : 함수 생성 시 일반 함수는 인자가 arguments 객체에 바인딩 되지만 화살표 함수에서는 인자가 arguments 객체에 바인딩 되지 않는다.

- 화살표 함수 사용 이유

  코드를 간결하게 작성할 수 있고 코드가 간결하기 때문에 생산성 향상 및 가독성이 좋아진다.

<br>

### # javascript의 use strict 모드

- 자바스크립트 언어의 문법을 보다 엄격히 적용하여 오류를 발생시킬 가능성이 높거나 자바스크립트 엔진의 최적화 작업에 문제를 일으킬 수 있는 코드에 대해 명시적인 에러를 발생시킨다. 전역에서 선언하면 모든 소스코드가 대상이고, 로컬(함수 내부)로 선언하면 함수 내에서만 대상이 된다. use strict 모드에서는 삭제가 불가능한 프로퍼티를 삭제하거나 함수의 매개변수를 중복해서 사용하는 것 등이 금지된다. use strict 모드를 사용하면 엄격한 동작으로 코드 작성 단계(컴파일 타임)에서 에러를 사전에 발견할 수 있다는 장점과 디버깅이 쉬워진다는 장점이 있다. 하지만 단점의 경우 대부분의 브라우저가 use strict 모드를 지원하지만 아주 오래된 브라우저의 경우 엄격 모드의 코드가 다른 방식으로 동작할 수 있다.

  ```js
  // case 1. 중복 매개변수
  function example(a, a) {
    console.log(a); // 에러 발생!
  }

  // case 2. 삭제 불가능한 프로퍼티
  delete Object.prototype; // 에러 발생!

  // case 3. this 바인딩
  function test() {
    console.log(this); // `undefined`, 엄격 모드에서는 `this`가 `undefined`
  }

  test();
  ```

<br>

### # ECMAScript

- ECMAScript

  ECMA 인터내셔널이라는 비영리 표준화 기구에서 정보 통신에 대한 표준을 제정하는데 ECMAScript는 ECMA 인터내셔널이 명세한 스크립트 언어를 어떻게 만들어야 하는지를 설명하는
  일종의 표준화 설명서이고, JavaScript는 ECMAScript의 사양을 바탕으로 만들어진 언어이다.

- ECMAScript 버전별 차이

  | 버전              | 발표년도 | 주요 기능                                                                                                                                       |     |                                                       |
  | ----------------- | -------- | ----------------------------------------------------------------------------------------------------------------------------------------------- | --- | ----------------------------------------------------- |
  | **ES6 (ES2015)**  | 2015     | `let`, `const`, 클래스, 화살표 함수, 템플릿 리터럴, 디스트럭처링, `Promise`, `Map`/`Set`, `module (import/export)`, `Symbol`                    |     |                                                       |
  | **ES7 (ES2016)**  | 2016     | `Array.prototype.includes`, 지수 연산자 `**`                                                                                                    |     |                                                       |
  | **ES8 (ES2017)**  | 2017     | `async/await`, `Object.entries()`, `Object.values()`, `String.padStart`, `String.padEnd`                                                        |     |                                                       |
  | **ES9 (ES2018)**  | 2018     | Rest/Spread 연산자 개선, 비동기 반복문 (`for await...of`), 정규식 개선 (lookbehind 등)                                                          |     |                                                       |
  | **ES10 (ES2019)** | 2019     | `Array.flat()`, `Array.flatMap()`, `Object.fromEntries()`, `trimStart/trimEnd`                                                                  |     |                                                       |
  | **ES11 (ES2020)** | 2020     | `optional chaining (?.)`, `nullish coalescing (??)`, `Promise.allSettled`, `globalThis`, BigInt                                                 |     |                                                       |
  | **ES12 (ES2021)** | 2021     | `String.replaceAll`, `Promise.any`, `WeakRef`, \`logical assignment operators (&&=,                                                             |     | =, ??=)`, `structuredClone\` (브라우저는 약간 지연됨) |
  | **ES13 (ES2022)** | 2022     | 클래스 필드, 정적 블록, `at()` 메서드 (`array.at()`), `Error.cause`, top-level await (모듈)                                                     |     |                                                       |
  | **ES14 (ES2023)** | 2023     | `Array.prototype.findLast`, `findLastIndex`, `Symbol.prototype.description`, `hashbang`(`#!`), 정적 `Array.prototype.toSorted()` 등 불변 메서드 |     |                                                       |

- ECMAScript 최신 버전 상세

  - Array.prototype.findLast() & Array.prototype.findLastIndex()

    기존의 find()는 앞에서부터 찾았지만, 이제 뒤에서부터도 찾을 수 있다.

    ```js
    const arr = [1, 2, 3, 4, 5, 6];

    arr.findLast((n) => n % 2 === 0); // 6
    arr.findLastIndex((n) => n % 2 === 0); // 5
    ```

  - Array.prototype.toSorted(), toReversed(), toSpliced(), with()

    기존 배열을 변경하지 않고 새로운 배열을 반환한다. (불변성 유지)

    ```js
    // toSorted
    const arr = [3, 1, 2];
    const sorted = arr.toSorted(); // [1, 2, 3]
    console.log(arr); // [3, 1, 2] (원본 그대로)
    ```

    ```js
    // toReversed
    const reversed = arr.toReversed(); // [2, 1, 3]
    ```

    ```js
    // toSpliced
    const arr = [1, 2, 3];
    const newArr = arr.toSpliced(1, 1, 99); // [1, 99, 3]
    ```

    ```js
    const arr = [0, 1, 2];
    const newArr = arr.with(1, 100); // [0, 100, 2]
    ```

  - Symbol.prototype.description

    기존에는 Symbol("foo").description이 명세상 없었지만, 이제는 표준적으로 접근 가능하다.

    ```js
    const sym = Symbol("example");
    console.log(sym.description); // "example"
    ```

  - Hashbang(#!) 지원

    Node.js에서 스크립트를 실행할 때 사용되는 #! 문법을 이제 JS 스펙으로 인정한다.

    ```js
    #!/usr/bin/env node

    console.log("Hello from Node script");
    ```

  - 기타 개선 사항

    - JSON.parse가 BOM(Byte Order Mark)을 무시하도록 명확히 정의됨

    - RegExp 개선 사항 (정규식 엔진 명세 업데이트)

    - Private 필드가 더 엄격하게 동작하도록 처리 (클래스 보안 향상)

<br>

### # 순수 함수

- 순수 함수란

  1. 동일한 인자 전달 시 항상 동일한 값 반환

  2. 외부에 영향을 주거나 받지 않음 (사이드 이펙트 x)

- 순수 함수를 사용하는 이유

  1. 반환되는 결과가 예측 가능하므로 실행 시점이 중요하지 않음

  2. 다른 순수 함수들과 조합하여 사용하는 것이 용이하여 재사용성이 증가

  3. 테스트가 간단함

<br>

### # 스코프(Scope)

- 스코프란?

  스코프는 변수나 함수 등 참조 대상 식별자를 구분할 수 있는 유효 범위를 말한다. 실행 컨텍스트 생성 단계에서 결정되며 이 스코프가 이어진 형태를 스코프 체인이라고 한다.

- 전역 스코프 / 함수 레벨 스코프 / 블록 레벨 스코프 / 렉시컬 스코프

  1. 전역 스코프 (Global scope) : 전역에서 참조할 수 있다. 전역 스코프를 갖는 변수를 전역 변수라고 한다.

  2. 지역 스코프 or 함수 레벨 스코프(Local scope or Function-level scope) : 함수 코드 블록이 만든 스코프로 함수 자신과 하위 함수에서만 참조할 수 있다. 지역 스코프를 갖는 변수를 지역 변수라고 한다.

  3. 블록 레벨 스코프(block-level scope) : 블록 레벨 스코프란 코드 블록({…})내에서 유효한 스코프를 의미한다. 함수나 조건문 코드 블록이 블록 레벨 스코프이다.

  4. 렉시컬 스코프(Lexical scope) : 함수를 어디서 호출하는지가 아니라 어디에 선언하였는지에 따라 상위 스코프가 결정되는 것을 말한다. 자바스크립트는 렉시컬 스코프를 따르며 실행컨텍스트 생성 단계에서 결정된다.

- 스코프 체인

  자신의 스코프에서 참조하고자 하는 식별자를 찾은 후 존재하지 않는다면 상위 스코프로 올라가며 마지막 최상위 스코프까지 순차적으로 식별자를 찾게 된다. 이와 같이 자신의 스코프부터 최상위 스코프까지 스코프가 연결되어 있는 형태를 스코프 체인이라고 한다.

  ```js
  var a = "전역 변수";

  function outer() {
    var b = "outer 함수 변수";

    function inner() {
      var c = "inner 함수 변수";

      console.log(a); // 전역 스코프 참조 -> 전역 변수
      console.log(b); // outer 함수의 지역 스코프 참조 -> outer 함수 변수
      console.log(c); // inner 함수의 지역 스코프 참조 -> inner 함수 변수
    }

    inner();
  }

  outer();
  ```

<br>

### # 이벤트 전파

- 이벤트 전파란?

  ![javascript_이벤트전파_01](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/d986b842-c9d3-4f50-ae72-7ab3572a1844)

  DOM 이벤트(마우스를 클릭하거나 키보드를 누르는 등 사용자 행위)의 흐름은 캡처링, 타깃, 버블링 단계로 나누어서 이루어진다.
  캡처링은 이벤트가 발생한 요소부터 하위 요소로 이벤트가 전파되는 단계이고 타깃 단계는 이벤트가 실제 타깃 요소에 전달되는 단계이며 별도로 처리되지 않는다.
  버블링은 이벤트가 발생한 요소부터 상위 요소로 이벤트가 전파되는 단계이다. 이벤트 흐름은 항상 캡처링으로 시작하여 버블링으로 종료된다.
  예를 들어 캡처링이 `Window -> Document -> <html> -> <body> -> <div> -> <button>` 와 같은 흐름으로 발생하고 있을 때 `<button>`에서 타깃 요소에
  이벤트가 전달된 후 버블링은 반대인 `<button> -> <div> -> <body> -> <html> -> Document -> Window`로 이벤트가 전달되는 것이다.
  또한 이벤트 리스너 등록 시 capture 파라미터의 불리언 값을 통해 캡처링 단계에서 이벤트를 감지할 지, 버블링 단계에서 이벤트를 감지할 지 결정할 수 있다.

  ```js
  div.addEventListener("click", clickEvent, { capture: true });
  ```

  예를 들어 div -> ul -> li 순으로 DOM을 구성하고 li에 이벤트 리스너를 등록한 후 버블링 단계에서 이벤트가 실행되도록 설정해놓는다.
  이 때 사용자가 li를 클릭하여 클릭이라는 이벤트를 발생시키게 되면 div -> ul -> li의 캡쳐링 단계를 지나쳐 li -> ul-> div의 버블링 단계를 거치는데
  버블링 단계 중 이벤트 리스너가 달린 li를 지나칠 때 이벤트가 발생하게 되며 이벤트 리스너가 등록되지 않은 ul과 div에서는 이벤트가 발생하지 않는다.

  ```js
  // li에만 리스너를 등록
  document.getElementById("li").addEventListener("click", function () {
    console.log("clicked li");
  });
  ```

  ```html
  <div id="div">
    <ul id="ul">
      <li id="li">Click me</li>
    </ul>
  </div>
  ```

- event.target vs event.currentTarget

  1. event.target : 실제 이벤트가 발생하는 요소

  ```html
  // 브라우저에서 "테스트"라는 텍스트를 클릭했을 때 span이 event.target // 실제
  클릭되는 요소는 버튼이 아닌 "테스트"라는 텍스트
  <button onClick="{onClick}">
    <span>테스트</span>
  </button>
  ```

  2. event.currentTarget : 이벤트 리스너가 달린 요소

  ```html
  // 브라우저에서 "테스트"라는 텍스트를 클릭했을 때 button이 event.currentTarget
  // 실제 클릭되는 요소는 버튼이 아닌 "테스트"라는 텍스트지만, 이벤트 리스너는
  버튼에 달려있음
  <button onClick="{onClick}">
    <span>테스트</span>
  </button>
  ```

<br>

### # event.preventDefault, event.stopPropagation

- event.preventDefault()

  이벤트가 발생했을 때 브라우저가 기본적으로 수행하는 행동을 막는다. 예를 들어 a태그 링크 이동, form태그의 submit 기능과 같은 경우가 있다. 이벤트 전파는 막히지 않는다.

- event.stopPropagation()

  이벤트 전파를 막는다.

<br>

### # 이벤트 바인딩

- 이벤트 바인딩이란?

  이벤트가 발생한 요소와 이벤트(콜백 함수)를 연결해주는 것이 이벤트 바인딩이다. 이벤트 바인딩의 방법은 총 3가지 방법이 있는데
  HTML 이벤트 핸들러, DOM 이벤트 핸들러, DOM EventListener을 이용한 방법이 있다.

  1. HTML 이벤트 핸들러 방법

  HTML 이벤트 핸들러 방식은 HTML 요소의 이벤트 Attribute에 이벤트 핸들러를 대응시키는 방법이다. 이 방법은 HTML과 Javascript가 혼용이 되는데,
  간단한 이벤트 처리에는 빠르게 사용할 수 있지만 자바스크립트와 HTML이 혼합되어 코드가 복잡해질 수 있다.

  ```html
  <button class="btn" onmouseover="alert('Mouse is over the button!')">
    Hover over me
  </button>
  <button class="btn" onclick="myFunction()"></button>
  ```

  2. DOM 이벤트 핸들러 방법

  DOM 이벤트 핸들러 방식은 자바스크립트에서 DOM 요소의 이벤트 속성을 사용하여 이벤트를 바인딩하는 방법이다.
  HTML과 Javascript가 혼용되는 문제는 해결되었지만 하나의 이벤트에 하나의 핸들러만 등록할 수 있는 단점이 있다.
  즉, 한 이벤트에 여러 개의 핸들러를 바인딩하려면 addEventListener를 사용해야 한다.

  ```html
  <button id="myBtn">Click me</button>;
  ```

  ```javascript
  var myBtn = document.getElementById("myBtn");

  // 첫 번째 바인딩된 이벤트 핸들러 => 실행되지 않는다.
  myBtn.onclick = function () {
    alert("Button clicked 1");
  };

  // 두 번째 바인딩된 이벤트 핸들러 => 첫 번째 이벤트 핸들러를 덮어쓴다.
  myBtn.onclick = function () {
    alert("Button clicked 2");
  };
  ```

  3. DOM 이벤트 리스너 방법

  addEventListener 함수를 이용하여 대상 요소(Event Target)에 이벤트를 바인딩하고, 해당 이벤트가 발생했을 때
  실행될 콜백 함수를 지정하는 방식이다. addEventListener 함수의 인자는 이벤트 타입(ex onclick), 실행 될 콜백함수, 캡처링 사용여부 순으로 전달할 수 있다.
  DOM 이벤트 리스너 방법은 하나의 이벤트에 여러 핸들러를 추가할 수 있고 버블링과 캡처링을 지원한다.

  ```js
  // 예시 target.addEventListener(type, listener[, useCapture]);

  var el = document.getElementById("outside");

  el.addEventListener(
    "click",
    function () {
      modifyText("four");
    },
    false
  );
  ```

<br>

### # undefined / undeclared / null 차이점

- undefined

  변수 선언 후 값이 할당되지 않은 상태, 타입 undefined

- undeclared

  선언 자체가 되지 않은 변수, 타입 없음 에러 발생

- null

  의도적인 빈 값, 타입 객체

<br>

### # IntersectionObserver

- IntersectionObserver는 WebAPI로 비동기적으로 실행되며 관찰 대상과 뷰포트의 교차점을 관찰하고 뷰포트 안으로 들어오는 시점에 정보를 제공하는 기능. 무한 스크롤이나 페이지 스크롤 시 다른 컨텐츠나 이미지 레이지 로딩 등에 사용

  ```html
  <div class="example">
    <img
      src="https://picsum.photos/600/400/?random?0"
      alt="random image"
      class="image-default"
    />
    <img
      data-src="https://picsum.photos/600/400/?random?1"
      alt="random image"
      class="image"
    />
    <img
      data-src="https://picsum.photos/600/400/?random?2"
      alt="random image"
      class="image"
    />
    <img
      data-src="https://picsum.photos/600/400/?random?3"
      alt="random image"
      class="image"
    />
    <img
      data-src="https://picsum.photos/600/400/?random?4"
      alt="random image"
      class="image"
    />
    <img
      data-src="https://picsum.photos/600/400/?random?5"
      alt="random image"
      class="image"
    />
    <img
      data-src="https://picsum.photos/600/400/?random?6"
      alt="random image"
      class="image"
    />
    <img
      data-src="https://picsum.photos/600/400/?random?7"
      alt="random image"
      class="image"
    />
  </div>
  ```

  ```js
  // IntersectionObserver의 options를 설정합니다.
  const options = {
    root: null,
    // 타겟 이미지 접근 전 이미지를 불러오기 위해 rootMargin을 설정했습니다.
    rootMargin: "0px 0px 30px 0px",
    threshold: 0,
  };

  // IntersectionObserver 를 등록한다.
  const io = new IntersectionObserver((entries, observer) => {
    entries.forEach((entry) => {
      // 관찰 대상이 viewport 안에 들어온 경우 image 로드
      if (entry.isIntersecting) {
        // data-src 정보를 타켓의 src 속성에 설정
        entry.target.src = entry.target.dataset.src;
        // 이미지를 불러왔다면 타켓 엘리먼트에 대한 관찰을 멈춘다.
        observer.unobserve(entry.target);
      }
    });
  }, options);

  // 관찰할 대상을 선언하고, 해당 속성을 관찰시킨다.
  const images = document.querySelectorAll(".image");
  images.forEach((el) => {
    io.observe(el);
  });
  ```

<br>

### # Object Literal, Template Literal

- Template Literal이란?

  Template Literal은 벡틱으로 감싸 사용하는 문자열 표기법이다. 다른 문자열이나 객체 등을 편리하게 결합하여 사용할 수 있다.

- Object Literal이란?

  Object Literal은 중괄호 안에 프로퍼티를 정의하여 객체를 생성한다. 손쉽게 객체를 생성하기 위해 사용한다.

<br>

### # 얕은 복사와 깊은 복사

- 얕은 복사와 깊은 복사

  얕은 복사란 객체를 복사할 때 객체만 복사하여 기존 객체와 복사된 객체가 같은 참조를 가리키는 복사를 말한다. 깊은 복사란 객체를 복사할 때 객체와 참조 값을 모두 복사하여 기존 객체와 복사된 객체의 참조가 완전히 끊어진 복사를 말한다. 자바스크립트에서 값은 원시값과 참조값 두 가지 데이터 타입의 값이 존재한다. 자바스크립트에서 원시 타입의 경우 값이 수정(새로운 값 할당)되면 새로운 메모리 공간에 독립적인 값을 저장하기 때문에 깊은 복사가 되고 참조 타입의 경우 값이 수정(새로운 요소 추가)되면 원본을 직접 수정하므로 얕은 복사가 된다. 얕은 복사의 경우 메모리를 새로 할당받지 않아 메모리 공간을 아낄 수 있지만 원본이 변화될 수 있는 위험이 있고 깊은 복사는 메모리 공간을 새로 할당받아 메모리 공간을 소비하지만 원본이 변화되지 않아 안전하다.

  ```js
  const a = 1;
  const b = 1;
  const c = [];
  const d = [];

  console.log(a === b); // true, 원시 데이터이므로 값을 비교하여 값이 같기 때문에 true
  console.log(c === d); // false, 참조 데이터이므로 참조를 비교하여 참조가 다르기 때문에 false
  ```

- 얕은 복사 방법

  1. slice() : 기본적으로 얕은 복사를 수행한다. 1차원 배열을 복사하면 깊은 복사처럼 보이는데 원시 타입은 기본적으로 깊은 복사이므로 깊은 복사처럼 보인다. 하지만 2차원 배열을 복사하면 얕은 복사가 된다.

  2. Object.assign() : 1차원 객체는 깊은 복사, 2차원 객체는 얕은 복사

  3. Spread 연산자 : 1차원 객체는 깊은 복사, 2차원 객체는 얕은 복사

- 깊은 복사 방법

  1. structuredClone()

  ```javascript
  const original = { a: 1, b: { c: 2 } };
  const copy = structuredClone(original);
  ```

  2. JSON.parse(JSON.stringify(obj))

  3. Lodash 라이브러리의 cloneDeep 메소드

<br>

- slice가 1차원 배열은 깊은 복사, 2차원 배열은 얕은 복사를 수행하는 이유

  ```javascript
  // 1차원 참조 타입 복사
  const originalArray = [1, 2, 3, 4];
  const copiedArray = [...originalArray];
  originalArray[0] = 100;

  console.log(originalArray); // [100, 2, 3, 4]
  console.log(copiedArray); // [1, 2, 3, 4]
  ```

  Array.prototype.slice(), Object.assign(), Spread 연산자(…) 모두 기본적으로 얕은 복사를 수행한다. 즉, 깊은 복사처럼 보이지만 실제로 깊은 복사를 수행하는 것이 아니다. 여기서 얕은 복사란 복사란 복사 대상인 참조 타입의 내부 요소들의 참조 주소를 새로운 배열의 참조로 복사하는 것을 의미한다. 즉 아래 예시에서는 originalArray가 가리키는 0x00000F1 배열의 내부 요소들의 참조 주소 0x00000F3,0x00000F4,0x00000F5,0x00000F6 자체를 originalArray이 가리키는 0x00000F2 배열의 참조 주소로 복사하는 것이다.

  여기서 1차원 참조 타입의 값을 복사할 때 깊은 복사처럼 보이는 이유는 1차원 참조 타입의 값은 원시 타입이기 때문이다. 만약 1차원 참조 타입의 값이 원시 타입이 아닌 참조 타입이라면 1차원 참조 타입이 아닌 2차원 참조 타입이다. 결국 1차원 참조 타입의 값은 무조건 원시 타입이라는 것인데 원시 타입의 값은 새로운 값으로 변경될 때 새로운 메모리 영역을 생성하고 그 메모리 주소로 참조 주소를 변경하게 된다.

  위 코드에서 originalArray[0] = 100;를 통해 index 0의 값을 변경할 때 해당 값은 1(0x00000F3)인 원시 타입이기 때문에 100(0x00000F7)으로 참조 주소가 변경되게 된다. 이 때 copiedArray는 복사될 때 참조하고 있던 참조 주소들을 여전히 참조하고 있으므로 변경되지 않는다. 그렇기 때문에 originalArray 의 참조 주소만 변경되게 된다.

  그렇기 때문에 결론적으로 깊은 복사처럼 보이게 된다.

  ![원시타입과_참조타입의_메모리_공간_할당_07](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/25a1bf8f-0fba-4a36-8864-de39d7cba7ae)

  ```javascript
  // 2차원 참조 타입 복사
  const originalArray = [
    [1, 2],
    [3, 4],
  ];
  const copiedArray = [...originalArray];
  originalArray[0][0] = 100;

  console.log(originalArray); // [[100, 2], [3, 4]]
  console.log(copiedArray); // [[100, 2], [3, 4]]
  ```

  위 코드에서 `Spread` 문법을 활용한 2차원 배열의 복사는 메모리 상에서 아래와 같이 동작한다. 우선 위에서 말한 것과 같이 얕은 복사를 수행하여 `originalArray`가 가리키는 `0x00000F1` 배열의 내부 요소들의 참조 주소`0x00000F3`, `0x00000F4`를 `copiedArray`가 가리키는 `0x00000F2` 배열의 내부 value로 복사하게 된다.

  이 때 해당 배열은 2차원 배열이므로 `0x00000F3`, `0x00000F4` 배열 또한 내부에 배열을 가리키는 참조 주소를 가지고 있게 된다. 아래 이미지에서 `[0x00000F5, 0x00000F6]`과 `[0x00000F7, 0x00000F8]`를 말한다.

  그 후 `originalArray[0][0] = 100;`를 통해 index 0 배열(`0x00000F3`)의 index 0(`0x00000F5`) value 참조 주소가 `0x00000F9`로 변경되게 된다. 콜스택에 두 식별자가 가리키고 있는 메모리힙에 참조 주소 `0x00000F1`, `0x00000F2` 배열의 내부 value는 여전히 `0x00000F3`, `0x00000F4` 로 동일하기 때문에 콘솔에 찍히는 값은 동일하게 된다.

  ![원시타입과_참조타입의_메모리_공간_할당_08](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/ae872617-5971-4762-ab62-cbe7a270c85b)

- 결론

  기본형은 값이 복사되고, 참조형은 주소(참조)가 복사된다!

  - 참조 복사 예시

    ```js
    const original = [1, 2, 3];
    const copy = original; // 참조를 복사

    copy[0] = 100;

    console.log(original); // [100, 2, 3]
    console.log(copy); // [100, 2, 3]

    // original과 copy는 서로 다른 변수입니다.
    // 하지만 둘 다 같은 배열 객체를 참조합니다.
    // 즉, 참조(주소)가 복사됐을 뿐, 가리키는 대상은 동일합니다.
    ```

  - 1차원 배열 (기본형 요소)

    ```js
    const originalArray = [1, 2, 3, 4];
    const copiedArray = [...originalArray];
    ```

    | 요소 타입  | 복사 방식    | 결과        |
    | ---------- | ------------ | ----------- |
    | 1, 2, 3, 4 | 값 자체 복사 | 서로 독립적 |

    - 각각 number → 기본형(primitive)

    - 값이 복사됨 → 두 배열은 완전히 다른 메모리에 같은 값들을 가지고 있음

    - 그래서 originalArray[0] = 100 해도 copiedArray는 영향 없음

    ```md
    originalArray: [ 1, 2, 3, 4 ] → 값 복사
    copiedArray: [ 1, 2, 3, 4 ] → 완전 독립
    ```

  - 2차원 배열 (참조형 요소)

    ```js
    const originalArray = [
      [1, 2],
      [3, 4],
    ];
    const copiedArray = [...originalArray];
    ```

    | 요소 타입      | 복사 방식     | 결과               |
    | -------------- | ------------- | ------------------ |
    | [1, 2], [3, 4] | 참조만 복사됨 | 내부 배열은 공유됨 |

    - 요소가 배열 → 배열은 객체 → 참조형(reference type)

    - [...originalArray]는 바깥 배열을 새로 만들지만, 안에 들어 있는 [1, 2], [3, 4]는 복사되는 게 아니라 주소(참조)만 복사됨. 그래서 originalArray[0][0] = 100 하면, 같은 내부 배열을 보고 있는 copiedArray[0][0]도 100이 되어버림

    ```mb
    originalArray:   [ ref1, ref2 ]       → ref1 → [1, 2]
    copiedArray:     [ ref1, ref2 ]       → 같은 내부 배열 참조

    즉,
    originalArray[0] === copiedArray[0] → true
    ```

<br>

### # 함수 선언식, 함수 표현식 설명

- 함수 선언식

  1. 함수 선언을 function으로 시작하는 함수

  2. 함수명이 정의되어 있어야 함

  3. 호이스팅 발생

  ```javascript
  function 함수명() {
    구현 로직
  }
  ```

- 함수 표현식

  1. 정의한 function을 별도의 변수에 할당한 함수

  2. 익명 함수 사용 가능

  3. 선언부만 호이스팅 되므로 호이스팅의 영향을 받지 않음

  ```javascript
  var 함수명 = function () {
    구현 로직
  };
  ```

<br>

### # 클래스

- 클래스는 생성자 함수와 같이 상속, 캡슐화 등 객체지향 프로그래밍을 위한 객체의 인스턴스를 생성하기 위해 사용한다. 생성자 함수와의 차이점은 클래스는 항상 strict mode(엄격 모드)로 동작하고 필수적으로 new 키워드와 함께 생성해야하는 등 조금 더 엄격하게 동작하고 사용법에도 차이가 있다. 클래스는 내부에 constructor라는 유니크한 프로퍼티를 가지고 있는데 이 constructor 내부에 선언된 변수들이 상속되는 것이다. 이 변수들을 클래스 필드라고 하며 인스턴스의 프로퍼티가 된다. 또한 클래스 코드 블럭 내 constructor를 제외한 영역을 클래스 바디라고 하며 클래스 바디에는 메소드를 선언하게 된다. 만약 클래스 바디에 클래스 필드를 선언하게 되면 에러가 발생한다. 이렇게 클래스를 생성한 뒤 new 키워드를 통해 인스턴스를 생성할 수 있다. 생성된 인스턴스는 클래스의 클래스 필드를 직접 가지고 있으며 클래스 바디에 선언된 메소드는 프로토타입을 통해 참조하여 사용하게 된다. 또한 클래스는 extends 키워드를 통해 다른 클래스에 상속을 구현할 수 있다. extends를 통해 상속받은 클래스로 생성된 인스턴스 또한 상속한 클래스의 클래스 필드를 직접 가지고 있으며 프로토타입 체인을 통해 클래스가 가지고 있는 메소드를 상속 받아 사용할 수 있게 된다. 또한 게터와 세터같은 접근자 프로퍼티를 클래스 바디에 생성하여 멤버 변수에 접근 시 혹은 값 할당 시 멤버 변수의 값을 제어할 수도 있다.

  ```js
  // ES5 생성자 함수
  const User = function (name, age) {
    this.name = name;
    this.age = age;
    this.showName = function () {
      console.log(this.name);
    };
  };

  const mike = new User("Mike", 30);

  // ES6 클래스
  class User2 {
    constructor(name, age) {
      this.name = name; // 클래스 필드
      this.age = age; // 클래스 필드
    }
    showName() {
      // 프로토타입 프로퍼티에 존재
      console.log(this.name);
    }
  }

  const tom = new User2("Tom", 19);
  ```

<br>

### # 클래스 vs 생성자

![클래스vs생성자](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/1f2955b6-cd59-4c0f-8778-29d81c1b6175)

<br>

### # 원시형 타입, 참조형 타입

- 원시형 타입

  String, Number, Boolean, Undefined, Null, BigInt, Symbol

  - 값 자체가 메모리에 저장됨 (immutable, 값 복사됨)

  - BigInt 타입

    Number 타입은 2⁵³ - 1(Number.MAX_SAFE_INTEGER)만큼의 정수만 안전하게 표현가능하지만 BigInt 타입은 길이의 제약 없이 정수를 다룰 수 있게 해주는 숫자형이다.
    정수 뒤에 n을 붙여 사용하거나 BigInt를 호출하여 인자로 숫자를 넘겨줄 수 있다. 나누기에 경우 소수점 없이 정수만 반환한다.

- 참조형 타입

  원시 타입을 제외한 나머지, 함수, 객체, 배열 등, 참조값(메모리 주소)이 저장됨 (mutable, 얕은 복사 시 원본 영향)

<br>

### # CDN(Content Delivery Network)

- CDN이란

  CDN은 “콘텐츠 전송 네트워크(Content Delivery Network)”의 약자이다. 전 세계 여러 지역에 엣지 서버(=캐시 서버)를 두고, 사용자에게 요청이 왔을 때 가장 가까운 서버에서 정적 콘텐츠를 전달하여 응답 속도와 성능을 향상시키는 기술이다.

  - 정적 컨텐츠

    - JS, CSS, HTML

    - 이미지, 폰트, 동영상

    - PDF, JSON 파일 등

- CDN 동작 방식

  1. 사용자가 웹사이트에 접속

  2. CDN은 사용자의 위치(지리적 거리)를 기반으로 가장 가까운 엣지 서버를 선택

  3. 엣지 서버에 캐시된 콘텐츠가 있으면 → 바로 응답 (빠름!)

  4. 없다면 → 원래 서버(오리진 서버)에서 받아오고, 엣지 서버에 캐시 저장

  5. 다음 사용자는 캐시된 데이터를 빠르게 받음

- CDN 장점

  1. 분산된 서버를 통해 서버의 트래픽 부하를 줄일 수 있다.

  2. 물리적으로 가까운 서버에 요청하므로 응답이 빠르다.

  3. 디도스(의도적으로 트래픽을 폭주시켜 해당 시스템의 서비스가 거부되도록 하는 공격) 공격과 같은 일부 악의적인 공격으로부터 상대적으로 안전하다.

- CDN vs 로드밸런서

  트래픽을 분산한다는 점에서 CDN과 로드 밸런서와 비슷해보일 수 있지만 엄연히 다르다.

  - CDN : CDN은 정적 콘텐츠를 사용자에게 가까운 서버에서 빠르게 전달하는 것

  - 로드 밸런서 : 요청을 여러 서버에 고르게 분산하여 서버 부하를 감소시키는 방법

- CDN 적용 방법 예시

  1. 웹사이트 배포 시 정적 파일을 S3에 저장하고, CloudFront(AWS CDN)로 전 세계 배포

  2. 폰트, 라이브러리(JS 라이브러리 등)를 jsDelivr나 unpkg 같은 퍼블릭 CDN에서 불러오기

<br>

### # 실행 컨텍스트

- 실행 컨텍스트란?

  실행 컨텍스트란 코드 실행에 필요한 환경을 저장해놓은 객체이다. 실행 시점에 따라 전역 컨텍스트, 함수 컨텍스트로 구분되며 자바스크립트 엔진의 콜스택에 쌓이게 된다.
  자바스크립트 런타임의 구조는 자바스크립트 엔진의 콜스택, 메모리 힙과 브라우저의 백그라운드인 Web API, 테스크 큐, 이벤트 루프로 구성되어 있다. 프로그램이 시작되면 가장 먼저 전역 실행 컨텍스트가 생성되고, 콜 스택에 쌓인다. 이후 함수가 호출될 때마다 해당 함수의 실행 컨텍스트 생성 단계가 시작하며 콜 스택의 가장 위에 추가된다.

- 실행 컨텍스트의 생성 단계, 실행 단계

  실행 컨텍스트의 생명 주기는 생성 단계와 실행 단계로 나눌 수 있다. (전역 컨텍스트는 프로그램 시작 시, 함수 컨텍스트는 호출문을 만나면 생성 단계가 시작된다)

  - 1. 생성 단계

    - 환경 레코드에 식별자 정보(변수, 객체, 함수 등)를 저장

    - 스코프 체인 형성

    - this 바인딩을 수행

  - 2. 실행 단계

    - 실제 코드가 위에서 아래로 실행되며, 변수에 값이 할당되고 함수가 호출됨

    - 만약 실행 단계에서 함수 호출 문을 만나게 되면 전역 컨텍스트에 실행 단계를 멈춘 뒤 새로운 함수 컨텍스트를 콜스택에 쌓는다. 그 후 새롭게 쌓인 함수 컨텍스트로 제어권을 넘긴 뒤 생성 단계와 실행 단계를 거치게 된다. 실행 단계가 종료된 후 다시 제어권을 받아와 이어서 실행한다.

    - 비동기 처리

      - 실행 단계에서 비동기 API(fetch, setTimeout 등)인 경우 WEB API로 해당 작업을 넘기고 해당 작업은 콜스택에서 제거한다. 그 후 메인 스레드 작업은 지속한다. 메인 스레드 작업을 수행하며 생성 단계와 실행 단계를 반복하는데 이벤트 루프가 콜스택을 감시하며 콜스택이 비워지는 경우 Web API 넘겨져 처리되어 테스크 큐에 쌓인 비동기 콜백 함수 선입선출 방식으로 밀어넣게 된다. 이 때 한번에 다 밀어넣는 것이 아닌 하나를 밀어넣고 하나가 실행되어 콜스택이 비어질 때 또 하나를 밀어넣는 방식으로 수행된다.

- 자바스크립트 브라우저 런타임 구조

  1. 콜스택

  - 실행 컨텍스트를 저장하는 스택 자료 구조, 실행 컨텍스트 객체 내부 렉시컬 환경에 원시 타입의 데이터가 저장된다.

  - 싱글 스레드 흐름을 관리, 함수 호출 시 위에 쌓이고 함수 실행이 끝나면 제거된다. (후입선출)

  2. 메모리 힙

  - 참조 타입(객체, 배열 등)의 데이터가 저장되는 공간

  - 구조화되지 않은 큰 저장소로, 객체는 주소(참조값)로 접근된다

  3. WebAPI

  - 웹 브라우저에서 제공하는 API로 AJAX나 Timeout등의 비동기 작업을 실행한다.

  - 자바스크립트 자체가 아닌 브라우저 환경에서 제공됨

  4. 테스크 큐

  - WebAPI에서 넘겨받은 콜백 함수를 저장하며 선입선출 방식이다.

  5. 이벤트 루프

  - 콜스택이 비어있는지 계속 감시하며, 콜스택이 비어있다면 테스크 큐의 작업을 콜스택으로 밀어넣는다. (선입선출)

  - 먼저 마이크로태스크(Promise.then 등)를 처리한 후 매크로태스크(Task Queue)를 처리함

<br>

### # 이터러블, 이터레이터와 제너레이터

- 이터러블

  이터러블 객체는 반복 가능한 객체를 말한다. 대표적인 이터러블 객체로는 배열과 문자열이 있다. 또한 기본적으로 이터러블 객체는 for of 반복문을 통해 반복이 가능하다. 이터러블과 비슷한 유사 배열이라는 개념도 있는데 유사 배열은 index와 length 프로퍼티를 가지고 있어 배열처럼 보이는 객체를 말한다. 유사 배열 또한 Symbol.iterator을 통해 이터러블 객체로 만들어 반복할 수 있다.

  ```js
  // 이터러블 예시
  const array1 = ["a", "b", "c"];

  for (const element of array1) {
    console.log(element); // "a" -> "b" -> "c"가 순서대로 출력
  }

  // 유사 배열 예시
  const arrayLike = {
    0: "Hello",
    1: "World",
    length: 2,
  };
  ```

- 제너레이터

  제너레이터는 일반 함수와 다르게 여러 개의 값을 필요에 따라 하나 씩 반환할 수 있다. 또한 제너레이터는 반복 가능한 이터러블 객체이다. function 뒤에 `*`을 붙여 제너레이터 함수를 생성할 수 있고 제너레이터 함수의 리턴 값은 일드(yield)와 리턴(return)이며 next 메소드로 순차적으로 호출할 수 있고 return을 호출할 때 함수가 최종적으로 종료된다. 대표적인 사용 예로 리덕스에서 비동기 api를 사용하기 위해 사용하는 미들웨어인 리덕스 사가에서 제너레이터 문법을 사용한다.

  ```js
  function* generateSequence() {
    yield 1;
    yield 2;
    return 3;
  }

  let generator = generateSequence();

  let one = generator.next();

  alert(JSON.stringify(one)); // {value: 1, done: false}

  for (let value of generator) {
    console.log(value); // 1, 2
  }
  ```

<br>

### # 객체지향 프로그래밍 OOP

- 객체지향 프로그래밍(OOP, Object Oriented Programming)란?

  Object Oriented Programming이며 객체지향 프로그래밍이라고 한다. 상태나 행위를 가진 독립적인 여러 객체들을 레고 블럭처럼 조립하여 프로그래밍하는 방식을 말한다. 상속, 다형성, 캡슐화, 추상화 등의 특징과 모듈화를 통해서 재사용성을 증가시키고 유지보수가 용이하도록 한다. 자바스크립트는 프로토타입 기반의 객체지향 프로그래밍 언어이다.

- 객체지향 프로그래밍 특징

  1. 상속

     부모 객체의 메소드나 변수를 자식 객체가 그대로 물려받을 수 있다. 예를 들어 클래스에서는 상위 클래스의 클래스 필드를 하위 클래스가 상속받는다. javascript에서는 `class`, `extends`, 프로토타입 등이 예시이다.

  2. 다형성

     같은 객체임에도 상황에 따라 다르게 동작할 수 있다. 예를 들어 함수는 매개변수에 따라 출력 값이 다르다. javascript에서는 자식 클래스 메서드 재정의(오버라이딩, 동적 바인딩) 등이 예시이다.

  3. 캡슐화

     메소드나 변수를 하나로 묶고 필요에 따라 접근 권한을 나누어 외부에서 접근하지 못하게 제한을 두는 것을 말한다. 캡슐화를 통해 객체의 손상을 방지하고 정보를 은닉할 수 있다. javascript에서는 클로저, private 필드 등이 예시이다.

  4. 추상화

     연관된 메소드나 변수를 따로 묶어 표현한다. 예를 들어 동물이라는 변수에 강아지, 고양이를 배열에 담아 할당하는 것을 말한다. javascript에서는 함수나 모듈로 추상화할 수 있다.

- 객체지향 프로그래밍의 5가지 설계 원칙, SOLID 원칙

  1. 단일 책임의 원칙

     모든 클래스는 각각 하나의 기능만 가진다.

     ```javascript
     // ❌ 역할이 너무 많음
     class UserManager {
       createUser() {}
       saveToDB() {}
       sendWelcomeEmail() {}
     }

     // ✅ 분리
     class UserCreator {
       createUser() {}
     }
     class UserRepository {
       saveToDB() {}
     }
     class EmailService {
       sendWelcomeEmail() {}
     }
     ```

  2. 개방 폐쇄 원칙

     클래스, 모듈, 함수 등 모든 구성요소는 확장에는 열려있고, 변경에는 닫혀있어야한다.

     ```javascript
     // ✅ 새로운 할인 정책 추가할 수 있지만 기존 코드는 건드리지 않음
     class DiscountPolicy {
       getDiscount(price) {
         return price;
       }
     }

     class BlackFridayDiscount extends DiscountPolicy {
       getDiscount(price) {
         return price * 0.8;
       }
     }
     ```

  3. 리스코프 치환 원칙

     부모 클래스의 자리에 자식 클래스를 넣어도 정상적으로 동작하여야 한다. 자식 클래스는 부모 클래스의 역할을 정확히 해내야한다는 뜻이다.

     ```javascript
     class Bird {
       fly() {}
     }

     class Penguin extends Bird {
       fly() {
         throw new Error("Penguins can't fly");
       } // ❌ LSP 위반
     }
     ```

  4. 인터페이스 분리 원칙

     하나의 인터페이스에 너무 많은 역할을 담지 말고, 클라이언트에 맞는 최소한의 인터페이스만 제공해야 함

     ```javascript
     // ❌ 하나의 인터페이스에 너무 많은 기능
     interface Machine {
       print();
       scan();
       fax();
     }

     // ✅ 역할에 따라 인터페이스 분리
     interface Printer { print(); }
     interface Scanner { scan(); }
     ```

  5. 의존 역전 원칙

     상위 모듈은 하위 모듈에 종속되면 안되고 하위 모듈은 상위 모듈에서 정의한 추상화(추상 타입)에 의존해야 한다.

     ```javascript
     class EmailService {
       sendEmail() {
         /* send logic */
       }
     }

     class UserController {
       constructor(emailService) {
         this.emailService = emailService; // 추상 인터페이스처럼 생각
       }
       registerUser() {
         this.emailService.sendEmail();
       }
     }
     ```

<br>

### # 함수형 프로그래밍(Function Programming)

- 함수형 프로그래밍에 대해 설명해달라.

  함수형 프로그래밍은 순수 함수(pure function)와 보조 함수(조합 함수)의 조합을 통해 상태 변화(state mutation)와 부작용(side-effect)을 피하려는 프로그래밍 패러다임이다. 조건문, 반복문보다는 고차 함수, 재귀, 함수 조합 등을 통해 문제를 해결하며, 불변성(immutability) 유지가 핵심 특징이다.

- 함수형 프로그래밍에 개념에서 순수함수란 무엇인가?

  순수함수는 같은 입력이 주어지면, 같은 출력을 반환해야하는 함수를 말한다. 즉 사이드 이펙트가 없는 함수를 말한다.

- 객체지향 프로그래밍 vs 함수형 프로그래밍 차이

  | 항목        | 객체지향 프로그래밍 (OOP) | 함수형 프로그래밍 (FP) |
  | ----------- | ------------------------- | ---------------------- |
  | 중심 개념   | 객체 (상태 + 행위)        | 함수와 데이터의 변환   |
  | 상태 변경   | 허용됨 (mutable)          | 지양 (immutable)       |
  | 동작 방식   | 메시지 전달, 상호작용     | 함수 호출, 조합        |
  | 주된 요소   | 클래스, 인스턴스, 메서드  | 순수 함수, 고차 함수   |
  | 코드 스타일 | 명령형 (imperative)       | 선언형 (declarative)   |

- 선언형 vs 명령형

  - 비교

    | 구분        | 선언형(Declarative)         | 명령형(Imperative)                    |
    | ----------- | --------------------------- | ------------------------------------- |
    | 개념        | 무엇을 할지 기술            | 어떻게 할지 기술                      |
    | 초점        | 결과에 집중                 | 절차/과정에 집중                      |
    | 코드 스타일 | 간결하고 읽기 쉬움          | 세부 흐름이 드러남                    |
    | 대표 예     | SQL, React, HTML, 함수형 JS | for 루프, DOM 직접 조작, JS 일반 함수 |

  - React 예시

    - 선언형

      ```jsx
      // React에서는 “어떻게 DOM을 생성할지”가 아니라 “이런 UI를 원해요”라고 선언하는 것
      return <div>Hello</div>;
      ```

    - 명령형

      ```javascript
      const div = document.createElement("div");
      div.textContent = "Hello";
      document.body.appendChild(div);
      ```

  - 문제풀이 예시

    - 선언형

      ```javascript
      // 로직 흐름을 전부 기술해야 함
      const nums = [1, 2, 3, 4];
      const result = nums.filter((n) => n % 2 === 0).map((n) => n * n);

      console.log(result); // [4, 16]
      ```

    - 명령형

      ```javascript
      // 내부 동작은 추상화되어 있음 (for문 없음)
      const nums = [1, 2, 3, 4];
      const result = [];

      for (let i = 0; i < nums.length; i++) {
        if (nums[i] % 2 === 0) {
          result.push(nums[i] * nums[i]);
        }
      }

      console.log(result); // [4, 16]
      ```

<br>

### # 절차지향 프로그래밍(procedural programming)

- 절차지향 프로그래밍이란?

  순차적인 처리가 중요시 되며 프로그램 전체가 유기적으로 연결되도록 만드는 프로그래밍 기법이다. 컴퓨터의 작업 처리 방식과 유사하기 때문에 객체지향 프로그래밍에 비해 처리가 빨랐지만 하드웨어의 발달로 인해 소프트웨어 개발 속도가 하드웨어의 처리 속도를 따라가지 못하는 상황이 발생하였다. 이로 인해 하드웨어의 성능을 깎아내리면서 소프트웨어 개발 속도를 빠르게 할 수 있는 객체지향 프로그래밍이 탄생하게 되었다. 절차지향 프로그래밍은 프로그램 전체가 연결되어 있기 때문에 유지보수가 어렵고 재사용성이 낮다. 객체지향 프로그래밍은 캡슐화, 상속, 다형성, 추상화 같은 특징으로 재사용성을 증가시키고 모듈화를 통해 유지보수를 용이하도록 하였다. 반면 어떤 모듈에 있는 하나의 기능만 필요하더라도 모듈 전체를 가져와야 하기 때문에 절차지향 프로그래밍보다 프로그램 사이즈가 더 커질 수도 있다.

- 절차지향 프로그래밍 VS 객체지향 프로그래밍 차이

  객체지향 프로그래밍이 절차지향 프로그래밍의 단점을 보완하기 위해 등장했지만 엄연히 다른 개념이다. 절차지향 프로그래밍의 경우 데이터를 중심으로 코드가 작성되며 객체지향 프로그래밍의 경우 상호작용하는 객체들의 관계를 중심으로 코드가 작성된다. 절차지향 프로그래밍이 실행 속도는 더 빠르지만 객체지향 프로그래밍이 유지보수가 용이하고 재사용성이 높다.

<br>

### # 자바스크립트 부동 소수점 연산 오차

- 자바스크립트의 넘버 타입은 정수(1, 2, 3..)와 실수(0.1, 0.2, 0.3..)를 따로 구분하지 않고 모든 수를 실수 하나로만 표현하며 64비트의 부동소수점 형식을 이용해 프로그래밍에 필요한 모든 수 체계를 지원한다. 따라서 자바처럼 float, int 같은 별도의 타입 대신 number 하나로 표현할 수 있다.

- 자바스크립트에서 0.1 + 0.2 결과 값을 확인해보면 정확하지않다. 이유는 자바스크립트를 통해 작성된 10진수를 자바스크립트 실행 시 내부적으로 64비트의 부동소수점 형식의 2진수로 변환하는데 이 과정에서 0.1, 0.2등의 10진수는 무한 소수가 되기 때문에 근사 값(유한 소수)으로 바꾸어 메모리에 저장한다. 이 과정에서 미세한 오차가 발생한다. 이러한 오차를 부동 소수점 연산 오차라고 한다. 이러한 문제를 해결하기 위해서는 bigNumber와 같은 라이브러리를 활용하여 계산할 수 있다.

<br>

### # 호스트 객체, 네이티브 객체

- 호스트 객체

  자바스크립트 코드가 실행되는 환경(호스트 환경)에서 제공하는 객체이다. 즉, 브라우저, Node.js, Web Worker 등 자바스크립트 엔진을 둘러싼 플랫폼이 자체적으로 제공하는 객체들이다. 호스트 객체는 자바스크립트의 표준이 아닌, 비표준 (환경에서 자체 제공)으로 환경에 따라 다르다.

  - 예시 (브라우저 환경)

    window, document, XMLHttpRequest, localStorage, navigator, location, alert(), console 등, BOM (Browser Object Model), DOM (Document Object Model)

  - 예시 (Node.js 환경)

    require, module, process, global, Buffer, setImmediate, **dirname, **filename 등

- 네이티브 객체

  ECMAScript 사양(ECMA-262)에 명시된 표준 객체이며, 어떤 환경에서도 동일하게 사용할 수 있는 표준 자바스크립트 객체입니다.

  - 예시

    - 기본 객체: Object, Function, Boolean, Symbol

    - 숫자 관련: Number, Math, BigInt

    - 문자열 관련: String

    - 날짜/정규표현식: Date, RegExp

    - 배열 관련: Array, Map, Set, WeakMap, WeakSet

    - 에러 관련: Error, TypeError, RangeError, ReferenceError 등

<br>

### # 기능 검출, 기능 추론

- 기능 검출(Feature detection)

  스크립트가 호출하는 기능을 사용자의 브라우저가 지원하는지 체크하는 것이다. if('localStorage' in window){...}과 같이 localStorage 기능이 존재하는지 체크할 수 있다.

- 기능 추론(Feature inference)

  만약 기능을 브라우저가 지원한다면 다른 기능도 존재할 것이라고 추론하는 것이다. 예를 들어 localStorage 기능을 지원한다면 sessionStorage 기능을 지원 할 것이라고 추론하는 것이다.

<br>

### # 사용하는 디버깅 툴

- 자바스크립트 : 크롬 개발자 도구 소스탭, debugger 키워드, console.log

- 페이지 성능 : 크롬 개발자 도구 라이트하우스

- API 요청 : 크롬 개발자 도구 네트워크, Apollo client devtools(요청 및 캐시 확인)

- 컴포넌트 렌더링 : react developer tools(컴포넌트 렌더링 및 리렌더링 확인)

- 기타 : Redux Devtools(스토어 상태 조회, 디스패치 이력 조회 등)

<br>

### # 객체 관련 메소드

- Object.assign : 객체 내부의 다른 객체의
  프로퍼티를 복사해서 가져온다. 중첩되는 경우 복사되는 프로퍼티가 우선이 된다.

  ```javascript
  const target = { a: 1, b: 2 };
  const source = { b: 4, c: 5 };

  const returnedTarget = Object.assign(target, source);

  console.log(target); // { a: 1, b: 4, c: 5 }
  ```

- Object.entries : 객체의 키와 벨류를 배열로 반환한다.

  ```js
  const obj = { key1: "value1", key2: "value2" };

  console.log(Object.entries(obj)); // [["key1", "value1"], ["key2", "value2"]]
  ```

- Object.fromEntries : 배열로 된 키와 벨류를 객체로 반환한다. Object.entries의 반대이다.

  ```js
  const arr = [
    ["key1", "value1"],
    ["key2", "value2"],
  ];

  console.log(Object.fromEntries(arr)); // { key1: "value1", key2: "value2" }
  ```

- Object.keys, Object.values : 객체의 키나 벨류를 배열로 반환한다.

  ```js
  const obj = { key1: "value1", key2: "value2" };

  console.log(Object.keys(obj)); // ["key1", "key2"]
  console.log(Object.values(obj)); // ["value1", "value2"]
  ```

- Object.is : 두 값이 같은지 확인하여 boolean을 반환한다. 원시 타입의 경우 값만 비교하고 참조 타입의 경우 같은 참조를 가리키는지 비교한다.

  ```js
  console.log(Object.is(100, 100)); // true
  console.log(Object.is(NaN, NaN)); // true (=== 는 false)
  console.log(Object.is(+0, -0)); // false (=== 는 true)
  ```

- Object.prototype.hasOwnProperty : 객체 내부의 해당 프로퍼티가 프로토체인을 통한 상속이 아닌 직접 존재하는지 확인하여 boolean을 반환한다.

  ```js
  const obj = { a: 1 };

  console.log(obj.hasOwnProperty("a")); // true
  console.log(obj.hasOwnProperty("toString")); // false (상속된 프로퍼티)
  ```

<br>

### # Javascript 내장 객체를 확장하는 것이 왜 좋은 방법이 아닌가?

- 내장 객체를 확장하는 것은 위험한 방법이다. 내장 객체를 확장하게 되면 이 내장 객체를 상속받아 사용하는 모든 객체에 영향이 갈 수 있으므로 확장하지 않는 것이 좋다. 내장 객체를 확장해야 하는 경우는 대체 코드(polyfill)을 추가해야 할 때 뿐이다. 예를 들어 특정 브라우저에서 지원하지 않는 메소드가 있는 경우 대체 코드인 폴리필을 추가해야 할 필요가 생긴다. (ex IE 브라우저가 지원하지 않는 Array.prototype.includes를 사용하려 할 때, Array.prototype에 includes 메소드를 추가)

<br>

### # 옵셔널 체이닝

- 자바스크립트에서 객체나 배열처럼 중첩된 데이터에 접근할 때 중간에 값이 null 또는 undefined인 경우 에러 없이 안전하게 멈추고 undefined를 반환해주는 문법이다. 물음표(?)로 사용할 수 있다.

  ```jsx
  const data = response.data; // data가 null일 수도 있음

  // 옵셔널 체이닝을 쓰면 에러 없이 안전하게 map 호출 가능
  const list = data?.map((item) => `<li>${item.name}</li>`) ?? [];
  ```

<br>

### # ?? (널 병합 연산자) vs || (논리 OR 연산자)

- ?? (널 병합 연산자)

  왼쪽 피연산자가 null 또는 undefined 일 때만 오른쪽 값을 반환, 그 외는 왼쪽 값을 그대로 사용

  ```js
  const a = null ?? "default"; // 'default'
  const b = undefined ?? "default"; // 'default'
  const c = false ?? "default"; // false  (false는 null/undefined가 아님)
  const d = 0 ?? "default"; // 0
  const e = "" ?? "default"; // ''
  ```

- || (논리 OR 연산자)

  왼쪽 피연산자가 falsy 값일 때 모두 오른쪽 값을 반환 (false, 0, '', null, undefined, NaN 등)

  ```js
  const a = null || "default"; // 'default'
  const b = undefined || "default"; // 'default'
  const c = false || "default"; // 'default'
  const d = 0 || "default"; // 'default'
  const e = "" || "default"; // 'default'
  ```

<br>

### # 쓰로틀링, 디바운싱

- 쓰로틀링

  여러 번 연속해서 발생하는 이벤트 중 이벤트를 모두 실행하지 않고 일정 시간 간격으로 실행되도록 제한하는 기법이다. 스크롤, 윈도우 리사이즈 이벤트 등에 자주 쓰인다.

  ```javascript
  import { useState } from "react";

  function Example() {
    const [throttle, setThrottle] = useState(false);
    const [page, setPage] = useState(1);

    const handleScroll = () => {
      if (throttle) return;

      setThrottle(true);
      setTimeout(() => {
        setPage((prevPage) => prevPage + 1);
        setThrottle(false);
      }, 300);
    };

    return (
      <div onScroll={handleScroll}>
        {/* 리스트 렌더링 */}
        <p>현재 페이지: {page}</p>
      </div>
    );
  }
  ```

- 디바운싱

  여러 번 연속해서 발생하는 이벤트 중 마지막 이벤트가 끝난 후 일정 시간 동안 추가 이벤트가 없으면 함수가 실행되도록 하는 기법이다. 검색어 입력, 버튼 클릭 연속 방지 등에 자주 쓰인다.

  ```javascript
  import { useEffect, useState } from "react";

  function Search() {
    const [searchText, setSearchText] = useState("");
    const [query, setQuery] = useState("");

    useEffect(() => {
      const handler = setTimeout(() => {
        setQuery(searchText);
      }, 300);

      // searchText가 바뀌기 전에 이전 타이머 제거
      return () => clearTimeout(handler);
    }, [searchText]);

    return (
      <input
        type="text"
        value={searchText}
        onChange={(e) => setSearchText(e.target.value)}
        placeholder="검색어 입력"
      />
    );
  }
  ```

<br>

### # 불변 객체(immutable)를 만드는 방법

- 기본적으로 원시 타입을 제외한 모든 값은 변경 가능한 값(mutable)이다. 즉 새로운 값을 다시 만들 필요없이 직접 변경이 가능하다는 것이다. 불변 객체를 만들기 위해서는 const와 Object.freeze 메소드를 사용하여 만들 수 있다. 하지만 const로 만드는 경우 재할당은 불가능하지만 할당된 값이 참조 타입인 경우 메모리 힙에 참조 값은 변경(객체 재할당 X 객체 프로퍼티 재할당 O)될 수 있으므로 완전한 불변 객체가 아니다. 또 Object.freeze 메소드는 동결된 객체를 반환하지만 객체의 재할당(객체 재할당 O 객체 프로퍼티 재할당 X)이 가능하므로 완전히 불변 객체가 아니다. 완전한 불변 객체를 만들기 위해 const와 Object.freeze 메소드를 함께 사용할 수 있다. 먼저 const로 바인딩 된 변수를 상수화 시킨 다음, Object.freeze()로 해당 변수를 동결 객체를 만들면 객체의 재할당과 객체의 속성 둘 다 변경 불가능한 불변 객체(객체 재할당 X 객체 프로퍼티 재할당 X)가 된다. 아니면 immutable.js와 같은 라이브러리를 활용하여 불변 객체를 만들 수 있다.

  ```js
  const test = {
    name: "jam",
  };

  Object.freeze(test);
  ```

<br>

### # 자바스크립트의 람다식

- 함수나 메서드를 이름 없이(익명) 간결하게 하나의 표현식으로 정의하는 방식이다. 자바스크립트에서는 화살표 함수가 람다식과 유사한 문법이다.

  ```js
  const add = (a, b) => a + b;
  ```

<br>

### # 싱글턴 패턴

- 개념

  싱글턴 패턴(Singleton Pattern)은 전체 시스템에서 클래스의 인스턴스를 오직 하나만 생성하도록 제한하는 디자인 패턴이다. 이를 통해 전역 상태를 일관되게 공유할 수 있다.

  JavaScript에서는 객체 리터럴로 비슷한 동작을 흉내낼 수 있지만, 객체 리터럴은 생성 시점에 즉시 만들어지고 모든 속성이 외부에 노출된다는 단점이 있다. 또 지연 생성(lazy initialization)이나 캡슐화가 어렵다.

  진정한 싱글턴 패턴은 인스턴스를 한 번만 생성하고, 필요할 때만 초기화하며, 내부 상태를 외부에 숨길 수 있는 구조를 가져야 한다. 이를 위해 즉시 실행 함수(IIFE)를 활용해 비공개 변수와 클로저를 통해 싱글턴을 구현할 수 있다.

  싱글턴을 통해 불필요한 인스턴스 생성을 막고, 항상 동일한 인스턴스를 공유한다. 실무에서는 전역 상태를 제어하거나, 설정/로그/DB 연결 등에 많이 사용된다.

  ```js
  const singleton = (() => {
    let instance; // 인스턴스를 저장할 변수 (비공개)
    const secret = "hello"; // 비공개 데이터

    const createInstance = () => {
      // 인스턴스 내용
      return {
        secretValue: secret,
        showSecret: () => {
          alert(secret);
        },
      };
    };

    return {
      getInstance: () => {
        if (!instance) {
          instance = createInstance(); // 최초 호출 시 인스턴스 생성
        }
        return instance; // 이후에는 기존 인스턴스 반환
      },
    };
  })();

  // 사용 예시
  const first = singleton.getInstance();
  const second = singleton.getInstance();

  console.log(first === second); // true → 동일 인스턴스
  ```

- 예시 (라인쓰리, AWS SDK 활용한 이미지 presignedURL S3 버킷 업로드)

  AWS SDK의 클라이언트 객체(AWS.S3)는 내부적으로 다음과 같은 리소스를 유지한다.

  1. HTTP 연결 풀 : 클라이언트는 HTTP keep-alive로 연결을 재사용하려고 함, 매번 만들면 연결 재사용이 안 되어 성능 저하
  2. Credential 설정 : 클라이언트 객체가 생성될 때 IAM 키를 바탕으로 인증 설정, 반복 생성하면 이 설정 과정을 계속 반복함
  3. Config 캐시 (리전, 서명 버전 등) : 매번 새로 만들면 config 파싱 비용 발생

  getS3Client 내부 프로퍼티를 보면 싱글턴 패턴을 하고 있다. 즉 한 번 생성된 S3 인스턴스(S3 클라이언트)를 재사용하여 비용/성능 최적화하고 있다. 클라이언트 객체 재사용으로 설정/인증 비용 최소화, 연결 재사용으로 빠른 요청 처리 가능, 인스턴스를 1개만 유지하므로 메모리 절약, 동일한 클라이언트로 일관된 처리를 하기 때문에 안정성 증가 등에 장점이 있다.

  ```ts
  import AWS from "aws-sdk";
  import { isUndefined } from "lodash";

  const endpoint = process.env.NEXT_PUBLIC_S3_END_POINT;
  const region = process.env.NEXT_PUBLIC_AWS_REGION;

  const awsClient = (function () {
    let s3Instance: AWS.S3 | undefined;
    let cloudFrontInstance: AWS.CloudFront | undefined;

    return {
      getS3Client: function ({
        accessKeyId,
        secretAccessKey,
      }: {
        accessKeyId: string | undefined;
        secretAccessKey: string | undefined;
      }) {
        if (isUndefined(accessKeyId) || isUndefined(secretAccessKey)) {
          console.error("accessKeyId or secretAccessKey is not provided");
        } else if (!s3Instance) {
          // 인스턴스를 재사용
          s3Instance = new AWS.S3({
            signatureVersion: "v4",
            endpoint,
            region,
            credentials: {
              accessKeyId,
              secretAccessKey,
            },
          });
        }
        return s3Instance;
      },
      getCloudFrontClient: function ({
        accessKeyId,
        secretAccessKey,
      }: {
        accessKeyId: string | undefined;
        secretAccessKey: string | undefined;
      }) {
        if (isUndefined(accessKeyId) || isUndefined(secretAccessKey)) {
          console.error("accessKeyId or secretAccessKey is not provided");
        } else if (!cloudFrontInstance) {
          cloudFrontInstance = new AWS.CloudFront({
            signatureVersion: "v4",
            region,
            credentials: {
              accessKeyId,
              secretAccessKey,
            },
          });
        }
        return cloudFrontInstance;
      },
    };
  })();

  export { awsClient };
  ```

  만약 요청마다 S3 인스턴스를 다시 생성한다면 이건 마치 커피숍에서 매 주문마다 바리스타를 새로 고용하는 것과 같다. 싱글턴 패턴을 사용하면 한 명의 바리스타가 모든 주문을 처리하는 것과 같게 된다.

  ```ts
  // 매번 새로 생성
  const s3 = new AWS.S3(); // 계속 객체 생성 -> 낭비

  // 싱글턴
  let s3Instance: AWS.S3;
  if (!s3Instance) {
    s3Instance = new AWS.S3(); // 최초 1회만 생성
  }
  ```

<br>

### # performance API

- 함수 성능을 측정할 때 사용하는 API이다. 측정 결과는 내부 퍼포먼스 엔트리 버퍼(performance entry buffer)에 수집된다.

  - 측정 메서드

    - performance.now

    - performance.mark

    - performance.measure

  - 결과 확인 메서드

    - performance.getEntries

    - performance.getEntriesByName

    - performance.getEntriesByType

- performance API vs console.time

  | 구분                    | `console.time()`                          | `performance.now()` / `mark()` 등                                    |
  | ----------------------- | ----------------------------------------- | -------------------------------------------------------------------- |
  | **정밀도**              | **ms 단위** (정확도 낮음)                 | **소수점 5자리까지 ms 측정** (고해상도)                              |
  | **기능**                | 단순한 시작/종료 시간 측정                | 여러 지점을 마킹하거나 구간 이름 지정 가능                           |
  | **활용 대상**           | 디버깅/로컬 측정 용도                     | 웹 앱 성능 분석, 정밀 측정, 로그 수집                                |
  | **측정 시점 이름 지정** | 문자열 1개로만 구분 (`console.time('X')`) | 여러 mark를 찍고, 구간 이름 지정 가능                                |
  | **측정 결과 기록**      | 콘솔에 출력됨                             | 브라우저 성능 entry 버퍼에 저장됨                                    |
  | **브라우저 표준 API**   | 아니고, 디버깅용 도구 수준                | **W3C Performance 표준 API**                                         |
  | **지원 환경**           | 거의 모든 브라우저, Node.js 지원          | 대부분 브라우저 지원 (Node에서는 `perf_hooks` 모듈로 유사 기능 가능) |

<br>

### # 숫자 포멧을 바꾸는 방법

| 방법                | 장점                     | 단점/주의점                      |
| ------------------- | ------------------------ | -------------------------------- |
| `toLocaleString()`  | 간단, 네이티브 최적화    | 옵션 제한적                      |
| `Intl.NumberFormat` | 다양한 옵션, 국제화 지원 | 약간 더 복잡                     |
| 정규식              | 커스텀 가능              | 국제화 지원 안 됨, 복잡하면 느림 |

<br>

### # 재귀 함수 (참고 : https://joooing.tistory.com/entry/%EC%9E%AC%EA%B7%80-%E2%86%92-%EA%BC%AC%EB%A6%AC-%EC%9E%AC%EA%B7%80-Tail-Recursion)

- 함수가 자기 자신을 호출하는 것을 재귀함수라고 한다. 재귀함수는 종료조건이 있어야 하며, 종료조건을 설정해주지 않으면 무한 반복을 하게된다. 재귀 함수를 사용하는 이유는 알고리즘 자체가 재귀적으로 표현하기 자연스러울 때 혹은 변수 사용을 줄이기 위해 사용한다.

  재귀 함수의 단점으로는 콜스택의 부하로 인한 메모리 낭비인데 꼬리 재귀(재귀 호출이 끝나면 아무 일도 하지 않고 결과만 바로 반환되도록 하는 방법)를 통해 해결할 수 있다. 꼬리 재귀를 사용하면 이전 함수의 상태를 유지하지도 않고 추가 연산을 하지도 않아서 콜스택의 부하 문제를 해결할 수 있게 된다. 즉 콜스택에 쌓이는 스택을 줄일 수 있다.

  ```js
  // 재귀 함수 : 팩토리얼 예시
  // 팩토리얼 : 1부터 어떤 수까지의 정수를 모두 곱한 값, ex) 5! = 5 × 4 × 3 × 2 × 1 = 120
  function factorial(n) {
    if (n === 1) {
      return 1;
    }
    return n * factorial(n - 1);
  }

  factorial(3); // 6

  /*
    1. factorial(3) 함수 컨텍스트 생성 -> factorial 호출문 만나면 실행 단계 중지 및 인자로 (2) 전달
    2. factorial(2) 함수 컨텍스트 생성 -> factorial 호출문 만나면 실행 단계 중지 및 인자로 (1) 전달
    3. factorial(1) 함수 컨텍스트 생성 -> n이 1이므로 1 출력 -> factorial(1,6) 함수 컨텍스트 제거
    4. factorial(2) 함수 컨텍스트가 n과 전달받은 호출 결과 1을 연산하여 2 출력 -> factorial(2) 함수 컨텍스트 제거
    5. factorial(3) 함수 컨텍스트가 n과 전달받은 호출 결과 2를 연산하여 6 출력 -> factorial(3) 함수 컨텍스트 제거
  */

  // 꼬리 재귀 함수
  function factorial(n, total = 1) {
    if (n === 1) {
      return total;
    }
    return factorial(n - 1, n * total);
  }

  factorial(3); // 6

  /*
    1. factorial(3,1) 함수 컨텍스트 생성 -> factorial 호출문 만나면 인자로 (2,3) 전달 및 호출하며 factorial(3,1) 함수 컨텍스트 제거
    2. factorial(2,3) 함수 컨텍스트 생성 -> factorial 호출문 만나면 인자로 (1,6) 전달 및 호출하며 factorial(2,3) 함수 컨텍스트 제거
    3. factorial(1,6) 함수 컨텍스트 생성 -> n이 1이므로 파라미터로 전달받은 total 변수의 값인 6 출력 후 factorial(1,6) 함수 컨텍스트 제거
  */
  ```

<br>

### # requestAnimationFrame 과 cancelAnimationFrame

- 애니메이션의 프레임(frame)

  사람은 1초에 60개의 프레임을 볼 수 있다고 한다. 그 이상의 프레임을 더 찍어내더라도 사람이 느끼기엔 거의 차이가 없다는 말이다. 그래서 브라우저 렌더링 사이클도 1초에 60번(16.6ms, 1000ms / 60frame) 반복한다. 즉 자바스크립트로 애니메이션을 구현할때도 1초에 60프레임 정도를 찍어내야한다. 16.6ms마다 1프레임을 찍어내기 위해 사용할 수 있는 방법은 setTimeout 혹은 setInterval, requestAnimationFrame 등이 있다.

- requestAnimationFrame(rAF)

  1. 재귀 호출 방식

     함수를 반복할 때 사용할 수 있는 메서드이다. 애니메이션을 구현할 때 사용되며 일반적으로 재귀적인 호출 방식을 통해 반복한다.

  2. 최대 호출 횟수

     Web API에서 동작하며 최대 1초에 60번 동작한다. 다수 애니메이션에도 각각 타이머를 생성하지 않고 동일한 타이머를 참조하게 된다.

  3. 렌더링 사이클 중 리플로우/리페인트 단계 전 정확한 타이밍에 호출

     setTimeout 혹은 setInterval 같은 경우 렌더링 사이클을 고려하지 않고 시간에 따라 실행되기 때문에 프레임 누락이 발생할 수 있다. 반면 requestAnimationFrame의 경우 렌더링 사이클 중 다음 리플로우/리페인트가 발생하기 전 정확한 타이밍에 실행되기 때문에 프레임 누락을 방지할 수 있다.

  4. 백그라운드 동작 및 비활성화시 중지

     브라우저 백그라운드 Web API에서 실행되며 브라우저창이 숨겨지거나 최소화되어 보여지지 않는 경우 애니메이션을 중지시키고 보여질 때 다시 실행시킨다. 이를 통해 CPU 리소스를 절약할 수 있다.

- cancelAnimationFrame(cAF)

  setTimeout의 clearTimeout과 같이 반복되는 requestAnimationFrame 함수를 정지시킬 때 사용한다.

<br>

### # 직렬화, 역직렬화

- 직렬화

  컴퓨터 메모리 상에 존재하는 객체(ex Object)를 저장 혹은 전송 가능한 형태로 변환(ex JSON)하는 것을 말한다. (ex JSON.stringify())

- 역직렬화

  전송 받은 데이터 혹은 문자열(ex JSON)을 컴퓨터 메모리 상에서 사용할 수 있는 객체로 변환(ex Object)하는 것을 말한다. (ex JSON.parse(), res.json())

<br>

### # HTML 문서의 생명주기 이벤트

- DOMContentLoaded

  브라우저가 HTML을 전부 읽고 DOM 트리를 완성하는 즉시 발생한다. 이미지 파일(img 태그)이나 스타일시트 등의 기타 자원은 기다리지 않는다. DOMContentLoaded 이벤트는 document 객체에서 발생한다. 따라서 이 이벤트를 다루려면 addEventListener를 사용해야 한다.

  ```js
  document.addEventListener("DOMContentLoaded", () => {
    alert("DOM이 준비되었습니다!");
  });
  ```

- load

  HTML로 DOM 트리를 만드는 게 완성되었을 뿐만 아니라 이미지, 스타일시트 같은 외부 자원도 모두 불러오는 것이 끝났을 때 발생한다.
  onload 프로퍼티로 발생시킬 수 있다.

  ```js
  window.onload = function () {
    // window.addEventListener('load', (event) => {...}와 동일
    alert("페이지 전체가 로드되었습니다.");
  };
  ```

- beforeunload/unload

  사용자가 페이지를 떠날 때 발생한다. window 객체에서 발생시킬 수 있다.

  ```js
  window.onbeforeunload = function () {
    return "저장되지 않은 변경사항이 있습니다. 정말 페이지를 떠나실 건 가요?";
  };
  ```

<br>

### # 함수 호출 방법 Call by Value & Call by Reference

- Call by Value(값에 의한 호출)

  인자로 원시 타입의 객체를 넘기는 것을 말한다. 함수의 파라미터는 인자와 같은 데이터의 주소 값을 참조하고 있지만 함수 내부에서 파라미터를 수정하는 경우 콜스택에서 새로운 데이터를 생성하여 그 데이터의 주소 값을 참조하기 때문에 원본의 변화는 없다. 값을 복사하여 처리하기 때문에 안전하고 원래의 값이 보존되지만 메모리 사용량이 늘어난다.

  ```js
  // Call by value(값에 의한 호출)
  const a = 1;

  const callByValue = (param) => {
    param = 2;

    return param;
  };

  console.log(callByValue(a)); // 2
  console.log(a); // 1, 원본 변경 X
  ```

- Call by reference(참조에 의한 호출)

  인자로 참조 타입의 객체를 넘기는 것을 말한다. 함수의 파라미터는 인자와 같은 데이터의 주소 값을 참조하고 있어 함수 내부에서 파라미터를 수정하는 경우 원본이 변화된다. 즉 함수의 인자는 얕은 복사를 통해 파라미터로 할당된다. 복사하지 않고 직접 참조를 하기에 처리가 빠르고 새로운 메모리를 할당받지 않지만 원본의 변화가 생길 수 있다. 만약 원본의 변화를 방지하려면 함수 내부에서 파라미터를 깊은 복사하여 참조를 끊어준 뒤 사용하면 된다.

  ```js
  // Call by Reference(참조에 의한 호출)
  const arr = [1, 2, 3];

  const callByReference = (param) => {
    param.push(4);

    return param;
  };

  console.log(callByReference(arr)); // [1, 2, 3, 4]
  console.log(arr); // [1, 2, 3, 4], 원본 변경 O
  ```

<br>

### # AJAX

- AJAX

  AJAX(Asynchronous JavaScript and XML)는 자바스크립트를 이용해서 비동기적(Asynchronous)으로 서버와 브라우저가 데이터를 교환할 수 있는 통신 방식을 의미한다. 과거에는 주로 XMLHttpRequest 객체를 사용해서 AJAX 요청을 보냈고 현재는 axios 라이브러리나 fetch API를 사용한다.

  -> 내가 이해한 내용으로는 AJAX는 방법론이며 브라우저가 AJAX라는 비동기 통신 방법론을 내부적으로 지원하고 구현해서 웹 페이지가 새로고침 없이 백그라운드에서 서버와 데이터를 주고받을 수 있도록 해준다고 이해했다. 즉 AJAX은 비동기 통신 방법 혹은 개념 자체를 이야기하며 HTTP 메서드는 그것을 실제 수행하는 도구라고 이해했다.

- AJAX 사용 이유

  자바스크립트는 싱글 스레드 언어로 한번의 하나의 테스크만 수행하게 된다. 이렇게 동기적으로 작업을 수행되게 되면 원하는 데이터를 원하는 시점에 불러올 수 없는 문제가 발생할 수 있다. 이 때 ajax 비동기 통신을 사용하게 되는데 ajax의 경우 자바스크립트 엔진이 아닌 Web API에서 처리되기 때문에 자바스크립트 엔진이 다른 작업을 수행하고 있다고 해도 블로킹되지 않고 수행되게 된다. 즉 Web API를 통해 멀티 스레드와 같은 효과를 볼 수 있는 것이다. 하지만 XMLHttpRequest는 코드가 직관적이지 않고 요청의 상태나 변경을 구독하기 위해서는 이벤트를 등록해서 변경사항을 받아야 하며 요청의 성공, 실패 여부나 상태에 따라 처리하는 로직이 들어가기 좋지 않다는 문제가 있다. 그렇기 때문에 XMLHttpRequest를 대체하여 프로미스 기반의 axios 라이브러리를 사용하거나 내장 라이브러리인 fetch를 사용할 수 있다.

- XML(eXtensible Markup Language)

  XML은 데이터 포맷 중 하나로 HTML과 유사한 마크업 언어이다. 데이터를 저장하고, 전달할 목적으로 고안되었다. 불필요한 태그들이 들어가 파일의 사이즈가 커질 뿐만 아니라 가독성도 좋지 않아 XML대신 JSON이 사용된다.

  ```xml
  <dog>
    <name>식빵</name>
    <family>웰시코기<family>
    <age>1</age>
    <weight>2.14</weight>
  </dog>
  ```

- JSON(JavaScript Object Notation)

  JSON은 데이터 포맷 중 하나로 XML과 마찬가지로 데이터 저장과 전달을 목적으로 고안되었으며, 자바스크립트 기반으로 작성되었으며 key와 value가 한 쌍을 이루는 구조의 객체로 구성되어 있다. XML의 대안으로서 고안되었으며, XML 대비 더 직관적이며, 작성하기 편리하며 프로그래밍 언어나 플랫폼에 상관없이 사용할 수 있다.

  ```json
  {
    "name": "식빵",
    "family": "웰시코기",
    "age": 1,
    "weight": 2.14
  }
  ```

<br>

### # fetch vs axios

| 구분                  | fetch                                                            | axios                                            |
| --------------------- | ---------------------------------------------------------------- | ------------------------------------------------ |
| 응답 처리             | Response 객체 반환, `.json()` 같은 메서드로 파싱 필요            | 응답 데이터를 바로 JSON 형태로 반환              |
| 기본 오류 처리        | HTTP 오류 상태(404, 500 등)도 정상 응답으로 처리, 수동 처리 필요 | HTTP 오류 상태일 때 자동으로 에러 처리 (reject)  |
| 요청 취소 지원        | AbortController 사용해서 취소 가능                               | 내장된 취소 토큰(CancelToken) 기능 제공          |
| 인터셉터 기능         | 없음 (window.fetch = () => { ... }와 같이 오버라이딩 가능)       | 요청/응답 인터셉터 기능 제공 (로깅, 에러처리 등) |
| 요청 데이터 자동 변환 | 직접 변환 필요                                                   | 자동으로 JSON 변환 및 직렬화 처리                |
| 지원하는 기능         | 기본적인 HTTP 요청                                               | 더 편리한 HTTP 요청/응답 처리 기능 제공          |

```javascript
// fetch
fetch("url")
  .then((response) => {
    if (!response.ok) {
      throw new Error("Network response was not ok");
    }
    return response.json();
  })
  .then((data) => {
    // Handle data
  })
  .catch((error) => {
    // Handle error
  });

// axios
axios
  .get("url")
  .then((response) => {
    // Handle response data
  })
  .catch((error) => {
    // Handle error
  });
```

<br>

### # axios의 withCredential과 fetch의 credential

- withCredential을 직역해보면 자격 증명을 함께라고 해석할 수 있다. 단어의 의미만 봐도 알 수 있듯이 무언가 인증할 때 필요한 옵션인 것을 알 수 있다. 정확히 withCredential 옵션의 역할은 서로 다른 도메인(크로스 도메인)에 요청을 보낼 때 요청에 Credential 정보를 담아서 보낼 지를 결정하는 옵션이다. axios에서는 withCredential , fetch에서는 credential로 지정할 수 있다.

  예를 들어 쿠키를 요청 헤더에 포함해야할 때 같은 도메인 요청 시 자동으로 포함되지만 서로 다른 도메인인 경우 해당 옵션을 true로 설정해주어야 요청 헤더에 포함된다.

  ex) 요청 origin이 `https://example.com`, API URL이 `https://example.com/api`인 경우 같은 도메인, 요청 origin이 `https://example.com`, API URL이 `https://api.example.com/api`인 경우 크로스 도메인, 프로토콜 + 도메인 + 포트번호까지 같아야 같은 도메인으로 취급된다. 예시의 경우 배포 환경에서 HTTPS 프로토콜의 기본 포트인 443 포트를 사용한다는 가정 하에 `https://example.com`과 `https://example.com/api`이 같은 도메인이라고 취급하는 것이다.)

  ```javascript
  /* axios */
  axios.get("https://example.com/items", {
    withCredentials: false, // default
  });

  /* fetch API */
  fetch("https://example.com:1234/users", {
    credentials: "include",
  });
  ```

- credential 정보가 포함되어 있는 요청은 아래 두 가지 경우를 의미한다.

  1. 쿠키를 첨부해서 보내는 요청

  2. 헤더에 Authorization 항목이 있는 요청

<br>

### # 가비지 컬렉터

- 가비지 컬렉터

  가비지 컬렉터는 `참조 카운팅`, `마크 앤 스윕` 알고리즘을 통해 메모리 힙에서 메모리 관리를 수행한다. 즉 메모리를 차지하는 데이터 중 사용하지 않는 데이터를 자동으로 삭제한다. 또한 자바스크립트는 자동으로 가비지 컬렉팅을 수행한다. 자바스크립트에서 데이터는 원시타입의 경우 콜스택, 참조타입의 경우 메모리 힙에 저장되는데 주소와 값에 형태로 저장되고 저장 된 데이터가 사용될 때는 주소와 값 중 주소 값을 참조하여 사용되게 된다. 만약 메모리 힙에서 객체나 배열 자신의 주소 값을 참조하는 식별자가 없는 경우 사용하지 않는 데이터이기 때문에 가비지 컬렉터에 의해 삭제되게 되는 것이다. 반면 콜스택의 원시 타입 데이터의 경우 전역 컨텍스트나 함수 컨텍스트가 종료될 때 자동으로 메모리에서 함께 제거된다.

  - 참조 카운팅: 객체가 참조되는 횟수를 세서 0이 되면 해제

  - 마크 앤 스윕: 도달할 수 없는 객체를 표시(mark)하고 한꺼번에 제거(sweep)

<br>

### # 비즈니스 로직

유저의 눈에 보이지는 않지만, 유저가 바라는 결과물을 올바르게 도출할 수 있게 짜여진 로직을 말한다. 예를 들어 유저가 회원가입 시 아이디가 사용되고 있는 아이디인지 검사 후 메세지를 통해 중복인지 아닌지를 확인할 수 있는 로직을 짯다고 가정했을 때 중복 아이디를 검사하는 로직이 비지니스 로직이 되고 비지니스 로직을 통한 결과를 단순히 메세지를 통해 유저에게 보여주기 위한 로직이 뷰 로직이 된다.

<br>

### # DOM

- DOM(Document Object Model)

  DOM은 문서 객체 모델이며 HTML이나 XML 문서를 브라우저의 렌더링 엔진이 HTML을 파싱하여 메모리에 저장한 객체 모델이며, 자바스크립트를 통해 문서 구조를 동적으로 읽고 조작할 수 있도록 도와주는 일종의 인터페이스입니다. DOM 트리는 크롬 개발자 도구 엘리먼트 탭에 하위 탭인 프로퍼티 탭에서 확인할 수 있다.

- HTML과 DOM의 차이

  - HTML

    웹 페이지를 표시하기 위해 태그, 속성 등 정해진 규칙에 따라 작성되는 언어 (정적인 구조)

  - DOM

    DOM은 브라우저의 HTML 파서가 HTML 파싱한 후 생성되는 객체 모델로 HTML 문서에 접근하기 위한 일종의 인터페이스 (브라우저 HTML을 해석해 만든 동적인 구조, javascript에 의해 변할 수 있다)

- DOM을 직접 접근할 때의 문제점

  DOM 조작 자체는 가능하지만, 직접 DOM을 반복적으로 다루는 방식은 코드가 복잡해지고 브라우저의 최적화 여지를 줄여 성능 저하의 원인이 될 수 있따. 이를 개선하기 위해 React는 변경 전후의 DOM을 비교(diffing)하여 필요한 최소한의 변경만 실제 DOM에 반영하는 가상 DOM(Virtual DOM) 개념을 도입했다.

<br>

### # 오버로딩(Overloading) vs 오버라이딩(Overriding)

- 오버라이딩(Overriding)

  상위 클래스가 가지고 있는 메소드를 하위 클래스가 재정의(복붙)하여 사용하는 방식이다. 자바스크립트의 클래스 확장 시 상속받는 클래스 내부에 super 키워드를 활용하여 오버라이딩 할 수 있다. constructor 내부에서 선언 시 생성자 오버라이딩을 할 수 있고 클래스 바디에 선언 시 메소드 오버라이딩을 할 수 있다.

  ```js
  class Animal {
    speak() {
      console.log("Animal speaks");
    }
  }

  class Dog extends Animal {
    speak() {
      super.speak(); // 부모 메서드 호출
      console.log("Dog barks");
    }
  }

  const dog = new Dog();
  dog.speak();
  // Animal speaks
  // Dog barks
  ```

- 오버로딩(Overloading)

  같은 이름의 함수를 여러 개 만든 뒤 각각의 함수에 매개변수의 타입, 갯수를 다르게 지정하여 호출 시 전달되는 인자에 타입이나 갯수에 따라 실행 될 함수를 매칭하여 다른 출력 값을 받는 방식을 말한다. 자바스크립트에서는 arguments 객체의 바인딩 되는 인자를 조건으로 하여 구현하거나, 조건문과 인자의 타입이 함수(function)인지를 평가하는 typeof 연산자를 함께 활용하여 구현할 수 있다.

  ```js
  function greet(name: string): string;
  function greet(age: number): string;
  function greet(value: any): string {
    if (typeof value === 'string') return `Hello, ${value}`;
    if (typeof value === 'number') return `You're ${value} years old`;
    return 'Hi';
  }

  greet('Jane'); // Hello, Jane
  greet(25);     // You're 25 years old
  ```

<br>

### # symbol 타입

- 심볼은 변경 불가능(immutable)한 원시 타입의 값이며, 다른 값과 중복되지 않는 유니크한 원시 타입의 값이다. 심볼은 객체의 프로퍼티 키로 사용할 수 있고 심볼 값을 키로 갖는 프로퍼티는 일반 문자열 키와는 충돌하지 않아 안전한 확장에 유용하다. Symbol(), Symbol.for()로 생성 가능하다. Symbol()의 경우 같은 키를 사용할 때마다 항상 새로운 고유 값이 생성되지만 Symbol.for()의 경우 생성한 심볼을 전역 심볼 레지스트리에 저장하여 같은 키를 사용할 때 재사용하여 참조가 동일하다.

  ```javascript
  // Symbol() -> 고유함
  const a = Symbol("id");
  const b = Symbol("id");
  console.log(a === b); // false
  ```

  ```javascript
  // Symbol.for() -> 고유하지만 같은 값을 공유
  const a = Symbol.for("foo");
  const b = Symbol.for("foo");

  console.log(a === b); // ✅ true
  ```

  ```javascript
  // 객체의 프로퍼티 키로 사용 가능
  const key = Symbol("key");
  const obj = { [key]: "value" };
  console.log(obj[key]); // 'value'
  ```

<br>

### # 블로킹(Blocking) vs 논블로킹(Non-Blocking)

- 제어권

  함수 코드를 실행할 권리, 제어권을 가진 함수는 자신의 코드를 끝까지 실행한 후, 자신을 호출한 함수에게 돌려준다.

- 블로킹(Blocking) vs 논블로킹(Non-Blocking) -> 제어 흐름 중심

  (1) 블로킹(Blocking) : 호출한 함수가 결과를 받을 때까지 멈춘다.

  (2) 논블로킹(Non-Blocking) : 호출한 함수가 멈추지 않고 다음 작업을 이어간다.

- 동기(Synchronous) vs 비동기(Asynchronous) -> 결과 처리 중심

  (1) 동기(Synchronous) : 호출자가 결과를 직접 받고 즉시 처리한다.

  (2) 비동기(Asynchronous) : 호출자가 결과를 직접 기다리지 않고, 콜백/프라미스 등을 통해 나중에 결과를 처리한다.

- 예시

  (1) 블로킹 + 동기 : 함수 호출자는 결과를 받을 때까지 멈추고 기다린다. 결과는 즉시 반환된다.

  (2) 블로킹 + 비동기 : 결과는 나중에 처리되지만, 호출자는 작업이 끝날 때까지 멈춰 있음.

  (3) 논블로킹 + 동기 : 결과는 즉시 반환되지만, 호출자는 멈추지 않고 다음 코드를 계속 실행한다.

  (4) 논블로킹 + 비동기 : 결과는 나중에 콜백/프라미스 등으로 처리되고, 호출자는 기다리지 않고 다음 코드 실행

<br>

### # Parameter, Argument

- 매개변수(Parameter)

  함수를 호출할 때 인수로 전달받은 값을 담는 변수이다. 함수 내부에서 사용할 수 있다. 인수를 얕은 복사한 값이다.

- 인수(Argument)(= 인자)

  함수를 호출할 때 매개변수로 전달되는 값이다.

<br>

### # 동적 언어 vs 정적 언어

- 동적 언어 (동적 타이핑 언어)

  타입(자료형)이 런타임(실행 시점)에 결정되는 언어이다. 즉, 소스 코드를 작성할 때 타입을 명시하지 않아도 되고, 변수에 어떤 타입의 값이든 할당할 수 있다. 덕분에 빠르게 코드를 작성할 수 있지만, 실행 도중 타입 관련 에러가 발생할 가능성이 있다. 대표적인 동적 언어로는 JavaScript, Ruby, Python 등이 있다.

- 정적 언어 (정적 타이핑 언어)

  타입(자료형)이 컴파일 타임(빌드 시점)에 결정되는 언어이다. 코드 작성 시 변수와 함수의 타입을 명시해야 하며, 컴파일러가 타입을 체크하여 타입 오류를 미리 발견할 수 있다. 덕분에 코드의 안정성과 가독성이 높아지고, 디버깅도 쉬워진다. 대표적인 정적 언어로는 C, C++, Java, TypeScript 등이 있습니다.

<br>

### # 크롤링

- 웹 크롤링

  웹 크롤링이란 웹 페이지에서 원하는 데이터를 자동으로 수집, 분류, 저장하는 작업을 의미한다. 주로 Selenium(셀레니움) 같은 라이브러리를 활용해 웹 브라우저를 자동으로 조작하거나, requests, BeautifulSoup, Puppeteer 등 다양한 도구로 구현할 수 있다.

- 웹 크롤링 시 유의사항

  - 크롤링 대상 서버에 과도한 부하를 주지 않기 (적절한 요청 간격 유지)

  - 저작권 등 컨텐츠 사용 권한을 준수하기

  - 크롤링을 금지하는 웹사이트나 페이지는 크롤링하지 않기 (robots.txt 파일 참고)

<br>

### # 테스트 코드

- TDD(Test Driven Development)

  TDD(테스트 주도 개발)는 테스트를 먼저 작성하고, 이후 테스트를 통과하며 실제 코드를 구현하는 개발 방식입니다. 기능 구현보다 테스트 코드를 우선 작성하며, 테스트의 피드백을 바탕으로 코드를 점진적으로 완성해 나갑니다.

- TDD(Test Driven Development) 장점

  1. 철저한 모듈화 : 테스트 작성을 위한 철저한 모듈화를 통해 가독성, 재사용성, 유지보수를 용이하게 한다.

  2. 효율적인 설계 : 테스트 작성 전 다양한 예외사항에 대해 생각해볼 수 있으며 전체적인 설계가 변경되는 일을 방지할 수 있다.

  3. 디버깅 시간 단축 : 자동화 된 유닛테스팅을 전제하므로 특정 버그를 손 쉽게 찾아낼 수 있다.

  4. 테스트 정의서 대체 : 테스트 정의서를 직접 작성하는 것보다 테스트를 자동화하여 테스트 시간을 작성하고 테스트를 빼먹는 등의 휴먼 에러를 방지할 수 있다.

- TDD(Test Driven Development) 단점

  1. 생산성의 저하 : 테스트 코드를 추가로 작성해야하고 중간 중간 테스트 후 코드를 수정해야하므로 생산성이 저하된다.

- TDD 구현 방법

  1. Red – 실패하는 테스트 작성 (아직 구현이 없으므로 실패)

  2. Green – 테스트가 통과할 수 있도록 최소한의 코드 작성

  3. Refactor – 기능을 변경하지 않으면서 코드를 리팩터링

- 테스팅 피라미드와 종류

  Google Test Automation Conference에서 제안된 테스트 피라미드와 테스트 비중

  1. UI 테스팅(E2E Testing) (10%) : 실제 사용자와 유사한 방식으로 전체 시스템을 테스트 (예 : 회원가입 → 로그인 → 마이페이지 진입까지 흐름 테스트)

  2. 통합 테스팅 (Integrating Testing) (20%) : 여러 모듈 또는 컴포넌트를 함께 동작시켜 테스트, 보통 유닛 테스트가 끝난 모듈을 묶어서 확인 (예 : 로그인 시 API 호출 → 사용자 정보 상태 업데이트 → UI 반영)

  3. 단위 테스팅 (Unit Testing) (70%) : 가장 작은 코드 단위(함수, 클래스, 컴포넌트 등)의 테스트, 외부 의존성 없이 고립된 상태에서 테스트 (예 : 함수가 특정 입력에 대해 예상한 결과를 반환하는지 확인)

<br>

### # 테스트 자동화

- 테스트 자동화

  테스트 자동화는 소프트웨어의 동작을 사람이 직접 하지 않고 자동화된 도구를 통해 테스트를 수행하는 것을 말한다. 테스트 자동화의 핵심 목적은 반복적인 테스트 작업을 효율적으로 수행하고 휴먼 에러로 인한 테스트 누락을 방지하는 데 있다. 특히 테스트 주도 개발(TDD)이나 CI/CD 환경에서는 테스트를 반복적으로 빠르게 실행해야 하므로, 자동화는 필수적이다.

- 대표적인 테스팅 라이브러리 및 프레임워크

  - 시나리오 테스트 : Cypress, Playwright 등

  - 통합 테스트 : testing library(@testing-library/react, @testing-library/vue 등)

  - 유닛 테스트 : Jest, Vitest 등 (컴포넌트 테스트는 Testing Library와 함께 쓰는 것이 일반적)

- 테스트 예시

  ```javascript
  // utils/math.js
  export function add(a, b) {
    return a + b;
  }
  ```

  ```javascript
  // __tests__/math.test.js
  import { add } from "../utils/math";

  describe("add 함수 테스트", () => {
    test("1 + 2는 3이어야 한다", () => {
      expect(add(1, 2)).toBe(3);
    });

    test("0 + 0은 0이어야 한다", () => {
      expect(add(0, 0)).toBe(0);
    });
  });
  ```

  - describe : 관련된 테스트들을 묶는 블록

  - test 또는 it : 실제 테스트 단위

  - expect(값).toBe(기댓값) : Assertion (단언문)

<br>

### # DRY원칙

돈 리피트 유얼셀프(Don’t Repeat Yourself)의 약자로 같은 코드(또는 로직)를 반복해서 작성하지 말자는 의미이다입니다. 중복을 피하고 재사용 가능한 구조로 만들자는 소프트웨어 개발의 핵심 원칙 중 하나이다.

<br>

### # for문에서의 비동기 함수 사용 시 문제, var와 let 그리고 클로저

- for문에서의 비동기 함수 사용 시 문제, var와 let 그리고 클로저

  아래와 같이 for문에서 비동기 함수 사용 시 초기 값을 var를 사용하느냐 혹은 let 사용하느냐에 따라 출력 값이 달라질 수 있다.
  이러한 결과가 나타나는 이유는 블록 레벨 스코프와 함수 레벨 스코프의 차이 때문이다.

  ```js
  // 예시1 : var 사용
  const functionScope = () => {
    for (var i = 0; i < 3; i++) {
      setTimeout(() => {
        console.log(i);
      }, 100);
    }
  };

  // 예시2: var 사용 + 클로저
  const closerFunction = () => {
    for (var i = 0; i < 3; i++) {
      ((x) => {
        setTimeout(() => {
          console.log(x);
        }, 100);
      })(i);
    }
  };

  // 예시3: let 사용
  const blockScope = () => {
    for (let i = 0; i < 3; i++) {
      setTimeout(() => {
        console.log(i);
      }, 100);
    }
  };

  functionScope(); // 3이 3번 찍힌다.
  closerFunction(); // 0, 1, 2가 순서대로 찍힌다.
  blockScope(); // 0, 1, 2가 순서대로 찍힌다.
  ```

- 예시1 functionScope에서 var 사용 시 3이 3번 찍히는 이유

  for문 동작 시 setTimeout을 호출하게 되면 콜스택에 함수컨텍스트를 생성한 후 바로 제거하여 웹API 백그라운드에서 처리된다.
  이 때 콜스택에 컨텍스트는 바로 제거되기 때문에 백그라운드에서 처리가 완료되기 전 다음 반복문으로 들어가게 된다.
  이 후 setTimeout은 비동기적으로 처리되기 때문에 나머지 for문도 방금과 같은 작업을 반복하게 된다. 그렇기 때문에
  setTimeout이 타이머에 의해 웹API에서 처리되기 전 for문은 이미 마지막 루프까지 마친 상태이기 때문에 i값은 3이 되고
  웹API에서 처리 후 큐를 통해 실행되는 setTimeout 콜백 함수들은 이 i값을 참조하게 되어 모두 3을 반환한다.

  ```js
  // 예시1 : var 사용
  const functionScope = () => {
    for (var i = 0; i < 3; i++) {
      setTimeout(() => {
        console.log(i);
        debugger;
      }, 100);
    }
  };

  functionScope(); // 3이 3번 찍힌다.

  // 예시1을 풀어보면 아래와 같이 동작하는 것 같다. 디버그를 통해 확인해보면 동일하게 동작한다. 개발자 도구 우측에 클로저 필드를 보면 i가 저장되있음을 확인할 수 있다.
  // var는 함수 레벨 스코프로 동작하기 때문에 아래와 같이 함수 코드 블럭 내에 존재하는 것과 같다. 그렇기 때문에 반복되는 콜백이 바라보는 값은 동일해진다.
  const functionScopeTest = () => {
    var i = 0;

    {
      setTimeout(() => {
        console.log(i);
        debugger;
      }, 100);
      i++;
    }

    {
      setTimeout(() => {
        console.log(i);
        debugger;
      }, 100);
      i++;
    }

    {
      setTimeout(() => {
        console.log(i);
        debugger;
      }, 100);
      i++;
    }
  };

  functionScopeTest(); // 3이 3번 찍힌다.
  ```

- 예시2 closerFunction에서 var 사용 시 클로저를 통한 해결

  클로저란 간단하게 말하면 내부함수가 외부함수에 접근할 수 있는 것을 말한다.
  기존에 동작시키던 방식과 다르게 즉시 실행 함수를 생성한 후 파라미터로 i값을 전달하는 방식을 활용한다.
  이런 방식을 활용하게 되면 콜스택에 즉시 실행 함수 컨텍스트가 쌓이고 먼저 사라지더라도 웹API에 콜백으로 넘긴
  setTimeout 콜백 함수 스코프에 파라미터로 넘긴 x의 값을 기억하고 있기 때문에 해당 x값을 참조하여 최신 값을 유지할 수 있다.

  ```js
  // 예시2: var 사용 + 클로저
  const closerFunction = () => {
    for (var i = 0; i < 3; i++) {
      ((x) => {
        setTimeout(() => {
          console.log(x);
          debugger;
        }, 100);
      })(i);
    }
  };

  closerFunction(); // 0, 1, 2가 순서대로 찍힌다.

  // 예시2를 풀어보면 아래와 같이 동작하는 것 같다. 디버그를 통해 확인해보면 동일하게 동작한다. 개발자 도구 우측에 클로저 필드를 보면 i가 저장되있음을 확인할 수 있다.
  // var는 함수 레벨 스코프로 동작하기 때문에 아래와 같이 함수 코드 블럭 내에 존재하는 것과 같다. 하지만 즉시실행함수의 인자로 i를 받아 클로저 함수를 사용하여 해결할 수 있다.
  const closerFunctionTest = () => {
    var i = 0;

    {
      ((x) => {
        setTimeout(() => {
          console.log(x);
          debugger;
        }, 100);
      })(i);
      i++;
    }

    {
      ((x) => {
        setTimeout(() => {
          console.log(x);
          debugger;
        }, 100);
      })(i);
      i++;
    }

    {
      ((x) => {
        setTimeout(() => {
          console.log(x);
          debugger;
        }, 100);
      })(i);
      i++;
    }
  };

  closerFunctionTest(); // 0, 1, 2가 순서대로 찍힌다.
  ```

- 예시3 blockScope에서 let 사용 시 0,1,2가 순서대로 찍히는 이유

  예를 들어 functionScope()와 같이 var를 사용한 경우 var는 함수 레벨 스코프를 가지기 때문에 for 루프마다 새로운 스코프를 만들어내는 것이 아닌
  functionScope 내부에 하나의 스코프로만 존재하게 된다. 그렇기 때문에 for 루프마다 동일한 참조를 바인딩해서 사용하게 되는 것이다.
  반면 blockScope()와 같이 let을 사용한 경우 let은 블록 레벨 스코프를 가지기 때문에 for 루프마다 새로운 스코프를 만들어낸다.
  i가 0인 스코프, 1인 스코프, 2인 스코프 ... 등등으로 만들어내게 되고 이 각 루프마다 만들어지는 새로운 스코프를 참조하게 되므로 서로 다른 참조를 하게 되어
  동일한 값이 출력되지 않게 된다. 아래 두 개의 함수가 동일하게 동작하는 것을 알 수 있다.

  ```js
  // 예시3: let 사용
  const blockScope = () => {
    for (let i = 0; i < 3; i++) {
      setTimeout(() => {
        console.log(i);
        debugger;
      }, 100);
    }
  };

  blockScope(); // 0, 1, 2가 순서대로 찍힌다.

  // 예시3을 풀어보면 아래와 같이 동작하는 것 같다. 디버그를 통해 확인해보면 동일하게 동작한다. 개발자 도구 우측에 블럭 필드를 보면 i가 저장되있음을 확인할 수 있다.
  // 아마도 setTimeout은 즉시호출함수라 호출과 동시에 환경을 기억하게 되고 그 때 기억해놓은 스코프에 블록스코프인 i값을 저장해두는 것이 아닌가 싶다!
  const blockScopeTest = () => {
    {
      let i = 0;

      setTimeout(() => {
        console.log(i);
        debugger;
      }, 100);
    }

    {
      let i = 1;

      setTimeout(() => {
        console.log(i);
        debugger;
      }, 100);
    }

    {
      let i = 2;

      setTimeout(() => {
        console.log(i);
        debugger;
      }, 100);
    }
  };

  blockScopeTest(); // 0, 1, 2가 순서대로 찍힌다.
  ```

### # Spread 문법과 Rest 파라미터

- Spread 문법

  Spread 라는 단어가 가지고 있는 의미는 확산의 의미를 가지고 있다. 이 문법을 사용하면, 객체 혹은 배열을 펼칠수 있다. 즉, Spread 문법(...)은 대상을 개별 요소로 분리한다. 단, Spread 문법의 대상은 이터러블이어야 한다.

  ```javascript
  const animals = ["개", "고양이", "참새"];
  const anotherAnimals = [...animals, "비둘기"];

  console.log(animals); // ['개', '고양이', '참새']
  console.log(anotherAnimals); // ['개', '고양이', '참새', '비둘기']
  ```

- Rest 파라미터

  Rest 라는 단어가 가지고 있는 의미는 나머지라는 의미를 가지고 있다. 이 문법을 사용하면, 나머지 값을 묶어서 정의할 수 있다.

  ```javascript
  // 배열에서의 Rest
  const numbers = [0, 1, 2, 3, 4, 5, 6];
  const [one, ...rest] = numbers;

  console.log(one); // 0
  console.log(rest); // [1, 2, 3, 4, 5, 6]
  ```

  함수의 인자를 전달할 때 Rest 파라미터의 특성을 이용해서 가변 인자를 전달할 수 있다. 아래 예시 코드 내부 sum 함수는 인자로 들어오는 number를 모두 더하는 함수이다. 이 때 인자는 몇 가지가 들어올 지 모르는 가변 인자를 받고 있다. 이 때 Rest 파라미터를 사용해서 함수에 전달된 인수들의 목록을 배열로 받아 가변 인자를 받아 처리할 수 있다.

  ```javascript
  function sum(...rest) {
    return rest.reduce((acc, current) => acc + current, 0);
  }

  const result = sum(1, 2, 3, 4, 5, 6);
  console.log(result); // 21
  ```

<br>

### # 함수의 인자 복사 예시

- 자바스크립트에서 함수의 인자를 넘길 때, 인자는 값에 의한 전달(pass by value) 방식으로 처리된다. 이는 인자의 값이 복사되어 함수 내부로 전달되는 것을 의미한다. 이 때 복사하는 방식은 얕은 복사와 같이 처리된다.

  ```javascript
  const person = { name: "Lydia", age: 21 };

  const changeAge = (x = { ...person }) => (x.age += 1);

  const changeAgeAndName = (x = { ...person }) => {
    x.age += 1;
    x.name = "Sarah";
  };

  changeAge(person);
  changeAgeAndName();
  console.log(person); // { name: “Lydia”, age: 22 }
  ```

  코드의 전반적인 흐름은 객체 타입의 value를 업데이트 시키는 코드이다. value를 업데이트 시키기 위한 함수로 changeAge, changeAgeAndName 를 선언해서 사용하고 있는데 이 때 두 함수의 차이점은 호출문에서 인자 전달의 유무에서 차이점이 있다. 두 함수의 파라미터인 x식별자에 값이 할당되는 방식은 아래와 같이 할당된다.

  - changeAge : 인자로 전달 된 객체의 값을 복사하지만 참조 타입의 값을 복사하기 때문에 결국 같은 참조를 가리키게 된다. 즉 x의 값이 할당되는 방식은 const x = person와 같이 동작하게 된다.

  - changeAgeAndName : person 변수의 값 자체를 Spread로 복사하기 때문에 콜스택에서 x와 person은 서로 다른 메모리힙의 주소를 가리키고 있고 메모리힙에서의 메모리 value는 동일한 상태가 된다. 즉 x의 값이 할당되는 방식은 const x = { name: "Lydia", age: 21 }과 같이 동작하게 된다.

<br>

### # 동등 연산자 "==" vs 일치 연산자 "==="의 차이

- `==`는 동등 연산자로, 두 값을 비교할 때 자료형 타입이 다른 경우 형변환을 수행한 뒤 비교한다. 이러한 형변환은 때로 예측하지 못한 결과를 초래할 수 있다. `===`는 일치 연산자로 형변환없이 자료형 타입과 값 모두 비교한다. 따라서 일치 연산자를 활용하여 비교하는 것이 더 안전하다.

  ```javascript
  // 원시 타입 비교 예시
  console.log(100 == "100"); // true
  console.log(100 == 100); // true

  console.log(100 === "100"); // false
  console.log(100 === 100); // true
  ```

  또한 두 연산자 모두 참조 타입을 비교할 때는 동일한 참조 주소를 가리키는지 비교한다. 만약 참조 타입의 내부 값을 비교하려면 Object.entries, toString과 같은 메소드를 통해 원시 타입으로 변경해서 비교하거나 Lodash의 isEqual 메소드를 활용하여 비교할 수 있다.

  ```javascript
  // 참조 타입 비교 예시
  const a = { name: "Tom" };
  const b = { name: "Tom" };

  console.log(a == b); // ❌ false → 참조값(주소)이 다르니까 마찬가지
  console.log(a === b); // ❌ false → 내용이 같아도 서로 다른 객체이기 때문

  const c = a;
  console.log(a == c); // ✅ true → 같은 참조(주소)를 바라보고 있음
  console.log(a === c); // ✅ true → 같은 참조(주소)를 바라보고 있음
  ```

<br><br><br>
