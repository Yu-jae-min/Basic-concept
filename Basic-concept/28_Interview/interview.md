## # interview

### # 스토리북 구축 및 배포

- 스토리북을 구성하기 위해 기본 애드온 사용

  - @storybook/preset-create-react-app: CRA 환경에서 Storybook 세팅 쉽게 해줌
  - @storybook/addon-onboarding: Storybook 입문자용 가이드 제공
  - @storybook/addon-links: 스토리 간 링크 연결
  - @storybook/addon-essentials: 인기 애드온 세트 (controls, actions, docs, viewport 등)
  - @storybook/addon-interactions: 플레이 기능 및 상호작용 테스트 지원

- stories 파일을 통해 스토리 생성

  - meta를 통해 스토리의 메타 데이터 설정 (title, component, tags, parameters, argTypes 등)
  - 그 외 스토리는 미리보기용 컴포넌트

- 기타 설정

  - Autodocs 설정을 통해 자동 문서화
  - main 파일에 `*.stories.tsx` 파일 생성 시 자동으로 추가되도록 구현

- 배포

  - 공유를 위해 배포하는데 S3, cloudfront를 활용해서 배포

- 모노레포 구축 및 배포

  - 터보레포의 book-it-now-shop에서 로컬 패키지가 dependencies인 이유, 그리고 peerDependencies

    - apps/bookitnow-shop/package.json 분석

      - peerDependencies : peerDependencies의 역할은 해당 라이브러리가 특정 버전으로 설치되어있어야함을 명시하는 것이다. 우리 프로젝트의 구조 중 book-it-now-shop의 경우 peerDependencies 내부 패키지들의 버전을 와일드 카드(`*`)로 설정하였는데 이런 경우에는 root package.json에 명시된 버전으로 설치되어있어야 함을 의미한다. 즉 root package.json에 의해 이미 설치되어 있는 패키지 버전을 따라간다는 것이다.

      - dependencies : dependencies의 경우 운영 환경에서 필요한 패키지를 설치한다고 알고 있는데 터보레포에서 생성되는 로컬 패키지(`ex @repo/ui`) 또한 여기에 포함되어야한다. peerDependencies에 포함될 수 없는 이유는 외부 라이브러리와 같이 root package.json에 버전을 명시하여 설치하는 방식이 아닌 로컬에서 생성한 패키지이기 때문이다. 그렇기 떄문에 별도로 생성된 로컬 패키지의 package.json을 참고하여 설치하게 된다. `(ex { "name": "@repo/ui", "version": "1.0.0", … })`

    - peerDependencies vs dependencies 요약

      - peerDependencies는 특정 패키지가 다른 패키지를 필요로 하지만, 그 패키지를 직접 포함하지 않고, 상위 프로젝트(패키지를 설치하는 프로젝트)에서 해당 의존성을 설치하도록 요구하는 방식

  - turbo.json

    - tasks 내부에서 bookitnow-client#build와 같이 각 프로젝트 혹은 build로 공통 빌드 설정을 적용, dependsOn의 경우 ^build로 설정하여 부모 혹은 의존하는 패키지들의 build 작업을 먼저 실행

  - packages

    - 공통 패키지 package.json 공통 요소

    - type의 경우 docker + openapitools/openapi-generator-cli를 통해 타입을 자동생성

  - 공통 apis, icons, logics, types, ui를 관리
