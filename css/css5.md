<h2>22.09.28</h2>
<a href="https://velog.io/@leedahye2001/CSS%EC%97%90-%EB%8C%80%ED%95%B4-
%EB%AA%B0%EB%9E%90%EB%8D%98-%EB%82%B4%EC%9A%A9-%EC%A0%95%EB%A6%AC-5-93k7e38p">danshye.log λ°λ‘κ°κΈ° :)</a>
<br>
<h3>πββοΈ λμΉ λΆλΆ μ λ¦¬!</h3>
<br>


### 1. CSS3 Flexbox Layout (νλ μ€ λ°μ€ λ μ΄μμ)

Flexboxλ λͺ¨λ μΉμ μνμ¬ μ μλ κΈ°μ‘΄ layoutλ³΄λ€ λ μΈλ ¨λ λ°©μμ λμ¦μ λΆν©νκΈ° μν CSS3μ μλ‘μ΄ layout λ°©μμ΄λ€.

μμμ μ¬μ΄μ¦κ° λΆλͺννκ±°λ λμ μΌλ‘ λ³νν  λλ μ μ°ν λ μ΄μμμ μ€νν  μ μλ€. λ³΅μ‘ν λ μ΄μμμ΄λΌλ μ μ μ½λλ‘ λ³΄λ€ κ°λ¨νκ² ννν  μ μλ€.

μλ₯Ό λ€μ΄, κ°λ¨ν flexbox λ μ΄μμμ λ§λ€μ΄ λ³΄μλ©΄ ,,

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

**πΒ μ€ν κ²°κ³Ό**

![](https://velog.velcdn.com/images/leedahye2001/post/82c386bd-63f0-4bcc-b097-6ca55bd3c8ae/image.png)


div μμλ block μμμ΄λ―λ‘ `μμ§μ λ ¬`λλ€. μ΄λ₯Ό `μνμ λ ¬` νλ €λ©΄ `μμμμλ₯Ό inline-block`μΌλ‘ μ§μ νκ±°λ `float` νλ‘νΌν°λ₯Ό μ§μ νλ€.

```css
.item {
	display: inline-blick;
	float: left;
}
```

μ΄λ κ° μμ μμλ₯Ό λΆλͺ¨ μμ λ΄μμ μ λ ¬νκΈ° μν΄μλ κ° μμμμμ λλΉλ₯Ό %λ‘ μ§μ νλ λ±μ μ²λ¦¬κ° νμνλ€. μμ μμμ μ¬μ΄μ¦κ° λΆλͺννκ±°λ λμ μΌλ‘ λ³νν  λλ λ μ²λ¦¬κ° λ³΅μ‘ν΄μ§λ€.

μλλ Flexboxλ₯Ό μ¬μ©ν΄ μμ cssλ¬Έμ λΆλͺ¨ μμ λ΄μμ `μν μ λ ¬`ν κ²μ΄λ€. λΆλͺ¨ μμμ μλμ κ°μ΄ μΆκ°νλ©΄ λλ€.

```css
.container {
	display: flex;
	justify-content: space-around;
}
```

πΒ **μ€ν κ²°κ³Ό**

![](https://velog.velcdn.com/images/leedahye2001/post/8b932ac7-5dc0-41db-a40d-7f4a14a7f5bb/image.png)


### 2. μ¬μ©λ²

Flexbox λ μ΄μμμ **flex item**μ΄λΌ λΆλ¦¬λ λ³΅μμ μμ μμμ μ΄λ€μ λ΄ν¬νλ **flex-container** λΆλͺ¨ μμλ‘ κ΅¬μ±λλ€.

**μ½κ² μ λ¦¬νμλ©΄**

`flex-container : λΆλͺ¨μμ`

`flex item : μμμμ`

μ΄λ κ² κΈ°μ΅νλ©΄ λλ€ γγ

flexboxλ₯Ό μ¬μ©νκΈ° μν΄ HTML λΆλͺ¨ μμμ display μμ±μ flexλ₯Ό μ§μ νλ€.

```css
.container {
	display: flex;
}
```

λΆλͺ¨ μμκ° inline μμμΈ κ²½μ°, μλμ κ°μ΄ inline-flexμ μ§μ νλ€.

```css
.container {
	display: inline-flex;	
}
```

flex λλ inline-flexλ λΆλͺ¨ μμμ λ°λμ μ§μ ν΄μΌνλ μ μΌν μμ±μ΄λ©° `μμ μμλ μλμ μΌλ‘ flex itemμ΄ λλ€.`

### 3. Flexbox container μμ±

**3.1 flex-direction**

flex-direction μμ±μ flex μ»¨νμ΄λμ μ£ΌμΆ λ°©ν₯μ μ€μ νλ€.

- flex-direction: row;

μ’μμ μ°λ‘ μν λ°°μΉλλ€. `flex-direction` μμ±μ `κΈ°λ³Έ κ°`μ΄λ€.

```css
.container{
	padding: 15px;
	border-radius: 5px;
	background: #ccc;

  display: flex;
  flex-direction: row;
}
```

πΒ **μ€ν κ²°κ³Ό**
![](https://velog.velcdn.com/images/leedahye2001/post/c6c85171-a525-4da2-8ea1-56590eddfde7/image.png)

<hr>

* flex-direction: row-reverse;

μ°μμ μ’λ‘ μν λ°°μΉλλ€.

πΒ **μ€ν κ²°κ³Ό**

![](https://velog.velcdn.com/images/leedahye2001/post/b7358d75-ec18-49e7-b25b-c4e0190352a3/image.png)

<hr>

* flex-direction: column;

μμμ μλλ‘ μμ§ λ°°μΉλλ€.

πΒ **μ€ν κ²°κ³Ό**
![](https://velog.velcdn.com/images/leedahye2001/post/84073bec-93f4-4b6e-a543-2cd25e1e7825/image.png)

<hr>

- flex-direction: column-reverse;

μλμμ μλ‘ μμ§ λ°°μΉλλ€.

πΒ **μ€ν κ²°κ³Ό**

![](https://velog.velcdn.com/images/leedahye2001/post/b1a8dac6-3f09-43b8-baa4-eed6fd8bce08/image.png)

**3.2 flex-wrap**
