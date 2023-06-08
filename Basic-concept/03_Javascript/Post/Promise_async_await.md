# **Promise, async & await**

## **# 프로미스(Promise)**

### **# 동기식 처리 모델과 비동기식 처리 모델**

동기식 처리 모델(Synchronous processing model)은 직렬적으로 태스크(task)를 수행한다. 즉, 태스크는 순차적으로 실행되며 어떤 작업이 수행 중이면 다음 태스크는 대기하게 된다. 예를 들어 서버에서 데이터를 가져와서 화면에 표시하는 태스크를 수행할 때, 서버에 데이터를 요청하고 데이터가 응답될 때까지 이후의 태스크들은 블로킹된다.

![javascript_Promise_async_await_01](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/0b2663af-652f-46c8-97cb-6be08c695cb9)

비동기식 처리 모델(Asynchronous processing model 또는 Non-Blocking processing model)은 병렬적으로 태스크를 수행한다. 즉, 태스크가 종료되지 않은 상태라 하더라도 대기하지 않고 즉시 다음 태스크를 실행한다. 예를 들어 서버에서 데이터를 가져와서 화면에 표시하는 태스크를 수행할 때, 서버에 데이터를 요청한 이후 서버로부터 데이터가 응답될 때까지 대기하지 않고(Non-Blocking) 즉시 다음 태스크를 수행한다. 이후 서버로부터 데이터가 응답되면 이벤트가 발생하고 이벤트 핸들러가 데이터를 가지고 수행할 태스크를 계속해 수행한다. 자바스크립트의 대부분의 DOM 이벤트와 Timer 함수(setTimeout, setInterval), Ajax 요청은 비동기식 처리 모델로 동작한다.

![javascript_Promise_async_await_02](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/78394e7a-12ed-46e0-b268-4177f0ab43d6)

자바스크립트에서 빈번하게 사용되는 비동기식 처리 모델은 요청을 병렬로 처리하여 다른 요청이 블로킹(blocking, 작업 중단)되지 않는 장점이 있다.

하지만 비동기 처리 모델은 실행 완료를 기다리지 않고 즉시 다음 태스크를 실행하므로(순서를 보장하지 않는다) 비동기 함수(비동기를 처리하는 함수) 내에서 처리 결과를 반환(또는 전역 변수에의 할당)하면 기대한 대로 동작하지 않는다.

즉, 비동기 처리 모델은 처리 순서를 보장하지 않기 때문에 처리 순서를 보장하기 작업이 필요하다. 그 중 하나의 전통적인 패턴으로 콜백 함수를 사용한다. 하지만 전통적인 콜백 패턴은 콜백 헬로 인해 가독성이 나쁘고 비동기 처리 중 발생한 에러의 처리가 곤란하며 여러 개의 비동기 처리를 한번에 처리하는 데도 한계가 있다.

<br>

### **# 콜백 패턴**

비동기 처리를 위해 콜백 패턴을 사용하면 처리 순서를 보장하기 위해 여러 개의 콜백 함수가 중첩(nesting)되어 복잡도가 높아지는 콜백 지옥(Callback Hell)이 발생하는 단점이 있다. 콜백 헬은 가독성을 나쁘게 하며 실수를 유발하는 원인이 된다.

```javascript
// 콜백 패턴의 문제점 1. : 콜백 지옥(Callback Hell)
const f1 = (callback) => {
  setTimeout(function () {
    console.log("1번 주문 완료");
    callback();
  }, 1000);
};

const f2 = (callback) => {
  setTimeout(function () {
    console.log("2번 주문 완료");
    callback();
  }, 3000);
};

const f3 = (callback) => {
  setTimeout(function () {
    console.log("3번 주문 완료");
    callback();
  }, 2000);
};

f1(function () {
  f2(function () {
    f3(function () {
      console.log("끝");
    });
  });
});
```

또한 가독성이 나빠진다는 문제와 함께 **에러 처리가 곤란하다**는 문제도 가지고 있다.

