<h2>22.09.18</h2>
<a href="https://velog.io/@leedahye2001/HTML%EC%97%90-%EB%8C%80%ED%95%B4-%EB%AA%B0%EB%9E%90%EB%8D%98-%EB%82%B4%EC%9A%A9-%EC%A0%95%EB%A6%AC">Danshye.log 바로가기 :)</a>
<br>
<h3>🙋‍♀️ 놓친 부분 정리!</h3>
<br>

### ✔️ HTML란?
웹페이지를 기술하기 위한 **마크업 언어**.
웹페이지의 내용과 구조를 담당하는 언어로써 HTML 태그를 통해 **정보를 구조화**하는 것

<br>

### ✔️ HTML5
HTML5 문서는 반드시 **<! DOCTYPE html > **로 시작하여 문서형식을 HTML5로 지정 (태그 앞뒤로 띄어쓰기 없지만 띄우지 않으면 여기 기록이 안됨)

<br>

### ✔️ 시맨틱 웹
웹에 있는 수많은 웹페이지들에 **메타데이터**를 부여하여, 기존의 잡다한 데이터 집합이었던 웹페이지를 **의미**와 **관련성**을 가지는 **거대한 데이터베이스로 구축**하고자 하는 발상이다.


예를 들어,
``` html
1행 : <font size="15"><b>**Hello**</b></font>
2행 : <h4>Hello</h4>
```


👉 결과
> <font size="15"><b>**Hello**</b></font>
> <h4>Hello</h4>
 
 👉 위 결과에 대한 설명!

 둘은 같아보이지만 의미 측면에서 다르다고 할 수 있음
 
 - 1행의 요소 : 폰트 크기와 볼드체를 지정하는 **메타데이터만을** 브라우저에게 **알림**
 => 의미가 명확히 드러나지 않음
 
 - 2행의 요소 : header중 가장 상위 레벨이라는 의미를 내포하고있음
 => 개발자가 **의도한 의미가 명확히 드러남**
 => 코드의 **가독성을 높이며 유지보수를 쉽게 함**
 
<br>


<h3> ✔️ semantic 요소</h3>

> form, table, img 등이 있으며 이들 태그는 content의 의미를 명확히 설명한다.

<br>

<h3> ✔️ non-semantic 요소</h3>

> div, span 등이 있으며 이들 태그는 content에 대하여 어떤 설명도 하지 않는다.

<br>
<br>

### < strong >

b tag와 동일하게 bold체를 지정한다.
하지만 **의미론적 중요성**의 의미를 갖는다는 것이 차이점!

``` html
<!DOCTYPE html>
<html>
  <body>
    <p>This text is normal.</p>
    <strong>This text is strong.</strong>
  </body>
</html>
```

👉 결과
>
<!DOCTYPE html>
<html>
  <body>
    <p>This text is normal.</p>
    <strong>This text is strong.</strong>
  </body>
</html>

<br>
<br>

### < form >

<table>
  <td><b>
    Attribute
  	<td><b>Value</td>
  	<td><b>Description
  </td>
  <tr>
  	<td>Action</td>
    <td>URL</td>
    <td>입력 데이터(form data)가 전송될 URL 지정</td>
  </tr>
    <tr>
  	<td>Method</td>
    <td>get / post</td>
    <td>입력 데이터(form data) 전달 방식 지정</td>
  </tr>
  </td>
  </table>
  
 
<br>

**< Get >**
```
Get은 전송 URL에 쿼리스트링으로 입력데이터를 보내는 방식.
URL에 전송 데이터가 노출이 되므로 보안에 문제가 있으며, 전송 가능한 데이터의 한계가 있음.
```
> ex) http://jsonplaceholder.typicode.com/posts?userId=1&id=1
<br>

**< Post >**
```
Post는 Request Body에 담아서 보내는 방식.
URL에 전송 데이터가 모두 노출되진 않지만 GET에 비해 속도가 느림.
```

> 예) http://jsonplaceholder.typicode.com/posts

<hr>
 END
