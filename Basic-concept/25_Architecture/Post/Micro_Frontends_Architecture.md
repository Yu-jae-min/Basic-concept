# [Architecture] Micro Frontends Architecture

2023년 09월 26일

<br>

# 1. Micro Frontends Architecture

마이크로 프론트엔드 아키텍처란 마이크로 서비스(MSA)의 개념을 프론트엔드 세계로 확장한 개념이다.
마이크로 서비스처럼 전체 화면을 작동할 수 있는 단위로 나누어 개발한 후 서로 조립하는 방식이다.

![Architecture_Micro_Frontends Architecture_01](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/559e6fe2-35bb-4ea1-acf8-3cdccb0d7b77)

![Architecture_Micro_Frontends Architecture_02](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/d1f69b75-8a83-451f-ba49-b5e6fc584366)

넓은 의미로, 하나의 웹앱의 배포 단위를 쪼개서 배포하는 방식을 가져간다면 Micro Frontends 아키텍처를 따른다고 이야기할 수도 있다.

웹앱으로 배포 단위를 쪼개는 것은 기존의 웹앱 프레임워크나 인프라를 통해 충분히 가능하다. 하나의 URL 호스트에 각 다른 basePath나 서브 도메인에 각각 분절된 웹앱을 태워서 배포하면 된다.

페이지의 묶음은 웹앱의 단위라고 할 수 있으니, 웹앱 단위로 배포 단위를 쪼개는 것은 모놀리식 앱을 처음으로 쪼개기 시작할 때 편리한 방식이다. 각 분절된 배포단위에 해당하는 페이지들이 서로를 몰라도 되고, 유저 네비게이션 경험에 악영향이 없다면 적정 수준의 엔지니어링이라고 생각한다.

하지만 다음과 같이 웹앱별 배포로 해결할 수 없는 문제가 있다.

![Architecture_Micro_Frontends Architecture_03](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/7e440356-e37a-47a3-b2fe-6dab0b3e331a)

먼저, 각 페이지에 공통적으로 들어가는 UI(네비게이션 바, 앱 헤더 등)가 존재하고, 이게 복잡해지면 운영에 고충이 생긴다. 만약 각 분절된 웹앱에서 빌드 타임에 통합되는 공통 UI에 문제가 있을 경우, 해당 UI가 존재하는 배포단위 전체를 꼼짝없이 모두 롤백해야 한다.

다음으로, 유저가 여러 페이지/앱을 넘나들 때 네비게이션 경험이 좋지 않을 수 있다.

유저 입장에서는 그저 앱 내부에서 다른 페이지로 이동하는 것이겠지만, 인프라단에서는 유저가 접속하는 앱이 바뀌기 때문에 앱 초기화, 앱에 필요한 자원을 다시 받는 동작이 일어난다.

물론 브라우저의 도움으로 페이지 네비게이션간 겹치는 DOM을 다시 재사용할 수는 있다. 하지만 초기화 과정에서 많은 번들 로딩과 API 요청이 일어나야 한다면 유저는 페이지 전환간 좀 더 기다리거나, 로딩 서클을 재차 볼 가능성이 높아진다.

만약 페이지간 UI가 거의 비슷할 정도로 공통 UI를 많이 포함하고 있다면 유저 입장에서는 거의 같은 UI가 다시 로딩되는 것이 더 어색할 것이다.

<br>
<br>

# 2. Micro Frontends의 적용 시점, 메인 컨셉, 장단점

## 2-1. 적용 시점

Micro Frontends는 웹앱 단위로 배포단위를 쪼개는 것으로 충분하지 않을 때 좋은 솔루션이 된다. “모든 웹앱에 적용하면 다 좋다!” 이건 당연히 아니다.

일반화하기는 힘들지만 Micro Frontends 아키텍처는

- 페이지마다 복잡한 공통 UI가 반복되어 포함되고
- 그런 와중에도 각 페이지들의 UI 유사성이 높고 크게 연관되어 있으며
- 여기에 더불어 분절된 각 앱의 크기가 이미 충분히 크고, 복잡도와 도메인 난이도가 높아 배포 단위를 더 잘게 쪼개고 싶은 요구사항이 있는

웹 애플리케이션에 적합하다고 보여진다.

이런 상황이라면 거대한 웹앱은 Micro Frontends 아키텍처로 전환했을 때 앞에서 설명했던 문제를 해결할 수 있다. 더불어 커다란 앱을 쪼갬으로 빌드/배포 사이클이 단축된다는 이점, 더 잘 나눠진 배포단위를 통해 협업에서의 이점까지 누릴 수 있게 된다.

<br>

## 2-2. 메인 컨셉

### 2-2-1. 기술 독립성

