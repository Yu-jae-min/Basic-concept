# [Architecture] 모노레포(Monorepo) 구성을 위한 터보레포(Turborepo)

2023년 09월 24일

<br>

# 1. 프로젝트 구성 방식과 모노레포(Monorepo)

![etc_모노레포_Monorepo_구성을_위한_터보레포_Turborepo_01](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/4c8d9e5a-1d24-438f-8a3b-da7fdc11e3cc)

<br>

## 1-1. 모놀리식(Monolithic)

최초의 `모놀리식` 방식은 소스 코드를 모듈화하지 않고 하나의 리포지터리에 모두 넣었다고 생각하면 된다. 모든 코드가 `단일 버전`으로 서로 직접 의존하기 때문에 코드 재사용이 용이하고 빌드 및 배포 과정도 단순하여 소수의 개발자가 빠르게 개발할 수 있다는 장점이 있다.

하지만 관심사 분리가 어렵고 기능 추가나 삭제가 레파지토리 전체에 영향을 줄 수 있으며 매번 거대한 프로젝트를 배포해야한다는 단점이 있다.

이러한 단점을 해결하고자 멀티 레포가 등장하게 된다.

<br>

## 1-2. 멀티레포(Multi-Repo)

`멀티레포` 방식에서는 소스 코드를 모듈화한 뒤 각 모듈에 `독자적인 영역을 부여(별도의 저장소)하고 버전 관리를 통해` 관심을 분리해서 기능 변경이 다른 레파지토리에 직접 영향을 미치지 않도록 개선했다. 다른 프로젝트와 의존성을 가지고 있지 않아 독립적으로 개발이 가능하고 관심사 분리가 쉬우며 개발, 테스트, 빌드 배포가 각각 존재한다.

하지만 각 모듈이 서로 독립된 영역에 존재하기 때문에 코드 코드 컨벤션 통일 및 코드 재사용이 어려워지고 관리 포인트가 증가하며 빌드와 배포 과정이 복잡해진다는 단점이 있다.

<br>

## 1-3. 모노레포(Mono-Repo)

`모노레포`는 이와 같은 모놀리식 레파지토리와 멀티레포의 장점을 모두 취하고자 등장했다. 단일 레파지토리에 여러 개의 서브 프로젝트가 존재하는 방식이다. 모노레포의 장점은 아래와 같다.

- 프로젝트 파악 수월 : 모든 커밋 히스토리가 한 레파지토리에 남기 때문에 히스토리를 추적하거나 전체 레파지토리의 개발 방향을 이해하는 게 쉬워지며 모든 프로젝트의 코드와 자원(assets) 간의 관계와 의존성을 한눈에 확인할 수 있다.
- 코드 재사용성 증가 : 여러 곳에서 중복으로 사용하는 자산들(테스트 코드 등)을 공유하고 재사용할 수 있다.
- 배포, 빌드, 테스트 속도 향상 : 배포와 빌드, 테스트와 같은 작업을 병렬로 한 번에 처리할 수 있으므로 한 번의 명령으로 여러 개의 레파지토리에서 작업을 진행할 수 있다.

모노레포 구성을 도와주는 프레임워크는 Lerna, yarn workspace, Nx, Turborepo 등이 있지만 이 중 Vercel이 인수하여 개발 중인 Turborepo에 대해 알아보자.

<br>
<br>

# 2. 터포레포(Turborepo)

