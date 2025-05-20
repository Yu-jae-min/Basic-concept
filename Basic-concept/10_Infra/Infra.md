## # Infra

<br>

### # AWS

- 배포 자동화란?

  말 그대로 배포를 자동화하는 것이고 명령어 하나만으로 배포를 자동적으로 진행하는 것을 말한다. 배포 자동화를 통해 개발자는 개발에만 더욱 집중할 수 있어 개발자 경험이 향상되고
  주기적인 배포를 통해 최신 버전을 빠르게 사용자에게 제공할 수 있습니다. 배포 자동화에서 자주 쓰이는 방식으로 CI/CD(지속적 통합/지속적 배포) 방식이 있다. 예를 들어 예를 들어 Next.js 프로젝트를
  Vercel에 연결하면 레포지토리와 연동만으로 CI/CD가 자동 구축되어 매우 편리합니다.

- CI/CD (지속적 통합/지속적 배포)

  1. CI(Continuous Integration)

  여러 개발자가 작성한 코드를 주기적으로 통합하는 과정을 말한다. 코드가 레포지토리에 병합되기 전에 자동으로 빌드하고 테스트해서 문제를 조기에 발견하고 해결할 수 있도록 돕는다.
  즉 CI는 빌드, 테스트 자동화를 담당한다. (예: `PR 올림 → 자동 빌드 + 테스트 (CI)`, `PR 머지 → 프로덕션 배포 전 다시 빌드 + 테스트 (CI)`)

  2. CD(Continuous Delivery/Continuous Deployment)

  CI가 성공적으로 끝난 코드를 사용자에게 서비스 가능한 환경까지 자동으로 배포하는 과정이다. 즉 CI/CD 방식에서 CD의 역할은 배포 자동화이다. CD를 수행하기 전 코드의 테스트, 빌드,
  통합은 필수이므로 CI가 항상 선행되어야 한다. CI를 성공적으로 마친 후 테스트 서버와 운영 서버에 곧바로 배포되는 환경을 CD라고 한다. (`예: PR 머지 후 빌드 테스트 통과 시 → 자동 배포 진행 (CD)`)

  3. CI/CD

  CI/CD는 개발부터 빌드, 테스트, 통합, 배포까지의 전 과정을 자동화하는 방식입니다. 이를 활용하면 개발 효율성이 높아지고 코드 품질 유지와 빠른 출시가 가능하다.

- CI/CD 파이프라인

  CI/CD의 여러 단계를 순차적으로 연결한 프로세스 구조이다. 주요 단계는 빌드(컴파일), 테스트(오류 및 호환성 검사), 릴리즈(버전 관리 저장소에 반영), 배포(프로덕션 환경 적용), 규정 준수 및 유효성 검사 등이 포함된다.

- 클라우드 서비스(클라우드 컴퓨팅)란?

  클라우드 서비스란 클라우드 컴퓨팅 기술을 사용하여 제공하는 서비스를 말한다. 클라우드 컴퓨팅 기술이란 인터넷을 통한 구독 기반의 기술로 서버, 스토리지, 소프트웨어 등
  필요한 IT 자원을 자신의 컴퓨터가 아닌 클라우드에 연결된 다른 컴퓨터에서 제공해주는 기술을 의미한다.

- 클라우드 서비스 사용 이유

  1. 시간 절약 : 직접 서버나 인프라를 구축하지 않아도 되어 초기 비용과 출시 시간을 크게 단축할 수 있다.

  2. 유연한 대응 : 서비스 수요에 따라 자원을 쉽게 늘리거나 줄일 수 있어 갑작스런 트래픽 증가에도 빠르게 대응할 수 있다.

  3. 비용 절약 : 사용한 만큼만 비용을 지불하는 구조(Pay-as-you-go)로 불필요한 자원 낭비를 줄일 수 있다.

