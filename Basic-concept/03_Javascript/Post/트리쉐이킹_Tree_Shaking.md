# **[javascript] 트리 쉐이킹 (Tree Shaking)**

## **1. 트리 쉐이킹이란?**

트리쉐이킹… 웹팩에서도 찾아볼 수 있고 네이밍에서도 알 수 있듯이 나무를 흔들어 필요없는 나뭇잎들을 떨어뜨린다는 뜻이다. 즉, 불필요한 코드를 제거하여 번들 사이즈나 시간을 줄이는 작업을 얘기한다. 즉 성능의 이점을 얻을 수 있다.

[Tree Shaking | 웹팩](https://webpack.kr/guides/tree-shaking/)

그럼 트리쉐이킹은 어떻게 할까?

```jsx
// Import only some of the utilities!
import { unique, implode, explode } from "array-utils";
```

ES6에서 정의한 표준 모듈 시스템으로 `export` , `import` 를 사용하여 의존성 모듈을 가져와 사용할 수 있다. 위와 같이 사용할 수 있는데 `import`를 통해 필요한 패키지만 가져와 사용하고 있다. 어렵게 생각할 것 없이 이게 트리 쉐이킹이다.

<br>
<br>

## **2. 트리 쉐이킹 고려사항**

### **2-1. 트리 쉐이킹 가능여부 확인**

트리쉐이킹을 하기에 앞서 우선 패키지를 파헤쳐보아야한다. 예를 들어 특정 컴포넌트 내부에서 아래와 같이 `import`로 utils 파일 내부에 패키지를 가져와 사용하고 있다고 가정해보자.

```jsx
// 특정 컴포넌트 내부
import * as utils from "../../utils/utils";

if (this.state.sortBy === "model") {
  json = simpleSort(json, "model", this.state.sortOrder);
} else if (this.state.sortBy === "type") {
  json = simpleSort(json, "type", this.state.sortOrder);
} else {
  json = simpleSort(json, "manufacturer", this.state.sortOrder);
}
```

위와 같이 코드를 작성하는 경우 utils 파일 내부에 있는 모든 코드를 utils 네임스페이스에 저장한다는 것이다.
그런데 만약 utils 파일 내부에 있는 코드가 1000줄 이상이라면 어떨까?

```jsx
// utils.js
export const simpleSort = function(arr, key, order = "asc") {
  if (Array.isArray(arr) === true) {
    return arr.sort((a, b) => {
      if (order === "asc") {
        return a[key].localeCompare(b[key]);
      } else {
        return b[key].localeCompare(a[key]);
      }
    });
  }

  return false;
};

export const uasort = function(inputArr, sorter) {
  var valArr = [];
  var k = "";
  var i = 0;
  var populateArr = {};

  if (typeof sorter === "string") {
    sorter = this[sorter];
  } else if (Object.prototype.toString.call(sorter) === "[object Array]") {
    sorter = this[sorter[0]][sorter[1]];
  }

  for (k in inputArr) {
    if (inputArr.hasOwnProperty(k)) {
      valArr.push([k, inputArr[k]]);
    }
  }

  valArr.sort((a, b) => {
    return sorter(a[1], b[1]);
  })

  for (i = 0; i < valArr.length; i++) {
    populateArr[valArr[i][0]] = valArr[i][1];
  }

  return populateArr;
};

...

export const uksort = function(inputArr, sorter) {
  var tmpArr = {};
  var keys = [];
  var i = 0;
  var k = "";
  var populateArr = {};

  if (typeof sorter === "string") {
    sorter = this.window[sorter];
  }

  for (k in inputArr) {
    if (inputArr.hasOwnProperty(k)) {
      keys.push(k);
    }
  }

  try {
    if (sorter) {
      keys.sort(sorter);
    } else {
      keys.sort();
    }
  } catch (e) {
    return false;
  }

  for (i = 0; i < keys.length; i++) {
    k = keys[i];
    tmpArr[k] = inputArr[k];
  }

  for (i in tmpArr) {
    if (tmpArr.hasOwnProperty(i)) {
      populateArr[i] = tmpArr[i];
    }
  }

  return populateArr;
};
```

위와 같이 utils 파일 내부에 있는 패키지가 여러 개가 있다고 해보자. 이 때 utils 파일 내부에 있는 모든 코드를 가져오는 것이 잘못된 것은 아니다. 하지만 필요한 모듈만 가져와 사용하는 것이 아닐 수 있는 것이다.

위 예시를 보았을 때 현재 utils 파일을 import 하고 있는 컴포넌트 내부에서 utils 파일 내부에 있는 여러 패키지 중 `simpleSort` 한 가지만 사용하고 있으므로 이것은 웹 성능을 최적화 시키는 데에 있어 효율적이지 못하다.

위 코드는 아래와 같이 수정할 수 있다.

```jsx
// 특정 컴포넌트 내부
import { simpleSort } from "../../utils/utils";

if (this.state.sortBy === "model") {
  json = simpleSort(json, "model", this.state.sortOrder);
} else if (this.state.sortBy === "type") {
  json = simpleSort(json, "type", this.state.sortOrder);
} else {
  json = simpleSort(json, "manufacturer", this.state.sortOrder);
}
```

이와 같이 트리쉐이킹을 적용하기 전 사용 중인 패키지를 확인하여 트리쉐이킹이 가능한 지 확인해볼 수 있다.

<br>

### **2-2. Babel로 ES6 모듈이 CommonJS 모듈로 변환되는 것 막기**

바벨은 크로스 브라우징 이슈를 해결하기 위해 사용하는 트랜스파일러이다.
바벨을 통해 ES6+의 자바스크립트 코드는 하위 버전으로 변환하여 크로스 브라우징 이슈를 해결할 수 있다.
하지만 바벨 사용으로 인해 트리쉐이킹이 어려워질 수 있다고 한다.

만약 [babel-preset-env](https://babeljs.io/docs/plugins/preset-env/)를 사용한다면, 이 모듈이 ES6+ 자바스크립트 코드를 자동으로 commonjs 변환해준다. 즉, `import`를 `require`로 바꿔주기도 한다. 이는 훌륭한 기능이지만, 트리 쉐이킹 관점에서는 그렇지 못하다. 트리쉐이킹 관점에서 commonjs의 문제점은 웹팩이 어떤 모듈이 사용중인지 아닌지를 판단하여 제거하기가 어렵다는 것이다. 이를 위해 `.babelrc`에서 `commonjs`로 변환하지 못하도록 설정을 추가해 줘야 한다.

```
{
  "presets": [
    ["env", {
      "modules": false
    }]
  ]
}

```

`"modules": false`를 지정하면, babel이 우리가 원하는 대로 동작하게 되어 디펜던시를 분석하고 사용되지 않는 디펜던시를 제거할 수 있다. 또한 웹팩은 코드를 광범위하게 호환되는 형식으로 변환하므로, 이 프로세스는 호환성 문제를 일으키지 않는다.

<br>

### **2-3. 사이드 이펙트 고려하기**

트리 쉐이킹 시 사이드 이펙트도 고려해야한다. 아래 예제는 실행에 대한 사이드 이펙트이다.

```jsx
let fruits = ["apple", "orange", "pear"];

console.log(fruits); // (3) ["apple", "orange", "pear"]

const addFruit = function (fruit) {
  fruits.push(fruit);
};

addFruit("kiwi");

console.log(fruits); // (4) ["apple", "orange", "pear", "kiwi"]
```

`addFruit` 함수는 `fruits` 배열을 변경할 때 사이드 이펙트를 발생시킨다.
즉 `addFruit` 함수는 호출 될 때 `addFruit` 함수 스코프 외부에 있는 `fruits` 배열을 변경시킨다.
사이드 이펙트는 ES6 모듈에도 적용되며, 트리 쉐이킹의 컨텍스트에서 문제가 된다.
그렇기 때문에 예측 가능한 입력을 가지고 동일하게 함수의 스코프 밖의 어떤 것도 변경하지 않으면서 예측 가능한 결과를 반환하는 모듈이 안전하게 트리 쉐이킹을 할 수 있는 디펜던시이다.

webpack에서 고려해야 할 부분은, 프로젝트의 `package.json` 파일에서 `"sideEffects": false`로 설정하면 패키지와 디펜던시들이 사이드 이펙트를 발생하지 않는다는 것이다.

```jsx
{
  "name": "webpack-tree-shaking-example",
  "version": "1.0.0",
  "sideEffects": false
}
```

또한 선택적으로, 사이드 이펙트의 영향을 받지 않을 특정 파일들을 지정할 수도 있다.

```jsx
{
  "name": "webpack-tree-shaking-example",
  "version": "1.0.0",
  "sideEffects": [
    "./src/utils/utils.js"
  ]
}
```

<br>
<br>

## **3. 트리 쉐이킹이 안된다..?!**

위 고려사항을 적용했음에도 불구하고 트리 쉐이킹이 적용되지 않는 경우가 있다. 예를 들어, [Lodash](https://lodash.com/)가 트리 쉐이킹이 잘 동작하지 않는 이상한 경우에 해당된다. 이유는 Lodash 설계 방식 때문이며 이를 해결하기 위해서 오래된 표준 [lodash](https://www.npmjs.com/package/lodash) 대신 [lodash-es](https://www.npmjs.com/package/lodash-es)를 설치하고 다른 디펜던시를 쉐이킹하기 위해 조금 다른 구문("cherry-picking"이라고도 한다)을 사용하여 해결할 수 있다.

```jsx
// 설정이 잘 되어있어도 lodash 모든 것들을 가져온다.
import { sortBy } from "lodash";

// sortBy 경로에서 가져온다.
import sortBy from "lodash-es/sortBy";
```

만약 일관되게 `import` 구문을 사용하고 싶다면 표준 `lodash` 패키지를 사용 *할 수 있다*. [babel-plugin-lodash](https://github.com/lodash/babel-plugin-lodash)를 설치하고 Babel 설정 파일에 플러그인을 추가하여 `import` 구문을 사용하면서 사용하지 않는 모듈들을 제거할 수 있다. 실행한 라이브러리가 트리 쉐이킹에 반응하지 않는다면, ES6 구문을 사용하여 메서드를 내보내는지 확인해야한다. 만약 CommonJS 형식(예: `module.exports`)으로 내보내고 있다면, 해당 코드는 트리 쉐이킹을 할 수 없다. 가끔 몇몇 플러그인들은 CommonJS 모듈을 위한 트리 쉐이킹 기능을 제공하기도 하지만 확실한 트리 쉐이킹을 위해서는 ES6 모듈을 사용해야한다.

<br>
<br>

## **# 레퍼런스**

- https://web.dev/reduce-javascript-payloads-with-tree-shaking/#go_shake_some_trees
