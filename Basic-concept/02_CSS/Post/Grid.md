# [CSS] Grid

<br>

## 1. Grid 속성

CSS 레이아웃을 잡을 때 display 속성 중 `flex` 혹은 `gird` 속성을 많이 사용한다.

두 속성의 차이점은 아래와 같다.

- **Flex** : 한 방향 레이아웃 시스템 (1차원)
- **Grid** : 두 방향(가로-세로) 레이아웃 시스템 (2차원)

![CSS_Grid_01](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/2caaedbb-6ed0-4c4b-93a1-12e31c127610)

그리드 용어를 정리해보면 아래와 같다.

![CSS_Grid_02](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/db1d6d95-5f57-46d6-b324-67c80fbd27ae)

- **그리드 컨테이너 (Grid Container) :** `display: grid`를 적용하는, Grid의 전체 영역이다. Grid 컨테이너 안의 요소들이 Grid 규칙의 영향을 받아 정렬된다고 생각하면 된다.
- **그리드 아이템 (Grid** **Item) :** Grid 컨테이너의 자식 요소들입니다. 바로 이 아이템들이 Grid 규칙에 의해 배치되는 것이다. `display: grid`를 적용한 요소의 `children`을 말한다.
- **그리드 트랙 (Grid Track) :** Grid의 행(Row) 또는 열(Column)
- **그리드 셀 (Grid Cell) :** Grid의 한 칸을 가리킨다. `display: grid`를 적용한 요소의 `children`과 같이 <div>같은 실제 html 요소는 그리드 아이템이고, 이런 Grid 아이템 하나가 들어가는 “가상의 칸(틀)”이라고 생각하면 된다.
- **그리드 라인(Grid Line) :** Grid 셀을 구분하는 선이다.
- **그리드 번호(Grid Number) :** Grid 라인의 각 번호이다.
- **그리드 갭(Grid Gap) :** Grid 셀 사이의 간격이다.
- **그리드 영역(Grid Area) :** Grid 라인으로 둘러싸인 사각형 영역으로, 그리드 셀의 집합이다.

브라우저에서 크롬 개발자 도구를 활용하여 디버깅할 때 `grid`가 적용되어 있는 컨테이너 요소의 grid 버튼이 생성되어 있는 것을 볼 수 있다. 이 버튼을 클릭하면 grid 속성 설정 시 더 편하게 작업할 수 있다.

![CSS_Grid_03](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/a110caf1-fd77-4282-a628-0419aed1be90)

<br>
<br>

## 2. 속성 알아보기

Grid의 속성들은 Flex와 마찬가지로 컨테이너에 적용하는 속성, 아이템에 적용하는 속성으로 나뉜다.

![CSS_Grid_04](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/3a7736da-275d-4908-a078-87189a7ebef7)

이제 각 속성에 대해 알아보자. 속성을 적용시킬 HTML 구조는 아래와 같다.
또한 육안으로 확인하기 쉽게 그리드 컨테이너는 파란색 보더, 그리드 아이템에는 빨간색 보더를 적용시켰다.

```html
<div class="container">
  <div class="item">A</div>
  <div class="item">B</div>
  <div class="item">C</div>
  <div class="item">D</div>
  <div class="item">E</div>
  <div class="item">F</div>
  <div class="item">G</div>
  <div class="item">H</div>
  <div class="item">I</div>
</div>
```

```css
.container {
  border: 1px solid blue;
}

.container .item {
  border: 1px solid red;
}
```

<br>

### 2-1. `display: grid`

```css
.container {
  display: grid;
  /* display: inline-grid; */
}
```

`grid 컨테이너에 적용하는 속성`이다. 해당 속성을 적용시킨 후 다른 gird 속성을 활용하여 그리드 컨테이너 요소의 자식 요소인 그리드 아이템 요소에 grid 규칙을 적용시킬 수 있다.

`display: inline-grid` 속성도 있는데, 이건 block과 inline-block의 관계를 생각하면 된다.

아이템의 배치와 관련이 있다기 보다는, 컨테이너가 주변 요소들과 어떻게 어우러질지 결정하는 값이다. inline-grid는 inline-block처럼 동작한다.

