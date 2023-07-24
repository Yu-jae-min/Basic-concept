# **[Next.js] PWA(Progressive Web Apps)**

2023년 07월 24일

<br>

## **1. PWA(Progressive Web Apps)**

### **1-1. PWA란?**

PWA(Progressive Web Apps)란 모바일 기기에서 네이티브 앱과 같은 사용자 경험을 제공하는 웹 앱이다.
즉 어떤 기술이나 앱을 뜻하는 것이 아닌, 비슷한 개념으로 반응형 웹 앱을 예로 들 수 있는데 이와 같이 사용자 경험을 기준으로 나타낼 수 있는 개념이다. PWA를 사용하면 사용자가 앱을 다운로드하고 업데이트 할 필요 없이 웹 브라우저를 통해 앱을 바로 사용할 수 있다.

<br>

### **1-2. PWA 장단점**

#### **1-2-1. 장점**

- **훨씬 빠른 페이지 로딩 속도**

  `Service Worker` 의 [Cache API](https://developer.mozilla.org/en-US/docs/Web/API/Cache)를 사용하여 데이터를 캐싱시킬 수 있다. 이를 통해 두번째 방문 부터 캐싱된 데이터를 통해 즉각적인 페이지 로딩을 시킬 수 있다. 정적데이터와 동적데이터에 대한 캐싱 정책을 어떻게 정하느냐에 따라 페이지 로딩 결과가 달라지게 된다.

- **오프라인 지원 (네트워크에 독립적)**

  `Service Worker` 에 캐싱된 데이터를 가져오게 되면 네트워크가 오프라인 상태라도 서비스를 사용할 수 있게 된다. 따라서 `PWA` 로 웹 앱을 구성하게 되면 오프라인 상태라도 브라우저에 더 이상 오프라인 상태라고 표시되지 않으며 캐싱된 데이터를 그대로 보여 줄 수 있다. 단, 우선 Service Worker에 캐싱을 해야되기 때문에 1, 2번은 페이지를 한 번이라도 방문 해야 한다. 그리고 이제 웹 앱에서도 `Background Sync`가 가능하기 때문에 오프라인 상황에서 서버에 전달할 데이터들의 유실을 방지할 수 있다.

- **검색 가능**

  웹 앱의 특성 그대로 검색이 가능하다.

- **설치 가능 (홈 화면에 추가)**

  `PWA` 는 웹 앱 매니페스트 내부에 설정된 속성과 [웹 앱 설치](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps/Developer_guide/Installing) 라는 최신 모바일 브라우저에서 사용할 수 있는 기능을 통해 웹 앱을 현재 모바일 브라우저를 사용하는 디바이스의 홈 화면에 추가 즉, 설치와 같이 등록 할 수 있다.

- **공유 가능 (링크를 통한)**

  웹 앱 이기 때문에 URL을 통한 공유도 가능하다.

- **푸시알림을 통한 지속적 참여 유도**

  최신 브라우저에서 Web API인 [Push API](https://developer.mozilla.org/en-US/docs/Web/API/Push_API) 를 사용하여 서버로부터 알림을 push event로 받고, [Notification API](https://developer.mozilla.org/en-US/docs/Web/API/Notifications_API) 을 이용해 브라우저에 시스템 알림을 보여 줄 수 있다. 이는 사용자의 재참여를 유도할 수 있고 사용자의 재참여를 유도하는 네이티브 앱의 핵심 기능을 웹에서 구현할 수 있게 된 것이다.

- **반응형 웹 화면**

  `PWA` 의 가장 기본은 반응형 웹 앱 이기 때문에 웹 브라우저를 사용하는 다양한 디바이스의 화면에 모두 대응할 수 있다.

- **안전**

  `PWA` 을 구현하기 위한 기술은 HTTPS 에서만 사용이 가능하고 브라우저의 보안정책인 CORS 등을 따르기 때문에 보안적인 이점도 있다.

- **점진적, 구축이 쉬움**

  이미 구축된 웹 앱이라고 해서 `PWA`로 사용하지 못하는 것은 아니다. 기존에 구축된 웹 앱에 `Service Worker`와 `Manifest.json` 파일을 만들어 PWA로 구축하는 것은 매우 쉽고 또, 점진적으로 `PWA`에 요구되는 기능들을 하나씩 점진적으로 추가해 갈 수 있다.

<br>

#### **1-2-2. 단점**

- **PWA에 대한 인지도 부족, 앱 설치의 애매함**

  사용자들에게 PWA는 익숙하지 않기 때문에 접근성이 낮을 수 있다. 스토어를 통해 설치된 앱은 그나마 안전하다는 인식을 가지고 있지만 PWA와 같이 홈 화면 추가 기능을 통한 앱 설치는 아니다. 또한 이를 유도하는 안내 또한 별도로 필요하다. 이러한 문제를 고려한 구글과 마이크로소프트는 스토어에 PWA를 배포할 수 있도록 해놓았다고 한다. 이전에 근무했던 라인쓰리의 매치아크도 Bubble wrap을 사용하여 PWA를 안드로이드 앱으로 빌드했었다. 하지만 애플에게는 아직 기대할 수 없다.

- **Non-native UI**

  HTML, CSS, JS를 가지고도 얼마든지 아름답고 훌륭한 UI를 구현할 수 있지만, 네이티브 앱에서 느낄 수 있는 각 운영체제 고유의 UI와 사용자 경험을 제공할 수 없다.

- **Apple의 소극적인 지원**

  현재 PWA가 널리 보급되는 데 가장 큰 걸림돌로 작용하는 것은 PWA에 대한 Apple의 소극적인 태도이다. 2015년 PWA 개념이 세상에 등장한 이후부터 구글, Microsoft, Mozilla 등이 웹 기술의 발전을 반기며 PWA 지원에 적극 동참하였지만 Apple은 아이폰 11.3 버전(2018년)이 되어서야 PWA를 지원했다.
  PWA의 핵심 중 하나인 푸시 알림 기능의 경우 안드로이드에서는 오래전부터 가능했지만 iOS에서는 아직도 불가능한 상황이다. 사실 Apple이 이렇게 PWA에 폐쇄적인 이유는 자명한데, 개발자와 사용자들이 Apple의 앱스토어를 통하지 않고도 자유롭게 앱을 만들고 사용할 수 있게 허용한다면 지금까지 자신들이 거두어들였던 앱 수수료라는 엄청난 수익원을 포기한다는 것과 다름없기 때문이다.
  하지만 Apple이 드디어 푸시 알림 인질을 풀어주려는 계획을 발표했다. Apple은 WWDC22(2022 연례 세계 개발자 콘퍼런스)에서 2023년에는 웹 푸시와 관련한 모든 API를 지원할 것이라고 알렸다. 아직 계획일 뿐이기 때문에 방심하기는 이르지만 굉장히 반가운 소식이다.

- **게임과 같은 고사양 앱 개발 불가능**

  현재 웹 기술이 계속해서 발전하고 있지만 운영체제의 자원을 직접적으로 사용할 수 있는 네이티브 앱의 퍼포먼스는 따라잡을 수 없다. 높은 연산을 요구하는 작업, 그래픽 사용이 필수인 게임 앱 개발에는 한계가 있다.

<br>

### **1-3. PWA 구축을 위한 핵심기술**

#### **1-3-1. Manifest.json**

`Manifest.json`은 웹 앱 매니페스트로 웹 앱을 디바이스의 홈 화면에 추가 할 수 있게 해주고 오프라인 상황에서 어떻게 할 지 등 그에 따른 설정을 할 수 있게 해준다. (ex 앱스토어에서 별도 설치없이 웹 페이지에서 디바이스에 추가 가능) 매니페스트에는 이름, 작성자, 아이콘, 버전, 설명, 필요한 모든 리소스 목록 등을 설정 할 수 있다.

<br>

#### **1-3-2. ServiceWorker**

`PWA`를 하기위한 가장 핵심 기술은 `Service Worker` 를 꼽을 수 있다. `PWA`는 `Service Worker` 때문에 가능해졌다고 해도 과언이 아니다.

`Service Worker`는 브라우저의 `thread`를 이용하는 `Web Worker`의 일종으로 Client Browser에 등록되어 Background로 동작하는 javascript file이다.

`Service Worker`의 주 역할은 브라우저에서 서버로 가는 request, response를 가로채는 proxy 서버로 작동하기 때문에 네트워크 작업을 통해 주고 받는 컨텐츠들을 수정하고 저장하는 등의 처리를 함으로써 웹 앱에 다양하고 유용한 기능을 구현 할 수 있다.

이러한 proxy 작업을 통해 정적 데이터 캐싱, 동적 데이터 캐싱과 같은 일이 가능해지고 캐싱된 데이터를 통해 오프라인 서비스 지원이 가능해 지며 서버로 요청되는 request를 오프라인시에 캐싱 및 작업 큐에 넣어두고, 온라인 환경이 되었을 때 관련 요청들을 큐에서 꺼내 다시 request 요청을 처리하게 하는 background sync 작업 도 가능해 진다.

또 Push API, Notification API등을 `Service Worker`에 등록 및 연계해서 사용 할 수 있어 웹 알람을 구현 할 수 있는 핵심 기술이라 할 수 있다.

<br>
<br>

## **2. Next.js에서 PWA 적용해보기**

### **2-1. 설치하기**

```jsx
npm i -D next-pwa
yarn add next-pwa -D
```

### **2-2. next.config.js 파일을 생성**

적용을 위해선 next.config.js 파일에 다음의 설정내용을 추가해야 한다.
반드시 `public`이 설정되어야 한다. 그렇지 않으면 다른 곳에 설치되어 서비스워커를 설정하지 못한다.

```jsx
const withPWA = require("next-pwa");

module.exports = withPWA({
  pwa: {
    dest: "public",
  },
});
```

플러그인을 여러 개 사용하고 싶다면 `next-compose-plugins`를 사용할 수 있다. `next-compose-plugins`는 패키지를 하나로 묶을 수 있도록 도와준다.

```jsx
const withPlugins = require("next-compose-plugins");
const withPWA = require("next-pwa");
const withOptimizedImages = require("next-optimized-images");
const withFonts = require("next-fonts");
const FilterWarningsPlugin = require("webpack-filter-warnings-plugin");

const nextConfig = {
  generateEtags: false,
  webpack: (config, { isServer }) => {
    config.plugins.push(
      new FilterWarningsPlugin({
        exclude: /mini-css-extract-plugin[^]*Conflicting order between:/,
      })
    );
    config.resolve.modules.push(__dirname);

    return config;
  },
};

module.exports = withPlugins(
  [
    [
      withPWA,
      {
        pwa: {
          dest: "public",
        },
      },
    ],
    [
      withOptimizedImages,
      {
        mozjpeg: {
          quality: 90,
        },
        webp: {
          preset: "default",
          quality: 90,
        },
      },
    ],
    withFonts,
  ],
  nextConfig
);
```

### **2-3. manifest.json 등록**

브라우저에게 이 웹은 PWA라는것을 알려주기 위해서 아래와 같은 manifest를 작성해준다.

```json
{
  "short_name": "APP 이름",
  "name": "APP 이름",
  "start_url": "/",
  "display": "standalone",
  "theme_color": "#000000",
  "background_color": "#ffffff",
  "icons": [
    {
      "src": "./icons/apple-touch-icon-57x57.png",
      "sizes": "57x57",
      "type": "image/png"
    },
    {
      "src": "./icons/apple-touch-icon-60x60.png",
      "sizes": "60x60",
      "type": "image/png"
    },
    {
      "src": "./icons/apple-touch-icon-72x72.png",
      "sizes": "72x72",
      "type": "image/png"
    },
    {
      "src": "./icons/apple-touch-icon-76x76.png",
      "sizes": "76x76",
      "type": "image/png"
    },
    {
      "src": "./icons/apple-touch-icon-114x114.png",
      "sizes": "114x114",
      "type": "image/png"
    },
    {
      "src": "./icons/apple-touch-icon-120x120.png",
      "sizes": "120x120",
      "type": "image/png"
    },
    {
      "src": "./icons/apple-touch-icon-144x144.png",
      "sizes": "144x144",
      "type": "image/png"
    },
    {
      "src": "./icons/apple-touch-icon-152x152.png",
      "sizes": "152x152",
      "type": "image/png"
    },
    {
      "src": "./icons/favicon-512x512.png",
      "sizes": "512x512",
      "type": "image/png"
    },
    {
      "src": "./icons/favicon.ico",
      "sizes": "64x64",
      "type": "image/icon",
      "purpose": "any maskable"
    }
  ]
}
```

위와 같이 한땀 한땀 작성할 수 있지만 아래 링크를 활용하여 조금 더 편리하게 작성할 수 있다.

- 참고 : [https://www.simicart.com/manifest-generator.html](https://www.simicart.com/manifest-generator.html/)

### **2-4. 메타태그 적용**

브라우저가 PWA라는것을 알아채고 manifest에 접근할 수 있도록 메타태그를 적용해야한다.
기본적인 메타태그는 아래와 같다.
메타태그는 `_document.js`를 생성해서 적용한다. (꼭 `_document.js`일 필요는 없다.)

- 참고 : https://github.com/gokulkrishh/awesome-meta-and-manifest

```html
<meta charset='utf-8' />
<meta http-equiv='X-UA-Compatible' content='IE=edge' />
<meta name='viewport' content='width=device-width,initial-scale=1,minimum-scale=1,maximum-scale=1,user-scalable=no' />
<meta name='description' content='Description' />
<meta name='keywords' content='Keywords' />
<title>Next.js PWA Example</title>

<link rel="manifest" href="/manifest.json" />
<link href='/favicon-16x16.png' rel='icon' type='image/png' sizes='16x16' />
<link href='/favicon-32x32.png' rel='icon' type='image/png' sizes='32x32' />
<link rel="apple-touch-icon" href="/apple-icon.png"></link>
<meta name="theme-color" content="#317EFB"/>
```

### **2-5. gitignore 파일 설정해 주기**

build 할 때 나오는 여러 파일을 git에서 제외하기 위해서 .gitignore 에서 다음과 같이 추가해 준다.

```
public/sw.js
public/workbox-*.js
```

### **2-6. 테스트해보기**

아래 명령어를 통해 빌드 후 실행한다.

```html
npm run build && npm run start
```

그 후 크롬 개발자도구 lighthouse탭으로 이동하여 generate report(보고서 생성)를 클릭한다.

![PWA_01](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/4d50f888-cb76-472a-a841-20087e069ccb)

아래와 같이 성공이 뜨면 PWA가 잘 적용되었다는 뜻이다.

![PWA_02](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/1b985d08-a02a-4887-9e2e-313c959e340c)

마지막 줄인 '매니페스트에 마스크 가능한 아이콘이 없음'이 보이는데, manifest.json 파일 내 icons 라는 배열 내부 객체에 `"purpose": "any maskable"`를 추가해주면 해결된다.

```json
...
"icons": [
    {
      "src": "./icons/favicon.ico",
      "sizes": "64x64",
      "type": "image/icon",
      "purpose": "any maskable" // 추가
    }
  ...
]
```
