## # GraphQL

<br>

### # GraphQL 특징

- GraphQL 은 REST 보다 효율적이고 강력하며 유연한 대안을 제공하는 새로운 API 표준입니다.

- Facebook에서 개발하고 오픈소스 로 개발했으며 현재 전 세계의 대규모 기업 및 개인 커뮤니티에서 관리하고 있습니다.

- 핵심적으로 GraphQL은 클라이언트가 API에서 필요한 데이터를 정확히 지정할 수있는 선언적(decalarative) 데이터 가져 오기를 지원합니다.

- 고정 데이터 구조를 반환하는 여러 엔드 포인트 대신 GraphQL 서버는 단일 엔드 포인트만 노출하고 클라이언트가 요청한 데이터로 정확하게 응답합니다.

<br>

### # GraphQL 장점

REST는 서버에서 데이터를 노출하는 인기있는 방법이었습니다. REST 개념이 개발되었을 때 클라이언트 애플리케이션은 비교적 단순했고 개발 속도는 현재와 거의 같지 않았습니다. 따라서 REST는 많은 애플리케이션에 적합했습니다. 그러나 API 환경은 지난 몇 년 동안 급격히 변화했습니다. 특히 API 설계 방식에 어려움을 겪고있는 세 가지 요소가 있습니다.

1. 모바일 사용 증가로 인해 효율적인 데이터로드가 필요합니다.
   Facebook이 GraphQL을 개발 한 초기 이유는 증가 된 모바일 사용, 저전력 장치 및 엉성한 네트워크였습니다. GraphQL은 네트워크를 통해 전송해야하는 데이터의 양을 최소화하여 이러한 조건에서 작동하는 애플리케이션을 크게 개선합니다.

2. 다양한 프런트엔드 프레임워크 및 플랫폼
   클라이언트 애플리케이션을 실행하는 프런트엔드 프레임워크 및 플랫폼의 이기종 환경으로 인해 모든 요구 사항에 맞는 하나의 API를 구축하고 유지 관리하기가 어렵습니다. GraphQL을 통해 각 클라이언트는 필요한 데이터에 정확하게 액세스 할 수 있습니다.

3. 빠른 기능 개발을위한 빠른 개발 및 기대
   지속적인 배포는 많은 회사의 표준이되었으며 빠른 반복과 빈번한 제품 업데이트는 필수 불가결합니다. REST API를 사용하면 클라이언트 측의 특정 요구 사항 및 설계 변경을 고려하여 서버에서 데이터를 노출하는 방식을 수정해야하는 경우가 많습니다. 이는 빠른 개발 관행과 제품 반복을 방해합니다.

<br>

### # SDL : The Schema Definition Language

- 특징

```tsx
const typeDefs = gql`
  type SpaceCat {
    name: String!
    age: Int
    missions: [Mission]
  }
`;
```

```tsx
type Lift {
  id: ID!
  name: String!
  status: LiftStatus
  capacity: Int!
  night: Boolean!
  elevationGain: Int!
  trailAccess: [Trail!]!
}
```

<br>

### # SDL Type

- Track Type : "트랙은 특정 주제에 대해 가르치는 모듈 그룹입니다."
- Author Type : "완전한 트랙의 저자"
- Query Type : "홈페이지 그리드에 대한 트랙 배열 가져오기"
- Query < Track < Author

```tsx
"Get tracks array for homepage grid"
type Query {
  tracksForHome: [Track!]!
}

"A track is a group of Modules that teaches about a specific topic"
type Track {
  id: ID!
  title: String! // "The track's title : 트랙 제목"
  author: Author! // "The track's main author : 트랙의 주요 저자"
  thumbnail: String //  "The track's main illustration to display in track card or track page detail : 트랙 카드 또는 트랙 페이지 세부 정보에 표시할 트랙의 기본 그림"
  length: Int // "The track's approximate length to complete, in minutes : 트랙의 대략적인 완료 길이(분)"
  modulesCount: Int // "The number of modules this track contains : 이 트랙에 포함된 모듈 수"
}

"Author of a complete Track"
type Author {
  id: ID!
  name: String! // "Author's first and last name : 저자의 성과 이름"
  photo: String // "Author's profile picture url : 작가 프로필 사진 url"
}
```

- Object Type

  - 해당 타입의 특성을 표현하는 필드들로 구성됩니다.

- Enums Type

GraphQL에서는 열거 타입(Enums)를 정의할 수 있습니다. Enums 타입이란 일정한 값들의 집합에 대하여 의미를 표현할 수 있는 언어 기능입니다.

미리 정의해둔 세트에 속하는 값만 필드에서 반환하도록 만들고 싶다면 열거 타입을 사용하면 됩니다.

위에서 본 LiftStatus가 바로 Enums 타입으로 정의한 것입니다.

- List Type

리스트는 GraphQL 타입을 대괄호를 감싸서 만들면 됩니다. 아래 처럼 말이죠.

근데 느낌표가 두개입니다.. 음.. 정리해보면 아래와 같습니다.

[String] : 리스트안에 담긴 String는 null이 될 수 있다.
[String!] : 리스트안에 담긴 String는 null이 될 수 없다.
[String]! : 리스트안에 담긴 String는 null이 될 수 있으나, 리스트 자체는 null이 될 수 없다.
[String!]! : 리스트안에 담긴 String는 null이 될 수 없고, 리스트 자체도 null이 될 수 없다.
예를 들어 [String!]에서 허용되는 경우와 안되는 경우는 어떤게 있을까요? 리스트 자체가 null이 되어도 상관없지만 안에 들어가는 내용물이 null이 되면 안됩니다.

myField: null // valid
myField: [] // valid
myField: ['a', 'b'] // valid
myField: ['a', null, 'b'] // error
이번에는 [String]!인 경우를 살펴보겠습니다. 여기서 주의할거는 자바스크립트에서 []는 null이랑 같지만 graphql에서 []는 허용이 됩니다. 😨😨

myField: null // error
myField: [] // valid
myField: ['a', 'b'] // valid
myField: ['a', null, 'b'] // valid
뭐 일반적인 경우에는 4번째가 많이 쓰이는거 같습니다.

- 유니온(Union) 타입

리스트에 항상 같은 타입만 들어가지 않습니다. 유니온(Union)과 인터페이스(Interface)를 이용하면 여러타입도 가능합니다. 유니온 타입 사용 시 인라인 프래그먼트를 함께 활용할 수 있습니다.

```tsx
type StudyGroup {
      name: String!
      subject: String!
      students: Int!
  }

  type Workout {
      name: String!
      reps: Int!
  }

  union AgendaItem = Workout | StudyGroup

  type Query {
      agenda: [AgendaItem!]!
  }
```

위와 같이 AgendaItem 유니온 타입을 생성하여 Workout, StudyGroup 타입을 결합시켰습니다.
그 후 아래와 같이 쿼리를 작성할때 프래그먼트를 사용해서 AgendaItem이 Workout일때와 StudyGroup일때 특정 필드만 선택되도록 만들 수 있습니다. 즉, 유니온 타입에서 각각의 객체가 어떤 필드를 반환할 것인지 정할 때 인라인 프래그먼트를 사용하면 됩니다.

