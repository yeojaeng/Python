# 순열과 조합

---



### 문제 설명

---

>숫자를 담은 일차원 리스트, mylist에 대해 mylist의 원소로 이루어진 모든 순열을 사전순으로 리턴하는 함수 solution을 완성해주세요.



### 제한조건

---

>* mylist 의 길이는 1 이상 100 이하인 자연수입니다.



### 예시

---

>| mylist    | output                                                 |
>| --------- | ------------------------------------------------------ |
>| [2, 1]    | [[1,2], [2,1]]                                         |
>| [1, 2, 3] | [[1,2,3], [1,3,2], [2,1,3], [2,3,1], [3,1,2], [3,2,1]] |



### 제출코드

---

>```python
>import itertools
>
>def solution(mylist):
>    answer = []
>    for perm in itertools.permutations(mylist):
>        answer.append(list(perm))
>        answer.sort()
>    return answer
>```



### 코드설명

---

>해당 문제 풀이의 핵심은 `itertools`모듈의 `permutations`이다.
>
>가능한 모든 순열을 뽑아내기 위해 `itertools.permutations`를 사용하고 이를 `answer` 리스트에 `append`한다.
>
>그 뒤, 사전순 정렬을 위해 `sort()`함수를 이용해 정렬한 뒤 반환한다.
>
>`itertools` 모듈은 매우 유용하다..!!



