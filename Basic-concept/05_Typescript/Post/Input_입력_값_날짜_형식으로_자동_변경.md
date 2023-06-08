# [Typescript] input 입력 값 날짜 형식으로 자동 변경

## **# input 입력 값 날짜 형식으로 자동 변경**

input의 입력 값을 YYYY-MM-DD 형식으로 자동 변환하는 코드이다.
사실 아래와 같은 코드 외에도 input의 type을 date로 설정하여 사용자가 날짜를 선택할 수 있도록 구현할 수 있다. 또 datepicker와 같은 관련 라이브러리를 사용해도 된다.
아래 코드는 input의 type이 text인 경우 입력 값을 YYYY-MM-DD 형식으로 자동으로 변환해주는 코드이다.

<br>

### **# 구현 코드**

```ts
const handleDateChange = (event: ChangeEvent<HTMLInputElement>) => {
  const { value } = event.currentTarget;
  const RegNotNum = /[^0-9]/g;
  const onlyNum = value.replace(RegNotNum, ""); // 숫자가 아닌 경우 ''

  let DataFormat: any;
  let RegDateFmt: any;

  if (onlyNum.length <= 6) {
    // 000000 -> 0000-00
    DataFormat = "$1-$2";
    RegDateFmt = /([0-9]{4})([0-9]+)/;
  } else if (onlyNum.length <= 8) {
    // 00000000 -> 0000-00-00
    DataFormat = "$1-$2-$3";
    RegDateFmt = /([0-9]{4})([0-9]{2})([0-9]+)/;
  }

  const newDate = onlyNum.replace(RegDateFmt, DataFormat);

  setDate(newDate); // YYYY-MM-DD
};
```

input에 onChange이벤트를 걸어 해당 함수를 실행시켰다. input 입력되는 값을 value로 디스트럭쳐링으로 받은 뒤 해당 value를 정규식을 통해 숫자만 감지하도록 하여 숫자가 아닌 경우는 제거하고 숫자인 경우 새로운 변수인 onlyNum에 할당하였다. 그 후 if문을 통해 입력 값이 6자리보다 적은 경우, 8자리보다 적은 경우 형식을 변경하여 newDate에 담도록 한 뒤 state에 할당해주었다.