```tsx
{
  agenda {
    ...on Workout {
      name
      reps
    }
    ...on StudyGroup {
      name
      subject
      students
    }
  }
}
```

![graphql_union_response](https://user-images.githubusercontent.com/85284246/186060176-1eb7d6d6-b621-4383-80f4-0ff79fd40ab7.png)

<br>

- 인터페이스(Interface)

```tsx
interface ScheduleItem {
  name: String!
  start: Int
  end: Int
}

type StudyGroup implements ScheduleItem {
  name: String!
  start: Int
  end: Int
  subject: String!
  students: Int!
}

type Workout implements ScheduleItem {
  name: String!
  start: Int
  end: Int
  reps: Int!
}

type Query {
  agenda: [ScheduleItem!]!
}
```

인터페이스란 자바에서 말하는 그 의미와 동일합니다. 추상화를 의미하며, 이걸 상속받은 타입은 그 필드는 반드시 구현해야한다는 것을 의미합니다.

```tsx
{
  agenda {
    name
    start
    end
    ...on Workout {
      reps
    }
  }
}
```

이제 agenda는 name, start, end 뿐만 아니라 Workout에만 있는 reps같이 인라인 프래그먼트를 이용해서 선택해서 쓸 수 있습니다. (유니온과 비슷하게 쓰일 수 있다는 것을 알 수 있습니다)

![graphql_interface_response](https://user-images.githubusercontent.com/85284246/186060169-7314a7cb-1f31-4b03-a1d4-01d7cc3ce082.png)

<br>

- 뮤테이션(Mutation) : 쿼리는 데이터를 읽기 위한 행위에 관한 기술이라면 데이터를 쓰기 위한 행위는 뮤테이션이 있습니다.
  일반적으로 세 가지 종류의 뮤테이션이 있습니다.

  1. 새로운 데이터 생성
  2. 기존 데이터 업데이트
  3. 기존 데이터 삭제

  뮤테이션은 쿼리문과 동일한 문법 구조를 가지지만, 반드시 mutation 키워드와 함께 시작해야 한다는 점이 다릅니다.

<br>

### # 관계

커스텀 객체 타입으로 필드를 만들면 두 객체가 서로 연결됩니다.

- 1대1 관계
  예를들어, 아래는 Lift와 Trail이 1대1로 연결되어있는 상태를 정의했습니다. "Lift는 반드시 한개의 접근가능한 코스 1개를 가지고 있다" 이런 의미겠네요.

```tsx
type Lift {
  id: ID!
  name: String!
  trailAccess: Trail!
}
```

- 1대다 관계
  Trail은 여러개의 접근가능한 Lift를 가질 수 있도록 설정했습니다.

```tsx
  type Trail {
    id: ID!
    name: String!
    accessedByLifts: [Lift!]!
  }
```

- 다대다 관계
  다대다 관계를 만들려면 양쪽 모두에 리스트 타입 필드를 추가하면 됩니다.

```tsx
type Lift {
  id: ID!
  name: String!
  trailAccess: [Trail!]!
}
type Trail {
  id: ID!
  name: String!
  accessedByLifts: [Lift!]!
}
```

<br>

### # Query 구조

- 필드 (Fieldw) : 쿼리 요청을 위해 내부에 작성되는 것들이 필드입니다. 필드는 스키마를 참고하여 작성됩니다.

```tsx
query lifts {
  allLifts {
    name
  }
}

query trails {
  allTrails {
    name
    difficulty
  }
}
```

- 스키마 (schema) : 쿼리 요청 후 응답 시 반환 할 데이터의 목록 및 타입을 결정합니다.

```tsx
type Query {
  allLifts(status: LiftStatus) : [Lift!]!
  allTrails(status: TrailStatus) : [Trail!]!
  Lift(id: ID!): Lift!
  Trail(id: ID!): Trail!
  liftCount(status: Liftstatus) : Int!
  trailCount(stauts: TrailStatus) : Int!
  gnar: String!
  sweet: String!
}
```

- 인자 (Arguments) : 인자를 전달하여 응답 받을 쿼리 필드 값을 지정할 수 있습니다. 이러한 동작 방식으로 쿼리 결과를 필터링 할 수 있습니다.

```tsx
query liftsAndTrails {
  allLifts(status: OPEN) {
    name
    status // "status" : "OPEN"
  }
  allTrails {
    name
    difficulty
  }
}
```

- 별칭 (Alias)

보면 알겠지만, 요청을 allLifts에서 id, name, status를 보냈다면 응답도 json 형태로 동일한 이름이 생성됩니다. 응답 객체 필드명을 다르게 받고 싶다면 어떻게 해야할까요??

만약 아래와 같이 쿼리를 실행하면 에러가 납니다. 동일한 Lift를 두번 호출했으니까요.

```tsx
query lift {
  Lift(id: "jazz-cat") {
    capacity
  }
  Lift(id: "snowtooth-express") {
    capacity
  }
}
```

에러를 해결하려면 별칭을 다르게 부여하면 됩니다.

```tsx
query lift {
  jazzCatLift: Lift(id: "jazz-cat") {
    capacity
  }
  expressLift: Lift(id: "snowtooth-express") {
    capacity
  }
}
```

- 프래그먼트 (Fragement) : 여러 쿼리의 중복되는 필드가 많을 경우 중복되는 필드의 값을 하나로 묶어 사용할 수 있습니다.

```tsx
// 수정 전
query {
  Lift(id: "jazz-cat") {
    name
    status
    capacity
    night
    elevationGain
    trailAccess {
      name
      difficulty
    }
  }
  Trail(id: "river-run") {
    name
    difficulty
    accessedByLifts {
      name
      status
      capacity
      night
      elevationGain
    }
  }
}

// 수정 후
query {
  Lift(id: "jazz-cat") {
    ...liftInto
    trailAccess {
      name
      difficulty
    }
  }
  Trail(id: "river-run") {
    name
    difficulty
    accessedByLifts {
      ...liftInto
    }
  }
}

fragment liftInto on Lift {
  name
  status
  capacity
  night
  elevationGain
}
```

fragment 를 정의하는 방법은 fragment 식별자를 쓴 다음 이름을 써줍니다. on Lift는 어떤 타입에 대한 fragment인지를 나타내고 이 정보는 꼭 써줘야 합니다.

<br>

#### # Code first vs Schema first

<br>

### # GraphQL server의 목적

1. 채워진 스키마 필드를 응답으로 반환
2. 새로 생성된 스키마에 대해 GraphQL 쿼리 검증
3. 클라이언트로부터 들어오는 GraphQL 쿼리 수신

<br>

### # GraphQL Data Mocking

웹개발은 Frontend, Backend 로 파트가 나뉘어져 파트별 개발자들의 협력으로 개발하는 경우가 많습니다.
이런식으로 나뉘어져 개발할 경우 Frontend 개발자의 작업은 Backend Data에 의존적입니다. API 호출을 통해서 받아온 데이터를 통해 UI가 그려지는 경우가 대부분이기 때문입니다.
이렇게 파트별 Task간의 의존성의 있는경우 병렬적으로 개발하지 못해서 생산성이 저하되는 단점이 있습니다. 이러한 이유로 API가 개발 완료되지 않은 상황이라면 Frontend 개발시 자체적으로 API 호출하는 부분을 분리하고 Mocking해서 사용하거나 Fake Data를 import 해서 진행하기도 합니다.
GraphQL에서는 Type System을 활용해서 손 쉽게 Data Mocking하는 기능을 사용할 수 있습니다. 기본적으로 Data mocking을 위해 new ApolloServer 생성자에 mock: true로 설정합니다.

- mock 속성 true

```tsx
const server = new ApolloServer({
  typeDefs,
  mocks: true,
});
```

- Type에 대한 Mock Resolver

```tsx
{
  Int :() => faker.random.number(100),
  String :() => faker.random.word(),
  Boolean :() => faker.random.boolean(),
}
```

- Custom Type에 대한 Mock Resolver

```tsx
const mocks = {
  Track: () => ({
    id: () => "track_01",
    title: () => "Astro Kitty, Space Explorer",
    author: () => {
      return {
        name: "Grumpy Cat",
        photo:
          "https://res.cloudinary.com/dety84pbu/image/upload/v1606816219/kitty-veyron-sm_mctf3c.jpg",
      };
    },
    thumbnail: () =>
      "https://res.cloudinary.com/dety84pbu/image/upload/v1598465568/nebula_cat_djkt9r.jpg",
    length: () => 1210,
    modulesCount: () => 6,
  }),
};
```

- List Type에 대한 Mock Resolver

```tsx
const mocks = {
  Query: () => ({
    tracksForHome: new MockList(20),
    // or MockList([1, 20])
    // or [...new Array(6)]
  });
}
```

### # SandBox를 활용한 GraphQL Data Mocking

1. server 실행 후 `http://localhost:4000` 으로 접속합니다.
2. Query Your Server 버튼을 클릭합니다.
3. Example Query 버튼 클릭하여 Query 요청 후 Response에서 응답을 확인합니다.
4. 좌측 Documentation 탭에서 로컬에 생성 된 Query Field 목록을 Fields에서 확인해볼 수 있습니다. 또한 해당 Query 목록을 클릭하여 필드에 대한 자세한 정보를 확인해볼 수 있습니다. (ex 필드 주석 내용) 그리고 Field 좌측에 `+` 버튼을 클릭하여 Query Field를 쉽게 추가할 수도 있습니다.

<br>

### # 클라이언트 설정

```tsx
// npm install graphql @apollo/client
// import { ApolloClient , InMemoryCache , ApolloProvider } from '@apollo/client' ;

const client = new ApolloClient({
  uri: "http://localhost:4000",
  cache: new InMemoryCache(options),
});
```

- uri : 서버의 위치를 결정하는 속성
- cache : 캐시 설정 속성, new InMemoryCache로 캐시 객체를 생성해서 넘겨주어야 합니다.

![apollo_cache_flow](https://user-images.githubusercontent.com/85284246/186052840-abcba693-aa7a-4e3a-aeb3-0e6876b777f1.png)

- Provider 연결

ApolloProvider는 react의 ContextAPI를 사용하여 구성된 ApolloClient의 인스턴스를 구성 요소 트리 전체에서 사용할 수 있게 해줍니다.
이를 사용하기 위해 앱의 최상위 구성 요소를 구성 요소에 래핑하고 ApolloProvider클라이언트 인스턴스를 소품으로 전달합니다.

```tsx
const client = new ApolloClient({
  uri: "http://localhost:4000",
  cache: new InMemoryCache(options),
});

ReactDOM.render(
  <ApolloProvider client={client}>
    <GlobalStyles />
    <Pages />
  </ApolloProvider>,
  document.getElementById("root")
);
```

<br>

### # useQuery 사용

구성 요소가 렌더링되면 UI를 렌더링하는 데 사용할 수 있는 loading, error, data 및 속성이 포함 된 useQueryApollo Client의 개체를 반환합니다.

<br>

### # Query Defining

```tsx
const TRACKS = gql`
  query GetTracks {
    tracksForHome {
      id
      title
      thumbnail
      length
      modulesCount
      author {
        name
        photo
      }
    }
  }
`;
```

3. 느낌표는 null이 들어올 수 없음을 의미합니다. (non-nullable, null 값을 허용하지 않음), 클라이언트가 쿼리를 호출한다고 했을때 서버가 반드시 반환해줘야 한다는 뜻입니다. (인자로 썼을때는 클라이언트가 반드시 서버에게 넘겨줘야 하는 값을 의미합니다.)

---

## ODYSSEY 1

<br>

### STEP 1. 기능 개요 및 설정(EATURE OVERVIEW AND SETUP)

- code first vs schema first

  스키마 작성 방식에는 code first 방식과 schema first 방식이 있습니다. schema first 방식의 이점 중 하나는 프론트엔드 및 백엔드 팀이 병렬로 작업할 수 있도록 하여 총 개발 시간을 단축한다는 것입니다. 프론트엔드 팀은 스키마가 정의되는 즉시 모의 데이터 작업을 시작할 수 있으며 백엔드 팀은 동일한 스키마를 기반으로 API를 개발합니다. 이것이 GraphQL API를 설계하는 유일한 방법은 아니지만 효율적인 방법입니다.

- schema first flow

  스키마 우선 설계의 이점 중 하나는 프론트엔드 및 백엔드 팀이 병렬로 작업할 수 있도록 하여 총 개발 시간을 단축한다는 것입니다. 프론트엔드 팀은 스키마가 정의되는 즉시 모의 데이터 작업을 시작할 수 있으며 백엔드 팀은 동일한 스키마를 기반으로 API를 개발합니다. 이것이 GraphQL API를 설계하는 유일한 방법은 아니지만 효율적인 방법이라고 생각하므로 이 과정 전체에서 사용할 것입니다.

  1. 스키마 정의 : 기능에 필요한 데이터를 식별한 다음 해당 데이터를 가능한 직관적으로 제공하도록 스키마를 구성합니다.

  2. 백엔드 구현 : Apollo Server를 사용하여 GraphQL API를 구축하고 포함된 데이터 소스에서 필요한 데이터를 가져옵니다. 이 첫 번째 과정에서는 모의 데이터를 사용합니다. 다음 과정에서는 앱을 라이브 REST 데이터 소스에 연결합니다.

  3. 프론트엔드 구현 : 클라이언트는 GraphQL API의 데이터를 사용하여 뷰를 렌더링합니다.

<br>

### STEP 2. 기능 데이터 요구 사항(FEATURE DATA REQUIREMENTS)

- 스키마(schema)란?

  REST API가 end point 집합이었다면, GraphQL API는 type 집합입니다. 그리고 이런 데이터 type 집합을 스키마라고 부릅니다. 스키마를 설계하기 전 필요한 데이터를 분석해야 합니다. 데이터를 분석한 후 데이터와 데이터의 관계를 자료 구조 중 노드와 간선으로 이어진 그래프로 나타내고 이 그래프의 구조를 스키마를 통해 정의할 수 있습니다. 스키마를 정의하는 언어는 줄여서 SDL(Schema Definition Language)이라고 합니다.

<br>

### STEP 3. 스키마 정의 언어(SDL : SCHEMA DEFINITION LANGUAGE)

- GraphQL 스키마

  스키마는 서버와 클라이언트 간의 계약과 같습니다. GraphQL API가 할 수 있는 것과 할 수 없는 것과 클라이언트가 데이터를 요청하거나 변경할 수 있는 방법을 정의합니다. 백엔드 구현 세부 정보를 숨기면서 소비자에게 유연성을 제공하는 추상화 계층입니다.

  기본적으로 스키마는 필드를 포함하는 개체 유형의 모음입니다. 각 필드에는 고유한 유형이 있습니다. 필드의 유형은 스칼라(예: Int 또는 String)이거나 다른 개체 유형일 수 있습니다.

  type 키워드를 사용하여 유형을 선언하고 그 뒤에 유형 이름(PascalCase가 모범 사례임)을 사용한 다음 포함된 필드를 유지하기 위해 대괄호를 엽니다.

  필드는 이름(camelCase), 콜론, 필드 유형(스칼라 또는 객체)으로 선언됩니다. 필드에는 대괄호로 표시된 List도 포함될 수 있습니다.

  매우 유사해 보이는 Javascript 객체와 달리 필드는 쉼표로 구분되지 않습니다. 또한 각 필드 값이 nullable인지 아니면 non-nullable인지 여부를 나타낼 수 있습니다. 필드가 null이 아니어야 하는 경우 해당 유형 뒤에 느낌표를 추가합니다.

- 스칼라(Scalar) Type

  내장 스칼라 타입은 Int, Float, String, Boolean, ID(문자열이기는 하나 고유한 값인지를 검사) 등이 있습니다.
  또한 스칼라 타입은 객체 타입이 아니기 때문에 필드를 가지지 않습니다.

- 스키마 주석 (descriptions)

  타입 전체에 descriptions을 사용할 때는 삼중따옴표, 타입 필드별 descriptions을 사용할 때는 따옴표를 사용할 수 있습니다.

  ```tsx
  const typeDefs = gql`
    """
    a cat astronaut
    """
    type SpaceCat {
      "the name of the cat"
      name: String!
      age: Int
      missions: [Mission]
    }
  `;
  ```

### STEP 4. 스키마 작성(BUILDING OUR SCHEMA)

- 스키마를 시작하려면 먼저 apollo-server 및 graphql의 몇 가지 패키지가 필요합니다.

  - graphql 패키지는 GraphQL 쿼리를 구문 분석하고 검증하기 위한 핵심 로직을 제공합니다.

  - apollo-server 패키지는 우리가 잠시 후에 사용할 gql 템플릿 리터럴과 같은 몇 가지 멋진 유틸리티와 함께 완전한 사양을 준수하는 GraphQL 서버를 제공합니다.

```tsx
// 1. npm install apollo-server graphql

const { gql } = require("apollo-server"); // 2.

const typeDefs = gql`
  # Schema definitions go here
`;
module.exports = typeDefs;
```

우리가 가져오는 이 gql은 무엇입니까? 이것은 우리가 작성하려는 스키마 정의와 같은 GraphQL 문자열을 래핑하는 데 사용되는 태그가 지정된 템플릿 리터럴입니다.

이것은 GraphQL 문자열을 작업 및 스키마 작업 시 Apollo 라이브러리가 예상하는 형식으로 변환하고 구문 강조도 활성화합니다.

다음으로 typeDefs("유형 정의"의 줄임말) 상수를 선언하고 정의가 들어갈 gql 템플릿을 지정합니다. 우리가 그것에 있는 동안 나중에 서버 파일에 필요하기 때문에 지금 typeDefs를 내보내자.

작은따옴표(')와 혼동하지 않도록 gql 태그와 함께 역따옴표(`)를 사용합니다.

좋습니다. 유형을 정의할 준비가 되었습니다. 목업을 다시 참조하여 각 학습 트랙에 대해 다음 데이터가 필요함을 확인했습니다.

이 데이터를 유형으로 구성하는 방법은 무엇입니까?

글쎄, 우리는 Track이라는 이름의 단일 유형을 만들고 모든 필드를 여기에 넣고 하루라고 부를 수 있습니다. 그러나 그것이 비즈니스 도메인 관점에서 의미가 있을까요? 설마. 우선 단일 작성자가 여러 트랙을 만들 수 있으며 해당 작성자의 정보가 여러 위치에 불필요하게 복제됩니다. 대신 우리는 독립된 개체의 관점에서 생각해야 합니다. 트랙과 작성자라는 두 가지 항목으로 시작하겠습니다.

<br><br><br>

## ODYSSEY 2

<br>

### STEP 1. GRAPHQL 쿼리의 여정(JOURNEY OF A GRAPHQL QUERY)

- GraphQL을 사용한 데이터 요청 중 클라이언트에서 하는 일은?

  데이터를 요청하기 위해 GraphQL 서버에 HTTP POST 혹은 GET을 통해 Query를 보냅니다. 이 때 Query는 Over Fetching을 막기 위해 필요한 필드만 선택하여 생성할 수 있습니다.

- GraphQL을 사용한 데이터 요청 중 서버에서 하는 일은?

  서버가 HTTP 요청을 받으면 먼저 GraphQL 쿼리로 문자열을 추출합니다. 문자열 추출 후 이 문자열을 추상구문트리(AST)로 변환합니다. 그리고 이 추상구문트리를 사용하여 서버는 스키마의 유형 및 필드에 대해 쿼리 유효성을 검사합니다. 요청된 쿼리의 필드가 스키마에 정의되지 않았거나 쿼리 형식이 잘못된 경우 서버는 오류를 발생시키고 오류를 클라이언트로 보냅니다.

  오류가 발생하지 않는 경우는 실제로 데이터를 가져오게 됩니다. 쿼리의 각 필드에 대해 서버는 해당 필드의 resolver 함수를 호출하고 resolver 함수의 역할은 데이터베이스 또는 REST API와 같은 소스에서 올바른 데이터를 검색하여 스키마의 단일 필드에 데이터를 채우는 역할(해결: resolve)을 합니다.

  resolver 함수를 통해 쿼리 필드가 모두 채워지면 쿼리와 모양이 정확히 동일한 JSON으로 조합되어 생성됩니다. 서버는 HTTP Body data key에 해당 JSON을 담아 응답합니다.

### STEP 2. 데이터 탐색(EXPLORING OUR DATA)

- 데이터는 어디에 저장되며 어떻게 구성되어 있습니까?
- 그 구조가 클라이언트 앱의 요구 사항 및 스키마와 다른가요?
- 리졸버 함수가 해당 데이터에 어떻게 액세스할 수 있습니까?

- resolver 함수는 쿼리가 요구하는 것과 일치하도록 데이터 속성 필터링을 처리합니다.

### STEP 3. 아폴로 RESTDATASOURCE(APOLLO RESTDATASOURCE)

---

### # REST의 단점

- 오버패칭(overfetching)
  만약 /person/1 이라는 엔드포인트가 있고 반환하는 데이터가 name, age, hobby, school, height, marry, birthday 등 20가지라고 해봅시다. 근데 정작 앱에서 필요한건 name, age, height 정보 뿐입니다.

  이런식으로 필요하지 않은 데이터를 불필요하게 전송했습니다. 물론 엔드포인트 가서 백엔드를 수정하면 되긴합니다. 하지만, 나중에 가보면 birthday 정보가 필요해서 또 수정해야하는 상황이 생길 수도 있습니다.

- 언더패칭(underfetching)
  이번에는 그 사람에 정보 뿐만 아니라 그 사람이 쓴 최근게시글 5개를 추가로 가져오고 싶습니다. 그렇다면 새로운 엔드포인트를 하나 더 만들어서 다시 한번 요청해야 하는 상황이 발생합니다. GraphQL을 사용하면 중첩 쿼리를 이용해서 이런 언더패칭 문제를 해결 할 수 있다는 것을 위에서 잠시 다뤄봤습니다.

- 엔드포인트 관리 문제
  REST API를 개발해봤다면 엔드포인트가 기본 수십개이지 않을까요? (초보라서 저만 그럴수도...?) 아무튼 엔드포인트 수도 많거니와 엔드포인트를 관리하기 위해 swagger라는 도구도 있습니다. 엔드포인트를 새로 만들기 위해서는 프론트엔드 개발팀과 백엔드 개발팀이 서로 회의해야 하고요...

<br>

## ODYSSEY 3

### GRAPHQL ARGUMENTS (GRAPHQL 인수)

- GraphQL 인수를 사용하는 방법 인수는 쿼리의 특정 필드에 제공하는 값입니다. 스키마는 각 필드가 허용하는 인수를 정의합니다. 그러면 리졸버는 필드에 제공된 인수를 사용하여 해당 필드에 대한 데이터를 채우는 방법을 결정할 수 있습니다. 인수는 특정 개체를 검색하거나 개체 집합을 필터링하거나 필드의 반환 값을 변환하는 데 도움이 될 수 있습니다. 검색을 수행하는 쿼리는 일반적으로 사용자의 검색어를 인수로 제공합니다. 스키마의 필드에 대한 인수를 정의하기 위해 필드 이름 뒤에 소괄호를 추가합니다. 내부에서 우리는 인수의 이름 다음에 콜론을 씁니다. 그런 다음 String 또는 Int와 같은 해당 인수의 유형을 씁니다. 인수가 두 개 이상인 경우 쉼표로 구분할 수 있습니다.

```tsx
track(id: ID!): Track
```

- 인수 사용 이유

사용자가 제출한 입력 값 제공
필드의 반환 값을 변환
특정 개체 검색
객체 세트 필터링

### RESOLVER ARGS PARAMETER (resolver 인수 매개변수)

- 리졸버는 부모, 인수, 컨텍스트 및 정보의 네 가지 선택적 매개변수가 있는 함수입니다.

- 사용하지 않는 파라미터의 경우 언더바로 처리하거나 완전히 생략할 수도 있다.

### RESOLVER CHAINS (리졸버 체인)

- 리졸버 함수는 스키마의 필드에 대한 데이터를 채웁니다. 함수에는 4개의 매개변수가 있습니다. 첫 번째 parent는 리졸버 체인에서 이전 함수의 반환 데이터를 담고 있습니다. 두 번째 args는 필드에 제공된 모든 인수를 포함하는 객체입니다. 세 번째 매개변수인 context를 사용하여 데이터베이스 또는 REST API와 같은 데이터 소스에 액세스합니다. 마지막으로 네 번째 매개변수인 info는 작업 상태에 대한 정보 속성을 포함합니다.

### QUERY BUILDING IN APOLLO SANDBOX (APOLLO SANDBOX에서 쿼리 작성)

- $ 기호는 GraphQL의 변수를 나타냅니다. $ 기호 뒤의 이름은 쿼리 전체에서 사용할 수 있는 변수의 이름입니다. 콜론 뒤에는 변수의 유형이 있으며 이는 우리가 사용할 인수 유형과 일치해야 합니다.

- 변수는 훌륭합니다. 변수를 사용하면 클라이언트 측에서 인수 값을 동적으로 전달할 수 있으므로 값을 쿼리에 하드코딩할 필요가 없습니다. 인수가 있는 쿼리를 만들 때마다 사용합니다.

- 변수는 $ 기호로 표시됩니다. 쿼리에 하드코딩된 값을 포함하지 않도록 인수에 대한 동적 값을 제공하는 데 사용됩니다. 각 유형의 유형은 스키마에 지정된 유형과 일치해야 합니다.

```tsx
// ex1
query GetTrack($trackId: ID!) {
 track(id: $trackId) {

 }
}

// ex2
const GET_MISSION = gql`
  query getMission($isScheduled: Boolean) {
    mission(scheduled: $isScheduled) {
      id
      codename
    }
  }
`;
```

### BUILDING THE TRACK PAGE (트랙 페이지 구축)

- 쿼리 문자열을 gql 템플릿 리터럴로 래핑한 다음 useQuery 후크를 사용하여 서버로 보냅니다.

### THE USEQUERY HOOK - WITH VARIABLES (USEQUERY 후크 - 변수 사용)

- 클라이언트에서 GraphQL 서버로 호출하려면 ApolloClient의 useQuery 후크를 사용해야 합니다.

```tsx
const GET_SPACECAT = gql`
  query getSpacecat($spaceCatId: ID!) {
    spacecat(id: $spaceCatId) {
      name
    }
  }
`;

const spaceCatId = "kitty-1";

const { loading, error, data } = useQuery(GET_SPACECAT, {
  variables: { spaceCatId },
});
```

- useQuery 후크는 앱에서 사용하는 세 가지 유용한 속성이 있는 객체를 반환합니다. loading은 쿼리가 완료되었고 결과가 반환되었는지 여부를 나타냅니다. error는 작업에서 발생한 오류가 포함된 개체입니다. data는 쿼리가 완료된 후의 결과를 포함합니다. 쿼리에서 변수를 설정하기 위해 options 객체 내부에 있는 useQuery 후크의 두 번째 매개변수에 변수를 선언합니다.

- 쿼리 로드가 완료되고 오류가 없으면 QueryResult 구성 요소는 자식을 렌더링하여 필요한 데이터를 전달합니다.

```tsx
<QueryResult error={error} loading={loading} data={data}>
  {/* this is where our component displaying the data will go */}
</QueryResult>
```

### NAVIGATING TO THE TRACK PAGE (트랙 페이지로 이동)

- GraphQL 서버에 처음으로 쿼리를 보낼 때 Apollo Client는 결과를 캐시에 저장합니다. 다음에 동일한 쿼리를 보내려고 할 때(예: 같은 페이지로 다시 탐색) 네트워크를 통해 불필요한 호출을 보내는 대신 캐시에서 결과를 로드합니다.

<br>

## ODYSSEY 3

### WHAT IS A MUTATION? (MUTATION은 무엇입니까?)

- 데이터를 수정하려면 다른 유형의 GraphQL 작업인 쓰기 작업인 Mutation을 사용해야 합니다. Query 유형과 마찬가지로 Mutation 유형은 스키마의 진입점 역할을 합니다. 지금까지 사용해온 스키마 정의 언어(SDL)와 동일한 구문을 따릅니다.

- type 키워드를 사용하여 Mutation 유형을 선언한 다음 Mutation이라는 이름을 사용합니다. 중괄호 안에는 진입점이 있으며 데이터를 변경하는 데 사용할 필드가 있습니다. (ex : deleteMisson, createMisson )

- 업데이트 작업의 특정 동작(예: 추가, 삭제 또는 생성)을 설명하는 동사로 시작하여 뮤테이션이 작동하는 모든 데이터가 뒤따를 것을 권장합니다. 뮤테이션은 일반적으로 특정 개체를 수정하기 때문에 종종 인수가 필요합니다. 동일한 SDL 구문에 따라 필요에 따라 인수를 추가할 수 있습니다. 뮤테이션의 반환 유형은 콜론 뒤에 옵니다. 뮤테이션 응답의 경우, 클라이언트가 후속 쿼리를 실행할 필요 없이 UI를 업데이트할 수 있도록 뮤테이션이 업데이트한 데이터를 반환해야 합니다.

- 모든 뮤테이션 응답에 세 가지 공통 필드를 추가하는 것이 좋습니다.

1. code: HTTP 상태 코드와 유사한 응답의 상태를 나타내는 Int입니다.
2. success: 모든 업데이트의 성공 여부를 나타내는 boolean 플래그입니다.
3. message: 클라이언트 측에서 뮤테이션 결과에 대한 정보를 표시하는 문자열. 이것은 뮤테이션이 부분적으로만 성공했고 일반 오류 메시지가 전체 내용을 말할 수 없는 경우에 특히 유용합니다.

- Mutations vs Queries : 쿼리와 뮤테이션은 모두 GraphQL 작업 유형입니다. 쿼리는 항상 데이터를 검색하는 읽기 작업입니다. 뮤테이션은 항상 데이터를 수정하는 쓰기 작업입니다. 쿼리 필드와 유사하게 뮤테이션 유형의 필드는 GraphQL API의 진입점이기도 합니다.

### UPDATING OUR TRACKAPI DATA SOURCE (TRACKAPI 데이터 소스 업데이트)

- RESTDataSource 사용하는 이유

1. REST API 호출에 대한 리소스 캐싱 및 요청 중복 제거를 자동으로 처리
2. 전용 클래스에서 데이터 가져오기 구현을 유지하고 리졸버를 간단하고 깔끔하게 유지

### RESOLVING A MUTATION SUCCESSFULLY (MUTATION을 성공적으로 해결)

- resolver 객체 구조

1. 스키마의 Query와 뮤테이션 타입은 리졸버 객체에 상응하는 키를 가지고 있어야 합니다.
2. 리졸버의 이름은 스키마의 필드 이름과 일치해야 합니다.

```tsx
const typeDefs = gql`
  type Mutation {
    assignSpaceship(spaceshipId: ID!, missionId: ID!): AssignSpaceshipResponse
  }

  type AssignSpaceshipResponse {
    code: Int!
    success: Boolean!
    message: String!
    spaceship: Spaceship
    mission: Mission
  }
`;

const resolvers = {
  Mutation: {
    assignSpaceship: async (_, { spaceshipId, missionId }, { dataSources }) => {
      // async와 await을 사용하여 resolver에 반환 결과를 담아놓고 스키마가 요구하는 code, success, message와 함께 반환한다.
      const { spaceship, mission } =
        await dataSources.spaceAPI.assignSpaceshipToMission(
          spaceshipId,
          missionId
        );
      return {
        code: 200,
        success: true,
        message: `Successfully assigned spaceship ${spaceshipId} to mission ${missionId}`,
        spaceship: spaceship,
        mission: mission,
      };
    },
  },
};
```

### RESOLVING A MUTATION WITH ERRORS (오류가 있는 MUTATION 해결)

- incrementTrackViews 변형에 대한 성공적인 응답이 준비되었습니다. TrackAPI 호출에서 오류가 발생하는 상황을 처리하기 위해 이 섹션을 try 블록으로 래핑하겠습니다. 오류가 발생하면 오류를 매개변수로 사용하는 catch를 추가하여 오류를 catch합니다.

```tsx
incrementTrackViews: async (_, {id}, {dataSources}) => {
  try {
    const track = await dataSources.trackAPI.incrementTrackViews(id);
    return {
      code: 200,
      success: true,
      message: `Successfully incremented number of views for track ${id}`,
      track
    };
  } catch (err) {
    return {
      // we'll return a new object here
    };
  }
},
```

- 코드를 404로 설정할 수도 있지만 더 동적이고 Apollo Server와 RESTDataSource 클래스가 제공하는 값을 사용할 수도 있습니다. 오류가 발생하면 Apollo Server는 관련 오류 세부 정보가 포함된 해당 오류에 확장 필드를 첨부합니다. 이 경우 TrackAPI가 RESTDataSource를 확장하므로 이 확장 개체는 HTTP 응답 자체에 대한 몇 가지 추가 정보를 제공하는 응답 속성으로 강화됩니다. HTTP 상태 코드를 참조하는 status 속성을 반환할 수 있습니다. 다음으로 success 속성을 false로 설정할 수 있습니다. message 속성의 경우 사용자 지정 속성을 만들 수 있지만 동일한 extension.response 개체의 다른 값을 사용하겠습니다. 이것이 extension.response.body 속성입니다. 나중에 다른 유형의 오류를 반환할 수 있으므로 이 값을 보다 동적으로 만듭니다.

```tsx
incrementTrackViews: async (_, {id}, {dataSources}) => {
  try {
    const track = await dataSources.trackAPI.incrementTrackViews(id);
    return {
      code: 200,
      success: true,
      message: `Successfully incremented number of views for track ${id}`,
      track
    };
  } catch (err) {
    return {
      code: err.extensions.response.status,
      success: false,
      message: err.extensions.response.body,
      track: null
    };
  }
},
```

- mutation 에러 처리 예시

```tsx
const resolvers = {
  Mutation: {
    assignSpaceship: async (_, { spaceshipId, missionId }, { dataSources }) => {
      try {
        const { spaceship, mission } =
          await dataSources.spaceAPI.assignSpaceshipToMission(
            spaceshipId,
            missionId
          );
        return {
          code: 200,
          success: true,
          message: `Successfully assigned spaceship ${spaceshipId} to ${missionId}`,
          spaceship: spaceship,
          mission: mission,
        };
      } catch (error) {
        return {
          code: error.extensions.response.status,
          success: false,
          message: error.extensions.response.body,
          spaceship: null,
          mission: null,
        };
      }
    },
  },
};
```

### THE USEMUTATION HOOK

- 쿼리가 아니라 뮤테이션인 경우 useQuery hook이 아닌 useMutation hook을 사용합니다. TrackCard 구성 요소 내에서 후크를 호출하여 시작합니다. 이전에 설정한 INCREMENT_TRACK_VIEWS를 첫 번째 매개변수로 취합니다. 두 번째 매개변수는 변수 키가 있는 객체입니다. 여기에서 incrementTrackViewsId 변수를 추가하고 탐색하려는 트랙의 ID로 설정합니다. 이 id는 이미 track prop의 맨 위에 있는 구조화 해제되었습니다. 자, 여기 반전이 있습니다. useQuery와 달리 useMutation을 호출해도 실제로는 자동으로 뮤테이션이 실행되지 않습니다! 대신 useMutation 후크는 두 개의 요소가 있는 배열을 반환합니다. 여기에서 분해를 시작할 것입니다. 첫 번째 요소는 나중에 뮤테이션을 실제로 실행하는 데 사용할 mutate 함수입니다. 우리는 그것을 incrementTrackViews라고 부를 것입니다. 두 번째 요소는 로딩, 오류 및 데이터와 같은 뮤테이션에 대한 정보가 있는 개체입니다. 이 구성 요소는 필요하지 않으므로 추출할 필요가 없습니다. 언제 mutate 함수를 실행하고 싶습니까? 사용자가 카드를 클릭할 때! CardContainer 구성 요소에 onClick 소품을 추가하고 mutate 함수인 incrementTrackViews를 호출하도록 구성해 보겠습니다.

```tsx
const [incrementTrackViews] = useMutation(INCREMENT_TRACK_VIEWS, {
  variables: { incrementTrackViewsId: id },
});

<CardContainer
  to={`/track/${id}`}
  onClick={incrementTrackViews}
>
```

- 뮤테이션 클라이언트 측 보내기

  우리는 후크를 사용하여 React 클라이언트에서 GraphQL API로 요청을 보냅니다. 뮤테이션을 보내기 위해 useMutation 훅을 사용합니다. 이것은 배열을 반환합니다. 여기서 첫 번째 요소는 뮤테이션을 트리거하는 데 사용되는 mutate 함수입니다. 두 번째 요소는 로딩, 오류 및 데이터와 같은 뮤테이션에 대한 추가 정보가 있는 개체입니다. 이 후크는 GraphQL 작업을 첫 번째 매개변수로 사용합니다. 또한 변수와 같은 속성이 설정되는 두 번째 매개변수로 options 객체를 사용합니다.

- useQuery vs useMutation

  1. useQuery hook은 객체를 반환하지만 useMutation은 배열은 반환
  2. useQuery hook은 쿼리를 보내는 데 사용되는 반면 useMutation hook은 뮤테이션을 보내는 데 사용됩니다.
  3. useQuery 후크는 컴포넌트 렌더링에서 자동으로 실행되는 반면 useMutation 후크는 뮤테이트 함수를 트리거하는 데 필요한 뮤테이션을 반환합니다.

- 뮤테이션 응답이 완료되었을 때 확인하기 위해 콘솔 로그를 추가해 보겠습니다. 이를 위해 useMutation 후크를 설정한 위치로 돌아가서 options 객체에 다른 속성을 추가합니다. onCompleted 속성은 뮤테이션이 성공적으로 완료되었을 때 실행될 콜백 함수이며, 되돌아오는 응답에 접근할 수 있습니다. 브라우저 콘솔에 대한 응답을 기록합니다.

```tsx
const [incrementTrackViews] = useMutation(INCREMENT_TRACK_VIEWS, {
  variables: { incrementTrackViewsId: id },
  // to observe what the mutation response returns
  onCompleted: (data) => {
    console.log(data);
  },
});
```

- useMutation 예시

```tsx
const ASSIGN_SPACESHIP_MUTATION = gql`
  mutation AssignSpaceshipToMissionMutation(
    $spaceshipId: ID!
    $missionId: ID!
  ) {
    assignSpaceship(spaceshipId: $spaceshipId, missionId: $missionId) {
      code
      success
      message
      spaceship {
        name
      }
      mission {
        codename
      }
    }
  }
`;

const spaceshipId = "ROCKET_X";
const missionId = "M0007";

const [assignSpaceship, { loading, error, data }] = useMutation(
  ASSIGN_SPACESHIP_MUTATION,
  {
    variables: { spaceshipId, missionId },
  }
);
```

### OUR MUTATION IN THE BROWSER (브라우저의 MUTATION)

- Apollo Client cache : Apollo Client 캐시를 활용하면 빠르게 데이터를 표시할 수 있습니다. 캐시에서 로드되기 때문에 GraphQL API에 불필요한 쿼리를 보내지 않았습니다. 뮤테이션이 API로 전송되는 동안에도 캐시에서 페이지를 로드하고 있습니다. 캐시가 업데이트되면 UI도 업데이트됩니다.

유사하게, 우리는 뮤테이션이 API로 전송되는 동안에도 캐시에서 페이지를 로드하고 있습니다. 성공적으로 반환되면 numberOfView에 대한 업데이트된 값을 반환합니다. Apollo Client는 이 트랙의 ID를 확인하고 캐시에서 검색하고 numberOfViews 필드를 업데이트하기 위해 뒤에서 작업을 수행하고 있습니다. 캐시가 업데이트되면 UI도 업데이트됩니다.

값은 먼저 캐시에서 로드된 다음 뮤테이션 응답이 성공적으로 돌아올 때 업데이트 됩니다.

---

## 질문

### # ODYSSEY 1

- gql로 래핑해서 쿼리를 요청하는데 gql은 스키마 정의, 쿼리문 작성할 때 무조건 래핑해서 사용해야하는지? -> 타입 추론 안되서 별루,,

- gql을 사용한 요청과 client.writeQuery와의 차이는? writeQuery는 그냥 로컬 스토리지 가져오는 메소드와 비슷한 개념으로 생각하면 된다. readQuery도 마찬가지로 로컬 스토리지를 저장하는 메소드와 비슷한 개념으로 생각하자. query를 서버에 날려 가져온 데이터를 캐싱해오는 것과는 완전 관계가 없다. 별도의 state라고 생각하자! (ApolloClient는 두 가지 역할을 하는데 state관리, query 날리고 가져온 데이터 캐싱인데 이 두 가지를 별도로 생각해야 한다.) 예를 들면 필터 값을 writeQuery로 저장한 뒤 readQuery로 가져올 수 있다! (헷갈리지 말자! 모양새는 쿼리와 비슷하다)

- 일반 쿼리의 경우 DB에서 데이터를 가져올 때 캐싱하는데 필드 하나라도 다르면 다른 요청으로 보고 새로 캐싱한다.

```js
const { gql } = require("apollo-server");

const TRACKS = gql`
  query getTracks {
    tracksForHome {
      id
      title
      thumbnail
      length
      modulesCount
      author {
        name
        photo
      }
    }
  }
`;
```

- 리졸버 함수에 대한 이야기가 계속 나오던데 혹시 클라이언트 단에서 리졸버 함수 만들어놓지 않고 쿼리로 요청만 할 경우 서버에서 자동으로 스키마에 맞는 데이터를 DB 찾아서 반환해주는 것인지? 커스텀 리졸버와 디폴트 리졸버와 다르다! 디폴트 리졸버가 스키마에 맞게 데이터를 채워주는 것이고 커스텀 리졸버는 특정 조건에 맞게 가공해서 가져온다. (커스텀 리졸버는 아예 내 마음대로 필드를 채워서 가져온다고 보면 된다.)

### # ODYSSEY 1

- 아래 이해한 내용이 맞을까요?

  - new ApolloClient로 client 객체 생성, 이 때 GraphQL 서버 url과 캐시 사용을 위해 InMemoryCache 전달 -> 프로퍼바이더에 props로 전달하여 캐시 된 데이터를 사용할 수 있도록 하고 서버에 쿼리를 요청할 수 있도록 한다.

  - 서버에서는 new ApolloServer로 server 객체를 생성하고 props로 리졸버 함수 및 스키마를 전달한다.

  - 클라이언트 단에서 쿼리를 서버에 날리고 서버에서는 스키마를 통해 유효성 검사를 한 뒤 유효한 쿼리라고 판단하면 각 필드에 맞는 리졸버 함수를 호출한 후 결과(JSON)를 반환한다. 그러면 클라이언트 단에서는 useQuery를 통해 해당 데이터를 응답받아 사용할 수 있다.

<br>

### # ODYSSEY 2

- RESTDataSource 자체가 잘 이해가 안됩니다..ㅠㅠ 왜 필요한지 잘 이해가 안되요!! 하단은 문서 내용인데 그냥 리졸버의 가독성을 위해 RESTDataSource로 확장한 클래스 내부에서 리졸버 함수의 기능을 대신하는 건가 싶습니다. 아니면 인자로 받은 값을 활용하여 엔드포인트에 맞는 데이터를 받아와 상세 페이지 구현 등에 사용되는 기능인 것 같기도 합니다. 아니면 쿼리로 데이터를 받아올 때 쿼리로 받아온 데이터 중 단일 필드만 받아올 때 사용하는 것일까요? (예제를 보면 this.get에 인자로 스키마에 지정된 필드명이 들어가는 것을 보고 이런 생각을 했어용,,)

  1. REST API 호출에 대한 리소스 캐싱 및 요청 중복 제거를 자동으로 처리

  2. 전용 클래스에서 데이터 가져오기 구현을 유지하고 리졸버를 간단하고 깔끔하게 유지

- 아래 이해한 내용이 맞을까요?

  - 리졸버 사용 시 키는 루트 타입, 벨류 안에 메소드가 담긴 키는 스키마 필드와 동일하게 선언한다.

  ```js
  const typeDefs = gql`
    type Query {
      tracksForHome: [Track!]!
    }
  `;

  const resolvers = {
    Query: {
      tracksForHome: (_, __, { dataSources }) => {
        return dataSources.trackAPI.getTracksForHome();
      },
    },
  };
  ```

  - 리졸버 함수의 인자

  1. parent : 쿼리 리턴 값..? (오디세이에는 이전 리졸버 함수의 리턴 값이라고 나와 있습니다. 근데 리졸버 함수가 하나라면 참조할 수 있는 데이터가 없는 것 일까요?)

  2. args : 쿼리에서 넣은 인자

  3. context : 모든 리졸버에게 전달 되는 값, 주로 미들웨어를 통해 입력된 값들이 들어있다.

  4. info : 스키마 정보와 더불어 현재 쿼리의 특정 필드 정보, 잘 사용하지 않음

<br>

### # ODYSSEY 3

- 아래 이해한 내용이 맞을까요?

  - 쿼리 인자는 특정 필드에 제공되는 특정 필드에 제공되는 값이다. 리졸버는 쿼리에서 넘겨준 인자를 활용하여 데이터를 채우는 방법을 결정한다. 또한 스키마는 허용되는 인자를 결정할 수 있다.

  - $이 붙은 변수는 다이나믹 라우팅에서 사용된다. Router를 통해 래핑한 컴포넌트의 path중 :의 뒤에 값을 받아와 이 값을 통해 쿼리의 인자로 사용하여 요청할 수 있다. (예시로 상세 페이지 구현 시 활용될 수 있다.)

  ```tsx
  // index.js : Router 래핑한 Track 컴포넌트
  export default function Pages() {
    return (
      <Router primary={false} component={Fragment}>
        <Tracks path="/" />
        <Track path="/track/:trackId" />
      </Router>
    );
  }

  // track.js : Track 컴포넌트의 인자로 trackId를 받은 뒤 useQuery의 두번째 인자로 전달한다. 이 두번째 인자는 쿼리 요청 시 $가 붙은 변수로 활용 됨.
  const GET_TRACK = gql`
    query getTrack($trackId: ID!) {
      track(id: $trackId) {
        id
        title
        author {
          ...
    }
  `;

  const Track = ({ trackId }) => {
    const { loading, error, data } = useQuery(GET_TRACK, {
      variables: { trackId },
    });

    return (
      <Layout>
        <QueryResult error={error} loading={loading} data={data}>
          <TrackDetail track={data?.track} />
        </QueryResult>
      </Layout>
    );
  };
  ```

<br>

### # ODYSSEY 4

- 아래 이해한 내용이 맞을까요?

  - 뮤테이션은 추가/삭제/수정 등의 사용, 데이터 업데이트 후 추가로 쿼리를 요청하지 않기 위해 사용할 수 있다.

  - 뮤테이션에서 code(상태코드), success(성공 시), message(결과 내용) 사용안하시는지?

  - 쿼리에서는 useQuery를 사용, 뮤테이션에서는 useMutation 사용

  - useMutation은 자동 호출 x, 배열로 구조 분해해서 호출해야 함 (첫번째 인자는 뮤테이션 트리거 함수, 두번째 인자는 useQuery와 마찬가지로 data, loading, error 등의 객체), onCompleted은 뮤테이션 호출 후 실행되는 콜백
