## # CSS

<br>

### # CSS 전처리기

- CSS 전처리기란?

  CSS 전처리기란 자신만의 특별한 syntax를 가지고 CSS를 생성하도록 하는 프로그램을 말한다. 대표적인 CSS 전처리기로는 Sass, Less, Stylus 등이 있다. 하지만 CSS 자체가 발전하면서 전처리기의 의존도는 줄어들고 있다.

- CSS 전처리기가 만들어진 이유

  웹 페이지가 점점 크고 복잡해지면서 불필요한 선택자의 과한 사용과 구조가 명확하게 구분되지 않아 가독성이 떨어지고 유지보수를 어렵게 하여 이를 보완하기 위해 등장하였다.

- CSS 전처리기 장단점

  - 장점

    (1) 재사용성 증가로 인한 개발 시간 단축 : 변수 및 Mixins의 사용으로 일관된 테마를 사용하므로 재사용성이 증가하고 개발 시간이 단축된다.

    (2) 유지관리 : Nesting을 통해 구조가 명확해져 유지보수가 용이해지고 여러 파일로 나누어 관리가 가능해 짐, 이 경우 일반 css도 가능하지만 서버에서 불러오는 파일이 css 전처리기에 경우 컴파일된 1개의 스타일시트만 불러오게 된다.

    (3) 구문 차이 평준화 : 정해진 룰에 따라 작업하기 떄문에 협업 시 구문의 수준 차이를 평준화

  - 단점 (전컴)

    (1) 전처리기 도구 필요 : 전처리기를 위한 도구 필요

    (2) 컴파일 과정 추가 : CSS로 컴파일하는 과정이 추가 됨

- Sass를 사용하는 이유

  전부 다 사용해보지 않은 상태에서 Sass를 선택하게 되었다. 서칭을 통해 세 가지의 장단점을 확인해보고 선택하게 되었다. Less같은 경우 Sass에 비해 제공하는 기능에 한계가 있으며 Stylus는 Sass와 Less에 비해 비교적 늦게 나왔기 때문에 컴파일 후 사소한 버그가 생기는 경우가 있다고 한다. 그에 비해 Sass는 가장 오래되어 상대적으로 안정적이며 가장 활발히 개발되고 있다고 한다. 또 친숙한 문법과 다양한 기능을 제공하기 때문에 Sass를 선택하게 되었다.

- SCSS를 모듈로 사용한 이유

  클래스가 겹치지 않도록 관리해야하는 문제를 해결하기 위해 CSS Modules을 사용하여 고유한 해시 문자열을 추가해 CSS 속성이 겹치지 않도록 하기 위해 사용하였다.

- SCSS, SASS 차이는?

  (1) 문법 차이 : SASS는 들여 쓰기+줄 바꿈 형식, SCSS는 중괄호+세미콜론 형식 사용

  (2) 호환성 : SASS보다 SCSS가 CSS와의 호환성이 더 좋다

<br>

### # SCSS vs styled-components

- 각각의 차이점 (속파동시문클)

  (1) 실행 속도 : scss는 css파일이 추출되므로 자바스크립트 해석 과정이 필요 없고 styled-components는 자바스크립트 해석 과정이 필요하기 때문에 속도가 더 늦다.

  (2) 스타일 작성 파일 : scss는 css-in-css로 css파일에 작성되고, styled-components는 css-in-js로 js파일에 작성된다.

  (3) 동적 스타일링 : scss는 동적 스타일링이 어렵고 styled-components는 편하다.

  (4) 스타일 정보를 읽는 시점 : scss는 서버에서 컴파일된 1개의 스타일 시트를 불러와 html 문서에 읽혀져 있는 상태이며 styled-components는 컴포넌트가 렌더링 될 때만 해당 스타일 정보를 읽는다.

  (5) 문법 차이 : scss는 친숙한 문법이고 styled-components는 상대적으로 생소한 문법이다.

  (6) 클래스 사용 여부 : scss는 클래스를 일일히 지정해야하고 styled-components는 지정하지 않아도 된다.

<br>

### # CSS framework 사용경험

- 유명한 css 프레임워크로는 부트스트랩, 메터리얼UI, 테일윈드CSS 등이 있는 것으로 알고 있고 이 중 MUI를 사용해보았다. css 프레임워크를 사용하는 이유로는 빠르고 일관적인 스타일링과 프로젝트 유지 보수 시 빠른 캐치업이 가능하기 때문에 사용하는 것으로 알고 있다.

<br>

### # 반응형

- 반응형이란?

  반응형 웹이란 하나의 웹사이트에서 PC, 태블릿, 모바일 등 접속하는 디스플레이의 종류에 따라 크기가 자동으로 변하게 만든 웹페이지 접근 기법을 말한다.

