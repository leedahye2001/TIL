<h2>23.05.14</h2>
<a href="https://velog.io/@leedahye2001/%EC%A0%95%EB%A0%AC">danshye.log 바로가기 :)</a>
<br>
<h3>🙋‍♀️ [Algorithm] Sort - python</h3>
<br>

## 1. 정렬

### 1-1 정렬 알고리즘 개요

정렬 : 데이터를 특정한 기준에 따라서 순서대로 나열하는 것

- 프로그램에서 데이터를 오름 or 내림차순 등 정렬해서 사용하는 경우가 많아 가장 많이 사용되는 알고리즘 중 하나임
- 이진 탐색의 전처리 과정이기도 함
- 파이썬에서는 특정 리스트의 원소를 뒤집는 메서드를 제공하며, 리스트를 뒤집는 연산은 O(N) 복잡도로 간단히 수행할 수 있음

### 1-2 선택 정렬

선택 정렬 : `가장 작은 데이터를 선택`해 맨 앞에 있는 데이터와 바꾸고, 그다음 작은 데이터를 선택해 앞에서 두 번째 데이터와 바꾸는 방식 ⇒ 매번 가장 작은 것을 선택

- 가장 작은 데이터를 앞으로 보내는 과정을 N-1번 반복하면 정렬이 완료된다.

### 선택 정렬 소스코드

```python
array = [7, 5, 9, 0, 3, 1, 6, 2, 4, 8]

for i in range(len(array)):
	min_index = i  # 가장 작은 원소의 인덱스
	for j in range(i+1, len(array)):
		if array[min_index] > array[j]:
			min_index = j
	array[i], array[min_index] = array[min_index, array[i]]  # swap                                             

print(array)
```

<aside>
💡 위의 코드에서 알 수 있었던 점 : 임시 저장용 변수가 필요한 다른 C 언어 등과는 달리, 파이썬에서는 간단히 리스트 내 두 원소의 위치를 변경할 수 있다.

</aside>

### 선택 정렬의 시간 복잡도

*반복문이 얼마나 중첩되었는지를 기준으로 시간 복잡도 판단이 가능*

- N-1번 만큼 가장 작은 수를 찾아 맨 앞으로 보내고, 매번 가장 작은 수를 찾기 위해 비교 연산이 필요함
- (N^2 + N) / 2 번 연산을 수행한다고 표현이 가능 ⇒ 빅오 표기법으로  O(N^2)
    - 쉽게 말해, 코드 상 2중 반복문이 사용되었으므로 O(N^2) 라고 이해하면 됨

선택 정렬은 데이터가 10000개 이상이면 정렬 속도가 급격히 느려짐

| 데이터의 개수(N) | 선택 정렬 | 퀵 정렬 | 기본 정렬 라이브러리 |
| --- | --- | --- | --- |
| N = 100 | 0.0123s | 0.00156s | 0.00000753s |
| N = 1000 | 0.354s | 0.00343s | 0.0000365s |
| N = 10000 | 15.475s | 0.0312s | 0.000248s |

⇒ 선택 정렬은 다른 알고리즘에 비해 매우 비효율적임

### 1-3 삽입 정렬

삽입 정렬 : 특정한 `데이터를 적절한 위치에 삽입`하는 알고리즘 (특정 데이터가 적절한 위치에 들어가기 이전에, 그 앞까지의 데이터는 이미 정렬 되어 있다고 가정)

- 선택 정렬에 비해 실행 시간 측면에서 더 효율적인 알고리즘임
- 필요할 때만 위치를 바꾸므로 **‘데이터가 거의 정렬되어 있을 때’** 훨씬 효율적
- 정렬이 이루어진 원소는 항상 오름차순을 유지한다는 특징이 있음 ⇒ 이 특징 때문에 특정 데이터가 들어갈 위치를 선정할 때, 자기보다 작은 데이터를 만나면 그 자리에서 멈추면 됨

### 삽입 정렬 소스코드

```python
array = [7, 5, 9, 0, 3, 1, 6, 2, 4, 8]

for i in range(1, len(array)):
	for j in range(1, 0, -1):  # 인덱스 i부터 1까지 감소하며 반복하는 문법
		if array[j] > array[j-1]:  # 한 칸씩 왼쪽으로 이동
			array[j], array[j - 1] = array[j - 1], array[j]
		else:  # 자기보다 작은 데이터를 만나면 그 위치에 멈춤
			break                                          

print(array)
```

<aside>
💡 **위의 코드에서 알 수 있었던 점** : 임시 저장용 변수가 필요한 다른 C 언어 등과는 달리, 파이썬에서는 간단히 리스트 내 두 원소의 위치를 변경할 수 있다.

</aside>

### 삽입 정렬의 시간 복잡도

