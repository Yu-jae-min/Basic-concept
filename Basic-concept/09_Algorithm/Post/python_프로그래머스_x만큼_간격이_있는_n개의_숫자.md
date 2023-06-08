# [python-algorithm] 프로그래머스 - x만큼 간격이 있는 n개의 숫자

## (1) 문제링크

<a href="https://programmers.co.kr/learn/courses/30/lessons/12954?language=python3" target='_blank'>https://programmers.co.kr/learn/courses/30/lessons/12954?language=python3</a>

<br>

## (2) 문제풀이 및 해설 1

### - 문제풀이

```python
x = 2
n = 5

def solution1(x, n) :
    answer = []
    i = 1
    while i <= n :
        answer.append(x * i)
        i += 1

    return answer

print(solution1(x,n))
```

### - 문제해설

> 1.  빈 배열 answer을 생성한다.<br>
> 2.  증감시킬 i의 초기값을 1로 할당한다.<br>
> 3.  반복문 while을 활용하는데 조건은 i가 n보다 작거나 같을 때까지만 반복한다.<br>
> 4.  반복문이 실행될때마다 빈 배열 answer에 x \* i 요소를 추가하고 i를 1씩 증감시킨다.

<br>

## (2) 문제풀이 및 해설 2

### - 문제풀이

```python
x = 2
n = 5

def solution2(x, n):
    return [i * x + x for i in range(n)]

print(solution2(x, n))
```

### - 문제해설

> 1.  반복문 for문과 range를 활용한다.<br>
> 2.  range() 인자값으로 n을 지정하여 0~n까지의 list를 생성한다.<br>
> 3.  for문을 이용하여 i \* x + x과 같이 등차수열 일반항 공식으로 값을 출력한다.

<br>

## (3) 참고자료

1. <a href="https://ko.khanacademy.org/math/algebra1/x2f8bb11595b61c86:sequences/x2f8bb11595b61c86:constructing-arithmetic-sequences/a/writing-explicit-formulas-for-arithmetic-sequences" target='_blank'>등차수열 일반항</a><br>
2. <a href="https://wikidocs.net/16045" target='_blank'>for in 반복문, Range, enumerate</a>