- 반응형 웹의 3요소

  (1) 미디어 쿼리(Media query) : media 크기의 범위를 지정하여 css를 동적으로 설정한다. 미디어쿼리는 모바일 퍼스트 방식이 더 편리하다. 모바일 퍼스트 방식은 모바일을 기준으로 스타일을 작성하여 점점 확장해나가는 방식인데 적은 스타일에 필요한 스타일을 추가해나가는 것이 더 편리하기 때문에 모바일 퍼스트 방식이 더 편리한 방식이다. max-width(~px 이하에서 적용되는 속성) 대신 min-width(~px 이상에서 적용되는 속성)로 바꾸면 된다.

  (2) 유연한 레이아웃(Fluid Layout) : 웹 페이지의 요소들이 고정된 너비 대신 백분율(%) 또는 vw, vh와 같은 상대적인 단위를 사용하여 크기를 조정하도록 설정하는 방법으로 media 크기에 따라 그리드가 동적으로 변하도록 설정하는 것이다.

  (3) 유동적인 이미지(Flexible Images) : 유동적인 이미지는 이미지가 화면 크기에 맞춰 자동으로 크기가 조정되도록 만드는 방법이다. 이를 위해 max-width를 100% 사용하여 이미지가 부모 요소의 너비를 넘지 않도록 설정한다. 주의할 점은 모든 화면에서 볼 수 있는 적절한 크기의 이미지를 사용해야한다는 점이다.

- 적응형과 반응형의 차이를 아는가?

  반응형 웹은 하나의 템플릿을 사용해 모든 기기에 대응하는데 반해, 적응형 웹은 선별된 기기 유형에 따라 별도의 독립적인 템플릿이 요구한다. 반응형은 하나의 템플릿을 사용하므로 개발이 상대적으로 간편하다는 장점이 있지만 속도는 사용자 기기에 맞는 템플릿과 css만 다운로드하는 적응형이 더 빠르다.

<br>

### # display flex

- display flex

  display에 flex를 적용하여 flex container를 만들 수 있다.

- flex-direction

  flex container 내부에 flex item이 배치 방향을 설정한다. 디폴트 값은 row이다. 속성의 종류로는 row, column 등이 있다.

- justify-contents

  가로 축을 기준으로 flex item에 배치를 결정한다. 속성의 종류로는 flex-start, flex-end, center, space-between 등이 있다.

- align-items

  세로 축을 기준으로 flex item에 배치를 결정한다. 속성의 종류로는 stretch, flex-start, flex-end, center 등이 있다.

- flex-wrap

  flex item이 flex container를 넘어갈 때 줄바꿈 처리를 어떻게 할지 결정한다. 속성의 종류로는 nowrap, wrap 등이 있다.

- align-content

  줄바꿈이 허용된 상태에서 flex item이 두 줄 이상이 되었을 때 세로 축을 기준으로 flex item에 배치를 결정한다.

- flex-basis

  flex item에 기본 크기(ex px)를 지정한다. 0인 경우 flex-grow에 따라 크기가 동적으로 결정된다.

- flex-grow

  flex-grow는 컨테이너에 남는 공간이 있을 때 내부 flex item이 커질 비율을 지정한다. 디폴트 값은 0이며 0이 아닌 경우의 값은 flex-basis 값을 제외한 여백을 나눠갖는 비율이다.

  ```html
  <!-- container에 남는 공간이 300px인 경우, A는 100px B는 200px -->
  <div class="container">
    <div class="item" style="flex-grow: 1">A</div>
    <div class="item" style="flex-grow: 2">B</div>
  </div>
  ```

- flex-shrink

  flex-shrink는 컨테이너에 공간이 부족할 때 내부 flex item이 작아질 비율을 지정한다. 디폴트 값은 1이며 1이 아닌 경우의 값은 줄어드는 비율이다. 0으로 설정할 경우 flex-basis보다 작아지지 않기 때문에 고정 폭의 컬럼을 만들 수 있다.

  ```html
  <!-- container에 공간이 부족할 때 B가 A보다 더 많이 줄어든다 (비율 1:2) -->
  <div class="container">
    <div class="item" style="flex-shrink: 1">A</div>
    <div class="item" style="flex-shrink: 2">B</div>
  </div>
  ```

- flex

  flex-grow, flex-shrink, flex-basis를 한 번에 쓸 수 있는 축약형 속성이다. flex-grow, flex-shrink, flex-basis 순으로 속성을 부여한다. (ex flex 1 1 200px, flex 1 -> flex 1 1 0의 단축 속성)

<br>

### # display grid

- grid와 flex의 차이

  flex는 한 방향 레이아웃 시스템 (1차원)이고 grid는 두 방향(가로-세로) 레이아웃 시스템 (2차원)이다.

- grid 영역 구분

  컨테이너 -> 셀 -> 아이템 순으로 존재하며 셀 사이에는 가로 세로의 개별 번호를 가진 그리드 라인이 존재