아래 이미지는 gird 컨테이너가 적용 된 요소가 span 요소와 함께 배치 된 상태인데 grid 컨테이너 속성은 좌측 이미지는 `display: grid`, 우측 이미지는 `display: inline-grid` 속성이 적용 된 모습이다. 좌측 이미지에서는 gird 컨테이너가 모든 width를 차지하여 inline 요소인 span이 아래에 배치된 것을 볼 수 있고 우측 이미지는 gird 컨테이너가 자기 자신의 영역만큼 width를 차지하여 inline 요소와 함께 배치된 것을 볼 수 있다.

| ![CSS_Grid_05-1](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/d3ebcbb6-1969-4be9-872e-2d469c1e889a) | ![CSS_Grid_05-2](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/64cf1c57-1f7c-4418-af92-aa4d0eff54b5) |
| :----------------------------------------------------------------------------------------------------------------: | :----------------------------------------------------------------------------------------------------------------: |

<br>

### 2-2. 그리드 형태 정의 grid-template-rows, grid-template-columns

컨테이너에 Grid 트랙의 크기들을 지정해주는 속성이다. 여러가지 단위(`px`, `fr`, `%` 등)를 사용할 수 있고 섞어서 쓸 수도 있다.

```css
.container {
  grid-template-columns: 200px 200px 500px;
  /* grid-template-columns: 1fr 1fr 1fr */
  /* grid-template-columns: repeat(3, 1fr) */
  /* grid-template-columns: 200px 1fr */
  /* grid-template-columns: 100px 200px auto */

  grid-template-rows: 200px 200px 500px;
  /* grid-template-rows: 1fr 1fr 1fr */
  /* grid-template-rows: repeat(3, 1fr) */
  /* grid-template-rows: 200px 1fr */
  /* grid-template-rows: 100px 200px auto */
}
```

- **grid-template-rows** : 행(row)의 배치
- **grid-template-columns** : 열(column)의 배치

예를 들어 `grid-template-columns: 200px 200px 500px;` 의 경우 column을 200px, 200px, 500px로 3개의 컬럼을 만들겠다는 의미(하단 좌측 이미지)이다. 만약 200px, 200px과 같이 두 가지 속성만 적용시킨다면 column은 200px, 200px의 2개의 컬럼이 생성(하단 우측 이미지)된다.

| ![CSS_Grid_06-1](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/9f53aee1-d456-4c0b-b503-cd8e6867f111) | ![CSS_Grid_06-2](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/61f2eb62-6157-4760-ad2b-a6c8f6548af0) |
| :----------------------------------------------------------------------------------------------------------------: | :----------------------------------------------------------------------------------------------------------------: |

<br>

#### 2-2-1. fr 속성

또 위 속성을 보면 `1fr`과 같은 속성 값이 사용되는데 fr은 fraction으로 숫자 비율대로 트랙의 크기를 나눈다. 즉 위의 `1fr 1fr 1fr`은 균일하게 1:1:1 비율인 3개의 column을 만들겠다는 의미이다.

```css
.container {
  border: 1px solid blue;
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
}
```

![CSS_Grid_07](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/519c5d51-0226-44be-b81b-d72c3a0980d5)

섞어서도 사용할 수 있다.

```css
.container {
  border: 1px solid blue;
  display: grid;
  grid-template-columns: 100px 2fr 1fr;
}
```

![CSS_Grid_08](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/f6d88e8d-c8d2-4604-8086-a398c9ca8ef6)

첫번째 컬럼의 크기는 100px, 두번째 컬럼과 세번째 컬럼의 크기는 남은 부분의 크기를 2:1 비율로 나누어 유연하게 움직이게 된다.

<br>

#### 2-2-2. repeat 함수 속성

또 위 속성 중 `repeat`라는 속성이 있다. 속성 이름만 보아도 무엇이 반복될 것 같은 느낌이 든다. 이 속성은 반복되는 값을 자동으로 처리할 수 있는 함수이다. 예를 들어 기존에 사용하던 방법같이 균등한 컬럼 5개를 생성한다고 했을 때 아래와 같은 속성을 적용시킬 수 있다.

```css
.container {
  border: 1px solid blue;
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr 1fr;
}
```

하지만 이러한 부분을 repeat를 통해 처리할 수 있다. repeat의 첫번째 인자는 반복되는 수이고 두번째 인자는 반복되는 값을 전달해주면 된다.

```css
.container {
  border: 1px solid blue;
  display: grid;
  grid-template-columns: repeat(5, 1fr);
}
```

