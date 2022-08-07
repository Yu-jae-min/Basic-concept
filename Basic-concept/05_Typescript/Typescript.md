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

### # 타입스크립트 기본 타입

<br>

(1) String : 문자열

```ts
let str: string = "hi";
```

(2) Number : 숫자

```ts
let num: number = 10;
```

(3) Boolean : 진위 값

```ts
let isLoggedIn: boolean = false;
```

(4) Array : 배열

```ts
let arr: number[] = [1, 2, 3];
let arr: Array<number> = [1, 2, 3]; // 제네릭 사용
```

(5) Tuple : 고정 된 길이와 각 요소의 타입이 지정되어 있는 배열, 만약 정의하지 않은 타입, 인덱스로 접근할 경우 오류 발생

```ts
let arr: [string, number] = ["hi", 10];
arr[1].concat("!"); // 에러
arr[5] = "hello"; // 에러
```

(6) Enum : 특정 값(상수)들의 집합, 인덱스 번호로도 접근할 수 있고 인덱스를 변경할 수도 있다.

```ts
enum Avengers {
  Capt = 2,
  IronMan,
  Thor,
}
let hero: Avengers = Avengers[2]; // Capt
let hero: Avengers = Avengers[4]; // Thor, IronMan과 Thor에 자동으로 인덱스 번호가 부여된다.
```

(7) Any : 모든 타입에 대해서 허용

```ts
let str: any = "hi";
let num: any = 10;
let arr: any = ["a", 2, true];
```

(8) Void : 변수에 사용 시 undefined와 null만 할당을 허용하고, 함수에 사용 시 반환 값이 없다는 것을 의미하는 타입

```ts
let unuseful: void = undefined;
function notuse(): void {
  console.log("sth");
}
```

(9) Null

(10) Undefined

(11) Never : 함수의 끝에 절대 도달하지 않는다는 의미를 지닌 타입

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

<br>

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

<br>

- 여러타입을 합쳐서 사용하는 타입, AND연산자와 같이 인터페이스 타입을 활용하는 경우 모든 타입을 만족해야한다. 하지만 옵션 속성(?)을 이용하여 해결할 수 있다. 또한 확장도 가능하다.

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
  ```

<br>

### # 클래스에서의 타입스크립트 활용

<br>

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

<br>

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

<br>

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

<br>

- 제네릭이란?

  제네릭(Generic) 재사용을 목적으로 함수나 클래스의 선언 시점이 아닌, 사용 시점에 타입을 선언할 수 있는 방법을 제공한다. 타입을 인수로 받아서 사용하는 개념이다.

  ```ts
  function getText<T>(text: T): T {
    return text;
  }

  getText<string>("hi");
  getText<number>(10);
  getText<boolean>(true);
  ```

<br>

- 제네릭 프로퍼티 체크

  제네릭 타입 사용 시 관련 메소드를 사용하려고 하면 컴파일러에서 에러를 발생시킬 수 있다. 왜냐하면 제네릭 타입의 경우 프로퍼티를 체크하는데 타입의 범위가 넓을 경우 관련 메소드가 있다는 단서를 찾을 수가 없기 때문이다. (아래와 같이 text에 .length가 있다는 단서는 어디에도 없다) 그렇기 때문에 타입가드나 명시적인 타입을 추가로 작성하여 타입 범위를 좁혀 사용해야한다.

  ```ts
  // 에러 발생 : 명시적인 타입 미선언
  function logText<T>(text: T): T {
    console.log(text.length); // Error: T doesn't have .length
    return text;
  }

  // 에러 미발생 : 명시적인 타입 선언
  function logText<T>(text: T[]): T[] {
    console.log(text.length); // 제네릭 타입이 배열이기 때문에 `length`를 허용합니다.
    return text;
  }
  ```

<br>

- 제네릭 인터페이스

  ```ts
  // 변형 전
  function logText<T>(text: T): T {
    return text;
  }

  let str: <T>(text: T) => T = logText; // #1
  let str: { <T>(text: T): T } = logText; // #2

  // 변형 후
  interface GenericLogTextFn {
    <T>(text: T): T;
  }
  function logText<T>(text: T): T {
    return text;
  }
  let myString: GenericLogTextFn = logText; // Okay
  ```

<br>

- 제네릭 클래스

  ```ts
  class GenericMath<T> {
    pi: T;
    sum: (x: T, y: T) => T;
  }

  let math = new GenericMath<number>();
  ```

<br>

### # 타입 추론

<br>

- 타입 추론이란?

  정적 타입 언의 단점은 타입을 정의하는데 많은 시간과 노력이 들기 때문에 생산성이 저하될 수 있다는 점이다. 하지만 타입스크립트의 경우 다양한 경우에 대해 타입 추론을 제공하기 때문에 꼭 필요한 경우에만 타입 정의를 할 수 있다. 여기서 말하는 타입 추론이란, 타입을 프로그래머가 따로 정의하지 않아도 자동으로 타입을 추론해주는 기능을 말한다. 타입 추론 덕분에 코드를 덜 작성하면서도 같은 수준의 타입 안정성을 유지할 수 있다는 점이 타입스크립트의 장점이다.

<br>

- 타입스크립트의 타입 추론 방법

  (1) 최적의 공통 타입(Best Common Type) : 타입은 보통 몇 개의 표현식(코드)을 바탕으로 타입을 추론한다. 그리고 그 표현식을 이용하여 가장 근접한 타입을 추론하게 되는데 이 가장 근접한 타입을 Best Common Type(최적의 공통 타입)이라고 한다. Best Common Type 알고리즘으로 다른 타입들과 가장 잘 호환되는 타입을 선정한다.

  ```ts
  let x = [0, 1, null]; // let x: (number | null)[]
  ```

  (2) 문맥상의 타이핑(Contextual Typing) : 문맥상의 타이핑(타입 결정)은 코드의 위치(문맥)를 기준으로 일어난다.

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

<br>

- 타입 가드는 컴파일러가 타입을 예측할 수 있도록 코드를 작성해서 버그가 발생하지 않도록 예방하는 방법이다.

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

  // 방법2: typeof 활용
  function someFuncTypeof(val: string | number) {
    if (typeof val === "number") {
      val.toFixed(2);
      isNaN(val);
    } else {
      val.split("");
      val.toUpperCase();
      val.length;
    }
  }

  // 방법3: in연산자 활용
  function someFuncIn(val: any) {
    if ("toFixed" in val) {
      val.toFixed(2);
      isNaN(val);
    } else if ("split" in val) {
      val.split("");
      val.toUpperCase();
      val.length;
    }
  }

  // 방법4: instanceof연산자 활용
  class Cat {
    meow() {}
  }
  class Dog {
    woof() {}
  }
  function sounds(ani: Cat | Dog) {
    if (ani instanceof Cat) {
      ani.meow();
    } else {
      ani.woof();
    }
  }
  ```

