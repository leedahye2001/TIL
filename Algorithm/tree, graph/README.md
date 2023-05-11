<h2>23.05.11</h2>
<a href="https://velog.io/@leedahye2001/%ED%8A%B8%EB%A6%AC-%EA%B7%B8%EB%9E%98%ED%94%84">danshye.log 바로가기 :)</a>
<br>
<h3>🙋‍♀️ [Algorithm] Tree, Graph - c++</h3>
<br>


## 1. 트리

### 1-1 트리의 개요

트리 : 정점과 선분을 이용하여 `사이클을 이루지 않도록 구성한` 그래프의 특수한 형태

- 트리는 하나의 기억 공간을 노드라고 하며, 노드와 노드를 연결하는 선을 링크라고 함
- 트리는 가족의 계보, 조직도 등을 표현하기에 적합

**트리 관련 용어**

- 노드(Node) : 트리의 기본 요소로서 자료 항목과 다른 항목에 대한 가지를 합친 것
- 근 노드(Root Node) : 트리의 맨 위에 있는 노드
- 디그리(Degree, 차수) : 각 노드에서 뻗어나온 가지의 수
- 단말 노드(Terminal Node) = 잎 노드(Leaf Node) : 자식이 하나도 없는 노드, 즉 디그리가 0인 노드
- 자식 노드(Son Node) : 어떤 노드에 연결된 다음 레벨의 노드들
- 부모 노드(Parent Node) : 어떤 노드에 연결된 이전 레벨의 노드들
- 형제 노드(Brother Node, Sibling) : 동일한 부모를 갖는 노드들
- 트리의 디그리 : 노드들의 디그리 중에서 가장 많은 수

### 1-2 트리의 운행법

운행법(Traversal) : 트리를 구성하는 `각 노드들을 찾아가는 방법`

- 이진 트리를 운행하는 방법은 산술식의 표기법과 연관성을 가짐

**이진 트리의 운행법 (Root 위치 확인하기)**

- Preorder 운행 : Root ⇒ Left ⇒ Right 순으로 운행
- Inorder 운행 : Left ⇒ Root ⇒ Right 순으로 운행
- Postorder 운행 : Left ⇒ Right ⇒ Root 순으로 운행

### 1-3 수식의 표기법

산술식을 계산하기 위해 기억공간에 기억시키는 방법으로 `이진 트리`를 많이 사용한다. 이진 트리로 만들어진 수식을 인오더, 프리오더, 포스트오더로 운행하면 각각 중위, 전위, 후위 표기법이 된다.

- 전위 표기법(PreFix) : 연산자 ⇒ Left ⇒ Right, +AB
- 중위 표기법(InFix) : Left ⇒ 연산자 ⇒ Right, A+B
- 후위 표기법(PostFix) : Left ⇒ Right ⇒ 연산자, AB+

## 2. 그래프

### 2-1 그래프란?

그래프 : 노드와 노드 사이에 연결된 간선의 정보를 가지고 있는 자료구조

|  | 그래프 | 트리 |
| --- | --- | --- |
| 방향성 | 방향 그래프 혹은 무방향 그래프 | 방향 그래프 |
| 순환성 | 순환 및 비순환 | 비순환 |
| 루트 노드 존재 여부 | 루트 노드가 없음 | 루트 노드가 존재 |
| 노드간 관계성 | 부모와 자식 관계 없음 | 부모와 자식 관계 |
| 모델의 종류 | 네트워크 모델 | 계층 모델 |

**그래프의 구현 방법 (두 방식은 메모리와 속도 측면에서 구별된다는 특징이 있음)**

노드의 개수가 V, 간선의 개수가 E 인 그래프에서

- 인접 행렬(Adjacency Matrix) : 2차원 배열을 사용하는 방식
    - 간선 정보를 저장하기 위해서 O(V^2) 만큼의 메모리 공간이 필요
    - 특정 노드 A에서 다른 노드 B로 이어진 간선의 비용을 O(1) 시간으로 즉시 알 수 있음
- 인접 리스트(Adjacency List) : 리스트를 사용하는 방식
    - 간선의 개수만큼인 O(E)만큼만 메모리 공간이 필요
    - O(V)만큼의 시간이 소요

### 2-2 다양한 그래프 알고리즘

### 플로이드 워셜 알고리즘

