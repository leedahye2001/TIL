![다운로드](https://user-images.githubusercontent.com/94473725/194716045-5c13fa57-9021-465e-8cb0-3e9bea661278.png)


## 힙(Heap)이란?

: 최댓값과 최솟값을 빠르게 찾기 위해 고안된 자료구조

- 각 노드의 key값이 해당 노드의 자식 노드의 key값보다 작지 않거나 크지 않은 완전 이진트리
- 키 값의 대소관계는 `**부모-자식** 노드 간에만` 성립하며 형제노드 간에는 영향을 미치지 않음
- 자식 노드의 최대 개수는 힙의 종류에 따라 다르지만 이진트리에서는 최대 2개 (완전이진트리를 사용한다고 가정)
- i번째 노드의 자식 노드가 2개인데 왼쪽 자식노드는 2i, 오른쪽 자식 노드는 2i+1이고, 부모 노드는 i/2가 됨.

⭐️ **최대 힙(max heap)**

: 각 노드의 키 값이 그 자식 노드의 키 값보다 작지 않은 힙

`key(T.parent(v)) > key(v)`

⭐️ **최소 힙(mix heap)**

: 각 노드의 키 값이 그 자식 노드의 키 값보다 크지 않은 힙

`key(T.parent(v)) < key(v)`

⭐️ **시간 복잡도**

: O(log n)

⭐️ **삽입 연산 (insertion)**

- 삽입하고자 하는 값을 트리의 가장 마지막 원소에 추가
- 부모 노드와의 대소관계를 비교하면서 만족할 때까지 자리 교환을 반복

 ⭐️ **삭제 연산 (deletion)**

- 힙에서는 루트 노드만 삭제가 가능하므로 루트 노드를 제거
- 가장 마지막 노드를 루트로 이동시킴
- 자식 노드와 비교하여 조건이 만족할 때까지 이동시킴

---

## **Heapq module**

: 파이썬에서 제공하는 힙큐 모듈, 일반적인 리스트를 min heap처럼 다룰 수 있게 해줌

👉 **모듈 임포트**

```python
import heapq
```

👉 **노드 추가 : heappush() 메소드를 이용**

```python
heap = []
heapq.heappush(heap, 1)
```

👉 **노드 삭제 : heappop() 메소드 이용**

```python
return heapq.heappop(heap)
# 최소 값을 꺼내지 않고 리턴만 하려면 인덱스로 접근
print(heap[0])
```

*인덱스 1이 2번째로 작다는 보장은 없으므로 n번째로 작은 원소를 얻고 싶다면  n-1개의 원소를 빼내야 함!*

<br>

👉 **기존에 사용한 리스트를 힙으로 변환하기 : heapify 메소드 이용**

시간 복잡도 : O(n)

```python
tmp = [4, 7, 3, 1];
heapq.heapify(tmp)
```

👉 **최대 힙 만들기 : 우선순위가 포함된 튜플 이용하기**

```python
import heapq

numbers = [7, 2, 4, 8, 9, 1]
heap = []

for num in numbers:
	# (우선 순위, 값)
	heapq.heappush(heap, (-num, num))

while heap:
	# index 1
	print(heapq.heappop(heap)[1])
```