```javascript
// 콜백 패턴의 문제점 2. : 에러 처리의 한계
try {
  setTimeout(() => {
    throw new Error("Error!");
  }, 1000);
} catch (e) {
  console.log("에러를 캐치하지 못한다..");
  console.log(e);
}
```

try 블록 내에서 setTimeout 함수가 실행되면 1초 후에 콜백 함수가 실행되고 이 콜백 함수는 예외를 발생시킨다. 하지만 이 예외는 catch 블록에서 캐치되지 않는다.

비동기 처리 함수의 콜백 함수는 해당 이벤트(timer 함수의 tick 이벤트, XMLHttpRequest의 readystatechange 이벤트 등)가 발생하면 태스트 큐로 이동한 후 호출 스택이 비어졌을 때, 호출 스택으로 이동되어 실행된다. setTimeout 함수는 비동기 함수이므로 콜백 함수가 실행될 때까지 기다리지 않고 즉시 종료되어 호출 스택에서 제거된다. 이후 tick 이벤트가 발생하면 setTimeout 함수의 콜백 함수는 태스트 큐로 이동한 후 호출 스택이 비어졌을 때 호출 스택으로 이동되어 실행된다. 이때 setTimeout 함수는 이미 호출 스택에서 제거된 상태이다. 이것은 setTimeout 함수의 콜백 함수를 호출한 것은 setTimeout 함수가 아니다라는 것을 의미한다. setTimeout 함수의 콜백 함수의 호출자(caller)가 setTimeout 함수라면 호출 스택에 setTimeout 함수가 존재해야 하기 때문이다.

예외(exception)는 호출자(caller) 방향으로 전파된다. 하지만 위에서 살펴본 바와 같이 setTimeout 함수의 콜백 함수를 호출한 것은 setTimeout 함수가 아니다. 따라서 setTimeout 함수의 콜백 함수 내에서 발생시킨 에러는 catch 블록에서 캐치되지 않아 프로세스는 종료된다.

이러한 문제를 극복하기 위해 프로미스(Promise)가 제안되었다. Promise는 ES6에 정식 채택되어 IE를 제외한 대부분의 브라우저가 지원하고 있다. 프로미스는 전통적인 콜백 패턴이 가진 단점을 보완하며 비동기 처리 시점을 명확하게 표현할 수 있다는 장점이 있다.

<br>

### **# 프로미스(Promise)**

비동기 처리를 위한 프로미스(Promise)는 아래와 같이 new Promise 생성자를 통해 생성할 수 있다.

```javascript
// Promise 객체 생성
const pr = new Promise((resolve, reject) => {
  // code (콜백함수)
});

console.log(pr); // {state: ..., result: ...}
```

new Promise 생성자가 반환하는 프로미스(Promise) 객체는 프토토타입 인터널 슬롯과 함께 비동기 처리에 대한 상태 정보를 가지고 있다. state 프로퍼티와 result 프로퍼티로 구성되며 이 상태 정보를 객체로 반환한다.

반환되는 이 객체는 비동기 처리가 성공(fulfilled)하였는지 또는 실패(rejected)하였는지, 즉 프로미스 상태에 따라 프로퍼티의 value 값이 변하게 된다. 비동기 처리 수행되지 않은 상태에는 pending 상태이며 비동기 처리 후 비동기 처리가 성공하면 resolve 함수를 호출하게 되고 실패하면 reject 함수를 호출하게 된다.

- **default(초기) 상태** : {state: pending(대기), result: undefined}
- **resolve(성공) 호출 시** : {state: fulfilled(이행됨), result: value(resolve로 전달된 값)}
- **reject(실패) 호출 시** : {state: rejected(거부됨), result: error(reject로 전달된 값)}

아래 예시를 통해 Promise가 반환하는 객체를 확인해보자.

