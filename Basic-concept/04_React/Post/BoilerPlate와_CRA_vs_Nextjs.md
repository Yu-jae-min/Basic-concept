# [react] Boiler Plate와 CRA vs Next.js

## # 보일러 플레이트(Boiler Plate)

<strong>보일러 플레이트(Boiler Plate)</strong>는 동작을 위해 반드시 포함되어야 하는 필수 내용이 포함된 코드 를 말한다. 일반적으로 수정되지 않아도 동작하는 코드이며, 필요에 따라 이 코드를 바탕으로 수정하여 사용하게 되는 기본 틀을 일컫는다.

>

- 변경이 거의 또는 전혀 없이 많은 곳에 포함되어야 하는 코드 섹션
- 최소한의 변경으로 여러 곳에서 재사용되는 것

<br>

## # CRA(eject X) vs CRA(eject O) vs Next.js

### - CRA(eject X)

CRA에서 eject를 하지 않고 사용하는 방법으로 React를 이용하여 프로젝트를 만들 때 사용하는 가장 기본적인 방법이다.

#### - 장점

- 신경 써야 할 코드양이 적다.
- webpack 설정을 신경 쓰지 않을 수 있다.

#### - 단점

- react-scripts로 인한 추상화로 설정 flow의 이해가 힘들다.
- 추상화 정도가 높아서 라이브러리 적용 시 webpack등 코어한 부분을 건드려야 할 경우, 결국 eject를 해야 한다.
- (CRA 공통) webpack-dev-server를 이용한 개발 모드를 위한 서버만 제공, build된 파일로 프로덕션 서버(BFF) 실행을 위해서는 CRA와 동떨어진 새로운 서버를 만들어야 한다.
- (CRA 공통) SSR을 자체적으로 지원하지 않기 때문에 추가 작업이 필요하다.
- (CRA 공통) code-splitting을 위해서는 특별히 코드에 명시해야 한다.
- (CRA 공통) client-side routing을 위해서 react-router같은 라이브러리를 설치해야 한다.

<br>

### - CRA(eject O)

CRA에서 eject를 해서 사용하는 방법이다.

#### - 장점

- webpack을 커스터마이징하여 설정할 수 있다.

#### - 단점

- 건드릴 필요 없는 불필요한 코드 증가로 인한 복잡성이 증가한다.
- JavaScript로 짜여진 CRA의 모든 config 파일들(Webpack, Babel ...)을 직접 유지보수해야 한다.
- One Build Dependency의 장점을 잃게 된다. 작업 도중 하나의 패키지가 필요해서 설치한다거나 삭제할 때 항상 다른 패키지들과의 의존성을 신경 써야 한다.

<br>

### - Next.js

Zero configuration 컨셉을 지닌 ZEIT사의 next.js이다. 카카오 페이지, 트리플, 하이퍼커넥트, 우아한 형제들 웹툰, Netflix, Tencent News, Twitch, Hulu, Nike, Uber 등 다양한 곳에서 사용하며 수십 가지 다양한 라이브러리 연동 예제(redux, apollo, …)를 제공한다.

#### - 장점

- Zero Configuration이라는 특징에 맞게 플랫폼 관리 시간이 적게 들고 컴포넌트 개발을 통한 서비스 개발에 집중할 수 있게 한다.
- 데이터 프리패칭을 지원한다. SSG(Static Site Generation), SSR(Server Side Rendering)이 사용 가능하며, CSR(Client Side Rendering)도 사용 가능하다.
- 개발 모드를 위한 서버뿐만 아니라, 프로덕션 서버(BFF)도 제공 및 다양한 서버 라이브러리(Express, Koa)로 수정이 가능하다.
- SSR 지원 및 Google Chrome 팀과 협업으로 SEO 및 로드 성능이 높다.
- 코드 베이스가 TypeScript이고, 자체적으로 TypeScript를 지원한다.
- 특별한 설정을 하지 않아도 개발 편의 기능을 지원한다. (페이지에 사용되는 코드만 로드하는 code-splitting를 통한 번들 최적화, 파일 기반 라우팅, Webpack, Babel을 이용한 자동 컴필레이션 및 번들링, React Fast Refresh, SSG, SSR, static 파일 서빙 시 ./public를 /에 매핑)

#### - 단점

- 커스텀 해야 할 부분이 생길 경우가 있다. (그러나 CRA eject에 비하면 편리)
  > next.config.js : next-transpile-modules, spritePlugin, optimizedImages
  > custom server : 지원하지 않는 브라우저 처리 혹은 미들웨어 사용
- 리액트 프레임워크이기 때문에 프레임워크에 대한 지식(\_app.js, \_document.js 등)이 필요하다.

<br>

### - 추상화 정도

CRA(eject X) > Next.js > CRA(eject O)

<br>

### - 개발자 경험

Next.js > CRA(eject X) > CRA(eject O)

<br>

---

<br>

참고자료

- <a href="https://coding-grandpa.tistory.com/2" target='_blank'>보일러 플레이트(Boiler Plate) 이해하기</a>
- <a href="https://velog.io/@lua_aw/201105-2-React-%EB%B3%B4%EC%9D%BC%EB%9F%AC%ED%94%8C%EB%A0%88%EC%9D%B4%ED%8A%B8-CRACreate-React-App" target='_blank'>React 보일러 플레이트 Boiler Plate CRA(Create-React-App)</a>
- <a href="https://blog-lino.dev/react/create-react-boilerplate/" target='_blank'>나만의 React Boilerplate를 만들어보자</a>
- <a href="https://geonlee.tistory.com/216" target='_blank'>create-react-app 와 next.js 어떤 걸 써야 할까?
- <a href="https://medium.com/@OPTASY.com/create-react-app-vs-next-js-which-one-should-you-go-with-for-building-your-next-app-c025159dc0b" target='_blank'>Create React App vs Next.js: Which One Works for You?
