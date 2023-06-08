## display 속성

display 속성은 값에 따라 요소가 사용자에게 보여지는 방식을 설정한다.
display 속성 값의 종류는 아래와 같다.

> - none
> - block
> - inline
> - inline-block

<br>

## none

해당 속성이 들어간 요소를 완전히 삭제된 것 처럼 보이게 한다.
visibility : hidden과는 다르게 영역을 차지하지 않는다.

<br>

## block

width가 100%를 차지하는 요소이다.
또한 width와 height를 사용자 임의로 지정할 수 있다.
대표적인 블록요소의 종류는 아래와 같다.

> address, article, aside, audio, blockquote, canvas, dd, div, dl, fieldset, figcaption, figure, footer, form, h1, h2, h3, h4, h5, h6, header, hgroup, hr, noscript, ol, output, p, pre, section, table, ul, video...

<br>

## inline

인라인요소는 속성 이름에서 알 수 있듯이 다른 인라인요소와 함께 위치할 수 있다.
또한 블록 요소와는 다르게 컨텐츠가 시작되는 부분부터 끝나는 부분까지를 넓이로 가진다.
그렇기 때문에 width와 height를 사용자 임의로 지정할 수 없다.
또한 line-height로 줄의 높낮이를 조절할 수 있고 text-align를 통해 텍스트의 위치를 지정할 수 있다.
대표적인 인라인요소의 종류는 아래와 같다.

> a, abbr, acronym, b, bdo, big, br, button, cite, code, dfn, em, i, img, input, kbd, label, map, object, q, samp, small, script, select, span, strong, sub, sup, textarea, tt, var

<br>

## inline-block

인라인 블록요소는 인라인요소의 특징과 블록요소의 특징 모두를 가진다.
블록요소처럼 width와 height를 설정할 수 있으며 인라인요소처럼 다른 요소와 같은 라인에 배치가 가능하다.

<br>

---

<br>

참고자료

1. <a href="https://ux.stories.pe.kr/44" target='_blank'>HTML5 태그의 블록 요소와 인라인 요소</a>
2. <a href="http://triki.net/css-display-block-inline-inline-block" target='_blank'>display 속성 값 block, inline, inline-block 개념 비교 정리</a>
3. <a href="https://www.daleseo.com/css-display-inline-block/" target='_blank'>display 속성: inline, block, inline-block</a>