- 그리드 용어

  - 그리드 컨테이너 (Grid Container)

    `display: grid`를 적용하는, Grid의 전체 영역이다. Grid 컨테이너 안의 요소들이 Grid 규칙의 영향을 받아 정렬된다고 생각하면 된다.

  - 그리드 아이템 (Grid Item)

    Grid 컨테이너의 자식 요소들이다. 바로 이 아이템들이 Grid 규칙에 의해 배치되는 것이다. `display: grid`를 적용한 요소의 `children`을 말한다.

  - 그리드 트랙 (Grid Track)

    Grid의 행(Row) 또는 열(Column)

  - 그리드 셀 (Grid Cell)

    Grid의 한 칸을 가리킨다. `display: grid`를 적용한 요소의 `children`과 같이 `<div>`같은 실제 html 요소는 그리드 아이템이고, 이런 Grid 아이템 하나가 들어가는 “가상의 칸(틀)”이라고 생각하면 된다.

  - 그리드 라인(Grid Line)

    Grid 셀을 구분하는 선이다.

  - 그리드 번호(Grid Number)

    Grid 라인의 각 번호이다.

  - 그리드 갭(Grid Gap)

    Grid 셀 사이의 간격이다.

  - 그리드 영역(Grid Area)

    Grid 라인으로 둘러싸인 사각형 영역으로, 그리드 셀의 집합이다.

