# **AJAX와 Axios & Fetch**

## **# AJAX (Asynchronous JavaScript and XML)**

**AJAX**(Asynchronous JavaScript and XML)는 자바스크립트를 이용해서 비동기적(Asynchronous)으로 서버와 브라우저가 데이터를 교환할 수 있는 통신 방식을 의미한다. 즉, AJAX는 자바스크립트에서 비동기 HTTP 통신이 가능하도록 해주며 서버와 통신 시 **XMLHttpRequest 객체**를 사용하여 다양한 데이터 포맷을 주고 받는다.

> 위에서 언급한 XMLHttpRequest 객체의 다양한 데이터 포맷이란 **XML 뿐만 아닌 JSON, HTML 그리고 일반 텍스트 형식 등을 포함한 다양한 포맷**을 말한다. 객체명에서 충분한 오해의 소지가 있으므로 XMLHttpRequest 객체는 객체 네이밍에 실패한 사례라고 할 수도 있다.

AJAX의 주요 두가지 특징으로는 페이지 새로고침 없이 서버에 요청할 수 있고, 서버로부터 데이터를 받고 작업을 수행할 수 있게 해준다.

> **비동기 통신이 필요한 이유**
>
> 초기의 HTML은 Static한 성질을 가지고 있었고, 각 페이지의 이동은 Anchor tag의 href 속성을 통해 서로 다른 화면으로 이동이 가능했다. 하지만, 이러한 방식대로라면 모든 페이지를 이동할때 화면의 깜빡임이 발생하게 될 뿐만 아니라 하나의 Static한 html 파일에 용량이 큰 Assets나 Library를 사용하게되면 화면이 완전히 뜰때까지의 시간이 길어지게 된다. 또한 전체 페이지가 리로드되어 중복되는 시멘틱 태그도 다시 보여주기 때문에 비효율적이다. 싱글스레드로 동작하는 Javascript Engine과 위의 문제점을 해결하기 위해 비동기 통신이 등장했다. 비동기 통신은 처음 화면에 꼭 보여주지 않아야 할 것들은 순차적으로 로딩하면서 첫 화면이 빠르게 보여지게 할 수 있고, 다른 화면으로의 이동을 자연스럽게 한다. 예를들어 Lazy Loading이나 Infinite Scroll이 비동기 통신을 활용한 예시이다. Javascript의 내장 객체에서 지원해주는 XMLHttpRequest 객체가 있고, 이를 쉽게 사용 할 수 있도록 해주는 라이브러리가 Jquery의 Ajax 이고 이외에도 axios나 Promise 등이 있다

<br>

### **# JSON (JavaScript Object Notation)**

**XML**은 데이터 포맷 중 하나로 HTML과 유사한 마크업 언어이다. 데이터를 저장하고, 전달할 목적으로 고안되었다. 불필요한 태그들이 들어가 파일의 사이즈가 커질 뿐만 아니라 가독성도 좋지 않아 XML대신 JSON이 사용된다.

아래 예시는 dog 라는 객체의 name 속성으로 식빵, family 속성으로 웰시코기, age 속성으로 1, weight 속성으로 2.14를 반환하는 데이터이다.

```xml
// XML
<dog>
   <name>식빵</name>
   <family>웰시코기<family>
   <age>1</age>
   <weight>2.14</weight>
</dog>
```

**JSON**은 데이터 포맷 중 하나로 XML과 마찬가지로 데이터 저장과 전달을 목적으로 고안되었으며, 자바스크립트 기반으로 작성되으며 key와 value가 한 쌍을 이루는 구조의 객체로 구성되어 있다.

XML의 대안으로서 고안되었으며, XML 대비 더 직관적이며, 작성하기 편리하다는 특징이 있다. 또 배열을 파싱할 수 없는 XML과 달리 JSON은 배열을 사용할 수 있다. 프로그래밍 언어나 플랫폼에 상관없이 사용할 수 있다.

브라우저에서 서버로 데이터 전송 시 object를 직렬화하여 string으로 변환하여 전송하고 서버에서 브라우저로 데이터를 받아올 때는 역직렬화하여 string을 object로 바꾼다.

> **직렬화(Serialization)와 역직렬화(Deserialization)**
>
> - 직렬화 : 컴퓨터 메모리 상에 존재하는 객체(Object) -> 문자열(string)로 변환
> - 역직렬화 : 문자열(string) -> 자바스크립트 객체(Object)로 반환

```javascript
// JSON
{
   "name": "식빵",
   "family": "웰시코기",
   "age": 1,
   "weight": 2.14
}
```

