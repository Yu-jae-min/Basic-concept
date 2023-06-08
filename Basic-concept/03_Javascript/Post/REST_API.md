# **# REST(Representational State Tansfer) API**

REST(Representational State Tansfer) API란 어떤 기술이나 제품이 아닌 방식, 형식을 말한다. API를 요청할 때 요청하는 모습 자체로 어떤 정보인지 추론 가능한 형태임을 말한다. 사전적 정의는 웹상에서 사용되는 여러 리소스를 HTTP URI로 표현하고 그 리소스에 대한 행위를 HTTP Method로 정의하는 방식, 즉 리소스(HTTP URI로 정의된)를 어떻게 한다(HTTP Method+Payload)를 구조적으로 깔끔하게 표현하는 것을 말한다.

<br>

## **# API란?**

API(Application Programming Interface)란 단어 자체의 뜻 처럼 어플리케이션 프로그래밍 인터페이스를 말한다. 인터페이스란 쉽게 말해 자판기의 버튼과 같은 역할을 하며 소프트웨어와 소프트웨어 간의 정보교환 창구이다. 지정된 형식으로 요청, 명령을 받을 수 있는 수단을 말한다. 예를 들어 기상청서버로부터 미리 작성된 소프트웨어(지정된 형식, 공개된 메뉴얼)를 통해 날씨 정보를 요청하고 전송 받을 수가 있다.

> 네트워크 상에서만이 아닌 로컬프로그램인 브라우저는 Web API를 통해 자바스크립트로부터
> 특정 동작을 지시받기도 한다. (ex 어떤 함수로 어떤 동작을 수행한다)

<br>

## **# SOAP vs REST**

REST와 SOAP는 각기 다른 두 가지의 온라인 데이터 전송 방식이다. 둘 다 웹 애플리케이션 간 데이터 통신을 허용하는 애플리케이션 프로그래밍 인터페이스(Application Programming Interface, API)를 구축하는 방법을 정의한다. REST(Representational State Transfer)는 아키텍처 원칙 세트이고, SOAP(Simple Object Access Protocol)는 World Wide Web Consortium(W3C)에서 유지관리하는 공식 프로토콜이다. 즉, SOAP는 프로토콜이지만, REST는 프로토콜이 아니라는 점이 주요 차이점이다.

```javascript
// SOAP example
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:sch="http://www.soapexample.com/xml/users">
  <soapenv:Header/>
  <soapenv:Body>
     <sch:UserDetailsRequest>
        <sch:name>John</sch:name>
     </sch:UserDetailsRequest>
  </soapenv:Body>
</soapenv:Envelope>

// REST example
{
 "name": "John",
 "age": 5,
 "address": "Greenville"
}
```

REST API의 장점은 self-descriptiveness, RESTful API는 그 자체만으로도 API의 목적이 쉽게 이해된다. 또한 단점으로는 표준 규약이 없어, 안티패턴(실제 많이 사용되는 패턴이지만 비효율적이나 비생산적인 패턴)으로 작성되는 경우가 흔하다.

> **SOAP vs REST의 차이** : https://www.upwork.com/resources/soap-vs-rest-a-look-at-two-different-api-styles

<br>

## **# RESTful API 설계 규칙**

(1) URI 정보를 명확하게 표현해야 한다.

> **resource는 명사를 사용한다.**
>
> - bad : GET /user/1
> - good : GET /users/1

(2) resource에 대한 행위를 HTTP Method로 표현한다.

> **URI에 HTTP Method가 포함되서는 안된다.**
>
> - bad : GET delete/user/1
> - good : DELETE /users/1

> **URI에 동사가 포함되서는 안된다.**
>
> - bad : GET /user/show/1
> - good : GET /users/1

(3) resource 사이에 연관 관계가 있는 경우

> **/리소스/고유ID/관계 있는 리소스**
>
> - ex : GET /users/{user_id}/profile

(4) 파일의 경우 payload의 포맷을 나타내기 위한 파일 확장자를 URI에 포함시키지 않는다.

