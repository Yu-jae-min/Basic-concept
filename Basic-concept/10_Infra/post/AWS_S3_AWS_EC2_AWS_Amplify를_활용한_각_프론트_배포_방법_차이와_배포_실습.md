# [Infra] AWS S3, AWS EC2, AWS Amplify를 활용한 각 프론트 배포 방법 차이와 배포 실습

2023년 09월 14일

<br>

# 1. AWS EC2 배포

AWS EC2는 웹 서버 구축 과정이 필요하고, 비용이 S3보다 더 높고, S3보다 많은 설정(운영체제, 보안그룹, 스케일링 관리 등)이 필요하다는 단점이 있지만 그에 따라 많은 제어 또한 가능하다는 장점이 있다. AWS EC2는 웹 서버가 구축되어 있기 때문에 SSR 프로젝트에 적합하다. EC2로 배포하게 된 후 사용자가 접속하면 EC2 인스턴스에 요청이 전달되고 EC2 인스턴스에서 요청을 처리(SSR)하여 HTML 생성 후 응답하게 된다.

<br>
<br>

# 2. AWS S3+Cloudfront 배포

AWS S3는 웹 서버 구축 과정이 필요없고 정적인 컨텐츠(build 결과물인 HTML, CSS, Javascript 번들 등)를 배포할 수 있다. EC2에 비해 비용이 상대적으로 저렴하고 배포도 간편하며 보통 AWS CDN 서비스인 Cloudfront(HTTPS 사용, 캐시, 빠른 데이터 제공 등을 위해 사용)와 함께 사용된다. S3로 배포할 프로젝트는 정적 웹페이지로 CSR를 사용하는 프로젝트에 적합하다. S3를 통해 배포한 서비스에 SSR을 구현하기 위해서는 추가적인 작업이 필요하다. S3로 배포하게 된 후 사용자가 접속하면 Cloudfront에 요청이 전달되고 캐시서버에 캐싱 된 데이터가 없다면 S3에 요청을 전달하여 개발자가 업로드한 빌드 결과물을 응답한다. 브라우저는 응답받은 결과물 중 js를 통해 렌더링한다. 그리고 사용자가 다시 접속하게 되면 Cloudfront 캐시서버에 캐싱 된 데이터를 활용하여 응답한다.

<br>
<br>

# 3. AWS Amplify 배포

AWS Amplify로 배포하게 되면 업로드 후, 빌드, 배포 과정을 거치기 때문에 SSR 적용이 가능하다.

<br>
<br>

# 4. 대표 프론트 배포 방법

(1) Nginx : 정적 콘텐츠를 배포하게 해준다.

(2) AWS EC2 : 웹 서버와 WAS 서버 배포가 가능하다.

(3) AWS S3 + Cloudfront : 정적 콘텐츠(프론트 서버)를 배포하게 해준다.

(4) AWS Amplify : 정적 콘텐츠(프론트 서버)를 배포하게 해줌. S3+ cloudfront 방법보다 간편하게 배포 가능하며 배포 자동화, 그리고 자동으로 S3와 Cloudfront가 구현된다.

<br>
<br>

# 5. EC2 배포하기

## 5-1. EC2 인스턴스를 생성

로그인 -> EC2 대시보드로 이동 -> 인스턴스 시작 버튼 클릭 -> EC2에서 사용할 OS머신 선택 -> CPU, 메모리 등 서버의 규모 선택 -> EC2 인스턴스 구성 설정 (서브넷, 퍼블릭 IP 자동 할당, 셧다운 시 OS 종료 방식, 종료 방지 기능 등) -> 스토리지 추가 -> 태그 추가 (EC2 리소스 태그, IAM 정책 권한 등) -> 보안 그룹 설정 단계에서 HTTP, HTTPS 접속을 허용하기 위해 규칙 추가 후 포트 범위를 8000, 소스를 위치무관으로 하여 규칙을 추가한다. -> 태그 추가 시 생성한 키페어를 선택하여 인스턴스 시작 버튼 클릭하여 인스턴스 생성, 인스턴스 상태가 러닝으로 바뀌게 되면 실제 서버가 동작하게 된다. -> 태그 추가 시 생성한 키벨류 페어가 파일로 생성되는데 aws 디렉토리에서 확인할 수 있다. 파일명은 키, 확장자는 pem으로 생성되는데 터미널에서 접근하여 chmod 400 으로 모드를 바꿔주어 ssh 접속을 할 수 있도록 한다. (chmod 400 yujaemin.pem) -> EC2 인스턴스에 접속하기 위해 터미널에 `ssh -i yujaemin.pem ubuntu@3.21.33.191` 와 같이 입력한다. 이 때 우분투 뒤 아이피는 EC2 공인아이피를 적어주어야한다. 아마존 사이트에서 인스턴스 목록 중 시작한 인스턴스를 선택하면 IPv4 퍼블릭 IP를 확인할 수 있다.