[Turborepo Quickstart – Turborepo](https://turbo.build/repo/docs)

Vercel이 인수한 Turborepo는 JavaScript와 TypeScript 코드 베이스의 모노레포를 위한 고성능 빌드 시스템이다. Vercel과 AWS, Miro, PayPal, Discord, LINE+의 Universal Video Player 등 여러 프로젝트에서 프로덕션 단계로 사용하고 있으며 지금도 활발하게 개발이 진행되고 있다.

Turborepo의 주요 미션은 모노레포 환경에서 개발자가 조금 더 쉽고 빠르게 개발할 수 있도록 빌드 도구를 제공하는 것이다. 고급 빌드 시스템을 구축하는 복잡한 과정을 Turborepo가 대신해 주기 때문에 개발자는 복잡한 설정과 스크립트에 신경 쓰는 대신 개발에 더 집중할 수 있다. Turborepo의 기본 원칙은 한 번 작업을 수행하며 수행한 계산은 이후 다시 수행하지 않는 것이다. 따라서 두 번째 실행할 때는 이전에 계산한 작업은 건너뛰고 이전에 캐싱해 놓은 로그를 다시 보여준다.

<br>

## 2-1. 터보레포의 특징

Turborepo는 아래 9가지 특징을 기반으로 Turborepo를 사용해야 하는 이유를 설명한다.

1. Incremental builds : 작업 진행을 캐싱해 이미 계산된 내용은 건너 뛰는 것을 의미한다. 빌드는 딱 한 번만 하는 것을 목표로 한다.

   ![etc_모노레포_Monorepo_구성을_위한_터보레포_Turborepo_02](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/187f8b93-53ed-4b5e-9a7f-57d4c8caaef7)

2. Content-aware hasing : 타임스탬프가 아닌 콘텐츠를 인식하는 방식으로 해싱을 지원한다. 이를 통해 모든 파일을 다시 빌드하는 것이 아니라 변경된 파일만 빌드한다.
3. Cloud caching : 클라우드 빌드 캐시를 팀원 및 CI/CD와 공유한다. 이를 통해 로컬 환경을 넘어 클라우드 환경에서도 빠른 빌드를 제공한다.
4. Parallel execution : 모든 코어를 사용하는 병렬 실행을 목표로 한다. 지정된 태스크 단위로 의존성을 판단해 최대한 병렬적으로 작업을 진행한다. (멀티태스킹 능력 극대화)

   ![etc_모노레포_Monorepo_구성을_위한_터보레포_Turborepo_03](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/bbeee194-b45b-4916-90b0-1fc8f152db8c)

5. Task Pipelines : 태스크 간의 연결을 정의해서 빌드를 언제 어떻게 실행할지 판단해 최적화한다.
6. Zero Runtime Overhead : 런타임 코드와 소스 맵을 다루지 않기 때문에 런타임 단계에서 파악하지 못한 리스크가 불거질 위험이 없다.
7. Pruned subsets : 빌드에 필요한 요소만으로 모노 레포의 하위 집합을 생성해 PaaS(Platform as a Service) 배포 속도를 높인다.
8. JSON configuration : 별도의 코드 작업 없이 JSON 설정으로 터보를 사용할 수 있다.

   ```json
   // turbo.json
   {
   	"baseBranch": "origin/main",
   	"pipeline": {
   		"build": {
   			...
   		}
   	}
   }
   ```

9. Profile in browser : 빌드 프로필로 빌드 과정을 시각화하면 병목 지점을 쉽게 찾을 수 있다.

   ![etc_모노레포_Monorepo_구성을_위한_터보레포_Turborepo_04](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/0525fc2c-ab6a-4668-9eef-18ad2b218057)

<br>

## 2-2. 터보레포 간단한 사용법

모노레포의 루트 디렉터리에 `turbo.json` 파일을 생성한 후 [파이프라인(pipeline)](https://turborepo.org/docs/features/pipelines)을 작성한다. 파이프라인의 각 명령어들은 하나의 태스크 단위이며 이 단위가 '병렬 처리 및 의존성의 범위'가 된다.

```json
{
  "baseBranch": "origin/main",
  "pipeline": {
    // 스크립트와 매핑되는 태스크 이름을 작성한다.
    "build": {
      // ^는 커맨드 실행 전 dependencies 혹은 devDependencies의 위상 의존성을 가질 때 명시해 준다. (https://turborepo.org/docs/glossary#topological-order)
      // 의존성 빌드 명령이 실행된 후 build 커맨드가 실행된다.
      "dependsOn": ["^build"],
      // 기본 캐시 폴더를 지정한다.
      "outputs": [".next/**", "lib/**", "storybook-static/**"]
    },
    "cypress:ci": {
      "dependsOn": [
        // 특정 패키지를 지정하고 싶다면 '패키지명#스크립트'로 하면 된다.
        "@linecorp/uvp#build"
      ]
    },
    // 아무런 명시가 없다면 의존성이 없다는 것을 의미하며, 이는 언제든지 실행될 수 있다는 것을 의미한다.
    // 작업이 가능할 때마다 실행한다.
    "lint": {},
    "deploy": {
      // 의존성을 여러 개 지정할 경우 터보가 똑똑하게 순서를 맞춰서 진행해 준다.
      "dependsOn": ["build", "cypress:ci", "snapshots", "lint"]
    },
    // 개발 환경과 같이 핫 로딩이 필요할 경우 캐시를 비활성화할 수 있다.
    "dev": {
      "cache": false
    }
  }
}
```

JSON 파일을 생성했다면 이제 아래와 같이 Turborepo를 설치한다.

```powershell
$ yarn add turbo -DW # devDependency, install workspace root
$ turbo run build # yarn uvp build, yarn storybook build 등 의존성을 가진 모든 package 스크립트가 실행된다.
```

파이프라인의 키 명령어들은 각 모노레포의 `package.json` 스크립트와 매핑된다. 만약 패키지 스크립트에 없는 명령어라면 해당 모노레포에서는 무시된다. 만약 A 패키지에는 린트(lint) 스크립트가 있지만 B 패키지에는 린트 스크립트가 없다면 A 패키지만 실행된다.

위와 같이 CLI로 설치해도 되고, 아래와 같이 최상위 package.json 파일에서 명령을 실행할 수도 있다.

```json
"scripts": {
  "build": "turbo run build",
}
```

<br>

## 2-3. 한 작업공간에서만 dev 스크립트 실행하기

기본적으로 turbo dev는 모든 작업공간에 있는 dev 명령어를 한번에 실행하지만, 때때로 한 가지 작업 공간만 수행하고자 할 때가 있다. 이를 위하여 --filter 플래그를 명령어에 추가할 수 있다.

```powershell
turbo dev --filter docs
```

<br>

## 2-4. 스크립트의 시각화

`--graph`와 `--profile` [CLI](https://turborepo.org/docs/reference/command-line-reference)를 이용하면 빌드 과정의 흐름과 소요 시간을 쉽게 확인할 수 있다.

먼저 아래와 같이 `--graph` 옵션으로 태스크를 실행하면 파이프라인에서 지정한 태스크의 관계를 그래프로 표현해 이미지 파일로 제공한다.

```powershell
$ turbo run TASK --graph
```

![etc_모노레포_Monorepo_구성을_위한_터보레포_Turborepo_05](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/74c0f919-127d-4bdd-8a19-59b703cda0e0)

다음으로 `--profile` 옵션을 사용하면 빌드가 어떤 식으로 진행됐고 어디가 병렬로 처리됐는지, 시간은 얼마나 걸렸는지 프로파일이 작성된 JSON 파일이 생성된다.

```powershell
$ turbo run TASK --profile
```

![etc_모노레포_Monorepo_구성을_위한_터보레포_Turborepo_06](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/9b92c298-35ee-4607-a5c8-7df48b5078d2)

이 파일은 Chrome 개발자 도구의 Performance 탭에서 확인할 수 있다. Performance 탭에서 아래 표시한 화살표 버튼을 클릭한 후 생성된 JSON 파일을 선택하면 시각화된 프로파일 정보를 확인할 수 있다.

![etc_모노레포_Monorepo_구성을_위한_터보레포_Turborepo_07](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/9d914445-3bc1-4de0-85d7-2787bff23575)

아래와 같이 브라우저에서 시각화한 프로파일 정보를 살펴보면 빌드 과정을 쉽게 파악할 수 있고 태스크의 병목 지점을 빠르게 찾을 수 있다.

![etc_모노레포_Monorepo_구성을_위한_터보레포_Turborepo_08](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/5208992a-8e46-4ab8-a56f-42b75284a928)

<br>
<br>

# #. 참고 URL

- https://turbo.build/repo/docs
- https://engineering.linecorp.com/ko/blog/monorepo-with-turborepo
- https://beomy.github.io/tech/etc/monorepo-concept/
- https://dev-scratch.tistory.com/161
