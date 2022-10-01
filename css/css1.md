

<a href="https://velog.io/@leedahye2001/CSS%EC%97%90-%EB%8C%80%ED%95%B4-%EB%AA%B0%EB%9E%90%EB%8D%98-%EB%82%B4%EC%9A%A9-%EC%A0%95%EB%A6%AC">danshye.log 바로가기!</a>
### ✔️ CSS
- HTML이나 XML과 같은 구조화 된 문서를 화면, 종이 등에 **어떻게 렌더링할 것인지**를 정의하기 위한 언어
- HTML의 각 요소의 **style**을 정의하여 화면 등에 어떻게 렌더링하면 되는지 브라우저에게 설명하기 위한 언어

<br>

### ✔️ 어트리뷰트 셀렉터 (Attribute Selector)


#### ✍ ex 1 )

<table> 
  <td style="background-color:slategrey;"><b>패턴
  	<td style="background-color:slategrey"><b>Description</td>
     <tr>
   		<td>셀렉터[어트리뷰트]
  		</td>
        <td>지정된 어트리뷰트를 갖는 모든 요소를 선택한다.
  		</td>
     </tr>
  </td>
</table>

```
 <head>
  <style>
    /* a 요소 중에 href 어트리뷰트를 갖는 모든 요소 */
    a[href] { color: red; }
  </style>
</head>
<body>
  <a href="http://www.google.com" target="_blank">google.com</a><br>
</body>
```
   
<br> 

👉 결과


> <a href="http://www.google.com" target="_blank">google.com</a><br>

<br>

<br>

#### ✍ ex 2 )

<table> 
  <td style="background-color:slategrey"><b>패턴
  	<td style="background-color:slategrey"><b>Description</td>
     <tr>
   		<td>셀렉터[어트리뷰트~=”값”]
  		</td>
        <td>지정된 어트리뷰트의 값이 지정된 값을 (공백으로 분리된) 단어로 포함하는 요소를 선택한다.
  		</td>
     </tr>
  </td>
</table>

```　
 <head>
  <style>
    /* h1 요소 중에 title 어트리뷰트 값에 "first"를 단어로 포함하는 요소 */
    h1[title~="first"] { color: red; }
  </style>
</head>
<body>
  <h1 title="heading first">Heading first</h1>
  <h1 title="heading-first">Heading-first</h1>
</body>
```
   
<br> 

👉 결과

>  <h1 title="heading first">Heading first</h1>
>  <h1 title="heading-first">Heading-first</h1>


<br>

### ✔️ Box
![](https://velog.velcdn.com/images/leedahye2001/post/35b06fa0-c621-4908-b7d9-4128cce353da/image.png)

- Box는 콘텐트(Content), 패딩(Padding), 테두리(Border), 마진(Margin)으로 이루어짐

- 브라우저는 **박스 모델의 크기와 프로퍼티, 위치**를 근거로 하여 **렌더링을 실행함**
    
<br>
<table> 
  <td style="background-color:slategrey"><b>명칭
  	<td style="background-color:slategrey"><b>설명</td>
     <tr>
   		<td>Content
  		</td>
        <td><b>실제 내용(텍스트나 이미지)</b>이 위치하는 영역
  		</td>
     </tr>
  <tr>
   		<td>Padding
  		</td>
    <td><b>테두리 안쪽에 위치하며 요소의 내부 여백 영역. </b>padding 프로퍼티 값은 패딩 영역의 두께를 뜻함. 요소에 적용된 배경 컬러 및 이미지는 패딩 영역까지 적용됨.
  		</td>
     </tr>
  <tr>
   		<td>Border
  		</td>
        <td>테두리 영역. border 프로퍼티 값은 테두리의 두께
  		</td>
     </tr>
  <tr>
   		<td>Margin
  		</td>
        <td><b>테두리 바깥에 위치하는 요소의 외부 여백 영역.</b> margin 프로퍼티 값은 마진 영역의 두께를 의미. 배경색 지정 불가
  		</td>
     </tr>
  </td>
</table>
    
<br>

    
<h3> ✔️ Padding과 Margin의 차이점은?</h3>
    
>   Padding은 테두리의 안쪽에 위치하며 요소의 내부 빈 공간이고, Margin은 테두리의 바깥쪽에 위치하며 요소의 외부 여백 영역이다.
    
    
    
<br>

### ✔️ 캐스캐이딩(Cascading)

하나 이상의 CSS 선언의 충돌을 피하기 위해 **CSS 적용 우선순위**
    
- **중요도**
`CSS가 어디에 선언 되었는지에 따라 우선순위가 달라짐`
    
- **명시도**
`대상을 명확하게 특정할수록 명시도가 높아지고 우선순위가 높아짐`
    
- **선언순서**
`선언된 순서에 따라 우선 순위가 적용됨. (나중에 선언된 스타일이 우선 적용)`
    
<hr><br>
끝
