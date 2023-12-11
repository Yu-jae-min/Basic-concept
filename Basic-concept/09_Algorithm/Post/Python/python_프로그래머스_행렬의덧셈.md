# [python-algorithm] 프로그래머스 - 행렬의 덧셈

## (1) 문제링크

<a href="https://programmers.co.kr/learn/courses/30/lessons/12950?language=python3" target='_blank'>https://programmers.co.kr/learn/courses/30/lessons/12950?language=python3</a>

<br>

## (2) 문제풀이 및 해설 1

### - 문제풀이

```python
arr1 = [[1,2],[2,3]]
arr2 = [[3,4],[5,6]]

def solution1(arr1, arr2) :
    answer = [];

    for i in range(len(arr1)) :
        tmp = [];
        for j in range(len(arr1[i])) :
            tmp.append(arr1[i][j] + arr2[i][j])

        answer.append(tmp)

    return answer

print(solution1(arr1, arr2))
```

### - 문제해설

> 1.  빈 배열 answer을 생성한다.<br>
> 2.  for문을 중첩하여 사용하는데 첫번째 for문의 컨테이너는 range()함수를 사용하고 파라미터로 len()함수를 사용하여 0~배열의 len의 리스트로 생성하여 지정한다.<br>
> 3.  두번째 내부 for문의 컨테이너 또한 range()함수를 사용하고 파라미터로 len()함수를 사용하여 0~배열 요소 len의 리스트로 생성하여 지정한다.<br>
> 4.  반복문의 실행될 때마다 연산을 진행하고 연산이 끝난 값을 배열로 나누어 담아야하기 때문에 첫번째 for문안에 빈 배열 tmp를 생성하여 담아준다.<br>
> 5.  배열안의 요소가 연산이 끝난 후 다음 요소로 넘어간 후 다시 배열로 담아야하므로 두번째 for문 반복이 끝난 뒤 answer변수에 tmp를 추가하여준다. 그러면 첫번째 내부 for문이 완전히 종료된 후 [4, 6]이 answer에 추가되고 두번째 사이클로 넘어가게 된다.

<br>

## (2) 문제풀이 및 해설 2

### - 문제풀이

```python
arr1 = [[1,2],[2,3]]
arr2 = [[3,4],[5,6]]

def solution2(A,B):
    return [list(map(sum, zip(*x))) for x in zip(A, B)]

print(solution2(arr1, arr2))
```

### - 문제해설

> 1.  for문을 사용한다. 이 때 zip()함수를 이용하여 각 배열의 요소를 튜플로 짝 지어준다. (ex ([1,2],[3,4]), ([2,3],[5,6]))<br>
> 2.  짝 지어진 튜플을 map()함수를 활용하여 파라미터로 받은 자료형에 각 함수를 적용시키는데 함수는 sum을 활용하여 더한다. 이 때 파라미터로 받은 자료형은 zip(\*x)가 되는데 \*을 활용하여 unzip을 한 것이다. (ex [1,2],[3,4] , [2,3],[5,6]) unzip가 된 파라미터가 sum()함수로 인해 연산이 진행된다.<br>
> 3.  map()한 연산 값을 list로 출력하기 위해 list()함수를 사용하여 출력한다.

<br>

## (2) 문제풀이 및 해설 3

### - 문제풀이

```python
arr1 = [[1,2],[2,3]]
arr2 = [[3,4],[5,6]]

def solution3(A,B):
    answer = [[A[i][j] + B[i][j] for j in range(len(A[i]))] for i in range(len(A))]

    return answer

print(solution3(arr1, arr2))
```

### - 문제해설

> 1.  for문을 중첩으로 사용한다. 이 때 가장 우항에 있는 for문이 먼저 실행되는데 컨테이너는 range()함수의 파라미터로 배열의 len이 된다. (0, 1)<br>
> 2.  두번째 for문에서의 컨테이너는 range()함수의 파라미터로 배열의 len(A[0])이 된다. (0, 1) 또한 배열로 나누어 반환하여야 하므로 대괄호로 묶어준다.<br>
> 3.  최종 리턴되는 값에서 A[i][j] + B[i][j]로 연산하여 반환한다. (연산 순서는 첫번째 for문에 i가 0일 때, [0][0]+[0][0] - [0][1]+[0][1]이 된 후 j가 1이 되어 반복이 종료되고 다시 i가 1이 되고 [1][0]+[1][0] - [1][1]+[1][1]의 연산이 진행된다.

<br>

## (3) 참고자료

1. <a href="https://www.daleseo.com/python-zip/" target='_blank'>zip()</a><br>
2. <a href="https://dojang.io/mod/page/view.php?id=2286" target='_blank'>map()</a>
3. <a href="https://codechacha.com/ko/python-sum/" target='_blank'>sum()</a>
4. <a href="https://docs.python.org/ko/3/library/stdtypes.html#list" target='_blank'>list()</a>