- **현재 리스트의 데이터가 거의 정렬되어있는 상태라면 매우 빠르게 동작함**
- 빅오 표기법으로  O(N^2)
    - 선택 정렬과 마찬가지로, 코드 상 2중 반복문이 사용되었으므로 O(N^2) 라고 이해하면 됨
    - 최선의 경우 O(N)

일반적으로 비효율적이나, 거의 정렬되어있는 상황에서는 퀵 정렬 보다 더 강력함

### 1-4 퀵 정렬

퀵 정렬 : `피벗(pivot)`을 설정하고 다음 큰 수와 작은 수를 교환한 후 `리스트를 반으로 나누는 방식`으로 동작

- 피벗(pivot)이란 큰 숫자와 작은 숫자를 교환할 때, 교환을 위한 기준을 이르는 말
- 가장 많이 사용되는 알고리즘
- 합병 정렬과 함께 대부분의 프로그래밍 언어에서 정렬 라이브러리의 근간이 되는 알고리즘
- 피벗 설정 후, 리스트 분할 방식에 따라 여러 가지 방식으로 퀵 정렬을 구분함
- 여기선 **호어 분할(Hoare Partition)** 방식을 기준으로 설명
    - 리스트에서 **첫 번째 데이터를 피벗**으로 정한다.

1. 왼쪽에서부터 피벗보다 큰 데이터를 찾고, 오른쪽에서부터 피벗보다 작은 데이터를 찾음
2. 그 다음 큰 데이터와 작은 데이터의 위치를 서로 교환

⇒ **피벗**에 대하여 정렬이 수행됨

퀵 정렬이 끝나는 조건은 언제일까?

- 현재 리스트의 데이터 개수가 1개인 경우
- 리스트의 원소가 1개라면, 이미 정렬이 되어있다고 간주할 수 있으며 분할이 불가능

### 퀵 정렬 소스코드

```python
array = [5, 7, 9, 0, 3, 1, 6, 2, 4, 8]

def quick_sort(array, start, end):
	if start >= end:  # 원소가 1개인 경우 종료
		return
	pivot = start
	left = start + 1
	right = end
	while left <= right:
		# 피벗보다 큰 데이터를 찾을 때까지 반복
		while left <= end and array[left] <= array[pivot]:
			left += 1
			# 피벗보다 작은 데이터를 찾을 때까지 반복
		while right > start and array[right] >= array[pivot]:
			right -= 1
		if left > right:
			array[right], array[pivot] = array[pivot], array[right]
		else:  # 엇갈리지 않았다면 작은 데이터와 큰 데이터를 교체
			array[left], array[right] = array[right], array[left]
	
	# 분할 이후 왼쪽 부분과 오른쪽 부분에서 각각 정렬 수행
	quick_sort(array, start, right - 1)
	quick_sort(array, right + 1, end)

quick_sort(array, 0, len(array - 1))
print(array)
```

### 파이썬 장점 살린 퀵 정렬 소스코드 (비교 연산 횟수 증가로 시간 면에서 비효율적)

```python
array = [5, 7, 9, 0, 3, 1, 6, 2, 4, 8]

def quick_sort(array):
	# 리스트가 하나 이하의 원소만을 담고 있다면 종료
	if len(array) <= 1
		return array
	
	pivot = array(0)  # 피벗은 첫 번째 원소
	tail = array[1:]  # 피벗을 제외한 리스트
	
	left_side = [x for x in tail if x <= pivot]  # 분할된 왼쪽 부분
	right_side = [x for x in tail if x > pivot]  # 분할된 오른쪽 부분
	
	# 분할 이후 왼쪽과 오른쪽 부분에서 각각 정렬 수행 후, 전체 리스트 반환
	return quick_sort(left_side) + [pivot] + quick_sort(right_side)

print(quick_sort(array))
```

### 퀵 정렬의 시간 복잡도

- 빅오 표기법으로 O(NlogN)
    - **최악의 경우 O(N^2) ⇒ 리스트의 가장 왼쪽 데이터를 피벗으로 삼을 때, 이미 정렬된 경우에서는 매우 느리게 동작한다.**
        - 삽입 정렬과는 반대라고 생각하면 됨
    - 선택, 삽입 정렬에 비해 매우 빠른 편 ⇒ 데이터가 무작위로 입력될 경우 빠르게 동작할 확률이 높음
- 데이터의 개수가 8개이며, 절반씩 나눈다고 가정한다면 ?
    - 이때 높이는 데이터의 개수가 N개일 때, 약 logN이라고 판단이 가능하다
    - 분할이 이루어지는 횟수가 기하급수적으로 감소하게 된다 (log는 밑이 2인 로그를 의미 ⇒ 10 가량)
    - N = 1000 일 때, log2N은 10과 비슷함 ⇒ 상대적으로 매우 작은 수