<br>

## 5-2. 프론트엔드 배포(우분투 환경)

터미널에서 ssh 접속을 허용하기 위해 `chmod 400 key이름.pem` 으로 권한 설정 -> 터미널에서 EC2 서버에 접속 `ssh -i key이름.pem ubuntu@1.23.45.678` 이 때 우분투 뒤 아이피는 EC2 공인아이피를 적어주어야한다. 아마존 사이트에서 인스턴스 목록 중 시작한 인스턴스를 선택하면 IPv4 퍼블릭 IP를 확인할 수 있다. -> 터미널에서 git clone으로 소스코드 받아오기 -> 노드js 설치를 위해 터미널에서 `curl -sL <https://deb.nodesource.com/setup_14.x> | sudo bash -` 실행 후 `sudo apt-get install nodejs` 실행 후 node -v 와 npm -v로 설치 확인 -> 터미널에서 clone한 프로젝트 디렉토리로 이동 후 npm i로 필요한 패키지 설치 -> `npm run build` 하여 배포환경에서 사용 할 파일 생성 (압축 형태 파일) -> 프로젝트 루트 디렉토리에서 `npm i express --save` node express 설치 -> 프로젝트 루트 디렉토리에서 express와 연동을 위해 `vi server.js`로 파일을 생성한다. 그 후 server.js에서 소스 코드(아래 참고)를 추가하여 express와 연결한다. 이 때 포트번호는 EC2 인스턴스 생성 시 사용했던 포트번호로 지정해야한다. -> `node server.js`로 서버 실행 -> 우분투 뒤 아이피 값과 포트번호로 접속하여 잘 동작하는지 확인한다. (ex `1.23.45.678:8080`) -> 터미널 종료 시에도 서버가 돌아가게 하기 위한 설정을 해야한다. 터미널에서 프로젝트 루트 디렉토리로 이동 후 `sudo node server.js &`로 서버를 실행하면 서버가 유지된다. 이렇게 하면 배포가 완료된 것이다.

```jsx
// server.js
const http = require("http");
const express = require("express");
const path = require("path");

const app = express();

const port = 8000;

app.get("/ping", (req, res) => {
  res.send("pong");
});

app.use(express.static(path.join(__dirname, "build")));

app.get("/*", (req, res) => {
  res.set({
    "Cache-Control": "no-cache, no-store, must-revalidate",
    Pragma: "no-cache",
    Date: Date.now(),
  });
  res.sendFile(path.join(__dirname, "build", "index.html"));
});

http.createServer(app).listen(port, () => {
  console.log(`app listening at ${port}`);
});
```

<br>
<br>

# 6. S3, Cloudfront, Route 53, IAM, CI/CD 배포하기

## 6-1. 도메인 만들기

무료 도메인 발급을 위해 Freenom 접속 -> Servieces 탭 -> Register a New Domain -> 원하는 도메인 checkout 후 도메인 상태가 active가 되면 사용 가능하다.

<br>

## 6-2. IAM 권한 설정

AWS 사이트에서 IAM 대시보드 -> 사용자 추가 버튼 -> 1단계에서 사용자 이름 입력, 액세스 유형은 액세스 키 선택 -> 2단계에서 기존 정책 직접 연결 탭에서 AmazonS3FullAccess 를 체크, CloudFront 진행을 위해 CloudFrontFullAccess 도 선택 -> 끝 단계까지 넘어간 후 사용자 만들기 클릭하여 액세스 키 발급, csv다운로드 버튼을 클릭하여 액세스 키 csv파일 저장

