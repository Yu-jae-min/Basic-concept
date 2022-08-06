## # Typescript

<br>

### # **타입스크립트**

<br>

- 타입스크립트란?

  타입스크립트는 자바스크립트의 슈퍼셋이다. 자바스크립트 기본 문법에 타입스크립트의 문법을 추가한 언어이다.

<br>

- 타입스크립트의 사용 이유

  (1) 안정성 향상과 자동완성 등 개발 편리성 향상 : 타입스크립트는 코드에 목적을 명시하고 목적에 맞지 않는 타입의 변수나 함수들에서 에러를 발생시켜 버그를 사전에 제거한다. 또한 코드 자동완성이나 실행 전 피드백을 제공하여 작업과 동시에 디버깅이 가능해 생산성을 높일 수 있다.

  (2) 더 나은 개발자 경험 : 객체의 필드나 함수의 매개변수로 들어오는 값이 무엇인지 파악이 용이하고 변수의 이름뿐만 아니라 그 데이터의 타입까지 알 수 있게 해주기 때문에 코드 작성을 좀 더 쉽고 직관적이게 만들어준다.

  (3) 메모리 절약 : 타입의 유무로 메모리 사용량이 달라지기때문에 메모리를 절약할 수 있다.

  (4) 크로스브라우징 문제 해결 : 타입스크립트는 컴파일 과정에서 ES6+ 문법들을 ES5(또는 ES3)로 바꿔주기 때문에 Babel의 도움 없이 구브라우저에도 대응 가능하다.

<br>

- 타입스크립트 유니온 타입과 인터섹션 타입의 차이점에 대해 설명해달라

  유니온 타입은 자바스크립트의 OR 연산자(||)와 같이 A이거나 B인 경우를 나타내는 타입이고 인터섹션 타입은 AND 연산자(&)를 이용해 여러 개의 타입을 하나로 합치는 방식이며 A와 B를 모두 만족해야하는 것과 같이 모든 타입을 만족하는 하나의 타입이다.

<br>

### # **타입스크립트 데코레이터**

<br>

- 데코레이터란?

  데코레이터가 붙은 클래스, 메소드(함수) 및 변수 등에 데코레이터에서 정의된 기능이 동작하는 것을 의미한다.

<br>

- 메소드에서의 데코레이터

  ```js
  function todo(target: any, prop: string, desc: PropertyDescriptor) {
    let originMethod = desc.value;
    desc.value = function (...args: any[]) {
      console.log("2. 함수 동작전 : " + prop);
      let result = originMethod.apply(this, args);
      console.log("4. 함수 동작후 : " + prop);
      return result;
    };
  }

  class Task {
    @todo
    runTask(arg: any): any {
      console.log("3.함수 동작 : " + arg);
      return "끝";
    }
  }

  let task = new Task();
  console.log("1. 클래스 생성 후 함수 호출 시작 ");
  let result = task.runTask("param");
  console.log("5. 결과 : " + result);

  // 결과는 1-> 2-> 3-> 4-> 5 순으로 콘솔에 찍힌다.
  ```

<br>

- 변수에서의 데코레이터

  ```js
  function SetDefaultValue(numberA: number, numberB: number) {
    return (target: any, propertyKey: string | symbol) => {
      const addNumber = numberA * numberB;
      let value = 0;
      Object.defineProperty(target, propertyKey, {
        //PropertyDescriptor에 대한 재 정의
        get() {
          return value + addNumber;
        },
        set(newValue: any) {
          value = newValue;
        },
      });
    };
  }

  class DataDefaultType {
    @SetDefaultValue(10, 20)
    num: number;
  }

  const test = new DataDefaultType();
  test.num = 30;
  console.log(`num is 30, 결과 : ${test.num}`);
  test.num = 130;
  console.log(`num is 130, 결과 : ${test.num}`);

  // 결과는 num is 30, 결과 : 230 -> num is 130, 결과 : 330 순으로 콘솔에 찍힌다.
  ```

<br>

### # **타입스크립트가 실행되는 과정**

<br>

- 2~4번은 TSC가 수행, 5~7번은 브라우저, NodJS, 기타 자바스크립트 엔진 같은 자바스크립트 런타임이 실행

  (1) 소스 코드 작성 by 프로그래머

  (2) 타입스크립트 소스 코드를 파싱하여 AST (추상문법트리)로 변환

  (3) 타입 검사기가 AST를 확인 (여기서 타입 검사가 이루어짐)

  (4) 컴파일러가 AST를 bytecode가 아닌 JavaScript로 변환한다.

  (5) JavaScript 소스를 AST로 변환

  (6) AST -> 바이트코드

  (7) 런타임이 바이트코드를 평가

