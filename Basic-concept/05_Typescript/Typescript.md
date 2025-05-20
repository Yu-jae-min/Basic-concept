## # Typescript

<br>

### # **타입스크립트**

<br>

- 타입스크립트란?

  타입스크립트는 자바스크립트의 슈퍼셋이다. 자바스크립트 기본 문법에 타입스크립트의 문법을 추가한 언어이다. 자바스크립트는 동적 언어로 런타임에 타입을 결정하는데 이와 같은 문제를 보완하고자 컴파일 타임에 타입을 결정하는 타입스크립트를 사용할 수 있다.

<br>

- 타입스크립트의 사용 이유

  (1) 안정성 향상 : 타입스크립트는 코드에 목적을 명시하고 목적에 맞지 않는 타입의 변수나 함수들에서 에러를 발생시켜 버그를 사전에 제거하여 안정성이 향상된다.

  (2) 더 나은 개발자 경험 제공 : 객체의 필드나 함수의 매개변수로 들어오는 값이 무엇인지 파악이 용이하고 변수의 이름뿐만 아니라 그 데이터의 타입까지 알 수 있게 해주기 때문에 코드 작성을 좀 더 쉽고 직관적이게 만들어준다.

  (3) 메모리 절약 : 타입의 유무로 메모리 사용량이 달라지기 때문에 메모리를 절약할 수 있다.

  (4) 크로스브라우징 문제 해결 : 타입스크립트는 컴파일 과정에서 ES6+ 문법들을 ES5(또는 ES3)로 바꿔주기 때문에 Babel의 도움 없이 구브라우저에도 대응 가능하다.

<br>

### # 타입스크립트 기본 타입

1. String : 문자열

   ```ts
   let str: string = "hi";
   ```

2. Number : 숫자

   ```ts
   let num: number = 10;
   ```

3. Boolean : 진위 값

   ```ts
   let isLoggedIn: boolean = false;
   ```

4. Array : 배열

   ```ts
   let arr: number[] = [1, 2, 3];
   let arr: Array<number> = [1, 2, 3]; // 제네릭 사용
   ```

5. Tuple : 고정 된 길이와 각 요소의 타입이 지정되어 있는 배열, 만약 정의하지 않은 타입, 인덱스로 접근할 경우 오류 발생

   ```ts
   let arr: [string, number] = ["hi", 10];
   arr[1].concat("!"); // 에러
   arr[5] = "hello"; // 에러
   ```

6. Enum : 특정 값(상수)들의 집합, 인덱스 번호로도 접근할 수 있고 다른 문자열로 지정할 수도 있다. 일반 객체와 차이점은 수정이 불가하다.

   ```ts
   enum Avengers {
     Capt = 2,
     IronMan,
     Thor,
   }
   let hero: Avengers = Avengers[2]; // Capt
   let hero: Avengers = Avengers[4]; // Thor, IronMan과 Thor에 자동으로 인덱스 번호가 부여된다.
   ```

7. Any : 모든 타입에 대해서 허용

   ```ts
   let str: any = "hi";
   let num: any = 10;
   let arr: any = ["a", 2, true];
   ```

8. Void : 변수에 사용 시 undefined와 null만 할당을 허용하고, 함수에 사용 시 반환 값이 없다는 것을 의미하는 타입

   ```ts
   let unuseful: void = undefined;
   function notuse(): void {
     console.log("sth");
   }
   ```

9. Null

10. Undefined

11. Never : 함수의 끝에 절대 도달하지 않는다는 의미를 지닌 타입, 예시로 무한 루프를 발생시키는 함수나 항상 에러를 반환하는 함수의 출력 값으로 지정할 수 있다. void와의 차이점은 void는 null 혹은 undefined 값의 반환을 허용한다는 것이고 never는 never 이외에는 허용하지 않는다.

```ts
// 항상 오류 발생
function invalid(message: string): never {
  throw new Error(message);
}

// 무한 루프
function infiniteAnimate(): never {
  while (true) {
    infiniteAnimate();
  }
}
```

<br>

### # 함수 타입

