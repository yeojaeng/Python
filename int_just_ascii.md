# 파이썬을 파이썬답게

---

### int(x, base) n진법 으로 표기된 string을 10진법 숫자로 변환하기

>`base` 진법으로 표기된 숫자를 10진법 숫자 출력하라.
>
>**입력**
>
>입력으로는 공백으로 구분된 숫자가 두개 주어진다.
>
>첫번쨰 숫자는 `num` 을 나타내며, 두번째 숫자는 `base`를 나타낸다.
>
>**출력**
>
>`base`진법으로 표기된 `num`을 10진법 숫자로 출력하라.
>
>**제한조건**
>
>* `base`는 10이하 자연수이다.
>* `num`은 3000이하 자연수이다.
>
>**예시**
>
>| input | output |
>| ----- | ------ |
>| 12 3  | 5      |
>| 444 5 | 12 4   |

나의 경우, 일단 test_case만 만족하자라는 생각으로 매우 무식하게 코드를 작성했다.

```python
num, base = map(int, input().split(' '))
result = 0
num = str(num)
for i in range(len(num)):
    result += int(num[i]) * (base**(len(num) = (i+1)))
print(result)
```

**n진법으로 표기된 string을 10진법 숫자로 변환하기**

진법 변환 문제는 알고리즘 문제로 자주 나오는 유형이다..

다른 언어에서나 또는 이 기능을 모르는 보통인들은 for문을 이용해 숫자를 곱해가며 문제를 풀 것이다.

필자 또한 그랬던 것 처럼..ㅜㅜ

그러나 파이썬에서는 **int(x, base = 10)** 와 같이 진법 변환을 지원한다..!!!

이 기본적인 함수를 잘 쓰면 코드를 짧게 쓸 수 있으며 시간 또한 절약할 수 있다.

```python
num,base = map(int, input().split(' '))
result = int(num, base)
```



### ljust, center, rjust - 문자열 정렬



>**문제 설명**
>
>문자열 s와 자연수 n이 입력으로 주어진다. 
>
>문자열 s를 좌측/ 가운데/ 우측 정렬한 길이 n인 문자열을 한 줄씩 프린트하라.
>
>**제한조건**
>
>* s의 길이는 n보다 작다.
>* (n-s의 길이)는 짝수다.
>* s는 알파벳과 숫자로만 이루어져 있으며, 공백 문자가 포함되어 있지 않다.

이번엔 문자열 정렬을 위한 함수인 **ljust, center, rjust**를 사용한다.

string의 메서드를 사용하여 문자열을 보다 쉽게 정렬할 수 있다.

```python
s = 'abc'
n = 7
s.ljust(n)	# 좌측 정렬
s.center(n)	# 가운데 정렬
s.rjust(n)	# 우측 정렬
```



### ascii_lowercase, ascii_uppercase - string module

보통 다른언어에서나 이 기능을 모르는 경우에는 a-z까지의 소문자 혹은 대문자를 가져오기 위해서는

배열에 일일히 알파벳을 저장하곤 한다.

파이썬에서는 이러한 데이터를 **상수(constants)**로 정의해놓았다.

```python
import string
string.ascii_lowercase # 소문자 a-z
string.ascii_uppercase # 대문자 a-z
string.ascii_letters   # 모든 아스키 문자, 대소문자 모두
string.digits 		  # 숫자 0~9
```

이렇게 간단하게 가져와서 쓸 수 있다.