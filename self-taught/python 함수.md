### **abs(x) :** 절대값을 구하는 함수

**예제**

- **정수**

```jsx
>>> abs(-1)
1
```

- **실수**

```jsx
>>> abs(-1.74)
1.74
```

- **복소수**

```jsx
>>> abs(1+1j)
1.4142135623730951
```

### combination **: 순서를 고려하지 않고 원소 나열**

Python의 itertools를 이용하면 순열과 조합을 for문 없이 구현할 수 있다.

**예제**

```python
import itertools

arr=['A', 'B', 'C']
nCr = itertools.combinations(arr, 2)
print(list(nCr))

=> 결과 : [('A', 'B'), ('A', 'C'), ('B', 'C')]
```
