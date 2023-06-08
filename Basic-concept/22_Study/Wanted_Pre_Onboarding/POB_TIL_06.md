# [pob] POB TIL-06

## # Today I Learn - 2022.05.11

### # Pre Onboarding Course

- **학습 내용**

1. **tsconfig에 절대경로 설정 옵션** : ts config에 include src옵션을 넣으면 절대 경로를 설정하기 매우 편리하다. 상대 경로보다 절대 경로를 사용하여야 폴더 구조가 변하여도 프로젝트가 터지는 경우가 발생하지 않는다.
2. **FE와 BE의 테스트 코드** : 백엔드의 경우 테스트 코드를 통해 에러를 많이 잡아내는데 프론트엔드의 경우 렌더 단에서 에러를 발생하기 때문에 테스트 코드의 필요성이 상대적으로 적다.
3. **module scss의 장점** : module scss의 장점은 디버깅 시 개발자 도구에서 파일의 위치를 바로 파악할 수 있다.
4. **EsLint 에서 plugin과 config** : `eslint-plugin-\*`는 plugin은 룰을 정의한 것이다. `eslint-config-*`는 `eslint-plugin-*` 패키지들이나 룰들을 모아서 설정으로 만든 것이 `eslint-config-\*` 패키지다.
5. **prettier 전체 옵션**

