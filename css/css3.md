<h2>22.09.22</h2>
<a href="https://velog.io/@leedahye2001/CSS%EC%97%90-%EB%8C%80%ED%95%B4-%EB%AA%B0%EB%9E%90%EB%8D%98-%EB%82%B4%EC%9A%A9-%EC%A0%95%EB%A6%AC-3">danshye.log ๋ฐ๋ก๊ฐ๊ธฐ :)</a>
<br>
<h3>๐โโ๏ธ ๋์น ๋ถ๋ถ ์ ๋ฆฌ!</h3>
<br>


### **2. Responsive Navigation Bar**

์๋๋ ๊ธฐ๊ธฐ์ ๋ฐ๋ผย `breakpoint`๋ฅผ ์ ์ํ ๊ฒ์ด๋ค.ย `Non Mobile First Method`๋ก ์ ์ํ์๊ธฐ ๋๋ฌธ์ Media Query๋ก ์ ์ํ์ง ์์ ์คํ์ผ์ ๋ฐ์คํฌํ ๊ทธ๋ฃน์ ์ํ ์ฝ๋์ด๋ค.

```html
<head>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    /* ํ๋ธ๋ฆฟ ์์ญ : ~ 800px */
    @media screen and (max-width: 800px) {

    }
    /* ์ค๋งํธํฐ ์์ญ : ~ 480px */
    @media screen and (max-width: 480px) {

    }
  </style>
</head>
```

CSS ์ ์ฉ ์ฐ์  ์์์ ๋ฐ๋ผ ๋์ค์ ์ ์ธ๋ ์คํ์ผ์ด ๋จผ์  ์ ์ฉ๋๋ค.

**๋ฐ๋ผ์ Media Query๋ ๊ธฐ์  ์์์ ์๋ฏธ๊ฐ ์๋ค.**

๋ง์ผ ์ค๋งํธํฐ์ฉ ์คํ์ผ์ด ํ๋ธ๋ฆฟ์ฉ๋ณด๋ค ๋จผ์  ๊ธฐ์ ๋๋ค๋ฉด? ์ต์ข์ ์ผ๋ก ํ๋ธ๋ฆฟ์ฉ ์คํ์ผ์ด ์ ์ฉ๋๋ค.

๋ฐ๋ผ์ Non Mobile First ๋ฐฉ์์ ๊ฒฝ์ฐ, max-width์ ๊ฐ์ด ํฐ ๊ฒ๋ถํฐ ์์ฑํ์ฌ์ผ ํ๋ค.

์ผ๋ฐ์ ์ผ๋กย `Mobile-first`ย ๋ฐฉ์์ย `ํด์๋๊ฐ ์์ ์์`,ย `Non-Mobile-first`ย ๋ฐฉ์์ย `ํด์๋๊ฐ ํฐ ์์`๋๋ก ๊ธฐ์ ํ๋ค.

### **2.1 Responsive Navigation Bar - Tablet**

๋ฐ์คํฌํ layout์์ ํ๋ฉด์ด ์์์ง ๋ header navigaion bar๊ฐ header ์์ญ ์๋๋ก ๋ด๋ ค์ค๋ ํ์์ด ๋ฐ์ํ๋ค. ์ด๋ฅผ ๋ณด์ํ๊ธฐ ์ํด ๋ค์๊ณผ ๊ฐ์ด ํ๋ธ๋ฆฟ์์์ layout์ ์ ์ํ๋ค.

viewport width๊ฐ 800px ์ดํ๊ฐ ๋๋ฉด header ์์ญ์ 2๋จ์ผ๋ก ๊ตฌ๋ถํ๊ธฐ ์ํด header ์์ญ์ ๋์ด๋ฅผ ํ์ฌ(60px)์ 2๋ฐฐ๋ก ๋ํ๋ค (120px๋ก). ๊ทธ๋ฆฌ๊ณ  ๋ก๊ณ  ์ด๋ฏธ์ง์ navigation bar๋ฅผ centering ํ๋ค.