- 인접 행렬을 이용하는 방식
- 모든 노드에 대하여 다른 노드로 가는 최소 비용을 V^2크기의 2차원 리스트에 저장한 뒤, 해당 비용을 갱신하여 최단 거리를 계산
- 최단 경로를 찾는 문제 출제 시, `노드의 개수가 적은 경우`에는 이 알고리즘 이용!

### 다익스트라 최단 경로 알고리즘

- 인접 리스트를 이용하는 방식
- 노드의 개수가 V개 일 때는 V개의 리스트를 만들어서 각 노드와 연결된 모든 간선에 대한 정보를 리스트에 저장
- 최단 경로 찾는 문제 출제 시, `노드와 간선의 개수가 많은 경우`에는 우선순위 큐와 함께 사용

### 2-3 서로소 집합 자료구조

서로소 집합 자료구조 : 서로소 부분 집합들로 나누어진 원소들의 데이터를 처리하기 위한 자료구조

- union-find(합치기 찾기) 자료구조라고 불리기도 함
- 두 집합이 서로소 관계인지를 확인할 수 있다 == 각 집합이 어떤 원소를 공통으로 갖고 있는지 확인할 수 있다

**서로소 집합 자료구조을 조작 가능하게 하는 2개의 연산**

- union(합집합) : 2개의 원소가 포함된 집합을 하나의 집합으로 합치는 연산
- find(찾기) : 특정한 원소가 속한 집합이 어떤 집합인지 알려주는 연산

**서로소 집합 계산 알고리즘**

1. union(합집합) 연산을 확인하여, 서로 연결된 두 노드를 확인한다.
    - A와 B의 루트 노드 A’ ,B’를 각각 찾는다
    - A’를 B’의 부모 노드로 설정한다
2. 모든 union(합집합) 연산을 처리할 때까지 위의 과정을 반복한다.

⇒ 이것이 트리를 이용해 서로소 집합을 계산하는 알고리즘

### 서로소 집합 알고리즘 소스코드

```python
# 특정 원소가 속한 집합 찾기
def find_parent(parent, x) :
	# 루트 노드가 아니라면, 루트 노드를 찾을 때까지 재귀적 호출
    if parent[x] != x :
    	return find_parent(parent, parent[x])
    return x
    
# 두 원소가 속한 집합을 합치기
def union_parent(parent, a, b) :
	a = find_parent(parent, a)
    b = find_parent(parent, b)
    if a < b :
    	parent[b] = a
    else :
    	parent[a] = b
        
# 노드의 개수와 간선(union 연산)의 개수 입력받기
v, e = map(int, input().split())
parent = [0] * (v + 1) # 부모 테이블 초기화

# 부모 테이블상에서, 부모를 자기 자신으로 초기화
for i in range(1, v + 1) :
	parent[i] = i
    
# union 연산을 각각 수행
for i in range(e) :
	a, b = map(int, input().split())
    union_parent(parent, a, b)
    
# 각 원소가 속한 집합 출력
print('각 원소가 속한 집합: ', end='')
for i in range(1, v + 1) :
	print(find_parent(parent, i), end=' ')
    
print()

# 부모 테이블 내용 출력
print('부모 테이블 : ', end='')
for i in range(1, v + 1) :
	print(parent[i], end=' ')
```

### 서로소 집합 알고리즘의 시간 복잡도

노드의 개수가 V개이고, 최대 V-1개의 union 연산과 M개의 find 연산이 가능할 때 경로 압축 방법을 적용한 시간 복잡도는 O(V+M(1+log2-M/VV))

### 서로소 집합을 활용한 사이클 판별

무방향 그래프 내에서의 사이클을 판별할 때 사용할 수 있음

- 참고로 방향 그래프에서의 사이클 여부는 DFS를 이용하여 판별할 수 있음

**사이클 판별 알고리즘**

1. 각 간선을 확인하며 두 노드의 루트 노드를 확인한다.
- 루트 노드가 서로 다르다면 두 노드에 대하여 union 연산을 수행한다.
- 루트 노드가 서로 같다면 사이클이 발생한 것이다.
1. 그래프에 포함되어 있는 모든 간선에 대하여 위의 과정을 반복한다.

### 서로소 집합을 활용한 사이클 판별 소스코드