- 그리드 속성

  - `display: grid`

    `grid 컨테이너에 적용하는 속성`이다. 해당 속성을 적용시킨 후 다른 gird 속성을 활용하여 그리드 컨테이너 요소의 자식 요소인 그리드 아이템 요소에 grid 규칙을 적용시킬 수 있다. `display: inline-grid` 속성도 있는데, 이건 block과 inline-block의 관계를 생각하면 된다. 아이템의 배치와 관련이 있다기 보다는, 컨테이너가 주변 요소들과 어떻게 어우러질지 결정하는 값이다. inline-grid는 inline-block처럼 동작한다.

  - grid-template-rows, grid-template-columns

    컨테이너에 지정해주는 속성이며 Grid 트랙의 크기들을 지정해주는 속성이다. grid-template-rows는 행(row)방향, grid-template-columns은 열(column)방향의 크기를 지정한다.

    - fr(fraction) 속성

      숫자 비율대로 트랙의 크기를 나눈다. 즉 위의 1fr 1fr 1fr은 균일하게 1:1:1 비율을 지정한다는 의미이다. 비율로 공간을 분배하기 위해 사용한다.

    - repeat 함수 속성

      반복되는 값을 자동으로 처리할 수 있는 함수이다. 첫번째 인자는 수이고 두번째 인자는 반복되는 값을 전달해주면 된다.

      ```css
      .container {
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        grid-template-rows: auto;
      }
      ```

    - minmax 함수 속성

      최솟값과 최댓값을 지정할 수 있는 함수이다. 예를 들어 minmax(100px, auto)의 의미는 최소한 100px, 최대는 자동으로(auto) 늘어나도록 한 것이다.

  - auto-fill과 auto-fit

    column의 개수를 미리 정하지 않고 설정된 너비가 허용하는 한 최대한 셀을 채운다. 만약 9개의 children을 가지는 부모 컨테이너에 `grid-template-columns: repeat(auto-fill, minmax(20%, auto))`과 같은 값을 지정하게 되면 두 개의 row와 다섯 개의 column을 가지는 레이아웃이 생성된다. 이 때 가장 끝 셀은 비어있게 된다. 왜냐하면 컬럼의 최소 크기를 20%로 지정해주었기 때문에 그리드 아이템은 로우 당 5개씩 아이템이 배치되고 두 번째 로우에는 4개의 아이템만 배치되게 된다. 이 때 auto-fit을 사용하면 나머지 셀의 크기를 균등하게 늘려 비어있는 셀을 채우게 된다. 또 auto-fill이나 auto-fit을 적용시킨 상태로 셀 크기를 px로 지정하면 브라우저 크기에 따라 레이아웃이 변경되도록 지정할 수 있다.

    ```css
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
    ```

  - row-gap, column-gap, gap

    셀 사이의 간격을 만든다.

  - grid-auto-columns, grid-auto-rows

    grid-template-columns, grid-template-rows의 통제를 벗어난 위치에 있는 트랙의 크기를 지정하는 속성이다. 예를 들어 children을 9개 가지고 있는 컨테이너에 grid-template-rows: repeat(3, minmax(50px, auto))와 같이 속성을 지정한다면 나머지 6개의 요소는 통제를 벗어난 위치에 있는 트랙이 되는 것이다. 이 때 grid-auto-rows: minmax(50px, auto)과 같이 해당 속성을 단독으로 사용하면 모든 트랙의 크기를 지정해줄 수 있다. 그리드 아이템 갯수를 미리 알 수 없을 때 유용하다.

    ```css
    .container {
      display: grid;
      grid-template-columns: 200px;
      grid-auto-columns: 100px;
      grid-auto-flow: column;
    }
    ```

    ```html
    <div class="container">
      <!-- 200px, 첫 번째 아이템 → 명시된 첫 번째 열 (200px) -->
      <div>1</div>
      <!-- 100px, 두 번째, 세 번째 아이템 → 자동으로 생긴 열 → grid-auto-columns: 100px -->
      <div>2</div>
      <!-- 100px -->
      <div>3</div>
    </div>
    ```

  - grid-column-start, grid-column-end, grid-column, grid-row-start, grid-row-end, grid-row

    이 속성들은 Grid 아이템에 적용하는 속성으로, Grid 아이템에 시작 위치와 끝 위치를 결정한다. 그리드 영역에는 그리드 라인 번호가 매겨져 있는데, 바로 그 번호를 이용해서 column과 row의 범위를 결정하는 것이다. 예를 들어 `grid-column: 1 / span 2` 속성을 지정하면 해당 Grid 아이템은 1번 그리드 라인이 시작 위치가 되고 Grid 아이템을 2칸 차지하는 영역이 끝 위치가 된다.

  - grid-template-areas

    각 영역(Grid Area)에 이름을 붙이고, 그 이름을 이용해서 배치하는 방법이다.

  - grid-auto-flow

    전체 아이템이 자동 배치되는 흐름을 결정하는 속성이다. 초기 속성은 행 방향 배치인 row이고, 열 방향 배치 속성인 column, 빈 셀 채우는 속성인 dense, 행 방향 배치와 빈 셀을 채우는 속성인 row dense, 열 방향 배치와 빈 셀을 채우는 속성인 column dense 등이 있다.

    ```css
    .container {
      display: grid;
      grid-template-columns: repeat(3, 100px);
      grid-auto-flow: row;
    }
    ```

    ```html
    <div class="container">
      <div>1</div>
      <div>2</div>
      <div>3</div>
      <!-- 다음 줄로 내려감 -->
      <div>4</div>
    </div>
    ```

  - align-items, justify-items

    align-items과 justify-items은 컨테이너에 적용되는 속성으로 셀 안에서 그리드 아이템들의 정렬 방식을 지정한다. align-items은 세로(column축) 방향, justify-items은 가로(row축) 방향을 지정할 수 있다. 기본 값은 stretch로 셀 내부에 꽉 차게 적용되고 축의 시작점부터 정렬 되는 start, 축의 중심점부터 정렬되는 center, 축의 끝점부터 정렬되는 end 등의 속성이 있다. 또 place-items이라는 축약형 속성으로 align-items과 justify-items을 한번에 지정해줄 수 있다. 해당 속성은 그리드 셀 내부 그리드 아이템들이 그리드 셀 내부에서 어떻게 배치되는지를 결정한다. 즉, 셀 위치에 영향을 주지 않고 셀 내부 아이템 위치에만 영향을 준다.

  - align-content, justify-content

    Grid 아이템들의 크기를 모두 합한 값이 Grid 컨테이너의 크기보다 작을 때 Grid 아이템들을 통째로 정렬한다. align-content은 세로(column축) 방향으로 그룹 정렬하는데 그리드 아이템들의 높이 합이 컨테이너 높이보다 작을 때 적용되고, justify-content은 가로(row축) 방향으로 그룹 정렬하는데 그리드 아이템들의 폭 합이 컨테이너 폭보다 작을 떄 적용된다. 기본 값은 stretch로 컨테이너 내부에 꽉 차게 적용되고 컨테이너 시작점부터 정렬되는 start, 컨테이너 중심점부터 정렬되는 center, 컨테이너 끝점부터 정렬되는 end, 그리드 아이템 사이에 균일한 간격을 두고 정렬되는 space-between, 그리드 아이템 둘레에 균일한 간격을 두고 정렬되는 space-around, 그리드 아이템 사이와 양 끝에 균일한 간격을 두고 정렬되는 space-evenly 속성 등이 있다. 또 place-content이라는 축약형 속성으로 align-content과 justify-content를 한번에 지정해줄 수 있다. 해당 속성은 그리드 컨테이너 내부 그리드 셀들이 어떻게 밷치되는지 결정한다. items 속성과는 다르게 셀 위치에 영향을 주고 셀 내부 아이템에는 영향을 주지 않는다.

  - align-self, justify-self

    그리드 아이템에 적용하는 속성으로 개별 아이템을 정렬할 수 있다. align-content와 justify-content와의 차이는 그리드 아이템 개별로 적용시킬 때 사용하는 속성이라는 것이다. 사용 방법은 동일하지만 개별로 동작하므로 stretch, start, center, end 속성만 존재한다. 또 place-self 축약형 속성으로 align-self justify-self를 한번에 지정해줄 수 있다.

  - order

    시각적 나열 순서를 결정하는 속성이다. 숫자 값이 들어가며 작은 숫자일 수록 먼저 배치된다. 시각적으로 변경되는 것일 뿐 HTML 자체 구조를 바꾸는 것은 아니므로 접근성 측면에서 사용에 주의하여야한다. 시각 장애인분들이 사용하는 스크린 리더로 화면을 읽을 때 order를 이용해 순서를 바꾼 것은 의미가 없다는 것이다.

  - z-index

    z-index로 Z축 정렬을 할 수 있다. 숫자가 클 수록 위로 올라온다. position에서의 z-index와 같은 개념이다.

<br>

### # before, after