<br>

## 6-3. S3 버킷 만들기

AWS 사이트에서 S3 대시보드 -> 버킷 만들기 버튼 -> 일반구성 탭에서 버킷 이름 입력, AWS 리전 선택 (기본값으로 설정되어 나옴) -> 객체 소유권 탭에서 ACL 활성화를 선택 -> 이 버킷의 퍼블릭 액세스 차단 설정 탭에서 퍼블릭 액세스를 차단하면 웹으로 접근이 불가능하기 때문에 차단을 풀어주고 아래 유의사항 체크박스에 체크하여 확인 -> 그 외의 항목들은 기본 값으로 두거나 상황에 맞게 설정, 버킷 만들기 버튼 눌러서 버킷 생성 -> 버킷 목록에서 생성한 버킷 선택 -> 속성 탭 선택 후 맨 아래 정적 웹 사이트 호스팅 편집 -> 정적 웹사이트 호스팅 활성화, 인덱스 문서와 오류 문서 index.html로 변경 후 변경사항 저장 -> 해당 버킷의 권한 탭 선택 -> 버킷 정책 탭에서 편집 -> 정책 생성기 클릭 -> Effect는 Allow (유저가 접속할 수 있도록 설정), Select Type of Policy는 S3 Bucket Policy, Principal는 `/*`입력 (모든 유저에 대해서 라는 뜻), Action은 GetObject (유저들이 이 버킷에 접근할 수 있는 권한을 준다는 뜻), ARN은 버킷 정책 편집 페이지에 적혀있는 ARN을 입력하는데 끝에 `/*` 를 추가 (`/*`은 모든 오브젝트에 대해서라는 뜻이며 작성 예시는 `arn:aws:s3:::버킷이름/*`)까지 입력 후 Add Statement 를 클릭하면 리스트가 생성 됨 -> Generate Policy 를 클릭하면 JSON 형태의 문서가 나오는데 전체 복사 -> 다시 버킷 정책 편집 탭으로 들어와 복사한 값을 붙여넣기 후 변경 사항 저장 버튼 클릭하여 저장

<br>

## 6-4. 빌드된 프로젝트 S3 버킷에 업로드(CLI를 통한 업로드)

