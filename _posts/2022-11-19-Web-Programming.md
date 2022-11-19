---
layout: single
title: "about Web Programming"
toc: true
toc_sticky: true
toc_label: "study"
categories:
    - Study
---

<br>

<br>

## 웹프로그래밍 (3월 16일)

<br>

### 월드와이드웹과 HTML

<br>

프론트엔드 프로그래밍의 근간이 되는 월드와이드웹을 살펴보고 월드와이드웹 콘텐츠 제작을 위해 필수적인 HTML의 기본 개념과 구조 등을 살펴본다. 

이 강의를 통해 월드와이드웹의 기본 개념과 HTML 문서의 기본 구조를 이해하고 css, javascript 와의 관계를 배우게 된다.

<br>

> WWW : World Wide Web 
>> 월드와이드웹은 대표적인 인터넷 서비스 중 하나로 언제 어디서나 접속 가능한 정보 서비스이다.

<br>

- 인터넷은 컴퓨터 네트워크 망을 의미하고, 웹은 인터넷 서비스입니다.
- 홈페이지는 특정 월드와이드웹 서비스의 시작 화면을 의미 합니다. 예를 들어 네이버에 접속하면 나오는 화면이 바로 홈페이지 입니다.

<br>

- 클라이언트: 웹서비스를 이용하는 사용자
- 서버: 웹서비스를 제공하기 위한 서비스 공급자
- 프론트엔드 프로그래밍: 클라이언트 중심의 프로그래밍 -> HTML, JavaScript, CSS
- 백엔드 프로그래밍: 서버를 구성하고 서비스를 제공하기 위한 프로그래밍 -> 웹서버SW, 웹프레임워크, 데이터베이스

<br>

- **HTML (Hyper Text Markup Laguage)** &rarr; Static
	- 웹 문서의 구조를 정의하고 콘텐츠를 표현하는 기본 마크업 언어
	- Hyper Text : 링크가 포함된 텍스트
	- Markup Language : 텍스트에 의미를 부여하기 위해 문서에 주석을 다는 시스템.

- **CSS (Cascading Style Sheet)**
	- HTML 문서에 레이아웃과 디자인을 포함한 시각적 요소를 정의하기 위한 규격.
	- HTML은 콘텐츠 내용과 구조를 정의하고 CSS에서 콘텐츠의 위치, 정렬, 글자크기, 여백, 배경색상 등을 정의하는 구조임.
	- HTML 요소를 **Selector**로 지정해 원하는 디자인 속성을 부여함.

- **- JavaScript** 
	- HTML 문서에 이벤트 처리나 동적으로 변화하는 콘텐츠를 표현하거나 서버와의 연결을 통해 데이터를 가지고 오는 등의 프로그램적인 요소
	- 서버에 새로 접속하지 않고도 화면의 정보가 변하는 기능

그니까 실시간으로 변하는 이미지들은 JavaScript로 동작하는 것이다.

<br>

### HTML tag

<br>

- Tag 

HTML의 기본 구성요소는 Tag 이며 태그는 <> 를 사용하여 나타낸다.

주석은 `<!--내용-->`

<br>

- Attribute (속성)

Attribute는 HTML Tag에 부가적인 정보를 제공하는 방법이다. 

그러나 html5 부터는 디자인적인 표현을 위한 속성들은 css로 이전되어 태그에서 사용할 수 있는 속성은 그리 많지 않음 ,,

Ex_ 그림을 넣기 위해 사용하는 `<img>` Tag의 경우 그림 파일의 위치를 지정하기 위한 src 속성이 존재한다.

```html
<img src="/img/smile.jpg" width="500" height="300"> 
```

<br>

- Tag Body

Tag와 Tag 사이의 콘텐츠를 의미.

```html
<h2>Hello World</h2>
<ul>
	<li>item1</li>
	<li>item2</li>
</ul>
```

<br>

### HTML 기본 문서 구조

<br>

```html

<!DOCTYPE html> , <HTML>, <HEAD>, <TITLE>, <BODY> 태그로 이루어져 있음

__

<!doctype html>

<html>
	<head>
		css, js, Meta (Link, File 등..)
	</head>

	<body>
		Content !!
	</body>

</html>
```

<br>

Basic HTML Tamplate !!

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <h2> Hello World </h2>
    <hr>
    My name: Kim Jungjun <br>
    Dept : Physics <br>
    Student ID : 202135317 
