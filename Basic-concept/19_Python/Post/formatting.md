# 포맷팅(Formatting)

## 포맷팅(Formatting)

파이썬 포맷팅(Formatting) 방법은 세 가지가 있다.
첫번째는 %를 이용한 포맷팅, 두번째는 format()함수를 이용한 포맷팅,
세번째는 python 3.6을 기준으로 새로 추가 된 f-string 포맷팅이 있다.

### % 포맷팅

% 포맷팅 연산자와 % 포맷팅 스트링을 사용한다.
% 포맷팅 스트링으로는 %s(문자), %d(정수), %f(실수)가 있다.

```python
# 문자 대입
my_formating1 = 'My name is %s' % 'Jae min'
print(my_formating1) # My name is Jae min

# 정수형 숫자 대입
my_formating2 = '%d %d' % (1, 2)
print(my_formating2) # 1 2

# 실수형 숫자 대입
my_formating3 = '%f' % 3.14
print(my_formating3) # 3.14
```

<br>
또한 연산자와 스트링 사이에 숫자를 넣을 수도 있다.
%s 사이에 숫자를 삽입하면 삽입한 숫자 만큼 공간을 확보한다.
%d 사이에 숫자를 삽입하면 삽입한 숫자로 공간을 채우게 된다.

```python
# %s 숫자 삽입 - 공간 확보
my_formating4 = 'My name is %5s' % 'Jae min'
print(my_formating4) # My name is Jae min

my_formating5 = 'My name is %10s' % 'Jae min'
print(my_formating5) # My name is    Jae min

# %d 숫자 삽입 - 공간 채우기
my_formating6 = 'Number %05d' % 5
print(my_formating6) # Number 00005

my_formating7 = 'Number %05d' % 400
print(my_formating7) # Number 00400
```

<br>

### format() 포맷팅

{}.format()를 이용하여 포맷팅하는 방법이다.
변수의 타입과는 상관없이 괄호와 숫자만을 활용하면 된다.

```python
my_format1 = 'My name is {}'.format('Jae min')
print(my_format1) # My name is Jae min

my_format2 = 'My name is {name}'.format(name='Jae min')
print(my_format2) # My name is Jae min

my_format3 = '{} x {} = {}'.format(2, 3, 2*3)
print(my_format3) # 2 x 3 = 6

my_format4 = '{1} x {0} = {2}'.format(2, 3, 2*3) # format 순서 지정
print(my_format4) # 3 x 2 = 6
```

<br>
% 포맷팅과 같이 공간 확보와 공간 채우기 또한 가능하다.

```python
my_format5 = 'Number "{0:>5d}"'.format(300)
print(my_format5) # Number "  300"

my_format6 = 'Number "{0:<5d}"'.format(300)
print(my_format6) # Number "300  "

my_format7 = 'Number "{0:>05d}"'.format(300)
print(my_format7) # Number "00300"

my_format8 = 'Number "{0:<05d}"'.format(300)
print(my_format8) # Number "30000"
```

<br>

### f-string 포맷팅

문자열 앞에 f를 추가하고 {}안에 변수명을 입력하여 포맷팅한다.
또한 내부적 함수 호출도 가능하며 딕셔너리 포맷도 사용이 가능하다.

```python
name = 'Jae min'
my_format8 = f'My name is {name}'
print(my_format8) # My name is Jae min

name = 'Jae min'
my_format9 = f'My name is {name.upper()}'
print(my_format9) # My name is JAE MIN

dictionary = {'name' : 'Jae min'}
my_format10 = f'My name is {dictionary["name"]}'
print(my_format10) # My name is Jae min
```

---

출처

1. <a href="https://blog.naver.com/PostView.nhn?isHttpsRedirect=true&blogId=ksg97031&logNo=221126216595&parentCategoryNo=&categoryNo=62&viewDate=&isShowPopularPosts=true&from=search" target='_blank'>파이썬 format 완전 정리</a>
2. <a href="https://codechacha.com/ko/python-string-formatting/" target='_blank'>Formatting의 다양한 방법 정리</a>
3. <a href="https://brownbears.tistory.com/421" target='_blank'>문자열 포맷팅 방법들</a>