- 각 자동 단위들은 기술적으로 독립적일 수 있어야 한다.
- 각 작동 단위에 사용된 프론트엔드 기술(React, Vue, Vanilla JS 등)에 상관없이 조합이 가능해야 한다.

<br>

### 2-2-2. 컨텍스트 독립성

- 각 작동 단위들이 같은 프레임워크를 사용하더라도 컨텍스트를 공유해서는 안된다.
- 독립적인 애플리케이션을 자체적으로 구축해야하고 상태 공유나 전역 변수에 의존해서는 안된다.

<br>

### 2-2-3. 네임스페이스를 활용한 분리

- 각 작동 단위의 격리가 불가능한 경우 네이밍 컨벤션에 따라 prefix 등으로 네임스페이스를 활용한다.
- CSS, 로컬 스토리지, 이벤트, 쿠키에 네임스페이스를 부여하여 충돌을 방지하고 명확히 분리한다.

<br>

### 2-2-4. 통신 시스템에 기본 브라우저 기능 활용

- 작동 단위 간의 통신을 위한 시스템을 자체 구축하는 것보다 브라우저 이벤트를 사용한다.
- 만약 정말로 작동 단위 간 커스텀 API가 필요한 경우 가능한 간단하게 유지한다.

<br>

### 2-2-5. 탄력적인 웹 디자인 구축

- 자바스크립트에서 에러가 나거나 실행할 수 없더라도 기능은 사용 가능해야 한다.
- 범용 렌더링(Universal Rendering)과 점진적 향상(Progressive Enhancement)을 통해 성능을 향상시킬 수 있다.

<br>

## 2-3. 장단점

### 2-3-1. 장점

- 작고, 응집력 있고 유지보수에 용이한 코드베이스를 가질 수 있다. 따라서 디커플링이라는 소프트웨어 개발 목표를 달성한다.
- 각 마이크로 프론트엔드는 고유한 기술 및 프레임워크를 선택할 수 있다. 독립적으로 구현, 테스트, 업그레이드, 업데이트 및 배포할 수 있어 팀에 유연성을 제공한다.
- 프론트엔드 개발을 점진적 업그레이드 또는 재작성이 수월해진다.
- 마이크로 프론트엔드는 수직 팀을 장려한다. 수직 팀에는 일반적으로 기능 소유자, UX 디자이너, 제품 관리자, 백엔드 개발자, 프론트엔드 개발자 및 품질 보증 엔지니어가 포함된다.

<br>

### 2-3-2. 단점

- 마이크로 프론트엔드는 분리되거나 느슨하게 결합 된 구성 요소를 위해 설계되었다. 그들 사이에 너무 많은 종속성을 넣으려고하면 디버깅 악몽이 발생할 수 있다.
- 마이크로 프런트 엔드를 가능하게하는 파이프라인으로 인해 복잡도가 증가한다. 외부로드 문제를 해결하려면 기술적 전문 지식이 필요하며 디버깅 프로세스에는 시간이 많이 걸린다. 또한 SSO (Single Sign-On), 글로벌 CSS 등과 관련된 문제에 직면 할 수 있다.
- 각 마이크로 프런트 엔드에는 중복 된 코드 또는 기능이 있을 수 있다. 예를 들어, React 라이브러리는 각 마이크로 프런트 엔드에 포함될 수 있어, 번들 크기와 메모리 소비를 증가시킨다.
- 런타임 시 마이크로 프런트 엔드를 동적 또는 지연로드하는 데 추가 시간이 걸린다.
- 사용자 인터페이스는 여러 팀에서 설계되었으므로 UX 설계는 마이크로 프런트 엔드에서 일관되지 않을 수 있다.

<br>
<br>

# 3. Micro Frontends 통합 방법

![Architecture_Micro_Frontends Architecture_04](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/fc09d117-86e0-4ec5-a0bc-ca3f88e0c9ee)

마이크로 앱들을 개발 후, 어떻게 통합할지 고려해야 한다. 여러 방식이 있는데, 공통적으로 존재하는 아키텍처가 있다. 일반적으로 마이크로 애플리케이션들이 있고(작동 단위), 그것들을 구성하는 단일 컨테이너 애플리케이션이 있다. 단일 컨테이너 애플리케이션은 다음과 같은 것들을 한다.

- 공통 페이지 요소를 렌더링한다.
- 인증 및 탐색과 같은 공통적으로 고려되어야 하는 문제들을 해결한다.
- 다양한 마이크로 앱들을 페이지에 모으고, 각 앱들에게 언제 어디서 렌더링할지 알려준다.

<br>

## 3-1. 서버 사이드 템플릿 통합

각 서버로 html 템플릿을 요청하고, 최종 응답서버에서 각 템플릿을 조합해서 응답을 보낸다. 서버측에서 최종 화면을 조합한다. (SSR에 적용) 코드로 살펴보자.