</body>
</html>
```

<br>

대부분 우리가 작성하는 코드는 `<body>`와 `</body>` 사이에 작성하게 됨 !!

- charset : 캐릭터셋으로 정상적인 한글 처리를 위해서는 반드시 UTF-8 세팅
- viewport : 서로 크기가 다른 디바이스에서 화면 최적화를 위한 설정
- http-equiv : HTTP 헤더 정보를 설정하는 속성
- X-UA-Compatible : 브라우저의 호환성보기 설정으로 ie=edge 설정은 항상 최신 렌더링 엔진을 사용한다는 의미

<br>

- 레이아웃

<br>

레이아웃은 화면의 구성 요소들을 배치하는 것을 말하는 것으로 웹페이지 디자인을 시작할 때 제일 먼저 해야하는 작업이다. 레이아웃 자체를 표현하는건 당연히 CSS 영역이지만, 문서의 구조를 레이아웃에 맞춰 설계하는 것은 HTML 영역이다. 보통 `<div>` 태그를 이용해 구획을 나누기도 하고 HTML5의 Semantic Tag 를 이용하기도 한다.

> HTML5 에서는 <header>, <nav>, <section>, <aside> 등의 Semantic 태그를 통해 영역 구분을 지원

<br>

### 예제 1-1) 웹페이지 요청하기 및 소스 보기

<br>

> url 을 이용해 원하는 웹페이지를 직접 요청하는 과정을 통해 웹의 기본적인 동작 구조인 request &rarr; response 개념을 살펴본다.
  
<br>
  
## 웹프로그래밍 (3월 24일)

<br>

### HTML 기본태그

<br>

제목, 문단, 형식, 목록, 하이퍼링크 등 HTML의 기본 태그들의 종류와 사용법을 배워보자.

콘텐츠 구조 설계 가능하게끔 공부하자

<br>

```
<html> 태그는 문서의 시작과 종료를 나타냄 !

<head> 태그는 HTML 문서에 필요한 여러 정보를 표시하는 메타 컨테이너 !
- <title> 태그를 통해 브라우저 상단 타이틀 정의
- JavaScript 및 CSS 코드를 직접 작성하거나 외부 파일을 import 혹은 url link.
- <meta> 태그를 통해 모바일 화면설정과 SEO (Search Engine Optimization) 정보 제공
- 모든 컨텐츠는 <body> </body> 사이에 위치해야 함

Block 태그

- 한 줄에 여러 요소가 위치하지 못하는 태그를 말한다.

ex_ <div>, <h1>, <h6>, ...

Inline 태그

- 나란히 배치 가능한 태그 ..

ex_ <span>, <a>, <img>, ...

나중에는 CSS로 서로 전환 가능 ..
```

여러 공백을 넣으려면 `&nbsp;` 

그다지 권장되는 방법은 아님 .....

이 수업 개꿀인게 태그 배워서 마크다운 파일에 그대로 적용할 수 있음 ,,,

`<strong> & <em> , <b> & <i> 태그의 결과가 같지만, 그 태그가 가지는 의미가 다르다..`


<br>

**목록 태그 중요함 !** &rarr; List 

`두 종류가 있다. <ul> <ol>`

Unordered List : 순서없이 모양으로 목록을 만듦 ...... 

Ordered List : 번호를 매기는 순서가 있는 목록을 만듦 ......

<br>

### 하이퍼링크

웹의 대표적인 특징, `<a>` (Anchor) 태그를 사용해 만들 수 있음 ..

href 속성을 사용해 이동할 컨텐츠의 주소를 기술하면 됨 ...

```html
<a href="이동할 컨텐츠" target="브라우저 윈도우 옵션">링크 텍스트</a>
```

href 에 들어가는 이동할 컨텐츠의 위치 &rarr; 상대경로 혹은 절대경로로 표현 가능

물론 내 컴퓨터 위치가 아니라 .. html 을 서비스하고 있는 웹서버 컴퓨터에서 콘텐츠 간의 위치를 말하는 것 ..

- 절대경로는 고유한 경로로 root (/) 에서부터 시작되는 위치로 지정하는 방법
	- ex_ /home/contents/img/1.jpg

- 상대경로는 HTML 문서를 기준으로 경로를 지정하는 방법. 권장 방법 !!
	- img/1.jpg

사실 절대경로를 쓰면 잘못될 일도 없고 좋음. 그러나 경우에 따라서 이 경로가 매우 길어짐 .. 즉 불편할수도 있음.

그러니까 콘텐츠의 위치가 가깝다면 그냥 상대경로를 쓰면 됨.

상황에 맞게 쓰면 되는거임 !!

- Local 컴퓨터의 절대경로를 쓰면 안 됨. 당연한 소리

<br>

target 속성 값

- _blank &rarr; 새로운 웹 브라우저 창으로 오픈
- _self &rarr; default (현재 웹 브라우저 창으로 오픈)
- _parent &rarr; 부모 웹 브라우저 창으로 오픈
- _top &rarr; 웹 브라우저 전체 영역에 오픈 / 근데 이건 요즘 안 씀

<br>

### 책갈피 구현

- `<a>` 태그를 이용해 같은 문서 내에서 특정 위치로 이동하는 책갈피 기능 구현 가능
- `<p>` 태그의 name 속성이나 id 속성을 이용해 문서 내 이동위치를 지정하고 하이퍼 링크에 `href=#name(id)` 과 같이 이동할 위치를 지정함.