> **이 때, payload의 포맷은 headers에 accept를 사용한다.**
>
> - bad : GET user/1/profile-photo.jpg
> - good : GET user/1/profile-photo

(5) URI는 / 구분자를 사용하여 자원의 계층 관계를 나타내는데 사용한다.

(6) URI 마지막 문자로 / 를 포함하지 않는다. 이유는 Query parameter에 대한 resource 상세 정보들을 덧붙이기 위해서이다.

(7) 불가피하게 URI가 길어지는 경우 -(하이픈)을 사용하여 가독성을 높인다.

(8) `_(언더바)`는 포함시키지 않는다.

(9) URI 경로에는 대문자 사용을 피하도록 규정하고 있다.

<br>

## **# 기본 용어 설명**

- URI : 해당 사이트의 특정 자원의 위치를 나타내는 유일한 주소
- HTTP Method : HTTP request가 의도하는 action을 정의한 것
- Payload : HTTP request에서 server로 보내는 데이터 (body)
  > **example : GET https://10.58.4.1/products**
  >
  > GET(HTTP Method) https(Protocol)://10.58.4.1(Host)/products(Resource)

<br>

## **# URI 작성 예시**

아래와 같이 자원을 구조와 함께 나타내는 이런 형태의 구분자를 URI(Uniform Resource Identifier) 라고 한다.

(1) http://(도메인)/classes/

-> 반의 목록을 받아오는 요청

(2) http://(도메인)/classes/2

-> 반의 목록 중 index가 2인 목록을 요청

(3) http://(도메인)/classes/2/students

-> 반의 목록 중 index가 2인 반의 학생들 목록 요청

(4) http://(도메인)/classes/2/students/15

-> 반의 목록 중 index가 2인 반의 학생들 목록 중 15번째 학생 목록 요청

(5) http://(도메인)/classes/2/students?gender=man

-> 반들 목록중 index가 2인 반의 학생들 목록 중 남학생들 목록 요청

(6) http://(도메인)/classes/2/students?page=2&count=10

-> 페이지 수를 제한하고, 페이지에 보여지는 데이터를 제한할 수 있다.

<br>

## **# HTTP Method의 사용**

대표적인 HTTP Method로는 GET, POST, DELETE, PUT, PATCH가 있다. 또한 POST, PUT, PATCH에는 body가 있어 데이터 담아 전송할 수 있다. 각 메소드는 특별하게 구분되어 있지 않지만 RESTful한 API를 만들기 위해 각 메소드를 목적에 따라 구분하여 사용한다.

```javascript
// 예시 데이터 형식
{
  "results" : [
    {"idx": 1, "name" : "홍길동", "gender" : "man"},
    {"idx": 2, "name" : "계월향", "gender" : "female"},
    {"idx": 3, "name" : "전우치", "gender" : "man"},
    {"idx": 4, "name" : "성춘향", "gender" : "female"}
  ]
}
```

- **GET** : GET은 데이터를 조회(Read)할 때 사용한다.

- **POST** : POST는 새로운 정보를 추가/생성(Create)할 때 사용한다.

  > 예를 들어 idx11을 가진 학생의 정보가 추가되는 경우
  >
  > {"idx": 11, "name" : "유재민", "gender" : "man"}과 같이 body에 실어 보내는데
  >
  > POST요청 시 URI는 아래와 같이 작성하면 된다.
  >
  > http://(도메인)/classes/2/students
  >
  > (idx 11은 추가되며 생성되는 것이기 때문에 URI에 11을 명기할 필요가 없다.)

- **DELETE** : DELETE는 삭제(Delete)시에 사용한다.

  > URI의 엔드포인트는 데이터를 정확하게 명기할 수 있도록 해야한다.
  >
  > 예를 들어 2반 학생 중 11번 째 학생의 데이터를 삭제하는 경우 아래와 같이 작성한다.
  >
  > http://(도메인)/classes/2/students/11

