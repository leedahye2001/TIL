<h2>22.10.03</h2>
<a href="https://velog.io/@leedahye2001/%ED%98%BC%EC%9E%90%ED%95%98%EB%8A%94-JavaScript-3">danshye.log 바로가기 :)</a>
<br>
<h3>🙋‍♀️ 혼자하는 JavaScript!</h3>
<br>


### 03. 연산자

<br>

연산자 : 프로그래밍 언어에서 특정 연산을 하도록 하는 문자

```jsx
let value = 1; // 변수 선언
value = 2; // 대입 연산자
```

여기서 `두번째 줄`에서 사용된 `=` 문자가 바로 연산자이다. 

그 중에서 `=` 는, 대입 연산자에 해당된다. 첫번째 줄은 새로운 변수를 선언하는 것으로서, 대입 연산자에 해당하지 않음.

### 산술 연산자

산술 연산자 : 사칙연산과 같은 작업을 하는 연산자를 의미합니다.

- `+`: 덧셈
- `-`: 뺄셈
- `*`: 곱셈
- `/`: 나눗셈

위 4가지가 가장 기본적인 산술 연산자임.

```jsx
let a = 1 + 2;
console.log(a);
```

👉 결과 : **a = 3**

```jsx
let a = 1 + 2 - (3 * 4) / 4;
console.log(a);
```

👉 결과 : **a = 0**

```jsx
let a = 1;
a++;
++a;
console.log(a);
```

👉 결과 : **a = 3**

`++` 는 특정 변수에 1을 바로 더해준다.

그런데, ++ 가 변수 이름 앞에 오는 것과 뒤에 오는것에 차이가 있음.

```jsx
let a = 1;
console.log(a++);
console.log(++a);

```

👉 결과 : **a = 1**

👉 결과 : **a = 3**

`console.log(a++);` 를 할 때에는 1을 더하기 직전 값을 보여주고
`console.log(++a);` 를 할 때에는 1을 더한 다음의 값을 보여준다는 차이가 있음.

⇒ 증감연산자,,

```jsx
let a = 1;
a--;
console.log(a);
```

👉 결과 : **a = 0**

### 대입 연산자

대입 연산자 : 특정 값에 연산을 한 값을 바로 설정 할 때 사용 할 수 있는 연산자

예를 들어서, 다음과 같은 코드를 대입 연산자를 사용하면 아래와 같이 작성이 가능하다.

```jsx
let a = 1;
a = a + 3;
```

위의 내용 작성..!

```jsx
// 위의 코드를 대입 연산자를 사용하여 작성
let a = 1;
a += 3;
```

다양한 연산도 가능함

```jsx
let a = 1;
a += 3;
a -= 3;
a *= 3;
a /= 3;
console.log(a);
```

👉 결과 : **a = 1**

### 논리 연산자

논리 연산자 :  불리언 타입 (true 혹은 false)를 위한 연산자

총 3가지가 있습니다.

- `!`: NOT
- `&&`: AND
- `||`: OR

### NOT

NOT 연산자 : true 는 false 로, false 는 true 로 바꿔줌

```jsx
const a = !true;
console.log(a);
```

👉 결과 : **a = false**

```jsx
const b = !false;
console.log(b);
```

👉 결과 : **b = true**

### AND

AND 연산자 : 양쪽의 값이 `둘 다 true 일때만` 결과물이 `true`

```jsx
const a = true && true;
console.log(a);
```

👉 결과 : **a = true**

```jsx
let b = false && false;
b = false && true;
b = true && false;
```

👉 결과 : **b = false**

### OR

OR 연산자 : 양쪽의 값 중 `하나라도 true` 라면 결과물이 `true` 입니다. 또, 두 값이 `둘 다 false` 일 때에만 `false` 입니다.

```jsx
let a = true || false;
a = false || true;
a = true || true;
```

👉 결과 : **a = true**

```jsx
let b = false || false;
```

👉 결과 : **b = false**

### 연산 순서

사칙연산을 할 때 곱셈 나눗셈이 먼저고 그 다음이 덧셈 뺄셈인 것 처럼 논리 연산자에도 순서가 있음.

순서는 `NOT -> AND -> OR` 이다

아래를 예시로 들어보자.

```jsx
const value = !((true && false) || (true && false) || !false);
```

괄호로 감싸져있을 때에는 가장 마지막에 처리를 하니까 맨 앞 NOT 은 나중에 처리해야한다.

1. 괄호 안 NOT 처리

```jsx
!((true && false) || (true && false) || true);
```

2. AND 를 처리

```jsx
!(false || false || true);
```

3. OR 연산자를 좌측에서 우측 방향으로 처리

```jsx
!true;
```

👉 결과 : **false**

### 비교 연산자

비교 연산자 : 두 값을 비교 할 때 사용

### 두 값이 일치하는지 확인

```jsx
const a = 1;
const b = 1;
const equals = a === b;
console.log(equals);
```

👉 결과 : **true**

`===` 는 두 값이 일치하는지 확인해줌.

일치한다면 true / 일치하지 않는다면 false

두 값이 일치 하는지 확인 할 때, `=` 문자 2개로도 비교를 할 수는 있음.

```jsx
const a = 1;
const b = 1;
const equals = a == b;
console.log(equals);
```

위 코드는 똑같은 결과 true 를 반환하긴 함.

<aside>
💡  **`=` 문자가 3개 있을 때와 2개 있을 때의 차이점?**
 2개 있을때에는 `타입 검사까지는 하지 않는다.`

</aside>

`==` 를 사용하면 숫자 1과 문자 '1' 이 동일한 값으로 간주됨.

```jsx
const a = 1;
const b = '1';
const equals = a == b;
console.log(equals);
```

👉 결과 : **true**

0 과 false 도 같은 값으로 간주됨.

```jsx
const a = 0;
const b = false;
const equals = a == b;
console.log(equals);
```

👉 결과 : **true**

null과 undefined도 같은 값으로 간주됨.

```jsx
const a = null;
const b = undefined;
const equals = a == b;
console.log(equals);
```

👉 결과 : **true**

### 두 값이 일치하지 않는지 확인

두 값이 일치하지 않는지 확인 할 때에는 `!==` 를 사용하면 됩니다.

```jsx
const value = 'a' !== 'b';
```

👉 결과 : **true**

`!=` 를 사용하게 되면 타입 검사를 하지 않습니다.

```jsx
console.log(1 != '1');
console.log(1 !== '1');
```

👉 결과 : **false**

👉 결과 : **true**

### 크고 작음

두 값 중에서 무엇이 더 크고 작은지 비교하기 위해서 사용.

```jsx
const a = 7;
const b = 10;
const c = 10;

console.log(a < b); // true
console.log(b > a); // true
console.log(b >= c); // true
console.log(a <= c); // true
console.log(b < c); // false;
```

### 문자열 붙이기

두 문자열을 붙일 때에는 `+` 로 사용함.

```jsx
const a = '안녕';
const b = '하세요';
console.log(a + b); // 안녕하세요
```

---

끝!
