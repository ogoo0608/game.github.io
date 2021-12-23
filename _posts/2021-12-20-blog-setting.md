---
layout: single
title: "minimal mistakes 블로그 세팅"
toc: true
toc_sticky: true
toc_label: "On This Page"
categories:
    - Blog
---

<br>

## 1. 블로그 글 제목 색상 변경

---
> _sass/minimal-mistakes/skins/_contrast.scss



다음과 같은 경로에서 내 blog의 메뉴, 글 제목 등등의 색깔을 변경할 수 있다.


나는 blog의 **Primary-Color, Link-Color** 가 맘에 안 들어서 적당한 색상으로 바꿨다. 


<br>
<br>

## 2. less than minutes 문구 삭제 및 날짜 표기

---
블로그 home 에서 **less than 1 minutes** 라는 문구가 맘에 안 들어서 ,,


**게시글을 작성한 날짜만을 표기하게끔 수정해보겠다..**

<br>

> /_includes/archive-single.html 

다음과 같은 경로 26번째 줄에 

~~~java
<p class="archive__item-excerpt"><i class="far fa-calendar-alt"></i> 
{//{ post.date | date: "%m/%d/%Y" }} </p>
~~~

와 같은 코드를 입력해주면 날짜가 표기될 것이다..

> 정상 작동하는 것을 확인했다. (근데 less than minutes 는 안 사라짐....)

+ _include 폴더에 read-time.html 을 추가했다.. 이거 없으면 작동 안 된다길래..
+ 추가로 카테고리 기능을 추가했다.. 제발 오류 뜨지마라 ㅜㅜ
+ __less than minutes 는 config_yml 에서 read_time: true --> false 로 수정해주면 된다..__


<br>
<br>

## 3. 글자 크기 변경

---
**블로그를 보고 있자니 글자 크기가 거슬려서 도무지 참을 수가 없다..**

> /_sass/minimal-mistakes/_reset.scss

다음과 같은 경로에 있는 **font-size** 를 조절해주면 된다고 한다. ^^

<br>

## 4. 폰트 변경


**추가적으로 폰트도 변경하고 싶다면**

> /assets/css/main.scss

의 맨 아래에 자신이 원하는 폰트의 링크를 import 한다..

참고로 import 할 때 앞 뒤 <//style> 태그는 제외하도록 한다.

<br>

그 다음 

> _sass/minimal-mistakes/_variables.scss

을 수정하면 된다. 

~~~java
/* system typefaces */
$serif: Georgia, Times, serif !default;
$sans-serif: -apple-system, BlinkMacSystemFont, "Roboto", "Segoe UI",
  "Helvetica Neue", "Lucida Grande", Arial, sans-serif !default;
$monospace: Monaco, Consolas, "Lucida Console", monospace !default;
~~~

에서 "Roboto" 를 "ex" 로 바꾸면 성공이다.


<br>

## 5. 코드 블럭 오류

---

마지막으로 마크다운 문법 중 코드블록 ( ``` ) 을 사용 했을 때

Syntax Color 가 적용 안 되는 것을 고치고 자러 가야겠다. 

+ VScode 미리 보기에서는 아무 문제 없이 코드블록이 출력되는데 블로그에는 그냥 밋밋한 코드블록만이 ..
  
찾아보던 중 문법이 잘 설명되어 있는 블로그를 발견했다.

<br>

<span style="color:red">[ansohxxn 님의 블로그](https://ansohxxn.github.io/blog/markdown/#%EC%BD%94%EB%93%9C-%EB%B8%94%EB%A1%9D)</span>

<br>

코드블록 type 를 java 로 변경하니까 아주 잘 렌더링 된다 . . .

해결 완료 .. ^^

<br>

---

