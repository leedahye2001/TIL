<h2>22.09.26</h2>
<a href="[%EC%9A%A9-%EC%A0%95%EB%A6%AC-3](https://velog.io/@leedahye2001/CSS%EC%97%90-%EB%8C%80%ED%95%B4-%EB%AA%B0%EB%9E%90%EB%8D%98-%EB%82%B4%EC%9A%A9-%EC%A0%95%EB%A6%AC-4)">
  danshye.log 바로가기 :)</a>
<br>
<h3>🙋‍♀️ 놓친 부분 정리!</h3>
<br>


### 3. Section & Aside & Footer

현재 article은 layout에 상관없이 1행에 1개씩 배치되었다.

article을 2열로 배치하기 위해서 width 값을 지정하여야 한다. %로 width 값을 지정하여 viewport에 상대적인 너비를 갖도록 한다. 이때 margin도 %로 지정한다. 그리고 `float: left` 를 지정하여 2열로 정렬되도록 한다.

```css
article {
	width: 48.5%;
	margin: 1%;
	padding: 25px;
	background-color: white;
	float: left;
}
```

짝수번째 배치되는 article의 좌측 마진과 3번째부터 등장하는 article의 위측 마진을 0로 하여 가운데 마진이 2배가 되는 것을 방지한다.

```css
article:nth-of-type(2n) {
	margin-left: 0;
}
article:nth-of-type(n+3) {
	margin-top: 0;
}
```

tablet layout을 작성한다. 800px 이하로 화면이 작아지면 2열 배치되어 있던 article을 1열로 배치한다.

```css
@media screen and (max-width: 800px){

	...

	article {
		width: inherit;
		display: block;
		margin: 10px;
		float: none;
	}
	article:nth-of-type(2n) {
		margin: 10px;
	}
	article:nth-of-type(n+2) {
		margin-top: 0;
	}
}
```

mobile layout을 작성한다. 480px 이하로 화면이 작아지면 고정되어있던 aside를 article 위로 올려 배치한다.

```css
@media screen and (max-width: 480px) {
	
	...

	aside {
		top: 60px;
		position: static;
    	width: 100%;
    	padding: 5px 0;
	}
	aside > ul {
    	width: 100%;
  	}
  	aside > h1 {
    	padding: 5px 0 10px 20px;
    	color: #fff;
  	}
  	section {
    	float: none;
    	margin-left: 0;
  	}

	...

}
```

<hr><br>
끝
