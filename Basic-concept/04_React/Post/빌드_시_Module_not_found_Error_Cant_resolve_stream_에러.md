# **# 빌드 시 "Module not found: Error: Can't resolve 'stream..." 에러**

kpa pedia 프로젝트를 netlify로 배포하는데 아래와 같은 문제가 발생했다.

<img width="1114" alt="react_빌드_시_Module_not_found_Error_Cant_resolve_stream_에러_01" src="https://github.com/Yu-jae-min/Basic-concept/assets/85284246/b57b2c30-4ccd-440a-ab24-c31f0eeedbcb">

<br>

## **# 해결 방법**

### **# 1. 필요 패키지 설치**

해결에 필요한 패키지를 설치한다. 필요 없는 패키지가 아래 목록 중 포함 되어있을 수 있다.

> yarn add url webpack-cli stream-http stream-browserify react-app-rewired os-browserify os https-browserify fs crypto-browserify buffer assert process

<br>

### **# 2. package.json 수정**

package.json에 script 부분을 수정한다.

```json
// package.json
...
  "scripts": {
    "start": "react-app-rewired start",
    "build": "react-app-rewired build",
    "test": "react-app-rewired test",
    "eject": "react-app-rewired eject"
  },
...
```

<br>

### **# 3. config-overrides.js 생성**

root 경로(package.json과 같은 위치)에 config-overrides.js를 생성한다.

```js
// config-overrides.js
module.exports = {
  // The Webpack config to use when compiling your react app for development or production.
  webpack: function (config, env) {
    const overridedConfig = {
      ...config,
      resolve: {
        ...config.resolve,
        fallback: {
          ...config.resolve.fallback,
          fs: false,
          net: false,
          stream: require.resolve("stream-browserify"),
          crypto: require.resolve("crypto-browserify"),
          http: require.resolve("stream-http"),
          https: require.resolve("https-browserify"),
          os: require.resolve("os-browserify/browser"),
          url: require.resolve("url"),
        },
      },
    };
    return overridedConfig;
  },
};
```

<br>

### **# 4. webpack.config.js 생성**

root 경로(package.json과 같은 위치)에 webpack.config.js를 생성한다.

```js
const webpack = require("webpack");

module.exports = {
  plugins: [
    new webpack.ProvidePlugin({
      process: "process/browser",
    }),
  ],
};
```

webpack polyfills 이슈과 연간이 있다. react-app-rewired 패키지 이용해서 웹팩 오버라이딩 해주니 정상적으로 빌드되었다.

<img width="676" alt="react_빌드_시_Module_not_found_Error_Cant_resolve_stream_에러_02" src="https://github.com/Yu-jae-min/Basic-concept/assets/85284246/90f2e90d-a73d-447c-bb38-98fbd925ef29">

<br>

## **# 추가 에러 해결**

> 위 에러를 해결한 뒤 라우팅 에러를 처리하는데 또 다시 에러가 발생하였다. axios의 return값이 index.html 자체를 반환하는 에러였다. 알고 보니 public/\_redirects에 만들어놓은 파일이 문제였다. 이 파일을 지우고 프로젝트 최상위 경로에 netlify.toml 파일에 아래와 같이 수정하여 해결하였다.

```toml
[[redirects]]
  from = "/proxy/*"
  to = "https://www.kopis.or.kr/:splat"
  status = 200
  force = true

[[redirects]]
  from = "/*"
  to = "/index.html"
  status = 200
```
