# [Javascript] for문에서의 비동기 함수 사용 시 스코프와 클로저

<br>

## 1. for문에서의 비동기 함수 사용 시 스코프와 클로저

아래와 같이 for문에서 비동기 함수 사용 시 초기 값을 var를 사용하느냐 혹은 let 사용하느냐에 따라 출력 값이 달라질 수 있다. 이러한 결과가 나타나는 이유는 블록 레벨 스코프와 함수 레벨 스코프의 차이 때문이다.

```javascript
// 예시1 : var 사용
const functionScope = () => {
  for (var i = 0; i < 3; i++) {
    setTimeout(() => {
      console.log(i);
    }, 100);
  }
};

// 예시2: var 사용 + 클로저
const closerFunction = () => {
  for (var i = 0; i < 3; i++) {
    ((x) => {
      setTimeout(() => {
        console.log(x);
      }, 100);
    })(i);
  }
};

// 예시3: let 사용
const blockScope = () => {
  for (let i = 0; i < 3; i++) {
    setTimeout(() => {
      console.log(i);
    }, 100);
  }
};

functionScope(); // 3이 3번 찍힌다.
closerFunction(); // 0, 1, 2가 순서대로 찍힌다.
blockScope(); // 0, 1, 2가 순서대로 찍힌다.
```

해당 코드를 풀이해보자.

<br>
<br>

## 2. 코드 풀이

### 2-1. functionScope에서 var 사용 시 3이 3번 찍히는 이유

for문 동작 시 setTimeout을 호출하게 되면 콜스택에 함수컨텍스트를 생성한 후 바로 제거하여 웹API 백그라운드에서 처리된다. 이 때 콜스택에 컨텍스트는 바로 제거되기 때문에 백그라운드에서 처리가 완료되기 전 다음 반복문으로 들어가게 된다. 이 후 setTimeout은 비동기적으로 처리되기 때문에 나머지 for문도 방금과 같은 작업을 반복하게 된다. 그렇기 때문에 setTimeout이 타이머에 의해 웹API에서 처리되기 전 for문은 이미 마지막 루프까지 마친 상태이기 때문에 i값은 3이 되고 웹API에서 처리 후 큐를 통해 실행되는 setTimeout 콜백 함수들은 이 i값을 참조하게 되어 모두 3을 반환한다.

```javascript
// 예시1 : var 사용
const functionScope = () => {
  for (var i = 0; i < 3; i++) {
    setTimeout(() => {
      console.log(i);
      debugger;
    }, 100);
  }
};

functionScope(); // 3이 3번 찍힌다.

// 예시1을 풀어보면 아래와 같이 동작하는 것 같다. 디버그를 통해 확인해보면 동일하게 동작한다. 개발자 도구 우측에 클로저 필드를 보면 i가 저장되있음을 확인할 수 있다.
// var는 함수 레벨 스코프로 동작하기 때문에 아래와 같이 함수 코드 블럭 내에 존재하는 것과 같다. 그렇기 때문에 반복되는 콜백이 바라보는 값은 동일해진다.
const functionScopeTest = () => {
  var i = 0;

  {
    setTimeout(() => {
      console.log(i);
      debugger;
    }, 100);
    i++;
  }

  {
    setTimeout(() => {
      console.log(i);
      debugger;
    }, 100);
    i++;
  }

  {
    setTimeout(() => {
      console.log(i);
      debugger;
    }, 100);
    i++;
  }
};

functionScopeTest(); // 3이 3번 찍힌다.
```

<br>

### 2-2. closerFunction에서 var 사용 시 클로저를 통한 해결

클로저란 간단하게 말하면 내부함수가 외부함수에 접근할 수 있는 것을 말한다. 기존에 동작시키던 방식과 다르게 즉시 실행 함수를 생성한 후 파라미터로 i값을 전달하는 방식을 활용한다. 이런 방식을 활용하게 되면 콜스택에 즉시 실행 함수 컨텍스트가 쌓이고 먼저 사라지더라도 웹API에 콜백으로 넘긴 setTimeout 콜백 함수 스코프에 파라미터로 넘긴 x의 값을 기억하고 있기 때문에 해당 x값을 참조하여 최신 값을 유지할 수 있다.

