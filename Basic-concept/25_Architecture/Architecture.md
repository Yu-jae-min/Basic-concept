## # Architecture

<br>

### # 모노레포(Monorepo) 구성을 위한 터보레포(Turborepo)

- 프로젝트 구성 방식

  - 모놀리식(Monolithic)

    - 개념

      최초의 모놀리식 방식은 애플리케이션의 모든 기능이 하나의 프로젝트 안에서 함께 개발되고 배포되는 구조를 말한다. 모든 코드가 단일 코드베이스로 구성되며, 서로 직접 의존한다.

    - 장점

      1. 코드 재사용이 쉽다.

      2. 빌드 및 배포 과정이 단순해 소수의 개발자가 빠르게 개발할 수 있다.

    - 단점

      1. 관심사 분리가 어렵다.

      2. 하나의 기능을 변경해도 전체 애플리케이션을 다시 빌드하고 배포해야 하는 등 유지보수가 어렵다는 단점이 있다.

  - 멀티레포(Multi-Repo)

    - 개념

      멀티레포는 기능별 또는 도메인별로 소스 코드를 모듈화하고, 각 모듈을 별도의 저장소로 관리하는 구조이다.

    - 장점

      1. 관심사 분리가 쉽다.

      2. 각 모듈이 독립적으로 개발, 테스트, 배포될 수 있어 팀 단위의 작업 분리가 용이하다.

    - 단점

      1. 저장소가 분산되어 있기 때문에 코드 공유와 일관된 컨벤션 유지가 어렵다.

      2. 의존성 관리 및 버전 충돌 등으로 인해 빌드와 배포가 복잡해질 수 있다.

  - 모노레포(Mono-Repo)

    - 개념

      모노레포는 여러 개의 프로젝트(또는 패키지)를 하나의 저장소에 함께 관리하는 구조로, 멀티레포의 관심사 분리 장점과 모놀리식의 일관된 개발 환경을 모두 지향한다.
      모노레포의 대표적인 장점은 다음과 같다. `모노레포`는 이와 같은 모놀리식 레파지토리와 멀티레포의 장점을 모두 취하고자 등장했다. 노레포 구성을 도와주는 프레임워크는 Lerna, yarn workspace, Nx, Turborepo 등이 있다.

    - 장점

      1. 프로젝트 파악 수월 : 모든 커밋과 변경 이력이 하나의 저장소에 남기 때문에, 히스토리를 추적하거나 전체 구조를 이해하기 쉽다.

      2. 코드 재사용성 증가 : 공통 코드(예: 유틸 함수, 컴포넌트, 테스트 도구 등)를 하나의 패키지로 관리하며 여러 프로젝트에서 쉽게 사용할 수 있다.

      3. 배포, 빌드, 테스트 속도 향상 : 작업을 병렬로 실행하거나 변경된 프로젝트만 선별적으로 처리할 수 있어 효율적이다.

    - 단점

      1. 초기 설정과 관리가 복잡하다 : 여러 프로젝트를 한 저장소에 관리하려면 빌드 도구, 의존성 관리, 배포 파이프라인을 잘 설계해야 해서 초기 세팅이 까다롭고 복잡할 수 있다.

      2. 대형 저장소로 인한 성능 문제 : 커밋, 검색, 빌드 시 전체 저장소 크기가 커지면 속도가 느려질 수 있다. 특히 Git 히스토리 관리나 CI/CD 빌드 시간이 오래 걸릴 수 있다.

      3. 권한 관리 어려움 : 저장소가 하나라서, 특정 프로젝트나 팀 단위로 권한을 세분화하기가 어렵다. 민감한 프로젝트가 섞여있으면 보안 이슈가 될 수 있다.

      4. 코드 변경 영향 범위 파악 어려움 : 큰 저장소 내에서 공유되고 있는 한 부분을 변경하면 어떤 프로젝트에 영향이 있을지 정확히 파악하기 어려울 수 있다.

