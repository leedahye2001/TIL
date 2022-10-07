## HashTable

: Key와 Value의 쌍으로 데이터를 저장하는 자료구조

언어에 따라 **HashMap**이라고도 불리며, 파이썬의 `Dictionary`도 HashTable로 구현되어 있음.

⭐️ HashTable(HashMap, Dictionary)의 특징

- 순차적으로 데이터를 저장하지 않음
- Key를 통해서 Value값을 얻음
- Value 값은 중복가능하나, Key는 중복될 수 없음
- 수정 가능함 (mutable)

 

<aside>
💡 파이썬의 List나 JavaScript의 Array와 달리
저장된 데이터를 순차적으로 찾는 게 아니라,
`Key를 통해 Value 값을 찾기 때문에 빠름!`

</aside>

## HashTable 내부 구조

**1. Hash Function (해시함수)**

: 임의의 길이를 갖는 임의의 데이터에 대해 고정된 길이의 데이터로 매핑하는 함수

임의의 길이를 갖는 데이터를 해시함수에 적용하여 나온 고정된 길이의 값을 `해시값`이라고 함.

![images_taeha7b_post_571e3d30-cd7d-4dd4-8f67-a7bf313230b3_hash (1).png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/df3c4556-1fde-47df-bb97-b0dc21540ad5/images_taeha7b_post_571e3d30-cd7d-4dd4-8f67-a7bf313230b3_hash_(1).png)

**Hashing(해싱)**

: 해시 함수를 이용해 해시테이블을 탐색하는 것

해시테이블에서 key로 ‘대한민국’, ’김태하’, ‘1234’, ’56789’를 갖고, 각각 '만세', '개발자', '아라비아', '숫자'를 `value 값` 으로 가짐

해시함수를 통해서 **해시 값**으로 **영문자와 소문자가 섞인 해시 값**을 얻을 수도 있고, 이 값을 **정수로 바꾼 해시 값**도 얻을 수 있음.

아래의 예는 해시 함수를 통해 해시 값을 정수로 얻은 것

이렇게 얻은 해시 값을 **buckets(버킷. 데이터가 저장되는 공간)**의 크기로 나누고, 나머지는 버킷의 **인덱스**로 가짐.

따라서, 아래의 예에서는

- '대한민국'이라는 key - 버킷의 0번째 인덱스에 value를 저장
- '김태하'라는 key - 버킷의 2번 인덱스에 value를 저장

해시 값을 버킷의 크기로 나누고 나온 나머지를 인덱스로 갖다보니 `나머지가 같은 값`이 나올 수 있음.

이때, **충돌(Collision)**이 발생하게 됨. 충돌의 해결 방법에는 여러가지가 있는데 이 중 Chaining이라는 방법이 있음.
