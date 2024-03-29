<h2>22.10.06</h2>
<a href="https://velog.io/@leedahye2001/%ED%98%BC%EC%9E%90%ED%95%98%EB%8A%94-JavaScript-5">danshye.log 바로가기 :)</a>
<br>
<h3>🙋‍♀️ 혼자하는 JavaScript!</h3>
<br>

### 04. 조건문
`조건문`을 사용하면 특정 조건이 만족됐을 때 특정 코드를 실행할 수 있다.

### **if 문**

: 가장 기본적인 `조건문`

: "~~하다면 ~~를 해라" 를 의미

```jsx
const a = 1;
if (a + 1 === 2) {
  console.log('a + 1 이 2 입니다.');
}
```

👉 **결과** : "a + 1 이 2 입니다."

만약에 여기서 a 를 0 으로 바꾼다면?

```jsx
const a = 0;
if (a + 1 === 2) {
  console.log('a + 1 이 2 입니다.');
}
```

👉 **결과** : 아무것도 출력되지 않음.

if문을 사용하면 **특정 조건이 만족 될 때에만** 특정 코드를 실행 시킬 수 있음

```jsx
if (조건) {
  코드;
}
```

조건이 만족됐을 때 실행시킬 코드가 `{ }` 로 감싸져있는데요, 이를 `코드 블록`이라고 한다.

만약에 조건이 true 가 된다면 우리가 지정한 코드가 실행되는 것이고, false 가 된다면 코드가 실행되지 않음.

⭐️ `let` 과 `const` 를 공부할 때, 다른 블록 범위에서는 똑같은 이름으로 선언 할 수도 있다고 했음.

```jsx
const a = 1;
if (true) {
  const a = 2;
  console.log('if문 안의 a 값은 ' + a);
}
console.log('if문 밖의 a 값은 ' + a);
```

위 코드에서, if문에 조건을 true 로 설정했기 때문에 코드 블록 내부의 코드가  ”무조건” 실행이 됨.

👉 **결과 :**

```jsx
// 결과
"if문의 안의 a 값은 2"
"if문 밖의 a 값은 1"
```

### **if-else 문**

: "if ~~하다면 ~~하고, else 그렇지 않다면 ~~해라." 를 의미

```jsx
const a = 10;
if (a > 15) {
  console.log('a 가 15 큽니다.');
} else {
  console.log('a 가 15보다 크지 않습니다.');
}
```

👉 **결과** :

```jsx
// 결과
"a 가 10보다 크지 않습니다."
```

만약에 특정 조건이 만족할 때와 만족하지 않을 때 서로 다른 코드를 실행해야 된다면 `if-else` 구문을 사용 할 수 있다.

### **if-else if 문**

: 여러 조건에 따라 다른 작업을 해야 할 때 사용한다.

```jsx
const a = 10;
if (a === 5) {
  console.log('5입니다!');
} else if (a === 10) {
  console.log('10입니다!');
} else {
  console.log('5도 아니고 10도 아닙니다.');
}
```

👉 **결과** 

```jsx
"10입니다!"
```

### **switch/case 문**

: 특정 값이 무엇이냐에 따라 다른 작업을 하고 싶을 때 사용

```jsx
const device = 'iphone';

switch (device) {
  case 'iphone':
    console.log('아이폰!');
    break;
  case 'ipad':
    console.log('아이패드!');
    break;
  case 'galaxy note':
    console.log('갤럭시 노트!');
    break;
  default:
    console.log('모르겠네요..');
}
```

switch/case 문은 특정 값이 무엇이냐에 따라 다른 작업을 수행 할 수 있게 해줌.

switch/case 문에서는 각 case 에서 실행할 코드를 작성하고 맨 마지막에 반드시 `break;` 를 해주어야 한다.

break 를 하지 않으면 그 다음 case 의 코드까지 실행해버리기 때문!

그리고, 맨 아래의 `default:` 는 device 값이 case 로 따로 값을 설정하지 않을 경우를 의미함.