위와 같이 사용할 수도 있고 `repeat(3, 1fr 4fr 2fr);` 이런 식의 패턴도 가능하다.

<br>

#### 2-2-3. minmax 함수 속성

최솟값과 최댓값을 지정할 수 있는 함수이다.

```css
.container {
  border: 1px solid blue;
  display: grid;
  grid-template-columns: repeat(3, minmax(100px, auto));
}
```

만약 위와 같이 처리한다고 했을 때 `minmax(100px, auto)`의 의미는 최소한 100px, 최대는 자동으로(auto) 늘어나도록 한 것이다. 즉 컬럼의 개수는 3이고 최소 px은 100px이므로 최소 300px의 크기를 가지게 되는데 브라우저 창 크기가 300px 미만으로 줄어들어도 해당 그리드 아이템들의 크기는 최소 100px씩 유지하게 되는 것이다. 아래 이미지는 위 속성을 준 뒤 브라우저창을 줄여본 이미지이다. 빨간 보더 부분이 그리드 아이템 영역인데 브라우저창을 영역을 벗어나 100px씩 유지되고 있는 것을 볼 수 있다.

![CSS_Grid_09](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/73019ec4-4bae-4432-a18b-aaa5378691e8)

<br>

#### 2-2-4. auto-fill과 auto-fit

`auto-fill`과 `auto-fit`은 column의 개수를 미리 정하지 않고 설정된 너비가 허용하는 한 최대한 셀을 채운다.

```css
.container {
  border: 1px solid blue;
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(20%, auto));
}
```

만약 위와 같이 `repeat(auto-fill, minmax(20%, auto))` 속성을 적용시키는 경우 컬럼 하나는 최소 20%의 크기를 가지고 있기 때문에 아래와 같이 한 개의 row에 5개의 셀이 만들어진다.

![CSS_Grid_10](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/0c025523-a82c-44d8-85f6-b16d29e74a2c)

만약 A-I까지의 text가 담긴 그리드 아이템이 9개인 상태로 최소 크기를 10%를 설정하면 어떻게 될까?

![CSS_Grid_11](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/f359b3b7-8d09-4de9-af7d-bddd8135377d)

바로 위와 같이 한 개의 row에 10개의 셀이 만들어지는데 그리드 아이템은 9개 밖에 없으므로 한 개의 셀은 비어있는 상태로 유지된다. 이 때 사용할 수 있는 속성이 `auto-fit` 속성이다. 해당 속성을 설정하는 경우 비어있는 셀이 있을 때 나머지 셀의 크기를 균등하게 나누어 아래와 같이 늘려준다. 아래는 `repeat(auto-fit, minmax(10%, auto))` 속성이 적용 된 상태이다.

![CSS_Grid_12](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/d8dad165-c3e6-4d91-a4e5-e8b3acd18649)

또 만약 `auto-fit`이나 `auto-fill`이 적용 된 상태에서 위와 같이 퍼센트로 그리드 아이템의 크기를 결정하는 것이 아닌 px로 크기를 결정한다면 어떻게 될까? 해당 속성들은 미리 컬럼의 개수를 정하지 않고 설정 된 너비가 허용하는 선에서 최대한 컬럼을 채운다고 했는데 이 말과 같이 px 크기가 들어가는 한 컬럼을 계속 생성하게 된다. 아래와 같은 코드를 적용시킨다고 가정해보자.

```css
.container {
  border: 1px solid blue;
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(100px, auto));
}
```

우선 결과는 아래 이미지와 같다. 현재 해당 그리드 컨테이너의 속성은 div 태그에 적용되어 있고 `display: gird`로 되어 있기 때문에 block 요소와 같이 브라우저 창 크기에 따라 width가 변경된다. 이 상태로 auto-fill 속성이 적용되어 컨테이너 크기에 맞게 최소 크기 100px의 그리드 아이템이 들어가기 때문에 브라우저 창이 변경될 때 마다 해당 크기에 맞게 그리드 아이템들이 정렬되는 것을 볼 수 있다.

![CSS_Grid_13](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/69ce0203-4d07-412c-b0ac-460afebae34d)

<br>

### 2-3. 간격 만들기 row-gap, column-gap, gap

`gap` 속성은 속성 이름과 같이 그리드 셀 사이의 간격을 설정한다. px, rem 등의 단위를 모두 사용할 수 있다.