```javascript
const pr = new Promise((resolve, reject) => {
  resolve("resolve로 전달된 값");
  reject(new Error("reject로 전달된 값")); // 무시됨
});

console.log(pr); // {<fulfilled>: 'resolve로 전달된 값'}
```

![javascript_Promise_async_await_03](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/26887e7e-9271-4e23-a66b-aa867a3194c4)

<br>

### **# 프로미스의 후속 처리 메소드**

Promise로 구현된 비동기 함수는 Promise 객체를 반환하여야 한다. Promise로 구현된 비동기 함수를 호출하는 측(promise consumer)에서는 Promise 객체의 후속 처리 메소드(then, catch)를 통해 비동기 처리 결과 또는 에러 메시지를 전달받아 처리한다. Promise 객체는 상태를 갖는다고 하였다. 이 상태에 따라 후속 처리 메소드를 체이닝 방식으로 호출한다. Promise의 후속 처리 메소드는 아래와 같다.

<br>

#### **# then**

**then 메소드**는 두 개의 콜백 함수를 인자로 전달 받는다. 첫 번째 콜백 함수는 성공(fulfilled, resolve 함수가 호출된 상태) 시 호출되고 두 번째 함수는 실패(rejected, reject 함수가 호출된 상태) 시 호출된다. then 메소드는 Promise를 반환한다.

```javascript
// 프로미스 객체 생성
const pr = new Promise((res, rej) => {
  setTimeout(() => {
    res("OK");
  }, 3000);
});

// 프로미스 후속 처리 1. : then을 이용한 후속 처리
// 두 개의 콜백 함수를 인자로 받는다. 첫번째 인자는 resolve, 두번째 인자는 reject
pr.then(
  function (result) {
    console.log(result + " : 이행 되었을 때 실행");
  },
  function (err) {
    console.log(err + " : 거부 되었을 때 실행");
  }
);
```

<br>

#### **# catch**

**catch 메소드**는 예외(비동기 처리에서 발생한 에러와 then 메소드에서 발생한 에러)가 발생하면 호출된다. catch 메소드는 Promise를 반환한다. 정상적인 경우라면 catch는 절대 트리거 되지 않는다.

```javascript
// 프로미스 객체 생성
const pr = new Promise((res, rej) => {
  setTimeout(() => {
    rej("NOT OK");
  }, 3000);
});

// 프로미스 후속 처리 2. : catch를 이용한 에러 처리
pr.then(function (result) {
  console.log(result);
}).catch(function (err) {
  console.log(err);
});
```

catch 메서드를 모든 then 메서드를 호출한 이후에 호출하면 비동기 처리에서 발생한 에러(reject 함수가 호출된 상태)뿐만 아니라 then 메서드 내부에서 발생한 에러까지 모두 캐치할 수 있다.

또한 then 메서드에 두 번째 콜백 함수를 전달하는 것보다 catch 메서드를 사용하는 것이 가독성이 좋고 명확하다. 따라서 에러 처리는 then 메서드에서 하지 말고 catch 메서드를 사용하는 것을 권장한다.

<br>

#### **# finally**

**finally 메소드**는 Promise가 처리되면 이행되거나 거부되는지 여부에 관계없이 지정된 콜백 함수가 실행됩니다.

```javascript
// 프로미스 객체 생성
const pr = new Promise((res, rej) => {
  setTimeout(() => {
    res("OK");
  }, 3000);
});

// 프로미스 후속 처리 3. : 이행 거부에 상관없이 실행되는 finally
pr.then(function (result) {
  console.log("then이 실행되었습니다.");
})
  .catch(function (err) {
    console.log("catch가 실행되었습니다.");
  })
  .finally(function (result) {
    console.log("finally가 실행되었습니다.");
  });

// then이 실행되었습니다.
// finally가 실행되었습니다.
```

<br>

#### **# throw**