> **왜 JSON을 사용해야 하는가?**
>
> XMLHttpRequest를 사용해서 데이터를 통신할 경우 배열 객체를 전달받고 사용하는 일이 까다로워질 수 밖에 없다. XMLHttpRequest.responseText는 문자열을 반환하므로 이를 사용하기 위해서는 , 를 중심으로 문자열을 나눠야한다. 그러나 JSON을 사용하면 배열 자체를 사용할 수 있기 때문에 번거로운 파싱작업을 할 필요가 없어진다. 또 XML 대신 최근에 JSON만을 사용하는 이유로는 JSON은 XML처럼 엔드 태그가 존재하지 자바스크립트로 간단히 작성할 수 있으며, 더 가볍기 때문이다. 또한 XML로는 배열을 표현하는데 한계가 있지만, JSON은 그렇지 않다는 특징도 있다.

<br>

#### **# JSON.stringify**

JSON.stringify 메소드는 Object(객체)를 JSON 형식의 문자열로 변환한다.

```javascript
// Object to JSON
// JSON.stringify
let json = JSON.stringify(true);
console.log(json); // true

json = JSON.stringify(["apple", "banana"]);
console.log(json); // ["apple","banana"]

const rabbit = {
  name: "tori",
  color: "white",
  size: null,
  birthDate: new Date(),
  // symbol: Symbol("id"),
  jump: () => {
    console.log(`${this.name} can jump!`);
  },
};

json = JSON.stringify(rabbit);
console.log(json); // {"name":"tori","color":"white","size":null,"birthDate":"2022-04-19T04:14:40.491Z"}

json = JSON.stringify(rabbit, ["name"]);
console.log(json); // {"name":"tori"}

json = JSON.stringify(rabbit, (key, value) => {
  console.log(`key: ${key}, value: ${value}`);
  return key === "name" ? "ellie" : value; // {"name":"ellie","color":"white","size":null,"birthDate":"2022-04-19T06:10:08.547Z"}
});
console.log(json);
```

위와 같이 json으로 변환할 수 있다. 단, 위 예시에서 jump 메서드는 json으로 변환 시 json에 포함되지 않는다. 함수는 object의 데이터가 아니기 때문에 제외된다. 또한 Symbol과 같이 자바스크립트에만 있는 특별한 데이터도 제외된다.

두번째 인자를 통해 json 변환 형태를 제어할 수 있다.

JSON.stringify(rabbit, ["name"])과 같이 두번째 인자를 전달하게 되면 두번째 인자에 들어간 key만 json으로 변환한다.