```css
.container {
  border: 1px solid blue;
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(100px, auto));
  gap: 20px;
  /* grid-gap: 20px; */
}
```

- **gap** : row, column 함께 조절, `10px`혹은 `10px 10px`과 같이 할당
- **row-gap** : row를 기준으로 gap 조절
- **column-gap** : column을 기준으로 gap 조절
- **grid-gap** : 초기에 사용하던 gap 속성인데 브라우저 호환성을 위해 gap과 함께 작성하기도 한다.

<br>

### 2-4. 그리드 형태를 자동으로 정의 grid-auto-columns, grid-auto-rows

`grid-auto-columns`, `grid-auto-rows`는 grid-template-columns, grid-template-rows의 통제를 벗어난 위치에 있는 트랙의 크기를 지정하는 속성이다. 예를 들어 아래와 같은 코드가 적용되었다고 해보자.

```css
.container {
  grid-template-rows: repeat(3, minmax(50px, auto));
}
```

그러면 아래 이미지와 같이 3개의 그리드 트랙 크기가 최소 50px로 지정되며 나머지 그리드 트랙은 통제를 벗어나게 된다.

![CSS_Grid_14](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/f829096d-780b-470c-82eb-dee183a7430f)

이와 같이 그리드 트랙, 그리드 아이템의 갯수를 미리 알 수 없을 때 유용하게 사용할 수 있다. 아래와 같이 변경해보자.

```css
.container {
  grid-auto-rows: minmax(50px, auto);
}
```

변경하면 아래 이미지와 같이 모든 그리드 트랙에 지정한 크기가 적용된 것을 볼 수 있다. 이와 같이 `grid-auto-rows` 혹은 `grid-auto-columns`를 사용하게되면 굳이 횟수를 지정해서 반복할 필요가 없다. 위와 같이 작성하는 `grid-template-rows`나 `grid-template-columns`로 미리 세팅해두지 않는 경우 모든 그리드 트랙은 통제를 벗어나는 것이기 때문에 전체적으로 사이즈를 지정해줄 수가 있는 것이다. 만약 `grid-template-rows`나 `grid-template-columns`로 미리 세팅해두었다면 통제를 벗어난 그리드 트랙만 해당 속성이 적용된다.

![CSS_Grid_15](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/58afc501-719b-47b8-8dc5-c22a46dcaf74)

만약 특정 아이템에 관한 데이터 정보를 api를 통해 받아와 사용자에게 뿌려주어야할 때 해당 아이템에 관한 갯 수가 미리 지정되어 있지 않다면 이런 속성을 활용해도 좋을 것 같다.

<br>

### 2-5. 각 셀의 영역 지정 grid-column-start, grid-column-end, grid-column, grid-row-start, grid-row-end, grid-row

이 속성들은 `Grid 아이템`에 적용하는 속성으로, 각 셀의 영역을 지정한다. 아래 그림을 보면 1부터 4까지의 Grid 라인 번호가 매겨져 있는데, 바로 그 번호를 이용해서 column과 row의 범위를 결정하는 것이다.

![CSS_Grid_16](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/9aeac510-d6fe-4a7d-8ea0-4cb1b800f808)

column으로 살펴보면, grid-column-start가 시작 번호, grid-column-end가 끝 번호입니다. `grid-column`은 start와 end 속성을 한번에 쓰는 `축약형`이다.

```css
.container {
  border: 1px solid blue;
  display: grid;
  grid-template-columns: repeat(5, auto);
}

.item:nth-child(1) {
  grid-column-start: 1;
  grid-column-end: 3;
  /* grid-column: 1 / 3; */
}
```

아래 이미지와 같이 맨 좌측 1번 컬럼 라인부터 3번 컬럼 라인까지 영역을 차지하는 것을 볼 수 있다.

![CSS_Grid_17](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/7eaaae94-cd36-44cd-85db-8b02de748449)

또한 시작 번호부터 몇 개의 셀을 차지할 것인지도 지정해줄 수 있다. 결과는 위 이미지와 동일하다. 시작 번호인 1번 컬럼 라인부터 2칸을 차지하도록 한다. 그러면 1번과 2번사이 칸, 2번과 3번 사이의 칸을 차지하여 위와 동일한 결과를 얻을 수 있다.

```css
.item:nth-child(1) {
  grid-column: 1 / span 2;
}
```