- 타입스크립트에서는 함수의 인자를 모두 필수 값으로 간주한다. 따라서, 함수의 매개변수를 설정하면 undefined나 null이라도 인자로 넘겨야하며 컴파일러에서 정의된 매개변수 값이 넘어 왔는지 확인한다. 달리 말하면 정의된 매개변수 값만 받을 수 있고 추가로 인자를 받을 수 없다는 의미이다.

  ```ts
  function sum(a: number, b: number): number {
    return a + b;
  }
  sum(10, 20); // 30
  sum(10, 20, 30); // error, too many parameters
  sum(10); // error, too few parameters
  ```

<br>

### # 인터페이스 타입

- 여러 타입을 합쳐서 사용하는 타입, AND 연산자와 같이 모든 타입을 만족해야한다.

- 옵셔널(?) 속성을 활용하여 특정 타입을 옵셔널하게 사용할 수 있다.

- extends 키워드를 사용해 기존 인터페이스를 확장(상속) 하여 새로운 인터페이스를 만들 수 있다.

- 인터페이스끼리 합칠 때는 & (교차 타입, Intersection Type)를 사용하여 여러 타입을 동시에 만족하도록 할 수 있다.

- 선언 병합이 가능하다.

  ```ts
  interface Person {
    name: string;
    age: number;
  }

  interface Employee {
    employeeId: string;
    department?: string; // 옵셔널 속성
  }

  // Person과 Employee 타입을 모두 만족하는 타입 만들기 (교차 타입)
  type Staff = Person & Employee;

  const staffMember: Staff = {
    name: "Alice",
    age: 30,
    employeeId: "E123",
    // department는 선택적이라 안 적어도 됨
  };
  ```

- 기타 예시

  ```ts
  // 예제1: 기본 사용
  interface Example {
    name: string;
  }

  // 예제2: 옵션 속성 활용
  interface Example {
    name: string;
    hop?: number;
  }

  // 예제3: 읽기 전용 속성 활용
  interface Example {
    readonly name: string;
  }

  let myBeer: Example = {
    brand: "Belgian Monk",
  };
  myBeer.brand = "Korean Carpenter"; // error!

  // 비슷한 활용 : 읽기 전용 배열
  let arr: ReadonlyArray<number> = [1, 2, 3];
  arr.splice(0, 1); // error
  arr.push(4); // error
  arr[0] = 100; // error

  // 예제4: 정의되지 않은 속성 활용
  interface Example {
    brand?: string;
    [propName: string]: any;
  }

  // 예제5: 클래스 타입 활용
  interface Example {
    beerName: string;
    nameBeer(beer: string): void;
  }

  class myBeer implements Example {
    beerName: string = "Baby Guinness";
    nameBeer(b: string) {
      this.beerName = b;
    }
    constructor() {}
  }

  // 예제6: 인터페이스 확장
  interface Person {
    name: string;
  }
  interface Drinker {
    drink: string;
  }
  interface Developer extends Person, Drinker {
    skill: string;
  }
  let fe = {} as Developer;
  fe.name = "josh";
  fe.skill = "TypeScript";
  fe.drink = "Beer";

  // 예제7: 선언 병합
  interface Person {
    name: string;
  }

  // 같은 이름의 인터페이스가 또 선언됐지만, 타입스크립트가 두 선언을 합쳐서 처리
  interface Person {
    age: number;
  }

  const p: Person = {
    name: "Lee",
    age: 30, // age 프로퍼티가 정상적으로 인식됨
  };
  ```

<br>

### # 클래스에서의 타입스크립트 활용

- readonly : 클래스의 속성에 readonly 키워드를 사용하면 아래와 같이 접근만 가능합니다.

  ```ts
  class Developer {
    readonly name: string;
    constructor(theName: string) {
      this.name = theName;
    }
  }
  let john = new Developer("John");
  john.name = "John"; // error! name is readonly.
  ```

- Accessor : 타입스크립트는 객체의 특정 속성의 접근과 할당에 대해 제어할 수 있다.

  ```ts
  class Developer {
    private name: string;

    get name(): string {
      // getter는 클래스 필드에 접근할 때마다 클래스 필드의 값을 조작하는 행위가 필요할 때 사용한다. 참조 시에 호출된다.
      return this.name;
    }

    set name(newValue: string) {
      // setter는 클래스 필드에 값을 할당할 때마다 클래스 필드의 값을 조작하는 행위가 필요할 때 사용한다. 클래스 필드에 값 할당 시 호출된다.
      if (newValue && newValue.length > 5) {
        throw new Error("이름이 너무 깁니다");
      }
      this.name = newValue;
    }
  }
  const josh = new Developer();
  josh.name = "Josh Bolton"; // Error
  josh.name = "Josh";
  ```

