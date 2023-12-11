# [python-algorithm] 프로그래머스 - 평균 구하기

## (1) 문제링크

<a href="https://programmers.co.kr/learn/courses/30/lessons/12944" target='_blank'>https://programmers.co.kr/learn/courses/30/lessons/12944</a>

<br>

## (2) 문제풀이 및 해설 1

### - 문제풀이

```python
arr = [1, 2, 3, 4]

def solution1(arr):
    answer = 0

    for i in arr :
        answer += i

    return answer / len(arr)


print(solution1(arr)) # 2.5
```

### - 문제해설

> 1.  for문으로 arr을 순환하며 answer에 누적하여 더해준다.<br>
> 2.  누적 값을 arr의 배열 요소 길이만큼 나누어준다.

<br>

## (2) 문제풀이 및 해설 2

### - 문제풀이

```python
arr = [1, 2, 3, 4]

def solution2(arr):
    return (sum(arr) / len(arr))

print(solution2(arr)); # 2.5
```

### - 문제해설

> 1.  내장 함수 sum을 활용하여 arr의 요소를 더한다.<br>
> 2.  누적 값을 arr의 배열 요소 길이만큼 나누어준다.

<br>

## (2) 문제풀이 및 해설 3

### - 문제풀이

```python
arr = [1, 2, 3, 4]

from functools import reduce

def solution3(arr):
    return reduce(lambda x, y : x + y, arr) / len(arr)

print(solution3(arr)); # 2.5
```

### - 문제해설

> 1.  고차 함수를 사용하기 위한 모듈 functools를 활용한다.<br>
> 2.  reduce함수에 람다 형식을 사용하여 arr값을 누적하며 더해준다.<br>
> 3.  누적 값을 arr의 배열 요소 길이만큼 나누어준다.

<br>

## (2) 문제풀이 및 해설 4

### - 문제풀이

```python
arr = [1, 2, 3, 4]

import statistics

def solution4(arr):
    return statistics.mean(arr)

print(solution4(arr)); # 2.5
```

### - 문제해설

> 1.  통계 모듈인 statistics를 import한다.<br>
> 2.  데이터의 평균을 구하는 mean()함수를 활용한다.

<br>

## (3) 참고자료

1. <a href="https://codechacha.com/ko/python-sum/" target='_blank'>sum()</a><br>
2. <a href="https://hezzong.tistory.com/entry/python-from-import-as-%EC%82%AC%EC%9A%A9%EB%B2%95" target='_blank'>from, import, as 사용법</a><br>
3. <a href="https://docs.python.org/ko/3/library/functools.html" target='_blank'>functools 모듈</a><br>
4. <a href="https://wikidocs.net/64" target='_blank'>람다(lambda)</a><br>
5. <a href="https://docs.python.org/ko/dev/library/statistics.html" target='_blank'>statistics 모듈</a>