<br>

### 2-6. 영역 이름으로 그리드 정의, grid-template-areas

각 영역(Grid Area)에 이름을 붙이고, 그 이름을 이용해서 배치하는 방법이다. 정말 직관적인 방법이다.

아래 예시를 보자.

![CSS_Grid_18](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/bba2d799-ff69-480b-911f-c8505272dd42)

위 이미지와 같이 Grid Area를 작성해보자. 우선 herder와 footer는 row에서 3개의 column을 차지하고 있으니 3번씩 작성해주었고 a, main, b는 각각 작성되었다. 그리고 빈칸의 경우 `.` 혹은 `none`으로 표시할 수있다. 해당 Grid Area는 아래와 같이 작성할 수 있다.

```css
.container {
  grid-template-areas:
    "header header header"
    "   a    main    b   "
    "   .     .      .   "
    "footer footer footer";
}
```

위와 같이 Grid Area를 작성 후 아래와 같이 위치를 변경시킬 수 있다. `grid-area` 속성에 value로 해당 `area의 이름`을 할당해주면 된다.

```css
.item:nth-child(1) {
  grid-area: main;
}
```

결과는 아래와 같다. 첫번째 아이템이었던 A가 main이 위치한 영역에 위치한 것을 볼 수 있다.

![CSS_Grid_19](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/f464ca1a-4569-452b-a14e-78aa8d82cd0a)

<br>

### 2-7. grid-auto-flow

아이템이 자동 배치되는 흐름을 결정하는 속성이다. 하나씩 적용시켜보자.

우선 기준이 되는 레이아웃은 아래와 같다.

```css
.container {
  border: 1px solid blue;
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(25%, auto));
  grid-template-rows: repeat(5, minmax(50px, auto));
}

.container .item {
  border: 1px solid red;
}

.item:nth-child(2) {
  grid-column: auto / span 3;
}
.item:nth-child(5) {
  grid-column: auto / span 3;
}
.item:nth-child(7) {
  grid-column: auto / span 2;
}
```

![CSS_Grid_20](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/f7e42a5b-0728-45fd-ae7c-95ae004cc5a6)

우선 columns는 최소 크기를 25%로 지정였고 rows는 50px로 지정하였다. 그 후 B, E, G의 경우 각각 셀을 3개 또는 2개를 점유하도록 설정했다. 그렇기 때문에 영역을 초과하여 빈 칸이 생겼다. grid 배치의 기본 설정은 아이템이 row를 기준으로 순서대로 배치 되다가 들어갈 자리가 없으면 그 칸을 비워두고 아래로 배치가 된다. 즉 초기 값은 `grid-auto-flow: row`이다. 이 기본 설정을 한번 바꿔보자.

![CSS_Grid_21](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/3db6f52b-aa3b-40aa-aacb-1d3f7cc18038)

위 이미지는 `grid-auto-flow: column` 을 적용시킨 이미지이다. 컬럼을 기준으로 그리드 아이템이 순서대로 배치되는 것을 볼 수 있다.

![CSS_Grid_22](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/b3a27ecd-36a9-45ea-98d7-899a87112cec)

위 이미지는 `grid-auto-flow: dense` 를 적용시킨 이미지이다. D옆에 비어있던 공간을 사이즈가 맞는 F, H가가 채우고 기존에 F 자리를 I가 채우는 것을 볼 수 있다. `dense` 속성은 기본적으로 빈 셀을 채우는 알고리즘이다. 빈 셀을 채우는 기준은 row와 column에 따라 기준이 달라진다.

![CSS_Grid_23](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/0116f778-9f02-492f-a167-b34a26a33ded)

위 이미지는 `grid-auto-flow: row dense` 를 적용시킨 이미지이다. `row`를 기준으로 배치하고 빈 셀을 채우는 모습을 볼 수 있다.

![CSS_Grid_24](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/9fad97ed-31e0-43d7-ae0c-fbd537d60bec)

위 이미지는 `grid-auto-flow: column dense` 를 적용시킨 이미지이다. `column`을 기준으로 배치하고 빈 셀을 채우는데 빈 셀이 없기 때문에 `grid-auto-flow: colum` 과 동일하게 적용된 것처럼 보인다.

<br>

### 2-8. 세로 방향 정렬 align-items, 가로 방향 정렬 justify-items