또한 JSON.stringify(rabbit, (key, value) => {...}과 같이 콜백 함수를 전달하여 위와 같이 특정 조건에 따라 json으로 변환하는 것도 가능하다.

<br>

#### **# JSON.parse**

JSON.parse 메소드는 JSON 데이터를 가진 문자열을 Object(객체)로 변환한다.

> 서버로부터 브라우저로 전송된 JSON 데이터는 문자열이다. 이 문자열을 객체로서 사용하려면 객체화하여야 하는데 이를 역직렬화(Deserializing)이라 한다. 역직렬화를 위해서 내장 객체 JSON의 static 메소드인 JSON.parse를 사용한다.

```javascript
// JSON to Object
// JSON.parse
const rabbit = {
  name: "tori",
  color: "white",
  size: null,
  birthDate: new Date(),
  // symbol: Symbol("id"),
  jump: function () {
    console.log(`${this.name} can jump!`);
  },
};

const json = JSON.stringify(rabbit); // rabbit을 json으로 변환

const obj = JSON.parse(json);
console.log(obj); // {name: 'tori', color: 'white', size: null, birthDate: '2022-04-19T05:14:41.903Z'}

rabbit.jump(); //  tori can jump!
// obj.jump(); // 에러 발생!

console.log(rabbit.birthDate.getDate()); // 19
// console.log(obj.birthDate.getDate()); // 에러 발생!

const obj2 = JSON.parse(json, (key, value) => {
  // console.log(`key: ${key}, value: ${value}`);
  return key === "birthDate" ? new Date(value) : value;
});

console.log(obj2.birthDate.getDate());
```

위 예제의 경우 몇 군데 에러가 발생한다.

rabbit.jump()는 정상적으로 실행되지만 obj.jump()는 실행되지 않는다. 그 이유는 rabbit에 포함되어있던 jump 메서드가 json으로 변환될 때 포함되지 않았으므로 다시 object로 변환해도 존재하지 않는다.

두번째로 obj.birthDate.getDate() 또한 비슷한 에러로 실행되지 않는다. rabbit에 포함되어있던 Date객체가 json으로 변환될 때 string으로 변환되었으므로 다시 object로 변환해도 string이 되므로 Date 관련 메서드 실행이 불가능하다.

obj.birthDate.getDate() 에러의 경우 obj2와 같은 형태인 콜백 함수를 통해 해결할 수 있다. key value를 파라미터로 받는 콜백 함수를 통해 key가 birthDate인 경우 기존 value와 같은 new Date로 변경시켰다.

<br>

### **# XHR(XMLHttpRequest)**

브라우저는 XHR(XMLHttpRequest) 객체를 이용하여 Ajax 요청을 생성하고 전송한다. 서버가 브라우저의 요청에 대해 응답을 반환하면 같은 XHR(XMLHttpRequest) 객체가 그 결과를 처리한다.

<br>

#### **# Ajax request**

아래 코드는 XHR(XMLHttpRequest)를 이용한 Ajax 요청 처리의 예이다.

```javascript
// XMLHttpRequest 객체의 생성
const xhr = new XMLHttpRequest();
// 비동기 방식으로 Request를 오픈한다.
xhr.open("GET", "/users");
// Request를 전송한다.
xhr.send();
```

<br>

#### **(1) XMLHttpRequest.open()**

XMLHttpRequest 객체의 인스턴스를 생성하고 XMLHttpRequest.open 메소드를 사용하여 서버로의 요청을 준비한다. XMLHttpRequest.open의 사용법은 아래와 같다.

```javascript
XMLHttpRequest.open(method, url[, async])
```

- method : HTTP method (“GET”, “POST”, “PUT”, “DELETE” 등)
- url : 요청을 보낼 URL
- async : 비동기 조작 여부. 옵션으로 default는 true이며 비동기 방식으로 동작한다.

<br>

#### **(2) XMLHttpRequest.send()**

XMLHttpRequest.send 메소드로 준비된 요청을 서버에 전달한다. 기본적으로 서버로 전송하는 데이터는 GET, POST 메소드에 따라 그 전송 방식에 차이가 있다.

- GET 메소드의 경우, URL의 일부분인 쿼리문자열(query string)로 데이터를 서버로 전송한다.
- POST 메소드의 경우, 데이터(페이로드)를 Request Body에 담아 전송한다.

```javascript
xhr.send(null);
// xhr.send('string');
// xhr.send(new Blob()); // 파일 업로드와 같이 바이너리 컨텐트를 보내는 방법
// xhr.send({ form: 'data' });
// xhr.send(document);
```

만약 요청 메소드가 GET인 경우, send 메소드의 인수는 무시되고 request body은 null로 설정된다.

<br>

#### **(3) XMLHttpRequest.setRequestHeader**

XMLHttpRequest.setRequestHeader 메소드는 HTTP Request Header의 값을 설정한다. setRequestHeader 메소드는 반드시 XMLHttpRequest.open 메소드 호출 이후에 호출한다.

자주 사용하는 Request Header인 Content-type, Accept에 대해 살펴보자.

<br>

#### **# Content-type**

Content-type은 request body에 담아 전송할 데이터의 MIME-type의 정보를 표현한다. 자주 사용되는 MIME-type은 아래와 같다.

- text 타입 : text/plain, text/html, text/css, text/javascript
- Application 타입 : application/json, application/x-www-form-urlencode
- File을 업로드하기 위한 타입 : multipart/formed-data

다음은 request body에 담아 서버로 전송할 데이터의 MIME-type을 지정하는 예이다.

```javascript
// json으로 전송하는 경우
xhr.open("POST", "/users");

// 클라이언트가 서버로 전송할 데이터의 MIME-type 지정: json
xhr.setRequestHeader("Content-type", "application/json");

const data = { id: 3, title: "JavaScript", author: "Park", price: 5000 };

xhr.send(JSON.stringify(data));
```

<br>

#### **# Accept**

HTTP 클라이언트가 서버에 요청할 때 서버가 센드백할 데이터의 MIME-type을 Accept로 지정할 수 있다.

다음은 서버가 센드백할 데이터의 MIME-type을 지정하는 예이다.

```javascript
// 서버가 센드백할 데이터의 MIME-type 지정: json
xhr.setRequestHeader("Accept", "application/json");
```

만약 Accept 헤더를 설정하지 않으면, send 메소드가 호출될 때 Accept 헤더가 `*/*`으로 전송된다.

<br>

#### **# Ajax response**

다음은 Ajax 응답 처리의 예이다.

```javascript
// XMLHttpRequest 객체의 생성
const xhr = new XMLHttpRequest();

// XMLHttpRequest.readyState 프로퍼티가 변경(이벤트 발생)될 때마다 onreadystatechange 이벤트 핸들러가 호출된다.
xhr.onreadystatechange = function (e) {
  // readyStates는 XMLHttpRequest의 상태(state)를 반환
  // readyState: 4 => DONE(서버 응답 완료)
  if (xhr.readyState !== XMLHttpRequest.DONE) return;

  // status는 response 상태 코드를 반환 : 200 => 정상 응답
  if (xhr.status === 200) {
    console.log(xhr.responseText);
  } else {
    console.log("Error!");
  }
};
```

XMLHttpRequest.send 메소드를 통해 서버에 Request를 전송하면 서버는 Response를 반환한다. 하지만 언제 Response가 클라이언트에 도달할 지는 알 수 없다. XMLHttpRequest.onreadystatechange는 Response가 클라이언트에 도달하여 발생된 이벤트를 감지하고 콜백 함수를 실행하여 준다. 이때 이벤트는 Request에 어떠한 변화가 발생한 경우 즉 XMLHttpRequest.readyState 프로퍼티가 변경된 경우 발생한다.

```javascript
// XMLHttpRequest 객체의 생성
var xhr = new XMLHttpRequest();
// 비동기 방식으로 Request를 오픈한다
xhr.open("GET", "data/test.json");
// Request를 전송한다
xhr.send();

// XMLHttpRequest.readyState 프로퍼티가 변경(이벤트 발생)될 때마다 콜백함수(이벤트 핸들러)를 호출한다.
xhr.onreadystatechange = function (e) {
  // 이 함수는 Response가 클라이언트에 도달하면 호출된다.
};
```

XMLHttpRequest 객체는 response가 클라이언트에 도달했는지를 추적할 수 있는 프로퍼티를 제공한다. 이 프로퍼티가 바로 XMLHttpRequest.readyState이다. 만일 XMLHttpRequest.readyState의 값이 4인 경우, 정상적으로 Response가 돌아온 경우이다.

readXMLHttpRequest.readyState의 값은 아래와 같다.

| Value | State            | Description                                           |
| ----- | ---------------- | ----------------------------------------------------- |
| 0     | UNSENT           | XMLHttpRequest.open() 메소드 호출 이전                |
| 1     | OPENED           | XMLHttpRequest.open() 메소드 호출 완료                |
| 2     | HEADERS_RECEIVED | XMLHttpRequest.send() 메소드 호출 완료                |
| 3     | LOADING          | 서버 응답 중(XMLHttpRequest.responseText 미완성 상태) |
| 4     | DONE             | 서버 응답 완료                                        |

```javascript
// XMLHttpRequest 객체의 생성
var xhr = new XMLHttpRequest();
// 비동기 방식으로 Request를 오픈한다
xhr.open("GET", "data/test.json");
// Request를 전송한다
xhr.send();

// XMLHttpRequest.readyState 프로퍼티가 변경(이벤트 발생)될 때마다 콜백함수(이벤트 핸들러)를 호출한다.
xhr.onreadystatechange = function (e) {
  // 이 함수는 Response가 클라이언트에 도달하면 호출된다.

  // readyStates는 XMLHttpRequest의 상태(state)를 반환
  // readyState: 4 => DONE(서버 응답 완료)
  if (xhr.readyState !== XMLHttpRequest.DONE) return;

  // status는 response 상태 코드를 반환 : 200 => 정상 응답
  if (xhr.status === 200) {
    console.log(xhr.responseText);
  } else {
    console.log("Error!");
  }
};
```

XMLHttpRequest의.readyState가 4인 경우, 서버 응답이 완료된 상태이므로 이후 XMLHttpRequest.status가 200(정상 응답)임을 확인하고 정상인 경우, XMLHttpRequest.responseText를 취득한다. XMLHttpRequest.responseText에는 서버가 전송한 데이터가 담겨 있다.

만약 서버 응답 완료 상태에만 반응하도록 하려면 readystatechange 이벤트 대신 load 이벤트를 사용해도 된다. load 이벤트는 서버 응답이 완료된 경우에 발생한다.

```javascript
// XMLHttpRequest 객체의 생성
var xhr = new XMLHttpRequest();
// 비동기 방식으로 Request를 오픈한다
xhr.open("GET", "data/test.json");
// Request를 전송한다
xhr.send();

// load 이벤트는 서버 응답이 완료된 경우에 발생한다.
xhr.onload = function (e) {
  // status는 response 상태 코드를 반환 : 200 => 정상 응답
  if (xhr.status === 200) {
    console.log(xhr.responseText);
  } else {
    console.log("Error!");
  }
};
```

<br>

### **# Axios**

**Axios**는 Node.js와 브라우저를 위한 Promise API를 활용하는 HTTP 통신 라이브러리이다. 비동기로 HTTP 통신을 가능하게 해주며 return을 promise 객체(심지어 Json 형식)로 해주기 때문에 response 데이터를 다루기도 쉽다.

써드파티 라이브러리로서 추가적인 설치 및 임포트가 필요하지만, 그 과정이 어렵지 않으며 폭넓은 브라우저 호환성이 보장된다. 사용하기도 쉬워 많은 개발자들이 사용을 하고 있는 라이브러리이다.

```javascript
let url = "https://someurl.com";
let options = {
  method: "POST",
  url: url,
  headers: {
    Accept: "application/json",
    "Content-Type": "application/json;charset=UTF-8",
  },
  data: {
    property_one: value_one,
    property_two: value_two,
  },
};
let response = await axios(options);
let responseOK =
  response && response.status === 200 && response.statusText === "OK";
if (responseOK) {
  let data = await response.data;
  // do something with data
}
```

<br>

### **# Fetch**

fetch API는 ES6부터 들어온 JavaScript 내장 라이브러리이다. 네트워크 통신을 포함한 리소스 취득을 위한 인터페이스가 정의되어 있다. XMLHttpRequest와 같은 비슷한 API가 존재하지만 Fetch API는 좀더 강력하고 유연한 조작이 가능하다.

또한 Built-in APIs 로서 별도의 설치 없이 모던 브라우저에서 사용이 가능하다. window object 에서 정의되어 있으며, HTTP Pipeline(Request/Response)을 위한 Javascript 인터페이스 이며, Promise 객체를 return 한다.

```javascript
let url = "https://someurl.com";
let options = {
  method: "POST",
  mode: "cors",
  headers: {
    Accept: "application/json",
    "Content-Type": "application/json;charset=UTF-8",
  },
  body: JSON.stringify({
    property_one: value_one,
    property_two: value_two,
  }),
};
let response = await fetch(url, options);
let responseOK = response && response.ok;
if (responseOK) {
  let data = await response.json();
  // do something with data
}
```

<br>

### **# Axios vs Fetch**

| Axios                                     | Fetch                                                                                                       |
| ----------------------------------------- | ----------------------------------------------------------------------------------------------------------- |
| 요청 객체 프로퍼티에 url이 있음           | 메서드의 파라미터로 url이 전달                                                                              |
| 써드파티 라이브러리로 설치가 필요         | Built-in APIs 로 별도의 설치 필요 없이, 모던 브라우저에서 사용 가능                                         |
| XSRF Protection 보안 기능 제공            | 별도 보호 없음                                                                                              |
| data 속성을 사용                          | body 속성을 사용                                                                                            |
| data는 object를 포함                      | body는 문자열화 되어야함                                                                                    |
| status가 200이고 statusText가 'OK'면 성공 | 응답 객체가 'OK'속성을 포함하면 성공                                                                        |
| 자동 JSOM 데이터 변환 지원                | JSON 데이터 핸들링 위해 추가 절차 필요                                                                      |
| Request 취소 와 Request Timeout 설정 가능 | 없음<br>(AbortController 이용하여 구현 가능)                                                                |
| HTTP Requests 의 Intercept 가능           | 기본적으로 제공되지 않음<br>(Global Fetch Method를 Overwrite 하여 나의 인터셉터 정의 가능)                  |
| Download Progress 지원                    | 지원하지 않음<br>(Response Object의 Body Property 통해 제공되는 ReadableStream 인스턴스 이용 가능)          |
| 대부분의 브라우저를 지원 (구형 포함)      | Chrome 42+, Firefox 39+, Edge 14+, and Safari 10.1+이상에 지원<br>(polyfill 이용해서 하위 호환성 지원 가능) |

<br>

> **Axios vs Fetch 무엇을 사용해야 될까?**
>
> 사용자의 입맛에 따라 고르면 될것 같다. 간단한 경우엔 fetch를 쓰고 좀더 기능이 필요할땐 axios를 쓰는것도 방법이다.

<br>

---

<br>

참고자료

- <a href="https://poiemaweb.com/js-ajax" target='_blank'>비동기식 처리 모델과 Ajax</a>
