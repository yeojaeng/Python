# collections module - Counter

---

컨테이너 내 동일한 값의 자료가 몇개인지 파악하는데 사용하는 객체이다.

>A Counter is a dict subclass for counting hashable objects. It is an urordered collection
>where elements are stored as dictionary keys and their counts are stored as dictionary values.
>Counts are allowed to be any integer value including zero or negative counts.
>The Counter class is similar to bags or multisets in other languages.



`collections.Counter()`의 결과값은 `Dict` 형태로 출력된다.

아래 예제를 통해 `collections.Counter()`에 대하여 이해해보자.

### 1. Counter()의 다양한 입력값

### 1) List



```python
# collections.Counter ex1
# input : list
import collections

arr = ['a', 'b', 'c', 'd' ,'a' ,'b', 'c']
print(collections.Counter(arr))
print(*collections.Counter(arr))

# Counter({'a': 2, 'b': 2, 'c': 2, 'd': 1})
# a b c d
```

unpacking을 통하여 iterable 객체들을 출력하면 위 예시와 같이 key값들만 출력되는것을 확인할 수 있다.



### 2) Dict

`collections.Counter()`는 아래와 같이 요소의 개수가 많은 것을 우선으로 출력한다.
입력값을 Dict 자료형으로 넣어줄 경우, 결과값 또한 당연히 Dict 형태이다.

```python
# collections.Counter ex2
# input : dict
import collections

ex_dict = ({'a': 3, 'b':2, 'c':1})
print(collections.Counter(ex_dict))
print(*collections.Counter(ex_dict))

# Counter({'a': 3, 'b': 2, 'c': 1})
# a b c
```



### 3) 값 = 개수

`collections.Counter()`는 아래와 같이 값=개수 형태로 입력을 전달할 수 있다.
예를들어, collections.Counter(a=3, b=2, c=1)의 경우, ['a', 'a', 'a', 'b', 'b', 'c']형태로 반환한다.

```python
# collections.Counter ex3
# '값 = 개수'
import collections

arr = collections.Counter(a=3, b=2, c=1)
print(collections.Counter(arr))
print(*collections.Counter(arr))

# Counter({'a': 3, 'b': 2, 'c': 1})
# a b c
```



### 2. Counter를 이용한 연산

`collections.Counter()`는 산술 / 집합 연산이 가능하다.

### 1) 덧셈 연산

```python
# collection.Counter()
# 덧셈 연산
import collections

a = collections.Counter(['a', 'b', 'c', 'a', 'b' ,'c'])
b = collections.Counter('collections')

print(a)
print(b)
print(a+b)

print(*a)
print(*b)
print(*(a+b))

'''
Counter({'a': 2, 'b': 2, 'c': 2})
Counter({'c': 2, 'o': 2, 'l': 2, 'e': 1, 't': 1, 'i': 1, 'n': 1, 's': 1})
Counter({'c': 4, 'a': 2, 'b': 2, 'o': 2, 'l': 2, 'e': 1, 't': 1, 'i': 1, 'n': 1, 's': 1})
a b c
c o l e t i n s
a b c o l e t i n s
'''
```



### 2) 뺄셈 연산

`collections.Counter()`의 뺄셈 연산의 경우, 연산의 결과가 음수인 값은 출력하지 않는다.

```python
# collection.Counter()
# 뺄셈 연산
import collections

a = collections.Counter('aaaabbbbbccccc')
b = collections.Counter('aaaaaaaaaaaaaaaaabb')

print(a-b)
print(*(a-b))

'''
Counter({'c': 5, 'b': 3})
b c
'''
```



### 3) 교집합 , 차집합

`collections.Counter()`의 교집합 및 합집합의 출력값은 {값 : 개수}의 `Dict` 형태로 반환한다.

```python
# collection.Counter()
# 교집합과 차집합
import collections

a = collections.Counter('aaaaaaabbbbccccc')
b = collections.Counter('asdaasdasdasd')

print(a&b)
print(a|b)
print(*(a&b))
print(*(a|b))

'''
Counter({'a': 5})
Counter({'a': 7, 'c': 5, 'b': 4, 's': 4, 'd': 4})
a
a b c s d
'''
```