`align-items`은 컨테이너에 적용되는 속성으로 아이템들을 세로(column축) 방향으로 정렬한다. `justify-items`은 컨테이너에 적용되는 속성으로 아이템들을 가로(row축) 방향으로 정렬한다. 방향만 다를 뿐 동작 방식은 동일하기 때문에 `align-items`을 기준으로 테스트해보자.

기준이 되는 레이아웃은 아래와 같다.

```css
.container {
  border: 1px solid blue;
  display: grid;
  grid-template-columns: repeat(3, minmax(25%, auto));
  grid-template-rows: repeat(3, minmax(50px, auto));
}
```

![CSS_Grid_25](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/6639f151-bf4f-4561-89b8-addeecf5c00b)

이제 각 속성들을 적용시켜보자. 우선 `align-items: stretch`이다. `stretch`는 기본 값으로 위 이미지와 동일하게 나타난다.

다음은 `start`이다. start는 아래 이미지와 같이 column 축의 시작 지점을 기준으로 그리드 아이템이 배치되는 것을 볼 수 있다. 그리드 아이템이 줄어드는 것 같이 보이는 이유는 그리드 아이템이 기존에 마치 block 요소와 같이 셀 크기를 모두 차지하는 크기를 가지다가 해당 속성이 변경되면 마치 inline 요소처럼 자기 자신의 크기만큼만 차지하는 형태로 변경되기 때문이다.

![CSS_Grid_26](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/bea01ae9-68e2-4dc0-a29c-acca4443dbf2)

다음은 `center`이다. center는 아래 이미지와 같이 column 축의 중간 지점을 기준으로 그리드 아이템이 배치되는 것을 볼 수 있다.

![CSS_Grid_27](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/e2c679b2-e070-4b37-9455-2f4d65d651bb)

다음은 `end`이다. end는 아래 이미지와 같이 column 축의 끝 지점을 기준으로 그리드 아이템이 배치되는 것을 볼 수 있다.

![CSS_Grid_28](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/d3fc69d3-a110-41a1-bf69-456c81fe6bea)

추가로 `place-items`라는 속성을 사용할 수 있는데 `align-items`와 `justify-items`를 같이 쓸 수 있는 `축약형` 속성이다. align-items, justify-items의 순서로 작성하고, 하나의 값만 쓰면 두 속성 모두에 적용된다.

```css
.container {
  border: 1px solid blue;
  display: grid;
  grid-template-columns: repeat(3, minmax(25%, auto));
  grid-template-rows: repeat(3, minmax(50px, auto));
  place-items: start end;
}
```

![CSS_Grid_29](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/156fd70f-0984-40dd-8c1b-70aa1a36925b)

<br>

### 2-9. 아이템 그룹 세로 정렬 align-content, 아이템 그룹 가로 정렬 justify-content

Grid 아이템들의 높이를 모두 합한 값이 Grid 컨테이너의 높이보다 작을 때 Grid 아이템들을 통째로 정렬한다. `align-content`은 세로(column축) 방향으로 그룹 정렬, justify-content은 가로(row축) 방향으로 그룹 정렬한다. 방향만 다를 뿐 동작 방식은 동일하기 때문에 `align-content`을 기준으로 테스트해보자.

기준이 되는 레이아웃은 아래와 같다.

```css
.container {
  border: 1px solid blue;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  height: 200px;
}
```

![CSS_Grid_30](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/a0d82f09-f42e-4d2e-a2d1-8ba7c9e01d91)

기본 값은 `align-content: stretch`이다. 다른 속성들도 적용시켜보자.

다음으로 `align-content: start`를 적용시켜보자. 우선 그리드 아이템이 줄어드는 것 같이 보이는 이유는 align-items에서 설명한 이유와 같다. 이 때 해당 그리드 아이템들의 높이 합이 컨테이너 높이보다 작기 때문에 그리드 아이템들이 통째로 컨테이너 시작점을 기준으로 정렬된다.

![CSS_Grid_31](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/63d8f5da-6cc5-43a0-826e-8c7b65fa1844)

다음으로 `align-content: center`를 적용시켜보자. start에서 설명한 이유와 마찬가지로 그리드 아이템들이 통째로 컨테이너 중간점을 기준으로 정렬된다.

![CSS_Grid_32](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/726e8c10-5e5c-4eeb-9270-338eaec066df)

