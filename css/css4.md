<h2>22.09.26</h2>
<a href="https://velog.io/@leedahye2001/CSS%EC%97%90-%EB%8C%80%ED%95%B4-%EB%AA%B0%EB%9E%90%EB%8D%98-%EB%82%B4%EC%9A%A9-%EC%A0%95%EB%A6%AC-4">
  danshye.log ๋ฐ๋ก๊ฐ๊ธฐ :)</a>
<br>
<h3>๐โโ๏ธ ๋์น ๋ถ๋ถ ์ ๋ฆฌ!</h3>
<br>


### 3. Section & Aside & Footer

ํ์ฌ article์ layout์ ์๊ด์์ด 1ํ์ 1๊ฐ์ฉ ๋ฐฐ์น๋์๋ค.

article์ 2์ด๋ก ๋ฐฐ์นํ๊ธฐ ์ํด์ width ๊ฐ์ ์ง์ ํ์ฌ์ผ ํ๋ค. %๋ก width ๊ฐ์ ์ง์ ํ์ฌ viewport์ ์๋์ ์ธ ๋๋น๋ฅผ ๊ฐ๋๋ก ํ๋ค. ์ด๋ margin๋ %๋ก ์ง์ ํ๋ค. ๊ทธ๋ฆฌ๊ณ  `float: left` ๋ฅผ ์ง์ ํ์ฌ 2์ด๋ก ์ ๋ ฌ๋๋๋ก ํ๋ค.

```css
article {
	width: 48.5%;
	margin: 1%;
	padding: 25px;
	background-color: white;
	float: left;
}
```

์ง์๋ฒ์งธ ๋ฐฐ์น๋๋ article์ ์ข์ธก ๋ง์ง๊ณผ 3๋ฒ์งธ๋ถํฐ ๋ฑ์ฅํ๋ article์ ์์ธก ๋ง์ง์ 0๋ก ํ์ฌ ๊ฐ์ด๋ฐ ๋ง์ง์ด 2๋ฐฐ๊ฐ ๋๋ ๊ฒ์ ๋ฐฉ์งํ๋ค.

```css
article:nth-of-type(2n) {
	margin-left: 0;
}
article:nth-of-type(n+3) {
	margin-top: 0;
}
```

tablet layout์ ์์ฑํ๋ค. 800px ์ดํ๋ก ํ๋ฉด์ด ์์์ง๋ฉด 2์ด ๋ฐฐ์น๋์ด ์๋ article์ 1์ด๋ก ๋ฐฐ์นํ๋ค.

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

mobile layout์ ์์ฑํ๋ค. 480px ์ดํ๋ก ํ๋ฉด์ด ์์์ง๋ฉด ๊ณ ์ ๋์ด์๋ aside๋ฅผ article ์๋ก ์ฌ๋ ค ๋ฐฐ์นํ๋ค.

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
๋
