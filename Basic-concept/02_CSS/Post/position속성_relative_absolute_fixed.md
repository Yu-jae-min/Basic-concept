## position 속성

position 속성은 HTML요소가 위치를 결정하는 방식을 설정한다.
아래와 같은 4가지 방식으로 지정할 수 있다.

> 1. 정적 위치(static position) 지정 방식
> 2. 상대 위치(relative position) 지정 방식
> 3. 고정 위치(fixed position) 지정 방식
> 4. 절대 위치(absolute position) 지정 방식

<br>

## 정적 위치(static position) 지정 방식

HTML 요소의 위치를 결정하는 가장 기본적인 방식은 정적 위치(static position) 지정 방식이다. position 속성의 defalut 값이며 웹 페이지의 흐름대로 요소를 배치한다.

```css
.wrap div:nth-child(3) {
  position: static;
}
```

<img src="https://github.com/Yu-jae-min/Basic-concept/assets/85284246/b7f60498-9ef3-4326-bb08-5d58134457e0" width="80%"/>

<br>

## 상대 위치(relative position) 지정 방식

요소 자신의 위치를 기준으로 요소를 이동시킨다.

```css
.wrap div:nth-child(3) {
  position: relative;
  top: 30px;
  left: 30px;
}
```

<img src="https://github.com/Yu-jae-min/Basic-concept/assets/85284246/5005c4d9-ab8f-4520-8f04-3add57bc9369" width="80%"/>

<br>

## 고정 위치(fixed position) 지정 방식

뷰포트를 기준으로 요소의 위치를 고정시킨다.

```css
.wrap div:nth-child(3) {
  background-color: green;
  position: fixed;
  top: 30px;
  left: 30px;
}
```

<img src="https://github.com/Yu-jae-min/Basic-concept/assets/85284246/0fb6fff8-39c2-4055-9215-c9bd83e364f5" width="80%"/>

<br>

## 절대 위치(absolute position) 지정 방식

부모 요소의 위치를 기준으로 요소를 이동시킨다.
이 때, 부모 요소에는 relative 속성이 추가되어야 한다.

```css
.wrap {
  position: relative;
}

.wrap div:nth-child(3) {
  position: absolute;
  top: 30px;
  left: 30px;
}
```

<img src="https://github.com/Yu-jae-min/Basic-concept/assets/85284246/9646d648-dbf2-4011-acc6-a2c9ff822a4b" width="80%"/>