- 가상 요소를 만들 때 사용하며 태그를 직접 추가하지 않고 장식 요소를 추가할 때 사용한다. 해당 속성을 사용함으로써 의미없는 태그를 추가하지 않아도 된다.

- float은 블록 요소를 강제로 정렬할 때 쓰인다. clear: both 속성을 통해 float 정렬을 취소했었다.

<br>

### # 이미지 파일 최적화 방법

- 이미지 크기 조절

  사용자에게 보여줄 너비를 고려하여 이미지 크기를 조절해 파일 용량을 줄인다.

- 이미지 포맷 변경

  avif와 같은 압축률이 좋은 이미지 포맷으로 변경한다. 단 지원하지 않는 브라우저를 고려하여 대체 이미지 처리가 필요하다. 예를 들어 picture 태그, source 태그, img 태그를 함께 사용하여 source 태그 이미지에 문제가 있는 경우 img 태그의 이미지를 fallback과 같이 사용할 수 있다. 또한 nextjs의 경우 이미지 최적화 모듈이 이미지 요청 헤더에 accept 필드에 있는 지원 가능한 이미지 포맷을 보고 알아서 변경해주기 때문에 크로스 브라우징 이슈에 유리하다.

  ```html
  <picture>
    <source srcset="image.avif" type="image/avif" />
    <source srcset="image.webp" type="image/webp" />
    <!-- source 태그 이미지의 문제가 있는 경우 아래 img 태그 이미지 노출, fallback 역할. source 태그에 media 속성을 활용하여 반응형도 이러한 방식으로 처리 가능 -->
    <img src="image.jpg" alt="description" />
  </picture>
  ```

- 디바이스 크기별 이미지 설정

  img 태그의 srcset 속성과 sizes 속성을 활용하여 디바이스 크기별 이미지를 설정한다. sizes 속성은 미디어쿼리와 같이 뷰포트 크기별로 이미지가 보여질 크기를 지정해줄 수 있고 srcset 속성을 통해 여러가지 크기의 이미지를 나열해놓을 수 있다. 예를 들어 현재 뷰포트 크기가 sizes 속성에 할당한 뷰포트 크기에 포함되는 경우 해당 뷰포트에서 보여질 이미지 영역 크기에 맞는 이미지를 srcset 속성에서 찾아 띄워주는 것이다. 디폴트 속성은 기존 사용하는 src 속성을 통해 지정해줄 수 있다.

  ```html
  <img
    srcset="images/500.png 500w, images/300.png 300w, images/150.png 150w"
    sizes="(min-width:960px) 500px, (min-width:640px) 300px, 320px"
    src="images/150.png"
    alt="gray-box"
  />
  ```

- 고정 값 설정

  치수가 없는 이미지들은 Reflow를 발생시켜 퍼포먼스를 저하시키고 CLS (Cumulative Layout Shift) 점수에 영향을 줘서 SEO에도 영향을 미친다. 그렇기 때문에 img 태그에 크기를 설정해준다.

- 이미지 스프라이트 기법

  이미지를 하나로 만든 뒤 position으로 이미지를 노출시키는 기법이다. 이미지 스프라이트 기법을 사용하면 트래픽이 절약되고 HTTP요청 횟수를 줄일 수 있다.

- image Lazy loading 기법

  페이지를 로드할 때, 모든 이미지를 로드하는 것이 아니라 중요하지 않은 자원 또는 당장 필요 없는 자원의 경우 서버에 요청을 미루고 필요한 경우 해당 자원을 요청 받는 기법이다. img 태그에 dateset 속성으로 url 저장 후 IntersectionObserver로 뷰포트 감지하여 뷰포트 내부에 이미지가 들어왔을 때 src 속성에 dateset 속성에 저장된 url을 할당하여 이미지 레이지 로딩을 적용시키는 방법과 img 태그에 loding 속성을 lazy로 설정하여 활용하는 방법 등으로 구현할 수 있다. 단, 이미지의 크기가 지정되어있어야 하고 페이지에서 가장 먼저 보이는 이미지는 사용하지 말아야한다. 또한 nextjs에서는 image 컴포넌트를 사용해 자동으로 이미지 레이지 로딩을 적용시킬 수 있다.

- image cdn 사용

  이미지 제공에 특화된 cdn을 사용한다. cdn은 이미지 제공 시 이미지를 줄이거나 포맷을 바꾸는 처리 과정을 통해 최적화 된 이미지를 제공한다. (ex AWS S3 + Cloudfront)

- nextjs 이미지 최적화 모듈 변경

  nextjs의 경우 이미지 최적화 모듈을 sqoosh에서 sharp로 변경해주는 것만으로도 이미지 최적화에 더욱 도움이 되는 것으로 알고 있다. -> 이미지 최적화 라이브러리인 sharp의 경우 next15 버전부터 자동으로 sharp를 사용하므로 수동으로 설치할 필요가 없다.

<br>

### # CSS의 attribute selector