- Abstract Class : 추상 클래스(Abstract Class)는 인터페이스와 비슷한 역할을 하면서도 조금 다른 특징을 갖고 있다. 추상 클래스는 특정 클래스의 상속 대상이 되는 클래스이며 좀 더 상위 레벨에서 속성, 메서드의 모양을 정의한다.

  ```ts
  abstract class Developer {
    abstract coding(): void; // 'abstract'가 붙으면 상속 받은 클래스에서 무조건 구현해야 함
    drink(): void {
      console.log("drink sth");
    }
  }

  class FrontEndDeveloper extends Developer {
    coding(): void {
      // Developer 클래스를 상속 받은 클래스에서 무조건 정의해야 하는 메서드
      console.log("develop web");
    }
    design(): void {
      console.log("design web");
    }
  }
  const dev = new Developer(); // error: cannot create an instance of an abstract class
  const josh = new FrontEndDeveloper();
  josh.coding(); // develop web
  josh.drink(); // drink sth
  josh.design(); // design web
  ```

<br>

### # 제네릭(Generic) 타입

- 제네릭이란?

  함수, 클래스, 인터페이스 등에서 타입을 고정하지 않고 사용하는 시점에 타입을 외부로부터 주입받아 사용하는 문법이다.

  ```ts
  function getText<T>(text: T): T {
    return text;
  }

  getText<string>("hi");
  getText<number>(10);
  getText<boolean>(true);
  ```

- 제네릭 타입의 제한 (제네릭 타입 프로퍼티 접근 시 문제점)

  제네릭 타입은 구체적인 타입이 정해지지 않았기 때문에, 타입에 따라 존재하지 않을 수도 있는 프로퍼티나 메서드에 접근하려고 하면 컴파일 에러가 발생한다. 그렇기 때문에 타입 가드 혹은 제네릭 타입에 제약(extends)를 걸어 타입 범위를 좁혀야한다.

  ```ts
  // ❌ 에러: T 타입이 어떤 타입인지 알 수 없기 때문에 .length 사용 불가
  function logText<T>(text: T): T {
    console.log(text.length); // Error
    return text;
  }

  // ✅ 제네릭 타입에 배열 제약을 걸면 length 사용 가능
  function logText<T>(text: T[]): T[] {
    console.log(text.length);
    return text;
  }

  // ✅ 제네릭에 string을 확장한 제약을 걸면 .length 사용 가능
  function logText<T extends { length: number }>(text: T): T {
    console.log(text.length);
    return text;
  }
  ```

- 제네릭 인터페이스

  ```ts
  // 함수 자체에 제네릭 정의
  interface GenericLogTextFn {
    <T>(text: T): T;
  }

  function logText<T>(text: T): T {
    return text;
  }

  let myString: GenericLogTextFn = logText; // OK
  ```

  ```ts
  interface GenericLogTextFn<T> {
    (text: T): T;
  }

  const logText: GenericLogTextFn<string> = (text) => text;
  ```

- 제네릭 클래스

  ```ts
  class GenericMath<T> {
    pi: T;
    sum: (x: T, y: T) => T;

    constructor(pi: T, sum: (x: T, y: T) => T) {
      this.pi = pi;
      this.sum = sum;
    }
  }

  const math = new GenericMath<number>(3.14, (a, b) => a + b);
  ```

<br>

### # 타입 추론

- 타입 추론이란?

  타입 추론이란 타입을 따로 정의하지 않아도 자동으로 타입을 추론해주는 기능을 말한다. 정적 타입 언어의 단점은 타입을 정의하는데 많은 시간과 노력이 들기 때문에 생산성이 저하될 수 있다는 점이다.
  하지만 타입스크립트의 경우 타입 추론을 제공하기 때문에 필요한 경우에만 타입 정의를 할 수 있어 코드를 덜 작성하면서도 같은 수준의 타입 안정성을 유지할 수 있다. (but 명시적인 타입 선언이 안전하다)
  타입 추론은 몇 개의 표현식을 참고하여 최적의 공통 타입(베스트 커먼 타입 알고리즘)을 추론하거나 코드가 작성되는 흐름을 기반으로 타입(문맥상의 타이핑)을 추론한다.

