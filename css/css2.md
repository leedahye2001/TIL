<h2>22.09.20</h2>
<a href="https://velog.io/@leedahye2001/Temp-Title-pw11rc8p">danshye.log 바로가기 :)</a>
<br>
<h3>🙋‍♀️ 놓친 부분 정리!</h3>
<br>


### 1. 반응형 웹 디자인(Responsive Web Design)란?
화면 해상도에 따라 가로폭이나 `배치를 변경하여 가독성을 높이는 것`
즉, 하나의 웹사이트를 구축하여 `다양한 디바이스`의 화면 해상도에 최적화된 웹사이트를 제공하는 것

<br>

### 1.1 viewport meta tag
viewport는 `웹페이지의 가시영역`이며, 디바이스에 따라 차이가 있다.
모바일 브라우저와 데스크탑 브라우저는 서로 구성이나 형태가 다르다. 또한 모바일 화면은 데스크탑 화면보다 작아 데스크탑용 웹페이지를 그대로 모바일에 출력하면 가독성이 나빠진다. 따라서 viewport를 이용하여 `디바이스의 특성과 디바이스의 화면 크기 등을 고려하여` 각종 디바이스 사용자에게 `최적화된 웹페이지 제공`이 가능하다.
<br>

`meta tag`는 브라우저 혹은 검색엔진최적화(SEO)를 위해 검색엔진에게 메타데이터를 전달하기 위해 사용된다.<br>
`viewport meta tag`는 브라우저의 화면 설정과 관련된 정보를 제공한다.

<br>

|프로퍼티|Description|예|
|:-:|:-:|:-:|
|width|viewport 너비(px)<br>기본값: 980px|width=240|
|height|viewport 높이(px)|height=800|
|initial-scale|viewport 초기 배율|initial-scale=1.0|
|user-scale|확대 축소 가능 여부|user-scale=no|
|maximum-scale|viewport 최대 배율|maximum-scale=2.0|
|minimum-scale|viewport 최소 배율|minimum-scale=1.0|

**일반적으로 viewport meta tag는 모바일 디바이스에서만 적용된다.**

<br>

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```
👉 위 예제는 가장 기본적인 viewport 설정이다.<br>
가로폭을 `디바이스의 가로폭`에 맞추고 `초기 화면 배율을 100%`로 설정하는 것을 의미한다.

### 1.2 @media

서로 다른 미디어 타입에 따라 각각의 styles을 지정하는 것을 가능하게 한다.

<br>

```html
<head>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    @media screen {
      * { color: red; }
    }
    @media print {
      * { color: blue; }
    }
  </style>
</head>
```

👉 위 예시는 `일반 화면(screen)`과 `인쇄장치(print)` 별로 `서로 다른 style`을 지정한 것이다.

<br>

반응형 웹디자인에 사용되는 핵심 기술은 `@media`이다.
**@media를 사용하여 미디어 별로 style을 지정하는 것**을 `Media Query`라고 한다.<br>
이는 디바이스를 지정하는 것뿐만 아니라 디바이스의 크기나 비율까지 구분할 수 있다.
<br>
다음은 Media Query의 문법이다.

`code`
```
@media not|only mediatype and (expressions){
	CSS-Code;
}
```
<br>

`CSS`

```css
@media screen and (min-width: 480px){
	body{
    	background-color: lightgreen;
    }
}
```

<br>

아래의 표는 Media Query의 표현식에서 사용할 수 있는 프로퍼티이다.

|프로퍼티|Description|
|:-:|:-:|
|width|viewport 너비(px)|
|height|viewport 높이(px)|
|device-width|디바이스의 물리적 너비(px)|
|device-height|디바이스의 물리적 높이(px)|
|orientation|디바이스 방향 (가로 방향: landscape, 세로방향: portrait)|
|device-aspect-ratio|디바이스의 물리적 width/height 비율|
|color|디바이스에서 표현 가능한 최대 색상 비트수|
|monochrome|흑백 디바이스의 픽셀 당 비트수|
|resolution|디바이스 해상도|

일반적으로 반응형 웹 디자인은 viewport 너비를 기준으로 한다.


아래는 화면이 세로일 때, 가로일 때를 구분해주는 예제이다. 주의할 점은 데스크탑은 언제나 가로화면이므로`device-width`로 스마트폰의 해상도를 지정하지 않으면 데스크탑에서도 가로 화면 시 style이 적용되는 문제가 발생한다.


_* device-width는 디바이스의 물리적인 너비 !! 잊으면 안 됨._

```html
	<head>
		<meta name="viewport" content="width=device-width", initial-scale=1.0>
      	<style>
          * { color: black; }
          
          @media screen
          	and (max-device-width: 760px)
          	and (orientation: landscape) {
          	* { color: skyblue; }
          	}
      	</style>
	</head>
	<body>
      <h1>색이 변하는지 확인하기 위함</h1>
    </body>
```

👉 결과

```html
	<head>
		<meta name="viewport" content="width=device-width", initial-scale=1.0>
      	<style>
          * { color: black; }
          
          @media screen
          	and (max-device-width: 760px)
          	and (orientation: landscape) {
          	* { color: skyblue; }
          	}
      	</style>
	</head>
	<body>
      <h1>색이 변하는지 확인하기 위함</h1>
  </body>
```


<hr><br>
끝!
