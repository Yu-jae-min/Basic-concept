## # React와 Node.js연동

<br>

### # 연동 과정

#### # 1. node express 설치

> yarn add express

<br>

#### # 2. 프로젝트 root 경로에 server 디렉토리와 server.js 생성

```js
// server/server.js
const express = require("express");

const app = express();
const api = require("./routes/index");
const cors = require("cors");

app.use(cors());
app.use("/api", api);

const PORT = 3001;
app.listen(PORT, () => console.log("Node.js Server is running on port 3001"));
```

서버 생성 코드이다. 포트번호는 충돌을 피하기 위해 3001번으로 할당하였으며 '/api'의 경로 요청을 라우팅해주었다.

<br>

#### # 3. server 디렉토리에 routes 디렉토리 생성 후 index.js 파일 생성

```js
// server/routes/index.js
const express = require("express");

const router = express.Router();

router.get("/", (req, res) => {
  res.send({ title: "hello react!" });
});

module.exports = router;
```

<br>

#### # 4. proxy 설정을 위한 모듈 설치

> yarn add http-proxy-middleware

<br>

#### # 5. src 디렉토리 안에 setupProxy.js 파일 생성

```js
// src/setupProxy.js
const proxy = require("http-proxy-middleware");

module.exports = function (app) {
  app.use(
    proxy("/api", {
      target: "http://localhost:3001/",
    })
  );
};
```

설정된 프록시는 클라이언트 사이드에서 Node.js 서버 사이드인 `http://localhost:3001/api`로의 요청을 처리하여 서버 데이터를 가져올 수 있도록 해준다.

<br>

#### # 6. 클라이언트/서버 사이드 실행

> **- 서버 사이드** : node ./server/server.js
>
> **- 클라이언트 사이드** : yarn start

<br>

#### # 7. http 통신 메소드를 활용하여 요청 보내기

```js
useEffect(() => {
  axios.get("http://localhost:3001/api").then((res) => {
    console.log(res);
  });
});
```

<br>

#### # 8. 성공 시 이미지

- 콘솔 이미지
  ![](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/b6f69995-e9ef-44e7-bdc0-4c5b3a0d8efc)
- node 실행 중인 터미널
  ![](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/a72de384-39e0-47e7-8595-8f833bac10f4)

> **! cors에러 발생** : yarn add cors로 모듈 설치 후 server.js에 아래 코드 추가

```js
// server.js
const cors = require("cors");
app.use(cors());
```
