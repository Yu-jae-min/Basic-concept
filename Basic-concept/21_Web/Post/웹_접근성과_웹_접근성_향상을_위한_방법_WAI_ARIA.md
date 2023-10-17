# [Web] 웹 접근성과 웹 접근성 향상을 위한 방법 WAI-ARIA

2023년 10월 17일

<br>

# 1. 웹 접근성이란?

`웹 접근성`이란 장애인, 고령자 등이 웹 사이트에서 제공하는 정보에 비장애인과 동등하게 접근하고 이해할 수 있도록 보장하는 것이다. 시각, 운동성, 청각, 발작, 인지 등을 고려해야한다. 웹 접근성에 도움을 주는 기능으로는 스크린 리더, 화면 확대 도구, 음성 인식, 키보드 오버레이 등이 있다.

<br>
<br>

# 2. WAI-ARIA란?

`WAI-ARIA(Web Accessibility Initiative's Accessible Rich Internet Applications)`는 W3C에서 정의한 기술로 웹 접근성을 향상을 의해 브라우저의 스크린 리더와 같은 보조 기술이 정보를 인식하고 사용자에게 무슨 일이 일어나고 있는지 알려주는 데 사용할 수 있는 추가 시맨틱 정보를 추가해주기 위한 기술이다. 대표적인 기술로는 role, aria-label 속성 등이 있다. 이러한 속성 등을 활용하여 스크린 리더가 해당 태그의 역할과 상태 등을 읽어낼 수 있다.

<br>

## 2-1. role

`role`은 태그의 역할을 알려주는 속성(attribute)이다. role에 들어가는 값은 우리 마음대로 정하는 게 아닌 정해진 값을 사용해야 한다. tab, banner 등이 있고 MDN(https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/ARIA_Techniques)에서 확인해볼 수 있다. 또한 시맨틱 태그에는 왠만하면 해당 속성을 사용하지 않는 것이 좋다. 만약 사용하게 되면 스크린 리더는 시맨틱 태그를 무시하고 role을 읽게 된다.

<br>

## 2-2. aria-label

`aria-label`은 role의 banner나 tab처럼 값이 정해져 있는 게 아닌, 브라우저가 스크린 리더 사용자에게 전달해야 할 내용을 상황에 따라 적어야 한다. 예를 들면 “상세 페이지로 이동” 등이 될 수 있다. 또한 role과 함께 사용하여 스크린 리더가 사용자에게 role을 통해 해당 태그의 역할을 전달하고 aria-label을 통해 상태를 전달할 수 있다.

```html
<div>
  <a href="#" aria-label="펼치기" role="button"
    ><i class="ico ico-arrow"></i
  ></a>
</div>
```

하지만 aria-label과 같이 써도 되는 태그가 있고 아닌 태그가 있다. 시멘틱 태그이거나, role 속성 값이 상호작용(interactive)을 하는 값일 때 aria-label을 붙일 수 있다 :

- a (href 속성이 있을 때)
- button
- header
- footer
- nav
- main
- form
- iframe
- img
- role="navigation"
- role="button"

…

시멘틱 태그가 아닌 의미 없는 태그에는 role이 붙어있지 않은 이상 aria-label을 마음대로 붙이면 안 된다 :

- div
- span
- p
- li

…

```html
<div aria-label="펼치기"><i class="ico ico-arrow"></i></div>
// x
<div role="button" aria-label="펼치기"><i class="ico ico-arrow"></i></div>
//o
```

<br>

## 2-3. aria-labelledby

`aria-label`이 이름표를 붙여주는 것이라면, aria-labelledby는 쉽게 말해 그룹으로 묶어주는 속성이다.

```html
<h2 id="today-todo">오늘 할 일</h2>
<ul aria-labelledby="today-todo">
  <li>자바스크립트 공부</li>
  <li>html/css 과제</li>
  <li>알고리즘 문제풀이</li>
</ul>
```

<br>
<br>

# 3. 결론

위에서 적용시킨 속성 외에도 웹 접근성을 지키기 위한 방법은 더 다양한 방법들이 있다. 예를 들어 위와 같은 속성을 적용시켰을 때는 항시 키보드의 탭과 엔터를 통한 접근이 가능하도록 해야하며 문법 준수, 예측 가능성, 콘텐츠의 논리성 등 다양한 측면에서 웹 접근성을 향상시킬 수 있다. 구글링을 통해 웹접근성 체크리스트와 같은 키워드로 검색하기만 해도 다양한 정보를 얻을 수 있으니 추후 더 많은 내용들에 대해 조사해보아야겠다.

<br>
<br>

# # 참고 URL

- 웹 접근성 체크 리스트 : http://210.116.77.11/pbGuide/guide/html/wah/wahChecklst.html
- Why, How, and When to Use Semantic HTML and ARIA : https://css-tricks.com/why-how-and-when-to-use-semantic-html-and-aria/
- MDN aria-label : https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Attributes/aria-label
- MDN aria-describedby : https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Attributes/aria-describedby
- MDN aria-labelledby : https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Attributes/aria-labelledby