- 타입스크립트의 타입 추론 방법

  1. 최적의 공통 타입(Best Common Type)

     여러 표현식이 동시에 존재하는 경우, 모든 표현식에 공통으로 적용 가능한 가장 일반적인 타입을 찾아서 추론한다.

     ```ts
     let x = [0, 1, null]; // let x: (number | null)[]
     ```

  2. 문맥상의 타이핑(Contextual Typing)

     문맥상의 타이핑(타입 결정)은 코드의 위치(문맥)를 기준으로 일어난다.

     ```ts
     // 예제1 : Window.onmousedown 함수의 타입을 사용하여 오른쪽에 할당된 함수 표현식의 타입을 추론하고 mouseEvent의 프로퍼티가 아닌 kangaroo는 에러가 발생한다.
     window.onmousedown = function (mouseEvent) {
       console.log(mouseEvent.button); //<- OK
       console.log(mouseEvent.kangaroo); //<- Error!
     };

     // 예제2 : 변수에 할당되므로 함수가 명시적으로 any타입으로 추론되기 때문에 오류가 발생하지 않는다.
     const handler = function (uiEvent) {
       console.log(uiEvent.button); //<- OK
     };
     ```

<br>

### # 타입 가드

- 타입 가드란?

  타입 가드는 타입의 범위가 넓을 때 컴파일러가 타입을 추론할 수 있도록 타입의 범위를 축소시키는 것을 말한다.

- 타입 가드 방법

  - 1. typeof 활용

    ```ts
    function printValue(value: string | number) {
      if (typeof value === "string") {
        console.log(value.toUpperCase()); // value는 string으로 좁혀짐
      } else {
        console.log(value.toFixed(2)); // value는 number로 좁혀짐
      }
    }
    ```

  - 2. instanceof 활용

    ```ts
    class Dog {
      bark() {
        console.log("멍멍!");
      }
    }

    class Cat {
      meow() {
        console.log("야옹!");
      }
    }

    function speak(animal: Dog | Cat) {
      if (animal instanceof Dog) {
        animal.bark(); // Dog로 좁혀짐
      } else {
        animal.meow(); // Cat으로 좁혀짐
      }
    }
    ```

  - 3. in 연산자 활용

    ```ts
    type Developer = { name: string; skill: string };
    type Designer = { name: string; tool: string };

    function introduce(person: Developer | Designer) {
      if ("skill" in person) {
        console.log(
          `${person.name}는 개발자입니다. 사용하는 기술은 ${person.skill}`
        );
      } else {
        console.log(
          `${person.name}는 디자이너입니다. 사용하는 도구는 ${person.tool}`
        );
      }
    }
    ```

  - 4. 사용자 정의 커스텀

    ```ts
    // pet is Fish 형태의 반환 타입이 핵심. 이게 사용자 정의 타입 가드
    // x is Y 문법 : 조건을 만족하면 타입스크립트가 자동으로 타입 좁힘, as 보다 안전하다. 조건에 부합하지 않는 경우 타입을 좁히지 않음.
    type Fish = { swim: () => void };
    type Bird = { fly: () => void };

    function isFish(pet: Fish | Bird): pet is Fish {
      return (pet as Fish).swim !== undefined;
    }

    function move(pet: Fish | Bird) {
      if (isFish(pet)) {
        pet.swim(); // pet은 Fish로 좁혀짐
      } else {
        pet.fly(); // pet은 Bird로 좁혀짐
      }
    }
    ```

  - 5. 타입 단언 활용

    ```ts
    // 방법1: as(타입 단언)을 활용
    function someFunc(val: string | number, isNumber: boolean) {
      if (isNumber) {
        (val as number).toFixed(2);
        isNaN(val as number);
      } else {
        (val as string).split("");
        (val as string).toUpperCase();
        (val as string).length;
      }
    }
    ```

### # 타입 단언

- 타입 단언이란?

  타입 단언은 타입을 추론하지 못한 타입을 강제로 지정할 때 사용한다. as 키워드를 통해 타입 단언을 할 수 있다. 주의할 점은 잘못된 타입 단언은 컴파일 에러는 없지만 런타임 에러를 유발할 수 있으므로, 반드시 해당 값이 실제로 해당 타입임을 확신할 수 있을 때만 사용해야 한다. (ex API response type)

