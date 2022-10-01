<h2>22.09.22</h2>
<a href="https://velog.io/@leedahye2001/CSS%EC%97%90-%EB%8C%80%ED%95%B4-%EB%AA%B0%EB%9E%90%EB%8D%98-%EB%82%B4%EC%9A%A9-%EC%A0%95%EB%A6%AC-3">danshye.log 바로가기 :)</a>
<br>
<h3>🙋‍♀️ 놓친 부분 정리!</h3>
<br>


### 2. Responsive Navigation Bar
아래는 기기에 따라 `breakpoint`를 정의한 것이다.
`Non Mobile First Method`로 정의하였기 때문에 Media Query로 정의하지 않은 스타일은 데스크탑 그룹을 위한 코드이다.

```html
<head>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    /* 태블릿 영역 : ~ 800px */
    @media screen and (max-width: 800px) {

    }
    /* 스마트폰 영역 : ~ 480px */
    @media screen and (max-width: 480px) {

    }
  </style>
</head>

```



CSS 적용 우선 순위에 따라 나중에 선언된 스타일이 먼저 적용된다. **따라서 Media Query는 기술 순서에 의미가 있다.**
만일 스마트폰용 스타일이 태블릿용보다 먼저 기술된다면? 최종적으로 태블릿용 스타일이 적용된다. 따라서 Non Mobile First 방식의 경우, max-width의 값이 큰 것부터 작성하여야 한다.
일반적으로 `Mobile-first` 방식은 `해상도가 작은 순서`, `Non-Mobile-first` 방식은 `해상도가 큰 순서`대로 기술한다.


### 2.1 Responsive Navigation Bar - Tablet

데스크탑 layout에서 화면이 작아질 때 header navigaion bar가 header 영역 아래로 내려오는 현상이 발생간다. 이를 보완하기 위해 다음과 같이 태블릿에서의 layout을 정의한다.

viewport width가 800px 이하가 되면 header 영역을 2단으로 구분하기 위해 header 영역의 높이를 현재(60px)의 2배로 넓힌다 (120px로). 그리고 로고 이미지와 navigation bar를 centering 한다.
이때 aside, section 영역도 header의 높이 만큼 내려가야 한다!

```css
	@media screen and (max-width: 800px) {
    	header {
        	height: 120px;
            text-align: center;
        }
        #wrap {
        	margin-top: 120px;
        }
        aside {
        	top: 120px;
        }
    }
```

logo image와 navigation bar가 가로로 나란히 정렬되어있는데, 이것을 상단과 하단으로 분리 배치 하기 위해 navigation bar의 `float: right;` 프로퍼티를 해제한다. 그러면 navigation bar는 `block` 프로퍼티를 가지게 되어 logo image의 아래 영역으로 내려가게 된다.

```css
	@media screen and (max-width: 800px) {
    	...
        nav {
        	float: none;
        }
        ...
    }

```


### 2.2 Responsive Navigation Bar - Smartphone
스마트폰의 viewport width는 가로로 나란히 정렬되어 있는 navigation bar를 모두 담기에는 너무 좁다. 그래서 우측 navigition icon(메뉴)을 클릭하면 navigation bar가 수직 정렬되어 화면에 나타나도록 한다. 한번 더 클릭하면 화면에서 사라지도록 하며, 이때 navigation icon에 `animation` 효과를 부여한다.

nav 요소 내에 클릭할 수 있는 navigation icon을 만들기 위한 html tag를 추가한다. `label tag의 for` 프로퍼티 값과 `input tag의 for `프로퍼티 값과 `input tag의 id` 프로퍼티 값이 `일치`해야 한다.

```html
	<nav>
    	<input class="nav-toggle" id="nav-toggle" type="checkbox">
        <label class="navicon" for="nav-toggle"><span class="navicon-bar"></span></label>
        <ul class="nav-items">
        	<li><a href="#home">Home</li>
            ...
```

<br>

```html
	<label for="remember-pw">Remember password?</label>
	<input type="checkbox" name="remember-pw" id="remember-pw">
```

input checkbox 요소의 id값과 label요소의 for값을 일치시켜 연동하면 label 요소를 클릭하여도 input checkbox 요소가 클릭된다.

이 다음은 navigation icon을 만드는 과정이다!

navigation icon은 input checkbox 요소와 연동되어야 하므로 label요소를 사용하였다. 즉 navigation icon을 클릭하면 checkbox input tag도 `checked` 상태가 된다.

다음은 navigation icon를 정의하는 css이다.

```css
	.navicon {
    	cursor: pointer;
        height: 60px;
        padding: 28px 15px;
        position: absolute;
        top: 0;
        right: 0;
    }
```

위 코드를 설명하자면,
navigation icon은 header 우측의 절대 위치에 배치되어야 하므로 `position: absolute;` 를 지정한다.

absolute 프로퍼티는 부모 요소 또는 가장 가까이 있는 조상 요소(static 제외)를 기준으로 좌표 프로퍼티(top, bottom, left, right)만큼 이동한다. 즉 relative, absolute, fixed 프로퍼티가 선언되어 있는 부모 또는 조상 요소를 기준으로 위치가 결정된다. 만일 부모 또는 조상 요소가 static인 경우, document body를 기준으로 하여 좌표 프로퍼티대로 위치하게 된다.