```json
{
  // prettier 전체 옵션
  "compilerOptions": {
    /* https://aka.ms/tsconfig.json 를 방문하면 해당 파일에 대한 더 많은 정보를 얻을 수 있습니다. */

    // 옵션은 아래와 같은 형식으로 구성되어 있습니다.
    "모듈 키": "모듈 값" /* 설명: 사용가능 옵션 (설명이 "~ 여부"인 경우 'true', 'false') */,

    /* 기본 옵션 */
    "incremental": true /* 증분 컴파일 설정 여부 */,
    "target": "es5" /* 사용할 특정 ECMAScript 버전 설정: 'ES3' (기본), 'ES5', 'ES2015', 'ES2016', 'ES2017', 'ES2018', 'ES2019', 'ES2020', 혹은 'ESNEXT'. */,
    "module": "commonjs" /* 모듈을 위한 코드 생성 설정: 'none', 'commonjs', 'amd', 'system', 'umd', 'es2015', 'es2020', or 'ESNext'. */,
    "lib": [] /* 컴파일에 포함될 라이브러리 파일 목록 */,
    "allowJs": true /* 자바스크립트 파일 컴파일 허용 여부 */,
    "checkJs": true /* .js 파일의 오류 검사 여부 */,
    "jsx": "preserve" /* JSX 코드 생성 설정: 'preserve', 'react-native', 혹은 'react'. */,
    "declaration": true /* '.d.ts' 파일 생성 여부. */,
    "declarationMap": true /* 각 '.d.ts' 파일의 소스맵 생성 여부. */,
    "sourceMap": true /* '.map' 파일 생성 여부. */,
    "outFile": "./" /* 단일 파일로 합쳐서 출력합니다. */,
    "outDir": "./" /* 해당 디렉토리로 결과 구조를 보냅니다. */,
    "rootDir": "./" /* 입력 파일의 루트 디렉토리(rootDir) 설정으로 --outDir로 결과 디렉토리 구조를 조작할 때 사용됩니다. */,
    "composite": true /* 프로젝트 컴파일 여부 */,
    "tsBuildInfoFile": "./" /* 증분 컴파일 정보를 저장할 파일 */,
    "removeComments": true /* 주석 삭제 여부 */,
    "noEmit": true /* 결과 파일 내보낼지 여부 */,
    "importHelpers": true /* 'tslib'에서 헬퍼를 가져올 지 여부 */,
    "downlevelIteration": true /* 타겟이 'ES5', 'ES3'일 때에도 'for-of', spread 그리고 destructuring 문법 모두 지원 */,
    "isolatedModules": true /* 각 파일을 분리된 모듈로 트랜스파일 ('ts.transpileModule'과 비슷합니다). */,

    /* 엄격한 타입-확인 옵션 */
    "strict": true /* 모든 엄격한 타입-체킹 옵션 활성화 여부 */,
    "noImplicitAny": true /* 'any' 타입으로 구현된 표현식 혹은 정의 에러처리 여부 */,
    "strictNullChecks": true /* 엄격한 null 확인 여부 */,
    "strictFunctionTypes": true /* 함수 타입에 대한 엄격한 확인 여부 */,
    "strictBindCallApply": true /* 함수에 엄격한 'bind', 'call' 그리고 'apply' 메소드 사용 여부 */,
    "strictPropertyInitialization": true /* 클래스의 값 초기화에 엄격한 확인 여부 */,
    "noImplicitThis": true /* 'any' 타입으로 구현된 'this' 표현식 에러처리 여부 */,
    "alwaysStrict": true /* strict mode로 분석하고 모든 소스 파일에 "use strict"를 추가할 지 여부 */,

    /* 추가적인 확인 */
    "noUnusedLocals": true /* 사용되지 않은 지역 변수에 대한 에러보고 여부 */,
    "noUnusedParameters": true /* 사용되지 않은 파라미터에 대한 에러보고 여부 */,
    "noImplicitReturns": true /* 함수에서 코드의 모든 경로가 값을 반환하지 않을 시 에러보고 여부 */,
    "noFallthroughCasesInSwitch": true /* switch문에서 fallthrough 케이스에 대한 에러보고 여부 */,

    /* 모듈 해석 옵션 */
    "moduleResolution": "node" /* 모듈 해석 방법 설정: 'node' (Node.js) 혹은 'classic' (TypeScript pre-1.6). */,
    "baseUrl": "./" /* non-absolute한 모듈 이름을 처리할 기준 디렉토리 */,
    "paths": {} /* 'baseUrl'를 기준으로 불러올 모듈의 위치를 재지정하는 엔트리 시리즈 */,
    "rootDirs": [] /* 결합된 컨텐츠가 런타임에서의 프로젝트 구조를 나타내는 루트 폴더들의 목록 */,
    "typeRoots": [] /* 타입 정의를 포함할 폴더 목록, 설정 안 할 시 기본적으로 ./node_modules/@types로 설정 */,
    "types": [] /* 컴파일중 포함될 타입 정의 파일 목록 */,
    "allowSyntheticDefaultImports": true /* default export이 아닌 모듈에서도 default import가 가능하게 할 지 여부, 해당 설정은 코드 추출에 영향은 주지 않고, 타입확인에만 영향을 줍니다. */,
    "esModuleInterop": true /* 모든 imports에 대한 namespace 생성을 통해 CommonJS와 ES Modules 간의 상호 운용성이 생기게할 지 여부, 'allowSyntheticDefaultImports'를 암시적으로 승인합니다. */,
    "preserveSymlinks": true /* symlik의 실제 경로를 처리하지 않을 지 여부 */,
    "allowUmdGlobalAccess": true /* UMD 전역을 모듈에서 접근할 수 있는 지 여부 */,

    /* 소스 맵 옵션 */
    "sourceRoot": "" /* 소스 위치 대신 디버거가 알아야 할 TypeScript 파일이 위치할 곳 */,
    "mapRoot": "" /* 생성된 위치 대신 디버거가 알아야 할 맵 파일이 위치할 곳 */,
    "inlineSourceMap": true /* 분리된 파일을 가지고 있는 대신, 단일 파일을 소스 맵과 가지고 있을 지 여부 */,
    "inlineSources": true /* 소스맵과 나란히 소스를 단일 파일로 내보낼 지 여부, '--inlineSourceMap' 혹은 '--sourceMap'가 설정되어 있어야 한다. */,

    /* 실험적 옵션 */
    "experimentalDecorators": true /* ES7의 decorators에 대한 실험적 지원 여부 */,
    "emitDecoratorMetadata": true /* decorator를 위한 타입 메타데이터를 내보내는 것에 대한 실험적 지원 여부 */,

    /* 추가적 옵션 */
    "skipLibCheck": true /* 정의 파일의 타입 확인을 건너 뛸 지 여부 */,
    "forceConsistentCasingInFileNames": true /* 같은 파일에 대한 일관되지 않은 참조를 허용하지 않을 지 여부 */
  }
}
```

- **그립 무비 앱 프로젝트 초기 세팅 (react + typescript, eslint + prettier + stylelint)**

