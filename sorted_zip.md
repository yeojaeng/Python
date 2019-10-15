# 파이썬을 파이썬답게

---

>### 원본을 유지한채, 정렬된 리스트 구하기 - sorted
>
>파이썬의 `sort()`함수를 사용하면 리스트의 원소를 정렬할 수 있다.
>이때, `sort`함수는 원본의 멤버 순서를 변경하지 않는다.
>따라서 원본의 순서는 변경하지 않고, 정렬된 값을 구하려면 `sort`함수를 사용할 수 없다.
>이러한 경우에는?

---

> ​	일반적인 경우, `deep copy` 또는 `sort` 함수를 이용한다.
>
> ```python
> list1 = [3, 2, 1]
> list2 = [i for i in list1] # 또는  copy.deepcopy
> list2.sort()
> ```
>
> 파이썬에서는`sorted()`를 사용한다, 이러한 경우 반복문이나 `deepcopy`를 쓰지 않아도 새로운 정렬된 리스트를 얻을수 있다.
>
> ```python
> list1 = [3, 2, 1]
> list2 = sorted(list1)
> ```

---

## 문제 설명

다음을 만족하는 함수, solution을 완성하라.

* solution 함수는 이차원 리스트, mylist를 인자로 받는다.
* solution 함수는 mylist 원소의 행과 열을 뒤집은 값을 리턴해야 한다.

예를 들어 mylist [ [1,2,3], [4,5,6], [7,8,9] ]가 주어진 경우, solution 함수는 [ [1,4,7], [2,5,8], [,3,6,9] ]를 반환하여야 한다.

### 제한 조건

* `mylist`의 원소 길이는 모두 같다.
* `mylist`의 길이는 `mylist[0]`의 길이와 같다.
* 각 리스트의 길이는 100 이하인 자연수이다.

```python
def solution(mylist):
  answer = list(map(list, zip(*mylist)))
  return answer
```

iterable 앞에 붙는 *는 unpacing을 해주는 역할을 한다.

---

> **2차원 리스트 뒤집기 - zip**
>
> 보통은 아래와 같이 2중 for문을 이용하여 리스트의 row와 column을 뒤집는다.
>
> ```python
> mylist = [ [1,2,3], [4,5,6], [7,8,9] ]
> new_list = [ [], [], [] ]
> 
> for i in range(3):
>   for j in range(3):
>     new_list[i].append(mylist[j][i])
>    
> ```
>
> 파이썬에서는 `zip`과 `unpacking`을 이용하면 한 줄로 리스트를 뒤집을 수 있다.
>
> ```python
> mylist = [ [1,2,3,], [4,5,6], [7,8,9] ]
> new_list = list(map(list, zip(*mylist)))
> ```

---

### zip 함수에 대해

**Python 3 한글 번역 -zip**에 따르면 

`zip(*iterables)는 각 iterables의 요소들을 모으는 이터레이터를 만든다.`
`튜플의 이터레이터를 반환하는데, i번째 튜플은 각 인자로 전달된 시퀀스나 이터러블의 i번째 요소를 포함한다.`

```python
mylist = [1, 2, 3]
new_list = [40, 50, 60]
for i in zip(mylist, new_list):
  print(i)

#(1, 40)
#(2, 50)
#(3, 60)
```

**사용예 #1 - 여러 개의 iterable 동시에 순회시**

```python
list1 = [1, 2, 3, 4]
list2 = [100, 120, 30, 300]
list3 = [392, 2, 33, 1]
answer = []
for i, j, k in zip(list1, list2, list3):
  print(i + j + k)
#493
#124
#66
#305
```

**사용예 #2 - key 리스트와 Value 리스트로 딕셔너리 생성하기**

`Python의 zip함수와 dict 생성자를 이용하면 코드 단 한 줄로, 두 리스트를 합쳐 딕셔너리로 만들 수 있다.`

```python
animals = ['cat', 'dog', 'lion']
sounds = ['meow', 'woof', 'roar']
answer = dict(zip(animals, sounds))
#{'cat' : 'meow', 'dog' : 'woof', 'lion' : 'roar'}
```