<br>

### # **keyof와 typeof**

- keyof `example` : `example`의 모든 프로퍼티의 키값을 union 형태로 반환

<br>

- typeof `example` : `example`(변수/함수등)의 type을 반환

<br>

- 예제

  ```ts
  // 예제1 : enum
  enum BrandEnum {
    Nike = "nike",
    Adidas = "adidas",
    Puma = "puma",
  }

  let type1: typeof BrandEnum = {
    Nike: BrandEnum.Nike,
    Adidas: BrandEnum.Adidas,
    puma: BrandEnum.puma,
  }; // 마우스 오버 시 : let type1: typeof BrandEnum
  let type2: keyof BrandEnum; // 마우스 오버 시 : let type2: number | typeof Symbol.iterator | "toString" | "charAt" ...
  let type3: keyof typeof BrandEnum; // 마우스 오버 시 : let type3: "Nike" | "Adidas" | "Puma"
  ```

  type1은 마우스를 올려보면 typeof BrandEnum가 찍힌다. enum은 객체로 변환되기 때문에 typeof를 사용하게 되면 그냥 그 객체 자체가 type이 되어버려 똑같이 사용해야만 한다. 그럼 이 typeof 를 했을 때 만들어진 type이 interface와 비슷하다고 생각된다.
  type2의 마우스를 올려보면 객체의 프로퍼티들이 찍히는걸 볼 수 있다. Brand가 Object이기 때문에 나오는 것이다.
  type3은 typeof Brand가 enum 객체 그 자체이고 그것의 key들을 뽑아냈기 때문에 key값이 유니온으로 반환된다.

  ```ts
  // 예제2 : interface
  interface BrandInterface {
    Nike: "nike";
    Adidas: "adidas";
    Puma: "puma";
  }

  let type: keyof BrandInterface; // 마우스 오버 시 : 'Nike' | 'Adidas' | 'Puma'
  ```

  이런식으로 작성하고 type에 마우스를 올려보면 아까 위와 똑같이 'Nike' | 'Adidas' | 'Puma'로 나오는것을 확인할 수 있다.
  즉, enum의 keyof typeof는 interface의 keyof와 똑같다고 볼 수 있을 것 같다. enum은 객체이기 때문에 keyof만 했을 때는 객체의 key들이 나오고 keyof typeof를 했을 때 원하는 값이 나왔다. interface는 객체가 아니기 때문에 keyof만 했을 때도 바로 원하는 값이 나온다.

  ```ts
  // 예제3 : 객체
  const object = {
    Nike: "nike",
    Adidas: "adidas",
    Puma: "puma",
  };

  let type: keyof typeof object;
  ```

  객체의 경우에도 enum과 똑같이 작동하는 것을 볼 수 있었다. 즉 enum 객체로 변환 되기 때문이다.

<br>

### # **any와 Generic 차이**

<br>

(1) 반환 타입 유추 : 함수의 any타입의 경우 함수의 반환 타입을 알기 어렵지만 제네릭 타입의 경우 호출 시 명시적으로 타입을 선언해줌으로서 반환 타입을 유추하기 쉽다.

```ts
// any 타입
function AnyReturnFunc(arg: any): any {
  return arg;
}

let numVar = AnyReturnFunc(123); // number 타입의 값인 123을 전달하였지만, 무슨 타입을 return 받는지 유추하기 어려움
let strVar = AnyReturnFunc("ABC"); // // number 타입의 값인 123을 전달하였지만, 무슨 타입을 return 받는지 유추하기 어려움

// Generic 타입
function GenericReturnFunc<T>(arg: T): T {
  return arg;
}

let numVar = GenericReturnFunc<number>(123); // 명시적인 타입 선언 사용, 반환 값을 유추할 수 있다.
```

(2) 프로퍼티 체크 : 함수의 any 타입은 매개변수의 프로퍼티를 체크하지 않고 제네릭 타입은 프로퍼티를 체크하므로 타입가드가 필요하기 때문에 사전에 에러를 방지할 수 있다.

```ts
function AnyReturnFunc(arg: any): any {
  return arg.length; // 에러가 발생하지 않는다.
}

function GenericReturnFunc<Type>(arg: Type): Type {
  return arg.length; // 제네릭 함수는 무슨 타입이 올지 모르기 때문에 length 프로퍼티를 사용할 수 없다는 에러 메시지를 노출한다.
}
```

<br>
