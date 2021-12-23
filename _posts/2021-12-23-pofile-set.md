---
layout: single
title: "깃허브 README.md 꾸미기"
toc: true
toc_sticky: true
toc_label: "On This Page"
categories:
    - Blog
---

<br> 


이런식으로 <mark background = color> 프로필 홈페이지</mark> 를 꾸미는 법을 알려주겠다 !!

![image](https://user-images.githubusercontent.com/96330958/147205002-fd6b69ca-b68b-4bfb-b6ac-c5ee7d6fa323.png)

<br>

## 1. New Repo 생성

<br>

![image](https://user-images.githubusercontent.com/96330958/147205393-e3fa23dc-03ef-4e10-a345-c94615172d28.png)

<br>

새로운 Repository 를 생성할 때, Repository name 을 <font color = 'orange'> 자신의 ID </font> 로 생성해야 한다.

또한 하단의 __Initialize this repository with: 탭__ 에서

__Add a README file__ 가 체크되어 있는지 확인해야 한다.

<br>

## 2. README.md 파일 수정 

<br>

![image](https://user-images.githubusercontent.com/96330958/147207024-6b2135ab-2042-4bfe-8b80-fdfcceedf706.png)

<br>

README.md 파일을 들어가서 본격적으로 수정해주자.

<br>

```
![header](https://capsule-render.vercel.app/api?type=waving&color=gradient&height=400&section=header&text=Hi!%20I'm%20JungJun&fontSize=90&animation=fadeIn&fontAlignY=38&desc=Being%20a%20%20%20%20%20%20Devloper&descAlignY=51&descAlign=80)
```

<br>

capsule-render 라는 repo 에서 구할 수 있는 소스이다.

[capsule-render 깃허브](https://github.com/kyechan99/capsule-render)

이걸 사용하면 자신이 원하는 문구나 bio 를 대문짝하게 걸어둘 수 있다 !!

<br>

```
type=waving&color=gradient&heitght=400
```

<br>

소스를 열어보면 위와 같은 코드를 볼 수 있을텐데,

type, color, height 를 자신이 원하는 디자인으로 수정해줄 수 있다. 

나는 새로고침 할 때마다 색깔이 바뀌게끔 `color=gradient` 로 수정했다.

<br>

```
section=header&text=Hi!%20I'm%20JungJun
```

<br>

위와 같은 코드는 대문짝만한 문구를 수정할 수 있는 부분이다.

보시다시피 나는 `Hi! I'm JungJun` 이라는 문구가 나오게끔 수정했다.

%20 사이사이에 문구를 넣어줘야만 띄어쓰기가 되니까 조심하자.

<br>

```
animation=fadeIn
```

<br> 

말그대로 애니메이션이 fadeIn 이라는 뜻이다.

다른 효과를 원한다면 `fadeIn` 부분을 수정해주면 된다.

<br>

마지막으로 문구를 중간에 딱 예쁘게 배치하고 싶다면 아래와 같은 코드를 쓰면 된다.

<br>

```
<h3 align="center"> 어쩌구저쩌구 </h3>
```

큰 따옴표를 쓰든 작은 따옴표를 쓰든 아무 상관 없다.

<br>

아래와 같은 코드를 붙여넣으면 아이콘이 생성된다.

<br>

//주석은 알잘딱으로 빼자 .. ^^

```
<img src="https://img.shields.io/badge/C++-00599C?style=flat-square&logo=C%2B%2B&logoColor=white"/></a> //C++
<img src="https://img.shields.io/badge/Java-007396?style=flat-square&logo=Java&logoColor=white"/></a> //JAVA
<img src="https://img.shields.io/badge/Python-3766AB?style=flat-square&logo=Python&logoColor=white"/></a> //Python
<img src="https://img.shields.io/badge/Html-E34F26?style=flat-square&logo=Html5&logoColor=white"/></a> //Html
<img src="https://img.shields.io/badge/Css-1572B6?style=flat-square&logo=Css3&logoColor=white"/></a> //Css
```

<br>

그리고 나처럼 이쁘게 배치하고 싶다면 아래 코드를 먼저 붙여넣고 아이콘을 넣어주자

```
<p align="center">
```

이거 안 넣으면 멋없음..