- 예시

  ```ts
  // 예시 1. 변수의 복사
  // 이 코드에서 a는 처음 선언 시 타입이 명시되지 않았기 때문에 any로 추론되고, b도 a의 타입을 그대로 따라가 any로 추론
  var a;
  a = 20;
  var b = a as number;
  ```

  ```ts
  // 예시 2. DOM API 조작
  // getElementById는 HTMLElement | null을 반환하기 때문에 null이 아님을 확신할 수 있는 경우 as HTMLDivElement를 사용하여 타입 단언
  const myDiv = document.getElementById("my-div") as HTMLDivElement;
  myDiv.innerText = "Hello";
  ```

<br>

### # 타입 호환성

- 타입 호환성이란?

  타입 호환성이란 구조적 타이핑(Structural Typing) 기반으로 두 타입 간 멤버 구조를 비교해 한쪽 타입을 다른 쪽에 할당 가능한지를 결정하는 규칙이다.

- 예시

  - 인터페이스 호환성 예시

    요구 타입을 모두 만족하는 경우 가능

    ```tsx
    interface A {
      x: number;
    }

    interface B {
      x: number;
      y: number;
    }

    // A는 B로 할당 불가능 (요구 타입에 부족함)
    const a: A = { x: 1 };
    const b: B = a; // 오류! Property 'y'가 필요합니다.

    // B는 A로 할당 가능 (요구 타입을 모두 가지고 있음)
    const bb: B = { x: 1, y: 2 };
    const aa: A = bb;
    ```

  - 함수 호환성 예시

    매개변수가 적어지는건 가능, 함수 호출 시 매개변수를 초과하여 전달하여도 무시할 수 있으므로

    ```tsx
    type FuncA = (x: number) => number;
    type FuncB = (x: number, y: number) => number;

    // FuncA는 FuncB로 할당 가능 (필요한 매개변수가 적어지는건 가능)
    // fnB(10, 20) 시 내부적으로 fnA가 호출되어 x=10, y=20은 무시됨
    let fnA: FuncA = (x) => x * 2;
    let fnB: FuncB = fnA; // 가능

    // FuncB는 FuncA로 할당 불가능  (필요한 매개변수가 많아지는건 불가능)
    let fnBB: FuncB = (x, y) => x + y;
    let fnAA: FuncA = fnBB;
    ```

  - 제네릭의 호환성 예시

    기본적으로 호환되지 않음, any 제외

    ```tsx
    interface Box<T> {
      value: T;
    }

    let box1: Box<number>;
    let box2: Box<string>;

    box1 = box2; // 오류! 제네릭의 타입이 다르기 때문에 호환되지 않습니다.

    // 하지만 제네릭 타입이 실제로 사용되는 경우에는 호환됩니다.
    let numBox: Box<number>;
    let anyBox: Box<any>;

    numBox = anyBox; // 가능, 'any' 타입은 모든 타입과 호환됩니다.
    ```

<br>

### # 타입 별칭(타입 앨리어스)

- 타입 별칭은 특정 타입에 별칭을 부여하여 새로운 타입을 만들어내는 타입이다. 인터페이스와 같은 객체 타입, 원시 타입, 유니온, 튜플, 함수 타입 등 모든 타입을 별칭으로 만들 수 있다.

  ```ts
  // 예시1 : 타입 앨리어스, 빈 객체를 Person 타입으로 지정
  type Person = {
    name: string;
    age?: number;
  };

  const person = {} as Person;
  person.name = "Lee";
  person.age = 20;
  person.address = "Seoul"; // Error

  // 예시2 : 원시, 유니온, 함수 타입 등
  type A = string;
  type B = string | number;
  type C = (name: string, age: number) => string;
  ```

  ```ts
  type A = { x: number };
  type B = { y: string };

  // 교차 타입을 사용해서 확장한 새로운 타입 만들기
  type C = A & B;

  const c: C = { x: 1, y: "hello" };
  ```

<br>

### # 타입 별칭과 인터페이스 차이

1. 확장성

   타입 별칭은 직접적으로 확장(extends) 및 선언 병합이 불가능하고 인터페이스는 확장(extends) 및 선언 병합이 가능하다. 단 타입 별칭은 교차 선언을 통해 간접적으로 확장은 가능하다.

2. 생성 타입 형태

   타입 별칭은 객체 형태의 타입 외에도 원시 타입 혹은 값, 유니온 타입, 튜플 타입 등을 지정할 수 있고 인터페이스는 객체 형태의 타입을 지정한다.

