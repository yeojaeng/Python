### zip()

파이썬 내장함수 zip()은 같은 길이의 iterable한 자료형를 같은 인덱스끼리 잘라서 반환해준다.

for문을 이용해 다수의 리스트로 부터 값을 가져와서 처리해야 하는 경우 매우 유용히 사용된다.

---

### 모든 멤버의 type 변환하기

>**문제 설명**
>문자열 리스트를 입력받아, 해당 리스트를 정수형 리스트로 바꾼 값을 리턴하는 함수, solution을 만들어라.
>
>예를들면, `mylist`가 ['1', '100', '33']인 경우,
>
>solution 함수는 [1, 100, 3]을 리턴하면 된다.
>
>**제한조건**
>
>1) `mylist`의 길이는 100이하 자연수이다.
>
>2) `mylist`의 원소는 10진수 숫자로 표현할 수 있는 문자열이다.
>즉, 'as2'와 같은 문자열은 들어있지 않다.
>
>
>```python
>def solution(mylist):
>  answer = list(map(int, mylist))
>	return answer
>```
>
>해당 문제의 핵심은 `map()`이다. 
>
>`map()`을 사용하면 Iterable한 모든 멤버의 type을 변환할 수 있다.

---

### map()

파이썬의 `map` 을 사용하면 for문을 통해 일일히 원소에 접근하여 type casting하지 않고도 멤버의 타입을 일괄 변환할 수 있다.

```python
list1 = ['1', '100', '33']
list2 = list(map(int, list1))
```

---

###**map 함수 응용하기**

>**문제설명**
>
>정수를 담은 이차원 리스트, `mylist`가 `solution`의 함수 파라미터로 주어진다.
>`solution` 함수가 `mylist` 각 원소의 길이를 담은 리스트를 리턴하도록 완성하라.
>
>**제한 조건**
>
>1)	`mylist`의 길이는 100 이하인 자연수다.
>
>2)	`mylist`각 원소의 길이는 100이하 자연수다.
>
>```python
>def solution(mylist):
>  answer = list(map(len, mylist))
>  return answer
>```



---

### sequence 멤버를 하나로 이어붙이기

>**문제 설명**
>
>문자열 리스트 mylist를 입력받아, 리스트의 원소를 모두 이어붙인 문자열을 리턴하는 solution을 만들어라.
>
>**필자 코드**
>
>```python
>def solution(mylist):
>  answer = ''
>  for i in mylist:
>    answer += i
>  return answer
>```
>
>**파이썬다운 코드**
>
>```python
>my_list = ['1', '100', '33']
>answer = ''.join(my_list)
>```
>
>파이썬에서는 `join`을 사용하면 코드를 두 줄로 줄일 수 있다.
>
>`join`의 역할은 `join`을 호출하는 객체를 `join`의 해당 인수의 각 요소 사이에 끼워넣어 문자열로 재탄생 시킨다. 따라서 `caller` 객체가 문자(열)말고 올 수 없다.

---

### 삼각형 별찍기

>**필자 코드**
>
>```python
>n = int(input().split())
>for i in range(n):
>  for j in range(n):
>    if(i >= j):
>      	 print("*", end='')
>    else:
>      	 print(' ', end='')
>  print()
>```
>
>**삼각형 별찍기 - sequence type의 * 연산**
>
>예시)
>
>* 'abc', 'abcabc', 'abcabcabc', 'abcabcabcabc...'와 같이 'abc'가 n번 반복되는 문자열 만들기
>* [123, 456, 123, 456, 123 ...]과 같이 123, 456이 n번 반복되는 리스트 만들기

---

보통은 for문을 이용해 기존 `string`에 `abc`를 여러번 붙이는 번거로운 일을 한다.. 마치 나처럼..

>```python
>answer = ''
>n = 3
>for i in range(n):
>  answer += 'abc'
>```
>
>파이썬에서는 `*`연산자를 사용하여 코드를 보다 획기적으로 줄일 수 있다.
>
>```python
>n = 3
>answer = 'abc' * n
>```
>
>또, `*`연산자를 이용하면 [123, 456, 123, 456, 123 ...]과 같이 123, 456이 n번 반복되는 리스트를 만들 수 있다.
>
>```python
>n = 3
>answer = [123, 456] * n
>```

---

### 곱집합  (Cartesian product) 구하기 - product

>`iterable`로 곱집합을 구해보자.
>
>ex) 두 스트링  'ABCD', 'xy'의 곱집합은 Ax Ay Bx By Cx Cy Dx Dy 이다.
>
>보통은 for문을 이용해 두 iterable의 원소를 하나씩 곱해갈 것이다.
>
>```python
>iterable1 = 'ABCD'
>iterable2 = 'xy'
>iterable3 = '1234'
>
>for i in iterable1:
>  for j in iterable2:
>    for k in iterable3:
>      print(i + j + k)
>```
>
>
>파이썬에서는 `itertools.product`를 이용하여 곱집합을 간단하게 구해낼 수 있다.
>
>```python
>import itertools
>
>iterable1 = 'ABCD'
>iterable2 = 'xy'
>iterable3 = '1234'
>itertools.product(iterable1, iterable2, iterable3)
>```
>
>

