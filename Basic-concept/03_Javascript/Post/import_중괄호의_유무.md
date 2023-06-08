# **import 중괄호 {}의 유무**

## **# import 중괄호 {}의 유무**

javascript ES6부터 추가된 모듈 시스템을 활용하여 타입을 모듈화 할 수 있다. export로 내보낼 수 있고 import로 가져와 사용할 수 있다.

그런데 js,react,ts등에서 import할 때 아래와 같은 {} 중괄호의 의미는 무엇일까?

```javascript
import React from "react";
import { render } from "react-dom";
```

결론은 export 방식에서 차이가 있다. export로 내보낸 경우 이름을 그대로 활용하여 {} 중괄호로 감싸 가져와야하고 export default로 내보낸 경우 이름을 변경하여 괄호 없이 가져올 수 있다. 이 때 중괄호가 있는 경우도 as 키워드를 이용하면 이름을 바꿔 받아올 수 있다. {a as b}의 경우 a의 값을 b에 할당하여 가져온다라고 해석할 수 있다.

<br>

### **# 예시**

```javascript
// App.js
const a = 1;
const b = 2;
export { a };
export const c = 3;
export default b;
```

위와 같이 App.js에서 세 가지 방식으로 export를 했다.
변수 a는 객체에 담아서 export하고, 변수 c는 선언 및 초기화와 동시에 바로 export 했다. 또한, 변수 b는 독특하게 앞에 default라는 키워드를 붙인 채 export했다.

또 다른 함수 Sub.js에서 App.js에 export한 것들을 불러오려고 한다.

```javascript
// Sub.js
import d, { a, c as e } from "./Example";
console.log(a, d, e); // 1, 2, 3
```

위와 같이 export로 내보낸 a, c는 이름을 변경하지 않고 중괄호 {}를 사용하여 받아올 수 있었고 export default로 내보낸 b는 d로 바꾸어 받아올 수 있었다.
또 상단에 설명한 것과 같이 export로 내보낸 c를 중괄호 {}안에서 e에 할당하여 받아왔다. 최종 출력 값은 모든 값이 문제없이 출력되는 것을 확인할 수 있다.

<br>

---

<br>

참고자료

- <a href="https://codingmania.tistory.com/333" target='_blank'>React에서 import할때, 중괄호 {} 의 의미는 무엇인가??</a>
