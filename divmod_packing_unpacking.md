## 파이썬을 파이썬답게

---

```python
def answer(mylist):
    answer = []
    for i in mylist:
        answer.append(len(i))
    return answer
```

```python
def solution(mylist):
    return list(map(len, mylist))
```



### 용어 정리

-**Iterable** : 자신의 멤버를 한 번에 하나씩 리턴할 수 있는 객체. list, str, tupe, dict...등이 여기에 속한다.

-**sequence** : int 타입의 idx를 통해, 원소에 접근할 수 있는 객체로 Iterable의 하위 카테고리
list, str, tupe이 여기에 속한다.

### 몫과 나머지 - divmod

알고리즘 문제를 풀다 보면, 정수를 나눈 몫과 나머지를 구해야 할 때가 있다.

정수 a,b가 있을 때 보통 나머지와 몫을 아래와 같이 구한다.

```python
a = 7
b = 5
print(a//b, a%b)
```

파이썬에서는 파이썬의 `divmod` 와 **unpacking**을 이용하면 다음과 같이 코드를 짤 수 있다.

```python
a = 7
b = 5
print( *divmod(a, b))
```

>#### **divmod**
>
>`divmod(a,b)` 는 2개의 숫자를 입력으로 받고 a를 b로 나눈 몫과 나머지를 튜플 형태로 돌려주는 내장 함수이다.
>
>그러나 `divmod`는 작은 숫자를 다룰 때는 `a//b, a%b` 보다 느리다. 하지만 큰 숫자를 다룰 때는 전자가 더욱 빠르다.

>**packing & unpacking**
>
>**packing**
>
>`print` 함수는 출력하고자 하는 객체가 몇개던지 상관하지 않고 출력해준다.
>
>```python
>print("가나다", "abc", "123")
>#output : 가나다 abc 123
>```
>
>이러한 경우와 같이 받을 인자의 갯수를 유연하게 지정할 수 있다면 보다 유연한 코드르를 제공할 수 있다.
>
>파이썬은 이런 경우를 지원하기 위헤 `packing`을 지원한다.
>
>**패킹**은 인자로 받은 여러개의 값을 하나의 객체로 합쳐서 받을수 있도록 지원한다.
>
>위치인자 패킹은 `*`한개를 매개변수 앞에 붙임으로 사용한다.
>
>```python
>def func(*args):
>    print(args)
>    print(type(args))
>```
>
>이런식으로 매개변수 이름 앞에 `*`를 붙여준다면, 위치인자로 보낸 모든 객체들을 하나의 객체로 관리한다.
>
>```python
>func(1, 2, 3, 4, 5, 6, 'a', 'b')
>#(1, 2, 3, 4, 5, 6, 'a', 'b')
>#<class 'tuple'>
>```
>
>위와 동일하게 키워드 인자에 패킹은 `**`를 통해서도 작성할 수 있다.
>
>```python
>def kwpacking(**kwargs):
>    print(kwargs)
>    print(type(kwargs))
>    
>kwpacking(a=1, b=2, c=3)
>#{'a':1, 'b':2, 'c':3}
>#<class 'dict'>
>```
>
>키워드 인자는 패킹한 인자들을 key 와 value로 이뤄진 **딕셔너리**로 관리한다.
>
>
>
>**unpacking**
>
>`packing`과 반대되는 개념으로 `unpacking`이 존재한다.
>
>`packing`은 여러개의 객체를 하나의 객체로 합쳐주었다. `unpacking`은 여러개의 객체를 포함하고 있는 하나의 객체를 풀어주는 기능을 제공한다.
>
>함수에서 `unpacking`을 할때는, 매개변수에서 `*`를 붙이는게 아니라 인자 앞에 `*`를 붙여서 사용한다.
>
>> ​	동일하게 위치인자를 `unpacking`하는 경우는 *를, 키워드인자를 `unpacking`하는 경우는 `**`를 사용한다.
>
>```python
>def sum(a, b, c):
>    return a+b+c
>
>numbers = [1, 2, 3]
>sum(numbers)	# error
>
>print(sum(*numbers))	#출력 : 6
>```
>
>`[1, 2, 3]`을 인자로 보낼때, `*`를 붙이면 `unpacking`이 발생한다.
>
>`unpacking`은 아래와 같은 순서로 변경되어 실행된다.
>
>```python
>1. sum(*numbers)
>2. sum(*[1, 2, 3])
>3. sum(1, 2, 3)
>```
>
>`unpacking`은 함수를 호출할 때 객체를 풀어주는 개념이기 때문에, 해체된 결과가 함수의 매개변수의 갯수와 다르다면 에러가 발생한다.
>
>```python
>sum(*[1, 2, 3, 4])
>#TypeError: sum() takes 3 positional arguments but 4 were given
>```
>
>**참고로, 위치인자를 unpacking할때는 Container 객체라면 모두 가능하다.**
>
>





