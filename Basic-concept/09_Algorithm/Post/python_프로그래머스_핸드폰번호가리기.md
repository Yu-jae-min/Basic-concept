# [python-algorithm] 프로그래머스 - 핸드폰 번호 가리기

## (1) 문제링크

<a href="https://programmers.co.kr/learn/courses/30/lessons/12950?language=python3" target='_blank'>https://programmers.co.kr/learn/courses/30/lessons/12950?language=python3</a>

<br>

## (2) 문제풀이 및 해설 1

### - 문제풀이

```python
phone_number = "01033334444"

def solution1(phone_number) :
    return "*" * len(phone_number[0:-4]) + phone_number[-4:]

print(solution1(phone_number)) # "*******4444"
```

### - 문제해설

> 문자열 + 문자열의 형태로 출력한다. 첫번째 문자열은 "\*"을 곱해주는데 곱해주는 값은 len()함수에 phone_number를 슬라이싱하여 0~-4까지의 문자열이 되고 두번째 문자열은 -4~마지막 문자까지 되므로 뒤 4자리 수가 된다. 이 두 문자열을 더하여 출력한다.

<br>

## (2) 문제풀이 및 해설 2

### - 문제풀이

```python
phone_number = "01033334444"

import re

def solution2(phone_number):
    p = re.compile(r'\d(?=\d{4})')
    return p.sub("*", phone_number, count = 0)

print(solution2(phone_number)); # "*******4444"
```

### - 문제해설

> 1.  정규표현식을 사용하기 위해 re모듈을 import한다.<br>
> 2.  re모듈에서 직접가져오지 않고 미리 컴파일을 하기 위해 re.compile()메서드를 활용하여 정규식을 파라미터 값으로 할당하여 패턴 객체를 반환한다.<br>
> 3.  파라미터 값으로 할당된 정규식 중 r은 백슬래시 문자를 해석하지 않고 남겨두기 위해 r을 선두에 사용하고 \d는 [0-9]와 동일하게 숫자를 가리킨다. 또한 (?=...)는 뒤에 (?=...)가 오는 경우 성립되는 것을 의미한다. 여기서는 뒤에 숫자가 4개인 경우를 의미한다. 즉 뒤에 숫자가 4개가 오는 숫자열을 변경하게 되는 것이다.<br>
> 4.  sub()메서드를 활용하여 문자를 치환한다. \*로 치환되며 뒤에 숫자 4개는 변하지 않는다. 여기서 count는 count가 0인 경우는 전체를, 1이상이면 해당 숫자만큼 치환 된다.

<br>

## (3) 참고자료

1. <a href="https://twpower.github.io/119-python-list-slicing-examples" target='_blank'>slicing</a><br>
2. <a href="https://www.tutorialspoint.com/python3/string_len.htm" target='_blank'>len()</a><br>
3. <a href="http://pythonstudy.xyz/python/article/401-%EC%A0%95%EA%B7%9C-%ED%91%9C%ED%98%84%EC%8B%9D-Regex" target='_blank'>re모듈</a><br>
4. <a href="https://ponyozzang.tistory.com/335" target='_blank'>re.sub()</a><br>
5. <a href="https://greeksharifa.github.io/%EC%A0%95%EA%B7%9C%ED%91%9C%ED%98%84%EC%8B%9D(re)/2018/08/04/regex-usage-05-intermediate/" target='_blank'>re.compile()</a><br>
6. <a href="https://whatisthenext.tistory.com/116" target='_blank'>정규표현식 r의 의미</a><br>
7. <a href="https://docs.python.org/ko/3/library/re.html" target='_blank'>정규표현식 (?=...)</a>