<br>

### # 타입 단언

<br>

- as키워드를 통해 타입 단언을 할 수 있다. 예를 들어 var a;를 선언한 뒤 var b=a;와 같이 할당하게 되면 타입 추론을 통해 변수 b는 any타입을 갖게 된다. 이 때 var b에 a가 할당되기 전 a=20과 같이 어떠한 값이 a에 할당되어도 var b=a;는 처음과 같이 any타입을 가리키게 된다. 이럴 때 var b=a as number;와 같이 타입 단언을 통해 타입을 지정할 수 있다. 타입 단언은 Dom API 조작 시 많이 사용된다. var dom = document.querySelector('.container') as HTMLDivElement;와 같이 작성하게 되면 변수dom에 타입 추론이 HTMLDivElement | null 에서 HTMLDivElement로 변하게 된다. 그렇기 때문에 if(dom){…}과 같은 예외처리를 해주지 않아도 dom API(innerText 등)를 바로 사용할 수가 있다. 타입 단언의 경우 타입스크립트보다 개발자가 더욱 정확한 타입을 알 수 있을 때 사용된다.

<br>

### # 타입 호환성

<br>

- 타입 호환이란 타입스크립트 코드에서 특정 타입이 다른 타입에 잘 맞는지를 의미한다. 타입스크립트의 타입 호환성은 구조적 서브 타이핑을 기반으로 한다. 구조적 서브 타이핑은 오직 멤버만으로 타입을 관계시키는 방법으로 알고 있다. 인터페이스 타입 호환 시에는 구조적으로 작은 부분에 큰 부분을 할당할 수 있다. 큰 부분에 작은 부분을 할당할 수는 없다. 우항(할당하는 값)이 좌항(할당받는 값)의 합집합이어야 한다. 함수 타입 호환시에는 파라미터의 갯수와 타입을 체크하여 호환할 수 있다. 단 인터페이스와 다른 관점에서 생각해야한다. 예를 들어 var add = function(a:number) { … }, var sum = function(a:number, b: number) { … } 이와 같은 함수가 있을 경우 add에는 sum을 할당할 수 없다. 왜냐하면 구조적으로 큰 sum은 add에 합집합이지만 인터페이스 같은 경우 객체의 프로퍼티는 부족해도 문제가 발생하지 않지만 함수에는 파라미터가 부족할 경우 문제가 발생할 수 있기 때문이다. 그렇기 때문에 함수 타입 호환시에는 구조적으로 큰 함수에 구조적으로 작은 함수를 할당하여야한다. 제네릭 타입 호환 시에 속성이 없다면 호환되고 제네릭 속성의 타입이 각각 다른 값으로 지정되어 있다면 호환이 불가능하다.

