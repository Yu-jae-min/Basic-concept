# [javascript] 바벨(Babel)

## **# 바벨(Babel)**

- ES6+(ECMAScript 2015+) 코드를 하위 버전으로 변환해주는 트랜스파일러
- 하위 JS 문법으로 변환할 수 없는 코드는 core-js같은 third-party 폴리필을 통해 변환
- Typescript 코드를 컴파일 시점에 Javascript 코드로 변환
- Webpack / Rollup 등의 정적 모듈 번들러들을 통해 함께 사용 가능

<br>

### **# 바벨 빌드 단계**

바벨은 아래와 같이 설치할 수 있다.

> npm install -D @babel/core @babel/cli

1. 파싱(Parsing)

- 코드를 읽고 추상 구문 트리(AST)로 변환하는 단계
- AST 자료구조는 빌드 작업을 처리하기에 적합한 하나의 자료구조
- **바벨 코어(core)가 수행**

2. 변환(Transforming)

- AST를 실제 코드로 변환하는 단계
- **플러그인(Plugin)이 수행**

3. 출력(Printing)

- 최종적으로 변환된 코드를 출력하는 단계
- **바벨 코어(core)가 수행**

<br>

### **# 변환을 담당하는 플러그인**

#### # 플러그인 설치

> npm install -D ‘플러그인 이름’

#### # 플러그인 종류

- 블록 스코핑에 따른 변수 변경 : @babel/plugin-transform-block-scoping
- 화살표 함수를 일반 함수로 변경 : @babel/plugin-transform-arrow-functions
- 엄격모드 사용 : @babel/plugin-transform-strict-mode

#### # 플러그인 적용

아래와 같이 설치 후 바로 적용시킬 수 있다.

> npx babel app.js --plugins @babel/plugin-transform-block-scoping

또한 웹팩 webpack.config.js를 기본 설정파일로 사용하듯 바벨도 babel.config.js를 사용한다.

```javascript
// ./babel.config.js
module.exports = {
  plugins: [
    "@babel/plugin-transform-block-scoping",
    "@babel/plugin-transform-arrow-functions",
    "@babel/plugin-transform-strict-mode",
  ],
};
```

<br>

### **# 프리셋**

목적에 맞게 여러 가지 플러그인을 세트로 모아놓은 것을 “프리셋”이라고 한다.

#### # 커스텀 프리셋

```javascript
// mypreset.js
module.exports = function mypreset() {
  return {
    plugins: [
      "@babel/plugin-transform-arrow-functions",
      "@babel/plugin-transform-block-scoping",
      "@babel/plugin-transform-strict-mode",
    ],
  };
};
```

위의 플러그인을 아래와 같이 변경할 수 있다.

```javascript
// babel.config.js
module.exports = {
  presets: ["./mypreset.js"],
};
```

#### # 제공되는 프리셋

- preset-env : 최신 문법 ES5로 변환
- preset-flow : 플로우(타입 체크 라이브러리) 변환
- preset-react : 리액트 변환
- preset-typescript : 타입스크립트 변환

1. 패키지 다운

```
npm install -D @babel/preset-env
```

2. 바벨 설정 변경

```javascript
// ./babel.config.js
module.exports = {
  presets: ["@babel/preset-env"],
};
```

3. 빌드

```
$ npx babel app.js
```

<br>

### **# 폴리필**

바벨은 ES6 이후 버전을 ES5 버전으로 변환할 수 있는 것만 빌드한다.
그렇지 못한 것들은 폴리필이라고 부르는 코드조각을 추가해서 해결한다.
다만 ES5 버전으로 구현할 수는 있다.

```javascript
// ./app.js
new Promise();
```

아래와 같이 env 프리셋으로 변환을 시도했지만, Promise 그대로 변함이 없다.

```javascript
$ npx babel app.js

"use strict";

new Promise();
```

이 때 폴리필을 지정한다.

```javascript
// ./babel.config.js
module.exports = {
  presets: [
    [
      "@babel/preset-env",
      {
        useBuiltIns: "usage", // 폴리필 사용 방식 지정.
        corejs: {
          // 폴리필 버전 지정.
          version: 2,
        },
      },
    ],
  ],
};
```

useBuiltIns는 어떤 방식으로 폴리필을 사용할지 설정하는 옵션이다.
usage, entry, false 세 가지 값을 사용하는데 기본값이 false이므로 폴리필이 동작하지 않았다.
반면 usage나 entry를 설정하면 폴리필 패키지 중 core-js를 모듈로 가져온다.
폴리필 추가 후 빌드해보면 인터넷 익스플로러에서 안전하게 돌아가는 결과물이 나온다.

<br>

### **# 웹팩**

실무 환경에서는 바벨을 직접 사용하지 않고 웹팩으로 통합해서 사용한다.
보통 로더 형태로 제공하는데 babel-loader가 있다.

```
npm install -D babel-loader
```

위와 같이 패키지 설치 후 아래와 같이 웹팩 설정에 로더를 추가한다.

```javascript
// ./webpack.config.js
module.exports = {
  module: {
    rules: [
      {
        test: /\.js$/,
        exclude: /node_modules/,
        loader: "babel-loader", // 바벨 로더를 추가한다.
      },
    ],
  },
};
```

.js 확장자로 끝나는 파일은 babel-loader가 처리하도록 설정했다.
사용하는 써드파티 라이브라리가 많을수록 바벨 로더가 느리게 동작할 수 있는데 node_modules 폴더를 로더가 처리하지 않도록 예외 처리했다.
폴리필 사용 설정을 했다면 core-js도 설치해야한다.
웹팩은 바벨 로더가 만든 아래 코드를 만나면 core-js를 찾을 것이기 때문이다.

```javascript
# 웹팩이 찾고자 하는 두 가지 모듈 예시.
require("core-js/modules/es6.promise")
require("core-js/modules/es6.object.to-string")
```

버전 2로 패키지를 추가하자.

```
$ npm i core-js@2
```

그리고 웹팩으로 빌드하면,

```
$ npm run build

> webpack

Hash: a30cff5fbf53027423a0
Version: webpack 4.41.2
Time: 718ms
Built at: 2019. 12. 16. 오전 8:52:05
Asset Size Chunks Chunk Names
main.js 59.7 KiB main [emitted] main
Entrypoint main = main.js
[./src/app.js] 166 bytes {main} [built]
```

미리 등록해 놓은 NPM build 스크립트의 webpack 명령어가 동작한다.
./src/app.js의 엔트리 포인트가 바벨 로더에 의해 빌드되고 결과물이 ./dist/main.js로 옮겨졌다.

```javascript
cat ./dist/main.js | grep 'var alert' -A 5

var alert = function alert(msg) {
return window.alert(msg);
};

new Promise();
```

<br>

---

<br>

참고자료

- <a href="https://jeonghwan-kim.github.io/series/2019/12/22/frontend-dev-env-babel.html" target='_blank'>프론트엔드 개발환경의 이해: Babel</a>
- <a href="https://www.inflearn.com/course/%ED%94%84%EB%A1%A0%ED%8A%B8%EC%97%94%EB%93%9C-%EA%B0%9C%EB%B0%9C%ED%99%98%EA%B2%BD" target='_blank'>프론트엔드 개발환경의 이해와 실습 (webpack, babel, eslint..)</a>
