# [Typescript] 맵드 타입(Mapped Type)

## # 맵드 타입(Mapped Type)

맵드 타입이란 기존에 정의되어 있는 타입을 새로운 타입으로 변환해 주는 문법을 의미한다. 마치 자바스크립트 map() API 함수를 타입에 적용한 것과 같은 효과를 가진다.

```ts
// 변환 전
{
  name: 'string',
  email: 'string',
}

// 변환 후
{
  name: 'number',
  email: 'number',
}
```

<br>

### # 맵드 타입의 기본 문법

맵드 타입은 아래와 같은 형태의 문법을 사용한다.

```ts
{ [ P in K ] : T }
{ [ P in K ] ? : T }
{ readonly [ P in K ] : T }
{ readonly [ P in K ] ? : T }
```

in operator를 활용하여 순회하며 in operator를 기준으로 좌항(위 P)은 일반 타입 변수, 우항(위 K)은 순회가 되는 대상이 된다. 타입은 콜론 뒤(위 T)에 지정해주면 된다.

<br>

### # 맵드 타입 기본 예제

```ts
// 맵드 타입 기본 예제
type Heroes = "Hulk" | "Capt" | "Thor";
type HeroAges = { [K in Heroes]: number };
const ages: HeroAges = {
  Hulk: 33,
  Capt: 100,
  Thor: 1000,
};
```

<br>

### # 맵드 타입 실용 예제

#### # 맵드 타입 실용 예제1

```ts
// 맵드 타입 실용 예제1
type Subset<T> = {
  [K in keyof T]?: T[K];
};

interface Person {
  age: number;
  name: string;
}

const ageOnly: Subset<Person> = { age: 23 };
const nameOnly: Subset<Person> = { name: "Tony" };
const ironman: Subset<Person> = { age: 23, name: "Tony" };
const empty: Subset<Person> = {};
```

맵드 타입인 Subset은 키와 값이 있는 객체를 정의하는 타입을 받아 그 객체의 부분 집합을 만족하는 타입으로 변환해주는 문법이다. 예를 들면 Person과 같은 인터페이스가 있다고 할 때 Subset 타입을 적용하면 ageOnly, nameOnly, ironman, empty과 같은 객체를 모두 정의할 수 있다.

#### # 맵드 타입 실용 예제2

아래 fetchUserProfile 함수 같이 사용자 프로필을 조회하는 API 함수가 있다고 했을 때 이 프로필의 정보를 수정하는 API는 아마 updateUserProfile 함수와 같은 형태일 것이다.

```ts
// 맵드 타입 실용 예제2
// 사용자 프로필을 조회하는 API
interface UserProfile {
  username: string;
  email: string;
  profilePhotoUrl: string;
}

function fetchUserProfile(): UserProfile {
  // ...
}

// 프로필의 정보를 수정하는 API
interface UserProfileUpdate {
  username?: string;
  email?: string;
  profilePhotoUrl?: string;
}

function updateUserProfile(params: UserProfileUpdate) {
  // ...
}
```

이 때 interface UserProfile, UserProfileUpdate과 같이 동일한 타입에 대해서 반복해서 선언하는 것을 피해야 한다.

위의 인터페이스에서 반복되는 구조를 아래와 같은 방식으로 재활용 할 수 있다.

```ts
type UserProfileUpdate = {
  username?: UserProfile["username"];
  email?: UserProfile["email"];
  profilePhotoUrl?: UserProfile["profilePhotoUrl"];
};
```

혹은 좀 더 줄여서 아래와 같이 정의할 수도 있다.

```ts
type UserProfileUpdate = {
  [p in "username" | "email" | "profilePhotoUrl"]?: UserProfile[p];
};
```

여기서 위 코드에 keyof를 적용하면 아래와 같이 줄일 수 있다.

```ts
type UserProfileUpdate = {
  [p in keyof UserProfile]?: UserProfile[p];
};
```

<br>

---

참고자료

- <a href="https://joshua1988.github.io/ts/usage/mapped-type.html#%EB%A7%B5%EB%93%9C-%ED%83%80%EC%9E%85-mapped-type-%EC%9D%B4%EB%9E%80" target='_blank'>맵드 타입</a>