- **PUT & PATCH** : PUT 또는 PATCH는 수정(Update)시에 사용한다. 작업자에 따라 PUT 하나만 사용하는 경우도 있지만, 두 가지를 구분하면 PUT은 데이터를 통째로 갈아끼울 때, PATCH는 정보 중 일부를 특정 방식으로 갈아 끼울 때 사용한다.

  > POST와 마찬가지로 body에 수정할 내용을 실어 보내는데 이 때 URI는 수정되는 데이터의 구분자를 아래와 같이 실어 보내야한다. 예를 들어 11번 학생의 데이터가 수정되는 경우 URI는 아래와 같다.
  >
  > http://(도메인)/classes/2/students/11

<br>

## **# Query parameter & Path parameter**

- **Query parameters (GET parameters)**

  Query parameter 혹은 Query String이라고 한다. 웹 페이지의 url 주소를 자세히 보면 종종 ? 가 포함되어 있는 것을 볼 수 있는데 이 물음표는 단순한 문자열이 아닌 특정한 기능을 수행하고 있다. 물음표 뒤에는 늘 key=value 형식의 문자열이 따라오며 이를 Query parameter라고 한다. 주로 데이터를 조건으로 거르거나(filtering), 특정 방식으로 정렬하거나(sorting), 검색(searching)하고자 하는 경우에 활용된다.

  > **(1) Query parameter - Filtering**
  >
  > GET /products?price=3000원 (price가 3000원인 데이터 요청)
  >
  > GET /products?price=3000원&name=사과 (price가 3000원, name이 사과인 데이터 요청)
  >
  > **(2) Query parameter - Ordering**
  >
  > GET /products?ordering=-id (id 역순으로 재정렬해서 데이터 요청)
  >
  > **(3) Query parameter - Pagination**
  >
  > GET /products?offset=0&limit=100 (데이터 양을 설정, offset은 데이터의 시작점이고 limit는 가져올 최대 데이터 갯수이다.)
  > **(4) Query parameter - Searching**
  >
  > GET /users?search=홍길동 (홍길동이라는 데이터가 들어간 데이터를 요청)

- **Path parameters**

  쿼리 파라미터와 유사해보이지만 그 역할이 완전히 다른 Path parameter도 있다. 매개변수를 Path(경로)로만 지정한다고해서 Path parameters이다. 해당 리소스에 더 자세한 정보를 얻기 위해 접근할 때 사용한다.

  > ex : http://10.58.4.1:8000/products/1

- **Path parameter vs Query parameter**

  Path parameter 방식을 사용하여 GET /products/3 로 작성한 결과 값과
  Query parameter 방식을 사용하여 GET /products?id=3 로 작성한 결과 값은 같다. 그럼 이 때 둘 중 무슨 방법을 사용해야할까? 정해진 규칙은 아니지만 Path parameter를 사용한다. Query parameter를 사용하는 경우는 Filtering, Sorting, Searching을 통해 데이터를 요청하는 경우 사용하는 것이 모범적이다.

<br>

### #8 HTTP 상태 코드 참조

> https://developer.mozilla.org/ko/docs/Web/HTTP/Status

<br>

---

<br>

참고자료

1. <a href="https://developer.mozilla.org/ko/docs/Web/HTTP/Status" target='_blank'>HTTP 상태 코드</a>
2. <a href="https://www.upwork.com/resources/soap-vs-rest-a-look-at-two-different-api-styles" target='_blank'>SOAP vs. REST: A Look at Two Different API Styles</a>
3. <a href="https://www.youtube.com/watch?v=qv5XK91OhFo" target='_blank'>Query Parameters - Web Development</a>
4. <a href="https://medium.com/@fullsour/when-should-you-use-path-variable-and-query-parameter-a346790e8a6d" target='_blank'>When Should You Use Path Variable and Query Parameter?</a>
5. <a href="https://www.redhat.com/ko/topics/integration/whats-the-difference-between-soap-rest" target='_blank'>REST와 SOAP 비교</a>