- 속성 선택자로 요소 중 해당 속성을 가진 요소를 선택한다. 대괄호를 통해 속성을 지정할 수 있다.

  ```css
  a[href="https://velog.io"]
  {
    color: #ffffff;
  }
  ```

<br>

### # 박스형 모델

- 모든 HTML 요소는 박스 모양으로 구성되며, 이것을 박스형 모델이라고 한다. 박스형 모델은 margin, border, padding, content으로 구분된다. 구글 개발자 도구에서도 박스형 모델을 눈으로 확인해볼 수 있다. 이 박스형 모델의 크기는 box-sizing 속성을 통해 width, height 크기 적용의 기준을 변경할 수 있는데 기본 값은 content-box로 content 크기가 박스형 모델의 크기가 되고 border-box의 경우 border, padding, content 크기를 합한 크기가 박스형 모델의 크기가 된다. 즉 border와 padding을 계산하여 content 크기가 자동으로 줄어든다. 그렇기 때문에 대부분 정확한 박스 모델의 크기를 지정하기 위해 스타일 초기화 시 box-sizing: border-box를 적용시켜 지정한 width와 height가 그대로 박스형 모델 크기에 적용되도록 사용한다.

<br>

### # CSS 적용 우선순위

1. !important
2. 인라
3. id
4. class
5. 태그이름(ex div)

<br>

### # 네이밍 설계 규칙 BEM 방식

- BEM은 Block, Element, Modifier를 뜻하며 이 세 가지를 활용하여 목적의 명확성, 재사용성, 클래스 충돌 방지를 위해 사용하는 규칙이다. `__`, `--`로 구분하며 재사용과 확장을 위해 id를 사용하지 않고 class만 사용한다. Block은 독립적으로 재사용 가능한 기본 단위 (ex button, card, form), Element는 Block 내부의 구성 요소 (ex `button__icon`, `form__label`), Modifier는 Block이나 Element의 변형/상태(ex `button--primary`, `form__label--error`)를 나타낸다.

  ```html
  <div class="card">
    <h2 class="card__title">제목</h2>
    <p class="card__description">설명</p>
    <button class="card__button card__button--primary">확인</button>
  </div>
  ```

<br>

### # Element 숨기는 방법

- opacity : 0

  뷰포트 내 박스 모델 O, 공간 차지 O, 클릭 가능 여부 O

- visibility : hidden

  뷰포트 내 박스 모델 O, 공간 차지 O, 클릭 가능 여부 X

- display : none

  뷰포트 내 박스 모델 X (DOM은 있음), 공간 차지 X, 클릭 가능 여부 X

### # CSS selector 동작원리

- 스타일 엔진이 선택자 가장 마지막에 있는 키 선택자부터 왼쪽으로 이동하면서 규칙에 부합하는지 검사하면서 파싱을 진행한다. 우측 우선 탐색 방식이다.

  ```css
  ul li a.button {
    color: red;
  }
  /*
    1. 먼저 모든 .button 클래스를 가진 요소를 찾고
    2. 그 부모가 <a>인지 확인
    3. 그 위 조상이 <li>인지 확인
    4. 다시 그 위 조상이 <ul>인지 확인
  */
  ```

<br>

### # CSS 결합자 종류

- 자손 결합자 (A B)

  A 요소의 자손인 B를 선택

- 자식 결합자 (A > B)

  A의 바로 아래 자식인 B를 선택

- 일반 형제 결합자 (A ~ B)

  A와 같은 부모를 가진 모든 형제 B를 선택

- 인접 형제 결합자 (A + B)

  A와 같은 부모를 가진 형제 요소 중 첫 번째 형제 요소 B만 선택

- 열 결합자 (A || B)

  A와 같은 열에 속하는 B를 선택, 일반적인 CSS에서는 거의 안 쓰임

<br>

### # CSS 크기 지정 종류

<br>

- 절대 값(absolute)

  px

- 상대 값(relative)

  rem(루트, 최상위 부모 요소 폰트 기준), em(직계 부모 요소 폰트 기준), vw(뷰포트 기준), vh(뷰포트 기준), %(부모 크기 기준)

<br>

### # CSS 애니메이션 vs JavaScript 애니메이션

- 적용 시기

  CSS 애니메이션은 비교적 작은 효과(크기 변경, 색상 변경 등)에 적합, JS 애니메이션은 세밀한 효과(바운스, 일시 중지 등)에 적합

- 호환성

  JS 애니메이션이 상대적으로 호환성이 높음

- 실행 스레드

  CSS 애니메이션은 컴포지터 스레드에서 실행 되고, JS 애니메이션은 메인 스레드에서 실행 됨 (CSS가 효율적) 하지만 requestFrameAnimation을 활용하여 비동기로 애니메이션을 처리하여 효율적으로 프레임 타이밍에 맞춰 처리되기 때문에 렌더링 부하를 줄일 수 있다.