<br>

### # strict 모드에서 null 에러

<br>

- strict모드 활성화 시 null 타입 관련 문제는 아래와 같은 타입 가드로 null 타입이 아닌 경우를 추가하여 해결할 수 있다.

  (1) as : const confirmedTotal = $('.confirmed-total') as HTMLSpanElement;

  (2) if문 : if (!rankList) return; rankList.addEventListener('click', handleListClick);

  (3) 삼항연산자 : selectedId = event.target.parentElement ? event.target.parentElement.id : undefined;

  (4) 옵셔널체이닝 : deathsList?.appendChild(li)

  (5) ! (Non-null assertion operator) : deathsList!.appendChild(li);

<br>

### # 타입 별칭

<br>

- 타입 별칭은 인터페이스의 기능과 유사하다. 새로운 타입 값을 하나 생성하는 것이 아니라 정의한 타입에 대해 나중에 쉽게 참고할 수 있게 이름을 부여하는 것과 같다. 이러한 특징은 VSCode 상의 프리뷰 상태로 다른 타입과 어떤 차이점이 있는지 확인해볼 수 있다. 인터페이스 타입의 경우 프리뷰 상태로 인터페이스 타입명을 보여주는 반면 타입 별칭은 타입 별칭 구조를 그대로 보여준다. 단 타입 별칭은 인터페이스 타입과 다르게 확장이 불가능하다.

  ```ts
  const name: string = "capt";

  // 타입 별칭을 사용할 때
  type MyName = string;
  const name: MyName = "capt";
  ```

<br>

### # 유틸리티 타입

- 유틸리티 타입이란?

  유틸리티 타입은 이미 정의해 놓은 타입을 변환할 때 사용하기 좋은 타입 문법입니다. 유틸리티 타입을 꼭 쓰지 않더라도 기존의 인터페이스, 제네릭 등의 기본 문법으로 충분히 타입을 변환할 수 있지만 유틸리티 타입을 쓰면 훨씬 더 간결한 문법으로 타입을 정의할 수 있습니다.

<br>

- 자주 사용되는 유틸리티 타입

  (1) 파셜(Partial) : 파셜(Partial) 타입은 특정 타입의 부분 집합을 만족하는 타입을 정의할 수 있다. 파셜을 사용하면 옵션 속성의 남발을 막을 수 있다.

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

  (2) 픽(Pick) : 픽(Pick) 타입은 특정 타입에서 몇 개의 속성을 선택(pick)하여 타입을 정의할 수 있습니다.

  ```ts
  interface Hero {
    name: string;
    skill: string;
  }
  const human: Pick<Hero, "name"> = {
    name: "스킬이 없는 사람",
  };
  ```

  (3) 오밋(Omit) : 오밋(Omit) 타입은 특정 타입에서 지정된 속성만 제거한 타입을 정의해 줍니다.

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

<br>

- 맵드 타입이란?

  맵드 타입이란 기존에 정의되어 있는 타입을 새로운 타입으로 변환해 주는 문법을 의미합니다. 마치 자바스크립트 map() API 함수를 타입에 적용한 것과 같은 효과를 가집니다.

<br>

- 맵드 타입 사용법

  in operator를 활용하여 순회하며 in operator를 기준으로 좌항(위 P)은 일반 타입 변수, 우항(위 K)은 순회가 되는 대상이 된다. 타입은 콜론 뒤(위 T)에 지정해주면 된다.

  ```ts
  // 예제1 : 기본 문법
  { [ P in K ] : T }
  { [ P in K ] ? : T }
  { readonly [ P in K ] : T }
  { readonly [ P in K ] ? : T }

  // 예제2 : 기본 예제
  type Heroes = "Hulk" | "Capt" | "Thor";
  type HeroAges = { [K in Heroes]: number };
  const ages: HeroAges = {
    Hulk: 33,
    Capt: 100,
    Thor: 1000,
  };

  // 예제3 : 실용 예제, 맵드 타입인 Subset은 키와 값이 있는 객체를 정의하는 타입을 받아 그 객체의 부분 집합을 만족하는 타입으로 변환해주는 문법이다. 예를 들면 Person과 같은 인터페이스가 있다고 할 때 Subset 타입을 적용하면 ageOnly, nameOnly, ironman, empty과 같은 객체를 모두 정의할 수 있다.

  type Subset<T> = {
    [K in keyof T]?: T[K];
  }

  interface Person {
    age: number;
    name: string;
  }

  const ageOnly: Subset<Person> = { age: 23 };
  const nameOnly: Subset<Person> = { name: 'Tony' };
  const ironman: Subset<Person> = { age: 23, name: 'Tony' };
  const empty: Subset<Person> = {};
  ```

<br>

### # 타입스크립트 유니온 타입과 인터섹션 타입의 차이점에 대해 설명해달라