```html
메뉴
<a href="#ml">5.HTML이란 무엇인가?</a>
......
<p id="ml"></p>
<h3>5.HTML이란 무엇인가?</h3>
```

href 태그의 ID 앞에는 반드시 # ..

ID 값은 문서 내에서 유인을 해야됨.. 즉 중복 X

그니까 뭐다? 찾기가 쉽다 .. 유일한 위치 .. !!

<br>

실습 과제 할 때 윈도우 사이즈 반드시 줄일 것 .. ^^

<br>

### 이미지 링크

- 텍스트가 아닌 이미지를 링크로 사용할 수도 있음 .. 이 경우 `<a><img></a>` 형식 .. 

```html
<a href="http://www.gachon.ac.kr">
	<img src="gachonlogo.jpg" alt="gachon_logo">
</a>
```

<br>

### 예제 2-1) 제목과 문단 태그 활용

```html
<!doctype html>
<html> 
    <head>
        <title> Example : 2-1 </title>
    </head>
    <body>
        <h1> example 2-1 </h1>
        <h2> html example </h2>
        
        <p> hello world </p>
        <p> hello
             world
        </p>
        <p> hello <br> world </p>
        <pre>
            hello world
            hello
                world
        </pre>
        <pre>
            <h2> hello
                     world
            </h2>
        </pre>
    </body>
</html>
```

<br>

### 예제 2-2) 텍스트 관련 태그 활용

```html
<!doctype html>
<html> 
    <head>
        <title>Example: 2-2</title>
    </head>
    <body>
        <b>bold text</b><br>
        <strong>strong text</strong><br>
        <i>italic text</i><br>
        <em>emphasized text</em><br>
        <mark>mark text</mark><br>
        <small>small text</small><br>
        <del>deleted text</del><br>
        <ins>inserted text</ins><br>
        This is <sup>superscript text</sup><br>
        This is <sub>subscript text</sub>
        
    </body>
</html>
```

<br>

### 예제 2-3) 목록 만들기

```html
<!doctype html>
<html> 
    <head>
        <title>Example: 2-3</title>
    </head>
    <body>
        <h2>Unordered List</h2>
        <ul type="square">
        <li>Coffee</li>
        <li>Tea</li>
        <li>Milk</li>
        </ul>  

        <h2>Ordered List</h2>
        <ol type="A">
        <li>Coffee</li>
        <li>Tea</li>
        <li>Milk</li>
        </ol> 
    </body>
</html>
```

<br>

### 예제 2-4) 하이퍼링크 활용

```html
<!doctype html>
<html> 
    <head>
        <title>Example: 2-4</title>
    </head>
    <body>
        <a href="http://www.gachon.ac.kr" target="_blank">Gachon</a> <br>
    </body>
</html>
```

<br>

### 예제 2-5) 책갈피 구현

```html
<!doctype html>
<html> 
    <head>
        <title>Example: 2-5</title>
    </head>
    <body>
        <h1>Menu</h1>
        <a href="#index1">Coffee</a><br>
        <a href="#index2">Cake</a><br>
        <a href="#index3">Juice</a><br>

        
        <h2 id="index1">Menu01::Coffee</h2>
        <ul>
            <li>Americano</li>
            <li>Cappuccino</li>
            <li>Cafe latte</li>
        </ul>
        
        <h2 id="index2">Menu02::Cake</h2>
        <ul>
            <li>Carrot cake</li>
            <li>black tea cake</li>
            <li>Strawberry shortcake</li>
        </ul>
        
        <h2 id="index3">Menu03::Juice</h2>
        <ul>
            <li>orange</li>
            <li>grape</li>
            <li>watermelon</li>
        </ul>

    </body>
</html>
```
  