- GPU 가속

  GPU 가속이란 브라우저가 CSS나 애니메이션 등의 화면 렌더링 작업을 CPU(중앙 처리 장치)가 아닌 GPU(그래픽카드)에 맡기는 걸 말한다. CSS에서 `transform`, `opacity`, `will-change` 등의 속성은 GPU 가속이 적용된다. GPU 가속이 일어나는 특정 속성을 통해 layout이나 paint를 건너뛰고 바로 compositing 단계로 가기 때문에 성능을 향상 시킬 수 있다. 하지만 너무 많은 요소에 GPU 레이어를 적용하면 GPU 메모리 과부하 발생하여 오히려 성능 저하가 발생할 수 있다.

- GPU 가속 속성 예시

  - `transform`, `opacity`, `will-change`

  - `translate3d`, `scale`, `backface-visibility: hidden`, `perspective`

<br>

### # 이미지 리플레이스먼트(Image Replacement)

- 이미지 리플레이스먼트(Image Replacement) 기법이란?

  이미지 리플레이스먼트(Image Replacement) 기법은 스크린 리더 사용자들을 위한, 이미지를 대신하는 대체 텍스트를 제공하는 기법으로 웹 접근성 준수하기 위해 사용하는 기법이다. img 태그에 alt과 같은 목적으로 사용한다. 만약 background-img와 같이 사용되는 경우 대체 텍스트가 없기 때문에 이미지 리플레이스먼트(Image Replacement) 기법을 통해 대체 텍스트를 제공해주어야한다. 단 스크린 리더 사용자들을 위한 텍스트이므로 일반 사용자들에게 보여지지 않도록 숨겨주어야한다. text-indent 속성을 활용한 방법, 추가 태그와 z-index 속성을 활용한 방법, clip 속성을 활용한 방법등이 있다. 주의할 점은 display none, 요소 크기 0, opacity 0 등의 방법은 스크린 리더가 읽을 수 없으므로 사용하지 않아야한다.

- 이미지 리플레이스먼트(Image Replacement) 기법 적용 방법 (텍제클)

  (1) text-indent 활용 : text-indent 속성(들여쓰기)을 -9999px로 주어 화면 밖으로 텍스트를 날리는 방법

  (2) z-index 활용 : 추가 태그(span)를 사용하고 position relative와 z-index -1로 설정하여 이미지 아래로 텍스트를 숨기는 방법

  (3) clip 속성 활용 : position을 absolute로 설정한 뒤 width와 height를 1px로 주고 화면 상 숨기기 위해 margin -1px을 설정하고 overflow hidden을 설정한다. 그 후 클리핑 범위를 0으로 설정하여 숨겨버린다.

<br>

### # 브라우저 스펙 차이에 따른 스타일링 이슈 처리

- 브라우저마다 렌더링 엔진이 달라 디폴트 스타일이 다르기 때문에 reset.css 파일을 이용하여 모든 디폴트 스타일을 초기화한 후 프로젝트를 진행한다. reset 파일 내부에서 태그별 기본 margin, padding, border 등을 제거해주거나 list-style 혹은 line-height 등을 기본 값으로 할당한다. 또한 css 속성 사용 시 호환되는 브라우저를 확인한 후 사용한다.

<br>

### # CSS(Cascading Style Sheets)에서 Cascading에 의미

- 케스케이딩은 흐르는, 종속하는 의미를 가지고 있고 어떤 스타일로 브라우저에 표현할 지 결정해주는 시스템을 의미한다. 케스케이딩 시스템을 사용하였을 때의 장점은 부모 요소의 스타일이 자식 요소에게 상속되는 점을 활용하여 부모 요소에 적절한 스타일을 부여할 경우 되므로 코드의 양을 줄여 성능 향상에 기여할 수 있다. 일반적으로 박스 모델과 관련된 속성(margin, padding, border, witdh, height 등)은 상속되지 않고 폰트와 관련된 속성(color, font-family, font-size, text-align 등)들은 상속된다. 기본적으로 상속되지 않는 속성을 상속하기 위해서 inherit 값을 사용할 수 있다.

<br>

### # root 선택자

- CSS의 :root속성을 통해 문서 트리의 루트 요소를 선택할 수 있다. HTML의 루트 요소는 `<html>`요소 선택자를 나타낸다. 다크 모드같은 경우 유용하게 사용할 수 있다.

  ```css
  /* :root에서 기본 색상 설정 (라이트 모드) */
  :root {
    --background-color: white;
    --text-color: black;
    --link-color: blue;
    --button-background: lightgray;
    --button-color: black;
  }
  ```

<br>

### # position 속성

- static : 기본 값이다. 차례대로 왼쪽에서 오른쪽, 위에서 아래로 쌓인다.

- relative : 자신의 위치를 기준으로 이동한다.

- absolute : 상위 요소의 relative를 기준으로 이동한다.

- fixed : 브라우저 창을 기준으로 스크롤 시 항상 고정된다.

- sticky : 부모 요소를 기준으로 스크롤 시 위치가 고정된다. 부모 요소의 특정 위치를 지나면 스크롤에 따라 고정이 해제되고, 다시 원래 문서 흐름으로 돌아간다.

<br>

### # image object-fit 속성