에러를 강제로 발생시켜야 경우(사용자 정의 예외)가 생길 때는 **throw** 키워드를 사용한다.
예외가 발생하면 현재 함수의 실행이 중지되고 (throw 이후의 명령문은 실행되지 않음), 제어 흐름은 콜스택의 첫 번째 catch 블록으로 전달된다. 호출자 함수 사이에 catch 블록이 없으면 프로그램이 종료된다.

또한 Error 객체와 함께 발생한 오류는 확장 할 때 스택 추적을 제공한다. 이를 통해 오류를 정확하게 발생시키는 유용한 정보를 얻을 수 있으며, 이는 코드 디버깅시 유용한 정보가 된다.

> **예외를 강제로 발생시키는 이유?**
>
> 객체를 잘못 사용하는 사용자에게 예외를 강제로 발생시켜서 사용자에게 주의를 줄 수도 있고 예외와 관련된 처리를 해달라고 부탁할 수도 있다.

<br>

### **# 프로미스 체이닝**

비동기 함수의 처리 결과를 가지고 다른 비동기 함수를 호출해야 하는 경우, 함수의 호출이 중첩(nesting)이 되어 복잡도가 높아지는 콜백 헬이 발생한다. 프로미스는 후속 처리 메소드를 체이닝(chainning)하여 여러 개의 프로미스를 연결하여 사용할 수 있다. 이로써 콜백 헬을 해결한다.

Promise 객체를 반환한 비동기 함수는 프로미스 후속 처리 메소드인 then이나 catch 메소드를 사용할 수 있다. 따라서 then 메소드가 Promise 객체를 반환하도록 하면(then 메소드는 기본적으로 Promise를 반환한다.) 여러 개의 프로미스를 연결하여 사용할 수 있다.

```javascript
new Promise((resolve, reject) => {
  setTimeout(() => resolve(10), 1000); // (*)
})
  .then((result) => {
    // (**)
    console.log(result); // 10
    return result * 2;
  })
  .then((result) => {
    // (***)
    console.log(result); // 20
    return result * 2;
  })
  .then((result) => {
    console.log(result); // 40
    return result * 2;
  });
```

프라미스 체이닝은 result가 then 메서드의 체인을 통해 전달된다는 점에서 착안한 아이디어이다.
위 예시는 아래와 같은 순서로 실행된다.

- 1초 후 최초 프라미스가 이행됩니다. – (\*)
- 이후 첫번째 .then 핸들러가 호출됩니다. –(\*\*)
- 2에서 반환한 값은 다음 .then 핸들러에 전달됩니다. – (\*\*\*)
- 이런 과정이 계속 이어집니다.

result가 핸들러 체인을 따라 전달되므로, 콘솔창에 1, 2, 4가 순서대로 출력된다.
이와 같이 프로미스를 연결하는 것을 프로미스 체이닝이라고 한다.

<br>

### **# 프로미스의 정적 메소드**

Promise는 주로 생성자 함수로 사용되지만 함수도 객체이므로 메소드를 갖을 수 있다. Promise 객체는 4가지 정적 메소드를 제공한다.

- Promise.resolve
- Promise.reject
- Promise.all
- Promise.race

<br>

#### **# Promise.resolve**

Promise.resolve 메소드는 인자로 전달된 값을 resolve하는 Promise를 생성한다.

```javascript
const resolvedPromise = Promise.resolve([1, 2, 3]);
resolvedPromise.then(console.log); // [ 1, 2, 3 ]
```

위 예제는 아래 예제와 동일하게 동작한다.

```javascript
const resolvedPromise = new Promise((resolve) => resolve([1, 2, 3]));
resolvedPromise.then(console.log); // [ 1, 2, 3 ]
```

<br>

#### **# Promise.reject**

Promise.reject 메소드는 인자로 전달된 값을 reject하는 Promise를 생성한다.

```javascript
const rejectedPromise = Promise.reject(new Error("Error!"));
rejectedPromise.catch(console.log); // Error: Error!
```

위 예제는 아래 예제와 동일하게 동작한다.

