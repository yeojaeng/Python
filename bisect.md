# Python bisect

---

>알고리즘 문제를 풀다 보면 **이진 탐색**을 써야할 경우가 존재한다.
>
>이러한 문제를 풀 때 마다 이진 탐색 알고리즘을 작성하는 것은 다소 효율적이지 못하다.
>
>이번에는 Python의 이진 탐색 모듈, `bisect`에 대해 알아보도록 한다.



### 일반적 이진탐색

---

>다른 언어 또는 파이썬을 이용하여도 이 기능을 모르는 경우에는 이진탐색 함수를 직접 작성한다.
>
>```python
>def bisect(a, x, lo=0, hi=None):
>    if lo < 0:
>        raise ValueError('lo must be non-negative')
>    if hi is None:
>        hi = len(a)
>    while lo < hi:
>        mid = (lo + hi) // 2
>        if a[mid] < x:
>            lo = mid + 1
>        else:
>            hi = mid
>    return lo
>
>mylist = [1, 2, 3, 7, 9, 11, 33]
>print(bisect(mylist, 3))
>```
>
>[출처](https://github.com/python/cpython/blob/master/Lib/bisect.py)



### 파이썬의 bisect

---

>```python
>import bisect
>mylist = [1, 2, 3, 7, 9, 11, 33]
>print(bisect.bisect(mylist, 3))
>```
>
>파이썬에서는 `bisect.bisect` 메소드를 사용하면 이 코드를 위와 같이 간략하게 작성할 수 있다.
>
>
>
>---
>
>`bisect.bisect(a, x, lo=0, hi=len(a))`
>
>`bisect()`는 `a`라는 오름차순으로 정렬된 시퀀스에 `x`값이 들어갈 위치를 리턴한다.
>
>```python
>import bisect
>
>sequence = [1, 3, 4, 5]
>print(bisect.bisect(sequence, 2))
>
>#1
>```
>
>`lo`와 `hi`를 통해 검색하는 시퀀스의 영역을 제어할 수 있다.
>
>`default`로는 시퀀스 전체를 범위로 한다.
>
>`bisect()`는 `bisect_right()`와 동일하며 `bisect_left()`함수도 제공한다.
>
>두 함수의 차이는 `x`와 동일한 값이 시퀀스 `a`에 존재할 때 다른 값을 반환한다.
>
>**`bisect_right()`는 `x`와 동일한 값이 시퀀스 `a`에 존재할 경우, `x`와 동일한 값의 뒤 위치를 리턴한다.**
>
>**`bisect_left()`는 `x`와 동일한 값 위치를 리턴한다.**
>
>```python
>import bisect
>
>sequence = [1, 3, 4, 5]
>print(bisect.bisect_left(sequence, 3))
>print(bisect.bisect_right(seuqnece, 3))
>
># 1
># 2
>```
>
>`bisect.insort(a, x, lo=0, hi=len(a))`
>
>`insort()`는  `a`라는 오름차순 정렬 시퀀스에 `x`값을 삽입한다.
>
>```python
>import bisect
>
>sequence = [1, 3, 4, 5]
>bisect.insort(sequence, 2)
>print(sequence)
>
># [1, 2, 3, 4, 5]
>
>```
>
>`bisect()`와 마찬가지로 `lo`와 `hi`를 통해 검색하는 시퀀스의 영역을 제어할 수 있다.
>
>`default`로 시퀀스 전체를 범위로 한다.
>
>`insort()`는 `insort_right()`와 같으며 `insort_left()`가 존재한다.
>
>`insort_right()`는 `x`와 동일한 값이 시퀀스 `a`에 존재할 때, `x`와 동일한 값 바로 뒤에 `x`를  삽입한다.
>
>`insort_left()`는 `x`와 동일한 값이 시퀀스 `a`에 존재할 때, `x`와 동일한 값 위치에 `x`를 삽입한다.