AWS CLI 설치(https://docs.aws.amazon.com/ko_kr/cli/latest/userguide/getting-started-install.html) -> 설치 완료 후 터미널에서 유저 추가 `aws configure --profile [유저명]` (IAM 에서 생성한 사용자 이름을 입력) -> IAM권한설정에서 다운받은 csv 파일을 확인하여 AWS Access Key ID, AWS Secret Access Key, fault region name, Default output format 입력 -> 터미널에서 배포할 프로젝트 디렉토리로 이동하여 명령어를 입력 `aws s3 sync ./build s3://[S3 버킷 이름] --profile=[사용자 아이디]` (예 `aws s3 sync ./build s3://woalsqjzlt --profile=yujaemin`), package.json script에 deploy로 추가해두면 편하게 실행할 수 있다.

<br>

## 6-5. Route 53 도메인 설정

AWS 사이트에서 Route53 대시보드 -> 호스팅 영역 -> 호스팅 영역 생성 버튼 클릭 -> 도메인 이름 탭에서 설정할 도메인 주소 입력 -> 유형 탭에서 퍼블릭 호스팅 영역 체크 -> 호스팅 영역 생성 버튼 클릭 -> 네임 서버 리스트 값들이 생성되는데 도메인 서버의 레코드 관리 페이지에 입력해주어야한다. -> Freenom 의 경우 Servieces 탭 -> My Domains -> ManageDomain 클릭 -> Management Tools -> Nameservers를 선택 -> Use custom nameservers 체크 -> 발급받은 Nameserver 적은 후 체인지 네임서버 버튼 선택

<br>

## 6-6. CloudFront 배포 생성

AWS 사이트에서 CloudFront 대시보드 -> CloudFront 배포 생성 버튼 클릭 -> 원본 도메인 탭에서 인풋 박스 클릭 후 생성한 S3 버킷 선택 -> S3버킷 액세스 탭에서 OAI 사용 체크 후 새 OAI를 생성 (이미 가지고 있으면 기존 ID선택, 자동으로 입력된 값 사용) -> 뷰어 프로토콜 정책 탭에서 Redirect HTTP to HTTPS 선택 (HTTP접속을 HTTPS로 리다이렉트 시킴) -> Route53으로 커스텀 도메인을 설정한 경우 대체 도메인 이름 탭에서 Route53으로 생성한 주소 입력 -> 대체 도메인 입력 시 HTTPS를 사용할 것이기 때문에 SSL 인증서가 필요하다. 인증서는 AWS Certificate Manager를 통해 발급 (https://console.aws.amazon.com/acm/home?region=us-east-1#/certificates/request) -> 모든 설정 후 배포 생성, 생성하면 state가 in progress라고 뜨는데 조금 기다리면 완료 됨.

<br>

## 6-7. CloudFront 주소와 Route53으로 생성한 도메인 연결

AWS 사이트에서 Route53 대시보드 -> 호스팅한 도메인에 레코드 생성 버튼 클릭 -> 라우팅 정책 선택 탭에서 단순 라우팅 선택 -> 레코드 구성 탭에서 단순 레코드 정의 클릭 -> 단순 레코드 정의 탭에서 레코드 유형은 A, 값/트래픽 라우팅 대상은 CloudFront 배포에 대한 별칭, 배포 선택에서는 우리가 생성한 CloudFront 를 선택 후 단순 레코드 정의 버튼 클릭하여 레코드를 생성을 완료하면 연결된다.

<br>

## 6-8. 캐시 무효화(Invalidation) 하기

캐시 무효화하는 이유는 프로젝트 업데이트를 위해서이다. S3에 파일을 업로드하면 CloudFront의 엣지 로케이션에 캐싱되어 저장된다. 파일의 캐시 만료 전 프로젝트가 업데이트 되어 갱신하기 위해서는 S3에 업데이트된 파일을 새로 업로드하고 CloudFront가 가지고 있는 캐시를 비워야한다. 그렇게 되면 사용자가 파일 요청 시 엣지 로케이션이 캐시를 가지고 있지 않기 때문에 S3에 새로 요청하여 내용을 업데이트 시킬 수 있다. ->
AWS 사이트에서 IAM 대시보드 -> 권한 추가 버튼 클릭 -> CloudFrontFullAccess 선택하여 추가 -> 터미널에 `aws cloudfront create-invalidation --profil=[사용자 아이디] --distribution-id [CloudFront ID] --paths /*` 입력, distribution-id 는 CloudFront 페이지에서 ID 값을 입력해주면 된다. paths 는 invalidation 할 파일들을 지정하는 것인데, 전체를 업데이트 해야할 경우 `/\*` 을 입력, 이 명령어 또한 package.json에 script로 추가하여 사용하면 편하다. ->
프로젝트 루트 디렉토리에 .env 환경 변수 파일 생성 후 해당 명령 입력 `PUBLIC_URL="https://[S3 버킷 이름].s3.[리전].amazonaws.com/"` 만약 Route53으로 커스텀 도메인을 생성한 경우에는 해당 도메인 주소를 PUBLIC_URL 에 입력 (예 https://www.jaemin.com/)

(8) react-router-dom 사용 시 페이지 이동 후 403 에러 발생 대응 : AWS 사이트에서 S3 버킷 설정으로 이동하여 인덱스 문서, 오류 문서를 index.html로 설정 -> CloudFront 설정 페이지로 이동 후 오류 페이지 탭 클릭 -> 사용자 정의 오류 생성 버튼 클릭하여 오류코드 403, 404 생성하고 응답 페이지 경로를 index.html로 설정 후 응답코드를 200으로 설정

<br>
<br>

# # 참고 URL

- https://42place.innovationacademy.kr/archives/9784

<br>