- AWS 관련 용어

  1. EC2 (Elastic Compute Cloud)

  AWS에서 제공하는 가상 서버 서비스로, 물리적 서버를 임대하듯 독립된 서버 환경을 사용할 수 있다. EC2 인스턴스란 이 가상 서버 한 대를 의미하며,
  다양한 사양을 선택할 수 있다. AWS가 제공하는 URL(Public DNS)를 통해 인터넷에서 접근 가능하다.

  2. Secuirty Group

  EC2 인스턴스에 대한 네트워크 접근을 제어하는 가상 방화벽입니다. HTTP, SSH 등의 포트를 열어줘야 외부에서 접속할 수 있습니다.

  3. RDS(Relational Database Service)

  AWS가 관리하는 관계형 데이터베이스 서비스로, 사용자가 직접 설치 및 운영할 필요 없이 쉽게 데이터베이스를 운용할 수 있고 비용도 된다.

  4. ELB(Elastic Load Balancing)

  여러 대의 서버에 트래픽을 분산시켜주는 로드 밸런서 서비스이다. 서버 상태를 실시간으로 모니터링하여 정상적인 서버로만 요청을 분배한다.

  5. Route 53

  AWS의 DNS(도메인 네임 시스템) 서비스로 도메인 등록, 트래픽 라우팅, 상태 확인 등을 제공한다.

  6. CloudFront

  AWS의 CDN(콘텐츠 전송 네트워크) 서비스로, 전 세계 엣지 서버에서 사용자에게 데이터를 빠르게 전송한다. HTTPS 리다이렉션 같은 보안 기능도 제공한다.

  7. S3(Simple Storage Service)

  AWS의 객체 스토리지 서비스로, 파일을 저장하고 인터넷에 공개하거나 비공개로 관리할 수 있다. 웹사이트 이미지, 백업 등 다양한 용도로 사용된다. (ex 파일 서버)

  8. PM2 (Process Manager 2)

  Node.js 애플리케이션을 관리하는 프로세스 매니저이다. 무중단 배포, 클러스터 모드 실행 등을 지원해 애플리케이션 안정성과 성능을 높인다.

  9. 젠킨스(Jenkins)

  오픈소스 CI 도구로, 자동 빌드/테스트/배포 파이프라인을 구성하여 여러 개발자가 협업할 때 통합을 쉽게 해준다.

  10. IAM(Identity and Access Management)

  AWS 자원에 대한 사용자별 접근 권한을 관리하는 서비스이다. 루트 계정 외에 여러 사용자/그룹별 권한을 설정할 수 있다.

  11. VPC(Virtual Private Cloud)

  사용자가 직접 정의하는 가상 네트워크로, AWS 내에서 격리된 네트워크 환경을 만들어 보안과 네트워크 설정을 맞춤형으로 구성할 수 있다.

  12. WAF (Web Application Firewall)

  웹 애플리케이션에 대한 비정상적이고 악의적인 트래픽을 탐지, 차단하는 방화벽이다.

- AWS S3, AWS EC2, AWS Amplify를 활용한 각 프론트 배포 방법 차이

  - AWS EC2

    웹 서버 및 애플리케이션 서버를 직접 구축하고 운영해야 한다. 비용과 관리 부담이 크지만, 서버 측 렌더링(SSR) 프로젝트에 적합하며, 높은 제어권을 제공한다.

  - AWS S3

    정적 웹사이트 호스팅에 최적화된 서비스로, 별도의 서버 구축 없이 빌드 결과물(HTML, CSS, JS 등)을 저장하고 배포한다. CloudFront CDN과 함께 사용해 빠르고 안정적인 콘텐츠 전달이 가능하다. SSR 지원은 별도 서버리스 함수나 백엔드가 필요하다.

  - AWS Amplify

    S3와 CloudFront 기반 정적 웹사이트 및 SSR을 포함한 애플리케이션 배포를 자동화하는 서비스다. 빌드, 배포, 호스팅, 백엔드 서비스 통합 관리가 가능해 편리하다.

  - 정리

    1. Nginx : 웹 서버로 정적 콘텐츠 및 리버스 프록시 역할

    2. AWS EC2 : 서버 운영 및 SSR 가능

    3. AWS S3 + Cloudfront : 정적 콘텐츠 빠른 배포 및 캐싱

    4. AWS Amplify : S3 + CloudFront + CI/CD 자동화 + SSR 일부 지원