<aside>
๐ก ์ด๋ aside, section ์์ญ๋ header์ ๋์ด ๋งํผ ๋ด๋ ค๊ฐ์ผ ํ๋ค!

</aside>

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

logo image์ navigation bar๊ฐ ๊ฐ๋ก๋ก ๋๋ํ ์ ๋ ฌ๋์ด์๋๋ฐ, ์ด๊ฒ์ ์๋จ๊ณผ ํ๋จ์ผ๋ก ๋ถ๋ฆฌ ๋ฐฐ์น ํ๊ธฐ ์ํด navigation bar์ย `float: right;`ย ํ๋กํผํฐ๋ฅผ ํด์ ํ๋ค. ๊ทธ๋ฌ๋ฉด navigation bar๋ย `block`ย ํ๋กํผํฐ๋ฅผ ๊ฐ์ง๊ฒ ๋์ด logo image์ ์๋ ์์ญ์ผ๋ก ๋ด๋ ค๊ฐ๊ฒ ๋๋ค.

```css
@media screen and (max-width: 800px) {
    ...
       nav {
       	float: none;
       }
    ...
}
```

### **2.2 Responsive Navigation Bar - Smartphone**

์ค๋งํธํฐ์ viewport width๋ ๊ฐ๋ก๋ก ๋๋ํ ์ ๋ ฌ๋์ด ์๋ navigation bar๋ฅผ ๋ชจ๋ ๋ด๊ธฐ์๋ ๋๋ฌด ์ข๋ค.

โ ์ฐ์ธก navigition icon(๋ฉ๋ด)์ ํด๋ฆญํ๋ฉด navigation bar๊ฐ ์์ง ์ ๋ ฌ๋์ด ํ๋ฉด์ ๋ํ๋๋๋ก ํ๋ค.

ํ๋ฒ ๋ ํด๋ฆญํ๋ฉด ํ๋ฉด์์ ์ฌ๋ผ์ง๋๋ก ํ๋ฉฐ, ์ด๋ navigation icon์ย `animation`ย ํจ๊ณผ๋ฅผ ๋ถ์ฌํ๋ค.

nav ์์ ๋ด์ ํด๋ฆญํ  ์ ์๋ navigation icon์ ๋ง๋ค๊ธฐ ์ํ html tag๋ฅผ ์ถ๊ฐํ๋ค.ย `label tag์ for`ย ํ๋กํผํฐ ๊ฐ๊ณผย `input tag์ for`ํ๋กํผํฐ ๊ฐ๊ณผย `input tag์ id`ย ํ๋กํผํฐ ๊ฐ์ดย **์ผ์น**ํด์ผ ํ๋ค.

```css
	<nav>
    	<input class="nav-toggle" id="nav-toggle" type="checkbox">
        <label class="navicon" for="nav-toggle"><span class="navicon-bar"></span></label>
        <ul class="nav-items">
        	<li><a href="#home">Home</li>
            ...
```

```css
	<label for="remember-pw">Remember password?</label>
	<input type="checkbox" name="remember-pw" id="remember-pw">
```

input checkbox ์์์ id๊ฐ๊ณผ label์์์ for๊ฐ์ ์ผ์น์์ผ ์ฐ๋ํ๋ฉด

label ์์๋ฅผ ํด๋ฆญํ์ฌ๋ input checkbox ์์๊ฐ ํด๋ฆญ๋๋ค.

์ด ๋ค์์ navigation icon์ ๋ง๋๋ ๊ณผ์ ์!

navigation icon์ input checkbox ์์์ ์ฐ๋๋์ด์ผ ํ๋ฏ๋ก label์์๋ฅผ ์ฌ์ฉํ์๋ค.

์ฆ navigation icon์ ํด๋ฆญํ๋ฉด checkbox input tag๋ย `checked`ย ์ํ๊ฐ ๋๋ค.

์๋๋ navigation icon๋ฅผ ์ ์ํ๋ css.

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

์ ์ฝ๋๋ฅผ ์ค๋ชํ์๋ฉด, navigation icon์ header ์ฐ์ธก์ ์ ๋ ์์น์ ๋ฐฐ์น๋์ด์ผ ํ๋ฏ๋ก

