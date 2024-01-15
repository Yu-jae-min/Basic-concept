# [Algorithm-SQL] 프로그래머스 - GROUB BY - **고양이와 개는 몇 마리 있을까**

<br>

2024년 01월 15일

# 1. 문제

- https://school.programmers.co.kr/learn/courses/30/lessons/59040

<br>
<br>

# 2. 나의 풀이

```sql
SELECT ANIMAL_TYPE, COUNT(ANIMAL_TYPE) FROM ANIMAL_INS
group by ANIMAL_TYPE
order by ANIMAL_TYPE
```

1. 1행에서 ANIMAL_INS 테이블의 ANIMAL_TYPE을 조회하고 ANIMAL_TYPE을 카운트한다.
2. group by를 통해 ANIMAL_TYPE의 같은 데이터를 묶는다. (ex Cat은 Cat끼리, Dog는 Dog끼리)
3. order by를 통해 ANIMAL_TYPE을 정렬한다. 이 때 cat은 dog보다 우선순위가 높기 때문에 오름차순 정렬해준다.

<br>
<br>

# 3. 후기

연습이 부족한건지 자꾸 WHERE문 먼저 떠오른다. group by와 order by 등 더 많은 방법을 자주 사용해보아야겠다.

<br>