아래와 같이 범용적인 페이지 요소들을 포함하는 index.html 파일을 만든다. 이 파일에는 HTML fragment 파일들이 서버사이드에서 포함되어진다(넣어진다).

```html
<html lang="en" dir="ltr">
  <head>
    <meta charset="utf-8" />
    <title>Feed me</title>
  </head>
  <body>
    <h1>Feed me</h1>
    <!--# include file="$PAGE.html" -->
  </body>
</html>
```

Nginx를 사용하여 아래 파일을 제공하고, 요청되는 URL이 $PAGE 변수에 대입되도록 구성한다.

```jsx
server {
	listen 8080;
	server_name localhost;

	root /usr/share/nginx/html;
	index index.html;
	ssi on;

	# Redirect / to /browse
	rewrite ^/$ http://localhost:8080/browse redirect;

	# Decide which HTML fragment to insert based on the URL
	location /browse {
		set $PAGE 'browse';
	}
	location /order {
		set $PAGE 'order';
	}
	location /profile {
		set $PAGE 'profile';
	}

	# All locations should render through index.html
	error_page 404 /index.html;
}
```

위와 같은 방식은 상당히 표준적인 서버측 구성 방식이다.

여기엔 어떻게 여러 개의 HTML 파일들이 웹 서버에 배치되는지는 나와있지 않지만, 각 파일들은 다른 페이지들을 고려하거나 다른 페이지들에게 영향을 미치지 않는다고 가정한다. 또한, 각각이 독립적인 배포 파이프라인을 가진다고 가정한다.

독립성을 높이기 위해, 각 마이크로 앱들을 렌더링하고 서비스하는 별도의 서버가 있을 수 있으며, 한 서버는 한 마이크로 앱에 요청을 한다. 또한 응답 캐싱을 통해 지연 시간에 영향을 주지 않고 작업을 수행하도록 할 수 있다.

![Architecture_Micro_Frontends Architecture_05](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/84e2ff6e-afeb-41dd-ac58-1ee59ba69758)

이걸 요즘 웹 개발 트랜드에 좀 더 맞게 말하면, 특정 페이지 단위의 앱을 가지고 있는 여러개의 Nextjs앱 서버를 배포해놓고, Route53이나 Cloud Front같은 인프라단에서 특정 앱에 해당되는 basePath로 요청이 들어왔을 때 해당 앱이 응답하는 HTML과 JS를 보내주어 웹앱을 그리는 방식이다.

결국, “웹앱 단위 이상으로 배포단위를 쪼개는 것” 과 같다.