### 1-5 계수 정렬 (Count Sort)

계수 정렬 : `특정한 조건이 부합할 때만` 사용할 수 있지만 매우 빠른 정렬 알고리즘

- 데이터의 크기 범위가 제한되어 정수 형태로만 표현할 수 있을 때만 사용이 가능함
    - 일반적으로 가장 큰 데이터와 가장 작은 데이터의 차이가 1,000,000 을 넘지 않을 때 효과적으로 사용 가능
    - 그 이유는, 모든 범위를 담을 수 있는 크기의 리스트(배열)를 선언해야 하기 때문임
- 앞의 선택, 삽입, 퀵 정렬처럼 직접 데이터의 값을 비교한 뒤에 위치 변경하며 정렬하는 방식이 아님
- 일반적으로 리스트를 선언하고 그 안에 정렬에 대한 정보를 담는 특징이 있음
- 결과적으로 리스트에는 각 데이터가 몇 번 등장했는지 그 횟수가 기록됨
    - 예를 들어 5 인덱스의 값이 2이면 5는 2번 등장한 것
    - 이 리스트에 저장된 데이터 자체가 정렬된 형태 그 자체라고 할 수 있음
    - `정렬된 결과를 눈으로 확인`하려면, 리스트의 첫 번째 데이터부터 하나씩 `그 값만큼 인덱스를 출력`하면 됨

### 계수 정렬 소스코드

```python
# 모든 원소의 값이 0보다 크거나 같다고 가정
array = [7, 5, 9, 0, 3, 1, 6, 2, 4, 8, 0, 5, 2]

# 모든 범위를 포함하는 리스트 선언(모든 값은 0으로 초기화)
count = [0] * (max(array) + 1)

for i in range(len(array)):
	count[array[i]] += 1  # 각 데이터에 해당하는 인덱스의 값 증가

for i in range(len(count)):
	for j in range(count[i]):
		print(i, end='')  # 띄어쓰기를 구분으로 등장한 횟수만큼 인덱스 출력
```

⇒ 0 0 1 1 2 2 3 4 5 5 6 7 8 9 9

### 계수 정렬의 시간 복잡도

- 빅오 표기법으로 **O(N + K)**
    - 모든 데이터가 양의 정수인 상황에서 `데이터의 개수를 N, 데이터 중 최대 값의 크기를 K`라고 할 때
    - 앞에서부터 데이터를 하나씩 확인하며 리스트에서 적절한 인덱스의 값을 1씩 증가시키고, 추후에 리스트의 각 인덱스에 해당하는 값들을 확인할 때 데이터 중 최댓값의 크기만큼 반복을 수행해야하기 때문임
    - 데이터만 한정되어있다면 효과적이고 항상 빠르게 동작
    

### 계수 정렬의 공간 복잡도

- 빅오 표기법으로 O(N + K)
    - 동일한 값을 가지는 데이터가 여러 개 등장할 때 적합한 알고리즘
        - 성적의 경우 100점 맞은 학생일 여러 명일 수 있음
    - **`데이터 크기 한정, 데이터 크기 많이 중복 시 유리`**

### 1-5 파이썬의 정렬 라이브러리

- 파이썬 제공 함수 - `sorted()`
    - 퀵 정렬보다는 느리나 최악의 경우에도 시간 복잡도 O(NlogN)을 보장한다는 특징이 있는 `병합 정렬`을 기반으로 만들어짐
    - 리스트, 딕셔너리 자료형 등을 입력받아 정렬된 결과를 출력함

### sorted 소스코드

```python
array = [7, 5, 9, 0, 3, 1, 6, 2, 4, 8]

result = sorted(array)
print(result)
```

- 파이썬 내장 함수 - `sort()`
    - 리스트 변수가 하나 있을 때, 내부 원소를 바로 정렬할 수 있음
    - **별도의 정렬된 리스트가 반환되지 않고** `내부 원소가 바로 정렬`됨

### sort 소스코드

```python
array = [7, 5, 9, 0, 3, 1, 6, 2, 4, 8]

array.sort()
print(array)
```

- `key 매개변수`
    - key 값으로는 `하나의 함수`가 들어가야 하며, 이는 `정렬 기준이 됨`
    - 예를 들어 리스트의 데이터가 `튜플로 구성될 때, 각 데이터의 두 번째 원소를 기준으로 설정하는 경우` 아래처럼 코드를 작성할 수 있음

### 정렬 라이브러리에서 key를 활용한 소스코드

```python
array = [('바나나', 2), ('사과', 5), ('당근', 3)]

def setting(data):
	return data[1]

result = sorted(array, key=setting)
print(result)
```

⇒ [('바나나', 2),  ('당근', 3), ('사과', 5)]