3. 프리뷰

   타입 별칭은 프리뷰 시 타입 전체 구조를 보여주고 인터페이스는 타입 명을 보여준다.

<br>

### # 유틸리티 타입

- 유틸리티 타입이란?

  유틸리티 타입은 이미 정의해 놓은 타입을 변환하여 새로운 타입을 만들 때 사용하는 타입이다. 유틸리티 타입의 종류는 매우 다양하지만 대표적으로 파셜, 오밋, 픽 등의 타입이 있다.

- 자주 사용되는 유틸리티 타입

  - 파셜(Partial)

    파셜 타입은 특정 타입의 부분 집합을 만족하는 타입을 정의한다. 파셜을 사용하면 옵셔널 속성의 남발을 막을 수 있다.

    ```ts
    interface Address {
      email: string;
      address: string;
    }

    type MayHaveEmail = Partial<Address>;
    const me: MayHaveEmail = {}; // 가능
    const you: MayHaveEmail = { email: "test@abc.com" }; // 가능
    const all: MayHaveEmail = { email: "capt@hero.com", address: "Pangyo" }; // 가능
    ```

  - 픽(Pick)

    픽 타입은 특정 타입에서 몇 개의 속성을 선택하여 타입을 정의한다.

    ```ts
    interface Hero {
      name: string;
      skill: string;
    }

    const human: Pick<Hero, "name"> = {
      name: "스킬이 없는 사람",
    };
    ```

  - 오밋(Omit)

    오밋 타입은 픽과 반대로 특정 타입에서 지정된 속성만 제거한 타입을 정의한다.

    ```ts
    interface AddressBook {
      name: string;
      phone: number;
      address: string;
      company: string;
    }

    const phoneBook: Omit<AddressBook, "address"> = {
      name: "재택근무",
      phone: 12342223333,
      company: "내 방",
    };

    const chingtao: Omit<AddressBook, "address" | "company"> = {
      name: "중국집",
      phone: 44455557777,
    };
    ```

<br>

### # 맵드 타입

- 맵드 타입이란?

  맵드 타입(Mapped Types)은 keyof 연산자와 in 키워드를 이용해 기존 객체 타입의 모든 속성을 변환하여 새로운 타입을 생성하는 타입이다.
  in 연산자를 활용하여 순회하며 in 연산자를 기준으로 좌항은 일반 변수(순회 대상이 순차적으로 반복 할당), 우항은 순회 대상(유니온 타입)이다.

- 예시

  - 예제1 : 기본 문법

    ```ts
    { [ P in K ] : T }
    { [ P in K ] ? : T }
    { readonly [ P in K ] : T }
    { readonly [ P in K ] ? : T }
    ```

  - 예제2: 유니온 타입 기반 객체 정의

    ```ts
    type Heroes = "Hulk" | "Capt" | "Thor";
    type HeroAges = { [K in Heroes]: number };

    const ages: HeroAges = {
      Hulk: 33,
      Capt: 100,
      Thor: 1000,
    };
    ```

  - 예제3 : Partial 직접 구현

    ```ts
    // keyof T: Person의 키인 age, name을 유니온 타입으로 추출 -> "age" | "name"
    // T[K]: T의 K 키에 해당하는 속성의 타입
    type Subset<T> = {
      [K in keyof T]?: T[K];
    };

    interface Person {
      age: number;
      name: string;
    }

    const ageOnly: Subset<Person> = { age: 23 };
    const nameOnly: Subset<Person> = { name: "Tony" };
    const ironman: Subset<Person> = { age: 23, name: "Tony" };
    const empty: Subset<Person> = {};
    ```

<br>

### # 유니온 타입, 인터섹션 타입

- 유니온 타입 (|)

  유니온 타입이란 OR 연산자와 같이 A이거나 B다를 의미하는 타입이다.

  ```ts
  let value: string | number;

  value = "hello"; // ✅ 가능
  value = 123; // ✅ 가능
  value = true; // ❌ 오류 - boolean은 해당 안 됨
  ```

  ```ts
  interface A {
    x: number;
    y: number;
  }

  interface B {
    x: number;
    z: number;
  }

  type AB = A | B;

  const obj: AB = { x: 10, y: 20 }; //  A 혹은 B 타입으로 초기화 되어야 함, 해당 코드는 A 타입으로 초기화

  // 공통된 속성 x만 접근 가능
  console.log(obj.x); // OK
  console.log(obj.y); // OK
  console.log(obj.z); // Error
  ```

