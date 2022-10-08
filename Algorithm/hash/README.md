## HashTable

: Key와 Value의 쌍으로 데이터를 저장하는 자료구조

언어에 따라 **HashMap**이라고도 불리며, 파이썬의 `Dictionary`도 HashTable로 구현되어 있음.

⭐️ HashTable(HashMap, Dictionary)의 특징

- 순차적으로 데이터를 저장하지 않음
- Key를 통해서 Value값을 얻음
- Value 값은 중복가능하나, Key는 중복될 수 없음
- 수정 가능함 (mutable)

 

💡 파이썬의 List나 JavaScript의 Array와 달리
저장된 데이터를 순차적으로 찾는 게 아니라,
`Key를 통해 Value 값을 찾기 때문에 빠름!`

<br>

## HashTable 내부 구조

<b>1. Hash Function (해시함수)</b>

: 임의의 길이를 갖는 임의의 데이터에 대해 고정된 길이의 데이터로 매핑하는 함수

임의의 길이를 갖는 데이터를 해시함수에 적용하여 나온 고정된 길이의 값을 `해시 값`이라고 함.

![images_taeha7b_post_571e3d30-cd7d-4dd4-8f67-a7bf313230b3_hash (1)](https://user-images.githubusercontent.com/94473725/194716161-01a11960-c15d-40b0-98b9-d827fc51b1b9.png)



**Hashing(해싱)**

: 해시 함수를 이용해 해시테이블을 탐색하는 것

해시테이블에서 key로 ‘대한민국’, ’김태하’, ‘1234’, ’56789’를 갖고, 각각 '만세', '개발자', '아라비아', '숫자'를 `value 값` 으로 가짐

해시함수를 통해서 <b>해시 값</b>으로 <b>영문자와 소문자가 섞인 해시 값</b>을 얻을 수도 있고, 이 값을 <b>정수로 바꾼 해시 값</b>도 얻을 수 있음.

아래의 예는 해시 함수를 통해 해시 값을 정수로 얻은 것

이렇게 얻은 해시 값을 <b>buckets(버킷. 데이터가 저장되는 공간)</b>의 크기로 나누고, 나머지는 버킷의 **인덱스**로 가짐.

따라서, 아래의 예에서는

- '대한민국'이라는 key - 버킷의 0번째 인덱스에 value를 저장
- '김태하'라는 key - 버킷의 2번 인덱스에 value를 저장

해시 값을 버킷의 크기로 나누고 나온 나머지를 인덱스로 갖다보니 `나머지가 같은 값`이 나올 수 있음.

이때, <b>충돌(Collision)</b>이 발생하게 됨. 충돌의 해결 방법에는 여러가지가 있는데 이 중 <b>Chaining</b>이라는 방법이 있음.

**2) 충돌 해결 방법 : Chaining**

![images_taeha7b_post_32dfe1bd-f735-4c71-9276-e3550e89b370_해싱 (1)](https://user-images.githubusercontent.com/94473725/194710376-6dfd64c1-40a7-4a8f-b4ec-0acc432bbf60.png)

key가 ‘1234’와 ‘56789’ 일 때, 나머지가 같아서 같은 버킷 인덱스를 갖게되면, 우선 ‘1234’일 때 버킷의 99번 인덱스로 가서 value (아라비아)를 저장.

그리고 ‘56789’ 일 때도 버킷의 99번재 인덱스로 가긴 하는데, 이미 저장된 값이 `연결 리스트` 형태로 ‘56789’ value 값을 저장.

아래 코드는 '대한민국', '김태하', '1234', '56789'에 해시함수를 적용해서 해시값과 해시값의 크기를 나타낸 파이썬 코드이다.

해시 값은 달라도 같은 크기인 것을 알 수 있다.

```python
import hashlib

def hash1(input_str):
    
    obj = hashlib.sha1(input_str.encode())
    value = obj.hexdigest()
    return value

hash_value_kor = hash1('대한민국')
print(hash_value_kor)
print(len(hash_value_kor))
print()

hash_value_name = hash1('김태하')
print(hash_value_name)
print(len(hash_value_name))
print()

hash_value_1234 = hash1('1234')
print(hash_value_1234)
print(len(hash_value_1234))
print()

hash_value_56789 = hash1('56789')
print(hash_value_56789)
print(len(hash_value_56789))
print()

#실행결과
4f12e8995f9606c6d2dc54c3cd8d1cfe35b8b83a
40

86c871b56d910a3b96edd3906256c3058deab192
40

7110eda4d09e062aa5e4a390b0a572ac0d2c0220
40

f2231d2871e690a2995704f7a297bd7bc64be720
40
```

## ✔️ 해쉬 테이블 용어

- **해쉬(Hash)** : 임의 값을 고정 길이로 변환하는 것
- **해쉬 테이블(Hash Table)** : 키값의 연산에 의해 직접 접근이 가능한 데이터 구조
- **해싱 함수(Hashing Function)** : Key에 대해 산술 연산을 이용해 데이터 위치를 찾을 수 있는 함수
- **해쉬 값(Hash Value) 또는 해쉬 주소(Hash Address)** : Key를 해싱 함수로 연산해서 해쉬 값을 알아내고, 이를 기반으로 해쉬 테이블에서 해당 Key에 대한 데이터 위치를 일관성 있게 찾을 수 있음
- **슬롯(Slot)** : 한 개의 데이터를 저장할 수 있는 공간
- 저장할 데이터에 대해 Key를 추출할 수 있는 별도 함수도 존재할 수 있음

## **간단한 해쉬 테이블 만들기**

⭐️ **hash table 만들기**


💡 <b>list comprehension</b>
<b>[출력표현식 for 요소 in 입력 sequence [if 조건문]]</b>

- 입력 sequence는 Iteration이 가능한 데이터 Sequence 혹은 컬렉션
- [if 조건문]에서 <b>[]</b>는 리스트 괄호가 아니라 <b>옵션</b>이라는 뜻, 즉 조건이 있을 때만 넣으면 된다는 뜻



```python
# ex) hash table 만들기
hash_table=list([i for i in range(10)])
print(hash_table)
```

**⭐️ 간단한 해쉬 함수 만들기**

- 다양한 해쉬 함수 고안 기법 중, 가장 간단한 방법은 **Division 법 (나누기를 통해 나머지 값을 사용하는 법)**

```python
def hash_function(key):
	return key % 5
```

⭐️ **해쉬 테이블에 저장하기**

- 데이터에 따라 필요시, key 생성 방법 정의가 필요함

```python
data1 = 'dahye'
data2 = 'lee'
data3 = 'computer'
data3 = 'Lotus'

## ord() : 문자의 ASCII(아스키)코드 리턴
print(ord(data1[0]), ord(data2[0]), ord(data3[0]),ord(data4[0]))
print(ord(data1[0]), hash_function(ord(data1[0])))
print(ord(data1[0], ord(data4[0])
```

⭐️ **해쉬 테이블 값 저장 예시**

- <b>data</b> : value와 같이 data와 value를 넣으면, 해당 data에 대한 key를 찾아서 `해당 key에 대응하는 해쉬주소에 value를 저장`하는 예

```python
def storage_data(data, value):
	key = ord(data[0])
	# key의 주소 표현
	hash_address = hash_function(key)
	# 그 주소에 입력한 value가 들어감
  hash_table[hash_address] = value

storage_data('dahye', '01033336666')
storage_data('dh', '01099994444')
```

## 해쉬 테이블 시간 복잡도

- 평균의 경우(Collision이 없는 경우)는 **`O(1)`**
- 최악의 경우(Collision이 있는 경우)는 **`O(n)`**