```python
# 특정 원소가 속한 집합을 찾기
def find_parent(parent, x) :
	# 루트 노드가 아니라면, 루트 노드를 찾을 때까지 재귀적 호출
    if parent[x] != x :
    	parent[x] = find_parent(parent, parent[x])
    return parent[x]
    
# 두 원소가 속한 집합을 합치기
def union_parent(parent, a, b) :
	a = find_parent(parent, a)
    b = find_parent(parent, b)
    if a < b :
    	parent[b] = a
    else :
    	parent[a] = b

# 노드의 개수와 간선(union 연산)의 개수 입력받기
v, e = map(int, input().split())
parent = [0] * (v + 1) # 부모 테이블 초기화

# 부모 테이블상에서, 부모를 자기 자신으로 초기화
for i in range(1, v + 1) :
	parent[i] = i
    
cycle = False # 사이클 발생 여부

for i in range(e) :
	a, b = map(int, input().split())
    # 사이클이 발생한 경우 종료
    if find_parent(parent, a) == find_parent(parent, b) :
    	cycle = True
        break
    # 사이클이 발생하지 않았다면 합집합(union) 수행
    else :
    	union_parent(parent, a, b)
        
if cycle :
	print("사이클이 발생했습니다.")
else :
	print("사이클이 발생하지 않았습니다.")
```

### 2-4 신장 트리

신장 트리(Spinning Tree) : 하나의 그래프가 있을 때 모든 노드를 포함하면서 사이클이 존재하지 않는 부분 그래프를 의미

- 이때 모든 노드가 포함되어 서로 연결되면서 사이클이 존재하지 않는 조건은 트리의 성립 조건이기도 함

### 2-5 크루스칼 알고리즘

**크루스칼 알고리즘** : `최소 신장 트리 알고리즘`의 대표적인 알고리즘

- 가장 적은 비용으로 모든 노드를 연결할 수 있음
- 최소 신장 트리 알고리즘 : 신장 트리 중에서 최소 비용으로 만들 수 있는 신장 트리를 찾는 알고리즘

**최소 신장 트리 알고리즘**

1. 간선 데이터를 비용에 따라 오름차순으로 정렬한다.
2. 간선을 하나씩 확인하며 현재의 간선이 사이클을 발생시키는지 확인한다.
- 사이클이 발생하지 않는 경우, 최소 신장 트리에 포함
- 사이클이 발생할 경우, 최소 신장 트리에 포함시키지 않음
1. 모든 간선에 대하여 2번의 과정을 반복

### 크루스칼 알고리즘 소스코드

```python
# 특정 원소가 속한 집합을 찾기
def find_parent(parent, x) :
	# 루트 노드가 아니라면, 루트 노드를 찾을 때까지 재귀적 호출
    if parent[x] != x :
    	parent[x] = find_parent(parent, parent[x])
    return parent[x]
    
# 두 원소가 속한 집합을 합치기
def union_parent(parent, a, b) :
	a = find_parent(parent, a)
    b = find_parent(parent, b)
    if a < b :
    	parent[b] = a
    else :
    	parent[a] = b
        
# 노드의 개수와 간선(union 연산)의 개수 입력받기
v, e = map(int, input().split())
parent = [0] * (v + 1)	# 부모 테이블 초기화

# 모든 간선을 담을 리스트와 최종 비용을 담을 변수
edges = []
result = 0

# 부모 테이블상에서, 부모를 자기 자신으로 초기화
for i in range(1, v + 1) :
	parent[i] = i
    
# 모든 간선에 대한 정보 입력받기
for _ in range(e) :
	a, b, cost = map(int, input().split())
    # 비용순으로 정렬하기 위해서 튜플의 첫 번째 원소를 비용으로 설정
    edges.append((cost, a, b))
    
# 간선을 비용순으로 정렬
edges.sort()

# 간선을 하나씩 확인하며
for edge in edges :
	cost, a, b = edge
    # 사이클이 발생하지 않는 경우에만 집합에 포함
    if find_parent(parent, a) != find_parent(parent, b) :
    	union_parent(parent, a, b)
    	result += cost
        
print(result)
```

### 크루스칼 알고리즘의 시간 복잡도

간선의 개수가 E개일 때, O(ElogE)의 시간 복잡도를 가짐

- 크루스칼 알고리즘에서 시간이 가장 오래걸리는 부분이 간선을 정렬하는 작업
- E개의 데이터를 정렬했을 때의 시간 복잡도는 O(ElogE)이기 때문
- 크루스칼 내부에서 사용되는 서로소 집합 알고리즘의 시간 복잡도는 정렬 알고리즘의 시간 복잡도 보다 작으므로 무시