- 인터섹션 타입 (&)

  인터섹션 타입은 AND 연산자와 같이 A와 B를 모두 만족하는 하나의 타입이다. 인터섹션 타입으로 인터페이스 타입 혹은 타입 별칭을 연결하는 경우 두 타입이 가진 모든 속성에 접근이 가능하다.

  ```ts
  type User = { name: string };
  type Admin = { role: string };

  type AdminUser = User & Admin;

  const person: AdminUser = {
    name: "Alice",
    role: "manager",
  };
  ```

  ```ts
  interface A {
    x: number;
    y: number;
  }

  interface B {
    z: string;
  }

  type AB = A & B;

  const obj: AB = {
    x: 10,
    y: 20,
    z: "hello",
  };

  console.log(obj.x); // 10
  console.log(obj.z); // hello
  ```

<br>

### # 타입스크립트 데코레이터

- 데코레이터란?

  데코레이터가 붙은 클래스, 메소드(함수) 및 변수 등에 데코레이터에서 정의된 기능이 동작하는 것을 의미한다.

- 메소드 데코레이터 : 메서드의 기능을 확장하는 역할을 한다.

  ```js
  function hello(constructFn: Function) {
    constructFn.prototype.hello = function () {
      console.log("hello");
    };
  }

  // 클래스 데코레이터
  @hello
  class Person {}

  const person = new Person();
  person.hello();
  ```

- 프로퍼티 데코레이터 : 클래스의 프로퍼티 선언에 사용되는 프로퍼티 데코레이터는 두 개의 인자를 받는다. 그리고 프로퍼티 데코레이터에서 Property Descriptor 형식으로 객체를 반환할 때는, 프로퍼티에 적용이 된다.

  (1) static 프로퍼티라면 클래스의 생성자 함수, 인스턴스 프로퍼티라면 클래스의 prototype 객체

  (2) 프로퍼티 이름

  ```js
  const writable =
    (canBeWritable: boolean) =>
    (target: any, propName: string): any => {
      return {
        writable: canBeWritable,
      };
    };

  class Person {
    @writable(false)
    name: string = "moaikang";
    constructor() {}
  }

  const person = new Person();
  person.name = "zz";
  console.log(person.name);
  ```

- 파라미터 데코레이터 : 파라미터 안에 들어가는 파라미터 데코레이터는 3개의 인자를 받는다.

  (1) static 메서드의 파라미터 데코레이터라면 클래스의 생성자 함수, 인스턴스의 메서드라면 prototype 객체

  (2) 파라미터 데코레이터가 적용된 메서드의 이름

  (3) 메서드 파라미터 목록에서의 index

  ```js
  const writable =
    (canBeWritable: boolean) =>
    (target: any, propName: string): any => {
      return {
        writable: canBeWritable,
      };
    };

  class Person {
    @writable(false)
    name: string = "moaikang";
    constructor() {}
  }

  const person = new Person();
  person.name = "zz";
  console.log(person.name);
  ```

<br>

### # 타입스크립트 실행 과정

- 2-4번은 타입 스크립트 컴파일러(TSC)가 수행, 5-7번은 브라우저, NodJS, 기타 자바스크립트 엔진 같은 자바스크립트 런타임이 실행

  1. 소스 코드 작성 : 프로그래머가 타입스크립트 코드 작성

  2. 파싱 : 타입스크립트 컴파일러가 소스 코드를 읽어 추상 문법 트리(AST)로 변환

  3. 타입 검사 : 타입스크립트 컴파일러가 추상 문법 트리(AST)를 기반으로 타입 규칙을 검사하여 오류 체크

  4. 트랜스 파일 : 타입 정보는 제거하고 타입스크립트 코드를 순수한 자바스크립트로 변환

  5. 런타임(자바스크립트 엔진) 실행 준비 : 브라우저, Nodejs 기타 자바스크립트 엔진이 코드를 받아서 다시 파싱 -> 추상 구문 트리 생성

  6. 바이트 코드 변환 및 최적화 : 자바스크립트 엔진 내부에서 추상 구문 트리를 바이트 코드 등 저수준 코드로 변환

  7. 코드 실행 : 런타임이 바이트 코드를 실행한다.

<br>

### # keyof와 typeof

