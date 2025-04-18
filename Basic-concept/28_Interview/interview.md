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