이 방법과 관련있는 솔루션으로는 Nextjs의 multi-zones가 있다. Nextjs로 개발된 여러 웹앱을 묶어서 배포하기 용이하게 만드는 방법이다. [vercel은 multi-zones를 micro frontends 아키텍처를 구현할 수 있는 방법](https://vercel.com/templates/next.js/microfrontends)으로 제시하고 있지만, 위에서 말한 웹앱별 배포로 해결할 수 없는 문제는 해결하지 못한다.

<br>

## 3-2. 빌드타임 통합

분리된 UI(마이크로 프론트엔드)를 패키징해 패키지로 배포하고 빌드타임에 통합시키는 방법이다. 특정 UI의 한 부분을 NPM 패키지로 만들어 애플리케이션의 package.json에 의존성과 버전을 표기한 후 빌드해 배포하는 방법이다. 컨테이너 앱이 그것들을 라이브러리 종속성으로 포함하도록 한다.

```jsx
{
	"name": "@feed-me/container",
	"version": "1.0.0",
	"description": "A food delivery web app",
	"dependencies": {
		"@feed-me/browse-restaurants": "^1.2.3",
		"@feed-me/order-food": "^4.5.6",
		"@feed-me/user-profile": "^7.8.9"
	}
}
```

이 방식은 배포 가능한 단일 Javascript 번들을 생성한다. 그리고 다양한 공통 종속성을 제거할 수 있다. 또한 특정 UI의 한 부분을 패키지화하면 코드 분리 면에서는 이점이 있다. 각 조직별로 오너십을 세분화하기 편해진다.

하지만 결국 빌드타임에 코드가 통합된다는 한계 때문에 웹앱별 배포로 해결할 수 없는 문제는 해결되지 못한다. 특정 패키지를 번들링해서 미리 트랜스파일하고 빌드해놓는 데서 발생하는 이점으로 어느정도 빌드 및 배포 사이클을 빠르게 할 수 있는 장점도 있기는 하다.

또한 이 접근 방식은 각각의 마이크로 앱에 변경사항이 있을 때마다, 그 변경사항을 반영한 단일 번들을 만들기 위해 다시 컴파일하고 릴리즈해야 한다.

애플리케이션을 개별 코드베이스로 나누는 많은 문제들을 해결해놓고, 다시 릴리즈 단계에서 커플링하는 방식은 제외하자. 마이크로 프론트엔드를 빌드타임이 아닌 런타임에 통합하는 방법을 찾아야 한다.

<br>

## 3-3. iframe을 통한 런타임 통합

여기서부터는 확실히 페이지 단위 이하로 배포 단위를 분리할 수 있는 방법들이며 분절된 UI 컴포넌트를 런타임에 통합하는 방식이다.

이 방식은 전통적인 방식이면서 가장 쉬운 방식이다. iframe을 사용하면 각 마이크로 페이지들을 독립적인 하위 페이지로 쉽게 만들 수 있다. 특정 외부 URL로 배포해놓은 UI의 일부를 HTML째로 넣어 기존 앱에 쉽게 통합하여 배포 단위를 UI 단위로 분리할 수 있다. 또한 스타일과 글로벌 변수가 서로 간섭하지 않는다는 측면에서 상당한 수준의 고립성을 제공한다.

```html
<html>
  <head>
    <title>Feed me!</title>
  </head>
  <body>
    <h1>Welcome to Feed me!</h1>

    <iframe id="micro-frontend-container"></iframe>

    <script type="text/javascript">
      const microFrontendsByRoute = {
      	'/': 'https://browse.example.com/index.html',
      	'/order-food': 'https://order.example.com/index.html',
      	'/user-profile': 'https://profile.example.com/index.html',
      };

      const iframe = document.getElementById('micro-frontend-container);
      iframe.src = microFrontendsByRoute(window.location.pathname);
    </script>
  </body>
</html>
```

새로운 기술이 아니라서 흥미롭지 않을 수 있지만, 마이크로 프론트엔드의 이점을 상기해본다면, 애플리케이션 분할과 팀을 구조화하는 데에 신경쓴다면, 이 방식이 가장 적합하다.

Iframe 방식을 선택하는 것을 꺼리는 경우가 종종 있는데, 사실 그런 데에는 타당한 이유가 있다. 이 방식을 통한 분리는 쉽지만, 다른 옵션들보다 유연성이 떨어지는 경향이 있다.

이 방식은 어플리케이션의 서로 다른 부분들을 통합 구축하는 것이 어렵다. 따라서 라우팅, 히스토리, deep linking, 컴포넌트간 상태값 공유 등이 더욱 복잡해지고, 반응형 페이지 개발에도 추가적인 어려움들이 따른다.

또한 UX가 iframe안에 갇히기 때문에 어색한 UI 표현을 가질 수 있다.

<br>

## 3-4. Web Components를 통한 런타임 통합

비교적 최신 web 스펙인 web-components를 이용한 런타임 통합 방식도 있다. iframe처럼 보안 문제가 없으면서 분리된 HTML을 기존 앱에 쉽게 통합할 수 있다. web-components를 개발하는 방식이 기존 앱이 React와 같은 라이브러리의 컴포넌트를 개발하는 방식과 달라서, 기존 앱과는 살짝 다른 방식으로 개발되어야 할 수 있다. 물론 모든 앱이 Micro 앱이 될 필요가 없고, 소수의 특수한 앱만을 Micro App으로 따로 배포하고 싶은 것이라면 관리 이슈가 아주 크지는 않는다.

하지만 상태 공유는 여전히 쉽지 않을 수 있다. web-components는 커스텀한 HTML 태그의 형태를 가지고 있어서 속성 값을 통해서만 데이터를 공유받을 수 있기 때문이다.

이 방식은 자바스크립트를 통한 런타임 통합 방식에서 한 가지만 변형이 있는 방식이다. 각 마이크로 앱이 호출할 컨테이너의 전역 함수를 정의하여, 상위에서 하위 앱들의 전역 함수를 호출하는 방식이 아니다. 대신, 컨테이너 앱에서 인스턴스화 할 HTML Custom Element를 정의하는 방식이다.

```html
<html>
  <head>
    <title>Feed me!</title>
  </head>
  <body>
    <h1>Welcome to Feed me!</h1>

    <!-- 이 스크립트는 즉시 무언가를 렌더링 하지 않는다. -->
    <!-- 대신, window에 entry-point 함수를 추가한다. -->
    <script src="https://browse.example.com/bundle.js"></script>
    <script src="https://order.example.com/bundle.js"></script>
    <script src="https://profile.example.com/bundle.js"></script>

    <iframe id="micro-frontend-root"></iframe>

    <script type="text/javascript">
      // 이 전역 함수들은 위의 script들에서 window에 추가된 것들이다.
      const microComponentsByRoute = {
        "/": "micro-fronted-browse-restaurants",
        "/order-food": "micro-frontend-order-food",
        "/user-profile": "micro-fronted-user-profile",
      };

      const webComponentType = microComponentsByRoute(window.location.pathname);

      /* 적합한 웹 컴포넌트를 coustom element 타입을 선언한 후 인스턴스를 생성하여 document에 추가한다. */
      const root = document.getElementById("micro-frontend-root");
      const webComponent = document.createElement(webComponentType);
      root.appendChild(webComponent);
    </script>
  </body>
</html>
```

최종 결과는 이전 방식과 매우 유사하다. 주요 차이점은 '웹 컴포넌트 방식'을 선택한다는 것이다. 웹 컴포넌트 스펙을 좋아하고, 브라우저가 제공하는 기능을 사용하는 것을 좋아한다면 이 옵션이 적합하다. 컨테이너 앱과 마이크로 앱들 사이에 고유한 인터페이스를 정의하여 사용하려면, Javascript를 통한 런타임 통합 방식이 적합하다.

이 방법에 해당하는 다른 솔루션으로는, SAP에서 만든 오픈소스 Micro Frontends 도구인 [luigi](https://docs.luigi-project.io/docs/getting-started)가 있다. HTML을 단위로 분절된 웹앱을 개발하고, 이를 설정값을 작성하여 통합하는 방식이다. iframe과 web-components의 형태 둘 다 지원하고 있다. [React를 사용하는 예제](https://github.com/SAP/luigi/tree/main/core/examples/luigi-example-react/public)도 있으니 한번 살펴보시면 좋을 것 같다.

iframe과 웹 컴포넌트를 통한 런타임 통합 방식의 경우, 이미 그것으로 완결되어 런타임에서 다른 컴포넌트와 상호작용할 필요가 없는 소수의 UI 컴포넌트들을 런타임에 통합하는데 사용하기 좋은 방식이다. 가령 포탈 메인 페이지에서 iframe으로 분리된 이런 각각의 탭들은 다른 UI 컴포넌트들의 상태를 알지 못해도 괜찮다.

![Architecture_Micro_Frontends Architecture_06](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/a97eee9c-1385-4fcd-a08a-1e63d123b8c2)

다수의 분리된 다른 UI 컴포넌트가 iframe이나 web-components로 런타임에 통합되는 경우, 여러 UI 컴포넌트가 공유하는 상태를 독립된 배포 단위로 넘기기 위한 브릿지 성격의 구현체에 더 의존하게 된다. 기존의 UI 컴포넌트와 약간 거리가 있는 곳에서 상태값들을 저장하고, 이를 기존 UI 컴포넌트들의 라이프사이클에 연동시켜야하기 때문에 복잡해질수록 관리가 어려워질 가능성이 높다.

![Architecture_Micro_Frontends Architecture_07](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/3b8747db-445b-4018-a894-2713ee96ddd2)

이런 지점들을 신경쓰지 않을 방법은 없을까? 웹앱이 React로 개발되고 있다고 생각해본다면, 배포 단위를 분리하되 공유하는 상태값들의 관리를 그냥 상위 컴포넌트에서 자연스럽게 해볼 수는 없을까? 정의한 컴포넌트들을 그냥 툭 떼서 별도의 배포단위로 만들고 런타임에서 합치게 할수는 없을까?

<br>

## 3-5. Javascript를 통한 런타임 통합

방법이 있다. 바로 UI 컴포넌트를 자바스크립트 번들 단위로 배포 단위를 나누고, 필요할 때 번들을 로딩하여 런타임에 통합시키는 방식이다. React를 사용한다고 가정한다면 이 방법에서는 “정의한 컴포넌트들을 그냥 툭 떼서 별도의 배포단위로 만들고 런타임에서 합치는 것” 이 가능하다. 해당 컴포넌트부터 런타임에 만들 수 있는 독립된 번들로 만드는 것이다.

![Architecture_Micro_Frontends Architecture_08](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/bc41c3cd-ba4b-45d9-ba65-773860f5a065)

당연히 배포 단위별 공유되는 상태의 관리는 React에서 제공하는 API들을 통해 앱 안에서 자연스럽게 가능하다. 미리 로딩된 앱이 가져온 CSS와 같은 자원들도 바로 사용할 수 있다.

이 방법이 주는 가장 큰 장점은 배포 단위를 유연하게 가져갈 수 있게 한다는 것이다. 배포 단위간 상태 공유를 위한 작업이 앞선 두 런타임 통합 방법보다 많거나 이질적이지 않고, 모두 웹 앱 내부에서 가능하니 기존 배포 단위를 합치거나 나누는 것이 비교적 간편하다.

[webpack 5가 제공하는 Module Federation Plugin](https://webpack.kr/plugins/module-federation-plugin/)이 이 방식에 해당하는 솔루션이다. 해당 플러그인은 분리된 배포 단위의 웹앱이 모이는 일명 host, 각각 분리된 배포 단위인 remote 앱을 정의하고 런타임에 합칠 수 있는 빌드 옵션을 제공한다.

![Architecture_Micro_Frontends Architecture_09](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/6c490fb6-d51f-490a-8974-f8fffe31ad90)

Module Federation Plugin을 사용하면 거대한 웹 앱을 따로 개발해 빌드/배포하는 것으로 MSA의 장점을 가져가고, 런타임에서는 모놀리식처럼 통합되어 통합의 자연스러움과 상태 관리의 이점을 얻을 수 있다.

솔루션을 사용하지 않고 구현하는 방법은 아래와 같다. 각 마이크로 앱들은 `<script>` 태그를 통해 페이지에 포함된다. 컨테이너 애플리케이션에서는 마이크로 앱 번들을 `<script>` 태그를 통합 다운로드 받고, 약속된 초기화 메소드를 호출한다. 컨테이너 앱에서는 mount 되어야 할 마이크로 앱을 결정하고, 마이크로 앱들에게 언제 어디에 렌더링할지 알려주기 위한 함수를 호출한다.

```html
<html>
  <head>
    <title>Feed me!</title>
  </head>
  <body>
    <h1>Welcome to Feed me!</h1>

    <!-- 이 스크립트는 즉시 무언가를 렌더링 하지 않는다. -->
    <!-- 대신, window에 entry-point 함수를 추가한다. -->
    <script src="https://browse.example.com/bundle.js"></script>
    <script src="https://order.example.com/bundle.js"></script>
    <script src="https://profile.example.com/bundle.js"></script>

    <iframe id="micro-frontend-root"></iframe>

    <script type="text/javascript">
      // 이 전역 함수들은 위의 script들에서 window에 추가된 것들이다.
      const microFrontendsByRoute = {
        "/": window.renderBrowseRestaurants,
        "/order-food": window.renderOrderFood,
        "/user-profile": window.renderUserProfile,
      };

      const renderFunction = microFrontendsByRoute(window.location.pathname);

      /* entry-point 함수를 선언한 후, 그것들을 호출한다. 엘리먼트의 id를 넘겨서 어디에 렌더링할지를 알려준다. */
      renderFunction("micro-frontend-root");
    </script>
  </body>
</html>
```

위 예시는 굉장히 기초적인 예시지만, 그래도 기본적인 기술을 보여준다.

빌드타임 통합과는 달리, 각 번들.js 파일들을 독립적으로 배치할 수 있고, iframe 통합과는 달리, 원하는대로 마이크로 앱들 간의 통합이 가능하도록 유연성을 제공한다. 필요한 경우에만 번들을 다운로드하거나, 마이크로 앱이 렌더링될 때 데이터를 주고받는 등 다양한 방법으로 코드를 확장할 수 있기 때문이다.

이처럼, 이 접근 방식은 유연성과 독립적 구현 가능성이 결합되어 자주 채택된다. (Full Examples : https://martinfowler.com/articles/micro-frontends.html#TheExampleInDetail)

<br>
<br>

# 4. Micro Frontends 통합 고려사항

## 4-1. 공통 고려사항

### 4-1-1. 스타일링

- BEM과 같은 엄격한 네이밍 규칙 사용
- SASS와 같은 전처리기를 통해 상위 선택자 추가 등을 통해 독립성 유지
- 모든 스타일을 CSS-in-JS 방식으로 처리
- Shadow DOM: 메인 document DOM 으로부터 독립적으로 렌더링 되는 캡슐화된 Shadow DOM 트리를 엘리먼트에 추가하고, 연관된 기능을 제어하기 위한 JavaScript API 의 집합. 이 방법으로 엘리먼트의 기능을 프라이빗하게 유지할 수 있어, 다큐먼트의 다른 부분과의 충돌에 대한 걱정 없이 스크립트와 스타일을 작성할 수 있다.

<br>

### 4-1-2. Component Library 공유

- 마이크로 앱들 간의 시각적 일관성을 유지하기 위해 재사용 가능한 UI 컴포넌트 라이브러리를 개발하여 공유한다. 코드 재사용성과 시각적 일관성을 유지할 수 있다.
- 너무 일찍 만드는 것은 좋지 않다. 실제로 사용하기 전에 컴포넌트의 API가 무엇이어야 하는지 추측하기는 쉽지 않다. 그러므로 많은 변동이 발생하게 되므로, 초기에는 일부 중복이 발생하더라도 각 팀이(각 마이크로 앱 내에서) 코드베이스에서 필요에 따라 자체 컴포넌트를 만들어두는 것이 좋다. 패턴이 자연스럽게 나타나도록 허용하고, 컴포넌트의 API가 명확해지면 그 때 만드는 것을 권장한다.

<br>

### 4-1-3. 애플리케이션 간 커뮤니케이션

- 가능한 적은 소통을 하는 것이 좋다.
- Custom events를 사용하면 마이크로 앱들이 간접적으로 통신할 수 있다. 이는 직접 결합을 최소화하는 좋은 방법이지만, 마이크로 앱들 간 약속을 정하고 구현해야 하므로 더 어려울 수 있다.
- 콜백과 데이터를 아래쪽으로 전달하는 React 모델로 약속을 명확하게 정하는 것도 좋은 솔루션이다.
- URL 표시 줄을 통신 메커니즘으로 사용하는 것도 좋은 방법이다.
- 어떤 방식을 선택하든, 서로 메시지 또는 이벤트를 전송하여 통신하는 것이 좋으며, 공유 상태를 갖는 것은 좋은 선택지가 아니다. 마이크로 서비스에서 데이터베이스를 공유하는 것이 좋지 않은 것처럼, 데이터 구조와 도메인 모델을 공유하자마자 엄청난 양의 결합이 생기게 되고, 변경에 많은 제약이 따르기 때문이다.
- vuex는 일반적으로 하나의 응용 프로그램에 대해 단일 전역 공유 저장소를 기본으로 한다. 그러나 각 마이크로 앱들이 자체 저장소를 갖는 것이 더 합리적이다.

<br>

### 4-1-4. 백엔드 통신

- BFF(Backend for Frontend Pattern) 패턴으로 프론트앤드 전용 API를 갖는다. 각 마이크로 앱들은 해당 프론트 엔드의 요구사항만 충족하는 목적을 가진 백엔드만을 가진다.
- 별도의 데이터베이스를 가질 수도 있다.
- 로그인 인증 정보는 통합하는 Container가 소유한다. 초기화 시 인증을 통해 얻은 토큰을 각 마이크로 프론트엔드에 주입되며, 마이크로 프론트엔드는 서버에 대한 요청과 함께 토큰을 보내고, 해당 마이크로 앱의 백엔드에서는 필요한 모든 유효성 검사를 수행하는 방식으로 구성할 수 있다.

  ![Architecture_Micro_Frontends Architecture_10](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/b1174311-24ae-4de1-b120-3718184b2c55)

<br>

## 4-2. **런타임 통합 방식 고려사항 (**Javascript를 통한 런타임 통합 기준)

### 4-2-1. **런타임 통합의 위험성을 완화해야 한다.**

런타임에 마이크로앱으로 분리된 UI 컴포넌트를 합쳐서 웹앱을 제공한다는 컨셉은 빌드 타임에 컴포넌트를 합쳐서 배포 나간다는 컨셉보다 더 위험하다. 배포를 해봐야만 확인할 수 있는 에러를 맞닥뜨릴 수 있기 때문이다.

![Architecture_Micro_Frontends Architecture_11](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/3af0c7fe-b315-43f2-bd6b-2ad2e3059d61)

Host-Remote 관계의 두 앱에서, Host에서 Remote로 특정 상태값을 공유하고 있다고 생각해보자. React의 예를 들어보면 Host에 Context API의 Provider가 존재하고, Remote에는 consumer가 존재하는 것이다.

Host에서 공유하는 상태값의 필드가 바뀌어 배포가 나갔을 때, 하위 배포 단위인 remote에는 리스크가 될 수 밖에 없다. 참조가 잘못되어 객체 속성값이 `undefined`로 나올 수도 있다.

따라서 이런 경우를 유발할 수 있는 코드를 최대한 줄여야 한다. 각 배포단위간 의존하는 상태가 바뀌었을 때 확실하게 배포가 나가야될 배포 단위가 구분되어야 하고, 공유하는 상태를 최대한 줄이는 것이 안정성을 확보할 수 있는 방법이다.

또한 분리된 배포단위 번들의 동적 로드(Dynamic Import)를 적극적으로 사용하게 되니 네트워크 의존도도 높아진다. 에러 처리가 확실하게 되어야 한다. 번들을 불러오지 못했거나, 불러온 번들에서 에러가 났을때 앱 전체의 장애로 전파되지 않도록 해야한다.

개발 과정에서 여러 배포단위들을 localhost의 여러 port에 띄울 수 있게 제공하는 등, 런타임 에러를 최대한 잡을 수 있는 개발 환경을 제공하는 것도 필요한 일이다.

<br>

### 4-2-2. **하나의 Micro 앱은 기존의 UI 컴포넌트보다 무거워질 수 있다.**

이러한 런타임 통합의 위험성을 완화하기 위해 배포 단위간 공유하는 상태값을 없애야 할 수 있다.

모놀리식 앱에서 상위에서 받아 공유하고 있었던 특정 UI 컴포넌트가 사용하는 데이터, 자원, 상태값들을 개별적으로 가지게 해야 할 수 있다. 이러면 하나의 UI 컴포넌트가 가지는 상태값과 번들의 크기가 기존보다 커진다. 중복된 API 요청이 더 발생할 수도 있다.

![Architecture_Micro_Frontends Architecture_12](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/8bb18d72-8502-492f-9242-8f71edde9ede)

기존에 앱을 개발하는 방식이나, 최적화 관점, DRY 원칙에 기대 생각하면 이러한 조치는 일반적이지 않다. 하지만 공유하는 데이터 때문에 배포 이후 런타임에서 앱이 깨지는 것보단 낫다.

정말 꼭 필요한 데이터만 공유하고, 전체 앱에서 형상을 엄격히 하나로 유지할 필요가 없는 상태값들은 적당히 쪼개진 마이크로앱들로 도로 집어 넣어 분리된 배포단위 사이 경계를 뚜렷이 하면, 각 마이크로앱 사이에 더욱 독립적인 배포가 가능해질 것이다.

<br>

### 4-2-3. **마이크로앱이 가져오는 복잡성을 통제해야 한다.**

javascript 런타임 통합을 사용한다면 그냥 자바스크립트 모듈로 UI 컴포넌트를 배포 단위로 뜯기 때문에 이론적으로는 배포 단위를 무한으로 만들어낼 수도 있다.

그렇지만 배포 단위가 많아지면 당연히 관리가 힘들고 배포하는데도 품이 많이 들 것이다. 분리된 배포 단위를 참조하는 코드를 작성하는 과정에서 의존성이 꼬일수도 있고, 많은 앱을 동적으로 로드해야 하기 때문에 성능에도 문제가 생길 수 있다.

webpack 5 Module Federation Plugin은 [전방위적(Omnidirectional)인 배포 단위 생성](https://webpack.js.org/concepts/module-federation/#uncaught-error-shared-module-is-not-available-for-eager-consumption)이 가능하다.

무슨 말이냐면 Host가 Remote를 가질 수 있고 Remote는 다시 또다른 Host로써 다른 Remote를 가질 수 있고 기존의 Host의 역할을 하는 Remote가 또 다른 Host를 Remote로 가질 수도 있다. 이런게 되긴 하는데, 이런 식으로 마이크로 앱을 운용하면 개인적으로는 큰일날 것 같다. [심지어 두 마이크로앱이 서로의 Host와 Remote가 동시에 되는 것](https://youtu.be/njXeMeAu4Sg?t=1064)도 된다.

따라서 배포 단위가 쉽게 늘거나 의존성이 복잡해지지 않도록 Module Federation plugin의 설정값을 어느정도 강제할 수 있게 규칙을 정하고, 특정 부분은 수정할 수 없게 한 번 래핑해서 쓸 수 있게 하면 좋을 것 같다.

또한 모노레포를 사용하고 있다면, 특정 내부 패키지의 사용처가 각 배포 단위 사이에서 명확해야 한다. 의존성이 너무 꼬여서 특정 패키지가 바뀔 때 배포할 앱들의 추적이 힘들고 결국 모든 앱이 배포되어야 한다면, Micro Frontends로 만드려고 했던 마이크로 앱간 확실한 경계 확립이 힘들다.

<br>
<br>

# 5. 통합 테스팅

모놀리틱과 마이크로 방식은 테스팅에서 모두 동일하지만 한 가지 명확한 차이는, 다양한 마이크로 프론트엔드와 컨테이너 애플리케이션의 통합 테스트이다. 이 작업은 기능 테스트나 e2e 테스트 도구(selenium, cypress 등)를 사용하여 수행할 수 있으나, 그렇게 멀리 갈 것 까진 없다.

통합 기능 테스트는 low level에서 다룰 수 없는 테스트만 다루면 된다. low level 에서는 비지니스 로직, 렌더링 로직 정도를 커버하는 수준의 단위 테스트를 수행하고, 통합 기능 테스트에서는 각 페이지들이 잘 조합되었는지만 확인하면 된다. 예를 들면, 특정 URL 에 완전히 통합된 애플리케이션이 로드되었는지 확인하기 위해, 마이크로 프론트엔드의 하드코딩 된 특정 텍스트가 페이지에 존재하는지를 assert 하는 것이 될 수 있다.

<br>
<br>

# #. 참고 URL

- https://blog.wanzargen.me/38
- https://maxkim-j.github.io/posts/runtime-integration-micro-frontends/
- https://martinfowler.com/articles/micro-frontends.html
- https://docs.luigi-project.io/docs/getting-started
- https://github.com/SAP/luigi/tree/main/core/examples/luigi-example-react/public
- https://webpack.kr/plugins/module-federation-plugin/

<br>
