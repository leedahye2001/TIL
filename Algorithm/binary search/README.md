## 2. 이진 탐색

### 2-1 순차 탐색

순차 탐색 : 리스트 안에 있는 특정한 데이터를 찾기 위해 앞에서부터 데이터를 하나씩 차례대로 확인하는 방법

- 보통 `정렬되지 않은 리스트에서` 데이터를 찾아야 할 때 사용
- 데이터 정렬 여부와 상관없이 가장 앞에 있는 원소부터 하나씩 확인해야한다는 특징이 있음

**순차 탐색이 사용되는 경우**

- 리스트에 `특정 값의 원소가 있는지 체크`할 때, 순차 탐색으로 원소 확인
- 리스트 자료형에서 특정한 값을 가지는 `원소의 개수를 세는 count() 메서드` 이용할 때, 내부에서 순차 탐색이 수행

### 순차 탐색 소스코드

```python
# 순차 탐색 소스코드 구현
def sequential_search(n, target, array):
	# 각 원소를 하나씩 확인하며
	for i in range(n):
		# 현재의 원소가 찾고자 하는 원소와 동일한 경우
		if array[i] == target:
			return i + 1  # 현재의 위치 반환(인덱스는 0부터니까 1 더하기)

print("생성할 원소 개수를 입력한 후, 한 칸 띄우고 찾을 문자열을 입력하세요.")
input_data = input.split()
n = int(int_data[0])  # 원소의 개수
target = input_data[1]  # 찾고자 하는 문자열

print("앞서 적은 원소 개수만큼 문자열을 입력하세요. 구분은 띄어쓰기 한 칸으로 합니다.")
array = input().split()

# 순차 탐색 수행 결과 출력
print(sequential_search(n, target, array))
```

**순차 탐색의 최악의 경우 시간 복잡도**

- 빅오 표기법으로 O(N)
    - 데이터의 개수가 N개일 때 최대 N번의 비교 연산이 필요하기 때문이다
    

### 2-2 이진 탐색 : 반으로 쪼개면서 탐색하기

이진 탐색 : `찾으려는 데이터와 중간점 위치에 있는 데이터를 반복적으로 비교`해서 원하는 데이터를 찾는 알고리즘

- 탐색 범위를 절반씩 좁혀가며 데이터를 탐색하는 특징이 있음
- 배열 내부의 데이터가 정렬되어 있어야만 사용할 수 있는 알고리즘
- 위치를 나타내는 변수 3개 ⇒ 탐색하고자 하는 범위의 **시작점, 끝점, 중간점**

### 이진 탐색의 시간 복잡도

- 빅오 표기법으로 O(logN)
    - 한 번 확인할 때마다 확인하는 원소의 개수가 절반씩 줄어든다 (**퀵 정렬과 공통점**)
    

### 재귀 함수로 구현한 이진 탐색 소스코드

```python
# 이진 탐색 소스코드 구현(재귀 함수)
def binary_search(array, target, start, end):
	if start > end:
		return None
	mid = (start + end) // 2  # 중간점을 의미. 2로 나눈 몫만 구하기 위해 몫 연산자(//)를 사용

	# 찾은 경우 중간점 인덱스 반환
	if array[mid] == target:
		return mid
	# 중간점의 값보다 찾고자 하는 값이 작은 경우 왼쪽 확인
	elif array[mid] > target:
		return binary_search(array, target, start, mid - 1)
	# 중간점의 값보다 찾고자 하는 값이 큰 경우 오른쪽 확인
	else:
		return binary_search(array, target, mid + 1, end)

# n(원소의 개수)과 target(찾고자 하는 문자열)을 입력받기
n, target = list(map(int, input().split()))
# 전체 원소 입력받기
array = list(map(int, input().split()))

# 이진 탐색 수행 결과 출력
result = binary_search(array,target, 0, n - 1)
if result == None:
	print("원소가 존재하지 않습니다")
else:
	print(result + 1)
```

### 반복문으로 구현한 이진 탐색 소스코드

```python
# 이진 탐색 소스코드 구현(반복문)
def binary_search(array, target, start, end):
	while start <= end:
		mid = (start + end) // 2  # 중간점을 의미. 2로 나눈 몫만 구하기 위해 몫 연산자(//)를 사용

	# 찾은 경우 중간점 인덱스 반환
	if array[mid] == target:
		return mid
	# 중간점의 값보다 찾고자 하는 값이 작은 경우 왼쪽 확인
	elif array[mid] > target:
		end = mid - 1
	# 중간점의 값보다 찾고자 하는 값이 큰 경우 오른쪽 확인
	else:
		start = mid + 1
	return None

# n(원소의 개수)과 target(찾고자 하는 문자열)을 입력받기
n, target = list(map(int, input().split()))
# 전체 원소 입력받기
array = list(map(int, input().split()))

# 이진 탐색 수행 결과 출력
result = binary_search(array,target, 0, n - 1)
if result == None:
	print("원소가 존재하지 않습니다")
else:
	print(result + 1)
```
