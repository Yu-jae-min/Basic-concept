# 소셜 로그인

<br>

## **# 소셜 로그인이란?**

<br>

소셜로그인은 모바일이나 웹에서 간편하게 로그인하기 위한 방법 중 하나입니다. 소셜로그인을 사용하면 별도의 회원가입 절차 없이 소셜미디어 계정으로 간편하게 로그인이 가능합니다.

소셜로그인의 장점은 다음과 같습니다.

- 회원가입 절차 없이 간편하게 로그인 가능
- 보안성이 높아져 개인정보 유출 가능성이 줄어듭니다.
- 다양한 플랫폼에서 동일한 계정으로 로그인 가능합니다.

하지만 소셜로그인을 사용하면 나중에 소셜미디어 계정을 삭제하게 되면 해당 서비스에서 사용하던 계정도 함께 삭제되므로 주의해야 합니다.

또한, 소셜로그인을 사용하면 해당 서비스에서 제공하는 정보를 수집할 수 있습니다. 따라서 이를 꼭 확인하고 동의한 뒤에 사용해야 합니다.

소셜로그인은 Facebook, Google, Twitter 등 다양한 소셜미디어 플랫폼에서 지원됩니다. 그러나 모든 서비스에서 모든 소셜미디어 플랫폼을 지원하지 않으므로, 소셜로그인을 사용하려면 해당 서비스가 지원하는 소셜미디어 플랫폼을 확인해야 합니다.

<br>
<br>

## **# 소셜로그인 기획**

![ETC_social_login_01](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/7426227b-3c4f-4f2d-8597-efca3416437b)

<br>
<br>

## **# 소셜로그인 구현 플로우**

<br>

### **# 애플 (apply)**

![ETC_social_login_02](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/a01d085f-4ce4-4b9b-be42-ea6c87525ae2)

(1) 클라이언트가 파리미터러 클라이언트 ID, 리다이렉트 URI, 응답 타입을 code로 지정하여 권한 서버에 전달합니다. 정상적으로 인증이 되면 권한 코드 부여 코드를 클라이언트에게 보냅니다.응답 타입은 code, token 이 사용 가능합니다.응답 타입이 token 일 경우 암시적 승인 타입에 해당합니다.

(2) 응답 해준 Access Token 이 유효한지 검증 요청을 합니다.

(3) 요청 받은 Access Token 정보에 대한 검증에 대한 응답값을 돌려줍니다.

(4) 유효한 Access Token 기반으로 Resource Server와 통신합니다.

> 3번에서 애플로그인에서는 clientsecret를 key.p8 파일을 이용해 암호화해서 애플 서버에 요청, 그리고 받은 결과값은 jwt를 이용해 풀어야한다. 또한 client_secret 값은 180일에 한번씩 업데이트를 해야한다.

<br>

### **# 구글 (google)**

![ETC_social_login_03](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/e8354362-a4a9-46ef-a24e-14d20a64b629)

![ETC_social_login_04](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/427b9856-ec16-41c3-bc37-5608bf94b296)

<br>
<br>

## **# 구현 방법**

<br>

### **# 애플 (apple)**