`position: absolute;`ย ๋ฅผ ์ง์ ํ๋ค.

absolute ํ๋กํผํฐ๋ ๋ถ๋ชจ ์์ ๋๋ ๊ฐ์ฅ ๊ฐ๊น์ด ์๋ ์กฐ์ ์์(static ์ ์ธ)๋ฅผ ๊ธฐ์ค์ผ๋ก ์ขํ ํ๋กํผํฐ(top, bottom, left, right)๋งํผ ์ด๋ํ๋ค.

์ฆ, relative, absolute, fixed ํ๋กํผํฐ๊ฐ ์ ์ธ๋์ด ์๋ ๋ถ๋ชจ ๋๋ ์กฐ์ ์์๋ฅผ ๊ธฐ์ค์ผ๋ก ์์น๊ฐ ๊ฒฐ์ ๋๋ค.

๋ง์ผ ๋ถ๋ชจ ๋๋ ์กฐ์ ์์๊ฐ static์ธ ๊ฒฝ์ฐ, document body๋ฅผ ๊ธฐ์ค์ผ๋ก ํ์ฌ ์ขํ ํ๋กํผํฐ๋๋ก ์์นํ๊ฒ ๋จ.

์ด ๊ฒฝ์ฐ, navigation icon์ body๋ฅผ ๊ธฐ์ค์ผ๋ก ์์นํ๋ฉด ๋๋ฏ๋ก ๋ถ๋ชจ ์์์ ๋ณ๋์ ์ฒ๋ฆฌ๊ฐ ํ์์๋ค.

๋ค์์ label tag ๋ด์ span tag์ style์ ์ ์ํ๋ค.

`span tag`๋ navigation icon์ ๋ด๋ถ ๋ง๋ 3๊ฐ(ํด๋ฆญ ์์๋ X ํ์)๋ฅผ ํํํ๊ธฐ ์ํด ์ ์ํ์๋ค.

```css
.navicon-bar {
	display: block;
	width: 20px;
    height: 3px;
    background-color: #000;
}
```

์์ ๊ฐ์ด ํ๋ฉด, navigation icon์ ๋ด๋ถ ๋ง๋ 1๊ฐ๊ฐ ์์ฑ๋๋ค.

`๊ฐ์ ์์ ์ ํ์`๋ฅผ ์ฌ์ฉํ์ฌ navigation icon์ ๋ด๋ถ ์๋ค ๊ณต๊ฐ์ ๋ด๋ถ ๋ง๋๋ฅผ ์ถ๊ฐํ๋ค.

- ์ฌ๊ธฐ์ ๊ฐ์ ์์ ์ ํ์๊ฐ ๊ถ๊ธํ๋ฉด ?ย ๐

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

์ ๋ ์์น๋ฅผ ์ง์ ํ๊ธฐ ์ํดย `postion: absolute;`ย ๋ฅผ ์ฌ์ฉํ๊ธฐ๋๋ฌธ์ ๊ฐ์ ์์์ ๋ถ๋ชจ ์์์ธย span์ย `position: relative;`๋ฅผ ์ถ๊ฐํ๋ค.

```css
.navicon-bar {
	position: relative;
	display: block;
	width: 20px;
    height: 3px;
    background-color: #000;
}
```

์์ง navigation icon์ ํด๋ฆญํด๋ ์๋ฌด ๋ฐ์์ด ์์.

navigation icon์ ํด๋ฆญํ๋ฉด ํด๋ฆญ๋จ์ ์ฌ์ฉ์๊ฐ ํ์ธํ๋๋ก navigation icon์ย `style์ ๋ณํ`์์ผ์ผ ํจ.

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

๋จผ์  ์ค๊ฐ์ ์์นํ ๋ง๋๋ฅผ ์์ ๊ณ , ์ํ ๋ง๋๋ฅผ 45๋ ํ์ ์ํจ๋ค.

์ด๋ ์์น๊ฐ ํ์ด์ง๋ฏ๋กย `top: 0;`๋ก ๋ณด์ ํ๋ค.