- 터포레포(Turborepo)

  - 터포레포(Turborepo)란?

    Vercel이 인수한 Turborepo는 JavaScript와 TypeScript 코드 베이스의 모노레포를 위한 고성능 빌드 시스템이다. Vercel과 AWS, Miro, PayPal, Discord,
    LINE+의 Universal Video Player 등 여러 프로젝트에서 프로덕션 단계로 사용하고 있으며 지금도 활발하게 개발이 진행되고 있다.

    Turborepo의 주요 미션은 모노레포 환경에서 개발자가 조금 더 쉽고 빠르게 개발할 수 있도록 빌드 도구를 제공하는 것이다. 고급 빌드 시스템을 구축하는 복잡한 과정을
    Turborepo가 대신해 주기 때문에 개발자는 복잡한 설정과 스크립트에 신경 쓰는 대신 개발에 더 집중할 수 있다. Turborepo의 기본 원칙은 한 번 작업을 수행하며
    수행한 계산은 이후 다시 수행하지 않는 것이다. 따라서 두 번째 실행할 때는 이전에 계산한 작업은 건너뛰고 이전에 캐싱해 놓은 로그를 다시 보여준다.

  - 터보레포 특징

    1. 빠른 빌드 속도(Incremental builds) : 작업 결과를 캐싱해서 이미 처리된 부분은 다시 빌드하지 않는다. 빌드를 한 번만 수행하는 것을 목표로 한다.

    2. 빌드 시 변경된 부분만 처리(Content-aware hasing) : 파일 변경 여부를 타임스탬프가 아닌 실제 파일 콘텐츠 기반으로 판단한다. 따라서 변경된 파일만 빌드하여 불필요한 재빌드를 방지한다.

    3. 클라우드 캐시 공유(Cloud caching) : 빌드 캐시를 클라우드에 저장하여 팀원과 CI/CD 환경 간에 공유한다. 덕분에 로컬뿐 아니라 클라우드 환경에서도 빠른 빌드가 가능하다

    4. 병렬 작업(Parallel execution) : 작업(task) 간 의존성을 분석해 가능한 한 모든 CPU 코어를 활용해 병렬로 빌드와 테스트를 실행한다.

    5. 의존성 기반 Task 실행(Task Pipelines) : 작업 간 연결 관계를 정의해 어떤 순서로 빌드를 실행할지 최적화한다.

    6. 불필요한 런타임 오버헤드 없음(Zero Runtime Overhead) : 런타임에 추가 코드나 소스맵을 삽입하지 않아 빌드된 코드의 성능이나 안정성에 영향을 주지 않는다.

    7. PaaS 배포 최적화 (Pruned Subsets) : 모노레포 내에서 필요한 부분만 골라 하위 집합(subset)을 만들어 PaaS 배포 시 효율성을 높인다.

    8. 설정이 비교적 간단(JSON configuration) : 별도 코드 작성 없이 JSON 설정만으로 쉽게 터보레포를 구성하고 사용할 수 있다.

    9. 시각화 도구 제공(Profile in browser) : 빌드 프로파일을 시각화해 쉽게 병목 구간을 파악할 수 있어 성능 최적화에 도움을 준다.

<br>

### # Micro Frontends Architecture

- Micro Frontends Architecture

  마이크로 프론트엔드는 마이크로서비스 아키텍처를 프론트엔드에 적용한 개념으로, 각 UI 혹은 페이지 단위를 독립된 애플리케이션처럼 구성하고 조합하여 하나의 웹 앱을 만든다.
  즉 각각 독립된 환경에서 나누어 개발, 배포되어 조립하는 방식이다.

- Micro Frontends의 적용 시점, 장단점

  - 적용 시점

    - 공통 UI가 많고 페이지 간 연관성이 높은 경우

    - 앱 규모가 크고 도메인 복잡도가 높은 경우

    - 배포 단위를 작게 나누고 싶은 경우

  - 메인 컨셉

    - 컨텍스트 독립성

      - 각 앱은 상태, 전역 변수 등을 공유하지 않고 독립적으로 동작해야 한다.

    - 네임스페이스를 분리

      - 마이크로 앱 각 작동 단위의 격리(완전히 격리된 환경)가 불가능한 경우 CSS, localStorage, 이벤트, 쿠키 등에 prefix를 붙여 충돌을 방지한다.

    - 브라우저 기반 통신

      - 마이크로 앱 간 통신은 브라우저 이벤트 등 기본 기능을 활용하여 단순하게 처리한다.

    - 탄력적인 웹 설계

      - JS 에러 상황에서도 기능이 동작해야 하며, 점진적 향상(Progressive Enhancement)와 범용 렌더링(Universal Rendering)을 통해 성능과 안정성을 확보한다.