<br>

- 유니온 타입 : 유니온 타입(Union Type)이란 자바스크립트의 OR 연산자(||)와 같이 'A' 이거나 'B'이다 라는 의미의 타입이다. 유니온 타입으로 인터페이스 두 개를 연결할 경우 함수 내부에서 공통 된 속성만 접근할 수 있다.

<br>

- 인터섹션 타입 : 인터섹션 타입(Intersection Type)은 여러 타입을 모두 만족하는 하나의 타입을 의미한다. 인터섹션 타입으로 인터페이스 두 개를 연결할 경우 인터페이스가 가진 모든 속성에 접근이 가능하다. & 연산자를 이용한다.

<br>

- 유니온 타입과 인터섹션 타입 차이

  유니온 타입은 다중 타입 중 하나를 선택하여 사용하는 개념이고, 인터섹션 타입은 다중 타입을 조합하여 새로운 타입을 만든다는 개념이다. 또한 유니온 타입으로 인터페이스 타입을 결합하는 경우 공통 된 속성만 접근 가능하고 인터섹션 타입은 모든 타입에 접근 가능하다.

<br>

### # 타입 별칭과 인터페이스 차이

- 타입 별칭과 인터페이스의 가장 큰 차이점은 타입의 확장 가능 여부이다. 인터페이스는 확장이 가능한데 반해 타입 별칭은 확장이 불가능하다. 따라서, 가능한한 type 보다는 interface로 선언해서 사용하는 것을 좋다. 또한 프리뷰에서도 차이가 있다. 타입 별칭은 타입의 구조를 모두 보여주는 반면 인터페이스 타입은 타입명을 보여준다.

<br>

### # **never 타입**

<br>

- never 타입이란?

  never는 절대 발생하지 않을 값을 나타내며, 모든 타입의 하위 타입으로 어떠한 타입도 할당할 수 없다. 예를 들어 무한 루프가 발생하는 함수(함수 내용에 while(true){}가 들어 있는 경우)의 경우나 항상 예외를 던지는 함수(function foo(){throw new Error('Not Implemented')의 리턴타입)가 있다.

<br>

- void와 never의 차이

  아무것도 반환하지 않는 함수의 리턴타입은 void이고 영원히 리턴하지 않는 함수(또는 항상 throw하는 함수)의 리턴타입은 never이다. void는 할당이 가능한 타입이지만 (strictNullCheckings를 끄면) never는 절대 never 이외에는 할당할 수 없다. 즉 void는 null 혹은 undefined 값의 반환을 허용한다는 것이고 never는 never 이외에는 허용하지 않는다.

<br>

### # **타입스크립트 데코레이터**

<br>

- 데코레이터란?

  데코레이터가 붙은 클래스, 메소드(함수) 및 변수 등에 데코레이터에서 정의된 기능이 동작하는 것을 의미한다.

<br>

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

<br>

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

<br>

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

### # **타입스크립트가 실행되는 과정**

<br>

- 2-4번은 TSC가 수행, 5-7번은 브라우저, NodJS, 기타 자바스크립트 엔진 같은 자바스크립트 런타임이 실행

  (1) 소스 코드 작성 by 프로그래머

  (2) 타입스크립트 소스 코드를 파싱하여 AST (추상문법트리)로 변환

  (3) 타입 검사기가 AST를 확인 (여기서 타입 검사가 이루어짐)

  (4) 컴파일러가 AST를 bytecode가 아닌 JavaScript로 변환한다.

  (5) JavaScript 소스를 AST로 변환

  (6) AST -> 바이트코드

  (7) 런타임이 바이트코드를 평가

<br>

### # **keyof와 typeof**

- keyof `example` : `example`의 모든 프로퍼티의 키값을 union 형태로 반환, “T extends keyof 인터페이스명”을 통해서 인터페이스의 있는 한 가지만 제네릭으로 설정한다. 인터페이스 내부의 key값으로 제네릭의 범위를 제한하는 것이다.

<br>

- typeof `example` : `example`(변수/함수등)의 type을 반환, enum 타입과 같은 객체를 반환하는 타입에 사용하면 이 객체 자체가 타입이 된다.

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

function GenericReturnFunc<T>(arg: T): T {
  return arg.length; // 제네릭 함수는 무슨 타입이 올지 모르기 때문에 length 프로퍼티를 사용할 수 없다는 에러 메시지를 노출한다.
}
```

<br>

### # 타입스크립트 설정 파일 (tsconfig.json)

<br>

- 타입스크립트 설정 파일은 타입스크립트를 자바스크립트로 변환할 때의 설정을 정의해놓는 파일이다. 프로젝트에서 tsc라는 명령어를 치면 타입스크립트 설정 파일에 정의된 내용을 기준으로 변환 작업(컴파일)을 진행한다.

<br>
