<h2>22.09.28</h2>
<a href="https://velog.io/@leedahye2001/CSS%EC%97%90-%EB%8C%80%ED%95%B4-
%EB%AA%B0%EB%9E%90%EB%8D%98-%EB%82%B4%EC%9A%A9-%EC%A0%95%EB%A6%AC-5-93k7e38p">danshye.log 바로가기 :)</a>
<br>
<h3>🙋‍♀️ 놓친 부분 정리!</h3>
<br>


### 1. CSS3 Flexbox Layout (플렉스 박스 레이아웃)

Flexbox는 모던 웹을 위하여 제안된 기존 layout보다 더 세련된 방식의 니즈에 부합하기 위한 CSS3의 새로운 layout 방식이다.

요소의 사이즈가 불명확하거나 동적으로 변화할 때도 유연한 레이아웃을 실현할 수 있다. 복잡한 레이아웃이라도 적은 코드로 보다 간단하게 표현할 수 있다.

예를 들어, 간단한 flexbox 레이아웃을 만들어 보자면 ,,

<HTML>

```html
<!DOCTYPE html>
<head>
<link rel="stylesheet" href="ex.css">
</head>
<div class="container">
	<div class="item">1</div>
	<div class="item">2</div>
	<div class="item">3</div>
	<div class="item">4</div>
	<div class="item">5</div>
</div>
</html>
```

<CSS>

```css
.container{
	margin: 10px;
	padding: 15px;
	border-radius: 5px;
	background: #ccc;
}
.item{
    margin: 10px;
    padding: 20px;
    color:#000;
    text-align:center;
    border-radius: 5px;
    background: #eee
}
```

**👉 실행 결과**

![](https://velog.velcdn.com/images/leedahye2001/post/82c386bd-63f0-4bcc-b097-6ca55bd3c8ae/image.png)


div 요소는 block 요소이므로 `수직정렬`된다. 이를 `수평정렬` 하려면 `자식요소를 inline-block`으로 지정하거나 `float` 프로퍼티를 지정한다.

```css
.item {
	display: inline-blick;
	float: left;
}
```

이때 각 자식 요소를 부모 요소 내에서 정렬하기 위해서는 각 자식요소의 너비를 %로 지정하는 등의 처리가 필요하다. 자식 요소의 사이즈가 불명확하거나 동적으로 변화할 때는 더 처리가 복잡해진다.

아래는 Flexbox를 사용해 위의 css문을 부모 요소 내에서 `수평 정렬`한 것이다. 부모 요소에 아래와 같이 추가하면 된다.

```css
.container {
	display: flex;
	justify-content: space-around;
}
```

👉 **실행 결과**

![](https://velog.velcdn.com/images/leedahye2001/post/8b932ac7-5dc0-41db-a40d-7f4a14a7f5bb/image.png)


### 2. 사용법

Flexbox 레이아웃은 **flex item**이라 불리는 복수의 자식 요소와 이들을 내포하는 **flex-container** 부모 요소로 구성된다.

**쉽게 정리하자면**

`flex-container : 부모요소`

`flex item : 자식요소`

이렇게 기억하면 된다 ㅎㅎ

flexbox를 사용하기 위해 HTML 부모 요소의 display 속성에 flex를 지정한다.

```css
.container {
	display: flex;
}
```

부모 요소가 inline 요소인 경우, 아래와 같이 inline-flex을 지정한다.

```css
.container {
	display: inline-flex;	
}
```

flex 또는 inline-flex는 부모 요소에 반드시 지정해야하는 유일한 속성이며 `자식 요소는 자동적으로 flex item이 된다.`

### 3. Flexbox container 속성

**3.1 flex-direction**

flex-direction 속성은 flex 컨테이너의 주축 방향을 설정한다.

- flex-direction: row;

좌에서 우로 수평 배치된다. `flex-direction` 속성의 `기본 값`이다.

```css
.container{
	padding: 15px;
	border-radius: 5px;
	background: #ccc;

  display: flex;
  flex-direction: row;
}
```

👉 **실행 결과**
![](https://velog.velcdn.com/images/leedahye2001/post/c6c85171-a525-4da2-8ea1-56590eddfde7/image.png)

<hr>

* flex-direction: row-reverse;

우에서 좌로 수평 배치된다.

👉 **실행 결과**

![](https://velog.velcdn.com/images/leedahye2001/post/b7358d75-ec18-49e7-b25b-c4e0190352a3/image.png)

<hr>

* flex-direction: column;

위에서 아래로 수직 배치된다.

👉 **실행 결과**
![](https://velog.velcdn.com/images/leedahye2001/post/84073bec-93f4-4b6e-a543-2cd25e1e7825/image.png)

<hr>

- flex-direction: column-reverse;

아래에서 위로 수직 배치된다.

👉 **실행 결과**

![](https://velog.velcdn.com/images/leedahye2001/post/b1a8dac6-3f09-43b8-baa4-eed6fd8bce08/image.png)

**3.2 flex-wrap**
