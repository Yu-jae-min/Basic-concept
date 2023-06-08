# # requestAnimationFrame 활용한 슬롯 카운트 기능 구현 (라이브러리 x)

## **# 슬롯 카운트 기능 구현**

라이브러리를 사용하지 않은 슬롯 카운트 기능을 구현해보았다.

<br>

## **# easeOutExpo**

`https://easings.net/ko#easeOutExpo`에서 참고할 수 있는 Easing 함수이다.
함수 내부에 1은 최대 값을 말하고 파라미터 x는 진행율을 말한다. 파라미터로 전달되는 진행율은 점점 증가해야 함으로 보통 재귀 호출을 통해 사용한다.

```js
function easeOutExpo(x: number): number {
  return x === 1 ? 1 : 1 - Math.pow(2, -10 * x);
}
```

진행율 x가 최대 값에 도달할 때까지 반복 실행하는데 Math.pow의 음수 제곱 값을 활용하여 전달되는 파라미터 값이 커질수록 최대 값에 빼는 수가 점점 작아지게 된다. 즉 최대 값에 가까워질수록 증감하는 값이 작아지는 것이다. 이로 인해서 카운트 기능 중 최대 값에 가까워질수록 점점 느리게 증가하는 기능을 구현할 수 있다.

<br>

## **# requestAnimationFrame과 cancelAnimationFrame**

### **# 애니메이션의 프레임(frame)**

사람의 눈은 적게는 초당 10프레임에서, 집중한 때에 초당 60프레임 정도의 프레임을 볼 수 있다고 한다. 그 이상의 프레임을 찍어내더라도 사람의 눈으로는 체감하기 힘들다는 것이다.

그래서 자바스크립트로 애니메이션을 구현할때도 1초에 60프레임 정도를 찍어내면 된다.
그 말은, 1프레임을 찍어내는데 16.6ms(1000ms / 60frame)를 넘겨서는 안된다는 말이다.

자바스크립트를 활용한 애니메이션에서 16.6ms마다 프레임을 찍어내기 위해 사용할 수 있는 방법은 setInterval과 requestAnimationFrame이 있다. 또한 빈번하게 호출되는 이벤트 핸들러에는 보통 3~4ms 정도로 실행을 마치게끔 해야한다. 그래야, 자바스크립트 실행 이후 리플로우 과정까지 총 16ms내에 프레임을 찍어낼 수 있게 된다.

<br>

### **# requestAnimationFrame(rAF)**

함수를 반복할 때 사용할 수 있는 메서드이다. 애니메이션을 구현할 때 사용되며 일반적으로 재귀적인 호출 방식을 통해 반복한다. 보통 setInterval 혹은 setTimeout과 비교된다.

```js
requestAnimationFrame(반복할 함수)
```

콜백으로 반복할 함수를 전달받는다. requestAnimationFrame가 직접 출력하는 값은 콜백 리스트의 항목을 정의하는 고유한 요청 id 인 long 정수 값을 출력한다. 이 값은 0 이 아니라는것 외에는 다른 추측을 할 수가 없는 값이므로 cancelAnimationFrame에 전달해 콜백 요청을 취소하는 경우에만 사용한다.

requestAnimationFrame 메서드의 특징은 아래와 같다.

- 최대 호출 횟수 : Web API에서 동작하며 최대 1초에 60번 동작한다. 다수 애니메이션에도 각각 타이머를 생성하지 않고 동일한 타이머를 참조하게 된다.

- rAF는 시간이 아닌 repaint 시점을 기준으로 호출 : 다음 리페인트가 진행되기 전에 함수를 호출 시키기 때문에 프레임 누락을 방지할 수 있다. 즉 프레임 시작 시간에 애니메이션 움직임을 업데이트하는 함수를 시작하게 되는 것이다. 애니메이션 함수의 실행과 실제 픽셀을 채우는 리페인트하는 과정에 순서를 보장하여 프레임 누락을 방지할 수 있는 것이다.

- 백그라운드 동작 및 비활성화시 중지 : WebAPI에서 실행되며 브라우저창이 숨겨지거나 최소화되어 보여지지 않는 경우 애니메이션을 중지시키고 보여질 때 다시 실행시킨다. 이를 통해 CPU 리소스를 절약할 수 있다.

<br>

### **# cancelAnimationFrame(cAF)**

setTimeout의 clearTimeout과 같이 반복되는 requestAnimationFrame 함수를 정지시킬 때 사용한다.

```js
const animation = requestAnimationFrame(callback);

cancelAnimationFrame(animation);
```

<br>

## **# useRef**

지금까지 useRef는 DOM에 직접 접근하는 경우에만 사용하였다. 하지만 이와 같은 타이머 같은 기능을 구현할 때도 사용할 수 있다. useRef가 반환하는 ref 객체의 current 프로퍼티에 값을 저장하게 되면 리렌더링에 관계없이 값을 유지시킬 수 있다. 계속 구독하여 사용해야하는 값이라면 useRef ref객체의 current 프로퍼티를 사용할 수 있다.

```js
const ref = useRef(0);

ref.current = ref.current += 1;
```

구현한 슬롯 카운트 기능에서는 setState에 담긴 현재 카운트 값이 변화될 때 마다 리렌더링이 발생하는데 리렌더링 시 카운트 값을 현재 값으로 유지하기 위해 ref 객체의 current 프로퍼티를 사용하였다.

<br>

## **# 구현 코드**

아래는 커스텀 훅으로 작성한 슬롯 카운트 기능 구현 코드이다.

```ts
import { useEffect, useRef, useState } from "react";

const useCounter = (maxCount: number) => {
  const [count, setCount] = useState(0);
  const ref = useRef(0);

  const countEasingOut = (progressRate: number) => {
    const remainder = Math.pow(2, -10 * progressRate);
    const maxProgress = 1;

    if (progressRate === maxProgress) {
      return maxProgress;
    } else {
      return maxProgress - remainder;
    }
  };

  useEffect(() => {
    // 0. 마운트 후 useEffect 실행
    const onCount = () => {
      const duration = 2000;
      const frameTimeout = 1000 / 60;
      const totalFrame = Math.round(duration / frameTimeout);
      const percentage = countEasingOut(ref.current / totalFrame);
      const currentCount = Math.round(maxCount * percentage);

      setCount(currentCount);

      ref.current = ref.current += 1;
      const counting = requestAnimationFrame(onCount);

      if (maxCount === currentCount) {
        cancelAnimationFrame(counting);
      }
    };

    const counting = requestAnimationFrame(onCount);

    return () => {
      cancelAnimationFrame(counting);
    };
  }, [maxCount]);

  return count;
};

export default useCounter;
```

컴포넌트 마운트 시 카운트가 시작되도록 useEffect hook을 사용하였고 state 변경으로 인한 리렌더링 시 카운트 값을 유지하기 위해 useRef hook을 사용하였다.

카운트 함수 호출 시 ref 객체의 current 프로퍼티 값을 증가시켜 카운트가 점점 증가되도록 구현하였으며 해당 값을 최대 프레임과 비교하여 애니메이션 진행율을 구한 뒤 퍼센티지 값으로 변환하여 여러 개의 카운트 값이 동일한 비율로 증가하고 동시에 종료되도록 구현하였다.

requestAnimationFrame 메서드를 활용하여 카운트 함수를 반복 실행하였으며 카운트가 최대 값에 도달하였을 경우 cancelAnimationFrame 메서드를 활용하여 반복 실행을 취소하였다.

<br>

---

<br>

참고자료

- <a href="https://easings.net/ko#easeOutExpo" target='_blank'>easeOutExpo</a>