- none : 이미지의 크기를 조절하지 않으며 원본 이미지 크기 그대로 유지한다.

- fill : 이미지 비율 유지 x, 컨텐츠 박스 가로, 세로 크기에 딱 맞도록 이미지 크기를 조절한다.

- contain : 이미지 비율 유지 o, 컨텐츠 박스에 이미지가 모두 포함되도록 이미지 크기를 조절한다. 컨텐츠 박스와 비율이 일치하지 않으면 컨텐츠 박스 내부에 여백이 생긴다.

- cover : 이미지 비율 유지 o, 컨텐츠 박스 가로, 세로가 모두 차도록 이미지를 크기를 조절한다. 컨텐츠 박스와 비율이 일치하지 않으면 이미지가 잘릴 수 있다.

- scale-down : none과 contain 중 이미지 크기가 더 작아지는 값을 선택한다.

<br>

### # 사용했던 CSS 속성 순서 컨벤션

1. Layout Properties (position, float, clear, display)

2. Box Model Properties (width, height, margin, padding)

3. Visual Properties (color, background, border, box-shadow)

4. Typography Properties (font-size, font-family, text-align, text-transform)

5. Misc Properties (cursor, overflow, z-index)

<br>

### # Runtime CSS-in-JS vs Zero Runtime CSS-in-JS

- Runtime CSS-in-JS

  Runtime CSS-in-JS는 런타임에서 javascript를 통해 동적으로 스타일을 생성한다. 대표적인 라이브러리로는 styled-components, emotion 등이 있다.
  개발모드에서는 디버깅에 이점이 있는 `<style>` 태그에 style을 추가하는 방식을 사용하고 배포 모드에서는 성능상의 이점이 있는 stylesSheet을 CSSStylesSheet.insertRule 통해
  바로 CSSOM에 주입하는 방식을 사용한다. CSS 파일을 생성하지 않기에 webpack에서 css-loader가 필요 없고 매우 복잡한 애니메이션 구현 시 런타임 오버헤드가 발생할 수 있다.
  또한 SSR 사용 시에도 문제가 될 수 있다. 예를 들어 styled-components 사용 시 별도의 설정을 하지 않는 경우 SSR에서 FOUC(스타일 번쩍임) 문제가 발생한다.
  이유는 styled-components는 Runtime CSS-in-JS로 런타임에 동적으로 스타일 시트를 생성하고 style 태그 내부에 추가된 뒤 DOM에 적용된다.
  그렇기 떄문에 서버에서는 서버 사이드 렌더링 시 스타일 생성이 되지 않아 페이지가 사용자에게 보여진 뒤 javascript 로드 후 스타일이 적용되는 깜빡임 문제가 발생하는 것이다.
  그렇기 떄문에 SSR에서 제대로 동작하게 하기 위해서는 별도의 설정이 필요하다. 이러한 문제로 인해 Zero Runtime CSS-in-js 라이브러리가 대체되어 사용되기도 한다.

- Zero Runtime CSS-in-JS

  Zero Runtime CSS-in-js는 Runtime CSS-in-JS와 다르게 CSS를 빌드 타임에 정적으로 생성한다.
  Webpack이나 Vite 같은 빌드 도구가 컴파일 타임(빌드 타임)에 Javascript를 실행(runtime)하지 않고 정적으로 파싱해서 정적 .css 파일을 추출하는 방식이다. 대표적인 라이브러리로는 vanilla-extract가 있다.
  CSS가 JS와 동일한 번들에 있는 Runtime CSS-in-JS와 달리 CSS와 JavaScript를 병렬로 로드할 수 있으므로 페이지 로드 시간이 향상되고 CSS 구문 분석과 같은 추가 작업이 런타임에 수행될 필요가 없기 때문에 런타임 성능이 향상된다.
  하지만 빌드 타임에 CSS를 생성하기 때문에 Babel이나 Webpack을 사용 시 직접 webpack 설정을 변경해줘야 하며 만약 CRA를 사용하고 있다면 eject를 해주고 loader를 설치해서 설정을 해줘야 하기 때문에 번거로울 수 있고 runtime에서 css polyfill를 사용할 수 없어 구형 브라우저에서 크로스 브라우징 이슈가 있을 수 있다.
  또한 props를 활용한 동적 스타일링을 위해서는 CSS 변수를 활용하여 적용하거나 @vanilla-extract/dynamic와 같은 패키지를 함께 사용해주어야한다.

- 오버헤드

  프로그램(런타임 혹은 빌드타임)의 실행 흐름 도중에 특정 기능을 수행하기 위해 추가적인 연산, 메모리 접근, 또는 처리 과정을 거쳐야 할 때 추가적으로 시간, 메모리, 자원이 사용되는 현상이다.
  한마디로 정의하자면, 오버 헤드는 특정 기능을 수행하는데 드는 간접적인 시간, 메모리 등 자원을 말한다. 예를 들어, 10초 걸리는 기능이 간접적인 원인으로 20초걸린다면 오버헤드는 10초가 되는것이다.

<br><br><br>