1. [애플 개발자 홈페이지 접속](https://developer.apple.com/)
2. [ App ID 등록 ] 좌측 메뉴 중 Identifiers - App ID 생성 (애플 개발자 페이지에 iOS 앱을 등록하지 않았을 경우에만 수행) - Identifiers 타이틀 옆 + 버튼 - App IDs 선택 - 등록할 iOS 앱 프로젝트의 Bundle ID를 입력 - Capabilities 목록에서 Sign In with Apple을 선택하고 Edit - Enable as a primary App ID 선택, 일종의 로그인을 공유한다는 개념인데 내가 가진 다른앱과 상관없는 독립적인 앱이라면 Enable as a primary App ID를 선택하고 저장하여 App ID 등록 절차 완료
3. [ Key 발급 ] 좌측 메뉴 중 Keys - Keys 타이틀 옆 + 버튼 - Key 이름 입력 후 Sign In with Apple을 활성화 및 우측 Configure 버튼 클릭 - 드롭다운 열어서 App ID 선택 - 마지막 단계에서 private key 파일 다운로드, 주의할 점은 재다운로드가 불가하므로 바로 다운로드해야하며 분실 시 Key를 새로 생성해야 함
4. [ Service ID ] 웹에서 애플로그인을 사용하기 위해 service ID 활성화해야 함, Identifiers 타이틀 옆 + 버튼 - Services IDs 선택 - Identifier를 지어준다. 보통 App ID(Bundle ID)를 역순으로 배치해서 쓴다. App ID가 *aaa.bbb.ccc*면 *ccc.bbb.aaa*로 지어주면 된다. 그 후 Sign In with Apple을 활성화 해주고 Configure 버튼을 클릭 - 애플 로그인도 일종의 OAuth 인증이기 때문에 로그인 화면에서 수행한 결과를 백엔드 서버로 전달하는데 위 창에는 그 결과를 전달받을 도메인과 하위 주소를 입력, 만약, 내가 *test.com*라는 도메인의 *callback/apple* 이라는 주소로 결과를 전달받고 싶다면 Web Domain에는 *test.com*을, Return URLs에는 *https://test.com/callback.apple*을 입력해주면 된다. 참고로 localhost도 안되며, HTTP가 아닌 커스텀 프로토콜(예를들어 markets://)도 안된다. 다 입력했으면 Save를 누르고 다시 Configure를 눌러서 위 창을 한 번 더 띄워준다. 입력을 완료하면 Download, Verify 버튼이 생긴다. Download 버튼을 눌러 *apple-developer-domain-association.txt*를 다운받고 */.well-known* 주소 아래에 해당 파일을 호스팅한다. 호스팅을 마쳤다면 Verify 버튼을 누른다. 이 후 초록 v표시가 생기면 완료

> **내 iOS 앱에 애플 로그인 기능을 넣어야 하는 이유** : 애플이 WWDC 2019에서 애플 로그인(Sign In with Apple) 기능을 발표함과 동시에, 구글이나 페이스북 로그인과 같이 타사 인증(OAuth)을 지원하는 iOS 앱에 애플 로그인을 강제로 넣어야 한다는 조항을 내걸었다. 우왕굳

<br>

### **# 페이스북 (facebook)**

- 참고 URL : https://imweb.me/faq?mode=view&category=29&category2=47&idx=71636

  ```js
  import FacebookProvider from "next-auth/providers/facebook";
  ...
  providers: [
    FacebookProvider({
      clientId: process.env.FACEBOOK_CLIENT_ID,
      clientSecret: process.env.FACEBOOK_CLIENT_SECRET
    })
  ]
  ...
  ```

<br>

### **# 구글 (google)**

1. [구글 클라우드 플랫폼](https://console.cloud.google.com/getting-started?pli=1) 접속
2. 상단 프로젝트 선택 - 프로젝트 생성
3. API 및 서비스 - 사용자 인증 정보
4. 상단 사용자 인증 정보 만들기 - OAuth 클라이언트 ID - 동의 화면 구성, 목적에 따른 내부/외부 선택 (내부는 조직 내 G Suite 사용자만 허용하며 외부는 모든 사용자 허용하는데 우리 서비스에서는 일반 사용자가 대상이기 때문에 외부를 선택) 후 만들기
5. [ 앱 등록 수정 step1 ] OAuth 동의 화면 개발자 정보 입력
6. [ 앱 등록 수정 step2 ] 범위 추가 또는 삭제 - 전달받고자 하는 정보 선택
7. [ 앱 등록 수정 step3 ] 테스트 계정 등록 - [ 앱 등록 수정 step 4 ] 요약 확인 후 등록
8. 앱 등록 완료 후 4에서 선택했던 OAuth 클라이언트 ID 다시 클릭 - 애플리케이션 유형, 이름, 로그인이 사용될 URL 입력하여 OAuth 클라이언트 ID 생성, 클라이언트 ID와 비밀번호는 환경 변수에 추가하여 사용
9. 클라이언트 코드 작성 (next-auth 혹은 react-google-login 등 사용)

- example : next-auth

  ```js
  // next-auth 사용시 pages/api/auth 폴더안에 [...nextauth].js 파일을 만들어야 합니다.

  import NextAuth from "next-auth";
  import GoogleProvider from "next-auth/providers/google";

  const nextAuthOptions = (req, res) => {
    return {
      providers: [
        GoogleProvider({
          clientId: process.env.GOOGLE_CLIENT_ID,
          clientSecret: process.env.GOOGLE_CLIENT_SECRET,
        }),
      ],
    };
  };

  const authHandler = (req, res) => {
    return NextAuth(req, res, nextAuthOptions(req, res));
  };

  export default authHandler;
  ```

  ```js
  // 로그인 화면에서 next-auth signIn 함수를 이용합니다.

  import { signIn } from 'next-auth/react';

  const Login = () => {

    ... 생략

    return (
      <Button onClick={() => signIn('google')}>
        구글 로그인
      </Button>
    );
  }
  ```

- example : react-google-login

  ```js
  // index.tsx
  import * as React from "react";
  import { NextPage } from "next";
  import styled from "styled-components";
  import Router from "next/router";
  import GoogleLogin from "react-google-login";

  const Index: NextPage = () => {
    const onSuccess = (res: any) => {
      console.log(res); // 로그인한 사용자 정보 조회

      Router.push("/google"); // /google 페이지로 이동
    };

    const onFailure = (error: any) => {
      console.log(error);
    };

    return (
      <Wrapper>
        <Header.Container>
          <Header.Title>로그인할 방법을 선택해주세요.</Header.Title>
        </Header.Container>

        <Button.Container>
          <Button.ButtonList>
            <Button.GoogleButton
              clientId="asdf12345.apps.googleusercontent.com" // 발급된 clientId 등록
              onSuccess={onSuccess}
              onFailure={onFailure}
              cookiePolicy={"single_host_origin"} // 쿠키 정책 등록
              buttonText="Google 로그인" // 버튼에 사용될 텍스트
            />
          </Button.ButtonList>
        </Button.Container>
      </Wrapper>
    );
  };

  export default Index;

  const Wrapper = styled.div`
    max-width: 720px;

    margin: 0 auto;
  `;

  const Header = {
    Container: styled.div`
      text-align: center;
    `,

    Title: styled.h2``,
  };

  const Button = {
    Container: styled.div``,

    ButtonList: styled.div`
      display: flex;
      flex-direction: column;
      align-items: center;
    `,

    GoogleButton: styled(GoogleLogin)`
      width: 360px;
      height: 40px;

      margin: 6px 0;

      justify-content: center;

      & span {
        font-size: 18px;
        font-weight: 700 !important;
      }
    `,
  };
  ```

  ```js
  // google.tsx
  import { NextPage } from "next";
  import Router from "next/router";
  import * as React from "react";
  import styled from "styled-components";
  import { GoogleLogout } from "react-google-login";

  const Google: NextPage = () => {
    const onLogoutSuccess = () => {
      console.log("onLogoutSuccess");

      Router.push("/");
    };

    const onFailure = () => {
      console.log("onFailure");
    };

    return (
      <Wrapper>
        <Title>Google Page...</Title>
        <Button
          clientId="asdf12345.apps.googleusercontent.com" // 발급된 clientId 등록
          onLogoutSuccess={onLogoutSuccess}
          onFailure={onFailure}
          buttonText="Google 로그아웃" // 버튼에 사용될 텍스트
        />
      </Wrapper>
    );
  };

  export default Google;

  const Wrapper = styled.div`
    max-width: 720px;

    margin: 0 auto;

    display: flex;
    flex-direction: column;
    align-items: center;
  `;

  const Title = styled.h2``;

  const Button = styled(GoogleLogout)`
    width: 360px;
    height: 40px;

    margin: 6px 0;

    justify-content: center;

    & span {
      font-size: 18px;
      font-weight: 700 !important;
    }
  `;
  ```

<br>

## **# 참고 자료**

- [OAuth 2.0 (Open Authorization)](https://tecoble.techcourse.co.kr/post/2021-07-10-understanding-oauth/)
- [react-google-login](https://github.com/anthonyjgrove/react-google-login)
- [next-auth official homepage](https://next-auth.js.org/)
- [next-auth github](https://github.com/nextauthjs/next-auth) : apple, google, facebook 모두 지원 😮
  - apple : https://next-auth.js.org/providers/apple
  - facebook : https://next-auth.js.org/providers/facebook
  - google : https://next-auth.js.org/providers/google
- [google one tab login](https://tilnote.io/pages/63b6a5b0eb6139cc0588447f)
- [JavaScript SDK를 사용하는 웹용 Facebook 로그인](https://developers.facebook.com/docs/facebook-login/web)