<br>
  
<br>


## 웹프로그래밍 (3월 31일)

<br>

### 이미지와 테이블

<br>

대표적인 웹 콘텐츠 리소스인 이미지를 보여주기 위한 방법과 데이터 표현을 위한 테이블의 구조 및 활용법을 배운다.

이 강의를 통해 `<img>` 태그의 상세 사용법을 배워 웹 콘텐츠 제작에 이미지를 자유롭게 활용할 수 있으며, 테이블을 활용해 데이터 구조를 표현 할 수 있다.

<br>

```html
<img src="이미지 경로" alt="대체텍스트" width = "너비" height = "높이">
```

<br>

- jpg/jpeg

가장 대표적인 이미지 파일 형식, 압축을 통해 용량을 줄인 이미지 형식.

- gif

256 색상만 표현 가능, 움직이는 이미지, 투명 이미지 처리가 가능.

- png

Portable Network Graphics의 약어로 jpg 와 함께 많이 사용되는 형식. 고화질을 유지하면서 투명 이미지도 지원한다.

- svg

Scalable Vector Graphics의 약어로 xml형식의 벡터 이미지(이미지 처리를 픽셀이 아닌 수학적 계산에 따른 선의 연결로 계산해서 처리)처리 규격이다. 벡터 이미지 특성상 크기 변화에 따라 이미지가 손상되지 않는 특징이 있다.

<br>

Note: 서버에서 동작하는 것을 전제로 하기 때문에 절대로 컴퓨터의 경로인 

c:\document\html\img\a.jpg 와 같은 경로는 사용하면 안 됨

<br>

### 테이블 기본 구조

<br>

```html
<table>
    <tr><th>title1</th><th>title2</th><th>title3</th></tr>
    <tr><td>title1</td><td>title2</td><td>title3</td></tr>
    <tr><td>title1</td><td>title2</td><td>title3</td></tr>
</table>
result
```

<br>

```html
<table>
    <thead>
        <tr><th>title1</th><th>title2</th><th>title3</th></tr>
    </thead>
    <tbody>
        <tr><td>title1</td><td>title2</td><td>title3</td></tr>
    </tbody>
    <tfoot>
        <tr><td>title1</td><td>title2</td><td>title3</td></tr>
    </tfoot>
</table>
```

<br>

> colspan

컬럼 (열) 을 확장할때 사용. 좌우로 원하는 칸만큼 시작 위치의 td 태그에 속성으로 지정.

<br>

```html
<table border="1">
<tr><td>1</td><td colspan="2">2, 3</td></tr>
<tr><td>4</td><td>5</td><td>6</td></tr>
</table>
```

<br>

> rowspan
로우 (행) 을 확장할때 사용. 위아래로 원하는 칸만큼 시작 위치의 td 태그에 속성으로 지정.

<br>

```html
<table border="1">
<tr><td rowspan="2">1,4</td><td>2</td><td>3</td></tr>
<tr><td>5</td><td>6</td></tr>
</table>
```

<br>

### 실습

<br>

```html
<!doctype html>
<html> 
    <head>
        <title>Example: 3-1</title>
    </head>
    <body>
        <img src="https://t1.daumcdn.net/cfile/tistory/17441F41509D287F03" width="100px" height="100px">
        <hr>
        <img src="https://XXX" alt="가천대 로고">
    </body>
</html>
```

<br>

```html
<!doctype html>
<html> 
    <head>
        <title>Example: 3-2</title>
    </head>
    <body>
        <img src="img/sample.png">
    </body>
</html>
```

<br>

```html
<!doctype html>
<html>
    <head>
        <title>Example: 3-3</title>
    </head>
    <body>
        <table border="1">
            <tr>
                <th>no.</th>
                <th>name</th>
                <th>email</th>
                <th>tel</th>
            </tr>
            <tr>
                <td>1</td>
                <td>James Kang</td>
                <td colspan="2">james@gachon.ac.kr,010-1234-1234</td>
            </tr>
            <tr>
                <td rowspan="2">2</td>
                <td>Justin Born</td>
                <td>justin@google.com</td>
                <td>010-9876-1234</td>
            </tr>
            <tr>
                <td>Mariata Kumba</td>
                <td>kumba@amazon.com</td>
                <td>010-2222-3333</td>
            </tr>
            <tr>
                <td>4</td>
                <td>Mola Landa</td>
                <td>mola@naver.com</td>
                <td>010-4444-5555</td>
            </tr>
        </table>
    </body>
</html>
```