- 컴포넌트 분리 vs 마이크로 프론트엔드

  | 항목           | **컴포넌트 분리**                         | **마이크로 프론트엔드 (MFE)**      |
  | -------------- | ----------------------------------------- | ---------------------------------- |
  | **분리 단위**  | UI 구성 요소 수준 (버튼, 카드, 페이지 등) | 애플리케이션 수준 (페이지, 기능군) |
  | **코드베이스** | 하나의 프로젝트 내에서 분리               | 서로 다른 리포지토리/프로젝트      |
  | **배포**       | 하나의 앱으로 통합 배포                   | 각 앱이 독립적으로 배포 가능       |
  | **개발팀**     | 하나의 팀이 전반 관리                     | 기능별로 다른 팀이 병렬 개발 가능  |
  | **기술스택**   | 동일한 스택이 기본                        | 서로 다른 프레임워크/버전도 가능   |

  - 팀 간 완전한 독립 개발

    - 대규모 조직에서는 여러 팀이 동시에 프론트엔드를 개발해야 할 때가 많아.

    - 이때 하나의 프로젝트에서 충돌이 많고, 빌드/배포도 병목이 생겨.

    - MFE는 코드, 빌드, 배포까지 완전히 분리하니까 병렬 작업이 가능해.

  - 배포 리스크 최소화

    - 기존 앱에서 작은 변경도 전체 빌드를 다시 해야 함.

    - 반면 MFE는 특정 기능만 업데이트하고 배포할 수 있어 → 롤백도 쉬움.

  - 레거시와의 공존

    - 예를 들어 기존에 Vue로 만들어진 페이지가 있고, 새로 React로 만들고 싶을 때.

    - MFE는 서로 다른 프레임워크를 한 화면에서 공존하게 할 수 있어.

  - 스케일을 위한 아키텍처

    - 도메인이 커지고 복잡도도 높아지면, 컴포넌트 단위로는 관리가 어려워져.

    - 기능군별로 완전히 분리하면 스케일에 강한 구조가 돼.

- 장단점

  - 장점

    - 작고, 응집력 있고 유지보수에 용이한 코드베이스를 가질 수 있다. 따라서 디커플링이라는 소프트웨어 개발 목표를 달성한다.

    - 각 마이크로 프론트엔드는 고유한 기술 및 프레임워크를 선택할 수 있다. 독립적으로 구현, 테스트, 업그레이드, 업데이트 및 배포할 수 있어 팀에 유연성을 제공한다.

    - 프론트엔드 개발을 점진적 업그레이드 또는 재작성이 수월해진다.

    - 마이크로 프론트엔드는 수직 팀을 장려한다. 수직 팀에는 일반적으로 기능 소유자, UX 디자이너, 제품 관리자, 백엔드 개발자, 프론트엔드 개발자 및 품질 보증 엔지니어가 포함된다.

  - 단점

    - 마이크로 프론트엔드는 분리되거나 느슨하게 결합 된 구성 요소를 위해 설계되었다. 그들 사이에 너무 많은 종속성을 넣으려고하면 디버깅 악몽이 발생할 수 있다.

    - 마이크로 프런트 엔드를 가능하게하는 파이프라인으로 인해 복잡도가 증가한다. 외부로드 문제를 해결하려면 기술적 전문 지식이 필요하며 디버깅 프로세스에는 시간이 많이 걸린다. 또한 SSO (Single Sign-On), 글로벌 CSS 등과 관련된 문제에 직면 할 수 있다.

    - 각 마이크로 프런트 엔드에는 중복 된 코드 또는 기능이 있을 수 있다. 예를 들어, React 라이브러리는 각 마이크로 프런트 엔드에 포함될 수 있어, 번들 크기와 메모리 소비를 증가시킨다.

    - 런타임 시 마이크로 프런트 엔드를 동적 또는 지연로드하는 데 추가 시간이 걸린다.

    - 사용자 인터페이스는 여러 팀에서 설계되었으므로 UX 설계는 마이크로 프런트 엔드에서 일관되지 않을 수 있다.

- Micro Frontends 통합 방법

  - 공통적으로 존재하는 아키텍처

    - 대부분의 MFE 구현은 “Shell (컨테이너 앱)” + “Micro Apps (각 기능 모듈)” 구조를 사용함

    - 컨테이너 앱의 역할

      - 공통 레이아웃 (헤더/푸터)

      - 인증, 라우팅, 퍼미션 제어

      - 어떤 마이크로 앱을 언제 어디서 렌더링할지 제어

  - 서버 사이드 템플릿 통합

    서버에서 각 마이크로 앱의 HTML을 조립해서 클라이언트에 반환.

  - 빌드타임 통합

    각 마이크로 앱을 NPM 패키지처럼 배포하고, 컨테이너 앱에서 가져다 씀. 앱 변경 시 반드시 컨테이너 앱 다시 빌드해야 함 → 독립 배포 불가

  - iframe을 통한 런타임 통합

    URL로 분리된 앱을 iframe으로 로딩

  - Web Components를 통한 런타임 통합

    웹 컴포넌트는 독립적인 UI 단위로, HTML의 Custom Element (예: `<my-app-header>`) 형태로 정의됨. 빌드 결과는 자바스크립트 번들로 생성되며, 컨테이너 앱에서 `<script>` 태그로 로드
    로드된 스크립트가 커스텀 엘리먼트를 브라우저에 등록하고, 해당 태그가 DOM에 있을 때 웹 컴포넌트가 실행되어 UI를 렌더링. 이를 통해 마이크로 앱을 컨테이너 앱에 런타임에 내장(통합) 가능

  - Javascript를 통한 런타임 통합

    Webpack Module Federation, SystemJS, Import Maps 등을 사용, 앱을 번들 단위로 나누고 런타임에 필요한 앱만 동적으로 로딩

    - 앱이 다른데 어떻게 번들을 공유할까? Webpack Module Federation를 통해 가능

      Webpack Module Federation를 통해 가능, 앱을 번들링할 때, 일부 모듈을 “외부에 노출(export)”시키고 런타임에 네트워크로 JS 모듈을 불러와 사용하는 구조

      ```js
      // 📦 app1 (Remote)
      // webpack.config.js
      module.exports = {
        name: "app1",
        exposes: {
          "./Button": "./src/components/Button", // 외부에서 사용할 수 있게 export
        },
        filename: "remoteEntry.js",
      };
      ```

      ```js
      // 🏠 app2 (Host)
      // webpack.config.js
      module.exports = {
        name: "app2",
        remotes: {
          app1: "app1@https://app1.example.com/remoteEntry.js",
        },
      };
      ```

      ```js
      // App.tsx
      const RemoteButton = React.lazy(() => import("app1/Button"));

      function App() {
        return (
          <Suspense fallback={<div>Loading...</div>}>
            <RemoteButton />
          </Suspense>
        );
      }
      ```