1. 프로젝트 생성 : npx create-react-app my-app --template typescript (참고: https://create-react-app.dev/docs/adding-typescript/)
2. eslint 패키지 설치 : npm i -D eslint @typescript-eslint/parser @typescript-eslint/eslint-plugin
3. root 디렉토리에 .eslintrc.js 혹은 .eslintrc.json 생성 후 설정

```json
{
  "extends": [
    // extends는 추가한 플러그인에서 사용할 규칙을 설정한다. 플러그인은 일련의 규칙 집합이며, 플러그인을 추가하여도 규칙은 적용되지 않는다. 규칙을 적용하기 위해서는 추가한 플러그인 중, 사용할 규칙을 추가해주어야 적용된다.
    "airbnb",
    "airbnb/hooks",
    "react-app",
    "prettier",
    "plugin:react/recommended"
  ],
  "env": {
    // 사전 정의된 전역 변수 사용을 정의
    "browser": true,
    "jasmine": true,
    "jest": true
  },
  "settings": {
    // 모든 규칙에 의해 공유되는 설정을 하는 부분이며 import/resolver 는 eslint-plugin-import 의 경로 설정 옵션이다. 여기서 노드에서 사용되는 경로부분을 src 로 적어주면 절대경로를 인식하는 원리이다.
    "import/extensions": [".js", ".jsx", ".ts", ".tsx"],
    "import/resolver": {
      "node": {
        "extensions": [".js", ".jsx", ".ts", ".tsx"]
      }
    },
    "react": {
      "pragma": "React",
      "version": "detect"
    }
  },
  "rules": {
    // ESLint에는 프로젝트에서 사용하는 규칙을 수정할 수 있다. 규칙을 변경하는 경우, 다음과 같은 방법으로 설정한다. "off" 또는 0" - 규칙을 사용하지 않음, "warn" 또는 1 - 규칙을 경고로 사용, "error" 또는 2 - 규칙을 오류로 사용
    "arrow-body-style": "off",
    "semi": ["warn", "never"],
    "react/function-component-definition": [
      "warn",
      { "namedComponents": "arrow-function" }
    ],
    "react/jsx-one-expression-per-line": "off",
    "react/jsx-filename-extension": [
      "error",
      { "extensions": [".js", ".jsx", ".ts", ".tsx"] }
    ],
    "react/jsx-indent": "warn",
    "react/jsx-props-no-spreading": "off",
    "react/no-array-index-key": "warn",
    "react/require-default-props": "off",
    "react/jsx-wrap-multilines": "off",
    "react/jsx-uses-react": "off",
    "react/react-in-jsx-scope": "off",
    "import/prefer-default-export": "off",
    "import/no-unresolved": "off",
    "import/order": "off",
    "import/no-anonymous-default-export": "off",
    "import/no-extraneous-dependencies": [
      "error",
      {
        "devDependencies": [".storybook/**", "src/stories/**"]
      }
    ],
    // "max-lines": ["warn", 150],
    "no-param-reassign": ["error", { "props": false }],
    "no-use-before-define": "off",
    "@typescript-eslint/no-use-before-define": ["error"],

    "no-shadow": "off",
    "no-unused-expressions": ["warn"],
    "@typescript-eslint/no-shadow": ["error"],
    "@typescript-eslint/camelcase": "off",
    "@typescript-eslint/unbound-method": "off",
    "@typescript-eslint/no-non-null-assertion": "off",
    "@typescript-eslint/no-unsafe-member-access": "off",
    "@typescript-eslint/no-unsafe-assignment": "off",
    "@typescript-eslint/no-unused-vars": [
      "warn",
      { "argsIgnorePattern": "^_" }
    ],
    "prefer-const": ["warn"],
    "prefer-destructuring": ["error", { "object": true, "array": false }],
    "lines-between-class-members": "off",
    "jsx-a11y/click-events-have-key-events": "off",
    "jsx-a11y/label-has-associated-control": [
      "error",
      {
        "labelComponents": ["label"],
        "labelAttributes": ["htmlFor"],
        "controlComponents": ["input"]
      }
    ],
    "import/extensions": [
      "error",
      "ignorePackages",
      {
        "js": "never",
        "jsx": "never",
        "ts": "never",
        "tsx": "never"
      }
    ]
  }
}
```

4. prettier 패키지 설치 : npm i -D prettier eslint-config-prettier eslint-plugin-prettier
5. root 디렉토리에 .prettierrc.js 혹은 .prettierrc.json 생성 후 설정

```json
// .prettierrc.json
{
  "jsxSingleQuote": true,
  "semi": false,
  "printWidth": 120,
  "proseWrap": "never",
  "singleQuote": true,
  "htmlWhitespaceSensitivity": "css",
  "endOfLine": "lf"
}
```

6. stylelint 패키지 설치 : npm install --save-dev stylelint
7. root 디렉토리에 .stylelintrc.json 생성 후 설정

```json
// .stylelintrc.json
{
  "extends": [
    "stylelint-config-standard-scss",
    "stylelint-config-recess-order"
  ],
  "overrides": [
    {
      "files": ["**/*.scss"],
      "customSyntax": "postcss-scss"
    }
  ],
  "plugins": ["stylelint-declaration-strict-value"],
  "rules": {
    "at-rule-empty-line-before": null,
    "color-function-notation": "legacy",
    "color-hex-case": "lower",
    "color-hex-length": "long",
    "custom-property-empty-line-before": null,
    "declaration-empty-line-before": "never",
    "function-name-case": [
      "lower",
      {
        "ignoreFunctions": "/^[a-z_](|[a-zA-Z0-9]+)$/"
      }
    ],
    "keyframes-name-pattern": "^[a-z][a-zA-Z0-9_]+$",
    "max-nesting-depth": 6,
    "no-descending-specificity": null,
    "no-invalid-position-at-import-rule": null,
    "number-leading-zero": "always",
    "property-no-vendor-prefix": [
      true,
      {
        "ignoreProperties": ["appearance"]
      }
    ],
    "scale-unlimited/declaration-strict-value": [
      "color",
      {
        "ignoreValues": ["inherit", "initial"]
      }
    ],
    "scss/at-function-pattern": "^[a-z_](|[a-zA-Z0-9-]+)$",
    "scss/at-mixin-pattern": "^[a-z_](|[a-zA-Z0-9]+)$",
    "scss/dollar-variable-empty-line-before": null,
    "scss/dollar-variable-pattern": [
      "^[A-Z0-9_]+$",
      {
        "ignore": "local"
      }
    ],
    "scss/double-slash-comment-empty-line-before": null,
    "selector-max-id": 0,
    "selector-class-pattern": "^[a-z](|[a-zA-Z0-9]+)$",
    "selector-pseudo-class-no-unknown": [
      true,
      {
        "ignorePseudoClasses": ["global"]
      }
    ],
    "string-quotes": "single"
  }
}
```

8. 나머지 필요한 패키지 & 플러그인 설치

```json
// package.json
{
  "name": "03.grip_movie_app",
  "version": "0.1.0",
  "private": true,
  "dependencies": {
    "@testing-library/jest-dom": "^5.16.4",
    "@testing-library/react": "^13.2.0",
    "@testing-library/user-event": "^13.5.0",
    "axios": "^0.27.2",
    "classnames": "^2.3.1",
    "react": "^18.1.0",
    "react-dom": "^18.1.0",
    "react-scripts": "5.0.1",
    "recoil": "^0.7.3-alpha.2",
    "store": "^2.0.12",
    "web-vitals": "^2.1.4"
  },
  "scripts": {
    "start": "react-scripts start",
    "build": "react-scripts build",
    "test": "react-scripts test",
    "eject": "react-scripts eject"
  },
  "eslintConfig": {
    "extends": ["react-app", "react-app/jest"]
  },
  "browserslist": {
    "production": [">0.2%", "not dead", "not op_mini all"],
    "development": [
      "last 1 chrome version",
      "last 1 firefox version",
      "last 1 safari version"
    ]
  },
  "devDependencies": {
    "@types/jest": "^27.5.0", // ts에서 단위 테스트 도구인 jest를 사용할 수 있다.
    "@types/node": "^17.0.32", // node.js에서 type 정의를 포함하고 있는 패키지이다.
    "@types/react": "^18.0.9", // react의 타입스크립트 버전이다.
    "@types/react-dom": "^18.0.3", // react-dom의 타입스크립트 버전이다.
    "@types/store": "^2.0.2", // store.js의 타입스크립트 버전이다.
    "@typescript-eslint/eslint-plugin": "^5.23.0",
    "@typescript-eslint/parser": "^5.23.0",
    "babel-eslint": "^10.1.0", // eslint 실행 시 사용할 Paser를 babel-eslint로 설정할 수 있다.
    "eslint": "^8.15.0", // eslint를 사용하기 위한 패키지이다.
    "eslint-config-airbnb": "^19.0.4", // airbnb의 스타일 가이드 코드 규칙 적용한다.
    "eslint-config-prettier": "^8.5.0", // eslint에서 prettier와 겹치거나 사용하지 않는 포매팅 기능을 끈다.
    "eslint-config-react": "^1.1.7", // react 프로젝트를 위해 맞춤화된 일련의 독창적인 규칙(모든 규칙 포함)을 적용시킨다.
    "eslint-config-react-app": "^7.0.1", // prettie와 eslint를 동시에 사용하기 위해 설치하며 이 패키지를 사용하면 non-style 룰만 포함되어 있기 때문에 별다른 설정없이 prettier를 같이 사용해도 문제가 없다.
    "eslint-plugin-flowtype": "^8.0.3", // 이 플러그인은 Flow 유형 모범 사례를 시행하는 권장 구성을 내보낸다. (어떤 역할의 플러그인인지 더 공부해봐야할 것 같다.)
    "eslint-plugin-import": "^2.26.0", // 이 플러그인은 ES2015+(ES6+) import/export 구문의 린트를 지원하고 파일 경로 및 가져오기 이름의 철자 오류 문제를 방지한다.
    "eslint-plugin-jsx-a11y": "^6.5.1", // ESLint 플러그인인 eslint-plugin-jsx-a11y는 JSX 내의 접근성 문제에 대해 즉각적인 AST 린팅 피드백을 제공한다.
    "eslint-plugin-prettier": "^4.0.0", // eslint에 prettier의 포매팅 기능을 추가한다.
    "eslint-plugin-react": "^7.29.4", // 리액트와 관련된 룰을 정의한 패키지이다.
    "eslint-plugin-react-hooks": "^4.5.0", // react hook의 두 가지 규칙인 React 함수 컴포넌트에서 Hook을 호출해야한다, Custom Hook에서 Hook을 호출해야한다는 규칙을 강제하는 플러그인이다.
    "eslint-plugin-testing-library": "^5.4.0", // 테스트 라이브러리로 테스트를 작성할 때 모범 사례를 따르고 일반적인 실수를 예상하는 ESLint 플러그인이다.
    "eslint-webpack-plugin": "^3.1.1", // eslint플러그인으로 JavaScript 코드에서 문제를 찾고 수정 하는 데 사용한다.
    "prettier": "^2.6.2", // prettier를 사용하기 위한 패키지이다.
    "sass": "^1.51.0", // sass를 사용하기 위한 패키지이다.
    "sass-loader": "^12.6.0", // sass/scss 파일을 로드하고 css로 컴파일한다.
    "style-loader": "^3.3.1", // css를 DOM에 삽입한다.
    "stylelint": "^14.8.2", // css,scss,less등 style 구문을 린팅하는 패키지이다.
    "stylelint-config-recess-order": "^3.0.0", // Recess 및 Bootstrap이 수행한 방식으로 CSS 속성을 정렬한다.
    "stylelint-config-standard-scss": "^3.0.0", // stylelint-config-standard 공유 구성을 확장하고 SCSS에 대한 규칙을 구성하며 stylelint-config-recommended-scss 공유 구성 확장한다.
    "stylelint-declaration-strict-value": "^1.8.0", // 변수($sass, namespace.$sass, @less, var(--cssnext), css-loader @value), 함수 또는 키워드(inherit, none, currentColor etc.), 색상(#fff, red, etc.) 또는 숫자, 단위((0, 1px, 100%, etc.)와 같은 사용자 정의 CSS 값 을 적용 하는 stylelint 플러그인이다.
    "typescript": "^4.6.4" // typescript를 사용하기 위한 패키지이다.
  }
}
```

9. api사용 시 환경 변수 .env 추가 후 필요에 따라 .gitignore, .prettierignore, .eslintignore 설정
10. 프로젝트 디렉토리 구조 설정
    <img width="1744" alt="study_POB_TIL_6_01" src="https://github.com/Yu-jae-min/Basic-concept/assets/85284246/a4dd2b3d-cfdb-468e-9704-f1123a4b08e9">

<br>

## # Takeaway

오늘은 그립 영화 무비 앱 프로젝트 초기 세팅을 진행하였다. 그립 영화 앱은 react + typescript 에 eslint + prettier + stylelint로 세팅하였다. 멘토이신 이준혁님께서 원티드 프리온보딩을 진행하시면서 항상 강조하시는 부분이 초기 세팅하는 부분이다. 주니어 개발자가 eslint와 preettier를 잘 세팅할 줄 안다면 훨씬 깔끔한 코드를 작성할 수 있다고 하셨다. 그래서 준혁님께서 추천해주신 옵션들을 참고하여 직접 세팅해보았다. 또한 각 패키지들과 플러그인들의 역할이 무엇인지 가볍게 살펴보았다. 아직 이해가지 않는 부분들이 몇 군데 있으나 이 부분들을 더욱 보완해서 공부해야할 것 같다. 이 프로젝트 외에도 프리온보딩 과정을 진행하며 남은 프로젝트가 많은데 여러번 반복해보며 프로젝트 초기 세팅을 잘하는 것에 익숙해져야겠다.
