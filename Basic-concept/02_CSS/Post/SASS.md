## SASS (Syntactically Awesome Style Sheets)

SASS는 CSS전처리기이다. 개발자들이 CSS를 편하게 작성하기 위해서 사용한다.
SASS로 편하게 작성한 후 그것이 브라우저가 읽을 수 있도록 CSS로 컴파일된다.
확장자는 ".scss"를 사용한다.

> 주의! SPA 라우터 적용시 CSS가 엮일 수 있다.

<br>

## SASS 특징

### 1. 변수(Variables)

$를 사용하여 변수 설정이 가능하다.

```scss
$font-stack: Helvetica, sans-serif;
$primary-color: #333;

body {
  font: 100% $font-stack;
  color: $primary-color;
}
```

<br />

### 2. 네스팅(Nesting)

들여쓰기를 통해 태그의 자식-부모 관계를 더욱 명확하게 구분할 수 있다.

```scss
nav {
  ul {
    margin: 0;
    padding: 0;
    list-style: none;
  }

  li {
    display: inline-block;
  }

  a {
    display: block;
    padding: 6px 12px;
    text-decoration: none;
  }
}
```

<br />

### 3. 모듈(Modules)과 부분(Partials)

파일명 앞에 \_(언더바)가 붙은 것들이 있다. 이 파일들은 다른 주인 파일의 일부분이라는 뜻이다. 이 파일은 import전용으로 사용된다.

```scss
// _base.scss (styles.scss과 다른 파일로 나누어져있는 경우이다.)
$font-stack: Helvetica, sans-serif;
$primary-color: #333;

body {
  font: 100% $font-stack;
  color: $primary-color;
}

// styles.scss
@use "base";

.inverse {
  background-color: base.$primary-color;
  color: white;
}
```

<br />

### 4. 셀렉터(Selector)

들여쓰기 블록으로 묶여있는 스타일에 &를 넣으면 부모를 가리킨다.

```scss
.wrap {
  div {
    &:first-child {
      border: 1px solid #333;
    }
  }

  .box1 {
    &:hover {
      text-decoration: underline;
      color: #fff000;
    }

    // .box1_inner
    &_inner {
      position: relative;
    }
  }

  :not(&) {
    display: none;
  }
}
```

<br />

### 5. 믹스인(Mixins)

스타일을 끼워넣는다. 함수형태이며 파라미터를 사용할 수 있다. 인자를 넣지 않은 경우 익스텐드처럼 사용할 수 있다. 또한 여러개의 파라미터를 부여하여 각각 제어할 수 있다.

```scss
@mixin theme($theme: DarkGray) {
  background: $theme;
  box-shadow: 0 0 1px rgba($theme, .25);
  color: #fff;
}

@mixin fontstyle($size, $color) {
  font-size : $theme
  color : $color
}

.info {
  @include theme;
}
.alert {
  @include theme($theme: DarkRed);
}
.success {
  @include theme($theme: DarkGreen);
}

.full {
  @include fontstyle(14px, red);
}
```

<br />

### 6. 익스텐드(Extend)

스타일을 상속시킨다. 자주쓰는 스타일을 저장해두고 사용할 수 있다.

```scss
%message-shared {
  border: 1px solid #ccc;
  padding: 10px;
  color: #333;
}

%equal-heights {
  display: flex;
  flex-wrap: wrap;
}

.message {
  @extend %message-shared;
}

.success {
  @extend %message-shared;
  border-color: green;
}

.error {
  @extend %message-shared;
  border-color: red;
}

.warning {
  @extend %message-shared;
  border-color: yellow;
}
```

> **믹스인(Mixins)과 익스텐드(Extend) 무엇이 다를까?**
> 믹스인(Mixins)과 익스텐드(Extend)는 비슷하지만 CSS로 컴파일해보면 차이를 알 수 있다. 믹스인의 경우 스타일이 그대로 담겨지는 반면 익스텐드는 스타일이 들어가는 태그들을 묶어 지정하게 된다. 이런 경우 CSS에 순서가 뒤엉켜 문제를 야기할 수 있다고 한다.

<br>

---

<br>

참고자료

1. <a href="https://sass-lang.com/guide/" target='_blank'>SASS 공식문서</a>
2. <a href="https://mytory.net/2016/12/23/when-to-use-extend-when-to-use-a-mixin.html" target='_blank'>SASS에서 웬만하면 Extend 말고 Mixins을 사용하자</a>
