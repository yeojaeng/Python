#deque

---

일반적으로 사용되는 자료구조 `Queue`는 `FIFO`방식을 채택하고 있다.

즉, **First In First Out** 방식의 자료구조이다.

그러나 큐 중에 한쪽 방향이 아닌 양방향에서 데이터를 처리할 수 있는 자료구조가 존재하는데 이것이 `deque`이다.

( **deque = Doubly - ended Queue** )

간단히 이야기하여 앞 또는 뒤 양쪽에서 요소(element)를 추가하거나 지울 수 있다.

아래는 `deque`에서 주로 사용되어지는 메서드들의 사용예시이다.

```python
from collections import deque

dq = deque([10, 20, 30, 40, 50])

print('Deque: ', dq)
# Deque:  deque([10, 20, 30, 40, 50])

# 오른쪽으로 원소 추가
dq.append(60)
print('Deque: ', dq)
# Deque:  deque([10, 20, 30, 40, 50, 60])

# 왼쪽으로 원소 추가
dq.appendleft(0)
print('Deque: ', dq)
# Deque:  deque([0, 10, 20, 30, 40, 50, 60])

# 오른쪽으로 복수개의 원소 추가
dq.extend([70, 80])
print('Deque: ', dq)
# Deque:  deque([0, 10, 20, 30, 40, 50, 60, 70, 80])

# 왼쪽으로 복수개의 원소 추가
dq.extendleft([-20, -10])
print('Deque: ', dq)
# Deque:  deque([-10, -20, 0, 10, 20, 30, 40, 50, 60, 70, 80])

# 값 삭제
dq.remove(0)
print('Deque: ', dq)
# Deque:  deque([-10, -20, 10, 20, 30, 40, 50, 60, 70, 80])

# 오른쪽 끝값 pop
dq.pop()
print('Deque: ', dq)
# Deque:  deque([-10, -20, 10, 20, 30, 40, 50, 60, 70])

# 왼쪽 끝값 pop
dq.popleft()
print('Deque: ', dq)
# Deque:  deque([-20, 10, 20, 30, 40, 50, 60, 70])

# 한칸씩 뒤로 rotate
dq.rotate(1)
print('Deque: ', dq)
# Deque:  deque([70, -20, 10, 20, 30, 40, 50, 60])

# 한칸씩 앞으로 rotate
dq.rotate(-1)
print('Deque: ', dq)
# Deque:  deque([-20, 10, 20, 30, 40, 50, 60, 70])
```

`rotate()`를 활용하여 모든 요소를 한번에 움직일 수 있다.