```javascript
// 예시2: var 사용 + 클로저
const closerFunction = () => {
  for (var i = 0; i < 3; i++) {
    ((x) => {
      setTimeout(() => {
        console.log(x);
        debugger;
      }, 100);
    })(i);
  }
};

closerFunction(); // 0, 1, 2가 순서대로 찍힌다.

// 예시2를 풀어보면 아래와 같이 동작하는 것 같다. 디버그를 통해 확인해보면 동일하게 동작한다. 개발자 도구 우측에 클로저 필드를 보면 i가 저장되있음을 확인할 수 있다.
// var는 함수 레벨 스코프로 동작하기 때문에 아래와 같이 함수 코드 블럭 내에 존재하는 것과 같다. 하지만 즉시실행함수의 인자로 i를 받아 클로저 함수를 사용하여 해결할 수 있다.
const closerFunctionTest = () => {
  var i = 0;

  {
    ((x) => {
      setTimeout(() => {
        console.log(x);
        debugger;
      }, 100);
    })(i);
    i++;
  }

  {
    ((x) => {
      setTimeout(() => {
        console.log(x);
        debugger;
      }, 100);
    })(i);
    i++;
  }

  {
    ((x) => {
      setTimeout(() => {
        console.log(x);
        debugger;
      }, 100);
    })(i);
    i++;
  }
};

closerFunctionTest(); // 0, 1, 2가 순서대로 찍힌다.
```

<br>

### 2-3. blockScope에서 let 사용 시 0,1,2가 순서대로 찍히는 이유

예를 들어 functionScope()와 같이 var를 사용한 경우 var는 함수 레벨 스코프를 가지기 때문에 for 루프마다 새로운 스코프를 만들어내는 것이 아닌 functionScope 내부에 하나의 스코프로만 존재하게 된다. 그렇기 때문에 for 루프마다 동일한 참조를 바인딩해서 사용하게 되는 것이다. 반면 blockScope()와 같이 let을 사용한 경우 let은 블록 레벨 스코프를 가지기 때문에 for 루프마다 새로운 스코프를 만들어낸다. i가 0인 스코프, 1인 스코프, 2인 스코프 ... 등등으로 만들어내게 되고 이 각 루프마다 만들어지는 새로운 스코프를 참조하게 되므로 서로 다른 참조를 하게 되어 동일한 값이 출력되지 않게 된다. 아래 두 개의 함수가 동일하게 동작하는 것을 알 수 있다.

```javascript
// 예시3: let 사용
const blockScope = () => {
  for (let i = 0; i < 3; i++) {
    setTimeout(() => {
      console.log(i);
      debugger;
    }, 100);
  }
};

blockScope(); // 0, 1, 2가 순서대로 찍힌다.

// 예시3을 풀어보면 아래와 같이 동작하는 것 같다. 디버그를 통해 확인해보면 동일하게 동작한다. 개발자 도구 우측에 블럭 필드를 보면 i가 저장되있음을 확인할 수 있다.
// 아마도 setTimeout은 즉시호출함수라 호출과 동시에 환경을 기억하게 되고 그 때 기억해놓은 스코프에 블록스코프인 i값을 저장해두는 것이 아닌가 싶다!
const blockScopeTest = () => {
  {
    let i = 0;

    setTimeout(() => {
      console.log(i);
      debugger;
    }, 100);
  }

  {
    let i = 1;

    setTimeout(() => {
      console.log(i);
      debugger;
    }, 100);
  }

  {
    let i = 2;

    setTimeout(() => {
      console.log(i);
      debugger;
    }, 100);
  }
};

blockScopeTest(); // 0, 1, 2가 순서대로 찍힌다.
```

<br>