<br>

```html
<!doctype html>
<html>
    <head>
        <title>Example: 4-1</title>
    </head>
    <body>
        <h2>html-11.html : Naver search</h2>
        <form action=""> 
        search: <input type="text">
        <input type="submit" value="search">
        </form>
    </body>
</html>
```

<br>

### 과제 (q1.html)

<br>

```html
<!doctype html>
<html>
    <head>
        <title>q1</title>
    </head>
    <body>
        <table border = "1" width="300px" height="300px">
            <tr>
                <th>1</th>
                <th>2</th>
                <th rowspan="2">3</th>
                <th>4</th>
            </tr>
            <tr>
                <td colspan="2">5</td>
                <td rowspan="2">6</td>
            </tr>
            <tr>
                <td>7</td>
                <td colspan="2">8</td>
            </tr>
        </table>
    </body>
</html>
```
<br>
  
## 웹프로그래밍 (4월 7일)

<br>

### 입력 양식

<br>

이번 강좌에서는 웹에서 사용자 입력을 처리하기 위한 입력양식(form)의 종류와 사용법을 배우게 됩니다. 

회원가입이나 게시글 포스팅 등 무언가를 입력해서 서버로 전송하거나 상품 주문시 옵션을 선택하고 주소를 입력하고 주문버튼을 누르는 등의 모든 화면들이 입력 양식에 해당 합니다.

이 강의를 통해 여러 입력양식 태그를 이해하고 원하는 양식을 디자인 할 수 있으며 입력양식과 서버의 연동 원리를 이해할 수 있게 됩니다.

<br>

입력 양식 &rarr; 웹에서 사용자에게 정보를 입력 받을 때 사용하는 UI를 말한다.

기본적으로 `<form>` 태그가 사용 된다.

<br>

### form 태그

<br>

```html
<form function = "데이터를 전송할 URL" method="전송방법">
	<input type = "text>
</form>
```
		       
<br>

전송 방법 : GET, POST

<br>

GET

- 기본 메소드는 GET 방식. (**GET은 서버에 데이터를 요청할 때 사용**)
- GET을 사용하면 제출된 양식 데이터가 페이지 주소 빌드에 표시됨.

<br>

POST

- 데이터를 서버에 전송할 때 사용.
- 전송할 폼 데이터에 중요 정보나 개인 정보가 포함되어 있으면 항상 POST 방식 사용 권장.
- 경우에 따라서는 파일을 전송하는 것도 가능함. (일반적인 텍스트 데이터 전송과는 다름)

<br>

### 입력 양식 태그

<br>

기본적으로는 `<input>` 태그를 사용하며 type 속성으로 다양한 입력 양식을 정의할 수 있다. (그 외에도 `<select>`,`<textarea>`,`<button>` 태그 사용 가능)

<br>

### `<input>` 태그

<br>

가장 많이 사용하는 입력 방식 태그이며 대부분의 입력 기능을 제공한다. type 속성으로 입력 양식의 종류를 나타내고 name 속성으로 서버에 전송될 데이터 이름을 지정한다.

<br>

`type`

&uarr;

필수 속성이며 사용할 수 있는 type은 다음과 같습니다.

text : 텍스트 입력 필드
password : 비밀번호 입력필드
checkbox : 복수 선택 가능한 체크 박스
radio : 복수 선택 불가능한 라디오 버튼 생성
submit : 입력양식을 서버로 전송하기 위한 버튼
reset : 리셋 버튼
button : 일반 버튼

<br>

`name`

```html
<input type="text" name="userid">
<input type="assword" name="pwd">
```

<br>

### `<button>` 태그

<br>

입력 양식에서 매우 많이 사용되는 구성요소입니다. 다만 그냥 버튼을 생성해서는 아무런 동작을 하지 않고 별도의 이벤트 처리와 연동되어야 함로 실제 활용은 자바스크립트 학습 요구.

<br>

- CSS 사용시 별도 디자인 적용이 편리함

<br>