```javascript
const rejectedPromise = new Promise((resolve, reject) =>
  reject(new Error("Error!"))
);
rejectedPromise.catch(console.log); // Error: Error!
```

<br>

#### **# Promise.all**

**Promise.all 메소드**는 프로미스가 담겨 있는 배열 등의 이터러블을 인자로 전달 받는다. 그리고 전달받은 모든 프로미스를 병렬로 처리하고 그 처리 결과를 resolve하는 새로운 프로미스를 반환한다.

```javascript
const f1 = (message) => {
  console.log(message);
  return new Promise((res, rej) => {
    setTimeout(() => {
      res("1번 주문 완료");
    }, 1000);
  });
};

const f2 = (message) => {
  console.log(message);
  return new Promise((res, rej) => {
    setTimeout(() => {
      res("2번 주문 완료");
    }, 3000);
  });
};

const f3 = (message) => {
  console.log(message);
  return new Promise((res, rej) => {
    setTimeout(() => {
      res("3번 주문 완료");
    }, 2000);
  });
};
```

위와 같은 비동기 처리를 아래와 같이 프로미스 체이닝을 활용하여 호출한다.

```javascript
// Promise.all 사용 전
// 시작 -> 1번 주문 완료 -> 2번 주문 완료 -> 3번 주문 완료 -> 끝
f1()
  .then((res) => f2(res))
  .then((res) => f3(res))
  .then((res) => console.log(res))
  .catch((err) => {
    console.log(err);
  })
  .finally(() => {
    console.log("끝");
  });
```

위와 같은 경우의 함수 속도를 측정해보면 대략 6초 정도가 걸리는 것을 알 수 있다. 이럴 경우 Promise.all 메소드를 사용하여 병렬적으로 처리할 수 있다.

```javascript
// Promise.all 사용 후
// ['1번 주문 완료', '2번 주문 완료', '3번 주문 완료']
Promise.all([f1(), f2(), f3()]).then((res) => {
  console.log(res);
});
```

위와 같이 Promise.all 메소드를 사용하게 되면 병렬적으로 처리되어 3초 정도가 걸리는 것을 확인할 수 있다. 단 주의할 점은 반환하는 프로미스 중 하나라도 에러를 발생시키게 되면 가장 먼저 실패한 프로미스의 에러가 출력된다. 즉, 페이지 전부를 보여주거나 하나라도 에러 발생 시 페이지를 아예 보여주지 않는 경우의 사용할 수 있다.

<br>

#### **# Promise.race**

Promise.race 메소드는 Promise.all 메소드와 동일하게 프로미스가 담겨 있는 배열 등의 이터러블을 인자로 전달 받는다. 그리고 Promise.race 메소드는 Promise.all 메소드처럼 모든 프로미스를 병렬 처리하는 것이 아니라 가장 먼저 처리된 프로미스가 resolve한 처리 결과를 resolve하는 새로운 프로미스를 반환한다.

```javascript
Promise.race([f1(), f2(), f3()]).then((res) => {
  console.log(res); // 1번 주문 완료
});
```

위와 같이 race 메소드를 통해 호출한 경우 메소드의 이름에서 알 수 있듯이 경주와 같이 동작한다. 즉, 제일 처음 반환하는 프로미스를 반환하고 실행을 종료하게 된다. 용량이 큰 이미지들을 로딩하는데 그 중에 하나라도 완료되면 그 이미지를 보여줄 때 이런 방식을 사용하고는 한다.

<br>

## **# async & await**

ES8에서 추가된 async와 await라는 특별한 문법을 사용하면 프라미스를 좀 더 편하게 사용할 수 있다.

<br>

### **# async**

**async**는 function 앞에 위치한다. function 앞에 async를 붙이면 해당 함수는 항상 프로미스를 반환한다. 프러미스가 아닌 값을 반환하더라도 이행 상태의 프로미스(resolved promise)로 값을 감싸 이행된 프로미스가 반환되도록 한다.