navigation icon์ transition ํจ๊ณผ๋ฅผ ๋ฃ์ด์ ์ข ๋ ๋ถ๋๋ฝ๊ฒ ์์ง์ด๋๋ก ํ๋ค.

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

transition ํ๋กํผํฐ๋ property, duration, delay ์์ผ๋ก ์ ์ํ๋ค.

navigation icon์ ํด๋ฆญํ๋ฉด ์๋ํ์ง ์๊ฒ ์ด๋ฏธ์ง๊ฐ ์ ํ๋๋ ํ์์ด ๋ฐ์ํ  ์ ์๋ค.

์ด๊ฒ์ navigation icon์ด ํ์คํธ์ด๊ธฐ ๋๋ฌธ์ ๋ฐ์ํ๋ ๋ฌธ์ ์ด๋ค.

์ด ๋ฌธ์ ๋ ํ์คํธ ์ ํ์ ์ฐจ๋จํ๋ ๋ฐฉ๋ฒ์ธย `user-select: none;`ย ํ๋กํผํฐ๋ฅผ ์ง์ ํจ์ผ๋ก์จ ํํผํ  ์ ์๋ค. user-select ํ๋กํผํฐ๋ ํ์ฌ W3C CSS ์ฌ์์ ํฌํจ๋์ด ์์ง ์๊ธฐ ๋๋ฌธ์ย **๋ฒค๋ ํ๋ฆฌ ํฝ์ค**๋ฅผ ์ฌ์ฉํ์ฌ์ผ ํ๋ค.

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

navigation icon๊ณผ checkbox input tag๋ ์ค๋งํธํฐ layout ์ด์ธ์ ๊ฒฝ์ฐ, ํ๋ฉด์ ํ์๋๋ฉด ์๋๋ค.

๋ฐ๋ผ์ย `display: none;`ย ์ผ๋ก ํ๋ฉด์ ํ์๋์ง ์๋๋ก ํ๋ค.

`display: none;`ย ์ ํด๋น ๊ณต๊ฐ์กฐ์ฐจ ์ ์ ํ์ง ์์ง๋งย `visibility: hidden;`ย ์ ์ฌ์ฉํ๋ฉด ํด๋น ๊ณต๊ฐ์ ๋จ์์๊ณ  ํ์๋ง ๋์ง ์๋๋ค.

CSS ์ ์ฉ ์ฐ์  ์์๋ฅผ ๊ณ ๋ คํ์ฌ ๊ฐ์ฅ ๋ง์ง๋ง์ ์ ์ํ๋ ๊ฒ์ด ์์ ํ๋ค.

์ผ๋ฐ์ ์ผ๋ก media query๋ฅผ ๊ฐ์ฅ ๋ง์ง๋ง์ ์ ์ํ๋ฏ๋ก media query ์ ์๋ถ ์ง์ ์ ์์น์ํจ๋ค.

```css
.nav-toggle {
	display: none;
}
.navicon {
	display: none;
}
```

tablet์ฉ layout์์ header height๋ฅผ 2๋ฐฐ๋ก ํ์์ผ๋ฏ๋กย `mobile์ฉ layout`์ ์ํดย `๋ค์ 60px`๋ก ๋ฐ๊พผ๋ค. ์ฝํ์ธ  ์์ญ๋ header ์์ญ ๋ฐ๋ก ์๋๋ก ๋ค์ ๋์ด์ฌ๋ฆผ.

๊ทธ๋ฆฌ๊ณ  ์ค๋งํธํฐ์์ nagivation bar๋ ์ด๊ธฐ ์ํ์์ ๋ณด์ด์ง ์์์ผ ํ๊ณ , navigation icon์ ๋ณด์ฌ์ผ ํ๋ค.

(์์ง navigation icon์ ์์ฑํ์ง ์์์ผ๋ฏ๋ก ํ์๋์ง ์๋๋ค.)

๋ง์ง๋ง์ผ๋ก navigation icon์ ํด๋ฆญํ๋ฉด navigation item์ด ํ์๋๋๋ก ํ๋ค.

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

---

๋!