### `q2.html`

<br>

```html
<!doctype html>
<html>
    <body>
        <form action=""> 
        First name: <br>
            <input type="text">
        </form>
        <form action=""> 
        Last name: <br>
            <input type="text">
        </form>
        <form action=""> 
        Email: <br>
            <input type="text">
        </form>
        <form action="">
        Gender:
            <input type="radio" name="GOOD">Male,
            <input type="radio" name="GOOD">Female
        </form>
        <form action="">
            Favorite:
                <input type="checkbox" name="GOOD">HTML,
                <input type="checkbox" name="GOOD">Java,
                <input type="checkbox" name="GOOD">PHP
            </form>
        <form action="">
        University:
        <select name=“cars”>
            <option value=“101”>Gachon University</option>
        </select>
        </form> 
        <form action="">
        Color:
            <input type = "color">
        </form>
        <form action=""> 
        Date:
            <input type="date" placeholder="연도-월-일">
        </form>
        <form action="">
            <input type = "submit" name = "Registration" placeholder = "Registration">
        </form>
    </body>
</html>
```
                                                                                     
<br>
                                                                                     
<br>

## 웹프로그래밍 (4월 14일)

<br>

### CSS 개념 이해

<br>

이번 강의에서는 CSS의 기본 개념과 구조, 문법등을 배우게 됩니다. 

CSS는 HTML로 만들어진 콘텐츠에 레이아웃과 디자인요소를 정의하는 기술로 잘 설계된 css 는 재활용이 가능하며 나아가 테마, 

템플릿의 형태로 확장할 수 있습니다. 

또한 자바스크립트와 연계해 콘텐츠의 내용이나 디자인을 동적으로 처리할 경우에도 유용하게 사용됩니다.

<br>

### CSS 개요

<br>

CSS는 HTML과 함께 웹을 구성하는 기본 프로그래밍 요소입니다.

- CSS &rarr; Cascading Style Sheet
- 자바스크립트와 연계해 동적인 콘텐츠 표현이나 디자인 적용 가능

<br>

CSS를 사용해야만 하는 이유

- 웹 문서의 내용과 상관없이 디자인만 바꾸거나 디자인은 그대로 두고 웹 문서의 내용 변경이 용이
- 동일한 문서구조를 가지고 서로 다른 CSS 테마 적용이 가능 함.

<br>

### CSS 기본 문법

<br>

CSS는 선택자와 선언부로 구성된다

선택자 (Selector) 는 스타일을 지정할 HTML 요소 (태그, 아이디 등) 를 가리킨다.

<br>

**선택자의 중요성**

- CSS의 핵심은 적절한 선택자를 사용하는 것이며 복잡한 문서 구조에서 특정 부분을 선택하기 위한 선택자 지정은 어려울 수 있으며 html 구조를 처음부터 잘 설계하는 것이 중요함.

<br>

### CSS 적용 방법

<br>

1. 내부 스타일시트
2. 외부 스타일시트
3. 인라인 스타일시트

<br>

### 내부 스타일시트

<br>

html 파일에 스타일을 기술하는 방법으로 `<head></head>` 태그 사이에 `<style></style>` 태그 부분에 작성합니다. 

html 과 css 가 한 파일에 있으므로 작업이 쉽고 간편하지만 

**css의 재활용이 안되는 문제가 있어** 특별한 경우가 아니면 외부 스타일시트가 권장 됩니다.

```html
<head>
<style>
body {
    background-color: red;
}

h1 {
    color: maroon;
    margin-left: 40px;
} 
</style>
</head>
<body>
    ...
</body>
```

<br>

### **외부 스타일시트**

<br>

**css 를 작성하는 가장 기본적인 방법 입니다.**

별도의 파일에 CSS 문서를 작성하고 해당 CSS를 필요로 하는 html 문서에서 불러와 사용하는 형식 입니다. 

이때 css는 동일한 서버에 있어도 되고 url을 통해 다른 서버의 css를 불러오는 것도 가능합니다.

```html
<link rel="stylesheet" type="text/css" href="mystyle.css">
<link rel="stylesheet" type="text/css" href="http://cdn.site.com/css/mystyle.css">
```

<br>

### 인라인 스타일시트

<br>

css 를 작성하는 가장 기본적인 방법 입니다. 

별도의 파일에 CSS 문서를 작성하고 해당 CSS를 필요로 하는 html 문서에서 불러와 사용하는 형식 입니다. 

