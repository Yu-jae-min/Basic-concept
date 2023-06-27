# **[Javascript] axios의 withCredential과 fetch의 credential**

23년 06월 27일

<br>

## **1. CORS를 허용하였는데 쿠키가 안넘어온다.**

사이드 프로젝트를 진행하면서 간단한 닉네임 입력 기능을 구현하였다. 해당 기능의 구현 플로우는 닉네임 입력 시 로그인 api를 쏘고 서버에서 브라우저에 쿠키로 토큰을 심는 방식으로 구현하려고 했다. 그런데 이 때 이슈가 발생했다. CORS를 허용하였는데 로그인 api 응답 값 쿠키가 넘어오지 않고 `Unauthorization` 에러가 발생하였다. 결론 먼저 말하면 `axios`의 `withCredential` 옵션을 true로 설정하여 해결할 수 있었다. 이유가 뭘까? `withCredential` 옵션에 대해 알아보자.

<br>
<br>

## **2. withCredential 옵션**

`withCredential`을 직역해보면 `자격 증명을 함께`라고 해석할 수 있다. 단어의 의미만 봐도 알 수 있듯이 무언가 인증할 때 필요한 옵션인 것을 알 수 있다. 정확히 `withCredential` 옵션의 역할은 서로 다른 도메인(크로스 도메인)에 요청을 보낼 때 요청에 `Credential` 정보를 담아서 보낼 지를 결정하는 옵션이다. axios에서는 `withCredential` , fetch에서는 `credential`로 지정할 수 있다.

```jsx
/* axios */
axios.get("https://example.com/items", {
  withCredentials: false, // default
});

/* fetch API */
fetch("https://example.com:1234/users", {
  credentials: "include",
});
```

즉, `credential` 정보가 포함되어 있는 요청은 아래 두 가지 경우를 의미한다.

1. 쿠키를 첨부해서 보내는 요청
2. 헤더에 `Authorization` 항목이 있는 요청

따라서, 보내고자 하는 요청이 위 두 가지 항목 중 한 가지라도 포함하고 있다면 `withCredentials` 옵션을 `true`로 설정해야만 한다.

또한, `credential` 정보가 포함되어 있는 요청 시 브라우저는 CORS 정책 위반 여부 검사 룰에 아래와 같은 룰을 추가하게 된다.

1. `Access-Control-Allow-Origin`에는 `*`를 사용할 수 없으며, 명시적인 URL이어야한다.
2. 응답 헤더에는 반드시 `Access-Control-Allow-Credentials: true`가 존재해야한다.

<br>

### **2-1. fetch의 credential**

fetch의 credential 옵션에는 총 3가지의 값을 사용할 수 있으며, 각 값들이 가지는 의미는 다음과 같다.

| 옵션 값              | 설명                                           |
| -------------------- | ---------------------------------------------- |
| same-origin (기본값) | 같은 출처 간 요청에만 인증 정보를 담을 수 있다 |
| include              | 모든 요청에 인증 정보를 담을 수 있다           |
| omit                 | 모든 요청에 인증 정보를 담지 않는다            |

<br>

### **2-2. axios의 withCredential**

axios의 withCredential 옵션에는 총 3가지의 값을 사용할 수 있으며, 각 값들이 가지는 의미는 다음과 같다.

| 옵션 값       | 설명                                           |
| ------------- | ---------------------------------------------- |
| false(기본값) | 같은 출처 간 요청에만 인증 정보를 담을 수 있다 |
| true          | 모든 요청에 인증 정보를 담을 수 있다           |

<br>
<br>

## **3. 서버에서의 필수 설정**

`credential` 정보가 포함되어 있는 요청이 정상적으로 처리되기 위해서는 해당 요청을 받는 서버 측에서도 다음과 같은 설정이 필요하다.

1. 응답 헤더의 `Access-Control-Allow-Credentials` 항목을 `true`로 설정해야 한다.
2. 응답 헤더의 `Access-Control-Allow-Origin`의 값이 반드시 설정되어야 합니다. 단 와일드카드 문자(`*`)는 사용할 수 없다.
3. 응답 헤더의 `Access-Control-Allow-Methods`의 값을 지정해야 할 경우 와일드카드 문자(`*`)는 사용할 수 없다.
4. 응답 헤더의 `Access-Control-Allow-Headers`의 값을 지정해야 할 경우 와일드카드 문자(`*`)는 사용할 수 없다.

유의해야 할 점은 `Access-Control-Allow-*` 헤더 값들을 지정해야 하는 경우에는, 와일드카드 문자를 제외한 값으로 설정되어야 한다는 것이다.

이 값이 와일드카드 문자로 설정될 경우, 요청에 대한 응답이 클라이언트로 전해지기는 하지만 클라이언트 js에서는 이 응답에 접근을 할 수 없는 상태가 된다. 이유는 브라우저가 이를 차단하고 있기 때문이다. 이는 브라우저 개발자도구에서 자주 볼 수 있는 `CORS Error`가 표시되는 이유 중 한 가지이기도 하다.

하지만, preflight가 필요 없는 요청의 경우(대표적으로 `GET` 요청) `Access-Control-Allow-Methods`와 `Access-Control-Allow-Headers`헤더는 아예 존재하지 않아도 된다.

![axios의_withCredential과_fetch의_credential_01](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/cf1be25f-7bdc-4fef-8165-a8c0b82ce09f)

<br>
<br>

## **4. Preflight**

`Preflight`란 브라우저에서 본 요청을 보내기 전 해당 요청이 안전한 요청인지 검증하는 예비 요청이다. 이 때 요청의 옵션을 활용하여 해당 요청의 유효성 검사를 진행한 후 본 요청을 보내게 된다.

![axios의_withCredential과_fetch의_credential_02](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/55ca21ab-63df-40f4-a01f-4606976a0693)

하지만 모든 요청에서 `Preflight`를 사용하는 것은 아니다. 예비 요청을 보내지 않는 `Simple Request`(Simple Request은 정식 명칭이 아니다.) 개념도 있다.

`Simple Request`은 예비 요청을 보내지 않고 바로 서버에게 본 요청부터 보낸 후, 서버가 이에 대한 응답 헤더에 `Access-Control-Allow-Origin`과 같은 값을 보내주면 그때 브라우저가 CORS 정책 위반 여부를 검사하는 방식이다. `Simple Request`방식과 `Preflight`방식은 로직 자체는 같지만 예비 요청의 존재 유무만 다르다.

![axios의_withCredential과_fetch의_credential_03](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/5102d913-8d5e-4555-a329-5c9d097e1706)

하지만 `Simple Request`방식으로 브라우저가 요청하는 경우는 아래와 같은 특정 조건들을 모두 만족하는 경우에만 해당 방식으로 요청하게 된다.

1. 요청의 메소드는 `GET`, `HEAD`, `POST` 중 하나여야 한다.
2. `Accept`, `Accept-Language`, `Content-Language`, `Content-Type`, `DPR`, `Downlink`, `Save-Data`, `Viewport-Width`, `Width`를 제외한 헤더를 사용하면 안된다.
3. 만약 `Content-Type`를 사용하는 경우에는 `application/x-www-form-urlencoded`, `multipart/form-data`, `text/plain`만 허용된다.

<br>
<br>

## **#. 레퍼런스**

- [HTTP Ajax 요청시 사용하는 withCredentials 옵션의 의미](https://junglast.com/blog/http-ajax-withcredential)
- [CORS 총정리!!](https://jaehoney.tistory.com/166)