- keyof 타입

  타입(인터페이스, 객체 타입 등)의 모든 프로퍼티 키를 유니온 타입으로 추출한다.

  ```ts
  interface BrandInterface {
    Nike: "nike";
    Adidas: "adidas";
    Puma: "puma";
  }

  let type: keyof BrandInterface; // 마우스 오버 시 : 'Nike' | 'Adidas' | 'Puma'
  ```

- typeof 변수명

  변수나 객체, 함수 등의 값(value) 에 대해 그 타입을 추출한다. 즉, typeof 변수명은 해당 변수의 타입을 가져오는 역할이다.

  ```ts
  enum BrandEnum {
    Nike = "nike",
    Adidas = "adidas",
    Puma = "puma",
  }

  let type1: typeof BrandEnum = {
    Nike: BrandEnum.Nike,
    Adidas: BrandEnum.Adidas,
    puma: BrandEnum.puma,
  }; // let type1: typeof BrandEnum
  let type2: keyof BrandEnum; // number | typeof Symbol.iterator | "toString" | "charAt" ...
  let type3: keyof typeof BrandEnum; // let type3: "Nike" | "Adidas" | "Puma"
  ```

  ```ts
  // 객체의 경우에도 enum과 똑같이 작동하는 것을 볼 수 있었다. 즉 enum 객체로 변환 되기 때문이다. typeof으로 타입을 얻은 뒤 keyof로 추출한다.
  const object = {
    Nike: "nike",
    Adidas: "adidas",
    Puma: "puma",
  };

  let type: keyof typeof object;
  ```

<br>

### # any와 Generic 차이

1. 반환 타입 유추

   함수의 any타입의 경우 함수의 반환 타입을 알기 어렵지만 제네릭 타입의 경우 호출 시 명시적으로 타입을 선언해줌으로서 반환 타입을 유추하기 쉽다.

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

2. 프로퍼티 체크 유무

   함수의 any 타입은 매개변수의 프로퍼티를 체크하지 않고 제네릭 타입은 프로퍼티를 체크하므로 타입가드가 필요하기 때문에 사전에 에러를 방지할 수 있다.

   ```ts
   function AnyReturnFunc(arg: any): any {
     return arg.length; // 에러가 발생하지 않는다.
   }

   function GenericReturnFunc<T>(arg: T): T {
     return arg.length; // 제네릭 함수는 무슨 타입이 올지 모르기 때문에 length 프로퍼티를 사용할 수 없다는 에러 메시지를 노출한다.
   }
   ```

<br>

### # 타입스크립트 설정 파일 (tsconfig.json)

- tsconfig.json은 타입스크립트 컴파일러의 설정을 정의하는 파일이다. 이 파일에서 컴파일 옵션, strict 모드 설정, 타입 검사 규칙, 출력 경로 등 다양한 컴파일 규칙과 동작 방식을 지정할 수 있다.

- tsconfig.json에서 strict: true 설정

  기본적으로 타입스크립트에서는 null과 undefined가 모든 타입의 하위 타입으로 간주되어서, 아무 변수나 null 또는 undefined 값을 가질 수 있다. strictNullChecks가 켜지면, null과 undefined는 오직 그 타입으로 명시적으로 지정된 변수에만 할당 가능하다. 즉, string 타입 변수에는 null이나 undefined를 할당할 수 없고, string | null 처럼 유니언 타입으로 명시해야만 할당할 수 있다.

  ```ts
  let name: string = "Alice";
  name = null; // 오류! 'null'은 'string' 타입에 할당 불가

  let age: number | null = null; // 가능: null을 포함하는 유니언 타입
  ```

  ```ts
  interface User {
    id: number;
    name: string;
    email?: string | null; // 이메일은 optional이고 null일 수도 있다
  }

  async function fetchUser(id: number): Promise<User | null> {
    const response = await fetch(`/api/user/${id}`);
    if (!response.ok) return null;
    return await response.json();
  }

  async function showUser(id: number) {
    const user = await fetchUser(id);

    // strict 모드라면 user가 null일 수 있으니 반드시 체크해야 한다
    if (user) {
      console.log(user.name);
      // email도 null일 수 있으니 옵셔널 체이닝으로 접근 가능
      console.log(user.email ?? "이메일 정보 없음");
    } else {
      console.log("유저를 찾을 수 없습니다.");
    }
  }
  ```

<br><br><br>