이때 css는 동일한 서버에 있어도 되고 url을 통해 다른 서버의 css를 불러오는 것도 가능 합니다.

```html
<h1 style="color:blue; margin-left:30px;">This is a heading</h1>
```

<br>

### 캐스케이딩과 우선순위

<br>

> 캐스케이딩 의미

css 에서 Cascading 은 사전적 의미로 **`폭포처럼 떨어져 내리는`** 과 같은 의미를 가지고 있습니다.

```html
<!-- body 태그 안에 있는 모든 태그 요소들은 빨간색 글자로 표시됨 -->
<body style="font-color:red">
    <h1>Hello</h1>
</body>
```

<br>

### 우선 순위

<br>

동일한 디자인 속성이 외부 스타일시트, 내부 스타일시트, 인라인 스타일시트에 적용 되어 있는 경우 

우선순위는 가장 나중에 정의되는 스타일에 있습니다. 

따라서 **인라인 스타일시트**가 가장 높은 우선순위로 적용되고 외부 스타일시트와 내부 스타일시트는 문서상 정의된 순서에 따라 

우선순위가 결정되는 형식입니다.

<br>

웹 브라우저 자체도 html 구성요소에 대한 내부적인 css 를 가지고 있다고 볼 수 있습니다. 

브라우저에 따라 사용자 정의 css를 사용할 수 있는것도 그 때문입니다. 

일반적인 우선순위 (낮은순 &rarr; 높은순) 는 다음과 같습니다.

**브라우저 디자인 정의 &rarr; 외부 스타일시트 &rarr; 내부 스타일시트 &rarr; 인라인 스타일시트**                                                                                    
<br>
			    
<br>

## 웹프로그래밍 (4월 28일)

<br>

### 셀렉터란 ?

<br>

스타일은 적용 대상이 있어야 하는데 셀렉터가 바로 그 대상입니다. 

기본적으로 태그, 아이디, 클래스를 셀렉터로 사용하며 이들을 조합해서 특정 조건에 맞는 셀렉터를 정의해 사용하게 됩니다.

<br>

## 웹프로그래밍 (5월 10일)

<br>

### 박스 모델

<br>

이번 강좌에서는 css 에서 화면 구성요소를 다루기 위한 기본적인 방법인 박스 모델에 대해 살펴 봅니다. 

박스 모델은 구성요소를 배치해 웹 페이지 레이아웃을 구성할 때 매우 중요한 개념입니다. 

또한 박스 모델들의 화면 배치를 위한 position 속성과 float, display 속성들을 활용하는 레이아웃 기법을 배웁니다.

이 강의를 통해 박스모델을 정의하고 웹페이지 레이아웃을 설계할 수 있으며 원하는 위치에 구성요소를 자유롭게 배치할 수 있게 됩니다.

<br>

- 절대 단위

	- cm
	- mm
	- in
	- **px**
	- **pt**
	- pc

<br>

- 상대 단위
	- em (부모 요소의 기본 크기를 1em으로 상대적인 크기를 지정.) (2em &rarr; 현재 글꼴 크기의 2배를 의미)
	- ex
	- rem (부모가 아닌 최상위 root를 기준으로 하기 때문에 중간에 기본 값이 바뀌지 않음.) (Root 요소의 글꼴 크기에 비례.)
	- vw
	- vh
	- vmin
	- vmax
	- % (100%를 기준으로 하는 상대 크기)

<br>

앞에 v가 붙은 단위들은 viewport와 관련된 것으로, viewport는 웹페이지가 사용자에게 보여지는 영역을 말하는 것임.

<br>		
			    
<br>

## 웹프로그래밍 (5월 15일)

<br>

### 복합 셀렉터

<br>

복합 셀렉터

본 강좌에서는 좀 더 복잡한 셀렉터를 배우게 됩니다. 

이를 위해 html 계층 구조 안에서 부모요소와 자식요소간의 관계를 파악하고 상속을 통해 CSS 속성 적용이 어떻게 이루어지는지 학습합니다. 

또한 사용자 동작과 UI 요소 상태에 스타일을 적용하는 가상클래스에 대해 배우고 어떤 속성들이 존재하는지 살펴봅니다.

이 강의를 통해 CSS 상속의 개념과 후손, 자손, 형제 선택자등의 선택자 조합과 가상 선택자를 이해하고 사용할 수 있게 됩니다.

<br>

			    