이 경우, navigation icon은 body를 기준으로 위치하면 되므로 부모 요소에 별도의 처리가 필요없다.

다음은 label tag 내의 span tag의 style을 정의한다. span tag는 navigation icon의 내부 막대 3개(클릭 시에는 X 표시)를 표현하기 위해 정의하였다.

```css
.navicon-bar {
	display: block;
	width: 20px;
    height: 3px;
    background-color: #000;
}
```

위와 같이 하면, navigation icon의 내부 막대 1개가 생성된다.

`가상 요소 선택자`를 사용하여 navigation icon의 내부 앞뒤 공간에 내부 막대를 추가한다.

* 여기서 가상 요소 선택자가 궁금하면 ?
👉 



```css
.navicon-bar::before,
.navicon-bar::after {
	position: absolute;
	display: block;
	width: 100%;
    height: 100%;
    background-color: #000;
    content: "";
}
.navicon-bar::before {
	top: -7px;
}
.navicon-bar::after {
	top: 7px;
}
```

절대 위치를 지정하기 위해 `postion: absolute;` 를 사용하였으므로 가상 요소의 부모 요소인 **span** 요소에 `position: relative;`를 추가한다.

```css
.navicon-bar {
	position: relative;
	display: block;
	width: 20px;
    height: 3px;
    background-color: #000;
}
```

아직 navigation icon을 클릭해도 아무 반응이 없다. navigation icon을 클릭하면 클릭됨을 사용자가 확인하도록 navigation icon의 `style을 변화`시킨다.

```css
.nav-toggle:checked ~ .navicon > .navicon-bar {
    background: transparent;
}
.nav-toggle:checked ~ .navicon > .navicon-bar::before {
    transform: rotate(45deg);
    top: 0;
}
.nav-toggle:checked ~ .navicon > .navicon-bar::after {
    transform: rotate(-45deg);
    top: 0;
}
```

먼저 중간에 위치한 막대를 없애고, 상하 막대를 45도 회전시킨다. 이때 위치가 틀어지므로 `top: 0;`로 보정한다.

navigation icon에 transition 효과를 넣어서 좀 더 부드럽게 움직이도록 한다.

```css
.navicon-bar {
	position: relative;
	display: block;
	width: 20px;
    height: 3px;
    background-color: #000;
	transition: background-color .2s ease-out;
}
.navicon-bar::before,
.navicon-bar::after {
	position: absolute;
	display: block;
	width: 100%;
    height: 100%;
    background-color: #000;
    content:"";
    transition: all .2s ease-out;
}
```

transition 프로퍼티는 property, duration, delay 순으로 정의한다.

navigation icon을 클릭하면 의도하지 않게 이미지가 선택되는 현상이 발생할 수 있다.

이것은 navigation icon이 텍스트이기 때문에 발생하는 문제이다. 이 문제는 텍스트 선택을 차단하는 방법인 `user-select: none;` 프로퍼티를 지정함으로써 회피할 수 있다. user-select 프로퍼티는 현재 W3C CSS 사양에 포함되어 있지 않기 때문에 **벤더 프리 픽스**를 사용하여야 한다.


```css
	.navicon {
    	cursor: pointer;
        height: 60px;
        padding: 28px 15px;
        position: absolute;
        top: 0;
        right: 0;
        
        -webkit-user-select:none;
        -moz-user-select: none;
  		-ms-user-select: none;
  		user-select: none;
    }
```

navigation icon과 checkbox input tag는 스마트폰 layout 이외의 경우, 화면에 표시되면 안된다. 따라서 `display: none;` 으로 화면에 표시되지 않도록 한다. `display: none;` 은 해당 공간조차 점유하지 않지만 `visibility: hidden;` 을 사용하면 해당 공간은 남아있고 표시만 되지 않는다.

CSS 적용 우선 순위를 고려하여 가장 마지막에 정의하는 것이 안전하다. 일반적으로 media query를 가장 마지막에 정의하므로 media query 정의부 직전에 위치시킨다.

```css
	.nav-toggle {
    	display: none;
    }
    .navicon {
    	display: none;
    }
```

tablet용 layout에서 header height를 2배로 하였으므로 `mobile용 layout`을 위해 `다시 60px`로 바꾼다. 콘텐츠 영역도 header 영역 바로 아래로 다시 끌어올린다. 그리고 스마트폰에서 nagivation bar는 초기 상태에서 보이지 않아야 하고, navigation icon은 보여야 한다. (아직 navigation icon을 완성하지 않았으므로 표시되지 않는다.) 마지막으로 navigation icon을 클릭하면 navigation item이 표시되도록 한다.

```css
	@media screen and (max-width: 480px) {
    	header {
        	height: 60px;
        }
        .nav-items {
        	display: none;
        }
        .navicon {
        	display: block;
        }
        #wrap {
			margin-top: 60px;
        }
        aside {
    		top: 60px;
  		}
        
        ...
        
        .nav-toggle:checked ~ .nav-items {
        	display: block;
    		width: 100%;
    		background-color: #fff;
    		box-shadow: 0 2px 2px rgba(0, 0, 0, 0.05), 0 1px 0 rgba(0, 0, 0, 0.05);
        }
        .nav-items > li  {
    		display: block;
 		}
  		.nav-items > li > a {
    		line-height: 50px;
  		}
    }
```
<hr><br>
끝!
