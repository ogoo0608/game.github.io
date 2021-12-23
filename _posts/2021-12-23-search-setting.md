---
layout: single
title: "깃허브 상단에 검색창 구현하기"
toc: true
toc_sticky: true
toc_label: "On This Page"
categories:
    - Blog
---

<br>

갑자기 깃허브 상단에 검색창을 구현해보고 싶다는 생각이 들었다.

블로그에 검색창이 없으면 섭하지 않은가 ..

암튼 오늘은 검색창을 구현해 볼 것이다 !!

<br>

## 1. __pages_ 폴더에 search.md 파일 생성

<br>

가장 먼저 _pages 폴더에 new file 을 누른 후 search.md 라는 파일을 생성해준다.

그 다음 아래와 같은 코드를 붙여넣어주자.
<br>

```js
    ---
    title: Search
    layout: search
    permalink: /search/
    ---
```