- Micro Frontends 통합 고려사항

  - 스타일링

    - BEM과 같은 엄격한 네이밍 규칙 사용

    - SASS와 같은 전처리기를 통해 상위 선택자 추가 등을 통해 독립성 유지

    - 모든 스타일을 CSS-in-JS 방식으로 처리

    - Shadow DOM: 메인 document DOM 으로부터 독립적으로 렌더링 되는 캡슐화된 Shadow DOM 트리를 엘리먼트에 추가하고, 연관된 기능을 제어하기 위한 JavaScript API 의 집합. 이 방법으로 엘리먼트의 기능을 프라이빗하게 유지할 수 있어, 다큐먼트의 다른 부분과의 충돌에 대한 걱정 없이 스크립트와 스타일을 작성할 수 있다.

  - Component Library 공유

    - 마이크로 앱들 간의 시각적 일관성을 유지하기 위해 재사용 가능한 UI 컴포넌트 라이브러리를 개발하여 공유한다. 코드 재사용성과 시각적 일관성을 유지할 수 있다.

    - 너무 일찍 만드는 것은 좋지 않다. 실제로 사용하기 전에 컴포넌트의 API가 무엇이어야 하는지 추측하기는 쉽지 않다. 그러므로 많은 변동이 발생하게 되므로, 초기에는 일부 중복이 발생하더라도 각 팀이(각 마이크로 앱 내에서) 코드베이스에서 필요에 따라 자체 컴포넌트를 만들어두는 것이 좋다. 패턴이 자연스럽게 나타나도록 허용하고, 컴포넌트의 API가 명확해지면 그 때 만드는 것을 권장한다.

  - 애플리케이션 간 커뮤니케이션

    - 가능한 적은 소통을 하는 것이 좋다.

    - Custom events를 사용하면 마이크로 앱들이 간접적으로 통신할 수 있다. 이는 직접 결합을 최소화하는 좋은 방법이지만, 마이크로 앱들 간 약속을 정하고 구현해야 하므로 더 어려울 수 있다.

    - 콜백과 데이터를 아래쪽으로 전달하는 React 모델로 약속을 명확하게 정하는 것도 좋은 솔루션이다.

    - URL 표시 줄을 통신 메커니즘으로 사용하는 것도 좋은 방법이다.

    - 어떤 방식을 선택하든, 서로 메시지 또는 이벤트를 전송하여 통신하는 것이 좋으며, 공유 상태를 갖는 것은 좋은 선택지가 아니다. 마이크로 서비스에서 데이터베이스를 공유하는 것이 좋지 않은 것처럼, 데이터 구조와 도메인 모델을 공유하자마자 엄청난 양의 결합이 생기게 되고, 변경에 많은 제약이 따르기 때문이다.

    - vuex는 일반적으로 하나의 응용 프로그램에 대해 단일 전역 공유 저장소를 기본으로 한다. 그러나 각 마이크로 앱들이 자체 저장소를 갖는 것이 더 합리적이다.

  - 백엔드 통신

    - BFF(Backend for Frontend Pattern) 패턴으로 프론트앤드 전용 API를 갖는다. 각 마이크로 앱들은 해당 프론트 엔드의 요구사항만 충족하는 목적을 가진 백엔드만을 가진다.

    - 별도의 데이터베이스를 가질 수도 있다.

    - 로그인 인증 정보는 통합하는 Container가 소유한다. 초기화 시 인증을 통해 얻은 토큰을 각 마이크로 프론트엔드에 주입되며, 마이크로 프론트엔드는 서버에 대한 요청과 함께 토큰을 보내고, 해당 마이크로 앱의 백엔드에서는 필요한 모든 유효성 검사를 수행하는 방식으로 구성할 수 있다.

<br><br><br>