다음으로 `align-content: end`를 적용시켜보자. start에서 설명한 이유와 마찬가지로 그리드 아이템들이 통째로 컨테이너 끝점 기준으로 정렬된다.

![CSS_Grid_33](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/2a6453f2-04c1-4c19-b8db-d793e3b2193e)

다음으로 `align-content: space-between`을 적용시켜보자. flex에서 사용하던 속성과 마찬가지로 그리드 아이템 `사이`에 균일한 간격을 두고 정렬한다.

![CSS_Grid_34](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/d3d70a17-446b-400d-9d4f-641b3b37cbb0)

다음으로 `align-content: space-around`을 적용시켜보자. flex에서 사용하던 속성과 마찬가지로 그리드 아이템 `둘레`에 균일한 간격을 두고 정렬한다.

![CSS_Grid_35](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/0574b818-c357-4ec0-9e2a-3ab2845b8a19)

다음으로 `align-content: space-evenly`을 적용시켜보자. flex에서 사용하던 속성과 마찬가지로 그리드 아이템 `사이와 양 끝`에 균일한 간격을 두고 정렬한다.

![CSS_Grid_36](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/688fdacc-f236-4c41-960d-e1ebcf9e7a06)

아래 이미지를 참고하면 이해하기 쉽다.

![CSS_Grid_37](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/4b4cd1bc-403b-4b9c-b918-7b5d3771b437)

추가로 `place-content`라는 속성을 사용할 수 있는데 `align-content`와 `justify-content`를 같이 쓸 수 있는 `축약형` 속성이다. align-content, justify-content의 순서로 작성하고, 하나의 값만 쓰면 두 속성 모두에 적용된다.

```css
.container {
  place-content: space-between center;
}
```

<br>

### 2-10. 개별 아이템 세로 정렬 align-self, 개별 아이템 가로 정렬 justify-self

그리드 아이템에 적용하는 속성으로 개별 아이템을 정렬할 수 있다. align-content와 justify-content와의 차이는 그리드 아이템 개별로 적용시킬 때 사용하는 속성이라는 것이다. 사용 방법은 동일하지만 개별로 동작하므로 `stretch`, `start`, `center`, `end` 속성만 존재한다.

```css
.container {
  border: 1px solid blue;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  height: 200px;
}

.container .item {
  border: 1px solid red;
}

.item:nth-child(2) {
  align-self: start;
}
```

위 코드와 같이 두번쨰 children에만 `align-self: start` 속성을 주었다. 결과는 아래 이미지와 같다.

![CSS_Grid_38](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/c0fd0d86-99a8-4afb-8387-32292accf58d)

추가로 `place-self`라는 속성을 사용할 수 있는데 `align-self`와 `justify-self`를 같이 쓸 수 있는 `축약형` 속성이다. align-self, justify-self의 순서로 작성하고, 하나의 값만 쓰면 두 속성 모두에 적용된다.

```css
.item {
  place-self: start center;
}
```

<br>

### 2-11. 배치 순서 order

시각적 나열 순서를 결정하는 속성이다. 숫자 값이 들어가며 작은 숫자일 수록 먼저 배치된다. 시각적으로 변경되는 것일 뿐 HTML 자체 구조를 바꾸는 것은 아니므로 접근성 측면에서 사용에 주의하여야한다. 시각 장애인분들이 사용하는 스크린 리더로 화면을 읽을 때 order를 이용해 순서를 바꾼 것은 의미가 없다는 것이다.

```css
.item:nth-child(1) {
  order: 3;
} /* A */
.item:nth-child(2) {
  order: 1;
} /* B */
.item:nth-child(3) {
  order: 2;
} /* C */
.item:nth-child(4) {
  order: 1;
} /* D */
```

![CSS_Grid_39](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/6c0132aa-5103-40c7-ae5e-59628606d1cd)

<br>

### 2-12. z-index

z-index로 Z축 정렬을 할 수 있다. 숫자가 클 수록 위로 올라온다. position에서의 z-index와 같은 개념이다.

```css
.item:nth-child(5) {
  z-index: 1;
  transform: scale(2);
  background-color: rgba(60, 76, 255, 0.5);
}
```

![CSS_Grid_40](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/8959e24f-9926-464c-a12e-4a4fb67963d0)

<br>
<br>

## 3. 참고 URL

- https://studiomeal.com/archives/533

<br>