```javascript
async function getName() {
  return "Mike";
}

console.log(getName()); // {<fulfilled>: 'Mike'}
getName().then((name) => console.log(name)); // Mike
```

위와 같이 프로미스를 반환하기 때문에 프로미스 메서드를 체이닝으로 연결하여 사용할 수 있다.

```javascript
async function getName() {
  return Promise.resolve("Tom");
}

getName().then((name) => console.log(name)); // Tom
```

또한 만약 함수가 반환하는 값이 프로미스라면 그 값을 사용한다.

<br>

### **# await**

**await**는 async 함수 내부에서만 사용되며 프로미스가 처리(settled)될 때까지 함수 실행을 기다리게 만든다. 여기서 기다린다는 의미는, 모든 작업이 종료된다는 의미가 아니라 내가 사용할 결과값이 나올 때까지 기다린다는 의미다. 메인 작업들은 멈추지 않고 await을 포함하고 있는 함수만 일시정지된다. 그 후 promise가 처리되면 그 결과와 함께 실행이 재개된다. promise가 처리되길 기다리는 동안엔 엔진이 다른 일(다른 스크립트를 실행, 이벤트 처리 등)을 할 수 있기 때문에, CPU 리소스가 낭비되지 않는다.

```javascript
function getName(name) {
  return new Promise((res, rej) => {
    setTimeout(() => {
      res(name);
    }, 1000);
  });
}

async function showName() {
  const result = await getName("Mike");
  console.log(result);
}

console.log("시작");
showName(); // 프로미스가 처리될 때까지 완료 후 Mike 출력
```

또한 에러 처리의 경우 아래와 같이 try catch문을 활용한다. try 내부의 함수를 먼저 실행하고 에러 발생 시 catch 내부의 함수를 실행하게 된다.

```javascript
function getName(name) {
  return new Promise((res, rej) => {
    setTimeout(() => {
      rej(new Error("err..."));
    }, 1000);
  });
}

async function showName() {
  try {
    const result = await getName("Mike");
    console.log(result);
  } catch (e) {
    console.log(e);
  }
}

console.log("시작");
showName(); // Error: err...
```

Promise.all과 같은 promise 메서드도 사용 가능하다.

```javascript
const f1 = (message) => {
  console.log(message);
  return new Promise((res, rej) => {
    setTimeout(() => {
      res("1번 주문 완료");
    }, 1000);
  });
};

const f2 = (message) => {
  console.log(message);
  return new Promise((res, rej) => {
    setTimeout(() => {
      res("2번 주문 완료");
    }, 3000);
  });
};

const f3 = (message) => {
  console.log(message);
  return new Promise((res, rej) => {
    setTimeout(() => {
      res("3번 주문 완료");
    }, 2000);
  });
};

async function order() {
  console.log("시작");
  try {
    const result = await Promise.all([f1(), f2(), f3()]);
    console.log(result);
  } catch (e) {
    console.log(e);
  }
  console.log("종료");
}
order(); // 시작 -> ['1번 주문 완료', '2번 주문 완료', '3번 주문 완료'] -> 종료
```

<br>

---

<br>

참고자료

- <a href="https://poiemaweb.com/es6-promise" target='_blank'>프로미스</a>
- <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Promise" target='_blank'>Promise</a>
- <a href="https://www.youtube.com/watch?v=4_WLS9Lj6n4" target='_blank'>자바스크립트 중급 강좌</a>
- <a href="https://inpa.tistory.com/entry/JS-%F0%9F%93%9A-%EC%98%88%EC%99%B8-%EC%B2%98%EB%A6%AC" target='_blank'>자바스크립트 - 예외 처리(Exception) 정리</a>
- <a href="https://ko.javascript.info/async-await" target='_blank'>async와 await</a>
- <a href="https://learnjs.vlpt.us/async/02-async-await.html" target='_blank'>02. async/await</a>
- <a href="https://poiemaweb.com/es6-generator" target='_blank'>제너레이터와 async/await</a>