<br>

- 배포 방법 (EC2)

  (1) EC2 인스턴스를 생성 : 로그인 -> EC2 대시보드로 이동 -> 인스턴스 시작 버튼 클릭 -> EC2에서 사용할 OS머신 선택 -> CPU, 메모리 등 서버의 규모 선택 -> EC2 인스턴스 구성 설정 (서브넷, 퍼블릭 IP 자동 할당, 셧다운 시 OS 종료 방식, 종료 방지 기능 등) -> 스토리지 추가 -> 태그 추가 (EC2 리소스 태그, IAM 정책 권한 등) -> 보안 그룹 설정 단계에서 HTTP, HTTPS 접속을 허용하기 위해 규칙 추가 후 포트 범위를 8000, 소스를 위치무관으로 하여 규칙을 추가한다. -> 태그 추가 시 생성한 키페어를 선택하여 인스턴스 시작 버튼 클릭하여 인스턴스 생성, 인스턴스 상태가 러닝으로 바뀌게 되면 실제 서버가 동작하게 된다. -> 태그 추가 시 생성한 키벨류 페어가 파일로 생성되는데 aws 디렉토리에서 확인할 수 있다. 파일명은 키, 확장자는 pem으로 생성되는데 터미널에서 접근하여 chmod 400 으로 모드를 바꿔주어 ssh 접속을 할 수 있도록 한다. (chmod 400 yujaemin.pem) -> EC2 인스턴스에 접속하기 위해 터미널에 `ssh -i yujaemin.pem ubuntu@3.21.33.191` 와 같이 입력한다. 이 때 우분투 뒤 아이피는 EC2 공인아이피를 적어주어야한다. 아마존 사이트에서 인스턴스 목록 중 시작한 인스턴스를 선택하면 IPv4 퍼블릭 IP를 확인할 수 있다.

  (2) 프론트엔드 배포(우분투 환경) : 터미널에서 ssh 접속을 허용하기 위해 `chmod 400 key이름.pem` 으로 권한 설정 -> 터미널에서 EC2 서버에 접속 `ssh -i key이름.pem ubuntu@1.23.45.678` 이 때 우분투 뒤 아이피는 EC2 공인아이피를 적어주어야한다. 아마존 사이트에서 인스턴스 목록 중 시작한 인스턴스를 선택하면 IPv4 퍼블릭 IP를 확인할 수 있다. -> 터미널에서 git clone으로 소스코드 받아오기 -> 노드js 설치를 위해 터미널에서 `curl -sL https://deb.nodesource.com/setup_14.x | sudo bash -` 실행 후 `sudo apt-get install nodejs` 실행 후 node -v 와 npm -v로 설치 확인 -> 터미널에서 clone한 프로젝트 디렉토리로 이동 후 npm i로 필요한 패키지 설치 -> `npm run build` 하여 배포환경에서 사용 할 파일 생성 (압축 형태 파일) -> 프로젝트 루트 디렉토리에서 `npm i express --save` node express 설치 -> 프로젝트 루트 디렉토리에서 express와 연동을 위해 `vi server.js`로 파일을 생성한다. 그 후 server.js에서 소스 코드(아래 참고)를 추가하여 express와 연결한다. 이 때 포트번호는 EC2 인스턴스 생성 시 사용했던 포트번호로 지정해야한다. -> `node server.js`로 서버 실행 -> 우분투 뒤 아이피 값과 포트번호로 접속하여 잘 동작하는지 확인한다. (ex `1.23.45.678:8080`) -> 터미널 종료 시에도 서버가 돌아가게 하기 위한 설정을 해야한다. 터미널에서 프로젝트 루트 디렉토리로 이동 후 `sudo node server.js &`로 서버를 실행하면 서버가 유지된다. 이렇게 하면 배포가 완료된 것이다.

  ```js
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

- 배포 방법 (S3, cloudfront, Route 53, IAM, CI/CD, 참고 : https://42place.innovationacademy.kr/archives/9784)

  (0) 도메인 만들기 : 무료 도메인 발급을 위해 Freenom 접속 -> Servieces 탭 -> Register a New Domain -> 원하는 도메인 checkout 후 도메인 상태가 active가 되면 사용 가능하다.

  (1) IAM 권한 설정 : AWS 사이트에서 IAM 대시보드 -> 사용자 추가 버튼 -> 1단계에서 사용자 이름 입력, 액세스 유형은 액세스 키 선택 ->
  2단계에서 기존 정책 직접 연결 탭에서 AmazonS3FullAccess 를 체크, CloudFront 진행을 위해 CloudFrontFullAccess 도 선택 ->
  끝 단계까지 넘어간 후 사용자 만들기 클릭하여 액세스 키 발급, csv다운로드 버튼을 클릭하여 액세스 키 csv파일 저장

  (2) S3 버킷 만들기 : AWS 사이트에서 S3 대시보드 -> 버킷 만들기 버튼 -> 일반구성 탭에서 버킷 이름 입력, AWS 리전 선택 (기본값으로 설정되어 나옴) ->
  객체 소유권 탭에서 ACL 활성화를 선택 -> 이 버킷의 퍼블릭 액세스 차단 설정 탭에서 퍼블릭 액세스를 차단하면 웹으로 접근이 불가능하기 때문에 차단을 풀어주고 아래 유의사항 체크박스에 체크하여 확인 -> 그 외의 항목들은 기본 값으로 두거나 상황에 맞게 설정, 버킷 만들기 버튼 눌러서 버킷 생성 -> 버킷 목록에서 생성한 버킷 선택 -> 속성 탭 선택 후 맨 아래 정적 웹 사이트 호스팅 편집 -> 정적 웹사이트 호스팅 활성화, 인덱스 문서와 오류 문서 index.html로 변경 후 변경사항 저장 -> 해당 버킷의 권한 탭 선택 -> 버킷 정책 탭에서 편집 -> 정책 생성기 클릭 -> Effect는 Allow (유저가 접속할 수 있도록 설정), Select Type of Policy는 S3 Bucket Policy, Principal는 `/*`입력 (모든 유저에 대해서 라는 뜻), Action은 GetObject (유저들이 이 버킷에 접근할 수 있는 권한을 준다는 뜻), ARN은 버킷 정책 편집 페이지에 적혀있는 ARN을 입력하는데 끝에 `/*` 를 추가 (`/*`은 모든 오브젝트에 대해서라는 뜻이며 작성 예시는 `arn:aws:s3:::버킷이름/*`)까지 입력 후 Add Statement 를 클릭하면 리스트가 생성 됨 -> Generate Policy 를 클릭하면 JSON 형태의 문서가 나오는데 전체 복사 -> 다시 버킷 정책 편집 탭으로 들어와 복사한 값을 붙여넣기 후 변경 사항 저장 버튼 클릭하여 저장

  (3) 빌드된 프로젝트 S3 버킷에 업로드(CLI를 통한 업로드) : AWS CLI 설치(https://docs.aws.amazon.com/ko_kr/cli/latest/userguide/getting-started-install.html) -> 설치 완료 후 터미널에서 유저 추가 `aws configure --profile [유저명]` (IAM 에서 생성한 사용자 이름을 입력) -> IAM권한설정에서 다운받은 csv 파일을 확인하여 AWS Access Key ID, AWS Secret Access Key, fault region name, Default output format 입력 -> 터미널에서 배포할 프로젝트 디렉토리로 이동하여 명령어를 입력 `aws s3 sync ./build s3://[S3 버킷 이름] --profile=[사용자 아이디]` (예 `aws s3 sync ./build s3://woalsqjzlt --profile=yujaemin`), package.json script에 deploy로 추가해두면 편하게 실행할 수 있다.

  (4) Route 53 도메인 설정 : AWS 사이트에서 Route53 대시보드 -> 호스팅 영역 -> 호스팅 영역 생성 버튼 클릭 -> 도메인 이름 탭에서 설정할 도메인 주소 입력 -> 유형 탭에서 퍼블릭 호스팅 영역 체크 -> 호스팅 영역 생성 버튼 클릭 -> 네임 서버 리스트 값들이 생성되는데 도메인 서버의 레코드 관리 페이지에 입력해주어야한다. -> Freenom 의 경우 Servieces 탭 -> My Domains -> ManageDomain 클릭 -> Management Tools -> Nameservers를 선택 -> Use custom nameservers 체크 -> 발급받은 Nameserver 적은 후 체인지 네임서버 버튼 선택

  (5) CloudFront 배포 생성 : AWS 사이트에서 CloudFront 대시보드 -> CloudFront 배포 생성 버튼 클릭 -> 원본 도메인 탭에서 인풋 박스 클릭 후 생성한 S3 버킷 선택 -> S3버킷 액세스 탭에서 OAI 사용 체크 후 새 OAI를 생성 (이미 가지고 있으면 기존 ID선택, 자동으로 입력된 값 사용) -> 뷰어 프로토콜 정책 탭에서 Redirect HTTP to HTTPS 선택 (HTTP접속을 HTTPS로 리다이렉트 시킴) ->
  Route53으로 커스텀 도메인을 설정한 경우 대체 도메인 이름 탭에서 Route53으로 생성한 주소 입력 -> 대체 도메인 입력 시 HTTPS를 사용할 것이기 때문에 SSL 인증서가 필요하다. 인증서는 AWS Certificate Manager를 통해 발급 (https://console.aws.amazon.com/acm/home?region=us-east-1#/certificates/request) -> 모든 설정 후 배포 생성, 생성하면 state가 in progress라고 뜨는데 조금 기다리면 완료 됨.

  (6) CloudFront 주소와 Route53으로 생성한 도메인 연결 : AWS 사이트에서 Route53 대시보드 -> 호스팅한 도메인에 레코드 생성 버튼 클릭 -> 라우팅 정책 선택 탭에서 단순 라우팅 선택 -> 레코드 구성 탭에서 단순 레코드 정의 클릭 -> 단순 레코드 정의 탭에서 레코드 유형은 A, 값/트래픽 라우팅 대상은 CloudFront 배포에 대한 별칭, 배포 선택에서는 우리가 생성한 CloudFront 를 선택 후 단순 레코드 정의 버튼 클릭하여 레코드를 생성을 완료하면 연결된다.

  (7) 캐시 무효화(Invalidation) 하기 : 캐시 무효화하는 이유는 프로젝트 업데이트를 위해서이다. S3에 파일을 업로드하면 CloudFront의 엣지 로케이션에 캐싱되어 저장된다. 파일의 캐시 만료 전 프로젝트가 업데이트 되어 갱신하기 위해서는 S3에 업데이트된 파일을 새로 업로드하고 CloudFront가 가지고 있는 캐시를 비워야한다. 그렇게 되면 사용자가 파일 요청 시 엣지 로케이션이 캐시를 가지고 있지 않기 때문에 S3에 새로 요청하여 내용을 업데이트 시킬 수 있다. ->
  AWS 사이트에서 IAM 대시보드 -> 권한 추가 버튼 클릭 -> CloudFrontFullAccess 선택하여 추가 -> 터미널에 `aws cloudfront create-invalidation --profil=[사용자 아이디] --distribution-id [CloudFront ID] --paths /*` 입력, distribution-id 는 CloudFront 페이지에서 ID 값을 입력해주면 된다. paths 는 invalidation 할 파일들을 지정하는 것인데, 전체를 업데이트 해야할 경우 /\* 을 입력, 이 명령어 또한 package.json에 script로 추가하여 사용하면 편하다. ->
  프로젝트 루트 디렉토리에 .env 환경 변수 파일 생성 후 해당 명령 입력 `PUBLIC_URL="https://[S3 버킷 이름].s3.[리전].amazonaws.com/"` 만약 Route53으로 커스텀 도메인을 생성한 경우에는 해당 도메인 주소를 PUBLIC_URL 에 입력 (예 https://www.jaemin.com/)

  (8) react-router-dom 사용 시 페이지 이동 후 403 에러 발생 대응 : AWS 사이트에서 S3 버킷 설정으로 이동하여 인덱스 문서, 오류 문서를 index.html로 설정 -> CloudFront 설정 페이지로 이동 후 오류 페이지 탭 클릭 -> 사용자 정의 오류 생성 버튼 클릭하여 오류코드 403, 404 생성하고 응답 페이지 경로를 index.html로 설정 후 응답코드를 200으로 설정

<br>

### # Presigned URL

- Presigned URL

  Presigned URL은 AWS S3 객체에 대해 별도의 권한 없이도 특정 작업(GET, PUT 등)을 한정된 시간 동안 허용하는 미리 서명된 임시 URL입니다. Presigned URL을 생성하기 위한
  createPresignedPost 메소드를 활용할 수 있다.

- 동작 방식

  1. 사용자가 클라이언트에서 업로드할 파일 이름 등 메타데이터를 서버에 요청한다.

  2. 서버는 AWS SDK를 통해 Presigned URL을 생성하여 클라이언트에 응답한다.

  3. 클라이언트는 이 Presigned URL을 이용해 직접 S3에 PUT 요청으로 파일을 업로드한다.

  4. 업로드가 완료되면, 클라이언트는 해당 파일의 S3 URL 또는 파일 경로를 서버에 전달하여 저장하거나 추후 사용한다.

<br>

### # 서버리스 아키텍처

- 서버리스 아키텍처란?

  서버리스는 ‘서버가 없다’는 뜻이 아니라, 개발자가 서버 인프라를 직접 관리하지 않아도 되는 아키텍처를 의미

- 기존 서비스 모델과 클라우드 서비스 모델 비교

  | 구분                               | 설명                                                                                                             | 예시                             |
  | ---------------------------------- | ---------------------------------------------------------------------------------------------------------------- | -------------------------------- |
  | 자체 시스템 관리 (온프레미스)      | 하드웨어부터 네트워크, OS, 서버, 애플리케이션까지 모두 직접 구축 및 운영                                         | 자체 데이터센터                  |
  | IaaS (Infrastructure as a Service) | 가상 서버, 스토리지, 네트워크 등 인프라를 클라우드로 제공. 서버 OS 설치 및 애플리케이션 배포 등은 직접 관리 필요 | AWS EC2, Microsoft Azure VM      |
  | PaaS (Platform as a Service)       | 인프라 + 런타임 환경 제공. 애플리케이션 개발과 배포에 집중할 수 있으며 자동 확장과 로드 밸런싱 기능 지원         | Heroku, AWS Elastic Beanstalk    |
  | SaaS (Software as a Service)       | 완성된 소프트웨어를 인터넷으로 제공. 사용자는 설치 없이 웹에서 바로 사용 가능                                    | Gmail, Google Workspace, Dropbox |

- 서버리스 컴퓨팅 서비스 종류

  - BaaS (Backend as a Service)

    - 미리 구축된 백엔드 기능(API, 인증, 데이터베이스, 파일 저장 등)을 서비스 형태로 제공

    - 개발자가 직접 서버 코드를 작성하지 않아도 기능을 쉽게 사용할 수 있음

    - 사용량 기반 과금

    - 예시: Firebase, AWS Cognito, Auth0

  - FaaS (Function as a Service)

    - 코드를 함수 단위로 작성해 클라우드에서 이벤트 기반으로 실행하는 컴퓨팅 서비스

    - 서버 프로비저닝, 관리 불필요

    - 함수가 호출되면 클라우드 환경에서 실행 후 종료, 사용한 만큼 비용 지불

    - 특징:

      - 무상태(stateless)로 설계해야 함 (함수 간 상태 공유 불가, 로컬 스토리지 등 로컬 데이터 사용 불가)

      - 콜드 스타트 문제 존재 (처음 호출 시 실행 지연)

      - 자원의 제한, 실행 시간 및 메모리 제한 존재 (예: AWS Lambda는 최대 15분, 메모리 최대 10GB 등)

    - 용도 예시: API 백엔드, 이미지 리사이징, 데이터 처리, 자동화 작업 등

    - 예시: AWS Lambda, Azure Functions, Google Cloud Functions

<br><br><br>
